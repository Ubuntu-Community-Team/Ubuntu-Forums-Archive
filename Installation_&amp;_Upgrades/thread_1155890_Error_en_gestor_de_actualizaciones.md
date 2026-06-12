---
title: "Error en gestor de actualizaciones"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by mikflichy on 2009-05-11
Hola. Estoy intentando actualizar mi ubuntu 8.10 a la nueva versión 9.04.
Pues bien, cuando intento realizar la comprobación de actualizaciones disponibles desde el Gestor de actualizaciones, pulso en comprobar y me da el siguiente error.

[SIZE=2]**W: Error de GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 09266047CE9FDCA9**[/SIZE]

Después me dice que todo está actualizado, pero no me da ninguna opción más.

Qué puedo hacer ??. Gracias.

---

### Post by Partyboi2 on 2009-05-11
Hi, you can add the key for that repo by opening a terminal (Applications>Accessories>Terminal)

```
gpg --keyserver keyserver.ubuntu.com --recv 09266047CE9FDCA9
gpg --export --armor 09266047CE9FDCA9 | sudo apt-key add -
```
then
```
sudo apt-get update
```

---

### Post by mikflichy on 2009-05-11
Thanks a lot. 
My english is not very good. Sorry.

The problem not persist, but when i want to check for updates, the system say me that all updates are ok.
However, i wait for a message for update to ubuntu 9.04.

Can i do it here or i am doing somthing wrong.

Thank you again.

---

### Post by Partyboi2 on 2009-05-11
Check under Software Sources (System>Admin>Software Sources) under the update tab that "Release Upgrade" is set to "normal release"

If that is already set to 'normal release' open a terminal and try
```
gksu update-manager -d
```Your English is a lot better then my Spanish :)

---

