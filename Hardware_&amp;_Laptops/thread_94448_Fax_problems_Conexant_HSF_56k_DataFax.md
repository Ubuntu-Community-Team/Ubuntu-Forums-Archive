---
title: "Fax problems Conexant HSF 56k Data/Fax"
date: 2005-11-24
forum: Hardware &amp; Laptops
---

### Post by PeaceMessenger on 2005-11-24
I need to be able to send and receive faxes using Breezy 5.10 with KDE installed.  I'm a noob.

lspci gives me this for my internal modem.
> 
0000:02:08.0 Communication controller: Conexant HSF 56k Data/Fax/Voice/Spkp Modem (rev 01)


When I run KDEprintfax and try to send a fax I get this error
> 
Converting input files to PostScript
Sending fax to 02087320495 ()
Sending to fax using: /usr/bin/fax NAME="'Ryan Peace'" DEV='modem' PAGE='a4' FROM='86-28-85192217' send  '02087320495' '/home/ryan/FederalExpress.ps' 
/etc/efax.rc: line 63: paperconf: command not found
/etc/efax.rc: line 63: paperconf: command not found
Error: PAGE="" not valid.
can't read file /home/ryan/FederalExpress.ps.001

When I run efax-gtk I get this error
> 
***********************
Beginning fax log at 1512 CST 24 Nov 2005

efax-0.9a: 12:51 Error: can't open pre-lock file /var/lock/LCK../dev/TMP..09803: No such file or directory
efax-0.9a: 12:51 failed -> /home/ryan/FederalExpress.ps.001
efax-0.9a: 12:51 failed -> /home/ryan/FederalExpress.ps.002
efax-0.9a: 12:51 done, returning 2 (unrecoverable error)


What else do I need to install to make faxing work?  My modem works fine in Windows for faxing.  

Thanks,

---

### Post by jml75 on 2006-02-19
Simple!

You need to install the "libpaper-utils" package.

Either use synaptic and search for it to install it.

Or,

Go to a terminal and run the following :

sudo apt-get install libpaper-utils

Et voilà!

Should work.

If not report it back so we can try an other solution.

---

### Post by jml75 on 2006-02-19
Oh one more thing...

Did you install the proper drivers for your HSF modem?

If not, you'll need to do it and since you have a conexant modem, there is light!

At [www.linuxant.com](www.linuxant.com), you can get for 10 or 15 $ a linux driver for your modem and they have a prebuild package for every ubuntu 5.10 kernels.

Works great for me except I have a conexant HCF modem. But I know for sure they have the drivers for both HCF and HSF modems.

Have a nice day!

---

### Post by SuperMau on 2006-10-25
Unfortunately the free version does not support fax capability:

# Free version (limited to 14.4Kbps data):( 
# Full version (with 56K and FAX), for the same price you can get a compatible modem since you get only one year support and after that it won't work with new kernels :mad:

---

