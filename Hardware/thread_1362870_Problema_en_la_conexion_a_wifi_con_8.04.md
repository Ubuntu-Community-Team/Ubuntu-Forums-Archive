---
title: "Problema en la conexion a wifi con 8.04"
date: 2009-12-23
forum: Hardware
---

### Post by fedescha on 2009-12-23
Instalé mi querido y viejo 8.04 en la maquina de la oficina.
Tengo un problema para conectarme a internet inalambrico. Aparece la señal de la red con una conectividad que va del 71% al 84%, pero no se conecta a internet. El firefox no tiene conexion y no puedo actualizar nada.
No se si se entiende.
Escucho o leo consejos, muchas gracias.

---

### Post by Applelnx on 2009-12-24
Hola fedescha. Si entendi bien, Ubuntu detecta las redes pero no puede conectarse. Para empezar convendria que postees de que computadora estas hablando, poniendo que placa de wifi tenes. Ahora te hago un par de preguntas:

- Estas seguro que estas poniendo bien la contraseña del Wifi con el tipo de encriptacion? (diria que esta es la primer cosa que tenes que comprobar por mas que suene muy estupida)
- Que drivers tenes? Los que vinieron por default en Ubuntu o instalaste otros?

La verdad es que no no soy muy ducho en estos temas asi que no se si podre ayudarte demasiado. Saludos

---

### Post by guillermolisi on 2009-12-24
> **fedescha said:**
> Instalé mi querido y viejo 8.04 en la maquina de la oficina.
Tengo un problema para conectarme a internet inalambrico. Aparece la señal de la red con una conectividad que va del 71% al 84%, pero no se conecta a internet. El firefox no tiene conexion y no puedo actualizar nada.
No se si se entiende.
Escucho o leo consejos, muchas gracias.
Mostra las salidas de "lspci" y "lsusb" (sin las comillas), tambien el contenido de /etc/networking/interfaces asi vemos algo mas de detalle al respecto.

Tambien seria interesante saber como es la salida a Internet en esa oficina por si tienen proxy, transparente o no, alguna disposicion en particular o es directa.

---

### Post by fedescha on 2009-12-26
Encontré una solución más simple. Baje la imajen de 9.10 y lo instalé. ahora no tengo problemas con internet.
Tengo que reorganizar las particiones pero eso es otro problema.
También teno el link a realtek para bajar los drivers de la placa que creo es muy útil.
Realtek RTL8111B/RTL8168B/RTL8111/RTL8168
RTL8111C/RTL8111CP/RTL8111D(L)
RTL8168C/RTL8111DP/RTL8111E
RTL8105E

http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168<br>RTL8111C/RTL8111CP/RTL8111D(L)<br>RTL8168C/RTL8111DP/RTL8111E<br>RTL8105E

saludos y muchas gracias.

---

