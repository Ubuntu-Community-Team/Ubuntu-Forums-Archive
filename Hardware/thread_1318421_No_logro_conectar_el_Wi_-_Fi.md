---
title: "No logro conectar el Wi - Fi"
date: 2009-11-07
forum: Hardware
---

### Post by barkaial on 2009-11-07
Hola,

Tengo un computador Acer Aspire One D150 y le instale ubuntu 9.10 netbook remix. Todo va bien excepto que el wifi no se quiere conectar. He buscado por todo internet montones de soluciones pero no he logrado que ninguna funcione realmente. Soy nuevo en esto de Ubuntu asi que he hecho todo lo que he podido. Me puedo conectar a internet via cable, y a traves de eso instale los drivers que me ofrecia el instalador de hardware de ubuntu, pero no han funcionado. Tambien instale Wicd, que segun una pagina podria funciarme, pero no paso nada...

Les dejo las caracteristicas de mi Pc que extraje con el programa que me baje de este foro ;D.

```

Escritorio:    GNOME

```
```

$iwconfig
eth2      IEEE 802.11bg  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          

```
```

$cat /proc/net/wireless
Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 22

```
```

$lsmod |grep wlan && lsmod |grep ath && lsmod |grep ra

```
```

$cat /etc/network/interfaces
auto lo
iface lo inet loopback


```
Gracias de antemano por la solucion.

---

### Post by RafaelG on 2009-11-08
> **barkaial said:**
> Todo va bien excepto que el wifi no se quiere conectar.

Hola Barkaial seria Bueno que proporciones el lspci de tu PC

---

### Post by rey_satan on 2009-11-08
mira amigo lo mas facil que se me ocurre es que vallas al synaptic y busques  el bcmwl-kernel-source y el bcmwl-modaliases y veas si estan instalado si no lo estan que creo que es el caso instalalos y reinicia y cuentas como te fue con el wifi

---

### Post by barkaial on 2009-11-08
Weno, ya lo arregle, no estoy muy seugor como pero bueno xD.

Pueden cerrar este post.

---

### Post by Carlos C on 2009-11-08
Lastima, la idea es saber cómo se resuelven los problemas para que a la próxima persona que le pase lo mismo sea posible ayudarla considerando el mismo procedimiento.

Mi humilde consejo es que evites intervenir el sistema sin estar seguro de lo que haces ;)

Me alegro que se solucionara el problema. No lo dejo "solved", ya que ignoramos cómo fue que se arregló el wifi. Si te acuerdas de lo que hiciste no dudes en publicarlo.

Saludos.

---

