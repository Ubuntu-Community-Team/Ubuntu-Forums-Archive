---
title: "Synaptic Point device verical Mouse scroll not working"
date: 2009-02-22
forum: Hardware
---

### Post by Meados on 2009-02-22
How can I fix it?

---

### Post by Meados on 2009-02-23
> **Meados said:**
> How can I fix it?

There aren't any driver or something to the scroll work?

---

### Post by era86 on 2009-02-23
What kind of laptop is it?  You might want to look up tutorials on enabling the mouse scrolling through xorg.conf.  If it is a Thinkpad, check out the links in my sig.

---

### Post by Meados on 2009-02-23
> **era86 said:**
> What kind of laptop is it?  You might want to look up tutorials on enabling the mouse scrolling through xorg.conf.  If it is a Thinkpad, check out the links in my sig.

My laptop is this one:
[http://www.worten.pt/ProductDetail.aspx?pid=04121107&oid=10|27&c=1024273](http://www.worten.pt/ProductDetail.aspx?pid=04121107&oid=10|27&c=1024273)

If you need I can take a photo to you look better at the mouse.

Do you think there any away to put it to work in my computer?

---

### Post by Meados on 2009-03-08
So there ins't any way to put it to work in linux?

---

### Post by Meados on 2009-04-26
Hello, just to say that I found a solution for my problem. (my packard bell computer)

Here's the instructions:

> 
1.- Abrimos una terminal (Aplicaciones > Accesorios > Terminal) (open terminal)

2.- Tecleamos estos dos comandos: (write the follow commands)

sudo modprobe -r psmouse

sudo modprobe psmouse proto=imps

3.- Ya debería funcionar el desplazamiento del touchpad.  Vamos a hacerlo permanente.  Cambiamos de directorio: (fork work everytime that you start ubuntu)

cd /etc/modprobe.d/

4.- Creamos un archivo nuevo:

sudo gedit options

5.- Escribimos esto en ese archivo: (write this in the archive)

options psmouse proto=imps

6.- Guardamos los cambios y cerramos. (save and restart)

source: [http://envezdelpsiquiatra.wordpress.com/2009/04/24/arreglando-el-fallo-del-touchpad-en-jaunty/](http://envezdelpsiquiatra.wordpress.com/2009/04/24/arreglando-el-fallo-del-touchpad-en-jaunty/)


Tested in ubuntu 8.10 and 9.04.

Good Luck.

---

