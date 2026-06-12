---
title: "Imposible montar pendrive ( u otros ) en Hardy"
date: 2008-06-26
forum: Hardware
---

### Post by Apipote on 2008-06-26
A alguien le pasa que no se puede montar, ni los pendrives, maquinas de fotos, ni mp3 en los Usb con Hardy?

Como lo solucionaron?

Gracias.

---

### Post by Hei Ku on 2008-06-26
No tuve ningun problema. Probaste a poner dmesg en la consola, a ver que aparece cuando metes el pen drive?

---

### Post by tzulberti on 2008-06-27
Que mensaje te aparece cuando los queres montar?

---

### Post by faktorqm on 2008-06-27
A mi lo que me pasó es que conectaba el pendrive y... ¡no pasaba nada! entonces (con el pendrive todavia conectado) fui a la terminal y escribi "lsusb" para ver si aunque sea lo estaba viendo y cuando termino de darme la salida (el linux lo estaba "viendo") agarró y me lo montó solo como si nada hubiera pasado. El problema? ni idea! La verdad que HH trajo mil mejoras pero con eso vinieron algunos bugcitos... y bue, todo no se puede! :D Salu2!

---

### Post by Apipote on 2008-06-27
Es rarísimo, e igual que a muchos que he leido en inglés. Se ve que soy el primero que lo publica.

Nunca les paso ???

Si enchufo el pendrive por el Live cd...no hay problema, pero luego de la instalación...no monta el Kingston de 4 gb. Lo ve...pero no lo monta.

Me pasó en Xubuntu y Ubuntu x86.

Xubuntu me dice luego de enchufarlo:

Failed to mount "KINGSTON".

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so.

Que hago masters ??

---

### Post by faktorqm on 2008-06-27
Yo lo que haría es intentar montarlo a mano, para eso lo unico que tenes que saber es a donde esta la "carpeta" digamos. un comando tentativo seria el siguiente:

```

sudo mkdir -p /media/pendrive
sudo mount -t vfat /dev/sdd /media/pendrive

```

donde /dev/sdd es tu pendrive. En mi caso es asi digamos, capaz en el tuyo no, por eso te digo que es lo unico que tendrias que cambiar. Salu2!

---

