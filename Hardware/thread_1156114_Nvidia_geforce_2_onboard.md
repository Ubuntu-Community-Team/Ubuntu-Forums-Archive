---
title: "Nvidia geforce 2 onboard"
date: 2009-05-11
forum: Hardware
---

### Post by sp33d3rs on 2009-05-11
Instalando ubuntu 9.04 llege a un problema con la placa de video onboard.
Tiene una nvidia gefroce 2 de 32mb onboard, la reconose en "controladores de Hardware" y la instala, pero al reiniciar se pone la pantalla negra, y me salen errores de video, se tildan ciertas imagenes o quedan "quemadas" en la pantalla.
 
Nota: Aclaro que si bien la pc no es de las mas nuevas, todos sus componentes funcionan ok; por otro lado, si cambio las x puedo subir la resolucion a 1024x768 (saliendo de la estandar de 800x600), el problema es que compiz y los juegos no toman los efectos de escritorio y demás (son solo 32, pero los quiero :( )
 
Muchas Gracias

---

### Post by guillermolisi on 2009-05-11
> **sp33d3rs said:**
> Instalando ubuntu 9.04 llege a un problema con la placa de video onboard.
Tiene una nvidia gefroce 2 de 64mb onboard, la reconose en "controladores de Hardware" y la instala, pero al reiniciar se pone la pantalla negra, y me salen errores de video, se tildan ciertas imagenes o quedan "quemadas" en la pantalla.

Nota: Aclaro que si bien la pc no es de las mas nuevas, todos sus componentes funcionan ok; por otro lado, si cambio las x puedo subir la resolucion a 1024x768 (saliendo de la estandar de 800x600), el problema es que compiz y los juegos no toman los efectos de escritorio y demás (son solo 64, pero los quiero :( )

Muchas Gracias
Te fijaste como reconoce Ubuntu a esa placa ?

Mira que las placas mas viejas como por ejemplo la TNTRiva y similares que venian con nvidia 400 ya no tiene soporte de drivers, ni siquiera los legacy.

---

### Post by sp33d3rs on 2009-05-12
> **guillermolisi said:**
> Te fijaste como reconoce Ubuntu a esa placa ?
 
Mira que las placas mas viejas como por ejemplo la TNTRiva y similares que venian con nvidia 400 ya no tiene soporte de drivers, ni siquiera los legacy.
La reconose, me da los drives para descargar, se descarga, se instala y cuando se reinicia funciona con la resolucion adecuada (1024x768 o 1280x1024), el tema es que tiene como "errores". A ver si les puedo explicar, carga la barra superior e inferior, pero la pantalla esta en negro. Si ejecuto algun programa se abre la ventana y se ve perfecto, pero al moverla queda como "marcada" en los movimientos, no se enpieza a ver bien, tira errores de video y llega a un punto en que la pc se tilda o no se ve nada.
 
Espero que me puedan dar una mano, leyendo por algunos lados, vi que se podria instalar una version anterior, pero no creo que esto sea así, se supone que mayor version, es mayor compatibiliad de drivers (o eso creo)
 
El problema es que la persona que lo tiene instalado vive en Mar del Plata!!, todo un viaje!!.
 
Quiere usar ubuntu, pero no quiere sin compiz y sin urban terror :P
Tambien, si no puede solucionarlo, quiere Win en su totalidad del disco (no el dual boot, como ahora lo tiene instalado), ... desp tendria que ver como se volvia a ese sistema operativo (se ponia el cd de inst, se borraban las partiones y se volvia a instalar??)
 
Muchas gracias por responder.

---

### Post by guillermolisi on 2009-05-13
> **sp33d3rs said:**
> La reconose, me da los drives para descargar, se descarga, se instala y cuando se reinicia funciona con la resolucion adecuada (1024x768 o 1280x1024), el tema es que tiene como "errores". A ver si les puedo explicar, carga la barra superior e inferior, pero la pantalla esta en negro. Si ejecuto algun programa se abre la ventana y se ve perfecto, pero al moverla queda como "marcada" en los movimientos, no se enpieza a ver bien, tira errores de video y llega a un punto en que la pc se tilda o no se ve nada.
 
Espero que me puedan dar una mano, leyendo por algunos lados, vi que se podria instalar una version anterior, pero no creo que esto sea así, se supone que mayor version, es mayor compatibiliad de drivers (o eso creo)
 
El problema es que la persona que lo tiene instalado vive en Mar del Plata!!, todo un viaje!!.
 
Quiere usar ubuntu, pero no quiere sin compiz y sin urban terror :P
Tambien, si no puede solucionarlo, quiere Win en su totalidad del disco (no el dual boot, como ahora lo tiene instalado), ... desp tendria que ver como se volvia a ese sistema operativo (se ponia el cd de inst, se borraban las partiones y se volvia a instalar??)
 
Muchas gracias por responder.
Las placas viejas como la que mencione no tienen aceleracion 3D. No tengo idea si esa gForce viene con esa caracteristica. Si tampoco trae aceleracion 3D los efectos no funcionaran.

Por otra parte, la placa estara en buenas condiciones, particularmente sus chips de memoria ?

---

### Post by sp33d3rs on 2009-05-13
> **guillermolisi said:**
> Las placas viejas como la que mencione no tienen aceleracion 3D. No tengo idea si esa gForce viene con esa caracteristica. Si tampoco trae aceleracion 3D los efectos no funcionaran.

Por otra parte, la placa estara en buenas condiciones, particularmente sus chips de memoria ?

Uhh, que feo, un poroto menos para mi ubuntu..:sad: bue, algun poroto se tenia que llevar el reverendo W!Nd0w$. En fin, igual ubuntu le gusto mucho, cuando se compre la pc nueva volvemos a probrar... gracias igual por todo.

Por otro lado, pone el cd de win, borra particiones, genera una unica (o dos, las que desee en formato ntfs) instala y listo, no?:?

---

### Post by guillermolisi on 2009-05-13
> **sp33d3rs said:**
> Uhh, que feo, un poroto menos para mi ubuntu..:sad: bue, algun poroto se tenia que llevar el reverendo W!Nd0w$. En fin, igual ubuntu le gusto mucho, cuando se compre la pc nueva volvemos a probrar... gracias igual por todo.

Por otro lado, pone el cd de win, borra particiones, genera una unica (o dos, las que desee en formato ntfs) instala y listo, no?:?
Si, si quiere volver a tener una maquina full Windows, cuando llega al particionador le dice que usara todo el disco (recomiendo aun en Win hacer una particion para el swap file por cuestiones relacionadas con la fragmentacion de FAT/NTFS file system, de un tamaño que permita un swap file lo mas generoso posible segun el uso que se le de a la maquina).

---

