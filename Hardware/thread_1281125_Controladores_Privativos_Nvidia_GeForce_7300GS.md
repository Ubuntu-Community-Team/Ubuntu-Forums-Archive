---
title: "Controladores Privativos Nvidia GeForce 7300GS"
date: 2009-10-02
forum: Hardware
---

### Post by GambitoCBA on 2009-10-02
Hola gente... les cuento le instale a mi hermano ubuntu en su PC... La instalacion duro mucho mas tiempo de lo normal ( y no es una maquina vieja: Amd 64X2 2GB Ram Nvidia GeForce 7300GS) y cuando quiero instalarle los controladores de la placa me aparece esto: [I]"Lo sentimos; ha fallado el backend de Jockey. Por favor, informe del fallo en:

  ubuntu-bug jockey-common

Intentando recuperarse reiniciando el backend."
[/I]
Y no tengo idea que puede ser, es la promera vez que veo eso.

Si alguien sabe como arregla se lo voy a agradecer

Gracias como siempre son una masa!!!!!

Salutes

---

### Post by guillermolisi on 2009-10-02
> **GambitoCBA said:**
> Hola gente... les cuento le instale a mi hermano ubuntu en su PC... La instalacion duro mucho mas tiempo de lo normal ( y no es una maquina vieja: Amd 64X2 2GB Ram Nvidia GeForce 7300GS) y cuando quiero instalarle los controladores de la placa me aparece esto: [I]"Lo sentimos; ha fallado el backend de Jockey. Por favor, informe del fallo en:

  ubuntu-bug jockey-common

Intentando recuperarse reiniciando el backend."
[/I]
Y no tengo idea que puede ser, es la promera vez que veo eso.

Si alguien sabe como arregla se lo voy a agradecer

Gracias como siempre son una masa!!!!!

Salutes
Que version de Ubuntu utilizaste ?

Ya habias instalado en esa maquina Ubuntu como para tener una referencia de cuanto tarda la instalacion o la estas comparando contra otras maquinas ?

---

### Post by GambitoCBA on 2009-10-03
Hola si ya habia instalado una vez intrepid, y ahora use jaunty... 

Salutes!

---

### Post by staar on 2009-10-03
no es algo grave, solo te está avisando que jockey (el programita que te baja e instala los drivers correctos, traducido en el menú como "Controladores de hardware") falló y se cerró, y que está tratando de reiniciarlo...

ayer los servers estaban sobrecargados, y esa puede ser la causa del fallo (el programa lo único que hace es bajar el paquete correspondiente de los repos e instalarlo), podrías intentar de nuevo, o tratar directamente desde Synaptic, buscando el paquete e instalándolo vos mismo. para esa placa creo que el paquete con el driver es el *nvidia-glx-185* (o 180, no estoy seguro)

saludos

---

### Post by guillermolisi on 2009-10-03
> **staar said:**
> no es algo grave, solo te está avisando que jockey (el programita que te baja e instala los drivers correctos, traducido en el menú como "Controladores de hardware") falló y se cerró, y que está tratando de reiniciarlo...

ayer los servers estaban sobrecargados, y esa puede ser la causa del fallo (el programa lo único que hace es bajar el paquete correspondiente de los repos e instalarlo), podrías intentar de nuevo, o tratar directamente desde Synaptic, buscando el paquete e instalándolo vos mismo. para esa placa creo que el paquete con el driver es el *nvidia-glx-185* (o 180, no estoy seguro)

saludos
Tambien esta la alternativa con el Envy-NG que tiene la ventaja, si se lo puede llamar asi, de recomendar el driver mas adecuado para la placa en uso.

---

### Post by mama21mama on 2009-10-03
Yo lo instalo [de esta manera siempre]("http://mamalibre.eshost.com.ar/?q=node/30") por que estoy con el ultimo driver estable.

---

