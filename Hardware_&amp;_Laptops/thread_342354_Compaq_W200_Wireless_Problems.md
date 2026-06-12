---
title: "Compaq W200 Wireless Problems"
date: 2007-01-19
forum: Hardware &amp; Laptops
---

### Post by perden on 2007-01-19
:(

So, I've acquired an old Compaq Evo N600c from my cousin. It's one of the lucky ones that have the optional W200 wireless adapter on the lid. I installed Edgy Eft (6.10) last night. Everything went perfectly, except for, you guess it, the wireless adapter on the lid. Now I've done my research and found the [WifiDocs/Device/CompaqW200 page]("https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200") and followed it to the letter (below are the steps I took). However, unlike everyone else it doesn't magically work once all the steps are completed. I noticed some other posts where some people had forgotten to install curl or gcc-3.4, but this is something different. No matter what I do, I just can't get that little green light to turn on.

For those of you who haven't experienced the Compaq W200, It's [this nifty device]("http://h20331.www2.hp.com/Hpsub/images/multiport_lil.jpg") that sits in the "multibay" on the lid of some Evo and Presario Notebooks. When it's not dead weight, it adds the asymmetric I'm-a-badass-hacker feel to the laptop. Tres cool. But I guess it's not to hard to see why it never caught on. It does add bulk and it's just a usb device after all, as Ubuntu was able to tell me.

So enough rambling. Has anyone had similar problems? Or even if you don't have this particular setup, maybe you could provide some insight on to a problem that just doesn't seem to have a way out, hm? (Watch the answer to my problem just be some little stupid error. I guess tish happens...)

My process:

```
$ svn co https://orinoco.svn.sourceforge.net/svnroot/orinoco/branches/usb orinoco_usb
A    orinoco_usb/orinoco_pci.c
A    orinoco_usb/prism_usb.c
A    orinoco_usb/net
A    orinoco_usb/net/ieee80211.h
A    orinoco_usb/orinoco.c
A    orinoco_usb/orinoco_pci.h
A    orinoco_usb/README
A    orinoco_usb/orinoco_tmd.c
A    orinoco_usb/orinoco.h
A    orinoco_usb/airport.c
A    orinoco_usb/dump_recs.c
A    orinoco_usb/orinoco_usb.c
A    orinoco_usb/hermes.c
A    orinoco_usb/README.orinoco
A    orinoco_usb/TODO
A    orinoco_usb/hermes_rid.h
A    orinoco_usb/spectrum_cs.c
A    orinoco_usb/hermes.h
A    orinoco_usb/compat.h
A    orinoco_usb/Kbuild
A    orinoco_usb/firmware
A    orinoco_usb/firmware/get_symbol_fw
A    orinoco_usb/firmware/parse_prism_ap_fw
A    orinoco_usb/firmware/SHA1SUM
A    orinoco_usb/firmware/get_ezusb_fw
A    orinoco_usb/firmware/get_prism_ap_fw
A    orinoco_usb/firmware/parse_sychip_fw
A    orinoco_usb/firmware/parse_symbol_fw
A    orinoco_usb/firmware/NEWS
A    orinoco_usb/firmware/Makefile
A    orinoco_usb/firmware/README
A    orinoco_usb/NEWS
A    orinoco_usb/orinoco_nortel.c
A    orinoco_usb/orinoco_plx.c
A    orinoco_usb/mkconf
A    orinoco_usb/Makefile
A    orinoco_usb/orinoco_cs.c
 U   orinoco_usb
Checked out revision 1273.

$ cd orinoco_usb/

$ ls -1
airport.c
compat.h
dump_recs.c
firmware
hermes.c
hermes.h
hermes_rid.h
Kbuild
Makefile
mkconf
net
NEWS
orinoco.c
orinoco_cs.c
orinoco.h
orinoco_nortel.c
orinoco_pci.c
orinoco_pci.h
orinoco_plx.c
orinoco_tmd.c
orinoco_usb.c
prism_usb.c
README
README.orinoco
spectrum_cs.c
TODO

$ make
make -C /usr/src/linux-headers-2.6.17-10-generic M=/home/patrick/orinoco_build/orinoco_usb KERNELRELEASE=2.6.17-10-generic modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/patrick/orinoco_build/orinoco_usb/orinoco.o
  CC [M]  /home/patrick/orinoco_build/orinoco_usb/orinoco_usb.o
  Building modules, stage 2.
  MODPOST
  CC      /home/patrick/orinoco_build/orinoco_usb/orinoco.mod.o
  LD [M]  /home/patrick/orinoco_build/orinoco_usb/orinoco.ko
  CC      /home/patrick/orinoco_build/orinoco_usb/orinoco_usb.mod.o
  LD [M]  /home/patrick/orinoco_build/orinoco_usb/orinoco_usb.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
patrick@brilliance:~/orinoco_build/orinoco_usb$ sudo make clean
make -C /usr/src/linux-headers-2.6.17-10-generic M=/home/patrick/orinoco_build/orinoco_usb KERNELRELEASE=2.6.17-10-generic NOCHECK=1 clean
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CLEAN   /home/patrick/orinoco_build/orinoco_usb/.tmp_versions
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
rm -f *.symvers

$ sudo make install
make -C /usr/src/linux-headers-2.6.17-10-generic M=/home/patrick/orinoco_build/orinoco_usb KERNELRELEASE=2.6.17-10-generic modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/patrick/orinoco_build/orinoco_usb/orinoco.o
  CC [M]  /home/patrick/orinoco_build/orinoco_usb/orinoco_usb.o
  Building modules, stage 2.
  MODPOST
  CC      /home/patrick/orinoco_build/orinoco_usb/orinoco.mod.o
  LD [M]  /home/patrick/orinoco_build/orinoco_usb/orinoco.ko
  CC      /home/patrick/orinoco_build/orinoco_usb/orinoco_usb.mod.o
  LD [M]  /home/patrick/orinoco_build/orinoco_usb/orinoco_usb.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make -C /usr/src/linux-headers-2.6.17-10-generic M=/home/patrick/orinoco_build/orinoco_usb KERNELRELEASE=2.6.17-10-generic modules_install \
                INSTALL_MOD_DIR=kernel/drivers/net/wireless
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  INSTALL /home/patrick/orinoco_build/orinoco_usb/orinoco.ko
  INSTALL /home/patrick/orinoco_build/orinoco_usb/orinoco_usb.ko
  DEPMOD  2.6.17-10-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
/sbin/depmod -ae

$ cd firmware/

$ ./get_ezusb_fw 
** Resuming transfer from byte position 6117483
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 94500  100 94500    0     0  25891      0  0:00:03  0:00:03 --:--:-- 84669
436+0 records in
436+0 records out
6976 bytes (7.0 kB) copied, 0.004595 seconds, 1.5 MB/s

$ ls -1
ezusb.drv.pkz
get_ezusb_fw
get_prism_ap_fw
get_symbol_fw
Makefile
NEWS
orinoco_ezusb_fw
orinoco_usb_fw.h
parse_prism_ap_fw
parse_sychip_fw
parse_symbol_fw
README
SHA1SUM

$ sudo cp ezusb.drv.pkz orinoco_usb_fw.h orinoco_ezusb_fw /lib/firmware/`uname -r`

$ sudo modprobe -v orinoco_usb
insmod /lib/modules/2.6.17-10-generic/kernel/drivers/net/wireless/orinoco.ko 
insmod /lib/modules/2.6.17-10-generic/kernel/drivers/net/wireless/orinoco_usb.ko
```

... no green light ...

```
$ sudo reboot
```

... still no green light ...

:(

Help?

---

### Post by gonbykn on 2007-02-01
I have a N620c and have been banging my head trying to get the W200 to work, until now!!! Yea :D I followed the instructions with copy and paste into the terminal and had the same results. I kept on reading and edited the /etc/pcmcia/config.opts and rebooted to a green light, wohoo!! I am now writing to you with my w200 wireless working just fine on a WEP enabled wireless network. Keep at it. It should work for you too.

---

### Post by perden on 2007-02-12
I don't know how many times I can go through the wiki and still get no green light, regardless of whether the pcmcia hack is there or not. (BTW, why would the pcmcia effect a usb device anyway?)

If there is anyone else out there that is having the same sort of problems that I'm having, please reply! Make sure you follow all the steps, and if it still doesn't work, maybe we can figure it out together.

Some questions:

Is there a way to determine what is going on in the system during and after the module load? If there is some way to get additional information other than the kernel log and verbosely running modprobe, I'd like to hear it.

Also, could there be some sort of module conflict? I noticed Ubuntu has been loading prism2_usb, even though there has never been a prism chipset device connected to my Evo N600c.

Any insight is greatly appreciated.

---

### Post by didiercool on 2007-09-22
I just installed Ubuntu for the first time last night, and I've been trying to get my Compaq W200 to work and so far no luck.  I ran through the steps from WifiDocs/Device/CompaqW200 and everything seems to work (as far as I can tell...) until it comes to activating the adapter and it says 'FATAL: Module orinoco_usb not found' and of course my green light does not come on no matter how much I reboot/repeat the whole process/rage for a while.
Any suggestions?

---

### Post by mluvw47 on 2008-05-02
Guess I am not alone after all. I tried on 8.04, I following the instruction but still got no luck. Then I tried to use the wlanng with prism2_usb, 
rmmod the prism2_usb and 80211p module few time, and reset using
wlanctl

rmmod prism2_usb
modprobe prism2_usb prism2_doreset=1
wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable

The green light comes up and blinking, after I issue the following line:

'wlanctl-ng wlan0 lnxreq_autojoin ssid=<your ssid> authtype=opensystem'

The green LED light stable, and I am able to use
iwlist wlan0 scanning to scan the network.

However, when I tried to use
dhpclient wlan0  I am not able to get ip address??

That is so strange. 

Mav

---

