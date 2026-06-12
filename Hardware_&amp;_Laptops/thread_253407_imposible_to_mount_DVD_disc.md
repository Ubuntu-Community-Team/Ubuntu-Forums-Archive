---
title: "imposible to mount DVD disc"
date: 2006-09-08
forum: Hardware &amp; Laptops
---

### Post by el_itur on 2006-09-08
Hi everyone.
I'm a happy ubuntu user since march this year.
Although I'm a latin user I have found that spanish comunity isn't as active as this is. I've been on this forum for a long time looking for answers and I've seen a better support. So thanks in advantage for any help you could give me, and keep on hard and good work!! :).

Well the problem that brings me here, I know, it's very frecuent in ubuntu users. But none of the solutions posted stisfied me. I don't want to reinstall my Ubuntu nor change my dvd reader.
I've plugged it in a WinXP system and it works fine when reading. It has problems when writing but thats another.

This is my fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       /media/sda5     ntfs    umask=0         0       0
/dev/sda4       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,auto     0       0
``` 

this is the message the system gives me when I try to mount the device
```

mount: dispositivo de bloques /dev/hda está protegido contra escritura; se monta como sólo lectura

mount: tipo de sistema de ficheros incorrecto, opción incorrecta,

       superbloque incorrecto en /dev/hda, falta la página de códigos,

       o algún otro error

       en algunos casos se encuentra información en syslog, pruebe

   dmesg | tail   o algo parecido

```

If you want I'll try to translate that message but in ressume it say that device is not possible to mount and "try dmesg | tail or sonmething" (textual)

well I have, and this is the message 
```

[17246060.856000] hda: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[17246061.040000] hda: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[17246062.908000] hda: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[17246063.092000] hda: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[17246064.960000] hda: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[17246065.152000] hda: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[17246067.012000] hda: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[17246067.204000] hda: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[17246069.064000] hda: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[17246069.264000] hda: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
```

Is all the information I have.
I have installed all the DVD libraries around. 
Any information that you could give me helps me. So thanks in advantage.

Bye.

---

