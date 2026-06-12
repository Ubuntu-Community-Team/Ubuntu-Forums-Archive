---
title: "Ubuntu Lucid on SONY VAIO VGN-P13GH"
date: 2010-06-24
forum: Hardware
---

### Post by alones on 2010-06-24
Hello,

Just like to share Lucid UNR installation tips on SONY VAIO VGN-P13GH
Spec is here: [http://www.sony-asia.com/product/vgn-p13gh](http://www.sony-asia.com/product/vgn-p13gh)

1. Video (Intel GM950) does not work out-of-box, the fix available here:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

2. Suspend\Resume do not work. The fix proposed here is almost helped
[http://www.linux.com/archive/feature/114220](http://www.linux.com/archive/feature/114220)
You have to patch it to enable wlan after resume, see patch below
19a20,25
> #remove wlan modules
> for m in `lsmod | grep ath9k | awk '{print $1}'` ;
> do
>   rmmod $m
> done
> 
25,28c31,35
< case "$1" in
<   suspend)   echo -n mem > /sys/power/state ;;
<   hibernate) s2disk  ;;
< esac
---
> #case "$1" in
> #  suspend)   echo -n mem > /sys/power/state ;;
> #  hibernate) s2disk  ;;
> #esac
> echo -n mem > /sys/power/state
36a44,46
> #load module
> modprobe ath9k
> 

if you do not want to run script manual then you have to replace pm-suspend with it.

   sudo cp /usr/sbin/pm-suspend /usr/sbin/pm-suspend.origin
   sudo cp suspend.sh /usr/sbin/pm-suspend

and do not forget to swap netbook-launcher into standard gnome desktop (the launcher wakes your CPU up very frequently)

   sudo apt-get install gnome-core gnome-desktop-environment

DO NOT USE: sudo apt-get install ubuntu-desktop, it would install compiz and other staff that eats your resources.

---

