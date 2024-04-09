# M480BSP_CALIBRATE_LIRC_BY_HIRC
 M480BSP_CALIBRATE_LIRC_BY_HIRC

udpate @ 2024/04/09

1. Due to LIRC have wide range (5K~20K) , which may not same as 10K 

- concept : use HIRC to calirbate LIRC counter before TIMER entry interrupt

2. use TIMER2 (w/ HIRC clock source) , set with 1 Hz (1 sec) interupt and get target TIMER counter (ex : TIMER1)

3. set TIMER1 (w/ LIRC clock source) , set CMP with MAX CMP , and wait for TIMER2 interrupt to get TIMER1 counter

and use the counter to initial TIMER1 interrupt , execute GPIO toggle

4. below is TIMER1 interrupt GPIO toggle WHEN LIRC IS NOT 10K 

![image](https://github.com/released/M480BSP_CALIBRATE_LIRC_BY_HIRC/blob/main/before_calirbate_LIRC.jpg)

below is TIMER1 interrupt GPIO toggle when use counter get by TIMER2 1Hz interrupt

![image](https://github.com/released/M480BSP_CALIBRATE_LIRC_BY_HIRC/blob/main/after_calirbate_LIRC.jpg)


5. below is log message WHEN LIRC IS NOT 10K , with function : TIMER1_Init_API

![image](https://github.com/released/M480BSP_CALIBRATE_LIRC_BY_HIRC/blob/main/log_LIRC_NG.jpg)

below is log message when LIRC is 10K , with function : TIMER1_Init_API

![image](https://github.com/released/M480BSP_CALIBRATE_LIRC_BY_HIRC/blob/main/log_LIRC_OK.jpg)

6. below is log message WHEN LIRC IS NOT 10K , with function : TIMER1_Init_Specific_PSC

![image](https://github.com/released/M480BSP_CALIBRATE_LIRC_BY_HIRC/blob/main/log_LIRC_NG_specific_psc.jpg)

below is log message when LIRC is 10K , with function : TIMER1_Init_Specific_PSC

![image](https://github.com/released/M480BSP_CALIBRATE_LIRC_BY_HIRC/blob/main/log_LIRC_OK_specific_psc.jpg)

