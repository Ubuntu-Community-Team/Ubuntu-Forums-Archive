---
title: "Las PCs &quot;del gobierno&quot; - [Wifi San Luis]"
date: 2009-05-19
forum: Hardware
---

### Post by Elzigzag on 2009-05-19
Les escribo desde San Luis. Seguramente ya deben estar al tanto de los planes para renovación tecnológica que hay por aquí. La cuestión es que me compré una portátil Exo Superior [http://www.exo.com.ar/sanluis/](http://www.exo.com.ar/sanluis/) e intenté correr el LiveCD de Ubuntu, y si bien aparece una pantalla donde dice algo así como PROBAR SIN ALTERAR NADA (que es la opción que quería probar por ahora) nunca arrancó. Probé con el Live CD de Xubuntu y el mismo resultado. Probé instalando Ubuntu dentro de Windows con Wubi. Y si bien se "instala" (o al menos al arrancar me da opción a arrancar con Ubuntu 9.04 o Microsoft Windows Vista) si elijo Ubuntu no pasa nada. Me ha resultado un poco decepcionante. No tengo conocimientos suficientes como para hacer tweaks y cosas de ese estilo (de hecho aspiro a tener un Sistema Operativo BIEN GRÁFICO, nada de línea de comando, soy contador, no pretendo ser analista de sistema ni técnico, sólo un triste usuario de una interfaz gráfica bonita). 
¿Alguien de San Luis ha tenido éxito instalando Ubuntu 9.04, Xubuntu o Debian en una notebook de esas características?
**                    EXO NOTEBOOK SUPERIOR**

 ** Potente Core 2 Duo! **


 
[LIST][SIZE=2] 	           
[*] Intel Core 2 Duo T5750, 2MB de Memoria Cache 	        [/SIZE][SIZE=2] 	           
[*] Memoria 2 Gigabytes DDR2 	        [/SIZE][SIZE=2] 	           
[*] Video Mirage 3 hasta 256 MB 	        [/SIZE][SIZE=2] 	           
[*] Pantalla WideScreen 14,1” Brillante 	        [/SIZE][SIZE=2] 	           
[*] Disco Rígido 250GB SATA  	        [/SIZE][SIZE=2] 	           
[*] Grabadora de DVD/CD Dual Layer 	        [/SIZE][SIZE=2] 	           
[*] Lector de memorias 	        [/SIZE][SIZE=2] 	           
[*] Wi-Fi Wireless 802.11b/g 	        [/SIZE][SIZE=2] 	           
[*] Cámara Webcam 1.3 M Pixels 30fps 	        [/SIZE][SIZE=2] 	           
[*] Windows Vista Home Premium Original  	        [/SIZE][SIZE=2] 	           
[*] Antivirus ESET NOD32 	        [/SIZE][SIZE=2] 	           
[*] Google Earth 	        [/SIZE][SIZE=2] 	           
[*] Microsoft® Office Home & Student 	        [/SIZE]
[/LIST]

---

### Post by luks911 on 2009-05-19
Bienvenido.
No tengo experiencia con esa máquina en particular, pero probá lo siguiente: en la pantalla inicial del LiveCD, antes de elegir la opción Probar Ubuntu sin alterar el Equipo, presioná F4 y elegí "modo gráfico seguro".

---

### Post by guillermolisi on 2009-05-19
Las placas Mirage 3 son de SIS y hay varios modelos para esa linea de placas.

Entre los variados modelos pude ver una constante luego de buscar opiniones en el foro (internacional): Hasta fines del 2008 y ya con la version 8.10 de Ubuntu, las placas de video SIS son un dolor de cabeza similar a plas placas VIA. Algunos se quejaron de que ni siquiera funcionaba bien ni con el driver Vesa.

Ni hablar de aceleracion 3D ....

Por si les interesa, en Ingles, uno de los threads que lei:

[http://ubuntuforums.org/showthread.php?t=958967](http://ubuntuforums.org/showthread.php?t=958967)

---

### Post by Hei Ku on 2009-05-19
Es una SiS. Basicamente, es lo peor para hacer andar un Linux. Proba arrancarla en modo grafico seguro, y despues podemos ver si te deja instalar este driver que esta aca.
[http://ubuntuforums.org/showpost.php?p=6983046&postcount=119](http://ubuntuforums.org/showpost.php?p=6983046&postcount=119)

Como maximo vas a llegar a tener aceleracion 2D. Lo lamento, pero no te puedo dar mas esperanzas que esto.

---

### Post by z37a on 2009-05-20
No se supone que SIS se retiro del mercado hace como un año?????

---

### Post by juancarlospaco on 2009-05-20
*No hay algun usuario por San Luis que haga la migration ?*
Yo te lo instalaria pero estoy en BsAs, 
el problema es la Placa de Video, es medio mala, el fabricante ya se ha retirado.

---

### Post by Elzigzag on 2009-05-20
Primero que todo => Gracias por responderme!
Me habían dicho que las comunidades ubunteras/linuxeras eran muy solidarias para responder y realmente es así. Sobrepasaron mis expectativas.

Segundo => Lo penoso es que me pinta una desilusión... pero bueno. Supongo que eso explica la dificultad para masificarse de Ubuntu en particular y Linux en general.

A pesar de eso hoy a la noche apenas llegue a casa pruebo los consejos que me dieron y luego les comento. Pero ya no creo que sea buena idea la de convertir mi portátil a Ubuntu 9.04. Me fastidia porque ya me había hecho la cabeza de que por fin podría tener una PC con Linux, cosa que obviamente no puedo hacer con mi PC de oficina por la sencilla razón de que ni SIAp (aplicativos tributarios) ni HOLISTOR (software de gestión contable) corren bajo Linux. Entonces me había comprado el portátil con la idea de poder instalarle Ubuntu e ir aprendiendo de a poco sin afectar (al menos temporariamente) el equipo que dedico al trabajo.

Bué, les cuento más luego cómo me fue con el F4 + modo gráfico seguro.

MIL GRACIAS!!! Si hay algún geek de Villa Mercedes (San Luis) que pueda ayudarme que me deje un mensaje en el foro.

---

### Post by Hei Ku on 2009-05-20
> **Elzigzag said:**
> 
Segundo => Lo penoso es que me pinta una desilusión... pero bueno. Supongo que eso explica la dificultad para masificarse de Ubuntu en particular y Linux en general.


Linux soporta mas hardware de lo que soportan todas las versiones de windows juntas. Sin embargo, para casos particulares, Windows tiene mejor soporte. Asimismo, te puedo nombrar una innumerable cantidad de hardware donde win no corre y Linux sí. Comenzando por todas las netbooks con chips ARM.

Aclaro esto para no empezar una discusion sobre "por que Linux no se hace masivo"

---

### Post by pablo.s on 2009-05-20
> **Hei Ku said:**
>  Comenzando por todas las netbooks con chips ARM.

?

---

### Post by Elzigzag on 2009-05-20
Amigos, de ninguna manera quise ofender a nadie.
Sólo que de todo el hardware que puedo conseguir donde vivo (Villa Mercedes) **tuve el mal ***** de elegir justo uno que no está bien soportado por Linux**. Y lo peor de todo es que esas notebooks son las únicas  (y de hecho todas las notebooks que se venden dentro del plan San Luis Digital [http://www.exo.com.ar/sanluis/](http://www.exo.com.ar/sanluis/) tienen esa configuración).

No lo tomes a mal, pero me da bronca haberme ilusionado con probar Ubuntu y ahora me encuentro con que no es tan sencillo.

A ver si me entendés, tengo en mi PC de oficina un Ubuntu "embutido" en Windows Vista con Wubi, y es como que está ahí, escondido. Y cuando me compré la notebook, lo primero que me dije es "VA A OSTENTAR ORGULLOSAMENTE LINUX, POR FIN VOY A PODER HACER DE UBUNTU SU ÚNICO SISTEMA OPERATIVO" y fantaseando cosas así... Pero resultó que apenas empezaba ya me topé con un problema (hasta ahora) insalvable... por eso me decepciono... quizás me hice muchas fantasías.

No me hagas caso.

---

### Post by guillermolisi on 2009-05-20
> **Elzigzag said:**
> Primero que todo => Gracias por responderme!
Me habían dicho que las comunidades ubunteras/linuxeras eran muy solidarias para responder y realmente es así. Sobrepasaron mis expectativas.

Segundo => Lo penoso es que me pinta una desilusión... pero bueno. Supongo que eso explica la dificultad para masificarse de Ubuntu en particular y Linux en general.

A pesar de eso hoy a la noche apenas llegue a casa pruebo los consejos que me dieron y luego les comento. Pero ya no creo que sea buena idea la de convertir mi portátil a Ubuntu 9.04. Me fastidia porque ya me había hecho la cabeza de que por fin podría tener una PC con Linux, cosa que obviamente no puedo hacer con mi PC de oficina por la sencilla razón de que ni SIAp (aplicativos tributarios) ni HOLISTOR (software de gestión contable) corren bajo Linux. Entonces me había comprado el portátil con la idea de poder instalarle Ubuntu e ir aprendiendo de a poco sin afectar (al menos temporariamente) el equipo que dedico al trabajo.

Bué, les cuento más luego cómo me fue con el F4 + modo gráfico seguro.

MIL GRACIAS!!! Si hay algún geek de Villa Mercedes (San Luis) que pueda ayudarme que me deje un mensaje en el foro.
Se que hubo experiencias con cierto grado de exito corriendo SIAP con Wine (Wine genera las condiciones operativas para que una aplicacion Windows corra en Linux sin que se de cuenta que no esta en Windows).

Habria que probar ese sistema contable tambien con Wine, a ver que pasa.

Ademas, si tu PC de oficina esta adecuadamente dimensionada, podrias correr WinXP virtualizado y ahi dentro toda la parafernalia de software que necesites usar en forma nativa bajo Windows, tal como hago en mi trabajo cuando no hay mas remedio que ese.

---

### Post by Elzigzag on 2009-05-21
> **guillermolisi said:**
> ..... podrias correr WinXP virtualizado y ahi dentro toda la parafernalia de software que necesites usar en forma nativa bajo Windows, tal como hago en mi trabajo cuando no hay mas remedio que ese.

Interesante opción! :D No quiero que se desvirtúe la finalidad de este thread pero quizás te escriba en privado para pedirte que me orientes en esa posibilidad. La PC de oficina es una Intel Core 2 Quad 2,4 GHz 2Gb RAM con Windows Vista Home Premium. ¿La cosa sería instalarle Ubuntu y luego hacer correr un Windows XP dentro de Ubuntu? Me interesa, me interesa.

---

### Post by guillermolisi on 2009-05-21
> **Elzigzag said:**
> Interesante opción! :D No quiero que se desvirtúe la finalidad de este thread pero quizás te escriba en privado para pedirte que me orientes en esa posibilidad. La PC de oficina es una Intel Core 2 Quad 2,4 GHz 2Gb RAM con Windows Vista Home Premium. ¿La cosa sería instalarle Ubuntu y luego hacer correr un Windows XP dentro de Ubuntu? Me interesa, me interesa.
Tal como decis uso en mi casa y en la oficina. Ubuntu como host y XP virtualizado que funciona mejor que en modo "real". Los dos al mismo tiempo en maquinas con Dual Core (vos tenes mejor procesador por lo que comentas) y 2Gb RAM.
Eso si, por mas que este virtualizado dentro de Ubuntu, tenes que ponerle antivirus, anti spyware, defragmentar el disco y todas las tareas de mantenimiento necesarias para que XP funcione bien con el paso del tiempo.

En el foro encontraras mucha informacion y si queres mas, date una vuelta por nuestro website [http://ubuntu-ar.org](http://ubuntu-ar.org). En la seccion Tutoriales podras ver muchas cosas interesantes y lo que escape a tus conocimientos lo aclaras aqui (en hilo especifico sobre el tema que se trate, asi algun otro que este buscando informacion puede identificar mensajes rapidamente por topico).

---

### Post by josecuervo86 on 2009-05-21
Coincido, Xp virtualizado anda mejor que nativo. Yo tengo un Core 2 duo y ni lo siente, asique con un Quad debe volar. Para virtualizar podes usar VirtulBox, que es el que uso yo (y creo que la mayoria)

---

### Post by Elzigzag on 2009-05-22
No sé si se habrán dado cuenta que pasamos de Ubuntu-en-mi-notebook a Ubuntu-en-mi-desktop.... **La ilusión es tener Ubuntu!** Tiene un qué-sé-yo que me atrapa.
Gracias por la ayuda!

Además me han dado una buena idea para correr SIAp (el entorno de aplicativos para liquidar impuestos) que tengo un montón de problemas bajo Vista.... problemas que bajo XP no los tenía. A lo mejor corriendo el SIAp en un XP virtualizado ande mejor que dentro de un Vista nativo.

(Está permitido reírse de mi uso de las palabras "virtualizado" y "nativo".... es la primera vez que lo hago y me siento raro usando esas palabras :p:p:p)

---

### Post by z37a on 2009-05-22
> **josecuervo86 said:**
> Coincido, Xp virtualizado anda mejor que nativo. Yo tengo un Core 2 duo y ni lo siente, asique con un Quad debe volar. Para virtualizar podes usar VirtulBox, que es el que uso yo (y creo que la mayoria)

Coincido, yo hasta flashie mi telefono de esta manera, el virtualbox anda muy bien, lastima que el OSE no funcione tambien como el otro, pero bueno es cosa de tiempo seguro.

PD: Tenes 2 VirtualBox ambos gratis, peor uno es abierto(OSE) y el otro no, ambos soportados por SUN y disponibles los debs para todos los ubuntu,  hasta hay un repositorio de sun para ubuntu!!!

PD2: Antes de flashear el tel(solo pro que lo puse como ejemplo!!!) pregunta bien con el tema de lo virtual, yo casi suicido un N95!!!!! Jajajaja

---

### Post by Elzigzag on 2009-11-05
Bueno, luego de un largo tiempo de ausencia del foro, leyendo cuando me cruzaba con noticias acerca de los drivers SiS Mirage 3 y toda su parentela, finalmente conseguí unos que anden lindo, al menos la apariencia del monitor es apropiada para la notebook.
Para instalar agarré el Ubuntu 9.19 Karmic Koala en F6 Otras Opciones le tildé el acpi=off, el noapic, el nolapic y el edd=on (que no tengo la más mínima idea de qué se tratan, y es muy probable que la mayoría de usuarios que Ubuntu quiere ganar, tampoco....) Ahora sí por fin pude instalarlo con el instalador gráfico, sin ningún problema. Luego navegué hasta el [sitio de Nacho Larrateguy]("http://nacho.larrateguy.com.ar/2009/07/11/drivers-de-sis-771671-para-xorg-1-6-mandriva-2009-1-ubuntu-jaunty-9-04/comment-page-1/") e instalé el driver que está apenas comienza la página. Tenía que reiniciar el servidor X, pero como no sabía cuál era, sencillamente reinicié la notebook, y todo pipí-cucú. Anda fenomenal, estoy feliz de la vida. Bueno, todavía no tengo 3D, pero al menos avancé algo. Ojalá le ayude a alguien especialmente si vive en San Luis.

---

### Post by lean-mini on 2009-11-05
AMigo, sólo es cuestión de probar para aquellos que no tenemos tanto conocimiento. Yo tengo una hp 2133 con VIA, y si bien no tengo 3D, anda muy bien. Siempre compito con la de mi suegra que tiene XP, y hasta tengo mejor conexión wifi (increible!).
Saludos
LEan

---

