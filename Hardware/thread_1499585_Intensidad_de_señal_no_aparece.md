---
title: "Intensidad de señal no aparece"
date: 2010-06-02
forum: Hardware
---

### Post by mcisternas on 2010-06-02
Hola gente, tanto tiempo. Esperando que todos se encuentren bien, recurro a ustedes para lo siguiente.

Ayer mi cuñado me trajo un Router D-Link DIR 600 que reemplazó al otro viejo aparato que bien carreteado lo tenía. Lo configuré sin más novedades. Pero al momento que pruebo la red en Ubuntu Lucid Lynx, me percato que no se encuentra la típica "barra" que muestra la intensidad de la señal. En su lugar, están dos pc's y una marca roja  y blanca, lo que me hace suponer que algo anda mal. Apesar de esto, puedo navegar sin ningún problema.

[U][[IMG]http://img199.imageshack.us/img199/8076/seal1f.jpg[/IMG]]("http://img199.imageshack.us/i/seal1f.jpg/")

[/U]Además, al momento de hacer un clic en estos dos pc's, noto que en realidad "no estoy conectado" a mi red, *Marleke*.

[[IMG]http://img12.imageshack.us/img12/8304/seal2rk.jpg[/IMG]]("http://img12.imageshack.us/i/seal2rk.jpg/")

No sé qué pasa. No sé si habré hecho algo mal al momento de configurar el router o algo en Ubuntu anda mal. Mi tarjeta inalámbrica es una famosa Broadcom BCM4311. Si necesitan más información, no duden en solicitarla.

Un abrazo.

---

### Post by asterix77 on 2010-06-02
Al parecer uas network manager para conectarte.

pero ¿como conectas el router al pc, vía cable o vía wifi?¿o lo conectastes a un modem?. Si lo configurastes me imagino que lo conectastes vía cable, y a lo mejor por eso te aparece ese icono.

La broadcom BCM4311 por lo general viene en la laptop dell, ¿estás tratando de conectarte al router con una laptop al router?¿es eso?

Faltan más antecedentes sobre como tienes la conexión ya sea física o inalámbrica, y cuantos pc están involucrados.

Tengo la sensación de que creastes una conexión inalámbrica nueva la cual no tiene nombre, ¿que pasa si a la red inalámbrica le das a desconectar y pinchas sobre Marleke?

ejecuta en la terminal iwconfig en la terminal tanto conectado como desconectado, y pégalos acá.


Saludos

---

### Post by mcisternas on 2010-06-02
Hola, gracias por responder.

Tengo un pc de escritorio(Windows xp) el que va conectado al router, y  tengo un Compaq Presario C708LA  con Lucid Lynx.

El router al pc de escritorio lo conecto por medio de cable. Y el router lo configure por medio de ese pc. Con el notebook cuando me "conecto" a la red, no aparece la intensidad de la señal, aunque puedo navegar normalmente. Cuando le hago clic en *Desconectar* y me conecto nuevamente vuelve a pasar lo mismo: no hay intensidad y me veo como *no conectado*.
 
Iwconfig como no conectado:
```

:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:199
          Rx invalid nwid:0  invalid crypt:1  invalid misc:0

:~$ iwconfig
```Iwconfig estando conectado

```
:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:4  Signal level:189  Noise level:199
          Rx invalid nwid:0  invalid crypt:1  invalid misc:0

:~$ 
```Saludos

---

### Post by mcisternas on 2010-06-03
Hola gente, he solucionado el problema de la siguiente manera:

Entré al Home del router y desactivé la opción 802.11 Mixed n/g/b y en su lugar activé 802.11 Mixed g/b. Cosas de la vida...

Gracias al compañero que ayudó :)

Saludos.

---

