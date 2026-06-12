---
title: "Problemas con conexión internet"
date: 2009-05-19
forum: Hardware
---

### Post by harryscode on 2009-05-19
Hola.. tengo que siguiente problema. Estoy conectado con cable de red desde un SmartAX MT882 de Arnet. Si enciendo el modem antes de encender la pc, la conexión esta perfecta. Pero si enciendo la pc antes que el modem no se conecta. Me muestra en el ícono de gestión de red que no hay conexión disponible. Tengo tildado el Activar Red, lo destilo y lo vuelvo a tildar y no pasa nada. Mucha noción no tengo, ya que migré hace poco de XP, no se como modificar eso, ya que si bien no me cuesta nada encender el modem antes, me gustaría que se conecte sin tener que pensar en eso, ya que para que se conecte tendría que reiniciar el sistema. Gracias.
Estoy usando Xubuntu 9.04.

---

### Post by guillermolisi on 2009-05-19
> **harryscode said:**
> Hola.. tengo que siguiente problema. Estoy conectado con cable de red desde un SmartAX MT882 de Arnet. Si enciendo el modem antes de encender la pc, la conexión esta perfecta. Pero si enciendo la pc antes que el modem no se conecta. Me muestra en el ícono de gestión de red que no hay conexión disponible. Tengo tildado el Activar Red, lo destilo y lo vuelvo a tildar y no pasa nada. Mucha noción no tengo, ya que migré hace poco de XP, no se como modificar eso, ya que si bien no me cuesta nada encender el modem antes, me gustaría que se conecte sin tener que pensar en eso, ya que para que se conecte tendría que reiniciar el sistema. Gracias.
Estoy usando Xubuntu 9.04.
Y por que apagas el modem ? Consume menos que una lampara de bajo consumo de baja potencia.

---

### Post by harryscode on 2009-05-19
> **guillermolisi said:**
> Y por que apagas el modem ? Consume menos que una lampara de bajo consumo de baja potencia.
Jaja.. ok.. fuera de eso... mi pregunta apunta a ¿es así?... no hay forma de conectarse si por descuido desenchufo el modem y se corta la señal, tengo que reiniciar el sistema?.. ¿no se conecta automáticamente?... las respuestas se que son más que obvias, tal cual la tuya guille, mi intención es buscar un poco más y aprender un poco más. No encontré mucho respecto a esto por eso preguntaba. Gracias de todos modos.

---

### Post by dirty fingers on 2009-05-19
me pinta que lo que anda mal es el modem, no la pc.
Dejalo prendido , fue, hay cosas mas terribles para preocuparse. jajaja sin entrar en el chiste de lo que consume obvio (300mA como mucho) :p

---

### Post by Hei Ku on 2009-05-19
Podes probar con poner en la consola:

sudo /etc/init.d/networking restart

---

### Post by guillermolisi on 2009-05-19
> **harryscode said:**
> Jaja.. ok.. fuera de eso... mi pregunta apunta a ¿es así?... no hay forma de conectarse si por descuido desenchufo el modem y se corta la señal, tengo que reiniciar el sistema?.. ¿no se conecta automáticamente?... las respuestas se que son más que obvias, tal cual la tuya guille, mi intención es buscar un poco más y aprender un poco más. No encontré mucho respecto a esto por eso preguntaba. Gracias de todos modos.
Te entiendo perfectamente y disculpa que no pude aportar algo mas alla de lo obvio pero me llamo la atencion el hecho de apagar el modem. :)

Lo que se me ocurre podria servir es reiniciar el servicio o demonio que permite este tipo de conexiones, para no tener que reiniciar la maquina completa.

Por ejemplo, si necesitas reiniciar los servicios de red, tenes que ingresar en una terminal/consola: ```
sudo /etc/init.d/networking restart
```que es lo mismo que ingresar esa linea con "stop" y luego con "start" (como para que elijas tu forma de reinicio).

---

### Post by harryscode on 2009-05-19
> **guillermolisi said:**
> Te entiendo perfectamente y disculpa que no pude aportar algo mas alla de lo obvio pero me llamo la atencion el hecho de apagar el modem. :)

Lo que se me ocurre podria servir es reiniciar el servicio o demonio que permite este tipo de conexiones, para no tener que reiniciar la maquina completa.

Por ejemplo, si necesitas reiniciar los servicios de red, tenes que ingresar en una terminal/consola: ```
sudo /etc/init.d/networking/interfaces restart
```
que es lo mismo que ingresar esa linea con "stop" y luego con "start" (como para que elijas tu forma de reinicio).

jaja.. ok.. costumbres vio.. no dejo encendido ni el televisor.. como con Xp nunca tuve dramas pensé que debía configurar algo para que sea igual. Lo mismo ya agendé todo para probar en otro momento. Veremos que tal anda. Gracias por la ayuda.

---

### Post by guillermolisi on 2009-05-19
Fe de erratas: donde dice " ..../networking/interfaces restart" debe leerse "..../networking restart"

Ya estoy cumpliendo la penitencia autoimpuesta de escribir 1000 veces "/etc/init.d/networking restart" :D

Disculpen ...

---

