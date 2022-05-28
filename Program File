#include <LiquidCrystal.h>

LiquidCrystal lcd_1(13, 12, 11, 9, 1, 0);


const int LED_VERMELHO = 8;

const int BOTAO = 10;
const int pino1 = A5;
const int pino2 = A4;
const int pino3 = A3;
const int pino4 = A2;
const int pino5 = A1;
const int pino6 = A0;
const int pino7 = 2;
const int pino8 = 3;
const int pino9 = 4;
const int pino10 = 5;
const int pino11 = 6;
const int pino12 = 7;

int state_button = 0;

void setup(){
  pinMode(LED_VERMELHO, OUTPUT);
  pinMode(BOTAO, INPUT);
  
  lcd_1.begin(16, 2);
  
  lcd_1.print("Inicializado");
}

void loop(){
  
  int butao_estado = digitalRead(BOTAO);
  

     
  if (butao_estado == 0){
   	state_button = 0;
  }
    
  if (butao_estado == 1 && !state_button){
    state_button = 1;
    
    delay(1000);
    
    testa_ci_7474();
    
    testa_ci_pinagem_igual();
    
    testa_ci_pinagem_igual();
    
    testa_ci_7402();
    
    testa_ci_7404();
       
  }
  delay(50);
}

//Função para testar a tabela verdade dos CIs que possuam 2 entradas e 1 saida
void tabela_verdade(int vetor[4], int pino_A, int pino_B, int pino_X){  
  digitalWrite(pino_A, LOW);
  digitalWrite(pino_B, LOW);
  vetor[0] = digitalRead(pino_X);
  
  digitalWrite(pino_A, LOW);
  digitalWrite(pino_B, HIGH);
  vetor[1] = digitalRead(pino_X);
  
  digitalWrite(pino_A, HIGH);
  digitalWrite(pino_B, LOW);
  vetor[2] = digitalRead(pino_X);
  
  digitalWrite(pino_A, HIGH);
  digitalWrite(pino_B, HIGH);
  vetor[3] = digitalRead(pino_X);
}

//DECLARANDO OS MODOS DOS PINOS DE PINAGEM IGUAL: 7408, 7432, 7400, 7486
void pinagem_igual(){
  pinMode(pino1, OUTPUT);
  pinMode(pino2, OUTPUT);
  pinMode(pino3, INPUT);
  pinMode(pino4, OUTPUT);
  pinMode(pino5, OUTPUT);
  pinMode(pino6, INPUT);
  pinMode(pino7, OUTPUT);
  pinMode(pino8, OUTPUT);
  pinMode(pino9, INPUT);
  pinMode(pino10, OUTPUT);
  pinMode(pino11, OUTPUT);
  pinMode(pino12, INPUT);
}

//FUNÇÃO PARA TESTES DOS CIs DE PINAGEM IGUAIS: 7408, 7432, 7400, 7486
void testa_ci_pinagem_igual(){
  
  pinagem_igual();
    
  int saida1[4];
  int saida2[4];
  int saida3[4];
  int saida4[4];
  
  tabela_verdade(saida1, pino1, pino2, pino3);
  tabela_verdade(saida2, pino4, pino5, pino6);
  tabela_verdade(saida3, pino7, pino8, pino9);
  tabela_verdade(saida4, pino10, pino11, pino12);
  
  //CI 7408
  
  if ((saida1[0]==0 and saida1[1]==0 and saida1[2]==0 and saida1[3]==1) 
  		or (saida2[0]==0 and saida2[1]==0 and saida2[2]==0 and saida2[3]==1)
     	or (saida3[0]==0 and saida3[1]==0 and saida3[2]==0 and saida3[3]==1)
      	or (saida4[0]==0 and saida4[1]==0 and saida4[2]==0 and saida4[3]==1)){
    
    //CI OK
    if ((saida1[0]==0 and saida1[1]==0 and saida1[2]==0 and saida1[3]==1) 
  		and (saida2[0]==0 and saida2[1]==0 and saida2[2]==0 and saida2[3]==1)
     	and (saida3[0]==0 and saida3[1]==0 and saida3[2]==0 and saida3[3]==1)
      	and (saida4[0]==0 and saida4[1]==0 and saida4[2]==0 and saida4[3]==1)){
    lcd_1.clear();
    lcd_1.print("7408 OK");
    }
    
    //CI com defeito
    else{
      digitalWrite(LED_VERMELHO, HIGH);
      if ((saida1[0]!=0) or (saida1[1]!=0) or (saida1[2]!=0) or (saida1[3]!=1)){
        lcd_1.clear();
        lcd_1.print("Porta 1 com defeito");
      } 
      if ((saida2[0]!=0) or (saida2[1]!=0) or (saida2[2]!=0) or (saida2[3]!=1)){
        lcd_1.clear();
        lcd_1.print("Porta 2 com defeito");
      }
     if ((saida3[0]!=0) or (saida3[1]!=0) or (saida3[2]!=0) or (saida3[3]!=1)){
        lcd_1.clear();
        lcd_1.print("Porta 4 com defeito");
      }
      if ((saida4[0]!=0) or (saida4[1]!=0) or (saida4[2]!=0) or (saida4[3]!=1)){
        lcd_1.clear();
        lcd_1.print("Porta 3 com defeito");
      }
    }
  }
  
  // CI 7432
  else if ((saida1[0]==0 and saida1[1]==1 and saida1[2]==1 and saida1[3]==1) 
    	or (saida2[0]==0 and saida2[1]==1 and saida2[2]==1 and saida2[3]==1)
     	or (saida3[0]==0 and saida3[1]==1 and saida3[2]==1 and saida3[3]==1)
      	or (saida4[0]==0 and saida4[1]==1 and saida4[2]==1 and saida4[3]==1)){
    
 	// CI OK  
     if ((saida1[0]==0 and saida1[1]==1 and saida1[2]==1 and saida1[3]==1) 
    	and (saida2[0]==0 and saida2[1]==1 and saida2[2]==1 and saida2[3]==1)
     	and (saida3[0]==0 and saida3[1]==1 and saida3[2]==1 and saida3[3]==1)
      	and (saida4[0]==0 and saida4[1]==1 and saida4[2]==1 and saida4[3]==1)){
        lcd_1.clear();
        lcd_1.print("7432 OK");
    }
    
    // CI com defeito
    else{
      digitalWrite(LED_VERMELHO, HIGH);
      if ((saida1[0]!=0) or (saida1[1]!=1) or (saida1[2]!=1) or (saida1[3]!=1)){
        lcd_1.clear();
        lcd_1.print("Porta 1 com defeito");
      } 
      if ((saida2[0]!=0) or (saida2[1]!=1) or (saida2[2]!=1) or (saida2[3]!=1)){
        lcd_1.clear();
        lcd_1.print("Porta 2 com defeito");
      }
      if ((saida3[0]!=0) or (saida3[1]!=1) or (saida3[2]!=1) or (saida3[3]!=1)){
        lcd_1.clear();
        lcd_1.print("Porta 4 com defeito");
      }
      if ((saida4[0]!=0) or (saida4[1]!=1) or (saida4[2]!=1) or (saida4[3]!=1)){
        lcd_1.clear();
        lcd_1.print("Porta 3 com defeito");
      }
    }     
  }
  
  // CI 7400
  else if ((saida1[0]==1 and saida1[1]==1 and saida1[2]==1 and saida1[3]==0) 
    	or (saida2[0]==1 and saida2[1]==1 and saida2[2]==1 and saida2[3]==0)
     	or (saida3[0]==1 and saida3[1]==1 and saida3[2]==1 and saida3[3]==0)
      	or (saida4[0]==1 and saida4[1]==1 and saida4[2]==1 and saida4[3]==0)){
    
    // CI OK
     if ((saida1[0]==1 and saida1[1]==1 and saida1[2]==1 and saida1[3]==0) 
    	and (saida2[0]==1 and saida2[1]==1 and saida2[2]==1 and saida2[3]==0)
     	and (saida3[0]==1 and saida3[1]==1 and saida3[2]==1 and saida3[3]==0)
      	and (saida4[0]==1 and saida4[1]==1 and saida4[2]==1 and saida4[3]==0)){
        lcd_1.clear();
        lcd_1.print("7400 OK");
    }
    
    //CI com defeito
    else{
      digitalWrite(LED_VERMELHO, HIGH);
      if ((saida1[0]!=1) or (saida1[1]!=1) or (saida1[2]!=1) or (saida1[3]!=0)){
        lcd_1.clear();
        lcd_1.print("Porta 1 com defeito");
      } 
      if ((saida2[0]!=1) or (saida2[1]!=1) or (saida2[2]!=1) or (saida2[3]!=0)){
        lcd_1.clear();
        lcd_1.print("Porta 2 com defeito");
      }
     if ((saida3[0]!=1) or (saida3[1]!=1) or (saida3[2]!=1) or (saida3[3]!=0)){
        lcd_1.clear();
        lcd_1.print("Porta 4 com defeito");
      }
      if ((saida4[0]!=1) or (saida4[1]!=1) or (saida4[2]!=1) or (saida4[3]!=0)){
        lcd_1.clear();
        lcd_1.print("Porta 3 com defeito");
      }
    }
  }
  
  // CI 7486
  else if ((saida1[0]==0 and saida1[1]==1 and saida1[2]==1 and saida1[3]==0) 
    	or (saida2[0]==0 and saida2[1]==1 and saida2[2]==1 and saida2[3]==0)
     	or (saida3[0]==0 and saida3[1]==1 and saida3[2]==1 and saida3[3]==0)
      	or (saida4[0]==0 and saida4[1]==1 and saida4[2]==1 and saida4[3]==0)){
    
     // CI OK
     if ((saida1[0]==0 and saida1[1]==1 and saida1[2]==1 and saida1[3]==0) 
    	and (saida2[0]==0 and saida2[1]==1 and saida2[2]==1 and saida2[3]==0)
     	and (saida3[0]==0 and saida3[1]==1 and saida3[2]==1 and saida3[3]==0)
      	and (saida4[0]==0 and saida4[1]==1 and saida4[2]==1 and saida4[3]==0)){
        lcd_1.clear();
        lcd_1.print("7486 OK");
    }
    
    //CI com defeito
    else{
      digitalWrite(LED_VERMELHO, HIGH);
      if ((saida1[0]!=0) or (saida1[1]!=1) or (saida1[2]!=1) or (saida1[3]!=0)){
        lcd_1.clear();
        lcd_1.print("Porta 1 com defeito");
      } 
      if ((saida2[0]!=0) or (saida2[1]!=1) or (saida2[2]!=1) or (saida2[3]!=0)){
        lcd_1.clear();
        lcd_1.print("Porta 2 com defeito");
      }
     if ((saida3[0]!=0) or (saida3[1]!=1) or (saida3[2]!=1) or (saida3[3]!=0)){
        lcd_1.clear();
        lcd_1.print("Porta 4 com defeito");
      }
      if ((saida4[0]!=0) or (saida4[1]!=1) or (saida4[2]!=1) or (saida4[3]!=0)){
        lcd_1.clear();
        lcd_1.print("Porta 3 com defeito");
      } 
    }
  }  
}

//DECLARANDO OS MODOS DOS PINOS DO CI 7402
void pinagem_7402(){
  pinMode(pino1, INPUT);
  pinMode(pino2, OUTPUT);
  pinMode(pino3, OUTPUT);
  pinMode(pino4, INPUT);
  pinMode(pino5, OUTPUT);
  pinMode(pino6, OUTPUT);
  pinMode(pino7, INPUT);
  pinMode(pino8, OUTPUT);
  pinMode(pino9, OUTPUT);
  pinMode(pino10, INPUT);
  pinMode(pino11, OUTPUT);
  pinMode(pino12, OUTPUT);
}

//FUNÇÃO DE TESTE DO CI 7402
void testa_ci_7402(){
  
  pinagem_7402();
  
  int saida1[4];
  int saida2[4];
  int saida3[4];
  int saida4[4];
  
  tabela_verdade(saida1, pino2, pino3, pino1);
  tabela_verdade(saida2, pino5, pino6, pino4);
  tabela_verdade(saida3, pino8, pino9, pino7);
  tabela_verdade(saida4, pino11, pino12, pino10);
  
  //CI 7402  
  if ((saida1[0]==1 and saida1[1]==0 and saida1[2]==0 and saida1[3]==0) 
  		or (saida2[0]==1 and saida2[1]==0 and saida2[2]==0 and saida2[3]==0)
     	or (saida3[0]==1 and saida3[1]==0 and saida3[2]==0 and saida3[3]==0)
      	or (saida4[0]==1 and saida4[1]==0 and saida4[2]==0 and saida4[3]==0)){
    
    //CI OK
    if ((saida1[0]==1 and saida1[1]==0 and saida1[2]==0 and saida1[3]==0) 
  		and (saida2[0]==1 and saida2[1]==0 and saida2[2]==0 and saida2[3]==0)
     	and (saida3[0]==1 and saida3[1]==0 and saida3[2]==0 and saida3[3]==0)
      	and (saida4[0]==1 and saida4[1]==0 and saida4[2]==0 and saida4[3]==0)){
        lcd_1.clear();
        lcd_1.print("7402 OK");
    }
    
    //CI com defeito
    else{
      digitalWrite(LED_VERMELHO, HIGH);
      if ((saida1[0]!=1) or (saida1[1]!=0) or (saida1[2]!=0) or (saida1[3]!=0)){
        lcd_1.clear();
        lcd_1.print("Porta 1 com defeito");
      } 
      if ((saida2[0]!=1) or (saida2[1]!=0) or (saida2[2]!=0) or (saida2[3]!=0)){
        lcd_1.clear();
        lcd_1.print("Porta 2 com defeito");
      }
     if ((saida3[0]!=1) or (saida3[1]!=0) or (saida3[2]!=0) or (saida3[3]!=0)){
        lcd_1.clear();
        lcd_1.print("Porta 4 com defeito");
      }
      if ((saida4[0]!=1) or (saida4[1]!=0) or (saida4[2]!=0) or (saida4[3]!=0)){
        lcd_1.clear();
        lcd_1.print("Porta 3 com defeito");
      }
    }
  }
}

// FUNÇÃO PARA TESTAR A TABELA VERDADE DO CI 7404
void tabela_verdade_7404(int vetor[2], int pino_A, int pino_X){  
  digitalWrite(pino_A, LOW);
  vetor[0] = digitalRead(pino_X);
  
  digitalWrite(pino_A, HIGH);
  vetor[1] = digitalRead(pino_X);
}

//DECLARANDO OS MODOS DOS PINOS DO CI 7402
void pinagem_7404(){
  pinMode(pino1, OUTPUT);
  pinMode(pino2, INPUT);
  pinMode(pino3, OUTPUT);
  pinMode(pino4, INPUT);
  pinMode(pino5, OUTPUT);
  pinMode(pino6, INPUT);
  pinMode(pino7, OUTPUT);
  pinMode(pino8, INPUT);
  pinMode(pino9, OUTPUT);
  pinMode(pino10, INPUT);
  pinMode(pino11, OUTPUT);
  pinMode(pino12, INPUT);
}

//FUNÇÃO DE TESTE DO CI 7404
void testa_ci_7404(){
  pinagem_7404();
  
  int saida1[2];
  int saida2[2];
  int saida3[2];
  int saida4[2];
  int saida5[2];
  int saida6[2];
  
  tabela_verdade_7404(saida1, pino1, pino2);
  tabela_verdade_7404(saida2, pino3, pino4);
  tabela_verdade_7404(saida3, pino5, pino6);
  tabela_verdade_7404(saida4, pino7, pino8);
  tabela_verdade_7404(saida5, pino9, pino10);
  tabela_verdade_7404(saida6, pino11, pino12);
  
  //7404  
  if ((saida1[0]==1 and saida1[1]==0) or (saida2[0]==1 and saida2[1]==0)
      or (saida3[0]==1 and saida3[1]==0) or (saida4[0]==1 and saida4[1]==0)
      or (saida5[0]==1 and saida5[1]==0) or (saida6[0]==1 and saida6[1]==0)){
    
    // CI OK
    if ((saida1[0]==1 and saida1[1]==0) and (saida2[0]==1 and saida2[1]==0)
      and (saida3[0]==1 and saida3[1]==0) and (saida4[0]==1 and saida4[1]==0)
      and (saida5[0]==1 and saida5[1]==0) and (saida6[0]==1 and saida6[1]==0)){
        lcd_1.clear();
        lcd_1.print("7404 OK");
      
    }  
    // CI com defeito
    else{
      digitalWrite(LED_VERMELHO, HIGH);
      if (saida1[0]!=1 or saida1[1]!=0){
        lcd_1.clear();
        lcd_1.print("Porta 1 com defeito");
      }
      if (saida2[0]!=1 or saida2[1]!=0){
        lcd_1.clear();
        lcd_1.print("Porta 2 com defeito");
      }
      if (saida3[0]!=1 or saida3[1]!=0){
        lcd_1.clear();
        lcd_1.print("Porta 3 com defeito");
      }
      if (saida4[0]!=1 or saida4[1]!=0){
        lcd_1.clear();
        lcd_1.print("Porta 6 com defeito");
      }
      if (saida5[0]!=1 or saida5[1]!=0){
        lcd_1.clear();
        lcd_1.print("Porta 5 com defeito");
      }
      if (saida6[0]!=1 or saida6[1]!=0){
        lcd_1.clear();
        lcd_1.print("Porta 4 com defeito");
      }
    }   
  }  
}

// TESTA O SET E RESET DO CI 7474
void testa_set_reset_7474(int vetor1[2], int vetor2[2], int reset, int dado, 
                        int clock, int set, int q_saida, int qn_saida){
  digitalWrite(set, LOW);
  digitalWrite(reset, HIGH);
  vetor1[0] = digitalRead(q_saida);
  vetor2[0] = digitalRead(qn_saida);
  
  digitalWrite(set, HIGH);
  digitalWrite(reset, LOW);
  vetor1[1] = digitalRead(q_saida);
  vetor2[1] = digitalRead(qn_saida);
}

// TESTA A TABELA VERDADE DO 7474
bool test_7474(int reset, int dado, int clock, int set, int q_saida, int qn_saida) {
  digitalWrite(set, LOW);
  digitalWrite(reset, HIGH);
  delay(1);
  if (!(digitalRead(q_saida) == 1 and digitalRead(qn_saida) == 0)) return false;
  
  digitalWrite(set, HIGH);
  digitalWrite(reset, LOW);
  delay(1);
  if (!(digitalRead(q_saida) == 0 and digitalRead(qn_saida) == 1)) return false;
  
  digitalWrite(set, HIGH);
  digitalWrite(reset, HIGH);
  digitalWrite(clock, LOW);
  delay(1);
  digitalWrite(dado, LOW);
  delay(1);
  digitalWrite(clock, HIGH);
  delay(1);
  if (!(digitalRead(q_saida) == 0 and digitalRead(qn_saida) == 1)) return false;
  
  digitalWrite(set, HIGH);
  digitalWrite(reset, HIGH);
  digitalWrite(clock, LOW);
  delay(1);
  digitalWrite(dado, HIGH);
  delay(1);
  digitalWrite(clock, HIGH);
  delay(1);
  if (!(digitalRead(q_saida) == 1 and digitalRead(qn_saida) == 0)) return false;
  
  return true;
}

//DECLARANDO OS MODOS DOS PINOS DO CI 7474
void pinagem_7474(){
  pinMode(pino1, OUTPUT);
  pinMode(pino2, OUTPUT);
  pinMode(pino3, OUTPUT);
  pinMode(pino4, OUTPUT);
  pinMode(pino5, INPUT);
  pinMode(pino6, INPUT);
  pinMode(pino7, OUTPUT);
  pinMode(pino8, OUTPUT);
  pinMode(pino9, OUTPUT);
  pinMode(pino10, OUTPUT);
  pinMode(pino11, INPUT);
  pinMode(pino12, INPUT);
}

//FUNÇÃO DE TESTE DO CI 7474
void testa_ci_7474(){
  
  pinagem_7474();
  
  int vetor1[2];
  int vetor2[2];
  int vetor3[2];
  int vetor4[2];
  
  testa_set_reset_7474(vetor1, vetor2, pino1, pino2, pino3, pino4, pino5, pino6); 
  testa_set_reset_7474(vetor3, vetor4, pino7, pino8, pino9, pino10, pino11, pino12);
  
  //7474
  if (((vetor1[0]==1 and vetor2[0]==0) and (vetor1[1]==0 and vetor2[1]==1)) 
      or ((vetor3[0]==1 and vetor4[0]==0) and (vetor3[1]==0 and vetor4[1]==1))){
    
    if (!test_7474(pino1, pino2, pino3, pino4, pino5, pino6)) {
        digitalWrite(LED_VERMELHO, HIGH);
        lcd_1.clear();
        lcd_1.print("FF 1 com defeito");
    }
    
    
    if (!test_7474(pino7, pino8, pino9, pino10, pino11, pino12)) {
        digitalWrite(LED_VERMELHO, HIGH);
        lcd_1.clear();
        lcd_1.print("FF 2 com defeito");
      
    }
    else {        
      lcd_1.clear();
      lcd_1.print("7474 OK");}
  }
}
