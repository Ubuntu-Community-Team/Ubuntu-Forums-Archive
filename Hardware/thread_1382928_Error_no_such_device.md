---
title: "Error: no such device"
date: 2010-01-16
forum: Hardware
---

### Post by Iced1 on 2010-01-16
Hace unos dias al arrancar el notebook y entrar al grub2 en ubuntu 9.10 y selecionar el windows xp en este caso, me sale este error:

Error: No such device (y varios numeros y letras)

No le he tomado mucha atencion porque en esta semana aprendi vastante sobre ubuntu y tengo el notebook funcionando apunto con este sistema operativo y trato de difundirlo a mis amigos y familiares.

Pero ayer necesitaba entrar a windows, bueno siempre es bueno tenerlo instalado, pero desde adentro de ubuntu al intentar entrar a la particion de windows, sale en blanco... es vastante extraño, ojala alguien sepa mas o menos que es, bueno gracias, y bye.

---

### Post by Carlos C on 2010-01-17
Hola. Creo que lo primero es ver cómo tienes particionado el disco. Por favor escribe en el terminal:
```
sudo fdisk -l
```También puedes aprovechar de ver la información que te da ntfsinfo:
```
sudo ntfsinfo -m [device]
```"[device]" lo reemplazas por la ruta de tu partición, la verás con fdisk y será del tipo "/dev/sda1". Lo otro que puedes hacer es correr ntfsfix:
```
sudo ntfsfix [device]
```Saludos.

---

### Post by Iced1 on 2010-01-17
Gracias por contestarme y tratar de ayudarme :P

Aqui esta lo que me dio fdisk

Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xd0000000

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       18779    99643162+   f  W95 Ext'd (LBA)
/dev/sda5            6375       16101    78132096    7  HPFS/NTFS
/dev/sda6           16102       18533    19535008+  83  Linux
/dev/sda7           18534       18779     1975963+  82  Linux swap / Solaris

voy a seguir intentando con los otros comandos ya que me dice command not found quisas los estoy escribiendo mal...

---

### Post by Carlos C on 2010-01-17
> **Iced1 said:**
> 

voy a seguir intentando con los otros comandos ya que me dice command not found quisas los estoy escribiendo mal...
Ese es el problema, tienes que instalar el paquete ntfsprogs:
```
sudo aptitude install ntfsprogs
```
Saludos.

---

### Post by Iced1 on 2010-01-20
Hola, muchas gracias por tu ayuda Carlos C pero aun asi instalando esos paquetes no se arregla, creo que me voy a dar por vencido, vi en el monitor de sistemas, la particion y la de 48 gb de windows que tenia usado como 30gb ahora solo sale en 16kb de uso, creo que se borraron y no se por que.... espero que no pase de nuevo.

---

### Post by Carlos C on 2010-01-20
Hola, creo que antes de que te des por vencido debes darnos todos los datos, porque aún no sé qué ocurrió luego de instalar ese paquete. ¿Volviste a intentar los comandos que te di? ¿cuál fue el resultado? El pauqte era para que ejecutaras los comandos, no para que se arreglara el problema.

"Command not found" significa que el comando no existe, algo que no es posible si instalaste el paquete ntfsprogs, por lo tanto el resultado debe haber cambiado.

---

### Post by Iced1 on 2010-01-20
Disculpa aun asi es raro que salga que no ahy nada en el disco, aqui estan los resultados de los comandos:

/dev/sda1 * 1 6374 51199123+ 7 HPFS/NTFS

sudo ntfsinfo -m /dev/sda1
Failed to startup volume: Argumento inválido.
Failed to mount '/dev/sda1': Argumento inválido.
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
Failed to open '/dev/sda1'.

sudo ntfsfix /dev/sda1
Mounting volume... Failed to startup volume: Invalid argument.
FAILED

Attempting to correct errors... FAILED
Failed to startup volume: Invalid argument.
Volume is corrupt. You should run chkdsk.

/dev/sda5 6375 16101 78132096 7 HPFS/NTFS

sudo ntfsinfo -m /dev/sda5
Volume Information 
    Name of device: /dev/sda5
    Device state: 11
    Volume Name: 
    Volume State: 1
    Volume Version: 3.1
    Sector Size: 512
    Cluster Size: 4096
    Volume Size in Clusters: 19533023
MFT Information 
    MFT Record Size: 1024
    MFT Zone Multiplier: 1
    MFT Data Position: 24
    MFT Zone Start: 786432
    MFT Zone End: 3228059
    MFT Zone Position: 786432
    Current Position in First Data Zone: 3228059
    Current Position in Second Data Zone: 0
    LCN of Data Attribute for FILE_MFT: 786432
    FILE_MFTMirr Size: 4
    LCN of Data Attribute for File_MFTMirr: 13135141
    Size of Attribute Definition Table: 2560
FILE_Bitmap Information 
    FILE_Bitmap MFT Record Number: 6
    State of FILE_Bitmap Inode: 0
    Length of Attribute List: 0
    Attribute List: (null)
    Number of Attached Extent Inodes: 0
FILE_Bitmap Data Attribute Information
    Decompressed Runlist: not done yet
    Base Inode: 6
    Attribute Types: not done yet
    Attribute Name Length: 0
    Attribute State: 3
    Attribute Allocated Size: 2445312
    Attribute Data Size: 2441632
    Attribute Initialized Size: 2441632
    Attribute Compressed Size: 0
    Compression Block Size: 0
    Compression Block Size Bits: 0
    Compression Block Clusters: 0

sudo ntfsfix /dev/sda5
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
NTFS partition /dev/sda5 was processed successfully.

esas son las infos de las particiones ntfs...

---

### Post by picknick on 2010-03-06
Buenas! Veo que el thread estuvo inactivo mucho tiempo. A mi me pasa algo semejante. Tenía win7 y ubuntu conviviendo en armonía. Instalé Vbox y decidí borrar la partición de Recovery de windows para alojar los disco duros de Vbox allí, así que use Gparted y formatee la partición recovery como Fat32 y había una pequeña partición que también la eliminé. No recuerdo si eran NTFS. La información de la partición de win la tengo intacta, de hecho, monto la de win cada vez que la necesito.

Esto es lo que me devuelven los comandos.

Disco /dev/sda: 320.1 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xb63575e1

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1               1        1917    15398271    b  W95 FAT32
/dev/sda3            1918       32303   244071289+   7  HPFS/NTFS
/dev/sda4           32304       38913    53094825    5  Extendida
/dev/sda5           32304       33397     8787523+  82  Linux swap / Solaris
/dev/sda6           33398       33410      104391   83  Linux
/dev/sda7           33411       35355    15623181   83  Linux
/dev/sda8           35356       38913    28579603+  83  Linux


Volume Information 
    Name of device: /dev/sda3
    Device state: 11
    Volume Name: OS
    Volume State: 1
    Volume Version: 3.1
    Sector Size: 512
    Cluster Size: 4096
    Volume Size in Clusters: 61017821
MFT Information 
    MFT Record Size: 1024
    MFT Zone Multiplier: 1
    MFT Data Position: 24
    MFT Zone Start: 786432
    MFT Zone End: 8413659
    MFT Zone Position: 786432
    Current Position in First Data Zone: 8413659
    Current Position in Second Data Zone: 0
    LCN of Data Attribute for FILE_MFT: 786432
    FILE_MFTMirr Size: 4
    LCN of Data Attribute for File_MFTMirr: 5631999
    Size of Attribute Definition Table: 2560
FILE_Bitmap Information 
    FILE_Bitmap MFT Record Number: 6
    State of FILE_Bitmap Inode: 0
    Length of Attribute List: 0
    Attribute List: (null)
    Number of Attached Extent Inodes: 0
FILE_Bitmap Data Attribute Information
    Decompressed Runlist: not done yet
    Base Inode: 6
    Attribute Types: not done yet
    Attribute Name Length: 0
    Attribute State: 3
    Attribute Allocated Size: 7630848
    Attribute Data Size: 7627232
    Attribute Initialized Size: 7627232
    Attribute Compressed Size: 0
    Compression Block Size: 0
    Compression Block Size Bits: 0
    Compression Block Clusters: 0

Espero que me puedan ayudar.

Saludos

---

