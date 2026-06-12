---
title: "instalar modem 3g claro ZTE MF626"
date: 2009-08-04
forum: Hardware
---

### Post by jordan090 on 2009-08-04
HOLA soi principiante y nesesito ayuda para configurar mi modem 3g de claro ya que es mi unico internet porfavor es urgente ayuda vi un tutorial para acerlo pero noo pudehace MAKE INSTALL por k no lo supe hacer ayuda porfavor uso ubuntu 9.04

---

### Post by gmunioz on 2009-08-04
Hola jor...:

Ve a este sitio:

[http://packages.debian.org/squeeze/usb-modeswitch](http://packages.debian.org/squeeze/usb-modeswitch)

Pulsa para obtener el archivo usb-modeswitch_1.0.2-1_xxx.deb 

Correspondiente a la version instalada amd64 ó i386

elige el servidor que mas te agrade

Una vez descargado, navega con nautilus hasta encontrarlo

pulsa sobre él y elige instalarlo con gdebi

puesta la contraseña y terminada la instalación, continua con:

Editar el archivo usb_modeswitch.conf

pulsa aplicaciones - accesorios - terminal y en la consola

ejecuta el siguiente comando:

sudo gedit /etc/usb_modeswitch.conf

Se abrirá el archivo, busca dentro del archivo el item MF626

Borra las almoahdillas [#] y los punto y coma [;] dejando el 

contenido parecido al siguiente:


```
########################################################

ZTE MF628+ (tested version from Telia / Sweden)

ZTE MF626

Contributor: Joakim Wennergren

DefaultVendor= 0×19d2

DefaultProduct= 0×2000

TargetVendor= 0×19d2

TargetProduct= 0×0031

MessageEndpoint=0×01

MessageContent=”55534243123456782000000080000c85010101180101010101000000000000&#8243;

if that command doesn’t work, try the other (”eject”)

MessageContent=”5553424312345678000000000000061b000000030000000000000000000000&#8243;



```

Guarda el archivo.

Cierra gedit.

Conecta el modem al puerto usb

Ejecuta en la consola la orden

sudo lsusb

Si el comando entro otras cosas te informa

acerca del ID 19d2:2000 

El modem esta reconocido, ahora hay que activarlo.

Ejecuta a continuación en la consola la orden

sudo /usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch.conf

y la orden

sudo /sbin/modprobe usbserial vendor=0×19d2 product=0×0031

A continuación para crear un archivo .fdi ejecutas en

la consola la orden

sudo gedit /usr/share/hal/fdi/information/20thirdparty/20-zte-mf626.fdi

Se abrirá un archivo en blanco, pega este contenido:

```
<!– -*- SGML -*- –>
<deviceinfo version=”0.2&#8243;>
<device>
<!– ZTE MF626 HSDPA USB Modem –>
<match key=”@info.parent:usb.vendor_id” int=”0×19d2&#8243;>
<match key=”@info.parent:usb.product_id” int=”0×0031&#8243;>
<match key=”@info.parent:usb.interface.number” int=”3&#8243;>
<append key=”modem.command_sets” type=”strlist”>GSM-07.07</append>
<append key=”modem.command_sets” type=”strlist”>GSM-07.05</append>
<append key=”info.capabilities” type=”strlist”>modem</append>
</match>
</match>
</match>
</device>
</deviceinfo>
```

Guarda el archivo

Cierra gedit.

Ya tendría que estar funcionando el modem, asi que cierra

la consola y 

Pulsa Sistema - Preferencias - Conexiones de red

- Pestaña Banda ancha movil

Y edita una conexión claro, con las parámetros de

tu conexión

El número de telefono es +99#

El nombre de usuario es ctigprs

La contraseña es 3616

---

### Post by chepe263 on 2009-08-09
Cuando vi esto senti como alivio porque pense que ya estaba hecho pero no. Yo encontre un programa llamado Wader [[http://trac.warp.es/wader]](http://trac.warp.es/wader]) Y siento que sale un poco mas facil de instalar. Lo unico que me di cuenta es que ubuntu como que no lo reconoce. Yo uso el 9.04 y si me urge porque solo ubuntu uso y windows es como para "emergencia". Por cierto, no he usado wader aun.

En fin, para claro Guatemala el apn seria ba.amx , no usa password ni usuario.

Si te funciona me avisas para que me ayudes jeje

---

