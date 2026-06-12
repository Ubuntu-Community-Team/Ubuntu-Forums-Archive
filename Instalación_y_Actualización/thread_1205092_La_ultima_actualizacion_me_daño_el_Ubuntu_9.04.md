---
title: "La ultima actualizacion me daño el Ubuntu 9.04?"
date: 2009-07-05
forum: Instalación y Actualización
---

### Post by PedroLuis on 2009-07-05
Hola a todos los Ubunteros, pongo esta interrogante para saber si a otros les a pasado.
Tenia mi Ubuntu 9.04 corriendo perfectamente, pero despues de la última actualización al reiniciar el computador se queda detenido al cargar en **Boot from (hd0,0) ext4 7bf..**.ect, luego aparece un error tal como ; **Error 25 : Disk read error** y mas abajo ; **Press any key to continue....**. Pulso una tecla y me aparece el Grub con su lista de kernel para ejecutarlo, pero al ejecutar cualquiera de ellos me manda nuevamente al principio mostrandome lo mismo que expongo anteriormente.

Buscando en foros y google encontre que habria que agregar al final del kernel "noapic nolapic" o probar con otros parecidos y rebotar, pero no me da resultado.

Puedo entrar con el LiveCd, capas que de aqui pueda recuperar la entrada grafica, pero como saber si el disco duro es el dañado? o hay un bug en la ultima actualizacion de Ubuntu ? 

Si puede alguien darme una manito ,estare agradecido. ;)

---

### Post by Carlos C on 2009-07-05
Si entras con el Live Cd puedes utilizar smartmontools:

[http://blockdeubuntu.blogspot.com/2008/07/utilizar-las-utilidades-smart-para.html](http://blockdeubuntu.blogspot.com/2008/07/utilizar-las-utilidades-smart-para.html)
[http://blockdeubuntu.blogspot.com/2009/01/monitoreando-el-estado-de-tu-disco-con.html](http://blockdeubuntu.blogspot.com/2009/01/monitoreando-el-estado-de-tu-disco-con.html)

De esa manera sabrás si tu disco tiene problemas.

Saludos.

---

### Post by pagondel on 2009-07-05
Movido a Instalacion y Actualizacion.

---

### Post by PedroLuis on 2009-07-06
Gracias Carlos , investigare con tus datos lo antes posible.

Saludos.  :p

> **Carlos C said:**
> Si entras con el Live Cd puedes utilizar smartmontools:

[http://blockdeubuntu.blogspot.com/2008/07/utilizar-las-utilidades-smart-para.html](http://blockdeubuntu.blogspot.com/2008/07/utilizar-las-utilidades-smart-para.html)
[http://blockdeubuntu.blogspot.com/2009/01/monitoreando-el-estado-de-tu-disco-con.html](http://blockdeubuntu.blogspot.com/2009/01/monitoreando-el-estado-de-tu-disco-con.html)

De esa manera sabrás si tu disco tiene problemas.

Saludos.

---

### Post by kamus on 2009-07-06
> **PedroLuis said:**
> Hola a todos los Ubunteros, pongo esta interrogante para saber si a otros les a pasado.
Tenia mi Ubuntu 9.04 corriendo perfectamente, pero despues de la última actualización al reiniciar el computador se queda detenido al cargar en **Boot from (hd0,0) ext4 7bf..**.ect, luego aparece un error tal como ; **Error 25 : Disk read error** y mas abajo ; **Press any key to continue....**. Pulso una tecla y me aparece el Grub con su lista de kernel para ejecutarlo, pero al ejecutar cualquiera de ellos me manda nuevamente al principio mostrandome lo mismo que expongo anteriormente.

Buscando en foros y google encontre que habria que agregar al final del kernel "noapic nolapic" o probar con otros parecidos y rebotar, pero no me da resultado.

Puedo entrar con el LiveCd, capas que de aqui pueda recuperar la entrada grafica, pero como saber si el disco duro es el dañado? o hay un bug en la ultima actualizacion de Ubuntu ? 

Si puede alguien darme una manito ,estare agradecido. ;)

Por casualidad actualizaste Kernel?,  Si fuer así puedes entrar a la version anterior en el menu de grub al momento de iniciar tu equipo selecciona la version anterior y dale enter.

Salu2

---

### Post by PedroLuis on 2009-07-07
Gracias Kamus, pero ya lo he hecho y no entro al escritorio grafico, vuelvo todo el tiempo al inicio de la cargada con [B]Boot from (hd0,0) ext4  Error 25:Disk read error
Press any key to continue.......[/B]

tengo el kernel 2.6.28-13-generic ademas este con (recovery mode) y el kernel 2.6.28-11-generic con su respectivo (recovery mode)
Pero en cualquiera de estos que quiera activar da lo mismo, vuelvo al **Boot...**..

El Ubuntu 9.04 me funcionaba de maravillas, cuando tenga tiempo investigare el disco rigido como me mostraron mas arriba.

Saludos.

> **kamus said:**
> Por casualidad actualizaste Kernel?,  Si fuer así puedes entrar a la version anterior en el menu de grub al momento de iniciar tu equipo selecciona la version anterior y dale enter.

Salu2

---

### Post by PedroLuis on 2009-07-08
Hola, hice el test de Smart y el resultado es el siguiente.

====START OF READ SMART DATA SECTION===
SMART Self-test log structure revision number 1
Num   Test_Description    Status           Remanining   LifeTime(hours)   LBA of first error
#1      Short offline     Completed:read failure  90%     746                   3834080
#2     Extended offline  Aborted by host            80%       0                   -

En el ejemplo del sajt tiene que tener 0%, al pareser mis resultados indican que el disco duro esta dañado.

Seguire investigando, y quiziera saber la opinion de ustedes.


> **Carlos C said:**
> Si entras con el Live Cd puedes utilizar smartmontools:

[http://blockdeubuntu.blogspot.com/2008/07/utilizar-las-utilidades-smart-para.html](http://blockdeubuntu.blogspot.com/2008/07/utilizar-las-utilidades-smart-para.html)
[http://blockdeubuntu.blogspot.com/2009/01/monitoreando-el-estado-de-tu-disco-con.html](http://blockdeubuntu.blogspot.com/2009/01/monitoreando-el-estado-de-tu-disco-con.html)

De esa manera sabrás si tu disco tiene problemas.

Saludos.

---

### Post by Carlos C on 2009-07-08
Hola. Voy a responder brevemente porque tengo poco tiempo.
Puedes verificar en uno de los enlaces que te di la manera de analizar los valores entregados por smart. En el terminal corre el siguiente comando:
```
sudo smartctl -A /dev/sda
```Eso siempre y cuando el disco analizado sea el sda. Luego mira los valores de la tabla "VALUE" y verifica que no sean menores a los encontrados en la tabla "THRESH". Si alguno de ellos es menor, el disco esta fallando o ha fallado y debiera aparecer registrado en la columna "WHEN FAILED". Para una descripción más detallada puedes mirar la entrada que antes indiqué.
Saludos.

---

### Post by PedroLuis on 2009-07-09
Hola, en Reallocated_Sector_Ct tengo un valor menor y me indica bajo When Failed un Failing Now, los valores son 134 en value y 140 en Thresh.

Ademas el disco duro lo escucho que tica bien amenudo, casi todo el tiempo.
Lo cambiare y despues lo comento.

Saludos.


> **Carlos C said:**
> Hola. Voy a responder brevemente porque tengo poco tiempo.
Puedes verificar en uno de los enlaces que te di la manera de analizar los valores entregados por smart. En el terminal corre el siguiente comando:
```
sudo smartctl -A /dev/sda
```Eso siempre y cuando el disco analizado sea el sda. Luego mira los valores de la tabla "VALUE" y verifica que no sean menores a los encontrados en la tabla "THRESH". Si alguno de ellos es menor, el disco esta fallando o ha fallado y debiera aparecer registrado en la columna "WHEN FAILED". Para una descripción más detallada puedes mirar la entrada que antes indiqué.
Saludos.

---

### Post by Carlos C on 2009-07-09
Está definitivamente malo. Una lástima.

---

