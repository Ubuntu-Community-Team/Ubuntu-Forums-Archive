---
title: "Disco Duro sin SO"
date: 2010-03-22
forum: Instalación y Actualización
---

### Post by capcabgue on 2010-03-22
Hola, ni sospecho como arreglar este error.

Bueno les cuento que tengo un notebook dell 1525 particionado conviviendo guin2 y Ubuntu 9.10 64 bits. La cosa es que ayer necesite crear una zona de intercambio entre windows y linux, alcancé a ampliar la partición windows, liberar un poco la linux y los 15 GB libres que dejé se los iba a dar a una partición extendida ntfs.
Lo que sucedió después, es nebuloso, no recuerdo haber grabado estos cambios y ahora no puedo ver el grub y me arroja "grub rescue, partition no found" o algo así. Si inicio con un live CD me dice que el disco no esta particionado de ninguna forma y si trato instalar me indica que no hay SO.
Me gustaría saber como volver a recuperar las particiones, si es que se puede ya que estaba ubuntu como quería. Si esto no se puede lo más importante es como recupero la información que tenía en el DD de ubuntu.

Alguien me puede decir que hacer?

Gracias y en espera de sus respuesta

---

### Post by capcabgue on 2010-03-22
Hola nuevamente.

Ahora les puedo contar, con la tranquilidad que da el haber recuperado todo, que fue lo que hice.

Inicié el sistema con live cd ubuntu
luego abrí una terminal e inicie en modo interactivo (sudo -i)[COLOR=#3333FF][COLOR=#000000][COLOR=#009900][/COLOR][/COLOR][/COLOR]
Descargué test disk [COLOR=#3333FF][COLOR=#000000][COLOR=#009900](wget [/COLOR][/COLOR][/COLOR][COLOR=#009900]http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2[/COLOR])
luego lo descomprimí [COLOR=#3333FF][COLOR=#000000][COLOR=#009900]tar xjf [/COLOR][/COLOR][/COLOR][COLOR=#009900]testdisk-6.10.linux26.tar.bz2[/COLOR][COLOR=#000000][COLOR=#000000][/COLOR]
[/COLOR][COLOR=#000000]ingresé al directorio que descomprimi ([/COLOR][COLOR=#3333FF][COLOR=#000000][COLOR=#009900]$ cd testdisk-6.10[/COLOR][/COLOR][/COLOR])
[COLOR=#3333FF][COLOR=#000000][COLOR=#009900][/COLOR][/COLOR][/COLOR][COLOR=#3333FF][COLOR=#000000][COLOR=#009900][/COLOR][/COLOR][/COLOR][COLOR=#000000]accedí al directorio  linux [/COLOR][COLOR=#3333FF][COLOR=#000000][COLOR=#009900] (cd linux[/COLOR][/COLOR][/COLOR])[COLOR=#000000] [/COLOR][COLOR=#3333FF][COLOR=#000000][COLOR=#009900][/COLOR][/COLOR][/COLOR]
[COLOR=#3333FF][COLOR=#000000][COLOR=#009900][/COLOR][/COLOR][/COLOR][COLOR=#3333FF][COLOR=#000000][COLOR=#009900][/COLOR][/COLOR][/COLOR][COLOR=#000000]ejecutamos el testdisk[/COLOR][COLOR=#000000] ([/COLOR][COLOR=#3333FF][COLOR=#000000][COLOR=#009900]./testdisk_static)[/COLOR][/COLOR][/COLOR]
[COLOR=#3333FF][COLOR=#000000][COLOR=#009900][COLOR=Black]Luego es bastante intuitivo:
Aceptamos CREATE, se selecciona el sda (en mi caso, ojo que tambien se ve el cd-room)
Seleccionamos escaneo de Intel (si alguien tiene otro tipo de procesador lo pone)
ANALYSE, QUICK SEARCH.
van a aparecer en verde la nueva tabla de particiones, dejé como "primary booteable" a guindows y ahora estoy como el viernes en mi PC.
Lo que si no entiendo por qué cuando dejé como primary booteable e linux no inicio el pc (Este procedimiento de elegir quien es boteable y quien no lo pueden hacer por ensayto y error)

Lesdejo lo que hice ya que a alguien le puede servir. En todo caso este es el link de donde saqué lo que hice:
[http://grk-t.blogspot.com/2008/08/recuperar-tabla-de-particiones-con.html](http://grk-t.blogspot.com/2008/08/recuperar-tabla-de-particiones-con.html)

Suerte
[/COLOR][/COLOR][/COLOR][/COLOR][COLOR=#3333FF][COLOR=#000000][COLOR=#009900][/COLOR][/COLOR][/COLOR]

---

### Post by CdK1 on 2010-03-22
Solved...

---

