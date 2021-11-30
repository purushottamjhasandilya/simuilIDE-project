# simuilIDE-project
#define _XTAL_FREQ 8000000
// CONFIG
#pragma config OSC = IntRC_CLKOUTEN// Oscillator Selection bits (Internal RC oscillator/CLKOUT function on RB4/OSC2/CLKOUT pin)
#pragma config WDT = OFF // Watchdog Timer Enable bit (WDT disabled)
#pragma config CP = OFF // Code Protection bit (Code protection off)
#pragma config MCLRE = OFF // RB3/MCLR Pin Function Select bit (GP3/MCLR pin function is digital input, MCLR internally tied to VDD)
// #pragma config statements should precede project file includes.
// Use project enums instead of #define for ON and OFF.
 
#include <xc.h>

#include <stdlib.h>

#include <pic16f505.h>

int main()
{

TRISB = 0b000000 ; //RB1 as Output PIN
TRISC = 0b000000 ; // = 0;

int status=0;
__delay_ms(10);
/////////////////////////////////////////Initialising///////////////
RB0 = 1;                                                              //RED LED ON
__delay_ms(4000);                     // 4 Second Delay
RB0 = 0;
__delay_ms(10);

RC4=1 ;                                                            //UV RELAY ON (ON forever)
__delay_ms(10);

RB1 = 1;                                                          // YELLOW LED ON
__delay_ms(2500);                    // 2.5 Second Delay
RB1 = 0;
__delay_ms(10);
RB2 = 1;                                                          //GREEN LED ON
__delay_ms(2500); // 1.5 Second Delay
//////////////////////////////////////////////////////Initialisation complete followed by buzzer//////////////////////
                          ////////////BUZZER BEEP PATTERN //////////
RC3 = 1;
__delay_ms(500);
RC3 = 0;
__delay_ms(100);
RC3 = 1;
__delay_ms(200);
RC3 = 0;
__delay_ms(100);
RC3 = 1;
__delay_ms(200);
RC3 = 0;

                               ////////////////BUZZER BEEPS DONE/////////
 

while(1) // Keep machine on
{
RB2 = 1;                                                           //GREEN LED ON
RC4=1 ;                                                            //UV RELAY ON (ON forever)
}

return 0;
}
