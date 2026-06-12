---
title: "Modem ZTE MF110 Movistar en Lucid"
date: 2010-05-02
forum: Hardware
---

### Post by nechus on 2010-05-02
¿Alguien sabe cómo hacer funcionar un módem USB ZTE MF110 de Movistar en Ubuntu?

No me resulta en Jaunty, Karmic ni Lucid. Este aparatito es lo único que está llevando a un amigo mío de regreso a Windows.

Lo necesito en Lucid, en un Acer Aspire One. Logré hacerlo funcionar una sola vez. Se conectó a Internet, apareció un formulario en el que el usuario tiene que ingresar sus datos para activar la banda ancha (lo cual parece ser un requisito de Movistar), y cuando presioné "enviar" la conexión murió y no pude restablecerla NUNCA MÄS!!!

Ahora conecto el modem USB, Lucid lo reconoce y lo pone en la lista de redes disponibles, pero la lucecita del modem nunca se pone verde (se mantiene roja) y el indicador en el área de notificaciones busca, y busca, y busca, y busca, y busca, y busca...

He visitado un montón de foros, pero hay que ser científico de la NASA para entender.

Gracias por cualquier ayuda.

---

### Post by bichopro on 2010-05-02
Ve al networ manager, dale boton derecho y despues editar conexiones. Ve a la pestaña de banda ancha movil y selecciona y borra la conexion que creaste antes. Para terminar dale añadir y empieza otra vez.

---

### Post by nechus on 2010-05-02
Creo que resultó!!  Muchas gracias.

Digo "creo" porque Ubuntu dice haberse conectado, y el ícono en el área de notificaciones indica que la conexión está activa. En el módem parpadea una luz verde, lo cual parece indicar que está funcionando.

Sin embargo, Firefox busca las páginas un buen rato y no logra abrirlas. Pero creo que eso debe ser ya un problema de Movistar.

Gracias!!!

---

### Post by Carlos C on 2010-05-02
Prueba haciendo un ping a una página como google (ping [www.google.cl](www.google.cl)) y ve si es capaz de encontrarla. En caso de que no lo haga prueba con el ip (ping 209.85.195.104). Si lo encuentra es porque tienes un problema de DNS.

Saludos.

---

### Post by nechus on 2010-05-02
Este fue un fin de semana constructivo. Claro que terminé con el colon en la mano y varias canas más, pero fue constructivo.

Después de pedir mucha ayuda (gracias a Bichopro), leer muchos foros, cortar y pegar infinitos comandos en la terminal y acabarme las gotitas de passiflora y valeriana que encontré en el baño, he aprendido que los (mald... hij... de...) módems USB ZTE MF110 funcionan sin problemas en Lucid instalando la versión más reciente de usb-modeswitch, que más encima viene en paquete deb, para que todo el jaleo que me sacó de quicio todo el fin de semana se reduzca a DOS CLICS!!!

Tan maravillosos son estos dos clics, que dejo aquí los links para que descarguen los debs y experimenten la dicha inefable que me invadió cuando yo los hice:

Primero instalan este: [http://www.4shared.com/file/APj9D9ut/usb-modeswitch-data_20100418-1.html](http://www.4shared.com/file/APj9D9ut/usb-modeswitch-data_20100418-1.html)
Segundo, este: [http://www.4shared.com/file/iyaw_o7R/usb-modeswitch_112-1_i386.html](http://www.4shared.com/file/iyaw_o7R/usb-modeswitch_112-1_i386.html)
Y si su procesador es de 64 bits, en vez de instalar el segundo instalan este: [http://www.4shared.com/file/Pt6eC5gt/usb-modeswitch_112-1_amd64.html](http://www.4shared.com/file/Pt6eC5gt/usb-modeswitch_112-1_amd64.html)

Y "vualá", conectan su módem al computador, esperan un minutito (o dos porque puede ser medio lento), y van a tener la conexión disponible. Le hacen clic y les pedirá su pin (numerito de cuatro dígitos que Movistar les da en una tarjeta).

Santo remedio! 

Entonces habría que marcar esto como "solved". Gracias. :P

---

### Post by nechus on 2010-05-02
Oops!  Carlos C, no alcancé a leer tu post porque estaba escribiendo mi posteo anterior.

Ya devolví el netbook a su dueño. Vamos a ver qué le dicen en Movistar. Si el problema persiste, voy a hacer el ping que dices.

Gracias!

---

### Post by asterix77 on 2010-05-03
Carlos una consulta
 
 
209.85.195.104 es la ip de google español, ¿Se supone que si tienes problemas de DNS de tu proveedor igual ingresas a esta página y a otras no?.
 
Tengo un problema con mi banda ancha movil de entel, es curioso, puedo descargar mis correos desde el server de mi empresa, e ingresar a su página web; y acabo de ingresar a la ip que mencionas. Pero no puedo ingresar a ninguna otra página web, no tengo ping.
 
Veré si puedo solucionar el problema esta noche, o de lo contrario abriré un post acá.
 
 
Saludos

---

### Post by nephlin on 2011-03-12
he intentado con la info q hay aca,
he intentado esto  [http://zdes.wordpress.com/2010/02/11/modem-zte-mf110-en-ubuntu/](http://zdes.wordpress.com/2010/02/11/modem-zte-mf110-en-ubuntu/)
[http://ubuntuforums.org/showthread.php?t=1384221](http://ubuntuforums.org/showthread.php?t=1384221)
[http://www.taringa.net/posts/linux/4123442/Instalar-Modem-3G-ZTE-MF-110-en-Linux.html](http://www.taringa.net/posts/linux/4123442/Instalar-Modem-3G-ZTE-MF-110-en-Linux.html)

he intentado instalando GNOME PPP 


sigo con el mismo problema A VECES RECONOCE EL MODEM Y A VECES NO . . .

---

### Post by RafaelG on 2011-03-15
> **nechus said:**
> Primero instalan este: [http://www.4shared.com/file/APj9D9ut/usb-modeswitch-data_20100418-1.html](http://www.4shared.com/file/APj9D9ut/usb-modeswitch-data_20100418-1.html)Segundo, este: [http://www.4shared.com/file/iyaw_o7R/usb-modeswitch_112-1_i386.html](http://www.4shared.com/file/iyaw_o7R/usb-modeswitch_112-1_i386.html)Y si su procesador es de 64 bits, en vez de instalar el segundo instalan este: [http://www.4shared.com/file/Pt6eC5gt/usb-modeswitch_112-1_amd64.html](http://www.4shared.com/file/Pt6eC5gt/usb-modeswitch_112-1_amd64.html)


Nechus,

Me gustaria poder rescatar una pequena descripcion que se encuentra en el paquete desde synaptic 

> _**Usb-modeswitch-datos**_

Varios de los nuevos dispositivos USB tienen su propiedad a bordo de controladores de Windows,
especialmente WAN dongles. Cuando se enchufa uno por primera vez, este actúa
como un flash de almacenamiento donde se puede instalar el controlador. Si
el controlador ya está instalado el dispositivo de almacenamiento se desvanece y
un nuevo dispositivo aparece como un módem USB. Esto se llama el
"ZeroCD".

En Debian, esto no es necesario, ya que el controlador se incluye como un
Módulo del kernel de Linux, tales como "usbserial". Sin embargo, el dispositivo continua
mostrandose como "usb-storage"por defecto. Usb-modeswitch resuelve el problema mediante el envío de una orden que cambia
el dispositivo de "usb-storage" a "usbserial".
Saludos,

---

