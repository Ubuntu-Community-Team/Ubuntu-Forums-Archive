---
title: "salvenme!"
date: 2008-10-30
forum: Hardware
---

### Post by katon on 2008-10-30
gente por favor talvez alguien tiene idea lo que hacer compre una maquina nueva 
Q6600 , mother intel DP43TF , 2 bancos de 1 gb ddr2 800mhz

Intrepid 8.10 lo baje antes y al querer entrar en el live cd da un feisimo error el cual les adjunto la imagen, tambien probe de entrar a instalar . Me refiero luego de que bootea del cd en el menu que dice "try ubuntu live..." 

no encuentro casi info sobre esto y lo poco que hay son cosas del kernel que no entiendo muy bien,,,

(aclaro que ya saque las memorias , las inverti el orden que estaban puestas, las cambie y puse otro banco , desconecte el disco Sata, ) todo

por favor ayuda!! y eso que elegi los componentes especialmente para instalar ubuntu...

---

### Post by Mauro22 on 2008-10-30
:confused:

No es por tirar mala onda :(... pero probaria con Hardy...


Probaste algo mas aparte de Intrepid?

---

### Post by josedamico on 2008-10-30
no se..no entiendo mucho, pero ¿probaste con otro live cd? me da pensar que puede haber un error en el cd. Yo pobraria  poniendo otro live cd de otra distro o bjar de nuevo de la pagina oficial de ubuntu y al quemarlo verificas que esta bien.

---

### Post by katon on 2008-10-30
Hardy si funciona, 
pero la idea mia era usar la nueva version, 


Cds ya probe el release candidate , el beta anterior, no es el cd porque en otras maquinas me funcionan .

---

### Post by pol666 on 2008-10-30
peor podia ser un kernel panic...

+Te fijaste si alguien ya reporto el bug?

---

### Post by sam_award on 2008-10-31
prueba desde hardy actualizar a ibex cn esto :

presionas alt+f2 y pones :

update-manager -d

y cn eso actualizas a ibes , no tienes xq tener problemas jejeje

---

### Post by katon on 2008-10-31
yo reporte el bug nadie lo miro ni siquiera...
y hay muchos bugs similares o con otro numero de error

con respecto a actualizar desde HARDY , es posible usar el kernel viejo pero con todos los "chiches" nuevos de Ibex? ya que la ultima vez que actualize por internet una version luego ni arranco...

aproposito ustedes bajaron Ibex ya?

---

### Post by faktorqm on 2008-10-31
Lo que pasa, ayer lo hablabamos en la release, es que II actualizo X.org por que hubo una modificacion en el kernel, y eso trajo aparejado varias cosas. Una de ellas, el driver "legacy" de nvidia no anda mas. La otra, no se si se puede tener el kernel viejo con el X.org nuevo... yo lo que haria (si queres probar) es agarrar instalar hardy, marcar el paquete de xorg y el kernel para no actualizar, y actualizar todo el resto. Si anda eso, grosso! jajaj y si no no se. Salu2!

---

### Post by katon on 2008-10-31
gracias a todos por las respuestas, 
la cuestion es que es muy raro estos errores teniendo en cuenta que el mother que tengo es relativamente nuevo , y las nuevas versiones de kernel se supone que deberian funcionar con las cosas nuevas primero y principal :)

---

### Post by BlackHero on 2008-10-31
Hola como va, jeje hoy todas mis respuestas son 

consola

desde tu version anterior de ubuntu


sudo aptitude update
sudo aptitude upgrade


y listo ya tenes intrepid con tus anteriores drivers y todo funcionando =)

---

### Post by katon on 2008-10-31
> **BlackHero said:**
> Hola como va, jeje hoy todas mis respuestas son 

consola

desde tu version anterior de ubuntu


sudo aptitude update
sudo aptitude upgrade


y listo ya tenes intrepid con tus anteriores drivers y todo funcionando =)

pero te actualiza el kernel tambien? 
el problema mio parece tener que ver con los nuevos kernel de intrepid, ya que HARDY no tiene ningun problema ,

---

