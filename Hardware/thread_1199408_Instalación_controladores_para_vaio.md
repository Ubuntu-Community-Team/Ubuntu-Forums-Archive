---
title: "Instalación controladores para vaio"
date: 2009-06-28
forum: Hardware
---

### Post by Foxtrot_35 on 2009-06-28
Hola Amigos, soy nuevo en Ubuntu, y deseo que los que tengan experiencia en éste SO me puedan ayudar.....se trata de lo siguiente, tengo un Vaio VGN SZ450fn e instale UBUNTU 9.04 todo ok...pero nosé que procedimientos seguir para instalar por ejemplo, webcam integrada, las teclas FN, la función stamina/speed, micrófono integrado, el lector biométrico, etc......es mucho pedir?? disculpen mi ignorancia...espero su cooperación, saludos

---

### Post by CdK1 on 2009-06-29
Desafortunadamente no tengo uno de esos :(, pero en tú caso haría lo siguiente, ir por partes, si quieres configurar el video, da las especificaciones etc, -lspci-, así con la webcam, etc, etc, etc....

look this;

[http://ubuntuforums.org/showthread.php?t=37469](http://ubuntuforums.org/showthread.php?t=37469)

---

### Post by Carlos C on 2009-06-29
Este thread es demasiado general y veo difícil que alguien te ayude por esa razón. En el caso de que alguien lo haga terminarán mezclándose varios temas y será un desorden. Cierro el thread y te pido que presentes los temas por separado, dando siempre toda la información necesaria (versión de Ubuntu, características del hardware, salida del comando "lspci").

Ante cualquier duda te sugiero siempre leer el siguiente thread:

[http://ubuntuforums.org/showthread.php?t=1162750](http://ubuntuforums.org/showthread.php?t=1162750)

Gracias por tu colaboración.
Saludos.

---

### Post by moreback on 2009-06-29
Estimado Foxtrot_35:

Por tu pregunta puedo deducir que vienes del mundo Windows donde cada hardware viene con su disco de drivers para que los reconozca. En Ubuntu no es necesario tener discos de drivers, la mayoría ya viene integrado en el mismo sistema y es altamente probable que ya te lo haya reconocido, por lo que sólo necesitas verificar que estén funcionando.

Por ejemplo, para verificar que tu cámara haya sido reconocida, puedes ir a **Sistema -> Preferencias -> Selector de sistemas multimedia** y luego pulsar en la pestaña **Vídeo** y revisar las opciones de **Entrada predeterminada**. Acá el botón de **Prueba** te va a servir para verificar tu cámara.

Si está todo bien, podrías instalar el Cheese para que le saques mayor provecho a tu cámara ```
apt-get install cheese
```Las teclas Fn es cosa que las pruebes.

El micrófono integrado lo verificas con **Aplicaciones -> Sonido y vídeo -> Grabador de sonido** y haciendo los ajustes necesarios en **Sistema -> Preferencias -> Sonido**.

La función stamina/speed no se qué es y lo del lector biométrico no sé como se verifica, así que para estos dos es mejor que abras un post por cada uno.

Saludos.

---

### Post by Carlos C on 2009-06-29
Este thread es demasiado general y terminarán mezclándose varios temas, lo que generará un desorden. Cierro el thread y te pido que presentes los temas por separado, dando siempre toda la información necesaria (versión de Ubuntu, características del hardware, salida del comando "lspci").

Ante cualquier duda te sugiero siempre leer el siguiente thread:

[http://ubuntuforums.org/showthread.php?t=1162750](http://ubuntuforums.org/showthread.php?t=1162750)

Gracias por tu colaboración.
Saludos.

---

