---
title: "[SOLVED] No inicia correctamente la placa de video"
date: 2009-06-29
forum: Hardware
---

### Post by sp33d3rs on 2009-06-29
*Estoy desde el trabajo, y como tengo un tiempo, explico mi problema en la pc de mi hogar.*

Las actualizaciones que hace ubuntu.. (*creo que eso son*, es decir, los "inicios" que se agregan en el grub de inicio, siempre tenia ubuntu y otros sistemas operativos, en mi caso windows)
El problema es que el último que se agrego (recuerdo que termina en .13) no inicia la placa de video, dice que no puede reconocer el driver, entonces uno acepta e inicia con resolución muy baja (es decir, sin placa de video, sin compiz, sin nvidia)
Actualmente inicio el que termina en .11.
[U]
Ahora explico mis inquietudes.[/U]
**1.** Si alguien entendio mas o menos lo que explique arriba, y me puede enseñar como se llaman las "opciones de inicio" que tira el grub, me seria de gran ayuda... asi no tengo que dar largas explicaciones sin sentido :S

**2.** Si se puede solucionar que inicie el ultimo ubuntu que se agrego (ese que termina en .13) con la nvidia funcionando perfectamente (tengo una nvidia 8600gt, con los drivers actualizados, el 180 recomendado por ubuntu). O sino, como hacer para que inicie automaticamente en el que termina en .11 (que ese si funciona ok)

**3.** Si bien el .11 inicia bien, solo tiene un problema, que inicia con 800x600 por defecto, y no se lo puedo cambiar

PD: perdon por mi explicacion "a medias", pasa que lo quiero solucionarlo, y llego como a las 2am a casa :S (no tengo muchos animos :P) y mañana arranco tempranito.

---

### Post by luks911 on 2009-06-29
Esas "opciones de inicio" son distintas versiones del kernel. Cuando se actualiza se agregan las nuevas versiones pero se conservan las viejas. En parte, por posibles errores en el nuevo, o más bien problemas entre el kernel y el hard.
Ahora, con esa placa deberías tener la definición bien con ambos kernel.
¿Tenés instalado los drivers de Nvidia? Tené en cuenta que si los tenés para una de las versiones del kernel podés no tenerlos para la otra. Cuando los instalás, lo hacés para la versión del kernel con la que iniciaste esa vez.
Para instalarlos, en una terminal ejecutá
```
sudo aptitude install nvidia-glx-180
```

---

### Post by sp33d3rs on 2009-06-29
> **luks911 said:**
> Esas "opciones de inicio" son distintas versiones del kernel. Cuando se actualiza se agregan las nuevas versiones pero se conservan las viejas. En parte, por posibles errores en el nuevo, o más bien problemas entre el kernel y el hard.
Ahora, con esa placa deberías tener la definición bien con ambos kernel.
¿Tenés instalado los drivers de Nvidia? Tené en cuenta que si los tenés para una de las versiones del kernel podés no tenerlos para la otra. Cuando los instalás, lo hacés para la versión del kernel con la que iniciaste esa vez.
Para instalarlos, en una terminal ejecutá
```
sudo aptitude install nvidia-glx-180
```
  Gracias por la info. El tema els que probe reinstalar los drivers (pense que magicamente se desistalaron :S) pero no, cuando voy al panel de nvidia me dice que lo agrege, lo agrego y no me figura activado (en verde), y al reiniciar tengo el mismo problema. Asi mismo, voy a probar desde la consola
Gracias!

---

### Post by guillermolisi on 2009-06-29
Para ubicarnos un poco mejor en el contexto del problema, que tal si pasas modelo de motherboard, modelo de placa de video, version de Ubuntu ? Podra ser ?

---

### Post by sp33d3rs on 2009-06-29
> **guillermolisi said:**
> Para ubicarnos un poco mejor en el contexto del problema, que tal si pasas modelo de motherboard, modelo de placa de video, version de Ubuntu ? Podra ser ?
No hace falta ya. Me explico, regrese a mi casa, prendi la pc e inicie el ultimo kernel y walla!, magicamente andaba bien... la realidad es que nose lo que paso.. en fin, ahora funciona (nota: hace 2 días el sistema se actualizo, quizas en esa actualizacion se habia arreglado el problema con el kernel nuevo y como hacia una semana estaba funcionando mal y yo ejecutaba el kernel .11, ps no me daba cuenta.)
En fin, perdon por las molestias, y gracias por la ayuda igual!

---

