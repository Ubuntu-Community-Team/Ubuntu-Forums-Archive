---
title: "Problemas de instalacion de uBUNTU"
date: 2009-10-11
forum: Installation &amp; Upgrades
---

### Post by sebales on 2009-10-11
[SIZE=3][FONT=Times New Roman]Sres. les comento que he tenido inconvenientes para instalar algunas versiones de UBUNTU ( 8.04 / 8.10 / 9.04), les comento que compré un disco de 80 GB sólo para instalar este sistema operativo pero doy en la tecla...me bajé las versiones desde la página oficial (versión i386) y usando la comienzo a instalar configuro el idioma, configuro el teclado, elijo en que disco instalarlo y después al comenzar a instalar todo bien..pero aproximadamente al 25% comienzan los problemas ya que me arrojar un error en un archivo que según informa no se condice con el que se encuentra el CD-DVD, el tema es que te permite seguir con la instalación eligiendo la opción SKIP, pero al aparecer 40 veces con diferentes archivos sacarán sus conclusiones de que se termina instalando...no obstante la notificación del error plantea algunos posibles orígenes del error:[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]* Disco rígido roto[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]* Problemas al grabar el CD-DVD; el problema que menciona es la velocidad de grabado.[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]* Problemas de temperatura del disco, por lo que recomienda llevarlo a un lugar con diferente temperatura.[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]No obstante ya trabajé estas posibilidades ya que el disco está bien porque instalé otros sistemas operativos sin ningún tipo de problemas (Windows Colossus 2), la velocidad de grabación la trabajé grabando cada versión hasta con 4X y ni ahí.....Me pueden ayudar????[/FONT][/SIZE]

---

### Post by Partyboi2 on 2009-10-11
Hi, check that the [[COLOR=Blue]md5sum[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM") matches for the Ubuntu iso that you downloaded. If they match then check the cd you burnt, you can check it by choosing the option at the Main menu of the Live cd.

---

### Post by rreese6 on 2009-10-11
SI, parece que su archivo . el ISO esta mala. comparir com el MD5SUM en el sito para la version que tiene.
 Aquí están algunos pasos para ayudarle a determinar si todo es aceptable. Cheque del archivo de la ISO 1. cerciórese de que el archivo de la ISO tenga el MD5 correcto usted puede hacer eso en terminal. Cambie el directorio a donde la ISO entonces se localiza 
```
 md5sum ubuntu-x.xx.x.iso
```
 eso volverá una línea con a lo largo de número en la primera columna. compare que número al número encontrado en esta página para la ISO que usted está utilizando: [https://help.ubuntu.com/community/Ub...hes#8.04%20LTS](https://help.ubuntu.com/community/Ub...hes#8.04%20LTS) o si usted tiene uno de estos ISOs yo han incluido una lista aquí: ```
 371bd54267de6169a602bd1fafa2abfd *ubuntu-8.04.3-alternate-amd64.
iso 7a729db496ce2f8a84fb6f3927398066 *ubuntu-8.04.3-alternate-i386.iso 
d7ba336d05045aa60d1114da686e6359 *ubuntu-8.04.3-desktop-amd64.iso 
419b20ff1066f436dc9705fc09de9d3b *ubuntu-8.04.3-desktop-i386.iso 
```
2. Si la ISO es mala, transfiérala otra vez, después funcione con el paso antedicho otra vez. 
CHEQUE CD 
3. Ahora let' cheque de s usted copia de su CD Usted puede comprobar la integridad del CD sin la reanudación como sigue. ```
 md5sum /dev/cdrom
```
usted puede necesitar cambiar el " cdrom" a cdrom0 o a cdrom1 para hacerle el trabajo. compare esa salida a los números sobre o en el Web site le di. 
4. Si la ISO archiva es buena, pero el CD es malo: Queme el archivo de la ISO al CD usando 4x o 8x&#8230; tan lento como usted puede. 
5. Después de que usted haga una quemadura lenta, vuelva al paso 3 verificarlo. 
Cheque que si bueno o' no el CD 
6. Una vez que usted patea encima del CD, usted puede también funcionar el " Compruebe Media" CD; del menú&#8230; si éste pasa entonces usted sabe que usted tiene todo listo para instalar. Verifique que la computadora sea compatible con 8.04LTS 
7. Elija la primera opción (básicamente apenas golpeada entre cuando sube el menú) para intentar Ubuntu sin la instalación. (Operación de LiveCD). si esto trabaja, después usted puede apenas elegir instala de la mesa para terminar la instalación. la reinicialización 
8 y goza.

---

### Post by Rodart on 2009-10-12
> **sebales said:**
> [SIZE=3][FONT=Times New Roman]Sres. les comento que he tenido inconvenientes para instalar algunas versiones de UBUNTU ( 8.04 / 8.10 / 9.04), les comento que compré un disco de 80 GB sólo para instalar este sistema operativo pero doy en la tecla...me bajé las versiones desde la página oficial (versión i386) y usando la comienzo a instalar configuro el idioma, configuro el teclado, elijo en que disco instalarlo y después al comenzar a instalar todo bien..pero aproximadamente al 25% comienzan los problemas ya que me arrojar un error en un archivo que según informa no se condice con el que se encuentra el CD-DVD, el tema es que te permite seguir con la instalación eligiendo la opción SKIP, pero al aparecer 40 veces con diferentes archivos sacarán sus conclusiones de que se termina instalando...no obstante la notificación del error plantea algunos posibles orígenes del error:[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]* Disco rígido roto[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]* Problemas al grabar el CD-DVD; el problema que menciona es la velocidad de grabado.[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]* Problemas de temperatura del disco, por lo que recomienda llevarlo a un lugar con diferente temperatura.[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]No obstante ya trabajé estas posibilidades ya que el disco está bien porque instalé otros sistemas operativos sin ningún tipo de problemas (Windows Colossus 2), la velocidad de grabación la trabajé grabando cada versión hasta con 4X y ni ahí.....Me pueden ayudar????[/FONT][/SIZE]
Hola, este problema , para mi , es bastante raro, pero te dejo esto [http://www.ubuntu-es.org/?q=forum](http://www.ubuntu-es.org/?q=forum) es el foro en español ahi van a poder ayudarte mas.

Saludos!

---

