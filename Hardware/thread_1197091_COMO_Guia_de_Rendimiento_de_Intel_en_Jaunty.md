---
title: "COMO: Guia de Rendimiento de Intel en Jaunty"
date: 2009-06-25
forum: Hardware
---

### Post by pablo.s on 2009-06-25
[SIZE=3]**[B][FONT=Droid Serif, serif]COMO: Guia de Rendimiento de Tarjetas de Video Intel en Ubuntu Jaunty[/FONT]**[/B][/SIZE]
 **[FONT=Droid Serif, serif]Autor: [psyke83]("http://ubuntuforums.org/member.php?u=50843") [/FONT]** 
 

 [COLOR=Red]**[FONT=Droid Serif, serif]Advertencia : Aunque me he esforzado para hacer esta guia lo más[/FONT]**[/COLOR]
 [COLOR=Red]**[FONT=Droid Serif, serif]accesible como me fué posible, debo aclarar que si usted es un principiante[/FONT]**[/COLOR]
 [COLOR=Red]**[FONT=Droid Serif, serif]en Ubuntu entonces se le recomienda no seguir esta guia  bajo ninguna[/FONT]**[/COLOR]
 [COLOR=Red]**[FONT=Droid Serif, serif]condición. Incluso si usted se guia por el método mas seguro explicado, su[/FONT]**[/COLOR]
 [COLOR=Red]**[FONT=Droid Serif, serif]sistema puede experimentar dificultades debido a la instalación de drivers[/FONT]**[/COLOR]
 [COLOR=Red]**[FONT=Droid Serif, serif]no oficiales. Considerese debidamente advertido! [/FONT]**[/COLOR] 
 

 [SIZE=3]**[FONT=Droid Serif, serif]Introducción[/FONT]**[/SIZE]
 **[FONT=Droid Serif, serif]Algunos usuarios están teniendo problemas de rendimiento con los chips[/FONT]**
 **[FONT=Droid Serif, serif]de las tarjetas de video integradas Intel con Ubuntu Jaunty Jackalope (9.04)[/FONT]**
 **[FONT=Droid Serif, serif]debido a las siguientes causas:[/FONT]**
 

 
[LIST=1]
[*]**[FONT=Droid Serif, serif]El     driver actual en nuestro repositorio tiene algunos problemas de[/FONT]**
     **[FONT=Droid Serif, serif]rendimiento     con el método de aceleración EXA. Los usuarios tendrán un[/FONT]**
     **[FONT=Droid Serif, serif]rendimiento     2D muy pobre debido a la &#8220;heuristica de migración&#8221; empleada[/FONT]**
     **[FONT=Droid Serif, serif]por     EXA (a &#8220;siempre&#8221; migrar pixmaps) pero esto provoca problemas de[/FONT]**
     **[FONT=Droid Serif, serif]rendimiento     a muchos usuarios. Configurar la heuristica a &#8220;greedy&#8221; de[/FONT]**
     **[FONT=Droid Serif, serif]alguna     manera logra solventar el problema. Consulte &#8220;man exa&#8221;[/FONT]**
[/LIST]
 
[LIST=1]
[*]**[FONT=Droid Serif, serif]El     método más nuevo y rápido (UXA) no está habilitado por defecto,[/FONT]**
     **[FONT=Droid Serif, serif]debido     a problemas reportados por muchos usuarios. Este código[/FONT]**
     **[FONT=Droid Serif, serif]está     siendo activamente desarrollado, y muchos problemas de[/FONT]**
     **[FONT=Droid Serif, serif]estabilidad     y rendimento han sido resueltos en los últimos drivers [/FONT]**     
     **[FONT=Droid Serif, serif](especificamente     entre el driver Intel, libdrm, mesa y el último núcleo[/FONT]**
     **[FONT=Droid Serif, serif]2.6.29.4).     Desafortunadamente, Jaunty no incluirá las últimas versiones[/FONT]**
     **[FONT=Droid Serif, serif]necesarias     para mejorar el rendimiento.[/FONT]**
[*]**[FONT=Droid Serif, serif]El     rendimento 3D ha tenido una regresión respecto a Intrepid, debido[/FONT]**
     **[FONT=Droid Serif, serif]posiblemente     a grandes cambios del código que son producto de la[/FONT]**
     **[FONT=Droid Serif, serif]introducción     del nuevo código de aceleración y gestión de memoria[/FONT]**
     **[FONT=Droid Serif, serif](UXA,     GEM, DRI2). Por estos cambios, parece haber ciertas regresiones[/FONT]**
     **[FONT=Droid Serif, serif]en     la aceleración DRI clásica.[/FONT]**
[*]**[FONT=Droid Serif, serif]Tanto     Xorg o el diver Intel parecen estar teniendo un bug en el cuál[/FONT]**
     **[FONT=Droid Serif, serif]la     región de memoria reservada (MTRR) para la tarjeta de video no está[/FONT]**
     **[FONT=Droid Serif, serif]preparada     con el tipo correcto de cacheado. Esto resulta en la[/FONT]**
     **[FONT=Droid Serif, serif]reproducción     de video abrupta de cualquier medio (partiendo desde los[/FONT]**
     **[FONT=Droid Serif, serif]videos     en 720p, hasta simple contenido mpeg de 320 x 240) y una[/FONT]**
     **[FONT=Droid Serif, serif]potencial     pérdida de rendimiento para otras operaciones de 2D y 3D.[/FONT]**
[/LIST]
 

 **[FONT=Droid Serif, serif]Hay tres posibles configuraciones que esta guia presenta:[/FONT]**
 

 [SIZE=3]**[FONT=Droid Serif, serif]Configuración Segura[/FONT]**[/SIZE]
 
[LIST]
[*]
[LIST]
[*]**[FONT=Droid Serif, serif]Para         esta configuración, usted actualizará a los drivers de Xorg más[/FONT]**
         **[FONT=Droid Serif, serif]actuales         y estables (por medio del [PPA X-Updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/")), habilitará la[/FONT]**
         **[FONT=Droid Serif, serif]aceleración         UXA y creará una solución para el bug MTRR. Esta es la[/FONT]**
         **[FONT=Droid Serif, serif]solución         recomendada a los usuarios que poseen dispositivos de[/FONT]**
         **[FONT=Droid Serif, serif]hardware         que dependen de un driver restringido. Si usted no sabe[/FONT]**
         **[FONT=Droid Serif, serif]lo         que esto significa, entonces es la solución que debería usar.[/FONT]**
[/LIST]
 
[/LIST]
 

 [SIZE=3]**[FONT=Droid Serif, serif]Configuración Optima[/FONT]**[/SIZE]
 
[LIST]
[*]
[LIST]
[*]**[FONT=Droid Serif, serif]Esta         configuración es identica a la &#8220;segura&#8221;, pero incluye al         núcleo[/FONT]**
         **[FONT=Droid Serif, serif][2.6.30]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30/").         Utilizar este núcleo mejorará el rendimiento 3D a muchos[/FONT]**
         **[FONT=Droid Serif, serif]usuarios,         pero usted perderá acceso a los drivers restringidos del[/FONT]**
         **[FONT=Droid Serif, serif]núcleo.         Esta configuración brinda los mejores resultados a mi[/FONT]**
         **[FONT=Droid Serif, serif]sistema         (con un chipset 855GM), pero desde luego, puede que su[/FONT]**
         **[FONT=Droid Serif, serif]propia         experiencia sea diferente.[/FONT]**
[/LIST]
 
[/LIST]
 [SIZE=3]**[FONT=Droid Serif, serif]Configuración Máxima[/FONT]**[/SIZE]
 
[LIST]
[*]
[LIST]
[*]**[FONT=Droid Serif, serif]Esta         configuración es la más riesgosa. Usted habilitará un         repositorio[/FONT]**
         **[FONT=Droid Serif, serif]que         contiene los drivers Xorg y mesa más recientes que hayan sido[/FONT]**
         **[FONT=Droid Serif, serif]actualizados         al dia (por medio del [PPA xorg-edgers]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")), habilitará la[/FONT]**
         **[FONT=Droid Serif, serif]aceleración         UXA,  creará una solución para el bug MTRR e instalará[/FONT]**
         **[FONT=Droid Serif, serif]el         núcleo 2.6.30. Esta configuración no es obligatoriamente la más[/FONT]**
         **[FONT=Droid Serif, serif]rápida         (a decir verdad la configuración Optima es la más rápida para[/FONT]**
         **[FONT=Droid Serif, serif]mi         placa) y solamente se recomienda para usuarios que quieran[/FONT]**
         **[FONT=Droid Serif, serif]probar         el código Xorg más reciente.[/FONT]**
         **[FONT=Droid Serif, serif]NOTA:         Por voluntad del mantenedor del PPA, se solicita que lea las[/FONT]**
         **[FONT=Droid Serif, serif]instrucciones [        aqui,]("https://launchpad.net/%7Exorg-edgers/+archive/ppa") debido a que este repositorio se suele averiar y[/FONT]**
         **[FONT=Droid Serif, serif]por         esa razón intrucciones importantes pueden ser añadidas. No[/FONT]**
         **[FONT=Droid Serif, serif]solicite         soporte para estos paquetes (y no se sorprenda que preguntas[/FONT]**
         **[FONT=Droid Serif, serif]que         haga queden sin responder) [/FONT]**
[/LIST]
 
[/LIST]
 

 [COLOR=Red]**[FONT=Droid Serif, serif][B]Precauciones y Consejos**[/FONT][/B]**[FONT=Droid Serif, serif]: El utilizar un núcleo de terceras partes significa que[/FONT]**[/COLOR]
 [COLOR=Red]**[FONT=Droid Serif, serif]usted no tendrá acceso a drivers restringidos como por ejemplo FGLRX, Nvidia,[/FONT]**[/COLOR]
 [COLOR=Red]**[FONT=Droid Serif, serif]algunos de tarjetas inalambricas Broadcom, algunas webcams y un puñado de[/FONT]**[/COLOR]
 [COLOR=Red]**[FONT=Droid Serif, serif]tarjetas de sonido nuevas que precisan firmware restringido para funcionar.[/FONT]**[/COLOR]
 [COLOR=Red]**[FONT=Droid Serif, serif]Si usted cree que tiene hardware de estas caracteristicas en su máquina, debería[/FONT]**[/COLOR]
 [COLOR=Red]**[FONT=Droid Serif, serif]seguir utilizando el núcleo oficial de Jaunty. En otras palabras, proceda con la[/FONT]**[/COLOR]
 [COLOR=Red]**[FONT=Droid Serif, serif]configuración Segura.[/FONT]**[/COLOR]
  [COLOR=Red][B][FONT=Droid Serif, serif]                No pase de la configuración Segura/Optima a la Máxima a menos que haya 
[/FONT][/B][/COLOR][COLOR=Red]**[FONT=Droid Serif, serif]seguido los pasos para revertir los cambios luego.[/FONT]**[/COLOR]
 [COLOR=Red]**[FONT=Droid Serif, serif]Por ejemplo, si prueba la configuración Máxima y acto seguido decide probar[/FONT]**[/COLOR]
 [COLOR=Red]**[FONT=Droid Serif, serif]la configuración Optima, seguirá utilizando los drivers de la Máxima (porque[/FONT]**[/COLOR]
 [COLOR=Red]**[FONT=Droid Serif, serif]el PPA xorg-edgers contiene drivers más recientes que el PPA X-Updates, los[/FONT]**[/COLOR]
 [COLOR=Red]**[FONT=Droid Serif, serif]cuales no son automaticamente desactualizados)[/FONT]**[/COLOR]
 

 **[FONT=Droid Serif, serif]Una vez que se haya decidido en la configuración que le conviene, puede[/FONT]**
 **[FONT=Droid Serif, serif]comenzar con la Parte A:[/FONT]**
 

 

 [SIZE=3]**[FONT=Droid Serif, serif][B]PARTE A &#8211; Instrucciones Compartidas (Segura/Optima/Máxima)**[/FONT][/B][/SIZE]
 **[FONT=Droid Serif, serif]Todos los usuarios deben leer esta parte. [/FONT]** 
 

 **[FONT=Droid Serif, serif]1.Edite     su archivo xorg.conf[/FONT]**[COLOR=Red][B][FONT=Droid Serif, serif] 
[/FONT][/B][/COLOR][COLOR=Red]**[FONT=Droid Serif, serif]$ gksudo gedit /etc/X11/xorg.conf[/FONT]**[/COLOR] [B][FONT=Droid Serif, serif]

E[/FONT][/B]**[FONT=Droid Serif, serif]ncuentre la sección &#8220;Device&#8221; y asegurese que es identica a la sección[/FONT]**
**[FONT=Droid Serif, serif]que aparece aqui (Importante: Borre o comente cualquiera de sus[/FONT]**
  **[FONT=Droid Serif, serif]ajustes propios que haya previamente escrito)[/FONT]**
 

 ```
Section "Device"
        Identifier      "Configured Video Device"
        Option          "AccelMethod"                   "uxa"
        Option          "EXAOptimizeMigration"          "true"
        Option          "MigrationHeuristic"            "greedy"
        Option          "Tiling"                        "true" [FONT=Arial]**# usuarios de chipsets 8xx: ver  la nota en la guia**EndSection[/FONT]  
``` **[FONT=Droid Serif, serif]NOTA: Si tiene un chipset 8xx, &#8220;Tiling&#8221; puede causar cierta inestabilidad[/FONT]**
 **[FONT=Droid Serif, serif]a menos que utilice la configuración Máxima. Entonces: si está utlizando[/FONT]**
 **[FONT=Droid Serif, serif]las configuraciones Segura/Optima, ponga &#8220;Tiling&#8221; en False, pero si usa[/FONT]**
 **[FONT=Droid Serif, serif]la Máxima, pongalo en True. [/FONT]** 
 

 **[FONT=Droid Serif, serif]2. Descargue     el script de [Bartec]("https://bugs.launchpad.net/%7Etschew") para [arreglar mtrr.sh]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/314928/comments/38") y otorguele permisos[/FONT]**
     **[FONT=Droid Serif, serif]de     ejecución:[/FONT]**
 [COLOR=Red]$ sudo wget [http://launchpadlibrarian.net/26193373/fixmtrr.sh](http://launchpadlibrarian.net/26193373/fixmtrr.sh) -O /usr/local/bin/fixmtrr.sh[/COLOR][COLOR=Red][B][FONT=Droid Serif, serif]
$ sudo chmod +x /usr/local/bin/fixmtrr.sh[/FONT][/B][/COLOR] 

 **[FONT=Droid Serif, serif]3. Cree     un link simbolico para asegurarse que el script se ejecuta cada vez[/FONT]**
     **[FONT=Droid Serif, serif]que     entra a la sesión por GDM[/FONT]**
     [COLOR=Red]**[FONT=Droid Serif, serif]$ sudo ln -s /usr/local/bin/fixmtrr.sh /etc/gdm/PostLogin/Default[/FONT]**[/COLOR]
 [FONT=Droid Serif, serif][SIZE=1]
Nota: Esto solamente funciona si usted utiliza GDM. Usuarios de KDE y otros[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]tienen que ejecutar 
este script de forma manual. [/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]Vea la sección Nota Importante.[/SIZE][/FONT]  [FONT=Droid Serif, serif][SIZE=1]
4. Si ha decidido por la configuración Segura/Optima, siga a la parte B. 
[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]Si ha decidido por la Máxima, pase a la parte D.[/SIZE][/FONT]  

[FONT=Droid Serif, serif][SIZE=3]**PARTE B &#8211; (Segura/Optima)**[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]
Los usuarios que sigan las configuraciones Segura u Optima deben[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]seguir leyendo esta parte.[/SIZE][/FONT]  [FONT=Droid Serif, serif][SIZE=1]

1. Añada el PPA de X Updates a su archivo sources.list[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]
Edite (con nano, gedit, vi o emacs) su /etc/apt/sources.list[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1][COLOR=Red]
$ gksudo gedit /etc/apt/sources.list[/COLOR][/SIZE][/FONT]  [FONT=Arial][SIZE=1][B]
Añada estas entradas al final del archivo:[/B][/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]
deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main #X-Updates PPA[/SIZE][/FONT] [FONT=Arial][SIZE=1][B]
deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main #X-Updates PPA[/B][/SIZE][/FONT] 

[FONT=Droid Serif, serif][SIZE=1]2. Importe la clave pública del PPA de X Updates, actualice sus fuentes[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]APT y 
proceda a actualizar:[/SIZE][/FONT] 
[COLOR=Red]$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9 
$ sudo apt-get update [/COLOR][FONT=Arial][SIZE=1][COLOR=Red]
$ sudo apt-get dist-upgrade[/COLOR][/SIZE][/FONT]  [FONT=Droid Serif, serif][SIZE=1]
NOTA: Si le pregunta por borrar paquetes, cancele inmediatamente el proceso.[/SIZE][/FONT] 
[FONT=Droid Serif, serif][SIZE=1]El comportamiento que se espera es solo actualizar paquetes, no el borrarlos.[/SIZE][/FONT]  [FONT=Droid Serif, serif][SIZE=1]

3. Si deseaba utilizar la configuración Segura, ya está listo. Proceda a la[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]sección Nota Importante. 
Si desea la configuración Optima, prosiga hacia[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]la Parte C.[/SIZE][/FONT]  [FONT=Droid Serif, serif][SIZE=3][B]

PARTE C (Optima/Máxima)[/B][/SIZE][/FONT] 
[FONT=Droid Serif, serif][SIZE=1]Los usuarios que desean las configuraciones Optima o Máxima[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]deben seguir por esta parte.[/SIZE][/FONT]  [FONT=Droid Serif, serif][SIZE=1]

1. Descargue e instale el núcleo 2.6.30 que sea coherente con la[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]arquitectura 
del procesador de su máquina.[/SIZE][/FONT]  [FONT=Droid Serif, serif][SIZE=1]

Usuarios de i386:[/SIZE][/FONT] 
[COLOR=Red]$ wget -c [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb") [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630_2.6.30-020630_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630_2.6.30-020630_all.deb") [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30/linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb")[/COLOR] [FONT=Droid Serif, serif][SIZE=1][COLOR=Red]
$ sudo dpkg -i linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb linux-headers-2.6.30-020630_2.6.30-020630_all.deb linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb[/COLOR][/SIZE][/FONT]  [FONT=Droid Serif, serif][SIZE=1]

Usuarios de AMD64[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1][COLOR=Red]$ wget -c [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630-generic_2.6.30-020630_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630-generic_2.6.30-020630_amd64.deb") [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630_2.6.30-020630_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630_2.6.30-020630_all.deb") [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-image-2.6.30-020630-generic_2.6.30-020630_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30/linux-image-2.6.30-020630-generic_2.6.30-020630_amd64.deb")[/COLOR][/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1][COLOR=Red]
$ sudo dpkg -i linux-headers-2.6.30-020630-generic_2.6.30-020630_amd64.deb linux-headers-2.6.30-020630_2.6.30-020630_all.deb linux-image-2.6.30-020630-generic_2.6.30-020630_amd64.deb[/COLOR][/SIZE][/FONT]  [FONT=Droid Serif, serif][SIZE=1]

3. Si quería la configuración Optima, ya está listo. No obstante, antes de[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]reininciar al nuevo núcleo, 
lea la sección Nota Importante.[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]Usuarios de configuración Máxima, sigan a la parte D.[/SIZE][/FONT]   [B][FONT=Droid Serif, serif][SIZE=3]

PARTE D (Máxima)[/SIZE][/FONT][/B] 
[FONT=Droid Serif, serif][SIZE=1]Los usuarios que desean la configuración Máxima deben[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]seguir por esta parte.[/SIZE][/FONT]  [FONT=Droid Serif, serif][SIZE=1]
1. Añada el PPA de xorg-edgers a su archivo sources.list[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]
Edite (con nano, gedit, vi o emacs) su /etc/apt/sources.list[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1][COLOR=Red]
$ gksudo gedit /etc/apt/sources.list[/COLOR][/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]
Añada el siguiente texto al final de su archivo, luego salve[/SIZE][/FONT][FONT=Droid Serif, serif][SIZE=1] y cierre.[/SIZE][/FONT] 
deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) jaunty main #xorg-edgers PPA [FONT=Droid Serif, serif][SIZE=1][COLOR=Red]
deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) jaunty main #xorg-edgers PPA[/COLOR][/SIZE][/FONT]  [FONT=Droid Serif, serif][SIZE=1]

Importe la clave pública del PPA de xorg-edgers, actualice sus fuentes[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]APT y 
realice una actualización:[/SIZE][/FONT] 
$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 8844C542 
$ sudo apt-get update 
[FONT=Droid Serif, serif][SIZE=1][COLOR=Red]$ sudo apt-get dist-upgrade[/COLOR][/SIZE][/FONT] 

[FONT=Droid Serif, serif][SIZE=1]NOTA: Si le pregunta por borrar paquetes, cancele inmediatamente el proceso.[/SIZE][/FONT] 
[FONT=Droid Serif, serif][SIZE=1]El comportamiento que se espera es solo actualizar paquetes, no el borrarlos.[/SIZE][/FONT]  [FONT=Droid Serif, serif][SIZE=1]
2. Ya terminó. No obstante, antes de reininciar al nuevo núcleo, [/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]lea la sección 
Nota Importante.[/SIZE][/FONT]   [FONT=Droid Serif, serif][SIZE=3][B]

NOTAS IMPORTANTES (Segura/Optima/Máxima)[/B][/SIZE][/FONT]  [FONT=Droid Serif, serif][SIZE=3][B]

Reporte de Bugs[/B][/SIZE][/FONT]  [B]
[FONT=Droid Serif, serif][SIZE=1]Si eligió la configuración Segura u Optima, estará utilizando los drivers[/SIZE][/FONT][FONT=Droid Serif, serif][SIZE=1]estables 
(aunque no oficiales) de X-Updates. Según la descripción del[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]repositorio:[/SIZE][/FONT][FONT=Droid Serif, serif][SIZE=1]    
&#8220;Aunque Ubuntu-X no soporta de manera oficial estos paquetes,[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]si usted descubre 
problemas mientras instala estos debs sientase libre[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]de reportar bugs a Launchpad. 
No obstante, asegurese de declarar que[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]está ejecutando paquetes de este PPA así nos
enteramos de los arreglos[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]que nos hacen falta.&#8221;[/SIZE][/FONT][FONT=Droid Serif, serif][SIZE=1]

Asimismo, si está utlizando la configuración Segura/Optima también[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]puede reportar 
bugs a Launchpad, mientras siga los lineamientos.[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]También le recomiendo que pruebe 
con el núcleo oficial de Ubuntu, o[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]por lo menos que declare en su reporte de bug que 
está utilizando el[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]núcleo no-oficial mainline.[/SIZE][/FONT][FONT=Droid Serif, serif][SIZE=3]

Utilizando el script de arreglo mtrr.sh[/SIZE][/FONT][FONT=Droid Serif, serif][SIZE=1]
El propósito del script de arreglo mtrr.sh es solucionar un bug en el[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]driver Intel y/o en el 
núcleo y además asegurarse que la región de [/SIZE][/FONT][FONT=Droid Serif, serif][SIZE=1]memoria de su tarjeta gráfica esté ajustada 
al al tipo correcto de[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]cacheado (combinado de escritura). Si la región de memoria no está[/SIZE][/FONT]
[FONT=Droid Serif, serif][SIZE=1]ajustada al tipo correcto de cacheado, usted experimentará parpadeos[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]en la reproducción
de videos y rendimiento 3D reducido.[/SIZE][/FONT][FONT=Droid Serif, serif][SIZE=3]

Interpretando la Ganancia de Rendimiento[/SIZE][/FONT][FONT=Droid Serif, serif][SIZE=1]
No Confie en Glxgears.[/SIZE][/FONT]  [FONT=Droid Serif, serif][SIZE=1]En serio. 
La medición de glxgears que obtenga puede ser reducida[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]después de seguir esta guia y 
habilitar la aceleración UXA, pero NO[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]SIGNIFICA que las cosas hayan empeorado.[/SIZE][/FONT][FONT=Droid Serif, serif][SIZE=1]
La aplicación glxgears nunca fué un banco de pruebas acertado de [/SIZE][/FONT][FONT=Droid Serif, serif][SIZE=1]rendimiento 3D, y 
los desarrolladores han intentado hacer entender[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]a los usuarios por mucho, mucho tiempo. 
Vea [esta página]("http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark") para tener[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]una mejor explicación.[/SIZE][/FONT]
[FONT=Droid Serif, serif][SIZE=1]Le sugiero que tome otra herramienta para medir rendimiento. En[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]mi caso particular, 
utilizo PlanetPenguin racer (habilitando el[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]contador de cuadros por segundo en las opciones).[/SIZE][/FONT][FONT=Droid Serif, serif][SIZE=3]

Para revertir los cambios[/SIZE][/FONT]
[FONT=Droid Serif, serif][SIZE=1]Si estas configuraciones no le solucionaron el problema, aqui tiene[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]cómo revertir los cambios.[/SIZE][/FONT][FONT=Droid Serif, serif][SIZE=1]

1. Edite el archivo sources.list[/SIZE][/FONT][FONT=Droid Serif, serif][SIZE=1]
[COLOR=Red]$ gksudo gedit /etc/apt/sources.list[/COLOR][/SIZE][/FONT][FONT=Droid Serif, serif][SIZE=1]

Borre las lineas para los repositorios xorg-edgers y/o X-Updates,[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]salve y cierre.[/SIZE][/FONT][FONT=Droid Serif, serif][SIZE=1]
2. Desactualice los paquetes:[/SIZE][/FONT][SIZE=1]
[/SIZE][COLOR=Red]$ sudo apt-get update[/COLOR][FONT=Droid Serif, serif][COLOR=Red][SIZE=1]
$ sudo apt-get install libdrm-dev/jaunty libdrm2/jaunty libdrm-intel1/jaunty xserver-xorg-video-intel/jaunty libdrm-nouveau1/jaunty libgl1-mesa-dri/jaunty libgl1-mesa-glx/jaunty libgl1-mesa-dev/jaunty libglu1-mesa/jaunty mesa-common-dev/jaunty mesa-utils/jaunty[/SIZE][/COLOR][/FONT][/B]                             

[B][FONT=Droid Serif, serif][SIZE=1]Asegurese que los paquetes solamente sean desactualizados, no[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]borrados. 
Si llega a ser asi, cancele el proceso.[/SIZE][/FONT]

[FONT=Droid Serif, serif][SIZE=1]3. Borre el núcleo 2.6.30
[/SIZE][/FONT][FONT=Droid Serif, serif][COLOR=Red][SIZE=1]$ sudo dpkg -r linux-headers-2.6.30-020630 linux-headers-2.6.30-020630-generic linux-image-2.6.30-020630-generic[/SIZE][/COLOR][/FONT]

[FONT=Droid Serif, serif][SIZE=1]4. Vuelva a la configuración por defecto de xorg.conf:[/SIZE][/FONT][FONT=Droid Serif, serif][SIZE=1]
[COLOR=Red]$ sudo dpkg-reconfigure xserver-xorg[/COLOR][/SIZE][/FONT]

[FONT=Droid Serif, serif][SIZE=1]5. Opcional: borre el script de arreglo de mtrr y el enganche de GDM
[/SIZE][/FONT][FONT=Droid Serif, serif][COLOR=Red][SIZE=1]$ sudo rm /usr/local/bin/fixmtrr.sh /etc/gdm/PostLogin/Default[/SIZE][/COLOR][/FONT][FONT=Droid Serif, serif][SIZE=1]

Su sistema estará restaurado al normal.[/SIZE][/FONT][/B]

---

### Post by leonardomdq on 2009-06-25
Excelente el tutorial Pablo, muy bueno.
Cual de las configuraciones me aconsejas para empezar?

---

### Post by pablo.s on 2009-06-25
Vos ya actualizaste a 2.6.30,
asi que podés probar con la
Optima. Fijate todos los pasos
pero no hagas la parte de
actualizar el kernel.

---

### Post by leonardomdq on 2009-06-25
Probe con la Optima, te digo los pasos que segui a ver si me comi alguno.

Primero edite el xorg.conf y me quedo asi:
```

Section "Device"
        Identifier      "Configured Video Device"
        Option          "AccelMethod"                   "uxa"
        Option          "EXAOptimizeMigration"          "true"
        Option          "MigrationHeuristic"            "greedy"
        Option          "Tiling"                        "false"
[FONT=Arial]EndSection[/FONT]


```despues ejecute en una terminal:
```

$ sudo wget [http://launchpadlibrarian.net/26193373/fixmtrr.sh](http://launchpadlibrarian.net/26193373/fixmtrr.sh) -O /usr/local/bin/fixmtrr.sh
$ sudo chmod +x /usr/local/bin/fixmtrr.sh 

```y este otro:
```

$ sudo ln -s /usr/local/bin/fixmtrr.sh /etc/gdm/PostLogin/Default[COLOR=Red][B][FONT=Droid Serif, serif]
[/FONT][/B][/COLOR]
```[COLOR=Red][B][FONT=Droid Serif, serif]

[/FONT][/B][/COLOR]Luego reinicie el sistema.
[COLOR=Red][B][FONT=Droid Serif, serif]
[/FONT][/B][/COLOR]Despues fui a sistema -> aparariencia -> efectos visuales y NO me dejo activarlos.

Nose si me comi algun paso.

Creo que me falto la Parte B, ya la estoy haciendo..

---

### Post by leonardomdq on 2009-06-25
Segui con la parte B :

```

[FONT=Droid Serif, serif][SIZE=1]2. Importe la clave pública del PPA de X Updates, actualice sus fuentes[/SIZE][/FONT] [FONT=Droid Serif, serif][SIZE=1]APT y 
proceda a actualizar:[/SIZE][/FONT] 
[COLOR=Red]$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9 
$ sudo apt-get update [/COLOR][FONT=Arial][SIZE=1][COLOR=Red]
[/COLOR][/SIZE][/FONT]
```cuando ejecute en la consola el** $sudo apt-get update** y **$sudo apt-get dist-upgrade** me devolvio esto:
> 
leonardo@leonardo-laptop:~$ gksudo gedit /etc/apt/sources.list
leonardo@leonardo-laptop:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9 
[sudo] password for leonardo: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9
gpg: solicitando clave AF1CDFA9 de hkp servidor keyserver.ubuntu.com
gpg: clave AF1CDFA9: clave pública "Launchpad PPA for Ubuntu-X" importada
gpg: Cantidad total procesada: 1
gpg:               importadas: 1  (RSA: 1)
leonardo@leonardo-laptop:~$ sudo apt-get update 
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty Release.gpg
Obj [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                     
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty/main Translation-es                    
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty/restricted Translation-es              
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty/universe Translation-es                
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty/multiverse Translation-es              
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty-updates Release.gpg                    
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                
Obj [http://deb.opera.com](http://deb.opera.com) lenny Release.gpg                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-es             
Ign [http://deb.opera.com](http://deb.opera.com) lenny/non-free Translation-es                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-es       
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty-updates/main Translation-es            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-es                        
Obj [http://deb.opera.com](http://deb.opera.com) lenny Release                                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-es         
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty-updates/restricted Translation-es      
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                
Ign [http://deb.opera.com](http://deb.opera.com) lenny/non-free Packages                               
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty-updates/universe Translation-es        
Obj [http://deb.opera.com](http://deb.opera.com) lenny/non-free Packages                               
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty-updates/multiverse Translation-es      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-es       
Obj [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release 
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty Release                             
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty-updates Release                        
Obj [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Obj [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages             
Obj [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                    
Obj [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources              
Obj [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages               
Obj [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                
Obj [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages             
Obj [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources              
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty/main Packages                          
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty/restricted Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty/main Sources   
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty/restricted Sources
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty/universe Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-es
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg        
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty/universe Sources                      
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty/multiverse Packages                   
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty/multiverse Sources                    
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty-updates/main Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty-updates/restricted Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty-updates/main Sources
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty-updates/restricted Sources
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty-updates/universe Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty-updates/universe Sources
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty-updates/multiverse Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty-updates/multiverse Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-es
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-es
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-es
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-es
Des:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-es
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                              
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                              
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Des:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74,7kB]                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                               
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                               
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                               
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                               
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Descargados 308B en 12s (24B/s)                                                
Leyendo lista de paquetes... Hecho
leonardo@leonardo-laptop:~$ sudo apt-get dist-upgrade 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Calculando la actualización... Listo
Se actualizarán los siguientes paquetes:
  fglrx-modaliases libdrm-intel1 libdrm2 libssl0.9.8 nvidia-173-modaliases
  nvidia-180-modaliases nvidia-96-modaliases openssl
  xserver-xorg-input-synaptics xserver-xorg-video-ati xserver-xorg-video-nv
  xserver-xorg-video-openchrome xserver-xorg-video-radeon
  xserver-xorg-video-sisusb
14 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
Necesito descargar 5204kB de archivos.
Se utilizarán 36,9kB de espacio de disco adicional después de esta operación.
¿Desea continuar [S/n]? s
Des:1 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty-updates/main libssl0.9.8 0.9.8g-15ubuntu3.2 [2924kB]
Des:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main libdrm2 2.4.9-1ubuntu1~xup~1 [381kB]
Des:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main libdrm-intel1 2.4.9-1ubuntu1~xup~1 [379kB]
Des:4 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty-updates/main openssl 0.9.8g-15ubuntu3.2 [398kB]
Des:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main nvidia-173-modaliases 173.14.16-0ubuntu2 [18,1kB]
Des:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main nvidia-180-modaliases 185.18.14-0ubuntu1 [14,4kB]
Des:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main nvidia-96-modaliases 96.43.10-0ubuntu2 [16,4kB]
Des:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main xserver-xorg-input-synaptics 0.99.3-2ubuntu5 [68,9kB]
Des:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main xserver-xorg-video-radeon 1:6.12.2-0ubuntu1~xup~1 [459kB]
Des:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main xserver-xorg-video-ati 1:6.12.2-0ubuntu1~xup~1 [190kB]
Des:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main xserver-xorg-video-nv 1:2.1.13-1ubuntu1~xup~1 [107kB]
Des:12 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main xserver-xorg-video-openchrome 1:0.2.903+svn741-1build1 [187kB]
Des:13 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main xserver-xorg-video-sisusb 1:0.9.1-1build1 [48,4kB]
Des:14 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main fglrx-modaliases 2:8.602-0ubuntu1~xup~1 [11,4kB]
Descargados 5204kB en 25s (207kB/s)                                            
Preconfigurando paquetes ...
(Leyendo la base de datos ...  
140533 ficheros y directorios instalados actualmente.)
Preparando para reemplazar libssl0.9.8 0.9.8g-15ubuntu3 (usando .../libssl0.9.8_0.9.8g-15ubuntu3.2_i386.deb) ...
Desempaquetando el reemplazo de libssl0.9.8 ...
Preparando para reemplazar libdrm2 2.4.5-0ubuntu4 (usando .../libdrm2_2.4.9-1ubuntu1~xup~1_i386.deb) ...
Desempaquetando el reemplazo de libdrm2 ...
Preparando para reemplazar libdrm-intel1 2.4.5-0ubuntu4 (usando .../libdrm-intel1_2.4.9-1ubuntu1~xup~1_i386.deb) ...
Desempaquetando el reemplazo de libdrm-intel1 ...
Preparando para reemplazar nvidia-173-modaliases 173.14.16-0ubuntu1 (usando .../nvidia-173-modaliases_173.14.16-0ubuntu2_i386.deb) ...
Desempaquetando el reemplazo de nvidia-173-modaliases ...
Preparando para reemplazar nvidia-180-modaliases 180.44-0ubuntu1 (usando .../nvidia-180-modaliases_185.18.14-0ubuntu1_i386.deb) ...
Desempaquetando el reemplazo de nvidia-180-modaliases ...
Preparando para reemplazar nvidia-96-modaliases 96.43.10-0ubuntu1 (usando .../nvidia-96-modaliases_96.43.10-0ubuntu2_i386.deb) ...
Desempaquetando el reemplazo de nvidia-96-modaliases ...
Preparando para reemplazar openssl 0.9.8g-15ubuntu3 (usando .../openssl_0.9.8g-15ubuntu3.2_i386.deb) ...
Desempaquetando el reemplazo de openssl ...
Preparando para reemplazar xserver-xorg-input-synaptics 0.99.3-2ubuntu4 (usando .../xserver-xorg-input-synaptics_0.99.3-2ubuntu5_i386.deb) ...
Desempaquetando el reemplazo de xserver-xorg-input-synaptics ...
Preparando para reemplazar xserver-xorg-video-radeon 1:6.12.1-0ubuntu2 (usando .../xserver-xorg-video-radeon_1%3a6.12.2-0ubuntu1~xup~1_i386.deb) ...
Desempaquetando el reemplazo de xserver-xorg-video-radeon ...
Preparando para reemplazar xserver-xorg-video-ati 1:6.12.1-0ubuntu2 (usando .../xserver-xorg-video-ati_1%3a6.12.2-0ubuntu1~xup~1_i386.deb) ...
Desempaquetando el reemplazo de xserver-xorg-video-ati ...
Preparando para reemplazar xserver-xorg-video-nv 1:2.1.12-1ubuntu5 (usando .../xserver-xorg-video-nv_1%3a2.1.13-1ubuntu1~xup~1_i386.deb) ...
Desempaquetando el reemplazo de xserver-xorg-video-nv ...
Preparando para reemplazar xserver-xorg-video-openchrome 1:0.2.903+svn713-1ubuntu1 (usando .../xserver-xorg-video-openchrome_1%3a0.2.903+svn741-1build1_i386.deb) ...
Desempaquetando el reemplazo de xserver-xorg-video-openchrome ...
Preparando para reemplazar xserver-xorg-video-sisusb 1:0.9.0-4 (usando .../xserver-xorg-video-sisusb_1%3a0.9.1-1build1_i386.deb) ...
Desempaquetando el reemplazo de xserver-xorg-video-sisusb ...
Preparando para reemplazar fglrx-modaliases 2:8.600-0ubuntu2 (usando .../fglrx-modaliases_2%3a8.602-0ubuntu1~xup~1_i386.deb) ...
Desempaquetando el reemplazo de fglrx-modaliases ...
Procesando disparadores para man-db ...
Procesando disparadores para hal ...
Regenerating hal fdi cache ...
 * Restarting Hardware abstraction layer hald                            [ OK ] 
Configurando libssl0.9.8 (0.9.8g-15ubuntu3.2) ...

Configurando libdrm2 (2.4.9-1ubuntu1~xup~1) ...

Configurando libdrm-intel1 (2.4.9-1ubuntu1~xup~1) ...

Configurando nvidia-173-modaliases (173.14.16-0ubuntu2) ...
Configurando nvidia-180-modaliases (185.18.14-0ubuntu1) ...
Configurando nvidia-96-modaliases (96.43.10-0ubuntu2) ...
Configurando openssl (0.9.8g-15ubuntu3.2) ...

Configurando xserver-xorg-input-synaptics (0.99.3-2ubuntu5) ...
Configurando xserver-xorg-video-radeon (1:6.12.2-0ubuntu1~xup~1) ...
Configurando xserver-xorg-video-ati (1:6.12.2-0ubuntu1~xup~1) ...
Configurando xserver-xorg-video-nv (1:2.1.13-1ubuntu1~xup~1) ...
Configurando xserver-xorg-video-openchrome (1:0.2.903+svn741-1build1) ...

Configurando xserver-xorg-video-sisusb (1:0.9.1-1build1) ...
Configurando fglrx-modaliases (2:8.602-0ubuntu1~xup~1) ...
Procesando disparadores para libc6 ...
ldconfig deferred processing now taking place
leonardo@leonardo-laptop:~$ 


Ahora me pidio Reinciar....sino me ves conectado imaginate porque es :lol:

---

### Post by pablo.s on 2009-06-25
Es raro. Tenes que copiar el texto
que aparece [aca]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x3B22AB97AF1CDFA9") y pegarlo en un
archivo de texto.
Despues fijate en Fuentes de Software, en
la solapa de Autentificacion, cliquea en
Importar Clave Publica y elegi el archivo
que guardaste antes.
Luego otra vez hace
[COLOR="DarkGreen"]**sudo apt-get update**[/COLOR]

---

### Post by leonardomdq on 2009-06-25
> **pablo.s said:**
> Es raro. Tenes que copiar el texto
que aparece [aca]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x3B22AB97AF1CDFA9") y pegarlo en un
archivo de texto.
Despues fijate en Fuentes de Software, en
la solapa de Autentificacion, cliquea en
Importar Clave Publica y elegi el archivo
que guardaste antes.
Luego otra vez hace
[COLOR=DarkGreen]**sudo apt-get update**[/COLOR]
Ya lo solucione ese tema, la segunda ves que probe la tomo sin problemas.
Hice lo que deje arriba en el mensaje, creo no haber olvidado nada en el camino, sino corregime.
Reinicie y sigo sin poder activar los efectos visuales.

Tendre que probar con la maxima?

---

### Post by pablo.s on 2009-06-25
El script mtrrfix lo bajaste y
está activado?

---

### Post by leonardomdq on 2009-06-25
> **pablo.s said:**
> El script mtrrfix lo bajaste y
está activado?
Mmm esa parte me la pase....estube mirando y no entiendo esa parte del script ni como activarlo tampoco :(

---

### Post by pablo.s on 2009-06-25
Si procediste según el
tutorial, tendría que
dejarte activar Compiz.
No sé bien que aconsejarte.

---

### Post by leonardomdq on 2009-06-25
Si te referias a bajar el script y activarlo es esto si lo hice.
```

$ sudo wget [http://launchpadlibrarian.net/26193373/fixmtrr.sh](http://launchpadlibrarian.net/26193373/fixmtrr.sh) -O /usr/local/bin/fixmtrr.sh
$ sudo chmod +x /usr/local/bin/fixmtrr.sh 

$ sudo ln -s /usr/local/bin/fixmtrr.sh /etc/gdm/PostLogin/Default

```[COLOR=Red][B][FONT=Droid Serif, serif]
[/FONT][/B][/COLOR]Lo unico que me queda es probar con la Opcion Maxima y sino hacer upgrade a KK alpha2 [COLOR=Red][B][FONT=Droid Serif, serif]:P
[/FONT][/B][/COLOR]
Nose que decirte, vengo luchando con esta placa Intel desde que estoy con JJ[COLOR=Red][B][FONT=Droid Serif, serif]
[/FONT][/B][/COLOR]

---

### Post by pablo.s on 2009-07-03
[COLOR=White].[/COLOR]

---

### Post by Hei Ku on 2009-07-04
Idem thread anterior.

---

### Post by Josemar on 2009-07-10
Buen tutorial, pero debo pedir algo, o más bien como una explicación que me ayude en esto.
Segui la parte de la configuración máxima y tengo una tarjeta wifi con chipset ralink, el asunto es que instale el driver para poder poner la tarjeta en modo monitor y al seguir dicha parte del tuto no puedo usarlo, ya que queda como privativo, que puedo hacer?, solo en la configuración segura es en donde puedo usar drivers privativos o existe una manera de poder poner dicho driver ahora?

---

### Post by pablo.s on 2009-07-10
A la placa no la reconoce
Ubuntu sin los drivers?
Hay muchas placas Ralink que
usan el firmware incorporado.

---

### Post by Josemar on 2009-07-10
> **pablo.s said:**
> A la placa no la reconoce
Ubuntu sin los drivers?
Hay muchas placas Ralink que
usan el firmware incorporado.
Lo que pasa es que instale los drivers que baje de la página para poder usar la tarjeta en modo monitor, con los que vienen por defecto me es imposible hacerlo, es ese el detalle, por ejemplo para usar el aircrack-ng

---

