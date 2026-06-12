---
title: "no puedo instalar ubuntu en acer 5050 64 bits"
date: 2009-05-19
forum: Instalación y Actualización
---

### Post by kresselacks on 2009-05-19
hola amigos soy queria hacer una consulta bueno yo soy nuebvo en este foro y de antemano les felicito el problema que tengo, es que no puedo instalar ubuntu desde 8.4 en adelante se queda pegado y la barra estatica puede, pero con la distro 7.10 ningun problema pero no me agarra el wifi amigos mi maquina es 
1. acer 64 bits mk 38 corre 2.2 
2 120 disco duro 
3. 1/2 ram 
4. wifi atreos 
5 tarjeta ati radeon xpress 1100 
 
esto lo probe con las 2 versiones de 64 y de 32 bits ojala haya una solucion de ante mano muchas gracias me aburri de $indows y quiero emigrar a linux:p

---

### Post by Carlos C on 2009-05-19
Prueba apretando F6 para que te de opciones de editar las opciones del GRUB. Añade el parámetro siguiente:
```
acpi=off
```

---

### Post by robertor on 2009-05-19
Que versión de BIOS tienes? En mi acer, tuve que hacer un downgrade de bios (la 3303 funciona perfecto). Con otras más nuevas, tenía muchos problemas... y lo peor es que eran aleatorios. Un día funcionaba de lo más bien un día completo y al otro era imposible usar el PC más de 5 minutos.
En general, los problemas los presentaba el wifi, el sonido y las funcionalidades de ahorro de energía (escalado de cpu, suspensión, hibernar, etc)

---

### Post by Carlos C on 2009-05-19
¿Y cómo se hace un downgrade de BIOS?

---

### Post by robertor on 2009-05-19
> **Carlos C said:**
> ¿Y cómo se hace un downgrade de BIOS?
A través de los utilitarios que te entrega el manufacturador de los equipos, en este caso, Acer.
Lamentablemente entregan herramientas que solo pueden ser usadas desde windows. Existe también para DOS, y lo puedes hacer con freedos.
Es una tarea crítica. Si eventualmente se produce algún error, te podrías quedar con un gran pisapapeles, así que si optas por esta opción, revisa bien las instrucciones.
Saludos!
Roberto

---

### Post by Carlos C on 2009-05-19
> **robertor said:**
> A través de los utilitarios que te entrega el manufacturador de los equipos, en este caso, Acer.
Lamentablemente entregan herramientas que solo pueden ser usadas desde windows. Existe también para DOS, y lo puedes hacer con freedos.
Es una tarea crítica. Si eventualmente se produce algún error, te podrías quedar con un gran pisapapeles, así que si optas por esta opción, revisa bien las instrucciones.
Saludos!
Roberto
Ufff yo le daría una oportunidad primero al "acpi=off" jajajaja

---

### Post by rodrigovb-cl on 2009-05-19
Y yo me cuidaría de dar soluciones tan radicales, no es de pesado, pero estamos acá para ayudar, muchas veces, a gente sin mucha experiencia ;)

---

### Post by robertor on 2009-05-19
> **rodrigovb-cl said:**
> Y yo me cuidaría de dar soluciones tan radicales, no es de pesado, pero estamos acá para ayudar, muchas veces, a gente sin mucha experiencia ;)

;)
Igualmente, ignoro que pasará cuando usas la bios 3309 en las versiones actuales de Ubuntu (y en general con cualquier Linux (la distro debiera dar lo mismo)), pero cuando probe, eran muchos los problemas.
Probé con varias combinaciones como las que propone CarlosC, y funcionaba una cosa y dejaba de funcionar la otra.
Yo tuve la suerte de que un amigo en la U, tenia el mismo equipo (comprado en la misma tienda). Despues de comparar todo, nos fijamos en las versiones de Bios... y ese era el problema.
Igualmente tendré más cuidado la próxima vez que responda.
Saludos!
Roberto

---

### Post by robertor on 2009-05-19
> **rodrigovb-cl said:**
> Y yo me cuidaría de dar soluciones tan radicales, no es de pesado, pero estamos acá para ayudar, muchas veces, a gente sin mucha experiencia ;)

;)
Igualmente, ignoro que pasará cuando usas la bios 3309 en las versiones actuales de Ubuntu (y en general con cualquier Linux (la distro debiera dar lo mismo)), pero cuando probé, eran muchos los problemas.
Probé con varias combinaciones como las que propone CarlosC, y funcionaba una cosa y dejaba de funcionar la otra.
Yo tuve la suerte de que un amigo en la U, tenia el mismo equipo (comprado en la misma tienda). Después de comparar todo, nos fijamos en las versiones de Bios... y ese era el problema.
Igualmente tendré más cuidado la próxima vez que responda.
Saludos!
Roberto

---

### Post by Carlos C on 2009-05-19
robertor: gracias de todos modos por el dato, el conocimiento siempre es bienvenido y nadie dice que no es bueno dar una solución, sobre todo si existen pocas opciones. Lo único que habría que precisar es que, cuando se da un consejo como ese aun usuario novato, se debe advertir cuáles son los riesgos existentes, lo que faltó en tu respuesta original. Salvo ese detalle creo que todo ok.

Saludos.

---

