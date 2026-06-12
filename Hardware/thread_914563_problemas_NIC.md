---
title: "problemas NIC"
date: 2008-09-08
forum: Hardware
---

### Post by llove on 2008-09-08
hola, estoy teniendo problemas con una placa de red, una realtek 8139, es una instalacion de cero de Ubuntu Hardy (de hecho la reinstale por si habia hecho algo mal), en fin, la placa de red figura como deshabilitada. buscando soluciones encontre varias cosas a hacer.

lshw -C network me da algo asi como
*-network:0 DISABLED

si pongo ifup eth0 me dice
SIOCSIFFLAGS: Invalid argument

lo mismo con ifconfig eth0 up

probe tambien editando /etc/netowork/interfaces dandole la mac que me aparece haciendo ifconfig -a y nada, lo mismo, sigue sin andar, sigue deshabilitada.
lei que algunas placas tiene problemas con dual boot con windows, pero esta placa no la use en windows, de hecho la saque de otra maquina con ubuntu, funcionando.

si necesitan que agregue algo mas avisen,,,espero su ayuda.
saludos.

---

