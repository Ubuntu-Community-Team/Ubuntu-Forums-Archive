---
title: "Desaparición de Particiones en Disco Duro URGENTE"
date: 2010-12-12
forum: Hardware
---

### Post by felipeleven on 2010-12-12
Hola a todos:

Junto con saludar quería contarle mi problema:

Hoy usando un live cd de Ubuntu 10.04, usando gparted, estuve redimensionando y moviendo algunas particiones del disco duro, a mitad de proceso, gparted lanzo un error y dejó de hacer los procesos. Al revisar las particiones, vi que habían desaparecido todas.
La única forma que tengo para acceder al disco duro es desde el live cd.

Alguien que me pudiera ayudar a recuperar las particiones junto a la información de esta.

Particiones:

2 particiones primarios ( C y D de windows), y una lógica (dentro de la lógica 2 adicionales comunes, una de swap y otra /)

Agradezco de antemano la ayuda, saludos !!!:confused:

---

### Post by RafaelG on 2010-12-13
felipeleven,

Tengo entendido que con Testdisk puede recuperar particiones perdidas. Dejo link de la documentacion oficial en Ubuntu lamentablemente la documentacion que consegui esta en ingles pero googleando puedes conseguir varios How to en espanol.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Saludos,

---

### Post by felipeleven on 2010-12-13
Hola Rafael G:

Primero que nada te agradezco la respuesta, te cuento que pude resolver el problema usando precisamente Testdisk, lo instalé desde el live cd de ubuntu 10.04, habilitando primero que nada los repositorios universe y multiverse, una vez hecho eso hice un "sudo apt-get install testdisk" y posteriormente con privilegios de administrador lo ejecute desde consola y siguiente la documentación de su página oficial pude recuperar las particiones.
Posteriormente usé Super Grub disk para reparar el arranque.

Eso, saludos y gracias por la ayuda ;):KS

---

### Post by felipeleven on 2010-12-13
Dejo el link del tutorial que ocupé:

[http://www.cgsecurity.org/wiki/TestDisk_Paso_A_Paso]("http://www.cgsecurity.org/wiki/TestDisk_Paso_A_Paso")

---

