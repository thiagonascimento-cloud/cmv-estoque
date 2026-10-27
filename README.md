# CMV e Estoque

Página única (HTML) que calcula o CMV mês a mês a partir de três arquivos:

1. **Razão da conta de estoque**: TXT exportado do Domínio, Excel ou CSV.
2. **SPED ICMS/IPI**: um `.txt` da EFD por mês.
3. **Inventários**: PDFs de veículos, peças etc. A página usa o total da última página.

Os arquivos são lidos só no navegador e nada é enviado para servidor.

## Como usar

Online: **https://thiagonascimento-cloud.github.io/cmv-estoque/**

Para instalar como aplicativo, abra o endereço no Chrome ou no Edge e clique no ícone **Instalar** no canto direito da barra de endereço (ou menu **⋮** → **Transmitir, salvar e compartilhar** → **Instalar página como app**). O app ganha ícone próprio na Área de Trabalho e no Menu Iniciar e abre numa janela própria.

Também funciona baixando a pasta: abra `CMV Estoque.html` no navegador e solte os arquivos nos três quadros. A página precisa de internet para carregar o leitor de PDF (pdf.js) e o de Excel (SheetJS).

### Usar como programa no computador

1. Baixe o repositório: botão verde **Code** → **Download ZIP**. Extraia numa pasta fixa, por exemplo `C:\CMV Estoque`.
2. Abra `CMV Estoque.html` no Google Chrome.
3. No menu **⋮** do Chrome, vá em **Transmitir, salvar e compartilhar** → **Criar atalho…**. Marque **Abrir como janela** e clique em **Criar**.

O atalho vai para a Área de Trabalho e para o Menu Iniciar e abre a interface numa janela própria, como um programa. Se a pasta mudar de lugar, crie o atalho de novo.

O estoque inicial do primeiro mês pode ser digitado por tipo (veículos e peças). Se o campo ficar em branco, a página usa o saldo do razão.

## O que a página mostra

- **CMV a lançar:** para cada mês, veículos e peças separados:
  - estoque inicial, compras, crédito de IPI, crédito de PIS/COFINS, devoluções e outros, inventário final;
  - o CMV (estoque inicial + compras − deduções − inventário final), com a marcação se já está lançado no Domínio. Em vermelho fica o que ainda não foi lançado, e em amarelo o que foi lançado com diferença;
  - clicando na linha, abre a memória de cálculo e os valores gerais do mês.
- **Mês a mês:** CMV apurado pelo SPED (estoque inicial + compras − estoque final), comparado com o CMV contabilizado, e uma tabela de estoque por tipo.
- **Detalhe do mês:**
  - apuração e conferência com o razão;
  - memória de cálculo;
  - compras conferidas nota a nota (SPED × razão);
  - entradas por CFOP, com o tratamento de cada CFOP ajustável.
- **Relatórios:** geral e mensal, em PDF (pela impressão do navegador) e em Excel. Mostram, mês a mês e por tipo de estoque: estoque inicial + entradas − deduções − CMV = estoque final, com a situação do CMV no Domínio.

## Regras de cálculo

- **Compras:** valor contábil (VL_OPR do C190/D190) dos CFOPs de compra, menos o IPI e o ICMS recuperáveis e os créditos de PIS/COFINS lançados no razão. Notas canceladas, denegadas e inutilizadas ficam de fora.
- **SPED retificador:** quando há original e retificadora do mesmo mês, vale a retificadora.
- **Inventário:** os PDFs do mesmo mês são somados. PDF digitalizado (sem texto) pede o total digitado. O Bloco H do SPED é usado quando não há PDF para aquele mês.
- **Lançamentos do razão:** o tipo de cada lançamento (compra, CMV, crédito de imposto, transferência, devolução) é identificado pelo histórico.
