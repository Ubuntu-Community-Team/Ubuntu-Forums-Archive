---
title: "Red ad hoc problema con orden de inicio"
date: 2010-03-30
forum: Hardware
---

### Post by totolinux on 2010-03-30
Hola a todos: es complicado de explicar lo que sucede y es lo siguiente.
tengo una pc de llamada escritorio:
amd sempron 1400 mhs 
ram 512 
eth0
wlan0 rtl8187 (encore) usb driver xp con ndiswrapper 
ubuntu 9.04 y xp 
internet a traves  de cable de red eth0 con ip fija
y el dispositivo de wifi lo uso para compartir internet modo ad hoc con ip fija a una notebook packard bell (ubuntu 9.04). He Configurado todo manualmente. Me refiero a interfaces e iptables. 
Logré hacer una red ad hoc con una notebook que además de verse, comparten archivos y además administro por ssh. hasta aquí todo bien.
El problema es que cuando arranca la pc escritorio primero y luego la notebook no logro que comparta internet ni se vean (ping) pero me indica la notebook que están conectadas a la red.
Para hacer funcionar la red tengo que reiniciar la pc escritorio o hacer siempre que la notebook arranque primero, una vez hecho esto puedo apagar la notebook todas la veces que quiero, que no pierdo la conexión.
Aclaro que cuando uso xp en la pc escritorio esto no pasa, se conectan siempre. Todo lo demás no anda :D pero es otro tema jaja
Desde ya muchas gracias

---

### Post by totolinux on 2010-04-02
Me gustaría saber que servicios puedo reiniciar para ver cual es el que falla y de esta manera solucionarlo o hacer un script para que cada vez que el sistema arranca se reinicie determinado demonio conflictivo.
He probado con  
sudo ifdown wlan0
sudo /etc/init.d/networking restart
sin resultados satisfactorios. alguien me puede sugerir otro?
Estoy seguro que el problema es esta rtl8187 ENCOOOORE
Gracias por su atención

---

### Post by totolinux on 2010-04-06
Bueno lo he solucionado de la siguiente manera: instalé firestarter 
luego en lugar de reiniciar la pc servidora inicio el cortafuegos (firestarter) y listo comparten internet y todo lo otro.

---

