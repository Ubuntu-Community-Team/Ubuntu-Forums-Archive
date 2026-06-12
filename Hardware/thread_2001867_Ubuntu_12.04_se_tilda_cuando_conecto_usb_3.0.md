---
title: "Ubuntu 12.04 se tilda cuando conecto usb 3.0"
date: 2012-06-11
forum: Hardware
---

### Post by monty3x on 2012-06-11
Buenos dias a todos: 
el problema planteado es que al conectar un rigido externo Iomega 3.0 en el puerto usb 3.0 de mi pc ( mother gigabyte GA-990FXA-UD3 )  UBUNTU 12.04 amd64 se tilda y me deja de responder todo. 
ACLARACION:  en los puertos usb 2.0 funciona perfecto  el disco xterno  y el sistema operativo.

Alguien tiene una idea a que se puede deber esto o algun posible log que me indique  x donde viene el problema y una posible solucion.
cualquier tpo de ayuda es bienvenida.
Saludos y gracias.

---

### Post by biale on 2012-06-11
Al menos en mi motherb Asus el soporte a USB 3.0 lo da un chip especial. Eso significa que si conecto algo a un port USB 2.0 y luego a un port USB 3.0 los resultados pueden ser distintos. Y sin embargo con 10.04 no he tenido problemas.

Podrías buscar en /var/log si antes del freeze se llegó a registrar algo...

A los efectos prácticos, diría que hay que darle a la distro un par de meses mas como para que la estabilicen bien.

---

### Post by euzkoarima on 2012-06-13
Lo del /var/log me parece muy acertado.
Además, se cuelga ni bien conectas ? o te da tiempo de tirar un dmesg en consola (a ver como lo toma al disco).

Sin más datos, yo miraría las configuraciones del usb3 en la bios (no si ni cuales son xq nunca tuve acceso a una mother con usb3). Pero es posible que haya alguna configuración que si ande bien con ubuntu.

Saludos,
Eduardo

---

