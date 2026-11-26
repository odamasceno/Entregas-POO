# Jogo Pong em C# com Windows Forms e Threads

Trabalho prático da disciplina **Programação Orientada a Objetos** (UNIFESP – Campus São José dos Campos, Prof. Rodrigo Colnago Contreras).

Pong para dois jogadores no mesmo teclado. A bola e cada raquete se movem em threads próprias, separadas da thread da interface.

**Integrantes**

- Felipe Pereira Vergal Rostirola – RA 185210
- Iago da Silva Leite – RA 185228
- Rafael Damasceno Marques dos Santos – RA 187561

## Conteúdo desta pasta

| Arquivo | O que é |
| --- | --- |
| `ProjetoPOO_Pong.zip` | Código-fonte completo (solução do Visual Studio) |
| `Relatorio-Pong.pdf` | Relatório descritivo |
| `videopong.mp4` | Vídeo demonstrativo (também em https://youtu.be/BaQ_L5Hdqvs) |

## Requisitos

- Windows 10 ou 11
- Visual Studio Community com a carga de trabalho **Desenvolvimento para desktop com .NET**
- .NET Framework 4.7.2 (já vem instalado no Windows 10 e 11 atualizados)

## Como executar

1. Baixe o arquivo `ProjetoPOO_Pong.zip` e extraia em uma pasta.
2. Abra o arquivo `ProjetoPOO_Pong/ProjetoPOO_Pong.sln` no Visual Studio.
3. Pressione **F5** (ou clique em **Iniciar**) para compilar e executar.

Também é possível executar direto o arquivo já compilado em `ProjetoPOO_Pong/ProjetoPOO_Pong/bin/Debug/ProjetoPOO_Pong.exe`.

## Como jogar

| Controle | Ação |
| --- | --- |
| `W` / `S` | Move a raquete do Jogador 1 (esquerda) para cima / para baixo |
| Seta para cima / Seta para baixo | Move a raquete do Jogador 2 (direita) para cima / para baixo |
| **Iniciar** | Inicia a partida e coloca a bola em movimento |
| **Pausar** / **Retomar** | Pausa a partida e depois a retoma do mesmo ponto |
| **Reiniciar** | Zera o placar e recoloca bola e raquetes no centro |

- A bola rebate nas bordas de cima e de baixo e nas raquetes, e fica um pouco mais rápida a cada rebatida.
- Se a bola passar pela raquete de um jogador, o adversário marca um ponto e a bola volta ao centro com uma nova direção.
- Vence quem fizer **5 pontos** primeiro.

## Organização do código

| Arquivo | Responsabilidade |
| --- | --- |
| `Bola.cs` | Posição, velocidade e movimento da bola |
| `Raquete.cs` | Posição e movimento vertical da raquete, dentro dos limites da arena |
| `Jogador.cs` | Nome, pontuação e raquete de cada jogador |
| `Jogo.cs` | Regras: colisões, pontuação, fim de partida e reinício |
| `Form1.cs` | Interface, teclado, botões e as três threads do jogo |

O formulário cria três threads (`threadBola`, `threadRaquete1` e `threadRaquete2`). Cada uma atualiza o modelo cerca de 60 vezes por segundo e usa `Invoke` para atualizar a tela na thread da interface. Os detalhes estão no capítulo 5 do relatório.
