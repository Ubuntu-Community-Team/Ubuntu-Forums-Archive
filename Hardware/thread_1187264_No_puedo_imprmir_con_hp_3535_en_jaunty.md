---
title: "No puedo imprmir con hp 3535 en jaunty"
date: 2009-06-14
forum: Hardware
---

### Post by leonardo83 on 2009-06-14
bunas gente, la verdad Jaunty me trajo muchas alegrias, por ejemplo pude usar Compiz que anteriormente con Gutsy no podia pero un drama de mi placa viejita jeje, pero ahora se ve todo y la verdad estoy contento....parcialemnte.
Hoy tenia que imprimir unas practicas para la facu y no lo pude  hacer. Tengo una impresora HP 3535 que en Gutsy detectaba de una e imprimia sin problemas, lo unico que le configuraba era el color para que sue blanco y negro y no solo color.

Ahora en Jaunty al enchufarlo lo reconoce, lo configuro (creo que bien, casi no cambio nada solo eso del color) y lo marco como predeterminado.
Pero alquerer imprmir por ejemplo la hoja sale en blanco, no hace nada y me aparece como "la impresora esta desconectada" o algo similar, cuando esta enchufada al usb :(.
Ademas me fije desde conectar, para conectarlo al localhost y al cups no se cuanto, pero sigue igual
Alguien le paso algo igual? Tendre que usar el cd de HP?
Espero ayuda, gracias :(

---

### Post by Hei Ku on 2009-06-14
Tenes que instalar la ultima version de hplip, desde este lugar: [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

---

### Post by leonardo83 on 2009-06-14
Gracias Hei, mira me lo baje y me quedo un archivo hplip-3.9.4b.run, que me da al opcion de abrir con wine (???)

Como instalo esto? tengo que hacer algo desde el terminal?

Gracias y saludos:(

EDIT : encontre en la pagina como abrirlo desde terminal para automatic install jeje
Veremos que pasa

---

### Post by Hei Ku on 2009-06-14
si, quizas tengas que darle permiso de ejecucion.

sudo sh <nombre del archivo>

y despues para correrlo:

sudo sh ./<nombre del archivo>

---

### Post by leonardo83 on 2009-06-14
Gracias, pude instalarlo y me aparecio el device manager, pero aun asi no imprime!

Ejemplo, cree un txt y escribi un par de palabras, si eligo "imprimir" desde ese programa o desde el boton en el bloc de notas inmediatamente me aparece el mensaje "trabajo completado" (??) y asi como entro lahoja en la impresora, sale, y si la pongo de vuelta la agarra y la muerde a la mitad, como si estaria lista para imprimir algo (??????)

Ya reinicie y todo pero sigue asi..no se quehacer

Repito, la impresora anda ok en Gutsy y me funca de maravilla sen Win asi que no es drmaa  de mi impresora..

AIUTOOOOOOO

Gracias :(


actualizacion : mande varios archivos pdf, que me imprime como maximo 3 lineas y ya me aparece el mensaje de trabajo completado, y la hoja que viene la agarra y la deja trabada como si fuese a seguri imprmiendo
Esto me supera ...Jaunty sin  impresion es malisimo!

---

### Post by Hei Ku on 2009-06-14
Cuando mandas a imprimir una pagina de prueba te pasa lo mismo?

---

### Post by leonardo83 on 2009-06-14
Recien mande a imprimir una pagina de prueba y lo unic que escribio casi ilegible es HP Printer Test Page pero despues me devuelve toda a hoja, me pide papel y de nuevo escribe lo mismo :(

Lo que note recien intentando mandar varias cosas a imprimir es que en un momento me aparecio el asistente de impresora, como si hubiese enchufado el usb de nuevo (cosa que no hice) detectando una impresora HP 35002 (??), que la borre...todo muy extraño.
No se si esta mal configurado algo, o que pero no puedo imprimir nada, y u si lo hago tengo que sacar a la fuerza el papel de la bandeja porque quedo trabado y solo con unas lineas impresas.

Si queres te pase screen o algun codigo avisame porfa

SALudos y gracias


PD: perdon si escribo algo ilegible pero se me estan helando los dedos :(

---

### Post by Hei Ku on 2009-06-14
En la pagina que te pase hay info sobre impresoras HP, capaz podes encontrar ahi mas info sobre tu impresora en particular. Podes probar de borrarla y crearla de vuelta, a veces eso ayuda.

---

### Post by leonardo83 on 2009-06-14
Por lo que lei supuestamente ya viene un paquete de hplip en la version y yo instalo una nueva, no sera que tengo que borar esa version??

Intente reinstalar la impresora pero nada....sigue igual


SH*T HAPPENS :cry:

---

### Post by Hei Ku on 2009-06-14
Jaunty trae una version de hplip que tiene problemas. El link que te pasé yo tiene una version que se encarga de borrar la anterior.

Lo que hice, en mi caso, fue borrar todas las impresoras que tenía, instalar la nueva versión y reconfigurar la impresora. Con eso salió andando.

Un lugar alternativo para configurar la impresora, y que a veces anda mejor que las preferencias del sistema es a través del browser, conectandote a [http://localhost:631](http://localhost:631)
También podes ejecutar hp-toolbox desde la terminal, que es una utilidad de HP para sus impresoras.

Como último recurso, cargar un bug en Launchpad en el proyecto hplip. :(

---

### Post by leonardo83 on 2009-06-14
Mmmmm eso hace que deteste esta version :o.

Peeeero descubri algo..

Cambie el puerto de la impresora (estabaen los puertos del frente) y lo pase a uno de atras,y em imprimio bien una hoja (raro porque sino no me hubiese reconocido la impresora si andaba mal pero bue).

Casi feliz probe otra hoja mas pero me aparece error como de transmisiond e datos, es decir la pagina se imprime ok, pero antes e terminar aparece el mensaje "trabajo # finalizado" , entonces deja de imprimri y te deja el papel donde quede y la impresion donde sea.

Probe imprimir en win y anda ok asi que no es cable que este jodido

No se no se , me esta partiendo la cabeza...

Me decis como hiciste para borrar todo e instalar vos?

Gracias, saludos

---

### Post by Hei Ku on 2009-06-14
yo solo borre la impresora, no los programas. En la parte de configuracion de impresora, click derecho sobre la impresora y borrar.

Despues instale la nueva version de hplip, configure de vuelta la impresora y salio andando. Me parece que tu problema viene por otro lado. Algo quizas con los puertos usb, por lo que contaste.

---

### Post by leonardo83 on 2009-06-14
no creo porque como dije, en win la impresora anda como trompada, y en ubuntu en cualquier puerto usb me reconoce el mouse y el mp4, asiq ue no son los puertos.

Me aparece un mensaje como "no hay transmision de datos" o algo parecido y ahi ya no imprime... creo que no em quwda otra que imprmirm en win o pasarme a Hardy :( :( :(

---

### Post by faktorqm on 2009-06-15
yo ultimamente tuve serios problemas con las impresoras en mi trabajo, pues intente instalarme un servidor de impresoras, y hasta que anduvo bien todo fue un caos. Todo ese "caos" salio de que estaba eligiendo mal el driver, en mi caso tenia que elegir PXL y yo elegia PS. 

Pasa algo parecido en la tuya? quiero decir, te aparece mas de una opcion de driver para instalar de la misma impresora? Me parece extremadamente raro que en windows te ande e inmediatamente en ubuntu no, será que por algun motivo se te queda """enganchado""" con otra cosa? Proba de apagar la compu, desenchufarla, esperar un minuto y arrancar en ubuntu. (a un amigo le pasaba eso con un modem usb, estaba en windows, andaba, reniciaba, arrancaba en ubuntu, no andaba. apagaba, volvia a prender en ubuntu, andaba :( )

si no de ultima para descartar problemas con el usb podes probar por paralelo (trae para puerto paralelo la tuya?) ya es viejo pero a veces te salva xD

Salu2!

---

### Post by LaZeta on 2010-12-30
> **Hei Ku said:**
> yo solo borre la impresora, no los programas. En la parte de configuracion de impresora, click derecho sobre la impresora y borrar.

Despues instale la nueva version de hplip, configure de vuelta la impresora y salio andando. Me parece que tu problema viene por otro lado. Algo quizas con los puertos usb, por lo que contaste.


Hola Hei Ku. Estoy recien registrado en el foro, y recien iniciado en el mundo de linux. Tengo el linux mint Julia y soy usuario de autocad. Tengo un ploter Hp 350c puerto paralelo y no lo puedo hacer imprimir. En principio lo reconoce, pero al mandarle la pagina de prueba, se queda ahí, "procesing", mientral el ploter no acusa recibo. Bajé el hplip, pero ni la menor idea de cómo se instala. Aclaro que no se NADA de linux (como buen usuario de las "ventanitas", un ignorante total.
Veo que el post tiene más de un año, pero hago el intento antes de abrir otro

---

