---
title: "Problema con archivo hal.dll"
date: 2009-12-15
forum: Instalación y Actualización
---

### Post by fern0z on 2009-12-15
Primero que todo, un Saludo.

Esta tarde me decidi cambiar de window xp a Ubuntu 9.10

inicie el live cd y luego lo instale desde escritorio, cuando llegue a la parte de las particiones me pidio si queria desmotar o no los discos ( tengo uno de 80gb(master) y otro de 160gb) le puse que no porque no sabia lo que era, aparte que no queria hacer particiones, luego le dije que borarara todo e instalara ubuntu en el disco de 80gb ( en este disco tenia el window XP) despues siguio todo normal y cuando reinicio y saco el live cd me sale un error que faltaba lo siguiente:
<window root> \system32\hal.dll

no logro saber que es.

Segun su conocimiento me podrian orientar a solucionarlo??

gracias de antemano

---

### Post by nechus on 2009-12-15
Hola

Mientras alguien más profesional te responde, tal vez te sirva saber que, por lo que encontré en Internet, también hay gente que no tiene nada que ver con Linux pero igual tiene problemas con ese archivo "hal.dll" y no pueden echar a andar su Windows.
( [http://www.trucoswindows.net/tutorial-120-TUTORIAL-Falta-el-archivo-HAL.DLL.html](http://www.trucoswindows.net/tutorial-120-TUTORIAL-Falta-el-archivo-HAL.DLL.html) )

Por lo visto, Ubuntu arrasó con Windows cuando lo instalaste (lo cual es algo muy bueno y debería ocurrir más a menudo), y obviamente también borró el archivo hal.dll, que es parte de Windows. Ahora bien, cuando uno instala Ubuntu, también se instala automáticamente un programita llamado GRUB que se activa al encender el computador para revisar qué sistemas operativos están instalados y echar a andar el sistema operativo que deseas.

GRUB se instala en un sector del disco duro que se llama Sector de Arrranque. En mi opinión, si ves un mensaje preguntándote por un archivo de Windows, probablemente es porque GRUB no quedó bien instalado y algo de Windows quedó dando vueltas por ahí, y por eso tu computador ahora sigue buscando Windows, pero obviamente, Windows ya no está ahí.

Si yo fuera tú, volvería a instalar Ubuntu (¡toma tan poco tiempo!) y me aseguraría de seguir bien todos los pasos de la instalación, seleccionando "Borrar todo el disco", e incluyendo lo de desmontar los discos y todo eso. Y si el programa de instalación te pregunta dónde instalar GRUB (aunque no creo que te lo pregunte), responde que en el "sector de arranque primario", (también llamado MBR, por "master boot record").

Si eso no resulta, asegúrate de detallar bien la información de tu computador, incluyendo marca, modelo, discos duros, RAM, etc en tu próximo posteo, para que te puedan ayudar mejor.

Buena suerte!

---

### Post by Carlos C on 2009-12-16
Mi duda es si la idea es mantener Windows o no. Tampoco entiendo si tienes más de un disco. También me gustaría saber si deseas compartir ambos sistemas en el mismo disco o no. Lo pregunto para que estemos seguros de lo que quieres.



Saludos.

---

### Post by nechus on 2009-12-16
Hola, Carlos C

Por lo que dice fern0z, su intención es borrar Windows ("*decidi cambiar de window xp a Ubuntu 9.10*"), y tiene más de un disco duro ("*tengo uno de 80gb(master) y otro de 160gb*")  Eso podría ayudar.

---

### Post by fern0z on 2009-12-16
Bueno muchas gracias por las respuestas.

luego de hacer la pregunta segui leyendo un poco por internet y me decidi a dejar window xp junto a ubuntu y no borrarlo (me refiero a XP) ya que soy nuevo en esto, pero mi idea principal es ir dejando de lado poco a poco a window ^:)

pero me sigue asaltando otra duda.

les explico:
tengo 2 discos duros
-80 gb
-160gb

window XP lo deje instalado en el disco de 80gb, este disco tiene una sola particion y esta como master (por si les interesa)
mi idea es dejar los sistemas operativos en el disco de 80gb y todos los datos,software,videos,juegos, etc en el de 160 gb.

trate de instalar ubuntu en el disco de 80gb con window xp previamente instalado pero al momento de ver el paso de las particiones me sale que window xp esta instalado en el disco de 160GB.

adjunto una captura.

De antemano muchas pero muchas gracias :P:)

PD: dejo una captura del modo avanzado de particion, me parecio importante

---

### Post by Carlos C on 2009-12-16
Abre el terminal y escribe lo siguiente:

```
sudo fdisk -l
```Te va a pedir tu clave. Copianos acá lo que te sale.
Saludos.

---

### Post by fern0z on 2009-12-16
Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xf9742454

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1               1        9728    78140128+   7  HPFS/NTFS

Disco /dev/sdb: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x76d0c5d3

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1         765     6144831   27  Desconocido
/dev/sdb2   *         766       19457   150143490    7  HPFS/NTFS


^^

---

### Post by Carlos C on 2009-12-16
Por lo que veo tienes dos discos, uno de 80 GB y otro de 160 GB y lo que pasa es lo siguiente:

El disco de 80 GB tiene una partición primaria que está formateada en NTFS.

El disco de 160GB tiene dos particiones, una pequeña de alrededor de 7 GB que no has formateado y otra más grande de alrededor de 153 GB formateada en NTFS. El sistema está iniciando desde esta última partición, por eso el asterisco al lado de "/dev/sdb2":
```
Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1         765     6144831   27  Desconocido
/dev/sdb2   *         766       19457   150143490    7  HPFS/NTFS
``` No tengo idea porque particionaste de esta manera este disco.

¿Estás seguro de que instalaste windows en el disco de 80 GB?

Si es así la solución es que durante la instalación realices un particionado manual, escoges la partición de 80 GB, modificas su tamaño dejándola más pequeña y te preocupas de no seleccionar la casilla que dice "¿Formatear?". También te preocupas de que el Flag "boot" quede en esta partición.

En el espacio libre puedes hacer una nueva partición para instalar Ubuntu que montarás en "/", otra para tu swap (escogiendo el tamaño adecuado para tu memoria RAM) y otra para tus archivos personales que montarás en "/home". Sobre el tamaño de estas particiones y lo que significa su "punto de montaje" hay bastante información en internet. Te recomiendo que leas esta página porque tiene información muy importante y te aclara muchas de tus dudas:

[http://www.guia-ubuntu.org/index.php?title=Particionar_el_disco_duro](http://www.guia-ubuntu.org/index.php?title=Particionar_el_disco_duro)


Saludos.

---

### Post by fern0z on 2009-12-16
oka muchas gracias.

el disco de 160 gb venia en el pc instalado con window vista, y cada vez que formateaba el pc me mostraba es particion como RECOVERY y por eso no la borro. voy a leer la guia. 
muchas gracias ^^

cualquier otra duda la ago ^^

igual estaba pensando.

¿No seria mejor y quedaria mas ordenado si instalara window de nuevo pero con le disco de 160gb desconectado??

otra pregunta.
¿si tengo 2 gb de ram? ¿tengo que dejar 4 gb de swap?

muchas gracias, esta muy bueno el foro super agradecido por sus respuestas.

y aguante LINUX!!!

---

### Post by Carlos C on 2009-12-16
> **fern0z said:**
> ¿No seria mejor y quedaria mas ordenado si instalara window de nuevo pero con le disco de 160gb desconectado??

otra pregunta.
¿si tengo 2 gb de ram? ¿tengo que dejar 4 gb de swap?

 Si lo puedes desconectar sería mejor, así te evitas confusiones. Sobre el tamaño del swap existe una sección de la página que te señalé que trata ese tema, se llama "tamaño de las particiones".

Saludos.

---

### Post by fern0z on 2009-12-18
logre solucionar el problema.

primero me meti a la setup del pc para ver desde que disco estaba booteando, me di cuenta wu boteaba desde el disco de 160gb asi que lo cambie.
luego instale window, borre todas las particiones del disco de 80 gb y cree una nueva de 15gb solo apra window, luego con el cd de ubuntu ise las particiones manualmente, deje 15gb para ubuntu, 2gb para Swap y todo lo demas para /home.

y funciono perfecto.

luego pase un susto, no me reconocia ningun disco, y se me ocurrio la idea de desconectar el de 160 y funciono, lo que saque pro conclusion es que en el de 160gb hay 2 particiones ( una es la para archivos y la otra es uan recovery) y mas las 3 que tenia en el de 80gb taban tirando problemas ^^

muchas gracias a todos por su ayuda ahora soy un usuario de UBUNTU :popcorn:

---

