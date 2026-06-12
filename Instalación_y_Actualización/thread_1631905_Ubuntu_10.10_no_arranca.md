---
title: "Ubuntu 10.10 no arranca"
date: 2010-11-27
forum: Instalación y Actualización
---

### Post by Diegox.Alboo on 2010-11-27
Buenos días, ayer instalé KDE para probar sus funciones, sus gráficos, etc, pero como no me gustó, decidí desintalarlo. Durante la desinstalación, recuerdo, apareció un mensaje que decía algo de: "Detener KDM", la opción predeterminada era no, y yo sin haber leído el mensaje completo cambié a si y apreté enter, en ese momento el PC se reinició y desde ahí que no puedo iniciar. Desearía que me ayudaran a arreglar el problema, ya que no quiero formatear perdiendo todos mis archivos.

Gracias de Antemano, Diego.

---

### Post by moreback on 2010-11-27
> **Diegox.Alboo said:**
> .. en ese momento el PC se reinició y desde ahí que no puedo iniciar. 

A ver... ¿no prende el pc? ¿se queda pegado en la bios? ¿no carga el kernel? ¿tira un error que no quieres mostrarnos porque supones que somos videntes y podemos ver tu pantalla desde acá? :-P

Por favor, cuando reportes algún problema date el tiempo de explicar con mayores detalles qué es lo que sucede, adjuntar algún pantallazo si es posible o los mensajes de error.

Saludos..

---

### Post by Diegox.Alboo on 2010-11-27
> **moreback said:**
> A ver... ¿no prende el pc? ¿se queda pegado en la bios? ¿no carga el kernel? ¿tira un error que no quieres mostrarnos porque supones que somos videntes y podemos ver tu pantalla desde acá? :-P

Por favor, cuando reportes algún problema date el tiempo de explicar con mayores detalles qué es lo que sucede, adjuntar algún pantallazo si es posible o los mensajes de error.

Saludos..

Eh... Simpático tu aporte del principio, pero bueh...  :roll:

Siguiendo con el tema, si te digo que el PC no inicia, ¿como quieres que adjunte pantallazos?, Simplemente cuando prendo la computadora aparece el mensaje de la bios y hasta ahí todo normal, después la pantalla queda en negro y nada más.-

---

### Post by Oscaroto on 2010-11-28
Hola Diego:

A pesar de que pueda sonar pesado el modo de preguntarte cosas para poder ayudarte, en cierta forma es verdad las cosas que te preguntaron. Para poder ayudarte de verdad, debes entregar la mayor  información posible de tu problema, los detalles, etc. Para así poder llegar a conclusiones más acertadas.

¿Tienes solo linux instalado en tu PC? Si es así, puedes instalar el ubuntu otra vez y no formatear la partición que haces para la carpeta HOME del sistema, no se pierde nada. Si tienes windows y ubuntu isntalado, puede que sea  un problema del GRUB, pero lo dudo. Lo otro, lo cual nunca lo he hecho, por lo que tendrás que buscar un tutorial por ahí en google, es intentar entrar sin modo gráfico y ver que pasa. O también entrar con  el CD de instalación al Sistema de prueba y ver si puedes arreglar desde ahí el asunto.

Nos cuentas como te fue, saludos.

---

### Post by moreback on 2010-11-28
> **Diegox.Alboo said:**
> ... Simplemente cuando prendo la computadora aparece el mensaje de la bios y hasta ahí todo normal, después la pantalla queda en negro y nada más.-

¿Viste que no habías dicho todo?

Con eso que dices parece ser algo del GRUB que está fallando. O no te encuentra la configuración, no detecta tu disco o intenta cambiar el modo de video y no puede.

También podría ser que está cargando (no nos has dicho que tipo de instalación tienes en tu pc) el grub pero sin mostrar el menú y falla al cargar el kernel y demases.

Hasta ahí llega mi bola de cristal.

Saludos!

---

### Post by RafaelG on 2010-12-08
> **Diegox.Alboo said:**
> Eh... Simpático tu aporte del principio, pero bueh...  :roll:

Siguiendo con el tema, si te digo que el PC no inicia, ¿como quieres que adjunte pantallazos?, Simplemente cuando prendo la computadora aparece el mensaje de la bios y hasta ahí todo normal, después la pantalla queda en negro y nada más.-

[SIZE=2]
Diego,

Favor tener en cuenta el codigo de conducta al momento de ingresar Post y comentarios en el Forums[/SIZE]

[COLOR=Navy]**Codigo de conducta Link oficial de Ubuntu: ****[http://www.ubuntu.com/community/conduct](http://www.ubuntu.com/community/conduct)**

*""Ser respetuosos."" La comunidad Ubuntu y sus miembros se tratan  unos a otros con respeto. Todo el mundo puede hacer una valiosa *[/COLOR]  [COLOR=Navy][I]contribución  a Ubuntu. Puede que no siempre están de acuerdo, pero los             desacuerdos no es excusa para el mal comportamiento y los malos modales.  Todos podemos experimentar algo de frustración de vez en cuando, pero  no podemos permitir que la frustración se convierta en un ataque  personal. Es importante recordar que una comunidad donde la gente se  sienta incómoda o amenazada no es productiva. Esperamos que los miembros de la comunidad Ubuntu sean respetuosos cuando se tratan con otros  contribuyentes, así como con personas fuera del proyecto Ubuntu y con  los usuarios de Ubuntu.
[/I]
[B]Codigo de Conducta del Foro Link Oficial Ubuntu: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)
[/B][I]
"El propósito de los foros de Ubuntu es proporcionar apoyo para Ubuntu.  También queremos que se trate de un lugar donde la comunidad puede  desarrollar y podamos disfrutar de su mutua compañía. Para  ello, nos  esforzamos por mantener una atmósfera que puede ser  disfrutado por  todos, y pedimos a todos los miembros de la comunidad a  ser respetuosos  en todo momento. Esto significa que por favor, utilice la etiqueta y la  cortesía. Tratar a la gente con amabilidad, gentileza y respeto. Si lo  hace, el resto del código de conducta no necesitará más que una mención  superficial."[/I][/COLOR]  [COLOR=Navy]
[/COLOR] 
[SIZE=2]Por todo lo explicado anteriormente en el codigo de conducta, se  agradeceria que para poder optimizar  las respuestas de los usuarios  unos a otros, mantener la buena convivencia y continuar con el normal  funcionamiento del foro es necesario utilizar este codigo de  conducta que es fundamental he importante para poder ingresar post y  comentarios en el mismo. Me despido de ustedes agradeciendo su  comprension en todo lo explicado anteriormente de mi parte.

Saludos cordiales![/SIZE]

---

### Post by RafaelG on 2010-12-13
Diegox.Alboo,

En el hipotetico caso que tu Grub este fallando y para no perder la informacion que tenias entonces puedes probar recuperar el Grub desde un Live CD, dejo link de How to recuperar Grub.

[http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB](http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB)

Saludos cordiales,

---

### Post by Oliver Perez on 2011-02-04
Hola, presento una urgencia de caracter urgente en cuanto al no poder ingresar al S.O. Ubuntu 10.10, encontré que la solución era realizar un ingreso al disco por medio de un Live CD pero la verdad sale el siguiente error:

DBus error org.gtk.Private.RemoteVolumeMonitor.Failed:An operation is already pending

Hasta ahi ya es preocupante el asunto, el problema continúa cuando me encuentro con este tema y de alguna forma veo que se puede solucionar por medio la siguiente guia : [http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB](http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB)

Terminal muestra lo siguiente

ubuntu@ubuntu:~$ sudo fdisk -l

Disco /dev/sda: 320.1 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0xa8637da4

Dispositivo Inicio    Comienzo      Fin      Bloques          Id    Sistema
/dev/sda1   *           1                 13054   104856223+    7     HPFS/NTFS
/dev/sda2           13055             38913   207712417+     f     W95 Ext'd (LBA)
/dev/sda5           13055             38913   207712386      7     HPFS/NTFS

Disco /dev/sdb: 320.1 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0xdda1d81a

Dispositivo Inicio    Comienzo      Fin            Bloques           Id    Sistema
/dev/sdb1               2                   38913       312560609+       f    W95 Ext'd (LBA)
/dev/sdb5               2                   25036       201093606       83    Linux
/dev/sdb6           25037               38913       111466971         7    HPFS/NTFS


pero viene lo duro ... me quedo en la siguiente operación:

sudo mount /dev/sdb5 /mnt
(aclarando que la partición de Ubuntu en el computador es sdb5)

Que puedo hacer, ya que necesito información de suma importancia para lo mas pronto y el S.O. no me responde de ninguna forma.

---

