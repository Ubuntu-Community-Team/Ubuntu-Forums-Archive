---
title: "The fine print"
date: 2008-12-20
forum: Hardware
---

### Post by dawhistler on 2008-12-20
Is there anyone out there who has successfully installed an HP 2200 onto an Ubuntu 8.10 network?

I have HPLP installed but it will not recognize the installed printer because it comes up with NO ip address.

The standard printer installation utility that comes with Ubuntu is equally worthless when it comes to this particular printer.

Any suggestions are of course very welcome.


Mas

---

### Post by Carl Hamlin on 2008-12-20
> **dawhistler said:**
> Is there anyone out there who has successfully installed an HP 2200 onto an Ubuntu 8.10 network?

I have HPLP installed but it will not recognize the installed printer because it comes up with NO ip address.

The standard printer installation utility that comes with Ubuntu is equally worthless when it comes to this particular printer.

Any suggestions are of course very welcome.


Mas

-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

I've also had horrible luck getting printers to run as standalone network devices, but I've never had much of a problem connecting them to an existing server via USB and sharing them as server peripherals.

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklNjAsACgkQyLm4ydrABvdufwCgiXdhdB6RM5VU9E7sN2pVjXHn
EQgAn08txPeUSUGmqo9INCfWNcXb9KmX
=A2Xz
-----END PGP SIGNATURE-----

---

### Post by dawhistler on 2008-12-20
It seems that this is what I must do...however...

I am stubborn.  I am going to try to set it up with Windoze and then plug it into the network.  I know that this goes against using purely Linux but it is just for my own twisted satisfaction of being able to say "HA" at some inanimate system.

Thanks for the reply


Mas

---

### Post by StevenHarper on 2008-12-20
I also can confirm that the HP's seem to have drivers for network use, but I have always failed back to USB.

---

### Post by jerrynewt on 2008-12-20
Try running the printer test page on the printer itself. There should be a printer information page available or network configuration page you can print out. There will be a URL listed on the printout. Open your System>Administration>Printing, choose "other" from the left hand drop down list. In the upper right enter the URL that was on the priner output page. See if your printer is recognized then.

---

### Post by dawhistler on 2008-12-20
The printer test page returns with the message : No information available.   This is the message on every line of the Network Information section.

The user guides both say that HP uses 192.0.0.192 as a fall back but I cannot access this IP either.

I did get HPLIP to see 192.0.0.192...but only once and I still could not modify the printer...

I input the MAC address from this information sheet and STILL - NUTTEN !

Perplexing.


Thanks for the quick replies.


Mas

---

