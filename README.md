# Miraa PWA — celular

Esta versão foi preparada para abrir diretamente no navegador do Android e pode ser adicionada à tela inicial como aplicativo.

## Uso
1. Publique esta pasta em um endereço HTTPS (GitHub Pages, Netlify, Cloudflare Pages etc.).
2. Abra o endereço no Chrome do Android.
3. Use o menu do Chrome → **Adicionar à tela inicial**.
4. Abra ⚙ no Miraa e informe o endereço do endpoint GPU, por exemplo:
   `https://SEU-SERVIDOR/transcribe`
5. Escolha o modo:
   - Rápido
   - Equilibrado
   - Preciso
6. Escolha o vídeo/áudio e toque em **Transcrever rápido**.

## Backend
O endpoint esperado é o backend `Miraa-GPU-Transcriber` que já foi preparado:
`POST /transcribe`
campos multipart:
- file
- mode = fast | balanced | accurate
- language = ja

A resposta esperada é JSON com:
`{"language":"ja","duration":123,"cues":[{"start":0,"end":2,"text":"..." }]}`

## Importante
O PWA pode ser aberto localmente como HTML, mas o modo instalável (PWA) exige HTTPS. A transcrição rápida depende de um servidor GPU; sem ele o navegador não terá a velocidade do TurboScribe.

A arquitetura usa GPU para a parte pesada, em vez de executar Whisper no Moto G52. Isso é deliberado para priorizar velocidade.
