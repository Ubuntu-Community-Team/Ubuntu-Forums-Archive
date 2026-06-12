---
title: "Easy MadWifi (Atheros WLAN) installation script"
date: 2008-05-18
forum: Hardware
---

### Post by Kajaste on 2008-05-18
**Latest news: **
11th March 2009 - 0.9.8.4: A (hopefully) better --uninstall which reinstalls module packages.
10th March 2009 - 0.9.8.2: thanks to JayD239 the SVN URL is no longer broken. Please update :)
21st October 2008 - 0.9.8.1: madwifi.sh now automatically adds ath_pci to /etc/modules to make Ubuntu load it automatically at boot. It also removes ath_pci from autoload when --uninstalling.
15th October 2008 - 0.9.8: By requests I added an --uninstall option. I didn't test it much so let's hope it works ;)
21st July 2008 - 0.9.7: New option --info and some hardware checking.
16th July 2008 - For AR5007 (AR252x in lspci, found at least on Asus EEE) on 32-bit you will need a special tarball of madwifi-ng or madwifi-hal that can be downloaded from [http://snapshots.madwifi-project.org/special/](http://snapshots.madwifi-project.org/special/). 64-bit users should check [this (ndiswrapper method) ]("http://blog.linuxoss.com/2008/05/08/ubuntu-804-enabling-atheros-ar5007-based-wireless/") or [this (madwifi-hal method)]("http://madwifi.org/ticket/1192") out.
--
[COLOR="Red"]**The new open source [ath5k]("http://madwifi-project.org/wiki/About/ath5k") and [ath9k]("http://linuxwireless.org/en/users/Drivers/ath9k") drivers included in Ubuntu 8.10 Intrepid Ibex and newer (should) replace MadWifi.** 
**When upgrading to 8.10** or newer version of Ubuntu you might want to **--uninstall MadWifi first** to avoid conflicts with the new drivers. Since 8.10 Atheros WiFi should work straight out-of-the-box.[/COLOR]
--

**What is this script all about?**
I have been working on an installation script for [MadWifi]("http://madwifi-project.org/"), the best Atheros driver for Linux at the moment, that should work in Ubuntu, Debian and Fedora. I have been using it with my MacBook [AR5418] for some time and found it very useful.

**Do I need this script? Will it solve my WiFi problems?**
If you're in need of MadWifi, then this script should help you. Please note that MadWifi does not support any USB devices. To find out which cards are supported see [http://madwifi-project.org/wiki/Compatibility](http://madwifi-project.org/wiki/Compatibility).

**Okay, so how do I use this script to install MadWifi?**
Basically, if you have a working Internet connection (no worries if you don't, see below), all you need to do is download the script
```
wget http://kolmoskone.homelinux.org/~kaja/kamaa/madwifi.sh -O madwifi.sh
chmod +x madwifi.sh
```
(you can also upgrade your current madwifi.sh to the latest version with these commands)

And then run it with sudo
```
sudo ./madwifi.sh
```

**What is going to happen when I run the script?**
This will install the build dependencies, fetch the latest source code from MadWifi SVN, compile and install the module. After it completes you should be able to connect to an AP with Ubuntu's NetworkManager icon in the notification area. 8) (it might take up to about a minute to pick up a network)

**Is there anything I should do after installing?**
If it works well enough, do sudo ./madwifi.sh --save to save the working version of sources. If an update breaks the sources you can then do sudo ./madwifi.sh --working to use the saved sources.
You might want to see --help every once in a while to help you remind how the script works.

**How about kernel updates?**
Note that **you have to run the script after every kernel update!** For a reinstall you can also use sudo ./madwifi.sh --reinstall which doesn't fetch a new version of MadWifi but uses the one last installed.

**Installing without an Internet connection or using a source tarball (not fun)**
SVN code does not always compile succesfully and not all of us can access a wired connection to the Internet. That's why I have included a possibility to use a source tarball from madwifi.org. 

You need to put madwifi.sh, madwifi-VERSION.tar.gz (from [http://madwifi-project.org/](http://madwifi-project.org/) or [http://snapshots.madwifi-project.org/madwifi-trunk/](http://snapshots.madwifi-project.org/madwifi-trunk/)) and the following Ubuntu packages (from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)): make, gcc, libc6-dev, linux-headers-YOURKERNELVERSION on a removable media (CD, flash memory,...). VERSION is something like 0.9.4 or trunk-r3721-20080613 and can be seen in the tarball filename. You can easily find out YOURKERNELVERSION by running the uname -r command. 

**Tip:** You can download the files to the hard drive in OS X or Windows (or whatever you might be dual booting) and then access the downloaded files in Ubuntu! 
If you have a wired connection in Ubuntu the dependencies will be automatically installed, so you don't need to manually install the packages then, just download the tarball and run the script.

Once you have the files, insert the removable media and install the packages by double clicking on them in Nautilus or by running
```
sudo dpkg -i /path/to/package.deb
```

Then run the script like this:
```
chmod +x madwifi.sh
sudo ./madwifi.sh --tarball /path/to/madwifi-VERSION.tar.gz
```

Of course you need to substitute VERSION with the actual MadWifi version. After it completes you should be able to connect to an AP with Ubuntu's NetworkManager icon in the notification area. 8)

Note that **you have to run the last command after every kernel update**, so keep the source tarball at hand! You can also start using the SVN way now that you have a working connection.

**Troubleshooting and different versions of MadWifi**
[COLOR="Red"]**If the driver isn't working, try another version of it (trunk, ng, hal or different revision)!**[/COLOR]
The script installs trunk by default.

Especially when having this output
```
ath_pci: HAL doesn't support MAC revision
```
it's most likely fixed by trying [ng tarball]("http://snapshots.madwifi-project.org/special/") or [hal tarball]("http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/").

There are alternatives to MadWifi called ath5k and ath9k. If the script doesn't work and you get some results by running for example
```
dmesg | grep ath5k
```
try running 
```
sudo modprobe -r ath5k
```
before running the script. If it helps, blacklist ath5k. If it doesn't, try the same replacing ath5k with atk9k.

**Problems?**
If the script is broken or sucks in any way, please let me know.

When reporting problems please provide the following information:
* output of command sudo ./madwifi.sh --info
* are you using SVN or a (version?) snapshot
* any interesting lines in dmesg output that the above command does not show
* information on the hardware used, laptop or pci card make/model

---

### Post by BlackRaven on 2008-05-21
Wow, thanks man.  You rock!!  :guitar:
That worked like a charm. On the first try too.
Much appreciated.

---

### Post by quanumphaze on 2008-05-24
Is there a way to go back to the old drivers in case this doesn't work?

I need my wireless. It works fine at home (WPA-PSK) but at university which uses EAP I must use wpa_suplicant from the terminal and it locks up the whole system 1/10 times. So I don't want to make things worse just yet.

Would you recommend that I wait until some more people try it and bugs get fixed before I try it or just go for it?
(I have a USB wireless chip if it doesn't work out.)

---

### Post by Kajaste on 2008-05-24
I'd say the script is very reliable at least if you go for the normal SVN installation.

I have had lock ups with the "stable" madwifi release but not with the SVN version. The only problem I've ever had with SVN was the source not compiling on x86_64 once. To be sure you can download a few snapshots from [http://madwifi.org/](http://madwifi.org/) so at least some of them will work.

For a backup you can take the package that you used to install madwifi before.

---

### Post by quanumphaze on 2008-05-25
What good is a Linux distro if you don't break things? :)
I'll try it out once I have free time on Wednesday / Tuesday evening after my test.

I'll be sure to post the outcome.

---

### Post by quanumphaze on 2008-05-28
Needs a bit more error checking

I stopped it prematurely as it couldn't use svn but kept on going.

```
You seem to be running Debian/Ubuntu.
Checking build dependencies...
No packages found matching subversion.
Installing subversion...E: Some packages could not be authenticated
OK
...build dependencies OK.
Fetching sources from SVN..../madwifi.sh: line 159: svn: command not found
./madwifi.sh: line 160: cd: madwifi: No such file or directory
OK
Running pre-install scripts../madwifi.sh: line 186: cd: scripts: No such file or directory
../madwifi.sh: line 193: ./find-madwifi-modules.sh: No such file or directory
.OK
Building MadWifi.make: *** No rule to make target `clean'.  Stop.
.make: *** No targets specified and no makefile found.  Stop.
.OK
Installing MadWifi.make: *** No rule to make target `install'.  Stop.
.

```

If any error happens at all it should quit. (I wish I knew bash scripting so I could actually help.)

Edit: I have installed subversion now. Luckily this stopped it because I forgot to backup.

---

### Post by Kajaste on 2008-05-28
Yeah that's totally my bad. I was going to add a check after every command later but didn't think it was critical. Sorry :(

You can always hit ^C (Ctrl and C) to stop a script or a program from running. (or at least in most cases)

I'll start adding checks now.

---

### Post by quanumphaze on 2008-05-28
> **Kajaste said:**
> Yeah that's totally my bad. I was going to add a check after every command later but didn't think it was critical. Sorry :(

You can always hit ^C (Ctrl and C) to stop a script or a program from running. (or at least in most cases)

I'll start adding checks now. If I don't have to go and help my parents with something it shouldn't take too long.

That's cool.

"sudo apt-get install subversion" made it work, and I have wireless back up, no problems. Hopefully it will work with the WPA EAP at uni without lockups.

You get a gold star (a Thanks)

---

### Post by Kajaste on 2008-05-28
(Just to make sure everyone notices) I'm writing this reply to inform you of a new version with some cool new features such as saving and loading a working backup of the sources in case something goes wrong with svn update.

---

### Post by quanumphaze on 2008-05-28
YAY! no atheros modules have locked up my system yet.
(It's only the first day at uni with the new modules so too soon to tell if it's stable.)

Survives suspend too.

---

### Post by libby-martian on 2008-05-29
ok I tried this and it seemed to install with no odd errors (including the subversion) and it still doesn't work.  is there anything else I need to do to get it to pick up the signal?  the wifi led is still off and going to edit wireless networks shows no networks (big shock I'm sure).  sorry but I'm not only new to laptops, I'm still quite new to linux

btw thanks for posting this

---

### Post by Kajaste on 2008-05-29
I'm sorry to hear that. Too bad I'm not a MadWifi guru and my only Atheros WLAN chip is in the MacBook.

Some things you might want to check are:
* dmesg (the command) output (especially the last lines)
* lspci (the command) output (to see exactly what chip you have)
* compatibility list at [http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)

The network tools don't usually work instantly, there is a slight delay of about 10 - 60 seconds after the script is done.

It might be useful to google around ubuntu and linux sites with the name and model of your wlan chip.

---

### Post by libby-martian on 2008-05-29
I did and found a different driver but I'm not sure how to actually install it, especially after installing something else.  sorry for the stupid questions but how do I uninstall the madwifi and then install the other one?

---

### Post by Kajaste on 2008-05-29
> **libby-martian said:**
> I did and found a different driver but I'm not sure how to actually install it, especially after installing something else.  sorry for the stupid questions but how do I uninstall the madwifi and then install the other one?

I guess you might have to sudo modprobe -r ath_pci and add ath_pci to /etc/modprobe.d/blacklist before installing another driver. It might be that it's not even necessary to remove MadWifi in any way.
Read the other driver's documentation to find out how to install it.

---

### Post by quanumphaze on 2008-05-30
I don't know about you but I found that when I toggled the wireless slide switch it did nothing (with the old driver). Next boot the wireless would not be detected and none of the modules were loaded.

Toggle the switch and reboot. The light should turn on at boot and it might work.

---

### Post by libby-martian on 2008-05-30
toggling the switch does nothing for hte wireless but it does work for the bluetooth.  same with fn/f5.  have rebooted several times and thaht doesn't help either.  *sigh* gonna have to keep fussing with it

---

### Post by quanumphaze on 2008-05-30
Oh noes!!!

Kernel update. Time to recompile it.

libby-martian, the kernel update will disable the madwifi driver. Try to enable the old one instead since you will have to recompile the svn one again.
I have no idea what I'm talking about since I'm still technicaly a n00b.

Although I hear that the ndiswrapper with the Windows Atheros driver lets you use the switch very well. Try that if you have no usable alternative.

---

### Post by libby-martian on 2008-06-04
thanks for the help everyone.  I've not had much time this week to mess with things but I will tomorrow or friday, and I'll let you know what works if it works or whatever the results are  :lolflag:

---

### Post by libby-martian on 2008-06-04
btw here are the last lines of dmesg (holy cow there are a lot of other lines!)

[  115.014859]  domain 0: span 03
[  115.014861]   groups: 01 02
[  115.014865] CPU1 attaching sched-domain:
[  115.014867]  domain 0: span 03
[  115.014868]   groups: 02 01
[  120.861711] usb 2-1: new low speed USB device using uhci_hcd and address 2
[  121.099815] usb 2-1: configuration #1 chosen from 1 choice
[  121.236528] usbcore: registered new interface driver hiddev
[  121.251705] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1a.1/usb2/2-1/2-1:1.0/input/input12
[  121.285455] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1a.1-1
[  121.285682] usbcore: registered new interface driver usbhid
[  121.285810] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[  381.713010] e1000: eth0: e1000_watchdog: NIC Link is Down
[ 1454.561217] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1454.561228] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[ 1454.566081] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1463.223214] eth0: no IPv6 routers present
[ 1613.785650] e1000: eth0: e1000_watchdog: NIC Link is Down
[ 1614.239109] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1614.239119] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[ 1614.243978] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1617.515657] eth0: no IPv6 routers present

---

### Post by libby-martian on 2008-06-04
and oh hey look I found this:  

rio1/input/input9
[   29.304968] iwl3945: Radio Frequency Kill Switch is On:
[   29.304970] Kill switch must be turned off for wireless networking to work.
[   29.313185] iwl3945: WARNING: Requesting MAC access during RFKILL wakes upNIC
[   29.323252] iwl3945: WARNING: Requesting MAC access during RFKILL wakes upNIC
[   29.343251] iwl3945: WARNING: Requesting MAC access during RFKILL wakes upNIC
[   29.370642] iwl3945: WARNING: Requesting MAC access during RFKILL wakes upNIC

how do you disable the kill switch?  and is this the actual problem here?

---

### Post by Kajaste on 2008-06-05
> **libby-martian said:**
> btw here are the last lines of dmesg (holy cow there are a lot of other lines!)

[  115.014859]  domain 0: span 03
[  115.014861]   groups: 01 02
[  115.014865] CPU1 attaching sched-domain:
[  115.014867]  domain 0: span 03
[  115.014868]   groups: 02 01
[  120.861711] usb 2-1: new low speed USB device using uhci_hcd and address 2
[  121.099815] usb 2-1: configuration #1 chosen from 1 choice
[  121.236528] usbcore: registered new interface driver hiddev
[  121.251705] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1a.1/usb2/2-1/2-1:1.0/input/input12
[  121.285455] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1a.1-1
[  121.285682] usbcore: registered new interface driver usbhid
[  121.285810] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[  381.713010] e1000: eth0: e1000_watchdog: NIC Link is Down
[ 1454.561217] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1454.561228] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[ 1454.566081] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1463.223214] eth0: no IPv6 routers present
[ 1613.785650] e1000: eth0: e1000_watchdog: NIC Link is Down
[ 1614.239109] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1614.239119] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[ 1614.243978] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1617.515657] eth0: no IPv6 routers present

No sign of MadWifi there. Did you run the script before checking dmesg? 

If MadWifi finds your wifi it shows in dmesg very clearly. First there's something like "ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)", this will show even if you don't have a card supported by MadWifi. 

If you get lines beginning with wifi0 and something like "ath_pci: wifi0: Atheros 5418: mem=0x50100000, irq=17" or "wifi0: Atheros AR5418 chip found (MAC 12.10, PHY SChip 8.1, Radio 12.0)" MadWifi has found your card. 

You can cut out irrelevant lines easily with grep. Using command dmesg | grep wifi0 or dmesg | grep ath_ it will only show interesting lines.

> and oh hey look I found this:

rio1/input/input9
[ 29.304968] iwl3945: Radio Frequency Kill Switch is On:
[ 29.304970] Kill switch must be turned off for wireless networking to work.
[ 29.313185] iwl3945: WARNING: Requesting MAC access during RFKILL wakes upNIC
[ 29.323252] iwl3945: WARNING: Requesting MAC access during RFKILL wakes upNIC
[ 29.343251] iwl3945: WARNING: Requesting MAC access during RFKILL wakes upNIC
[ 29.370642] iwl3945: WARNING: Requesting MAC access during RFKILL wakes upNIC

iwl3945 is a driver module for Intel Wireless that comes with 2.6.24 and newer kernels. Is it possible that you have an Intel wifi card? If you don't then you should probably try to blacklist that module.

---

### Post by Kajaste on 2008-06-05
Before version 0.9.6 the script claims that the sources were not updated even if they were. This is because it looks for changes in /usr/src/madwifi/svnversion.h which seemed like a good idea. It wasn't. 
New version checks the output of svn info before and after update. It seemed to contain correct version information.

To see your version you can ./madwifi.sh --help

To update to the latest version of the script use wget [http://kolmoskone.homelinux.org/~kaja/kamaa/madwifi.sh](http://kolmoskone.homelinux.org/~kaja/kamaa/madwifi.sh) -O madwifi.sh && chmod +x madwifi.sh

I'm deeply sorry.:(

---

### Post by BMan12 on 2008-06-05
I'm trying to use your method but I have to do it the without internet way. Where do I find the .deb files? I can find .tar.gz files for all of the packages listed, but what do I do with those?
Any help would be greatly appreciated.

---

### Post by Kajaste on 2008-06-06
> **BMan12 said:**
> I'm trying to use your method but I have to do it the without internet way. Where do I find the .deb files? I can find .tar.gz files for all of the packages listed, but what do I do with those?
Any help would be greatly appreciated.

* go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
* search package directories
  * use package name as keyword
  * select distribution according to your current version (lsb_release -c)
* click on the best (usually first) search result
* scroll down to architecture and select according to your installation (uname -m, i(6/5/4/3)86 -> i386, x86_64 -> amd64)
* pick a download mirror close to you

---

### Post by dented42 on 2008-06-12
I'm on a macbook, and this works brilliantly, it runs with no errors, gave me just enough feedback so I don't start to panic thinking that it froze, but not so much feedback that it clutters my screen.

my only problem is that it didn't seem to have any effect, although the script says it completed succesfully.:confused:

but other then that, it worked perfectly!:lolflag:

---

### Post by Kajaste on 2008-06-12
> **dented42 said:**
> I'm on a macbook, and this works brilliantly, it runs with no errors, gave me just enough feedback so I don't start to panic thinking that it froze, but not so much feedback that it clutters my screen.

my only problem is that it didn't seem to have any effect, although the script says it completed succesfully.:confused:

but other then that, it worked perfectly!:lolflag:

Network manager shows no wireless even after waiting a minute? Is there anything interesting in dmesg? Does your MacBook have Atheros WiFi (lspci)? Is the version of the chip supported by MadWifi?

Commands you might want to run:
```
lspci | grep Atheros
dmesg | grep ath_
dmesg | grep wifi0
```

If the last command shows something then MadWifi should be up and running.

---

### Post by Zaff on 2008-06-17
Thanks this worked flawlessly and is really convenienty as there's been quite a few kernel updates lately (I wonder why ...)
I don't really understand why it wouldn't work when I tried to compile and install manually. Never had that issue in Gutsy but oh well...
So thanks again I'll be keeping this one around for a while.

---

### Post by Kajaste on 2008-06-18
> **Zaff said:**
> Thanks this worked flawlessly and is really convenienty as there's been quite a few kernel updates lately (I wonder why ...)
I don't really understand why it wouldn't work when I tried to compile and install manually. Never had that issue in Gutsy but oh well...
So thanks again I'll be keeping this one around for a while.

I'm glad to hear it's working for you!

You can open the script file in a text editor to see what it does. I have not written any informative comments in the file like I should have, but at least you can see the commands it uses.

There have been quite a few security updates to Linux 2.6 lately so naturally Ubuntu has to update their kernels too =/

---

### Post by demonstealer on 2008-06-26
Dude

You rock.. Thanks a ton for this script

Worked like a charm on my Asus F3ka with Atheros AR5148. Tried so many things before this with no success. But this one just worked and I didn't have to do anything other than run the script. Thanks again

Regards
-Apoorva

---

### Post by Flag on 2008-06-26
Thanks

OOOKEEE used the [http://blog.linuxoss.com/2008/05/08/...ased-wireless/](http://blog.linuxoss.com/2008/05/08/...ased-wireless/).

was struggling for a while now, needed to rmmod / modprobe ndsiswrapper, that's been solved now.

Thanks again

---

### Post by quanumphaze on 2008-06-27
> **Flag said:**
> Thanks

OOOKEEE used the [http://blog.linuxoss.com/2008/05/08/...ased-wireless/](http://blog.linuxoss.com/2008/05/08/...ased-wireless/).

was struggling for a while now, needed to rmmod / modprobe ndsiswrapper, that's been solved now.

Thanks again

Your link is broken :(

---

### Post by Kajaste on 2008-06-27
> **quanumphaze said:**
> Your link is broken :(

Working link in the first post of the thread.

---

### Post by heavenly_blade101 on 2008-07-01
```
OK
...build dependencies OK
Fetching sources from SVN...
svn: PROPFIND request failed on '/madwifi/trunk'
svn: PROPFIND of '/madwifi/trunk': could not connect to server (http://svn.madwifi.org)
root@justin-laptop:~# 

```

: / any ideas? everything up to that point worked fine.

---

### Post by quanumphaze on 2008-07-01
You seem to be having connection problems

The script is trying to fetch the sources from the svn server and failing.

OP shows how to get the sources manually if you don't get a connection. Even if you have a connection you can try this way and it will still work.

Get the latest sources from here: [http://snapshots.madwifi.org/madwifi-trunk/](http://snapshots.madwifi.org/madwifi-trunk/)

Then:```
sudo ./madwifi.sh --tarball /path/to/madwifi-VERSION.tar.gz
```

---

### Post by libby-martian on 2008-07-08
I copied and pasted the code just as you have it in the box and it tells me basically no

libby-martian@the-geekpad:~$ sudo ./madwifi.sh --tarball /path/to/madwifi-VERSION.tar.gz
[sudo] password for libby-martian:
You seem to be running Debian/Ubuntu.
./madwifi.sh: line 26: Tarball not found in /path/to/madwifi-VERSION.tar.gz, exiting...: No such file or directory
libby-martian@the-geekpad:~$


btw thanks all for continuing to help...  I've been swamped and not able to work on this for weeks now

---

### Post by Kajaste on 2008-07-08
> **libby-martian said:**
> I copied and pasted the code just as you have it in the box and it tells me basically no

libby-martian@the-geekpad:~$ sudo ./madwifi.sh --tarball /path/to/madwifi-VERSION.tar.gz
[sudo] password for libby-martian:
You seem to be running Debian/Ubuntu.
./madwifi.sh: line 26: Tarball not found in /path/to/madwifi-VERSION.tar.gz, exiting...: No such file or directory
libby-martian@the-geekpad:~$


btw thanks all for continuing to help...  I've been swamped and not able to work on this for weeks now

You are supposed to replace that example path with the actual path to the downloaded tarball. Something like /home/libby/Desktop/madwifi-0.9.4.tar.gz might be pretty close.

---

### Post by Sorex on 2008-07-15
I ran this script and it never completed.  Now the wireless part of the Network Manager is absent... (only wired and point to point have an entry) how do I get it back?  If I try to run the script again it says that I am already up to date.  Please be kind I'm new here.

---

### Post by Kajaste on 2008-07-15
> **Sorex said:**
> I ran this script and it never completed.  Now the wireless part of the Network Manager is absent... (only wired and point to point have an entry) how do I get it back?  If I try to run the script again it says that I am already up to date.  Please be kind I'm new here.

You should try running it with --reinstall like this:
```
sudo ./madwifi.sh --reinstall
```

---

### Post by Sorex on 2008-07-15
Thanks Kajaste - I got this to complete the install, which I think is good news.  However, when I run dmesg, the line concerning MadWifi says

[  806.806709] MadWifi: unable to attach hardware; 'Hardware didn't respond as expected' (HAL status 3)

I (unsuprisingly) get no response from dmesg | grep wifi0 .

Any hints?  Thanks for your time on this one!

---

### Post by Kajaste on 2008-07-16
> **Sorex said:**
> Thanks Kajaste - I got this to complete the install, which I think is good news.  However, when I run dmesg, the line concerning MadWifi says

[  806.806709] MadWifi: unable to attach hardware; 'Hardware didn't respond as expected' (HAL status 3)

I (unsuprisingly) get no response from dmesg | grep wifi0 .

Any hints?  Thanks for your time on this one!

I tried google with that error message and it gave me nothing very interesting or up to date. Which chip do you have (lspci | grep Atheros) and is it in a laptop or a PCI card? What model is the laptop or PC?

...and also which version of Ubuntu are you running (lsb_release -c) and what is the kernel version you are using (uname -r).

---

### Post by Sorex on 2008-07-16
The chip is AR242x, it is in a laptop.
It is a brand new custom built lappy - model JTF00 (T5650, 2GB RAM)
I'm running Hardy.
Kernel version is 2.6.24-19-generic

---

### Post by Kajaste on 2008-07-16
> **Sorex said:**
> The chip is AR242x, it is in a laptop.
It is a brand new custom built lappy - model JTF00 (T5650, 2GB RAM)
I'm running Hardy.
Kernel version is 2.6.24-19-generic

It seems that you need a special version of MadWifi called madwifi-hal. You can get it's snapshots from [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/) but I don't know which version works best. Trying the latest version first should be a good idea.

Here's an example on how to use the latest madwifi-hal snapshot:
```
wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3772-20080716.tar.gz
sudo ./madwifi.sh --tarball madwifi-hal-0.10.5.6-r3772-20080716.tar.gz
```

Here's a link for more information [http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192) it should be up to date (modified 1 day ago).

---

### Post by Sorex on 2008-07-17
I've been reading all those pages, and I think I have all the requirements.  However, when I run 

sudo ./madwifi.sh --tarball madwifi-hal-0.10.5.6-r3772-20080716.tar.gz

I get the error

sudo: ./madwifi.sh: command not found

It seems that I have the file, I also tried expanding it but that doesn't help...

---

### Post by Kajaste on 2008-07-17
> **Sorex said:**
> I've been reading all those pages, and I think I have all the requirements.  However, when I run 

sudo ./madwifi.sh --tarball madwifi-hal-0.10.5.6-r3772-20080716.tar.gz

I get the error

sudo: ./madwifi.sh: command not found

It seems that I have the file, I also tried expanding it but that doesn't help...

Have you got the script in the same dir? Try running 
```
wget http://kolmoskone.homelinux.org/~kaja/kamaa/madwifi.sh -O madwifi.sh
chmod +x madwifi.sh
``` before trying sudo ./madwifi.sh anything.

---

### Post by Sorex on 2008-07-17
Thanks - it worked that time and Madwifi installed.  

If it is working, should I be able to go to "edit wireless connections" and see the wireless network that I am trying to connect to in the left hand box? or is there something else I should be doing for it to see networks?

Thanks for you ongoing help!

---

### Post by Sorex on 2008-07-17
[SIZE="7"]thankyou![/SIZE]

it's working!

:KSI LOVE YOU:KS

---

### Post by Sorex on 2008-07-18
Arg... Yes it has worked as in madwifi is installed!  It can't see any wireless networks though.  I have made sure that it is on .11g, as is the router. If I try to scan with 
```
iwlist ath0 scan
```
It says no scan results.  But it doesn't seem to try to scan, it immediately returns that there are no results.  I'm pretty sure the card is on (there's no external switch).

Any suggestions?

EDIT: this is clearly now a problem with not being able to turn on my RF switch, as madwifi is definitely running.  Sorry for post irrelevant to this thread.

---

### Post by Kajaste on 2008-07-18
> **Sorex said:**
> Arg... Yes it has worked as in madwifi is installed!  It can't see any wireless networks though.  I have made sure that it is on .11g, as is the router. If I try to scan with 
```
iwlist ath0 scan
```
It says no scan results.  But it doesn't seem to try to scan, it immediately returns that there are no results.  I'm pretty sure the card is on (there's no external switch).

Any suggestions?

EDIT: this is clearly now a problem with not being able to turn on my RF switch, as madwifi is definitely running.  Sorry for post irrelevant to this thread.

I hope you get it working whatever the problem is. The dmesg command could show some useful information that might help.

---

### Post by charles_316 on 2008-07-20
thanks so much.. been trying to get wireless working on my thinkpad t60 for months!

---

### Post by Kajaste on 2008-07-21
> **charles_316 said:**
> thanks so much.. been trying to get wireless working on my thinkpad t60 for months!

Nice to hear it's working now :)

---

### Post by Hits3 on 2008-07-23
hi, can anyone helps me?

i have a toshiba u-300 laptop with GN-WI01GT mini-pci.
```
GN-WI01GT
Chipset:	AR5006EG, 108Mbps,b/g
Interface:	Mini PCI Express
Notes:	Works great with Network-Manager in Ubuntu with latest MadWifi snapshot
Notes:	Is this actually a WI01GT? If so it should be AR5006EGS, XR, 108Mbps, b/g
Notes:	Works from HAL version 0.9.18 onward. This card was not detected with HAL 0.9.17.2 (which happens to be the version found in madwifi-ng-0.9.2.1 in Gentoo portage as of Feb. '07). Gentoo users should install from the tarball provided here until portage is updated.
September/October 2006
Notes:	I just changed my Intel Pro Wireless 3945 against this device in my Dell D620. Works great (out of the box) with gentoo kernel 2.6.23.
```
I have downloaded madwifi-hal-0.10.5.6-r3772-20080716.tar.gz and doesn't work.
```
hits@hits-portatil:~$ sudo ./madwifi.sh --tarball /home/hits/Escritorio/madwifi-hal-0.10.5.6-r3772-20080716.tar.gz
[sudo] password for hits: 
Found at least one Atheros device.
Checking build dependencies...
...build dependencies OK
Unrolling tarball version hal-0.10.5.6-r3772-20080716...OK
Running pre-install scripts...OK
Building MadWifi...OK
Installing MadWifi...OK
Loading kernel module...OK
No compatible chip found for the driver installed

```

Thanks for help

---

### Post by Kajaste on 2008-07-23
Is it really not working? The script might say that it's not but it could work anyway. If it's really not working, post the output of sudo ./madwifi.sh --info here and if there are any other interesting lines in dmesg output post them too.

---

### Post by Hits3 on 2008-07-23
wifi connection now works well, but when i try to put wifi card in monitor mode i can't.

> hits@hits-portatil:~$ sudo ./madwifi.sh --info
Found at least one Atheros device.
Linux hits-portatil 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux
Distro: Debian
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Giga-byte Technology Unknown device e913
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at f0200000 (64-bit, non-prefetchable) [size=64K]

ath_rate_sample        16000  1 
ath_pci               248632  0 
wlan                  235888  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               252512  3 ath_rate_sample,ath_pci


---

### Post by Kajaste on 2008-07-23
Have you tried the normal SVN installation or different versions of madwifi-hal and madwifi-ng. I understood that AR5006EG should work with most of them since there are so many reports of it working.

---

### Post by Hits3 on 2008-07-23
i have installed the ng version and hl version.
in both, when i use airmon:

> hits@hits-portatil:~$ sudo airmon-ng start ath0


Interface	Chipset		Driver

wifi0		Atheros		madwifi-ng
ath0		Atheros		madwifi-ng VAP (parent: wifi0) (VAP cannot be put in monitor mode)



my /etc/kismet/kismet.conf
> 
source=madwifi_ag,ath0,madwifi

---

### Post by Kajaste on 2008-07-23
I'm sorry I haven't used airmon/kismet on Linux although I've heard that madwifi should work like a charm with it.

---

### Post by dstan on 2008-07-24
Sorry for my ignorance here - I am usually pretty much able to figure things out.

It looks like my card is functional as I can see different wireless networks in range and I even turned on my essid broadcast on my router so that I was sure it could be seen.

The issue is that I cannot get anything other than an internal (169) IP.  I also do not see anything other than wired network (if I have it plugged in), connect to 802.1x Protected Wired Network, or manual configuration if I click on the networking icon on the bar up next to the clock.

I have used this script and the error received was that no chips were found that were compatible, though like I said if I do an ifconfig it shows me the card itself is functional, just that it has an internal IP.  I have tried giving the card a static IP, but that was no go either.

I do have my wireless secured with WEP and TKIP PSK which I am sure I have typed the PSK multiple times and I have other computers connecting to this AP so I don't believe it is there that the issue lies.  I have turned off MAC filtering for the time being.

I guess what my issue is is that it looks to me like the card is working fine, but I cannot get it to associate to the AP, though I am not 100% positive the card is functional because I can only run the few commands I know (not many).

Any suggestions?

Never mind at all - for some reason I was able to get it to associate.  Like I said the card looked like it was working.......thanks anyway

---

### Post by dstan on 2008-07-24
Actually now after the updates to the machine I reinstalled madwifi using the script - the card shows up and looks ok again but will not associate.

I will continue to try to make this things work, I really don't understand it at all why it is so flaky.

Strange - when I allow the ssid to be broadcast I can connect - when I hide it, even though I type it right, it will not connect.

---

### Post by Kajaste on 2008-07-25
> **dstan said:**
> Actually now after the updates to the machine I reinstalled madwifi using the script - the card shows up and looks ok again but will not associate.

I will continue to try to make this things work, I really don't understand it at all why it is so flaky.

Strange - when I allow the ssid to be broadcast I can connect - when I hide it, even though I type it right, it will not connect.

That sounds really weird to me too. Maybe [this thread]("http://ubuntuforums.org/showthread.php?t=684495") has some tricks to make it work.

---

### Post by Pete89 on 2008-08-03
Hello,

I have an IMB x31 running Xubuntu 8.04 with a Proxim 8470-WD card in it. I ran the script and here is the output:

```
sudo ./madwifi.sh 
Found at least one Atheros device.
Checking build dependencies...
...build dependencies OK
Running pre-install scripts.ERROR: Module ath_pci is in use
ERROR: cannot unload module "ath_pci"
..OK
Building MadWifi...OK
Installing MadWifi...OK
Loading kernel module...

```

And there it stays and never finishes. Here is some more info:

```
dmesg | grep ath
[   32.647551] ath_hal: module license 'Proprietary' taints kernel.

```

and 

```
lspci | grep Atheros
03:00.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
```

Any ideas?? I am a newbie so I appreciate the help.

P.

---

### Post by Kajaste on 2008-08-03
That seems really weird. The module should be unloadable at least I have never seen it fail. Try turning wireless of with the nm-applet (network icon in notification area) before running the script and then turning it back on once the script has finished.

Also rebooting the computer after running the script should load the new ath_pci module compiled by the script.

---

### Post by Pete89 on 2008-08-03
Thanks for your quick reply. 

When I open the Network Applet I have under *Connections Wired Conection* and *Point to Point Connection*. Should I see *Wireless Connection* there too?

I have tried to reboot and then do the script again with *--reinstall* but not working either

Thanks

---

### Post by Kajaste on 2008-08-03
Yes you should. It seems that you need to do some tricks before it starts working. I'll try to google some answers.

EDIT: Try this
```
sudo rm /lib/modules/`uname -r`/net/ath_pci.ko
sudo rm /lib/modules/`uname -r`/net/ath_hal.ko

```
then reboot and sudo ./madwifi.sh --reinstall

If it doesn't work, try using another version of madwifi such as madwifi-ng or madwifi-hal.

---

### Post by Pete89 on 2008-08-03
Please let me help. What are we looking for? What is the basic problem here?

---

### Post by Kajaste on 2008-08-03
If the tricks in last edit don't work you should try to find some information specific to your Atheros chip and MadWifi (and Ubuntu).

---

### Post by Pete89 on 2008-08-03
Its doing the same thing.... the script hangs on *Loading kernel module...*

Could you explain what my basic problem is? I would appreciate it very much.

Pete

---

### Post by Kajaste on 2008-08-03
If I knew the exact problem I would have already told it =) I'm sure you can find the problem and the answer with a little time.

---

### Post by rfincher on 2008-08-06
[QUOTE=Kajaste;4985931]**Latest news: **
21st July 2008 - New version 0.9.7. New option --info and some hardware checking.5th June 2008 - New version 0.9.6. **[COLOR="Red"]SVN update check was broken[/COLOR]**, is working now. Sorry.

Hello Kaja,
I'm very new at this Ubuntu game,but persistent! My Compaq C731TU laptop dual boots Vista and U804. After installing the Madwifi r3366 driver for the Atheros wireless device in the laptop, all ran well until recently when for no apparent reason wireless access between the compaq and my router ceased. Also the whole U system seemed to have become a bit flaky, so I reinstalled the OS. However still no WLAN under U. BTW the system works perfectly under Vista.I found your post and followed your instructions, unfortunately without success. Here's the Terminal screenshot requested:

rob@compaqC731-laptop:~$ sudo ./madwifi.sh --info
Found at least one Atheros device.
Linux compaqC731-laptop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux
Distro: Debian
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 137b
	Flags: fast devsel, IRQ 22
	Memory at 91300000 (64-bit, non-prefetchable) [size=64K]

ath_pci               248760  0 
wlan                  235888  1 ath_pci
ath_hal               252512  1 ath_pci
wifi0: 0 ath0: 0
rob@compaqC731-laptop:~$ 
 
So do you have any suggestions on how I should proceed from here.
Rob
.

---

### Post by Kajaste on 2008-08-06
Maybe you should try using madwifi-hal or madwifi-ng or an older version of "trunk" (the normal version). The --info output seems that the driver doesn't work at the moment.

---

### Post by rfincher on 2008-08-06
Thanks Kaja,
I've tried using the madwifi-ng-r3366+ar5007.tar.gz "patch" again but without success. This was the patch I originally used before having to reload 8.04. Clearly the AR5007 is not now being seen by Network Manager. Only "Wired Connection" and "POint to point Connection" appear on its menu. Well I'll keep trying, and will firstly download the later kernel 2.6.24-19 generic which supposedly has the atheros drivers included as part of it. Thanks for your interest and a great post - even if they haven't solved my problem, they've given me quite a few insights into this problem.
Rob

---

### Post by johneddiekerr on 2008-08-27
Hello

Thank you, this is great. I just have one problem. Hardy will not save my settings after the install. I shut down, reboot, and I have to run 
sudo ./madwifi.sh --working  and then reconfigure the card.

At least I know the wireless card D-Link wda-2320 will work.

Has anyone a solution to the settings not saving?

Kindest regards, 

John Eddie Kerr
Guelph, Ontario Canada

---

### Post by era506 on 2008-08-30
You're a genius!!! I love you!! Thank so much for this!!! It works great on Compaq Presario C762NR with "Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)" using "madwifi-hal-0.10.5.6-r3835-20080801.tar.gz" tarball.

---

### Post by OrangeCrush112 on 2008-08-30
Having trouble installing this. Whenever I run the sudo script, it gives me a subversion error,
"Installing subversion...E:couldn't find subversion.

---

### Post by mephala on 2008-09-01
K, so I tried to install using this script and this is the message that came up (sry for the newb question, pls help!):


Found at least one Atheros device.
Linux Mephala 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
Distro: Debian
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: AMBIT Microsystem Corp. Unknown device 0428
	Flags: fast devsel, IRQ 21
	Memory at f2200000 (64-bit, non-prefetchable) [size=64K]

ath_pci               248760  0 
wlan                  235376  1 ath_pci
ath_hal               252512  1 ath_pci
[ 1779.198687] ath_pci: driver unloaded
[ 1779.497920] ath_hal: driver unloaded
[ 1822.316656] ath_pci: HAL doesn't support MAC revision 0xffffffff
[ 2241.691603] ath_pci: HAL doesn't support MAC revision 0xffffffff
[   34.403442] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   34.571749] ath_pci: 0.9.4
wifi0: 0 ath0: 0

---

### Post by MrPickle12481632 on 2008-09-11
I was having trouble getting the script to work due to the fact that my current computer has no ability to get a hard wire in, and I've been using ndiswrapper as a temporary workaround for my internet connection. It got me connected, but it was cutting out unexpectedly and I had to reload it to the modules after every restart.

In any case, when running the script, I was getting an error saying that the driver could not gain control of the chip. I'm not a coder [in fact this is my first successful attempt at programming anything!], but I managed to figure out the syntax of the .sh file to add in a few functions to remove the ndiswrapper modules AFTER the packages had been downloaded, but BEFORE the ath_pci module was loaded.

I have uploaded a copy of the modified script here for your revision. Let me know what you think and what can be further added to make this the end-all be-all madwifi install script!
:guitar:

---

### Post by Etirn on 2008-09-16
Im helping a friend install kubuntu on their new acer aspire one and cant get the wifi working, any help would be appreciated.

Here is a dump of madwifi.sh --info

Found at least one Atheros device.
Linux momo-chan 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
Distro: Debian
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Foxconn International, Inc. Unknown device e008
	Flags: fast devsel, IRQ 18
	Memory at 55200000 (64-bit, non-prefetchable) [size=64K]

ath_pci               248760  0 
wlan                  235376  1 ath_pci
ath_hal               252512  1 ath_pci
[   29.866250] ath_hal: module license 'Proprietary' taints kernel.
[   29.901902] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   30.301361] ath_pci: 0.9.4
[  577.005390] ath_pci: driver unloaded
[  577.439778] ath_hal: driver unloaded
[  678.831227] ath_pci: HAL doesn't support MAC revision 0xffffffff
wifi0: 0 ath0: 0

---

### Post by bpalyshka on 2008-09-16
Hello 

looks like I have a similer problem like the rest of the people posted here.  installed ok, and then recieved a error message


[PHP]Found at least one Atheros device.
Checking build dependencies...
...build dependencies OK
Running pre-install scripts...OK
Building MadWifi...OK
Installing MadWifi...OK
Loading kernel module...OK
It seems that the driver did not detect compatible hardware.
Please try to connect to an AP and post the output of
sudo ./madwifi.sh --info to the forum.
satan@Hell:~$ sudo ./madwifi.sh --info
Found at least one Atheros device.
Linux Hell 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux
Distro: Debian
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Askey Computer Corp. Unknown device 7128
	Flags: fast devsel, IRQ 18
	Memory at f8000000 (64-bit, non-prefetchable) [size=64K]

ath_pci               250048  0 
wlan                  253472  1 ath_pci
ath_hal               280320  1 ath_pci
[  273.840300] ath_hal: module license 'Proprietary' taints kernel.
[  273.858538] ath_pci: HAL doesn't support MAC revision 0xe2
wifi0: 0 ath0: 0
[/PHP]
 
Ubuntu recognized i had restricted drivers. then i checked System> Administration> Hardware drivers. I can see the drivers here and are enabled here and no wifi.

So i followed the steps outlined to install, and here we are.  Any thoughts or suggestions are welcome.  Just got ubuntu installed yesterday, dualboot XP and i can use wifi fine, but i love linux and cannot figure this out.

thanks

---

### Post by CapnChkn on 2008-09-21
I am having an entirely different problem with the install.  

I'm trying to install Ubuntu 8.04 with all the bits working on an Asus Eee PC 4G Surf (701).

I ran the script, got an error message, turned off the Anteros drivers, rebooted, and ran my Uname and Pword without problem.  When the system was fully operational, I started my Synergy and while typing in the IP, the numberpad keys that come in under the FN key at where you would usually find the "windows" key are active, and I can't turn them off!

In other words, when I try to use the numbers at the top of the keyboard to type my IP address, I get the "/" character instead of "0."  You can imagine what kind of hassle it is when I'm trying to type my username and password for a SUDO.  I have no problems with an external keyboard.

Does anybody have a fix, or failing that, an uninstall for the above mentioned MadWiFi script?

Cap'n!

---

### Post by Kajaste on 2008-09-21
I have been absent for a while. Anyway, if the driver doesn't work, try another version of it. The script doesn't install anything extra, it does just what you would do if you followed the madwifi installation guide. It just does it automagically.

I'm sorry I have not included (and will not include) an uninstall option. 

There have been other Atheros WiFi drivers released lately (ath9k, ath5k). They will replace MadWifi anytime soon so putting effort on this script doesn't seem reasonable. If it works for you, it's just great. If it doesn't, I'm sorry. Feel free to modify it for your needs. Do what you want with it.

---

### Post by CapnChkn on 2008-09-21
I had this problem before with the last install of same.  I didn't use your script though.  It doesn't have anything to do with your script, it's the MadWiFi.  I've been fooling with this stuff on and off for a while, so I know just enough to be dangerous with the Linux...

Not to worry Kajaste, it's worked for many people, thank you.  I'm the worlds smartest man who, psychotically, keeps leaping out of the plane with a backpack...

Cap'n!

---

### Post by kisha2 on 2008-09-26
Hello

Thank you so much. In order to your script is my wireless working, but I just have one problem. Hardy will not save my settings after the install. I shut down, reboot, and I have to run
sudo ./madwifi.sh --working and then reconfigure the card.

could somebody help with this? Thanks a lot.

---

### Post by Kajaste on 2008-09-26
> **kisha2 said:**
> Hello

Thank you so much. In order to your script is my wireless working, but I just have one problem. Hardy will not save my settings after the install. I shut down, reboot, and I have to run
sudo ./madwifi.sh --working and then reconfigure the card.

could somebody help with this? Thanks a lot.
After booting try ```
sudo modprobe ath_pci
``` 

If it works, do
```
sudo -s
echo ath_pci >> /etc/modules
```
and Ubuntu will load the module for you automatically at boot.

---

### Post by jpete on 2008-09-30
> **Kajaste said:**
> After booting try ```
sudo modprobe ath_pci
``` 

If it works, do
```
sudo -s
echo ath_pci >> /etc/modules
```
and Ubuntu will load the module for you automatically at boot.

How do you reverse the last code?

I did it and now I get 

> No command arguments supplied!
Usage: kdesudo [-u <runas>] <command>
KdeSudo will now exit...

---

### Post by dougscudder.com on 2008-09-30
When I run the script to install the driver i get this error message:

./madwifi.sh: 2: Syntax error: newline unexpected

Can anyone help?

---

### Post by KaOS-bEat on 2008-10-03
I'm on 64bit ubuntu 8.04 on a lenovo thinkpad SL400. If i define [**this**]("http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3861-20080903.tar.gz") tarball as described in ./madwifi.sh --help It works perfectly!

thanks


> kaos@kaospad:~$ sudo ./madwifi.sh --info
[sudo] password for kaos: 
Found at least one Atheros device.
Linux kaospad 2.6.24-22-generic #1 SMP Mon Sep 29 20:39:44 UTC 2008 x86_64 GNU/Linux
Distro: Debian
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Atheros Communications Inc. Unknown device 0035
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fd6f0000 (64-bit, non-prefetchable) [size=64K]

ath_rate_sample        17152  1 
ath_pci               250304  0 
wlan                  254368  5 wlan_wep,wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               333200  3 ath_rate_sample,ath_pci
[  132.118300] ath_hal: module license 'Proprietary' taints kernel.
[  132.543679] ath_pci: HAL doesn't support MAC revision 0xe2
[  321.309440] MadWifi: ath_attach: Switching rfkill capability off.
[  321.340511] ath_pci: wifi0: Atheros 5424/2424: mem=0xfd6f0000, irq=17
[  321.322478] wifi0: Atheros AR2425 chip found (MAC 14.2, PHY SChip 7.0, Radio 10.2)
[  321.340511] ath_pci: wifi0: Atheros 5424/2424: mem=0xfd6f0000, irq=17
wifi0: 8 ath0: 9


---

### Post by andre.kappes on 2008-10-04
Hello!

Thank you for your script! Unfortunately, I have some trouble running it. Here is the output of --info . Maybe you know what is going wrong?

Best,

André


```
Found at least one Atheros device.
Linux andre-laptop 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux
Distro: Debian
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: AMBIT Microsystem Corp. Unknown device 0428
	Flags: fast devsel, IRQ 19
	Memory at f0400000 (64-bit, non-prefetchable) [size=64K]

ath_pci               251072  0 
wlan                  253472  1 ath_pci
ath_hal               280320  1 ath_pci
[  203.499977] ath_pci: HAL doesn't support MAC revision 0xe2
wifi0: 0 ath0: 0

```

---

### Post by Kajaste on 2008-10-04
> **andre.kappes said:**
> Hello!

Thank you for your script! Unfortunately, I have some trouble running it. Here is the output of --info . Maybe you know what is going wrong?

Best,

André


```
Found at least one Atheros device.
Linux andre-laptop 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux
Distro: Debian
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: AMBIT Microsystem Corp. Unknown device 0428
	Flags: fast devsel, IRQ 19
	Memory at f0400000 (64-bit, non-prefetchable) [size=64K]

ath_pci               251072  0 
wlan                  253472  1 ath_pci
ath_hal               280320  1 ath_pci
[  203.499977] ath_pci: HAL doesn't support MAC revision 0xe2
wifi0: 0 ath0: 0

```

It seems that the version of MadWifi you are using does not support your hardware. Try using the other versions. The above post might give you some answers.

---

### Post by N00bB00b on 2008-10-04
No Joy.

Atheros radio.

Acer Aspire 3680
HH (8.04.1?)

I've tried turning the radio on with the machine already started, after Grub but before the Ubuntu splash, but we're not working yet.

In the Network administration panel, there is no mention of the radio, just the modem and the cat-5 card.

Here's the output
```

Found at least one Atheros device.
Checking build dependencies..No packages found matching linux-headers-2.6.24-19-386.
.
No packages found matching subversion.
Installing subversion...Selecting previously deselected package libapr1.
(Reading database ... 107115 files and directories currently installed.)
Unpacking libapr1 (from .../libapr1_1.2.11-1_i386.deb) ...
Selecting previously deselected package libaprutil1.
Unpacking libaprutil1 (from .../libaprutil1_1.2.12+dfsg-3_i386.deb) ...
Selecting previously deselected package libsvn1.
Unpacking libsvn1 (from .../libsvn1_1.4.6dfsg1-2ubuntu1_i386.deb) ...
Selecting previously deselected package subversion.
Unpacking subversion (from .../subversion_1.4.6dfsg1-2ubuntu1_i386.deb) ...
Setting up libapr1 (1.2.11-1) ...

Setting up libaprutil1 (1.2.12+dfsg-3) ...

Setting up libsvn1 (1.4.6dfsg1-2ubuntu1) ...

Setting up subversion (1.4.6dfsg1-2ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
OK
Installing linux-headers...Selecting previously deselected package linux-headers-2.6.24-19-386.
(Reading database ... 107189 files and directories currently installed.)
Unpacking linux-headers-2.6.24-19-386 (from .../linux-headers-2.6.24-19-386_2.6.24-19.41_i386.deb) ...
Setting up linux-headers-2.6.24-19-386 (2.6.24-19.41) ...

OK
Installing libc6-dev...Selecting previously deselected package linux-libc-dev.
(Reading database ... 112433 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.24-19.41_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.7-10ubuntu4_i386.deb) ...
Setting up linux-libc-dev (2.6.24-19.41) ...
Setting up libc6-dev (2.7-10ubuntu4) ...
OK
...build dependencies OK
Fetching sources from SVN...OK
Running pre-install scripts...OK
Building MadWifi...OK
Installing MadWifi...OK
Loading kernel module...OK
It seems that the driver did not detect compatible hardware.
Please try to connect to an AP and post the output of
sudo ./madwifi.sh --info to the forum.

```

---

### Post by arcus j on 2008-10-05
*well... i wish i didnt need to post, but here i am after diligently following this thread all the way i have still got nothing. *

[I]i started with a clean install of ubuntu hardy, bumped up to the latest updates on a (what i now believe to be pure evil) compaq presario c700 laptop.
[/I]

*first up a check of my chipset:*

franky@franky-laptop:~$ sudo lshw -C network
PCI (sysfs)  
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  
franky@franky-laptop:~$ 


*next a ran thru with the basic script (never know, mighta worked straight up ;) )*

*all seemed fine untill:*

...build dependencies OK
Unrolling tarball version ng-r2756+ar5007...OK
Running pre-install scripts../madwifi.sh: line 253: cd: scripts: No such file or directory
franky@franky-laptop:~$

*hmmm problem. didnt make it to install *

*i tryd a manual D/L using the NG version first (which was not compatible but at least got me past the install) then finding that the HAL set should be good for me:*
 
madwifi-hal-0.10.5.6-r3772-20080716.tar.gz

Found at least one Atheros device.
Checking build dependencies...
...build dependencies OK
Unrolling tarball version hal-0.10.5.6-r3772-20080716...OK
Running pre-install scripts...OK
Building MadWifi...OK
Installing MadWifi...OK
Loading kernel module...OK
It seems that the driver did not detect compatible hardware.
Please try to connect to an AP and post the output of
sudo ./madwifi.sh --info to the forum.

*also not compatible! someone was yelling about a specific version that worked for his AR242x (r3835-20080801)so i tried that too, with no progress. heres the current info*

Found at least one Atheros device.
Linux franky-laptop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
Distro: Debian
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
    Subsystem: Hewlett-Packard Company Unknown device 137b
    Flags: fast devsel, IRQ 22
    Memory at 91300000 (64-bit, non-prefetchable) [size=64K]

ath_pci               249016  0
wlan                  236144  1 ath_pci
ath_hal               305376  1 ath_pci
[  216.278177] ath_pci: driver unloaded
[  216.438908] ath_hal: driver unloaded
[   40.177126] ath_hal: module license 'Proprietary' taints kernel.
[   40.241689] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   40.400297] ath_pci: 0.9.4
wifi0: 0 ath0: 0


*my network manager wasnt giving me any options other then wired connections so i restarted with the ethernet unplugged to give it a kick, and it at least gave me the option of trying to connect, but still no wireless. i seem to have run out of options at this point. does that propreitary taint comment mean very much? i ran across some posts saying to blacklist the win drivers, but it was not about my AR242x set so i didnt fiddle with it. any more tips on what to try next would be greatly appreciated, a lappy without wireless net is a tragic beast indeed!  Thanks for reading ;)*

---

### Post by jmd9qs on 2008-10-05
having the exact same problem as the guy above(i'm pretty sure i have all the same settings... at least its the same exact laptop).... please help!

---

### Post by shibbz on 2008-10-14
Heya, ran into this problem on Hardy... Fresh install with all updates.  any of you have an idea?
Trying to install AR5413

Also, the following drivers are in use.

[[IMG]http://img362.imageshack.us/img362/1534/sson2.th.png[/IMG]](http://img362.imageshack.us/my.php?image=sson2.png)[[IMG]http://img362.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

**(sudo ./madwifi.sh output)**

```
It seems that the driver did not detect compatible hardware.
Please try to connect to an AP and post the output of
sudo ./madwifi.sh --info to the forum.
```

**(sudo ./madwifi.sh --info output)**

```
Found at least one Atheros device.
Linux lol 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux
Distro: Debian
05:01.0 Ethernet controller: Atheros Communications Inc. AR5413 802.11abg NIC (rev 01)
	Subsystem: Lite-On Communications Inc Unknown device 5001
	Flags: medium devsel, IRQ 17
	Memory at febf0000 (32-bit, non-prefetchable) [size=64K]

ath_pci               249912  0 
wlan                  235376  1 ath_pci
ath_hal               252512  1 ath_pci
[  282.435341] ath_pci: driver unloaded
[  282.575464] ath_hal: driver unloaded
[   33.801244] ath_hal: module license 'Proprietary' taints kernel.
[   33.801737] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   34.164503] ath_pci: 0.9.4
wifi0: 0 ath0: 0

```

**(sudo lspci | grep Ethernet output)**

```
02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
05:01.0 Ethernet controller: Atheros Communications Inc. AR5413 802.11abg NIC (rev 01)
```


Any help would be great!

---

### Post by carcar1 on 2008-10-14
Guys and girls using linux mint which is based off of ubuntu with a differetn ui and soem java flash etc installed and a graphical ndiswrapper which all you have to do is download the net5211.ini and the otehr files pop it in with the restricted drivers off and bam wireless with the ar5007eg but shoudl work with other cards.  Check it out!

[Here]("http://www.linuxmint.com/")

---

### Post by shibbz on 2008-10-14
> **carcar1 said:**
> Guys and girls using linux mint which is based off of ubuntu with a differetn ui and soem java flash etc installed and a graphical ndiswrapper which all you have to do is download the net5211.ini and the otehr files pop it in with the restricted drivers off and bam wireless with the ar5007eg but shoudl work with other cards.  Check it out!

[Here]("http://www.linuxmint.com/")

Yeah, but you lose a lot of functionality.

Ndiswrapper does not support monitor mode. That's what I'm after.

---

### Post by MrGreen on 2008-10-14
```
Found at least one Atheros device.
Linux mrgreen-laptop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
Distro: Debian
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: AMBIT Microsystem Corp. Unknown device 0428
	Flags: fast devsel, IRQ 19
	Memory at 54100000 (64-bit, non-prefetchable) [size=64K]

ath_pci               249912  0 
wlan                  235376  1 ath_pci
ath_hal               252512  1 ath_pci
[  214.126716] ath_hal: module license 'Proprietary' taints kernel.
[  214.163755] ath_pci: HAL doesn't support MAC revision 0xe2
wifi0: 0 ath0: 0

```

output from madwifi.sh --info .... failed to install drivers ...

Any ideas?

---

### Post by sab0tage on 2008-10-15
Macbook 2,1 Ubuntu Hardy - worked like a charm! Thanks so much!

---

### Post by Kajaste on 2008-10-15
> **MrGreen said:**
> ```
Found at least one Atheros device.
Linux mrgreen-laptop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
Distro: Debian
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: AMBIT Microsystem Corp. Unknown device 0428
	Flags: fast devsel, IRQ 19
	Memory at 54100000 (64-bit, non-prefetchable) [size=64K]

ath_pci               249912  0 
wlan                  235376  1 ath_pci
ath_hal               252512  1 ath_pci
[  214.126716] ath_hal: module license 'Proprietary' taints kernel.
[  214.163755] ath_pci: HAL doesn't support MAC revision 0xe2
wifi0: 0 ath0: 0

```

output from madwifi.sh --info .... failed to install drivers ...

Any ideas?

That means the driver was installed successfully but doesn't support your hardware. You might want to try other versions of MadWifi or even the newer ath5k and ath9k drivers.

---

### Post by MrGreen on 2008-10-15
Ok will try those thanks

---

### Post by DrCoolSanta on 2008-10-19
ath5k works for these.
I was so happy when I fixed my Atheros 5007EG. I had just bought myself an Acer Aspire One, the very small one (8in something)
All you need to do is, get compat-wireless from [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download) (The old one works for Ubuntu Hardy).
Now open terminal and
lsmod | grep ath
and sudo rmmod all those that are listed
then get rid of ndiswrapper if you have it aswell, if you don need it get it out from synaptec or simply remove your driver from ndiswrapper.
Finally in compat-wireless folder (extract the tarball)
make
sudo make install

Now restart, then click on the internet icon shown in the top bar and it displays all the wireless connections near you. Select the one you want and you are good to go.

I am so damn happy now.

---

### Post by velayo on 2008-10-20
Just wanted to thank you for your work!! I couldn't get linksys wmp-110 to work with ndiswrapper on ubuntu hardy.  Tried your script and it worked flawlessly. The only problem was that the card wouldn't be turned on by default on restart but found a fix on a latter post that you made.  Thanks, I'm a happy camper with my ubuntu rig!!! :KS

---

### Post by darklordveynom on 2008-10-20
Glorious! Thank you!!

---

### Post by era506 on 2008-10-20
Again thank you!!! It worked with HP Pavillion DV6700 and hal version of the driver, just had to add the ath_pci module to /etc/modules becuase ubuntu wasn't loading it at start up, after that everything worked just great!! Even the blue light is working!!

---

### Post by pasencorelui on 2008-11-02
madwifi.org is unreachable. is there another wau to get madwifi-hal-0.10.5.6 ? Is someone can share or indicate a mirror to get it?

Thank's

---

### Post by webdevmydnac on 2008-11-02
> madwifi.org is unreachable. is there another wau to get madwifi-hal-0.10.5.6 ? Is someone can share or indicate a mirror to get it?

Thank's 

Anyone have a copy of the files?

---

### Post by matheist76 on 2008-11-04
Thanks a heaps for the script. Wow the wireless works better than it ever has done before. I've got a Macbook pro and an 3G connection. It's so sweet. :guitar:

---

### Post by rodrigobad on 2008-11-20
doesnt work for me :( 
notebook LG E500
```
~$ sudo ./madwifi.sh --info
Found at least one Atheros device.
Linux whiplash 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686 GNU/Linux
Distro: Debian
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Unknown device 1a3b:1026
	Flags: fast devsel, IRQ 18
	Memory at feaf0000 (64-bit, non-prefetchable) [size=64K]

ath_pci               248376  0 
wlan                  235504  1 ath_pci
ath_hal               252512  1 ath_pci
[  149.140940] ath_hal: module license 'Proprietary' taints kernel.
[  149.276069] ath_pci: HAL doesn't support MAC revision 0xe2
[  489.631727] ath_pci: HAL doesn't support MAC revision 0xe2
wifi0: 0 ath0: 0
```
some think?:(:confused:

---

### Post by tadees on 2008-11-29
> **Kajaste said:**
> Nice to hear it's working now :)

Thanks Kajaste for your time in helping the community. Much appreciated! \\:D/

---

### Post by quanumphaze on 2008-12-02
Good news, the HAL has been opened up [[LINK]("http://madwifi-project.org/wiki/news/20081129/sam-leffler-releases-hal-source")]

This hopefully means that eventually all the older cards will be supported by the ath5k driver (or similar).

So far the stock Madwifi in 8.10 are working fine, only needing a kick in the butt sometimes after suspend. I'll find out if it still crashes using EAP

---

### Post by N00bB00b on 2008-12-02
Don't hold your breath.  On my Acre Aspire 3680 with Intrepid it still doesn't work - I can't even make it.  The MadWiFi forums have been no help, either.

---

### Post by spaarks on 2008-12-02
Is there any way this can be used with Ubuntu live CD? I have a new Toshiba using the Atheros 5007 wireless card.

---

### Post by hipogrito on 2008-12-07
Hello,

Thanks for the script.

I am another case of 

[ 2697.539305] ath_pci: HAL doesn't support MAC revision 0xe2


You have commented that either we try to use another version of madwifi, or we try to use ath5 or ath9.

Regarding this last option, could somebody give us a quick guide of how to use ath5 or ath9? How do I install those drivers? How do I use them?

Thanks,
Regards,
Hipo

---

### Post by morbidous on 2008-12-14
Hey, guys. My girlfriend bought a notebook last week and since then we're trying to figure out a way to make her wireless card work properly. The wireless Atheros driver that came with Intrepid didn't work so I tried to use a backported one. To my surprise, it kind of worked, she was able to use the connection for about three hours but suddenly the connection stopped to work and since then she can't use it anymore.

The driver that HAL suggested is listed in Jockey as being "Atheros 802.11 wireless LAN cards" and the one that worked for a while is "Support for 5xxx series of Atheros 802.11 wireless LAN cards".

Searching on Google i found this topic and followed the instructions on the first post but, unfortunately, was not able to get her wireless card working. Here is the output I get when running sudo ./madwifi.sh --info :

```

Linux camila-daninho 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux
Distro: Debian
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Device 1a32:0105
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f0200000 (64-bit, non-prefetchable) [size=64K]
	Kernel driver in use: ath5k_pci
	Kernel modules: ath5k, ath_pci

ath_pci               218296  0 
wlan                  239984  1 ath_pci
ath_hal               259552  1 ath_pci
[ 1483.909521] ath_hal: module license 'Proprietary' taints kernel.
wifi0: 0 ath0: 0

```

Any ideas of what might be causing the problem? Using the FOSS drivers might help us? If yes, how can I install it?

---

### Post by ~Phoenix~ on 2008-12-16
Hello guys i tried the tutorial in the first page but i still have problems.the output of sudo ./madwifi.sh --info is this:

Found at least one Atheros device.
Linux phoenix-laptop 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux
Distro: Debian
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Device 137b
	Flags: fast devsel, IRQ 16
	Memory at f2000000 (64-bit, non-prefetchable) [size=64K]
	Kernel modules: ath_pci

ath_pci               218296  0 
wlan                  239984  1 ath_pci
ath_hal               259552  1 ath_pci
[   37.383832] ath_hal: module license 'Proprietary' taints kernel.
[   37.421657] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   37.619930] ath_pci: 0.9.4
[   37.620718] ath_pci 0000:03:00.0: PCI INT A -> Link[LK1E] -> GSI 16 (level, low) -> IRQ 16
[   37.620726] ath_pci 0000:03:00.0: setting latency timer to 64
[   37.646775] ath_pci 0000:03:00.0: PCI INT A disabled
[  468.691814] ath_pci: driver unloaded
[  469.342957] ath_hal: driver unloaded
[  519.245116] ath_pci 0000:03:00.0: enabling device (0000 -> 0002)
[  519.245133] ath_pci 0000:03:00.0: PCI INT A -> Link[LK1E] -> GSI 16 (level, low) -> IRQ 16
[  519.245147] ath_pci 0000:03:00.0: setting latency timer to 64
[  519.245161] ath_pci: HAL doesn't support MAC revision 0xffffffff
[  519.245173] ath_pci 0000:03:00.0: PCI INT A disabled
wifi0: 0 ath0: 0

if i understand correct the Atheros wireless card is found but it can't find the correct driver.Can Anyone help me with that?

Thanx in advance :)

---

### Post by Manty01Actual on 2008-12-17
Here's the data, but first an explanation.  I got an update earlier that bombed ath5k out and I have not been able to fix it even with a total reinstall of the OS.  Must be missing something from here.  Anyway, the problem now is that when I do the update and install the backports and try to activate the driver in the drivers field, it auto deactivates when I activate it.  This is the most glaring thing, as when I did it before, I was able to turn on both driver fields and experience 4 blissful days of wireless happiness.  Now the other part, Wireless Networks is still in the network manager field, it's just greyed out, and when I try and connect via the Connect to Hidden Network field, I input all of the data required, and it too tries then auto disco's.  Here's iwconfig:

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

I know we can do this people, I did it the other day and blew Vista right out the airlock, so I will suffer the fate of Cat6 corded troglodyte technology for a few more days...............[-o<

---

### Post by mocha on 2009-01-01
This is an awesome script to download and compile and load the latest SVN version of the atheros ath_pci module.  Thank you very much!  I love Ubuntu but sometimes the devs put a junky version of some software or modules into the releases.  They did this with the Intrepid version of ath_pci, which was causing hard locks of my machine.  This script made it very easy to upgrade to SVN version and correct these issues.  Thanks again!!!

---

### Post by bejinx on 2009-01-10
Thank you thank you!

8.10 did not work well on my hp pavillion dv6000 (amd, nvidia, atheros 5007eg) laptop.  Since im no guru I re-insatlled 8.04 and totally forgot how I even got the wifi working back then.  I ran across this thread, and the hal tarball worked for me.  

Thank you so much for your efforts.

---

### Post by atzounis on 2009-01-20
Hello and BRAVO for your script!
I have this problem:
I have run the script everything seems to be OK
But since i have upgraded to latest kernel Network Manager is unable to manage my wireless networks. 

wlan0
disalbed

ath0
disabled

I am using KUBUNTU 8.10
And i have both D-link pcmcia atheros card and intel Pro wirelles card on board.

Any ideas?
I am novice user... :(

A.

---

### Post by bluntknife on 2009-01-21
atzounis - Have you re-run the script since updating the Kernel?

---

### Post by JayD239 on 2009-01-27
> **era506 said:**
> Again thank you!!! It worked with HP Pavillion DV6700 and hal version of the driver, just had to add the ath_pci module to /etc/modules becuase ubuntu wasn't loading it at start up, after that everything worked just great!! Even the blue light is working!!
Hi, does this include the button itself? I have a HP (CQ60) myself and trouble with the button.
I think my wireless card is detected and installed nicely out-of-the-box, but the wifi-toggle button itself is just not working.

Some things that made me think things are all right
```
joost@optil-ding:~$ dmesg | grep ath
joost@optil-ding:~$ dmesg | grep ath
[   14.365870] ath_hal: module license 'Proprietary' taints kernel.
[   14.379891] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   14.470570] ath_pci: 0.9.4
[   14.471800] ath_pci 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.471812] ath_pci 0000:02:00.0: setting latency timer to 64
[   14.520325] ath_pci 0000:02:00.0: PCI INT A disabled
These last three lines seems like the card is detected

```
```
joost@optil-ding:~$ lspci | grep Ath
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
Yeah, i do have an Atheros
```
```
joost@optil-ding:/etc/modprobe.d$ lsmod | grep ath
ath_pci                99096  0 
wlan                  211952  1 ath_pci
ath_hal               198864  1 ath_pci
Modules seem up and running
```

But still
```
joost@optil-ding:/etc/modprobe.d$ dmesg | grep wif
[   14.520306] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
```

After pressing (and holding) the wifi button for a while this has not changed either
```

joost@optil-ding:~$ dmesg | tail
[   32.092833] NET: Registered protocol family 10
[   32.094127] lo: Disabled Privacy Extensions
[   72.129784] CPU0 attaching NULL sched-domain.
[   72.129805] CPU1 attaching NULL sched-domain.
[   72.132128] CPU0 attaching sched-domain:
[   72.132138]  domain 0: span 0-1 level MC
[   72.132143]   groups: 0 1
[   72.132154] CPU1 attaching sched-domain:
[   72.132158]  domain 0: span 0-1 level MC
[   72.132162]   groups: 1 0

```

I checked the script source but I don't see anything button related... Can anyone confirm things are working okay with the Atheros driver (System > Manage (or something) > Hardware drivers, only 1 and activated) based on this? Is there a command line command i could use to manually enable this card?

The button did work in vista, but not in windows 7 either. HP limited my bios like crazy so i can enable it there there, but i'd like to toggle it anyway. The reason i'm not that eager to try the madwifi is because i don't want to recompile every kernel, and out it principle. Things should just work right?

(Ow, and i'm on inteprid 2.6.27-9-generic)


Edit: Hmm, this sucks.
I found [this page]("https://wiki.edubuntu.org/LaptopTestingTeam/HotkeyResearch") but unfortunatly, my wifi button does not send any messages to Ubuntu. Not to the gnome keybinder, nor in showkey, not in acpid (i have no /var/log/acpid) and xev does not show anything when pressing the button. Can anyone pinch me, maybe i dreamed having a wifi switch?

ReEdit: This is odd, the touchpad also has an en/disable button, but that works like a charm... Also does not process anything on xev

ReReEdit: Now I am quite sure I'm missing something in Ubuntu (and W7). I restored my vista (cp /media/windir/windows.old/* /media/windir, surprisingly it worked (somewhat)) and the button works like a charm (only a delay of 1 second in led color). I tried looking for the command the button sends to Windows but im just as stuck as [this guys]("http://ubuntuforums.org/showthread.php?t=861233") asking for a xev windows alternative (i'm scared of windows keyloggers).

ReReReEdit (maybe next time i'll wait before posting)
It has nothing to do with the HP Wireless Assistant. Even with that uninstalled the button works under windows. 

Re(x4)Edit (No i didn't)
```

joost@optil-ding:~$ sudo lshw 
...
      *-pci:1
      ...
           *-network UNCLAIMED
                description: Ethernet controller
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix cap_list
                configuration: latency=0

```
What is this UNCLAIMED thing? Maybe things are not so -it's only the button- as i thought. Might try the script after all tommorow

Re(5)Edit (this definitely is the craziest post i ever made)
Reinstalled vista (brrr) (coping system files does corrupt a lot). Button doesn't work out-of-the-box after all. After driver installation it does. So it sure is driver related. Although unsure if madwifi supports the button i'll try when i'm done playing games on windows (WINE is nice but lacks fps). I'll start a new post on my findings ;)

---

### Post by JayD239 on 2009-01-29
Nooooooo

```

....
Installing MadWifi...OK
Loading kernel module...OK
Adding ath_pci to /etc/modules...OK
It seems that the driver did not detect compatible hardware.
Please try to connect to an AP and post the output of
sudo ./madwifi.sh --info to the forum.
joost@optil-ding:~$ sudo ./madwifi.sh --info
Found at least one Atheros device.
Linux optil-ding 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux
Distro: Debian
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Device 137a
	Flags: fast devsel, IRQ 17
	Memory at 92600000 (64-bit, non-prefetchable) [size=64K]
	Kernel modules: ath_pci

ath_pci               218552  0 
wlan                  239984  1 ath_pci
ath_hal               259552  1 ath_pci
[   13.707515] ath_hal: module license 'Proprietary' taints kernel.
[   13.711631] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   13.729911] ath_pci: 0.9.4
[   13.729957] ath_pci 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.729970] ath_pci 0000:02:00.0: setting latency timer to 64
[   13.778265] ath_pci 0000:02:00.0: PCI INT A disabled
[ 1537.569789] ath_pci: driver unloaded
[ 1537.919310] ath_hal: driver unloaded
[ 1574.412941] ath_pci 0000:02:00.0: enabling device (0000 -> 0002)
[ 1574.412954] ath_pci 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 1574.412971] ath_pci 0000:02:00.0: setting latency timer to 64
[ 1574.412989] ath_pci: HAL doesn't support MAC revision 0xffffffff
[ 1574.413014] ath_pci 0000:02:00.0: PCI INT A disabled
wifi0: 0 ath0: 0

```

Ow, and there is a tiny little error in the script. svn.madwifi.org does not exist (anymore, I guess). This should be svn.madwifi-project.org. You will need to change this on line 213.

So, this doesn't work. So I tried the NG tarball but ran into another error.

```

joost@optil-ding:~$ sudo sudo ./madwifi.sh --tarball madwifi-ng-r3366+ar5007.tar.gz
Found at least one Atheros device.
Checking build dependencies...
...build dependencies OK
Unrolling tarball version ng-r3366+ar5007...OK
Removing previous MadWifi installations../madwifi.sh: line 260: cd: scripts: Bestand of map bestaat niet (File or folder does not exist, in Dutch)
```

I tried running the script from 
~/madwifi-0.9.4/# ../madwifi.sh --tarball ../tarbalfile.tar
and
cp ~/madwifi.sh ~/madwifi-0.9.4/
~/madwifi-0.9.4/# ../madwifi.sh --tarball ../tarbalfile.tar
But they didn't work.
Hardcoding ~/madwifi-0.9.4/scripts on line 260 of the script did work but still ends in error (NG and HAL both end up in similar errors

```

joost@optil-ding:~$ sudo ./madwifi.sh --tarball madwifi-ng-r3366+ar5007.tar.gz 
Found at least one Atheros device.
Checking build dependencies...
...build dependencies OK
Unrolling tarball version ng-r3366+ar5007...OK
Removing previous MadWifi installations...OK
Building MadWifi..athstats.c: In function 'main':
athstats.c:285: warning: format not a string literal and no format arguments
athstats.c:287: warning: format not a string literal and no format arguments
athstats.c:307: warning: format not a string literal and no format arguments
athstats.c:309: warning: format not a string literal and no format arguments
athstats.c:344: warning: format not a string literal and no format arguments
80211stats.c: In function 'main':
80211stats.c:290: warning: format not a string literal and no format arguments
wlanconfig.c: In function 'if_find_unit':
wlanconfig.c:297: warning: ignoring return value of 'fgets', declared with attribute warn_unused_result
wlanconfig.c: In function 'list_keys':
wlanconfig.c:830: warning: ignoring return value of 'system', declared with attribute warn_unused_result
wlanconfig.c: In function 'ieee80211_status':
wlanconfig.c:946: warning: ignoring return value of 'system', declared with attribute warn_unused_result
ath_info.c: In function 'main':
ath_info.c:1041: warning: ignoring return value of 'fwrite', declared with attribute warn_unused_result
/home/joost/madwifi-0.9.4/net80211/ieee80211_power.c: In function 'ieee80211_pwrsave':
/home/joost/madwifi-0.9.4/net80211/ieee80211_power.c:240: error: implicit declaration of function '__skb_append'
make[3]: *** [/home/joost/madwifi-0.9.4/net80211/ieee80211_power.o] Error 1
make[3]: *** Waiting for unfinished jobs....
make[2]: *** [/home/joost/madwifi-0.9.4/net80211] Error 2
make[1]: *** [_module_/home/joost/madwifi-0.9.4] Error 2
make: *** [modules] Fout 2

```


The new kernel (2.6.27-11-generic) doesn't change a thing

---

### Post by Robster2 on 2009-01-29
Did not work for me.

Resolving kolmoskone.homelinux.org... 81.175.201.149
Connecting to kolmoskone.homelinux.org|81.175.201.149|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8,804 (8.6K) [text/x-sh]

100%[====================================>] 8,804         11.48K/s             

00:04:07 (11.45 KB/s) - `madwifi.sh' saved [8804/8804]

rob@rob-laptop:~$ chmod +x madwifi.sh
rob@rob-laptop:~$ sudo ./madwifi.sh
[sudo] password for rob: 
Found at least one Atheros device.
Checking build dependencies...
...build dependencies OK
Fetching sources from SVN...svn: PROPFIND request failed on '/madwifi/trunk'
svn: PROPFIND of '/madwifi/trunk': Could not resolve hostname `svn.madwifi.org': No address associated with hostname ([http://svn.madwifi.org](http://svn.madwifi.org))
:(

---

### Post by JayD239 on 2009-01-30
> **Robster2 said:**
> Did not work for me.

Resolving kolmoskone.homelinux.org... 81.175.201.149
Connecting to kolmoskone.homelinux.org|81.175.201.149|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8,804 (8.6K) [text/x-sh]

100%[====================================>] 8,804         11.48K/s             

00:04:07 (11.45 KB/s) - `madwifi.sh' saved [8804/8804]

rob@rob-laptop:~$ chmod +x madwifi.sh
rob@rob-laptop:~$ sudo ./madwifi.sh
[sudo] password for rob: 
Found at least one Atheros device.
Checking build dependencies...
...build dependencies OK
Fetching sources from SVN...svn: PROPFIND request failed on '/madwifi/trunk'
svn: PROPFIND of '/madwifi/trunk': Could not resolve hostname `svn.madwifi.org': No address associated with hostname ([http://svn.madwifi.org](http://svn.madwifi.org))
:(

Open the madwifi.sh with a texteditor. Scroll down to line 213. In that line change svn.madwifi.org to svn.madwifi-project.org. That should fix the hostname error.

---

### Post by kissber on 2009-02-01
Hello, the script won't work here.

here is my result for --info

```
administrateur@Master:~$ sudo ./madwifi.sh --info
Found at least one Atheros device.
Linux Master 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
Distro: Debian
03:00.0 Network controller: Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter (rev 01)
	Subsystem: Atheros Communications Inc. Unknown device 0033
	Flags: fast devsel, IRQ 21
	Memory at df2f0000 (64-bit, non-prefetchable) [size=64K]

ath_pci               248248  0 
wlan                  235504  1 ath_pci
ath_hal               252512  1 ath_pci
[   31.063853] ath_hal: module license 'Proprietary' taints kernel.
[   31.862863] MadWifi: ath_getchannels: Unable to collect channel list from HAL; regdomain likely 98 country code 250
wifi0: 0 ath0: 0

```

any idea ?

---

### Post by PhoHammer on 2009-02-02
I'm having a problem:

powermite@Fallon:~$ wget [http://kolmoskone.homelinux.org/~kaja/kamaa/madwifi.sh](http://kolmoskone.homelinux.org/~kaja/kamaa/madwifi.sh) -O madwifi.sh
--21:23:20--  [http://kolmoskone.homelinux.org/~kaja/kamaa/madwifi.sh](http://kolmoskone.homelinux.org/~kaja/kamaa/madwifi.sh)
           => `madwifi.sh'
Resolving kolmoskone.homelinux.org... 81.175.201.149
Connecting to kolmoskone.homelinux.org|81.175.201.149|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8,804 (8.6K) [text/x-sh]

100%[====================================>] 8,804         21.12K/s             

21:23:22 (21.09 KB/s) - `madwifi.sh' saved [8804/8804]

powermite@Fallon:~$ sudo ./madwifi.sh
[sudo] password for powermite: 
sudo: ./madwifi.sh: command not found

Not sure what to do now. I'm having the hardest time getting my wireless working under xubuntu 8.04. I've tried many different things!

---

### Post by PhoHammer on 2009-02-02
I finally got mine working!! I had to google for a atheros driver for xp and found one [here]("http://www.driversdown.com/drivers/25860.shtml"). I then used ndiswrapper with this driver and the waters parted, revealing magical wireless networks all around me:D:D:D

---

### Post by us3rX on 2009-02-03
```
jer3my@jer3my-laptop:~$ sudo ./madwifi.sh --info
Found at least one Atheros device.
Linux jer3my-laptop 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux
Distro: Debian
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev ff) (prog-if ff)
	!!! Unknown header type 7f
	Kernel modules: ath_pci, ath5k

ath_pci               218552  0 
wlan                  239984  1 ath_pci
ath_hal               259552  1 ath_pci
[142285.775266] ath_hal: module license 'Proprietary' taints kernel.
[142285.833989] ath_pci 0000:06:00.0: PCI INT A -> Link[LNKC] -> GSI 10 (level, low) -> IRQ 10
[142285.834008] ath_pci 0000:06:00.0: setting latency timer to 64
[142285.863607] ath_pci 0000:06:00.0: PCI INT A disabled
wifi0: 0 ath0: 0
jer3my@jer3my-laptop:~$ 

```

Didnt work for me. =s

~us3rX:twisted:

---

### Post by JayD239 on 2009-02-03
I got it working by installing the madwifi hal by hand, instead of this script. I used [this walkthrough]("http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/") to do it.

The button does not seem to work yet, but i hope disabling wireless via the panel applet also saves my precious battery power.

---

### Post by fonsi2099 on 2009-02-14
> **Kajaste said:**
> **Latest news: **
21st October 2008 - 0.9.8.1: madwifi.sh now automatically adds ath_pci to /etc/modules to make Ubuntu load it automatically at boot. It also removes ath_pci from autoload when --uninstalling.
15th October 2008 - 0.9.8: By requests I added an --uninstall option. I didn't test it much so let's hope it works ;)
21st July 2008 - 0.9.7: New option --info and some hardware checking.
16th July 2008 - For AR5007 (AR252x in lspci, found at least on Asus EEE) on 32-bit you will need a special tarball of madwifi-ng or madwifi-hal that can be downloaded from [http://snapshots.madwifi-project.org/special/](http://snapshots.madwifi-project.org/special/). 64-bit users should check [this (ndiswrapper method) ]("http://blog.linuxoss.com/2008/05/08/ubuntu-804-enabling-atheros-ar5007-based-wireless/") or [this (madwifi-hal method)]("http://madwifi.org/ticket/1192") out.
5th June 2008 - 0.9.6: **[COLOR="Red"]SVN update check was broken[/COLOR]**, is working now. Sorry.
--
**The new open source [ath5k]("http://madwifi-project.org/wiki/About/ath5k") and [ath9k]("http://linuxwireless.org/en/users/Drivers/ath9k") drivers included in Ubuntu 8.10 Intrepid Ibex (should) replace MadWifi.** 
**When upgrading to 8.10** you might want to **--uninstall MadWifi first** to avoid conflicts with the new drivers. In 8.10 Atheros WiFi should work straight out-of-the-box.

At the moment ath9k is in rapid development and doesn't support AP mode yet. Some users might want to continue using the old MadWifi drivers.
--

**What is this script all about?**
I have been working on an installation script for [MadWifi]("http://madwifi-project.org/"), the best Atheros driver for Linux at the moment, that should work in Ubuntu, Debian and Fedora. I have been using it with my MacBook [AR5418] for some time and found it very useful.

**Do I need this script? Will it solve my WiFi problems?**
If you're in need of MadWifi, then this script should help you. Please note that MadWifi does not support any USB devices. To find out which cards are supported see [http://madwifi-project.org/wiki/Compatibility](http://madwifi-project.org/wiki/Compatibility).

**Okay, so how do I use this script to install MadWifi?**
Basically, if you have a working Internet connection (no worries if you don't, see below), all you need to do is download the script
```
wget http://kolmoskone.homelinux.org/~kaja/kamaa/madwifi.sh -O madwifi.sh
chmod +x madwifi.sh
```
(you can also upgrade your current madwifi.sh to the latest version with these commands)

And then run it with sudo
```
sudo ./madwifi.sh
```

**What is going to happen when I run the script?**
This will install the build dependencies, fetch the latest source code from MadWifi SVN, compile and install the module. After it completes you should be able to connect to an AP with Ubuntu's NetworkManager icon in the notification area. 8) (it might take up to about a minute to pick up a network)

**Is there anything I should do after installing?**
If it works well enough, do sudo ./madwifi.sh --save to save the working version of sources. If an update breaks the sources you can then do sudo ./madwifi.sh --working to use the saved sources.
You might want to see --help every once in a while to help you remind how the script works.

**How about kernel updates?**
Note that **you have to run the script after every kernel update!** For a reinstall you can also use sudo ./madwifi.sh --reinstall which doesn't fetch a new version of MadWifi but uses the one last installed.

**Installing without an Internet connection or using a source tarball (not fun)**
SVN code does not always compile succesfully and not all of us can access a wired connection to the Internet. That's why I have included a possibility to use a source tarball from madwifi.org. 

You need to put madwifi.sh, madwifi-VERSION.tar.gz (from [http://madwifi-project.org/](http://madwifi-project.org/) or [http://snapshots.madwifi-project.org/madwifi-trunk/](http://snapshots.madwifi-project.org/madwifi-trunk/)) and the following Ubuntu packages (from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)): make, gcc, libc6-dev, linux-headers-YOURKERNELVERSION on a removable media (CD, flash memory,...). VERSION is something like 0.9.4 or trunk-r3721-20080613 and can be seen in the tarball filename. You can easily find out YOURKERNELVERSION by running the uname -r command. 

**Tip:** You can download the files to the hard drive in OS X or Windows (or whatever you might be dual booting) and then access the downloaded files in Ubuntu! 
If you have a wired connection in Ubuntu the dependencies will be automatically installed, so you don't need to manually install the packages then, just download the tarball and run the script.

Once you have the files, insert the removable media and install the packages by double clicking on them in Nautilus or by running
```
sudo dpkg -i /path/to/package.deb
```

Then run the script like this:
```
chmod +x madwifi.sh
sudo ./madwifi.sh --tarball /path/to/madwifi-VERSION.tar.gz
```

Of course you need to substitute VERSION with the actual MadWifi version. After it completes you should be able to connect to an AP with Ubuntu's NetworkManager icon in the notification area. 8)

Note that **you have to run the last command after every kernel update**, so keep the source tarball at hand! You can also start using the SVN way now that you have a working connection.

**Troubleshooting and different versions of MadWifi**
[COLOR="Red"]**If the driver isn't working, try another version of it (trunk, ng, hal or different revision)!**[/COLOR]
The script installs trunk by default.

Especially when having this output
```
ath_pci: HAL doesn't support MAC revision
```
it's most likely fixed by trying [ng tarball]("http://snapshots.madwifi-project.org/special/") or [hal tarball]("http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/").

There are alternatives to MadWifi called ath5k and ath9k. They are still quite experimental. Anyway, if the script doesn't work and you get some results by running dmesg | grep ath5k try running sudo modprobe -r ath5k before running the script. If it helps, blacklist ath5k.

**Problems?**
If the script is broken or sucks in any way, please let me know.

When reporting problems please provide the following information:
* output of command sudo ./madwifi.sh --info
* are you using SVN or a (version?) snapshot
* any interesting lines in dmesg output that the above command does not show
* information on the hardware used, laptop or pci card make/model
It worked for me too, at first try with HP Pavillon DV5-1210ez, many many THANKS,

---

### Post by JayD239 on 2009-02-15
> **JayD239 said:**
> I got it working by installing the madwifi hal by hand, instead of this script. I used [this walkthrough]("http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/") to do it.

The button does not seem to work yet, but i hope disabling wireless via the panel applet also saves my precious battery power.After experiencing low speeds (5~12kb/s from my local server) I decided to look further. So I googled, and googled (again) and found the [FONT="Courier New"]linux-backports-modules-intrepid[/FONT] package. 

Installed it (after removing every traces (I found) of previous wifi hacks), did a [FONT="Courier New"]modprobe ath5k[/FONT] an suddenly I downloaded a 4 megabyte file in over a few seconds. Pretty sure this is closer to 54M than 8kb/s :D

Hope this helps anyone.

---

### Post by dBuster on 2009-02-15
By the way the script if followed exactly as it is works or at least worked for me on my HP/Compaq CQ60 without any issues.  Using Jaunty Since I could not get another 64 bit distro of Ubuntu to load on this machine.

Just curious, since the button works to turn the wifi on and off, has anyone figured out how to get the wifi button to trigger the change of the led?  From the off color of orange to the on color of blue?  I have tried all the softled and other commands to no avail...

---

### Post by JayD239 on 2009-02-15
> **dBuster said:**
> By the way the script if followed exactly as it is works or at least worked for me on my HP/Compaq CQ60 without any issues.  Using Jaunty Since I could not get another 64 bit distro of Ubuntu to load on this machine.

Just curious, since the button works to turn the wifi on and off, has anyone figured out how to get the wifi button to trigger the change of the led?  From the off color of orange to the on color of blue?  I have tried all the softled and other commands to no avail...

When I got the time I will try to apply this patch:
[http://www-user.tu-chemnitz.de/~doto/kernel/0001-ath5k-initial-RFKILL-support-for-Atheros-5xxx-cards.patch](http://www-user.tu-chemnitz.de/~doto/kernel/0001-ath5k-initial-RFKILL-support-for-Atheros-5xxx-cards.patch) 

it is discussed here
[http://kerneltrap.org/index.php?q=mailarchive/linux-ath5k-devel/2009/1/8/4654414](http://kerneltrap.org/index.php?q=mailarchive/linux-ath5k-devel/2009/1/8/4654414)
and [http://kerneltrap.org/index.php?q=mailarchive/linux-ath5k-devel/2009/1/13/4711314](http://kerneltrap.org/index.php?q=mailarchive/linux-ath5k-devel/2009/1/13/4711314)

---

### Post by rottenpunker on 2009-02-16
I did everything from the original post, and nothing happened. I tried it again, and I get this.

> nicki@nicki-laptop:~$ wget [http://kolmoskone.homelinux.org/~kaja/kamaa/madwifi.sh](http://kolmoskone.homelinux.org/~kaja/kamaa/madwifi.sh) -O madwifi.sh
--2009-02-16 10:27:28--  [http://kolmoskone.homelinux.org/~kaja/kamaa/madwifi.sh](http://kolmoskone.homelinux.org/~kaja/kamaa/madwifi.sh)
Resolving kolmoskone.homelinux.org... 81.175.201.149
Connecting to kolmoskone.homelinux.org|81.175.201.149|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8804 (8.6K) [text/x-sh]
Saving to: `madwifi.sh'

100%[======================================>] 8,804       18.7K/s   in 0.5s    

2009-02-16 10:27:29 (18.7 KB/s) - `madwifi.sh' saved [8804/8804]

nicki@nicki-laptop:~$ chmod +x madwifi.sh
nicki@nicki-laptop:~$ sudo ./madwifi.sh
[sudo] password for nicki: 
Found at least one Atheros device.
Checking build dependencies...
...build dependencies OK
Checking for updates...OK
Already up to date, exiting...
Use --reinstall to rebuild the current source tree.


So it should be working, right? But of course, it isn't. I have an HP DV6700 laptop, which I did read that someone on here was having problems with and ended up going back to an earlier version of Ubuntu. This is my first Ubuntu experience, and I'd rather not downgrade if I don't have to. But if that's the only way, I suppose I will have to.

---

### Post by rottenpunker on 2009-02-16
Okay, I got a little further this time.

```
nicki@nicki-laptop:~$ sudo ./madwifi.sh --info
Found at least one Atheros device.
Linux nicki-laptop 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux
Distro: Debian
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Device 137a
	Flags: fast devsel, IRQ 19
	Memory at f6000000 (64-bit, non-prefetchable) [size=64K]
	Kernel modules: ath_pci

ath_pci               218552  0 
wlan                  239984  1 ath_pci
ath_hal               259552  1 ath_pci
[   17.777197] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   17.815391] ath_pci: 0.9.4
[   17.815900] ath_pci 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[   17.815909] ath_pci 0000:03:00.0: setting latency timer to 64
[   17.843938] ath_pci 0000:03:00.0: PCI INT A disabled
[ 9190.668043] ath_pci: driver unloaded
[ 9191.232475] ath_hal: driver unloaded
[ 9237.999847] ath_pci 0000:03:00.0: enabling device (0000 -> 0002)
[ 9237.999870] ath_pci 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[ 9237.999884] ath_pci 0000:03:00.0: setting latency timer to 64
[ 9237.999906] ath_pci: HAL doesn't support MAC revision 0xffffffff
[ 9237.999922] ath_pci 0000:03:00.0: PCI INT A disabled
[ 9425.242995] ath_pci 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[ 9425.243013] ath_pci 0000:03:00.0: setting latency timer to 64
[ 9425.243031] ath_pci: HAL doesn't support MAC revision 0xffffffff
[ 9425.243045] ath_pci 0000:03:00.0: PCI INT A disabled
wifi0: 0 ath0: 0
```

I read some of the other posts about this issue, and I saw that the response was to get a different version. I tried to get ath9k, but I'm a noob and I have no idea what to do. If anyone could help, it would be greatly appreciated. Thanks.

---

### Post by MarkCC on 2009-02-18
I've got a brand new Compaq CQ60, and I'm trying to get the wireless working. I'm running Ubuntu Ibex, with kernel 2.6.27-11-generic.

I tried the instructions from the original post, and got a failure because it couldn't find the SVN server. So I downloaded the current MadWifi (version 0.9.4), and ran the script using the "-tarball" option. The compilation failed, with the following error:

/home/markcc/Desktop/madwifi-0.9.4/net80211/ieee80211_power.c: In function 'ieee80211_pwrsave':
/home/markcc/Desktop/madwifi-0.9.4/net80211/ieee80211_power.c:240: error: implicit declaration of function '__skb_append'

Checking dmsg to see what's going on with the standard drivers, I found the following:

[   13.441447] ath_hal: module license 'Proprietary' taints kernel.
[   13.464472] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413
, RF5413)
[   13.518986] wlan: 0.9.4
[   13.542055] ath_pci: 0.9.4
[   13.542340] ath_pci 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.542353] ath_pci 0000:02:00.0: setting latency timer to 64
[   13.590859] wifi%d: unable to attach hardware: 'Hardware revision not support
ed' (HAL status 13)

So it definitely seems that the drivers that are pre-installed aren't compatible with my wireless hardward. But without being able to compile madwifi, I'm not sure how to proceed. Any suggestions?

Thanks,

      -Mark

---

### Post by JayD239 on 2009-02-18
> **MarkCC said:**
> I've got a brand new Compaq CQ60, and I'm trying to get the wireless working. I'm running Ubuntu Ibex, with kernel 2.6.27-11-generic.
...
Thanks,
      -MarkI got a CQ60 myself. See my [earlier post]("http://ubuntuforums.org/showpost.php?p=6739136&postcount=128") (just a few before this one, you actually should have read it already) about how to get it working at a normal speed. 

You might need to do a [FONT="Courier New"]# modprobe ath5k[/FONT] once in a while. At least i have to when it's not working. A few seconds after that command you're wifi will connect again.

---

### Post by picardo on 2009-02-20
I am encountering the following error

Fetching sources from SVN...svn: OPTIONS of 'http://svn.madwifi.org/madwifi/trunk': Could not resolve hostname `svn.madwifi.org': Host not found ([http://svn.madwifi.org](http://svn.madwifi.org))

Seems like their svn servers are down, eh?

---

### Post by larryhaja on 2009-02-26
> **picardo said:**
> I am encountering the following error

Fetching sources from SVN...svn: OPTIONS of 'http://svn.madwifi.org/madwifi/trunk': Could not resolve hostname `svn.madwifi.org': Host not found ([http://svn.madwifi.org](http://svn.madwifi.org))

Seems like their svn servers are down, eh?

Their svn server is not down.  Due to some issues in hosting they have changed their website from madwifi.org to madwifi-project.org.  The appropriate command would be.
```
# svn co http://svn.madwifi.org/madwifi/trunk madwifi-ng
```

---

### Post by picardo on 2009-03-01
> **larryhaja said:**
> Their svn server is not down.  Due to some issues in hosting they have changed their website from madwifi.org to madwifi-project.org.  

Cool. I managed to download it but now the script tells me that my hardwarwe is incompatible and that I should post the result in the forums. 

Here it goes:

> Found at least one Atheros device.
Checking build dependencies...
...build dependencies OK
Fetching sources from SVN...OK
Removing previous MadWifi installations...OK
Building MadWifi..athstats.c: In function 'main':
athstats.c:289: warning: format not a string literal and no format arguments
athstats.c:291: warning: format not a string literal and no format arguments
athstats.c:311: warning: format not a string literal and no format arguments
athstats.c:313: warning: format not a string literal and no format arguments
athstats.c:348: warning: format not a string literal and no format arguments
ath_info.c: In function 'main':
ath_info.c:2847: warning: ignoring return value of 'fwrite', declared with attribute warn_unused_result
80211stats.c: In function 'main':
80211stats.c:287: warning: format not a string literal and no format arguments
wlanconfig.c: In function 'list_keys':
wlanconfig.c:779: warning: ignoring return value of 'system', declared with attribute warn_unused_result
wlanconfig.c: In function 'ieee80211_status':
wlanconfig.c:895: warning: ignoring return value of 'system', declared with attribute warn_unused_result
.OK
Installing MadWifi...OK
Loading kernel module...OK
Adding ath_pci to /etc/modules...OK
It seems that the driver did not detect compatible hardware.
Please try to connect to an AP and post the output of
sudo ./madwifi.sh --info to the forum.




PS: I'm so exasperated with Ubuntu right now. I've been working to set up a wireless connection for months. Why is it so frickin'  difficult to set up a wireless connection on my machine (Asus EEE 1000h)? I also got a Windows XP on this machine which can easily establish wireless connections. Meh.

---

### Post by McBain26 on 2009-03-03
I think what they mean is the output from
```
sudo ./madwifi.sh --info
```

I have the exact same problem so I'll post mine:
```

Found at least one Atheros device.
Linux ubuntu 2.6.28-8-generic #26-Ubuntu SMP Wed Feb 25 04:27:53 UTC 2009 x86_64 GNU/Linux
Distro: Debian
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Device 1a3b:1026
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at fe1f0000 (64-bit, non-prefetchable) [size=64K]
	Kernel driver in use: ath5k_pci
	Kernel modules: ath5k, ath_pci

ath_pci               224704  0 
wlan                  259488  1 ath_pci
ath_hal               286208  1 ath_pci
[  124.061408] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[  124.076301] ath_pci: 0.9.4
[  503.131115] ath_pci: driver unloaded
[  503.473714] ath_hal: driver unloaded
wifi0: 0 ath0: 0

```

---

### Post by daiwei on 2009-03-07
I have encountered with the same problems as picardo.
what's wrong ???

who can help us ?

---

### Post by PureVen0m on 2009-03-10
> ven0m@ven0m-laptop:~$ sudo ./madwifi.sh
sudo: unable to resolve host ven0m-laptop
[sudo] password for ven0m: 
Found at least one Atheros device.
Checking build dependencies...
No packages found matching subversion.
Installing subversion...Selecting previously deselected package libapr1.
(Reading database ... 160679 files and directories currently installed.)
Unpacking libapr1 (from .../libapr1_1.2.11-1_i386.deb) ...
Selecting previously deselected package libaprutil1.
Unpacking libaprutil1 (from .../libaprutil1_1.2.12+dfsg-3_i386.deb) ...
Selecting previously deselected package libsvn1.
Unpacking libsvn1 (from .../libsvn1_1.4.6dfsg1-2ubuntu1_i386.deb) ...
Selecting previously deselected package subversion.
Unpacking subversion (from .../subversion_1.4.6dfsg1-2ubuntu1_i386.deb) ...
Setting up libapr1 (1.2.11-1) ...

Setting up libaprutil1 (1.2.12+dfsg-3) ...

Setting up libsvn1 (1.4.6dfsg1-2ubuntu1) ...

Setting up subversion (1.4.6dfsg1-2ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
OK
...build dependencies OK
Fetching sources from SVN...svn: PROPFIND request failed on '/madwifi/trunk'
svn: PROPFIND of '/madwifi/trunk': Could not resolve hostname `svn.madwifi.org': No address associated with hostname ([http://svn.madwifi.org](http://svn.madwifi.org))

Here's where my fun ended today...

I'm triing to get my Atheros AR5007EG wirelles adapter working now for 5 hours, unsucesfully.

The laptop is an Asus X50SL

---

### Post by JayD239 on 2009-03-10
> **PureVen0m said:**
> Here's where my fun ended today...
If you would have read the whole thread you would have seen this post:
> **JayD239 said:**
> Open the madwifi.sh with a texteditor. Scroll down to line 213. In that line change svn.madwifi.org to svn.madwifi-project.org. That should fix the hostname error.

If there are other errors after that, please first read the topic first. Maybe there is already a solution given for your problem.

*update
Kajaste has just updated his script, so if you'll download it again the svn-link is okay.

---

### Post by PureVen0m on 2009-03-10
> Found at least one Atheros device.
Linux ven0m-laptop 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686 GNU/Linux
Distro: Debian
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Unknown device 1a3b:1026
	Flags: fast devsel, IRQ 22
	Memory at fdff0000 (64-bit, non-prefetchable) [size=64K]

ath_pci               248248  0 
wlan                  235504  1 ath_pci
ath_hal               252512  1 ath_pci
[  475.672626] ath_pci: HAL doesn't support MAC revision 0xe2
wifi0: 0 ath0: 0


It said device  not recognized, and to post this on forum, i'm a bit lost here :(

---

### Post by XPM on 2009-03-10
Hi

I tried the script after recieving a bad signal with my Atheros compatible card.

Thing is, after I installed this, the signal drops in and out and keeps disconnecting me all the time

All I want to do now is to uninstall the driver and go back to the old.

If I do the sudo ./madwifi.sh --uninstall it uninstalls perfectly but then no wireless cards show up.

Nor does any Atheros show up if I start the "Hardware Drivers" application like it used to

How do I get the old stuff back?

Running 8.10

---

### Post by Kajaste on 2009-03-11
> **XPM said:**
> Hi

I tried the script after recieving a bad signal with my Atheros compatible card.

Thing is, after I installed this, the signal drops in and out and keeps disconnecting me all the time

All I want to do now is to uninstall the driver and go back to the old.

If I do the sudo ./madwifi.sh --uninstall it uninstalls perfectly but then no wireless cards show up.

Nor does any Atheros show up if I start the "Hardware Drivers" application like it used to

How do I get the old stuff back?

Running 8.10
Uninstalling the script version and reinstalling all module packages should bring you back to where you started.
```

sudo ./madwifi.sh --uninstall
sudo apt-get install --reinstall linux-restricted-modules-`uname -r`
sudo apt-get install --reinstall linux-backports-modules-`uname -r`
```

---

### Post by JayD239 on 2009-03-11
I had 'a' disconnecting error to. Does it has a very bad speed too?

Have you tried installing the [FONT="Courier New"]backports-modules-intrepid[/FONT] package? That worked for me. This going to use module [FONT="Courier New"]ath5k[/FONT] instead of [FONT="Courier New"]ath_pci,ath_hal[/FONT]. So after installing, open [FONT="Courier New"]/etc/modules[/FONT] and remove the ath_ lines and add add ath5k

---

### Post by XPM on 2009-03-11
Yes, I do get very bad speeds!
I got å netgear rangemax wpn311 :)
Is that package in synaptic?
Wont it conflict with the script?
Thanks for the reply!

---

### Post by XPM on 2009-03-11
> **Kajaste said:**
> Uninstalling the script version and reinstalling all module packages should bring you back to where you started.
```

sudo ./madwifi.sh --uninstall
sudo apt-get install --reinstall linux-restricted-modules-`uname -r` linux-backports-modules-`uname -r`
```

Thanks!

---

### Post by Homitsu on 2009-03-18
I have an EEE PC 904HD - Intrepid Ibex - No Adam Kernel

This is the log after installation:

```
Found at least one Atheros device.
Checking build dependencies...
...build dependencies OK
Removing previous MadWifi installations...OK
Building MadWifi (warnings are okay)..ath_info.c: In function 'main':
ath_info.c:2847: warning: ignoring return value of 'fwrite', declared with attribute warn_unused_result
athstats.c: In function 'main':
athstats.c:289: warning: format not a string literal and no format arguments
athstats.c:291: warning: format not a string literal and no format arguments
athstats.c:311: warning: format not a string literal and no format arguments
athstats.c:313: warning: format not a string literal and no format arguments
athstats.c:348: warning: format not a string literal and no format arguments
80211stats.c: In function 'main':
80211stats.c:287: warning: format not a string literal and no format arguments
wlanconfig.c: In function 'list_keys':
wlanconfig.c:779: warning: ignoring return value of 'system', declared with attribute warn_unused_result
wlanconfig.c: In function 'ieee80211_status':
wlanconfig.c:895: warning: ignoring return value of 'system', declared with attribute warn_unused_result
.OK
Installing MadWifi...OK
Loading kernel module...OK
Adding ath_pci to /etc/modules...OK

It seems that the driver did not detect compatible hardware.
Please try to connect to an AP. If it doesn't work, see the 
Troubleshooting part in the forum. If after reading the Troubleshooting
part and the WHOLE THREAD it still doesn't work, post your
sudo ./madwifi.sh --info output to the forum.

```

Please HELP! I'm gettin' crazy with this WiFi stuff...

---

### Post by Drufi on 2009-05-21
Hello
I tried using the madwifi.sh script but it still hasn't solved my problem.
I'm using a Fujitsu-Siemens Amilo Pro  1.5Ghz, 504mb of Ram with dual boot XP and Ubuntu 8.10
I got this computer from a friend. So it has already lived a bit... It seems that the internal wifi card is broken. But I received a Gigaset 108 PC card with it which works well under XP, although the Gigaset program sometimes freezes the shutdown process under XP.

I'm pretty new to Linux in general. I made a CD installation, all worked out of the box except the Wifi. The hardware control panel showed the athk5 but even when this was enabled I couldn't enable the wireless connection on the menu bar (the option showed wifi0 but i couldn't select it. 
I tried to install the windows driver with ndiswrapper and with ndgisk(or similar spelling) but this still didn't work (i disabled the athk5)... 
So seeing the results of the other posts I tried to run the madwifi.sh script but I got some errors. 
Note: I have no rj45 connection possible, i can only pass through wifi, so i used the traball method.

Here is the output I got with the script:
**Script output:**

Found at least one Atheros device.
Checking build dependencies...
...build dependencies OK
Unrolling tarball version 0.9.4...OK
Removing previous MadWifi installations...OK
Building MadWifi (warnings are okay)..athstats.c: In function 'main':
athstats.c:285: warning: format not a string literal and no format arguments
athstats.c:287: warning: format not a string literal and no format arguments
athstats.c:307: warning: format not a string literal and no format arguments
athstats.c:309: warning: format not a string literal and no format arguments
athstats.c:344: warning: format not a string literal and no format arguments
80211stats.c: In function 'main':
80211stats.c:290: warning: format not a string literal and no format arguments
wlanconfig.c: In function 'if_find_unit':
wlanconfig.c:297: warning: ignoring return value of 'fgets', declared with attribute warn_unused_result
wlanconfig.c: In function 'list_keys':
wlanconfig.c:830: warning: ignoring return value of 'system', declared with attribute warn_unused_result
wlanconfig.c: In function 'ieee80211_status':
wlanconfig.c:946: warning: ignoring return value of 'system', declared with attribute warn_unused_result
ath_info.c: In function 'main':
ath_info.c:1041: warning: ignoring return value of 'fwrite', declared with attribute warn_unused_result
/usr/src/madwifi-0.9.4/net80211/ieee80211_power.c: In function 'ieee80211_pwrsave':
/usr/src/madwifi-0.9.4/net80211/ieee80211_power.c:240: error: implicit declaration of function '__skb_append'
make[3]: *** [/usr/src/madwifi-0.9.4/net80211/ieee80211_power.o] Error 1
make[3]: *** Waiting for unfinished jobs....
make[2]: *** [/usr/src/madwifi-0.9.4/net80211] Error 2
make[1]: *** [_module_/usr/src/madwifi-0.9.4] Error 2
make: *** [modules] Error 2"

 **Here is the output of "sudo ./madwifi.sh --info":**

"Found at least one Atheros device.
Linux ubuntu 2.6.27-11-generic #1 SMP Wed Apr 1 20:57:48 UTC 2009 i686 GNU/Linux
Distro: Debian
03:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
    Subsystem: Device 02fa:3070
    Flags: medium devsel, IRQ 10
    Memory at 38000000 (32-bit, non-prefetchable) [disabled] [size=64K]
    Kernel modules: ath_pci

wifi0: 0 ath0: 0"


[B]The madwifi document: Madwifi-0.9.4.tar.gz
[/B]
**and the dmesg:**
[    0.004051] SELinux:  Disabled at boot.
[    0.004082] AppArmor: AppArmor initialized
[    0.004092] Mount-cache hash table entries: 512
[    0.004316] Initializing cgroup subsys ns
[    0.004322] Initializing cgroup subsys cpuacct
[    0.004325] Initializing cgroup subsys memory
[    0.004347] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004351] CPU: L2 cache: 1024K
[    0.004365] Checking 'hlt' instruction... OK.
[    0.020630] SMP alternatives: switching to UP code
[    0.027692] Freeing SMP alternatives: 11k freed
[    0.027696] ACPI: Core revision 20080609
[    0.030704] ACPI: Checking initramfs for custom DSDT
[    0.502117] ACPI: setting ELCR to 0200 (from 0c00)
[    0.504104] weird, boot CPU (#0) not listedby the BIOS.
[    0.504107] SMP motherboard not detected.
[    0.504111] Local APIC not detected. Using dummy APIC emulation.
[    0.504114] SMP disabled
[    0.504198] Brought up 1 CPUs
[    0.504202] Total of 1 processors activated (2999.64 BogoMIPS).
[    0.504218] CPU0 attaching NULL sched-domain.
[    0.504526] net_namespace: 840 bytes
[    0.504542] Booting paravirtualized kernel on bare hardware
[    0.508037] Time: 23:31:07  Date: 05/20/09
[    0.508075] NET: Registered protocol family 16
[    0.508444] EISA bus registered
[    0.508464] ACPI: bus type pci registered
[    0.510040] PCI: PCI BIOS revision 2.10 entry at 0xfd6c4, last bus=3
[    0.510044] PCI: Using configuration type 1 for base access
[    0.511910] ACPI: EC: Look up EC in DSDT
[    0.515061] ACPI: Interpreter enabled
[    0.515068] ACPI: (supports S0 S3 S4 S5)
[    0.515088] ACPI: Using PIC for interrupt routing
[    0.515943] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.922451] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.922455] ACPI: EC: driver started in interrupt mode
[    0.922518] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.922697] PCI: 0000:00:02.0 reg 10 32bit mmio: [e8000000, efffffff]
[    0.922703] PCI: 0000:00:02.0 reg 14 32bit mmio: [e0000000, e007ffff]
[    0.922709] PCI: 0000:00:02.0 reg 18 io port: [1800, 1807]
[    0.922729] pci 0000:00:02.0: supports D1
[    0.922745] PCI: 0000:00:02.1 reg 10 32bit mmio: [f0000000, f7ffffff]
[    0.922751] PCI: 0000:00:02.1 reg 14 32bit mmio: [e0080000, e00fffff]
[    0.922773] pci 0000:00:02.1: supports D1
[    0.922840] PCI: 0000:00:1d.0 reg 20 io port: [1820, 183f]
[    0.922889] PCI: 0000:00:1d.1 reg 20 io port: [1840, 185f]
[    0.922938] PCI: 0000:00:1d.2 reg 20 io port: [1860, 187f]
[    0.922993] PCI: 0000:00:1d.7 reg 10 32bit mmio: [e0100000, e01003ff]
[    0.923043] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.923049] pci 0000:00:1d.7: PME# disabled
[    0.923120] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.923129] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    0.923134] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH4 GPIO
[    0.923156] PCI: 0000:00:1f.1 reg 10 io port: [0, 7]
[    0.923163] PCI: 0000:00:1f.1 reg 14 io port: [0, 3]
[    0.923170] PCI: 0000:00:1f.1 reg 18 io port: [0, 7]
[    0.923177] PCI: 0000:00:1f.1 reg 1c io port: [0, 3]
[    0.923184] PCI: 0000:00:1f.1 reg 20 io port: [1810, 181f]
[    0.923192] PCI: 0000:00:1f.1 reg 24 32bit mmio: [0, 3ff]
[    0.923238] PCI: 0000:00:1f.3 reg 20 io port: [1880, 189f]
[    0.923278] PCI: 0000:00:1f.5 reg 10 io port: [1c00, 1cff]
[    0.923285] PCI: 0000:00:1f.5 reg 14 io port: [18c0, 18ff]
[    0.923292] PCI: 0000:00:1f.5 reg 18 32bit mmio: [e0100c00, e0100dff]
[    0.923299] PCI: 0000:00:1f.5 reg 1c 32bit mmio: [e0100800, e01008ff]
[    0.923325] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.923330] pci 0000:00:1f.5: PME# disabled
[    0.923354] PCI: 0000:00:1f.6 reg 10 io port: [2400, 24ff]
[    0.923360] PCI: 0000:00:1f.6 reg 14 io port: [2000, 207f]
[    0.923393] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.923399] pci 0000:00:1f.6: PME# disabled
[    0.923433] PCI: 0000:02:03.0 reg 10 32bit mmio: [e0202000, e0202fff]
[    0.923471] pci 0000:02:03.0: supports D1
[    0.923473] pci 0000:02:03.0: supports D2
[    0.923476] pci 0000:02:03.0: PME# supported from D0 D1 D2 D3hot
[    0.923481] pci 0000:02:03.0: PME# disabled
[    0.923506] PCI: 0000:02:05.0 reg 10 32bit mmio: [e0200000, e0201fff]
[    0.923532] PCI: 0000:02:05.0 reg 30 32bit mmio: [0, ffff]
[    0.923546] pci 0000:02:05.0: supports D1
[    0.923548] pci 0000:02:05.0: supports D2
[    0.923551] pci 0000:02:05.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.923555] pci 0000:02:05.0: PME# disabled
[    0.923582] PCI: 0000:02:06.0 reg 10 32bit mmio: [e0203000, e0203fff]
[    0.923622] pci 0000:02:06.0: PME# supported from D0 D3hot D3cold
[    0.923627] pci 0000:02:06.0: PME# disabled
[    0.923656] PCI: 0000:02:09.0 reg 10 32bit mmio: [0, fff]
[    0.923670] pci 0000:02:09.0: supports D1
[    0.923672] pci 0000:02:09.0: supports D2
[    0.923675] pci 0000:02:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.923680] pci 0000:02:09.0: PME# disabled
[    0.923705] pci 0000:00:1e.0: transparent bridge
[    0.923713] PCI: bridge 0000:00:1e.0 32bit mmio: [e0200000, e02fffff]
[    0.923738] bus 00 -> node 0
[    0.923747] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.924155] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.930790] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 *11)
[    0.930932] ACPI: PCI Interrupt Link [LNKB] (IRQs *10 11)
[    0.931071] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 *11)
[    0.931208] ACPI: PCI Interrupt Link [LNKD] (IRQs *11)
[    0.931346] ACPI: PCI Interrupt Link [LNKE] (IRQs *10 11)
[    0.931483] ACPI: PCI Interrupt Link [LNKF] (IRQs *10 11)
[    0.931628] ACPI: PCI Interrupt Link [LNKG] (IRQs *10 11)
[    0.931766] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 *11)
[    0.931976] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.932019] pnp: PnP ACPI init
[    0.932042] ACPI: bus type pnp registered
[    1.137414] pnp: PnP ACPI: found 12 devices
[    1.137418] ACPI: ACPI bus type pnp unregistered
[    1.137424] PnPBIOS: Disabled by ACPI PNP
[    1.137850] PCI: Using ACPI for IRQ routing
[    1.137996] NET: Registered protocol family 8
[    1.137996] NET: Registered protocol family 20
[    1.137996] NetLabel: Initializing
[    1.137996] NetLabel:  domain hash size = 128
[    1.137996] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.137996] NetLabel:  unlabeled traffic allowed by default
[    1.137996] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    1.137996]    actual entries 65620
[    1.137996] AppArmor: AppArmor Filesystem Enabled
[    1.137996] ACPI: RTC can wake from S4
[    1.137996] system 00:04: ioport range 0x600-0x60f has been reserved
[    1.137996] system 00:04: ioport range 0x700-0x70f has been reserved
[    1.137996] system 00:04: ioport range 0x800-0x80f has been reserved
[    1.137996] system 00:04: ioport range 0x1000-0x107f has been reserved
[    1.137996] system 00:04: ioport range 0x1180-0x11bf has been reserved
[    1.137996] system 00:04: iomem range 0xfec10000-0xfec1ffff could not be reserved
[    1.173911] pci 0000:02:09.0: CardBus bridge, secondary bus 0000:03
[    1.173915] pci 0000:02:09.0:   IO window: 0x003000-0x0030ff
[    1.173921] pci 0000:02:09.0:   IO window: 0x003400-0x0034ff
[    1.173926] pci 0000:02:09.0:   PREFETCH window: 0x30000000-0x33ffffff
[    1.173931] pci 0000:02:09.0:   MEM window: 0x38000000-0x3bffffff
[    1.173936] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    1.173941] pci 0000:00:1e.0:   IO window: 0x3000-0x3fff
[    1.173947] pci 0000:00:1e.0:   MEM window: 0xe0200000-0xe02fffff
[    1.173953] pci 0000:00:1e.0:   PREFETCH window: 0x00000030000000-0x00000035ffffff
[    1.173966] pci 0000:00:1e.0: enabling device (0005 -> 0007)
[    1.173974] pci 0000:00:1e.0: setting latency timer to 64
[    1.174242] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 10
[    1.174246] PCI: setting IRQ 10 as level-triggered
[    1.174251] pci 0000:02:09.0: PCI INT A -> Link[LNKF] -> GSI 10 (level, low) -> IRQ 10
[    1.174259] bus: 00 index 0 io port: [0, ffff]
[    1.174262] bus: 00 index 1 mmio: [0, ffffffff]
[    1.174265] bus: 02 index 0 io port: [3000, 3fff]
[    1.174268] bus: 02 index 1 mmio: [e0200000, e02fffff]
[    1.174270] bus: 02 index 2 mmio: [30000000, 35ffffff]
[    1.174273] bus: 02 index 3 io port: [0, ffff]
[    1.174276] bus: 02 index 4 mmio: [0, ffffffff]
[    1.174279] bus: 03 index 0 io port: [3000, 30ff]
[    1.174282] bus: 03 index 1 io port: [3400, 34ff]
[    1.174285] bus: 03 index 2 mmio: [30000000, 33ffffff]
[    1.174288] bus: 03 index 3 mmio: [38000000, 3bffffff]
[    1.174305] NET: Registered protocol family 2
[    1.174485] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    1.174804] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    1.174935] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    1.175068] TCP: Hash tables configured (established 16384 bind 16384)
[    1.175073] TCP reno registered
[    1.175176] NET: Registered protocol family 1
[    1.175335] checking if image is initramfs... it is
[    1.676091] Switched to high resolution mode on CPU 0
[    2.152170] Freeing initrd memory: 8263k freed
[    2.152474] Simple Boot Flag at 0x36 set to 0x1
[    2.153025] audit: initializing netlink socket (disabled)
[    2.153055] type=2000 audit(1242862268.152:1): initialized
[    2.160394] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.163528] VFS: Disk quotas dquot_6.5.1
[    2.163655] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.163799] msgmni has been set to 985
[    2.163976] io scheduler noop registered
[    2.163980] io scheduler anticipatory registered
[    2.163983] io scheduler deadline registered
[    2.164035] io scheduler cfq registered (default)
[    2.164063] pci 0000:00:02.0: Boot video device
[    2.164666] isapnp: Scanning for PnP cards...
[    2.518359] isapnp: No Plug & Play device found
[    2.568719] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.569003] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    2.570004] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[    2.570010] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[    2.570020] serial 0000:00:1f.6: PCI INT B disabled
[    2.571969] brd: module loaded
[    2.572429] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.572595] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.575303] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.576532] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.576539] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.576542] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.576546] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.576549] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.577129] mice: PS/2 mouse device common for all mice
[    2.577304] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    2.577323] rtc0: alarms up to one month, y3k
[    2.577469] EISA: Probing bus 0 at eisa.0
[    2.577478] Cannot allocate resource for EISA slot 1
[    2.577482] Cannot allocate resource for EISA slot 2
[    2.577486] Cannot allocate resource for EISA slot 3
[    2.577508] EISA: Detected 0 cards.
[    2.577512] cpuidle: using governor ladder
[    2.577516] cpuidle: using governor menu
[    2.578309] TCP cubic registered
[    2.578357] Using IPI No-Shortcut mode
[    2.578613] registered taskstats version 1
[    2.578778]   Magic number: 9:415:555
[    2.578904] tty ptya1: hash matches
[    2.579015] pci_link PNP0C0F:06: hash matches
[    2.579056] rtc_cmos 00:01: setting system clock to 2009-05-20 23:31:09 UTC (1242862269)
[    2.579061] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.579064] EDD information not available.
[    2.579359] Freeing unused kernel memory: 424k freed
[    2.579422] Write protecting the kernel text: 2580k
[    2.579462] Write protecting the kernel read-only data: 940k
[    2.607086] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.880061] fuse init (API version 7.9)
[    3.163265] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    3.163338] processor ACPI0007:00: registered as cooling_device0
[    3.163344] ACPI: Processor [CPU0] (supports 8 throttling states)
[    3.235035] thermal LNXTHERM:01: registered as thermal_zone0
[    3.268630] ACPI: Thermal Zone [THRS] (52 C)
[    3.336628] thermal LNXTHERM:02: registered as thermal_zone1
[    3.370219] ACPI: Thermal Zone [THRC] (60 C)
[    4.267949] usbcore: registered new interface driver usbfs
[    4.267987] usbcore: registered new interface driver hub
[    4.276576] No dock devices found.
[    4.318703] usbcore: registered new device driver usb
[    4.361256] SCSI subsystem initialized
[    4.361667] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    4.361671] PCI: setting IRQ 11 as level-triggered
[    4.361678] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    4.361695] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    4.361700] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.361763] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    4.365658] ehci_hcd 0000:00:1d.7: debug port 1
[    4.365666] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    4.365679] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xe0100000
[    4.374153] USB Universal Host Controller Interface driver v3.0
[    4.384171] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.384452] usb usb1: configuration #1 chosen from 1 choice
[    4.384494] hub 1-0:1.0: USB hub found
[    4.384510] hub 1-0:1.0: 6 ports detected
[    4.575243] libata version 3.00 loaded.
[    4.592763] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    4.592771] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    4.592783] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    4.592788] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.592826] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    4.592854] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001820
[    4.593004] usb usb2: configuration #1 chosen from 1 choice
[    4.593040] hub 2-0:1.0: USB hub found
[    4.593051] hub 2-0:1.0: 2 ports detected
[    4.704126] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    4.801043] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    4.801051] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    4.801064] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    4.801069] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.801109] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    4.801138] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001840
[    4.801304] usb usb3: configuration #1 chosen from 1 choice
[    4.801341] hub 3-0:1.0: USB hub found
[    4.801351] hub 3-0:1.0: 2 ports detected
[    4.838142] usb 1-2: configuration #1 chosen from 1 choice
[    4.904719] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    4.904727] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    4.904740] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    4.904745] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.904784] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    4.904813] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001860
[    4.904959] usb usb4: configuration #1 chosen from 1 choice
[    4.904997] hub 4-0:1.0: USB hub found
[    4.905022] hub 4-0:1.0: 2 ports detected
[    5.008473] ata_piix 0000:00:1f.1: version 2.12
[    5.008490] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    5.008501] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    5.008558] ata_piix 0000:00:1f.1: setting latency timer to 64
[    5.008655] scsi0 : ata_piix
[    5.008794] scsi1 : ata_piix
[    5.010266] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    5.010270] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    5.040911] usbcore: registered new interface driver libusual
[    5.054060] Initializing USB Mass Storage driver...
[    5.054522] scsi2 : SCSI emulation for USB Mass Storage devices
[    5.054635] usbcore: registered new interface driver usb-storage
[    5.054640] USB Mass Storage support registered.
[    5.054755] usb-storage: device found at 2
[    5.054758] usb-storage: waiting for device to settle before scanning
[    5.100552] Marking TSC unstable due to TSC halts in idle
[    5.172572] ata1.00: ATA-6: FUJITSU MHT2060AT, 0022, max UDMA/100
[    5.172577] ata1.00: 117210240 sectors, multi 16: LBA 
[    5.188523] ata1.00: configured for UDMA/100
[    5.344195] ata2.01: NODEV after polling detection
[    5.352517] ata2.00: ATAPI: QSI     DVDRW SDW-041, DU05, max UDMA/33
[    5.368463] ata2.00: configured for UDMA/33
[    5.368626] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHT2060A 0022 PQ: 0 ANSI: 5
[    5.368940] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    5.370968] scsi 1:0:0:0: CD-ROM            QSI      DVDRW SDW-041    DU05 PQ: 0 ANSI: 5
[    5.371134] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    5.378366] ohci1394 0000:02:03.0: PCI INT A -> Link[LNKF] -> GSI 10 (level, low) -> IRQ 10
[    5.430133] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[10]  MMIO=[e0202000-e02027ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    5.442888] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
[    5.442894] b44 0000:02:05.0: PCI INT A -> Link[LNKE] -> GSI 10 (level, low) -> IRQ 10
[    5.500123] ssb: Sonics Silicon Backplane found on PCI device 0000:02:05.0
[    5.504778] b44.c:v2.0
[    5.524514] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:0a:e4:28:20:4a
[    5.600470] Driver 'sd' needs updating - please use bus_type methods
[    5.604203] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[    5.604225] sd 0:0:0:0: [sda] Write Protect is off
[    5.604229] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.604259] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.604354] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[    5.604371] sd 0:0:0:0: [sda] Write Protect is off
[    5.604374] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.604403] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.604408]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    5.688621]  sda1
[    5.688776] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.700346] sr0: scsi3-mmc drive: 12x/24x writer cd/rw xa/form2 cdda tray
[    5.700353] Uniform CD-ROM driver Revision: 3.20
[    5.700511] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    6.349008] loop: module loaded
[    6.411473] kjournald starting.  Commit interval 5 seconds
[    6.411495] EXT3-fs: mounted filesystem with ordered data mode.
[    6.712210] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[04e40a009b172036]
[   10.052363] usb-storage: device scan complete
[   10.052837] scsi 2:0:0:0: Direct-Access     SanDisk  U3 Contour       4.04 PQ: 0 ANSI: 2
[   10.053200] scsi 2:0:0:1: CD-ROM            SanDisk  U3 Contour       4.04 PQ: 0 ANSI: 2
[   10.054177] sd 2:0:0:0: [sdb] 8013457 512-byte hardware sectors (4103 MB)
[   10.054675] sd 2:0:0:0: [sdb] Write Protect is off
[   10.054678] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   10.054682] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   10.056293] sd 2:0:0:0: [sdb] 8013457 512-byte hardware sectors (4103 MB)
[   10.056805] sd 2:0:0:0: [sdb] Write Protect is off
[   10.056809] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   10.056812] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   10.056817]  sdb: sdb1
[   10.057581] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   10.057831] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   10.058680] sr1: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[   10.058768] sr 2:0:0:1: Attached scsi CD-ROM sr1
[   10.058845] sr 2:0:0:1: Attached scsi generic sg3 type 5
[   16.172139] Clocksource tsc unstable (delta = -125646997 ns)
[   17.059517] udevd version 124 started
[   18.412111] iTCO_vendor_support: vendor-support=0
[   18.528518] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   18.531140] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   18.531367] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   18.559755] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   18.625125] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.724945] Linux agpgart interface v0.103
[   18.731150] agpgart-intel 0000:00:00.0: Intel 855GM Chipset
[   18.731461] agpgart-intel 0000:00:00.0: detected 8060K stolen memory
[   18.741381] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe8000000
[   18.904027] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   18.916034] ACPI: Power Button (FF) [PWRF]
[   18.919571] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[   18.919769] ACPI: Lid Switch [LID]
[   18.919892] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   18.928034] ACPI: Sleep Button (CM) [SLP2]
[   18.989546] intel_rng: FWH not detected
[   19.151723] ACPI: AC Adapter [AC] (on-line)
[   19.344359] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   20.264136] ACPI: Battery Slot [BAT0] (battery present)
[   20.265604] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:03/input/input6
[   20.276036] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   20.390218] irda_init()
[   20.390236] NET: Registered protocol family 23
[   20.756512] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   20.756549] nsc-ircc, chip->init
[   20.756559] nsc-ircc, Found chip at base=0x02e
[   20.756584] nsc-ircc, driver loaded (Dag Brattli)
[   20.756591] nsc_ircc_open(), can't get iobase of 0x2f8
[   20.756619] nsc-ircc, Found chip at base=0x02e
[   20.756644] nsc-ircc, driver loaded (Dag Brattli)
[   20.756647] nsc_ircc_open(), can't get iobase of 0x2f8
[   20.756893] nsc-ircc 00:09: disabled
[   20.837236] parport_pc 00:08: reported by Plug and Play ACPI
[   20.837295] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   21.256661] ieee80211_crypt: registered algorithm 'NULL'
[   21.320206] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   21.320212] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   21.497917] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   21.497922] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   21.498311] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 10
[   21.498318] ipw2200 0000:02:06.0: PCI INT A -> Link[LNKG] -> GSI 10 (level, low) -> IRQ 10
[   21.499184] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   21.499257] firmware: requesting ipw2200-bss.fw
[   22.113322] wbsd: Winbond W83L51xD SD/MMC card interface driver
[   22.113327] wbsd: Copyright(c) Pierre Ossman
[   22.118539] mmc0: W83L51xD id 7112 at 0x820 irq 6 FIFO PnP
[   22.288935] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x9248b1, caps: 0x904713/0x4000
[   22.326934] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   25.135693] ipw2200: Radio Frequency Kill Switch is On:
[   25.135697] Kill switch must be turned off for wireless networking to work.
[   25.211350] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   25.211460] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   25.211499] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   25.211534] Yenta: CardBus bridge found at 0000:02:09.0 [1734:1033]
[   25.211551] Yenta: Using CSCINT to route CSC interrupts to PCI
[   25.211554] Yenta: Routing CardBus interrupts to PCI
[   25.211560] Yenta TI: socket 0000:02:09.0, mfunc 0x01001002, devctl 0x64
[   25.440471] Yenta: ISA IRQ mask 0x0018, PCI irq 10
[   25.440477] Socket status: 30000020
[   25.440481] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   25.440490] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   25.440514] cs: IO port probe 0x3000-0x3fff: clean.
[   25.440817] pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
[   25.440822] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x35ffffff
[   26.076138] pccard: CardBus card inserted into slot 0
[   26.076180] PCI: 0000:03:00.0 reg 10 32bit mmio: [0, ffff]
[   26.178688] cs: IO port probe 0x100-0x3af: clean.
[   26.180857] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   26.181562] cs: IO port probe 0x820-0x8ff: excluding 0x840-0x847
[   26.182115] cs: IO port probe 0xc00-0xcf7: clean.
[   26.182880] cs: IO port probe 0xa00-0xaff: clean.
[   26.240600] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   26.492032] intel8x0_measure_ac97_clock: measured 55331 usecs
[   26.492037] intel8x0: clocking to 48000
[   26.626130] ndiswrapper (load_wrap_driver:108): couldn't load driver netathr; check system log for messages from 'loadndisdriver'
[   26.627506] usbcore: registered new interface driver ndiswrapper
[   27.125133] lp0: using parport0 (interrupt-driven).
[   28.149209] EXT3 FS on loop0, internal journal
[   66.797638] Adding 976552k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:860 across:1156964k
[   67.134090] type=1505 audit(1242855134.208:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4099
[   67.403457] type=1505 audit(1242855134.476:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4104
[   67.403869] type=1505 audit(1242855134.476:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4104
[   67.643239] ip_tables: (C) 2000-2006 Netfilter Core Team
[   68.579368] ACPI: WMI: Mapper loaded
[   69.905863] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   69.964718] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   69.964727] apm: overridden by ACPI.
[   70.170073] ppdev: user-space parallel port driver
[   72.501588] ttyS1: LSR safety check engaged!
[   72.571510] cdrom: This disc doesn't have any tracks I recognize!
[   72.850601] Bluetooth: Core ver 2.13
[   72.853854] NET: Registered protocol family 31
[   72.853867] Bluetooth: HCI device and connection manager initialized
[   72.853878] Bluetooth: HCI socket layer initialized
[   72.930884] Bluetooth: L2CAP ver 2.11
[   72.930891] Bluetooth: L2CAP socket layer initialized
[   72.972599] Bluetooth: RFCOMM socket layer initialized
[   72.972918] Bluetooth: RFCOMM TTY layer initialized
[   72.972924] Bluetooth: RFCOMM ver 1.10
[   72.974048] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   72.974054] Bluetooth: BNEP filters: protocol multicast
[   73.038592] Bridge firewalling registered
[   73.073477] Bluetooth: SCO (Voice Link) ver 0.6
[   73.073485] Bluetooth: SCO socket layer initialized
[   77.546320] [drm] Initialized drm 1.1.0 20060810
[   77.568109] pci 0000:00:02.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   77.568125] pci 0000:00:02.0: setting latency timer to 64
[   77.570237] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   77.570256] pci 0000:00:02.1: setting latency timer to 64
[   77.571795] [drm] Initialized i915 1.6.0 20060119 on minor 1
[  110.613561] ISO 9660 Extensions: Microsoft Joliet Level 3
[  110.615682] ISOFS: changing to secondary root
[  208.044626] ppdev0: registered pardevice
[  208.187315] ppdev0: unregistered pardevice
[  208.243969] ttyS1: LSR safety check engaged!
[  208.244003] type=1503 audit(1242855275.320:5): operation="capable" name="sys_admin" pid=5735 profile="/usr/sbin/cupsd"
[  209.191669] ppdev0: registered pardevice
[  209.240990] ppdev0: unregistered pardevice
[  209.332907] ppdev0: registered pardevice
[  209.380115] ppdev0: unregistered pardevice

[B]I would be extremely grateful if you could help resolve this problem.. I'm losing so much time jumping back and forth between XP and Ubuntu and I would really like to spend some more time exploring Ubuntu.

Many thanks for all help!

drufi

While trying to uninstall the madwifi.sh... the idea came to me that i might have overdone it i.e. installed to many drivers for the same hardware. I thus checked and sure enough i still had ndisgkt and ndiswrapper installed... I uninstalled both and reenabled the ubuntu drivers for the atheros 5xxx and it suddenly worked... It suppose that my initial appreciation of the problem was the secured network. But since this one is not, it works perfectly.
Sometimes we just stumble on answers :)
[/B]

---

### Post by Kajaste on 2009-05-22
> **Drufi said:**
> Hello
I tried using the madwifi.sh script but it still hasn't solved my problem.
I'm using a Fujitsu-Siemens Amilo Pro  1.5Ghz, 504mb of Ram with dual boot XP and Ubuntu 8.10
I got this computer from a friend. So it has already lived a bit... It seems that the internal wifi card is broken. But I received a Gigaset 108 PC card with it which works well under XP, although the Gigaset program sometimes freezes the shutdown process under XP.

I'm pretty new to Linux in general. I made a CD installation, all worked out of the box except the Wifi. The hardware control panel showed the athk5 but even when this was enabled I couldn't enable the wireless connection on the menu bar (the option showed wifi0 but i couldn't select it. 
I tried to install the windows driver with ndiswrapper and with ndgisk(or similar spelling) but this still didn't work (i disabled the athk5)... 
So seeing the results of the other posts I tried to run the madwifi.sh script but I got some errors. 
Note: I have no rj45 connection possible, i can only pass through wifi, so i used the traball method.

Here is the output I got with the script:
**Script output:**

Found at least one Atheros device.
Checking build dependencies...
...build dependencies OK
Unrolling tarball version 0.9.4...OK
Removing previous MadWifi installations...OK
Building MadWifi (warnings are okay)..athstats.c: In function 'main':
athstats.c:285: warning: format not a string literal and no format arguments
athstats.c:287: warning: format not a string literal and no format arguments
athstats.c:307: warning: format not a string literal and no format arguments
athstats.c:309: warning: format not a string literal and no format arguments
athstats.c:344: warning: format not a string literal and no format arguments
80211stats.c: In function 'main':
80211stats.c:290: warning: format not a string literal and no format arguments
wlanconfig.c: In function 'if_find_unit':
wlanconfig.c:297: warning: ignoring return value of 'fgets', declared with attribute warn_unused_result
wlanconfig.c: In function 'list_keys':
wlanconfig.c:830: warning: ignoring return value of 'system', declared with attribute warn_unused_result
wlanconfig.c: In function 'ieee80211_status':
wlanconfig.c:946: warning: ignoring return value of 'system', declared with attribute warn_unused_result
ath_info.c: In function 'main':
ath_info.c:1041: warning: ignoring return value of 'fwrite', declared with attribute warn_unused_result
/usr/src/madwifi-0.9.4/net80211/ieee80211_power.c: In function 'ieee80211_pwrsave':
/usr/src/madwifi-0.9.4/net80211/ieee80211_power.c:240: error: implicit declaration of function '__skb_append'
make[3]: *** [/usr/src/madwifi-0.9.4/net80211/ieee80211_power.o] Error 1
make[3]: *** Waiting for unfinished jobs....
make[2]: *** [/usr/src/madwifi-0.9.4/net80211] Error 2
make[1]: *** [_module_/usr/src/madwifi-0.9.4] Error 2
make: *** [modules] Error 2"

 **Here is the output of "sudo ./madwifi.sh --info":**

"Found at least one Atheros device.
Linux ubuntu 2.6.27-11-generic #1 SMP Wed Apr 1 20:57:48 UTC 2009 i686 GNU/Linux
Distro: Debian
03:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
    Subsystem: Device 02fa:3070
    Flags: medium devsel, IRQ 10
    Memory at 38000000 (32-bit, non-prefetchable) [disabled] [size=64K]
    Kernel modules: ath_pci

wifi0: 0 ath0: 0"


[B]The madwifi document: Madwifi-0.9.4.tar.gz
[/B]
**and the dmesg:**
[    0.004051] SELinux:  Disabled at boot.
[    0.004082] AppArmor: AppArmor initialized
[    0.004092] Mount-cache hash table entries: 512
[    0.004316] Initializing cgroup subsys ns
[    0.004322] Initializing cgroup subsys cpuacct
[    0.004325] Initializing cgroup subsys memory
[    0.004347] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004351] CPU: L2 cache: 1024K
[    0.004365] Checking 'hlt' instruction... OK.
[    0.020630] SMP alternatives: switching to UP code
[    0.027692] Freeing SMP alternatives: 11k freed
[    0.027696] ACPI: Core revision 20080609
[    0.030704] ACPI: Checking initramfs for custom DSDT
[    0.502117] ACPI: setting ELCR to 0200 (from 0c00)
[    0.504104] weird, boot CPU (#0) not listedby the BIOS.
[    0.504107] SMP motherboard not detected.
[    0.504111] Local APIC not detected. Using dummy APIC emulation.
[    0.504114] SMP disabled
[    0.504198] Brought up 1 CPUs
[    0.504202] Total of 1 processors activated (2999.64 BogoMIPS).
[    0.504218] CPU0 attaching NULL sched-domain.
[    0.504526] net_namespace: 840 bytes
[    0.504542] Booting paravirtualized kernel on bare hardware
[    0.508037] Time: 23:31:07  Date: 05/20/09
[    0.508075] NET: Registered protocol family 16
[    0.508444] EISA bus registered
[    0.508464] ACPI: bus type pci registered
[    0.510040] PCI: PCI BIOS revision 2.10 entry at 0xfd6c4, last bus=3
[    0.510044] PCI: Using configuration type 1 for base access
[    0.511910] ACPI: EC: Look up EC in DSDT
[    0.515061] ACPI: Interpreter enabled
[    0.515068] ACPI: (supports S0 S3 S4 S5)
[    0.515088] ACPI: Using PIC for interrupt routing
[    0.515943] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.922451] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.922455] ACPI: EC: driver started in interrupt mode
[    0.922518] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.922697] PCI: 0000:00:02.0 reg 10 32bit mmio: [e8000000, efffffff]
[    0.922703] PCI: 0000:00:02.0 reg 14 32bit mmio: [e0000000, e007ffff]
[    0.922709] PCI: 0000:00:02.0 reg 18 io port: [1800, 1807]
[    0.922729] pci 0000:00:02.0: supports D1
[    0.922745] PCI: 0000:00:02.1 reg 10 32bit mmio: [f0000000, f7ffffff]
[    0.922751] PCI: 0000:00:02.1 reg 14 32bit mmio: [e0080000, e00fffff]
[    0.922773] pci 0000:00:02.1: supports D1
[    0.922840] PCI: 0000:00:1d.0 reg 20 io port: [1820, 183f]
[    0.922889] PCI: 0000:00:1d.1 reg 20 io port: [1840, 185f]
[    0.922938] PCI: 0000:00:1d.2 reg 20 io port: [1860, 187f]
[    0.922993] PCI: 0000:00:1d.7 reg 10 32bit mmio: [e0100000, e01003ff]
[    0.923043] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.923049] pci 0000:00:1d.7: PME# disabled
[    0.923120] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.923129] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    0.923134] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH4 GPIO
[    0.923156] PCI: 0000:00:1f.1 reg 10 io port: [0, 7]
[    0.923163] PCI: 0000:00:1f.1 reg 14 io port: [0, 3]
[    0.923170] PCI: 0000:00:1f.1 reg 18 io port: [0, 7]
[    0.923177] PCI: 0000:00:1f.1 reg 1c io port: [0, 3]
[    0.923184] PCI: 0000:00:1f.1 reg 20 io port: [1810, 181f]
[    0.923192] PCI: 0000:00:1f.1 reg 24 32bit mmio: [0, 3ff]
[    0.923238] PCI: 0000:00:1f.3 reg 20 io port: [1880, 189f]
[    0.923278] PCI: 0000:00:1f.5 reg 10 io port: [1c00, 1cff]
[    0.923285] PCI: 0000:00:1f.5 reg 14 io port: [18c0, 18ff]
[    0.923292] PCI: 0000:00:1f.5 reg 18 32bit mmio: [e0100c00, e0100dff]
[    0.923299] PCI: 0000:00:1f.5 reg 1c 32bit mmio: [e0100800, e01008ff]
[    0.923325] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.923330] pci 0000:00:1f.5: PME# disabled
[    0.923354] PCI: 0000:00:1f.6 reg 10 io port: [2400, 24ff]
[    0.923360] PCI: 0000:00:1f.6 reg 14 io port: [2000, 207f]
[    0.923393] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.923399] pci 0000:00:1f.6: PME# disabled
[    0.923433] PCI: 0000:02:03.0 reg 10 32bit mmio: [e0202000, e0202fff]
[    0.923471] pci 0000:02:03.0: supports D1
[    0.923473] pci 0000:02:03.0: supports D2
[    0.923476] pci 0000:02:03.0: PME# supported from D0 D1 D2 D3hot
[    0.923481] pci 0000:02:03.0: PME# disabled
[    0.923506] PCI: 0000:02:05.0 reg 10 32bit mmio: [e0200000, e0201fff]
[    0.923532] PCI: 0000:02:05.0 reg 30 32bit mmio: [0, ffff]
[    0.923546] pci 0000:02:05.0: supports D1
[    0.923548] pci 0000:02:05.0: supports D2
[    0.923551] pci 0000:02:05.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.923555] pci 0000:02:05.0: PME# disabled
[    0.923582] PCI: 0000:02:06.0 reg 10 32bit mmio: [e0203000, e0203fff]
[    0.923622] pci 0000:02:06.0: PME# supported from D0 D3hot D3cold
[    0.923627] pci 0000:02:06.0: PME# disabled
[    0.923656] PCI: 0000:02:09.0 reg 10 32bit mmio: [0, fff]
[    0.923670] pci 0000:02:09.0: supports D1
[    0.923672] pci 0000:02:09.0: supports D2
[    0.923675] pci 0000:02:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.923680] pci 0000:02:09.0: PME# disabled
[    0.923705] pci 0000:00:1e.0: transparent bridge
[    0.923713] PCI: bridge 0000:00:1e.0 32bit mmio: [e0200000, e02fffff]
[    0.923738] bus 00 -> node 0
[    0.923747] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.924155] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.930790] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 *11)
[    0.930932] ACPI: PCI Interrupt Link [LNKB] (IRQs *10 11)
[    0.931071] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 *11)
[    0.931208] ACPI: PCI Interrupt Link [LNKD] (IRQs *11)
[    0.931346] ACPI: PCI Interrupt Link [LNKE] (IRQs *10 11)
[    0.931483] ACPI: PCI Interrupt Link [LNKF] (IRQs *10 11)
[    0.931628] ACPI: PCI Interrupt Link [LNKG] (IRQs *10 11)
[    0.931766] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 *11)
[    0.931976] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.932019] pnp: PnP ACPI init
[    0.932042] ACPI: bus type pnp registered
[    1.137414] pnp: PnP ACPI: found 12 devices
[    1.137418] ACPI: ACPI bus type pnp unregistered
[    1.137424] PnPBIOS: Disabled by ACPI PNP
[    1.137850] PCI: Using ACPI for IRQ routing
[    1.137996] NET: Registered protocol family 8
[    1.137996] NET: Registered protocol family 20
[    1.137996] NetLabel: Initializing
[    1.137996] NetLabel:  domain hash size = 128
[    1.137996] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.137996] NetLabel:  unlabeled traffic allowed by default
[    1.137996] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    1.137996]    actual entries 65620
[    1.137996] AppArmor: AppArmor Filesystem Enabled
[    1.137996] ACPI: RTC can wake from S4
[    1.137996] system 00:04: ioport range 0x600-0x60f has been reserved
[    1.137996] system 00:04: ioport range 0x700-0x70f has been reserved
[    1.137996] system 00:04: ioport range 0x800-0x80f has been reserved
[    1.137996] system 00:04: ioport range 0x1000-0x107f has been reserved
[    1.137996] system 00:04: ioport range 0x1180-0x11bf has been reserved
[    1.137996] system 00:04: iomem range 0xfec10000-0xfec1ffff could not be reserved
[    1.173911] pci 0000:02:09.0: CardBus bridge, secondary bus 0000:03
[    1.173915] pci 0000:02:09.0:   IO window: 0x003000-0x0030ff
[    1.173921] pci 0000:02:09.0:   IO window: 0x003400-0x0034ff
[    1.173926] pci 0000:02:09.0:   PREFETCH window: 0x30000000-0x33ffffff
[    1.173931] pci 0000:02:09.0:   MEM window: 0x38000000-0x3bffffff
[    1.173936] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    1.173941] pci 0000:00:1e.0:   IO window: 0x3000-0x3fff
[    1.173947] pci 0000:00:1e.0:   MEM window: 0xe0200000-0xe02fffff
[    1.173953] pci 0000:00:1e.0:   PREFETCH window: 0x00000030000000-0x00000035ffffff
[    1.173966] pci 0000:00:1e.0: enabling device (0005 -> 0007)
[    1.173974] pci 0000:00:1e.0: setting latency timer to 64
[    1.174242] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 10
[    1.174246] PCI: setting IRQ 10 as level-triggered
[    1.174251] pci 0000:02:09.0: PCI INT A -> Link[LNKF] -> GSI 10 (level, low) -> IRQ 10
[    1.174259] bus: 00 index 0 io port: [0, ffff]
[    1.174262] bus: 00 index 1 mmio: [0, ffffffff]
[    1.174265] bus: 02 index 0 io port: [3000, 3fff]
[    1.174268] bus: 02 index 1 mmio: [e0200000, e02fffff]
[    1.174270] bus: 02 index 2 mmio: [30000000, 35ffffff]
[    1.174273] bus: 02 index 3 io port: [0, ffff]
[    1.174276] bus: 02 index 4 mmio: [0, ffffffff]
[    1.174279] bus: 03 index 0 io port: [3000, 30ff]
[    1.174282] bus: 03 index 1 io port: [3400, 34ff]
[    1.174285] bus: 03 index 2 mmio: [30000000, 33ffffff]
[    1.174288] bus: 03 index 3 mmio: [38000000, 3bffffff]
[    1.174305] NET: Registered protocol family 2
[    1.174485] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    1.174804] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    1.174935] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    1.175068] TCP: Hash tables configured (established 16384 bind 16384)
[    1.175073] TCP reno registered
[    1.175176] NET: Registered protocol family 1
[    1.175335] checking if image is initramfs... it is
[    1.676091] Switched to high resolution mode on CPU 0
[    2.152170] Freeing initrd memory: 8263k freed
[    2.152474] Simple Boot Flag at 0x36 set to 0x1
[    2.153025] audit: initializing netlink socket (disabled)
[    2.153055] type=2000 audit(1242862268.152:1): initialized
[    2.160394] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.163528] VFS: Disk quotas dquot_6.5.1
[    2.163655] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.163799] msgmni has been set to 985
[    2.163976] io scheduler noop registered
[    2.163980] io scheduler anticipatory registered
[    2.163983] io scheduler deadline registered
[    2.164035] io scheduler cfq registered (default)
[    2.164063] pci 0000:00:02.0: Boot video device
[    2.164666] isapnp: Scanning for PnP cards...
[    2.518359] isapnp: No Plug & Play device found
[    2.568719] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.569003] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    2.570004] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[    2.570010] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[    2.570020] serial 0000:00:1f.6: PCI INT B disabled
[    2.571969] brd: module loaded
[    2.572429] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.572595] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.575303] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.576532] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.576539] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.576542] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.576546] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.576549] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.577129] mice: PS/2 mouse device common for all mice
[    2.577304] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    2.577323] rtc0: alarms up to one month, y3k
[    2.577469] EISA: Probing bus 0 at eisa.0
[    2.577478] Cannot allocate resource for EISA slot 1
[    2.577482] Cannot allocate resource for EISA slot 2
[    2.577486] Cannot allocate resource for EISA slot 3
[    2.577508] EISA: Detected 0 cards.
[    2.577512] cpuidle: using governor ladder
[    2.577516] cpuidle: using governor menu
[    2.578309] TCP cubic registered
[    2.578357] Using IPI No-Shortcut mode
[    2.578613] registered taskstats version 1
[    2.578778]   Magic number: 9:415:555
[    2.578904] tty ptya1: hash matches
[    2.579015] pci_link PNP0C0F:06: hash matches
[    2.579056] rtc_cmos 00:01: setting system clock to 2009-05-20 23:31:09 UTC (1242862269)
[    2.579061] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.579064] EDD information not available.
[    2.579359] Freeing unused kernel memory: 424k freed
[    2.579422] Write protecting the kernel text: 2580k
[    2.579462] Write protecting the kernel read-only data: 940k
[    2.607086] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.880061] fuse init (API version 7.9)
[    3.163265] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    3.163338] processor ACPI0007:00: registered as cooling_device0
[    3.163344] ACPI: Processor [CPU0] (supports 8 throttling states)
[    3.235035] thermal LNXTHERM:01: registered as thermal_zone0
[    3.268630] ACPI: Thermal Zone [THRS] (52 C)
[    3.336628] thermal LNXTHERM:02: registered as thermal_zone1
[    3.370219] ACPI: Thermal Zone [THRC] (60 C)
[    4.267949] usbcore: registered new interface driver usbfs
[    4.267987] usbcore: registered new interface driver hub
[    4.276576] No dock devices found.
[    4.318703] usbcore: registered new device driver usb
[    4.361256] SCSI subsystem initialized
[    4.361667] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    4.361671] PCI: setting IRQ 11 as level-triggered
[    4.361678] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    4.361695] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    4.361700] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.361763] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    4.365658] ehci_hcd 0000:00:1d.7: debug port 1
[    4.365666] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    4.365679] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xe0100000
[    4.374153] USB Universal Host Controller Interface driver v3.0
[    4.384171] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.384452] usb usb1: configuration #1 chosen from 1 choice
[    4.384494] hub 1-0:1.0: USB hub found
[    4.384510] hub 1-0:1.0: 6 ports detected
[    4.575243] libata version 3.00 loaded.
[    4.592763] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    4.592771] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    4.592783] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    4.592788] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.592826] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    4.592854] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001820
[    4.593004] usb usb2: configuration #1 chosen from 1 choice
[    4.593040] hub 2-0:1.0: USB hub found
[    4.593051] hub 2-0:1.0: 2 ports detected
[    4.704126] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    4.801043] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    4.801051] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    4.801064] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    4.801069] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.801109] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    4.801138] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001840
[    4.801304] usb usb3: configuration #1 chosen from 1 choice
[    4.801341] hub 3-0:1.0: USB hub found
[    4.801351] hub 3-0:1.0: 2 ports detected
[    4.838142] usb 1-2: configuration #1 chosen from 1 choice
[    4.904719] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    4.904727] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    4.904740] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    4.904745] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.904784] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    4.904813] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001860
[    4.904959] usb usb4: configuration #1 chosen from 1 choice
[    4.904997] hub 4-0:1.0: USB hub found
[    4.905022] hub 4-0:1.0: 2 ports detected
[    5.008473] ata_piix 0000:00:1f.1: version 2.12
[    5.008490] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    5.008501] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    5.008558] ata_piix 0000:00:1f.1: setting latency timer to 64
[    5.008655] scsi0 : ata_piix
[    5.008794] scsi1 : ata_piix
[    5.010266] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    5.010270] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    5.040911] usbcore: registered new interface driver libusual
[    5.054060] Initializing USB Mass Storage driver...
[    5.054522] scsi2 : SCSI emulation for USB Mass Storage devices
[    5.054635] usbcore: registered new interface driver usb-storage
[    5.054640] USB Mass Storage support registered.
[    5.054755] usb-storage: device found at 2
[    5.054758] usb-storage: waiting for device to settle before scanning
[    5.100552] Marking TSC unstable due to TSC halts in idle
[    5.172572] ata1.00: ATA-6: FUJITSU MHT2060AT, 0022, max UDMA/100
[    5.172577] ata1.00: 117210240 sectors, multi 16: LBA 
[    5.188523] ata1.00: configured for UDMA/100
[    5.344195] ata2.01: NODEV after polling detection
[    5.352517] ata2.00: ATAPI: QSI     DVDRW SDW-041, DU05, max UDMA/33
[    5.368463] ata2.00: configured for UDMA/33
[    5.368626] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHT2060A 0022 PQ: 0 ANSI: 5
[    5.368940] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    5.370968] scsi 1:0:0:0: CD-ROM            QSI      DVDRW SDW-041    DU05 PQ: 0 ANSI: 5
[    5.371134] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    5.378366] ohci1394 0000:02:03.0: PCI INT A -> Link[LNKF] -> GSI 10 (level, low) -> IRQ 10
[    5.430133] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[10]  MMIO=[e0202000-e02027ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    5.442888] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
[    5.442894] b44 0000:02:05.0: PCI INT A -> Link[LNKE] -> GSI 10 (level, low) -> IRQ 10
[    5.500123] ssb: Sonics Silicon Backplane found on PCI device 0000:02:05.0
[    5.504778] b44.c:v2.0
[    5.524514] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:0a:e4:28:20:4a
[    5.600470] Driver 'sd' needs updating - please use bus_type methods
[    5.604203] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[    5.604225] sd 0:0:0:0: [sda] Write Protect is off
[    5.604229] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.604259] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.604354] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[    5.604371] sd 0:0:0:0: [sda] Write Protect is off
[    5.604374] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.604403] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.604408]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    5.688621]  sda1
[    5.688776] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.700346] sr0: scsi3-mmc drive: 12x/24x writer cd/rw xa/form2 cdda tray
[    5.700353] Uniform CD-ROM driver Revision: 3.20
[    5.700511] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    6.349008] loop: module loaded
[    6.411473] kjournald starting.  Commit interval 5 seconds
[    6.411495] EXT3-fs: mounted filesystem with ordered data mode.
[    6.712210] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[04e40a009b172036]
[   10.052363] usb-storage: device scan complete
[   10.052837] scsi 2:0:0:0: Direct-Access     SanDisk  U3 Contour       4.04 PQ: 0 ANSI: 2
[   10.053200] scsi 2:0:0:1: CD-ROM            SanDisk  U3 Contour       4.04 PQ: 0 ANSI: 2
[   10.054177] sd 2:0:0:0: [sdb] 8013457 512-byte hardware sectors (4103 MB)
[   10.054675] sd 2:0:0:0: [sdb] Write Protect is off
[   10.054678] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   10.054682] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   10.056293] sd 2:0:0:0: [sdb] 8013457 512-byte hardware sectors (4103 MB)
[   10.056805] sd 2:0:0:0: [sdb] Write Protect is off
[   10.056809] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   10.056812] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   10.056817]  sdb: sdb1
[   10.057581] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   10.057831] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   10.058680] sr1: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[   10.058768] sr 2:0:0:1: Attached scsi CD-ROM sr1
[   10.058845] sr 2:0:0:1: Attached scsi generic sg3 type 5
[   16.172139] Clocksource tsc unstable (delta = -125646997 ns)
[   17.059517] udevd version 124 started
[   18.412111] iTCO_vendor_support: vendor-support=0
[   18.528518] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   18.531140] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   18.531367] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   18.559755] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   18.625125] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.724945] Linux agpgart interface v0.103
[   18.731150] agpgart-intel 0000:00:00.0: Intel 855GM Chipset
[   18.731461] agpgart-intel 0000:00:00.0: detected 8060K stolen memory
[   18.741381] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe8000000
[   18.904027] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   18.916034] ACPI: Power Button (FF) [PWRF]
[   18.919571] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[   18.919769] ACPI: Lid Switch [LID]
[   18.919892] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   18.928034] ACPI: Sleep Button (CM) [SLP2]
[   18.989546] intel_rng: FWH not detected
[   19.151723] ACPI: AC Adapter [AC] (on-line)
[   19.344359] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   20.264136] ACPI: Battery Slot [BAT0] (battery present)
[   20.265604] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:03/input/input6
[   20.276036] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   20.390218] irda_init()
[   20.390236] NET: Registered protocol family 23
[   20.756512] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   20.756549] nsc-ircc, chip->init
[   20.756559] nsc-ircc, Found chip at base=0x02e
[   20.756584] nsc-ircc, driver loaded (Dag Brattli)
[   20.756591] nsc_ircc_open(), can't get iobase of 0x2f8
[   20.756619] nsc-ircc, Found chip at base=0x02e
[   20.756644] nsc-ircc, driver loaded (Dag Brattli)
[   20.756647] nsc_ircc_open(), can't get iobase of 0x2f8
[   20.756893] nsc-ircc 00:09: disabled
[   20.837236] parport_pc 00:08: reported by Plug and Play ACPI
[   20.837295] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   21.256661] ieee80211_crypt: registered algorithm 'NULL'
[   21.320206] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   21.320212] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   21.497917] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   21.497922] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   21.498311] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 10
[   21.498318] ipw2200 0000:02:06.0: PCI INT A -> Link[LNKG] -> GSI 10 (level, low) -> IRQ 10
[   21.499184] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   21.499257] firmware: requesting ipw2200-bss.fw
[   22.113322] wbsd: Winbond W83L51xD SD/MMC card interface driver
[   22.113327] wbsd: Copyright(c) Pierre Ossman
[   22.118539] mmc0: W83L51xD id 7112 at 0x820 irq 6 FIFO PnP
[   22.288935] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x9248b1, caps: 0x904713/0x4000
[   22.326934] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   25.135693] ipw2200: Radio Frequency Kill Switch is On:
[   25.135697] Kill switch must be turned off for wireless networking to work.
[   25.211350] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   25.211460] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   25.211499] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   25.211534] Yenta: CardBus bridge found at 0000:02:09.0 [1734:1033]
[   25.211551] Yenta: Using CSCINT to route CSC interrupts to PCI
[   25.211554] Yenta: Routing CardBus interrupts to PCI
[   25.211560] Yenta TI: socket 0000:02:09.0, mfunc 0x01001002, devctl 0x64
[   25.440471] Yenta: ISA IRQ mask 0x0018, PCI irq 10
[   25.440477] Socket status: 30000020
[   25.440481] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   25.440490] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   25.440514] cs: IO port probe 0x3000-0x3fff: clean.
[   25.440817] pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
[   25.440822] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x35ffffff
[   26.076138] pccard: CardBus card inserted into slot 0
[   26.076180] PCI: 0000:03:00.0 reg 10 32bit mmio: [0, ffff]
[   26.178688] cs: IO port probe 0x100-0x3af: clean.
[   26.180857] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   26.181562] cs: IO port probe 0x820-0x8ff: excluding 0x840-0x847
[   26.182115] cs: IO port probe 0xc00-0xcf7: clean.
[   26.182880] cs: IO port probe 0xa00-0xaff: clean.
[   26.240600] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   26.492032] intel8x0_measure_ac97_clock: measured 55331 usecs
[   26.492037] intel8x0: clocking to 48000
[   26.626130] ndiswrapper (load_wrap_driver:108): couldn't load driver netathr; check system log for messages from 'loadndisdriver'
[   26.627506] usbcore: registered new interface driver ndiswrapper
[   27.125133] lp0: using parport0 (interrupt-driven).
[   28.149209] EXT3 FS on loop0, internal journal
[   66.797638] Adding 976552k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:860 across:1156964k
[   67.134090] type=1505 audit(1242855134.208:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4099
[   67.403457] type=1505 audit(1242855134.476:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4104
[   67.403869] type=1505 audit(1242855134.476:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4104
[   67.643239] ip_tables: (C) 2000-2006 Netfilter Core Team
[   68.579368] ACPI: WMI: Mapper loaded
[   69.905863] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   69.964718] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   69.964727] apm: overridden by ACPI.
[   70.170073] ppdev: user-space parallel port driver
[   72.501588] ttyS1: LSR safety check engaged!
[   72.571510] cdrom: This disc doesn't have any tracks I recognize!
[   72.850601] Bluetooth: Core ver 2.13
[   72.853854] NET: Registered protocol family 31
[   72.853867] Bluetooth: HCI device and connection manager initialized
[   72.853878] Bluetooth: HCI socket layer initialized
[   72.930884] Bluetooth: L2CAP ver 2.11
[   72.930891] Bluetooth: L2CAP socket layer initialized
[   72.972599] Bluetooth: RFCOMM socket layer initialized
[   72.972918] Bluetooth: RFCOMM TTY layer initialized
[   72.972924] Bluetooth: RFCOMM ver 1.10
[   72.974048] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   72.974054] Bluetooth: BNEP filters: protocol multicast
[   73.038592] Bridge firewalling registered
[   73.073477] Bluetooth: SCO (Voice Link) ver 0.6
[   73.073485] Bluetooth: SCO socket layer initialized
[   77.546320] [drm] Initialized drm 1.1.0 20060810
[   77.568109] pci 0000:00:02.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   77.568125] pci 0000:00:02.0: setting latency timer to 64
[   77.570237] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   77.570256] pci 0000:00:02.1: setting latency timer to 64
[   77.571795] [drm] Initialized i915 1.6.0 20060119 on minor 1
[  110.613561] ISO 9660 Extensions: Microsoft Joliet Level 3
[  110.615682] ISOFS: changing to secondary root
[  208.044626] ppdev0: registered pardevice
[  208.187315] ppdev0: unregistered pardevice
[  208.243969] ttyS1: LSR safety check engaged!
[  208.244003] type=1503 audit(1242855275.320:5): operation="capable" name="sys_admin" pid=5735 profile="/usr/sbin/cupsd"
[  209.191669] ppdev0: registered pardevice
[  209.240990] ppdev0: unregistered pardevice
[  209.332907] ppdev0: registered pardevice
[  209.380115] ppdev0: unregistered pardevice

[B]I would be extremely grateful if you could help resolve this problem.. I'm losing so much time jumping back and forth between XP and Ubuntu and I would really like to spend some more time exploring Ubuntu.

Many thanks for all help!

drufi

While trying to uninstall the madwifi.sh... the idea came to me that i might have overdone it i.e. installed to many drivers for the same hardware. I thus checked and sure enough i still had ndisgkt and ndiswrapper installed... I uninstalled both and reenabled the ubuntu drivers for the atheros 5xxx and it suddenly worked... It suppose that my initial appreciation of the problem was the secured network. But since this one is not, it works perfectly.
Sometimes we just stumble on answers :)
[/B]

Seems like that (very old) version of MadWifi doesn't compile on your system for some reason such as changed kernel API. Probably a newer version would, but since you already have your wifi working perfectly with ath5k I think you should stick to it. 

There are several benefits in using ath5k instead of MadWifi. Just to name a few, ath5k is a newer project and it's completely open source whereas MadWifi is partly closed source. ath5k is intended to replace MadWifi, it's in the Linux kernel source tree and it's also in more active development. That means ath5k upgrades automatically with Ubuntu kernel/module updates. MadWifi needs to be recompiled after every kernel update and upgrades are not automatic.

---

### Post by Drufi on 2009-05-23
Hey Kajaste,

Many thanks for your reply to my query. I was a bit over enjoyed when I edited my post i.e. I hadn't restarted :) 
Having done that, the wireless was again disabled but I found a workaround although I have to repeat it on each boot.
I quickly explain it in [http://ubuntuforums.org/showthread.php?t=1167811](http://ubuntuforums.org/showthread.php?t=1167811)

Many thanks again,
drufi

---

### Post by duruttye on 2009-06-10
Hey guys!

Due to some update I just lost my huawei vodafone mobile connection. I have a wireless network at home, but I had to buy some cables to be able to use the ethernet card, because the wireless is gone, too :). I'm using a dell vostro a680, and ubuntu 9.04.

outputs:
lspci
[HTML]09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
0c:00.0 Network controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)[/HTML]

[HTML]sudo ./madwifi.sh --info
Found at least one Atheros device.
Linux ubuntuboxdell 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
Distro: Debian
0c:00.0 Network controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Device 1a32:0112
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f6cf0000 (64-bit, non-prefetchable) [size=64K]
	Kernel driver in use: ath5k
	Kernel modules: ath_pci, ath5k

ath_pci               208440  0 
wlan                  234352  1 ath_pci
ath_hal               371488  1 ath_pci
wifi0: 0 ath0: 0
[/HTML]

[HTML]$ iwlist wlan0 scan
wlan0     No scan results
[/HTML]

[HTML]$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:21:70:8e:ad:42  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:70ff:fe8e:ad42/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:6987 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5905 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7853459 (7.8 MB)  TX bytes:473336 (473.3 KB)
          Interrupt:252 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:17:c4:4e:cd:69  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-17-C4-4E-CD-69-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
[/HTML]

[HTML]lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
[/HTML]

The hardware driver says that a different version of the madwifi driver is in the use. There is no change when I deactivate it.

In case somebody needs some additional information, just ask!

I don't know what could I do without this forum... I am sure I won't be Ubuntu user for long...

thanx guys!

---

### Post by duruttye on 2009-06-12
It turns out that the update didn't break my wireless, it actually fixed it! Until now, the Fn+wireless button didn't work at all, the led was always off, but the wireless was always on. Now, I can switch it on and off, the led isn't on, but that is not a problem. Ohh, and I was mad at ubuntu for a few weeks now!!!

---

### Post by wowiesy on 2009-06-18
Will this also be good for an Atheros WLAN for Master mode use?  


I'm now trying to compile the madwifi driver (which I downloaded manually) and I'm getting compile errors.  lspci and iwconfig shows a wireless interface but I haven't tested it if it's working in managed mode - actually I don't know how to test it in manual mode in a purely command line interface environment.   But assuming I get to test it and it works, I've done the test if the card can go master mode, it already failed, I read that this shows that the driver doesn't support master mode.  

Will following the instructions here enable master mode?

---

### Post by n1ght28 on 2009-06-26
hey not having any luck here

ran the script, even the sudo modprobe -r ath5k  as i'm currently using athh9k drivers but the outout from lshw -C network is still


```
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 01
       serial: 00:22:43:71:da:fc
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.1.70 latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn

```

i'm running easy peasy ubuntu on a eeepc 1000HE which is a derivantive of ubuntu but it has its own reestricted module package, 

is this the problem,
can i mod the script to make it work,
where do i need to mod it?

sudo modprobe -r ath5k

---

### Post by Kajaste on 2009-09-01
> **n1ght28 said:**
> 
ran the script, even the sudo modprobe -r ath5k  as i'm currently using athh9k drivers

You're supposed to run sudo modprobe -r ath9k when you're using the ath9k driver.

---

### Post by inokungfu on 2009-09-26
Worked great on 32bit 9.04 with AR5212. Thanks!

---

### Post by kanibalv on 2009-09-27
Anyone knows if this work on kubuntu karmic, which doesn't suport madwifi anymore.
This in my machine:
Linux G60 2.6.31-11-generic #36-Ubuntu SMP Fri Sep 25 06:37:23 UTC 2009 x86_64 GNU/Linux
Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


:confused::confused::confused::confused::confused:



Resolved: I don't know what I did, but is working know. using wpa_supplicant and ath5k. Mysteriously work when I changed the Channel of the router.

---

### Post by jdhawk on 2009-10-03
Just tried this on 9.10 Beta - Toshiba pa3233u-1mpc with Atheros AR5211

```

Installing MadWifi.WARNING: -e needs -E or -F
.WARNING: -e needs -E or -F.OK
Loading kernel module...OK
Adding ath_pci to /etc/modules...OK

It seems that the driver did not detect compatible hardware.
Please try to connect to an AP. If it doesn't work, see the 
Troubleshooting part in the forum. If after reading the Troubleshooting
part and the WHOLE THREAD it still doesn't work, post your
sudo ./madwifi.sh --info output to the forum.


```

After that, network manager did not work properly, so...

I'm not sure if all these steps are necessary, but I removed everything, including the driver ubuntu was trying to use (ath5k), then reloaded the 3 madwifi modules, and did a depmod -a.

Works now.

```

root@godzilla:~# madwifi-unload 
Unloading "ath_pci"
Unloading "wlan"
Unloading "ath_hal"
root@godzilla:~# rmmod ath5k
root@godzilla:~# modprobe wlan
root@godzilla:~# modprobe ath_pci
root@godzilla:~# modprobe ath_hal
root@godzilla:~# depmod -a

```

---

### Post by musicboy1125 on 2009-12-20
thanks so much for this. I'm hoping it will work.

I've been without wireless for a year now.

---

### Post by Ian Ferguson on 2010-05-13
I never had any problems with my Atheros AR5001 wifi till I upgraded from 9.10 to 10.04, but this has fixed it. Great to have a script handy to repeat the process whenever a kernel update breaks Madwifi!
:)

---

### Post by evgen_m on 2010-10-19
[B]I did this and it works. thank you!!
----



Okay, so how do I use this script to install MadWifi?[/B]
Basically, if you have a working Internet connection (no worries if you don't, see below), all you need to do is download the script
 	Code:
 	wget [http://kolmoskone.homelinux.org/~kaja/kamaa/madwifi.sh](http://kolmoskone.homelinux.org/~kaja/kamaa/madwifi.sh) -O madwifi.sh
chmod +x madwifi.sh 
(you can also upgrade your current madwifi.sh to the latest version with these commands)

And then run it with sudo
 	Code:
 	sudo ./madwifi.sh

---

### Post by IIC0RRUPT10NII on 2010-10-27
It seems that the driver did not detect compatible hardware.
Please try to connect to an AP. If it doesn't work, see the 
Troubleshooting part in the forum. If after reading the Troubleshooting
part and the WHOLE THREAD it still doesn't work, post your
sudo ./madwifi.sh --info output to the forum.
c0rrupt10n@iic0rrupt10nii-r00t:/etc/default$ 
c0rrupt10n@iic0rrupt10nii-r00t:/etc/default$ sudo ./madwifi.sh --info output
Found at least one Atheros device.
Linux iic0rrupt10nii-r00t 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:48:22 UTC 2010 i686 GNU/Linux
Distro: Debian
02:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
    Subsystem: Toshiba America Info Systems Device ff1e
    Flags: bus master, fast devsel, latency 0, IRQ 29
    Memory at 95600000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at 3000 [size=128]
    Kernel driver in use: atl1c
    Kernel modules: atl1c

ath_pci               193197  0 
wlan                  222892  1 ath_pci
ath_hal               398604  1 ath_pci
[    0.120338]  [<c014c6e2>] warn_slowpath_common+0x72/0xa0
[    0.120346]  [<c014c75b>] warn_slowpath_fmt+0x2b/0x30
[    0.120624]  [<c014c6e2>] warn_slowpath_common+0x72/0xa0
[    0.120632]  [<c014c75b>] warn_slowpath_fmt+0x2b/0x30
wifi0: 0 ath0: 0

---

### Post by scotiangold on 2010-11-02
I just resolved a problem getting a wireless connection from my Acer Aspire Netbook with Atheros AR5XXXX wireless adapter to my D-Link DIR-625 Router that I want to share if it saves someone the wasted time it took me to figure it out.

The mac address for the Atheros wireless device actually sent to the router is different from that reported by the network manager in Ubuntu on the Netbook. I only clued in when checking the router logs. Once I configured the router to accept this mac address no problem connecting.

---

