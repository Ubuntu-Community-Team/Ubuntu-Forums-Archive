---
title: "Sobre montar particiones de windows al inicio."
date: 2009-03-28
forum: Hardware
---

### Post by nemodot on 2009-03-28
Buenas gente.

Cómo puedo hacer para que los discos NTFS de windows que tengo se monten al inicio?

Por que no se montan hasta que entro voluntariamente a ellos.

Gracias.

---

### Post by Hei Ku on 2009-03-28
Podes ir al administrador de discos y marcarlas como para que se automonten, o modificar el archivo /etc/fstab manualmente.

---

### Post by nemodot on 2009-03-28
Donde encuentro el administrador de discos?

---

### Post by EnriqueK on 2009-03-28
> **nemodot said:**
> Donde encuentro el administrador de discos?.

A partir de Intrepid figura en repositorios la aplicación **disk-manager **, te sugiero que la descargues , luego ponés en terminal **killall nautilus** y ya podés acceder al programa desde el menú Sistema-->Administración-->Administrador de discos , luego entrando a la pestaña Configuración Avanzada marcás las particiones que se montarán al inicio y además podés elegir si se harán con atributus de lectura/escritura o de solo lectura.
Si tenés la 8.04, esta aplicación no figura en repositorios pero sirve la que es para Intrepid.

---

