---
title: "Wireless troubles on Dell Vostro 3700 - Broadcom drivers."
date: 2010-07-17
forum: Hardware
---

### Post by michele.bartolettistella on 2010-07-17
Here we are!

Dear John,

to properly activate your wireless, try the following instructions.

. Go to "System > Administration > Driver Hardware" and disable  "Driver Broadcom STA Wireless";
. Reboot your PC;
. Connect your PC by cable and download this [Driver]("http://www.broadcom.com/docs/linux_sta/hybrid-portsrc-x86_32-v5.60.48.36.tar.gz") (you can also get it through another PC and copy then to your Dell Vostro 3700, of course);
. Extract the .tar archive ("[Mouse right button] > Extract here");
. Copy the folder just created to your home directory (home/[yourname]/) and rename it as "hybrid_wl";
. Open a terminal (should be "Applications > Accessories > Terminal") and write:
```

cd hybrid_wl
make clean
make
```You should see that some new files has been created in "hybrid_wl": in particular, check if a file named "wl.ko" has been created; this is our precious driver. You now must install wl.ko. So:

. In the Terminal:
```
rmmod b43
rmmod ssb
rmmod wl
```Then:
```
modprobe lib80211
modprobe ieee80211_crypt_tkip
insmod wl.ko
```Now your driver should be operational. Check if your computer is now able to detect the wireless network available on air.

Anyway, you must make your system to automatically open the driver at every boot. So try to write in the Terminal as follow:
```
sh: for i in `find /lib /var -name wl\.ko`; do mv $i ${i}.orig; done
```And reboot your system to see if the wireless automatically detect the networks.

Probably you will encounter some issues and error alerts: if so, take note of them and write me! ;-)

---
Please note:
. Whenever the Terminal doesn't execute an instruction and replies that "you don't have enough permissions to ask me this", you have to retype the instruction preceded by the "sudo" passpartout:
```

sudo [your instruction]
```and type the root password, as requested.

---

### Post by michele.bartolettistella on 2010-07-18
Dear John,

I was also thinking about 32bit/64bit...

In fact, my Vostro runs under Windows 7 Professional 64bit, so I also initially tried the 64bit drivers, but the procedure failed; so I tried with the 32 bit version, and I succeded...

Anyway, all the Broadcom drivers for Linux are available [_**here**_]("http://www.broadcom.com/support/802.11/linux_sta.php"): you can download the 64bit version, so we can try with them.

But before proceeding, please run these instructions on the Terminal:
```
sudo apt-get install build-essential linux-headers-generic
sudo apt-get build-dep linux
```This is to verify that you have all the building modules properly installed in your system; note that you have here to be connected by cable to permit your Ubuntu to search its archive for the missing modules.

Now delete all the files in hybrid_wl, and extract the new package (hybrid-portsrc-x86_64-v5.60.48.36.tar) in there.

Open the Terminal, move to hybrid_wl and build the package:
```
cd hybrid_wl
sudo make clean
sudo make
```Verify that a file named [COLOR=DarkRed]wl.ko[/COLOR] has been created in hybrid_wl; if not, extract again also the 32bit package into hybrid_wl, together with the 64bit files, and try again the* make *instructions as above.

After that, tell me if you succeded, so we can go on with the installing procedures of the drivers; otherwise report me your error messages, so I can understand the situation better.

Stay in touch!

Michele

---

### Post by berni4385 on 2010-07-23
Hi,
i'm trying to install the drives like you described, and i've got my wl.ko and when i load it manually my wlan works fine. The only problem i still have, is that your "sh: ..." command doesn't work properly, because i don't have any old wl.ko's. So where should i put my new wl.ko and how can i load it at every startup? Probably a basic question, but help is really appreciated! :)

david

---

### Post by michele.bartolettistella on 2010-07-23
Dear David,

I also encountered this problem: there is probably something wrong in the instruction syntax, but I don't know what precisely: I got it from official Broadcom Support.

Anyway, you can try this:

```
sudo -s
echo modeprobe wl >> /etc/rc.local
```Moreover, go to /lib/modules/`uname -r`/kernel/drivers/net/wireless and manually copy wl.ko from the directory you have created when you built the driver, eventually overwriting the old one: then reboot.

If you have a Dell Vostro 3700, take always a look to the wireless light located higher the F7 key, near the Bluetooth symbol; if the drivers are correctly installed to activate automatically at every startup, you will see that during the Ubuntu initialization it turns on: in this case the Broadcom is on.

---------

It seems that these issues are not so easy to solve: I added *[solved]* to the title of this thread, but in the next days I encountered some other troubles. Now my wireless card automatically turns on at every boot, it receives the signals and detects the networks, but I don't know exactly how I did.  :oops: If you want, I'll try to expose my attempts, in order to make also your Broadcom go on its own.

In my opinion the best thing to do is to install also the Broadcom drivers available in Synaptic. So open your packages repository:

```
sudo synaptic
``` and install the following modules:

bcmwl-kernel-source;
bcmwl-modaliases;
broadcom-sta-source;
broadcom-sta-common.

Then go to **System>Administration>Driver Harware** and activate the _Broadcom STA Wireless Driver_ third-part driver. Reboot and probably tou will see that the card automatically turns on.

Please let me know the situation after your attempts, because I need to clarify my ideas a bit more... ;)

---

### Post by j1nn on 2010-08-13
Thanks for the guide, it helped me to fix  my Broadcom.
I'd like to add a few more tips, to help someone who will encounter the same problems I did:

1. to blacklist b43 and ssb modules on boot, run:
```
echo 'blacklist b43' >> /etc/modprobe.d/blacklist.conf
echo 'blacklist ssb' >> /etc/modprobe.d/blacklist.conf
update-initramfs -u
```

2. to add our wl.ko on boot, after you copied it to /lib/modules/`uname -r`/kernel/drivers/net/wireless, run
```

depmod -a
echo 'lib80211' >> /etc/modules
echo 'ieee80211_crypt_tkip' >> /etc/modules
echo 'wl' >> /etc/modules

```

My Broadcom now is successfully loaded on boot, and loads after waking up from suspend.

Hope this helps someone.

---

### Post by michele.bartolettistella on 2010-08-13
Nice!

:)

---

