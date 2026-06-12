---
title: "Problema con drivers nvidia 180 en Kubuntu Jaunty Jackalope"
date: 2009-04-24
forum: Hardware
---

### Post by fgl82 on 2009-04-24
Muchachos,

como posteé en el thread de escritorios en su momento, yo había instalado la RC de Ubuntu upgradeando mi instalación de Intrepid.

Ayer me agarró la locura y, como había algunas cositas que no habían quedado funcionando del todo bien, decidí backupear mis datos y mandarme a formatear en ext4 e instalar Kubuntu 9.04 desde 0, recién bajadito del sitio oficial (un mirror de Alemania que iba rapidísimo).

Quemé el CD, lo instalé sin mayores problemas (salvo que se quedó configurando apt muuuuuuuuuucho tiempo) y me dispuse a hacer lo primero que siempre hago: instalar los drivers privativos.

Mi primera sorpresa fue cuando quise correr la herramienta correspondiente: me tiraba un error diciendo básicamente que había habido una falla en "Jockey".

Traté entonces de instalar los drivers mediante apt-get o aptitude, con iguales resultados: me decía que había problemas de paquetes, que para instalar nvidia-glx-180, debía instalar primero nvidia-180-kernel-source. quise hacerlo y tampoco logré nada. Seguía diciendo que había conflicots de dependencias.

Pensé que podía ser tema de que el repositorio de Argentina (patán) no estaba bien, así que cambié al de EEUU, pero obtuve los mismos resultados.

Hice un purge y, a continuación, quise instalar el driver 173 mediante la herramienta gráfica. Ahí si me dejó, pero lo saqué porque yo quería el 180, que en la RC me andaba mucho mejor que el 173.

La pregunta, obviamente, es, ¿alguien más tuvo estos problemas? ¿Hay algo que estoy haciendo mal?

Espero sus comentarios y gracias como siempre.

(pd: Hei Ku, perdoná si esto no va acá, pero no supe si ponerlo en soft o en hard, movelo a donde más te  parezca así la próxima ya sé dónde postear [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG])

---

### Post by pablo.s on 2009-04-24
> **fgl82 said:**
> 
Mi primera sorpresa fue cuando quise correr la herramienta correspondiente: me tiraba un error diciendo básicamente que había habido una falla en "Jockey".

La pregunta, obviamente, es, ¿alguien más tuvo estos problemas? ¿Hay algo que estoy haciendo mal?


A mi me diò el mismo error de Jockey, seguì
configurando otras cosas sin prestarle mucha
importancia. A los diez minutos reinicié la
maquina. De vuelta a Hardware Drivers, de
vuelta a elegir el driver 180, pum, lo instala
normalmente.
Saludos

---

### Post by fgl82 on 2009-04-24
No, ya probé eso.

Es más, instalé nuevamente Kubuntu por si la instalación había quedado chingada por algo...

:sad:

---

### Post by pablo.s on 2009-04-24
Con Envy probaste?

---

### Post by fgl82 on 2009-04-24
No, la verdad no quería instalar nada que no fuera propio del SO, menos para algo que hago una vez cada muerte de obispo.

Me llamó mucho la atención el tema de que me diga que están mal las dependencias...

Pero bueno, cualquier cosa hoy pruebo con envy...

qué mal, parece que soy el único con este quilombito. Culpa de los alemanes! :P

---

### Post by pablo.s on 2009-04-24
> **fgl82 said:**
> Culpa de los alemanes! :P

Qué alemanes?

---

### Post by fgl82 on 2009-04-24
Los del mirror!!! :P

(ver mi primer mensaje)

---

### Post by luks911 on 2009-04-24
Sí, sí, a mí también me pasó. Lo arreglé con 

```
sudo aptitude install nvidia-glx-180
```

Ah, ah, ahora veo que no pudiste así, qué raro. Debería instalar las dependencias solo. Mmmm....

---

### Post by fgl82 on 2009-04-24
como dije en el post, ya probé  eso y tengo errores de dependencias...

el apt-get install -f no los arregla, dice que está todo ok...

---

### Post by luks911 on 2009-04-24
> **fgl82 said:**
> como dije en el post, ya probé  eso y tengo errores de dependencias...

el apt-get install -f no los arregla, dice que está todo ok...

Sí, veo. Edité arriba, perdón. ¿Y si instalás el deb de Ubuntu Packages[0]?


[0] [http://mirrors.kernel.org/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/nvidia-180-kernel-source_180.44-0ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/nvidia-180-kernel-source_180.44-0ubuntu1_i386.deb)

---

### Post by fgl82 on 2009-04-25
Gente,

como dijo alguen más arriba, el problema se resolvió sólo.

Reinstalé Kubuntu, corrí la herramienta de drivers.

Luego de una rato tiró el error de Jockey.

No le di bola y la cerré.

La abrí de vuelta.

Ya estaba instalado!

Gracias a todos!

Saludos!

---

