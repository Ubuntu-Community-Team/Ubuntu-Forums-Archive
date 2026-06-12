---
title: "Another laptop/wirelesscard problem..."
date: 2006-02-14
forum: Hardware &amp; Laptops
---

### Post by UbuntuLinuxUser on 2006-02-14
Alright, I'm a week old noobie with a Toshiba Satellite A65-S1067 with a 2.8Ghz P4 w/ HT, 768MB of ram, 40Gig hdd, and a Linksys WPC54GS wireless card and a WRT54GS router. Friend #1(Fedora User) and I went thru the installation setup at least twice, but didn't have any luck. Friend #2(Debian?) and I went thru this at least two more times and still no luck. The "on" light is on the card is working, but Ubuntu doesn't seem to be reconizing it, no wlan0 device in the connectivity window and tried installing serveral wireless drivers, but didn't work. Keep in mind  that I'm still learning all the codes and stuff, but yea.....thanks in advance.

---

### Post by jml on 2006-02-14
I've had the same problem with that card myself.  It seems that the Linksys card uses a wireless chip set that is not recognized by Ubuntu, or any other distro, (I know, I've tried at least six).  I would recommend selling that card to someone who is still using Windows, (Linksys equipment is very Windows Friendly  :-? )  If your budget permits, try to get a NetGear WG511T  wireless PC Card.  It uses the Ahteros Chip Set and is recognized by Ubuntu 5.10 out of the box.  The only thing that is not automatically supported is WPA encryption.  That requires something called WPA_Supplicant.  There are several posts on these forums discussing that topic.  Hope this helps.

Joe

---

### Post by crd on 2006-02-19
Did you try the ndiswrapper approach to setting it up?  There has been some reported success (other distro) using ndiswrapper:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

It might be able to put your Windows driver files for that Linksys card to use in Ubuntu.  I ended up using ndiswrapper for my Broadcom wireless.

crd

---

### Post by UbuntuLinuxUser on 2006-02-19
[QUOTE=crd]Did you try the ndiswrapper approach to setting it up?  There has been some reported success (other distro) using ndiswrapper:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

It might be able to put your Windows driver files for that Linksys card to use in Ubuntu.  I ended up using ndiswrapper for my Broadcom wireless.

crd[/QUOTE]

I tried it, but it didn't work....how did you do it?

---

### Post by crd on 2006-02-19
Well, I don't have that specific card, but more or less that is not significant when configuring the ndiswrapper.  It sounds like you have it installed already, so from there:

First, make sure you can locate the Windows version of this driver.  If it came on the laptop, it should be available from somewhere (Windows partition, Included driver CD, etc..).  Make a copy of the folder that has the driver, which will be a ".inf" file along with a ".sys" file or maybe some others to your linux partition to an area you can get to easily.

Open up a terminal, type and type *ndiswrapper -l* to see if any devices are currently using it.  Unless you left it configured, nothing should be listed.  To  set it up, change directory to the location of your Linksys drivers and type *ndiswrapper -i DriverName.inf*.  It will give a status of that, and you can do another *ndiswrapper -l* to verify that it found the hardware and driver okay.  If it didn't then you might have to see if you can find another driver for the same hardware.  With mine, the WinXP and Win98 drivers act a bit differently.

Now, type *ndiswrapper -m* to verify that the module gets loaded.  Then with a bit of luck, you can go to System -> Administration -> Networking and check out if your card is showing up.  You might have to play around with the *iwconfig* command in the terminal as well to get it set up to work with your network.  

Maybe you already tried all this, though.

crd

---

