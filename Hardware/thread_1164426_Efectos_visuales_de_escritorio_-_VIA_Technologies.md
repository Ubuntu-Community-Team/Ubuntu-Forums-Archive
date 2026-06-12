---
title: "Efectos visuales de escritorio - VIA Technologies"
date: 2009-05-19
forum: Hardware
---

### Post by Transgenic on 2009-05-19
Mi problema es que no puedo activar los efectos visuales del escritorio. 
Buscando bastante por google y encontrando a usuarios con problemas parecidos, intente solucionarlo, pero nada me ha dado resultado. 
 
Viendo otro post de aca (el anterior foro), empezare colocando informacion de mi maquina para que me guien. 
 
 	  			  ```
$ lspci |grep VGA 
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)
```	 
 	  			  ```
$ lsmod |grep drm 
drm                    86056  3 via 
agpgart                42184  2 drm,amd64_agp
```	 
 	  			  ```
$ glxinfo |grep direct 
direct rendering: Yes
```	 
 
Gracias

---

### Post by Carlos C on 2009-05-19
Hola. La verdad es que esa marca no tiene buenos resultados en linux hasta donde sé. Puedes mirar la documentación oficial:

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

Se señala que la aceleración 3D no es muy buena y no siempre funciona. Puedes probar con el método que ahí aparece, compilando los módulos libdrm y drm. Yo que tu le daría una oportunidad y si tienes problemas vuelve a preguntar en este mismo hilo (en ese caso recuerda por favor comentar exactamente qué paso es el que falla)

Saludos
[B][FONT=Book Antiqua][SIZE=2]
[/SIZE][/FONT][/B]

---

### Post by Transgenic on 2009-05-19
Eso lo habia hecho con una version anterior de Ubuntu a la que tengo. Ahora uso Ubuntu 8.10 Intrepid Ibex
Es recomendable actualizar nuevamente mi version?

---

### Post by Carlos C on 2009-05-19
Tengo poca información sobre esa tarjeta. Darte un consejo al respecto sería muy irresponsable de mi parte, por que no sé si te conviene :(. Lo único que puedo decirte es que en el sitio de VIA tienen un paquete para Intrepid Ibex:

[http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)

---

### Post by radixs on 2009-05-20
Mira yo tengo un laptop con esa misma tarjeta, la verdad intente de muchas maneras configurar la acelerecion 3D + lo efectos visuales y siempre obtuve resultados negativos, lo mejor es dejarlo sin efectos visuales... sorry pero es mi experiencia.

---

### Post by Iced_R on 2009-05-25
Lamento desilusionarte colega, pero no vas a poder hacer funcionar esa tarjeta. Yo tb tengo un chipset VIA (el K8M890) y el driver publicado en la página es más que todo compatible con los chipset de notebooks más recientes, y si lees el README del código fuente te aparece que PUEDE funcionar en la versión de P4 de tu chipset, no en la de AMD (no entiendo la diferencia, pero a mi no me ha querido funcionar ni a palos xD).

---

### Post by Transgenic on 2009-05-29
Hola de nuevo.

Ahora actualize a Ubuntu 9.04 y segui los pasos para instalar [OpenChrome]("https://help.ubuntu.com/community/OpenChrome") pero quede atascado en un paso. Me pide ir a la consola (ctrl + alt + F1) y hacer una nueva X (no entiendo nada de esto)

> To test the new driver, go to a console (Ctrl+Alt+F1), log in and start a new X screen:      X :1

Lo hago, me logeo, escribo "X :1" y la pantalla queda en negro y no puedo hacer nada, solo reiniciar, porque si espero tampoco pasa nada.

:confused:

---

### Post by guillermolisi on 2009-06-01
> **Transgenic said:**
> Hola de nuevo.

Ahora actualize a Ubuntu 9.04 y segui los pasos para instalar [OpenChrome]("https://help.ubuntu.com/community/OpenChrome") pero quede atascado en un paso. Me pide ir a la consola (ctrl + alt + F1) y hacer una nueva X (no entiendo nada de esto)



Lo hago, me logeo, escribo "X :1" y la pantalla queda en negro y no puedo hacer nada, solo reiniciar, porque si espero tampoco pasa nada.

:confused:
Para probar como funciona con el nuevo driver podes cerrar tu sesion y en la pantalla de login elegis "Reiniciar el servidor X". Si todo salio bien, podras usar la maquina con todos los "chiches" graficos.

Si no funciona bien, con editar el archivo /etc/X11/xorg.conf y cambiar el nombre del driver existente por "vesa" (sin comillas) es suficiente (reiniciando X-server nuevamente).

---

### Post by radixs on 2009-06-01
Disculpa, pero esa instalación es para ubuntu 7.10, yo intente instalarlo tipenado

```
sudo apt-get install xserver-xorg-video-openchrome
```y me salio un mensaje diciendo que ya esta en la versión mas reciente.

PD: lo efectos visuales en esta tarjeta son casi imposibles, lo mejor que puedes hacer es quedarte con aceleración 2D. claramente en la web dice que se a logrado tener efectos visuales con VIA. Pero al realizar los pasos siempre hay resultados negativos.

---

### Post by Transgenic on 2009-06-03
No encontre nada que dijiera drivers, aca dejo lo que muestra el archivo:

```
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
EndSection
```Tampoco encontre algo como Reiniciar el servidor X, solo habia algo de un scrip X, lo hice pero no paso nada.

radixs, la instalacion no es tan solo para 7.10, tambien se puede para superiores, lo hice siguiendo los pasos de la pagina.
Ingresando eso tambien me dice que tengo la version mas reciente.

Creo que seria mi ultimo intento.. ya no tengo esperanzas xD

---

### Post by icarofallen on 2009-06-04
Hola, quizás te funcione lo que yo hice en mi notebook:

en la terminal le das

$ sudo gedit /usr/bin/compiz

y en el archivo que se te abrira borras la parte 

# blacklist based on the pci ids ....hasta....
BLACKLIST_PCIIDS="$T"

luego reinicias y debiese funcionar.

Espero te sirva.

---

### Post by nopersona on 2009-06-04
Mira, lamento desilucionarte, pero a los chipset via NO se les puede sacar aceleración 3d, a los más un 2 d muy pobre, que es el controlador que entregra via para Linux. Ni con openchrome, ni con nada. En el otro foro hay bastante información al respecto. Lo siento, cosas del destino... y de los fabricantes.

Lo mejor es comprar una trajetita barata, y olvidarse de esos chips, que dicho sea de paso, dejan bastante que desear, tanto en windous como en linux. 


P.S.: Dato extra, con la nueva versión de metacity se le puede sacar un composite más o menos decente, que te da para activar algunas aplicaciones como cairo dock, screenlets, y algo más. Sería.

---

### Post by moreback on 2009-06-07
> **nopersona said:**
> P.S.: Dato extra, con la nueva versión de metacity se le puede sacar un composite más o menos decente, que te da para activar algunas aplicaciones como cairo dock, screenlets, y algo más. Sería.

**/apps/metacity/general/compositing_manager**
Determines whether Metacity is a compositing manager.

Editar con gconf-editor (Aplicaciones -> Herramientas del sistema -> Editor de configuración)

Supongo que es esa opción, no?

---

### Post by Marcos on 2009-06-07
> **nopersona said:**
> Mira, lamento desilucionarte, pero a los chipset via NO se les puede sacar aceleración 3d, a los más un 2 d muy pobre, que es el controlador que entregra via para Linux. Ni con openchrome, ni con nada. En el otro foro hay bastante información al respecto. Lo siento, cosas del destino... y de los fabricantes.

Lo mejor es comprar una trajetita barata, y olvidarse de esos chips, que dicho sea de paso, dejan bastante que desear, tanto en windous como en linux.

Doy fe de lo que dice nopersona. Efectivamente, los chipset VIA solamente poseen 2D. Incluso en una de las páginas de VIA sobre Linux lo especifica (no tengo ya la dirección).

Mi experiencia con una VIA Chrome9 HC en Linux fue pésima. Desde Ubuntu 6.06 si mal no recuerdo que, cada vez que instalaba, debía configurar manualmente xconf.org. Para que nombrar que nunca pude sacarle aceleración 3D.

---

### Post by dbyjazz on 2009-10-25
¿Es imposible?

---

### Post by guillermolisi on 2009-10-26
Solo para prolongar la esperanza (porque fui uno de los que desistio al tener dos maquinas con ese bendito chip de video y termine comprando sendas placas con nVidia), te paso como tengo configurado el archivo /etc/X11/xorg.conf en una de ellas. Ahi podras ver la mencion al driver remarcada en rojo:
> guille@guillermo:~$ cat /etc/X11/xorg.conf
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Feb 14 18:20:37 PST 2008                                                                       
# xorg.conf (xorg X Window System server configuration file)                  
#                                                                             
# This file was generated by dexconf, the Debian X Configuration tool, using  
# values from the debconf database.                                           
#                                                                             
# Edit this file with caution, and see the xorg.conf manual page.             
# (Type "man xorg.conf" at the shell prompt.)                                 
#                                                                             
# This file is automatically updated on xserver-xorg package upgrades *only*  
# if it has not been modified since the last upgrade of the xserver-xorg      
# package.                                                                    
#                                                                             
# If you have edited this file but would like it to be automatically updated  
# again, run the following command:                                           
#   sudo dpkg-reconfigure -phigh xserver-xorg                                 

Section "Monitor"
        Identifier     "Samsung"
        VendorName     "Samsung"
        ModelName      "Samsung SyncMaster 794MB/794MBplus/798MB"
        HorizSync       30.0 - 70.0                              
        VertRefresh     50.0 - 160.0                             
        Gamma           1                                        
        ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync                                                                      
        ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync                                                                      
        ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync                                                                      
        ModeLine       "640x480@85" 36.0 640 696 752 832 480 481 484 509 -hsync -vsync                                                                      
        ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync                                                                     
        ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync                                                                     
        ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync                                                                     
        ModeLine       "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync                                                                     
        ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync                                                                     
        ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync                                                                     
        ModeLine       "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync                                                                 
        ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync                                                                 
        ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync                                                                 
        ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync                                                                 
        ModeLine       "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync +vsync interlace                                                       
        ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync                                                                
        ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync                                                                
        ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync                                                           
        ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync                                                           
EndSection                                                                    

Section "Monitor"
        Identifier     "monitor1"
        VendorName     "Plug 'n' Play"
        ModelName      "Plug 'n' Play"
        Gamma           1             
        ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync                                                                      
        ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync                                                                      
        ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync                                                                      
        ModeLine       "640x480@85" 36.0 640 696 752 832 480 481 484 509 -hsync -vsync                                                                      
        ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync                                                                     
        ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync                                                                     
        ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync                                                                     
        ModeLine       "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync                                                                     
        ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync                                                                     
        ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync                                                                     
        ModeLine       "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync                                                                 
        ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync                                                                 
        ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync                                                                 
        ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync                                                                 
        ModeLine       "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync +vsync interlace                                                       
        ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync                                                                
        ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync                                                                
        ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync                                                           
        ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync                                                           
EndSection                                                                    

Section "Screen"
        Identifier     "Default Screen"
        Device         "nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)]"
        Monitor        "Samsung"                                              
        Option         "NoLogo" "True"                                        
        DefaultDepth    24                                                    
        SubSection "Display"                                                  
                Virtual     1280 1024                                         
                Depth       24                                                
                Modes      "1280x1024@60" "1400x1050@60" "1280x960@60" "1152x864@75" "1024x768@43" "1024x768@60" "1024x768@70" "1024x768@75" "1024x768@85" "832x624@75" "800x600@60" "800x600@85" "800x600@75" "800x600@72" "800x600@56" "640x480@85" "640x480@75" "640x480@72" "640x480@60"                            
        EndSubSection                                                         
EndSection                                                                    

Section "Screen"
        Identifier     "screen1"
        Device         "device1"
        Monitor        "monitor1"
        DefaultDepth    24       
        Option         "AddARGBGLXVisuals" "True"
        SubSection "Display"                     
                Depth       24                   
                Modes      "640x480@60" "640x480@72" "640x480@75" "640x480@85" "800x600@56" "800x600@72" "800x600@75" "800x600@85" "800x600@60" "832x624@75" "1024x768@85" "1024x768@75" "1024x768@70" "1024x768@60" "1024x768@43" "1152x864@75" "1280x960@60" "1280x1024@60" "1400x1050@60"                            
        EndSubSection                                                         
EndSection                                                                    

Section "Module"
        Load           "v4l"
        Load    "glx"       
        Disable "dri2"      
EndSection                  

Section "InputDevice"
        Identifier     "Generic Keyboard"
        Driver         "kbd"             
        Option         "CoreKeyboard"    
        Option         "XkbRules" "xorg" 
        Option         "XkbModel" "pc105"
        Option         "XkbLayout" "latam"
EndSection                                

Section "InputDevice"
        Identifier     "Configured Mouse"
        Driver         "mouse"           
        Option         "CorePointer"     
        Option         "Device" "/dev/input/mice"
        Option         "Protocol" "ImPS/2"       
        Option         "ZAxisMapping" "4 5"      
        Option         "Emulate3Buttons" "true"  
EndSection                                       

Section "InputDevice"
        Identifier     "stylus"
        Driver         "wacom" 
        Option         "Device" "/dev/input/wacom"
        Option         "Type" "stylus"            
        Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection                                                  

Section "InputDevice"
        Identifier     "eraser"
        Driver         "wacom" 
        Option         "Device" "/dev/input/wacom"
        Option         "Type" "eraser"            
        Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection                                                  

Section "InputDevice"
        Identifier     "cursor"
        Driver         "wacom" 
        Option         "Device" "/dev/input/wacom"
        Option         "Type" "cursor"            
        Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection                                                  

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "Default Screen" 0 0
        InputDevice    "Generic Keyboard"  
        InputDevice    "Configured Mouse"  
        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "Device"
        Identifier     "nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)]"
        VendorName     "NVIDIA"
        BoardName      "NVIDIA GeForce 6 Series"
        BusID          "PCI:2:0:0"
        Screen          0
        Option  "NoLogo"        "True"
        [COLOR=Red]Driver  "vesa"[/COLOR]
EndSection

Section "Device"
        Identifier     "device1"
        VendorName     "NVIDIA"
        BoardName      "NVIDIA GeForce 6 Series"
        BusID          "PCI:2:0:0"
        Screen          1
        Driver  "nvidia"
EndSection

Section "ServerFlags"
        [COLOR=Blue]Option  "DontZap"       "False"[/COLOR]
EndSectionLo que remarque en azul sirve para rehabilitar la combinacion de Ctrl-Alt-Backspace para reiniciar la sesion X cuando no te responde mas (no es un logout, es algo mas violento, parecido a ir a una consola y correr "sudo /etc/init.d/<gdm/kdm> restart" (descartar el display manager que no uses de lo que esta entre angulos, y los angulos tambien)

---

### Post by guillermolisi on 2009-10-26
> **dbyjazz said:**
> ¿Es imposible?
Yo diria que si, que es imposible por ahora siempre que VIA mantenga su actual politica respecto de drivers para Linux.

---

### Post by dbyjazz on 2009-10-28
Yo no soy muy bueno en español, por favor discúlpame. He encontrado este [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

---

### Post by guillermolisi on 2009-10-28
> **dbyjazz said:**
> Yo no soy muy bueno en español, por favor discúlpame. He encontrado este [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)
Ya lo habian pasado [al principio del thread]("http://ubuntuforums.org/showpost.php?p=7310722&postcount=2"). Gracias igual !

---

