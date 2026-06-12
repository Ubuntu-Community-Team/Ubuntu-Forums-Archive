---
title: "[SOLVED] Dual Boot"
date: 2008-12-24
forum: Hardware
---

### Post by Vero1 on 2008-12-24
Hola,

Tengo el siguiente problema.

Tengo dos discos. En uno(el mas grande) instalé Ubuntu 8.10. En el otro tambien tenía Ubuntu 8.10. Decidí instalar en este último Windows XP para uso familiar.

Instalé XP pero desapareció el Grub. Lo recuperé con SuperGrubDisk, pero ahora en el Grub no me aparece Windows y sigue apareciendo el Ubuntu que eliminé.

He leído y me han dicho que para que el Grub me muestre ambos SO, primero había que instalar Windows y despues Ubuntu.

Pregunto: hay alguna forma de arreglar ésto sin tener que desinstalar todo y volver a instalar?

Desde ya gracias a los que me orienten.

saludos

---

### Post by KrossX on 2008-12-24
[COLOR="Navy"]Sí, teniendo instalado Windows, en la instalación de Ubuntu el sistema de Debian detecta la instalación y configura GRUB para múltiples OS.

De [caljohnsmith](http://ubuntuforums.org/showpost.php?p=6404943&postcount=5):[/COLOR]
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
[COLOR="Navy"]Eso descarga y ejecuta un script que permite ver la información sobre los OS instalados.
Se crea una archivo "boot_info_results.txt" con la información. Copia y pega la información en tu siguiente post.

**#EDIT:** Siempre es recomandable no andar ejecutando scripts que encuentras por ahí. Si quieres puedes simplemente decargarlo, mirarlo para ver que hace y luego decidir si ejecutarlo o no.

**#Disclaimer:** use-at-thy-own-risk[/COLOR]

---

### Post by Vero1 on 2008-12-24
Hola y gracias por contestar.

Si yo hago un fdsk -l, sale lo siguiente:

Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x2b2e2b2d

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        9542    76646083+  83  Linux
/dev/sda2            9543        9729     1502077+   5  Extendida
/dev/sda5            9543        9729     1502046   82  Linux swap / Solaris

Disco /dev/sdb: 41.1 GB, 41110142976 bytes
255 cabezas, 63 sectores/pista, 4998 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x4f744f74

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *           1        4811    38644326    7  HPFS/NTFS
/dev/sdb2            4812        4998     1502077+   5  Extendida
/dev/sdb5            4812        4998     1502046    7  HPFS/NTFS


por lo tanto windows está instalado tambien pero no se puede bootear.

Lo que hice, entretanto, fue eliminar del menu.lst el ubuntu que figuraba y
agregar Windows XP. Salir sale en el boot pero cuando le hago click informa que no lo puede leer.

Ahora pregunto: Si se cambian en el menu.lst los lugares, serviría de algo? o hacer alguna otra cosa?

O sea, ahora en primer lugar está ubuntu y en segundo windows.

Gracias

---

### Post by KrossX on 2008-12-24
[COLOR="Navy"]Falta información, usa el script mencionado.

El orden en GRUB es sólo estético, no funcional.[/COLOR]

---

### Post by Vero1 on 2008-12-24
Me contesta esto:

bash: cd: /home/veronica/Desktop: No existe el fichero ó directorio

saludos

---

### Post by KrossX on 2008-12-24
[COLOR="Navy"]Que raro, será cosa del idioma quizá.[/COLOR]

```
wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
[COLOR="Navy"]
Ve al escritorio con la consola (aunque estando sólo en HOME está bien) y usa el code sin la parte del "cd". El archivo "boot_info_results.txt" con los resultados se crea donde está el script, así que no hay problema.[/COLOR]

---

### Post by Vero1 on 2008-12-24
Hola,

Te agradezco pero ya se arregló.

Me indicaron agregar unas lineas al menu.lst y bootear desde hda0,0 y dió resultado :-)

A vos, muchas gracias por tu tiempo.

Feliz Navidad

---

