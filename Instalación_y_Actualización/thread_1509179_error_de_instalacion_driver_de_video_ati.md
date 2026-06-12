---
title: "error de instalacion driver de video ati"
date: 2010-06-13
forum: Instalación y Actualización
---

### Post by xGrinderx on 2010-06-13
beno instale el driver de video ati radeon hd 4200 via terminal y los instalo bien 
reinicie mi maquina y se ejecuto el gestor de synaptic, con el mensaje
"Tiene 1 paquete roto en su sistema

Use el filtro «Rotos» para encontrarlo."
(Error:BrokenCount 0)

al precionar aceptar comiensa a descargar el controlador  y aparece lo siguiente
> E: /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu3_i386.deb: el subproceso script pre-installation nuevo devolvió el código de salida de error 1
googlie un rato y me encontre con un topic similar el cual  lo solucionaba con lo siguiente
> ...ejecuta el Gestor de paquetes desde la terminal, es decir, abre un  terminal y pon por ejemplo:[INDENT][QUOTE]$ sudo apt-get install loquesea[/INDENT]Después, supongo que te pedirá que hagas un:[INDENT]> $ sudo dpkg --configure -a [/INDENT]para reparar las dependencias.
[/QUOTE]pero no pasa nada y me sigue mandando error :C

saludos

---

### Post by bichopro on 2010-06-14
esto hago yo cuando ya no quedan mas recursos:

ok, vamos a ponernos un poco mas "salvajes", por asi decirlo.

Prueba a hacer lo siguiente:
> 
# sudo mv /var/lib/dpkg/info/ /var/lib/dpkg/info_moved

> # sudo mkdir /var/lib/dpkg/info

<instala un paquete cualquiera>

> # sudo mv /var/lib/dpkg/info/* /var/lib/dpkg/info_moved

> # sudo rm /var/lib/dpkg/info

> # sudo mv /var/lib/dpkg/info_moved /var/lib/dpkg/info

---

### Post by Carlos C on 2010-06-14
o, antes de hacer lo que te sugiere bichopro, yo te recomiendo probar el comando:

```
sudo dpkg -C
```

Eso debiera darte algún tipo de sugerencia. Sino resulta, bueno, se puede proceder a métodos más radicales.

Saludos.

---

