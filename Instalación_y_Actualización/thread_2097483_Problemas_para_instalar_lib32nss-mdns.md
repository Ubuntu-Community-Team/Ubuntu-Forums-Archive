---
title: "Problemas para instalar lib32nss-mdns"
date: 2012-12-23
forum: Instalación y Actualización
---

### Post by yumbo on 2012-12-23
Hola, 

Estoy intentando instalar el paquete **lib32nss-mdns **escribiendo en la terminal:

[INDENT]sudo apt-get install lib32nss-mdns
[/INDENT]
pero me sale el siguiente error:

[INDENT]Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
El paquete lib32nss-mdns no está disponible, pero algún otro paquete hace referencia
a él. Esto puede significar que el paquete falta, está obsoleto o sólo se
encuentra disponible desde alguna otra fuente

E: El paquete «lib32nss-mdns» no tiene un candidato para la instalación

[/INDENT]Si alguien me pudiera ayudar se lo agradecería porque sin este paquete no me funciona la aplicación Java correctamente, dándome un java.net.UnknownHostException.

Muchas gracias de antemano.

---

### Post by Sortega on 2012-12-28
Que versión de Ubuntu tienes?, yo estoy usando la 12.04 y si pude instalar ese paquete.

Saludos

---

### Post by HernanLinux93 on 2012-12-29
ya intentastes actualizar los paquetes eso puede ser el problema
y que version de Ubuntu estas utilizando ahora? Ubuntu 12.04.1 LTS??
para actualizar los repositorios en Ubuntu[COLOR=#008000] [COLOR=Black]sudo gedit /etc/apt/sources.list[/COLOR][/COLOR] Si lo anterior no funciona, podes probar un editor de texto en consola: sudo nano /etc/apt/sources.list

---

