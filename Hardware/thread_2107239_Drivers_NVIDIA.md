---
title: "Drivers NVIDIA"
date: 2013-01-21
forum: Hardware
---

### Post by frankom3 on 2013-01-21
hola mi nombre es franco y soy nuevo en esto de ubuntu. hace dos días instale ubuntu 12.04 lts y ahora quiero familiarizarme con este sistema operativo. una de mis primeras dudas es como saber si tengo bien instalados los controladores de video. Mi PC es una Semprom 2800 con 1GB de ram y una placa de video Geforce FX 5500. Como se si tengo todos sus controladores instalados correctamente?

---

### Post by dirty fingers on 2013-01-29
te referís a los controladores de código privado o los libres ?

---

### Post by guillermolisi on 2013-01-30
> **frankom3 said:**
> hola mi nombre es franco y soy nuevo en esto de ubuntu. hace dos días instale ubuntu 12.04 lts y ahora quiero familiarizarme con este sistema operativo. una de mis primeras dudas es como saber si tengo bien instalados los controladores de video. Mi PC es una Semprom 2800 con 1GB de ram y una placa de video Geforce FX 5500. Como se si tengo todos sus controladores instalados correctamente?
Lo mas concluyente, IMHO, es ver la salida del log de Xorg: ```
sudo less /var/log/Xorg.0.log
``` No solo te permitira ver que controladores esta considerando el Xserver sino tambien si estan funcionando bien o son reemplazados y por cual (en general, si tenes una placa con aceleracion grafica el reemplazo se realiza por el driver Noveau).

---

