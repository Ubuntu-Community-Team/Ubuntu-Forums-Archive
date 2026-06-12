---
title: "Stuck at &quot;Loading manual drivers&quot;"
date: 2009-03-03
forum: Hardware
---

### Post by afeasfaerw23231233 on 2009-03-03
My /boot/grub/menu.lst doesn't have the "quiet" option because I want to know what's going on during bootup. 
Almost every time I boot up to Ubuntu it stucks at 
```
Loading manual drivers
```

Then I can do nothing execpt pressing ctrl+alt+del. But this hotkey terminate the stucking** Loading manual driver** and keeps the boot process going instead of rebooting the notebook. Finally a blue screen appears and said the graphic driver is not install and X cannot be started. Then I press ctrl+alt+del again and this time it reboot normally. It finally boot into x successfully. 

Here's what it wrote exactly: 
1st boot
```

Reading files needed to boot 
setting preliminary keymap 
preparing restricted drivers 
setting the system clock
starting basic networking 
stopping the firestarter firewall
wlan0: error fetching interface information: device not found
wlan0: error fetching interface information: device not found
wlan0: error fetching interface information: device not found
... done

starting ther firestarter firewall..
wlan0
wlan0: error fetching interface information: device not found
wlan0: error fetching interface information: device not found
...fail!
run-parts:/etc/network/if-up.d/50firestarter exited with return code 2 

starting kernel event manager
loading hardware drivers...
setting the system clock 
loading kernel modules
loading manual drivers

```




It's quite annoying for me to press ctrl-alt-del and boot again everytime. Any help would be highly appreciated!

I am using ubuntu 8.10 32-bit on a SiS 671MX chipset notebook.  
I installed the SiS integrated graphic driver and the WLAN driver (ndiswrapper) manually because they didn't work by default. Would it be the cause of the problem? 

My /boot/grub/menu.lst 
```

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		25053297-13ad-4ad2-8e86-e4bb594c5f7d
kernel		/vmlinuz-2.6.27-11-generic root=UUID=24df0199-31f4-47b6-b604-94a521ddad60 ro  apicmaintimer idle=mwait
initrd		/initrd.img-2.6.27-11-generic

```

---

### Post by afeasfaerw23231233 on 2009-03-09
Bump

---

