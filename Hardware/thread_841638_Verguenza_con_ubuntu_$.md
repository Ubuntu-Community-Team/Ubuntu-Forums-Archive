---
title: "Verguenza con ubuntu :$"
date: 2008-06-26
forum: Hardware
---

### Post by ramiro_md on 2008-06-26
Muchachos ! me quiero matar con lo que me paso !! me sentia como ese tipo que presentoo windows 98 y le salto la pantalla azul !!!...resulta que estaba con un amigo de la facu haciendo unos trabajos en linux (mientras que mi ubuntu descargaba las actus)..ejercicio va, ejercicio viene..floreaba a linux,comentandole un poco del lujo que es tenerlo y sus ventajas con respecto a windous xD...cuestion, que cuando temrina de actualizar reinicio el sistema...y ahi "..la devacle total!..un conjunto de hechos bochornosos" como decian en deportes en el recuerdo...al reiniciar me decia algo de que habia un error en la configuracion del xorg y en los controladores de nvidia...y de ahi me tira  ala terminal y no puedo ingresar a ubuntu en modo grafico =S.Se que me pueden ayudar jeje..asique sere paciente.Un saludo.

---

### Post by dgcampos on 2008-06-26
> **ramiro_md said:**
> Muchachos ! me quiero matar con lo que me paso !! me sentia como ese tipo que presentoo windows 98 y le salto la pantalla azul !!!...resulta que estaba con un amigo de la facu haciendo unos trabajos en linux (mientras que mi ubuntu descargaba las actus)..ejercicio va, ejercicio viene..floreaba a linux,comentandole un poco del lujo que es tenerlo y sus ventajas con respecto a windous xD...cuestion, que cuando temrina de actualizar reinicio el sistema...y ahi "..la devacle total!..un conjunto de hechos bochornosos" como decian en deportes en el recuerdo...al reiniciar me decia algo de que habia un error en la configuracion del xorg y en los controladores de nvidia...y de ahi me tira  ala terminal y no puedo ingresar a ubuntu en modo grafico =S.Se que me pueden ayudar jeje..asique sere paciente.Un saludo.

tranquilo , me pasó lo mismo, es por el driver de nvidia..., decime, te pasó con la versión 2.6.20.17? usá la anterior mientras, está intacta, y remové esta que instalaste y listo...

saludos,

dgc

---

### Post by pabloatilio on 2008-06-26
> **ramiro_md said:**
> Muchachos ! me quiero matar con lo que me paso !! me sentia como ese tipo que presentoo windows 98 y le salto la pantalla azul !!!...resulta que estaba con un amigo de la facu haciendo unos trabajos en linux (mientras que mi ubuntu descargaba las actus)..ejercicio va, ejercicio viene..floreaba a linux,comentandole un poco del lujo que es tenerlo y sus ventajas con respecto a windous xD...cuestion, que cuando temrina de actualizar reinicio el sistema...y ahi "..la devacle total!..un conjunto de hechos bochornosos" como decian en deportes en el recuerdo...al reiniciar me decia algo de que habia un error en la configuracion del xorg y en los controladores de nvidia...y de ahi me tira  ala terminal y no puedo ingresar a ubuntu en modo grafico =S.Se que me pueden ayudar jeje..asique sere paciente.Un saludo.

A mi me paso lo mismo pero por suerte no tenia "público" y pude desinstalar el nuevo kernel y volver a lo que tenía. Eso y el problema que comenté de que se me descompuso el openoffice me hacen pensar que deberían ser más cuidadosos cuando largan las actualizaciones ya que a mucha gente que uno les instala el ubuntu después de un largo trabajo de convensimiento para que prueben algo distinto, te llaman y te dicen "al final es igual  o peor que **el otro**" :-? y ante éste tipo de hechos se hace difícil la defensa de nuestros argumentos (sobre todo cuando me pasan esos dos en 10 días). En mi caso yo solo les dejo marcado actualizaciones de seguridad y actualizaciones importantes, pero pasa igual. Creo que se está logrando mucho con esta distro y no hay que descuidad este tipo de detalles para poder mantener lo logrado.

Saludos

---

### Post by dgcampos on 2008-06-26
> **pabloatilio said:**
> A mi me paso lo mismo pero por suerte no tenia "público", eso y el problema que comenté de que se me descompuso el openoffice me hacen pensar que deberían ser más cuidadosos cuando largan esas actualizaciones ya que a mucha gente que uno les instala el ubuntu te llaman y te dicen "al final es igual  o peor que **el otro**" :-?

prueba de que, si bien linux SI es mejor sistema operativo que $win$, tampoco es perfecto, pero hablando de la vergüenza que pasó, con windows me pasaban cosas peores...como borrar un archivo desde el explorer y poder recuperarlo desde la papelera, pero si lo borrabas desde un script no lo recuperás más...entre otras y la lista de $win$ sigue...

Pero fijate que además tu sistema no hizo CRASH, solo no reconoció un driver y no pudo arrancar el sistema gráfico, pero linux sigue funcionando...vas a ver que en poco tiempo eso se soluciona también, como todo en linux, en cambio si era $win$, andá a que te manden en "service pack" dentro de 6 meses si tenés suerte...

---

### Post by Mister X on 2008-06-26
Una pregunta, el driver de nvidia, es el que viene con Ubuntu en controladores restringidos o lo instalaste vos por tu cuenta?

---

### Post by Hei Ku on 2008-06-26
De acuerdo a los desarrolladores del kernel, los cuelgues por culpa del driver propietario de NVidia estan en el top 10 de manera constante. De hecho, mas de 130 firmaron una carta pidiendo que todos los fabricantes de hardware abran sus drivers de una buena vez. [https://www.linuxfoundation.org/en/Kernel_Driver_Statement](https://www.linuxfoundation.org/en/Kernel_Driver_Statement)
Es una acusacion directa a NVidia, que ya dijo que no va a abrirlos, porque "asi como estan, andan bien".
Hay un ensayo que cuenta la historia de los drivers de video de los 3 fabricantes mas importantes, Intel, ATI y NVidia, y le pega con un caño a este ultimo. [https://www.linuxfoundation.org/en/Linux_Graphics_Essay](https://www.linuxfoundation.org/en/Linux_Graphics_Essay)

Asi que, la proxima vez que pregunten que placa comprar, piensen a quien le dan su plata. Y que eso de que "mientras ande, no me importa si es libre" tiene sus consecuencias.

---

### Post by faktorqm on 2008-06-26
Che y como puede ser que a mi no me pase eso? yo no segui la guia que posteó vor e instale los drivers de nvidia 71.XX con el envy-ng. Es mágico? Salu2!

---

### Post by Hei Ku on 2008-06-26
depende mucho de tu hardware. como con el alcohol, lo que te mata es la mezcla. :D

---

### Post by ramiro_md on 2008-06-26
Muchachos muy buena la organizacion nueva del foro...me costo un hu3v0 encottrar mi post =P...x oro lado en el grub no me aparece la version vieja del kernel =O..los dirvers lso instale de agregar y quitar..en el menu de aplicaciones.

---

### Post by Mister X on 2008-06-27
> **Hei Ku said:**
> 
Asi que, la proxima vez que pregunten que placa comprar, piensen a quien le dan su plata. Y que eso de que "mientras ande, no me importa si es libre" tiene sus consecuencias.

Absolutamente cierto!

---

### Post by EnriqueK on 2008-06-27
> **Hei Ku said:**
>  De hecho, mas de 130 firmaron una carta pidiendo que todos los fabricantes de hardware abran sus drivers de una buena vez. 
Nunca lo van a hacer, por mas que junten 500 millones de firmas y esto no es por conspiraciones, presiones de M$ ni nada que se les parezca, sino por que simplemente no están dispuestos de distribuir el código fuente de los drivers por que es información que en manos de gente de la competencia pueden tener conocimiento pleno de los secretos industriales de los productos, los fabricantes no entregan el código fuente a M$ ni a Apple, simplemente los distribuyen listos para instalar por el usuario, opino que Linux y las distros son las que tienen que cambiar de metodología y de esa manera los fabricantes no tendrían ningún problema en distribuir sus drivers compilados para Linux, pero para un solo Linux.

---

### Post by ramiro_md on 2008-06-27
Muy lindas las charlas de filosofia comercial jajaja...pero sigo sin correr ubuntu :(

---

### Post by vk-cdg on 2008-06-27
El grub te muestra un solo kernel o te muestra los anteriores tambien?
Si te muestra los anteriores, probá de arrancar con el 18 a ver si levanta.

---

### Post by ramiro_md on 2008-06-27
> **vk-cdg said:**
> El grub te muestra un solo kernel o te muestra los anteriores tambien?
Si te muestra los anteriores, probá de arrancar con el 18 a ver si levanta.

No man, me marca un solo kernel. Toqueteando un poco logre arrancar el sistema en modo grafico, pero al activar la aceleracion y demas cuando reiinicio se caga todo de nuevo =S
Lo que hago para q arranque digamos es lo siguiente:
Entro a la opcion recovery mode del grub
selecciono "xfix"
despues le doy a normal boot y anda sale andando hasta que hago eso de activar la aceleracion.

---

### Post by faktorqm on 2008-06-27
arranca con lo que tengas ganas, y reinstala el driver de nvidia utilizando el mismo metodo que la vez anterior (ya que segun me acuerdo tenes la mother ecs y el envy no te funcaba) y ahi reinicia. Salu2!

---

### Post by ramiro_md on 2008-06-27
Instale los drivers con envy q si funco esta vez :D...acomode mi resolucionde pantalla...active la aceleracion 3d y cuando reinicio la pc zaz! otra vez falla el X :confused:

---

### Post by dgcampos on 2008-06-30
> **ramiro_md said:**
> Instale los drivers con envy q si funco esta vez :D...acomode mi resolucionde pantalla...active la aceleracion 3d y cuando reinicio la pc zaz! otra vez falla el X :confused:

no pudiste desinstalar el kernel con el q t dio problemas? q raro te haya quedado solo un kernel...estás seguro que no hiciste otra cosa mas ademas de instalar un nuevo kernel?

---

### Post by MeduZa on 2008-07-02
> **ramiro_md said:**
> Muchachos ! me quiero matar con lo que me paso !! me sentia como ese tipo que presentoo windows 98 y le salto la pantalla azul !!!...resulta que estaba con un amigo de la facu haciendo unos trabajos en linux (mientras que mi ubuntu descargaba las actus)..ejercicio va, ejercicio viene..floreaba a linux,comentandole un poco del lujo que es tenerlo y sus ventajas con respecto a windous xD...cuestion, que cuando temrina de actualizar reinicio el sistema...y ahi "..la devacle total!..un conjunto de hechos bochornosos" como decian en deportes en el recuerdo...al reiniciar me decia algo de que habia un error en la configuracion del xorg y en los controladores de nvidia...y de ahi me tira  ala terminal y no puedo ingresar a ubuntu en modo grafico =S.Se que me pueden ayudar jeje..asique sere paciente.Un saludo.

pasaste verguenza porque no mirantes (o si lo hiciste no sabias) la lista de updates tenia un kernel nuevo, cuando hay kernel nuevo todo lo que sea compilado contra el kernel. ej: nvidia driver, vmplayer deja de andar porque necesitas compilarlos de nuevo, se puede hacer automatico.

---

### Post by jualin on 2008-07-02
Porque no tratas de reinstalar el Xorg con los drivers de OpenSource. Si tenes acceso a una linea de comandos podes escribir > sudo dpkg-reconfigure xserver-xorg Esto me ha salvado muchas veces cuando algo falla y me quedo sin GUI. Tratalo, a lo mejor soluciona tu problema. Suerte!

---

### Post by madelaki on 2008-07-02
> **ramiro_md said:**
> Muchachos ! me quiero matar con lo que me paso !! me sentia como ese tipo que presentoo windows 98 y le salto la pantalla azul !!!...resulta que estaba con un amigo de la facu haciendo unos trabajos en linux (mientras que mi ubuntu descargaba las actus)..ejercicio va, ejercicio viene..floreaba a linux,comentandole un poco del lujo que es tenerlo y sus ventajas con respecto a windous xD...cuestion, que cuando temrina de actualizar reinicio el sistema...y ahi "..la devacle total!..un conjunto de hechos bochornosos" como decian en deportes en el recuerdo...al reiniciar me decia algo de que habia un error en la configuracion del xorg y en los controladores de nvidia...y de ahi me tira  ala terminal y no puedo ingresar a ubuntu en modo grafico =S.Se que me pueden ayudar jeje..asique sere paciente.Un saludo.

Si queres mostrarle a alguien la estabilidad de GNU/Linux, que no sea con Ubuntu. Es una buena distro pero lamentablemente en algunas cosas se parece demasiado a Windows.

---

### Post by ramiro_md on 2008-07-03
GRacias gente, pero  desisntale hh hace rato, disculpne me colgue con este thread xD. Voy a seguir trabajando con Gutsy x el momento...sigueindo los consejos de mi viejo (si anda,no lo cambies)..Gracias x tdoo, para la proxima ya se donde sacar posibles soluciones =)

---

