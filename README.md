# Apuração por região — Eleições 2026, 2º turno

Site estático que mostra, ao vivo, a apuração do 2º turno para Presidente:
percentual de urnas apuradas e votos de cada candidato no Brasil, em cada
região (Norte, Nordeste, Centro-Oeste, Sudeste, Sul e Exterior) e por estado.

Os dados vêm direto dos arquivos públicos do TSE
(`resultados.tse.jus.br`), sem backend.

## Como funciona

- A cada 10 s a página baixa o arquivo nacional
  `oficial/ele2026/6258/dados/br/br-c0001-e006258-u.jws`.
- Quando o TSE publica uma nova totalização, recarrega os arquivos das 27 UFs
  e do exterior e soma por região.
- Os arquivos `.jws` são JSON assinados (JWS); o conteúdo é o payload em
  base64url.

Outra eleição ou cargo pela URL: `/?e=6257` (1º turno), `/?c=1` (cargo).

## Rodar localmente

Abra o `index.html` no navegador, ou:

```bash
python -m http.server 8000
```

## Deploy

Projeto estático: na Vercel, importe o repositório e use as configurações
padrão (Framework Preset: Other, sem build).
