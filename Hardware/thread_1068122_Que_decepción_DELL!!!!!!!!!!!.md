---
title: "Que decepción DELL!!!!!!!!!!!"
date: 2009-02-12
forum: Hardware
---

### Post by gustmarti on 2009-02-12
Hola gente, acabo de cambiar mi vieja compu por una notebook Dell Studio 1535 que mandé a traer de EEUU, y la pedí con Ubuntu con la ilusión de que no tendría que andar posteando mis dudas o pedidos de socorro. PERO NO. Le quiese particionar el disco de la manera que me gusta y cuando reinstalé (obviamente con el DVD que ellos mandaron) tuve los problemas que cualquier hijo del vecino. Principalmente de webcam y micrófono.
Entonces agradecerá su colaboración en solucionar los siguientes problemas:

1. No puedo usar el Skype. Cuando pongo "llamar" me tira: "problemas con la reproducción de audio".

2. Los micrófonos incorporados no se si andan, porque siempre q traté de grabar algún sonido no pude, no se si fue ignorancia o que no andaban.

3. Cuando trato de sacar una foto con el Cheese, todo el escritorio se pone en blanco, tengo que pasar a otro escritorio y matar el proceso en el monitor del sistema para recuperar el escritorio colgado. Y cuando trato de filmar, los cuadros que graba son muy, pero muy lentos.
Hasta ahí lo esencial

4. No se como configurar los botones multimedia para reproducir musica con el Amarok II y con el Totem.

5. La pc traía un set multimedia para utilizar sin arrancar el SO. En Dell lo llaman DVD Pack. La cuestión es que cuando lo quise usar pasó que en principio arranca pero a los 5 segundos el Grub se superpone sobre escribiendo todo lo que hay en la pantalla y arranca el SO. ¿Alguna punta?

Desde ya agrazeco todos los consejos y ayudas posibles.
Y les digo ¡QUE FLOJO DELL!!!!

---

### Post by AliTabuger7 on 2009-02-12
The microphone issue may be easily resolved by going to:
System > Preferences > Sound
then changing the sound capture dropdown and testing it until it works.

Multimedia buttons can be configured through:
System > Preferences > Keyboard Shortcuts

Click the action that you wish to set, then press the button on your keyboard that you want to perform the action.

The last problem has to do with usplash or the quiet option in grub, but I don't know grub very well.

SPAINISH:
El micrófono problema puede ser fácilmente resuelto, vaya a:
Sistema> Preferencias> Sonido
a continuación, cambiar el menú desplegable de captura de sonido y el ensayo hasta que funcione.

Multimedia botones se pueden configurar a través de:
Sistema> Preferencias> Atajos de teclado

Haga clic en la acción que desea establecer, a continuación, pulse el botón en el teclado que desea realizar la acción.

El último problema tiene que ver con usplash y la tranquila opción en grub, pero no sé muy bien de grub.

---

### Post by marianom on 2009-02-12
> **gustmarti said:**
> Hola gente, acabo de cambiar mi vieja compu por una notebook Dell Studio 1535 que mandé a traer de EEUU, y la pedí con Ubuntu con la ilusión de que no tendría que andar posteando mis dudas o pedidos de socorro. PERO NO. Le quiese particionar el disco de la manera que me gusta y cuando reinstalé (obviamente con el DVD que ellos mandaron) tuve los problemas que cualquier hijo del vecino. Principalmente de webcam y micrófono.

¿Cuantos paquetes hay en el repositorio de Ubuntu? ¿18000? No podes esperar que Dell (y por el caso ningún otro vendedor) pruebe todas las aplicaciones para asegurarse que anden ok. Fuera de las aplicaciones que vienen por defecto en el LiveCD estimo que no se hacen responsables por nada más y -como vos decís- sos como todo hijo de vecino.

> **gustmarti said:**
> 
1. No puedo usar el Skype. Cuando pongo "llamar" me tira: "problemas con la reproducción de audio".

Skype no es un paquete que venga por defecto en una instalación de Ubuntu y ni siquiera es software libre, definitivamente no está probado como soft. standard así que no es ilogico pensar que tengas problemas. Anyway, anda a Options en Skype, Sound Devices y allí cambia lo que trae por defecto a "HDA Intel" para las tres opciones desplegables. Yo tenía el mismo problema y con eso lo arreglé.

> **gustmarti said:**
> 
2. Los micrófonos incorporados no se si andan, porque siempre q traté de grabar algún sonido no pude, no se si fue ignorancia o que no andaban.

¿Qué programa por ejemplo usaste? (Sorry, no sabía que la máquina traía microfono incorporado). 

> **gustmarti said:**
> 
3. Cuando trato de sacar una foto con el Cheese, todo el escritorio se pone en blanco, tengo que pasar a otro escritorio y matar el proceso en el monitor del sistema para recuperar el escritorio colgado. Y cuando trato de filmar, los cuadros que graba son muy, pero muy lentos.
Hasta ahí lo esencial


Tengo XPS 1330 con II: instalé Cheese para ver si me pasaba (es la primera vez que escucho de tal programa) y funcionó out of the box (más abajo les dejo un regalito para comprobarlo). ¿Andará en II pero no en HH? ¿Será algo que instalaste en tu máquina y te complica la vida? Sugiero que busques un poco para ver que aparece con "ubuntu hardy cheese xps" y nos cuentes si surje algo interesante para que te ayudemos.

> **gustmarti said:**
> 
4. No se como configurar los botones multimedia para reproducir musica con el Amarok II y con el Totem.


Lo dicho: para gnome el reproductor por defecto es Rhythmbox y ese tiene todas las teclas funcionando. Si querés usar Amarok -no me parece que sea delirado lo tuyo, es un buen programa- lo más simple sería configurar las hotkeys desde el propio Amarok el cual te provee tal posibilidad (sorry no lo tengo instalado como para darte el hint justo pero seguro los amaroktalibanes andan por aca y en seguida nos arrojaran luz). Aún así no creo que te funcione tan simple (si en vez de Ubuntu, tuvieras Kubuntu tenés un programa que se encarga de las configuraciones globales del sistema pero en Gnome no para Amarok). Lo más ingenioso que se me ocurre es buscar algunos de esos programas que te indican cual es la tecla que estás presionando (en el código de la notebook) y te permiten mapearla con la acción que quieras: en gnome tenés tal menu en System-Preferences-Keyboard Shortcuts pero debo reconocer que no es completo y "creo" que no te solucionará el problema con Amarok. Programas más completos son crikey! o Hotkeys. 

> **gustmarti said:**
> 
5. La pc traía un set multimedia para utilizar sin arrancar el SO. En Dell lo llaman DVD Pack. La cuestión es que cuando lo quise usar pasó que en principio arranca pero a los 5 segundos el Grub se superpone sobre escribiendo todo lo que hay en la pantalla y arranca el SO. ¿Alguna punta?


Ni idea con este tema, no me di cuenta que existía tal DVD cuando recibí mi máquina. ¿Capaz que es solo para windows?

---

### Post by sergiom99 on 2009-02-12
en kubuntu 7.10 yo hice andar las teclas multimedia de mi laptop instalando kmilo o keytouch. despues de la 8.04 andan OOB.
Por otro lado recien buscando en synaptic vi un paquete 'i8kutils' que dice que es para manejar las funciones adicionales de las laptop Inspiron y Latitud. Tal vez te sirva.

---

### Post by marianom on 2009-02-13
> **gustmarti said:**
> 
3. Cuando trato de sacar una foto con el Cheese, todo el escritorio se pone en blanco, tengo que pasar a otro escritorio y matar el proceso en el monitor del sistema para recuperar el escritorio colgado. Y cuando trato de filmar, los cuadros que graba son muy, pero muy lentos.


Si te reconozco el tema de grabar video con Cheese, es muy lento y la verdad no parece usable para hacer algo.

---

### Post by gustmarti on 2009-02-14
Gracias a todos, voy a probar las soluciones propuestas y después les digo!!!!!

---

