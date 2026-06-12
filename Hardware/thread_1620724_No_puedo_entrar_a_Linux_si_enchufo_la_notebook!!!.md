---
title: "No puedo entrar a Linux si enchufo la notebook!!!"
date: 2010-11-13
forum: Hardware
---

### Post by exxon_valdez on 2010-11-13
Hola a todos!  hace poco compré una notebook (Eurocase E12) y le instalé Ubuntu 10.04 (vale decir que soy novato en Linux) y resulta que al prenderla, si quiero entrar a Linux, tengo que desenchufarla para poder entrar. De lo contrario, la pantalla se pone en negro y no hace nada. En cambio, con windows 7 no tengo problemas.  

Les cuento: mi notebook tiene una tarjeta gráfica ATI 4650. Obviamente, cuando le puse Ubuntu dí un millón de vueltas para instalarle el controlador. Al principio, Ubuntu ponía un controlador genérico pero el ventilador no paraba de girar y se calentaba tanto que podía hacer un asado sobre el teclado. Entonces le instalé los controladores de la página oficial de ATI (siguiendo las intrucciones) pero la pantalla se ponía en negro (o también púrpura). En fin... hice un montón de cosas que ya ni me acuerdo.
Terminé intalando el controlador FGLRX privativo (Sistema->Administración->Controladores de hardware). Como siempre, la pantalla se ponía en negro cuando quería entrar a Linux. Pero de casualidad, un día no tenía enchufada la notebook y pude entrar! Desde ahí, me dí cuenta del patrón: "Enchufada = No entra a Linux"/ "No enchufada = Entra a Linux".  El problema es cuando entra; una vez que entró la puedo enchufar sin causar problemas.

Pensé que podía ser un problema con la batería, por lo que la saqué y dejé simplemente la notebook enchufada a la corriente eléctrica, pero no hubo caso: no podía entrar.

Por otro lado, sí puedo entrar a Linux cuando está enchufada pero únicamente en Modo Gráfico Seguro.
¿Alguien tuvo el mismo problema? ¿por qué se repite este patrón en mi computadora?:confused:
Gracias!

---

### Post by hectorivand on 2010-11-15
> **exxon_valdez said:**
> Hola a todos!  hace poco compré una notebook (Eurocase E12) y le instalé Ubuntu 10.04 (vale decir que soy novato en Linux) y resulta que al prenderla, si quiero entrar a Linux, tengo que desenchufarla para poder entrar. De lo contrario, la pantalla se pone en negro y no hace nada. En cambio, con windows 7 no tengo problemas.  

Les cuento: mi notebook tiene una tarjeta gráfica ATI 4650. Obviamente, cuando le puse Ubuntu dí un millón de vueltas para instalarle el controlador. Al principio, Ubuntu ponía un controlador genérico pero el ventilador no paraba de girar y se calentaba tanto que podía hacer un asado sobre el teclado. Entonces le instalé los controladores de la página oficial de ATI (siguiendo las intrucciones) pero la pantalla se ponía en negro (o también púrpura). En fin... hice un montón de cosas que ya ni me acuerdo.
Terminé intalando el controlador FGLRX privativo (Sistema->Administración->Controladores de hardware). Como siempre, la pantalla se ponía en negro cuando quería entrar a Linux. Pero de casualidad, un día no tenía enchufada la notebook y pude entrar! Desde ahí, me dí cuenta del patrón: "Enchufada = No entra a Linux"/ "No enchufada = Entra a Linux".  El problema es cuando entra; una vez que entró la puedo enchufar sin causar problemas.

Pensé que podía ser un problema con la batería, por lo que la saqué y dejé simplemente la notebook enchufada a la corriente eléctrica, pero no hubo caso: no podía entrar.

Por otro lado, sí puedo entrar a Linux cuando está enchufada pero únicamente en Modo Gráfico Seguro.
¿Alguien tuvo el mismo problema? ¿por qué se repite este patrón en mi computadora?:confused:
Gracias!

Hola Exxon, es un patrón, bastante raro. Aunque puede ser que teniendo la notebook enchufada, el sistema quiera iniciarte con los efectos de escritorio activados desde el comienzo y ahí tengas problemas.

Cuando la arrancas con la batería, por la gestión de energía, no carga algunos y extras y el problema no existe. 

Podes probar con esto.:

```
sudo apt-get remove compiz-core
```

```
sudo dpkg-reconfigure xserver-xorg
```

Esto si acusamos al driver de vídeo como el conflictivo.

Con en el driver de ATI que viene en la distro, tan mal te anda? tengo una HD3100 en la Toshiba y funciona mucho mejor que el privativo.

Saludos
Nacho

---

### Post by asterix77 on 2010-11-17
¿posible error de acpi?

Sería interesante ver que te arroja el sistema, para ello escribe "dmesg" en consola y pégalo acá.


¿qué pasa si inicias con batería y una vez arrancado lo conectas a la corriente?¿igual se pone la pantalla negra?

Saludos

---

### Post by faktorqm on 2010-11-18
ya respondio eso, una vez arrancada la compu la enchufa y anda normal.

yo voy 97% a un problema de acpi. cuando pegues el dmesg te decimos posibles soluciones. salu2!

---

### Post by exxon_valdez on 2010-11-18
Hola a todos! Gracias por darme una mano!  hectorivand, hice lo que me dijiste pero no tuve éxito: la compu seguía sin entrar si estaba enchufada. Con respecto al comando "dmesg", la salida es la siguiente:

[    0.000000] Initializing cgroup subsys cpuset
..... Bla, bla,bla (jeje) Lo acabo de borrar (19/12/10) Si alguien necesita la salida que me dá el comando dmesg lo vuelvo a poner. No hay problema
[   51.688026] wlan0: no IPv6 routers present

Saludos,
Exxon

---

### Post by exxon_valdez on 2010-12-19
Hola a todos! Creo que acabo de encontrar la solución. Aparentemente es un problema con la opción de "Power Play". La cosa es así: voy a 

'Sistema>Preferencias>ATI Catalyst Control Center(Administrador)' 

y veo que en la sección "Power Play" está seleccionado 'Enable Power Play' y en 'When the power source is plugged in' veo que está al máximo!!!.     Cuando deshabilito 'Enable Power Play': voilá! puedo entrar a Linux con la computadora enchufada!!!!. Lo que no entiendo es cómo puede afectar tanto a la computadora la opción de Power Play. ¿Alguna idea? Espero que el dato ayude a otros que tienen problemas con ATI y los drivers privativos. Tal vez configurar mal Power Play cause algunos problemas. 

Saludos, 

Exxon

---

