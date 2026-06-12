---
title: "X crashes several times a day"
date: 2005-06-29
forum: Hardware &amp; Laptops
---

### Post by guadafan on 2005-06-29
I don't know why this happens, X crashes several times a day, here is my logs:

------------------------------------------------------------------------
------------------------------------------------------------------------

USER.LOG

Jun 29 14:01:27 localhost gconfd (root-13054): Se resolvió la dirección «xml:readonly:/etc/gconf/gconf.xml.defaults» a una fuente de configuración de sólo lectura en la posición 2
Jun 29 18:42:53 localhost gconfd (gea-8467): Se ha recibido la señal 15, finalizando limpiamente
Jun 29 18:42:53 localhost gconfd (gea-8467): Finalizando

SYSLOG

Jun 29 18:31:43 localhost -- MARK --
Jun 29 18:42:53 localhost udev[19806]: removing device node '/dev/vcs7'
Jun 29 18:42:53 localhost udev[19808]: removing device node '/dev/vcsa7'
Jun 29 18:42:53 localhost gconfd (gea-8467): Se ha recibido la señal 15, finalizando limpiamente
Jun 29 18:42:53 localhost gconfd (gea-8467): Finalizando
Jun 29 18:42:54 localhost gdm[7022]: gdm_slave_xioerror_handler: ha ocurrido un error fatal de X - Reiniciando :0
Jun 29 18:42:55 localhost udev[19825]: creating device node '/dev/vcs7'
Jun 29 18:42:55 localhost udev[19827]: creating device node '/dev/vcsa7'
Jun 29 18:42:55 localhost udev[19844]: removing device node '/dev/vcs7'
Jun 29 18:42:55 localhost udev[19850]: removing device node '/dev/vcsa7'
Jun 29 18:42:55 localhost udev[19862]: creating device node '/dev/vcs7'
Jun 29 18:42:55 localhost udev[19864]: creating device node '/dev/vcsa7'
Jun 29 18:42:56 localhost kernel: mtrr: base(0xf0020000) is not aligned on a size(0x640000) boundary

MESSAGES

Jun 29 18:42:53 localhost gconfd (gea-8467): Se ha recibido la señal 15, finalizando limpiamente
Jun 29 18:42:53 localhost gconfd (gea-8467): Finalizando
Jun 29 18:42:56 localhost kernel: mtrr: base(0xf0020000) is not aligned on a size(0x640000) boundary

KERN.LOG

Jun 29 11:13:57 localhost kernel: eth2: no IPv6 routers present
Jun 29 18:42:56 localhost kernel: mtrr: base(0xf0020000) is not aligned on a size(0x640000) boundary

DAEMON.LOG

Jun 29 11:11:57 localhost udev[8324]: creating device node '/dev/vcs2'
Jun 29 11:11:57 localhost udev[8326]: creating device node '/dev/vcs3'
Jun 29 11:11:57 localhost udev[8330]: creating device node '/dev/vcs5'
Jun 29 11:11:57 localhost udev[8332]: creating device node '/dev/vcs6'
Jun 29 11:11:57 localhost udev[8334]: creating device node '/dev/vcsa2'
Jun 29 11:11:57 localhost udev[8336]: creating device node '/dev/vcsa3'
Jun 29 11:11:57 localhost udev[8342]: creating device node '/dev/vcsa6'
Jun 29 11:11:57 localhost udev[8328]: creating device node '/dev/vcs4'
Jun 29 11:11:57 localhost udev[8338]: creating device node '/dev/vcsa4'
Jun 29 11:11:57 localhost udev[8340]: creating device node '/dev/vcsa5'
Jun 29 11:13:47 localhost pppoe[8807]: PADS: Service-Name: ''
Jun 29 11:13:47 localhost pppoe[8807]: PPP session is 29654
Jun 29 11:13:51 localhost pppoe[8807]: Received signal 1 on session 29654.
Jun 29 11:13:51 localhost pppoe[8807]: Sent PADT
Jun 29 11:13:52 localhost pppoe[8911]: PADS: Service-Name: ''
Jun 29 11:13:52 localhost pppoe[8911]: PPP session is 29663
Jun 29 18:42:53 localhost udev[19806]: removing device node '/dev/vcs7'
Jun 29 18:42:53 localhost udev[19808]: removing device node '/dev/vcsa7'
Jun 29 18:42:54 localhost gdm[7022]: gdm_slave_xioerror_handler: ha ocurrido un error fatal de X - Reiniciando :0
Jun 29 18:42:55 localhost udev[19825]: creating device node '/dev/vcs7'
Jun 29 18:42:55 localhost udev[19827]: creating device node '/dev/vcsa7'
Jun 29 18:42:55 localhost udev[19844]: removing device node '/dev/vcs7'
Jun 29 18:42:55 localhost udev[19850]: removing device node '/dev/vcsa7'
Jun 29 18:42:55 localhost udev[19862]: creating device node '/dev/vcs7'
Jun 29 18:42:55 localhost udev[19864]: creating device node '/dev/vcsa7'

XORG.LOG.OLD


   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Fatal server error:
Caught signal 4.  Server aborting


Please consult the The X.Org Foundation support
         at [http://wiki.X.Org](http://wiki.X.Org)
 for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

---------------------------------------------------------
---------------------------------------------------------


And my hardware:

Centrino 1.6 Ghz
512 RAM
Video Card: intel 85GM

I have tried with several X drivers like i810, vesa, fbdev... and the same problems continue. :|  :roll:

---

