---
title: "How to make Intel 82566MM work in Dapper?"
date: 2007-09-01
forum: Hardware &amp; Laptops
---

### Post by sailing511 on 2007-09-01
Hi all,

I am a new-bie of Ubuntu. A few days ago, I bought a T61 with the Intel 82566MM network adapter, but it seems that in Dapper, this device cannot be found. As in System-Administration-Networking, both the wired and wireless network adapter are not in the list.

I google in ThinkPad wiki, and found that a module called e1000 should have supported the network adapter. I did the following:
  sudo modprobe e1000
and then lsmod | grep e1000, the module exists.

However, the wired network adapter still cannot be found.

So any ideas how to make it work?

BTW, without connection to the internet, I cannot download code and compile...

Thank you all.

---

### Post by moore.bryan on 2007-09-01
*i think your adapter runs an atheros chip, meaning you should probably use madwifi.  just to be sure, what are the outputs of ```
lspci
``` and ```
iwconfig
```?*

---

### Post by sailing511 on 2007-09-01
lspci:

0000:00:00.0 Host bridge: Intel Corporation: Unknown device 2a00 (rev 0c)
0000:00:02.0 VGA compatible controller: Intel Corporation: Unknown device 2a02 (rev 0c)
0000:00:02.1 Display controller: Intel Corporation: Unknown device 2a03 (rev 0c)
0000:00:19.0 Ethernet controller: Intel Corporation: Unknown device 1049 (rev 03)
0000:00:1a.0 USB Controller: Intel Corporation: Unknown device 2834 (rev 03)
0000:00:1a.1 USB Controller: Intel Corporation: Unknown device 2835 (rev 03)
0000:00:1a.7 USB Controller: Intel Corporation: Unknown device 283a (rev 03)
0000:00:1b.0 0403: Intel Corporation: Unknown device 284b (rev 03)
0000:00:1c.0 PCI bridge: Intel Corporation: Unknown device 283f (rev 03)
0000:00:1c.1 PCI bridge: Intel Corporation: Unknown device 2841 (rev 03)
0000:00:1c.2 PCI bridge: Intel Corporation: Unknown device 2843 (rev 03)
0000:00:1c.3 PCI bridge: Intel Corporation: Unknown device 2845 (rev 03)
0000:00:1c.4 PCI bridge: Intel Corporation: Unknown device 2847 (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation: Unknown device 2830 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation: Unknown device 2831 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation: Unknown device 2832 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation: Unknown device 2836 (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
0000:00:1f.0 ISA bridge: Intel Corporation: Unknown device 2811 (rev 03)
0000:00:1f.2 IDE interface: Intel Corporation: Unknown device 2828 (rev 03)
0000:00:1f.3 SMBus: Intel Corporation: Unknown device 283e (rev 03)
0000:03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
0000:15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
0000:15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd: Unknown device 0832 (rev 04)


iwconfig:

lo     no wireless extensions.
sit0   no wireless  extensions.

---

### Post by moore.bryan on 2007-09-01
*okay, what flavor of ubuntu are you running; e.g., dapper, edgy, feisty, or gutsy?*

---

### Post by sailing511 on 2007-09-01
Dapper

---

### Post by moore.bryan on 2007-09-01
[I]okay, here goes:
[/I][LIST=1]
[*]*add "deb [http://wicd.longren.org](http://wicd.longren.org) dapper extras" to your /etc/apt/sources.list. ```
sudo nano /etc/apt/sources.list
```*
[*]*update and upgrade the system, then install wicd.  it may ask you to remove network-manager; that's okay, you won't need it with wicd. ```
sudo aptitude update && sudo aptitude upgrade && sudo aptitude install wicd
```*
[*]*run wicd in your tray. ```
cd /opt/wicd && ./tray.py
```*
[*]*single-click on the icon in the tray and the Wicd Manager GUI will pop-up.  go to "preferences," choose madwifi as your "WPA Supplicant Driver," and type "ath0" as your "Wireless Interface."  Click "OK" and then "Refresh" at the top of the Wicd Manager screen.*
[*][I]you should now be connected.
[/I][/LIST][I] if any step above didn't work or the choice wasn't available, just post and we'll work
through it.[/I]

---

### Post by sailing511 on 2007-09-01
Thank you so much.

However, as both the wired and wireless network adapters do not work now, I cannot connect to the internet, and thus cannot run apt-update...

---

### Post by moore.bryan on 2007-09-01
[I]ah, very true.  in that case, download the wicd .deb from [here]("http://downloads.sourceforge.net/wicd/wicd_1.3.1-all.deb?modtime=1184023948&big_mirror=0") and transfer it to the lappie in question by floppy/usbthumb/etc/ and install it with ```
sudo dpkg -i wicd_1.3.1-all.deb
```
and then start from step #3.
[/I]

---

### Post by sailing511 on 2007-09-01
Ok, I will try.

Also I am quite confused  why I cannot find modules.conf in my system?
Is that because something wrong happened when installing Dapper?

---

### Post by moore.bryan on 2007-09-01
*ubuntu has simply split all the info one would find in an /etc/modules.conf file into separate module-specific files in /etc/modprobe.d.  for example, if one had a section in the  /etc/modules.conf file pertaining to a module named "firewall," one could now find those specific attributes in the /etc/modprobe.d/firewall file.*

---

### Post by sailing511 on 2007-09-01
AIEE, how to "transfer it to the lappie in question by floppy/usbthumb/etc/"
I do not quite understand what you mean.

Can I save wicd_1.3.1-all.deb in flash disk and mount it to some directory in UBUNTU and run
"sudo dpkg -i wicd_1.3.1-all.deb"

---

### Post by moore.bryan on 2007-09-01
*yup.  if the .deb is on your flash, you don't **need** to transfer it to your hard-drive, just run it from where it is.  it may (and i think it probably will) give you errors about dependencies.  once we know them, we can go about satisfying them.*

---

