---
title: "Drivers Unichrome VIA P4M980 (ex Ayuda)"
date: 2009-05-18
forum: Hardware
---

### Post by SlipkRamm on 2009-05-18
Hola soy nuevo, y no logro encontrar los drivers de video de mi compu, es un drivers VIA, Unichrome, es de 64 mb, ya viene integrada en mi Motherboard, es una P4M980 - TE.

creo q con eso podre agregarle efecots a mi ubuntu????

---

### Post by guillermolisi on 2009-05-18
> **SlipkRamm said:**
> Hola soy nuevo, y no logro encontrar los drivers de video de mi compu, es un drivers VIA, Unichrome, es de 64 mb, ya viene integrada en mi Motherboard, es una P4M980 - TE.

creo q con eso podre agregarle efecots a mi ubuntu????
Hay algunos casos reportados con exito y muchisimos reportados que nunca la hicieron funcionar. En el caso mas leve, lograron algo pero muuuuy lento.

Personalmente recomiendo no usar esas placas de video y reemplazarlas con alguna nVidia que posee muy buen soporte y rendimiento, casi sin excepciones.

De las dos maquinas con ese chipset, una la use mucho tiempo con el driver "VESA" hasta que me decidi ponerle una nVidia 7300, y la otra, despues de pruebas y mas pruebas en varias oportunidades, lectura de cuanto post habia sobre el tema y mas pruebas, le puse una 6200 y a partir de ello vivi feliz. :)

Es una decision dificil por lo que representa comprar una placa de video cuando ya tenes una, pero es lo mas practico y expeditivo para casos como este.

---

### Post by josecuervo86 on 2009-05-18
Coincido con Guillermo. Esas placas suelen dar muchos problemas. La verdad que es bastante feo darte esta noticia cuando recien entras en este mundo, pero es asi. Como usuario de nVidia, te las recomiendo largamente ya que son las que mejor soporte tienen para GNU/linux.

---

### Post by SlipkRamm on 2009-05-18
> **josecuervo86 said:**
> Coincido con Guillermo. Esas placas suelen dar muchos problemas. La verdad que es bastante feo darte esta noticia cuando recien entras en este mundo, pero es asi. Como usuario de nVidia, te las recomiendo largamente ya que son las que mejor soporte tienen para GNU/linux.


esq en las especificaciones de la placa madre dice eso q trae VIA UniChrome Pro IGP P4M890 de 64 MB ya iantegrada en la placa, es de fabrica q viene asi, entonces uqiero ponerle los drivers para ver si asi le puedo poner efectos de escritorio a mi ubuntu

---

### Post by staar on 2009-05-18
el problema es que VIA hace unos drivers para linux MUY malos, son práctiamente inusables, no vale la pena probarlos, ni mucho menos usarlos, por eso te recomendamos que, o uses el driver VESA (sin aceleración grafica, sin efectos de escritorio) o te consigas otra placa con drivers más decentes, en especial una NVIDIA, que andan muy bien...

es una pena darte esta noticia, pero el problema de los fabricantes que no hacen drivers para nuestro sistema lo tenemos que soportar a diario :-(

saludos

---

### Post by guidito73 on 2009-05-18
Esas placas son simplemente *****. A mi me trajeron problemas de compatibilidad incluso en Windows XP, y la aceleración que tienen es simplemente horrible (y eso que mi Unichrome es de 128 MB).

Hasta que para una navidad apareció una hermosa GeForce 5500 FX. Así de simple, ya sé que está durisimo desembolsar 300 morlacos en una plaquita, pero cuando los fabricantes no le ponen ni la mínima onda a sus productos es así.

Queremos hardware libre!! ;)

---

### Post by staar on 2009-05-18
> **guidito73 said:**
> Queremos hardware libre!! ;) eso!! procesadores SPARC para todo el mundo!! :-D :lolflag:

---

### Post by z37a on 2009-05-20
Perdón por el off pero quería comentar que es una pena que no se vendan placas Intel!!!! la verdad en mi laptop tengo una integrada que va de 10!!!

Ahora con lo del post, la verdad las Via son bastante malas, jamas logre hacerlas andar con el 3D, como te dijeron lo ideal es que consigas alguna placa de vídeo, aunque sea alguna bien barata de Nvidia y no solo ganas en tener los efectos si no que también te van a hacer ahorrar 64MB mas de RAM de tu sistema!!!

PD: Algo que no siempre la gente entiende, la cantidad de memoria RAM de tu placa de video no va a hacer que rinda mejor(por lo menos en la mayoria de los casos), en una epoca unas ATIs de 64MB andaban mejor que las mismas(mismo chipset) con 128MB!!!!

---

