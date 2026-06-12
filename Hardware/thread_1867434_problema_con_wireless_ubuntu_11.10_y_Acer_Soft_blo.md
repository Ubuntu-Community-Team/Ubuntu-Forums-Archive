---
title: "problema con wireless ubuntu 11.10 y Acer: Soft blocker: YES"
date: 2011-10-22
forum: Hardware
---

### Post by canosebastian on 2011-10-22
Wireless y Ubuntu nunca se han llebado bien. Ninguna version de Ubuntu ha funcionado perfectamente con todas las placas de coneccion. 

comando:
 sudo rfkill list 
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
2: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

Si tienes otra placa que no sea Acer se describira otra definicion que no sea acer-wireless, osea que podrian darse otros resultados.

Si dise Soft blocked: YES implica que wireless ha sido desactivado por defecto. 

Solucion 1:

Si estas conectado a Ethernet (Wired Network) desconectate e introduce el siguiente comenado:
sudo rfkill unblock all
sudo rfkill list all

Solution 2: 

Si lo anterior no soluciona el problema introduce:

sudo rmmod -f acer-wmi
sudo rfkill unblock all
sudo rfkill list all

Para hacer esto permanente y no tener que habilitar wireless cada vez que reseteas:

sudo su
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit

Puedes hacer lo mismo con otras placas simplemente cambiando la abreviasion "acer" por el nombre de tu placa.

---

