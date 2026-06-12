---
title: "Expulsión de cds: la bandeja se cierra automáticamente antes de que pueda sacar el di"
date: 2009-07-19
forum: Hardware
---

### Post by anagramagia on 2009-07-19
Estoy usando Kubuntu 8.10 32bits, en una pc (AMD Athlon 64 X2 Dual Core Processor 5200+, 2GB RAM). La regrabadora de cd y dvd es PIONEER DVD-RW DVR-216D.

El problema es el siguiente: pongo un cd cualquiera, cuando lo quiero sacar empleo alguna de las formas usuales (más abajo especifico) pero unos poquísimos segundos después, la bandeja se cierra sola. Algunas veces, en las que no me muevo con suficiente rapidez, el disco queda adentro.  Esto no sucedía con Ubuntu 8.04.

Quisiera que la bandeja del cd-dvd no se cierre automáticamente, si no cuando yo presione el botón. ¿Cómo se puede configurar?

Formas en que desmonto los cds (todas con el mismo resultado):
*Desde Dolphin: en el panel de places que está a la izquierda hago click con el botón derecho del mouse sobre el nombre que identifica al cd y en el menú emergente selecciono expulsar.
*Desde la línea de comandos con umount (umount /media/cdrom0) y con eject (simplemente eject)
*Desde el notificador de nuevos dispositivos (click en el ícono de eyectar que se muestra a la derecha del nombre del disp.)
*Desde KDiskFree (click con botón derecho sobre el nombre del dispositivo y click en la opción desmontar).

Por si sirve de algo, esta es la información relativa al uso de sr0 cuando pongo un cd (obtenida de dmesg):

[ 6460.347064] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK                                                                                     
[ 6460.347072] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current]                     
[ 6460.347076] Info fld=0x4c980                                                         
[ 6460.347077] sr 3:0:0:0: [sr0] Add. Sense: CIRC unrecovered error                     
[ 6460.347083] end_request: I/O error, dev sr0, sector 1254912                          
[ 6460.347088] Buffer I/O error on device sr0, logical block 313728                     
[ 6461.099994] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK                                                                                     
[ 6461.100002] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current]                     
[ 6461.100006] Info fld=0x4c980                                                         
[ 6461.100008] sr 3:0:0:0: [sr0] Add. Sense: CIRC unrecovered error                     
[ 6461.100012] end_request: I/O error, dev sr0, sector 1254912                          
[ 6461.100016] Buffer I/O error on device sr0, logical block 313728                     
[ 6461.681692] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK                                                                                     
[ 6461.681701] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current]                     
[ 6461.681705] Info fld=0x4c980                                                         
[ 6461.681708] sr 3:0:0:0: [sr0] Add. Sense: CIRC unrecovered error                     
[ 6461.681711] end_request: I/O error, dev sr0, sector 1254912                          
[ 6461.681716] Buffer I/O error on device sr0, logical block 313728                     
[ 6461.900587] end_request: I/O error, dev sr0, sector 978144                           
[ 6461.900595] Buffer I/O error on device sr0, logical block 244536                     
[ 6462.007069] end_request: I/O error, dev sr0, sector 978148                           
[ 6462.007075] Buffer I/O error on device sr0, logical block 244537                     
[ 6462.347144] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK                                                                                     
[ 6462.347151] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current]                     
[ 6462.347156] Info fld=0x4c980                                                         
[ 6462.347158] sr 3:0:0:0: [sr0] Add. Sense: CIRC unrecovered error                     
[ 6462.347162] end_request: I/O error, dev sr0, sector 1254912                          
[ 6462.347166] Buffer I/O error on device sr0, logical block 313728                     
[ 6462.648391] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK                                                                                     
[ 6462.648398] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current]                     
[ 6462.648402] Info fld=0x4c980                                                         
[ 6462.648405] sr 3:0:0:0: [sr0] Add. Sense: CIRC unrecovered error                     
[ 6462.648408] end_request: I/O error, dev sr0, sector 1254912                          
[ 6462.648413] Buffer I/O error on device sr0, logical block 313728                     
[ 6462.818639] end_request: I/O error, dev sr0, sector 978144                           
[ 6462.818647] Buffer I/O error on device sr0, logical block 244536                     
[ 6462.818650] Buffer I/O error on device sr0, logical block 244537                     
[ 6463.281290] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK                                                                                     
[ 6463.281298] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current]                     
[ 6463.281302] Info fld=0x4c980                                                         
[ 6463.281305] sr 3:0:0:0: [sr0] Add. Sense: CIRC unrecovered error
[ 6463.281309] end_request: I/O error, dev sr0, sector 1254912
[ 6463.281313] Buffer I/O error on device sr0, logical block 313728
[ 6463.582492] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6463.582499] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current]
[ 6463.582503] Info fld=0x4c980
[ 6463.582505] sr 3:0:0:0: [sr0] Add. Sense: CIRC unrecovered error
[ 6463.582509] end_request: I/O error, dev sr0, sector 1254912
[ 6464.239032] end_request: I/O error, dev sr0, sector 1254908
[ 6464.486457] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6464.486467] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current]
[ 6464.486472] Info fld=0x4c980
[ 6464.486473] sr 3:0:0:0: [sr0] Add. Sense: CIRC unrecovered error
[ 6464.486477] end_request: I/O error, dev sr0, sector 1254912
[ 6464.787794] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6464.787801] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current]
[ 6464.787806] Info fld=0x4c980
[ 6464.787807] sr 3:0:0:0: [sr0] Add. Sense: CIRC unrecovered error
[ 6464.787811] end_request: I/O error, dev sr0, sector 1254912

---

### Post by SLA_leandrin on 2009-07-19
Que pasa si ponés simplemente

```
sudo eject dvd
```

Pregunto porque yo alguna vez con el mismo problema lo solucioné así... (Importante hacerlo con el sudo)

---

### Post by anagramagia on 2009-07-22
No sé, lo voy a probar. Pero de todos modos ¿no sabés en dónde se configura este asunto de la expulsión de cds?

Saludos.

---

### Post by GGsalas on 2010-08-31
> **SLA_leandrin said:**
> Que pasa si ponés simplemente

```
sudo eject dvd
```

Pregunto porque yo alguna vez con el mismo problema lo solucioné así... (Importante hacerlo con el sudo)

Muchas gracias, pude solucionar el problema. Espero que más adelante no sea necesario ;)

---

