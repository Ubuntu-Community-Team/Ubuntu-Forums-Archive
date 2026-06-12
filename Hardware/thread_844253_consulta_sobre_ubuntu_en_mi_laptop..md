---
title: "consulta sobre ubuntu en mi laptop."
date: 2008-06-29
forum: Hardware
---

### Post by gabyrsh on 2008-06-29
Hola como estan?, son muy nuevo en ubuntu, ya lo he estado provando hace unos meses  en mi pc de escritorio, ahora bien, me he comprado una laptop DELL XPS M1330 y le he instalado el Ubuntu 8.04 64 bits LTS. Ahora bien, la instalacion fue exitosa, hasta me ha detectado la red wireless =), mi pregunta es la siguiente, he leido en algun sitio que esta version ubuntu con esta laptop, tiene un problema que deja encendido los FAN todo el tiempo y no regula, provocando asi un desgaste del mismo, ademas que ubuntu le quita vida al disco rigido. Esto es verdad? si es asi, se puede solucionar?.:confused:

La verdad que me gusta ubuntu y quiero tenerlo.:guitar:
Ademas de esto alguna recomendacion acerca del ubuntu en mi laptop?

Muchas gracias por su paciencia.
Un Abrazo.

---

### Post by sergiom99 on 2008-06-29
Hola gabyrsh, bienvenido.
Es cierto, hay un problema en TODOS los OS, no solo en ubuntu, con los discos rígidos de laptop. Te recomiendo mirar este thread que explica todo y están siempre discutiendo el tema. Ahí mismo esta el parche para zafar el problema.
[http://ubuntuforums.org/showthread.php?t=805570](http://ubuntuforums.org/showthread.php?t=805570)

Aplicando el parche que corresponda para tu versión y disco, y después mirando como cambia el Load_Cycle_Count mientra la estas usando lo vas controlando un poco y vas a ver que no cambia tan frecuente como sucede sin el parche.
```
sergio@kubuntu:~$ date; sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)'
dom jun 29 13:36:32 ART 2008
190 Temperature_Celsius     0x0022   069   049   045    Old_age   Always       -       520814623
193 Load_Cycle_Count        0x0032   099   099   000    Old_age   Always       -       17851
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       31 (Lifetime Min/Max 11/51)
 
```
Espero te sirva.

---

### Post by gabyrsh on 2008-06-30
Hola, gracias por la respuesta, a ver si voy entendiendo, recien hice los primeros pasos y en el smart monitor, me ha dado los siguientes valores:
 
```

 sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)'
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       343
194 Temperature_Celsius     0x0022   113   102   000    Old_age   Always       -       34


```
Esto esta mal? no entiendo bien el concepto de lo que varia, y como obtenerlo. Me podrias explicar un poquito mas?

Muchas Gracias.

---

### Post by gabyrsh on 2008-06-30
hola de nuevo, bueno viendo varioos sitios de internet eh entendido finalmente el problema, en mi caso el raw value del disco, ha pasado de 343 a 377 en solo 30 minutos, es demasiado creo. ahora bien, quisiera saber si el parche a aplicar es compatible con este modelo de disco:

```
Device Model:     WDC WD3200BEVT-75ZCT0 
```

Otra consulta, con las versiones de Window$ tambien pasa lo mismo? me interesa esta informacion sobre le manejo de este problema en los OS. Muchas Gracias/

---

### Post by sergiom99 on 2008-06-30
No estoy completamente seguro de los modelos afectados. Por el cambio del valor en tan poco tiempo parecería que sí.

Dicen que el problema es de todos los OS.
Yo te aconsejo que trates de leer el tema completo del thread que te pasé y en todo caso consultarlo directamente ahí, así te responden los que saben del tema.

---

### Post by sdennie on 2008-06-30
Yo también tengo un XPS m1330 y no tengo ningún problema con el fan.  Si solo tenés 343 Load_Cycle_Count despues de usar Ubuntu por un par de meces, no vas a tener ningún problema con la vida del disco.  La gente que tiene 50000 o 100000 después de mes tiene un problema.

---

### Post by niko_3100 on 2008-07-01
Tu notebook no tiene un led que indica cuando el disco esta trabajando o no?? Mi msi si tiene y el led realmente funciona porque cuando se prende el led y acercas la oreja escuchas el ruido del disco trabajando.

---

### Post by gabyrsh on 2008-07-10
Probe haciendo esto

sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)'


Y cada mas o menos 15 minutos el RawValue me sube de 2 a 3 unidades. Esto es normal?

---

### Post by sdennie on 2008-07-10
> **gabyrsh said:**
> Probe haciendo esto

sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)'


Y cada mas o menos 15 minutos el RawValue me sube de 2 a 3 unidades. Esto es normal?

Si.  En realidad es perfecto.

---

### Post by gabyrsh on 2008-07-11
Mi consulta es la siguiente, si pongo en la consola:
```
sudo hdparm -B 254 /dev/sda 
``` 
Los RawValue yo no bajan mas, y se quedan estáticos. Es bueno dejarlo asi? que no bajen los RawValue. O Se recomienda dejarlo como lo tenía que cada 15 minutos me sumen 2 rawvalue?.

Desde ya muchas gracias por su colaboración.:lolflag:

---

### Post by sdennie on 2008-07-11
No te recomiendo usar "hdparm -B 254" si no tenés un problema de Load_Cycle_Count muy grave.  En serio te digo: 2 Load_Cycle_Count cada 15 minutos es perfecto.  Con 8 por hora, en 9 años, capaz que vas a tener un problema con Load_Cycle_Count.  ;)

---

