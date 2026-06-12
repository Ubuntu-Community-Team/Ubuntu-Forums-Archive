---
title: "ADSL modem zyxel 600 usb"
date: 2005-04-29
forum: Hardware &amp; Laptops
---

### Post by Nico666 on 2005-04-29
I try to install this modem following this steps from the site [http://es.geocities.com/robmasterxx/](http://es.geocities.com/robmasterxx/)

#  Module Kernel for Zyxel 630-c1
> tar xzf modulo-630-c1.tar.gz
> cd modulo-630-c1
> make
> make install

#  cxacru para Zyxel 630-c1
> tar xzf cxacru-630-new.tar.gz
> cd cxacru-630-new
> make

But in this final make a large list of errors appear (i posts the list of erros in the end of message).

Please help me.

ERROR:

[B]root@Benz:/home/nico/driver_modem_zyxel/cxacru-630-new # make

cd init && make clean

make[1]: Entering directory `/home/nico/driver_modem_zyxel/cxacru-630-new/init'


rm -f cxload cxioctl cxloaddbg cxloaddbgt
make[1]: Leaving directory `/home/nico/driver_modem_zyxel/cxacru-630-new/init'


cd bridged && make clean
make[1]: Entering directory `/home/nico/driver_modem_zyxel/cxacru-630-new/bridged'


rm -f br2684ctl
make[1]: Leaving directory `/home/nico/driver_modem_zyxel/cxacru-630-new/bridged'


cd init && make && make install


make[1]: Entering directory `/home/nico/driver_modem_zyxel/cxacru-630-new/init'


gcc -O2 -Wstrict-prototypes -fomit-frame-pointer -pipe -march=i686 -Wall -DLINUX -I../include -lusb -lpthread cxload.c -o cxload


cxload.c:132:17: usb.h: No existe el fichero o el directorio


En el fichero incluído de cxload.c:133:


../include/usbi.h:4:17: usb.h: No existe el fichero o el directorio


In file included from cxload.c:133:


../include/usbi.h:49: error: error de decodificación before '*' token


../include/usbi.h:49: aviso: function declaration isn't a prototype


../include/usbi.h:54: error: error de decodificación before '*' token


../include/usbi.h:54: aviso: function declaration isn't a prototype


../include/usbi.h:55: error: error de decodificación before '*' token


../include/usbi.h:55: aviso: function declaration isn't a prototype


cxload.c:236: error: error de decodificación before '*' token


cxload.c:237: aviso: function declaration isn't a prototype


cxload.c: En la función `transfer_ctrl_msg':


cxload.c:247: aviso: implicit declaration of function `usb_control_msg'


cxload.c:247: error: `adsl_handle' undeclared (first use in this function)


cxload.c:247: error: (Each undeclared identifier is reported only once


cxload.c:247: error: for each function it appears in.)


cxload.c:247: error: `requesttype' undeclared (first use in this function)


cxload.c:247: error: `request' undeclared (first use in this function)


cxload.c:247: error: `value' undeclared (first use in this function)


cxload.c:247: error: `buf' undeclared (first use in this function)


cxload.c:247: error: `size' undeclared (first use in this function)


cxload.c:257: aviso: implicit declaration of function `usb_strerror'


cxload.c:257: aviso: el argumento de formato no es un puntero (argumento 2)


cxload.c:259: aviso: implicit declaration of function `usb_clear_halt'


cxload.c: En el nivel principal:


cxload.c:275: error: error de decodificación before '*' token


cxload.c:276: aviso: function declaration isn't a prototype


cxload.c: En la función `read_bulk':


cxload.c:281: error: `buf' undeclared (first use in this function)


cxload.c:287: aviso: implicit declaration of function `usb_bulk_read'


cxload.c:287: error: `adsl_handle' undeclared (first use in this function)


cxload.c:287: error: `ep' undeclared (first use in this function)


cxload.c:287: error: `size' undeclared (first use in this function)


cxload.c:297: aviso: el argumento de formato no es un puntero (argumento 2)


cxload.c: En el nivel principal:


cxload.c:314: error: error de decodificación before '*' token


cxload.c:315: aviso: function declaration isn't a prototype


cxload.c: En la función `send_bulk':


cxload.c:321: error: `nfil' undeclared (first use in this function)


cxload.c:327: aviso: implicit declaration of function `usb_bulk_write'


cxload.c:327: error: `adsl_handle' undeclared (first use in this function)


cxload.c:327: error: `ep' undeclared (first use in this function)


cxload.c:327: error: `buf' undeclared (first use in this function)


cxload.c:327: error: `ncol' undeclared (first use in this function)


cxload.c:337: aviso: el argumento de formato no es un puntero (argumento 2)


cxload.c: En el nivel principal:


cxload.c:383: error: error de decodificación before '*' token


cxload.c:384: aviso: function declaration isn't a prototype


cxload.c: En la función `dispatch_info':


cxload.c:397: error: `adsl_handle' undeclared (first use in this function)


cxload.c:438: aviso: el argumento de formato no es un puntero (argumento 2)


cxload.c:442: aviso: implicit declaration of function `usb_resetep'


cxload.c:449: error: `timeout' undeclared (first use in this function)


cxload.c: En el nivel principal:


cxload.c:459: error: error de decodificación before '*' token


cxload.c:460: aviso: function declaration isn't a prototype


cxload.c: En la función `send_cmd_wait_answers':


cxload.c:464: error: `adsl_handle' undeclared (first use in this function)


cxload.c:464: error: `buf' undeclared (first use in this function)


cxload.c:470: error: `answers' undeclared (first use in this function)


cxload.c:471: error: `wait' undeclared (first use in this function)


cxload.c:472: error: `timeout' undeclared (first use in this function)


cxload.c: En el nivel principal:


cxload.c:501: error: error de decodificación before '*' token


cxload.c:502: aviso: function declaration isn't a prototype


cxload.c: En la función `write_value':


cxload.c:506: error: `value' undeclared (first use in this function)


cxload.c:510: error: `address' undeclared (first use in this function)


cxload.c:511: error: `adsl_handle' undeclared (first use in this function)


cxload.c: En el nivel principal:


cxload.c:518: error: error de decodificación before '*' token


cxload.c:519: aviso: function declaration isn't a prototype


cxload.c: En la función `send_cmd':


cxload.c:523: error: `id' undeclared (first use in this function)


cxload.c:525: error: `adsl_handle' undeclared (first use in this function)


cxload.c:527: error: `answers' undeclared (first use in this function)


cxload.c: En el nivel principal:


cxload.c:532: error: error de decodificación before '*' token


cxload.c:533: aviso: function declaration isn't a prototype


cxload.c: En la función `send_cmd_wait':


cxload.c:537: error: `id' undeclared (first use in this function)


cxload.c:538: error: `adsl_handle' undeclared (first use in this function)


cxload.c:538: error: `wait' undeclared (first use in this function)


cxload.c:538: error: `answers' undeclared (first use in this function)


cxload.c:538: error: `timeout' undeclared (first use in this function)


cxload.c: En el nivel principal:


cxload.c:542: error: error de decodificación before '*' token


cxload.c:543: aviso: function declaration isn't a prototype


cxload.c: En la función `send_cmd_value':


cxload.c:547: error: `id' undeclared (first use in this function)


cxload.c:547: error: `value' undeclared (first use in this function)


cxload.c:549: error: `adsl_handle' undeclared (first use in this function)


cxload.c:551: error: `answers' undeclared (first use in this function)


cxload.c: En el nivel principal:


cxload.c:556: error: error de decodificación before '*' token


cxload.c:557: aviso: function declaration isn't a prototype


cxload.c: En la función `send_goto_cmd':


cxload.c:561: error: `address' undeclared (first use in this function)


cxload.c:562: error: `adsl_handle' undeclared (first use in this function)


cxload.c: En el nivel principal:


cxload.c:589: error: error de decodificación before '*' token


cxload.c:590: aviso: function declaration isn't a prototype


cxload.c: En la función `send_configuration':


cxload.c:593: error: `last' undeclared (first use in this function)


cxload.c:593: error: `first' undeclared (first use in this function)


cxload.c:623: error: `adsl_handle' undeclared (first use in this function)


cxload.c: En el nivel principal:


cxload.c:630: error: error de decodificación before '*' token


cxload.c:630: aviso: function declaration isn't a prototype


cxload.c: En la función `clear_endpoints':


cxload.c:631: error: `adsl_handle' undeclared (first use in this function)


cxload.c: En el nivel principal:


cxload.c:644: error: error de decodificación before '*' token


cxload.c:645: aviso: function declaration isn't a prototype


cxload.c: En la función `send_block':


cxload.c:646: error: `len' undeclared (first use in this function)


cxload.c:664: error: `bufin' undeclared (first use in this function)


cxload.c:670: error: `place' undeclared (first use in this function)


cxload.c:675: error: `adsl_handle' undeclared (first use in this function)


cxload.c: En el nivel principal:


cxload.c:684: error: error de decodificación before '*' token


cxload.c:685: aviso: function declaration isn't a prototype


cxload.c: En la función `load_firmware':


cxload.c:696: error: `adsl_handle' undeclared (first use in this function)


cxload.c: En la función `init_modem':


cxload.c:910: error: dereferencing pointer to incomplete type


cxload.c:911: error: dereferencing pointer to incomplete type


cxload.c: En la función `main':


cxload.c:1153: error: `usb_dev_handle' undeclared (first use in this function)


cxload.c:1153: error: `adsl_handle' undeclared (first use in this function)


cxload.c:1201: aviso: implicit declaration of function `usb_init'


cxload.c:1202: aviso: implicit declaration of function `usb_find_busses'


cxload.c:1207: aviso: implicit declaration of function `usb_find_devices'


cxload.c:1214: error: `usb_busses' undeclared (first use in this function)


cxload.c:1218: error: dereferencing pointer to incomplete type


cxload.c:1221: error: dereferencing pointer to incomplete type


cxload.c:1221: error: dereferencing pointer to incomplete type


cxload.c:1228: error: dereferencing pointer to incomplete type


cxload.c:1231: error: dereferencing pointer to incomplete type


cxload.c:1238: error: dereferencing pointer to incomplete type


cxload.c:1238: error: dereferencing pointer to incomplete type


cxload.c:1252: aviso: implicit declaration of function `usb_open'


cxload.c:1259: aviso: implicit declaration of function `usb_set_configuration'


cxload.c:1261: aviso: el argumento de formato no es un puntero (argumento 2)


cxload.c:1265: aviso: implicit declaration of function `usb_claim_interface'


cxload.c:1267: aviso: el argumento de formato no es un puntero (argumento 2)


cxload.c:1276: aviso: implicit declaration of function `usb_release_interface'


cxload.c:1278: aviso: implicit declaration of function `usb_close'


make[1]: *** [cxload] Error 1


make[1]: Leaving directory `/home/nico/driver_modem_zyxel/cxacru-630-new/init'


make: *** [CX_INIT] Error 2[/B]

---

### Post by kamstrup on 2005-04-29
Do you have the proper kernel sources installed?

---

### Post by Nico666 on 2005-04-29
Yes, I intall the linux source package from the hoary CD using sinaptyc

---

### Post by [~Ga$h~] on 2005-05-11
:-? I have the same problem. It's a fresh ubuntu install, sources grabed from de install CD. Any ideas?

---

