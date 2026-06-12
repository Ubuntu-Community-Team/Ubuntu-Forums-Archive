---
title: "ubuntu 9.04 on dell vostro 1310"
date: 2009-05-28
forum: Hardware
---

### Post by al.adab on 2009-05-28
hello,

still looking out for a good cheap laptop compatible with ubuntu 9.04. Looking into the dell vostro 1310 (shipped with windows vista). I was wondering if anyone has used it with ubuntu (preferably 9.04), ie, can I safely install this OS to replace vista?

thanks!

---

### Post by geekygirl on 2009-05-28
I have Jaunty in a triple boot (with Vista and Windows 7)setup on my Vostro 1310 - everything is working well on it.

:D

---

### Post by al.adab on 2009-05-28
thanks! that's reassuring. Can I safely assume (this is going to sound naive, but I really don't know) that if it works well on a triple boot it should as well work well on a single boot, ie, ubuntu 9.04 only?

---

### Post by al.adab on 2009-05-28
sorry, forgotten to ask: would you run the 32-bit or 64-bit Ubuntu 9.04? The Vostro 1310 I'm getting has got either 1 or 2 Giga RAM memory, if that's relevant...thanks!

---

### Post by al.adab on 2009-05-28
...and also I came across the following: 

"Some versions of the Vostro 1310 include the Dell Wireless 1395 and 1505 controllers which are Broadcom based. These are not well supported under Linux and should be avoided if possible. If you are about to order this laptop it is recommended you select an Intel wireless option as tested here." ([http://www.linlap.com/wiki/dell+vostro+1310](http://www.linlap.com/wiki/dell+vostro+1310))

Incidentally, the one I'm getting has got he 1395...any idea?

---

### Post by raymondh on 2009-05-28
> **al.adab said:**
> sorry, forgotten to ask: would you run the 32-bit or 64-bit Ubuntu 9.04? The Vostro 1310 I'm getting has got either 1 or 2 Giga RAM memory, if that's relevant...thanks!

Running 64 will depend if the machine is capable. It is possible to have a 64-bit capable machine and run a 32-bit Ubuntu.  It is a headache to have a 32-bit machine and try to run a 64-bit ubuntu.  Most dual-cores are OK.

If you're set on the vostro ... try the liveCD "without any changes to your computer" before intsalling.  The liveCD (although a bit sluggish) is a good indicator.

With regard to compatability, allow me to share with you an experience ....some christmas ago, my wife and I bought "his-and-her's-matching-laptops" from Dell.  Only lately (whilst tweaking the machines for Ubuntu) did I realize that not all internal hardwares' are identical (i.e. her wifi card is different from my wifi card).  Go figure?!

I find (always) a good starting point in any install is the "release notes".  Then, I look for the compatibility list.  Of course, your mileage and experience may differ.

[https://help.ubuntu.com/community](https://help.ubuntu.com/community)

Have fun and happy Ubuntu-ing.

Regards,

---

### Post by al.adab on 2009-05-29
Thanks Raymond. 

I contacted Dell, and it looks like they're actually shipping it with a "Dell Wireless 1395 (802.11 b/g) MiniPCI Card - Celeron Processors". 
 
I also went through the help docs, and came across
[https://help.ubuntu.com/community/WifiDocs/Driver/1390](https://help.ubuntu.com/community/WifiDocs/Driver/1390)

Do you think I could apply a solution equivalent to this to install Ubuntu 9.04 (or 8.10 I wouldn't mind) on the Dell Vostro 1310? If I could, do you know where I can find it? 

In fact, it'd really be great if I could use ANY version of Linux on the new machine as long as I can run OO.org Writer (or equivalent to Microsoft Word in terms of performance) on it and a basic internet browser. I don't really care much for multimedia software and the like. 

Your advice is highly appreciate. Thanks!

---

### Post by raymondh on 2009-05-29
Hello ai.adab,

There are many solutions out there and the only way to know if it works or not is to actually try it.  By many solutions, I mean from a simple update to editing to actually changing the wifi card.

You are actually one step closer by researching various solutions in advance... :)

I would :

1. Burn a 32-bit liveCD for 9.04, 8.10 and 8.04 LTS
2. Try each of those LiveCD's in the new laptop and see which one (or one's) give you wifi and sound.
3. Install what you like best and go from there.

Also, check the loco forums and see if you have an ubuntu group in your area. If so, consider joining.  Such loco's are also a great resource.

Congratulations on your new laptop.

---

### Post by geekygirl on 2009-05-29
Ok my wireless is Intel 4965AGN (Draft N capable) - probably why I haven't had any issues.

I am also running 4G of memory with a 9.04 32bit install (I dont have a CPU that's capable of virtualization and am running VM's with 32bit hosts..meh)

---

### Post by rmhartman on 2009-06-27
> **geekygirl said:**
> I have Jaunty in a triple boot (with Vista and Windows 7)setup on my Vostro 1310 - everything is working well on it.

:D

I just burned 9.04 desktop CD and my Vostro 1310 does not work at all.  Neither the mouse nor the keyboard work once it is in graphics mode.  Keyboard works in the setup screen, so if there are specific options I need for the Vostro, please let me know.

---

### Post by dwair on 2009-06-28
I have a similar problem to rmhartman – but I managed to install and run Ubunto for a week before I lost the mouse and keyboard.  The good news is that the second or third time I used the Ubunto boot, my wirless connection seemed to sort itself out with out any fiddling and ran with no issues (but now I cant even log on!)

---

### Post by rmhartman on 2009-06-30
Ok, on another thread I got the answer to the mouse/keyboard problem.  On the boot options line you need to add "i8042.reset".

This can be done by hitting f6 on the livecd, then escaping the menu and editing the line (I put it before the "--" at the end of the line).

After you are running you want to add it to the kernel lines in the /boot/grub/menu.lst file.

(Still need help with the wireless though...)

---

### Post by al.adab on 2009-07-05
finally tried it out on this laptop and it works flawlessly without having to replace any wi-fi card or anything at all :)

---

