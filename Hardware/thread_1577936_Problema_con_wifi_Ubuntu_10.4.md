---
title: "Problema con wifi Ubuntu 10.4"
date: 2010-09-19
forum: Hardware
---

### Post by mchojrin on 2010-09-19
Hola:

  Estoy teniendo un problema para conectarme a mi red wifi. Este es mi lspci:

[HTML]00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce Go 6100] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)[/HTML]

  Recientemente me pasé de OpenSuse a Ubuntu 10.4, en OpenSuse no tenía problemas con la conexión a la wifi, pero ahora no puedo conectarme con la seguridad habilitada. La placa esta funcionando bien, me conecta a alguna otra red (que no tenga seguridad habilitada) e incluso me conecté a mi propia red pero sin la seguridad y la verdad es que no quiero dejar las cosas así.
  Probé cambiarle el SSID, el tipo de seguridad, la password... en fin, unas cuantas cosas, pero nada... 

  Tuve también algunos problemas con el depósito de claves, pero eso lo solucioné aparentemente... alguna idea? Gracias!

---

### Post by mchojrin on 2010-09-19
Hola:

  Un poco más de info. Acabo de instalar wicd según leí por ahí que puede resultar mejor que NetworkManager. Por lo menos me da un poco más de info sobre las redes que tengo alrededor. Ahora veo que el problema que me está pasando es que al tratar de conectar a cualquier red que no sea la cableada, siempre termina intentando conectarse a la misma red wifi (que no es la mia:confused:).

  De cualquier manera creo que me voy a quedar con wicd, pero... me gustaría conectarme a mi red privada por wifi :(

  Gracias por la ayuda!

---

### Post by mchojrin on 2010-09-19
Yo otra vez, je... parece que se solucionó el problema cuando desinstale el network-manager y dejé sólo el wicd. Ahora tendría que ver qué pasa cuando reinicie si se conecta automáticamente. Gracias!!

---

### Post by alfplayer on 2010-09-20
En realidad, la versión de Ubuntu es 10.04.

---

### Post by mchojrin on 2010-09-21
Hola:

  Bueno... acá estoy otra vez... Parece que me apuré a dar por cerrado el tema. La verdad es que ya no sé qué puede estar pasando. Por ahora lo que parece que pasa es que me puedo conectar sin problemas a mi red si la dejo desprotegida. En cuanto le pongo un WPA empieza a fallar. A veces directamente no me conecta porque dice que la clave es incorrecta, otras se conecta pero pierde la conexión al toque... no sé. Ahora estoy conectado mediante wifi pero a la red insegura. Ayer estuve viendo que alguna otra gente tuvo problemas con estas placas (BCM4311) en 10.04, seguí algún tuto para cambiar el driver, pero me parece que tengo el driver que tiene que ser (Broadcom STA). Alguna idea? Gracias!

---

### Post by hectorivand on 2010-09-28
Hola Master, tengo el mismo problema y mi wifi es una realtek, con lo cual me parece es que es algo medio general.

Todavia no le encuentro la vuelta, cuando lo haga la publico por acá.

Saludos
Nacho

---

### Post by guillermolisi on 2010-09-28
> **hectorivand said:**
> Hola Master, tengo el mismo problema y mi wifi es una realtek, con lo cual me parece es que es algo medio general.

Todavia no le encuentro la vuelta, cuando lo haga la publico por acá.

Saludos
Nacho
Los chips mas nuevos de Realtek tienen muy buen soporte con el kernel que usara la version 10.10, el 2.6.35.

Probe una antena USB Encore clase N con chip Realtek (de los mas nuevitos) con ese kernel y anduvo perfecto.

---

### Post by hectorivand on 2010-09-28
> **guillermolisi said:**
> Los chips mas nuevos de Realtek tienen muy buen soporte con el kernel que usara la version 10.10, el 2.6.35.

Probe una antena USB Encore clase N con chip Realtek (de los mas nuevitos) con ese kernel y anduvo perfecto.

No probe todavía 10.10, iba a hacerlo, pero faltando tan poquito para que salga el final, espero unos días. De paso, cañaso, resuelvo el problema de la Wifi.

Gracias por la data.

Saludos
Nacho

---

### Post by chulelinux on 2010-10-09
Para sumar... yo que alguna vez creí que ya lo había solucionado (hay algún post de esto) me pasa algo muy parecido con la enlwi G2 que nunca pude hacer andar de modo estable con ubuntu. Probé todo y no he podido. El tema viene que el chip rlt no es muy compatible que digamos como si atheros. A ver si la 10.10 permite mejorar esto
Slds.

---

### Post by hectorivand on 2010-10-09
Chule, el tema de mi wifi lo resolvi, consegui unos drivers para Linux por parte de Realtek y no he tenido problemas. 

Que modelo es tu placa?

Saludos
Nacho

---

### Post by chulelinux on 2010-10-09
Hola y gracias Nacho... a ver si sale esta... el modelo es enlwi G2 (pci) con chip realtek 8185. En su momento había bajado los driver para linux y no me habían andado... pero lo voy a probar nuevamente ahora que me decís que te anduvo  bien a vos. 
Por las dudas, recordas el modo de como los compilaste y si desistalaste algo? No se si está bien seguir el hilo por aquí sino abro otro post. 

Saludos

---

### Post by hectorivand on 2010-10-09
Te paso los drivers para la 8185... seguí las instrucciones del readme, al pie de la letra y va a funcionar.

Este es el enlace.:

[http://www.mediafire.com/?b9nzy0k10o119vh](http://www.mediafire.com/?b9nzy0k10o119vh)

Nota, el readme no dice nada, pero en el primer paso, arranca con sudo y lo que sigue.

Cuenta como sigues después de esto

Saludos
Nacho

---

### Post by chulelinux on 2010-10-11
Seguí los pasos del readme de la placa (enlwi G2) que me pasaste Nacho pero con el método 1 no anda.. Directamente  luego de reiniciar hago "iwconfig" y no aparece wlan e "ifconfig wlan0 up" tira que no existe el dispositivo. Es como que no se instalara y creo que no cometo ningún error al instalarlo.
Utilizando el método 2 corro ./wlan0up (parado en el directorio en que descargué el controlador) y me carga. 
Ahí comienza a andar... pero luego de un rato es como que va perdiendo intensidad (primero encuentra por ej 10 redes, luego 7, luego 2) y al final se corta. Aparte con este método siempre habría que correr manualmente el script no?
Por las dudas aviso que no tengo Network ni wicd instalados ni nada, y dejo el modo en que cargo los controladores abajo.

Saludos y gracias por cualquier ayuda

<<Method 1>>
Running the scripts can finish all operations of building up modules from source code and start the nic:
    1. Build up the drivers from the source code
        make

    2. Install the driver to the kernel
        make install
        reboot

    3. bring up wlan if nic is not brought up by GUI, such as NetworkManager
        ifconfig wlan0 up

        Note: use ifconfig to check whether wlan0 is brought up and use iwconfig to check your wlan interface name,
        since it may change wlan0 to wlan1,etc.

<<Method 2>>
Or only load the driver module to kernel and start up nic.
    1. Build up the drivers from the source code
        make

    2. Load driver module to kernel and start up nic.
        ./wlan0up

        Note: when "insmod: error inserting 'xxxx.ko': -1 File exists" comes out
        after run ./wlan0up, please run ./wlan0down first, then it should
        be ok..
        Note: If you see the message of "unkown symbol" during ./wlan0up, it
        is suggested to build driver by <<Method 1>>.

---

### Post by hectorivand on 2010-10-11
Hace los pasos del modo uno, pero en SUDO, asi nomás, por algún motivo de permisos no funciona.
 
proba con sudo make
 
sudo make install
 
reboot
 
Si no te reconoce nada en la wlan0 es por que no es la interfaz.
 
Saludos
Nacho

---

### Post by chulelinux on 2010-10-12
Probé varias veces y reconoce la conexión, sí... pero anda totalmente inestable y se corta al rato... Así que sigue sin solución. El tema es que podría ser la placa pero en el so de las ventanas me anda de 10... Ahora instalé maverick a ver que pasa pero ya voy viendo que no funca... si alguien sabe de algo más bienvenido y gracias por la ayuda brindada hasta ahora...

---

### Post by hectorivand on 2010-10-12
Instala network Manager y proba de vuelta, son los drivers oficiales, si no te anda con eso, la verdad, vas a estar j****o.

a menos, que le estés pifiando al chipset de la placa.

---

### Post by chulelinux on 2010-10-13
Y así es... le di casi un par de años de posibilidad a la enlwi pero no la pude hacer andar así que saldrá fuera del gabinete a pasear porque quiero dejar el equipo 100% linux y no tener que usar las ventanas cdo me piden internet... Supuestamente el modelo que tengo y chipset es compatible pero a mí no me anda ni a gancho y por lo leído a muchos otros tampoco.

En fin, gracias por la ayuda y esperemos con la próxima placa tener más suerte. Slds

---

