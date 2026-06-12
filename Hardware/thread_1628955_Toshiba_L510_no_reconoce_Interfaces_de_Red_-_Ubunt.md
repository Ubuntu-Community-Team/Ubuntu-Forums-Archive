---
title: "Toshiba L510 no reconoce Interfaces de Red - Ubuntu 10.04"
date: 2010-11-23
forum: Hardware
---

### Post by sys.adm.og on 2010-11-23
Hola a todos,

   Anoche feliz fui a instalarle Gnu/Linux a mi novia que se le regalo una Notebook Toshiba (que venia con Windows 7). Para mi sorpresa no me reconoce la red cableada ni por modem, hice un STFG y nada.

Con lspci pude ver que reconocia la tarjeta ethernet y la de wireles pero al conectar el cable de red nada y de wireless no lo pude probar porque no tengo una red de ese tipo. Probe con un modem de personal y no me lo reconoce, asi tambien con uno de Claro ese si me reconoce para configurar pero no me reconoce como conectado!

[http://www.ubuntu-es.org/node/140953](http://www.ubuntu-es.org/node/140953) en este thread encontre que decian que el windows 7 apaga la tarjeta de red, pero yo ya lo elimine!

Alguna idea?

Desde ya muchas Gracias!

---

### Post by asterix77 on 2010-11-23
¿Que te arroja el comando lspci | grep Ethernet en la consola?
 
¿ y el comando ifconfig?
 
 
¿usas network-manager?
 
Saludos

---

### Post by sys.adm.og on 2010-11-23
lspci me reconoce la ethernet que es una realtek y con ifconfig solo muestra el localhost y wlan0, por lo que intente hacer un ifconfig ethX up y llegue hasta cinco pero me decia que no existia la interfaz.
Si network-manager esta por defecto!

---

### Post by juancarlospaco on 2010-11-23
Ver el tema de las Hotkeys que traen las notebook, 
algunas no anda el dispocitivo hasta que no lo activas via Hotkey,
me pasa asi con la Webcam, la detecta pero no anda hasta que no la activas.

---

### Post by sys.adm.og on 2010-11-23
Me voy a fijar pero la de wireless si me da como activa las demas nomas no me dan! Que son la de red y modem!

Lo que me preocupa es que si es cierto que el win 7 desabilita las tarjetas al apagarse porque el win lo elimine aunque deje el de recovery pero no me gustaria instalar de nuevo!

Desde ya muchas Gracias

---

### Post by sys.adm.og on 2010-11-30
Buenas de nuevo, resolvi el problema instalando Ubuntu 10.10 y habilitando antes Wake On line en el bios.

Solo tengo un problema, al intentar conectar mi modem no lo hace y la configuracion es correcta! Cuando me fijo en el Network Manager me dice que por ejemplo en el caso de las redes cableadas: desconectado y de igual forma con la inalambrica pero en el caso del moden me dice no disponible de la misma forma cuando esta conectado el modem! Creo que es por eso que no me conecta!

Alguna idea de que deba hacer?
Saludos

---

