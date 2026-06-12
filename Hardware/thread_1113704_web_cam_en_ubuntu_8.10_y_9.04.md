---
title: "web cam en ubuntu 8.10 y 9.04"
date: 2009-04-01
forum: Hardware
---

### Post by joseluis on 2009-04-01
hola. tengo un problema. 
Seguramente o probablemente esto ya se habra tratado, pero no lo encontre
En ubuntu 8.04 me anda perfecto mi webcam. La detectó al toque en su momento. Como ubuntu 8.10 no la detecta preferí seguir con el 8.04. Probé ahora , por las dudas, con el beta de ubuntu 9.04 y ¡tampoco anda! ¿alguien sabe qué pasa o como se soluciona? sigo con la 8.04, pero quiero actualizar y pasar al 9.04 porque esta bueno todas las mejoras. 
Para datos, cuando pongo el amsn, me detecta v41:flexcam 100 camera; y en canal me dice que es SPCA561. no se que otros datos puedan servir, pero quisiera usar mi cam en ubuntu y pasarme...gracias

---

### Post by Hei Ku on 2009-04-02
Pone el resultado del comando lsusb, asi sabemos bien que modelo es tu camara.

---

### Post by joseluis on 2009-04-02
ok aca va

Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 04fc:0561 Sunplus Technology Co., Ltd Flexcam 100
Bus 001 Device 001: ID 0000:0000

---

### Post by Hei Ku on 2009-04-02
Parece ser un bug en el kernel
[https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/260918](https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/260918)

Que programa usaste en la 9.04 para decir que no anda?
Que resultado te da el lsusb desde la 9.04?

Te pregunto porque parece ser que algunos programas andan y otros no.

---

### Post by z37a on 2009-04-02
Son bugs con los drivers del kernel, a mi me paso pro ejemplo con un card reader de mi desktop, en el 9.04 con el kernel 9 me anda de 10, pero con el beta kernel 11 no anda!!!! Yo lo reporte en launchpad.

---

### Post by joseluis on 2009-04-02
el rsultado de lsusb es el que me larga la 8.04.
en la 8.10 y 9.04 no tengo idea, porque la puse y la desinstalé porque justamene no me andaba..q ****** no? pero me parece que  si, que es un lio con el kernel. ¿habra que esperar que lo arreglen?
Yo estoy usando la 8.04 y en verdad quiero pasar a la 9.04, pero si tengo estos lios, me quedaria en una version anterior

---

### Post by joseluis on 2009-04-02
en la notebook puse la version 9.04, enchufe la web cam y me largo esa misma leyenda del lsusb

---

### Post by Hei Ku on 2009-04-02
Entonces la 9.04 la reconoce. Que programa probaste para usarla?

---

### Post by joseluis on 2009-04-02
el amsn

---

### Post by Hei Ku on 2009-04-02
No hay arreglo para el amsn todavia. Podes probar el ekiga, o el xawtv, para verificar si tu cam anda. En caso afirmativo, tenes que esperar el arreglo para el amsn.

---

### Post by joseluis on 2009-04-03
ok..voy a probar con esos programas y aviso...saludos

---

### Post by joseluis on 2009-04-03
ok..voy a probar con esos programas y aviso...saludos

---

### Post by faktorqm on 2009-04-06
> **joseluis said:**
> en la 8.10 y 9.04 no tengo idea, porque la puse y la desinstalé porque justamene no me andaba..q cagada no? pero me parece que  si, que es un lio con el kernel. ¿habra que esperar que lo arreglen?
Yo estoy usando la 8.04 y en verdad quiero pasar a la 9.04, pero si tengo estos lios, me quedaria en una version anterior

disculpame, por que no probas desde el live cd en lugar de instalar y desinstalar? salu2!

---

