---
title: "Qué versión de Ubuntu instalar en la HP All-in-One 200-5030 PC"
date: 2010-06-02
forum: Hardware
---

### Post by leosr on 2010-06-02
Hola.
Estoy por comprar una HP All-in-One 200-5030 PC [http://h10010.www1.hp.com/wwpc/ar/es/ho/WF06b/12454-12454-4144617-4144618-4144618-4147564-4182923.html?lang=es&jumpid=oc_R1002_ARESC-001_PC%20de%20sobremesa%20HP%20All-in-One%20200-5030la&cc=ar]("http://h10010.www1.hp.com/wwpc/ar/es/ho/WF06b/12454-12454-4144617-4144618-4144618-4147564-4182923.html?lang=es&jumpid=oc_R1002_ARESC-001_PC%20de%20sobremesa%20HP%20All-in-One%20200-5030la&cc=ar")
Tiene 4 gb de ram, qué versión de Ubuntu conviene, 32 o 64 bits?
Alguien sabe si Ubuntu Lucid me va a reconocer todo el hardware?

Saludos.

---

### Post by guillermolisi on 2010-06-03
Si llegas a usar 64 bits con 4Gb RAM vas a ver toda la memoria pero tendras un uso adicional porque los SOs de 64b consumen mas RAM que los de 32. Sobre este tema hay por lo menos un par de threads.
Si usas 32b posiblemente no veas completamente los 4Gb por las caracteristicas de la arquitectura Intel (genericamente hablando).

Entonces habria que ver que diferencias de consumo observas con uno y otro al mismo tiempo que revisas si todo el hardware es correctamente reconocido por Ubuntu con los correspondientes LiveCDs.

---

### Post by leosr on 2010-08-06
> **guillermolisi said:**
> Si llegas a usar 64 bits con 4Gb RAM vas a ver toda la memoria pero tendras un uso adicional porque los SOs de 64b consumen mas RAM que los de 32. Sobre este tema hay por lo menos un par de threads.
Si usas 32b posiblemente no veas completamente los 4Gb por las caracteristicas de la arquitectura Intel (genericamente hablando).

Entonces habria que ver que diferencias de consumo observas con uno y otro al mismo tiempo que revisas si todo el hardware es correctamente reconocido por Ubuntu con los correspondientes LiveCDs.

Hola. Finalmente me compré la HP, no pude instalar Ubuntu 10.04 de 64 ni de 32 bits. La pc se queda congelada y muestra lo que se ve en la imagen adjunta.

Alguna idea? Por ahora estoy usando W7, no me desagrada pero extraño Ubunu.

Saludos.

---

### Post by euzkoarima on 2010-08-06
Probá de usar la opción "F6 Other Options" y dentro de eso marcar "acpi=off" cuando arranca el livecd.

Saludos,
Eduardo

---

### Post by leosr on 2010-09-10
> **euzkoarima said:**
> Probá de usar la opción "F6 Other Options" y dentro de eso marcar "acpi=off" cuando arranca el livecd.

Saludos,
Eduardo

Hola.
Funciona eso; hay forma de que no tenga que hacerlo cada vez que prenda la PC?
Gracias!

Salu2

---

### Post by yaserdiel on 2011-02-03
Logre instalar el ubuntu 10.x en mi pc hp all in one, pero al momento de seleccionar el sistema operativo se congela la pc, y no me permite usar la tecla f6 al presionarla de la misma manera se congela el sistema que puedo, hacer. Alguien me puede ayudar????? De antemano mil gracias

---

### Post by elcorazondelator23 on 2012-03-27
Yo tuve el mismo problema con "HP ALL IN ONE 200", y luego de un tiempo encontré la solución aquí:
[https://bugs.freedesktop.org/show_bug.cgi?id=43171#c15](https://bugs.freedesktop.org/show_bug.cgi?id=43171#c15)

el problema está en el módulo i915 ( "creo"por lo que entendí al mirar el código del  parche, el problema tiene que ver con el monitor integrado)

también en la página dejan la sig dirección para descargar los kernels con el parche ya incluido:
[http://www.rapido.net.br/debs_hpomni200/](http://www.rapido.net.br/debs_hpomni200/)


*en mi caso preferí aplicar el parche al modulo, compilar este modulo separado y remplazarlo en mi kernel.
*sin tener que compilar todo el kernel, y sin cambiar de kernel, y mantener el original de ubuntu

si les interesa mi solución cuando tenga tiempo armo un tutorial.


con respecto a la distribución a elegir , creo que ninguna distribución soporta esa configuración de harware (grande "HP all in one 200"), ya que el problema radica en el kernel...( yo probé antes de saber esto, con susse, fedora ubuntu, y alguna mas, inutilmente).


saludos y suerte

---

### Post by elcorazondelator23 on 2012-03-30
AcA publiqué el tutorial

[http://ubuntuforums.org/showthread.php?p=11805235#post11805235](http://ubuntuforums.org/showthread.php?p=11805235#post11805235)

Saludos

---

