---
title: "olivetti notebook"
date: 2009-10-10
forum: Hardware
---

### Post by maxi.es on 2009-10-10
Soy nuevo en esto 
Nesecito ayuda con una olivetti notebook. Le instale ubuntu 8.04 y no puedo prender el wifi por favor ayuda.-
Tampoco pude cambiar la resolucion de pantalla ni los efectos 3d.- eso es seguro porque no tengo los drivers apropiados.-

Busque en muchos foros y hago lo que dicen pero no hay resultado y hay pasos que no entiendo

---

### Post by faktorqm on 2009-10-11
te olvidaste de lo mas importante... el modelo! olivetti es una marca... 

y anda a aplicaciones -> accesorios -> terminal y escribi "lspci" y copia y pega el resultado. salu2!

---

### Post by z37a on 2009-10-11
> **maxi.es said:**
> Soy nuevo en esto 
Nesecito ayuda con una olivetti notebook. Le instale ubuntu 8.04 y no puedo prender el wifi por favor ayuda.-
Tampoco pude cambiar la resolucion de pantalla ni los efectos 3d.- eso es seguro porque no tengo los drivers apropiados.-

Busque en muchos foros y hago lo que dicen pero no hay resultado y hay pasos que no entiendo

Si no me equivoco Olivetti usa placas de video SIS todavia, por lo cual la parte del 3D vas a tener problemas, lamentablemente estas placas son ultraincompatibles y hasta en windows andan medio mal.

Con lo del wifi ya ahi lo veo medio raro, si bien estas usando 8.04 te diria que pruebes con 9.04 que dispone de una mayor cantidad de drivers para el WiFi, te pediria que pongas mas informacion sobre el hardware asi podriamos ver aca como poder solucionar ambas cosas, aunque ya te anticipo que en caso de ser un video SIS el 3D no va a funcionar(pasa lo mismo con unas cuantas placas VIA).

Lo que podes hacer es ir a una terminal(Aplicaciones->Accesorios->Terminal) e introducir el comando "lspci", luego con el mouse copia todo lo que te arroje y pegalo en el aca en el foro asi se puede ver esactamente que hardware tenes, en especial el WiFi y el video!!!!

---

