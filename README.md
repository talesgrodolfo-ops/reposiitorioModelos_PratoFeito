# Repositório de Modelos 3D — Prato Feito

Assets visuais do jogo educativo **Prato Feito**, desenvolvido como projeto integrador pelo 4° Info do IFSP Câmpus Itapetininga: modelos 3D em glTF para realidade aumentada, fotos 2D para as telas de confirmação e resultado, e o PDF dos cartões físicos usados no rastreamento MindAR.

Este repositório **não contém a aplicação web**. Ele complementa o [repositório principal](https://github.com/talesgrodolfo-ops/PratoFeito), que consome estes arquivos via URL publicada no Cloudflare Pages.

---

## Visão geral

| Aspecto | Detalhe |
|---|---|
| Formato 3D | glTF 2.0 (`.gltf` + `.bin` + texturas) |
| Uso na AR | Carregados pela cena A-Frame + MindAR no `index.html` do app |
| Fotos 2D | JPEG / WebP em `img/`, referenciadas no catálogo `produtos.json` |
| Cartões AR | `cardsPraoFeito-Impressao.pdf` (19 alvos impressos) |
| Licença dos modelos | CC-BY-4.0 (créditos em `license.txt` de cada pasta) |
| Alimentos no jogo | 19 itens |

---

## Estrutura do repositório

```
reposiitorioModelos_PratoFeito/
├── README.md
├── cardsPraoFeito-Impressao.pdf    # Cartões para impressão e escaneamento
│
├── img/                            # Fotos 2D dos alimentos (telas pós-AR)
│   ├── tomate.webp
│   ├── alface.jpg
│   └── ...
│
├── tomato/                         # Um diretório por alimento
│   ├── scene.gltf                  # Modelo principal (padrão)
│   ├── scene.bin
│   ├── textures/
│   └── license.txt                 # Autoria e licença Sketchfab
│
├── beetroot/
│   ├── beterraba.gltf              # Exceção: nome de arquivo alternativo
│   └── ...
│
└── ...                             # Demais alimentos (ver catálogo abaixo)
```

Cada pasta de alimento segue o mesmo padrão:

- **`scene.gltf`** — entrada do modelo (usada na maioria dos itens).
- **`scene.bin`** — geometria binária referenciada pelo glTF.
- **`textures/`** — mapas de cor e materiais quando aplicável.
- **`license.txt`** — título original, link Sketchfab, autor e texto de atribuição CC-BY-4.0.

---

## Catálogo de alimentos

Correspondência entre `id` (MindAR / `produtos.json`), pasta no repositório e arquivos servidos na AR.

| ID | Pasta | Alimento | Arquivo glTF | Foto 2D (`img/`) |
|:---:|:---|:---|:---|:---|
| 0 | `tomato` | Tomate | `scene.gltf` | `tomate.webp` |
| 1 | `broccoli` | Brocolis | `scene.gltf` | `brocolis.jpg` |
| 2 | `cabbage` | Repolho | `scene.gltf` | `repolho.jpg` |
| 3 | `lechuga` | Alface | `scene.gltf` | `alface.jpg` |
| 4 | `beetroot` | Beterraba | `beterraba.gltf` | `beteraba.jpg` |
| 5 | `banana` | Banana | `scene.gltf` | `banana.jpeg` |
| 6 | `rice` | Arroz | `scene.gltf` | `arroz.jpg` |
| 7 | `spaghetti` | Macarrão | `scene.gltf` | `macarao.jpg` |
| 8 | `miojo` | Miojo de Queijo | `scene.gltf` | `miojo.jpg` |
| 9 | `pork` | Carne de Porco | `scene.gltf` | `carneDEporco.jpg` |
| 10 | `beef` | Carne Vermelha | `scene.gltf` | `carneVermelha.webp` |
| 11 | `chicken` | Frango Frito | `scene.gltf` | `frnagoFrito.webp` |
| 12 | `fried_fish` | Peixe Frito | `scene.gltf` | `peixeFrito.jpg` |
| 13 | `french_fries` | Batata Frita | `scene.gltf` | `batataFrita.webp` |
| 14 | `boiled_egg` | Ovo Cozido | `scene.gltf` | `ovoCozido.webp` |
| 15 | `fried_egg` | Ovo Frito | `scene.gltf` | `ovoFrito.webp` |
| 16 | `chicken_steak` | Steak | `scene.gltf` | `steak-de-frango.webp` |
| 17 | `sausage` | Salsicha | `scene.gltf` | `salsicha.webp` |
| 18 | `pizza` | Pizza de Calabresa | `scene.gltf` | `pizza.jpg` |


---

## Integração com a aplicação Prato Feito

No app principal, cada entrada de `produtos.json` referencia URLs absolutas para o modelo 3D e a foto 2D:

```json
{
  "id": 0,
  "nome": "Tomate",
  "modelo": "https://reposiitoriomodelos-pratofeito.pages.dev/tomato/scene.gltf",
  "foto": "https://reposiitoriomodelos-pratofeito.pages.dev/img/tomate.webp",
  "peso": 100,
  "escala": { "x": 0.20, "y": 0.20, "z": 0.20 }
}
```

1. Publique o conteúdo deste repositório em um host estático (GitHub Pages, Cloudflare Pages, etc.).
2. Atualize as URLs em `produtos.json` no repositório da aplicação.
3. Gere o arquivo `mind/targets.mind` a partir das imagens dos cartões impressos (processo feito no projeto AR, não neste repo).
4. Imprima [`cardsPraoFeito-Impressao.pdf`](cardsPraoFeito-Impressao.pdf) para uso físico no jogo.

### URL em produção

Os assets deste repositório são publicados em **Cloudflare Pages**:

```
https://reposiitoriomodelos-pratofeito.pages.dev/
```

Exemplos de URLs já usadas pelo app:

- Modelo: `https://reposiitoriomodelos-pratofeito.pages.dev/tomato/scene.gltf`
- Foto: `https://reposiitoriomodelos-pratofeito.pages.dev/img/tomate.webp`
- Beterraba: `https://reposiitoriomodelos-pratofeito.pages.dev/beetroot/beterraba.gltf`

Para testes locais ou forks, o raw do GitHub também funciona:

```
https://raw.githubusercontent.com/talesgrodolfo-ops/reposiitorioModelos_PratoFeito/main/<pasta>/<arquivo>
```

---

## Cartões físicos (MindAR)

O jogo usa **19 cartões impressos**, um por alimento. O PDF neste repositório contém as imagens que o jogador escaneia com a câmera.

- [Baixar cartões para impressão](cardsPraoFeito-Impressao.pdf)
- Cada cartão corresponde a um `targetIndex` no arquivo `mind/targets.mind` (gerado no projeto da aplicação)
- O `id` do alimento em `produtos.json` deve ser o mesmo índice do alvo MindAR

---

## Especificações técnicas dos modelos

| Requisito | Recomendação |
|---|---|
| Formato | glTF 2.0 |
| Escala na cena | Definida por alimento em `produtos.json` (`escala.x/y/z`); o app ajusta proporcionalmente ao peso |
| Caminhos relativos | Texturas e `.bin` referenciados com caminhos relativos ao `.gltf` (manter estrutura de pastas ao publicar) |

Ao substituir um modelo, preserve o nome do arquivo glTF esperado pelo `produtos.json` ou atualize a URL no catálogo da aplicação.

---

## Licenciamento e atribuição

Todos os modelos 3D foram obtidos sob licença.

Para cada alimento, consulte o `license.txt` na respectiva pasta. O arquivo contém:

- Título e link do modelo original
- Nome do autor
- Texto de crédito pronto para copiar

**Ao reutilizar ou redistribuir estes modelos**, mantenha a atribuição exigida pela licença em qualquer material derivado, site ou publicação do projeto.

---

## Contribuindo

Ao adicionar ou atualizar um alimento:

1. Crie uma pasta com nome original, alinhado ao catálogo.
2. Exporte em glTF 2.0 com texturas embutidas ou em subpasta `textures/`.
3. Adicione `license.txt` com fonte, autor e licença.
4. Inclua a foto correspondente em `img/`.
5. Atualize `produtos.json` e `targets.mind` no repositório da aplicação.
6. Se o jogo ganhar um novo cartão, atualize também `cardsPraoFeito-Impressao.pdf`.

---

## Aviso legal

Este material faz parte de um **jogo educativo**. As representações visuais dos alimentos e as informações nutricionais associadas no app não substituem orientação de profissional de saúde ou nutricionista.

---

## Links relacionados

- Aplicação web: [talesgrodolfo-ops/PratoFeito](https://github.com/talesgrodolfo-ops/PratoFeito)
- URL dos modelos: [reposiitoriomodelos-pratofeito.pages.dev](https://reposiitoriomodelos-pratofeito.pages.dev/)
- Vídeo explicativo do jogo: [YouTube — Prato Feito](https://www.youtube.com/watch?v=IfmlV2pRZ0M)
