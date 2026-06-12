---
title: "Cuando van a arreglar el problema de los auriculares??"
date: 2008-07-12
forum: Hardware
---

### Post by niko_3100 on 2008-07-12
Simplemente eso gente, a alguien le anda bien? Es decir enchufar los auriculares y que no salga por los parlantes a la ves?? Pense que para hardy ya lo iban a solucionar y parece que no, va por lo menos en mi notebook no es asi...

---

### Post by Mauro22 on 2008-07-12
No hay alguna forma que hagas un script??


O sea, subis el volumen de los auriculares que ponga en mute el de los parlantes o algo asi?

---

### Post by santiagoward2000 on 2008-07-12
> **niko_3100 said:**
> Simplemente eso gente, a alguien le anda bien? Es decir enchufar los auriculares y que no salga por los parlantes a la ves?? Pense que para hardy ya lo iban a solucionar y parece que no, va por lo menos en mi notebook no es asi...

La verdad que a mi NUNCA me paso. Estuve buscando un poco, y vi varias soluciones, dependiendo del modelo de la notebook. Podrias subir el modelo para ver si alguna de estas te puede ayudar?
Saludos!

---

### Post by sergiom99 on 2008-07-12
en HH me anduvo de una.
en GG lo hice así:

> editar el archivo **/etc/modprobe.d/alsa-base** y agregar "*options snd-hda-intel model=laptop*" en una nueva línea al final

(el original en inglés en [http://ubuntuforums.org/showthread.php?t=575750](http://ubuntuforums.org/showthread.php?t=575750))

suerte

---

### Post by luks911 on 2008-07-12
> **niko_3100 said:**
> Simplemente eso gente, a alguien le anda bien? Es decir enchufar los auriculares y que no salga por los parlantes a la ves?? Pense que para hardy ya lo iban a solucionar y parece que no, va por lo menos en mi notebook no es asi...

Yo no encontré manera de solucionarlo en Gutsy. Pero con Hardy funciona bien sin tocar nada. Posteá que notebook tenés a ver qué se puede hacer.

Saludos

---

### Post by gefarion on 2008-07-15
Yo no logro solucionarlo en mi laptop, tengo esta placa:

 Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

en una notebook oliveti.

---

### Post by sergiom99 on 2008-07-15
> **gefarion said:**
> Yo no logro solucionarlo en mi laptop, tengo esta placa:

 Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

en una notebook oliveti.

Ni siquiera agregando la linea al archivo como decia un par de post mas arriba?

---

### Post by FlyerDie on 2008-07-15
Que notebook tenes? yo en la Olivetti lo pude recien solucionar instalando la version HH (8.04)...cosa que con la anterior por mas que pusiera los auriculares seguian sonando los parlantes como si nada..

---

### Post by gefarion on 2008-07-15
Una olivetti 800 series, logre dividir los canales del auricular y de los parlantes, pero no logo hacer q los parlantes se muteen automaticamente.
Saludos.

---

### Post by FlyerDie on 2008-07-15
ah..yo tengo una 610-430...viejita.

---

### Post by niko_3100 on 2008-07-16
Yo una notebook msi s430x, sempron 2,2 ghz, 2 gb de ram, 120 de disco, sonido integrado realtek... pense que en hardy se iba a solucionar de una pero por lo menos en mi caso no es asi.. que macana

---

