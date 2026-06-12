---
title: "config aviso bateria baja"
date: 2008-10-11
forum: Hardware
---

### Post by sergiom99 on 2008-10-11
hola gente, estoy teniendo un problema con el aviso de batería baja.
resulta que directamente dice algo así como "la batería esta por agotarse, hibernando ahora" y acto seguido hiberna.
En el Kpowermanager está puesto que cuando la batt esta por debajo de 5min tiene que hibernar.

Hay alguna manera de hacer que avise antes? O sea, yo quiero que primero me avise que se esta terminando y de última hiberne, pero que me dé tiempo de buscar el cargador y enchufarla.

gracias!

---

### Post by Mauro22 on 2008-10-11
Si no me equivoco usas KDE y con el SuperKaramba se puede poner un monitor de la bateria y era altamente configurable.

---

### Post by sergiom99 on 2008-10-11
mauro, no pude encontrar ninguno que me funcione.
Uso el AERO AIO que esta barbaro, pero la parte de energía en mi laptop no funciona y no muestra data.

sabes cual funciona?
gracias

---

### Post by Mauro22 on 2008-10-11
No ni idea, tengo gnome y pc de escritorio y en la notebook tengo puppylinux :D


Te tiro lo --unico-- que encontre:

Usando crontab, en este caso un sonido te avisa cuando quieras, pero podes cambiar por lo que sea.

```

# apt-get install acpitool cron grep mplayer
$ crontab -e
*/10 * * * * /usr/bin/acpitool | grep 00:0 && mplayer /home/pepito/sounds/alarm.mp3


```

---

### Post by sergiom99 on 2008-10-11
gracias, es algo, pero no es la solucion que mas me gusta.
voy a seguir buscando.

---

### Post by faktorqm on 2008-10-14
Hola, estuve buscando una hora pero no encontre demasiado, lo cual me preocupa...

Ayuda de kpowersave: [http://powersave.sourceforge.net/kpowersave/index.html](http://powersave.sourceforge.net/kpowersave/index.html)

post en kde.es: [http://www.kubuntu-es.org/foro/200809/administrador-energia-kde4-notebook](http://www.kubuntu-es.org/foro/200809/administrador-energia-kde4-notebook)

Espero que haya servido de algo, incluso le podes preguntar al chabon ese como hizo para poner el icono con el nivel de la bateria.
Si abris una consola y escribis "acpi", que pasa? salu2!

EDITO: por fin encontre algo! [https://launchpad.net/ubuntu/+source/gnome-power-manager/+bug/39413](https://launchpad.net/ubuntu/+source/gnome-power-manager/+bug/39413)
tambien [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/114412](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/114412) (esta relacionado)

---

### Post by sergiom99 on 2008-10-14
gracias capo, esta tarde lo pruebo a ver que onda.
salutes! sergio

---

### Post by Mauro22 on 2009-04-18
Revivo post!!

**ACTUALIZADO 19 de Abril**

Ahora que tengo notebook, hice este script para que avise en bateria baja, bateria muy baja y apague cuando que muy pero muy poco...

ATENCION: Usenlo a modo de prueba... Solo GNOME, modifiquen los valores de acuerdo a la capacidad de su bateria, la mia es de 4400 mAh y estos valores son justos para el aviso y el apagado..

Tienen que cambiar, los valores de mAh de acuerdo a su bateria, el path de BAT0 o BAT1 de acuerdo a su caso, y por ultimo el path de mpg123 para que lee el archivo de la alarma...

```
#!/bin/bash
# Hecho por mauro22
# Ubuntu Ar
# Under GNU/GPL
# ----------------------------------------------------
# Se recomienda usar con crontab cada 1 o 2 minutos
# Por defecto:

# Avisa a los 1100 mAh
# Alarma a los 800 mAh
# Apaga a los 500 mAh

# Alarma que avisa de bateria baja e hiberna el equipo
# previo aviso.


Min=1100 #Primer Nivel
Low=800 #800 mAh representa el el 18% en una bateria de 4400 mAh
Apa=500 #Aca se apaga 

#Si esta en 'charging' salimos, no tiene sentido...
Cargando=$(cat /proc/acpi/battery/BAT0/state | grep "charging" | cut -c26-33)

if [ $Cargando = "charged" ]; then
    echo "Cargando y trabajando con AC al 100%"
    exit 0
fi

if [ $Cargando = "charging" ]; then
    echo "Cargando y trabajando con AC"
    exit 0
fi

#Obtenemos el nivel actual y directo a la variable Nivel
Nivel=$(cat /proc/acpi/battery/BAT0/state | grep "remaining" | cut -c25-29)

#Comenten el anterior y descomenten este para probar valores.
#Nivel=600
echo "Nivel actual en mAh: "$Nivel #Mostramos el nivel


#Si es muy bajo, apagamos, habiendo avisado antes..
if (( "$Nivel" < "$Apa" )); then
       echo "Apagando equipo..."
       gnome-power-cmd.sh shutdown
       exit 0
fi


#Comparamos, primero si esta debajo de Low, tocamos alarma 
if (( "$Nivel" < "$Low" )); then
       echo "Bateria en Nivel Critico"
    mpg123 /home/mauro/Documentos/warn.mp3
       zenity --warning --text 'Bateria en Nivel Critico'
       exit 0
fi
#Estamos por encima de Low, asi que verificamos contra Min
      
if (( "$Nivel" < "$Min" )); then
           echo "Bateria Agotandose..."
        zenity --info --text 'El nivel de la bateria esta bajo'
else
    #Estamos por encima de Min, nada para hacer ahora....
    echo "Todo bien por ahora."
fi

```Tiene alarma sonora y visual en "Nivel Critico", visual solo en "Bateria Baja" y luego apaga cuando quedan 3 minutos de bateria..

Usen crontab:

```
 */2 * * * * export DISPLAY=:0 && /home/mauro/Documentos/alarma_bat_baja >> /home/mauro/Documentos/alarma.log
```


ese ejemplo es para correrlo cada 2 minutos, cambien el path del script y si quieren el del log.


:popcorn:

---

