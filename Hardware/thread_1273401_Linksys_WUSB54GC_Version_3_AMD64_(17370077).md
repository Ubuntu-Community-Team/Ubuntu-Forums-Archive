---
title: "Linksys WUSB54GC Version 3 AMD64 (1737:0077)"
date: 2009-09-23
forum: Hardware
---

### Post by zip311 on 2009-09-23
It took me a while, but I discovered a very simple solution to using this wireless card.

Make sure your device id is 1737:0077 from lsusb.

First, download the source for the rt3070 usb driver from ralinktecit h: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)
(should be RT3070USB(RT307x) link)

Untar the source, which should be a file named something like: 2009_0525_RT3070_Linux_STA_v2.1.1.0.bz2

You will then need to edit two (2) files.

In os/linux/config.mk change:
```

HAS_WPA_SUPPLICANT=n
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n

```
to:
```

HAS_WPA_SUPPLICANT=y
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

```

In os/linux/usb_main_dev.c:
On about line #44 starts the definition of the rt_usb_id struct:
```

/* module table */
struct usb_device_id rtusb_usb_id[] = {

```

You want to change the end of that structure on about line #76 from:
```

        {USB_DEVICE(0x203D,0x1480)}, /* Encore 3070 */
#endif // RT3070 //
        { }/* Terminating entry */
};

```
to:
```

        {USB_DEVICE(0x203D,0x1480)}, /* Encore 3070 */
        {USB_DEVICE(0x1737,0x0077)}, /* Linksys WUSB54GC */
#endif // RT3070 //
        { }/* Terminating entry */
};

```

Make and install the module, making sure to edit your /etc/modules.

Why this works:
The WUSB54GC Version 3 card has the rt3070 chipset - it's just that the ralink drivers don't contain the device ID for the linksys model (doh!)

---

### Post by skriwelae on 2009-09-29
Hi,

I have modified the files as you show, and built the module. How can I make sure it is correctly installed? Do I have to call modprobe to load it?

After following your instructions my dongle is still not working. What else do I have to do?

Thanks!

---

### Post by rockon1215 on 2009-10-13
I followed the steps, but whenever I try to 'make' I get

```
install: cannot stat `rt3070sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/alex/Documents/Wireless/os/linux'
make: *** [install] Error 2

```

I tried again with 'sudo make' but no such luck. 

(I renamed '2009_0525_RT3070_Linux_STA_v2.1.1.0' to 'Wireless' to make typing it out in the terminal easier)

---

### Post by Kjeldgaard on 2009-10-20
> **zip311 said:**
> Make and install the module, making sure to edit your /etc/modules.

What is it exactly I need to write in the module file?

/Kjeldgaard

---

### Post by TeamCK on 2009-11-03
So, I am brand new to ubuntu (and haven't even thought about programming languages in quite a while). Can you tell me what I need to write in order to build a module and install a module please?

thanks.

---

### Post by vanjan on 2009-11-06
trying to build this in 9.10 I get a following error:
```

make -C tools
make[1]: Entering directory `/home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/tools'
/home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/Makefile
make  -C  /lib/modules/2.6.31-14-generic/build SUBDIRS=/home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/crypt_md5.o
  CC [M]  /home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/mlme.o
/home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/mlme.c:4406: warning: the frame size of 1572 bytes is larger than 1024 bytes
  CC [M]  /home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_wep.o
  CC [M]  /home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/action.o
  CC [M]  /home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_data.o
  CC [M]  /home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/rtmp_init.o
/home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/rtmp_init.c: In function ‘RtmpRaDevCtrlInit’:
/home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/rtmp_init.c:3710: warning: passing argument 2 of ‘os_alloc_mem’ from incompatible pointer type
/home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:5687: note: expected ‘UCHAR **’ but argument is of type ‘UCHAR *’
  CC [M]  /home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_aes.o
/home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_aes.c: In function ‘AES_GTK_KEY_WRAP’:
/home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_aes.c:1338: warning: the frame size of 1092 bytes is larger than 1024 bytes
  CC [M]  /home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_sync.o
  CC [M]  /home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/eeprom.o
  CC [M]  /home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_info.o
  CC [M]  /home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/dfs.o
  CC [M]  /home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/spectrum.o
  CC [M]  /home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/rt_channel.o
  CC [M]  /home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_profile.o
  CC [M]  /home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_asic.o
  CC [M]  /home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/assoc.o
/home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/assoc.c: In function ‘wext_notify_event_assoc’:
/home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/assoc.c:1401: warning: pointer targets in passing argument 5 of ‘RtmpOSWrielessEventSend’ differ in signedness
/home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:7025: note: expected ‘PUCHAR’ but argument is of type ‘char *’
  CC [M]  /home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/auth.o
  CC [M]  /home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/sync.o
/home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/sync.c:651: warning: the frame size of 1252 bytes is larger than 1024 bytes
/home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/sync.c:1429: warning: the frame size of 1312 bytes is larger than 1024 bytes
/home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/sync.c:929: warning: the frame size of 1260 bytes is larger than 1024 bytes
/home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/sync.c: In function ‘MlmeStartReqAction’:
/home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/sync.c:525: warning: the frame size of 1064 bytes is larger than 1024 bytes
  CC [M]  /home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/sanity.o
  CC [M]  /home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/connect.o
/home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/connect.c: In function ‘LinkDown’:
/home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/connect.c:1975: warning: unused variable ‘Cancelled’
/home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/connect.c:343: warning: the frame size of 1600 bytes is larger than 1024 bytes
  CC [M]  /home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/wpa.o
  CC [M]  /home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.o
/home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1510: error: ‘struct net_device’ has no member named ‘open’
/home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1511: error: ‘struct net_device’ has no member named ‘stop’
/home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1512: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1513: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1519: error: ‘struct net_device’ has no member named ‘get_stats’
/home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1553: error: ‘struct net_device’ has no member named ‘validate_addr’
make[2]: *** [/home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/jan/Downloads/Drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [LINUX] Error 2

```

---

### Post by mandava on 2009-11-18
I am getting the same errors as vanjan above!
 Did anyone find a solution for this one?

I am going to try the instructions given [here]("http://ubuntuforums.org/showthread.php?p=8071728").
Let's see what happens!

---

### Post by noppie on 2009-12-06
> **Kjeldgaard said:**
> What is it exactly I need to write in the module file?

/Kjeldgaard

I don't have a
 making sure to edit your /etc/modules.

and went  I do #modprobe rt3070sta with sudo in front nothing happens.

#ifconfig ra0 inet 192.168.0.33 up
#iwconfig ra0
nothing happens.. using sudo in front of all
and where do i find where to configure the card
thank you  very much
noppie

---

### Post by RiveraK2 on 2010-01-10
Hey,

I was wondering if someone can help me through this process.
I'm brand new to Linux/Ubuntu having installed it a few hours ago.

Anyway, I own this exact adapter (WUSB54GC V3 1737:0077) and I
would like to get it working on my PC.

I followed the steps above, but I have no idea on how to make and
install a module to get this thing working. Can anyone help me 
out with this?

I'll greatly appreciate any help I get.

Thanks!,
RK2

---

### Post by KherKhere on 2010-01-13
Please some one help us how can i install it setp by step .

Thanks in advance .

---

### Post by LguyStillFly on 2010-01-16
Anyone find out what to put in the /etc/modules file yet??

---

### Post by Xog on 2010-01-18
edit

---

### Post by quick10 on 2010-02-08
Got the WUSB54GC working on Ubuntu 2.6.31-19-generic-pae.

Followed the steps mentioned earlier in the thread with several modifications and additions.

If still in need, please let me know.

I'll try to make a small HOWTO.

---

### Post by Taemojitsu on 2010-05-11
For the extreme newb, any instructions that includes "make and install" is not very simple. For anyone who didn't get it to work or was too scared to try, it's mostly fixed in Lucid using wireless backports but I haven't tried an encrypted connection.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446889](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446889)

---

### Post by rightkick on 2010-11-10
Why Linksys WUSB54GC v3 USB antenna has rt3070 chipset, as stated in post 1??? According to [http://linux-wless.passys.nl/](http://linux-wless.passys.nl/) it has rt2870 chipset and seeing its intallation cd i found a rt2870.inf file also, and not a rt3070.inf!
I'm asking because I'm trying one week to install this USB dongle in Backrack4-R1 with a Ralink driver that supports rt2870 chipset succeeding only to make the LED flash but the dongle doesn't seem to work (it can't find any wireless networks, not even mine in home).   
Thank  you.

---

