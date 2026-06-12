---
title: "notas sobre cómo elegir hardware"
date: 2009-06-07
forum: Hardware
---

### Post by Kantier on 2009-06-07
estaba pasándole estos tips a un amigo, y se me ocurrió postearlos acá así ayudan a más gente. Estaría copado que esta información esté en sticky, o en la wiki, o en algún lado en el que se vea fácil porque estas son cosas que se preguntan mucho (o que se deberían avisar antes de que uno compre una máquina nueva)

Al momento de escribir esto, acaban de salir la línea de Phenom II (socket AM3) por el lado de AMD y la línea Core i7 (Socket B / LGA 1366) por el lado de Intel. Los AMD para AM3 andan en AM2+, pero la mother tiene que soportarlos. Los Intel para LGA 1366 no andan en otro socket.

micro:[list]
[*] siempre conviene tecnología de fabricación más nueva (menos nm)
[*] en AMD, Phenom II sobre Phenom I, siempre
[*] en Intel, Core i7 sobre Core 2
[*] en Intel, menos nm con 2 core sobre más nm con 4 core
[*] si van a usar una VM, ayuda mucho tener procesadores con hardware que asista a la virtualización (AMD-V o Intel VT-x)[/list]

mother:[list]
[*] en general las mother sin video integrado suelen ser mejores, por el público al que apuntan.
[*] en general las mother con cuatro zócalos de memoria suelen ser mejores, por el público al que apuntan.
[*] hay que mirar el chipset de la mother, los modelos de chipset van variando con el tiempo y hay gamas más altas y más bajas.
[*] si se compra mother con video integrado, el tema de marca de video se aplica al chipset de la mother.
[*] Las mothers AM3 son muy caras, pero no todas la smother AM2+ soportan Phenom II, hay que fijarse esto antes de comprar.
[/list]

video:[list]
[*] Intel (integrado) y NVIDIA (discreto o integrado) tienen drivers para linux que funcionan (aceleración 3D, etc.). Ati es una lotería, por ahora no hay vuelta para eso. (más detalles [acá]("http://ubuntuforums.org/showpost.php?p=7418647&postcount=3"))
[*] Los de NVIDIA tienen mejor performance que los de Intel, pero son cerrados.[/list]


Dónde buscar información:[list]
[*] En wikipedia (inglés) hay tablas actualizadas con todos los modelos de micros Intel y AMD con sus detalles (core, tecnología de fabricación, clock, etc.)
[*] Phoronix tiene benchmarks bajo linux, lo cual está copado para performance de video, pero para ver cuestiones generales de performance de micro/memoria/etc. cualquier página de reviews sirve.[/list]


esto no es de hardware, pero está entre la info que pasé:

64bit vs 32bit:[list]
[*] Si usan 1GB o menos, conviene 32bit porque los programas ocupan un poco menos en memoria (en 64bit las direcciones son más largas).
[*] Si tienen un micro moderno (64bit) y no les molesta la ligera pérdida de RAM, 64bit garantiza algunas instrucciones de procesador que hace más eficientes algunas tareas.
[*] Pasando las 3 y pico gigas de RAM, ubuntu 32bit no detecta la memoria. Lo probé, hay una forma de que lo haga y no está activada en el kernel, es una molestia, pero viene así.
[/list]

---

### Post by rafadev on 2009-06-07
Acá reportándose el amigo de Kantier. Simplemente quería agradecerle públicamente por su ayuda, espero que con estos buenos consejos otra gente sea también beneficiada.

---

### Post by Hei Ku on 2009-06-07
Sip, Gracias!

No coincido con lo de ATI, aunque es cierto que los drivers estan teniendo un momento dificil ultimamente. De todas maneras, yo tengo aceleracion 3D sin problemas con los mios. Y el driver libre tiene aceleracion 3D para las placas que ya no estan soportadas por el privativo.

Acá hay info sobre la instalación del driver libre de ATI, incluyendo las placas soportadas: [https://wiki.ubuntu.com/RadeonDriverHowto](https://wiki.ubuntu.com/RadeonDriverHowto)

Acá hay info sobre la instalación del driver privativo de ATI. En este momento, las placas soportadas son las ultimas, pero algunos modelos tienen problemas y otros andan sin problema. Es una lotería.
[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

---

### Post by staar on 2009-06-08
muy bueno, solo agregar dos cositas:

-memos ddr3 no valen la pena, todavía, no existe aún mucha diferencia de rendimiento con las ddr2...

-los mejores chipset para AMD son los (paradójicamente :-D) AMD, y entre ellos, los mejores traen todos video integrado (que por cierto es excelente en esos chipsets), asi que, si la opción es un micro AMD, los mothers con video integrado son los mejores (OJO, con chipset AMD, no Nvidia)

saludos

---

