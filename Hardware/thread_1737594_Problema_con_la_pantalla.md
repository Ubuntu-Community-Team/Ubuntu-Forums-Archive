---
title: "Problema con la pantalla"
date: 2011-04-23
forum: Hardware
---

### Post by Trowares on 2011-04-23
Buenas, soy nuevo en ubuntu y siempre he tenido un problema con la resolución de pantalla. He investigado y probado de todo y nada funciona... El xorg.conf esta vacío, cuando me voi a la configuración de la resolución del monitor, me dice que el monitor es desconocido y la resolución por defecto es 800x640. Ver todo grande me molesta mucho y es el principal motivo por el que me he cambiado varias veces de so.
Ley por ahí que escribiera lspci en la terminal y mostrara por acá lo que me saliera. 

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)


También he intentado buscar drivers para el video, pero no me funciona. Mi computador es un notebook olidata y se describe mas o menos en la cita de lspci anterior.
Espero puedan resolver mi problema ya que windows xp me tiene bastante jodido. 
Saludos.

---

### Post by idi0tf0wl on 2011-04-23
Ha probado sudo dpkg-reconfigure xserver-xorg por el terminal? Si no, lo proba por favor, pero cual Ubuntu estás usando?

---

### Post by Trowares on 2011-04-23
estoy usando el ubuntu 10.10
escribi el comando y no paso nada =/

---

### Post by rokan2008 on 2011-04-23
> **Trowares said:**
> Buenas, soy nuevo en ubuntu y siempre he tenido un problema con la resolución de pantalla. He investigado y probado de todo y nada funciona... El xorg.conf esta vacío, cuando me voi a la configuración de la resolución del monitor, me dice que el monitor es desconocido y la resolución por defecto es 800x640. Ver todo grande me molesta mucho y es el principal motivo por el que me he cambiado varias veces de so.
Ley por ahí que escribiera lspci en la terminal y mostrara por acá lo que me saliera. 

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)


También he intentado buscar drivers para el video, pero no me funciona. Mi computador es un notebook olidata y se describe mas o menos en la cita de lspci anterior.
Espero puedan resolver mi problema ya que windows xp me tiene bastante jodido. 
Saludos.

Mira tengo la misma tarjeta de video una sis mirage 3, en ubuntu 9.10 hay un deb que te proporcina una aceleracion 2d y puedes configurar el monitor en 1280x800, lamentablemente no sirve para ubuntu 10.04, pero hay una manera de dejar la pantalla en una configuracion de 1280x800, esa misma manera no sirve para la version 10.10. Lo mejor es saber que version tienes y te posteo el link de donde lo saque, esta en portugues pero algo se entiende.

---

### Post by idi0tf0wl on 2011-04-23
El ya diga que está usando 10.10. Creo que lo mejor es que él obtiene un versión más viejo y que se postas el link para lo de 9.04 y 10.04.

Trowares, necesitas reiniciar tu computadora antes de pensar que nada pasó, por favor.

---

### Post by Trowares on 2011-04-23
Probe reiniciando y aun asi nada. Osea que debo bajarme una version anterior de ubuntu? 
Si es asi, de donde me la puedo descargar?
Saludos

---

### Post by rokan2008 on 2011-04-23
> **rokan2008 said:**
> Mira tengo la misma tarjeta de video una sis mirage 3, en ubuntu 9.10 hay un deb que te proporcina una aceleracion 2d y puedes configurar el monitor en 1280x800, lamentablemente no sirve para ubuntu 10.04, pero hay una manera de dejar la pantalla en una configuracion de 1280x800, esa misma manera no sirve para la version 10.10. Lo mejor es saber que version tienes y te posteo el link de donde lo saque, esta en portugues pero algo se entiende.


Mira yo utilice este tutorial paso por paso y tengo la resolucion en 1280x800 en ubuntu 10.10, incluso hasta algunas transpariencias gracias a ubuntu tweak y metacity, te doy el link [http://diversosassuntosbrasil.blogspot.com/2010/09/driver-mandriva-2011-0-para-uso-em-sis.html](http://diversosassuntosbrasil.blogspot.com/2010/09/driver-mandriva-2011-0-para-uso-em-sis.html), a mi me resulto a las mil maravillas, es una pena que esa tarjeta no tenga soporte 3d en ubuntu, bueno espero que te sirva... como opcion deberias usar chromium para traducir la pagina ya que esta en portugues.

---

### Post by rokan2008 on 2011-04-23
> **rokan2008 said:**
> Mira yo utilice este tutorial paso por paso y tengo la resolucion en 1280x800 en ubuntu 10.10, incluso hasta algunas transpariencias gracias a ubuntu tweak y metacity, te doy el link [http://diversosassuntosbrasil.blogspot.com/2010/09/driver-mandriva-2011-0-para-uso-em-sis.html](http://diversosassuntosbrasil.blogspot.com/2010/09/driver-mandriva-2011-0-para-uso-em-sis.html), a mi me resulto a las mil maravillas, es una pena que esa tarjeta no tenga soporte 3d en ubuntu, bueno espero que te sirva... como opcion deberias usar chromium para traducir la pagina ya que esta en portugues.

P.D.: en la parte de abajo de la pagina en letras rojas esta el tutorial para la version en 32 bits, por si no tienes un equipo de 64 bits

---

### Post by idi0tf0wl on 2011-04-23
La puedes descargar de [http://releases.ubuntu.com/](http://releases.ubuntu.com/), pero mira que puedes reparar tu sistema coriente. Probala primero si tienes la energia!

---

### Post by Trowares on 2011-04-23
Por fin solucione el tema. Con el link de rokan2008 me las arregle. Me costo bastante eso si aja.
Muchas gracias a todos por su ayuda.
__

---

### Post by rokan2008 on 2011-04-23
> **Trowares said:**
> Por fin solucione el tema. Con el link de rokan2008 me las arregle. Me costo bastante eso si aja.
Muchas gracias a todos por su ayuda.
__

Me alegro compadre da jugo la tarjetita de video, a esperar que algun dia tenga soporte 3d

---

