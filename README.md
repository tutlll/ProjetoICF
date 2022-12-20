# ProjetoICF

Este programa foi desenvolvido como projeto final da disciplina de Introdução à Computação em Física, da Universidade Federal de Minas Gerais. O programa tem como objetivo determinar uma estrela da sequência principal a partir de parâmetros primários, além disso também são determinadas as principais informações sobre a estrela procurada. O código está disponível no repositório tanto no formato de notebook("Projeto_ICF(notebook).ipynb") tanto como python comum("Projeto_ICF(py).py").

### Identificando a estrela
 
 Como banco de dados, será usado o SIMBAD Astronomical Database, do Centro de dados astronômicos de Estrasburgo[1], para evitar estrelas com parâmetros faltando, e limitar o tempo de execução do programa, esse banco de dados foi limitado a 20000 estrelas da sequência principal, mas o programa pode ser aplicado à um banco de dados de qualquer tamanho, esses dados estão no arquivo de texto "data_SIMBAD_2.txt" que pode ser encontrado no repositório. Na primeira parte do código esse banco de dados é convertido de um arquivo de texto para listas. Na segunda parte do programa são solicitados 3 parâmetros para identificar a estrela, **Paralaxe , Magnitude em B, Magnitude em V**, dentre eles o mais importante é a paralaxe, os demais podem ser omitidos caso o primeiro tenha precisão suficiente. Assim, é realizada a busca no banco de dados por uma estrela que corresponde ao parâmetro, nisso é utilizada a função ""consultafloat ou consultastring", a depender do tipo do parâmetro utilizado. Com a estrela identifica, seu tipo espectral é utilizado para consultar uma tabela com os parâmetros médios de cada tipo espectral para estrelas da sequência principal, essa tabela pode ser encontrada no aquivo "tabela_mainseq.txt"[4], com isso mais parâmetros da estrela são determinados, aproximando eles pelos parâmetros de seu tipo espectral na tabela.
 
 ### Determinando mais parâmetros
 
  A partir da tabela, são identificados : Temperatura, Correção Bolométrica, Luminosidade, Magnitude Bolométrica, Raio, Magnitude absoluta em V, Índice de cor B-V, Massa. Outros parâmetros são determinados por meio das seguintes funções. Aproximando o tempo para a estrela deixar a sequência principal, como o tempo que ela leva para perder a massa de hidrogênio(10%), considerando a eficiência de 0.7% e o gasto da energia igual a luminosidade, assim t=en/L, a função "temponuclear" calcula esse tempo. A cor da estrela pode ser aproximada, considerando a estrela como um corpo negro assim a cor pode ser determinada em função da temperatura, assim a cor é calculada pela função "cor", as funções estão disponíveis na referência [2]. O estágio final da evolução dessa estrela é determinado pela função "finalevol", a previsão do fim dessa evolução é tabelado em função da massa da estrela na sequência principal[3].
  
 ### Visualização de outros resultados
 
  Já que os parâmetros RGB da estrela foram identificados pela função "cor", essa cor é disposta na forma de um gráfico, usando a biblioteca matplotlib. Usando essa mesma biblioteca é disposta uma comparação visual entre o tamanho dessa estrela e do sol. Por fim, usando os tipos espectrais da tabela em "tabela_mainseq.txt" como pontos, foi calculada a interpolação desses pontos utilizando a biblioteca scipy, e foi evidenciada a posição da estrela procurada no diagrama HR de magnitude absoluta e índice da cor B-V.
 
### Referências

[1] Base de dados SIMBAD/CDS; http://simbad.u-strasbg.fr; Acesso em: 18 de novembro, 2022.

[2] "Convert Temperature (K) to RGB" Tanner Helland's website : https://tannerhelland.com/2012/09/18/convert-temperature-rgb-algorithm-code.html

[3] Evolução Final das Estrelas; http://astro.if.ufrgs.br/estrelas/node14.htm

[4] Erick Mamajek, University of Rochester; http://www.pas.rochester.edu/ emamajek/spt/B9IV.txt;
Acesso em : 18 de novembro, 2022.

[5] Allen, CW. Allen's Astrophysical Quantities. 4º edição. NY, Springer New York, 2002.
