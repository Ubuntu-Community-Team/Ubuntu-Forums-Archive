---
title: "El GRUB puede dañar un disco duro?"
date: 2010-01-26
forum: Hardware
---

### Post by Miss Fenriz on 2010-01-26
En primer lugar; agradezco la ayuda de la comunidad que fue esencial para arreglar mi anterior problema. Ahora tengo otro altercado que necesito discutir, pero requiero la ayuda de gente que este mucho mas interiorizada que yo en este tema (llevo casi dos años con Ubuntu, pero aun me siento una novata) puesto que es de suma importancia para mi saber si esto es posible.

Sucede que yo tenia como disco duro principal un disco duro Seagate de 80 gb. el cual fue comprado para armar este pc. La persona que armo este computador se encargo de instalarlo y dejarlo con Windows XP, pero al traerlo a casa decidi de inmediato hacer una particion e instalar Ubuntu Karmic Koala. Todo bien hasta ahi. Luego el pc funciono correctamente por alrededor de dos meses, hasta que mi hermano -mientras jugaba en Windows- me aviso que la pantalla habia quedado negra sin ningun tipo de accion. Despues de millones de intentos de reinstalacion fallidos quede funcionando solo con Ubuntu en mi pc (lo cual para mi es bueno, pero comparto equipo con mi hermano y a el no le gusta).

El tecnico que armo el pc lo unico que hizo todo el tiempo fue reinstalar Windows. Yo le decia que el disco duro al girar daba ruido pero me insistia con que solo era problema de software. Como formateo todo yo volvi a particionar y reinstalar Ubuntu, justo antes que el disco fallara nuevamente. Le lleve el pc a este tipo y concluyo que era el disco duro el que habia fallado, pero que el no podia responder por el disco y el arreglo ya que el problema era el siguiente:

**Segun el, al instalar Ubuntu y su GRUB lo que hacia era dañar Windows, su metodo de arranque y por lo tanto el sector cero del disco duro. Me dijo que no se debian tener dos sistemas operativos con sistemas de archivo diferentes trabajando a la vez e hizo especial enfasis en que Ubuntu es un sistema malo, ineficiente, que daña la integridad de Windows y que no debia ser usado por gente inexperta o con nulos conocimientos de informatica.**

A eso viene este largo tema, pues el no quiere responder (el pc tiene un par de meses y aun esta en garantia) ya que dice que la culpa fue mia por instalar un producto como Ubuntu, siendo que el entrego el computador con Windows XP y eso era suficiente para cualquier cosa. 

**Quiero saber si realmente el GRUB puede dañar un disco duro**. Yo siempre tengo cuidado de instalar Windows primero y luego Ubuntu para evitar dramas con el GRUB... nunca habia tenido problemas hasta ahora, que aquel tecnico se niega a responder por el arreglo de mi computador y culpa a Ubuntu de haber arruinado mi disco. No se que hacer, quiero discutirle con bases y exigirle que responda por el pc que armo, pues no creo que por ser asi deba funcionar con Windows toda la vida.

Agradezco desde ya toda respuesta, saludos!

---

### Post by bichopro on 2010-01-27
No...

asi de simple.

---

### Post by nopersona on 2010-01-27
> **Miss Fenriz said:**
> **Segun el, al instalar Ubuntu y su GRUB lo que hacia era dañar Windows, su metodo de arranque y por lo tanto el sector cero del disco duro. Me dijo que no se debian tener dos sistemas operativos con sistemas de archivo diferentes trabajando a la vez e hizo especial enfasis en que Ubuntu es un sistema malo, ineficiente, que daña la integridad de Windows y que no debia ser usado por gente inexperta o con nulos conocimientos de informatica.**

Uf! Con esa calidad de técnicos :popcorn:

Y la respuesta a tu pregunta; NO.

---

### Post by Carlos C on 2010-01-27
Hola. Mira, como ya te dijeron la respuesta es no. Si la falla es de hardware el debe responder, pero como parece que no quiere hacerlo te recomiendo que acudas al **[Sernac]("http://www.sernac.cl/")**. Entra a su página web y rellenas un formulario. Eso hará que la gente de Sernac se contacte con él y si no llegan a un acuerdo por las buenas te pedirán que acudas a una de sus oficinas para dar inicio a una acción legal. Yo lo hice una vez y puedo decirte que funciona, en general nadie quiere meterse con el servicio nacional del consumidor.

Saludos.

---

### Post by Miss Fenriz on 2010-01-27
Gracias a todos por responder, la verdad tenia miedo de enfrentarme a esto pues es una pregunta bien tonta... pero me complicaba el siquiera pensar que podia ser posible.

Lo malo de esto es que el pc fue comprado por mi familia sin previa consulta. Por eso ahora que vi las fallas he tomado yo el asunto y me he puesto a investigar y reclamar, pues en mi casa estan convencidos que fue mi culpa por instalar Ubuntu (cosa que hice antes con otro pc, sin ningun drama).

Tomare en cuenta la recomendacion de acudir al Sernac, pues mañana en la tarde debo ir a ver si me responden por el disco duro y si no me vere obligada a tomar medidas mas drasticas.

Un saludo a todos!

---

### Post by xtremox on 2010-02-09
el grub no te daña el discoduro a lo mas por una mala maniobra te molestara en el boot pero se arregla facilmente reinstalando el grub ```
sudo aptitude install grub
``` en el terminal

**pero de ahi a dañar de forma fisica el hardware NO**

---

