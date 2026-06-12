---
title: "Muchos colores... a lo psicodélico!"
date: 2008-12-15
forum: Hardware
---

### Post by erdosain9 on 2008-12-15
Buenas.  Les pido ayuda dado que instalé una nueva placa de video nvidia 6200 256ram... el tema es que luego de un tiempo de andar haciendo cosas (navegar, escribir... lo que fuere) comienzan a aparecer un montón de colores en cualquier lado de la pantalla... todo se comienza a borronear... si muevo el mouse todo se va deformando a su paso... Antes de instalar esta tarjeta tenía una 440mx... y funcionaba todo bien.  Luego al cambiarla también cambié los drivers cuando ubuntu me lo pidió.  
Es raro que cuando aún así me guío "a ciegas" para darle al botón de apagar/reiniciar (virtual) y resulta que al poner reiniciar se borran todos los colores y lo deforme que haya quedado al aparecer el cartel de Ubuntu (cuando comienza a apagarse)... como que todo volviera a la normalidad... 
es Ubuntu Hardy.

Saludos a todos y gracias... si no se entiende algo preguntenme por favor.

---

### Post by staar on 2008-12-15
mmmm... suena a problema de hard, donde compraste la placa? es usada?

saludos

---

### Post by erdosain9 on 2008-12-15
Sabés que yo pensé lo mismo.  Es nueva... estaba en garantía...fue un despelote hacer que la cumplieran (no sé si la cumplieron... tema aparte).  Pero bueno, un dato importante que me olvidé de poner es que si la pongo en una máquina con windows... esto CHARÁN!!! no ocurre!
Este tipo de errores me rompe mucho... por ejemplo ahora la estoy usando mientras escribo (en Ubuntu) y por supuesto todo está O.K... qué cosa rara... espero a alguien se le ocurra otra cosa.  Igual seguiré probándola con guindos a ver si pasa algo...

Saludos

---

### Post by Hei Ku on 2008-12-15
Te fijaste que no sea la temperatura? Como es algo que ocurre despues de un rato, quizas sea eso.

---

### Post by erdosain9 on 2008-12-16
Cómo podría fijarme la temperatura de la placa de video??? igual miré el ventilador y va bien la velocidad... pero bueno, cómo hago??

P.d.: adelantando algo aún no probado 100% he sacado los efectos del compiz... es decir en apariencia saqué todo (ojo que no tenía ninguna gran cantidad de efectos sino sólo lo básico, es decir: "Normal"... y desde ayer lo puse en ninguno y no ha vuelto a ocurrir el error... es raro no?

pero bueno, aún no canto victoria....

---

### Post by hictio on 2008-12-16
> **erdosain9 said:**
> Cómo podría fijarme la temperatura de la placa de video??? igual miré el ventilador y va bien la velocidad... pero bueno, cómo hago??

Probaste con 'nvidia-settings' ?

```

sudo aptitude install nvidia-settings

```

Después la accedés desde:

System > Administration > NVIDIA X Server settings

Una vez abierto, fijate la opción "Termal Monitor", acá tengo algunas notas de cuando la instalé en Hardy: [NVIDIA configuration utility](http://oesediez.blogspot.com/2008/10/nvidia-configuration-utility.html)

---

### Post by erdosain9 on 2008-12-16
jejeje... justo edité el mensaje... ahora veo lo que me mencionaste!

---

