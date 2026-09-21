# 📰 Pulso News

O **Pulso News** é um agregador de notícias em português que reúne manchetes de vários feeds RSS e as apresenta em uma interface escura, responsiva e com atualização automática. A proposta é oferecer uma visão rápida do que está acontecendo em mundo, Brasil, tecnologia, ciência, economia, esportes e entretenimento.

🌍 **Versão publicada:** [pulsonews.vercel.app](https://pulsonews.vercel.app/)

## Recursos

- Consulta simultânea de diversos feeds RSS por meio do serviço RSS2JSON.
- Atualização automática a cada cinco minutos e botão de atualização manual.
- Categorias com contagem de notícias e filtro instantâneo.
- Ticker de urgência com as manchetes mais recentes.
- Destaque principal e três cards laterais para as notícias em evidência.
- Grid responsivo de notícias com imagem, fonte, resumo, horário relativo e link original.
- Deduplicação local por título para evitar manchetes repetidas.
- Fallback para o feed da BBC Brasil quando nenhum feed retorna resultados.
- Skeleton loading, estados vazios, toast de erro e relógio em tempo real.

## Fontes e fluxo

As fontes são declaradas no array `FEEDS` do `index.html`, cada uma com URL RSS, nome da fonte e categoria. O navegador consulta o endpoint RSS2JSON, normaliza os itens, combina as respostas, ordena por data, remove duplicatas e renderiza a interface.

```text
feeds RSS → RSS2JSON → normalização → ordenação/deduplicação → filtros e cards
```

Fontes configuradas incluem BBC Brasil, Gazeta do Povo, Agência Brasil, Veja, Olhar Digital, Canaltech, Super, Inovação Tecnológica, InfoMoney, Exame, Futboo, Notícias ao Minuto, Rolling Stone e Motor1.

## Rodar localmente

Não há build ou servidor próprio. Para testar com um servidor HTTP:

```bash
git clone https://github.com/phoenixsrd/pulsonews.git
cd pulsonews
python3 -m http.server 8080
```

Abra `http://localhost:8080`.

## Estrutura

```text
index.html  # Marcação, estilos, feeds, lógica de atualização e renderização
.github/    # Configurações auxiliares do GitHub
license     # Licença do projeto
```

## Observações

- O conteúdo pertence às fontes originais; o Pulso News apenas agrega e aponta para os links de origem.
- A disponibilidade depende dos feeds RSS, do serviço RSS2JSON, da rede e de eventuais limites de requisição.
- Como o app é totalmente client-side, não há banco de dados nem armazenamento permanente de notícias.
- Para adicionar uma fonte, inclua um objeto em `FEEDS` com `url`, `source` e `cat`.
