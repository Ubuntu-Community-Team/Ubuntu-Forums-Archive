---
title: "Xubuntu HH - GRUB Error 25 - No inicia mas"
date: 2010-06-13
forum: Hardware
---

### Post by sergiom99 on 2010-06-13
Hola gente,
tengo una PIII, que funcionaba perfecto con Xubuntu 8.10 LTS, que la tengo en el escritorio para bajar cosas y demas.
El asunto es que hoy la quise usar y no despertaba. Pense que se habria colgado o algo y la resetee.
Cuando inicia, en vez de entrar al GRUB tira un mensaje:
> 
GRUB Loading Stage2.......

[Minimal BASH - Like line editing is supported.For the first word,TAB lists possible comman completions.Anywhere else TAB lists the possible completions of device/filename.]

GRUB>

Busque un poco y parece que lo indicado es hacer
1. ```
find /grub/stage2
find /boot/grub/stage2
```
para ver donde esta el GRUB y luego
2. ```
setup (hdX)
``` con la particion donde estaria el GRUB.

Bueno, el paso 1 me da "Error 15 File not found" y el 2 si lo hago con hd0, me devuelve "ERROR 25: Disk read error"

Como sigo?
Murio el disco?

En esta maquina, muerte de disco = muerte de CPU, porque los IDE estan mas caros que cualquier SATA actualmente.

Saludos/ Sergio

---

### Post by guillermolisi on 2010-06-13
Si podes iniciarla con un live CD y desde ahi corre fsck para revisar el disco y/o verificar si esta fusilado o aun sigue con vida :)

De que capacidad es el disco ?

---

### Post by sergiom99 on 2010-06-16
Gracias Guille, lo voy a probar el fin de semana.

---

### Post by sergiom99 on 2010-06-22
Hola gente,
les comento que lo probe con un LiveCD de Xubuntu 8.04 y no logre arrancarla.
Me va tirando 
```

[542.11234] ata2.00: Status: { DRDY ERR }
[542.11234] ata2.00: error: { UNC }
[542.11234] ata2.00: DMDMA stat 0x64

```
y asi sucesivamente.

Pense en bootearlo solo con consola, pero no encontre una opcion para hacerlo desde el LiveCD.

Y ahora?

Tengo dos discos IDE Maxtor, uno de 10 gb y otro de 40 Gb. El muerto es el de 10, donde estaba el OS y el otro es el /home.

---

### Post by guillermolisi on 2010-06-22
> **sergiom99 said:**
> Hola gente,
les comento que lo probe con un LiveCD de Xubuntu 8.04 y no logre arrancarla.
Me va tirando 
```

[542.11234] ata2.00: Status: { DRDY ERR }
[542.11234] ata2.00: error: { UNC }
[542.11234] ata2.00: DMDMA stat 0x64

```y asi sucesivamente.

Pense en bootearlo solo con consola, pero no encontre una opcion para hacerlo desde el LiveCD.

Y ahora?

Tengo dos discos IDE Maxtor, uno de 10 gb y otro de 40 Gb. El muerto es el de 10, donde estaba el OS y el otro es el /home.
Hace una instalacion limpia usando el de 40Gb como home asi recuperas el contenido. Cambiar la maquina te va a salir mas dinero que conseguir un disco IDE de 10/20 o 40Gb.

---

### Post by sergiom99 on 2010-06-24
Listo. Cambie el HDD, instale Xubuntu LL (Que esta buenisimo BTW) y quedo andando nuevamente como antes.

Antes de eso, probe todas las utilidades para discos del Hierens Boot CD y nada lo revivio.

Gracias Guille, abrazo.

---

