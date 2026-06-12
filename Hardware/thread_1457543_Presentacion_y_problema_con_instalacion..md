---
title: "Presentacion y problema con instalacion."
date: 2010-04-18
forum: Hardware
---

### Post by Nu7shell on 2010-04-18
Bueno, 
Hace 4 dias aproximadamente que estoy con todo este tema de linux y  creo que voy avanzadando a pasos bastante acelerados. 
 Bueno no es la mejor manera de presentarse y tirar un problema de una pero es que ya no se que más hacer. 
 Bien primero, meto el CD y pongo Instalar Ubuntu, hasta ahí todo bien. Aparece el logo y al minuto la pantalla se pone de colores (exactamente una Paleta RGB) al segundo de eso se pone la pantalla negra, y después blanca. Así se queda el resto del tiempo, la paleta rgb, después la pantalla negra y después la pantalla blanca.
 Yo creo que debe que no me toma el monitor porque ubuntu sigue corriendo (apreto alt+f1 y funciona) 
 Ya he posteado esto en el foro de Ubuntu de españa (no conocia de éste foro antes) y nadie me ha respondido. 
 
Bueno, esto es todo por favor si alguien tiene alguna teoria o idea que la comparta..

 Un abrazo y desde ya gracias :)

PD.: No se donde va el thread así que no hay problema si lo mueven.

---

### Post by guillermolisi on 2010-04-18
Que motherboard y placa de video estas usando ?
Que version de Ubuntu es ?
La motherboard posee video integrado y tenes una segunda placa o es una notebook ?
Si es una notebook, marca y modelo, please.

---

### Post by Nu7shell on 2010-04-18
La version de ubuntu es la 9.10
La placa es MSI K9N6PGM-F/FI (MS-7309) con una GeForce 6150SE nForce 430 integrada.
Hace 3 meses que tengo la PC es un ordenador de mesa.
  
Epero que sirva. 
 Gracias

---

### Post by guillermolisi on 2010-04-18
Por lo que comentas pareceria que no encuentra una configuracion adecuada para tu monitor, por eso Ubuntu inicia pero no te puede mostrar el escritorio grafico.

Si esto que creo es asi, no queda otra que configurar el archivo /etc/X11/xorg.conf con las frecuencias de barrido horizontal y vertical de tu monitor, datos que obtenes o del manual o de Internet para la marca y modelo que se traten.

Tambien podemos intentar que se inicie con el driver Vesa y ver que pasa, tambien modificando el mismo archivo que mencione.

---

### Post by Nu7shell on 2010-04-18
Te comento que hace 4 días que estoy en linux y no tengo mucha idea. Sólo aprendí los comandos básicos. 

Acá dejo unos datos del monitor:

· Identificación del monitor	SAM0599
· Modelo	SyncMaster
· Frecuencia horizontal	30 - 81 KHz
· Frecuencia vertical	56 - 75 Hz
· Resolucion 1600x900

---

### Post by Nu7shell on 2010-04-23
Nadie tiene alguna idea ?

---

### Post by rojojuan on 2010-04-23
Mañana podés encontrar muchísima gente que te puede ayudar personalmente, en La Plata.
Visitá esta página:

[http://www.flisol.net/FLISOL2010/Argentina/La_Plata](http://www.flisol.net/FLISOL2010/Argentina/La_Plata)

---

### Post by guillermolisi on 2010-04-23
Para la prueba que sugiero hagas tendras que entrar en una consola/terminal, abrir con un editor de texto simple, tipo nano, un archivo con el nombre que indicare mas abajo, copiar y pegar por lo menos lo que te indico en este post.
```
sudo nano /etc/X11/xorg.conf
```

La seccion mas importante es esta y te deberia permitir iniciar la maquina con el driver generico Vesa. Si funciona despues podras instalarle y activarle el de nVidia:

```
Section "Device"
    Identifier    "Configured Video Device"
    Boardname    "VESA driver (generic)"
    Driver        "vesa"
    Screen    0
EndSection
```

Copias y pegas en ese archivo este bloque (sin las etiquetas de CODE), guardas los cambios y reinicia la maquina.
Si arranca con video es muy probable que la resolucion no sea la mas adecuada, pero lo importante es que Jockey se active y te permita instalar y activar algun driver de video nVidia para que luego te quede bien.

Te adjunto el /etc/X11/xorg.conf que usaba cuando no tenia nVidia con un monitor Samsung CRT.

---

### Post by Nu7shell on 2010-04-26
Guillermo, no me andubo para nada. Traté todo y no puedo. Voy a tratar de ir ahora el 15 al Flisol que se hace en la plata.
Grabé lo que me aparece en la pantalla para poder explicarlo mejor.

[http://www.youtube.com/watch_private?v=6-fnRsLtfq0&sharing_token=ort1R3KrpEH2lEBhNyREFQ](http://www.youtube.com/watch_private?v=6-fnRsLtfq0&sharing_token=ort1R3KrpEH2lEBhNyREFQ)

Yo estoy tan interesado en este problema no solo por el hecho de que no puedo instalarlo en mi propia pc sino que he visto que hay gente que tiene el mismo problema (en otros foros) y nadie les ha respondido.
Espero que sirva.

---

### Post by guillermolisi on 2010-04-26
No puedo ver el video porque me pide usuario y pass para Youtube y no tengo.

Una foto ?

---

### Post by Nu7shell on 2010-04-26
[HTML]<a href="http://s251.photobucket.com/albums/gg311/fedx_bass/?action=view&current=error.jpg" target="_blank"><img src="http://i251.photobucket.com/albums/gg311/fedx_bass/th_error.jpg" border="0" alt="error" ></a>[/HTML]

Después aparece se pone en negro, después en gris y después en blanco y de vuelta lo mismo.
 
Ahora estoy tratando de instalar la version alternate en modo texto.
Igualmente estaría bueno encontrarle una solucion.

---

### Post by guillermolisi on 2010-04-26
> **Nu7shell said:**
> [HTML]<a href="http://s251.photobucket.com/albums/gg311/fedx_bass/?action=view&current=error.jpg" target="_blank"><img src="http://i251.photobucket.com/albums/gg311/fedx_bass/th_error.jpg" border="0" alt="error" ></a>[/HTML]Después aparece se pone en negro, después en gris y después en blanco y de vuelta lo mismo.
 
Ahora estoy tratando de instalar la version alternate en modo texto.
Igualmente estaría bueno encontrarle una solucion.
No vi aun el grafico pero con esa placa solo hay que lograr que se inicie en mode de video seguro (Vesa) y despues te avisara que hay controladores propietarios para bajar e instalar. Uno de ellos sera sin duda el de la tarjeta de video nVidia.

Cuando instalas podes elegir el modo de video seguro con la tecla de funcion F6 (si no recuerdo mal).

---

### Post by Nu7shell on 2010-04-28
Bueno arranco dandote las gracias, Guille por la mano que me estás dando en este tema. En serio, lo aprecio.
Ahora pude instalar ubuntu desde el CD Alternate en modo Texto.
Hasta ahora bien.. por lo menos cuando edito el Xorg.conf queda guardado. Ahora el problema sigue.
  Es más.. cuando arranco ubuntu entra directamente todo a modo texto (pide el login en modo texto). Ya intenté apretar Alt+F7 y nada.. edité el xorg.conf file como vos me dijiste, Guille, pero no funciona.. calculo que tendré que bajar el driver de mi placa o editar el xorg.conf de otra manera.
Hasta ahora lo que intenté fue poner tal cual el xorg.conf que me mandaste y el anterior codigo.
Alguna idea ?

---

### Post by guillermolisi on 2010-04-28
Agregale el bloque que hace referencia al monitor y ponele las frecuencias de barrido del tuyo (para evitar que se queme o que bloquee la señal de video como proteccion). Si con driver Vesa no levanta para mi es porque las frecuencias que el X-server quiere usar para tu monitor y la resolucion que intenta estan fuera de rango, por eso no se "arma" el entorno grafico y siempre terminas en modo consola.

La otra alternativa es que instales por esta via el ultimo driver nVidia (creo que es el 185) disponible en los repositorios de Ubuntu (indicado como "restringido" o restricted porque poseen paquetes privativos). Para que funcione su instalacion tenes que tener habilitado esta clase de repositorio (Origenes de Software).

Tambien instalaria el paquete nvidia-settings, por las dudas funcione pero no logres caracteristicas de video aceptables con el driver nVidia.

---

### Post by Nu7shell on 2010-04-29
Bueno Guille, por fin, pude.
Gracias por el aguante, che. 
Instalé los drivers privativos de Nvidia y andubo joya.
 Un abrazo y gracias.

---

### Post by guillermolisi on 2010-04-30
> **Nu7shell said:**
> Bueno Guille, por fin, pude.
Gracias por el aguante, che. 
Instalé los drivers privativos de Nvidia y andubo joya.
 Un abrazo y gracias.
Excelente ! Ahora conta un poco como lo terminaste resolviendo asi queda para otros que pasen por la misma experiencia.

Que disfrutes.

---

### Post by Nu7shell on 2010-04-30
Bueno, el problema de lo que aparecía en la pantalla no pude saber que era.
 Lo único que hize fue descargar la version Alternate instalé en modo texto, busqué e instalé el driver de la placa y listo.
 
Para instalar el driver hice ésto.

1º Descargué el driver
 ```
sudo add-apt-repository ppa:nvidia-vpau/ppa 
```

2º Hice un backup del xorg.conf (no se para que xD)
 ```
 cd /etc/X11 
 sudo cp xorg.conf xorg.con.bak 
```

3ºActualicé la lista de fuentes
 ```
sudo apt-get install update
```

4º Instalé el driver
 ```
sudo apt-get install nvidia-190-modalises nvidia-glx-190 
```

5º Le pegué una reiniciada y listo.

Y bueno.. masomenos quedó.. ahora tengo otro problemita pero creo que lo voy a resolver llamando a Speedy.
Resulta que internet me anda super lento.. traté de poner la cuenta y la pass en la pestaña DSL pero no me la toma.. estuve buscando algo de info por ahí pero es media vieja.. así que voy a llamar y ver que onda.

---

### Post by guillermolisi on 2010-04-30
> **Nu7shell said:**
> Bueno, el problema de lo que aparecía en la pantalla no pude saber que era.
 Lo único que hize fue descargar la version Alternate instalé en modo texto, busqué e instalé el driver de la placa y listo.
 
Para instalar el driver hice ésto.

1º Descargué el driver
 ```
sudo add-apt-repository ppa:nvidia-vpau/ppa 
```
Aqui lo que hiciste fue incorporar un repositorio personal a tu lista de repositorios, no bajaste ningun driver en esta etapa
> 2º Hice un backup del xorg.conf (no se para que xD)
 ```
 cd /etc/X11 
 sudo cp xorg.conf xorg.con.bak 
``` Nunca esta de mas tener un backup, que te sobre no molesta, no tenerlo es un dolor de cabeza y muchisimo retrabajo 
> 3ºActualicé la lista de fuentes
 ```
sudo apt-get install update
```
Me parece que te sobra "install" en la linea
> 4º Instalé el driver
 ```
sudo apt-get install nvidia-190-modalises nvidia-glx-190 
```5º Le pegué una reiniciada y listo.

Y bueno.. masomenos quedó.. ahora tengo otro problemita pero creo que lo voy a resolver llamando a Speedy.
Resulta que internet me anda super lento.. traté de poner la cuenta y la pass en la pestaña DSL pero no me la toma.. estuve buscando algo de info por ahí pero es media vieja.. así que voy a llamar y ver que onda.
Suerte con esto !

---

### Post by rojojuan on 2010-04-30
Internet me funcionaba un poco lento y encontré que la norma ipv6 todavía no funciona aquí, Firefox pierde tiempo buscando.

Lo solucioné cambiando la configuración de Firefox así:


network.dns.disableIPv6;true

Tenés que colocar en la barra de direcciones about:config y luego buscar esa clave y modificarla

Espero te sirva

---

### Post by Nu7shell on 2010-04-30
> **rojojuan said:**
> Internet me funcionaba un poco lento y encontré que la norma ipv6 todavía no funciona aquí, Firefox pierde tiempo buscando.

Lo solucioné cambiando la configuración de Firefox así:


network.dns.disableIPv6;true

Tenés que colocar en la barra de direcciones about:config y luego buscar esa clave y modificarla

Espero te sirva

Ahora voy a probar eso en firefox pero me parce que va mas allá que firefox solo.

---

