---
title: "No funcionan los dos monitores a la vez"
date: 2010-12-26
forum: Hardware
---

### Post by PeTTi on 2010-12-26
Quiero conectar dos monitores a la pc, esto es posible ya que tengo una placa de video (Geoforce 9500), y este trae un conector VGA, entonces al conectar los dos monitores, el que es conectado a la placa de video no es reconocido.

Cuando voy a Preferencias>>Monitores me dice esto:
Parece que su controlador gráfico no admite las extensiones necesarias para usar esta herramienta ¿Desea usar en su lugar la herramienta del fabricante de su controlador gráfico?

Si le cliqueo en no, me aparecel la opción de Preferencias del Monitor, pero no puedo hacer nada, y si le pongo que si, me aparece esto:
[IMG]http://imgur.com/YhIEq[/IMG][IMG]http://i.imgur.com/YhIEq.png[/IMG]
Gracias :)

---

### Post by granjero on 2010-12-27
te hago una pregunta: ¿Estás enchufando los dos monitores a la placa Nvidia? o uno a la placa Nvidia y el otro a la placa onboard?

Para que funcionen los dos a la vez tienen que estar enchufados a la misma placa.


Si están los dos en la Nvidia tenés que usar la herramienta que mostrás y en el segundo renglón **X Server Display Configuration** es donde tenés que configurar. Yo los usaba en Twin View.

yo ahora estoy sin mi pc de escritorio para guiarte más pero la herramienta es bastante intuitiva.


salud!

---

### Post by PeTTi on 2010-12-30
> **granjero said:**
> te hago una pregunta: ¿Estás enchufando los dos  monitores a la placa Nvidia? o uno a la placa Nvidia y el otro a la  placa onboard?

Para que funcionen los dos a la vez tienen que estar enchufados a la misma placa.


Si están los dos en la Nvidia tenés que usar la herramienta que mostrás y en el segundo renglón **X Server Display Configuration** es donde tenés que configurar. Yo los usaba en Twin View.

yo ahora estoy sin mi pc de escritorio para guiarte más pero la herramienta es bastante intuitiva.


salud!
Ahora que tengo un solo monitor lo tengo conectado en la placa, y la  placa tiene un solo conector VGA, por ende solo puedo conectar uno :/

---

### Post by guillermolisi on 2010-12-30
> **PeTTi said:**
> Ahora que tengo un solo monitor lo tengo conectado en la placa, y la  placa tiene un solo conector VGA, por ende solo puedo conectar uno :/

Me parece que esta respuesta no ayuda a resolver el tema.

Tenes una o dos placas de video ?

Si tenes dos placas, y no estan interconectadas via SLI, solo funcionara una de las dos. 

Si tenes una sola placa y esta es la placa nVidia, teniendo el conector apropiado podras conectar dos monitores a la misma y lograr clonado o expansion del escritorio grafico (mediante nvidia-settings.

---

### Post by granjero on 2011-01-02
petti, hice una búsqueda en google y si tu placa es efectivamente una geforce 9500 vas a poder conectar dos monitores. lo que vas a necesitar es un adaptador de la salida blanca que creo se llama DVI a VGA. no es demasiado costosa.

saludos!

---

### Post by PeTTi on 2011-01-05
> **guillermolisi said:**
> Me parece que esta respuesta no ayuda a resolver el tema.

Tenes una o dos placas de video ?

Si tenes dos placas, y no estan interconectadas via SLI, solo funcionara una de las dos. 

Si tenes una sola placa y esta es la placa nVidia, teniendo el conector apropiado podras conectar dos monitores a la misma y lograr clonado o expansion del escritorio grafico (mediante nvidia-settings.
Tengo una sola placa, y es esa nvidia 9500.

> **granjero said:**
> petti, hice una búsqueda en google y si tu placa es efectivamente una geforce 9500 vas a poder conectar dos monitores. lo que vas a necesitar es un adaptador de la salida blanca que creo se llama DVI a VGA. no es demasiado costosa.

saludos!
Sí, tengo una 9500. Después averiguo si consigo ese adaptador.

---

