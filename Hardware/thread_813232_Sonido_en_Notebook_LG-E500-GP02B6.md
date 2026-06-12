---
title: "Sonido en Notebook LG-E500-GP02B6"
date: 2008-05-30
forum: Hardware
---

### Post by marcosconio on 2008-05-30
Buenas....
El problema es el siguiente:
Cuando conecto los auriculares a la notebook, puedo escuchar por los mismos, pero no se apagan los parlantitos de la notebook! 
Alguien sabrá porque? Como podria solucionarlo? 
Muchas Gracias!

---

### Post by MeduZa on 2008-05-30
> **marcosconio said:**
> Buenas....
El problema es el siguiente:
Cuando conecto los auriculares a la notebook, puedo escuchar por los mismos, pero no se apagan los parlantitos de la notebook! 
Alguien sabrá porque? Como podria solucionarlo? 
Muchas Gracias!

epa, eso se supone que es por hardware
el conector miniplug del jack del auricular tiene una chapita que esta siempre haciendo contacto con el "canal de audio" cuando enchufas la ficha esa chapita se abre hacia afuera abriendo el circuito y solo haciendo contacto con el plug

osea no se que decirte (me pasa lo mismo pero se que es porque no tengo manera por hard de cortar el audio)
fijate si esta bien enchufado (A fondo)
la otra es que lo haga por soft pero seria muy aparatoso al cuete!

---

### Post by majatu on 2008-05-30
Hola che, te comento que tengo una LG E500 tambien y no me hace en ninguno de los 3 Jacks tu problema, yo no creo q sea por algo de Ubuntu, de ultima la maquina te vino con Windows Vista, si no lo eliminaste fijate desde ahi y comentanos que tal te fue. No se que decirte, como te dijeron arriba, puede ser por hardware el problema.
Saludos y espero puedas solucionarlo! ;)

---

### Post by osensei on 2008-05-31
Tengo el mismo maquinón, y tenía el mismo problema.

Logré solucionarlo de la siguiente manera:

1) Ejecutá el siguiente comando en la terminal:

```
echo options snd-hda-intel model=3stack-6ch-dig | sudo tee -a /etc/modprobe.d/alsa-base
```

(Lo que hace esto es agregar la línea "options snd-hda-intel model=3stack-6ch-dig" al final del archivo /etc/modprobe.d/alsa-base . Si querés lo podés hacer editando el archivo vos, pero así es más directo)

2) Reiniciá.

3) Una vez que te hayas logueado, hacé doble clik en el parlantecito para que te abra el mixer. Fijate que ahora además de la solapa "Playback" (no sé cómo dirá si lo tenés en español, ya que yo lo uso en inglés) tenés otra que dice "Switches". En esa solapa te va a aparecer una opción que dice "Headphone" y está marcada. Desmarcá esa opción y el sonido va a dejar de salir por los parlantes de la notebook y sólo va a salir por los auriculares.

Espero que te sirva.

Saludos!

---

### Post by marcosconio on 2008-06-04
Muchas gracias por las respuestas! Apenas pruebe las sugerencias les comento como me fue. En  WVista(que ya lo traia instalado) y WXP anda perfecto, lamentablemente. (Lamentablemente porque si no quiero molestar a nadie, escuchar musica y programar al mismo tiempo tengo que entrar ahi :evil: )

Marcos

---

### Post by marcosconio on 2008-06-05
> **osensei said:**
> Tengo el mismo maquinón, y tenía el mismo problema.

Logré solucionarlo de la siguiente manera:

1) Ejecutá el siguiente comando en la terminal:

```
echo options snd-hda-intel model=3stack-6ch-dig | sudo tee -a /etc/modprobe.d/alsa-base
```

(Lo que hace esto es agregar la línea "options snd-hda-intel model=3stack-6ch-dig" al final del archivo /etc/modprobe.d/alsa-base . Si querés lo podés hacer editando el archivo vos, pero así es más directo)

2) Reiniciá.

3) Una vez que te hayas logueado, hacé doble clik en el parlantecito para que te abra el mixer. Fijate que ahora además de la solapa "Playback" (no sé cómo dirá si lo tenés en español, ya que yo lo uso en inglés) tenés otra que dice "Switches". En esa solapa te va a aparecer una opción que dice "Headphone" y está marcada. Desmarcá esa opción y el sonido va a dejar de salir por los parlantes de la notebook y sólo va a salir por los auriculares.

Espero que te sirva.

Saludos!

Excelente!!. Soy feliz... Les agradezco mucho, eso funciona perfecto! 

Marcos

---

### Post by ale2289 on 2009-05-15
Hola, les cuento que yo tengo la misma notebook, una LG E500... bueno el tema es que la solucion que postean anteriormente me da un problema, solo desactiva el sonido de los altavoces destildando "Headphones" en Control de Volumen > Conmutadores.
Buscando en internet encontré este post, [http://ubuntuforums.org/showpost.php?p=3748297&postcount=21](http://ubuntuforums.org/showpost.php?p=3748297&postcount=21) y modifiqué el archivo  /etc/modprobe.d/alsa-base con la opción "targa-2ch-dig", quedo asi ```
options snd-hda-intel model=targa-2ch-dig
```. Reinicié y funcionó, ahora enchufo y desenchufo los auriculares y activa y desactiva los parlantes.
Lo que pasa es que esta notebook es una MSI, no recuerdo bien el modelo, pero la mother es MSI y la notebook completa es exactamente igual a la MSI pero de otros colores.
Cuentenme si les funciona, saludos..

---

### Post by marcosconio on 2009-05-22
> **ale2289 said:**
> Hola, les cuento que yo tengo la misma notebook, una LG E500... bueno el tema es que la solucion que postean anteriormente me da un problema, solo desactiva el sonido de los altavoces destildando "Headphones" en Control de Volumen > Conmutadores.
Buscando en internet encontré este post, [http://ubuntuforums.org/showpost.php?p=3748297&postcount=21](http://ubuntuforums.org/showpost.php?p=3748297&postcount=21) y modifiqué el archivo  /etc/modprobe.d/alsa-base con la opción "targa-2ch-dig", quedo asi ```
options snd-hda-intel model=targa-2ch-dig
```. Reinicié y funcionó, ahora enchufo y desenchufo los auriculares y activa y desactiva los parlantes.
Lo que pasa es que esta notebook es una MSI, no recuerdo bien el modelo, pero la mother es MSI y la notebook completa es exactamente igual a la MSI pero de otros colores.
Cuentenme si les funciona, saludos..

Funcionó de maravilla :) Perfecto!! Te agradezco muchísimo por este aporte!!

---

