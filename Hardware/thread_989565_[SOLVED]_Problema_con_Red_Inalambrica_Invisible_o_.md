---
title: "[SOLVED] Problema con Red Inalambrica Invisible o No accesible."
date: 2008-11-21
forum: Hardware
---

### Post by User21 on 2008-11-21
Poseo una placa wireless Realtek RTL 8185 IEEE 802.11 a/b/g conectada a un router TP-LINK Wireless Router WR340G . Esta pc cuenta con WIN XP y tengo Intrepid Ibex en un disco externo USB. 
Desde win, puedo ver 3 redes inalambricas y conectarme a una de ellas que me da el acceso a Internet (sin problemas), mientras que en Intrepid solo veo 2. Justamente la que falta me da Internet. 
Los parametros de red que veo en Win son:

SSID: MultiCXan
Cifrado: WEP
Clave: 12543
Indice de Clave: 1
Autenticacion: Abierta
IP: 192.168.1.100
Mascara de subred: 255.255.255.0
Puerta de enlace: 192.168.1.1
DNS: 200.42.0.111  ;  200.42.97.111
Direccion Fisica: 00-19-e0-66-e1-5d
Host: zulma


Desde Intrepid puedo ver 2 redes, pero una de ellas no aparece, y no puedo conectar a Internet. Tampoco puede verse como red oculta, ni agregandola a mano. Nunca me deja ingresar. Alguna idea ?
Todo esto suponiendo, que la tarjeta de red inalambrica está reconocida, ya que veo otras redes wi fi...

PD: No tengo acceso fisico al router como para usar un cable RJ45, ni acceso de administrador al configurador web del Router.

---

### Post by arielcabral on 2008-11-22
Para que no te la muestre solo puede ser por dos cosas:
1.- Alcance (qué tan lejos estás del router?)
2.- Mal funcionamiento o intalación de la placa y en tal caso revisemos la forma en la que instalaste el driver (ndiswrapper o es encore y usaste el driver linux?)

---

### Post by sergiom99 on 2008-11-22
> **User21 said:**
> 
PD: No tengo acceso fisico al router como para usar un cable RJ45, ni acceso de administrador al configurador web del Router.

no te estaras choreando la señal no?? :lolflag:

si haces
```
  sudo iwlist eth1 scanning 
```
eth1= tu placa

te muestra las 3 redes?

---

### Post by luks911 on 2008-11-22
Hace poco alguien en el foro tenía problemas con una placa con ese chip y era un problema de drivers, como sugiere Ariel. La solución que encontramos fue instalar linux-backports-modules y cargar uno de los módulos que incluye. Era en Hardy pero el módulo sigue estando en el paquete de Intrepid. Sería algo así:

1) Instalás backports
```
sudo aptitude install linux-backports-modules-intrepid
```

2) Cargás el módulo

```
sudo modprobe rtl8180
```

3) Si todo salió bien, lo agregás para que se cargue en el inicio

```
echo rtl8180 | sudo tee -a /etc/modules
```

Todo esto asumiendo que no lo hayas hecho antes :-P

En su momento la información la saqué de [acá]("http://willdaniels.co.uk/articles/howto-guides/10-howto/15-rtl8180-hardy") [0].
Y el thread del problema era [este]("http://ubuntuforums.org/showthread.php?t=955160")[1].

Saludos

[0] [http://willdaniels.co.uk/articles/howto-guides/10-howto/15-rtl8180-hardy](http://willdaniels.co.uk/articles/howto-guides/10-howto/15-rtl8180-hardy)
[1] [http://ubuntuforums.org/showthread.php?t=955160](http://ubuntuforums.org/showthread.php?t=955160)

---

### Post by User21 on 2008-11-23
Pues hice todo lo que luks911 sugirió e incluso seguí un [troubleshooting]("http://help.ubuntu.com/8.10/internet/C/troubleshooting.html"), imprimiendome todos los enlaces y muuuchos tutos, pero no. No veo esa red. Lo que mas bronca me da que ween la ve sin problemas. Incluso instale wifi-radar y me detecta las otras 2 redes, pero NO LA QUE TIENE INET.
La cuestion es que estoy de casero en lo de mi prima. Ellos se conectan via wi fi a un router comunitario, y solo sé los datos que me proporciona equis-pé y la clave que me dieron. Me llevo el disco extraible con Intrepid a todos lados, y pensaba usar su PC con Ubuntu. Una pena. Tendré que pasar una semana con el hijo tonto de William..?

la salida de sudo iwlist wlan0 scanning es:
```
sudo iwlist wlan0 scanning
wlan0     Scan completed :
          Cell 01 - Address: 00:15:6D:63:49:1E
                    ESSID:"Red 500"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=9/100  Signal level:15/65  
                    Encryption key:on
                    IE: Unknown: 000752656420353030
                    IE: Unknown: 010882848B968C9298A4
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD2A000C42000000011E0000000033660902FF0F303031353644363334393145000000000000000005028509
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:tsf=000000018b0cd184
                    Extra: Last beacon: 560ms ago
          Cell 02 - Address: 02:15:6D:63:49:1E
                    ESSID:"wlan2"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=10/100  Signal level:15/65  
                    Encryption key:on
                    IE: Unknown: 0005776C616E32
                    IE: Unknown: 010882848B968C9298A4
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: DD2A000C42000000011E0000000033660902FF0F303031353644363334393145000000000000000005028509
                    IE: Unknown: DF24011E0000000033660902FF0F303031353644363334393145000000000000000005028509
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:tsf=000000018b0cded8
                    Extra: Last beacon: 556ms ago


```
Como se ve, aun detecta solo 2 redes. Ahora mismo estoy en EquisPe en la red de la cual les hablo...

---

### Post by sergiom99 on 2008-11-23
extraño....
no se que mas decirte.
si probas de crear la conexion a mano poniendo los datos del router y la wlan?
Se que hay redes que no emiten el SSID y te conectas creando todo a manopla, pero nunca lo probe.

---

### Post by User21 on 2008-11-24
Lo solucioné [instalando los drivers de equispé]("http://www.guia-ubuntu.org/index.php?title=Instalar_driver_de_tarjetas_WIFI_con_Ndiswrapper") de la [**RTL 8185**]("http://tc.versiontracker.com/product/redir/lid/767787/x86-8185%281094%29.zipx86-8185%281094%29.zip"), mediante Ndiswrapper. Aparentemente, con el modulo rtl8180 no era suficiente (los de linux-backports-modules-intrepid ), y seteando la red manualmente.
 Ahora, desde Ubuntu, siento la red inalambrica mas rapida! o_O Antes descargaba a 75 kpbs, ahora estoy en 100 todo el tiempo. 
Muchisimas gracias a todos!!! :)

---

### Post by marianom on 2008-11-24
> **sergiom99 said:**
> 
Se que hay redes que no emiten el SSID y te conectas creando todo a manopla, pero nunca lo probe.

Exacto, al router lo configuras para que no haga broadcast de tu red y queda en invisible. No creo, de todos modos, que hagan eso en un wifi comunitario.

---

### Post by sergiom99 on 2008-11-24
si me lo imaginaba, pero yo le decia que pruebe de agregar la conexion por mas que el network manager no se la detecte.
al final era solo problema de drivers.

---

