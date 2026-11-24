# 💐 Buquê 3D Interativo em ASCII (`bouquet3d`)

Um buquê de flores tridimensional renderizado em tempo real com caracteres ASCII coloridos, construído do zero em **HTML5 Canvas e JavaScript puro** (sem bibliotecas externas de 3D), inspirado na estética clássica de renderização em terminal (*donut.c*).

🔗 **Acesse ao vivo:** [rafaacosta12.github.io/buque-para-voce](https://rafaacosta12.github.io/buque-para-voce/)

---

## ✨ Funcionalidades

- **Renderização 3D em ASCII a 60 FPS:** Nuvem de pontos paramétricos projetada em grade tipográfica com escala responsiva para desktop e dispositivos móveis.
- **Z-Buffer (Buffer de Profundidade):** Garante a oclusão correta entre pétalas, caules, folhagens e o cone de embrulho durante toda a rotação.
- **Iluminação Difusa:** Cálculo de produto escalar entre o vetor normal de cada ponto e a fonte de luz direcional para mapear luminosidade em caracteres (`.,-~:;=!*#$@`) e intensidade RGB.
- **Interatividade Total:**
  - Rotação automática suave com opção de pausar/retomar.
  - Controle manual por arraste (mouse ou toque na tela) nos eixos X e Y, além de zoom.
- **Links Personalizáveis via URL:** Botão integrado (**✎ Personalizar**) que permite editar a dedicatória e gerar um link compartilhável com parâmetros de query (`?m=...&s=...`).

---

## 🧮 Como funciona a matemática por trás

1. **Modelagem Paramétrica:** Cada espécie no arranjo (rosas em espiral, girassóis com miolo texturizado, tulipas, ramos de mosquitinho e folhagens) é gerada matematicamente no espaço $(x, y, z)$ junto com seu vetor normal $(n_x, n_y, n_z)$.
2. **Matrizes de Rotação:** A cada frame, os pontos e suas normais são rotacionados nos eixos $Y$ e $X$ usando transformações trigonométricas ($\sin$ e $\cos$).
3. **Projeção em Perspectiva:** As coordenadas 3D são projetadas no plano 2D do Canvas dividindo pela profundidade da câmera:
   $$x_{tela} = \frac{w}{2} + \frac{x \cdot escala}{d + z}, \quad y_{tela} = \frac{h}{2} + \frac{y \cdot escala}{d + z}$$
4. **Sombreamento ASCII:** O nível de brilho $L = \vec{N} \cdot \vec{L}$ define tanto o caractere escolhido na paleta de densidade quanto o fator de multiplicação de cor.

---

## 🚀 Como executar localmente

Como o projeto não possui dependências externas, basta clonar o repositório e abrir o arquivo `index.html` no navegador:

```bash
git clone [https://github.com/rafaacosta12/buque-para-voce.git](https://github.com/rafaacosta12/buque-para-voce.git)
cd buque-para-voce
