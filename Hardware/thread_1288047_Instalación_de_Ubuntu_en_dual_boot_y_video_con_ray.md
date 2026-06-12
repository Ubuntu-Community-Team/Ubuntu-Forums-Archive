---
title: "Instalación de Ubuntu en dual boot y video con rayas"
date: 2009-10-10
forum: Hardware
---

### Post by emicolarusso on 2009-10-10
Buenas noches, soy nuevo por acá. Estoy incursionando por primera vez en Ubuntu y segui la guia que ustedes plantean en este post, todo barbaro hasta que entra a leer el cd y la pantalla se ve toda rayada se ve que carga el programa de instalacion y todo, pero no se ve mucho porque esta todo rallado... estuve viendo de ver otras alternativas pero nada, ¿alguien me podrá dar una mano con esto?

Saludos y suerte.
Emiliano.

---

### Post by ramiro_md on 2009-10-15
Buenas Emiliano..quedo un poco olvidado este thread :P. Te comento, estaría buen oque pongas algunos datos técnicos sobre tu compu (procesador, memoria, discos, placa de video, etc...) para que nos sea más fácil detectar la falla.
De momento te podría aconsejar que grabes nuevamente la imagen de cd o que directamente bajes otra. Si el problema persiste podrías bajar una imagen de cd de algun alternate.
[B][U]
Descarga imagen de alternate:[/U][/B] solo te pude conseguir los de ubuntu 8.10.
[[COLOR="DarkOrange"]_32 Bits_[/COLOR]]("ftp://ftp.rediris.es/sites/releases.ubuntu.com/releases/intrepid/ubuntu-8.10-alternate-i386.iso")
[[COLOR="DarkOrange"]_64 Bits_[/COLOR]]("ftp://ftp.rediris.es/sites/releases.ubuntu.com/releases/intrepid/ubuntu-8.10-alternate-amd64.iso")

---

### Post by emicolarusso on 2009-10-15
Gracias Ramiro por la ayuda, voy con lo que me pediste:
Disco rigido  80gb ( Particionado a la mitad )
Memoria RAM 504 Mb
Pentium 4 2.66 GHz
Placa de video on board

Tengo instalado Windows XP Service Pack 3, pero creo que eso no debe molestar mucho.
Vos me decis lo de bajar una imagen nueva, ¿pero tendrá algo que ver? ( Te lo pregunto desde la ignorancia ) Porque tengo un CD original, o no se como lo llaman... autentificado de Ubuntu 9.04 edicion de escritorio que me regalaron en la facultad.
Muchas gracias!

---

### Post by lrcaballero on 2009-10-15
Buenas Emiliano, dices que tienes una Pentium 4 y corres Win. XP verdad? asegurate de que el cd/dvd sea i386(para 32 bits) y NO para i686 ya que esta ultima es para una pc de 64 bits. En una ocasion yo compre una revista donde me regalaron un Distro de Ubuntu y me salio defectoso no me dejaba entrar al desktop. Y tambien quise instalar Fedora pero el Distro DVD era i686 y en aquel entonces mi laptop era 32bits osea i386. Checate esto a ver si te ayuda de algo??? si no me escribe en privado.....

Luis:popcorn:

---

### Post by josecuervo86 on 2009-10-15
Esos problemas de resolución me suenan a que hay problema con el hardware. Como te sujirio Ramiro, probaria con la versión alternate

---

### Post by staar on 2009-10-16
> **lrcaballero said:**
> Buenas Emiliano, dices que tienes una Pentium 4 y corres Win. XP verdad? asegurate de que el cd/dvd sea i386(para 32 bits) y NO para i686 ya que esta ultima es para una pc de 64 bits. En una ocasion yo compre una revista donde me regalaron un Distro de Ubuntu y me salio defectoso no me dejaba entrar al desktop. Y tambien quise instalar Fedora pero el Distro DVD era i686 y en aquel entonces mi laptop era 32bits osea i386. Checate esto a ver si te ayuda de algo??? si no me escribe en privado.....

Luis:popcorn:

no. i386 e i686 son de 32 bits, solo que la segunda corre solo en procesadores domésticos más nuevos (de pentium 4 para adelante) debido a que aprovecha determinadas instrucciones solo presentes en estos últimos, i386 funciona en procesadores compatibles con los viejos intel 386 (desde estos hacia adelante). de 64 bits es AMD64 (a veces llamada x86_64).

emiliano, decís que tenés una placa de video onboard, podrías especificar la marca? te aviso que las placas marca VIA o SiS carecen de buenos drivers para GNU/Linux, y es prácticamente imposible lograr aceleración 3d con ellas (no se puede usar compiz) o incluso lograr un rendimiento aceptable sin usar 3d, esto es debido a que estos fabricantes no hacen los drivers para nuestro SO...

saludos

---

### Post by emicolarusso on 2009-10-16
Ante todo, muchas gracias por las respuestas. Les comento que la placa de video on board me dice que es Intel(R) 82915G Express Chipset Familiy. La verdad que no se que tipo de version de Ubuntu tengo (si para 32 o 64 bits) ya que no se como fijarme. Me parece que va ser mas facil bajarme la version que me recomiendas ustedes y probar con eso.
Muchas Gracias!

---

### Post by lucho 2000 on 2009-10-21
Emiliano, yo tambien tengo ese problema y lo solucione apagando y volviendo a prender el monitor, al parecer alli settea correctamente el monitor; en mi caso el problema es el monitor que no soporta una resolucion superior como la que viene prefijada en el instalador, uso un monitor viejo con PC nueva, no se si es el mismo caso que el tuyo pero por lo que contas se parecen.
Saludos
Luis

---

### Post by emicolarusso on 2009-10-22
Estoy en el mismo caso que vos Luis, gracias por la informacio. Tengo un monitor que a duras penas se mueve.
Gracias!

---

