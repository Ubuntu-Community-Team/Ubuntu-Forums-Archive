---
title: "Actualización a 10.04 - Estoy pegado en la pantalla de inicio"
date: 2010-05-07
forum: Instalación y Actualización
---

### Post by KHF on 2010-05-07
Hola amigos!
Me presento: soy Karl, soy nuevo en el foro, y bueno... este es mi primer post :P soy relativamente "nuevo" en Ubuntu (instalé Ubuntu Karmic Koala hace unos 5 meses).

Resulta que yo tenía Ubuntu Karmic Koala, y me funcionaba perfect! ...pero todo cambió cuando, ansioso por probar Lucid Lynx, el sábado pasado actualicé el SO.
Tengo un PC medio viejo, de como el 2004, de 1,25 GHz de procesador, 1,25 GB de RAM (venía con 256 MB, pero le compré 1GB ) y 80 GB de disco duro. Además, tenía configurado el log-in automático, ya que este PC lo uso solamente yo (tiene solo un usuario)

En el proceso de actualización, todo parecía ir bien, hasta que tuve que reiniciar el PC:
booteó bien, empezó a cargar, y instantes después de que me apareciera mi fondo de pantalla, empezé a escuchar la melodía de inicio "tum-turum-tum-turum-turum-tum-turum-tum", pero antes de que esta melodía terminara, se cortó el sonido, la pantalla se puso negra y instantes después me apareció la pantalla "splash", diciendome que hiciera log-in (cosa extraña, ya que tengo log-in automático).
Elegí mi usuario, puse mi contraseña, elegí como tipo de sesión "GNOME" y, de esta vez, alcanzé a escuchar por completo la melodía y ver mi fondo de pantalla, pero después se volvió a poner la pantalla de color negro y volví a la pantalla "splash"
Intenté varias veces, pero siempre con el mismo resultado.
Después decidí usar una sesión KDE, todo parecía ir bien, me apareció la típica pantalla azul KDE (nunca había usado KDE antes), se me cargaron 3 iconitos y...... ¡¡¡CASPITA!!! se me puso la pantalla negra, y tuve que apretar ctrl+alt+supr para volver a la pantalla "splash"
 La única forma que tengo de usar el computador es en el modo "GNOME a prueba de fallos (y xterm, pero eso no sé como ocuparlo). Si bien así tengo internet, buena resolución y sonido.... es una lata, por una serie de factores: tengo que hacer el procedimiento de elegir como sesión "GNOME a prueba de fallos", poner la clave, no puedo ver videos (avi, rmvb, etc), además del hecho de que estoy a prueba de fallos, y lo más probable es que hayan hartas opciones inhabilitadas.
He buscado harto en google (así lo había hecho con toooooodos los otros problemas que he tenido), pero como esta versión es nueva, creo que no le ha pasado a mucha gente.... además: ¡Para mi es desesperante! como no me tira ningún mensaje de error no sé que es lo que está gatillando el problema... no sé por donde empezar!!!!!

SALUDOS!!!!:guitar:

---

### Post by Carlos C on 2010-05-08
Intenta ver los mensages que te entrega el sistema con el comando "dmesg". ¿Tienes los efectos gráficos activados? Puede que tengas problemas por ese lado.

Saludos.

---

### Post by KHF on 2010-05-09
Estimado Carlos,
Efectivamente, ese era un gran problema.... no sabía como diagnosticar el problema :P
Probé con ese comando que me pasaste, y me sale una chorrera de datos.... un montón de problemas :(
Para que no haya una ensalada de letras en el thread, copié los errores y los pegué en un archivo de texto (lo guardé como errores.txt) y lo subí al servidor 4shared.
OJO: eran tantos errores que no me alcanzaron a salir todos en el terminal, el primer error que visualicé empezaba con el número [      12.XXXXXXXX] ..........

Mucho me temo que algo se haya instalado mal..... será que la única salida es reinstalarlo???? [IMG]http://img1.bb2.org/uploads/bb2.org/argensteel/emo-_E.gif[/IMG]

```
http://www.4shared.com/document/SsOoRo0M/errores_Ubuntu.html

```

---

