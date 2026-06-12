---
title: "Problemas con Ubuntu-netbook"
date: 2010-10-07
forum: Hardware
---

### Post by Rodo040 on 2010-10-07
Hola a todos, quisiera decirles que este foro es de gran ayuda para todos los que nos estamos iniciando en estos temas de ubuntu.
Puntualmente estoy con un problema, tengo una Compaq Evo N400C con una placa wireless linksys WPC11, tengo configurado el perfil para que se conecte a la red wireless de mi casa pero lo hace solo al iniciar el equipo y por no mas de un minuto, luego aparece el cartel de "sin conexion".
La red es OPEN y solo tiene MAC Filter (tambien probé sin MAC Filter y con autenticacion).
Alguien sabe que puede estar fallando?
Ah, en otras maquinas (linux/windows) esto no pasa, es mas, cuando la compaq se conecta aparece en la lista de macs conectadas y hasta le da IP el DHCP y puede navegar sin problemas durante el tiempo que está conectada.
Realmente, muy raro.
Muchas Gracias.

---

### Post by guillermolisi on 2010-10-07
Esa interface wifi es USB externa ?
Cuando mencionas que en otras maquinas funciona bien con Win y Linux, es la misma antena inalambrica o es otra ?
Que version de Ubuntu estas usando ?

Podrias mostrarnos la salida de los siguientes comandos en una terminal/consola ?:

```
sudo lshw
```
```
lsusb
```
```
lsmod
```
```
lspci
```

Para saber que version de Ubuntu y que kernel estas usando, ingresa en consola/terminal

```
uname -a
```

---

