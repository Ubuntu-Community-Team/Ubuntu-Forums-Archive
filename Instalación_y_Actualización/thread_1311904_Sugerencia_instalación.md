---
title: "Sugerencia instalación"
date: 2009-11-02
forum: Instalación y Actualización
---

### Post by Maciett on 2009-11-02
Hola a todos.

Bueno, he leido harto sobre linux y llegué a una conclusión, no todos los SO sirven en todos los equipos. 

Me gustó mucho la filosofía del software libre, así que me gustaría instalar una versión que optimice el pc. No podré migrar 100% a linux por que unos de los programas de la u (el mplab y proteus) corren con errores en wine, lo probé en el ubuntu jaunty, y no están suportados para otro SO que no sea win por los fabricantes.

Quisiera saber que distribución es la más apropiada a mi pc, es un portatil chiquitito en todos los sentidos, los detalles los pongo al final.

Por gustos, me hubiera quedado con algo de la linea de ubuntu, pero no se lo puede bien.

Y requerimientos, uso explorador, chat, gestor de correos, editor de textos y diapositivas, ojala que exporte a pdf, visor de pdf, algún programa editor de imágenes tipo photoshop y vlc.

Características del pc:

lspci |grep Ethernet && lspci |grep Wireless && lspci |grep Network

00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

 lspci 

00:01.0 Host bridge: Advanced Micro Devices [AMD] CS5536 [Geode companion] Host Bridge (rev 31)
00:01.1 VGA compatible controller: Advanced Micro Devices [AMD] Geode LX Video
00:01.2 Entertainment encryption device: Advanced Micro Devices [AMD] Geode LX AES Security Block
00:0c.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
00:0c.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
00:0c.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0f.0 ISA bridge: Advanced Micro Devices [AMD] CS5536 [Geode companion] ISA (rev 03)
00:0f.2 IDE interface: Advanced Micro Devices [AMD] CS5536 [Geode companion] IDE (rev 01)
00:0f.3 Multimedia audio controller: Advanced Micro Devices [AMD] CS5536 [Geode companion] Audio (rev 01)
00:0f.4 USB Controller: Advanced Micro Devices [AMD] CS5536 [Geode companion] OHC (rev 02)
00:0f.5 USB Controller: Advanced Micro Devices [AMD] CS5536 [Geode companion] EHC (rev 02)

iwconfig 

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

Algunos datos extra:

Se calienta mucho >.<.
Ya no me urge la wifi, si no corre no importa.

Acepto sus sugerencias

Saludos

---

### Post by N4zgu1 on 2009-11-02
No se que tiene de malo ubuntu
para el chat you uso emesene que es estable y es muy parecido a messenger
gestor de correos esta thunderbird
con open office 3 podras editar textos, diapositivas y exportar pdf
gimp es un buen editor de imagenes

para proteous hay varias opciones como kicad y xcircuit

en cuanto a mlab puedes probar instalarlo con crossover o instalar xp en una maquina virtual


Otros linux que tambien son buenos son fedora, opensuse, archlinux, etc

---

### Post by moreback on 2009-11-02
Piklab sirve para los PIC, pero no lo he probado mucho y no sé si sirva para usarlo con el PICkit2.

El MPLAB si funciona vía VirtualBox (el OSE no, tiene que ser el oficial por el soporte USB).

Te faltó indicar cantidad de memoria RAM y disco duro, de paso indicar el modelo del laptop, ya que GIMP y el OpenOffice son grandes consumidores de memoria (el FIrefox también).

Saludos.

---

### Post by AlexDDR on 2009-11-03
pero tienes un mini notebook con amd geodelx de 800mhz??

porque si es asi no se si pueda correr ubuntu muy rápido ni alguno programa muy pesado como una maquna virtual y etc

para mi windows xp como SO y lo que mas puedas como progrmas en opensouerce que tiene sus ersiones para windows

saludos

---

### Post by Maciett on 2009-11-03
Olvide poner la memoria, tienen razón, tiene 1G de Ram y 80G de disco duro. El modelo no lo puse porque estaba en otro post que hice hace algún tiempo acá, pero lo reescribo, packardbell easynote sp 18. Lo uso con pantalla, teclado y mouse externo en casa y a la u lo llevo sin periféricos.

Ubuntu jaunty corre lento y casi con cualquier aplicación se toma su tiempo para hacer lo básico. No estoy diciendo nada malo contra Ubuntu, es mi pc que parece que no se la puede con esta versión.

También probe el software que me indicas N4zgu1, pero tarda mucho en cargar estas aplicaciones, onda el openoffice de repente se pegaba mientras escribia y después de un rato me mostraba lo que puse.

Sobre los simuladores, no se si los que me indicas pueden simular los archivos que exporta el mplab en hexa. Si pueden, me dices. MPlab fue un problema cuando lo corri, como indique antes, con wine, me daba resultados erroneos comparado a ejecutar lo mismo en win. Pero esto no es problema, puedo vivir hasta que salga de la u con el pc particionado.

Alex, entendiste justo lo que quise transmitir. Por eso, quiero saber que distribución o versión de linux me optimizaría el equipo, con que software, que sea eficiente y no tenga programas que no voy a usar en el mediano plazo.

Saludos y gracias por sus sugerencias, seguimos en contacto.

---

### Post by AlexDDR on 2009-11-03
la verdad es que yo tenia un amd duron de 1600 mhz que actualicé porque ya lo encontraba muy lento para ubuntu.

De hecho si te fijas en firefox por ejemplo si lo comparas contra windows es mucho mas lento , ya que el plugin de flash de linux es hasta 10 veces mas lento que el de windows en algunas aplicaciones, por lo que no se (no he probado tu equipo) si pueda correr un video de youtube sin cortes en linux, pero talvez en windows si lo haga al menos los de baja calidad.

Entoncs empiezo a ver la ultilidad osea lo practico del asunto, y asi como tu equipo no esta hecho para ni siquiera correr windows vista o 7, si fue hecho para windows xp, por eso te recomiendo que mantengas windows xp en tu netbook y hagas una instalacion compartida entre alguna distro linux y XP


¿Que distro?

En general las distribuciones linux no son pesadas, lo que las hace pesadas son los programas , el entorno de escritorio y os servicios que corran por detras.

Otra cosas que afecta el rendimiento son los drivers de video (puedes correr un video a pantala completa sin tearing o flickering ?? (se nota en escenas de mucho movimiento que se ven como lineas ya que el cuardo no se alcanza a dibujar en pantalla cuando ya tiene que dibujar el otro entonces queda a la mitad, por lo que no se esta usando la aceleracion de video XV)


Entonces??

te recomiendo  esta , crunchbang linux

[http://crunchbanglinux.org/](http://crunchbanglinux.org/)

es un poco espartana pero esta basada en ubuntu y con un escritorio liviano , manejador de ventanas liviano software liviano etc


Y para firefox , tiene que instalar el complemento adblock plus y el flash killer para blockear todo el contenido flash que pueda consumir recursos de tu pc, ademas para los videos de youtube puedes instalar el complemento greasemonkey y despues el script youtube without flash auto que esta aca [http://userscripts.org/scripts/show/50771](http://userscripts.org/scripts/show/50771)  con eso podras ver videos de youtube en totem, que consume menos recursos y no te sale propaganda , ejejej, pero no funciona la barra de seeking de totem pero casi no es problema para lo que se gana (tienes que tener instalado el complemento de firefox mozilla totem.

para aumentar el buffer de totem , puedes hacerlo ejecutando el gconf-editor, buscas el directorio de totem en y editas la parte del buffer total y el minimo, para aumentarlo para que precargue lo suficiente el video y no haya cortes

para los documentos de office 2007, puedes instalar con wind, agregando el repositorio de wine para su ultima version, y ver si corre más rapido que openoffice (lo que no me extrañaria)

Además un editor de texto ligero es Abiword, podrias probarlo, y tambien guarda en .doc y en odt


saludos, esper ohaberte ayudado

---

### Post by nopersona on 2009-11-03
Una buena buena es DreamLinux, abajito en mi firma sale el link. La uso en un note single core con 512 y vuela. Algo más actual y moderno podría ser ChakraLinux, aunque viene con KDE4 al estar basada en archlinux es una maravilla, probada en el mismo equipo, también vuela. Si estás acostumbrada a ubuntu linuxmint con xfce sería una muy buena idea, es bastante funcional. 

Si ningúna te convence podrías ir mirando otras distros con otros entornos, hay muuucho de donde elegir, eso es lo bonito :p

Suerte!

P.S.: Todas las que te recomendé vienen en livecd, y chakra incluye drivers propietarios para el testeo.

---

### Post by Maciett on 2009-11-04
En realidad, no lo uso para ver videos. No necesito aplicaciones como esa, por ahora.

De fabrica venía con un SO win xp home.

Sobre el entorno gráfico, no me importa mucho la estética, me importa su practicidad.

Estoy entendiento que puedo tener un SO y aplicaciones que no vienen con él y así lograr la optimización, así que por lo pronto definiré que SO es el mejor para el portátil, y después veré lo del software.

Voy a leer dentro de la semana los SO que me proponen y si alguno me convence, me facilitarían el live cd?

Saludos

---

### Post by Carlos C on 2009-11-04
Una opción es instalar el minimal cd de Ubuntu. Con eso tendrás la base del sistema y si tienes conexión a internet puedes ir instalando los paquetes que necesites. Yo hice eso en un laptop del año 95 (venía con windows 95) y conseguí instalar el minimal de ubuntu con entorno lxde. El equipo tiene 256 de ram, una cpu pentium 3 de 500 y no vuela, pero sirve mucho más que cuando tenía windows.

Basado en Ubuntu existe [U-lite]("http://u-lite.org/") (aunque no es una variante oficial). Tiene LiveCD y he tenido buenos comentarios sobre ella.

---

### Post by Maciett on 2009-11-14
Hola a todos,

Ya leí sobre todos los SO que me sugirieron y la compatibilidad con hardware del fabricante de mi equipo. Estuve como una semana anonadada, no sabía que existía tal cantidad de distribuciones, me sorprendí.

Encontré dos con buenas referencias, Crunchlinux y linuxmint. Me tinca más linuxmint. Esto es subjetivo. No tiene una versión especial para equipos portátiles, por lo que bajé el de escritorio que se llama linux mint 8 "Helena" RC1.

Si saben algo que debo considerar antes de comenzar la instalación, este es buen momento para decirlo.  

Gracias a todos, desde ya, por darme tantas alternativas.

Saludos

---

### Post by AlexDDR on 2009-11-15
que bueno que sigas adelante.


mi recomendacion Nº1 es siempre RESPALDA TUS DATOS!!!, al menos los mas importantes.

y la numero dos es crea una particion separada para /home para reinstalar de manera mas menos facil

esas

despue snos cuentas como te anda linux en tu netbook 

saludos

---

### Post by nopersona on 2009-11-15
> **Maciett said:**
> Hola a todos,

Ya leí sobre todos los SO que me sugirieron y la compatibilidad con hardware del fabricante de mi equipo. Estuve como una semana anonadada, no sabía que existía tal cantidad de distribuciones, me sorprendí.

Encontré dos con buenas referencias, Crunchlinux y linuxmint. Me tinca más linuxmint. Esto es subjetivo. No tiene una versión especial para equipos portátiles, por lo que bajé el de escritorio que se llama linux mint 8 "Helena" RC1.

Si saben algo que debo considerar antes de comenzar la instalación, este es buen momento para decirlo.  

Gracias a todos, desde ya, por darme tantas alternativas.

Saludos

NO te recomiendo que instales la RC1, ya que es la primera prueba de la versión que viene, por ende, es para testear, no recomendable para uso diario. Instala la estable.

---

### Post by Maciett on 2009-11-16
Hola,

Creo que ya me confundí. Cuando baje la version de mint, leí que los paquetes de prueba si uno quiere las baja aparte, creo que los beta se llaman "Romeo". No te entiendo por que dices el 8 es para testear nopersona.

De todos modos aun no instalo, y lo probé en live cd, es muy lindo y trae muchos codecs y drivers, pero se demora igual que ubuntu para las aplicaciones básicas, usa los mismos repositorios. Así que descartado.

Y sigo buscando SO...Que pena que exista un ubuntu netbook solo para procesadores intel, es lo mas parecido a lo que me gustaría que he visto.

Bueno, seguiré atenta a sus sugerencias.

Seguimos en Contacto

---

### Post by AlexDDR on 2009-11-16
[QUOTE]pero se demora igual que ubuntu para las aplicaciones básicas/QUOTE]


Pero se demora en iniciarlas o ya cuando estan funcionando??

cuales aplicaciones??


WINDOWS  precarga las aplicaciones como word , IE y varias otras con el super fetch o algo asi, en el inicio de sesion , por eso demora tanto en cargar windows pero despues al abrir las aplicaciones , estas abren mas rapido debido a que estan ya precargadas en memoria, lo que aumenta el consumo de ram aunque uno no las este ocupando, en cambio en ubuntu no se precargan en forma predeterminada.


Te recomiendo instalas el adblock plus de firefox o usar chromium como navegador ya que firefox en linux es mas lento que en windows , y flash (las animaciones) consume mas recusos tambien que su version de windows.


saludos

---

### Post by Maciett on 2009-11-16
Hola Alex,

Cuando digo que se demoran las cosas básicas, ahora que lo mencionas probé las aplicaciones que traía por defecto, openoffice, gimp, firefox, thunderbird, etc. Probé viendo el monitor del sistema y sólo con mover el mouse sobre el escritorio rapidamente la cpu se cargaba al 8x-9x%, por correr los programas anteriores al 100% y por modificar preferencias del sistema como el idioma o el tamaño de la letra también.

¿Entonces con sólo cambiar el software ya no consumirá tanto recurso el sistema?
 
Saludos

---

### Post by nopersona on 2009-11-16
> **Maciett said:**
> Hola,

Creo que ya me confundí. Cuando baje la version de mint, leí que los paquetes de prueba si uno quiere las baja aparte, creo que los beta se llaman "Romeo". No te entiendo por que dices el 8 es para testear nopersona.

De todos modos aun no instalo, y lo probé en live cd, es muy lindo y trae muchos codecs y drivers, pero se demora igual que ubuntu para las aplicaciones básicas, usa los mismos repositorios. Así que descartado.

Y sigo buscando SO...Que pena que exista un ubuntu netbook solo para procesadores intel, es lo mas parecido a lo que me gustaría que he visto.

Bueno, seguiré atenta a sus sugerencias.

Seguimos en Contacto

Esas son las fases de desarrollo de software. Había escrito algo más educativo, pero lo pasé a borrar.

[http://es.wikipedia.org/wiki/Fases_del_desarrollo_de_software](http://es.wikipedia.org/wiki/Fases_del_desarrollo_de_software)

La versión que tú basjate es la RC, o sea, casi la final, pero no lo es. Por ejemplo, ubuntu usa: alpha, beta, rc y versión final. Bajate la estable, que creo es la 7, con xfce que es más liviano. Probaste DreamLinux? Es una muy buena distro, Debian PURO. 

Links de ineterés:

[http://www.jolicloud.com/](http://www.jolicloud.com/) (tiene muy buena pinta, sobre todo por el soporte de "jaguar")

[http://www.thinkgos.com](http://www.thinkgos.com)

[http://www.taringa.net/posts/linux/2678088/Distro-de-Linux-para-netbooks.html](http://www.taringa.net/posts/linux/2678088/Distro-de-Linux-para-netbooks.html)

Suerte!

---

### Post by AlexDDR on 2009-11-17
> **Maciett said:**
> Hola Alex,

Cuando digo que se demoran las cosas básicas, ahora que lo mencionas probé las aplicaciones que traía por defecto, openoffice, gimp, firefox, thunderbird, etc. Probé viendo el monitor del sistema y sólo con mover el mouse sobre el escritorio rapidamente la cpu se cargaba al 8x-9x%, por correr los programas anteriores al 100% y por modificar preferencias del sistema como el idioma o el tamaño de la letra también.

¿Entonces con sólo cambiar el software ya no consumirá tanto recurso el sistema?
 
Saludos

Segun lo que se , se supone que es un asusnto de sistema , osea hardware+SO+drivers+software, de eso dependerá si el sistema correr más rapido o no.

En general Ubuntu es un poco mas lento que xp, pero no el sistema, sino las aplicaciones, como veras linux o ponen hasta en celulares.

Te recomiendo instalar Chromium como navegador, es bastante rapido

Openoffice es más pesado que MSOffice

Y en mi experiencia, correr UBuntu en un CPU dual core es muchisimo mejor que en un mono core.


Por ejemplo yo tenia un amd duron de 1600mhz y una ati radeon 7000 de 64mb(vieja), y los driver de viedo libres fueron empeorando con cada version de Xorg(el servidor grafico de linux), a la vez que me acostumbraba a la rapidez de computadors modernos. Asi que tuve que renovar el pc para usar linux. peor el computador todavia se defiende para navegar en intenet conwin xp, en cambio con Ubuntu 9.10 se traba contantemente y el consumo es siempre alto.

Tengo ganas de probar ubuntu con un netbook  para ver que tal, en cuanto a consumo de CPU. Pero como te digo, los drivers tiene muchoque ver, recuerda que los fabricantes la mayoria de las veces no proeen informacion a los desarrolladores linux y estos se las tiene que arreglar como sea y eso no siempre es lo optimo, menos en rendimiento.


Tu procesador segun lei por ahi esta bajo en rendimiento a un celeron de 900mhz, asi que yo no esperaria mucho tampoco, tu equipo esta pensado para portabilidad y hacer lo basico.

Por esa razon te recomende chrunchbang linux ya uqe consume menos cpu en varias aspectos.

saludos

---

### Post by Maciett on 2009-11-17
Hola a todos,

Gracias por lo de las fases de la creación de un software, nopersona, ahora entiendo eso, tienes razón con que RC no es estable.

No probé dreamlinux, porque pide de requerimiento mínimo un procesador de características superiores al que tengo.

Con debian mantengo distancia, le tengo respeto. Creo que fue la primera ditribución de linux que conocí y probé. Y me pedía mucho tiempo. Tengo muchos recuerdos frustantes de él, así que no lo veo como alternativa en este caso.

Vi lo de jolicloud, muy lindo, pero lento y aún en desarrollo. (Aparte: me encantó el foro que tienen, con la respuesta al tiro después de la pregunta y luego los post como fueron expuestos.)

Good SO, no lo entendí bien. Lo que capté es como que es un sistema en la web(?), que para lo único que estaba pensado era para internet, pero no me quedó claro si funciona sin él...

Y ahora estoy descargando Eeedubuntu base 3.0 y crunchbang lite 32 bit, probaré los dos, luego les cuento como me fue.

Gracias por la paciencia que invierten en mi, en alguna junta se agradecera en persona.

Seguimos en contacto

---

### Post by Maciett on 2009-11-18
Hola a todos,

Ya probé los dos y mi experiencia fue:

Eeedubuntu no corrió ni en modo live cd.

Crunchbang corré bien, es rápido y reconoció hardware suficiente para funcionar.(Reconoció pantalla táctil, botones laterales a la pantalla y las particiones existentes.)

Instalé crunch y funciona, quede bien contenta con el sistema, trae un montón de aplicaciones desde consola bien útiles como un reproductor de mp3, que consumen lo justo.

En este periodo aprendí a filtrar mejor los tutoriales que hay en la web, y que ya casi todo está allí.

Gracias a todos los que aportaron, y aunque mi procesador no sea la gran maravilla como decía alex, ahora vuela, es lo que quería.

Saludos

PD: El sistema no es perfecto, pero me gusta. No reconoce todo, pero es significativamente más rápido que ubuntu, cuando lo actualizé usó los repositorios de jaunty, por lo que me imagino que si encuentro soluciones para Ubuntu a algunos detalles que se presentaron me sirven igual.

---

### Post by AlexDDR on 2009-11-18
Que bueno que llegaste a un punto, yo en mi antiguo pc llegue a esa solucion, proban y probando. Además de que no queria perder la cantidad de informacion y programas extras que hay para ubuntu. Crunchbang esta basado en ubuntu y usa sus repositorios, por lo que si quieres un programa ahi lo tendras directo desde synaptic.

Esta distro de linux, saca sus versiones un tiempo despues de Ubuntu, ya que se basa en ella , tiene que desarrollar despues de las version estable de ubuntu. Asi que no demorarán en sacar una basada en la 9.10.

por lo pronto te recomiendo que agregues el ppa de chrumium daily y que uses programas bajos en recursos de cpu, Audacious como reproductor de mp3 por ejemplo.

Y cuando navegues, cuidado con las aplicacioes flash que consumen mucha CPU


Y por ultimo te recomiendo esta web, [http://planetubuntu.es/](http://planetubuntu.es/)
Se pueden sacar muchas cosas de ahi, son geniales, mucha informacion


SAludos

---

### Post by Maciett on 2009-11-18
Ya instalé el chromium, en el segundo intento(la primera vez no leí y se instaló un juego que lleva ese nombre...), lo hice según [http://torturo.com/2009/07/16/instalar-chrome-en-linux-chromium/](http://torturo.com/2009/07/16/instalar-chrome-en-linux-chromium/) y la primera parte no me resultó, así que le metí el repositorio a mano desde el administrador de paquetes, y la clave no se si la pescó o no, pero funciona bien.

Reproductor de mp3 estoy usando una aplicación de consola que se llama MoC y reproduce sin quedarse pegada, buena.

Gracias por la página, así de entrada se ve profunda...

De verdad muchas gracias por todo.

Seguimos en contacto.

---

