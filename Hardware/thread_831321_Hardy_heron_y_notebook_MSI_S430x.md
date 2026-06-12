---
title: "Hardy heron y notebook MSI S430x"
date: 2008-06-16
forum: Hardware
---

### Post by niko_3100 on 2008-06-16
Bueno gente pude vender mi notebook compaq v3415 (se la di a mi hermana a un precio super barato, no soy adorable??) y me compre esta MSI que la tube entre cejas durante un mes. La notebook en cuestion es una notebook marca MSI S430x con un sempron 3800+ es decir 2,2 ghz de clock y 256 kb de cache L2, 120 de disco, un 1 gb de ram aunque ahora ya tiene 2 jjeje, mother MSI (menos mal no? sino... seria el colmo), placa de video nvidia geforce go 6100 con hasta 256 megas de video compartida, pantalla 14,1, GARANTIA DE DOS AÑOS!!!!! a un precio de $2368. La verdad que la notebook es super compacta parece del tamaño de una de 13,3 pulgadas y ni hablar del peso, 2,2 kg con la bateria puesta y 1,8pico sin la bateria super liviana. Les cuento que me vino con un SO ubuntu XP o algo asi, en el local donde la compre le pusieron un ubuntu super parecido al xp, entonces dije "Chau si anda bien con esto con hardy vuela" y efectivamente asi fue... Levanto toooodo de una, sonido, mouse, las teclas FN, el acpi, todo todo todo. Cuando le fui a poner compiz me tube que bajar los driver propietarios de nvidia... lo cual fue todo normal saaaalvo porque cada ves que se apagaba la pantalla para ahorrar energia se colgaban las x cuando la apagaba tambien se colgaban las x, entonces con envy me baje el ultimo driver el 169.12 o algo asi. La cosa es que seguia andando igual hasta que probe desde envy los drivers 96.43.05 y ahi si andubo todo de diez, y todavia anda jej, asi que gente si quieren comprar esta notebook y dudan si funciona bien para ubuntu esta suuuuper comprobado por mi que anda de 10 salvo ese pequeño problemita pero que se soluciona super facil. Bueno si quieren pregunten en este post y les respondere sus dudas, la verdad que esta muy bien esta msi por el precio que pague. Un saludos ubunteross!!!!!

---

### Post by brunovecchi on 2008-08-02
Hola! Mirá, gracias a tu recomendación me compré la misma (misma misma) compu y estoy bastante contento... sobre todo por no haber tenido que pagar una licencia de Windows (es difícil conseguir esto en notebooks). 
Quería preguntarte por un problemita que estoy teniendo; no se me conecta a internet con la red cableada... la configuración que le puse es la misma que con mi pc de escritorio que conectada al módem de banda ancha reconoce la conexión de una, pero con la notebook no hay caso.
¿alguna ayuda? Les agradecería!

---

### Post by Hei Ku on 2008-08-02
Que tipo de modem tenes? Es adsl o cablemodem? Modelo del modem?

---

### Post by brunovecchi on 2008-08-02
Bueno, muchas gracias Hei Ku por ayudarme! Pero por suerte lo pude hacer andar. Bah, en realidad no hice mucho, fui a Administración->Red y configuré la parte de "red cableada" asignandole "Configuración automática por DHCP". Antes tuve que quitar el "modo itinerante".
Así que ahora si puedo decir que la compu anda 100% joya! Se las recomiendo. Tiene buen hard a muy buen precio: sempron 3800 2.2 gHz, 2 gb RAM kingston, HDD 120 gb, placa nVIDIa GeForce 6100, y lo mejor de todo: viene con ubuntu hardy preinstilado con todo andando, wi-fi inclusive. Me salio 2500, nada mal!

---

### Post by niko_3100 on 2008-08-02
Jaja viste... nada mal, y a muy buen precio. El cpu no sera doble nucleo pero tiene una velocidad mas que aceptable 2,2 hz es muuucho. Ahora te hago una consulta, te fijaste si con conky o algun programa para medir la temperatura del cpu te funciona? porque a mi siempre me da 40 grados, es decir termino de ver una peli y me sigue marcando 40 grados obvio que esta mal porque pones la mano y sale bastante aire calentito.

---

### Post by brunovecchi on 2008-08-02
No, la verdad no he probado eso todavía... ¿me pasarías tu archivo .conkyrc así lo pruebo acá en la mía?

---

### Post by niko_3100 on 2008-08-04
aca va, es simple pero dice todo lo importante que tenes que saber:

 UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#

# Create own window instead of using desktop (required in nautilus)
background yes
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer true
use_xft no

# Update interval in seconds
update_interval 2.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color black

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color orange}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine

${color orange}CPU 1 ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}

NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}
${top name 2} ${top pid 5}   ${top cpu 5}    ${top mem 5}
${top name 3} ${top pid 6}   ${top cpu 6}    ${top mem 6}

${color orange}MEMORY ${hr 2}$color
RAM: $mem/$memmax - $memperc% 
${membar 6}$color
Swap: $swapperc% 
${swapbar 6}$color

${color orange}DISK ${hr 2}$color
Root: ${fs_free_perc /}% ${fs_bar 6 /}$color 
Home: ${fs_free_perc /home/nicolas}% ${fs_bar 6 /home/nicolas}$color

${color orange}WIFI (${addr wlan0}) ${hr 2}$color
Down: $color${downspeed wlan0} k/s ${alignr}Up: ${upspeed wlan0} k/s
${downspeedgraph wlan0 25,140 000000 ff0000} ${alignr}${upspeedgraph wlan0
25,140 000000 00ff00}$color
Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan0}

---

### Post by brunovecchi on 2008-08-04
> **niko_3100 said:**
> aca va, es simple pero dice todo lo importante que tenes que saber:
[..]



Bueno, probé con tu .conkyrc y tengo el mismo problema que vos: la temperatura está clavada en 40 grados. Pero no creo que la culpa la tenga el sensor de la computadora; para mi el problema está en la aplicación "acpi", que es la que se encarga de colectar la información de temperatura. Digo esto porque en mi compu de escritorio con tu .conkyrc también marca 40 ºC.
Por otra parte, recuerdo que antes de formatear la laptop y reinstalarle Hardy (no me gustó demasiado cómo la habían configurado los de TecknoAr) había visto en Nvidia Settings (o algo así, se instala con los drivers del Envy) que la lectura de la temperatura del GPU funcionaba perfectamente, por lo que creo que la del micro se debería poder medir sin problemas...

---

### Post by Hei Ku on 2008-08-05
le corrieron el lm-sensors --autodetect para habilitar los modulos necesarios para medir la temperatura?

---

### Post by brunovecchi on 2008-08-05
> **Hei Ku said:**
> le corrieron el lm-sensors --autodetect para habilitar los modulos necesarios para medir la temperatura?

¡Muchas gracias por avisparme! Instalé el paquete "lm-sensors" (está en los repositorios) y luego corrí:
```
$ sudo sensors-detect
```

Y detectó un sensor de temperatura del micro. Agregó las siguientes líneas en /etc/modules:

```
# Chip drivers
k8temp
```

Después de reiniciar, el conky todavía seguía midiendo 40 grados, PERO haciendo desde la terminal

```
$ sensors
```

me tira:

```
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +29.0°C                                    
Core0 Temp:  +37.0°C  
```

Ahora, 1) cómo meter esto en el conky y 2) si esto es la verdadera temperatura, no lo sé. Supongo que iré chusmeando con el tiempo a ver si cambian los valores.

UPDATE:

El siguiente comando extrae las temperaturas:

```
 sensors | awk '{ if ( $1 == "Core0" ) { print $3 } }';
```

Ahora haciendo esto me tira:

```

+30.0°C
+38.0°C

```

Vieron que la temperatura es 1ºC mayor que antes? Quiere decir que funciona! Creo que se debería poner esto en el conky, no?

---

### Post by niko_3100 on 2008-08-05
Que raro a mi me dice que tengo dos core: core0 y core1, el core0 me dice -49 ºc  y el core1 +34ºc que raro... encima en negativo el primer core....

---

### Post by niko_3100 on 2008-08-12
bueno aparentemente el core1 con sensors me marca bien, no entiendo porque me marca un core0 con -49 grados jeje, como podria poner este dato en conky? intente pero no pude conseguirlo satisfactoriamente. Por otro lado ya llego al pais la msi wind, que compite con la asus eee pc pero esta wind tiene lcd de 10 pulgadas, disco de 80... creo que es mas computadora y se puede llegar a usar para muchas cosas, en youtube hay videos de esta notebook msi wind corriengo juegos onda warcraft 3, pero lo malo es que no viene con unidad de cd/dvd entonces... como se podria instalar ubuntu? se puede por pendrive?

---

### Post by faktorqm on 2008-08-13
si, por supuesto que se puede. es mas, tambien se puede crear algo estilo "live pendrive" que es lo que quiero hacer yo. TU ubuntu personalizado, en cualquier computadora que soporte booteo por usb :P, suena grosso no?
lo que pasa es que no se si me conviene uno de 8gb o de 16gb... salu2!!

---

