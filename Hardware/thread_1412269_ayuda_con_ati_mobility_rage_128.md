---
title: "ayuda con ati mobility rage 128"
date: 2010-02-21
forum: Hardware
---

### Post by danny.woodstock on 2010-02-21
hola a todos, 
mi duda es, como puedo instalar una ati mobility rage 128 en ubuntu?
ya que me gustaria poder usar efectos 3d, en estos momentos estoy usando el driver ati!
pero no tengo efectos 3d... :(
que driver debo usar? 
o lamentablemente no hay un driver libre que de acleracion 3d para esa atrheta?
en la pagina de ati no nada de info sobre esa tarjeta ya que es bastante vieja...

estoy usando ubuntu hardy.

---

### Post by robertor on 2010-02-21
danny.woodstock, ati va eliminando el soporte de algunas tarjetas gráficas antiguas. La tuya cae en ese saco. Tienes dos opciones... buscar en el sitio de ati, el binario con la ultima versión que tiene soporte para tu tarjeta o usar el driver libre.

Mencionas que estás usando el driver ati libre... me parece que hay uno especial para las ati rage. Verifica eso y prueba ese... puede que tenga mejor soporte que el ati para lo 3D.

Por cierto, yo me apeste de usar el fglrx, si bien lograba obtener la aceleración 3D, el notebook andaba con kernels panics todo el rato. Preferí usar el driver libre. En ese sentido, muy malo el driver fglrx.

Saludos,
Roberto

---

### Post by ClarkXP on 2010-02-21
ese modelo de tarjeta no ofrece aceleración por hardware, por ese motivo no puede rendear compiz, la ati radeon 7000 es como lo minimo para correr compiz, y por nvidia, la geforce 256

---

### Post by danny.woodstock on 2010-02-21
ya veo, eso quiere decir que estoy sonado? jajajaja

y si uso el driver r128???
tampoco serviria?
pregunto, porque quise instalarlo desde synaptics pero veo que no esta :S
(el driver, no synap.)

---

### Post by robertor on 2010-02-22
> **danny.woodstock said:**
> ya veo, eso quiere decir que estoy sonado? jajajaja

pues si :P. Lo otro es que busques una version antigua del fglrx en el sitio de ati.
> **danny.woodstock said:**
> 
y si uso el driver r128???
tampoco serviria?
pregunto, porque quise instalarlo desde synaptics pero veo que no esta :S
(el driver, no synap.)
El paquete se llama xserver-xorg-video-r128. Por lo menos en ubuntu 9.04 está.

Saludos,
Roberto

---

### Post by danny.woodstock on 2010-02-23
ok, entonces mmm creo que seguire con hardy
hasta que salga lucid :) hehehe
me gustar usar lts asike ahi lo instalaré
y probaré con r128
y si aun asi no funciona, creo que usare cairo composite manager :)
hehe para dejar las ventanitas mononas que sea :) jejeje
gracias!

---

