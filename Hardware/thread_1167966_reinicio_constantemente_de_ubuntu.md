---
title: "reinicio constantemente de ubuntu"
date: 2009-05-23
forum: Hardware
---

### Post by elgerjerry on 2009-05-23
Hola Gente. Les quisiera hacer una consulta para ver si a alguien mas  le pasa o me puede dar una idea de como solucionarlo. 

Acabo de instalar mi ubuntu 9.04 jaunty y luego de instalar el driver de video cuanto utilizo alguna caracteristica como transparencia o algo "compose" se reinicia automaticamente la pc. Inicialmente le heche la culpa al compiz ya que nunca se llevo muy bien con mi geforce fx5500. Pero luego de desinstalado si uso la caracteristica de composicion de metacity o xfwm se produce este problema.
Mi pc es un amd athlon xp de 2200+, 764mb de ram, aceleradora fx5500 y mother asus a7n266-vm (chipset nforce)

Desde ya gracias por cualquier ayuda que me puedan dar.):P

---

### Post by juancarlospaco on 2009-05-24
todos los updates?, de donde instalaste el driver?

---

### Post by elgerjerry on 2009-05-25
Los drivers que probe fueron los 2 que me permite jaunty por defecto (173 y 96) y el descargado de la pagina de nvidia.- :(
Los instala bien y funciona bien X luego de la instalacion pero siempre que no active ninguna opcion de composite. Ya sea xfwm o metacity en ambos se produce el problema.- 
Siempre tuvo una mala relacion mi placa con estos drivers ya que en intrepid simplemente colgaban X y ya que estaban la PC.
En Jaunty inicialmente no se producia este cuelgue pero si reinicios esporadicos. Los cuales ultimamente se volvieron exageradamente frecuentes al punto que en este momento uso gnome con metacity sin composite y me quita un par de opciones y funcionamiento de algunos programas como el gnome-do (DOCKY) que estaba muy acostumbrado a usar.

---

### Post by staar on 2009-05-25
mmm, no me parece problema de drivers, tengo la misma placa con el composite funcionando bien, en tu archivo /etc/X11/xorg.conf, tenés una sección como la siguiente? ```

Section "Extensions"
 Option "Composite" "Enable"
EndSection
``` la placa funciona bien? de temperatura como va? en otro SO anda bien?

saludos

---

### Post by elgerjerry on 2009-05-25
El sistema no es. (Reinstale el otro dia y quedo asi luego de la instalacion limpia).
La placa problema de refrigeracion no tiene para hacer las pruebas trabaje con un ventilador apuntandole asi que temperatura no parece ser. Aparte con el dedometro no aparenta estar a mas de 35grados (es decir no quema)...
Lo que me hace sospechar del driver es que cuando desactivo el mismo no se produce ningun reinicio.(uso driver nv por defecto)..
La opcion composite no la tengo en el xorg.conf porque las veces que lo puse X simplemente no corria y preferia activarlo por el apartado de configuracion del xfwm o usando la opcion de composite de metacity.(mediante ubuntu-tweak).
Sin el driver encargandose de X el sistema no reinicia por eso sospechaba del driver.

---

