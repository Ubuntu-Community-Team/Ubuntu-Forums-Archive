---
title: "Cómo instalar drivers para video"
date: 2009-05-09
forum: Hardware
---

### Post by cor_stellae on 2009-05-09
Hola:

He estado teniendo problemas con programas como Stellarium y Google Earth. El primero no se visualiza bien (el monitor no responde adecuadamente) y el segundo no se visualiza del todo. Lo que me sospecho es que no tengo instalado ningún controlador de video para la tarjeta de video de la computadora. Esto se explica porque soy nueva usando Ubuntu.

El disco original de controladores indica que es una tarjeta de la serie Intel-Via, pero ni idea de cuál puede ser el modelo específico.

Lo que me gustaría saber es cómo averiguar en Ubuntu cuál es el controlador que necesito y, desde luego, cómo instalarlo.

Adjunto captura de pantalla del error que reporta Google. El sistema es Ubuntu Jaunty Jackalope.

---

### Post by pablo.s on 2009-05-09
Comando **[COLOR=DarkGreen]lspci[/COLOR]**:

**[COLOR=DarkGreen]l[/COLOR]**i[COLOR=DarkGreen]**s**[/COLOR]t **[COLOR=DarkGreen]pci[/COLOR]** 

pero debes escribir en
una terminal

lspci

y pegar en un post nuevo
el resultado. Algo me dice
que la placa no puede ser
Intel-Via.

---

### Post by cor_stellae on 2009-05-09
Aquí van, Pablo... todos dicen Via por todo lado... :)

---

### Post by pablo.s on 2009-05-09
En Windows no aparece como
Unichrome la placa de video?
De ser asi... no 3D para ti.

EDIT: El tema es que esta placa
funciona en GNU/Linux con un
driver abierto llamado OpenChrome
que solo tiene 2D.
GoogleEarth es un programa que
utiliza gráficos 3D y sin aceleración
no funciona.

---

### Post by cor_stellae on 2009-05-09
Mmmm... no entiendo, ¿en cuál Windows? Siempre he podido correr bien programas como Google Earth (antes lo tenía instalado en Windows) y el equivalente a Stellarium que usaba allá, el Backyard... no veo por qué no pueda manejar lo mismo en Ubuntu..., si el hardware sí lo permite...

---

### Post by pablo.s on 2009-05-09
Es por la implementación del
driver. En Windows el driver lo
programa la misma gente que
fabrica la tarjeta de video. Pero
como no han programado un
driver igual para Linux, la comunidad
ha realizado una implementación
libre (o sea el código se puede
mejorar y ver) que todavia no ha
logrado habilitar las propiedades
3D de la placa.

Actualización: Parece que han 
habilitado el 3D pero no funciona
siempre, lo que en la práctica es 
lo mismo que nada.

---

### Post by cor_stellae on 2009-05-09
¡qué triste!

Bueno, no desfallezco... estoy siguiendo las instrucciones que encontré aquí:
[URL="http://www.guia-ubuntu.org/index.php?title=Aceleraci%C3%83%C2%B3n_gr%C3%83%C2%A1fica_VIA_/_ASROC"]
http://www.guia-ubuntu.org/index.php?title=Aceleración_gráfica_VIA_/_ASROC[/URL]

---

### Post by cor_stellae on 2009-05-09
A ver si me pueden ayudar un poquitín más...

Me encontré en otro foro un método para instalar los drivers de mi tarjeta madre, pero me quedé bloqueda en lo más básico. La instrucción dice "hay que ejecutar en modo root"... y ¡no sé cómo hacerlo! Intenté abrir el nautilos y hacerle doble clic al archivo, pero no pasó nada. Algo me dice que debo escribir algo en la consola... ¿me pueden dar una luz sobre qué debo poner exactamente? 

La ruta del archivo sería esta: /home/roweena/Documentos/Software para Ubuntu/Controladores de hardware/Via Unichrome

Adjunto aquí las instrucciones que encontré y el link:

------------------------------------
[http://foros.ubuntu-cl.org/viewtopic.php?t=4823](http://foros.ubuntu-cl.org/viewtopic.php?t=4823)

Despues de tiempo buscando en la web logre solucionar el problema, espero esto le sirva a mas personas. 
Bueno para hacerlo mas sencillo lo que hice fue descargar el driver oficial de la pagina de [VIA.]("http://www.viaarena.com/default.aspx?PageID=2&OSID=45&CatID=3220") Ahí tienes que buscar el driver según tu chip en mi caso P4M800/CE/Pro UniChrome Pro integrated graphics. Lo que se hace ahora es descomprimir el zip y ejecutar en modo root el archivo VIA_U710_UniChrome-GFX-v40072d.run. Nos saldrá lo siguiente: 
 
Verifying archive integrity… All good. 
Uncompressing VIA UniChrome (Pro) Family Linux Graphics Driver for Ubuntu 7.10 v40072d……… 
Please choose the job you want to do: 
1. Install driver 
2. Uninstall driver 
 
Entonces le damos a 1 para instalar el driver. 
Después de instalar modificamos el xorg.conf, para poner el teclado en español: 
 
$ sudo nano /etc/X11/xorg.conf  
Section “InputDevice” 
Identifier      “Generic Keyboard” 
Driver          “kbd” 
Option          “CoreKeyboard” 
Option          “XkbRules”      “xorg” 
Option          “XkbModel”      “pc105&#8243; 
Option          “XkbLayout”     “es” 
EndSection 
 
Y ahora queda lo ultimo, tienes que editar el archivo /usr/bin/compiz con sudo nano /usr/bin/compiz y donde dice WHITELIST = "nvidia ati raedon...." agregá via con minúsculas. Reiniciamos y listo. 
Ahora tendríamos el sistema listo para usar los efectos de escritorio compiz. No funciona de maravilla lo recomendable es usar una tarjeta con chip Nvidia, pero por mientras va bien.

---

### Post by pablo.s on 2009-05-09
> **cor_stellae said:**
>  La instrucción dice "hay que ejecutar en modo root"... y ¡no sé cómo hacerlo! Intenté abrir el nautilos y hacerle doble clic al archivo, pero no pasó nada. Algo me dice que debo escribir algo en la consola... ¿me pueden dar una luz sobre qué debo poner exactamente? 

La ruta del archivo sería esta: /home/roweena/Documentos/Software para Ubuntu/Controladores de hardware/Via Unichrome


Escribe en una terminal

**[COLOR=DarkGreen]cd /home/roweena/Documentos/Software\ para\ Ubuntu/Controladores\ de\ hardware/Via\ Unichrome[/COLOR]**

luego

[COLOR=DarkGreen]**sudo sh VIA_U710_UniChrome-GFX-v40072d.run**[/COLOR]

---

### Post by cor_stellae on 2009-05-09
Mil gracias... ya logré esa parte... Ahora, cuando me salen esas ventanitas que tienen abajo un menú lleno de simbolitos con techitos y letras para aplicar comandos... ¿cómo guardo? Me refiero sobre todo al archivo COMPIZ, que se debe modificar... lo que pasa es que logro modificarlo pero no guardarlo como se debe... (Yo y mis ignorancias ubunteras...)...

---

### Post by pablo.s on 2009-05-09
Ya volví, tuve un problema con un disco.
Estaba bajando un archivo torrent y
comenzó a dar error de disco. Reinicié
la maquina y salió el error 17 de Grub.
No te preocupes, comento al aire.

> **cor_stellae said:**
> Mil gracias... ya logré esa parte... Ahora, cuando me salen esas ventanitas que tienen abajo un menú lleno de simbolitos con techitos y letras para aplicar comandos... ¿cómo guardo?

Ah, ese programa se llama **[COLOR=DarkGreen]nano[/COLOR]**, es uno
de los mejores editores de texto que existen.
Para **[COLOR=DarkGreen]guardar[/COLOR]** lo que escribes presionas
**[COLOR=DarkGreen]Control + O[/COLOR]** y para salir del programa **[COLOR=DarkGreen]Control[/COLOR]**
[COLOR=DarkGreen]**+ X.**[/COLOR]

> **cor_stellae said:**
>  Me refiero sobre todo al archivo COMPIZ, que se debe modificar... lo que pasa es que logro modificarlo pero no guardarlo como se debe... 

No te preocupes por ese archivo, para
tu problema actual no es relevante, es más,
mejor que no lo actives por ahora.

> **cor_stellae said:**
> (Yo y mis ignorancias ubunteras...)...

Vas bien, estás aprendiendo mucho y
muy pronto. Linux no es como Mac, requiere
aprender y entender bastante, pero para una
persona inteligente no es problema eso.

---

### Post by cor_stellae on 2009-05-11
Muchas gracias, Pablo, por toda la ayuda. Ya logré modificar el archivo, pero igual no funcionó... En fin, sobreviviré sin 3D por ahora. :-({|=

---

