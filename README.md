# Mutiplier-and-Display-7-FPGA-Dataflow-Modeling
Multiplicador e display de 7 segmentos usando modelagem por fluxo de dados (dataflow modeling) na ferramenta Quartus II da Altera.




## O código:

```verilog

module multiplicador (
						input [4:0] A,   // tem 5 bits
						output a1, b1, c1, d1, e1, f1, g1, a2, b2, c2, d2, e2, f2, g2, 
							   a3, b3, c3, d3, e3, f3, g3, a4, b4, c4, d4, e4, f4, g4 
						);
						   //o valor máximo de A é 31, e 31*3=93 , logo,
						   //o produto máximo também poderá ser mostrado nos displays.
wire [6:0]  seteSegmentos1,		
			seteSegmentos2,
			seteSegmentos3,
			seteSegmentos4;				


assign {seteSegmentos2, seteSegmentos1} = (A == 5'b00_000) ? {7'b1111_110, 7'b1111_110} :  //0
										  (A == 5'b00_001) ? {7'b1111_110, 7'b0110_000} :  //1
										  (A == 5'b00_010) ? {7'b1111_110, 7'b1101_101} :  //2
										  (A == 5'b00_011) ? {7'b1111_110, 7'b1111_001} :  //3
										  (A == 5'b00_100) ? {7'b1111_110, 7'b0110_011} :  //4
										  (A == 5'b00_101) ? {7'b1111_110, 7'b1011_011} :  //5
										  (A == 5'b00_110) ? {7'b1111_110, 7'b1011_111} :  //6
										  (A == 5'b00_111) ? {7'b1111_110, 7'b1110_000} :  //7
										  (A == 5'b01_000) ? {7'b1111_110, 7'b1111_111} :  //8
										  (A == 5'b01_001) ? {7'b1111_110, 7'b1111_011} :  //9
										  (A == 5'b01_010) ? {7'b0110_000, 7'b1111_110} :  //10
										  (A == 5'b01_011) ? {7'b0110_000, 7'b0110_000} :  //11
										  (A == 5'b01_100) ? {7'b0110_000, 7'b1101_101} :  //12
										  (A == 5'b01_101) ? {7'b0110_000, 7'b1111_001} :  //13
										  (A == 5'b01_110) ? {7'b0110_000, 7'b0110_011} :  //14
										  (A == 5'b01_111) ? {7'b0110_000, 7'b1011_011} :  //15
										  (A == 5'b10_000) ? {7'b0110_000, 7'b1011_111} :  //16
										  (A == 5'b10_001) ? {7'b0110_000, 7'b1110_000} :  //17
										  (A == 5'b10_010) ? {7'b0110_000, 7'b1111_111} :  //18
										  (A == 5'b10_011) ? {7'b0110_000, 7'b1111_011} :  //19
										  (A == 5'b10_100) ? {7'b1101_101, 7'b1111_110} :  //20
										  (A == 5'b10_101) ? {7'b1101_101, 7'b0110_000} :  //21
										  (A == 5'b10_110) ? {7'b1101_101, 7'b1101_101} :  //22
										  (A == 5'b10_111) ? {7'b1101_101, 7'b1111_001} :  //23
										  (A == 5'b11_000) ? {7'b1101_101, 7'b0110_011} :  //24
										  (A == 5'b11_001) ? {7'b1101_101, 7'b1011_011} :  //25
										  (A == 5'b11_010) ? {7'b1101_101, 7'b1011_111} :  //26
										  (A == 5'b11_011) ? {7'b1101_101, 7'b1110_000} :  //27
										  (A == 5'b11_100) ? {7'b1101_101, 7'b1111_111} :  //28
										  (A == 5'b11_101) ? {7'b1101_101, 7'b1111_011} :  //29
										  (A == 5'b11_110) ? {7'b1111_001, 7'b1111_110} :  //30
										  (A == 5'b11_111) ? {7'b1111_001, 7'b0110_000} :  //31
										  {7'b0000_000, 7'b0000_000};  
										  
										  

assign {a2, b2, c2, d2, e2, f2, g2, a1, b1, c1, d1, e1, f1, g1} = {seteSegmentos2, seteSegmentos1};



assign {seteSegmentos4, seteSegmentos3} = (A == 5'b00_000) ? {7'b1111_110, 7'b1111_110} :  //0
										  (A == 5'b00_001) ? {7'b1111_110, 7'b1111_001} :  //3
										  (A == 5'b00_010) ? {7'b1111_110, 7'b1011_111} :  //6
										  (A == 5'b00_011) ? {7'b1111_110, 7'b1111_011} :  //9
										  (A == 5'b00_100) ? {7'b0110_000, 7'b1101_101} :  //12
										  (A == 5'b00_101) ? {7'b0110_000, 7'b1011_011} :  //15
										  (A == 5'b00_110) ? {7'b0110_000, 7'b1111_111} :  //18
										  (A == 5'b00_111) ? {7'b1101_101, 7'b0110_000} :  //21
										  (A == 5'b01_000) ? {7'b1101_101, 7'b0110_011} :  //24
										  (A == 5'b01_001) ? {7'b1101_101, 7'b1110_000} :  //27
										  (A == 5'b01_010) ? {7'b1111_001, 7'b1111_110} :  //30
										  (A == 5'b01_011) ? {7'b1111_001, 7'b1111_001} :  //33
										  (A == 5'b01_100) ? {7'b1111_001, 7'b1011_111} :  //36
										  (A == 5'b01_101) ? {7'b1111_001, 7'b1111_011} :  //39
										  (A == 5'b01_110) ? {7'b0110_011, 7'b1101_101} :  //42
										  (A == 5'b01_111) ? {7'b0110_011, 7'b1011_011} :  //45
										  (A == 5'b10_000) ? {7'b0110_011, 7'b1111_111} :  //48
										  (A == 5'b10_001) ? {7'b1011_011, 7'b0110_000} :  //51
										  (A == 5'b10_010) ? {7'b1011_011, 7'b0110_011} :  //54
										  (A == 5'b10_011) ? {7'b1011_011, 7'b1110_000} :  //57
										  (A == 5'b10_100) ? {7'b1011_111, 7'b1111_110} :  //60
										  (A == 5'b10_101) ? {7'b1011_111, 7'b1111_001} :  //63
										  (A == 5'b10_110) ? {7'b1011_111, 7'b1011_111} :  //66
										  (A == 5'b10_111) ? {7'b1011_111, 7'b1111_011} :  //69
										  (A == 5'b11_000) ? {7'b1110_000, 7'b1101_101} :  //72
										  (A == 5'b11_001) ? {7'b1110_000, 7'b1011_011} :  //75
										  (A == 5'b11_010) ? {7'b1110_000, 7'b1111_111} :  //78
										  (A == 5'b11_011) ? {7'b1111_111, 7'b0110_000} :  //81
										  (A == 5'b11_100) ? {7'b1111_111, 7'b0110_011} :  //84
										  (A == 5'b11_101) ? {7'b1111_111, 7'b1110_000} :  //87
										  (A == 5'b11_110) ? {7'b1111_011, 7'b1111_110} :  //90
										  (A == 5'b11_111) ? {7'b1111_011, 7'b1111_001} :  //93
										  {7'b0000_000, 7'b0000_000};  
										  
										  

assign {a4, b4, c4, d4, e4, f4, g4, a3, b3, c3, d3, e3, f3, g3} = {seteSegmentos4, seteSegmentos3};

endmodule   



```



## Algumas observações:

 * Tentei fazer um código que se mantivesse na modelagem por fluxo de dados.
 * A entrada tem 5 dígitos, logo seu valor máximo de entrada é 31 (11111).
 * 31*3 = 93
 * O produto do valor máximo poderá ser apresentado nos seus devidos dois displays de 7 segmentos.
 * É na função de controle de fluxo que se verifica a correspondência do número binário pelo seu respectivo valor decimal, sendo esse valor decimal expresso em termos dos leds do display.
 * Há duas funções de controle de fluxo: uma serve para a representar o valor de entrada em 2 displays e a outra é para representar o produto em outros 2 displays. Usa-se, assim, os 4 displays de 7 segmentos que o FPGA Ciclone II contém. 


## Detalhe:

 * Neste código, os números 6 e 9 são representado por 6 segmentos ligados e 1 segmento desligado.
 * Antes de chegar a esse projeto, eu fiz um [projeto teste](https://github.com/thiago-aguilar1/Testando-7-segmentos-FPGA-Data-Flow), no qual eu simulo a forma de onda de um projeto com uma entrada de apenas 2 bits, e a saída apresentada em dois displays de 7 segmentos, um display para mostrar o valor de entrada, e o outro para mostrar o valor do produto da entrada por 2.  


![Imagem da forma de onda](https://github.com/thiago-aguilar1/Mutiplier-and-Display-7-FPGA-Dataflow-Modeling/blob/main/image.png)

![Imagem do final da forma de onda](https://github.com/thiago-aguilar1/Mutiplier-and-Display-7-FPGA-Dataflow-Modeling/blob/main/Captura%20de%20Tela%20(4975).png)





