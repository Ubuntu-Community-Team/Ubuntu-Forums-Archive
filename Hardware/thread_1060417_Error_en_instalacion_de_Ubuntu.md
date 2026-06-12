---
title: "Error en instalacion de Ubuntu"
date: 2009-02-04
forum: Hardware
---

### Post by NickCis on 2009-02-04
Hola, contagiando a un amigo con el software libre, le estaba ayudando a instalar Ubuntu, ya que no tiene una Pc muy nuevita (Athlon 550mhz y 256mb de ram), opte por el alternate install. Baje el cd, hice un chequeo de Md5, daba bien, meti el cd y hice una prueba de archivos, tambien todo bien sin errores.

Pudo particionar y todo, el error llego cuando empezo a instalar, tiraba errores con archivos corruptos, bajamos de vuelta la imagen, hicimos la prueba de archivos, ningun error, pero al instalar el sistema base siempre daba errores.

Bueno, entonces me lleve el disco rigido de esa maquina, se lo puse a otra de rendimiento muy parecido (Celeron 500hz, 512mb ram), baje de vuelta la imagen, doy a instalar, se tilda la maquina en un Kernel Panic, pruebo varias veces con el mismo resultado.

Entonces le vuelvo a colocar el disco que tenia la maquina originalmente, llega el grub, eligo Ubuntu 8.04, y tilda en ubuntu "Kernel panic", reinicio la computadora teniendo el mismo resultado.

1) Alguien sabe como puedo solucionar el problema de la imagen con los supuestos archivos corruptos? (baje el Ubuntu 8.04 Alternate, desde el servidor argentino)

2)Segun lo que lei, ese problema se aregla haciendo un Memtest, estoy haciendo eso, si alguien tiene mas info de como solucionarlo me viene bien :P

Saludos.

---

### Post by euzkoarima on 2009-02-05
Yo haría dos cosas:

1) verificar el md5 de la imagen que bajaste de internet, para estar seguro que la bajado fue correcto.

2) una vez que lo anterior está ok, grabá la imagen a la menor velocidad que puedas (1 o 2 x). Cuando baje 8.10 y grabé, ese cd no me anduvo en 3 Pc, volví a grabar lento y pude instalar en las 3 sin problemas.

Saludos,
Eduardo

---

### Post by joseluisb on 2009-02-05
Medio caprichoso el error, ¿tendrás algún problema de temperatura?
Me ha sucedido que errores aleatorios en distintas etapas de alguna instalación de Micro$oft se debieron a problemas de calentamiento del micro.

¿no tenés ningún log para adjuntar?
Suerte.

---

### Post by NickCis on 2009-02-05
> **euzkoarima said:**
> 
2) una vez que lo anterior está ok, grabá la imagen a la menor velocidad que puedas (1 o 2 x). Cuando baje 8.10 y grabé, ese cd no me anduvo en 3 Pc, volví a grabar lento y pude instalar en las 3 sin problemas.


Y,, estoy teniendo un problema con este punto, con lo de la maquina Ok :S...

No se cuanto tiene que tardar un memtest, pero ya va como 8hs seguidas y esta en el Test 2 46% y si entiendo lo que estoy leyendo dice que paso el 0% y tiene 102 millones de errores, puede ser que este disco me halla jodido la pc :S.

Saludos.

---

### Post by NickCis on 2009-02-05
> **joseluisb said:**
> Medio caprichoso el error, ¿tendrás algún problema de temperatura?
Me ha sucedido que errores aleatorios en distintas etapas de alguna instalación de Micro$oft se debieron a problemas de calentamiento del micro.

¿no tenés ningún log para adjuntar?
Suerte.

Mira la pc andaba totalmente normal, sin ningun problema hasta que le puse el otro disco rigido (40gb), ahi empezaron a saltar "Kernel Panic", le volvi a poner el que tenia originalmente (18gb) y ahora no inicia Ubuntu, como lo hacia antes...

No puedo ni ingresar a ubuntu, cuando prende dsp del grub, dice "Kernel Panic", actualmente estoy haciendo un memtest,,, pero no se cuanto tiene qe tardar ya estubo mas de 8hs y sigue en el test 2, 45% , con mas o menos 108 millones de errroes :S...

Saludos.

---

### Post by joseluisb on 2009-02-05
Ok. En base a la cantidad de errores que te tira yo no seguiría adelante con el testmem. No creo que 110mill de errores sea peor que 108mill.

Probaría con un live Cd...
Cambiaría el chip de memoria (si tenes otro) 
Incluso hasta probaría ver que dice el WinUE.
Suerte

---

### Post by Hei Ku on 2009-02-05
El memtest prueba la memoria. Probablemente se te rompio un banco de memoria. Lo mas probable es por sobrecalentamiento o algo similar.

---

### Post by NickCis on 2009-02-05
Bueno, le volvi a poner las memorias viejas que tenia esta pc (128mb), dsp probe las qe daban error y el error desaparecio magicamente :S...

Muy extraño, pero se soluciono el problema,,,

Saludos.

---

### Post by Hei Ku on 2009-02-05
No sera un tema de temperatura?

---

### Post by NickCis on 2009-02-05
> **Hei Ku said:**
> No sera un tema de temperatura?
Me parece que no, pero no tengo forma de saberlo,,, Es una compaq Presario 5473, capas tenia una incompatibilidad con el disco rigido, lo que no entiendo es por que el problema se soluciono sacando las memorias poniendo otras y dsp volviendo a poner las que tenia antes.
En esta compaq, no se por que, pero no se puede acceder al bios, todo se configura solo (cambio de disco, booteo x cd, por disquet, cambio de ram), asi que capas el cambio del hardware hizo que se borre una mala configuracion, generada por el nuevo HD

No entiendo mucho de esto :S...

Saludos.

---

