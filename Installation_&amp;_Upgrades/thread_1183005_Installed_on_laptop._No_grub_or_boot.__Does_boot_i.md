---
title: "Installed on laptop. No grub or boot.  Does boot if loading up HD from Live CD though"
date: 2009-06-09
forum: Installation &amp; Upgrades
---

### Post by ShadowK on 2009-06-09
Hey guys,

I have installed the latest Ubuntu onto my laptop tonight though for some reason it won't boot.  I've checked the boot menu and have them in the order of DVD Drive, HDD & then Broadcom Adapter (which I can't get rid of!).  

Whenever I turn the machine on it just tries to load up an OS via the Broadcom Adapter which it of course can't do.  There doesn't seem to be any option for any other bootup.

Put the live CD in and selected 'boot from first Hard Drive' and Ubuntu booted up perfectly.  Still no GRUB though.

Any ideas??

---

### Post by ShadowK on 2009-06-09
Just tried using the Super Boot Disk and it will boot into the OS if I select GRUB or go via other routes.  Tried a few repairs and it says its done though its still not working.

Have triple checked the HD is first on the boot order now but still no luck.  Anybody?

---

### Post by ShadowK on 2009-06-09
Just tried to install Lilo and run the config file and got this error message about fstab....

```
WARNING!                                                                  &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Your /etc/fstab configuration file gives device                           &#9474; 
 &#9474; UUID=f9a70686-5a5c-48b2-8c14-6339fbcba6bb as the root filesystem device.  &#9474; 
 &#9474; This doesn't look to me like an "ordinary" block device. Either your      &#9474; 
 &#9474; fstab is broken and you should fix it, or you are using hardware (such    &#9474; 
 &#9474; as a RAID array) which this simple configuration program does not         &#9474; 
 &#9474; handle.                                                                   &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; You should either repair the situation or hand-roll your own              &#9474; 
 &#9474; /etc/lilo.conf configuration file; you can then run /usr/sbin/liloconfig  &#9474; 
 &#9474; again to retry the configuration process. Documentation for LILO can be   &#9474; 
 &#9474; found in /usr/share/doc/lilo/.              
```

Don't know if that helps?

---

### Post by ShadowK on 2009-06-10
Am now temporarily having to boot with either Super Boot Disk or the Ubuntu Live CD and select boot from HD.  Does no one have any inclination as to what could be the issue here?? Is slowly frustrating the hell out of me. :(

---

### Post by blocktalk on 2009-09-13
> **ShadowK said:**
> Am now temporarily having to boot with either Super Boot Disk or the Ubuntu Live CD and select boot from HD.  Does no one have any inclination as to what could be the issue here?? Is slowly frustrating the hell out of me. :(

Am in the same situation myself. Almost seems like the BIOS is permanently set to look for a CD startup source. Running an AMD desktop.

---

