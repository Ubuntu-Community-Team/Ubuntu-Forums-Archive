---
title: "Ubuntu 12.04 LTS Daily Build problema para configurar placa de video nvidia 6 series"
date: 2015-06-19
forum: Hardware
---

### Post by gustavo16 on 2015-06-19
Hola, tenia una pc viejita y se me quemo la placa madre, me instalaron una placa Conroe 945 G-DVL y como me tenia una placa de video nvidia 6600 gt que me habia quedado de la placa madre quemada, pedi que la colocaran. Tengo 1 GB de ram
Como siempre me gusto ubuntu porque lo tenia instalado en la maquina anterior, busque la 12.04 LTS por tener soporte hasta el 2017.
Inicie el live dvd con la opcion de probar la version, un poquito lento pero andaba, luego la instalo pero aparece una pantalla que dice: The system is running in low-mode.

La version que figura en terminal es 3.13.0-55-generic i686

Desde terminal ya probe de instalar los drivers de nvidia de varias formas que encontre en la web pero no hay caso, no tengo el conocimiento para poder lograrlo.
Soy un novato, si alguien podria guiarme les agradeceria


Saludos

---

### Post by euzkoarima on 2015-06-22
Primero, como estás instalando el driver, lo más simple es desde la terminal con el comando ```
sudo apt-get install nvidia-current
```
De todos modos, como ya estuviste tratando de hacer cosas, fijate este link [how-to-fix-the-system-is-running-in-low-graphics-mode-error]("http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error") que tienen la explicación paso a paso.
Si en inglés no te sirve, una versión similar pero "muy resumida" la podés ver en este link de [taringa]("http://www.taringa.net/posts/linux/17249665/Error-The-system-is-running-in-low-graphics-mode.html")

Saludos,
Eduardo

---

