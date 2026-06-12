---
title: "Casi How to compiz y via made in ubuntu-es"
date: 2008-01-21
forum: Hardware
---

### Post by anka on 2008-01-21
Buenas, voy al grano.

Teniendo en cuenta de que hice un ["casi how to"]("http://www.ubuntu-es.org/index.php?q=node/74158") para hacer andar compiz en una placa via en ubuntu-es, la idea es transcribirla aca, mas que nada porque en este pais los mother asrock con esas placas abundan. Ayer, domingo, aparecio un usuario (Rex creo que era el nombre), que siguio el tuto y le anduvo bien (el primer argentino al que se que le anda, aparte de mi), asi que dije.., "por que no?". Si esta aca el how to se puede mejorar con el aporte de los usuarios y quedar lindo. Aclaro que no lo segui porque esa maquina para mi tiene tendencias suicidas (el xorg en especial :P).

**Bue.., copypasteo:**

Bueno, les paso a comentar lo que logre y lo que aun no logro (y temo no saber como todavia). Se los dividi en 2 partes, una parte tipo how to.., no completa y mas abajo la duda que surgio.

Poseo una pc que casi no uso, una PIV 2.8 Ghz, 1 gb de ram, un disco de 80 Gb y.., una horrible.., pero mucho muy fea mother Asrock 775VM800.., si, tiene una placa de video integrada S3 unichrome pro igp con no me acuerdo que chip (p4m800.., creo, no estoy seguro). Con ella probe varias distros, incluida la de ahora Ubuntu 7.10.

No les cuento la cantidad de veces que mate mi xorg en busqueda de, por lo menos aceleracion, probando desde la pagina de openchrome, de synaptic etc.., un desastre total..., pero se hizo la luz.. casi

Gracias a [este post]("http://www.ubuntu-es.org/index.php?q=node/73901") me entero que viaarena puso un [driver nuevo]("http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3220&SubCatID=150"), especial para Ubuntu 7.10 y otro para 7.04 (me voy a referir a 7.10 por ser la version en donde lo probe y la ultima disponible). Digamos que, como usuario de Ubuntu 7.04 me pico la intriga de probar nuevamente ese driver en esa maquina con Ubuntu 7.10, total, no perdia nada. Lo baje, veo que tiene un txt, un pdf y el .run, hermoso. Bueno, paso a explicarles como se instala de paso. Aviso que esto se hizo luego de una instalacion limpia, toma todos los recaudos necesarios antes, desinstale algun otro driver y, como dice un amigo "this comes whitout any warranty":

**_SECCION "CASI" COMO:_**

Al archivo.run, hay que darle permisos de ejecucion, en mi caso como justo lo tenia descomprimido.., boton derechon>>propiedades>>permisos y tildan ejecucion. Luego en la terminal ponen:

sh nombredelarchivo.run

Ahi tenemos la opcion de instalarlo o desisntalarlo, instalamos, reiniciamos las X y listo. Aca pueden surgir 2 problemas, uno seguro.., te cambia el idioma del teclado a ingles, busca como cambiarlo (sino esto se va a hacer muy largo), otra es que te tome cualquier monitor y con resoluciones raras (como en mi caso, que me tomo que tenia un LCD Wide.., que no poseo). Es porque el driver entra en modo panoramico, con lo cual y segun el pdf que vienecon el driver hay que agregale al xorg unas lineas. vamoa a la consola:

sudo gedit etc/X11/xorg.conf

Buscamos Section "Device" y antes de EndSection, agregamos: Option "NoDDCValue". Con eso ya tendria que reconocer las resoluciones mas comunes, en caso de que tengas un monitor raro el txt tiene mas.

En este punto ya estaras esperando ver que tenga aceleracion, otra vez a la consola e introducimos glxinfo, buscamos una linea que diga direct rendering y verificamos que diga "yes". Luego puedes ver el framerate con glxgears, esto varia segun el chip.

Listo, placa fea, driver nuevo, aceleracion.., falta algo?.., Compiz!!. Bueno, aca se pone turbio. Dependiendo que placa puede variar.., pero vamos por partes. Instalamos el compiz manager con el bendito y tan nombrado:

apt-get install compizconfig-settings-manager

Vemos si en Sistema>Preferencias>Apariencia aparece una nueva opcion en la solapa "efectos visuales", la seleccionamos y .., puede que si o puede que no se te activen directamente (en mi caso no ¬_¬).

Ahora en caso de que no, yo istale estos paquetes que aparecen en el pdf: compiz-core y compiz. Probamos nuevamente.., nada.., bueno.., a tocar algo mas.

Compiz tiene una whitelist de placas "compatibles", via no lo es.., pero si puedes probar.., probamos (en mi caso no pierdo nada). El pdf recomienda un comando.., que en micaso no funciono y solucione a las mias. El comando en si es:

echo "SKIP_CHECKS=yes" > /root/.config/compiz/compiz-manager

Yo tube que cambiar /root/ por /home/miusuario, con eso funciono y.., pude activar compiz con cubo y todo algooooo, y unos horribles marcos negros alrededor de las ventanas ¬_¬
 
[B][U]
FIN SECCION "CASI" COMO[/U][/B]

DUDA:

Aca la duda.., como se soluciona esto?!!, es lo ultimo, aunque creo que no tiene solucion por el pobre respaldo a open gl por parte de esta placa en particular. Probe con: compiz --replace, compiz --replace --indirect-rendering, instalar Emerald y hacer compiz --replace -c emerald, añadir en el xorg en la seccion "Device" estas lineas:

Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"

pero nada, no se soluciona. Tengo sospechas que se trate de las transparencias, porque pasan 2 cosas. Cuando desactivo el decorador de ventanas, se van los bordes negros (junto a los marcos) y cuando probe el plugin "opacity" al pasar por la ventana en segundo plano, la de adelante (que debe transparentarse), se pone negra, tal cual los bordes.

Bueno, espero que esto le sirva a alquien y si tienen alguna solucion o pueden orientarme, avisen asi termino este COMO definitivamente.

Saludos!!

Aca termina el post original en ubuntu-es, depues siguen un par de opinines de Panko, Milton_Ivan y eld1e6o, a los cuales agradezco. 

Asi que bueno, espero que lo puedan mejorar y llegar a terminar o que discutamos algunas soluciones (se que las hay, pero no las probe)

Adios

---

### Post by frippio on 2008-01-26
Mi experiencia con el nuevo driver fue buena, salvo con los efectos de Compiz, los cuales son bien inestables además que las sombras se ven con marcos negros y la opacidad no funciona. Creo que es un How To completo el que hiciste, ya que estos errores no se solucionan con esta versión del driver. Esperemos que en este año aparezca una nueva versión de estos drivers y que se solucione algunos problemas. Saludos

---

### Post by pol666 on 2008-01-28
A mi los driver de mi nvdia no dieron problemas ;) 

por suerte

el bardo fue con el sonido :KS

---

### Post by anka on 2008-01-28
Pero esto es VIA.., el infierno en silicio!, ojala fueran chips intel ¬¬.

Algun dia los fabricantes se daran cuenta que les es mucho mas conveniente liberar los drivers, no solo porque hara que se puedan implementar en diferentes plataformas y mas eficazmente, sino que simplemente les saldra mas barato.

Por ahora, esto es lo que se tiene.., por ahora ¬_¬!

---

### Post by wazaraki on 2008-02-17
Hola, he seguido los pasos y me ha ido bien con la aceleracion 2D, el problema es que no se me activa el direct rendering.

 Me sale esto:

# glxinfo
name of display: :0.0
libGL error: open DRM failed (Operation not permitted)
libGL error: reverting to (slow) indirect rendering
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
.........
.........

Ya agregue la opcion de "NoDDCValue" pero sigue sin funcionar el direct rendering y, por supuesto, no puedo activar los efectos visuales.

¿Que podrá ser? :confused:

Tengo una S3 Unichrome Pro VGA Adapter de 64mb

Gracias de antemano

---

### Post by faktorqm on 2008-02-18
Bueno Anka, no se como agradecerte todo esto, desde hace casi 1 año y medio que aca en el laburo tengo una VIA del infierno y me pasee por millones de lugares y nunca nada...
Y ahora con el mini tuto que me diste vos mas un par de cosas que toque yo me anda lo mas bien. Sabes que es lo mas gracioso? que mi modelo no esta soportado jajaja
Les cuento lo que hice, yo tengo ubuntu 7.04, y cuando fui a instalar el driver me tiro la bronca de que no tenia la version soportada de kernel. yo tengo la 2.6.20-16-generic y el tipo queria la 2.6.20-15-generic (que es la que viene por defecto en 7.04. Entonces claro, descomprimi el .run y fui hasta el script de instalacion, y le puse el 16 y lo instalo lo mas bien. Ahora que pasa, cuando tiro glxinfo me tira un par de errores de libgl y despues me dice, direct rendering: yes y tooodas las instrucciones opengl que soporta y todo, pero cuando le doy al glxgears me aparece la pantalla negra de la muerte......... asi que no se si es por que lo instale con una version de kernel que no debia, o si me conviene instalar la version para 7.10 y que me lo reconozca bien, no se. por ahora, esta es mi experiencia. Estoy feliz anka, te mereces muchos thanks. salu2!

---

### Post by faktorqm on 2008-02-18
bueno, todo no podia ser bueno, asi que hago aca mi experiencia:

Arranque con el kernel 15, instale los drivers, y me tiraba esto:

```

faktorqm@ttheedge:~$ glxinfo
name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x53
libGL warning: 3D driver claims to not support visual 0x22
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x31
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_swap_control, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_visual_select_group
OpenGL vendor string: VIA Technology
OpenGL renderer string: Mesa DRI UniChrome 20060710 x86/MMX+/3DNow!+/SSE2
OpenGL version string: 1.2 Mesa 6.5.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod

```

o sea, ctrl + c, sino no sale de ahi :( y el glxgears tira esto:

```

faktorqm@ttheedge:~$ glxgears
libGL warning: 3D driver claims to not support visual 0x53
libGL warning: 3D driver claims to not support visual 0x22
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x31
3 frames in 9.2 seconds =  0.326 FPS

```

y me mostraba todo negro y tampoco terminaba hasta ctrl + c, luego desactive el load "dri" en la seccion
modules del xorg.conf y pasaba esto:

```

faktorqm@ttheedge:~$ glxinfo
name of display: :0.0
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  16
  Current serial number in output stream:  17

```

y el glxgears esto:

```

faktorqm@ttheedge:~$ glxgears
Fallo de segmentación (core dumped)
faktorqm@ttheedge:~$ 

```

Asi que esa no era la solucion. Les agrego el log del xorg asi ven el problema:

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux ttheedge 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 18 January 2008
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Feb 18 11:06:02 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "MonitorGeneric Video Card"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,0336 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 1106,1336 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:2: chip 1106,2336 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:3: chip 1106,3336 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:4: chip 1106,4336 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:5: chip 1106,5336 card 0000,0000 rev 00 class 08,00,20 hdr 80
(II) PCI: 00:00:6: chip 1106,6290 card 0008,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:7: chip 1106,7336 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b188 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1106,a238 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:03:0: chip 1106,c238 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:0f:0: chip 1106,0591 card 1043,81b5 rev 80 class 01,01,8f hdr 80
(II) PCI: 00:0f:1: chip 1106,0571 card 1043,81b5 rev 07 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1106,3038 rev a0 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1106,3038 rev a0 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1106,3038 rev a0 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3038 card 1106,3038 rev a0 class 0c,03,00 hdr 80
(II) PCI: 00:10:4: chip 1106,3104 card 1106,3104 rev 86 class 0c,03,20 hdr 80
(II) PCI: 00:11:0: chip 1106,3337 card 1043,81b5 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:7: chip 1106,287e card 1106,337e rev 00 class 06,00,00 hdr 00
(II) PCI: 00:12:0: chip 1106,3065 card 1043,80ed rev 7c class 02,00,00 hdr 00
(II) PCI: 00:13:0: chip 1106,337b card 0000,0000 rev 00 class 06,04,00 hdr 81
(II) PCI: 00:13:1: chip 1106,337a card 0000,0000 rev 00 class 06,04,01 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 1106,3230 card 1043,81b5 rev 01 class 03,00,00 hdr 00
(II) PCI: 04:01:0: chip 1106,3288 card 1043,81e7 rev 10 class 04,03,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000b (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfa000000 - 0xfbefffff (0x1f00000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:2:0), (0,2,2), BCTRL: 0x0003 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:3:0), (0,3,3), BCTRL: 0x0003 (VGA_EN is cleared)
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:19:0), (0,4,4), BCTRL: 0x0003 (VGA_EN is cleared)
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xfbf00000 - 0xfbffffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:19:1), (0,5,5), BCTRL: 0x0003 (VGA_EN is cleared)
(--) PCI:*(1:0:0) unknown vendor (0x1106) unknown chipset (0x3230) rev 1, Mem @ 0xd0000000/28, 0xfa000000/24, BIOS @ 0xfbef0000/16
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf0000000 from 0xf7ffffff to 0xefffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfbffc000 - 0xfbffffff (0x4000) MX[B]
	[1] -1	0	0xf9fff800 - 0xf9fff8ff (0x100) MX[B]
	[2] -1	0	0xf9fffc00 - 0xf9fffcff (0x100) MX[B]
	[3] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[4] -1	0	0xfbef0000 - 0xfbefffff (0x10000) MX[B](B)
	[5] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[6] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[7] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[8] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[9] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[10] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[11] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[12] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[13] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[14] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[17] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfbffc000 - 0xfbffffff (0x4000) MX[B]
	[1] -1	0	0xf9fff800 - 0xf9fff8ff (0x100) MX[B]
	[2] -1	0	0xf9fffc00 - 0xf9fffcff (0x100) MX[B]
	[3] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[4] -1	0	0xfbef0000 - 0xfbefffff (0x10000) MX[B](B)
	[5] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[6] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[7] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[8] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[9] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[10] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[11] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[12] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[13] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[14] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[17] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfbffc000 - 0xfbffffff (0x4000) MX[B]
	[5] -1	0	0xf9fff800 - 0xf9fff8ff (0x100) MX[B]
	[6] -1	0	0xf9fffc00 - 0xf9fffcff (0x100) MX[B]
	[7] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[8] -1	0	0xfbef0000 - 0xfbefffff (0x10000) MX[B](B)
	[9] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[14] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[15] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[16] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[17] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[18] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[19] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[24] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "via"
(II) Loading /usr/lib/xorg/modules/drivers//via_drv.so
(II) Module via: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 4.1.72
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) via: driver for VIA chipsets: CLE266, KM400/KN400, K8M800/K8N800,
	PM800/PM880/CN400, P4M800PRO, CX700, K8M890, P4M890, CN750, P4M900
(II) Primary Device is: PCI 01:00:0
(--) Chipset K8M890 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfbffc000 - 0xfbffffff (0x4000) MX[B]
	[5] -1	0	0xf9fff800 - 0xf9fff8ff (0x100) MX[B]
	[6] -1	0	0xf9fffc00 - 0xf9fffcff (0x100) MX[B]
	[7] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[8] -1	0	0xfbef0000 - 0xfbefffff (0x10000) MX[B](B)
	[9] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[14] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[15] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[16] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[17] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[18] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[19] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[24] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfbffc000 - 0xfbffffff (0x4000) MX[B]
	[5] -1	0	0xf9fff800 - 0xf9fff8ff (0x100) MX[B]
	[6] -1	0	0xf9fffc00 - 0xf9fffcff (0x100) MX[B]
	[7] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[8] -1	0	0xfbef0000 - 0xfbefffff (0x10000) MX[B](B)
	[9] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[17] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[18] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[19] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[20] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[21] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[22] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[23] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[25] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[26] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[27] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[28] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[29] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(**) VIA(0): Depth 24, (--) framebuffer bpp 32
(==) VIA(0): RGB weight 888
(==) VIA(0): Default visual is TrueColor
(**) VIA(0): Option "NoDDCValue"
(II) VIA(0): MergedFB mode forced off.
(==) VIA(0): Not using video BIOS to set modes
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) Loading sub module "vm86"
(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules//libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) VIA(0): Primary V_BIOS segment is: 0xc000
(II) VIA(0): MapBase = b7a99000, MmioBase=fa000000
(II) VIA(0): RegCR08 = 0, RegCR09=4f
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) VIA(0): VESA BIOS detected
(II) VIA(0): VESA VBE Version 3.0
(II) VIA(0): VESA VBE Total Mem: 65536 kB
(II) VIA(0): VESA VBE OEM: VIA K8M890CE

(II) VIA(0): VESA VBE OEM Software Rev: 1.0
(II) VIA(0): VESA VBE OEM Vendor: 
(II) VIA(0): VESA VBE OEM Product: 
(II) VIA(0): VESA VBE OEM Product Rev: 
(--) VIA(0): Chipset: "K8M890"
(--) VIA(0): Chipset Rev.: 0
(**) VIA(0): Option: Not using DDC probed value to set HorizSync & VertRefresh
(--) VIA(0): mapping MMIO @ 0xfa000000 with size 0x9000
(--) VIA(0): mapping BitBlt MMIO @ 0xfa200000 with size 0x200000
(II) VIA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) VIA(0): Using gamma correction (1.0, 1.0, 1.0)
(--) VIA(0): videoram =  65536k
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Reloading /usr/lib/xorg/modules//libi2c.so
(II) VIA(0): I2C bus "I2C bus 1" initialized.
(II) VIA(0): I2C bus "I2C bus 2" initialized.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) VIA(0): VESA VBE DDC supported
(II) VIA(0): VESA VBE DDC Level 2
(II) VIA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VIA(0): VESA VBE DDC read successfully
(II) VIA(0): Manufacturer: GSM  Model: 3b66  Serial#: 16843009
(II) VIA(0): Year: 2005  Week: 1
(II) VIA(0): EDID Version: 1.3
(II) VIA(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) VIA(0): Signal levels configurable
(II) VIA(0): Sync:  Separate
(II) VIA(0): Max H-Image Size [cm]: horiz.: 28  vert.: 21
(II) VIA(0): Gamma: 2.76
(II) VIA(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) VIA(0): First detailed timing is preferred mode
(II) VIA(0): redX: 0.642 redY: 0.330   greenX: 0.273 greenY: 0.605
(II) VIA(0): blueX: 0.142 blueY: 0.063   whiteX: 0.283 whiteY: 0.298
(II) VIA(0): Supported VESA Video Modes:
(II) VIA(0): 720x400@70Hz
(II) VIA(0): 640x480@60Hz
(II) VIA(0): 640x480@67Hz
(II) VIA(0): 640x480@72Hz
(II) VIA(0): 640x480@75Hz
(II) VIA(0): 800x600@56Hz
(II) VIA(0): 800x600@60Hz
(II) VIA(0): 800x600@72Hz
(II) VIA(0): 800x600@75Hz
(II) VIA(0): 832x624@75Hz
(II) VIA(0): 1024x768@60Hz
(II) VIA(0): Manufacturer's mask: 0
(II) VIA(0): Supported Future Video Modes:
(II) VIA(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) VIA(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) VIA(0): Supported additional Video Mode:
(II) VIA(0): clock: 65.0 MHz   Image Size:  270 x 200 mm
(II) VIA(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) VIA(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) VIA(0): Supported additional Video Mode:
(II) VIA(0): clock: 56.2 MHz   Image Size:  270 x 200 mm
(II) VIA(0): h_active: 800  h_sync: 832  h_sync_end 896 h_blank_end 1048 h_border: 0
(II) VIA(0): v_active: 600  v_sync: 601  v_sync_end 604 v_blanking: 631 v_border: 0
(II) VIA(0): Ranges: V min: 50  V max: 120 Hz, H min: 30  H max: 54 kHz, PixClock max 70 MHz
(II) VIA(0): Monitor name: 500G
(II) VIA(0): EDID (in hex):
(II) VIA(0): 	00ffffffffffff001e6d663b01010101
(II) VIA(0): 	010f0103781c15b0ea6059a454469b24
(II) VIA(0): 	10484cbfe80031594559010101010101
(II) VIA(0): 	01010101010164190040410026301888
(II) VIA(0): 	36000ec810000018f91520f830581f20
(II) VIA(0): 	204013000ec81000001e000000fd0032
(II) VIA(0): 	781e3607000a202020202020000000fc
(II) VIA(0): 	00353030470a20202020202020200011
(II) VIA(0): Using hsync ranges from config file
(II) VIA(0): Using vrefresh ranges from config file
(II) VIA(0): Printing DDC gathered Modelines:
(II) VIA(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) VIA(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) VIA(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) VIA(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) VIA(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) VIA(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) VIA(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) VIA(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) VIA(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) VIA(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) VIA(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) VIA(0): Modeline "640x480"   35.00  640 664 728 816  480 483 487 507 -hsync +vsync
(II) VIA(0): Modeline "800x600"   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync
(II) VIA(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) VIA(0): Modeline "800x600"   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync
(--) VIA(0): Max Monitor H =  800
(--) VIA(0): Max Monitor V =  600
(II) VIA(0): MonitorGeneric Video Card: Using hsync range of 30.00-113.00 kHz
(II) VIA(0): MonitorGeneric Video Card: Using vrefresh range of 43.00-60.00 Hz
(II) VIA(0): Clock range:  20.00 to 270.00 MHz
(II) VIA(0): Not using default mode "640x350" (vertical timing out of range)
(II) VIA(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "640x400" (vertical timing out of range)
(II) VIA(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "720x400" (vertical timing out of range)
(II) VIA(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) VIA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) VIA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) VIA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1024x768" (vertical timing out of range)
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1152x864" (vrefresh out of range)
(II) VIA(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1280x960" (mode clock too high)
(II) VIA(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1280x960" (vrefresh out of range)
(II) VIA(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1280x1024" (mode clock too high)
(II) VIA(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) VIA(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) VIA(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1600x1200" (mode clock too high)
(II) VIA(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) VIA(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) VIA(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) VIA(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) VIA(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1792x1344" (mode clock too high)
(II) VIA(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) VIA(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1856x1392" (mode clock too high)
(II) VIA(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1920x1440" (mode clock too high)
(II) VIA(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "832x624" (horizontal timing out of range)
(II) VIA(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1280x768" (mode clock too high)
(II) VIA(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1280x800" (mode clock too high)
(II) VIA(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1152x768" (vertical timing out of range)
(II) VIA(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1152x864" (vrefresh out of range)
(II) VIA(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1400x1050" (mode clock too high)
(II) VIA(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) VIA(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) VIA(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) VIA(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1440x900" (mode clock too high)
(II) VIA(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1600x1024" (mode clock too high)
(II) VIA(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1680x1050" (mode clock too high)
(II) VIA(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1920x1200" (mode clock too high)
(II) VIA(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1920x1200" (vrefresh out of range)
(II) VIA(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "2048x1536" (mode clock too high)
(II) VIA(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using driver mode "640x480" (vrefresh out of range)
(II) VIA(0): Not using driver mode "640x480" (vrefresh out of range)
(II) VIA(0): Not using driver mode "640x480" (vrefresh out of range)
(II) VIA(0): Not using driver mode "720x400" (vertical timing out of range)
(II) VIA(0): Not using driver mode "832x624" (horizontal timing out of range)
(II) VIA(0): Not using driver mode "800x600" (vrefresh out of range)
(II) VIA(0): Not using driver mode "800x600" (vrefresh out of range)
(II) VIA(0): Not using driver mode "640x480" (vrefresh out of range)
(II) VIA(0): Not using driver mode "800x600" (vrefresh out of range)
(II) VIA(0): Not using driver mode "800x600" (vrefresh out of range)
(--) VIA(0): Virtual size is 1024x768 (pitch 1024)
(**) VIA(0): *Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) VIA(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) VIA(0):  Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) VIA(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) VIA(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) VIA(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) VIA(0):  Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) VIA(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) VIA(0):  Driver mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) VIA(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) VIA(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) VIA(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) VIA(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) VIA(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) VIA(0):  Driver mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) VIA(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) VIA(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) VIA(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
(**) VIA(0): Display dimensions: (280, 210) mm
(**) VIA(0): DPI set to (92, 92)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(**) VIA(0): Option: Cap0 auto detect= 0
(**) VIA(0): Option: Cap1 auto detect= 0
(**) VIA(0): Option: Cap0_FieldSwap Disabled
(**) VIA(0): Option: Cap0_HFilter Enabled
(**) VIA(0): Option: Cap1_HFilter Enabled
(**) VIA(0): Option: Capture Over Scan ON
(**) VIA(0): Option: HQV Filter Manual Select Disabled
(**) VIA(0): Option: Set MPEG decode frame buffer number Disable
(**) VIA(0): Option: Capture 1 use H/W auto flip
(**) VIA(0): Option: Capture 0 use V1 engine : Default path
(**) VIA(0): Option: HQV Manual Switch Disabled
(**) VIA(0): Option: No mpeg add one line on bottom = 0
(**) VIA(0): Option: DeBlocking Disable!!
(**) VIA(0): DeBlocking Minimum Width Default : 320
(**) VIA(0): DeBlocking Minimum Height Default: 240
(**) VIA(0): Option: Use 2D BitBlt method to write event-tag into VQ and make sure MPEG decode END Disable
(II) VIALoadVideoOption
(WW) No Video option file .VIAVIDEORC exist. 
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfa000000 - 0xfaffffff (0x1000000) MS[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MS[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfbffc000 - 0xfbffffff (0x4000) MX[B]
	[7] -1	0	0xf9fff800 - 0xf9fff8ff (0x100) MX[B]
	[8] -1	0	0xf9fffc00 - 0xf9fffcff (0x100) MX[B]
	[9] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[10] -1	0	0xfbef0000 - 0xfbefffff (0x10000) MX[B](B)
	[11] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[19] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[20] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[21] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[22] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[23] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[24] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[25] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[26] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[27] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[28] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[29] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[30] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[31] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(--) VIA(0): mapping framebuffer @ 0xd0000000 with size 0x4000000
(==) VIA(0): Write-combining range (0xd0000000,0x4000000)
(--) VIA(0): Frame buffer start: 0xb37fa000, free start: 0x300000 end: 0x4000000
(--) VIA(0): mapping MMIO @ 0xfa000000 with size 0x9000
(--) VIA(0): mapping BitBlt MMIO @ 0xfa200000 with size 0x200000
(II) VIA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) VIA(0): VIAScreenInit : V4L Enabled : fd2 = 9 
(II) VIA(0): I2C device "I2C bus 2:TV" registered at address 0x40.
(II) VIA(0): I2C device "I2C bus 2:TV" removed.
(II) VIA(0): I2C device "I2C bus 2:TV" registered at address 0x40.
(II) VIA(0): I2C device "I2C bus 2:TV" removed.
(II) VIA(0): I2C device "I2C bus 2:TV" registered at address 0x40.
(II) VIA(0): I2C device "I2C bus 2:TV" removed.
(II) VIA(0): 3D Engine has been initilized.
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) VIA(0): [drm] DRM interface version 1.2
(II) VIA(0): [drm] created "via" driver at busid "PCI:1:0:0"
(II) VIA(0): [drm] added 8192 byte SAREA at 0xe0d67000
(II) VIA(0): [drm] mapped SAREA 0xe0d67000 to 0xb37f8000
(II) VIA(0): [drm] framebuffer handle = 0xd0000000
(II) VIA(0): [drm] added 1 reserved context for kernel
(II) VIA(0): [drm] drmAgpEnabled succeeded
(II) VIA(0): [drm] agpAddr = 0xf0000000
(II) VIA(0): [drm] agpBase = 0x00000000
(II) VIA(0): [drm] agpAddr = 0xf0000000
(II) VIA(0): [drm] agpSize = 0x02000000
(II) VIA(0): [drm] agp physical addr = 0x00000000
(II) VIA(0): [dri] use agp.
(II) VIA(0): [dri] frame buffer initialized.
(II) VIA(0): [dri] visual configs initialized.
(II) VIA(0): [drm] register handle = 0xfa000000
(II) VIA(0): [drm] mmio Registers = 0xfa000000
(II) VIA(0): [dri] mmio maped.
(II) VIA(0): VIAInternalScreenInit
(II) VIA(0): Frame Buffer From (0,0) To (1024,1280)
(II) VIA(0): Using 1280 lines for offscreen memory.
(II) VIA(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	8x8 color pattern filled rectangles
	CPU to Screen color expansion
	Solid Lines
	Dashed Lines
	Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		15 128x128 slots
		4 256x256 slots
		32 8x8 color pattern slots
(II) VIA(0): [drm] FBFreeStart= 0x00500000 FBFreeEnd= 0x03fba000 FBSize= 0x03aba000
(==) VIA(0): Backing store disabled
(==) VIA(0): Silken mouse enabled
(**) Option "dpms"
(**) VIA(0): DPMS enabled
(II) VIA(0): X context handle = 0x1
(II) VIA(0): [drm] installed DRM signal handler
(II) VIA(0): [DRI] installation complete
(II) VIA(0): [dri] kernel data initilized.
(II) VIA(0): [drm] Initialized AGP ring-buffer, size 0x1000000 at AGP offset 0x0.
(II) VIA(0): direct rendering enabled
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(WW) AIGLX: 3D driver claims to not support visual 0x22
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(II) AIGLX: Loaded and initialized /usr/lib/dri/via_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "es"
(**) Generic Keyboard: XkbLayout: "es"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!

```

Estado de desarrollo del driver openchrome:

[http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=HardwareCaveats](http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=HardwareCaveats)

La mia (k8m890) dice que todavia no soporta aceleracion 3d pero si 2d. no tiene un monton de cosas, pero como videos aca en el laburo no veo, no me calienta. El error por lo que lei es incompatibilidad con el xorg, o sea, es un tema de compilacion y demas yerbas, pero bueno, habra que ver bien como es la onda. 

En un foro vi que habia que tener instalados los siguientes paquetes para el driver unichrome:

```
sudo apt-get install x11proto-gl-dev libgl1-mesa-dev x11proto-fonts-dev x11proto-randr-dev x11proto-render-dev x11proto-xf86dri-dev libdrm-dev
```

Los instalé, pero no paso nada. Ahora voy a ver lo que esta en

[http://ubuntuforums.org/showthread.php?t=485646&highlight=K8M890&page=19](http://ubuntuforums.org/showthread.php?t=485646&highlight=K8M890&page=19)

que hay un flaco que tiene el k8m890 y dice que le anda pero no para el compiz.....
Salu2 muchachos!!:)

---

### Post by shinta_87 on 2009-09-09
una pregunta como descargo el drivers yo tengo este modelo VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] y tampoco he podido activar compiz...alguna idea?........

---

### Post by guillermolisi on 2009-09-09
> **shinta_87 said:**
> una pregunta como descargo el drivers yo tengo este modelo VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] y tampoco he podido activar compiz...alguna idea?........
Las placas de video basadas en chipset VIA, como la que mencionas, no funcionan en Linux con aceleracion grafica y ha habido muy pero muy pocos casos en que la aceleracion 2d fuese aceptable. La mayoria terminaba o usando driver VESA o colocando una ATI/nVidia en su reemplazo.

Los drivers que estan en el site VIA Arena no sirven.

---

### Post by shinta_87 on 2009-09-10
> **guillermolisi said:**
> Las placas de video basadas en chipset VIA, como la que mencionas, no funcionan en Linux con aceleracion grafica y ha habido muy pero muy pocos casos en que la aceleracion 2d fuese aceptable. La mayoria terminaba o usando driver VESA o colocando una ATI/nVidia en su reemplazo.

Los drivers que estan en el site VIA Arena no sirven.

pero colocando el drivers vesa puedo usar compiz? y como lo puedo hacer?........

---

### Post by guillermolisi on 2009-09-10
> **shinta_87 said:**
> pero colocando el drivers vesa puedo usar compiz? y como lo puedo hacer?........
Al momento de escribir esto no conozco un solo caso de exito que haya logrado aceleracion 3D con chips VIA y drivers Unichrome o similares.

Y, como te estaras imaginando, sin aceleracion 3D no hay Compiz.

Fijate que el ultimo post anterior al tuyo data de Febrero del 2008 y el tema aun sigue pendiente por parte de VIA porque no quieren abrir su tecnologia ni desarrollar drivers que funcionen bien en Linux.

Uso dos maquinas con chip VIA para video y en ambas termine instalando placas nVidia.

---

### Post by nopersona on 2009-09-10
Jojojo, una VIA. Por ahí tengo un tarrito con una placa MSI y con este tristemente celebre chip. Ojalá que funcione, aunque en el mismo soporte de VIA explican que a lo sumo se le puede sacar un 2d en linux, creo que lo conseguí en feisty, ya ni recuerdo. En el antiguo foro Chileno hay mucha información útil al respecto, a ver si desempolvo algunos links.

Suerte!

---

### Post by shinta_87 on 2009-09-11
> **guillermolisi said:**
> Al momento de escribir esto no conozco un solo caso de exito que haya logrado aceleracion 3D con chips VIA y drivers Unichrome o similares.

Y, como te estaras imaginando, sin aceleracion 3D no hay Compiz.

Fijate que el ultimo post anterior al tuyo data de Febrero del 2008 y el tema aun sigue pendiente por parte de VIA porque no quieren abrir su tecnologia ni desarrollar drivers que funcionen bien en Linux.

Uso dos maquinas con chip VIA para video y en ambas termine instalando placas nVidia.

ya soy el segundo que conosco que logra compiz en ubuntu en esta tarjeta fue mamon pero al final lo logre lo consegui aqui [http://ubuntuforum-br.org/index.php/topic,40174.0.html](http://ubuntuforum-br.org/index.php/topic,40174.0.html) y hasta muestran un video y si funciona a mi me funciono......

---

