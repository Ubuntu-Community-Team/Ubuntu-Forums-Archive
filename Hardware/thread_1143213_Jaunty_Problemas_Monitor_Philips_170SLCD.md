---
title: "Jaunty Problemas Monitor Philips 170SLCD"
date: 2009-04-29
forum: Hardware
---

### Post by Viciuxs on 2009-04-29
Tengo un gran problema que es el mismo por el cual volvi de Intrepid a Hardy y es el siguiente:
Tengo un motherboard Intel DG31PR (graficos integrados X3100) y un monitor LCD Philips 170S.Resulta que al querer instalar botea el cd puedo elegir idioma y todo pero luego de comenzar no me corre el entorno grafico y me deja en consola. Probre la instalacion en modo grafico seguro y si pude (pero a costa de las limitaciones graficas que todos conocemos del driver VESA)ahora estoy usando Jaunty pero sin aceleracion grafica.
Tambien probe instalarlo con la misma motherboard intel DG31PR pero con un monitor CRT y para mi sorpresa se instalo todo correctamente incluida la aceleracion grafica.
Asi que mi problema es el siguiente al arrancar con el monitor CRT tengo aceleracion grafica, pero al arrancar con el LCD (que es el quiero usar)no tengo aceleracion grafica  y me tira este error:
(EE)intel(0):No valid modes.
(EE)Screen(s)found, but none have a usable configuration.
Tambien probe iniciar con el CRT y una ves logueado desconectar el CRT y conectar el LCD y para mi sorpresa si lo reconocio y tambien anduvo la aceleracion grafica pero luego al reiniciar me vuelve a salir el error que ya mencione arriva.
E intentado configurar el xorg pero nada a funcionado.Si alguien me puede ayudar se lo agradeceria.
Nota:en Hardy Heron me andaba todo el mismo mother y el LCD mi problema comenzo en Intrepid.

---

### Post by clasificado on 2009-04-29
En principio te recomendaría fijar los hercios verticales y horizontales de tu monitor en el xorg.conf. Es uno de los parámetros que definen el buen funcionamiento de tu monitor y normalmente la detección automática funciona bárbaro, excepto cuando no.

por ejemplo, los de mi flatron w2252s son:

Horizontal Frequency	30KHz~83KHz
Vertical Frequency	56Hz~75Hz

Si querés que te guiemos bien, te abrir el archivo xorg.conf:

```
gksudo gedit /etc/X11/xorg.conf
```

agarrá el contenido y pegalos en este thread como para que veamos como te podemos ayudar

clasificado

---

### Post by Viciuxs on 2009-04-29
Bueno este es mi xorg cunado uso el Monitor CRT y si tengo aceleracion grafica:

> 
Section "Device"
                Identifier    "Configured Video Device"
EndSection

Section "Monitor"
                Identifier    "Configured Monitor"
EndSection

Section "Screen"
                Identifier    "Default Screen"
                Monitor        "Configured Monitor"
                Device        "Configured Video Device"
          SubSection     "Display"
                    Depth       24
                    Modes      "1280x1024" "1024x768" "800x600" "640x480"
         EndSubSection
EndSection
Luego cuando uso el LCD me tira este error: 
 
(EE)intel(0):No valid modes.
(EE)Screen(s)found, but none have a usable configuration.

Y me pide reconfigurar el servidor grafico para poder iniciar el sistema.Luego de reconfigurar la unica forma de que vuelvan a arrancar las x con el monitor LCD es usando el driver VESA osea el modo grafico seguro que este seria el xorg: 
> 
Section "Device"
                Identifier    "Configured Video Device"
                Driver        "vesa"
EndSection

Section "Monitor"
                Identifier    "Configured Monitor"
EndSection

Section "Screen"
                Identifier    "Default Screen"
                Monitor        "Configured Monitor"
                Device        "Configured Video Device"
EndSection
Finalmente aca estan las caracteristicas de mi monitor:
> 
Section "Monitor"
                Identifier     "Philips 170S"
                HorizSync       30.0 - 82.0
                VertRefresh     56.0 - 76.0
                Option         "DPMS"
EndSection

que las saque de esta pagina [http://www.phoronix.com/forums/showthread.php?t=13931](http://www.phoronix.com/forums/showthread.php?t=13931)

---

### Post by Viciuxs on 2009-04-30
Hola algun admin que pueda cerrar el tema porque alfin logre solucionarlo. 
Luego de 5 dias probando mil y una configuraciones en el xorg instalando distintas versiones de drivers intel y kernels alfin e logrado arrancar con el Monitor LCD y aceleracion grafica, parece ser que el problema era que al cargar el grub por defecto lo hacia a una resolucion de 640x480 asi que solo tuve que instalar un programita llamado Administrador de Arranque e ir a Opciones de Arranque>Pantalla y selecionar la resolucion 1280x1024 (que es la optima para mi LCD) y listo problema resuelto.:P

---

