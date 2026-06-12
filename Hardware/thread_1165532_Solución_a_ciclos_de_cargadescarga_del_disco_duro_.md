---
title: "Solución a ciclos de carga/descarga del disco duro en Ubuntu"
date: 2009-05-20
forum: Hardware
---

### Post by felipeleven on 2009-05-20
El siguiente Post es extraído del antiguo foro de ubuntu-cl, y describe la solución para el problema de ciclos de carga y descarga de los discos duros.
post original: [http://foros.ubuntu-cl.org/viewtopic.php?t=6238&start=0&postdays=0&postorder=asc&highlight=](http://foros.ubuntu-cl.org/viewtopic.php?t=6238&start=0&postdays=0&postorder=asc&highlight=)

Los discos duros en ordenadores portátiles presentan una función de carga y descarga en el aparcado de los cabezales, esto hace que el disco duro libere energía, baje la temperatura de este y además lo haga menos propenso a golpes, recalcar que esto se presenta solamente en ordenadores portátiles.
La cantidad de ciclos de carga y descarga del disco duro son limitadas, aproximadamente un disco duro soporta 600.000 ciclos, llegando a su límite el disco duro deja de funcionar, este límite es variable, hay casos en que a durado 1.000.000 o más.

**Problema:**
En ciertos sistemas operativos, dentro de esto Ubuntu se presenta un problema donde esta cantidad de ciclos de carga/descarga se vuelven extremadamente frecuentes, acortando la vida del portátil.

**Síntomas:**
Una forma fácil de reconocer tal problema es través de la percepción de estos ciclos de carga/descarga, que se oyen directamente como un "click" desde el disco duro, al apagarse frecuentemente se presentan.

**Diagnóstico:**

Para ubuntu y otras distribuciones GNU/linux existe un programa que se llama Smartmontools, este se instala en Ubuntu desde consola con el siguiente comando:

```
sudo apt-get install smartmontools 
```Una vez instalado se teclea el siguiente comando:

```
sudo smartctl -a /dev/sda | egrep 'ID|Load_Cycle'
```Tal cual, al dar esa orden en la consola aparecerá algo como esto:

```
# sudo smartctl -a /dev/sda | egrep 'ID|Load_Cycle' 
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE 
225 Load_Cycle_Count        0x0032   062   062   000    Old_age   Always       -       **391140** 
```Donde lo que esta en negrita "391140" son los ciclos de carga/descarga del disco duro, para saber si tienes el problema debes estimar la cantidad de ciclos que tienes en relación con el tiempo de vida de tu disco duro, si ves que son demasiados debes proceder con la solución propuesta en este post, recuerda que aproximadamente los ciclos que aguanta un disco duro son de 600.000.

**Solución:**

Si tu portátil presenta los síntomas y lo verificaste con Smartmontools, debes modificar ciertos archivos de textos, que dependiendo de la versión de Ubuntu pueden variar.

[I][SIZE=4]Nota: 

[SIZE=3][COLOR=Red]-La solución propuesta modificará valores que afectarán directamente al hadware, favor de cumplir el procedimiento con rigurosidad, y hacerlo bajo su propia responsabilidad.[/COLOR][/SIZE][/SIZE][/I][COLOR=Red]

*[SIZE=3]-Los comandos que se usarán a continuación necesitan privilegios de administrador, así que deben teclear con sumo cuidado.[/SIZE]*[/COLOR]  



[CENTER][SIZE=5]Solución de ciclos de carga/descarga del disco duro válido hasta Ubuntu Hardy Heron[/SIZE]



[LEFT]Lo primero, es hacer una copia de seguridad de los archivos que vamos a usar, tecleando los siguientes comandos en la consola:

```
sudo cp /etc/laptop-mode/laptop-mode.conf /etc/laptop-mode/laptop-mode.conf.backup 
``````
sudo cp /etc/default/acpi-support /etc/default/acpi-support.backup 
 
``````
sudo cp /etc/acpi/power.sh /etc/acpi/power.sh.backup

```[/LEFT]
[/CENTER]
Lo anterior es en caso de error por haber hecho mal el procedimiento, para que posteriormente podamos recuperar los archivos originales.

Para comenzar con la solución en sí, debemos teclear en la consola:

```
sudo gedit /etc/laptop-mode/laptop-mode.conf
```Y dejamos la parte del archivo que mostraré a continuación de la siguiente forma (cambiando los valores en el editor de texto):

```
CONTROL_HD_IDLE_TIMEOUT=1 
 
LM_AC_HD_IDLE_TIMEOUT_SECONDS=300 
 
LM_BATT_HD_IDLE_TIMEOUT_SECONDS=300 
 
NOLM_HD_IDLE_TIMEOUT_SECONDS=7200 
 
CONTROL_HD_POWERMGMT=1 
 
BATT_HD_POWERMGMT=239 
 
LM_AC_HD_POWERMGMT=239 
 
NOLM_AC_HD_POWERMGMT=239 
```Guardamos los cambios y ahora cambiaremos los valores de otro archivo, para esto tecleamos:

```
sudo gedit  /etc/default/acpi-support
```,y modifiquen la siguiente parte de esta forma: 

```
ENABLE_LAPTOP_MODE=true 
SPINDOWN_TIME=60 
```Y ahora modificamos el último archivo:

```
sudo gedit /etc/acpi/power.sh
```Buscamos en el archivo la sección "function laptop_mode_enable", y  cambiamos todos los **$HDPARM -B 1**... por **$HDPARM -B 239**... 

Guardamos todos los cambios y listo, al reiniciar el portátil los ciclos deberían haber desaparecido.



[CENTER][SIZE=5]Solución de ciclos de carga/descarga del disco duro válido para Ubuntu Intrepid Ibex
[SIZE=1]


[/SIZE][/SIZE][LEFT]Para ubuntu intrepid ibex la solución es más sencilla ya que solamente se debe cambiar los valores a un solo archivo de texto.

Pero primero hacemos un respaldo del archivo a modificar de la siguiente forma:

```
sudo cp /etc/default/acpi-support /etc/default/acpi-support.backup 
```Hecho esto, procedemos con la solución, para lo cuál tecleamos en la consola:

```
sudo gedit /etc/default/acpi-support
```Buscamos y cambiamos la siguiente línea y la dejamos así:

```
ENABLE_LAPTOP_MODE=true  
```[/LEFT]
[/CENTER]
 
En Ubuntu Intrepid Ibex esta línea se encuentra en distinta posición que en Ubuntu Hardy Heron, al reiniciar el portátil los ciclos deberían haber desaparecido.



[CENTER][SIZE=5]Restaurar los archivos respaldados en caso de error
[SIZE=1]


[/SIZE][/SIZE][LEFT]En caso de haber editado mal los archivos, o no se haya solucionado el problema, simplemente restauran los archivos modificados a su forma original de la siguiente forma:

En Ubuntu Hardy Heron (y versiones anteriores):

```
sudo cp /etc/laptop-mode/laptop-mode.conf.backup /etc/laptop-mode/laptop-mode.conf 
``````
sudo cp /etc/default/acpi-support.backup /etc/default/acpi-support 
 
``````
sudo cp /etc/acpi/power.sh.backup /etc/acpi/power.sh
```En Ubuntu Intrepid Ibex:

```
sudo cp /etc/default/acpi-support.backup /etc/default/acpi-support

```[CENTER]
[/CENTER]
[/LEFT]
[CENTER][SIZE=5]Anexo[SIZE=1]



[/SIZE][/SIZE][LEFT]-Gran parte de esta solución fue estraída de los foros de Ubuntu-es:

Página donde se trata el problema: [http://www.ubuntu-es.org/index.php?q=node/68986 ]("http://www.ubuntu-es.org/index.php?q=node/68986")

[SIZE=3]- [/SIZE][SIZE=3]En Ubuntu Jaunty Jackalope no se me presentó el problema, en caso de que a alguien si, favor de avisar.[/SIZE]
[/LEFT]
[/CENTER]


[LEFT]-En caso de que haya un error en la redacción o falte algo por explicar, también favor de avisar.

Saludos y que esten muy bien):P
[/LEFT]
[/CENTER]

---

