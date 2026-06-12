---
title: "howto setup/install skystar2 in ubuntu? wiki is in german."
date: 2005-08-28
forum: Hardware &amp; Laptops
---

### Post by c-m on 2005-08-28
i have a skystar2 v2.3 pci satellite card. Unfortunatly i do not know how to go about installing and setting this up.

an "lspci" gives the following (concerning the card):

> 
0000:01:08.0 Network controller: Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card (rev 01)


a "lsmod2 gives:
> 
skystar2               30468  0
dvb_core               82920  1 skystar2
mt352                   5700  1 skystar2
stv0299                10244  1 skystar2
mt312                   8324  1 skystar2
i2c_core               22416  8 skystar2,mt352,stv0299,mt312,tuner,cx88xx,i2c_algo_bit,i2c_nforce2


The card is detected then i take it. I just need to
i know how to install it correctly and then set it up.

I have found this in the WIKI [http://www.ubuntuusers.de/wiki/treiber:tv:skystar2_installation](http://www.ubuntuusers.de/wiki/treiber:tv:skystar2_installation)

But its in German and despite having an austrian gf for some years i haven't learned much.

From a search i know a couple of you on these forums have this card up and running so i'd appreciate you input. 

thank you.

---

### Post by c-m on 2005-08-29
[QUOTE=c-m]i have a skystar2 v2.3 pci satellite card. Unfortunatly i do not know how to go about installing and setting this up.

an "lspci" gives the following (concerning the card):



a "lsmod2 gives:


The card is detected then i take it. I just need to
i know how to install it correctly and then set it up.

I have found this in the WIKI [http://www.ubuntuusers.de/wiki/treiber:tv:skystar2_installation](http://www.ubuntuusers.de/wiki/treiber:tv:skystar2_installation)

But its in German and despite having an austrian gf for some years i haven't learned much.

From a search i know a couple of you on these forums have this card up and running so i'd appreciate you input. 

thank you.[/QUOTE]
 bah! why is setting up hardware so difficult. software is fine. all the infomation i can find to do with correctly installing a skystar2 in linux and setting it up, is in German.

---

### Post by Thraxes on 2005-09-21
Just so happens I am installing this card right now, alot of the page you linked to is scripts and commands and not that much stuff to translate... lucky for you I'm bilingual ;)

Installing Skystar2 and Xine on Ubuntu kernel 2.6.8

Load the Modules
> modprobe budget
modprobe stv0299

So the modules load at boot-time they have to be added to **/etc/modules**.

Create the following script in **/etc/init.d** and name it **dvb**
use vi, emacs or nano or whatever editor you prefer

*nano /etc/init.d/dvb*
> #!/bin/bash
#/etc/init.d/dvb
# get rid of old DVB API devices; do it twice for good measure...
   
rm -rf /dev/ost
rm -rf /dev/ost
rm -rf /dev/dvb
rm -rf /dev/dvb
 
#for major and minor devicenumber see here
#vi /usr/src/linux/Documentation/devices.txt
 
cd /dev
mkdir dvb
chmod 755 /dev/dvb
cd dvb
mkdir adapter0
cd adapter0
mknod -m 0660 frontend0 c 212 3
mknod -m 0660 demux0 c 212 4
mknod -m 0660 dvr0 c 212 5
mknod -m 0660 ca0 c 212 6
chown root.video /dev/dvb/adapter0/*''
chmod 744 /etc/init.d/dvb

Now add this to the runlevels

> update-rc.d dvb defaults

Thraxes Comments: This takes care of the driver installation. The modules needed are preinstalled by default, all this just did was activate them and set up the devices in /dev. If you have perhaps streamlined your Kernel and thrown out exess baggage like Video for Linux you will need to recompile with the correct modules. These are in the DVB for Linux section of menuconfig and for the Skystar involve B2C2, budget cards and the stv0299 frontend - all as modules.

**Installing Xine and dvb-utils**

> sudo apt-get install xine-ui dvb-utils

First thing to do is make a programme table that XINE can use. This will be called channels.conf and should normally be created in **~/.xine/**. Included in DVB-Utils is a tool called scan that will create this file for you. IIRC scan works like this but better check the help before you try! UPDATE: I checked and this is actually how to do it: You need the initialization data so scan knows which frequencies to scan. This initialization data can be downloaded at linuxtv.org. They are included in the dvb apps and have listings for DVB-C, DVB-S and DVB-T. No need to compile the proggies as we have already installed them with apt-get but these initialization files are very important to make a channels.conf. Execute this command in the directory with the initialization files (I put them in /usr/bin/dvb)

> scan -o zap path/to/initialization > /path/to/channels.conf

This should usually be in your home directory.
Now let's start up Xine! [ALT]+[F2]

> xine dvb://

Channels can be changed on the Numpad. If xine doesn't work, you can try to manually tune the dvb card with szap (also included in dvb-utils)

> zcat /usr/share/doc/dvb-utils/examples/channels.conf-dvbs-astra.gz > channel
szap -c channel -n 1 -r

You should now see some output scroll by, if you can see FE_HAS_LOCK then all is well and the card is tuned to a TV-programme.

Now open a second terminal and call up xine and tell it to use the cards current output that we enabled with szap.

> xine stdin:// < /dev/dvb/adapter0/dvr0

Hope this helps. I'm actually working on not watching the DVB card locally but streaming the DVB Stream with VLC over a network so I can't really say anything about xine and it's problems. I can confirm however that the hardware installation described here works - at least for me it did.

---

### Post by tacom6 on 2005-10-11
Any of you installed this card as a DVB modem for one-way satellite internet? I will try to accomplish such a task soon, I will start from here. Thanks for the translation! :p

---

