---
title: "Conexión en Kubuntu"
date: 2009-11-01
forum: Hardware
---

### Post by FB91 on 2009-11-01
Tengo problemas para conectarme a mi red casera... desde el live CD de Kubuntu pude lograrlo lo más bien, pero ahora que lo instalé ya no puedo. Es un poco raro...

Les comento como me pude conectar desde el liveCD:

en el archivo /etc/network/interfaces escribo:
[FONT=Courier New]
auto eth0
iface eth0 inet static
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1[/FONT]

y en el archivo /etc/resolv.conf
[FONT=Courier New]
nameserver 208.67.222.222
nameserver 208.67.220.220[/FONT]

todo esto me lo había facilitado HeiKu en este [post]("http://ubuntuforums.org/showthread.php?t=1241214") y me funcionó correctamente desde el liveCD, pero ahora que lo instalé no funciona más.

Les comento que también probé con el networkmanager pero no hay caso...

---

### Post by guillermolisi on 2009-11-01
Tenes que repetir los pasos que te indico Hei Ku para dejar todo tal como lo tenias para el LiveCD.
Digo esto porque entiendo que lo tenias realizado para la sesion Live pero una vez que instalas eso no se traslada. Tenes que volverlo a configurar y hace que el NManager no intervenga.

Si no es tal como interpreto, una vista del /etc/network/interfaces ayudara.

---

### Post by FB91 on 2009-11-01
ya logré tener acceso a Internet.

---

### Post by guillermolisi on 2009-11-01
> **FB91 said:**
> ya logré tener acceso a Internet, ahora lo único que no me deja hacer es ver los archivos de las otras PC en red.

Ingreso a Red -> Comparticiones Samba y ahi dentro se vé el grupo de trabajo (que se llama CASA) pero adentro no se vé nada
Va en nuevo thread en Software (ya que tiene que ver con Samba)

---

