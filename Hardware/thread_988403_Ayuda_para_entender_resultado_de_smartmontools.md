---
title: "Ayuda para entender resultado de smartmontools"
date: 2008-11-20
forum: Hardware
---

### Post by chulelinux on 2008-11-20
Hola gente, Ando con el disco duro jodido,le pase el long test y me arroja esto y no se bien que hacer... Será necesario un formateo de baja? Gracias por cualquier ayuda...Dejo las características del disco y abajo el resultado del test a ver si me pueden dar una mano... Saludos
=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.10 family
Device Model:     ST3250410AS
Serial Number:    5RY01JC2
Firmware Version: 3.AAA
User Capacity:    250.059.350.016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu Nov 20 12:30:34 2008 ARST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Interrupted (host reset)      90%      4589         -
# 2  Short offline       Completed: read failure       90%      4578         524476
# 3  Extended offline    Interrupted (host reset)      90%      4578         -
# 4  Short offline       Interrupted (host reset)      90%      4578         -
# 5  Short offline       Interrupted (host reset)      90%      4573         -
# 6  Short offline       Interrupted (host reset)      90%      4573         -
# 7  Short offline       Interrupted (host reset)      90%      4573         -
# 8  Short offline       Interrupted (host reset)      90%      4572         -
# 9  Short offline       Interrupted (host reset)      90%      4572         -
#10  Short offline       Interrupted (host reset)      90%      4572         -
#11  Short offline       Interrupted (host reset)      90%      4572         -
#12  Short offline       Completed without error       00%      3396         -
#13  Short offline       Completed without error       00%      3392         -
#14  Short offline       Completed without error       00%      3373         -
#15  Short offline       Completed without error       00%      3373         -

---

### Post by guillermolisi on 2008-11-20
La ultima columna, llamada LBA_of_first_error, te marca en que sector se produjo un incidente.
Como lo interpreto y por la cantidad de distintos sectores, algunos repetidos, no confiaria en el disco asi como esta.
Un buen analisis de superficie que te permita remapear pistas dañadas, para no perder capacidad util del disco, seria lo mejor.

De ultima, poder determinar si el disco se esta degradando y amerita un cambio urgente o son fallas que ya estaban ahi cuando lo pusiste en marcha (de fabrica).

Sea como sea, backup urgente, "por si las moscas".

---

### Post by chulelinux on 2008-11-20
Gracias Guillermo por la respuesta... Hoy termine de backapear todo porque tardaba, calculo por los sectores defectuosos, una bocha... Y me costó un perú para poder iniciarlo con un cd live o lo que sea... Esa info era ya habiendo backapeado y formateado todo... (pude seguir andando porque tengo otro disco por suerte) 

¿Qué buen programa puedo usar desde Ubuntu para remapear el disco y analizarlo? (hace poco que empecé con el genial mundo linux y no conozco los recovecos todavía je je. Ese p disco tenía el "ventanas" justamente)

---

### Post by guillermolisi on 2008-11-21
> **chulelinux said:**
> Gracias Guillermo por la respuesta... Hoy termine de backapear todo porque tardaba, calculo por los sectores defectuosos, una bocha... Y me costó un perú para poder iniciarlo con un cd live o lo que sea... Esa info era ya habiendo backapeado y formateado todo... (pude seguir andando porque tengo otro disco por suerte) 

¿Qué buen programa puedo usar desde Ubuntu para remapear el disco y analizarlo? (hace poco que empecé con el genial mundo linux y no conozco los recovecos todavía je je. Ese p disco tenía el "ventanas" justamente)

En realidad no creo que necesites algun programa especial para esto ya que este remapeo deberia realizarlo el utilitario que formatea y deja listo el file system en la particion (por ejemplo mkfs.ext3).

Hasta ahora con Linux no he tenido problemas de esta clase, si me ha pasado de que el disco presente inconvenientes desde el inicio (suelo usar WD SATA y WD/Seagate SCSI).

Considera que este remapeo de pistas malas, si bien mantiene la capacidad del disco, impacta negativamente en el rendimiento general del sistema, sobre todo en actividades disco intensivas.

---

### Post by chulelinux on 2008-11-26
Por suerte pude bajar toda la info que tenía.... y lamentablemente me parece que tuvo una vida muy corta este disco (un año) dado que le pasé de todo y no reacciona más que para tirar errores....
Gracias por la ayuda...

---

