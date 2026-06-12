---
title: "HP Photosmart B110 printer"
date: 2010-12-07
forum: Hardware
---

### Post by matogrosso on 2010-12-07
Those of you trying to use a HP Photosmart B110 printer on Ubuntu 10.04 please see the bug report below

-------------------------------------------------
[https://bugs.launchpad.net/bugs/685583](https://bugs.launchpad.net/bugs/685583)

[https://bugs.launchpad.net/bugs/685583]("https://bugs.launchpad.net/bugs/685583")

Naga,

Thank you so much for your reply.

I used the latest HPLIP version from

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

It did recognise the printer (on wireless mode, USB disconnected) as it found the right HP printer name and displayed "HP Photosmart B110" so I suppose it had connectivity to the printer. But I did not try to ping it. The printer was previously set up to wireless mode using windows 7. Works fine on windows 7 in wireless mode.

On Ubuntu (on wireless mode, USB disconnected) it finds the printer and sends the job to the printer but sits there hanging forever and does not throw an error message.

After that I plugged in the USB cable, reinstalled the latest HPLIP and then the printer worked on Ubuntu. But it is not wireless. I did not use hp-wificonfig and hp-setup utility you mentioned. Are they available on Ubuntu repositories ?

Another smaller problem I have is that HPLIP from the site above does not come with the HPLIP-GUI. If I try to install the HP-GUI from ubuntu (using apt-get or Synaptic) it installs an older version of HPLIP which does not support the printer (HP Photosmart B110). Is there any workaround for this ? Please do you have a date for when the latest HPLIP (with support for HP Photosmart B110) will be available from the Ubuntu 10.04 repositories ? I can live with a wired printer for now and wait for an update that will make it plug and play (and HP GUI) on Ubuntu 10.04.

Kind Regards,


> Date: Tue, 7 Dec 2010 10:29:44 +0000
> From: [email]samrat.hplip@gmail.com[/email]
> To: [email]matogrosso@hotmail.com[/email]
> Subject: [Bug 685583] Re: HP Photosmart B110 does not work on Ubuntu 10.04
>
> I hope you are configured the printer using both hp-wificonfig and hp-setup utility, and followed the instructions while configuring.
> Did you be able to ping the printer's IP address from your Linux Box?
>
> Thanks,
> Naga Samrat Chowdary, Narla
>
> --
> You received this bug notification because you are a direct subscriber
> of the bug.
> [https://bugs.launchpad.net/bugs/685583](https://bugs.launchpad.net/bugs/685583)
>
> Title:
> HP Photosmart B110 does not work on Ubuntu 10.04

---

### Post by demidam on 2010-12-27
Today I installed B110 wireless with the latest hplip version (hplip-3.10.9) on Ubuntu 10.04. Did the setup as follows:

After installing hplip open up device manager and go to new or add via + then mark at connection type:
Network/Ethernet/Wireless network...........................................

Then go to advanced options and choose Manual discovery. Then make sure you know the IP address of the printer(go to settings, wireless and you will see the IP). With IP Address or network name enter your printer's IP. Leave Jetdirect port unharmed at nr 1.
Then enter Next. Your printer should show up enter Next and try it out. For me everything worked perfectly also scanning wireless no problem.

I hope I could be of any help for you and everyone who needs to configure their B110

For those who cannot install hplip on ubuntu 10.10 copy this in terminal and then try to install hplip again:

sudo aptitude install --assume-yes libcups2 cups libcups2-dev cups-bsd  cups-client libcupsimage2-dev libdbus-1-dev build-essential ghostscript  openssl libjpeg62-dev libsnmp-dev libtool libusb-dev python-imaging  policykit-1 policykit-1-gnome python-qt4 python-qt4-dbus python-dbus  python-gobject python-dev python-notify python python-reportlab libsane  libsane-dev sane-utils xsane

Cheers,

demidam

---

### Post by obieito on 2011-01-08
I have just setup one of these B110 printers, with stock 10.10 hplip (3.10.6-1), and after configuring the printer's wifi network,  it was automagically detected by the system as a network printer.

All the best!

---

### Post by ecosprog on 2011-01-11
Same here. Installation was quick and easy and all my computers see the printer and print as expected.

---

### Post by Tom Mann on 2011-01-14
Here's what you need to do:

- Make sure you're connected to the network the printer is on.
- Open Firefox and navigate to [http://localhost:631](http://localhost:631) and click the Administration link. 
- Click "Add Printer" and log in with a user with sudo rights (eg the first user set up on the system)
- CUPS will detect and find your printer, which will show up several times under the Discovered Network Printers section. Click the first one that shows up, then the Continue button.
- Change the name and description to how you want it to look (I left it on the default) and hit Continue.
- On the driver page make sure "HP Photosmart b110 Seies hpijs, 3.10.6 (en) is selected and hit add printer.
- Change printing defaults if necessary and complete the setup.

Then you can manage it from System > Administration > Printing to set as default/change settings.

---

### Post by krisgesling on 2011-05-15
It worked fine for me, wifi and all, once I manually searched by the printers IP. It does slow down my system quite a lot every time it's processing a print job but at least it works.

Thanks to anyone that's worked on the package.

---

