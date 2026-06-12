---
title: "problema disco duro"
date: 2012-09-21
forum: Hardware
---

### Post by asterix77 on 2012-09-21
Estimados:

Tengo un pc de escritorio con windows y ubuntu 12.04, hace unos 2 meses aproximado empecé a tener problemas en el arranque. Iniciaba, prendía la pantalla, mostraba la bios, mostraba el grub, y al elegir windows o ubuntu, el pc se apagaba completamente. Al principio al segundo intento arrancaba bien, pero poco a poco tenía que reintentarlo más veces al punto que arrancar con windows me era imposible, de cada 8 a 10 intentos, uno funcionaba. Fui desconectando uno por uno cada dispositivo pero el problema persisitía (lector de dvd-tarjeta gráfica- otro disco duro-memoria). 

Me di cuenta que sacando una de las memorías (tengo 2 de un giga cada una), se "arreglaba" el problema, volví a uno de cada 2 ó 3 intentos. El sistema se tornó bastante lento y un poco inestable. En windows (cuando puedo ingresar), por lo general de improviso me pone la típica pantalla azul, con ubuntu es más estable, pero en un par de ocasiones se me ha congelado el sistema y he tenido que apagarla a la mala (no responde nada).

Ahora bien, se me ocurrió chequear el disco duro con gsmartcontrol y detectó un problema (gsmart1.jpg).

El log completo es:

Complete error log:

SMART Error Log Version: 1
ATA Error Count: 107 (device log contains only the most recent five errors)
    CR = Command Register [HEX]
    FR = Features Register [HEX]
    SC = Sector Count Register [HEX]
    SN = Sector Number Register [HEX]
    CL = Cylinder Low Register [HEX]
    CH = Cylinder High Register [HEX]
    DH = Device/Head Register [HEX]
    DC = Device Command Register [HEX]
    ER = Error register [HEX]
    ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 107 occurred at disk power-on lifetime: 8256 hours (344 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 f1 96 1b e6  Error: UNC at LBA = 0x061b96f1 = 102471409

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 06 f1 96 1b 06 0a      00:51:47.849  READ DMA
  ec 00 00 00 00 00 00 0a      00:51:47.840  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 0a      00:51:47.833  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 00 0a      00:51:47.825  IDENTIFY DEVICE
  c8 00 06 f1 96 1b 06 0a      00:51:44.356  READ DMA

Error 106 occurred at disk power-on lifetime: 8256 hours (344 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 f1 96 1b e6  Error: UNC at LBA = 0x061b96f1 = 102471409

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 06 f1 96 1b 06 0a      00:51:44.356  READ DMA
  ec 00 00 00 00 00 00 0a      00:51:44.347  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 0a      00:51:44.340  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 00 0a      00:51:44.334  IDENTIFY DEVICE
  c8 00 06 f1 96 1b 06 0a      00:51:40.860  READ DMA

Error 105 occurred at disk power-on lifetime: 8256 hours (344 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 f1 96 1b e6  Error: UNC at LBA = 0x061b96f1 = 102471409

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 06 f1 96 1b 06 0a      00:51:40.860  READ DMA
  ec 00 00 00 00 00 00 0a      00:51:40.851  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 0a      00:51:40.844  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 00 0a      00:51:40.836  IDENTIFY DEVICE
  c8 00 06 f1 96 1b 06 0a      00:51:37.627  READ DMA

Error 104 occurred at disk power-on lifetime: 8256 hours (344 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 f1 96 1b e6  Error: UNC at LBA = 0x061b96f1 = 102471409

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 06 f1 96 1b 06 0a      00:51:37.627  READ DMA
  ec 00 00 00 00 00 00 0a      00:51:37.618  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 0a      00:51:37.611  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 00 0a      00:51:37.603  IDENTIFY DEVICE
  c8 00 06 f1 96 1b 06 0a      00:51:34.134  READ DMA

Error 103 occurred at disk power-on lifetime: 8256 hours (344 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 f1 96 1b e6  Error: UNC at LBA = 0x061b96f1 = 102471409

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 06 f1 96 1b 06 0a      00:51:34.134  READ DMA
  ec 00 00 00 00 00 00 0a      00:51:34.125  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 0a      00:51:34.118  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 00 0a      00:51:34.113  IDENTIFY DEVICE
  c8 00 06 f1 96 1b 06 0a      00:51:30.641  READ DMA


Por su parte Gparted me arroja los siguiente:

Gparted 1
Gparted 2

El log completo es el siguiente:

[COLOR=#000000][FONT=Times New Roman]GParted 0.11.0 --enable-libparted-dmraid[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Libparted 2.3[/FONT][/COLOR]
**Verificar y reparar el sistema de archivos (ntfs) en /dev/sdc1**  00:00:00    ( ERROR )    calibrar /dev/sdc1  00:00:00    ( ÉXITO )    [I]ruta: /dev/sdc1
inicio: 63
fin: 204.796.619
tamaño: 204.796.557 (97.65 GiB)[/I]comprobar errores en el sistema de archivos en /dev/sdc1 y (si es posible) arreglarlos  00:00:00    ( ERROR )    ***ntfsresize -P -i -f -v /dev/sdc1***    [I]ntfsresize v2012.1.15AR.1 (libntfs-3g)
Device name : /dev/sdc1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 104855835136 bytes (104856 MB)
Current device size: 104855837184 bytes (104856 MB)
Checking for bad sectors ...
Bad cluster: 0xc372d6 - 0xc372d6 (1)
ERROR: This software has detected that the disk has at least 1 bad sector.
****************************************************************************
* WARNING: The disk has bad sector. This means physical damage on the disk *
* surface caused by deterioration, manufacturing faults or other reason. *
* The reliability of the disk may stay stable or degrade fast. We suggest *
* making a full backup urgently by running 'ntfsclone --rescue ...' then *
* run 'chkdsk /f /r' on Windows and rebooot it TWICE! Then you can resize *
* NTFS safely by additionally using the --bad-sectors option of ntfsresize.*
****************************************************************************
[/I][COLOR=#000000][FONT=Times New Roman]========================================[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Mi consulta es si mis problemas de reinicios se pueden deber a esto o no; mi problema aumenta ya que ni siquiera puedo respaldar mi información, intenté hacer un backup con clonzilla y no se puede, lo que mas me inquieta es la posible pérdida de información.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Por favor si alguien me puede dar algún comentario o sugerencia se lo agradecería.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Saludos
[/FONT][/COLOR]

---

### Post by hictio on 2012-09-21
Personalmente trataría de bootear con un CD o USB live, montar el disco rígido que decís que te está dando tantos problemas, copiá todo lo que puedas a un externo.
Después apagá, saca el disco que anda mal y re-emplazalo por uno nuevo.
Cuanto antes lo hagas, mejor.

---

### Post by asterix77 on 2012-09-24
Al final será lo mejor, y como indicas cuanto antes mejor.  Muchas gracias por tu comentario

Saludos

---

