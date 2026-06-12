---
title: "Upgrading Prism2.5 firmware"
date: 2007-07-14
forum: Hardware &amp; Laptops
---

### Post by remeron on 2007-07-14
HI there, I've just installed ubuntu and linux for the first time and i'm loving it....been tinkering with it day and night. I've got a Presario 2100 and the wifi is running Prism 2.5 station firmware v1.4.9
I'm trying to upgrade the frimware to v1.7.4 as i heard that the newest firmware supports WPA encryption. I've downloaded hostap-utils 0.4.0 and installed

i'm running into trouble when i try to flash the latest firmware (yes, i checked, i downloaded the correct firmware), but whenever i use

prism2_srec -v -f wifi0 <primary firmware> <station firmware>

i get an error saying

"Could not read wlan PDA. This requires PRISM2_DOWNLOAD_SUPPORT definition in driver/module/hostap_config.h

I don't know what that means. And i can't even find that hostap_config.h

Plsease help.

---

### Post by medomedo on 2007-11-18
Hi,

I am interested if you have some luck with your card. I dont have a Winsow mahcine and would like to upgrade the firmware as well.

---

### Post by medomedo on 2007-11-18
I found this link very useful [http://linux.junsun.net/intersil-prism/](http://linux.junsun.net/intersil-prism/) .

When I used this command 
> prism2_srec -vf -O /proc/net/hostap/wlan0/pda eth2 PK010101.HEX SF010802.HEX

I got this result
>   addr=0x007E0000..0x007E0B55 (len=2902)
  addr=0x007E0C00..0x007E151F (len=2336)
  addr=0x007E17FE..0x007EEAEF (len=54002)
  addr=0x007F0800..0x007F17FF (len=4096)
  addr=0x007FE000..0x007FECD1 (len=3282)
Total data length: 66618
OK.

Downloading to non-volatile memory (flash).
Note! This can take about 30 seconds. Do _not_ remove card during download.
Odd.. Download request for the kernel driver failed.
Are you sure you have compiled (and loaded the correct version of)
hostap.o module with PRISM2_DOWNLOAD_SUPPORT definition in
driver/module/hostap_config.h?
In addition, non-volatile download requires PRISM2_NON_VOLATILE_DOWNLOAD
to be defined.
ioctl[PRISM2_IOCTL_DOWNLOAD]: Operation not supported

Download failed!

I am afraid that we have to compile hostap ourselves.

---

