---
title: "la computadora se prende sola"
date: 2009-03-27
forum: Hardware
---

### Post by drazhe on 2009-03-27
Hola, la cosa es mas o menos asi, tengo xp y ubuntu instalados en 2HD separados pero que estan en la misma computadora, al apagar el sistema desde xp, este se apaga y se queda asi, pero al hacerlo desde ubuntu, a los 2 o 3 minutos se vuelve a prender... 

que puede estar pasando y como se soluciona??

---

### Post by pol666 on 2009-03-27
Nunca escuche eso en mi vida, y hasta me gustaria saber como hacer que la compu se prenda sola :P. Supongo que si no es un problema de hard es que la computadora no se esta apagando sino suspendiendo.

---

### Post by albandy on 2009-03-27
para apagarlo prueba escribiendo en la consola 
sudo poweroff
si así se vuelve a encender (curioso nosotros decimos encender y vosotros prender y las dos significan incendiar algo XD) entoces realmente es algo paranormal XD

---

### Post by drazhe on 2009-03-27
con xp me pasaba eso, cuando el cable de red LAN estaba conectado, pero despues de formatear dejo de hacer eso... ahora que le instale ubuntu la maquina se prende o enciende (para Argentinos y Españoles) jejeje solita... 

Es decir, ahora para apagar mi PC desde ubuntu, tengo que reiniciar con xp y apagarla desde ahi.....

En otro foro por este mismo asunto me decian que puede estar seteada la opcion WAKE ON LAN, pero no me dijeron donde buscar eso, sin en las configuraciones de red del SO o de la BIOS, y en BIOS no dice nada sobre wake on lan.... algun sabe donde estaria una opcion asi en ubuntu?

---

### Post by albandy on 2009-03-27
Si puedes hacer una captura de la BIOS te diré donde esta la opciónd el Wake On Lan. 

La captura no tendrás más remedio que hacerla con una cámara de fotos.

---

### Post by drazhe on 2009-03-27
recien probe eso de sudo poweroff y aun asi, se volvio a prender... la foto te la mando en un rato... en estos momentos no estoy en casa...

---

### Post by drazhe on 2009-03-27
Bueno aca estan las fotos, dentro de Power Managment Features encontre una etiqueta que decia "Wake Up Events" tambien saque una foto de esa pantalla por las dudas, es lo mas cercano que encontre a Wake On Lan, pero en ninguna de las etiquetas encontre algo asi.... 

Pantalla principal de la bios
[IMG]http://s3.subirimagenes.com/fotos/previo/thump_224087227032009.jpg[/IMG]

Etiqueta Powermanagment Features
[http://s3.subirimagenes.com/fotos/previo/thump_224087927032009001.jpg](http://s3.subirimagenes.com/fotos/previo/thump_224087927032009001.jpg)

---

### Post by Hei Ku on 2009-03-27
Tenes el Wake Up activado, aparentemente. Pasa todos los eventos a disabled.

---

### Post by pablo.s on 2009-03-27
Tengo miedo, Dave. Dave, mi mente se disuelve. Puedo sentirlo, puedo sentirlo...:)

---

### Post by guillermolisi on 2009-03-27
> **Hei Ku said:**
> Tenes el Wake Up activado, aparentemente. Pasa todos los eventos a disabled.

Exactamente. Tiene el Wake-up on LAN activado y cuando detecta actividad de red se enciende.

Si queres probar, desenchufale el cable de red y fijate si se vuelve a encender.

---

### Post by drazhe on 2009-03-27
Pablo.S me preocupas... de que tenes miedo???
y albandy que tengo los eventos en WakeUp estas seguro? porque ahi dice PCI y PCIe no LAN... esas son las ranuras de expancion por lo que se.... (placa de video, sonido... etc)

---

### Post by pablo.s on 2009-03-27
Ahora quedé como un (:() porque era un chiste referenciando a una
computadora que maneja una nave espacial. Mata a toda la tripulación
y cuando queda un solo tripulante, este la desconecta de a poco,
sacandole módulos. A todo esto la computadora que no quería que la
desconectaran, empieza a recordar cuando la ensamblaron, etc.

Y tu computadora me hizo acordar a esta de la pelicula, porque se
enciende sola.

---

### Post by guillermolisi on 2009-03-27
> **drazhe said:**
> Pablo.S me preocupas... de que tenes miedo???
y albandy que tengo los eventos en WakeUp estas seguro? porque ahi dice PCI y PCIe no LAN... esas son las ranuras de expancion por lo que se.... (placa de video, sonido... etc)

Si no es wake-up on LAN debe ser otro que hace se encienda la PC al detectar actividad.

La seccion del BIOS habla de eventos para el wake-up y ahi dentro vas a ver cantidad de alternativas por las que el sistema sensa y despierta la PC. Por eso HeiKu te sugirio que deshabilites todos esos eventos.

---

### Post by drazhe on 2009-03-27
> **pablo.s said:**
> Ahora quedé como un (:() porque era un chiste referenciando a una
computadora que maneja una nave espacial. Mata a toda la tripulación
y cuando queda un solo tripulante, este la desconecta de a poco,
sacandole módulos. A todo esto la computadora que no quería que la
desconectaran, empieza a recordar cuando la ensamblaron, etc.

Y tu computadora me hizo acordar a esta de la pelicula, porque se
enciende sola.

tenes razon, que mal lo mio... 2001 es de las mejores peliculas y libros que lei en mi vida, tendria que haberme dado cuenta... jejejej

por cierto, ya pase todos los eventos a "disable", ahora cuando temrine de hacer lo que tengo que hacer pruebo si se prende de nuevo... esperemos que no.....

---

### Post by pablo.s on 2009-03-27
Y si después de desabilitar Wake on Lan se prende otra vez
alegrate que tenés una maquina de ultima generación que tiene
inteligencia artificial.

---

### Post by drazhe on 2009-03-27
> **pablo.s said:**
> Y si después de desabilitar Wake on Lan se prende otra vez
alegrate que tenés una maquina de ultima generación que tiene
inteligencia artificial.

jeje, no se si tendra inteligencia artificial, pero de que es mas inteligente que yo, sin duda.. jejejee.... hace mucho lo acepte...

---

### Post by infernus92 on 2009-03-27
lo raro es que se enciende solamente cuando la apagas desde ubuntu... si el problema fuera de la BIOS deberia prenderse tambien desde window$... proba desde la consola poner 
```
sudo halt
```
si asi se vuelve a prender tenes la computadora mas rara de la que he escuchado o casi la mas rara...
la verdad no se si eso se pueda configurar desde ubuntu... a mi me parecia que era solamente desde la BIOS... pero no soy un usuario muy experto precisamente...

Saludos

---

### Post by drazhe on 2009-03-27
Bueno, hace media hora la apague desde ubuntu y se quedo asi... asi que parece haberse solucionado.... esperemos que haya sido eso solamente... 

Gracias a todos por la ayuda!

---

### Post by guillermolisi on 2009-03-27
> **drazhe said:**
> Bueno, hace media hora la apague desde ubuntu y se quedo asi... asi que parece haberse solucionado.... esperemos que haya sido eso solamente... 

Gracias a todos por la ayuda!
Y antes de apagarla, que hiciste ?

---

### Post by drazhe on 2009-03-27
> **guillermolisi said:**
> Y antes de apagarla, que hiciste ?

habia desactivado el WakeUP Events de la bios, estuve navegando por internet, revisando correo, leyendo el diario, posteando mensajes aca, probando la impresora desde ubuntu, jugando al buscaminas y al ajedrez...... cuando termine apague el sistema desde el boton apagar y se quedo asi como 30minutos mas o menos... y antes se prendia a los 2 o 3 solitas, asi que supongo que se soluciono despues de cambiar la configuracion del bios.

---

### Post by albandy on 2009-03-28
> **drazhe said:**
> Pablo.S me preocupas... de que tenes miedo???
y albandy que tengo los eventos en WakeUp estas seguro? porque ahi dice PCI y PCIe no LAN... esas son las ranuras de expancion por lo que se.... (placa de video, sonido... etc)

Busca dentro de la BIOS algo como "Integrated Peripherals"

---

