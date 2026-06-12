---
title: "Musica se traba"
date: 2009-09-21
forum: Hardware
---

### Post by sitiomatic on 2009-09-21
Hola, tengo un problemita pavo pero que me tiene loco.
Cuando escucho musica, la misma se traba, probe con rhythmbox y con exaile y en los dos casos pasa lo mismo.
El procesador no esta al mango, apenas 10% y memoria hay 2 gigas.
Alguien me da una mano para arreglarlo?
Uso ubuntu 9.04 kernel 2.6.31
Si tengo que postear algo de la config, please indiquenme que, soy un usuario light pero abandone definitivamente el lado oscuro :P y esto me tiene podrido

---

### Post by pablo.s on 2009-09-21
Pregunta:
¿Si usás otro núcleo te
sucede lo mismo?

---

### Post by sitiomatic on 2009-09-21
No recuerdo haber tenido problemas, pero con otro nucleo tengo miles de problemas con el video (intel)
Cambie el nucleo para arreglar los problemas de video
Voy a probar bootear con alguno anterior

---

### Post by pablo.s on 2009-09-21
El 2.6.31 es el de Ubuntu PPA
o es compilado por vos?

---

### Post by sitiomatic on 2009-09-21
No lo compile, lo baje de [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31/)
Usando el 2.6.28 pareceria trabarse menos pero igual se traba. El tema es que no puedo usar ese kernel por el video

---

### Post by pablo.s on 2009-09-21
Con respecto al tema de
actualizaciones, tenés 
pendiente los paquetes de
GStreamer y/o PulseAudio
para ser actualizados?

---

### Post by sitiomatic on 2009-09-21
Que yo sepa no, siempre actualizo lo que me aparece.
Tendria que agregar algun repositorio por haber cambiado el nucleo?

---

### Post by pablo.s on 2009-09-21
No. Podemos probar
un ajustecito que quizá
solucione el problema.
Escribí esto en una terminal
```
gksudo gedit /etc/pulse/daemon.conf 
```
y pegá en un post nuevo el
contenido del archivo.

---

### Post by sitiomatic on 2009-09-21
Vi que es la version 0.9.14
Pego el pulse/daemon.conf

; daemonize = no
; fail = yes
; disallow-module-loading = no
; disallow-exit = no
; use-pid-file = yes
; system-instance = no
; disable-shm = no
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB

; high-priority = yes
; nice-level = -11

; realtime-scheduling = no
; realtime-priority = 5

; exit-idle-time = 20
; module-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; load-default-script-file = yes
; default-script-file = 

; log-target = auto
; log-level = notice

resample-method = src-linear
; disable-remixing = no
; disable-lfe-remixing = yes

; no-cpu-limit = no

; rlimit-fsize = -1
; rlimit-data = -1
; rlimit-stack = -1
; rlimit-core = -1
; rlimit-as = -1
; rlimit-rss = -1
; rlimit-nproc = -1
; rlimit-nofile = 256
; rlimit-memlock = -1
; rlimit-locks = -1
; rlimit-sigpending = -1
; rlimit-msgqueue = -1
; rlimit-nice = 31
; rlimit-rtprio = 9
; rlimit-rtttime = 1000000

; default-sample-format = s16le
; default-sample-rate = 44100
; default-sample-channels = 2

default-fragments = 8
default-fragment-size-msec = 10

---

### Post by pablo.s on 2009-09-21
Bueno, lo que debés
modificar es lo que está
resaltado en rojo.
Vas a darle a reproducir
fragmentos más pequeños
y ver si se sigue trabando.

```
; daemonize = no
; fail = yes
; disallow-module-loading = no
; disallow-exit = no
; use-pid-file = yes
; system-instance = no
; disable-shm = no
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB

; high-priority = yes
; nice-level = -11

; realtime-scheduling = no
; realtime-priority = 5

; exit-idle-time = 20
; module-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; load-default-script-file = yes
; default-script-file = 

; log-target = auto
; log-level = notice

resample-method = src-linear
; disable-remixing = no
; disable-lfe-remixing = yes

; no-cpu-limit = no

; rlimit-fsize = -1
; rlimit-data = -1
; rlimit-stack = -1
; rlimit-core = -1
; rlimit-as = -1
; rlimit-rss = -1
; rlimit-nproc = -1
; rlimit-nofile = 256
; rlimit-memlock = -1
; rlimit-locks = -1
; rlimit-sigpending = -1
; rlimit-msgqueue = -1
; rlimit-nice = 31
; rlimit-rtprio = 9
; rlimit-rtttime = 1000000

; default-sample-format = s16le
; default-sample-rate = 44100
; default-sample-channels = 2

**[COLOR=Red] default-fragments = 4[/COLOR]**
**[COLOR=Red]default-fragment-size-msec = 5[/COLOR]**
```Después que editás este archivo,
guardás y reiniciás la maquina.
Luego probá si se sigue trabando.

---

### Post by sitiomatic on 2009-09-21
Quedo de lujo.
Millon de gracias man, sos un capo :)

---

