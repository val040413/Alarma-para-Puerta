# Alarma-para-Puerta
Alarma para puerta con arduino
#include "LowPower.h"//Exportación de libreria para poner al arduino en modo sleep

int contacto=2;//Pin asignado al reed switch
int led=13;//Pin asignado al led
int bocina=12;//Pin asignado a la bocina

void setup() {
  pinMode (contacto, INPUT);//El reed switch como entrada
  pinMode(led, OUTPUT);//Led como salida
  pinMode(bocina,OUTPUT);//Bocina como salida

}

void loop() {
  LowPower.powerDown(SLEEP_FOREVER, ADC_OFF, BOD_OFF);//Pone a dormir al arduino
 if(digitalRead (contacto)==LOW){//Si el iman se acerca al reed switch
  digitalWrite(led,LOW);//El led se mantiene apagado
  digitalWrite(bocina,LOW);//La bocina se mantiene apagada
 }else{//Si el iman esta lejos del reed switch
  digitalWrite(led,HIGH);//Se enciende el led
  digitalWrite(bocina,HIGH);//Se enciende la bocina y activa la alarma
 }//Fin del if

}//Fin del programa
