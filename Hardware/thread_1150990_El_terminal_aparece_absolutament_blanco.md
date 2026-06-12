---
title: "El terminal aparece absolutament blanco"
date: 2009-05-06
forum: Hardware
---

### Post by Urfe on 2009-05-06
Hola.

Desde que estuve haciendo unos cambios en el controlador de la tarjeta gráfica (Nvidia 7700) el terminal me aparece totalmente blanco. No se ve ningún texto. Todos los marcos de los cuadros de diálogo de, por ejemplo, el Synaptic se ven invisibles.

El problema es que no sé como deshacer esos cambios.

Alguna idea? Gracias.

---

### Post by luks911 on 2009-05-06
¿Te desaparecieron los marcos de las ventanas (donde están los botones para cerrar, maximizar y restaurarlas)? Para recuperarlos momentaneamente ejecutá en la terminal 

```
metacity --replace
```

Después andá a Sistema > Administración > Controladores de Hardware

y fijate ahí que estén habilitados los drivers propietarios de Nvidia.

---

### Post by Urfe on 2009-05-07
Perfecto, ya vuelven a aparecer los marcos.

Ha funcionado solo con reemplazar metacity.

Gracias.

---

