---
title: "compaq mini cq10-100ss problema con wifi atheros AR9825"
date: 2011-01-30
forum: Hardware
---

### Post by arriero on 2011-01-30
Tengo un gran problema con este compac mini cq10-100ss después de haber instalado Ubuntu 10.04.1 ya que la versión UNR no era del gusto de su dueña e instalado esperando que se reconociese todo, pero desde liveusb parecía que se reconocía el wifi, crei en principio que seria un problema de network-manager pero una vez instalado sigo sin poder usar el wifi. 
[dmesg]("http://paste.ubuntu.com/560202/")
[lsmod]("http://paste.ubuntu.com/560203/")

iwconfig
> estefania@estefania-laptop:~$ iwconfig
lo no wireless extensions.
eth0 no wireless extensions.
wlan0 IEEE 802.11bgn ESSID:off/any
Mode:Managed Access Point: Not-Associated Tx-Power=off
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management:on

lspci
> 01:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
02:00.0 Ethernet controller: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)

Tiene un botón físico en el frontal del netbook que no hace ningún caso al off/on de la tarjeta e instalado wicd y tampoco he conseguido nada.
Por favor alguien que pueda darme un tip sobre el problema que pueda tener este netbook. Un saludo.

---

### Post by arriero on 2011-01-31
Vale solucionado. Despues de mirar cielo y tierra encontré varias enlaces donde me decían que utilizase los linux-backport-modules-wireless-lucid, pues tengo instalado la ubuntu 10.04.1 versión desktop, que es lo ultimo que he dejado en este compaq mini.
Después de leer y llegando a un punto de desperación por el compromiso con un familiar, estuve buscando en [launchpad]("https://launchpad.net/+search?field.text=atheros+AR9285") y deje [mi problema]("https://answers.launchpad.net/ubuntu/+question/143518") reflejado en la pagina.
Después busque por ubuntuforums y también deje mi problema en este hilo.
Buscando entre muchos post e hilos de varios sitio, [encontré este hilo ]("https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/136624")que decía textualmente apaga el ordenador desconectalo de la red, quitale la bateria y espera 30 minutos y una vez que lo enciendas deberia de reconocerte el hardware, dicho y hecho, pues despues de arrancar me encuentro con que el led de la wifi cambia de color naranja a azul en el arranque. Ya tenemos detectada la wifi gracias compañeros, dejo el hilo completo para quien quiera saber mas o tenga este problema.
Esta es la respuesta mas convincente y mas alegrias me ha dado despues de tres dias de busqueda.:guitar::p:p:p

---

