---
title: "Hora del sistema se retrasa"
date: 2009-09-21
forum: Hardware
---

### Post by akiestudio on 2009-09-21
Pues eso que no se porque , la hora del sistema siempre anda mal , se retrasa, siempre que la cambio en reloj del escritorio que me dice que si quiero que sea la hora del sistema y le dijo que si , se guarda pero cuando vuelvo a reiniciar el laptop la hora esta retrasada...Como puedo solucionar esto?

---

### Post by Hei Ku on 2009-09-21
> **akiestudio said:**
> Pues eso que no se porque , la hora del sistema siempre anda mal , se retrasa, siempre que la cambio en reloj del escritorio que me dice que si quiero que sea la hora del sistema y le dijo que si , se guarda pero cuando vuelvo a reiniciar el laptop la hora esta retrasada...Como puedo solucionar esto?

Esta retrasada 3 horas al reiniciar?

---

### Post by akiestudio on 2009-09-21
No necesariamente , a veces unas horas otras veces unos 30 minutos y algunas veces unos minutos...Ahora mismo al iniciar esta 15 minutos retrasados

---

### Post by guillermolisi on 2009-09-21
Que reloj usas ? Es un screenlet/gdesklet, un comando en consola (date), otros medios ?

---

### Post by akiestudio on 2009-09-21
Pues no se muy bien, es el reloj que te instala ubuntu 9.04 por defecto y que esta en la barra superior, pero si ejecuto por un terminal date: la hora que me da tambien esta mal, cuando en el reloj de la barra superior te da la opcion de configurar la hora como si fuese la hora del sistema y la pongo bien , hago un date en un terminal y queda bien configurada hasta que reinicio que es cuando se retrasa el reloj....

---

### Post by sergiom99 on 2009-09-21
Reiniciar o apagar?
Podria ser la pila del mother.

---

### Post by oktubrer on 2009-09-21
Antiguamente si la pila del mother estaba gastada atrasaba el reloj del sistema... no se si será el mismo caso.
Si tenés conectivdad la mayor parte del tiempo podes hacer que sincronice con algún servidor ntp

---

### Post by mama21mama on 2009-09-21
probaste comprar una pila salen baratas, si no es la pila sincroniza la hora por medio de algún servidor. 

Saludos

---

### Post by sergiom99 on 2009-09-21
En mi desktop viejita, la pila del mother esta gastada y cuando esta apagada un tiempo pierde fecha y hora. Como me da fiaca cambiarla, tengo croneado este script para actualizar la hora al arrancar:
```
## horario.sh
#! /bin/bash
ntpdate time.sinectis.com
hwclock --systohc

```

Tambien lo uso en algunas virtuales VMWare que por algun motivo no llevan del todo bien la hora con su servidor.

---

### Post by akiestudio on 2009-09-22
El ordenador no tiene ni 6 meses, y puede ser la pila?¿cada cuanto hay que cambiar la pila?

Sergiom999 ese script donde lo guardo para que inicie cada vez que reinicio el laptop...

---

### Post by sergiom99 on 2009-09-22
> **akiestudio said:**
> El ordenador no tiene ni 6 meses, y puede ser la pila?¿cada cuanto hay que cambiar la pila?

Sergiom99 ese script donde lo guardo para que inicie cada vez que reinicio el laptop...

Para orientarte si es o no la pila, hace la prueba. Si reinicias, no tiene que perder la hora. Si lo tenes apagado un rato largo, ahi puede ser que atrase unos minutos.

En las preferencias del sistema tenes los scripts que arrancan al inicio. Creo que dice Autoejecutar o algo asi.

---

### Post by akiestudio on 2009-09-23
Muchas gracias el script , parece que funciona perfectamente , pero no encontre donde colocarlo en preferencias asi que busque y encontre este link que te explica como hacerlo por terminal 



[http://www.exaquo.com/ejecutar-un-script-al-inicio-de-tu-ubuntu/](http://www.exaquo.com/ejecutar-un-script-al-inicio-de-tu-ubuntu/)

Saludos ,y gracias creo que se puede dar por cerrado el tema.

---

### Post by josecuervo86 on 2009-09-23
Para darlo por cerrado "oficialmente" podes apretar donde dice Thread tools (Arriba a la derecha, en rojo, y luego donde dice *Mark this thread as solved* (o algo asi)

---

### Post by akiestudio on 2009-09-23
Noooo, pensaba que todo estaba bien , pero cuando se reinicia carga la hora correcta , pero me he dado cuenta , que cuando estoy trabajando con el lapto al cabo del tiempo , el reloj se atrasa , vamos que no avanza la hora, de momento solo unos 10 minutos en 2 horas de trabajo....
Cual puede ser el problema?, si es la pila como dice algunos porque no pasa en windows...

---

### Post by Hei Ku on 2009-09-23
No, eso no es la pila.

Proba booteando con las opciones noapic nolapic

---

### Post by akiestudio on 2009-09-24
Hei ku perdona, pero lo que me has dicho me ha sonado a chino:confused:, como se hace eso ...muchas gracias por la ayuda , :guitar:

---

### Post by Hei Ku on 2009-09-24
Alguien puede explicarle como agregar esa opcion al grub? Yo hace rato que no lo hago.

---

### Post by akiestudio on 2009-09-24
Heiku vi un post tuyo donde decias como agregar a un documento 
noapic , noapic.

Pues bien he seguido esos paso y ahora el laptop no arranca normal sale lo siguiente;

Una pantalla en negro:
Bios bug, local api # 0 not detected
Foring use of dumme apic emulation(tell your hw vendor .....)

Despues de un rato sale carga la pantallla de ubuntu donde sale cargando, pero sin entrar al login de usuario.

y despues sale otra pantalla en negro donde dice los siguiente:


Loading pleasse wait ....
gave up waiting for root device common problem

-boot args( cat/proc/cmline) 
 -check rootdelay = (did the system wait long enought?
 -check root = (did the system wait for the right device?
-Missing modules ( cat/proc/modules ; ls /dev)
Alert ! /dev/disk/by -uuid /( AQUI PONE MUCHOS NUMERO) /does not exist Drooping to a shell 
(initramfs)


Y si lo arranco en recovery sale 
una pantalla en negro con muchas letras en blanco y al final:

bigin rumming /scritp/init -bottom done

Y ya esta , que puedo hacer, que ha pasado....

El post  tuyo que lei era que se retrasaba  el reloj y un juego al que juagabas o algo parecido y que editastes una archivo de texto poniendo noapic noapic

Helppp

---

### Post by Hei Ku on 2009-09-24
La opción que explico ahí es editando el menú del grub, pero como es permanente, mejor la otra opción que te sirve para hacer la prueba.

Por lo que veo, pusiste las opciones en el lugar equivocado o tu pc no soporta bootear con esa opcion.

---

### Post by akiestudio on 2009-09-24
Cuano he pobado a bootear dando e; despues seleccionando la opcion de kerne y dando e de nuevo estaba noapic y noapic , despues le di a b , y tampoco funcionaba el laptop asi que volvi a repetir el paso y quite noapic noapic , y acabo de suprimir noapic noapic en menu.lst, y despues actualize , ya que no me funciona el pc con noapic....

Alguna otra sugerencia para lo del reloj

---

### Post by Hei Ku on 2009-09-24
Verifica si tu hora del sistema esta puesta para sincronizar automaticamente. Si ya tenes esa opcion activada, sacala y vas a tener que hacerlo manualmente. Lo que sucede es que si la diferencia supera un cierto valor, se desactiva sola.

En su momento, yo puse una tarea en el cron que llamaba al ntp cada hora. De esta forma la diferencia del reloj nunca superaba mas de unos minutos. En mi caso sucedia porque mi chipset en particular tenia un bug.

---

### Post by akiestudio on 2009-09-24
Como puedo:

Verifica si tu hora del sistema esta puesta para sincronizar automaticamente.

Donde o como lo hago

---

### Post by Hei Ku on 2009-09-24
Supongo que en el applet de la hora o en la configuracion de la hora debes tener alguna opcion. Uso KDE, que es distinto, asi que ahi no puedo ayudarte.

---

### Post by akiestudio on 2009-09-26
Gracias pero no tengo ninguna de esas opciones, ni sincronizar con servidor etc....

---

### Post by Hei Ku on 2009-09-26
Entonces con un cron cada hora, que llame a un script de ntp, que vas a tener que instalarlo, si no lo tenes.

---

