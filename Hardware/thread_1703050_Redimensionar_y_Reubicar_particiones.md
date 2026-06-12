---
title: "Redimensionar y Reubicar particiones"
date: 2011-03-08
forum: Hardware
---

### Post by mano negra on 2011-03-08
Buenas,
   Resulta que necesito redimensionar el disco rígido porque necesito usar si o si un programa en el win que ocupa mucho mucho. Lo que iba a hacer era sacar espacio a la partición /home y listo, con el gparted desde el cd live de ubuntu. El tema es que la partición de win está primero y la /home última. El tema es que el espacio libre que genero no lo puedo mover y así agrandar la partición de win. Por lo menos el gparted no me deja.
  Alguien sabe que se puede hacer sin necesidad de formatear ubuntu? 
Salud!

---

### Post by guillermolisi on 2011-03-08
Deberias mover las particiones hasta lograr que ese espacio libre este contiguo a la particion que queres incrementar de tamaño.

---

### Post by mano negra on 2011-03-08
> **guillermolisi said:**
> Deberias mover las particiones hasta lograr que ese espacio libre este contiguo a la particion que queres incrementar de tamaño.
Claro, pero no se como hacerlo con el gparted. O en todo caso desconozco si lo puede hacer.

---

### Post by sebasthian777 on 2011-03-08
> **mano negra said:**
> Claro, pero no se como hacerlo con el gparted. O en todo caso desconozco si lo puede hacer.

Yo tengo que hacer algo parecido.

Creo que lo que dice Guillermo es que vayas redimensionando particiones desde el final hasta el principio hasta lograr el cambio que queres. El tema, y aquí mi pregunta.

Siempre y cuando se respete el espacio libre y no se exagere la MB a redimencionar, 
¿Corre algún riesgo la integridad de datos al re-dimensionar reiteradas veces varias particiones?
¿Se corre algún tipo de riesgo diferente al que mencione?

o sea, en modo gráfico a modo de ejemplo.

Tengo 4 particiones:
A,B,C,D.

A=100Mb, B=100Mb, C=100Mb, D=100Mb.

Objetivo: dejar a la partición A con 150Mb.

Pasos:
1) Achico D y la dejo en 50Mb. y agrando C a 150Mb.
2) Achico C a 100Mb, y agrando B a 150Mb.
3) Achico B a 100Mb y agrando A a 150Mb
Resultado:

A=150Mb, B=100Mb, C=100Mb, D=50Mb.

Esto se puede hacer tal cual así? sin correr ningún riesgo?

---

### Post by gmunioz on 2011-03-09
*"...Esto se puede hacer tal cual así? sin correr ningún riesgo?..."*
**NO.**
Toda modificación de particiones, genera un cierto riesgo de pérdida de datos. aún mayor cuando se trata de un caso como el de este post.
Hace muchos años que no uso Windows, pero estimo que es capaz de utilizar un programa *(un programa en el win que ocupa mucho mucho)*desde otra partición.
me parece que lo mas practico es:
Desde una sesión cd-live, desmontar la partición a modificar, reducirla y crear en el espacio liberado una nueva en sistema de archivos ntfs, para instalar en ella ese programa windows.
Solo queda controlar que la UUID de la partición reducida no cambió, si cambió, hacer las modificaciones necesarias en el archivo /etc/fstab

---

### Post by EnriqueK on 2011-03-09
En primer lugar te recomiendo instalar Xp en VirtualBox, si no te satisface, prueba con usar Remastersys para crear un Live DVD de tu actual instalación de Ubuntu, usa la opción "dist·" así no respaldas tu carpeta de usuario que debes dejar sin tocar, luego instala Xp en sda1 , seguidamente Ubuntu lo instalas en el espacio que quitaste de /home usando el Live DVD que creas con Renastersys y si lo haces con criterio y cuidado, vas a poder lograrlo con el menor esfuerzo de máquina ya que el estar movienndo partuciones require mucho tiempo con el procesador al mango

[http://geekconnection.org/remastersys/](http://geekconnection.org/remastersys/)
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by guillermolisi on 2011-03-09
> **EnriqueK said:**
> .... vas a poder lograrlo con el menor esfuerzo de máquina ya que el estar movienndo partuciones require mucho tiempo con el procesador al mango

[http://geekconnection.org/remastersys/](http://geekconnection.org/remastersys/)
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)
.... y que no se corte el suministro de energia electrica en medio del proceso de reconfiguracion de las particiones.

---

