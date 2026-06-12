---
title: "Problem with Atheros Wiereless (AR5006EG) on Hardy"
date: 2008-07-11
forum: Hardware
---

### Post by apocalipsiz on 2008-07-11
Hi.

   I have a Sony Vaio Laptop model: VGN-NR330E with 2Gb of RAM, a Pentium Dual Core processor and a WLAN card Atheros (AR5006EG).

  I canot configure it, the driver is installed, when i check the Hardware Controlers everythig seems ok, Atheros... HAL is enabled and same for the Atheros wireless support, everything is enabled and in use.

 I had tried all that is posted in the forums,¨use madwifi¨...¨use ndiswarpper¨, but i don´t think the driver is the problem, because when i check the interfaces there´s only : lo and eth0 nothing else.

 Please help me... i´m over 2 weeks trying to fix this but i can´t.

Thanks!

---

### Post by almaddin on 2008-07-11
> **apocalipsiz said:**
> Hi.

   I have a Sony Vaio Laptop model: VGN-NR330E with 2Gb of RAM, a Pentium Dual Core processor and a WLAN card Atheros (AR5006EG).

  I canot configure it, the driver is installed, when i check the Hardware Controlers everythig seems ok, Atheros... HAL is enabled and same for the Atheros wireless support, everything is enabled and in use.

 I had tried all that is posted in the forums,¨use madwifi¨...¨use ndiswarpper¨, but i don´t think the driver is the problem, because when i check the interfaces there´s only : lo and eth0 nothing else.

 Please help me... i´m over 2 weeks trying to fix this but i can´t.

Thanks!


download at [http://snapshots.madwifi.org/special/](http://snapshots.madwifi.org/special/) :

madwifi-ng-r2756+ar5007.tar.gz
extract it.
open a terminal and type cd madwifi-ng-r2756+ar5007 and enter
use the command make and enter. Watch it do its work and
then type sudo make install and enter.
reboot and leftclick on the network manager and you will see every wireless network in your area. Then just click on the one you which connect to, type if necessary your password and it will connect.

Do however not forget to install the package build-essential first or it will only give you errors.
Second thing is that you will have to repeat these steps after every new kernel you have installed.

---

### Post by apocalipsiz on 2008-07-11
HI.


   Ok i'll do that (again), but i don't ensure anything, thanks.

---

### Post by apocalipsiz on 2008-07-11
Hi.

  I did what you told me.. but it apears the same old problem with madwifi... this is what happend when i "make" jeje:

Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/k~/N~/Software Linux/madwifi-ng-r2756+ar5007 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** No rule to make target `Linux/madwifi-ng-r2756+ar5007'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2


and this when i make install:
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/k~/N~/Software Linux/madwifi-ng-r2756+ar5007 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** No rule to make target `Linux/madwifi-ng-r2756+ar5007'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2

Thank you almaddin.

---

### Post by howlingmadhowie on 2008-07-11
i'm not sure about the atheros driver, but the usual procedure is:

./configure
make
sudo make install

however, seeing as you have already started a make, you'd best enter:

make clean

first, to make sure that any work make has alreay done is reverted to the basic state.

---

### Post by apocalipsiz on 2008-07-11
Hi.

   Somehow i did it... moving the folder to another directory like /home/ works for me (in the compilation and instalation of madwifi).. but here's the sad part, everything looks fine make fine ... but the interface doesn't appears (i mean the wlan interface) and with the Net Manager.. well the wireless connections also doesn't appear, so... in few words.. not functioning.

i don't know what to do..:confused:

thanks for the advices.

---

### Post by Zack McCool on 2008-07-11
> **apocalipsiz said:**
> 
 I had tried all that is posted in the forums,¨use madwifi¨...¨use ndiswarpper¨, but i don´t think the driver is the problem, because when i check the interfaces there´s only : lo and eth0 nothing else.

That's exactly what it means when folks say the driver is the problem...

Your 2 options are to get the madwifi update to work (updated atheros drivers that support your chipset) or to use ndiswrapper with the WinXP drivers.  If you choose to go the ndiswrapper route, let me know, as I have the XP driver.  The vista driver will not work.

---

### Post by howlingmadhowie on 2008-07-11
are you sure the wireless card is switched on in the bios?

what happens if you load the driver manually? 

sudo modprobe ath-pci

---

### Post by apocalipsiz on 2008-07-11
Hi.


    I tried with ndiswrapper and... yes.. used the xp driver but nothing happed, the wireless card is on , and when i use modprobe ath-pci... nothing happen now, but there was a moment when it works, but still the same problem, the wlan interface doesn't appear to be up or something, and i cannot make the config with the network manager. In the interface file only apears lo and eth0.

  The extrangest thing is that when i use mandriva everything works ok, but i like ubuntu that's why i'm taking all this problems jejej.

  Please help!!   :(

 Thanks!

---

### Post by apocalipsiz on 2008-07-11
Hi.


   Th reason for putting the model of the lap, its just that with others models the problem has been resolved, but in my model nothing works.


  With the hardware manager everything looks cool.. but look what is in my interfaces file:

 auto lo
iface lo inet loopback

when i have dhcp its:

auto lo
iface lo inet loopback
iface eth0 inet dhcp
auto eth0

I tried this:
 wlanconfig ath0 create wlandev wifi0 wlanmode sta
wlanconfig: ioctl: No such device


And when i use lshw -C network the output is this:
 *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0

Thanks!

---

### Post by howlingmadhowie on 2008-07-11
what's listed when you enter:

ifconfig

? can you also tell me the output of:

lsmod | grep ath

and maybe post the result of

cat /var/log/messages

---

### Post by almaddin on 2008-07-11
> **apocalipsiz said:**
> Hi.

  I did what you told me.. but it apears the same old problem with madwifi... this is what happend when i "make" jeje:

Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/k~/N~/Software Linux/madwifi-ng-r2756+ar5007 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** No rule to make target `Linux/madwifi-ng-r2756+ar5007'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2


and this when i make install:
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/k~/N~/Software Linux/madwifi-ng-r2756+ar5007 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** No rule to make target `Linux/madwifi-ng-r2756+ar5007'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2

Thank you almaddin.

Like I said do not forgot to install build-essential. 
either via synaptic or via the terminal by:
sudo apt-get install build-essential

---

### Post by apocalipsiz on 2008-07-12
Hi.

The output for lsmod | grep ath :

ath_pci               123192  0 
wlan                  231680  1 ath_pci
ath_hal               261376  1 ath_pci

this is the interface file content: 

auto lo
iface lo inet loopback
iface eth0 inet dhcp
auto eth0


the result of the log is too big to be attached, but do you need somenthing in particular?

and almaddin ... i don think thats the problem, cause all that  works pretty well, the only thing i cannot do it's to configure the wireless, thanks.

regards.

---

### Post by apocalipsiz on 2008-07-15
hi.

  I was reading and reading and reading...and the problem will persist in ubuntu hardy heron, and solved until ubunut 8.10.

Thanks to everyone.

---

### Post by howlingmadhowie on 2008-07-15
can you try:

iwlist scan

and post the result?

---

### Post by marcushe on 2008-07-24
Having the same issue with Hardy on the same exact laptop.

---

