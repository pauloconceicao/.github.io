---
layout: post
title:  "Análise Geoespacial com GIS (Geographic Information System) e Python: uma breve introdução - segunda parte"
date: 2020-07-24 00:00:00
description: Segundo blogpost de uma sequência de 3
img: capa.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Mining, Dataset, Geocoding, Visualization]
categories: [Mining, Dataset, Geocoding, Visualization]
---
Como mencionado na [primeira parte](https://pauloconceicao.github.io/como-postar-no-github-com-jekyll/) deste artigo ele é divido em três e, nesta, será abordada a utlizização de GIS e alguns conceitos direcionados ao problema em curso.

### O que é GIS (Geographic Information System)? ###
Usando a terminologia popular, é um conjunto de ferramentas para coletar, gerenciar e analisar dados. É utilizada para análise de dados geoespaciais, como a localização de pontos, linhas e polígonos e organiza as informações em camadas para visualização em mapas. Com GIS é possível revelar-se novos insights dos dados, tais como, interações, padrões e relacionamentos para auxiliar a tomada de decisões.

O uso de GIS está sendo difundido em diversos setores mundiais como educação, saúde, segurança, petróleo, recursos naturais, sustentabilidade, eletricidade, gás, manufatura, comércio, transporte, segurança pública, telecomunicações, água e muito mais.

#### Dados vetoriais ####
Como falávamos em mapas, não podemos deixar de falar em dados vetoriais, que são compostos de localizações geométricas discretas, conhecidas como vértices que definem a forma do objeto espacial. A organização destes vértices determina o tipo de vetor que está sendo trabalhado. São divididos em três tipos:

**Pontos**: cada ponto é definido por seu par de coordenada (x,y). Em um arquivo de vetores, composto por pontos, podem existir muitos pontos. Como exemplo de dados composto por pontos, tem-se pontos de amostragens, localização de objetos específicos ou localização de gráficos.

**Linhas**: linhas são compostas por pelo menos dois vértices, ou pontos, que são conectados. Por exemplo, uma rua ou estrada podem ser representadas por uma linha. Essa linha pode ser representada por uma série de segmentos, cada encontro entre os segmentos da estrada representa um vértice que tem uma localização x e y.

**Polígonos**: um polígono consiste em pelo menos três vértices que são conectados e fechados. Os polígonos podem representar as bordas de lagos, oceanos, cidades, estados, países, etc. 

#### Shapefiles: pontos, linhas e polígonos ####
Os dados geoespaciais em forma de vetor são frequentemente armazenados em um arquivo chamado de shapefile e este dá nome, de forma geral, para os arquivos que têm essa finalidade. Também possui formato chamado de shapefile ou **.shp**. Devida a estrutura dos pontos, linhas e polígonos serem diferentes entre si, cada shapefile contém somente vetores do mesmo tipo, todos serão pontos ou linhas ou polígonos, ou seja, os arquivos não ficam misturados em um mesmo arquivo.

Objetos armazenados em shapefiles, normalmente, um conjunto de atributos associados, que descrevem o tipo de dado. Como atributo pode-se ter o nome, tipo, status, classe, tamanho, largura, etc.

#### Estrutura de um shapefile ####
Existem pelo menos três arquivos associados a um shapefile:

* **.shp**: é a extensão do formato de arquivo que contém a geometria para os objetos.
* **.shx**: é a extensão do formato de arquivo que indexa a geometria.
* **.dbf**: é a extensão do formato de arquivo que armazena os atributos dos objetos em um formato tabular.

Além destes arquivos, o shapefile poderá ter outros arquivos associados:

* **.prj**: é a extensão do formato de arquivo que contém informação sobre a projeção incluindo o sistema de coordenadas e informações sobre a projeção. É um arquivo descrevendo a projeção.
* **.sbn** e **.sbx**: os arquivos são o índice espacial dos objetos.
* **.shp.xml**: é o arquivo que contém os metadados em formato XML.

Estes arquivos necessitam ter o mesmo nome, por exemplo, **mapa.shp**, **mapa.shx**, **mapa.dbf**, e estarem armazenados no mesmo diretório para poderem ser lidos e abertos de acordo com a ferramenta que se está trabalhando, neste caso, Python.

#### Importando e lendo arquivos no formato shapefile ####
Todo o desenvolvimento de como trabalhar com esse tipo de arquivo será voltado para a linguagem Python, por isso, os meios para ler os arquivos serão referidos exatamente para Python.

Existem algumas maneiras de ler os arquivos shapefile com Python. Pode-se “fazer na mão”, ou seja, com um script próprio, ou através do uso das poderosas bibliotecas do Python. As bibliotecas mais populares para essa finalidade são Geopandas, Fiona, PyShp, Shapely, OGR. Eu, particularmente, prefiro Geopandas, o que não impede que as outras bibliotecas ou funções sejam utilizadas de forma conjunta, pois se existem várias é pela abrangência ou particularidade que cada uma possui.

#### Importando os dados ####
Como exemplo de base de dados em formato shapefile vamos usar dados que representam a distribuição de minas paralisadas no estado de Minas Gerais e as fronteiras do estado e dos municípios. Para tanto, faz-se o download dos arquivos de dados. Quem trabalha com Windows pode fazer da maneira tradicional e que usa Linux, basta um comando via terminal. Os dados serão baixados do Instituto Prístino que é uma pessoa jurídica de direito privado sem fins econômicos, criado para desenvolver pesquisas direcionadas em diagnóstico, conservação e uso racional do patrimônio natural.

Para quem usa Linux basta digitar na linha de comando:

<div style="width: 600px;">
 <a href="/assets/img/2020-07-24-P2-FIG_01_DLOAD.png"> <img src="/assets/img/2020-07-24-P2-FIG_01_DLOAD.png" width="580px"></a>
</div>

Uma vez realizado o download, é necessário que o arquivo seja descompactado. Para isso, basta ir ao diretório onde o arquivo foi armazenado e descompactá-lo com **unzip**:

<div style="width: 600px;">
 <a href="/assets/img/2020-07-24-P2-FIG_02_UNZIP.png"> <img src="/assets/img/2020-07-24-P2-FIG_02_UNZIP.png" width="580px"></a>
</div>

Verifique se tudo ocorreu de forma satisfatório com o comando **ls**. Os arquivos descompactados devem parecer como na figura.

<div style="width: 600px;">
 <a href="/assets/img/2020-07-24-P2-FIG_03_ls.png"> <img src="/assets/img/2020-07-24-P2-FIG_03_ls.png" width="580px"></a>
</div>

Como comentado anteriormente, são vários os arquivos com diferentes extensões. O arquivo **.dbf** contém as informações sobre os atributos e o arquivo com extensão **.prj** contém informações sobre o sistema de coordenadas.

Bom, por hoje ficamos por aqui. No próximo post finalizarei o estudo.

Grato pela leitura.
