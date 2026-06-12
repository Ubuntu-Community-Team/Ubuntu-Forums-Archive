---
title: "Valores BAUD Modem banda ancha movil"
date: 2009-11-17
forum: Hardware
---

### Post by asterix77 on 2009-11-17
Les cuento que en mi trabajo la señal 3g de mi modem Huawei E176, es muy débil, tanto que es preferible trabajar con edge. El problema es que tiende a captarse esa señal, y al ser muy débil se vuelve a conectar a edge. Esto trae como consecuencias retrasos en la navegación.

Mi consulta es entonces, ¿como configurar el módem de tal forma que solo me capte única y exclusivamente edge y evitar que se trate de conectar a 3g (HSPA)?.

Por lo que he leido, al parecer para esto hay que modificar los valores de BAUD (me conecto a través de wvdial), pero he buscado en internet y no he logrado dar con la solución.

Por cierto uso BAM de Entel Pcs.

Saludos

---

### Post by moreback on 2009-11-17
Yo creo que la selección de las bandas depende del modem que tengas y debieran usarse comandos AT para hacer eso.

Busca el manual de los comandos AT de tu modem 3G.

Saludos.

---

### Post by asterix77 on 2010-01-11
Estimados ubunteros

Hace bastante tiempo que tenía problemas en mi trabajo con este modem, por lo comentado por mi en el primer post.
Configurar este modem para que trabaje solo en edge, o solo en 3g en windows, es fácil ya que para ello existe la aplicación que viene en el. La única opción entonces era conectarlo a un pc con windows, configurarlo para que solo capte edge (en mi trabajo), e instalarlo en mi ubuntu. Curiosamente el modem guardaba la conexión, y en ubuntu solo enganchaba en edge.

Finalmente encontré una solución para no depender de windows.

En mi caso (karmic amd64), descargué el archivo [COLOR=Black][ vodafone-mobile-connect_2.15.01-2_all.deb]("https://forge.betavine.net/frs/download.php/583/vodafone-mobile-connect_2.15.01-2_all.deb")[/COLOR] desde la siguiente página [https://forge.betavine.net/frs/?group_id=12](https://forge.betavine.net/frs/?group_id=12), donde aparecen otras distros y arquitecturas.
Al tratar de instalarlo aparecía un error de dependencias con el archivo ozerocdoff, que lo descargué de la misma página web [https://forge.betavine.net/frs/download.php/456/ozerocdoff_0.4_amd64.deb](https://forge.betavine.net/frs/download.php/456/ozerocdoff_0.4_amd64.deb)

Finalmente se instaló todo; corrí la aplicación, me detectó el módem, se abre un diálogo para elegir el proveedor de aceeso a internet, y lo más importante: coloca las mismas opciones que en windows donde uno puede escoger el tipo de red a conectarse.

Otro aspecto que hay que considerar es que me parece que soporta varios modelos de módem de BAM.

Saludos, y espero que a alguien les sirva esto.

---

