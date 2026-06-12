---
title: "HP ompaq 515 y ubuntu 8.04"
date: 2009-09-30
forum: Hardware
---

### Post by Mr-Judo on 2009-09-30
hola soy nuevo en esto de linux, tengo una noteboock Compaq 515 con ubuntu 8.04 ya que la vercion 9.04 nunca arranco. el sistema arranca lo mas bien pero cuando configuro la placa de video integrada ATI HD 3200 es como que me da un error. Entonces bajo el driver de la pagina oficial de ATI(amd) y resulta que no puedo ejecutar el archivome dice:

"gedit no ha podido detectar la codificación de caracteres.
Compruebe que no está intentando abrir un archivo binario.
Seleccione una codificación de caracteres desde el menú e intente de nuevo."

---

### Post by pablo.s on 2009-09-30
¿Cómo se llama el archivo
que tenés que instalar?

---

### Post by Mr-Judo on 2009-09-30
hola gracias por responder...
El nombre del archivo es "ati-driver-installer-9-9-x86.x86_64.run"

---

### Post by pablo.s on 2009-09-30
Abrí una terminal. Andá a donde
está el archivo, por ejemplo

```
cd Desktop
```

una vez que estás en el mismo
directorio, hacés

```
chmod 755 ati-driver-installer-9-9-x86.x86_64.run
```

y luego hacés

```
sh ./ati-driver-installer-9-9-x86.x86_64.run
```

---

### Post by luks911 on 2009-09-30
Más allá de la explicación de Pablo, si seguís teniendo problemas (con el video, no con lo específico que comentás al principio) probá con Envy-NG para instalar los drivers.
En la máquina de un amigo, con esa placa, fue la única forma que encontramos para que se instalaran correctamente. Es probable que el problema hayamos sido nosotros, pero bueno, tenelo en cuenta.

Un saludo

---

### Post by Applelnx on 2009-09-30
Fijate que en la pagina hay un instructivo de instalacion:

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat99-inst.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat99-inst.pdf)

Esta en ingles, si necesitas ayuda avisa que no tengo drama en traducirte.

Saludos

---

### Post by Mr-Judo on 2009-09-30
Muchas gracias a todos, pude solucionar el problema con el instructivo que esta en la pagina junto al driver, mi ingles no es muy bueno pero fue bien.

---

