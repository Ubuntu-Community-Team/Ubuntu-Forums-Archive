---
title: "Dell 1545 con Win 7 64bits en Ubuntu 9.10 KK no me funciona el wireless."
date: 2010-03-15
forum: Hardware
---

### Post by Melva on 2010-03-15
Hola! Hace mucho tiempo yo intente instalar ubuntu en mi vieja ocmputadora y anduvo barbaro y fui feliz hasta que ocurrio un incidente combinando lluvia, demasiado enchufe, y un mal techo que concluyo en una ocmptuadora quemada.
Ahora, como decidi entrar en el siglo 21, me ocmpre una Dell inspiron 1545 con Windows 7 64bits.
Como windows, fiel a si mismo, es una pendorcha, La computadora tiene 20 dias y ya me tira pantallas azules, y el panel de control se cuelga desde el primer dia. Y me dije naaaaaaahhh, vamos con ubuntu.
Y le instale ubuntu 9.10 Karmic Koala, que bonito. Pequeño problema, no reconoce mi tarjeta WLAN 1397 Half MiniCard. Y aclaremos, yo no entiendo una sota. Encuentro threads hablando del tema, pero no se ni por donde empezar a hacer lo que sugieren. Probe algo en la terminal, que no me acuerdo que era, que dice que estan ahi las dos tarjetas, y tengo entendido que el problema es el driver. 
Aclaro que la tarjeta funciona perfecto en windows 7, y el router, tambien, asi que no, no es la tarjeta. 
Pero necesito una explicacion para tontitos de como hacerla funcionar, para rubias tontitas, mas especificamente. Ayuda, alguien?

---

### Post by guillermolisi on 2010-03-15
En una consola/terminal ingresa ```
sudo lshw
``` y luego intenta mostrarnos aqui la salida que te da ese comando. Con eso podremos saber que chip utiliza tu placa inalambrica y que driver deberias estar usando.

Cuando utilizas el comando "sudo" te va a pedir que ingreses una clave. Esa clave no es ni mas ni menos que la que usas para el login de tu usuario en Ubuntu.

La salida que te da el comando "lshw" es mas bien larga. Si bien una gran parte de la informacion que brinda no nos interesa, no vendra mal para atender cualquier otro problema que surja con esa maquina (en caso de que ocurra).

---

