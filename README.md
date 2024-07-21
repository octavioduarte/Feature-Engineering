(README in Portuguese-BR - Project in English)
# Feature Engineering pros gringos - Engenharia de Atributos pra nós - O que é?

<br/>

É o nome dados a técnica de utilizar o conhecimento sobre o negócio para selecionar/manipular os atributos a partir dos dados brutos. 

No texto sobre as etapas para a construção de um modelo de Machine Learning, vimos que a primeira etapa consiste em entender o domínio para, em seguida, realizarmos a coleta e preparação dos dados. É indispensável que essa sequência seja seguida, pois compreender o problema do negócio é fundamental para aplicar a melhor abordagem no processo de coleta e manipulação dos dados.

É sempre bom lembrar que os dados não chegam em um formato propício para o treinamento do modelo. No primeiro contato entre um profissional de dados e os dados em si, sempre será necessário um processo de limpeza, pois os chamados dados brutos  💪🎲 (nome dado aos dados ainda não formatados) podem gerar modelos ineficientes. No entanto qualquer estratégia para editar/excluir ou criar dados em um conjunto deve ser feita com a premissa de que a solução para o problema do negócio não sera afetada - Essa é a base da Engenharia de Atributos/ Feature Engineering.

<br/>

#### Algumas  técnicas utilizadas durante o processo de Engenharia de Atributos

Ok, a essa altura já compreendemos que precisamos ter o conhecimento do negócio e do problema que precisa ser resolvido (assim espero 🧐). Depois disso, entendemos que precisamos realizar a coleta dos dados, que são a matéria-prima de qualquer modelo. Na sequência, realizamos o processo da análise exploratória, etapa na qual nos aprofundamos nos dados para entender as relações entre eles, possíveis lacunas, etc. Agora, chega a hora de realizarmos o processo de seleção dos atributos que serão escolhidos para o treinamento do modelo. Uma vez escolhidos, existem técnicas para garantir que o formato desses mesmos atributos esteja adequado para o processo. Vamos ver mais sobre essas técnicas:

<br/>

## Feature Engineering para seleção de atributos 👇:

<br/>

> ### Filtros 🔬

<br/>

> Consiste em aplicarmos técnicas para verificar o quão próximo está o atributo em relação à minha variável de saída. Por exemplo, em um contexto de análise de fraude, quão determinante é escolher o atributo "Idade" para determinar se uma compra é ou não uma fraude? São perguntas que são respondidas através da análises correlação por exemplo. Importante notar que isso independe de tecnologia é uma análise humana, é claro que podemos recorrer a recursos gráficos para visualizar quais atributos fazem ou não sentido para o treinamento do modelo, mas a decisão neste caso é humana, ou seja, a vantagem de utilizar filtros para seleção de atributos  é não demandar custo computacional para o processo - Usar filtros para seleção de atributos é uma técnica comum na comunidade de cientista de dados.

<br/>
<hr/>
<br/>

> ### Wrapper methods 

<br/>

> Essa técnica envolve instanciar um algoritmo e passar a ele nosso conjunto de dados -  O algoritmo divide o conjunto em subconjuntos com diferentes combinações de atributos e determina, através de um processo de avaliação (guarde bem essa parte) qual a melhor combinação de atributos para nosso treinamento. Um exemplo de algoritimo que implementa essa técnica é o RFE do sklearn.

> Abaixo uma imagem extraída deste link da documentação do sklearn onde o RFE aplicou os testes em diferentes subconjuntos e determinou qual o mais eficiente com base no resultado - É como se fosse um ranking dos atributos  mais importantes para nossa variável de saída, cada quadrado representa o quão forte é a interação entre um determinado atributo e nossa variável de saída.

> Um ponto importante sobre wrapper methods é que podem demandas um alto custo computacional, principalmente quando estamos lidando com um alto número de atributos em nosso conjunto, mas ainda sim é extremamente eficiente e tende a costuma entregar modelos com resultados melhores do que aqueles que foram treinados através do processo de filtros.

<br/>
<hr/>
<br/>

> ### Embedded methods 

<br/>

> Enquanto os wrapper methods determinam a melhor combinação de atributos através de um processo de avaliação, os embedded methods fazem isso a partir dos resultados do treinamento do modelo. Isso significa que o treino e a seleção de atributos são processos que ocorrem de forma sincronizada nos embedded methods. No scikit-learn, por exemplo, métodos como RandomForest (seja para classificação ou regressão) já contam com técnicas durante o treinamento que determinam quais são os atributos mais relevantes para o modelo, mas isso não significa que ao utilzar modelos RandomForest não devemos nos preocupar com a seleção de atributos, embedded methods demandam um alto custo computacional e em conjuntos grandes isso pode ser um problema - Aplicar a filtragem antes do RandomForest para que ele lide com um menor conjunto de atributos é uma solução apropriada por exemplo.