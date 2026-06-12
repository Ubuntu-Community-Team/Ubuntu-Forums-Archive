---
title: "[SOLUCIONADO] Problemas de sonido con ubuntu jaunti - HP mini"
date: 2009-05-31
forum: Hardware
---

### Post by milkocepeda on 2009-05-31
Hola gente:
Tengo un HP Mini y desde que le cargaron el jaunty no tengo sonido, he intentado todo, el manual ubuntero, las repuestes del foro y aún no tengo sonido. Carlos C me pidio que ejecutara en la terminal dos comandos aquí van las respuestas.
mcepeda@mcepeda-laptop:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) 
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) 
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) 
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) 
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02) 
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02) 
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01) 
mcepeda@mcepeda-laptop:~$ lsmod| grep snd 
snd_hda_intel         435636  3  
snd_pcm_oss            46336  0  
snd_mixer_oss          22656  1 snd_pcm_oss 
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss 
snd_seq_dummy          10756  0  
snd_seq_oss            37760  0  
snd_seq_midi           14336  0  
snd_rawmidi            29696  1 snd_seq_midi 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
snd_timer              29704  2 snd_pcm,snd_seq 
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
snd 62628 15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
soundcore              15200  1 snd 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm

Luego de esto no sé que más hacer.
Solicito orientación.

Gracias.
Milko Cepeda

---

### Post by radixs on 2009-06-01
Anduve buscando tu problema ve si te sirve el siguiente link:


[ver]("http://www.ubuntu-ve.org/?q=node/1134")

---

### Post by vtssrm on 2009-06-02
Compañero yo tengo el HP Mini 1020LA y lo que hice fue colocar en consola lo siguiente:

$ cd ~
$ mkdir alsa
$  cd alsa
$ wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2)
$ wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.20.tar.bz2)
$ wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.20.tar.bz2)
$ tar xjf alsa-driver-1.0.20.tar.bz2
$ tar xjf alsa-lib-1.0.20.tar.bz2
$ tar xjf alsa-utils-1.0.20.tar.bz2
$ sudo apt-get install build-essential kernel-package gcc make gettext
$ sudo apt-get install libncurses5-dev
$ cd alsa-driver-1.0.20
$ ./configure -with-cards=hda-intel -with-sequencer=yesLinux && make && sudo make install
$ cd ../alsa-lib-1.0.20
$ ./configure && make && sudo make install
$ cd ../alsa-utils-1.0.20
$ ./configure && make && sudo make install

Eso y reinicias. Pueden demorar un poco los "últimos" pasos, paciencia.

Cuanta si te sirvió...

Ojo: el foro sustituyo parte de la dirección por "..." en los comandos 4, 5 y 6. Si no entiendes guíate por mi blogspot:

[http://vtssrm.blogspot.com/2009/05/sonido-en-ubuntu-904.html](http://vtssrm.blogspot.com/2009/05/sonido-en-ubuntu-904.html)

---

### Post by Carlos C on 2009-06-02
Aquí está sin cambios:

> $ cd ~
$ mkdir alsa
$  cd alsa
$ wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2)
$ wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.20.tar.bz2)
$ wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.20.tar.bz2)
$ tar xjf alsa-driver-1.0.20.tar.bz2
$ tar xjf alsa-lib-1.0.20.tar.bz2
$ tar xjf alsa-utils-1.0.20.tar.bz2
$ sudo apt-get install build-essential kernel-package gcc make gettext
$ sudo apt-get install libncurses5-dev
$ cd alsa-driver-1.0.20
$ ./configure -with-cards=hda-intel -with-sequencer=yesLinux && make && sudo make install
$ cd ../alsa-lib-1.0.20
$ ./configure && make && sudo make install
$ cd ../alsa-utils-1.0.20
$ ./configure && make && sudo make installHay que seleccionar el texto y luego hacer click en el símbolo "#". Creo que esa opción no aparece si escoges "Quick Reply", debes escoger "New Reply".
Saludos.

---

### Post by milkocepeda on 2009-06-04
Sigo sordomudo.
No he podido hacer que el audio aparezca, el link que me enviaron no funcionó ya que la tarjeta era distinta a la que aparecía en la ayuda que me prestaron. Vuelvo a colococar las respuestas obtenidas en anteriores foros a mi problema.


			 		 	 	 		[Volver arriba]("http://foros.ubuntu-cl.org/viewtopic.php?p=43070#top") 		 			 				[[IMG]http://foros.ubuntu-cl.org/templates/subUbuntu/images/lang_spanish/icon_profile.gif[/IMG]]("http://foros.ubuntu-cl.org/profile.php?mode=viewprofile&u=3003") [[IMG]http://foros.ubuntu-cl.org/templates/subUbuntu/images/lang_spanish/icon_pm.gif[/IMG]]("http://foros.ubuntu-cl.org/privmsg.php?mode=post&u=3003")  [[IMG]http://foros.ubuntu-cl.org/templates/subUbuntu/images/lang_spanish/icon_www.gif[/IMG]]("http://blockdeubuntu.blogspot.com/")    
			 		 	 	 		[IMG]http://foros.ubuntu-cl.org/templates/subSilver/images/spacer.gif[/IMG] 	 	 		**milkocepeda**
Novat@


Registrado: 07 May 2009
Mensajes: 4

		 			 				[[IMG]http://foros.ubuntu-cl.org/templates/subUbuntu/images/icon_minipost.gif[/IMG]]("http://foros.ubuntu-cl.org/viewtopic.php?p=43070#43070")Publicado: Dom May 17, 2009 6:35 pm    **Asunto**: Respecto de la respuesta a problemas de sonido 				[[IMG]http://foros.ubuntu-cl.org/templates/subUbuntu/images/lang_spanish/icon_quote.gif[/IMG]]("http://foros.ubuntu-cl.org/posting.php?mode=quote&p=43070")    			 			 				 			 			 				mcepeda@mcepeda-laptop:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) 
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) 
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) 
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) 
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02) 
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02) 
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01) 
mcepeda@mcepeda-laptop:~$ lsmod| grep snd 
snd_hda_intel         435636  3  
snd_pcm_oss            46336  0  
snd_mixer_oss          22656  1 snd_pcm_oss 
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss 
snd_seq_dummy          10756  0  
snd_seq_oss            37760  0  
snd_seq_midi           14336  0  
snd_rawmidi            29696  1 snd_seq_midi 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
snd_timer              29704  2 snd_pcm,snd_seq 
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
snd 62628 15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
soundcore              15200  1 snd 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm

---

### Post by kamus on 2009-06-04
> **milkocepeda said:**
> Sigo sordomudo.
No he podido hacer que el audio aparezca, el link que me enviaron no funcionó ya que la tarjeta era distinta a la que aparecía en la ayuda que me prestaron. Vuelvo a colococar las respuestas obtenidas en anteriores foros a mi problema.


			 		 	 	 		[Volver arriba]("http://foros.ubuntu-cl.org/viewtopic.php?p=43070#top") 		 			 				[[IMG]http://foros.ubuntu-cl.org/templates/subUbuntu/images/lang_spanish/icon_profile.gif[/IMG]]("http://foros.ubuntu-cl.org/profile.php?mode=viewprofile&u=3003") [[IMG]http://foros.ubuntu-cl.org/templates/subUbuntu/images/lang_spanish/icon_pm.gif[/IMG]]("http://foros.ubuntu-cl.org/privmsg.php?mode=post&u=3003")  [[IMG]http://foros.ubuntu-cl.org/templates/subUbuntu/images/lang_spanish/icon_www.gif[/IMG]]("http://blockdeubuntu.blogspot.com/")    
			 		 	 	 		[IMG]http://foros.ubuntu-cl.org/templates/subSilver/images/spacer.gif[/IMG] 	 	 		**milkocepeda**
Novat@


Registrado: 07 May 2009
Mensajes: 4

		 			 				[[IMG]http://foros.ubuntu-cl.org/templates/subUbuntu/images/icon_minipost.gif[/IMG]]("http://foros.ubuntu-cl.org/viewtopic.php?p=43070#43070")Publicado: Dom May 17, 2009 6:35 pm    **Asunto**: Respecto de la respuesta a problemas de sonido 				[[IMG]http://foros.ubuntu-cl.org/templates/subUbuntu/images/lang_spanish/icon_quote.gif[/IMG]]("http://foros.ubuntu-cl.org/posting.php?mode=quote&p=43070")    			 			 				 			 			 				mcepeda@mcepeda-laptop:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) 
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) 
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) 
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) 
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02) 
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02) 
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01) 
mcepeda@mcepeda-laptop:~$ lsmod| grep snd 
snd_hda_intel         435636  3  
snd_pcm_oss            46336  0  
snd_mixer_oss          22656  1 snd_pcm_oss 
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss 
snd_seq_dummy          10756  0  
snd_seq_oss            37760  0  
snd_seq_midi           14336  0  
snd_rawmidi            29696  1 snd_seq_midi 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
snd_timer              29704  2 snd_pcm,snd_seq 
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
snd 62628 15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
soundcore              15200  1 snd 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm

Deberian mover este topic al foro Hardware! 

Para no ser tan poco aportivo.. podrias especificar mas detalles sobre tu equipo? por ejemplo placa madre, modelo, serie, etc.?

Salu2

---

### Post by Carlos C on 2009-06-05
milkocepeda, he juntado estos dos threads en uno ya que continuas el mismo tema. Por favor deja de abrir temas nuevos cada vez que respondes, lo que debes hacer es responder al thread que ya abriste. Además, pon atención donde estas publicando. Los 3 threads que has iniciado han sido publicados en el foro equivocado. Si continuas haciéndolo me vere obligado a borrarlos. Espero que comprendas que es la única manera de obtener ayuda en este foro.
Gracias por tu comprensión.
Saludos.

---

### Post by guillermolisi on 2009-06-06
No veo nada raro en la informacion aportada sobre los modulos de sonido asi que mi primer consejo, porque no vi que aun se haya dado, es abrir una consola/terminal e ingresar Alsamixer para revisar el nivel de los controles del mixer de audio.

Posiblemente no tenga sonido porque el que opera como Master esta silenciado o con nivel muy bajo.

---

### Post by milkocepeda on 2009-06-11
Hola gente:
Agradezco [vtssrm]("http://ubuntuforums.org/member.php?u=847614") el apoyo de comandos para este problema. Ya tengo sonido en mi HP Mini. recomiendo esta solución para aquellos que tiene esta marca.
Gracias.
Milko Cepeda

---

