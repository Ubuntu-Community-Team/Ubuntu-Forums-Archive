---
title: "Grabadora LG no lee ni graba"
date: 2009-05-02
forum: Hardware
---

### Post by guidito73 on 2009-05-02
Bueno, tengo el siguiente problema:

Tengo una grabadora de dvd LG GSA-H20N (segun dice la misma, aunque Windows la reconoce como GSA-H42N), funciona perfectamente bajo windows, pero en Ubuntu reconoce los discos pero no los reproduce (MP3, películas,etc) y tampoco graba.

Actualicé el firmware de la grabadora en Windows, etc pero no logré que funque en Ubuntu, qué puede ser?

---

### Post by clasificado on 2009-05-03
No tengo tu mismo modelo de lectora, pero es bastante probable que sea otra cosa.

¿probaste ejecutar el progarma desde consola para ver que te dice? por ahi los problemas con mp3 y avi vengan por otro lado.

clasificado

---

### Post by euzkoarima on 2009-05-04
Muy raro. Proba por ejemplo de copiar un archivo del cd o dvd a tu HD y reproducirlo desde ahí a ver que pasa. Quizás sea un problema de permisos.

Saludos,
Eduardo.

---

### Post by guidito73 on 2009-05-04
Cuando trato de copiar un archivo, me sale este error:

```
cp: leyendo «01 - X-Ray Eyes.mp3»: Error de entrada/salida
```

La verdad que ni idea que puede ser :S

Hoy tuve que usar windows para grabar un dvd ¬¬

---

### Post by josecuervo86 on 2009-05-04
Ese error que te salio, fue cuando lo trataste de reproducir desde el cd o desde el disco?
Puede ser un problema de drivers, trata de bajar este paquete

**ubuntu-restricted-extras**

ya se por synaptic o desde la terminal por apt

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by KaKuS on 2009-05-05
A mi me pasa lo mismo con una LG nuevita, no me deja expulsar la bandeja, no me reconoce medios en blanco (DVD-R, CD-R) ni dvd. A duras penas reconoce CDs, y desde windows funciona todo ok.

Me sumo al la lucha! xD

---

### Post by luks911 on 2009-05-05
> **guidito73 said:**
> Bueno, tengo el siguiente problema:

Tengo una grabadora de dvd LG GSA-H20N (segun dice la misma, aunque Windows la reconoce como GSA-H42N), funciona perfectamente bajo windows, pero en Ubuntu reconoce los discos pero no los reproduce (MP3, películas,etc) y tampoco graba.

Actualicé el firmware de la grabadora en Windows, etc pero no logré que funque en Ubuntu, qué puede ser?

Mmmm... mi hermano tiene la misma (creía que era la GSA-H20N, pero Ubuntu me dice que es la GSA-H42N) y funciona sin problemas desde Intrepid hasta Jaunty.
Si puedo ayudar en algo, avisen.

---

### Post by guidito73 on 2009-05-05
Bueno, el fin de semana estaré migrando a Jaunty, les aviso qué onda ahí... =(

PD: Ubuntu-restricted-extras ya lo tengo...

EDIT: El error que me dio anteriormente fue al querer copiar un archivo desde un dvd al disco duro...

---

### Post by euzkoarima on 2009-05-05
Ok, primero proba con Jaunty, me parece lo más sano.
Si no anda vemos. Yo tuve un problema similar pero para que reconozca el cd, una vez montado copiaba sin problemas. En mi caso se arregló tocando en la BIOS, poniendo que sata lo vea como scsi (si mal no recuerdo)

Saludos,
Eduardo

---

### Post by guidito73 on 2009-05-05
Ahhh claro, el tema es que está conectada por IDE la grabadora, no SATA...

---

### Post by guidito73 on 2009-05-15
Bueno, se solucionó instalando Jaunty. La reconoció sin problemas, lee y graba a la perfección. Viva Jaunty ^^

---

