---
title: "Broadcom Wireless Problem"
date: 2005-03-26
forum: Hardware &amp; Laptops
---

### Post by blu.gecko on 2005-03-26
Ok,

I am completely new to the linux world so, bare with me please.

I bought a Compaq 2210US presario laptop and decided I was over "Billy Gates"
we use SUN SOLARIS at work so I am somewhat familiar, I installed Ubuntu 4:10
from a cd I recieved in the mail. everything installed with 0 issues, completely compatible, except im not sure how to make my wireless take off, I use it at work and other places, so I dont have a wireless router at home. I looked in the device manager and the "BCM94306 802.11g" is listed. So detection is good. I read a thread and they downloaded a secondary app called NDISWRAPPER I downloaded the ubuntu ndiswrapper-source_0.12+1.0rc2-1_i386.deb Im not sure yet how to install this, I tried to double click and well its no EXE file.......

So im not sure if I am on the correct track with this but I need some help

LINUX NEWBIE......blu.gecko 8-[

---

### Post by dcraven on 2005-03-27
Well, I have a similar card (BCM4306) and the Hoary ndiswrapper package didn't work for me. I needed to compile a newer version of ndiswrapper for it to work. Since you are new to Linux this may seem complex, but I'll try to make it simple. It'll require some console work though.

First, go to ndiswrapper.sf.net  do download the latest and greatest version of the wrapper. I extracted mine to /usr/src but you could put it wherever you want. In order to do some of the commands I'll mention you'll need to be root, so "sudo -s" will make that so. I'll assume you extracted the tarball to /usr/src from here on in, and that your version of ndiswrapper is 1.1.

You will also need the kernel headers installed on your system so that ndiswrapper has something to compile against. You can do this with apt-get or synaptic or aptitude. Whatever your pleasure. Make sure they match your running kernel though. For example, the command "uname -r" for me says 2.6.10-5-386, so I installed the package called linux-headers-2.6.10-5-386. It's also a good idea to make sure you have a proper build toolchain and fakeroot install. To do all of this in one fell swoop, I would type:
```

# apt-get install linux-headers-2.6.10-5-386 build-essential fakeroot

```

Next, you need to build and install the module. This is the series of commands needed to do that for me. You may need to tailor them to your kernel. The changes necessary will be relatively obvious, as in just the kernel versions may vary.
```

# cd /usr/src/ndiswrapper-1.1
# make deb
# cd /usr/src
# dpkg -i ndiswrapper-utils_1.1-1_i386.deb
# dpkg -i ndiswrapper-modules-2.6.10-5-386_1.1-1_i386.deb

```
Now you have the freshly compiled module installed. The problem now is that the module was installed in the same place. By default using this method, the module gets installed in /lib/modules/2.6.10-5-386/misc/ndiswrapper.ko which is not the right place. To remedy this I made a symbolic link to the correct location. Here's how. 
```

# cd /lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/
# mv ndiswrapper.ko ndiswrapper.ko.orig       (this just backs up Ubuntu's default module)
# ln -s /lib/modules/2.6.10-5-386/misc/ndiswrapper.ko ./ndiswrapper.ko

```
There you go! Now plug the new module into your running kernel.
```

# modprobe ndiswrapper

```
And with any luck, you should be golden. I hope I didn't leave anything out or make any glaring errors... hehe Now you can just continue on as normal installing your Windows drivers and configuring the network with the Networking tool.

When your kernel gets upgraded, you will probably lose your wireless so keep that /usr/src/ndiswrapper directory around so that some of these steps can be repeated as necessary.

HTH,
~djc

---

### Post by blu.gecko on 2005-03-28
EH uH Oh MAN,

What the heck did I jump into. Since my hardware shows up in the device manager with no issues, is there anyway around the NDISwrapper application?
In windows I have to push my WLAN icon for my wireless to activate.

here is a link to my screenshot for my device manager.

[http://opensource.now.port5.com/4:10//lcd-view.1](http://opensource.now.port5.com/4:10//lcd-view.1)

blu.gecko.........linux, its gonna kick my $%^

---

### Post by dcraven on 2005-03-29
[QUOTE=blu.gecko] is there anyway around the NDISwrapper application?
[/QUOTE]
In terms of Free solutions, no. There is the Linuxant solution that may or may not work with your chipset however. Search the forum and/or wiki for "Linuxant".

[QUOTE=blu.gecko]
here is a link to my screenshot for my device manager.
[/QUOTE]
This really doesn't mean much aside from telling you what wireless chipset you have. It doesn't indicate that anything is configured. You get similar output from "lspci".

Cheers,
~djc

---

### Post by blu.gecko on 2005-03-30
Well then I guess as the next step I need some help installing this ndiswrapper. I downloaded a ".deb" file from the website, I treied dpkg -i and it told me permissiion denied, 

just a little more help

por favor

blu.gecko

---

### Post by unco on 2005-03-30
I'm in the same boat as blu.gecko.

But got ndiswrapper-1.1.tar.gz then extracted. Ran all the commands detailed ... but then final step "modprobe ndiswrapper" returns the following:

"FATAL: Error inserting ndiswrapper (/lib/modules/2.6.8.1-3-386/misc/ndiswrapper.ko): Operation not permitted"

Clearly security, but what.

---

### Post by ekendra on 2005-03-31
[QUOTE=unco]I'm in the same boat as blu.gecko.

But got ndiswrapper-1.1.tar.gz then extracted. Ran all the commands detailed ... but then final step "modprobe ndiswrapper" returns the following:

"FATAL: Error inserting ndiswrapper (/lib/modules/2.6.8.1-3-386/misc/ndiswrapper.ko): Operation not permitted"

Clearly security, but what.[/QUOTE]
 I get the same message as unco above. fatal error inserting ndiswrapper.


What to do?????

THis is a frustrating nightmare!

The wireless card shows up in the device manager. Why can't i use it. I'm this close to returning back to windows if I can't get this up and running?

Honestly, there's no way ubuntu will take off being this complicated to configure.

cheers, ekendra

---

### Post by ekendra on 2005-03-31
???

---

### Post by alehorb on 2005-03-31
Try "sudo" then" modprobe ndiswrapper".
With "dmesg" you can see the errors.
All above in a console.

---

### Post by CarlosJHernandez on 2005-04-01
a lot of the commands you have to issue while installing ndiswrapper need sudo, so either go for **sudo -s** to stay as superuser for the rest of the session or do **sudo <this>  sudo <that>** whenever you seem to not being able to do something because of permissions.

the best source for the ndiswrapper installation is the wiki page for ndiswrapper [http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)  they have detailed some of the problems you guys describe here. 

Finally don't blame linux for not supporting some wifi cards. the hw makers that do not allow the community to write drivers for their cards that have pushed solutions as ndiswrapper = hacking the windows drivers to make them work in linux.

---

### Post by unco on 2005-04-02
Does anyone know what command line behind the action of the GUI Networking dialog's "Activate" button is? 

Thanks to earlier reply, but not sure why I need to do "sudo <anything>" when issuing all commands in the root terminal.  Doesn't matter now, as passed all that.

For all newbies still trying to get it going, I've managed to get my BCM94306 card working with WPA.  Just need to finalise the process.  And then turn into startup at boot.
Was a combination of 3 or 4 different pages.  Will post my instructions here, when I have them nailed down.  I suggest waiting a day or so for my instructions, but these are the references I have used so far:

1. Instructions in second post of this thread.
2. [http://ndiswrapper.sourceforge.net/phpwiki/index.php/Installation](http://ndiswrapper.sourceforge.net/phpwiki/index.php/Installation)
3. [http://ndiswrapper.sourceforge.net/phpwiki/index.php/WPA?PHPSESSID=266d7377e57a4bf34d7c9dac82a36fab](http://ndiswrapper.sourceforge.net/phpwiki/index.php/WPA?PHPSESSID=266d7377e57a4bf34d7c9dac82a36fab)
4. [http://www.ubuntulinux.org/support/documentation/howto/ndiswrapper](http://www.ubuntulinux.org/support/documentation/howto/ndiswrapper)

---

### Post by blu.gecko on 2005-04-02
I am very close to going back to windows, although I hate that thought.

I downloaded 5.0.4 UBUNTU and NDISWRAPPER is actually on that cd, "ISO image".

I tried "ndiswrapper -i bcmwl5.inf" like the program site suggests but I am running into complications. I was trying this under root terminal.

Im struggling here,

Now I was able to fix my touchpad tap problem my going to root terminal and typing "gedit" the going to Xorg.config and installing a tap "0" value that I read from another site. 

So I only have this NDISwrapper and Dialup problem left................



I hope to get this resolved soon so I can learn more about linux.

---

### Post by unco on 2005-04-02
I am still having a problem with setting up to activate wireless network when computer boots so see Problems section at the boot of this post if you can offer suggestions.

I said I would post the process it took to get my wifi card to work.  The steps should be complete for someone who has just install ubuntu, but I haven't detailed every comand line in the area of managing files ...   Also review links in my previous post for info I didn't find relavent but you might, most of this is copied, but reduced.

The installation of the driver is a long process but you only need do it once!  As I said above haven't gotten it to activate at restart.  But the restart steps I need to do are detailed at the very bottom, are minor just annoying.

**START of install instructions**

First, go to [http://ndiswrapper.sf.net](http://ndiswrapper.sf.net)  download the latest version of the wrapper.
Extracted to /usr/src or can put it wherever. 
Open Root Terminal.
(instruction assumed extracted to /usr/src, and version of ndiswrapper is 1.1, change action as appropriate).

Need kernel headers installed on system so that ndiswrapper can compile.
Do this with apt-get or synaptic or aptitude.  Read on for how.
Match running kernel to linux-headers.
The following command returns linux version:
```
uname -r 
```
returns "2.6.8.1-3-386" so install the package called linux-headers-2.6.8.1-3-386...
It's a good idea to make sure the proper build toolchain and fakeroot install.
To do this install by typing:
```
apt-get install linux-headers-2.6.8.1-3-386 build-essential fakeroot
```
Next, build and install the module.
Type these commands to create the module install tailored to the kernel.
```
cd /usr/src/ndiswrapper-1.1
make deb
cd /usr/src
dpkg -i ndiswrapper-utils_1.1-1_i386.deb
dpkg -i ndiswrapper-modules-2.6.8.1-3-386_1.1-1_i386.deb
```
The compiled module is installed.
Now move the module to the correct place.
The module gets installed in /lib/modules/2.6.8.1-3-386/misc/ndiswrapper.ko
which is not the right place.
Correct using the folowing:
```
cd /lib/modules/2.6.8.1-3-386/kernel/drivers/net/ndiswrapper/
mv ndiswrapper.ko ndiswrapper.ko.orig
ln -s /lib/modules/2.6.8.1-3-386/misc/ndiswrapper.ko ./ndiswrapper.ko
```
Now find and install the wireless card driver.
Important: Do NOT use drivers on your CD. They may work, but may not have been tested.

Instead, download appropriate Windows XP driver for your card from the Wiki entry List.
First identify the driver needed, identify the card you have type:
```
lspci
```
Note the first column (such as 0000:01:06.0) and then find the PCI ID of the card, type:
```
lspci -n
```
Identify the line corresponding to the first column from "lspci" output.
The PCI ID is third column (or fourth in some distributions) and of the form "14e4:4320".

Now you need to get the Windows driver for this chipset from the list of drivers, find an
entry for the same PCIID (and compare the chipset as there may be multiple matches on PCIID)
and download the driver corresponding to it, from the following page (Wiki entry List):

[http://ndiswrapper.sourceforge.net/phpwiki/index.php/List?PHPSESSID=e3c29925f1d70dd4664ce4ade02f03e9](http://ndiswrapper.sourceforge.net/phpwiki/index.php/List?PHPSESSID=e3c29925f1d70dd4664ce4ade02f03e9) 

Extract the Windows driver and find the INF file (i.e., file with .INF or .inf extension)
and SYS file (i.e., file with .SYS or .sys extension).
If multiple INF/SYS files, you may look in the List if there are any hints about which to use.

Make sure the INF file, SYS file and any BIN files are all in one directory.
Now use "ndiswrapper" tool to install the driver using the inf file:
```
ndiswrapper -i bcmwl5.inf
```
This copies necessary files to /etc/ndiswrapper and creates the config files for your card.
After installing you can run:
```
ndiswrapper -l
```
To see the status, should be:

 -> Installed ndis drivers
 -> bcmwl5 driver present, hardware present 

Where "present" means that you have a card that can be used with the driver installed.
In this case, broadcom driver bcmwl5 is used.

Now plug the new module into the running kernel using:
```
modprobe ndiswrapper
```
If you done't get an error the driver should now be loaded.
You can verify by checking system log, produced by typing: 
```
dmesg
```
If the driver is loaded successfully, you should see a message in the system log like:

 -> ndiswrapper version 1.1 loaded

Should then see the following message in system log for each of the drivers:

 -> ndiswrapper: driver bcmwl5 added

If you don't see these messages, it usually means that there are no (usable) drivers
installed in /etc/ndiswrapper directory.
Check if the /etc/ndiswrapper directory has one sub-directory for each driver and if
in each driver's directory there are inf, sys and conf files.
Otherwise, you may need to repeat finding and installing the drive from Wiki entry List.

If this does not bring up the lights on the card, try ejecting it and re-inserting it.
(I skipped checking for lights)

If the system has a card that works with one of the loaded drivers, you should see the
following message in the system log:

  -> wlan0: ndiswrapper ethernet device 0A:00:29:20:0E.12

Use iwconfig to configure wireless network interface. First, see if the interface is available:
```
iwconfig
```
Should list device wlan0 details (or similar for wifi card).

Next scan for access points:
```
iwlist wlan0 scan
```
Should show list of cell (assess points) details.

If the AP is in scan above, set the operating mode of the interface according to your setup.
In most cases, it is Managed:
```
iwconfig wlan0 mode Managed
```
Set the network name:
```
iwconfig wlan0 essid ESSID
```
**WEP Authentication Section**

If you use encryption (WEP), set the key:
```
iwconfig wlan0 key restricted XXXXXXXX
```
**WPA Authentication Section**

If you use encryption (WPA), do the following:

Get latest version of wpa_supplicant from: 

[http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/) 

Extract to a new wpa_supplicant directory.
Add .config file so it contains driver support for ndiswrapper and a control interface.
i.e., add the following lines to .config file, may need to create new file:
```
CONFIG_DRIVER_NDISWRAPPER=y
CONFIG_CTRL_IFACE=y
```
Now compile wpa_supplicant stuff:
```
cd /<wherever>/wpa_supplicant
make
```
Copy wpa_supplicant, wpa_passphrase and wpa_cli to some place that is in your $PATH, e.g., /usr/local/bin
```
cp /<wherever>/wpa_supplicant/wpa_supplicant /usr/local/bin/
cp /<wherever>/wpa_supplicant/wpa_passphrase /usr/local/bin/
cp /<wherever>/wpa_supplicant/wpa_cli /usr/local/bin/
```
Create a wpa_supplicant configuration file, e.g. /etc/wpa_supplicant.conf which contains:
```
ctrl_interface=/var/run/wpa_supplicant # for wpa_cli support

network={
  ssid="myssid"
  psk="mykey"
  key_mgmt=WPA-PSK
  proto=WPA
}
```
Note that psk given above can be plain text (ASCII) pass phrase that is used on the AP,
or 64 hex digits that can be generated with wpa_passphrase from the same ASCII pass phrase.
For simplicity, go with ASCII pass phrase for now.

Now simultaneously start up the interface and wpa_supplicant. For example, as
```
ifconfig wlan0 up
wpa_supplicant -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf -dd
```
The option "-dd" to wpa_supplicant gives lot of output so you can see if there is a problem.
If everything works, you can drop "-dd" option.
You may also want to leave wpa_supplicant running in the background with the option "-Bw" so you don't need to start it everytime.

Once wpa_supplicant authenticates, you can use DHCP to configure the network interface.

**END OF WPA Authentication**


Now wlan0 should be configured as a device that can be used to setup a network.
Do this in the GUI "Computer/System Configuration/Networking" option from the ubuntu menu.
On connection tab, Add, then Foward thru wizard page setting:

  Type as Wireless
  Wireless device as wlan0 (or your equivalent)
  ESSID as your AP essid
  WEP (or WPA key not sure if need yet)
  Set network configuration type, e.g. DHCP
  Apply and activate.

Note: I had trouble if I disabled the ESSID from being boardcast, so make sure it
is shown when you do a "iwlist wlan0 scan".

At this point your wireless card should work ... you should be able to go online ...

BUT this doesn't mean that the device is setup to be configured when booting or restarting.
Which is where I am having trouble finishing of the process.
The references I used stated the following, but they don't seem to do anything for me.

  Once everything works fine write the correct modprobe settings
  to load ndiswrapper automatically when wlan0 interface is used,
  by running:
```
ndiswrapper -m
```
  This doesn't automatically load ndiswrapper module at boot time.
  For the module to be loaded automatically at boot time, you should
  configure your module setup, which depends on the distrbution.
  Most distributions will load all modules listed in /etc/modules
  at boot time. Mandrake 10.x uses /etc/modprobe.preload. 
  Add the line in /etc/modules:
```
ndiswrapper
```

**PROBLEMS being experienced.**

1. If in the GUI Networking wlan0 connection is set to "Activate when Computer Starts".
   Then it slows down the boot process at the network stage.
2. Not sure what "ndiswrapper -m" or putting ndiswrapper in the /etc/modules file is
   meant to do but don't seem to do anything.
   Wireless is not activated when restarting and have to manually run script to load 
   ndiswrapper, and activate wireless connection in GUI.

**STEPS I am currently taking to start wireless each time I boot system.**

1. Once in gnome, open Root Terminal and execute the following:
```
modprobe ndiswrapper
iwconfig wlan0 essid Myssid
iwconfig wlan0 mode Managed
ifconfig wlan0 up
wpa_supplicant -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf -Bw
```
2. Manually activate the networking connection in the networking GUI.

---

### Post by bigscotty20 on 2006-10-27
:confused::confused::confused:
Dcraven

> Next, you need to build and install the module. This is the series of commands needed to do that for me. You may need to tailor them to your kernel. The changes necessary will be relatively obvious, as in just the kernel versions may vary.
 	Code:
 	[LEFT]# cd /usr/src/ndiswrapper-1.1
# make deb
# cd /usr/src
# dpkg -i ndiswrapper-utils_1.1-1_i386.deb
# dpkg -i ndiswrapper-modules-2.6.10-5-386_1.1-1_i386.deb[/LEFT]
 


It works great for me until # make deb. then i get this message:

```
make: *** No rule to make target `deb'.  Stop.
```

I have Ubuntu 6.10 for ppc.

---

### Post by draeath on 2006-10-28
It's not the fault of Ubuntu, rather its a combination of the fault of the hardware manufacterer and the FCC of the USA.

Basically, the manufacturers don't want to release hardware specs so we can design drivers to work with the cards. "Trade Secrets" and all that.

Also, some cards, notably the Broadcom cards, are full-fleged radio transmitters with software controllers. If the manufacturer decided to release the specs so we could use them, the FCC would tear their head off. For a couple of reasons: the broadcoms can transmit/recieve on frequencies that require a licence, and they can also do the same on restricted frequencies (for instance, USA police radios and USA military transmissions).


It's a really sucky situation. Personally, I bought a Netgear WG511T (The 108mbps pcimcia card) with the atheros chipset. Ubuntu supports it out of the box (with the madwifi driver, if you are curious)

---

