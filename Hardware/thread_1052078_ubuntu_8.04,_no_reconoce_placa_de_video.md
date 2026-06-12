---
title: "ubuntu 8.04, no reconoce placa de video"
date: 2009-01-27
forum: Hardware
---

### Post by ss222 on 2009-01-27
hola, bueno soy nuevo asi que de paso me presento :D
por lo que veo, desde que actualize a 8.04, dejaron de andar primero los driver de la placa y luego la placa, tengo compartido el disco con guindows asi que la placa de video anda por que me serciore hay, pero si hago la prueba de hardware reconoce que tengo una nvidia, pero en controladores de hardware no!

es por qwe ubuntu 8.04 no es compatible o hay un error?

placa de video: Geforce 6100 nforce 405
Placa madre: Geforce 6100 SM-M

---

### Post by guillermolisi on 2009-01-27
> **ss222 said:**
> hola, bueno soy nuevo asi que de paso me presento :D
por lo que veo, desde que actualize a 8.04, dejaron de andar primero los driver de la placa y luego la placa, tengo compartido el disco con guindows asi que la placa de video anda por que me serciore hay, pero si hago la prueba de hardware reconoce que tengo una nvidia, pero en controladores de hardware no!

es por qwe ubuntu 8.04 no es compatible o hay un error?

placa de video: Geforce 6100 nforce 405
Placa madre: Geforce 6100 SM-M

Desde que version actualizaste a 8.04 ?

Activaste los controladores propietarios para la placa ?

Esa placa funciona bien con esa version de Ubuntu, asi que no aflojes que tiene solucion.

---

### Post by karlos8712 on 2009-02-02
Bueno en realidad no se que le pasa a mis sistema.

Desde que actualice desde hardy heron a intrepid no me corren algunos programas y pienso yo(con muy poca experiencia) que es un problema con la placa de video, antes me corria blender y algunos juegos como openarena, dreamchess y otros pero desde entonces ya ni abren dichas aplicaciones.

antes con un glxinfo | grep direct me salian un mundo de cosas y hasta una poca aceleracion segun otros foros pero ahora solo me sale:

name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10

Lo mismo que sale cuando intento iniciar blender desde una terminal.

les agradeceria cualquier ayuda.:(

---

