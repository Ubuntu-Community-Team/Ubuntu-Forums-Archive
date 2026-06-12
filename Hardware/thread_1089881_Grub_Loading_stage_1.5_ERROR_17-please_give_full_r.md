---
title: "Grub Loading stage 1.5 ERROR 17-please give full response"
date: 2009-03-07
forum: Hardware
---

### Post by rubecuber on 2009-03-07
Grub Loading stage 1.5 ERROR 17

what do i do?????!??!?!?!?!?!?!??!?! AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA AAGH!

I recently installed ubuntu 9.04 alpha5 onto a separate partition alongside windows7beta, and wehen i start up my computer I get the above message. PLEASE HELP IT'S REALLY URGENT!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!


P.S. please don't direct me to another thread, please explain

---

### Post by davidmohammed on 2009-03-07
... means can't find how to boot ubuntu.  Generally you should install the boot partition on a separate partition from the rest of ubuntu -remember also to install windows first before you install ubuntu.

... remember jaunty is alpha - you should expect things like this being a bit flaky.

Suggest wipe and retrieve your backup... you did make one didn't you :-)

---

### Post by rubecuber on 2009-03-07
That CAN'T be the only option, I have my entire hard drive used up; 160,gigs Windows 7 and 160 gigs ubuntu on a 320 gig hard drive. When I try to re-install it, it only gives me the option of taking up the entire drive. Would someone PLEASE give me a better solution?

---

### Post by ssj3g0ku on 2009-03-07
> **rubecuber said:**
> That CAN'T be the only option, I have my entire hard drive used up; 160,gigs Windows 7 and 160 gigs ubuntu on a 320 gig hard drive. When I try to re-install it, it only gives me the option of taking up the entire drive. Would someone PLEASE give me a better solution?

you have to chose manualy partition
than create 3 partitions for ubuntu
1: 2 gb swap 
2: 1 gb ext3 /boot
3: how much do you like for ubuntu ext3 /

if you cant chose manual partition get another iso or request free
cd

---

### Post by meierfra. on 2009-03-08
In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the Boot Info Script to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

