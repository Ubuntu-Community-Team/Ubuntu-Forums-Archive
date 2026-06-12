---
title: "[SOLVED] problemas con router, transfer de archivos"
date: 2008-04-24
forum: Hardware
---

### Post by sergiom99 on 2008-04-24
hola gente, queria hacer unas consultas.
Tengo un router Linksys WRT54g v8 y 2 PCs con XP y una laptop con Kubuntu.

El problema que tengo es que si desde la laptop quiero traerme una ISO o cualquier otro archivo similar desde la PC, no puedo hacerlo. Si desde otra PC con XP quiero traerme archivos, no puedo hacerlo desde ninguna de las 2. (archivitos chicos, mp3, etc si.). Me tira un error de conexion o de lectura, ahora no lo recuerdo del todo.

Ahora bien, si desde la pc de origen muevo el ISO a una carpeta compartida con samba en Kubuntu no tengo problemas. Mismo entre las 2 PC windoze, moviendo desde la de origen a una carpeta compartida de la de destino.

Hay algo que necesite configurar o revisar en el router?
supongo que debe venir por ese lado, porque en los dos OS pasa lo mismo, 3 maquinas !=

Otro tema: muy ilusionado, queria conseguir una antena externa para el router, para llevar en un lugar de casa la señal de 2 a 4 rayitas (Excelente) y me entero que desde la version 6 en adelante del WRT54G ya no tienen antena desmontable. Alguien tiene idea si se puede hacer algo? o como subir un poquito la señal?

gracias y saludos

---

### Post by clasificado on 2008-04-25
> **sergiom99 said:**
> como subir un poquito la señal?

En un probleeeeeeeeeeeema.

La forma facil: No se puede. Mejor tener un router con poca señal que romperlo por conseguir un poco más. Para eso te compras un segundo router y éste último lo usas de repetidora.

La forma geek: 
1) Que las antenas esten fijas quere decir que no tenés rosca, pero si lo abrís podés llegar al par de contactos como para soldarle ahi la antena externa. Deberias de hacerle un hueco para pasar los cables y usar pistola de pegamento para fijarlo.

2) Podrias overclockear al router: los firmware originales son aburridos: Si le ponés algo como [dd-wrt]("http://www.dd-wrt.com"), podés subirle la potencia a las antenas. No lo probé con un WRT54g v8, pero en mi WRT54gl 1.0 cuando lo he necesitado funcionó de perillas. aunque tuve que agregarle un cooler al chipset porque sobrecalentaba.

clasificado

---

### Post by sergiom99 on 2008-04-25
clasificado, gracias por la data.
la forma 1 la voy a meditar. la dos, el dd-wrt no funciona (por ahora) con la v8. Linskys se avivo de lo que estaban haciendo con un router de u$s40 y cambio muchas cosas. Ahora tenes que comprar uno mas caro, o ir agregando repetidoras.

Alguien tiene alguna idea por el problema del trasnfer?

---

### Post by sergiom99 on 2008-04-25
clasificado, gracias por la data.
la forma 1 la voy a meditar. la dos, el dd-wrt no funciona (por ahora) con la v8. Linskys se avivo de lo que estaban haciendo con un router de u$s40 y cambio muchas cosas. Ahora tenes que comprar uno mas caro, o ir agregando repetidoras.

Alguien tiene alguna idea por el problema del trasnfer?

---

### Post by clasificado on 2008-04-25
> el dd-wrt no funciona (por ahora) con la v8

¿vos estas seguuuuuuuuuuro?

mirá que segun [los dispositivos soportados de la wiki de dd-wrt]("http://www.dd-wrt.com/wiki/index.php/Supported_Devices#Linksys_.28all_the_rest_that_is_not_re-engineered_til_today.29") las versiones 8.0, 8.1 y 8.2 estan etiquetados como **Micro only**, que es más que nada

Por tu problema de transfer: Lo leí de nuevo y no entendí nada :P ¿Es un problema del linux al windows o al revés?

clasificado

---

### Post by sergiom99 on 2008-04-25
gracias! la ultima vez q habia mirado la lista decia q todavia no estaba soportado. ahora tengo q ver q es 'micro only' y animarme.

lo de la transferencia: no importa si es XP o Kubuntu. Digamos que el archivo esta en la PC1 y yo estoy en la PC2 y trato de copiarmelo. Ahi me da un error. 
Pero si desde la PC1 lo muevo a la PC2, puedo copiarlo sin problemas.
Me pasa desde Linux o desde Win. O entre Win y Win. 
Eso es lo que me tiene desorientado.

Gracias por tu ayuda!

---

### Post by clasificado on 2008-04-26
Podria ser problema del router o de las placas de red.

1) Probá eliminando problemas de operativo: levantá las dos pcs con live cds y probá la copia, fijate si sigue igual

2) Probá eliminando problemas de router: Acá tenes dos para probar

2.1) Eliminá el router conectando directamente pc con pc (vas a tener que moverlas) conseguite un cable cruzado y conecta las pcs directamente y probá la copia: Si funciona bien, es el router.

2.2) Puede ser que el router tenga los puertos quemados: Cambialos de puertos. Suelen tener cuatro probá varias combinaciones.

3) Probá eliminando problemas de cables: Cambiá los cables :)

4) La mas pesada, que tengas problemas en las placas. Deberias de conseguirte una placa pedorra realtek compatible (20$) y probarla en un equipo y el otro.

No se me ocurren mas cosas. Con eso practicamente renovamos todo el sistema. Si sigue sin funcionarte puede ser que

1) Estes usando redes wireless (para lo cual esa lista no te sirve para nada)

2) Que haya que pasar al campo paranormal: Entramos en engualichados, mal de ojo, router con pata de cabra y demases cosas.

clasificado

---

### Post by sergiom99 on 2008-04-27
Gracias capo, voy a conseguir todo el material necesario y hacer el mega operativo de pruebas a ver que pasa.
salutes.

---

### Post by clasificado on 2008-04-27
> **sergiom99 said:**
> Gracias capo, voy a conseguir todo el material necesario y hacer el mega operativo de pruebas a ver que pasa.
salutes.

:P Parece un montón, pero es ir descartando las partes de a una.

Yo te recomiendo empezar por las que no necesitas nada de nada (1 y 2.2)

y recien despues en las que son mas molestas. (seguiria por la 2.1)

bué, no sé. Fijate. Y suerte!

clasificado

---

### Post by sergiom99 on 2008-05-03
master, ya empece con las pruebas. 
logre meter el DD-WRT en el router, entro de pelos y parece mejor q el firm original.
Esta version de router no soporta overclocking, le subi un poco el TX power de 28mW a 70mW pero no logre subir una rayita en la calidad de conexion. Tampoco me animo a ponerlo a mas para q no levante temperatura. No entiendo un corno de electronica asi que no sabria ponerle un cooler. Busque instrucciones "for dummies" para agregarle antenna externa pero no supe encontrar y me da cosita abrirlo y toquetear al tuntun.

Lo que sigue es probar el liveCD en la PC con windoze.
Como siempre, gracias capo por tu ayuda!

---

### Post by clasificado on 2008-05-03
> **sergiom99 said:**
> le subi un poco el TX power de 28mW a 70mW 

Es exactamente a lo que me referia, le pifié al nombre. El Overclocking es otra cosa; aún si lo pudieras hacer no sirve a tu propósito.

70mw supongo estará bien. Los foros lo marcan como el "límite seguro", ya supongo que tendras que revisar vos a ojo si es tan seguro como se dice.

Tampoco hace falta un cooler, con un disipador cualquiera sirve, mientras entre en la carcaza.

clasificado

---

### Post by sergiom99 on 2008-05-04
bueno maestro, una vez mas tenias razon.
probe la desktop con el primer liveCD que encontre (ubuntu 7.04) y comparti la carpeta, entre x smb desde la laptop con el kubuntu como siempre y pude traerme una ISO sin ningun problema. 
Asi que debe ser algo de Windou$.

el router sigue a 70mW, tiene temperatura externa normal al tacto, y me parece que lo dejo asi, porque no encontre howtos for dummies para hacer el reemplazo de antennas y  mis conocimientos de electronica son nulos. (pensaba hacer cirugia, reemplazando el bisturi y portaagujas por soldador y estanio, pero la verdad no cazo un fulbo.)

---

### Post by clasificado on 2008-05-05
> **sergiom99 said:**
> Asi que debe ser algo de Windou$.

Que raro...

Los problemas con Windows + samba suelen ser tres:

1) Problemas de permisos a nivel de archivo (ACL): Para verificar esto podrias cambiar los permisos de la carpeta y sus archivos para que [TODOS] tengan permisos de [Control Total]

2) Problemas de permisos a nivel de compartición: Deberias de asegurarte que el recurso compartido tiene asignado para [TODOS] los permisos de [Control Total]

3) Te estas conectando con un usuario sin contraseña: A Windows esto no le gusta (no es que no se pueda, no le gusta, mejor evitemosló). Probá crearte un usuario nuevo, asignarle contraseña, darle los dos permisos aclarados mas arriba y decirle al ubuntu que use ese usuario para conectarse (o dale contraseña al que estas usando ahora, como quieras)

Esos serian algunos puntos de partida. Hay mas, veamoslo después.

Te adjunté dos screenshots para los puntos uno y dos.

clasificado

---

### Post by sergiom99 on 2008-05-05
¡¡¡grande clasi!!!
mira la pavada que resulto ser!!!
Sabes q antes revise mil veces la config de la carpeta, pero no tenia las solapas que vos me mostras, entonces la daba por bueno.
En el laburo las tengo, pero pense que era por estar en dominio y con mas usuarios.
El asunto es q cuando vi tus fotos, lo recorde, lo google un poco y resulta que hay q desmarcar en "Opciones de carpeta\Ver--> utilizar uso compartido simple de archivos"
Destildando eso, aparecen las solapas para definir bien los permisos. Di control total a [TODOS] y listo.

solo queda subir una rayita el wifi y estoy feliz.

Gracias maestro por tu ayuda y paciencia.

PS: como le pongo 'solved' al post?

---

### Post by sergiom99 on 2008-05-08
clasi,
te pregunto una mas:
cuando agrego archivos a esa carpeta, tengo q volver a setearle los permisos a todos, porque sino no tengo acceso a los nuevos.

Como hago para que XP lo haga solo?

---

### Post by clasificado on 2008-05-08
¿Probaste revisando los permisos de la carpeta que los contiene?

Supuestamente los hereda.

clasificado

---

### Post by sergiom99 on 2008-05-09
si, yo siempre toque los permisos de la carpeta, no de los archivos individuales, pero al agregar uno nuevo, se ve que no lo hereda

---

### Post by sergiom99 on 2008-06-08
creo que lo arregle seteando directamente los permisos del disco C: y que de ahi para abajo los herede.
marco como SOLVED.

---

### Post by diego.s.eik on 2008-08-19
Hola a todos he tenido ultimamente este problema, prendi mi router y no mandaba señal inalambrica , pero si por el cable de red, lo reinicie y comenzo a mandar señal normal.
Hoy se fue la luz por unos minutos, cuando regreso pues, prendio normal funcionaba el inter por cable, pero no mandaba señal, lo reinicie otra ves y recien comenzo a mandar.
Esta prendido todo el dia, desde hace mucho, y bueno a me llaman en la mañana porq me dicen qe no ahy internet, reviso y no mandaba señal inalmbrica solo me qedo reiniciar (apagar y prender) y comenzo a mandar.

¿Que podria ser eso O_O?, por favor ayudenme

mi router es
WRT54G v8.0 Broadcom
Firmware: DD-WRT v24 generic micro

---

### Post by sergiom99 on 2008-08-20
seguramente en el foro de DD-WRT en español [1] te van a poder ayudar mejor, ya que es un problema especifico del router y no de Ubuntu.
como primer medida asegurate de tener la ultima version del FW.
suerte!

[1] [http://www.dd-wrt.com/phpBB2/viewforum.php?f=9&sid=e37ebde6d6e21e5ad84ad097ea573157](http://www.dd-wrt.com/phpBB2/viewforum.php?f=9&sid=e37ebde6d6e21e5ad84ad097ea573157)

---

