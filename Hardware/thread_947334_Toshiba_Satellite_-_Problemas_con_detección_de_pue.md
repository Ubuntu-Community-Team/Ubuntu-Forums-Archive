---
title: "Toshiba Satellite - Problemas con detección de puertos"
date: 2008-10-14
forum: Hardware
---

### Post by carlosgim on 2008-10-14
Hola a todos, tengo una laptop marca Toshiba, modelo Satellite. El problema es el siguiente:

Los puertos usb onboard no funcionan, ya los deshabilité desde el setup, pero parece que ubuntu los busca y tarda una vida en arrancar el sis. Me tira el siguiente mensaje cuando esta arrancando el sistema:
```
[17.668971] MP-BIOS bug:8254 timer not connected to IO-APIC
```

Creo que lo ideal seria que el sistema no los busque y que inicie directamente. Por que hay veces que tarda hasta 10 minutos en arrancar y en terminos de informatica el tiempo no se dilata se contrae... Saludos

---

### Post by faktorqm on 2008-10-14
El error es debido a un incremento en el rendimiento del timer para ser compatible con Windows Vista....

Cuando arrancas la compu, 

- presiona la tecla 'e' sobre la primera línea para editar la entrada (no la recovery, la normal).
- volver a presionar la 'e' sobre la línea "kernel" (la más larga normalmente) y añadir al final "noacpi" (sin comillas).
-Presionar "enter" una vez escrito esto.
-Presionar 'b' sobre la línea de "kernel" para arrancar el sistema.

Eso deberia solucionarte el problema. Si no lo hace, tambien podes buscar si existe una opcion llamada "HPET timer" y deshabilitarla, y re arrancar el ubuntu (primero normal, luego editando la linea de vuelta)
Si te anda lo de agregar acpi=off, para que cuando reinicies te tome los cambios debes editar el archivo /boot/grub/menu.lst, para esto apretas ALT + F2 y escribis:

```
gksudo gedit /boot/grub/menu.lst
```

y ahi le agregas noacpi a la linea del kernel y te queda permanente el cambio. Para futuras actualizaciones, busca la linea comentada 

```
#defoptions=
```

y agregalo ahi tambien. A todo esto, que version de ubuntu usas? Salu2!

p.d.: google no muerde....

---

### Post by carlosgim on 2008-10-14
> Cuando arrancas la compu,

- presiona la tecla 'e' sobre la primera línea para editar la entrada (no la recovery, la normal).[COLOR="Red"]**(1)**[/COLOR]
- volver a presionar la 'e' sobre la línea "kernel" (la más larga normalmente) y añadir al final "noacpi" (sin comillas).[COLOR="Red"]**(2)**[/COLOR]
-Presionar "enter" una vez escrito esto.
-Presionar 'b' sobre la línea de "kernel" para arrancar el sistema.[COLOR="Red"]**(3)**[/COLOR]
Perdón por la ignorancia pero:
(1) Presionar la tecla 'e' sobre la primera línea para editar la entrada. 
Nota: Te pido un poco mas de datos, ya que no se cual es la primera linea de entrada. ¿Es decir cuando comienza le doy e? ¿O hay que hacer algo mas?
(2) linea Kernel? Insisto pero disculpá la ignorancia no se que es eso.

PD: Gracias por la paciencia

---

### Post by faktorqm on 2008-10-15
Ésta es la primera linea de entrada (si no es seleccionala vos con las flechas)
[http://blackflash.com.ar/wp-content/uploads/2007/11/grub1.jpg](http://blackflash.com.ar/wp-content/uploads/2007/11/grub1.jpg)

y la "linea kernel" es la que aparece en blanco en esta foto:
[http://www.cyberciti.biz/nixcraft/vivek/blogger/uploaded_images/grub-boot-press-b.png](http://www.cyberciti.biz/nixcraft/vivek/blogger/uploaded_images/grub-boot-press-b.png)

aclaracion: probablemente no sean exactamente iguales a las que veas vos en la pantalla, y esto esta bien y es normal. sólo las fotos son de caracter ilustrativo para que pudieras ver de lo que estaba hablando.

Salu2!

---

### Post by carlosgim on 2008-10-17
Muchas gracias. Te cuento que ahora me aparece el siguiente cartel
```
[15.998971] MP-BIOS bug:8254 timer not connected to IO-APIC
```
Tarda un poco menos. Pero sigue con el problema.

---

### Post by carlosgim on 2008-10-17
Perdon, la versión de Ubuntu que tengo es la 8.04

---

### Post by faktorqm on 2008-10-20
Y buscaste de deshabilitar el HPET timer en el bios? 

Solucione el problema del error de sicronizacion del timer en una MOBO ASUS P5NSLI con mensaje de error "Timer not connected to IO-APIC" deshabilitando desde el BIOS la entrada "HPET Support" ubicada en "Power-->APM Configuration-->HPET Support".

Eso lo saque de ubuntu-es. Tu modelo quiza no sea el mismo, pero las opciones las podes buscar. Salu2!

---

