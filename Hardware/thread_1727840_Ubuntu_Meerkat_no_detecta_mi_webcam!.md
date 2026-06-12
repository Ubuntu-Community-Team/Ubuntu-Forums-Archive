---
title: "Ubuntu Meerkat no detecta mi webcam!"
date: 2011-04-13
forum: Hardware
---

### Post by carega on 2011-04-13
Hola! Estoy usando una laptop compaq presario cq-40-320LA y ubuntu no reconoce la webacm. Alguien que me pueda decir cómo puedo solucinar esto? Skype no detecta la webcam y tampoco Cheese, y cuando uso gstreamer-properties me aparece lo siguiente:
```
carega@amaterasu:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': El dispositivo «/dev/video0» no existe. [v4l_calls.c(168): gst_v4l_open (): /GstPipeline:pipeline0/GstV4lSrc:v4lsrc1]
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': No se puede identificar el dispositivo «/dev/video0». [v4l2_calls.c(488): gst_v4l2_open (): /GstPipeline:pipeline1/GstV4l2Src:v4l2src1:
system error: No existe el fichero o el directorio]
```

Gracias por su ayuda!

---

### Post by mama21mama on 2011-04-13
a ver si forzando cargar el modulo te anda


[fijate aquí ]("http://mamalibre.text0.tk/?q=content/webcam-la-fuerza-en-skype")

---

### Post by carega on 2011-04-13
Hola, gracias por responder!

Seguí los pasos del sitio web que me mandaste y no funcionó nada... te muestro acá lo que me apareció:

```
 carega@amaterasu:~$ #!/bin/bash
carega@amaterasu:~$ modprobe gspca_main autoexpo=0 gamma=5
WARNING: Error inserting videodev (/lib/modules/2.6.35-28-generic/kernel/drivers/media/video/videodev.ko): Operation not permitted
FATAL: Error inserting gspca_main (/lib/modules/2.6.35-28-generic/kernel/drivers/media/video/gspca/gspca_main.ko): Operation not permitted
carega@amaterasu:~$ modprobe gspca_sunplus
WARNING: Error inserting videodev (/lib/modules/2.6.35-28-generic/kernel/drivers/media/video/videodev.ko): Operation not permitted
WARNING: Error inserting gspca_main (/lib/modules/2.6.35-28-generic/kernel/drivers/media/video/gspca/gspca_main.ko): Operation not permitted
FATAL: Error inserting gspca_sunplus (/lib/modules/2.6.35-28-generic/kernel/drivers/media/video/gspca/gspca_sunplus.ko): Operation not permitted
carega@amaterasu:~$ modprobe videodev
FATAL: Error inserting videodev (/lib/modules/2.6.35-28-generic/kernel/drivers/media/video/videodev.ko): Operation not permitted
carega@amaterasu:~$ cvlc v4l2://
VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x963c494] dummy interface: using the dummy interface module...
[0x963fd64] v4l2 demux error: cannot open video device '/dev/video0' (No such file or directory)
[0x963fd64] v4l2 demux error: cannot open video device '/dev/video0' (No such file or directory)
[0x9641674] v4l2 access error: cannot open video device '/dev/video0' (No such file or directory)
[0x9641674] v4l2 access error: cannot open video device '/dev/video0' (No such file or directory)
[0x963afb4] main input error: open of `v4l2://' failed: (null)
[0x963afb4] main input error: Su entrada no puede abrirse
[0x963afb4] main input error: VLC es incapaz de abrir el MRL «v4l2://». Vea el registro para más detalles.
^C[0x962536c] signals interface error: Caught Interrupción signal, exiting... 
```

Creo que el problema está en que la cámara no está siendo detectada por la computadora, lo cual es raro ya que viene con la laptop (ie no es una cámara externa).

---

