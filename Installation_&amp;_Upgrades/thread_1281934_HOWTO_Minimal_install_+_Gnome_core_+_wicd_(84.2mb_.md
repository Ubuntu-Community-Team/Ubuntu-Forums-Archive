---
title: "HOWTO: Minimal install + Gnome core + wicd (84.2mb ram used)"
date: 2009-10-03
forum: Installation &amp; Upgrades
---

### Post by loudog23 on 2009-10-03
**_simple HOWTO: Minimal install + Gnome core + wifi (84.2mb ram used)_**

_I just setted ubuntu-jaunty on:_
Toshiba tecra 8100
CPU: 600mhz intel
RAM: 512mb
I/O: cd-rom/pcmcia wifi (zonet zew1530)
:KS total mem usage 84.2mb :KS

Here what you do:
1. Download ubuntu server edition
2. In the 1st install menu press F4 and select minimal install
3. Proceed through the installation
4. Login -> from here you'll need an internet connection (see below for little help on wifi)
5. At the prompt, update the system 'sudo apt-get update'
6. Install your prefered desktop
-> for gnome: sudo apt-get install gnome-core gdm xorg
-> find more [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
7. Reboot into your new desktop
->here i was at 84.2mb ram used (wicd also installed)

_Installing basic packages:_
don't forget this is a 'near-bare-bone' install
you will need to install update-manager, themes and such things manually.
Take a look [http://packages.ubuntu.com/](http://packages.ubuntu.com/) to help you see the package you might want or need.

I strongly suggest you use the synatic-package-manager and add/remove menu to get the software and drivers you want and/or need. If you already know the name of your package, you can use 'sudo apt-get install **package-name-here**' from terminal

**_WIFI Connect:_**
--> Im my case i don't have the wire option on the laptop and i like to use wicd with an WPA encrypted Wifi Router
1. open a terminal on an already connected computer
2. type 'sudo apt-get clean' to clean old donwloaded package [COLOR="Red"]!!! This WILL delete the previsouly downloaded .deb files from the cache folder. Deleting those files is warmless to your system in most case. !!![/COLOR] I just like to tell you before i make you delete stuff :P
3. go to you apt archives folder by typing 'cd /var/cache/apt/archives'. It sould be empty. (If not, don't worry too much about it - better not delete the remaining files)
4. type 'sudo apt-get -d install wicd' to download wicd (will not install because of the -d key)
5. create somewhere to copy the files 'mkdir /home/**%user%**/deb'
6. copy these files into it 'sudo cp /var/cache/apt/archives/* /home/**%user%**/deb/
7. close terminal
8. Make a debian iso files (i used APTonCD -> find it in add/remove software menu)
9. Burn the image
10. Put the newly burned cd in the unconnected system 
--> from here command are to be use on the unconnected system
11. type 'sudo apt-cdrom add' to add the newly made cd to rep
12. type 'sudo apt-get install wicd' to install wicd
13. make sure to configure your wicd conf files using 'sudo nano -w /etc/wicd/wireless-settings.conf'. See Annexe-1 for sample
14.Reboot


Annexe-1 : sample file of '/etc/wicd/wireless-settings.com'
(**bold** caracter sould be replace by your setting)
```

[**MacAddressOfYourRouter (xx:xx:xx:xx:xx:xx)**]
afterscript = None
bssid = **MacAddressOfYourRouter (xx:xx:xx:xx:xx:xx)**
ip = None
quality = 51
gateway = None
use_global_dns = 0
strength = -50
disconnect = None
encryption = True
beforescript = None
hidden = False
channel = 11
essid = **YourNetworkName**
has_profile = True
netmask = None
key = **YourNetworkKey**
enctype = **wpa**
dns3 = None
dns2 = None
dns1 = None
use_settings_globally = 0
use_static_dns = 0
encryption_method = **WPA**
mode = Master
automatic = True

```

Hope this help someone.:guitar:

---

### Post by loudog23 on 2009-10-03
_Here some basic package, the name says it all:_
[http://packages.ubuntu.com/jaunty/gnome-system-tools](http://packages.ubuntu.com/jaunty/gnome-system-tools)
[http://packages.ubuntu.com/jaunty/gnome-utils](http://packages.ubuntu.com/jaunty/gnome-utils)
[http://packages.ubuntu.com/jaunty/setserial](http://packages.ubuntu.com/jaunty/setserial) - If you use serial ports
[http://packages.ubuntu.com/jaunty/firefox](http://packages.ubuntu.com/jaunty/firefox)
[http://packages.ubuntu.com/jaunty/update-manager](http://packages.ubuntu.com/jaunty/update-manager)

---

### Post by loudog23 on 2009-10-04
My final Product (under 100mb and looking nice :)):
[IMG]http://www.tchiwam.net/gallery/d/65877-2/Screenshot_001.png[/IMG]

---

