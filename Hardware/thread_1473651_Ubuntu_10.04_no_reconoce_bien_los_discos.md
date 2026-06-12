---
title: "Ubuntu 10.04 no reconoce bien los discos"
date: 2010-05-05
forum: Hardware
---

### Post by Brath-ga on 2010-05-05
Soy usuario de Ubuntu desde hace años, y nunca me pasara algo así.
Me explico:
Tengo un disco IDE ATA de 80Gb. antiguo con el Windows XP y Windows Server y otro Sata II de 500 Gb. con Ubuntu y una partición NTFS.

El Sata lo tengo conectado en SATA II_1 ( Principal) y el ATA como exclavo IDE.

En el Gparted dela versión de Ubuntu 9.10 aparecian correctamente como Sda el SATA y como Sdb el ATA.

Al actualizar a la 10.04 no me paré en decirle donde quería instalar el Grub, suponiendo que lo haría en el SATA, pero es que el Gparted de la 10.04 me pone el ATA como Sda y el SATA como sdb, con lo cual el grub se instaló mal y me cargó el arranque de windows.

Comprobé que en ordenadores con un solo disco, lo hace perfecto, pero creo que es un error que debería ser anunciado pues somos muchos los que tenemos arranque dual.

Alguien sabe algo sobre el tema ?

---

### Post by alfplayer on 2010-05-05
Si sucedió esa inversión con el cambio de versiones, puede ser un cambio de comportamiento esperado sin ser un error.

---

### Post by z37a on 2010-05-05
> **Brath-ga said:**
> Soy usuario de Ubuntu desde hace años, y nunca me pasara algo así.
Me explico:
Tengo un disco IDE ATA de 80Gb. antiguo con el Windows XP y Windows Server y otro Sata II de 500 Gb. con Ubuntu y una partición NTFS.

El Sata lo tengo conectado en SATA II_1 ( Principal) y el ATA como exclavo IDE.

En el Gparted dela versión de Ubuntu 9.10 aparecian correctamente como Sda el SATA y como Sdb el ATA.

Al actualizar a la 10.04 no me paré en decirle donde quería instalar el Grub, suponiendo que lo haría en el SATA, pero es que el Gparted de la 10.04 me pone el ATA como Sda y el SATA como sdb, **con lo cual el grub se instaló mal y me cargó el arranque de windows.**

Comprobé que en ordenadores con un solo disco, lo hace perfecto, pero creo que es un error que debería ser anunciado pues somos muchos los que tenemos arranque dual.

Alguien sabe algo sobre el tema ?

Durante la instalación, en el ultimo paso te permite seleccionar donde instalar el grub, pro tanto se puede evitar ese problema, solo que en vez de seleccionar SDA se debería haber seleccionado SDB(por defecto usara SDA!)

---

### Post by Brath-ga on 2010-05-06
De hecho, recuperé el boot de "windows" y reinstalé el Ubuntu, haciendo como indica Z37a, y debido a eso logro funcionar.

Pero a lo que me refiero es al hecho de que versiones anteriores a la 10.04 reconocián los discos en su orden original perfectamente. En la 10.04, los reconoce mal, y si no entras en el apartado de "avanzadas", te coloca el grub en el "sda" sin más y puede pasar lo que a mí.

Yo lo supe modificar, porque llevo tiempo en esto, pero a un novato, que es a quien queremos que use Ubuntu y se olvide Windows, le puede resultar incómodo y seguramente pasará de Ubuntu inmediatamente "echando pestes".

Comprobé que todas las releases, inculido Lubuntu que se basen en la 10.04 tienen el mismo comportamiento.

---

