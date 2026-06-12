---
title: "BIOS Reboot"
date: 2010-01-05
forum: Hardware
---

### Post by egravede on 2010-01-05
I'm not sure if this is hardware or conflicting software but my Dell Optiplex 760 with Ubuntu 9.10(Karmic) has been having this strange problem lately.  Every morning when I go to boot it, it'll get as far as the BIOS splash, the GRUB loader, and then it will reboot.  Now I know the computer works cause I'll just have to turn it off and on a few times and it will go through to the Karmic splash screen and everything will be fine from there.


Any ideas?  I'm thinking it could be a hard drive problem...

---

### Post by pricetech on 2010-01-05
If it's a Dell, start with the Dell diagnostics.  That should tell you whether it's a hardware or software problem.

You might also try a live CD to see if it boots normally.

---

### Post by egravede on 2010-01-05
Will do, I'll let it run over night and get back to you tomorrow.

---

### Post by mabonvin on 2010-01-16
Hi, I think I have the same problem, and I figured out a cheap way of making it through the reboots, but I hate to have to do it. My system will get past grub menu, but when it reaches the white ubuntu logo (ubuntu 9.10) after a few seconds it restarts :-x. I found that if I press enter or some other F keys while on the white logo it will not reboot.

Is there a legit solution to this? 

I have used this laptop with linux mint before, and others and didn't have this problem. 

Let me know if you need me to post some other information. (and how to get it)

Thanks.

---

### Post by IcarusR on 2010-01-17
Disable the boot splash screen then you will be able to see where it reboots.

Follow instructions here 

[http://ubuntuforums.org/showpost.php?p=8612908&postcount=828]("http://ubuntuforums.org/showpost.php?p=8612908&postcount=828")

& remove ```
quiet splash
```

This will only work for the next boot, ie not permanent.

When it actually boots into Ubuntu also check log files to see at what point it reboots.

You could also try a live CD to see if it does the same.

---

### Post by zach.detton on 2010-02-10
I had the same thing happen on my Dell laptop. I wouldn't receive any error message at all. It would say "Grub Loading" and then just reboot. I found it is something to do with Grub 2 and I followed the steps listed on [this]("https://wiki.ubuntu.com/Grub2?highlight=%28grub2%29#Recover%20Grub%202%20via%20LiveCD") tutorial to fix it. I hope you find this helpful.

---

