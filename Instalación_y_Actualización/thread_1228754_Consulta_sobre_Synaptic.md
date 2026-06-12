---
title: "Consulta sobre Synaptic"
date: 2009-08-01
forum: Instalación y Actualización
---

### Post by AlvaroV on 2009-08-01
Algien me puede señalar que significa cuando synaptic dice que "aparecen *dependencias no resolubles"*

---

### Post by Carlos C on 2009-08-01
Cuando sale eso es porque el sistema intenta instalar un paquete cuyas dependencias generan un conflicto. Puede ser que uses repositorios no oficiales o que hayas instalado un paquete que genere un conflicto con una dependencia que sea necesario instalar. ¿Te está saliendo este error cuando tratas de instalar algún programa?

---

### Post by AlvaroV on 2009-08-03
Me parece  python-gammu pendiente de actualizar , pero no lo hace.

---

### Post by Carlos C on 2009-08-05
Has añadido algún repositorio no oficial?
Prueba escribiendo en el terminal:
```
sudo dpkg -C
```
De esa forma obtendrás un poco más de información.

---

