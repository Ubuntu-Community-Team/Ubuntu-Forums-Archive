---
title: "Consulta: que me aconsejan KK amd64 o 32 bits"
date: 2009-11-27
forum: Hardware
---

### Post by leonardomdq on 2009-11-27
Hola gente, hace unos dias cambie mi pc y quiero hacerles una consultas antes de instalar el nuevo KK 9.10.
Tengo procesador AMD Athlon 7750 Black Edition dual core 2.70 GHZ , mother Gigabyte GA-MA74GM-S2 con video ATI Randeon 2100 integrada.
La duda que si instalado **ubuntu 9.10 desktop amd64 **o **ubuntu 9.10 32 bits**

Desde ya gracias y espero me puedan guiar. Saludos ;)

---

### Post by albandy on 2009-11-27
Depende de la cantidad de memoria que tengas instalada.
Si tienes 3GB o más te recomiendo 64 bits, ya que si no el kernel utilizará PAE para acceder a toda la memoria.

Si tienes que utilizar alguna aplicación de fuera de los repositorios que sea de 32 bits siempre es mejor hacerlo de forma nativa que a traves de las ia32-libs (se utilizan para correr aplicaciones de 32bits cuando tu sistema operativo es de 64bits), aunque por norma general siempre suele funcionar bien.

Yo tengo un portatil intel dual core con 2GB de memoria y estoy utilizando la de 64 bits y solo puedo decir que funciona genial.

---

### Post by leonardomdq on 2009-11-27
Gracias albandy por contestar.
De memoria ram tengo 2 GB, entonses por lo que me decis me conviene instalar la version 9.10 de 32 bits.

---

### Post by Tosh78 on 2009-11-29
Si, yo tambien te recomiendo que si tenes 3gb o menos de ram instales la de 32.

---

### Post by dirty fingers on 2009-11-29
uso 64bit con 1GB sin problema. mismo consumo de ram a simple vista y mejor rendimiento del micro.

---

### Post by sergiom99 on 2009-11-29
y el tema de flash y otras aplicaciones en 64 bits?

---

### Post by oktubrer on 2009-11-29
> **sergiom99 said:**
> y el tema de flash y otras aplicaciones en 64 bits?

Te diría que ya funcionan en forma nativa sin problemas (o mejor dicho con los mismos problemas naturales de flash en 32 bits).

---

### Post by guillermolisi on 2009-11-29
En la [lista de soporte]("http://old.nabble.com/-ubuntu-ar--32-o-64--to26442994.html") hubo un intercambio parecido hace unos dias atras.

---

### Post by leonardomdq on 2009-11-30
Muchas gracias por todas las respuestas, por lo leido voy a instalar KK 32 bits.

Saludos y gracias nuevamente.

---

