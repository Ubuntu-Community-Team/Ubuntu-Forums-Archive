---
title: "Internet después del Upgrade"
date: 2009-02-09
forum: Hardware
---

### Post by xX-Felipao-Xx on 2009-02-09
Buenas gente, recién me entero estod el español en el foro, así que podré explicarme mejor acá.

La cosa es que hice un upgrade de Hardy a Intrepid y cuando terminó de instalar, todo bien, reinició y no funcionaba internet.

Usé pppoeconf (siempre lo usaba para configurar internet), hice todo, me detectó el concentrador eth0 en la terminal me dice que se lanzó la conexión pero no anda.

Aparte el iconito ese de las 2 pantallitas arriba tiene una crucesita de fondo rojo y si le hago doble click arriba, me dice:

"No se encontró ninguna conexión activa válida".

Mi conexión es directa del modem de ADSL a la PC, no tengo router ni nada de eso.

Alguien sabe que puedo hacer?

Muchas gracias :)

---

### Post by xX-Felipao-Xx on 2009-02-09
Raro, apagué el modem, lo prendí e hice el pppoeconf de nuevo y anduvo, pero me funciona por esta sesion y la proxima vez ya no me funciona más.

Aparte mientras funciona internet, sigue la crucesita en el icono del Network Manager.

Alguna idea?

---

### Post by BlackHero on 2009-02-09
talves tengas problemas con los drivers de la placa de red =)

---

### Post by david_mza on 2009-02-10
Probá de desinstalar el paquete pppoeconf y borrar la configuración -personalmente no lo he hecho nunca- ([https://lists.ubuntu.com/archives/ubuntu-co/2008-September/008393.html]("https://lists.ubuntu.com/archives/ubuntu-co/2008-September/008393.html")) y volverlo a instalar y configurar. Quizas se deba a que en intrepid el network-manager te permite configurar las conexiones adsl y se creo el conflicto con la configuración anterior. Tambien mira el archivo /etc/networks/interfaces si tienes configuraciones hechas manualmente el network-manager deja de funcionar.

Saludos y suerte

---

### Post by xX-Felipao-Xx on 2009-02-11
Actualizacion: Cada vez que prendo la PC, tengo que apagar el modem, volver a prenderlo y ahi hacer pppoeconf, y ahi tengo internet.

Ahora hago lo que me dijiste david_mza!

---

### Post by santiagoward2000 on 2009-02-23
Hola gente!
Perdón que me cuelgue, pero estoy teniendo un problema parecido. Después de instalar alguna actualización (perdonen que no sea más específico, pero no sé qué fue) el Network Manager dejó de detectar la conexión. Está hecha con un router Linksys, y apagarlo y prenderlo no me sirve.
Si corro lspci, me detecta la placa:
> 03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
Además, probé correr desde mi LiveCD de Intrepid y anda todo perfecto.
¿Alguna sugerencia?
Saludos!

---

### Post by hictio on 2009-02-23
> **santiagoward2000 said:**
> 
Después de instalar alguna actualización (perdonen que no sea más específico, pero no sé qué fue) el Network Manager dejó de detectar la conexión.


Santiago, si tenés una idea de la fecha cuando empezó este problema, podés ver los logs de instalación de updates en '/var/log/dpkg.log' (y rotaciones anteriores).

---

### Post by santiagoward2000 on 2009-02-23
> **hictio said:**
> Santiago, si tenés una idea de la fecha cuando empezó este problema, podés ver los logs de instalación de updates en '/var/log/dpkg.log' (y rotaciones anteriores).

Hola Hictio!
Como no me anda la conexión, me imagino que el problema viene en alguno de los últimos paquetes en instalarse. Ese día se instalaron:
[LIST]
[*]libgnutils26
[*]libgnutls-dev
[*]man-db
[*]dkms
[*]pm-utils
[*]libc6
[/LIST]
Por las descripciones que leí en Synaptic, me imagino que el problema viene por libgnutls, aunque yo siempre asocié TLS a conexiones para mails. Tampoco entendí bien que hace dkms, no sé si vendrá por ahí.
Por las dudas, dejo una copia del log de ese día, por si me olvidé algo.
Saludos y gracias!!

---

