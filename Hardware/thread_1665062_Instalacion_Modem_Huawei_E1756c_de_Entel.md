---
title: "Instalacion Modem Huawei E1756c de Entel"
date: 2011-01-11
forum: Hardware
---

### Post by javierfigueroa on 2011-01-11
Tengo instalado ubuntu en mi pc. Recientemente adquiri un plan de internet móvil de entel, el huawei corresponde a un 1756C. Sin embargo,no puedo navegar en este sistema. 
Cómo puedo configurarlo para usarlo?
Agradeceré profundamente los aportes.

---

### Post by asterix77 on 2011-01-12
Vamos por parte:

Primero es importante averiguar si ubuntu lo reconoce como módem, ya que hay algunos módems usb que solo los reconoce como unidades de almacenamiento. Para ello debes escribir en consola lo siguiente:

$lsusb

En la salida debe haber algo parecido a:

.......
Bus 001 Device 003: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
......

En el ejemplo si aparece detectado como "Modem"

Si solo aparece reconocido como unidad de almacenamiento, debes instalar el paquete usb-modeswitch

Nuevamente en la terminal escribes:

$sudo apt-get install usb-modeswitch (creo que está en los repositorios de ubuntu). En caso de no estarlo lo puedes descargar de la siguiente dirección:

[https://forge.betavine.net/frs/?group_id=12](https://forge.betavine.net/frs/?group_id=12)

Después de esto no deberías tener problemas para conectarte. Lo puedes hacer de distintas formas, la mas usual es por network manager, también por wvdial. En el enlace anterior, también puedes intentar descargar e instalar las aplicaciones "Betavine connection Manager", o "Vodafone Mobile Connect Card Driver For Linux". La gracia de estas dos últimas es que la aplicación es muy similar a las que vienen en los respectivos módem para windows.

Saludos

PD: Si vas a instalar las aplicaciones del proyecto betavine, primero averigua si tu módem está soportada. La gran mayoría de los modem huawei están soportadas en todo caso.

---

### Post by RafaelG on 2011-01-14
Javierfigueroa,


Bueno yo tengo el mismo modem con Entel asi que te puedo recomendar  leer el siguiente donde detalla rapidamente como instalar y configurar el modem ya que funcione correctamente en tu sistema.

Nota: He modificado el titulo del thread para que pueda ser mas factible la busqueda en el forum y sea mas especifica la busqueda.

Saludos cordiales,

---

### Post by RafaelG on 2011-01-14
Javierfigueroa,


Bueno yo tengo el mismo modem con Entel asi que te puedo recomendar  leer el siguiente Link donde detalla rapidamente como instalar y configurar el modem en Ubuntu.

Instalacion Modem Huawei E176c en Entel:
[http://ubuntuparatodos.wordpress.com/2010/07/30/instalar-modem-huawei-e1756c-entel-en-ubuntu-10-04/](http://ubuntuparatodos.wordpress.com/2010/07/30/instalar-modem-huawei-e1756c-entel-en-ubuntu-10-04/)

Nota: He modificado el titulo del thread para que pueda ser mas factible la busqueda en el forum y sea mas especifica la busqueda.

Saludos cordiales,

---

