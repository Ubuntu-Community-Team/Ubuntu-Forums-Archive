---
title: "pregunta"
date: 2008-11-08
forum: Hardware
---

### Post by francosp on 2008-11-08
hola tengo dos problemas:
1)  la temperatura de mi laptop(acer aspire) sube  en muy poco tiempo y se apaga,el cooler funciona correctamente, me dijeron que puede ser una funcion q ocupa 100%id 


2) me baje el driver  para el atheros ar5007eg que es de 64 bit (mi placa wifi es de 64 bits) y el ndiwrapper pero no funciona, me baje un controlador (kwifimanager) y me dice que no hay interface y esta desactivado

por la dudas si preguntan tengo el ubuntu 8.04(hardy), nucleo linux 2.6.24-21-genreic, gnome 2.22.3



desde ya gracias

---

### Post by hictio on 2008-11-08
#1-
Fijate de abrir un Terminal (Applications -> Accessories -> Terminal), maxificalo a pantalla completa, y tipea:
```

top (ENTER)

```

Vas a ver los procesos ejecutandose listados por el uso de CPU. Para terminarlo, apreta la tecla 'q'.
Ahi vas a ver cual es el proceso que esta usando todo el CPU, postealo aca para ver que pasa.

#2-

Fijate esta pagina: [Atheros AR5007 wireless with madwifi on Ubuntu 8.04 (Hardy heron)](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)
Yo tengo tu misma WiFi, pero en una Compaq F700, y en Hardy no pude hacerla funcionar, lamentablemente.
Es decir, despues del driver, y de las instrucciones, etc, la tarjeta andaba, pero no me pude conectar a ningun Access Point, sin importar que tipo de seguridad tuvieran setteado (o si tuvieran o no).

---

### Post by francosp on 2008-11-09
esto me aparecio 
 

top - 03:51:16 up 9 min,  2 users,  load average: 1.07, 0.76, 0.37
Tasks: 113 total,   2 running, 111 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.0%us,  1.3%sy,  0.0%ni, 97.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1019404k total,  1011652k used,     7752k free,   192780k buffers
Swap:   976552k total,    39232k used,   937320k free,   341548k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
 5398 root      20   0  443m  54m 7964 S  1.3  5.5   0:08.98 Xorg                                                                                            
    1 root      20   0  4020  884  600 S  0.0  0.1   0:00.86 init                                                                                            
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                                                        
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                     
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0                                                                                     
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                                      
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 events/0                                                                                        
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                                                         
   39 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0                                                                                       
   42 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                                          
   43 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                                                    
  127 root      15  -5     0    0    0 S  0.0  0.0   0:00.08 kseriod                                                                                         
  169 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                         
  170 root      20   0     0    0    0 S  0.0  0.0   0:00.02 pdflush                                                                                         
  171 root      15  -5     0    0    0 S  0.0  0.0   0:00.10 kswapd0                                                                                         
  214 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                                           
 1480 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                                                   
 1483 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                                           
 1533 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 ata/0                                                                                           
 1536 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                                                         
 2276 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 scsi_eh_0                                                                                       
 2278 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1                                                                                       
 2312 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2                                                                                       
 2313 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_3                                                                                       
 2535 root      20   0 16380 1360  608 S  0.0  0.1   0:07.34 mount.ntfs                                                                                      
 2556 root       0 -20     0    0    0 S  0.0  0.0   0:00.34 loop0                                                                                           
 2571 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                                                                                       
 2770 root      16  -4 17184 1300  384 S  0.0  0.1   0:00.28 udevd                                                                                           
 3167 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused                                                                                       
 4099 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ntos_wq                                                                                         
 4101 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ndis_wq                                                                                         
 4103 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 wrapndis_wq                                                                                     
 4562 root      20   0  3864  596  500 S  0.0  0.1   0:00.00 getty                                                                                           
 4563 root      20   0  3864  592  500 S  0.0  0.1   0:00.00 getty

---

### Post by hictio on 2008-11-09
No se ve nada raro para una maquina que esta prendida hace 10 minutos, Xorg es el que se encarga de la parte mas baja de todo el ambiente grafico de Ubuntu.

Como sabes que la temperatura sube de forma desproporcionada en la laptop (ademas de darte cuenta por el tacto :D )?

Un proceso que es especialmente maldito en terminos de uso de CPU es el '[scrollkeeper](http://en.wikipedia.org/wiki/ScrollKeeper)', en desktop que es una batata se come el CPU como si fuera chocolatines.

Dejala andando un rato mas a ver si aparece otro proceso que use mas CPU, fijila el output de top especialmente cuando notas que la temperatura esta alta.

Aca hay un output de mi top:
```

top - 04:41:01 up 2 days,  3:29,  5 users,  load average: 0.29, 0.17, 0.14
Tasks: 113 total,   2 running, 111 sleeping,   0 stopped,   0 zombie
Cpu(s):  7.6%us,  3.7%sy,  0.0%ni, 88.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    903012k total,   873812k used,    29200k free,    95480k buffers
Swap:   995988k total,     4736k used,   991252k free,   331412k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
22830 root      20   0 90220  48m  11m S  2.3  5.5   9:45.60 Xorg               
25128 esteban   20   0  109m  28m  14m R  2.0  3.2   0:16.98 gnome-terminal     
23131 esteban   20   0 21348 5700 4228 S  0.7  0.6   0:28.92 gnome-screensav    
24897 esteban   20   0  214m 105m  28m S  0.7 12.0  12:56.81 firefox            
23139 esteban   20   0 55604  30m  11m S  0.3  3.5   2:08.21 compiz.real        
    1 root      20   0  3056 1948  628 S  0.0  0.2   0:01.34 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:06.46 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:03.86 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0      
   48 root      15  -5     0    0    0 S  0.0  0.0   0:00.40 kblockd/0          
   50 root      15  -5     0    0    0 S  0.0  0.0   0:00.68 kacpid             
   51 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 kacpi_notify       
  145 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue             

```

---

