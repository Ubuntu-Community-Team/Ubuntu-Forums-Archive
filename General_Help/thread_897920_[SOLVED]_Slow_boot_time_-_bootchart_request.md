---
title: "[SOLVED] Slow boot time - bootchart request"
date: 2008-08-22
forum: General Help
---

### Post by alicebtoklas on 2008-08-22
Hello all,

I'm trying to optimize my boot time (2:31 for now). Bootchart image is attached - but I don't know how to read it... 

I think the boot sequence became very slow after I tried various ways to install the speedtouch USB modem I've been using for my connexion during a few days. 

Could someone help?

Specifications are below. Note that I use dual boot MacOS/Ubuntu.

Thanks a lot,

---

### Post by LateNiteTV on 2008-08-22
ubuntu can be extremely slow when booting. try editing out all the kernel modules in your kernel config then recompiling your kernel. this will speed up boot time because it wont have to load all those modules for hardware that you dont even have in your system.

---

### Post by alicebtoklas on 2008-08-25
Please, can you explain what you mean by "editing" and "recompiling" the kernel? i'm a real newbie (but willing to learn)...

I've tried some of the things i found in the forums already:
- reprofiled bootup, as explained in [http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263)
- turned off some services as explained in [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

but it didn't help.

Is it something else that you suggest me to do?

Thanks for the help so far,

---

### Post by Elfy on 2008-08-25
It appears to be hanging when s40 networking starts - there are some fixes, I've never used wireless so have not needed to do anything similar. This might help, although it is old, you could try to search the netwroking forum for s40 etc.

[http://ubuntuforums.org/showthread.php?t=305852](http://ubuntuforums.org/showthread.php?t=305852)

Sorry I can't help more.

---

### Post by chrisccoulson on 2008-08-25
I think it is related to your modem. As forestpixie pointed out, it hangs on s40networking, and then resumes after a burst of activity from pppd. Could you post your /etc/network/interfaces file?

LateNiteTV - Modules are only loaded for hardware present in the system, so removing modules won't help at all.

---

### Post by Elfy on 2008-08-25
>  Could you post your /etc/network/interfaces file?That's what I was thinking, but not having had to touch it didn't want to say more :)

---

### Post by chrisccoulson on 2008-08-25
The funny thing is is that the delay is *exactly* 2 minutes, which sounds like a timeout due to misconfigured network settings.

---

### Post by Elfy on 2008-08-25
> **chrisccoulson said:**
> The funny thing is is that the delay is *exactly* 2 minutes, which sounds like a timeout due to misconfigured network settings.
So it is - didn't notice that, I was working more on the assumption that something went awry here - 

> I think the boot sequence became very slow after I tried various ways to install the speedtouch USB modem 

I'm sure that it is fixable anyway, I'll just watch and learn from here :)

---

### Post by alicebtoklas on 2008-08-25
Here is the content of etc/network/interfaces:

auto lo
iface lo inet loopback

auto ppp0
iface ppp0 inet ppp
  provider speedtch


What I mainly use is an ethernet connexion, which works all right. As I said, I don't really need to use the USB-speedtouch modem anymore. As for wireless, I tried but never managed to make it work...

thanks a lot,

---

### Post by chrisccoulson on 2008-08-25
Does your modem actually work once your machine has finished booting? Does the boot time improve if you comment out the lines relating to your modem (so your /etc/network/interfaces looks like this):
```
auto lo
iface lo inet loopback

#auto ppp0
#iface ppp0 inet ppp
#provider speedtch
```

I know your modem won't work with the above configuration though.

---

### Post by alicebtoklas on 2008-08-25
Great! I did it and my boot time is 0:29 now! Thank you!

I guess i'll just have to uncomment these 3 lines if I need to use this modem again some day - which is what I secretly hoped. Actually, this modem has been working only after I installed this: [http://www.ubudsl.com](http://www.ubudsl.com) So I don't even know if these three lines were necessary.

Thanks again,

---

