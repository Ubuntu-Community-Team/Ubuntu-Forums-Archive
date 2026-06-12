---
title: "Problemas con tarjeta ati y nvidia ubuntu 11.10"
date: 2012-02-01
forum: Hardware
---

### Post by sitodonosti on 2012-02-01
Hola, he querido instalar ubuntu en mis dos ordenadores, uno tiene una ati y la otra una nvidia, el caso es que no se me activa la aceleración gráfica. De hecho si quiero saber si tengo aceleración gráfica me sale esto:

sito:~$ /usr/lib/nux/unity_support_test -p
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  21
  Current serial number in output stream:  21
Tanto en el ordenador nvidia como en la ati. En la de la ati incluso me descarge los drivers de la pagina amd los instale pero al reiniciar se me quedaba en consola sin entorno grafico. Sabéis a q puede deberse?

Edito:he seguido un tutorial y al iniciar me aparece la pantalla en negro con letras y tal jiji
el caso es que me aparece todo ok menos deferred execution scheduler fail

gracias

---

### Post by silpablo on 2012-03-23
paso a explicarte,
vos ni bien instalas ubuntu, te instala automaticamente el driver mesa (libre) que en ciertas ocaciones, por ejemplo placas nvidia y radeon instala una variacion llamada gallium, basada en mesa pero con soporte 2d y 3d.

ahora bien, queda en vos migrar a un driver propietario (driver de amd o de nvidia que te descargas de la pagina)

nunca instale el de nvidia, pero el de ati una ves instalado, tenes que entrar en consola (modo de recuperacion de errores como root) y ejecutar aticonfig --initial

eso seteará los valores por default y no te mostrará esa pantalla negra cuando inicias.

lo mas facil es usar la la aplicacion que trae ubuntu para drivers propietarios porque te salva de tener que meter mano en la configuracion, aunque no siempre funca en todos los casos.

lo que yo te recomiendo si podes es hacer la instalacion limpia de ubuntu xubuntu kubuntu o lo que quieras y usar la opcion de "drivers opcionales" o algo asi qeu esta en el menu para instalar los controladores propietarios de amd y nvidia.

cualquier duda avisa.

---

### Post by sitodonosti on 2012-04-30
Ola, he isntaldo ubuntu 12.04, y sigo teniendo el mismo problema. Intento instalar los privativos desde "controladores adicionales" y me pone "El controlador está activado pero no se está usando actualmente". He desinstaldo nouveau pero sigo sin tener aceleración grafica

es una nvidia GeForce 8600M GT, ahora provaré con la Ati a ver que pasa...

---

