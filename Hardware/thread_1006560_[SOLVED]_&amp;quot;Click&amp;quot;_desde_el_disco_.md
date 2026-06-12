---
title: "[SOLVED] &amp;quot;Click&amp;quot; desde el disco en XPS m1330"
date: 2008-12-09
forum: Hardware
---

### Post by santiagoward2000 on 2008-12-09
Hola gente!
Vengo con una duda. Tengo una Dell XPS m1330, con el Disco Duro SATA de 160GB (5400RPM). El tema es que cada tanto escucho un "click", que creo que viene del disco. Además veo actividad del disco cuando lo escucho. Estuve buscando info en la página de Dell, pero encontré cosas desde que es normal por las opciones de energía del disco (que el ruido es cuando el disco se prende y apaga para ahorrar energía), hasta que puede ser señal que el disco está por morir.
¿Tengo que preocuparme?
Saludos!

---

### Post by sergiom99 on 2008-12-09
Santiago, 
hay un sticky que vengo siguiendo en el foro de laptops que cubre este tema, es un bug bastante grave de linux con el manejo de discos.
[http://ubuntuforums.org/showthread.php?t=805570](http://ubuntuforums.org/showthread.php?t=805570)

el amigo vor (a.k.a. 'Luca Prodan') tambien esta en el tema y la tiene clara.
espero te sirva.

---

### Post by sajnox on 2008-12-09
Mi mujer tiene una inspiron 1525 y siempre se asusto por que la maquina hace un "click", esto lo hace desde que la  tiene (tres meses) y por ahora el disco anda bien.

PS: Ella agrega que lo hace abajo a la izquierda, que es precisamente donde esta el disco

---

### Post by santiagoward2000 on 2008-12-09
> **sajnox said:**
> Mi mujer tiene una inspiron 1525 y siempre se asusto por que la maquina hace un "click", esto lo hace desde que la  tiene (tres meses) y por ahora el disco anda bien.

PS: Ella agrega que lo hace abajo a la izquierda, que es precisamente donde esta el disco

A mí me pasa lo mismo, y parece que viene del mismo lugar. Ahora ando leyendo todo lo que pasó sergio para ver qué encuentro. Lo único raro (aunque la verdad no estoy del todo seguro) es que me parece haberlo escuchado usando Windows también. Y yo la compré pensando que como la venden con Ubuntu preinstalado me iba a andar todo bien (aunque la compré con Windows). :(
Voy a seguir leyendo a ver qué encuentro.
Saludos! Y gracias a sergio por la info!

---

### Post by Hei Ku on 2008-12-09
No quiere decir que ande mal. Sólo pasa que el mecanismo de ahorro de energía del disco es demasiado agresivo a veces. Pero si lees, es algo que podés modificar muy facilmente.

---

### Post by santiagoward2000 on 2008-12-09
Bueno, estuve leyendo el post que pasó Sergio. Antes de ponerme a tocar cosas, usé el **smartmontools** para revisar el estado del disco, como recomienda.
Primero, cuando hice:
```
sudo smartctl -H /dev/sda
```
me dio:
```
=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
```
O sea que esto está bien. Pero cuando quise ver el Load_Cycle_Count, hice:
```
sudo smartctl -a /dev/sda | grep Load_Cycle_Count
```
y no me devolvió nada... :confused:
Pero después revisé todo con:
```
sudo smartctl -a /dev/sda | more
```
no encontré nada raro. Ahí figura que el Load_Cycle_Count es de 532. Mientras escribía esto hizo el ruido ese de nuevo (2 veces), revisé otra vez, pero no había subido.
Ahora, estuve buscando cuál es el límite real para este disco, pero no lo encuentro. Lo busqué como Duro SATA de 160GB (5400RPM) (que es el nombre que figura en la página de Dell) y también como SAMSUNG HM160HI (que es el nombre que aparece en el smartctl).
Igual, si en 2 meses subió 532 ciclos, y supongo que el límite es de 600000, como según el post es para la mayoría, haciendo cuentas rápidas me da que aguantaría como 200 años. ¿O sea que puedo estar tranquilo y no se va a romper? ¿O estoy re equivocado? (Acabo de rendir un parcial de termodinámica, así que es bastante probable que haya dicho cualquier cosa)
Gracias!

---

### Post by sergiom99 on 2008-12-10
me parece demasiado bajo.
yo lo tengo mas o menos controlado con el ugly_fix.sh que esta en ese post.
creo (ahora no estoy con la laptop) que estoy por debajo de los 30k y voy por casi un año de usarla.

---

### Post by santiagoward2000 on 2008-12-10
> **sergiom99 said:**
> me parece demasiado bajo.
yo lo tengo mas o menos controlado con el ugly_fix.sh que esta en ese post.
creo (ahora no estoy con la laptop) que estoy por debajo de los 30k y voy por casi un año de usarla.

Si, a mí también me parece medio bajo. Y hasta ahora no aumentó... Me preocupa que esté tan bien. ¿Me faltará algún paquete y estará midiendo mal?

---

### Post by Mister X on 2008-12-10
Corrijo lo que pusieron mas arriba porque se hace una bola de nieve...

NO ES UN BUG DE LINUX, NI DE UBUNTU

es el mecanismo para proteger el disco de las laptops, que descarga las cabezas cuando no hay acceso al disco.
paradojicamente el mecanismo de proteccion puede hacer que se acorte muchisimo la vida util del disco...

---

### Post by santiagoward2000 on 2008-12-10
> **Mister X said:**
> es el mecanismo para proteger el disco de las laptops, que descarga las cabezas cuando no hay acceso al disco.
paradojicamente el mecanismo de proteccion puede hacer que se acorte muchisimo la vida util del disco...

Gracias por la info. El tema de "proteger", se refiere a posibles golpes o vibraciones. O sea que si lo desactivo, además de bajar la duración de la batería, puedo llegar a romper el disco con algún movimiento, no?
Y el tema de la vida util, ¿cuánto se acorta? Por lo que estoy viendo, me parece que no conviene cambiar estas opciones, excepto a que sino la vida del disco sea muy baja...

---

### Post by Mister X on 2008-12-10
el click que se escucha es cuando las cabezas salen de los platos y se "estacionan", esta funcion sirve para protegerlo de los golpes, pero no es una funcion de ahorro de energia ya que el disco sigue girando, son 2 cosas distintas.

he visto varias marcas que establecen la vida util en 600.000 ciclos de carga/descarga, pero puede variar con el fabricante, con smartctl obtenes la cantidad de ciclos y la cantidad de tiempo encendido, por lo tanto podes calcular el tiempo estimado que le "queda"

yo en mi caso se lo desactive, sobre todo porque me molestaba bastante el "click", era como una tortura china...:p

---

### Post by sergiom99 on 2008-12-10
asi esta el mio, despues de 1 año de Kubuntu en la laptop:
```
sergio@kubuntu:~$ date; sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|194)'
mié dic 10 18:09:06 ARST 2008
193 Load_Cycle_Count        0x0032   099   099   000    Old_age   Always       -       19555
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       45 (Lifetime Min/Max 11/55)
sergio@kubuntu:~$

```

lo de bug o no bug, asi fue catalogado en el foro respectivo y estuvo como sticky casi un año. los craneos sabran como clasificarlo, para eso hay paginas y paginas en ese thread y varios mas por internet y foros de otras distros.

hasta que se corrija definitivamente, el ugly_fix te salva un poco. :-D

---

### Post by santiagoward2000 on 2008-12-10
> **Mister X said:**
> el click que se escucha es cuando las cabezas salen de los platos y se "estacionan", esta funcion sirve para protegerlo de los golpes, pero no es una funcion de ahorro de energia ya que el disco sigue girando, son 2 cosas distintas.

he visto varias marcas que establecen la vida util en 600.000 ciclos de carga/descarga, pero puede variar con el fabricante, con smartctl obtenes la cantidad de ciclos y la cantidad de tiempo encendido, por lo tanto podes calcular el tiempo estimado que le "queda"

Bueno, revisé bien el smartctl y me aparecen 535 en Power_Cycle_Count en 661 horas de uso. Supongo que me puedo quedar tranquilo :p

> **Mister X said:**
> yo en mi caso se lo desactive, sobre todo porque me molestaba bastante el "click", era como una tortura china...:p

Si, puede ser bastante molesto, pero por ahora me la banco. No vaya a ser que apague la protección y lo termine rompiendo antes.
GRACIAS!

---

### Post by Mister X on 2008-12-10
> **santiagoward2000 said:**
> Bueno, revisé bien el smartctl y me aparecen 535 en Power_Cycle_Count en 661 horas de uso. Supongo que me puedo quedar tranquilo :p



normalmente el atributo de smart se llama Load/Unload Cycle Count o algo asi, el que vos decis parece tener mas que ver con el apagado del disco, fijate cual es el valor que se incrementa despues de cada click

---

### Post by santiagoward2000 on 2008-12-10
> **Mister X said:**
> normalmente el atributo de smart se llama Load/Unload Cycle Count o algo asi, el que vos decis parece tener mas que ver con el apagado del disco, fijate cual es el valor que se incrementa despues de cada click

¿Puede ser el **Start_Stop_Count**? Ese está en 62079. Aunque todavía no hizo "Click", no sé si sube.
No encuentro ningún **Load_Cycle_Count** (o algo parecido).

---

### Post by z37a on 2008-12-10
Ahora que complicado sacrificar hdd o sacrificar Bateria????? la verdad no me decido por cual!!!

Igualmente no se pro que en mi laptop cuando apenas instalo anda haciendo el famoso clack, apens instalo un solo update(sea cual sea) de repente se queda la luz del hdd siempre prendida y no se escucha mas el tack metalico ese horrendo(y la betaria me la come cruda, entre eso y que el kernel no tiene soporte para el escalado de mhz de mi micro).

---

### Post by Mister X on 2008-12-10
> **santiagoward2000 said:**
> ¿Puede ser el **Start_Stop_Count**? Ese está en 62079. Aunque todavía no hizo "Click", no sé si sube.
No encuentro ningún **Load_Cycle_Count** (o algo parecido).


Si, es ese, a mi tambien me figura Start_Stop_Count, esta es la salida del mio:

```

smartctl -A /dev/sda |grep Start
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       4800

```

me parece que tenes un numero muy alto para solamente 600 horas, controlalo bien

---

### Post by santiagoward2000 on 2008-12-10
> **Mister X said:**
> Si, es ese, a mi tambien me figura Start_Stop_Count, esta es la salida del mio:

```

smartctl -A /dev/sda |grep Start
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       4800

```

me parece que tenes un numero muy alto para solamente 600 horas, controlalo bien

Eh... sigue subiendo. Ahora anda por 62157. ¿Me tengo que preocupar? ¿Alguien sabe dónde puedo encontrar los límites para mi disco?
Lo otro que no entiendo es por qué no aparece el **Load_Cycle_Count**. Cuando pongo:
```
sudo smartctl -a /dev/sda | grep Load
```
no aparece nada.

---

### Post by sergiom99 on 2008-12-10
proba con esto:
```
sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|194)'
```

---

### Post by santiagoward2000 on 2008-12-10
> **sergiom99 said:**
> proba con esto:
```
sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|194)'
```

Lo probé, pero solo me da la temperatura, no el Load_Cycle_Count.

---

### Post by marianom on 2008-12-10
De más está decir que mis conocimientos de hardware son nulos pero mirando los threads y los números de Santiago (tenemos la misma máquina), creo que yo si debería preocuparme...

¿Que me dicen los que saben?

```
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   253   006    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   099   098   085    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       59
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   066   057   030    Pre-fail  Always       -       8598108513
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       635
 10 Spin_Retry_Count        0x0013   100   100   034    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       59
187 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
189 Unknown_Attribute       0x003a   100   100   000    Old_age   Always       -       0
190 Temperature_Celsius     0x0022   063   055   045    Old_age   Always       -       673382437
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       56
193 Load_Cycle_Count        0x0022   071   071   000    Old_age   Always       -       58075
194 Temperature_Celsius     0x001a   037   045   000    Old_age   Always       -       37 (Lifetime Min/Max 0/19)
195 Hardware_ECC_Recovered  0x0012   075   057   000    Old_age   Always       -       188894204
197 Current_Pending_Sector  0x0010   100   100   000    Old_age   Offline      -       0
198 Offline_Uncorrectable   0x003e   100   100   000    Old_age   Always       -       0
199 UDMA_CRC_Error_Count    0x0000   200   200   000    Old_age   Offline      -       0
200 Multi_Zone_Error_Rate   0x0032   100   253   000    Old_age   Always       -       0
202 TA_Increase_Count       0x0000   100   253   000    Old_age   Offline      -       0
240 Head_Flying_Hours       0x0000   000   000   000    Old_age   Offline  FAILING_NOW 24232205484670
241 Unknown_Attribute       0x0000   000   000   000    Old_age   Offline  FAILING_NOW 265439393
242 Unknown_Attribute       0x0000   000   000   000    Old_age   Offline  FAILING_NOW 1567775
254 Unknown_Attribute       0x0000   100   253   000    Old_age   Offline      -       0

```

Yo la tengo casi todo el tiempo enchufada y muchas horas al día prendida (días y días), con respecto al "click" solo lo escuho cuando desenchufo la máquina.

---

### Post by marianom on 2008-12-11
Definitivamente 20/30 ciclos para 10 minutos cuando la máquina está enchufada no es bueno. Sale un ugly fix para mi...

---

### Post by sdennie on 2008-12-11
Yo tambien tengo un XPS m1330 y hoy me di cuenta de que el disco va a "Old_Age" despues de 200000 Load_Cycle_Count (como lo de marianom: 58075 / (100 - 71) = 200000).  En este caso, "Old_Age" (> 200000 Load_Cycle_Count) no significa "Dead" pero es mas probable que el disco va a morir.

Ojo que el "99-hdd-ugly-fix.sh" de [http://ubuntuforums.org/showpost.php?p=5031046&postcount=3](http://ubuntuforums.org/showpost.php?p=5031046&postcount=3) no va a funcionar 100% con Hardy o Intrepid.  Esta bien el script pero, para instalarlo debes usar:

```

sudo install 99-hdd-ugly-fix.sh /etc/pm/sleep.d
sudo install 99-hdd-ugly-fix.sh /etc/pm/power.d

```

Tambien, yo tengo otros scripts parecidos (pero mas de power savings) aca: [ HOWTO: XPS m1330 power savings]("http://ubuntuforums.org/showthread.php?t=847773") y otra manera para bajar Load_Cycle_Count un poco aca: [  HOWTO: Decrease disk activity]("http://ubuntuforums.org/showthread.php?t=839998") (No podes usar los dos al mismo tiempo).

---

### Post by marianom on 2008-12-11
Una máquina con ni siquiera dos meses de uso y ya con vejez prematura es triste... ¿Con ir ahorrando para un disco nuevo hago bien no? :)

Gracias vor por tus tips, prometo molestarte en forma abundante luego de una tranquila lectura de tus posts (aunque les di ya una ojeada y son muy claros).

Mariano.

---

### Post by fgl82 on 2008-12-11
perdon pero no entendí:

58075 / (100 - 71) = da 2002 y monedas, no 200000 :S

de qué me perdí?

---

### Post by santiagoward2000 on 2008-12-11
Gracias Vor por los how-to's. Esta noche me pongo a leerlos y veo qué hago. Y me imagino que voy a molestarte tanto como Mariano! :lolflag:

> **marianom said:**
> Una máquina con ni siquiera dos meses de uso y ya con vejez prematura es triste... ¿Con ir ahorrando para un disco nuevo hago bien no? :)

Una pregunta sobre esto: ¿alguien sabe si te lo cubre la garantía? Ya me contacté con la gente de Dell, pero todavía no me contestaron...

---

### Post by sajnox on 2008-12-11
Algo me dice que este thread va a desatar panico por lo que me atrevo a sugerir lo siguiente, y para ello recurro a los amigos con un poco mas de experiencia en el tema para que nos aclaren lo siguiente.

1) Esto aplica a todos los discos (notebooks y desktops) o es una cuestion de seguridad impuesta por Dell?
2) Esto lo maneja directamente el bios y no el sistema operativo, es asi? En caso que lo sea, por que lo habilitaron?
3) Si lo deshabilito, que riesgos se corren / que ventajas se obtienen?
4) Que comandos hay que correr y que valores analizar para ver el estado del disco?
5) Esto tiene relacion directa con el tiempo de encendido de la maquina?

Desde ya muchas gracias a todos los que puedan colaborar

Saludos

---

### Post by fgl82 on 2008-12-11
¿Che, hablo yo o pasa un carro? :lolflag:

---

### Post by marianom on 2008-12-11
> **fgl82 said:**
> ¿Che, hablo yo o pasa un carro? :lolflag:

Hola, gracias por el tip que tiraste (y de paso pusiste en evidencia cuan malo soy en matematica). Estimo que vor nos explicará exactamente que pasa con ese cálculo. Yo creí que el dato de Cycles se leía literal como estaba (58.000 en mi caso, yendo a los 600.000).

---

### Post by marianom on 2008-12-11
> **sajnox said:**
> Algo me dice que este thread va a desatar panico por lo que me atrevo a sugerir lo siguiente, y para ello recurro a los amigos con un poco mas de experiencia en el tema para que nos aclaren lo siguiente.

No veo porque debería haber pánico. Hay un circunstancia clara sobre configuraciones que posiblemente traigan problemas y por suerte hay gente que sabe y linux te da todas las posibilidades para que puedas corregirlo y seas conciente de los pros y contras de esos cambios. No hay que desesperar, solo prestar atención y acomodar lo que sea necesario.

> **sajnox said:**
> 
1) Esto aplica a todos los discos (notebooks y desktops) o es una cuestion de seguridad impuesta por Dell?
2) Esto lo maneja directamente el bios y no el sistema operativo, es asi? En caso que lo sea, por que lo habilitaron?
3) Si lo deshabilito, que riesgos se corren / que ventajas se obtienen?
4) Que comandos hay que correr y que valores analizar para ver el estado del disco?
5) Esto tiene relacion directa con el tiempo de encendido de la maquina?
Como lo entiendo yo:
1) Aplica en su mayoría a las notebooks ya que son las que se conectan/desconectan y son pasibles de recibir algunos golpes de vez en cuando.
2) Son seteos standards que vienen por defecto en las máquinas, mayormente favorecen a máquinas con windows (aunque hay reportes de problemas con Vista). Esos seteos no siempre son los ideales para linux (más allá que muchos de ellos sirvan para todos los sistemas operativos).
3) Depende de lo que quieras haces, aumentas la vida util de tu disco a riesgo de levantar la temperatura de la máquina y tener posibles problemas con golpes en la máquina porque no vas a estar tan protegido con que el disco no se vea afectado por una mala maniobra. O viceversa.
4) Ver el post que linkearon al principio de esta conversa, de [Ubuntu_demon]("http://ubuntuforums.org/showthread.php?t=805570"). Ahi está todo.
5) No entendí la pregunta.

Gente más capaz, inteligente y meritoria que yo sabrá corregirme.

---

### Post by santiagoward2000 on 2008-12-11
> **marianom said:**
> Hola, gracias por el tip que tiraste (y de paso pusiste en evidencia cuan malo soy en matematica). Estimo que vor nos explicará exactamente que pasa con ese cálculo. Yo creí que el dato de Cycles se leía literal como estaba (58.000 en mi caso, yendo a los 600.000).

Entonces no me termina de quedar claro cómo se cuentan los Load_Cycles. ¿En el caso de Mariano serían 58.000 o 2002?

---

### Post by luks911 on 2008-12-11
> **vor said:**
> Yo tambien tengo un XPS m1330 y hoy me di cuenta de que el disco va a "Old_Age" despues de 200000 Load_Cycle_Count (como lo de marianom: 58075 / (100 - 71) = 200000).  En este caso, "Old_Age" (> 200000 Load_Cycle_Count) no significa "Dead" pero es mas probable que el disco va a morir.

Ojo que el "99-hdd-ugly-fix.sh" de [http://ubuntuforums.org/showpost.php?p=5031046&postcount=3](http://ubuntuforums.org/showpost.php?p=5031046&postcount=3) no va a funcionar 100% con Hardy o Intrepid.  Esta bien el script pero, para instalarlo debes usar:

```

sudo install 99-hdd-ugly-fix.sh /etc/pm/sleep.d
sudo install 99-hdd-ugly-fix.sh /etc/pm/power.d

```

Tambien, yo tengo otros scripts parecidos (pero mas de power savings) aca: [ HOWTO: XPS m1330 power savings]("http://ubuntuforums.org/showthread.php?t=847773") y otra manera para bajar Load_Cycle_Count un poco aca: [  HOWTO: Decrease disk activity]("http://ubuntuforums.org/showthread.php?t=839998") (No podes usar los dos al mismo tiempo).

Para Intrepid apliqué [esto]("http://ubuntuforums.org/showpost.php?p=5031047&postcount=3")[0], que en realidad es [esto]("http://en.opensuse.org/Disk_Power_Management")[1] y funciona. Sube sólo un ciclo por cada reinicio. Antes, muy cavernícola yo, le había agregado 
```
hdparm -B 255 /dev/sda
```
al rc.local, como la uso siempre enchufada... Antes de eso era un click a cada rato.
:lolflag:

[0] [http://ubuntuforums.org/showpost.php?p=5031047&postcount=3](http://ubuntuforums.org/showpost.php?p=5031047&postcount=3)
[1] [http://en.opensuse.org/Disk_Power_Management](http://en.opensuse.org/Disk_Power_Management)

---

### Post by marianom on 2008-12-11
Yo probé en el rango descendente de 254 a 245 con intervalos de media hora aprox y el Cycle no se ha movido desde entonces.

---

### Post by luks911 on 2008-12-11
> **marianom said:**
> Yo probé en el rango descendente de 254 a 245 con intervalos de media hora aprox y el Cycle no se ha movido desde entonces.

Sí, el valor depende del disco según leí. En mi caso con 255 va bien pero con 254 empezaba a moverse. Así que es cuestión de probar.

---

### Post by sdennie on 2008-12-11
> **fgl82 said:**
> perdon pero no entendí:

58075 / (100 - 71) = da 2002 y monedas, no 200000 :S

de qué me perdí?

Oops:

58075 / (1 - .71) = 200000

En mi caso:

91101 / (1 - .55) = 202000

Los numeros viene de los columnas RAW_VALUE y WORST (que es un porcentaje).  En realidad a llegar a WORST=00 (200000 Load_Cycle_Count), no es que el disco se muere.  Es simplemente que durante las pruebas del disco, algunos (capaz que 1 en 1000) se murio despues de 200000 Load_Cycle_Count.  Capaz que la mayoria de los discos de la misma marca duran hasta 1000000 pero tienen que decir 200000 igual.

---

### Post by santiagoward2000 on 2008-12-11
Estaba por ponerme a usar el ugly_fix, y antes quería ver cómo está el disco. Pero yo sigo con la duda de por qué no puedo ver el Load_Cycle_Count. Cuando uso:
```
sudo smartctl -a /dev/sda
```
me da:
```
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   252   252   025    Pre-fail  Always       -       2062
  4 Start_Stop_Count        0x0032   094   094   000    Old_age   Always       -       62486
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       668
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       546
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       256
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       38
194 Temperature_Celsius     0x0022   157   112   000    Old_age   Always       -       27 (Lifetime Min/Max 13/42)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       36525
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       1025
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       4292
199 UDMA_CRC_Error_Count    0x0036   252   252   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   252   252   000    Old_age   Always       -       0

```
¿Alguien sabe qué me puede faltar? ¿Si no cómo hago para ver qué valor usar?
Gracias!

_EDIT:_
Por lo que leí en acá: [http://ubuntuforums.org/showthread.php?t=948884]("http://ubuntuforums.org/showthread.php?t=948884") mi disco no lo soporta y tengo que usar el Start_Stop_Count para calcularlo.
¿Está bien?

---

### Post by marianom on 2008-12-11
> **santiagoward2000 said:**
> Estaba por ponerme a usar el ugly_fix, y antes quería ver cómo está el disco. Pero yo sigo con la duda de por qué no puedo ver el Load_Cycle_Count.
...
¿Alguien sabe qué me puede faltar? ¿Si no cómo hago para ver qué valor usar?
Gracias!

No todos los discos reportan el valor Load_Cycle_Count. Mira [aca]("http://sourceforge.net/mailarchive/message.php?msg_id=a2c126ef0811271402y37e44d86kdcafe32f7d1687b5%40mail.gmail.com") por un ejemplo de alguien con un disco Samsung en una Dell Inspiron comprada en 2008.

---

### Post by marianom on 2008-12-11
> **santiagoward2000 said:**
> _EDIT:_
Por lo que leí en acá: [http://ubuntuforums.org/showthread.php?t=948884]("http://ubuntuforums.org/showthread.php?t=948884") mi disco no lo soporta y tengo que usar el Start_Stop_Count para calcularlo.
¿Está bien?

No se vale, no leí tu Edit antes de ponerme a buscar :)

---

### Post by marianom on 2008-12-11
Ahora veo que me pasa algo raro. Como les comenté, había corrido varios

```
sudo hdparm -B *n* /dev/sda
```

para probar cual me iba mejor. Los ciclos no se movieron más pero la temperatura de la máquina variaba entre 62° y 72°, algo que no me agradó (bajando a 57° cuando la desenchufaba). Además no me acordaba cual era el valor por defecto que traía la máquina, así que reinicié (se supone que sin grabar nada de estos cambios).

Ahora con la máquina recién iniciada, setee un valor de 196 para probar y si bien veo que el disco trabaja los ciclos han quedado con el valor que tuve antes de reiniciar no importa lo que yo haga:

```
mariano@kafka:~$ date; sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|194)'
Fri Dec 12 00:32:49 ARST 2008
193 Load_Cycle_Count        0x0022   071   071   000    Old_age   Always       -       58413
194 Temperature_Celsius     0x001a   040   045   000    Old_age   Always       -       40 (Lifetime Min/Max 0/19)

```

Además la temperatura está en los 42°. Desconecté la electricidad, puse un video, me pasee un poco, actualicé todos mis feeds, puse a correr mi offlineimap, etc, etc... la máquina sigue estacionada en ese valor de 58413.

Ahora me pone muy contento que no se mueva pero yo entiendo el ciclo lógico de la vida: todos debemos envejecer y morir (salvo Gardel y Elvis, obvio) y también mi disco. ¿Por qué no se mueve más?

---

### Post by santiagoward2000 on 2008-12-11
A mí también me está pasando lo mismo que a Mariano con el tema que no aumenta más. Lo setié en 254 para empezar, y ahora el Start_Stop_Count no sube de 62597. Yo no ví el problema de la temperatura, ahora anda en 35°. Admás ya no escucho el "Click", ni siquiera andando en batería (por lo menos durante la última media hora).
Yo no lo guardé todavía, ni reinicié la máquina, ¿pero es normal que se quede ahí?

---

### Post by vk-cdg on 2008-12-12
Se que es mucho pedir, pero entre mi limitado inglés que no me permite seguir a fondo el thread inicial donde se trata el tema, y las pruebas de cada uno, estoy como medio perdido.

Imagino (si no ya estaría posteado) que no hay una versión en castellano no?

---

### Post by luks911 on 2008-12-12
> **vk-cdg said:**
> Se que es mucho pedir, pero entre mi limitado inglés que no me permite seguir a fondo el thread inicial donde se trata el tema, y las pruebas de cada uno, estoy como medio perdido.

Imagino (si no ya estaría posteado) que no hay una versión en castellano no?

Te paso un par de links con algo de información en castellano, mi inglés tampoco es ninguna maravilla...

[http://www.vicente-navarro.com/blog/2007/10/28/linux-no-mata-discos-duros-se-mueren-solos/](http://www.vicente-navarro.com/blog/2007/10/28/linux-no-mata-discos-duros-se-mueren-solos/)
[http://www.kriptopolis.org/ubuntu-podria-acortar-vida-disco-duro-portatiles](http://www.kriptopolis.org/ubuntu-podria-acortar-vida-disco-duro-portatiles)

---

### Post by marianom on 2008-12-12
Podes fijarte en [ubuntu-es]("http://www.google.com/cse?cx=017201757735414495044%3As1rbiqklhec&ie=UTF-8&q=hdparm&sa=Buscar"), parece haber abundantes articulos al respecto.

---

### Post by marianom on 2008-12-12
> **santiagoward2000 said:**
> A mí también me está pasando lo mismo que a Mariano con el tema que no aumenta más. Lo setié en 254 para empezar, y ahora el Start_Stop_Count no sube de 62597. Yo no ví el problema de la temperatura, ahora anda en 35°. Admás ya no escucho el "Click", ni siquiera andando en batería (por lo menos durante la última media hora).
Yo no lo guardé todavía, ni reinicié la máquina, ¿pero es normal que se quede ahí?

Santiago, el valor 254 no es definitivo, lo podes ir moviendo entre 0 a 255 hasta que encuentres el que mejor se ajuste a tu máquina. Si bien el no aumento de ciclos y la buena temperatura parecería ser una buena noticia, a mi me tiende a preocupar en mi máquina (debe ser que no puedo aceptar las cosas buenas así nomás).

---

### Post by santiagoward2000 on 2008-12-12
> **marianom said:**
> Santiago, el valor 245 no es definitivo, lo podes ir moviendo entre 0 a 255 hasta que encuentres el que mejor se ajuste a tu máquina. Si bien el no aumento de ciclos y la buena temperatura parecería ser una buena noticia, a mi me tiende a preocupar en mi máquina (debe ser que no puedo aceptar las cosas buenas así nomás).

JAJA! Eso mismo! O sea, está buenísimo que esté así, y no se mueva, pero... ya está todo bien y mi disco va a andar perfectamente de por vida? Seré pesimista, pero no me cierra.

---

### Post by santiagoward2000 on 2008-12-12
> **santiagoward2000 said:**
> Una pregunta sobre esto: ¿alguien sabe si te lo cubre la garantía? Ya me contacté con la gente de Dell, pero todavía no me contestaron...

Bueno, me constestaron desde Dell. Esto es lo que me dijeron:
> Luego de verificar la informacion de su correo electronico me dirijo a usted indicandole que si en un futuro el disco duro de su computador llega a fallar **la garantia cubrira este daño, incluso si su computador esta funcionando con otro sistema operativo**. Lo que el computador ha perdido es todo servicio tecnico con respecto a software ya que al cambiar el sistema operativo no nos hacemos responsables de ningun tipo de problema de software.

Si el disco duro falla en un futuro se le brindara apoyo al momento de la instalacion y si es su deseo instalar Ubuntu nuevamente pues ese sera un servicio que no podremos brindarle.

A mí por lo menos me deja más tranquilo, y supongo que a los demás con este problema con alguna Dell también.
Saludos!

---

### Post by marianom on 2008-12-12
No he escuchado quejas del service de Dell así que me esperaba algo así. La duda es... ¿por qué te compraste una máquina con Windows? La próxima lamparita que él cambie en uno de sus yates, es gracias a vos :)

---

### Post by santiagoward2000 on 2008-12-12
> **marianom said:**
> No he escuchado quejas del service de Dell así que me esperaba algo así. La duda es... ¿por qué te compraste una máquina con Windows? La próxima lamparita que él cambie en uno de sus yates, es gracias a vos :)

Y, después de haber borrado la partición de recuperación y tenido que reinstalar el Vista y todos los drivers uno por uno como 5 veces pregunto lo mismo... Hay algunos programas que necesito para la facu, que hasta donde leí no andaban con wine, pero creo que la próxima veo bien cómo hacerlo con VMware o alguna otra máquina virtual.

---

### Post by sdennie on 2008-12-13
> 
Luego de verificar la informacion de su correo electronico me dirijo a usted indicandole que si en un futuro el disco duro de su computador llega a fallar la garantia cubrira este daño, incluso si su computador esta funcionando con otro sistema operativo. Lo que el computador ha perdido es todo servicio tecnico con respecto a software ya que al cambiar el sistema operativo no nos hacemos responsables de ningun tipo de problema de software.

Si el disco duro falla en un futuro se le brindara apoyo al momento de la instalacion y si es su deseo instalar Ubuntu nuevamente pues ese sera un servicio que no podremos brindarle.


Que grande Dell!  Ahora pongo el "hdparm -B1" hasta que se muere el disco y despues preguntar si hay un descuento a reemplazarlo con un SSD.  Bueno, primero debo fijarme si la garantia aca cubre las maquinas compradas en EE.UU...

---

### Post by marianom on 2008-12-13
vor... sos un argentino más!!! Acabas de acreditar lo necesario para recibir ciudadanía (eso y decir "che" cada 3 frases).

---

### Post by sdennie on 2008-12-13
> **marianom said:**
> vor... sos un argentino más!!! Acabas de acreditar lo necesario para recibir ciudadanía (eso y decir "che" cada 3 frases).

Jeje.  Aprendí castellano aca en los bares asi que me cuesta mucho a no decir "che", "bol...", etc.  Lastima que no dan cuidadanía por hablar lunfardo (Ya pregunté.  Me dijeron que no.)

---

### Post by santiagoward2000 on 2008-12-14
Bueno gente, la estuve probando, y con el "ugly-fix" ya no sube cuando está enchufada, la temperatura todavía no me subió de 35ºC, y no hace "click"... Parece que está todo perfecto ahora! :p
Gracias a todos!!!

---

