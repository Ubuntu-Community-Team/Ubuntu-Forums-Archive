---
title: "Problema. Instalacion de Mother ASUS"
date: 2009-01-02
forum: Hardware
---

### Post by vagoybostero on 2009-01-02
Como veran por mi usuario, soy novato en Ubuntu.
Realmente lo tengo instalado hace tiempo, pero como no tengo tiempo durante el año, me dedico a usar windows ya que lo tenia configurado y listo para usar.

Volviendo al tema... La version 8.04 (64) no me detecta automaticamente mi mother Asus M2NPV-VM. Es por ello que trato de instalarlos desde el CD que habia venido cuando la compre.

Para instalarlo segui los siguientes pasos:
Abro la consola, me autentico como root, y arrastro el Driver.run (que vino en el cd) y lo instalo.
Luego de pedirme que acepte los terminos y condiciones, me salta el siguiente error:

[B]No precompiled kernel interface was found to match your kernel; this means that the installer will need to compile a new kernel interface.

ERROR: You do not appear to have libc header files installed on your system. Please install your distribution's libc development package.[/B]

Realmente no se que quiere decir esto, asi que si alguien me puede ayudar se lo agradeceria mucho.

Debido a que no pueod instalar esos drivers, no puedo usar nada ya que la placa tiene todo on board :(

Desde ya les agradezco que se tomen la molestia de leer mi duda...

---

### Post by Hei Ku on 2009-01-02
Pone esto en una consola:

```

sudo apt-get install build-essential

```

Lo que pasa es que no tenés instaladas las herramientas de compilación.

PD: Movido a Hardware

---

### Post by vagoybostero on 2009-01-04
> **Hei Ku said:**
> Pone esto en una consola:

```

sudo apt-get install build-essential

```

Lo que pasa es que no tenés instaladas las herramientas de compilación.

1) Gracias por moverlo donde iba y perdon por haberlo puesto en cualquier lado

2) Poniendo eso solo ya se "instalaran" las herramientas de compilacion?

---

### Post by vagoybostero on 2009-01-04
Hai Ku puse lo que me dijiste... pero me tira el siguiente error:

administrador@pcpatricio:~$ sudo apt-get install build-essential
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
E: No se pudo encontrar el paquete build-essential

Q es eso??? Q puedo hacer???

Porq se me niega tanto linuxxxxxxxxxxxxxx????????????????

---

### Post by Hei Ku on 2009-01-04
Es muy raro que no tengas ese paquete.

Proba esto:
```

sudo apt-get update
sudo apt-get install build-essential

```

Si te sigue dando el mismo error, posteá acá el contenido del archivo /etc/apt/sources.list

PD: Recibi tu mensaje, pero es mejor seguir la conversacion por el foro para que otros tambien puedan aprender

PD2: Si es posible, posteá también el resultado de poner lspci en la pantalla. Es raro que no te tome la placa de red automaticamente. En general no hay que hacer nada para instalarla.

---

### Post by vagoybostero on 2009-01-07
Hei Ku antes que nada quiero agradecerte por comprometerte con mi problema y aportar soluciones, pero lo de hacer **sudo apt-get update** y **sudo apt-get install build-essential** no me sirvio.

El problema es que no tengo internet por 2 razones:
[LIST=1]
[*]No tengo configurada la placa de red porq es on board, y los drivers que intento instalar son de la mother
[*]Por mas que instale los drivers del mother, todavia me falta instalar los drivers del modem (un ZyXEL Prestige 600) y configurar la conexion
[/LIST]

En el laburo me dijeron que abra el synaptic y genere un script del build-essential. Luego correr ese script en el laburo, en un ubuntu con internet, para bajar todo lo que necesite y despues llevarlo a mi maquina.

El problema es que con el synaptic no encuentro el build-essential. Entonces me dijeron que la instalacion que tengo esta mal. Asi que voy a instalar el 8.10 y ver que onda...

---

### Post by Hei Ku on 2009-01-07
Proba el 8.10, a ver si te toma la placa de red. Con eso te ahorras unos pasos.

Si no, en packages.ubuntu.com, te fijas el paquete build-essential y te bajas el .deb
Lo copias a un lugar que lo puedas acceder desde el ubuntu y lo instalas dandole doble click.

---

### Post by MeduZa on 2009-01-07
pone y pega aca lo que te salga cuando pones:
lsusb
y
lspci

---

### Post by vagoybostero on 2009-01-08
> **Hei Ku said:**
> Proba el 8.10, a ver si te toma la placa de red. Con eso te ahorras unos pasos.

Si no, en packages.ubuntu.com, te fijas el paquete build-essential y te bajas el .deb
Lo copias a un lugar que lo puedas acceder desde el ubuntu y lo instalas dandole doble click.

Gracias por la info. Ayer en casa no tuve tiempo de instalarlo, asi que me voy a bajar el paquete y voy a ver que onda. Igualmente la idea es instalar rl 8.10, porq capaz soluciono este tema, pero si la instalacion esta cagada, seguro voy a tener otros problemas en el futuro.

> **MeduZa said:**
> pone y pega aca lo que te salga cuando pones:
lsusb
y
lspci

Ok. Hoy hago eso y te copio lo q sale pero... para q es??

---

### Post by Hei Ku on 2009-01-08
te muestra que tenes conectado por usb y por pci.

---

### Post by vagoybostero on 2009-01-18
Hola gente antes que nada pido perdon por haber desaparecido tanto tiempo.

Les cuento q pude resolver el problema. Gracias a lo q dijeron de poner lspci y lsusb, pude ver que tenia reconocido el modem usb (ZyXEL Prestige Series 600). Entonces me puse en campaña en buscar como configurar la conexion a internet. La pude hacer siguiendo el tutorial q esta en este link: [http://ubuntu-ar.org/soporte/comos/modemzyxel]("http://ubuntu-ar.org/soporte/comos/modemzyxel")

Una vez q tuve instalado el modem, pude hacer todas las actualizaciones y ahi tomo todo bien.

Desde ya les agradezco infinitamente que me hayan ayudado y realmente gracias a lo q dijeron pude solucionar el problema y ahora ya casi ni uso Win XP!!! jajajaja

---

### Post by vagoybostero on 2009-01-18
Hola gente antes que nada pido perdon por haber desaparecido tanto tiempo.

Les cuento q pude resolver el problema. Gracias a lo q dijeron de poner lspci y lsusb, pude ver que tenia reconocido el modem usb (ZyXEL Prestige Series 600). Entonces me puse en campaña en buscar como configurar la conexion a internet. La pude hacer siguiendo el tutorial q esta en este link: [http://ubuntu-ar.org/soporte/comos/modemzyxel]("http://ubuntu-ar.org/soporte/comos/modemzyxel")

Una vez q tuve instalado el modem, pude hacer todas las actualizaciones y ahi tomo todo bien.

Desde ya les agradezco infinitamente que me hayan ayudado y realmente gracias a lo q dijeron pude solucionar el problema y ahora ya casi ni uso Win XP!!! jajajaja

---

