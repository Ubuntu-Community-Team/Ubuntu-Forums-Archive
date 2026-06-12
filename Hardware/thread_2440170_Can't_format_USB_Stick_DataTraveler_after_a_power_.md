---
title: "Can't format USB Stick DataTraveler after a power loss"
date: 2020-04-06
forum: Hardware
---

### Post by cocaybica on 2020-04-06
Hi,

After a loss of power I can't format my 16Gb sub stick. Using Disk utility I'm getting this message:

"Error deleting partition /dev/sdc1: Failed to read partition table on device '/dev/sdc' (Invalid partition table on /dev/sdc --wrong signature b1b1.) (udisks-error-quark, 0)"

```
fdisk -l
Disco /dev/loop0: 93,8 MiB, 98336768 bytes, 192064 sectores
Unidades: sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico/físico): 512 bytes / 512 bytes
Tamaño de E/S (mínimo/óptimo): 512 bytes / 512 bytes




Disco /dev/loop1: 48,3 MiB, 50642944 bytes, 98912 sectores
Unidades: sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico/físico): 512 bytes / 512 bytes
Tamaño de E/S (mínimo/óptimo): 512 bytes / 512 bytes




Disco /dev/loop2: 4,26 MiB, 4464640 bytes, 8720 sectores
Unidades: sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico/físico): 512 bytes / 512 bytes
Tamaño de E/S (mínimo/óptimo): 512 bytes / 512 bytes




Disco /dev/loop3: 54,97 MiB, 57614336 bytes, 112528 sectores
Unidades: sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico/físico): 512 bytes / 512 bytes
Tamaño de E/S (mínimo/óptimo): 512 bytes / 512 bytes




Disco /dev/loop4: 13,92 MiB, 14569472 bytes, 28456 sectores
Unidades: sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico/físico): 512 bytes / 512 bytes
Tamaño de E/S (mínimo/óptimo): 512 bytes / 512 bytes




Disco /dev/loop5: 91,38 MiB, 95805440 bytes, 187120 sectores
Unidades: sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico/físico): 512 bytes / 512 bytes
Tamaño de E/S (mínimo/óptimo): 512 bytes / 512 bytes




Disco /dev/loop6: 12,89 MiB, 13496320 bytes, 26360 sectores
Unidades: sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico/físico): 512 bytes / 512 bytes
Tamaño de E/S (mínimo/óptimo): 512 bytes / 512 bytes




Disco /dev/loop7: 3,66 MiB, 3825664 bytes, 7472 sectores
Unidades: sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico/físico): 512 bytes / 512 bytes
Tamaño de E/S (mínimo/óptimo): 512 bytes / 512 bytes








Disco /dev/sda: 465,78 GiB, 500107862016 bytes, 976773168 sectores
Disk model: WDC WD5000AAKS-0
Unidades: sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico/físico): 512 bytes / 512 bytes
Tamaño de E/S (mínimo/óptimo): 512 bytes / 512 bytes
Tipo de etiqueta de disco: dos
Identificador del disco: 0x58404473


Dispositivo Inicio Comienzo     Final  Sectores Tamaño Id Tipo
/dev/sda1              2048 976773119 976771072 465,8G  7 HPFS/NTFS/exFAT




Disco /dev/sdb: 931,53 GiB, 1000204886016 bytes, 1953525168 sectores
Disk model: WDC WD10EZEX-00B
Unidades: sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico/físico): 512 bytes / 4096 bytes
Tamaño de E/S (mínimo/óptimo): 4096 bytes / 4096 bytes
Tipo de etiqueta de disco: dos
Identificador del disco: 0x000580e9


Dispositivo Inicio  Comienzo      Final   Sectores Tamaño Id Tipo
/dev/sdb1   *           2048  421032127  421030080 200,8G  7 HPFS/NTFS/exFAT
/dev/sdb2          421033984  422842367    1808384   883M 27 NTFS de WinRE ocult
/dev/sdb3          422844414  843614207  420769794 200,7G  5 Extendida
/dev/sdb4          843614208 1953519615 1109905408 529,3G  7 HPFS/NTFS/exFAT
/dev/sdb5          422844416  618153983  195309568  93,1G 83 Linux
/dev/sdb6          618156032  835796991  217640960 103,8G 83 Linux
/dev/sdb7          835801088  843614207    7813120   3,7G 82 Linux swap / Solari


La partición 3 no empieza en el límite del sector físico.
Las entradas de la tabla de particiones no están en el orden del disco.




Disco /dev/loop8: 140,68 MiB, 147501056 bytes, 288088 sectores
Unidades: sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico/físico): 512 bytes / 512 bytes
Tamaño de E/S (mínimo/óptimo): 512 bytes / 512 bytes




Disco /dev/loop9: 181,8 MiB, 189870080 bytes, 370840 sectores
Unidades: sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico/físico): 512 bytes / 512 bytes
Tamaño de E/S (mínimo/óptimo): 512 bytes / 512 bytes




Disco /dev/loop10: 193,2 MiB, 202395648 bytes, 395304 sectores
Unidades: sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico/físico): 512 bytes / 512 bytes
Tamaño de E/S (mínimo/óptimo): 512 bytes / 512 bytes




Disco /dev/loop11: 9,7 MiB, 9510912 bytes, 18576 sectores
Unidades: sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico/físico): 512 bytes / 512 bytes
Tamaño de E/S (mínimo/óptimo): 512 bytes / 512 bytes




Disco /dev/loop12: 163,68 MiB, 171618304 bytes, 335192 sectores
Unidades: sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico/físico): 512 bytes / 512 bytes
Tamaño de E/S (mínimo/óptimo): 512 bytes / 512 bytes




Disco /dev/loop13: 140,68 MiB, 147501056 bytes, 288088 sectores
Unidades: sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico/físico): 512 bytes / 512 bytes
Tamaño de E/S (mínimo/óptimo): 512 bytes / 512 bytes




Disco /dev/loop14: 193,2 MiB, 202395648 bytes, 395304 sectores
Unidades: sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico/físico): 512 bytes / 512 bytes
Tamaño de E/S (mínimo/óptimo): 512 bytes / 512 bytes




Disco /dev/loop15: 14,77 MiB, 15466496 bytes, 30208 sectores
Unidades: sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico/físico): 512 bytes / 512 bytes
Tamaño de E/S (mínimo/óptimo): 512 bytes / 512 bytes




Disco /dev/loop16: 3,7 MiB, 3862528 bytes, 7544 sectores
Unidades: sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico/físico): 512 bytes / 512 bytes
Tamaño de E/S (mínimo/óptimo): 512 bytes / 512 bytes




Disco /dev/loop17: 156,7 MiB, 164290560 bytes, 320880 sectores
Unidades: sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico/físico): 512 bytes / 512 bytes
Tamaño de E/S (mínimo/óptimo): 512 bytes / 512 bytes




Disco /dev/loop18: 14,76 MiB, 15462400 bytes, 30200 sectores
Unidades: sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico/físico): 512 bytes / 512 bytes
Tamaño de E/S (mínimo/óptimo): 512 bytes / 512 bytes




Disco /dev/loop19: 956 KiB, 978944 bytes, 1912 sectores
Unidades: sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico/físico): 512 bytes / 512 bytes
Tamaño de E/S (mínimo/óptimo): 512 bytes / 512 bytes




Disco /dev/loop20: 44,9 MiB, 47063040 bytes, 91920 sectores
Unidades: sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico/físico): 512 bytes / 512 bytes
Tamaño de E/S (mínimo/óptimo): 512 bytes / 512 bytes




Disco /dev/loop21: 956 KiB, 978944 bytes, 1912 sectores
Unidades: sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico/físico): 512 bytes / 512 bytes
Tamaño de E/S (mínimo/óptimo): 512 bytes / 512 bytes




Disco /dev/loop22: 197,26 MiB, 206839808 bytes, 403984 sectores
Unidades: sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico/físico): 512 bytes / 512 bytes
Tamaño de E/S (mínimo/óptimo): 512 bytes / 512 bytes




Disco /dev/loop23: 160,16 MiB, 167931904 bytes, 327992 sectores
Unidades: sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico/físico): 512 bytes / 512 bytes
Tamaño de E/S (mínimo/óptimo): 512 bytes / 512 bytes




Disco /dev/loop24: 54,66 MiB, 57294848 bytes, 111904 sectores
Unidades: sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico/físico): 512 bytes / 512 bytes
Tamaño de E/S (mínimo/óptimo): 512 bytes / 512 bytes




Disco /dev/loop25: 9,7 MiB, 9506816 bytes, 18568 sectores
Unidades: sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico/físico): 512 bytes / 512 bytes
Tamaño de E/S (mínimo/óptimo): 512 bytes / 512 bytes




Disco /dev/loop26: 4,2 MiB, 4403200 bytes, 8600 sectores
Unidades: sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico/físico): 512 bytes / 512 bytes
Tamaño de E/S (mínimo/óptimo): 512 bytes / 512 bytes




No se tienen en cuenta los datos adicionales de la tabla de particiones 5.
No se tienen en cuenta los datos adicionales de la tabla de particiones 5.
No se tienen en cuenta los datos adicionales de la tabla de particiones 5.
El indicador 0xb1b1 no válido de EBR (para la partición 5) se corregirá mediante w(rite).
Disco /dev/sdc: 14,45 GiB, 15500574720 bytes, 30274560 sectores
Disk model: DataTraveler 2.0
Unidades: sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico/físico): 512 bytes / 512 bytes
Tamaño de E/S (mínimo/óptimo): 512 bytes / 512 bytes
Tipo de etiqueta de disco: dos
Identificador del disco: 0x4cac7ff1


Dispositivo Inicio   Comienzo      Final   Sectores Tamaño Id Tipo
/dev/sdc1   *            2048   16002047   16000000   7,6G 83 Linux
/dev/sdc2            16003070   30273535   14270466   6,8G  5 Extendida
/dev/sdc5          2677171250 5877315203 3200143954   1,5T 12 Compaq diagnostics

```

I'm lost here.

---

### Post by yancek on 2020-04-06
Since you are planning to format the usb and thus overwrite any data on it and based on the error you report, have you tried creating a new partition table since the current one is invalid?

---

### Post by cocaybica on 2020-04-06
Thanks.

I tried GParted-> Select /dev/sdc/ Device -> Create New Partition Table (msdos) and then I'm getting this popup message.

"Wrong Partition table on /dev/sdc -- invalid signature b1b1."

---

### Post by cocaybica on 2020-04-06
Trying again some times I'm getting Input/Output errors while writing /dev/sdc. Dead USB Stick?

---

### Post by CelticWarrior on 2020-04-07
Yes, dead USB stick.

---

### Post by sudodus on 2020-04-07
Before giving up on the USB stick you can analyze the problem and try again according to [this link](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035)

---

### Post by cocaybica on 2020-04-07
Ok,

I tried mkusb with "Restore to a Standard storage device" option, I had an error, and after that, using Disk utility, the pendrive is detected like a Generic USB Mass Storage with no more options and GParted doesn't see it.

---

### Post by sudodus on 2020-04-08
> **CelticWarrior said:**
> Yes, dead USB stick.

> **cocaybica said:**
> Ok,

I tried mkusb with "Restore to a Standard storage device" option, I had an error, and after that, using Disk utility, the pendrive is detected like a Generic USB Mass Storage with no more options and GParted doesn't see it.

After this 'extra effort' by you I am afraid the the USB stick is damaged beyond repair. @CelticWarrior is right about that.

---

### Post by cocaybica on 2020-04-08
Ok. Thanks!

---

