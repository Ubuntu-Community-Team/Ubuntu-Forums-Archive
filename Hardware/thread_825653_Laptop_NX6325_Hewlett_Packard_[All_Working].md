---
title: "Laptop NX6325 Hewlett Packard [All Working]"
date: 2008-06-11
forum: Hardware
---

### Post by herbie van tetering on 2008-06-11
Dear Developers,

I was wondering if anyone owns a security enabled [COLOR="Red"]compaq NX6325 laptop of Hewlett Packard[/COLOR]. The laptop is currently installed with [COLOR="Red"]fully functional battlestation[/COLOR] secure drivers enabled, biometric security enabled, dual and single screen acceleration, audio input and -output, standby- and update mode, wired- and wireless roaming, desktop- and communication applications all installed and working. 

Installation time took [COLOR="Red"]2 days[/COLOR] out-of-the-box fully working. Anyone who manages to do this faster and shows me the hardinfo log gets from me a [COLOR="RoyalBlue"]bottle of champagne[/COLOR] for free!

I have *tips* for whoever would like to get a Hewlett Packard laptop to work on Ubuntu Hardy 8.0.4 realtime kernel [xubuntu cdrom download] with all drivers installed. 

* realtime kernel needs to be enabled to make full use of machine
* screen works dual screen from vesa- switched for acceleration mode
* screen works best with ati or nvidia driver command line tools
* audio works best with alsa command line tools and io tests
* security biometric works with authentec driver and fprint pam
* wireless configuration works best when making config readonly

Some important tools to check you hardware and configure things [so that you do not have to type all those commands and make linux less desktop like] in an easy manner.

TOOLS:

* [COLOR="Sienna"]auth authentec [/COLOR]scanner driver [to read biometric]
* [COLOR="Sienna"]fprint finger[/COLOR] project [to enable biometric]
* [COLOR="Sienna"]startupmanager[/COLOR] tool [to handle startup properly]
* [COLOR="Sienna"]hardinfo[/COLOR] hardware tool [to check hardware]
* [COLOR="Sienna"]seahorse keyring[/COLOR] application [to communicate secure]
* [COLOR="Sienna"]ndisgtk[/COLOR] wireless[to talk to windows wireless drivers]
* [COLOR="Sienna"]firestarter[/COLOR] fwall [for firewall frontend]
* [COLOR="Sienna"]gnome network admin[/COLOR] tool [for network admin]
* [COLOR="Sienna"]audio[/COLOR] recorder [for audio io maxvol test]
* [COLOR="Sienna"]xfce mixer[/COLOR] [for audio max volume test]
* [COLOR="Sienna"]aticonf[/COLOR] command [for generating screen views]
* [COLOR="Sienna"]joystick[/COLOR] applet [for joystick testing]
* [COLOR="Sienna"]sd/ms fw card[/COLOR] applet [for card data]

FILES:

[COLOR="Sienna"]/etc/default/acpi-support [/COLOR]      [snatchy standby with those tiny strawhats]
[COLOR="Sienna"]/boot/System.map.<version>-rt [/COLOR]  [os no tampering only cut and paste]
[COLOR="Sienna"]/boot/config.<version>-rt [/COLOR]      [os no tampering only cut and paste]
[COLOR="Sienna"]/boot/initrd.img.<version>-rt [/COLOR]  [os no tampering only cut and paste]
[COLOR="Sienna"]/boot/vmlinuz.<version>-rt[/COLOR]      [os no tampering only cut and paste]
[COLOR="Sienna"]/etc/pam.d/common-auth[/COLOR]          [biometric identity entrance point]
[COLOR="Sienna"]/etc/X11/xorg.conf [/COLOR]             [graphics card for aticonf screen]
[COLOR="Sienna"]/etc/pam.d/gdm [/COLOR]                 [your biometric identity entrance]

Cheers,

Herbie van Tetering.

P.S. Ubuntu is a great Linux version to install commercial off the shelf on laptops like Dell and Hewlett Packard. If you would like to configure a laptop by yourself keep on the lookout of the yard for these things. When your laptop obfuscates, there are some companies that sell ms [metasys] metascript- & membedscript scanners to identify obfuscation activities and -layers. There is also a lot of open work for control panels and other applications to leverage linux operating system into the market.

---

