---
title: "Como manejar el ancho de pantalla?"
date: 2008-11-08
forum: Hardware
---

### Post by EDGAR MORENO on 2008-11-08
con las nuevas panatallas veo las fotos con un ancho que no es normal , aguna o algun amiga o amigo , puede darme por favor,luces para corregir esta "anchura" de imagen 

saludos

---

### Post by santiagoward2000 on 2008-11-08
Hola Edgar!
Una pregunta: ¿con fotos te referís a las que ponés como wallpaper en tu esctritorio o a cualquier foto que quieras ver con algún programa?

---

### Post by EDGAR MORENO on 2008-11-10
> **santiagoward2000 said:**
> Hola Edgar!
Una pregunta: ¿con fotos te referís a las que ponés como wallpaper en tu esctritorio o a cualquier foto que quieras ver con algún programa?

ESTIMADO SANTIAGO, AMIGO Y COMPAÑERO DE FORO EN UBUNTU ,me presento ante vos,como un artista que dibujas caricaturas, esto con el fin de que tal ves me entiendas , el porque de mi problema ,a veces me encargan caricaturas por internet , antes cuando tenia una pantalla  de 20 centimetros de alto por 27 centimetros de largo (pantallas de la anterior tecnologia)   , veia las imagenes tal cual, es decir con las proporciones reales , pero ahora , tengo una pantalla plana de 25 por 41  centimetros  y veo las figuras que se estiran a lo ancho , no se que pantalla tenes , pero si son de las actuales , mira mis dibujos, asi tambien distorcionados a lo ancho , te mando el vinculo de mi blog [http://caricaturasedgar.blogspot.com/](http://caricaturasedgar.blogspot.com/) , si tu pantalla , es de las antiguas , entonces la veras como en realidad son , pero si la tenes de las de ahora , las veras "anchadas" (ese termino parece que no existia , pero lo estamos creando a raiz de este problema ), , bueno lo cierto es si   alguien me manda una foto , ahora la veria distorcionada a lo ancho y por lo tanto , no podria dibujarlo tal como es en la realidad , yo soy flaco y me veo gordo je je je je , bueno amigo espero que me entiendas el problema para poder dibujar a mis amigas y amigos , que solicitan mi arte y verlos tal cual son , cuando abro sus fotos 

gracias por tu respuesta y atencion 

saludos atentos 

edgar

---

### Post by santiagoward2000 on 2008-11-10
Me acabo de meter en tu blog. Primero: ¡QUE BUENAS QUE ESTAN LAS CARICATURAS! :)
Sobre el problema, acá en mi laptop (con widescreen) no parecen deformadas. ¿Cambiaste la pantalla en una pc con Ubuntu ya instalado? Tal vez tengas que reconfigurar el xorg. Fijate si este thread te sirve:
[http://ubuntuforums.org/showthread.php?t=959311&highlight=widescreen]("http://ubuntuforums.org/showthread.php?t=959311&highlight=widescreen")
Saludos!

---

### Post by sajnox on 2008-11-10
Me parece que el problema es que tiene mal seteada la configuracion del monitor, para poder darte una mano necesitamos que hagas lo siguiente

1) Pasanos tu marca y modelo de monitor

2) Para mi que te detecto mal el maximo de resolucion que tu monitor acepta, hace lo siguiente, anda a: Sistema > Preferencias > Resolucion de la Pantalla y en resolucion elegi los valores mas altos que figuren.

3) Si eso no lo modifica tenes que hacer lo siguiente 

a) apretas ctrl + alt + f1 (con esto te vas a una terminal de comando, anota lo que sigue por que por un ratito apagamos el entorno grafico)

Entonces, apretas ctrl + alt +f1 te pide tu usuario y tu contraseña (cuando ingresas la contraseña en la pantalla no ves que nada pase, ni circulitos, ni asteriscos, nada. No te preocupes es asi.

b) Una vez logueado haces lo siguiente.
```

sudo /etc/init.d/gdm stop

sudo dpkg-reconfigure -phigh xserver-xorg

startx
```

Deberia arrancar de vuelta con la maxima resolucion que soporte el monitor y chau tu problema de fotos deformadas.

Saludos

---

### Post by EDGAR MORENO on 2008-11-12
gracias por las respuestas y por los comentarios sobre los dibujos , je je je ( cuando quieran uno sera un placer dibujarlos , identifiquense como amigos de ubuntu en el foro, recuerdoles  que estos dibujos son de cortesia) 
amigas y amigos la pantalla que tengo tiene un logo NOC, esa es la marca , atraz tambien tiene NOC, lcd monitor ,Envision peripherals, inc el tamaño de la pantalla  es de 25.5 de alto por 41 centimetros de largo, segun creo que son de 17 pulgadas(no manejo muy bien esta idea)

bueno tratare de ver que puedo hacer con lo que me dicen , me preocupa hacer algo que no pueda arreglar luego , dada mi nula  educacion en programacion , este tema y todas las palabras tecnicas , son nuevas para mi , asi que de nuevo les pido mis excusas, si de primera, no entiendo muy bien lo que uds , gentilmente me tratan de explicar 

saludos

---

### Post by sajnox on 2008-11-12
Proba arreglarlo con lo que te pasamos, sino sale...

Te podes dar una vuelta por aca [0]

[0] [http://ubuntuforums.org/showthread.php?t=970522](http://ubuntuforums.org/showthread.php?t=970522)

---

### Post by EDGAR MORENO on 2008-11-13
amigo te mande la marca del monitor es noc y todavia no he podido solucionar la deformacion , me explica alguien. (fuera del foro)  que debo tener el programa que configura la targeta de video y este se baja de internet, creo que debo abrir el computador para ver que marca es ...

---

### Post by sajnox on 2008-11-13
Si podes date una vuelta el sabado o el domingo por la tribu y ahi entre todos seguro lo arreglamos

Saludos

---

