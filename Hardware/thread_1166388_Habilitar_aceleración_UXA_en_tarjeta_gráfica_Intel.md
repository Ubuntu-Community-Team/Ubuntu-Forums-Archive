---
title: "Habilitar aceleración UXA en tarjeta gráfica Intel"
date: 2009-05-21
forum: Hardware
---

### Post by moreback on 2009-05-21
Con Ubuntu 9.04 viene X.org 1.6, el cual viene con UXA que se supone reemplazará al EXA que se usaba como arquitectura aceleración anteriormente. Como es algo relativamente nuevo a tenido algunos problemas de estabilidad en Ubuntu, por lo que no viene activado, pero igual ha habido gente que ha tenido excelentes experiencias. 
 
Para información de como activarlo, lo mejor es revisar aquí [https://wiki.ubuntu.com/X/UxaTesting](https://wiki.ubuntu.com/X/UxaTesting), pero en resumen, tienes que agregar **Option AccelMethod" "UXA"** dentro de la sección "Device" de tu xorg.conf

```
Section "Device"
        Identifier    "Configured Video Device"
        # ...
        **Option        "AccelMethod" "uxa"**
EndSection
```NOTA: Con la versión 9.04 varias tarjetas Intel cayeron dentro de una lista negra de Compiz y por esta razón, a pesar de habilitar UXA no podremos activar los efectos. Para que Compiz no tome en cuenta la lista negra, hay que agregar la línea

```
SKIP_CHECKS=yes
```dentro del archivo **/etc/xdg/compiz/compiz-manager**.

PD. Resumen del post antiguo [http://foros.ubuntu-cl.org/viewtopic.php?t=8198](http://foros.ubuntu-cl.org/viewtopic.php?t=8198)

---

### Post by Carlos C on 2009-05-21
Y si quieren más información útil pueden mirar acá:

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

### Post by kubuntero on 2009-05-26
yo arreglé el problema de rendimiento revirtiendo la versión del driver de video a la de intrepid.

acá está la info [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

es realmente muy sencillo

---

### Post by ClarkXP on 2009-05-26
de todas maneras dentro del archivo de configuracion de compiz
buscas la linea donde comienza la blacklist:

# blacklist based on the pci ids

y ahi estan debidamente documentados los modelos de tarjetas,
simplemente buscas tu modelo de tarjeta y lo comentas con un #
asi:
T=”$T 8086:2a02 ” # Intel GM965

comentado que asi

#T=”$T 8086:2a02 ” # Intel GM965

yo tuve personalmente problemas con este chipset
con compiz corriendo les comento que en ocacsiones simplemente se baja el brillo, onda como si estuviera con solo bateria, pero nada más.

corriendo juegos no he probado.

---

### Post by RafaelG on 2009-06-04
Hola disculpen bueno tengo una pequena consulta y discrepancia ya que en mi Xorg.conf aparece:

Section "Device"
    Identifier    "Configured Video Device"
EndSection

NO APARECE: 

Section "Device"
        Identifier    "Configured Video Device"
        # ...

mi consulta y mi discrepancia es por que en tu Howto aparece al final (#...) y en mi xorg.conf no aparece eso, disculpe que pregunte este detalle pero quiero activar la aceleracion UXA pero se que si no lo hago bien en el xorg.conf puedo danar el archivo por eso prefiero saber exactamente que es lo que se debe agregar, si es solamente

Option        "AccelMethod" "uxa" 

o 

# ...
        Option        "AccelMethod" "uxa"

---

### Post by Carlos C on 2009-06-04
> **RafaelG said:**
> prefiero saber exactamente que es lo que se debe agregar, si es solamente

Option        "AccelMethod" "uxa" 

Sí, eso es.

Saludos!

---

### Post by RafaelG on 2009-06-05
Gracias Carlos ya active UXA.

---

### Post by Carlos C on 2009-06-08
[Post de la semana]("http://ubuntuforums.org/showthread.php?t=1176055"): [Mayo 27, 2009]("http://ubuntucl.wordpress.com/2009/05/27/habilitar-aceleracion-uxa-en-tarjeta-grafica-intel/").

---

