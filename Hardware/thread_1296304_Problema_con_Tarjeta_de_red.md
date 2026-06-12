---
title: "Problema con Tarjeta de red"
date: 2009-10-20
forum: Hardware
---

### Post by josecardenasvejar on 2009-10-20
Estimados: 
 He detectado un problema que me tiene algo inquieto. Al encender mi pc, se iniciaba una conexión eth1, al reiniciarlo aparecía una conexión eth2 y así sucesivamente, ya voy en la 17. Tengo configurado todo con dhcp para navegar en mi casa y trabajo. pero trato de eliminar esa conexión y me aparece un mensaje que dice "message did not receive a reply (timeout by message bus ethernet)" y no se puede eliminar, aparece nuevamente, aunque haga click en los diferentes perfiles de conexión que tengo.

Cambié la configuración de etc/udev/rules.dev/70-persistent-net.rules y eliminé todas las conexiones que me había creado, solo dejé la inalámbrica y eth0, pero reinicio y vuelve a conectarme con eth1 y cambia la dirección mac.

Tengo esta inquietud, hace unos días no me aparecía esto

Agradezco muchísimo su ayuda

Saludos:confused:

---

### Post by felipe51 on 2009-10-20
buscando en google.. encontre esto. y es muy similar a tu situacion con tu hardware

[http://davehall.com.au/blog/dave/2008/02/10/flakey-bios-gigabyte-ga-m68sm-s2l-makes-mac-address-change-reboot]("http://davehall.com.au/blog/dave/2008/02/10/flakey-bios-gigabyte-ga-m68sm-s2l-makes-mac-address-change-reboot")

---

