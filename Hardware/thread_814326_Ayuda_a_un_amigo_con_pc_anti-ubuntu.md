---
title: "Ayuda a un amigo con pc anti-ubuntu"
date: 2008-05-31
forum: Hardware
---

### Post by pol666 on 2008-05-31
Hola, les cuento que la semana pasada un amigo quedo facinado con ubuntu, la velocidad, los efectos y el hecho de no tener virus ni programas que ralentizen el sistema me pidio que le instalase ubuntu con Wubi

Bueno Le dije que si pero antes tenia que ver cuales eran los componentes que tenia su PC, suplicando por dentro que no tuviera ATI, Sound Blaster Audigy, discos incompatibles etc...

Bueno lamentablemente cuando voy a su casa me entero que tenia wireless 
y una Ati Raedeon X1650 (creo que no me equivoco de modelo)
Tragando saliva lo instalo igual, y por suerte se veia todo bien y habia levanto el sonido de una, pero como era de suponer  no reconocia la placa  wire-less ademas de que yo no tengo conocimientos acerca de estos componentes por que jamas los use...

el primer punto antes de ver que puedo hacer con EnvyNG necesito que la PC levante la coneccion

La placa es  **IEEE 802.11g wireless cardbus/PCI**  
El modem un **motorola SB5100**, la compania de internet **CABLE MODEM es Telecentro**  y el modelo del router se los debo (luego le pregunto)


Tampoco me moleste mucho en buscar por que era imposible instalar cosas por Apt-Get. ASi que les pido por favor que puedo hacer para levantar internet en esta pc obviamente sin afectar la coneccion de windows ni de la otra PC

si necesito drivers o algo diganme de donde puedo bajar los tar.gz o .deb  y de que mandera instalarlos.. De otro modo tendre que desinstalrle ubuntu

---

### Post by sergiom99 on 2008-05-31
mira que la placa no es esa. eso es el tipo/standard de placa. tenes que fijarte que placa es, o que chipset tiene (broadcom, atheros, etc) creo que lo podes ver con "sudo lspci" y ahi buscar algo de la wlan.
con ese dato seguimos mirando.
Sino la otra es abrir la PC y fijarte que placa tiene y va a ser mas facil.

PS: sino postea el output de 'lspci' y lo miramos entre todos a ver que corno tiene.
el mio dice:
```

03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)


```

---

### Post by pol666 on 2008-05-31
si el fabricante... Lo habia anotado y no lo tengo ahora se loo pido

---

### Post by Kantier on 2008-06-01
respirá tranquilo, si usa cablemodem de lo único que te tenes que preocupar es que ande la placa de red de lo que tiene la IP "de internet" (en este caso el router, pero a veces es directamente la PC en cuestión)

---

### Post by pol666 on 2008-06-01
> **Kantier said:**
> respirá tranquilo, si usa cablemodem de lo único que te tenes que preocupar es que ande la placa de red de lo que tiene la IP "de internet" (en este caso el router, pero a veces es directamente la PC en cuestión)

No entiendo tu punto. La pc tiene una entrada de red pero no la usa por que esta conectada a un router por wireless.  osea el que le da la IP es el router. Ahora.... yo me meti en las propiedades de RED y no aparece el dispositivo.

---

### Post by Kantier on 2008-06-01
> **pol666 said:**
> No entiendo tu punto. La pc tiene una entrada de red pero no la usa por que esta conectada a un router por wireless.  osea el que le da la IP es el router. Ahora.... yo me meti en las propiedades de RED y no aparece el dispositivo.
y el router está conectado por ethernet (red no wireless) al modem. el router toma la IP pública, y separa la red local de internet.

mi punto es que una vez que te ande la placa wifi, ya stás listo y no tenés que preocuparte más por temas de conectividad.

---

### Post by pol666 on 2008-06-01
claro, el punto es que no me reconoce la placa wireless ahora voy a preguntarle la marca del fabriante para ver si alguien me facilita los drivers

---

### Post by pol666 on 2008-06-01
me dijo que el chipset es del fabricante **MARVELL**

---

### Post by sergiom99 on 2008-06-01
postea el lspci asi vemos bien como viene la mano con esa placa.

---

