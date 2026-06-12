---
title: "Installation sucessfull, ahora problema con audio y vids"
date: 2009-06-11
forum: Hardware
---

### Post by Barasuishou on 2009-06-11
Hola, bueno no se como pero la bendición de dios(o sea la deidad que sea XD) cayó sobre mi y justo hoy cayeron en mi puerta los cds que tanto esperaba el de ubuntu y el de kubuntu 9.04, con mucha emoción me puse a formatear la pc, y volví a instalar todas las aplicaciones que utilizo, y todo funciona de lujo, estoy más que contento con mi instalación, al final me decidí por instalar solo kubuntu, y empezar a investigarlo kde un poco más y a configurarlo según mis preferencias

al parecer todo funciona de lujo, solo tengo unos pequeños inconvenientes, de seguro de fácil resolución

1.el sonido sale por mi parlante "frontal" el ubicado en mi monitor, pero además tengo conectado un edifier x100, si no me equivoco en la entrada de parlantes laterales, pero no sale sonido alguno a través de estos, ¿alguna solución?

2.(no probe con konqueror pero según recuerdo pasa lo mismo), usando firefox los videos reproducidos tipo youtube o en cualquier web cuelgan a los pocos segundos de iniciarse y de tener abierta otra aplicación que utilize el audio no reproducen sonido, ¿alguna idea?

3.el audacity me reconoce el mic de la cam logitech quickcam 9000, pero al grabar graba medio segundo y luego deja de captar, digo captar por que el control de grabación continúa pero no se registra nada ni una linea aparece luego del medio segundo pasado, ¿alguna solución? 

gracias  por todos los consejos ayuda, seguiré investigando para ver si encuentro algún otro problema para consultar, 

me despido chauu

---

### Post by staar on 2009-06-11
me parecen todos síntomas del mismo problema, la placa de audio, posteá la salida de poner ```
lspci
``` en una Terminal (Konsole en kubuntu)

saludos

---

### Post by Barasuishou on 2009-06-11
primero que nada gracias por la ayuda pero me ah pasado esto

con tristeza debo decir que tube un problema mayor y supongo ocasionado debido a el ext4(supongo), se me "rompió" kde, cuando trataba de iniciar sesión aparecía la pantalla donde carga "los iconos" cargaba hasta el "mundo" y después moría ahí diciendo que no podía iniciar kde, y tuve que volver a formatear debido a poco tiempo ya que para mañana tengo que terminar un trabajo para la facultad, esta vez (por las dudas) puse gnome, además no se si era por los efectos de escritorio o que pero el rendimiento en juegos era menor al que había tenido previamente, me refiero a juegos nativos precisamente el doom3

realmente me gusta más kde pero no tengo suerte con este al parecer XS, de todas formas no me rendiré =D, ahora tengo una duda mi procesador es un AMD Athlon64 1.8ghz +3000, y mi placa de video una Nvidia Geforce 7100gs, por cuestion de rendimiento en gaming, 

1.¿recomiendan me quede en gnome, o vuelva a intentarlo con kde(lo que me gustaría)?

2.¿activo o desactivo los efectos de escritorio(si en algo afecta)?

3.¿los entornos de escritorio, kde o gnome, tienen mejor rendimiento en distribuciones en las que "se les da más bola"?, ej:gnome rinde más en ubuntu, kde rinde más en opensuse,etc.

---

### Post by staar on 2009-06-12
uh, que bardo, no habrá habido un error en la instalación che? que raro...

por el rendimiento en juegos no te hagas problema, los drivers de nvidia para linux son muy buenos (aunque privativos), a tu placa le van a sacar todo el jugo posible, eso sí, antes de lanzar el juego es mejor desactivar los efectos visuales (KDE tiene un atajo global para esto, Alt + Shift + F12)

la decisión entre entornos de escritorio, es una cuestión de gusto personal, entre gnome y KDE no hay grandes diferencias de rendimiento...

placa para los efectos de escritorio, tenés, yo con una FX 5500 los muevo perfectamente (eso sí, nada muy sobrecargado, algunos efectitos útiles nomás, los chiches los dejo para cuando vienen visitas :-D)

el tema de cual escritorio rinde más en que distro, también es relativo, lo mejor es comprobarlo en carne propia, aunque hay algunas cosas que se notan, kde en ubuntu no está demasiado pulido, aunque en jaunty se mejoró mucho, el soporte es mucho (MUCHO) mayor para gnome, igual si querés rendimiento, o te pasas a un escritorio más liviano, o te vás a una distro mas liviana (arch con KDEMod va como trompada :-D:-D) y opensuse no es precisamente reconocida porque en ella KDE vaya rápido :-P (por lo menos en la última versión)

saludos

---

### Post by Barasuishou on 2009-06-12
bien acabo de reinstalar kubuntu, y al parecer esta vez anda bien, a ver voy a poner en consola eso que me dijiste a ver si se arregla mi problema de "audio"

bien y me devuelve esto:

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] AddressMap
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation GeForce 7100 GS (rev a1)


a ver si esto ayuda

gracias por ayudarme, disculpas si soy algo "pesado", estoy intentando hacer el cambio total a linux, solo me quedan pequeñas cosas por resolver para poder completarlo  :), por eso "insisto"

---

### Post by Barasuishou on 2009-06-13
olvide aclarar los videos ya no cuelgan, y ahora ando usando (y comenzando a amar) konqueror, 

pero sigo teníendo los problemas de audio, el del audacity, y  el de audio "no compartido" por aplicaciones

espero respuesta gracias por todo chauuu

---

### Post by staar on 2009-06-13
tenés instalados todos los paquetes que se refieran a phonon, en particular los que hagan de puente con gstreamer o xine?

saludos

---

### Post by Barasuishou on 2009-06-14
la verdad qeu no se, ahora los busco en el KPackageKit e instalo todos menos el dev

---

### Post by Barasuishou on 2009-06-16
ayuda por favor, hoy reformatié para acomodar unas cosas y poner el /usr en otra partición, terminé de instalar todo, reinicié, y me volvió a pasar, no me puede cargar el kde cuando trato de loguearme, pasa exactamente lo mismo, me tira un error diciendo que no tengo permisos de escritura en /miusuario/nomeacuerdocuando XS, le doy aceptar y después aparece un cartel en la esquina derecha superior diciendo que no pudo iniciar kdmserver, alguien me ayuda?, incluso había solucionado el tema con los parlantes TT_TT, no quiero formatear otra vez por favor ayuda 

espero alguna repuesta, gracias me despido suerte chauuuu

---

### Post by staar on 2009-06-16
porque poner el /usr en otra partición?? poné el error exacto que te tira...

saludos

---

### Post by Barasuishou on 2009-06-16
esto es exactamente lo que dice:

the following instalation problem was detected while trying to start KDE:
no write access to '/home/miusuario/.ICEauthority'.
KDE is unable to start

después de dar aceptar eso en la ventana que aparece a la derecha dice:
could not start ksmserver. Check your installation

doy ok, y me manda devuelta al login

---

### Post by Hei Ku on 2009-06-16
Por consola, borrá ese archivo

sudo rm /home/usuario/.ICEauthority

---

### Post by Barasuishou on 2009-06-16
muchas gracias, ahí se arregló y ya puedo loguearme y usar todo bien,

ahora tengo otro problema, instalé de forma nativa con los .run el quake4 y el doom3, pero no me inician, al hacer click en el icono intenta iniciar pero después se cierra, probé pro konsola a ver si era problema de permisos y me tiró este error

Free86-VidModeExtension Activated at 640x480                               
Xlib:  extension "GLX" missing on display ":0.0".                          
Xlib:  extension "GLX" missing on display ":0.0".                          
Xlib:  extension "GLX" missing on display ":0.0".                          
Xlib:  extension "GLX" missing on display ":0.0".                          
Xlib:  extension "GLX" missing on display ":0.0".                          
Xlib:  extension "GLX" missing on display ":0.0".                          
Xlib:  extension "GLX" missing on display ":0.0".                          
Xlib:  extension "GLX" missing on display ":0.0".                          
Xlib:  extension "GLX" missing on display ":0.0".                          
Xlib:  extension "GLX" missing on display ":0.0".                          
Xlib:  extension "GLX" missing on display ":0.0".                          
Xlib:  extension "GLX" missing on display ":0.0".                          
Xlib:  extension "GLX" missing on display ":0.0".                          
Xlib:  extension "GLX" missing on display ":0.0".                          
Xlib:  extension "GLX" missing on display ":0.0".                          
Xlib:  extension "GLX" missing on display ":0.0".                          
Couldn't get a visual                                                      
dlopen(libGL.so.1)                                                         
Initializing OpenGL display                                                
Using XFree86-VidModeExtension Version 2.2                                 
DGA DirectVideo Mouse (Version 2.0) initialized                            
Free86-VidModeExtension Activated at 640x480                               
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Couldn't get a visual
idRenderSystem::Shutdown()
Xlib:  extension "GLX" missing on display ":0.0".
Fatal X Error:
  Major opcode of failed request: 105
  Minor opcode of failed request: 0
  Serial number of failed request: 36
BadValue (integer parameter out of range for operation)
Fatal X Error:
  Major opcode of failed request: 2
  Minor opcode of failed request: 0
  Serial number of failed request: 40
BadWindow (invalid Window parameter)
Fatal X Error:
  Major opcode of failed request: 4
  Minor opcode of failed request: 0
  Serial number of failed request: 41
BadWindow (invalid Window parameter)
Sys_Error: Unable to initialize OpenGL

alguna idea?

desde ya muchísimas gracias por ayudarme a recuperar mi pc =D, aa y solo por curiosisdad,  ¿cuando borré el archivo se generó uno nuevo?

acabo de descubrir que tampoco me deja reactivar los efectos de escritorio que previamente había desactivado para jugar

---

### Post by Barasuishou on 2009-06-16
bueno tratándo de ver en el panel de nvidia que andaba mal, me dijo que haga un 'nvidia-config', hize   eso y me volvió a pasar lo del .ICEauthority, lo volví a borrar y al parecer todo anda de lujo ahora, así que muchísimas gracias =)

---

### Post by Barasuishou on 2009-06-16
ahora pregunta, tengo problemas para abrir hotmail en konqueror, me cuelga cuando abro hotmail :S

---

### Post by staar on 2009-06-16
konqueror no se lleva bien con hotmail, en realidad, ningún navegador en serio se lleva bien con ESO (IE no cuenta), me parece que vas a tener que probar con otro navegador...

saludos

---

