---
title: "rtl8187b wireless cuts out after about 20 minutes with Ubuntu 8.10"
date: 2008-10-31
forum: General Help
---

### Post by tjwoosta on 2008-10-31
i have an rtl8187b wireless card

with previous releases of Ubuntu i used a hacked driver found here
[http://www.datanorth.net/~cuervo/blog/rtl8187b-drivers-and-patches/]("http://www.datanorth.net/~cuervo/blog/rtl8187b-drivers-and-patches/")
(it was hacked because the original realtek rtl8187 driver would only work with rtl8187L, so now this one works with rtl8187B)

but Ubuntu 8.10 has the 2.6.27 kernel

the 2.6.27 kernel has built in support for the rtl8187b

so with 8.10 my card worked out of the box  (after updates)

the problem is that after i use firefox and/or transmission for about 20 minutes it will lose connection and stall out

i check the network icon and it says that i am still connected at full strength

i close and reopen firefox or transmission and they still dont work

also, even when the connection is working it seems far slower than it should be

so if i reboot it will work again but only for about another 20 minutes

what is happening, and how can i fix it?


EDIT: i have just discovered that it will stay connected as long as i dont start Transmission

(if i try to download any torrents it will work for a few minutes and then my connection will die for transmission and firefox and i dont know what else because the network applet still says connected)

---

### Post by afterwego on 2008-11-02
I am noticing this issue as well, but I haven't opened Transmission. I just have Firefox and Pidgin running, so something goofy is going on.

---

### Post by gletob on 2008-11-12
I too have the 8187b and my problem is slightly different I have to manually set a lower rate if I don't have good signal

---

### Post by Washington Irving on 2008-11-17
I also have this problem. The wireless connection randomly stops but says that it's connected. Also the range is (slightly) less then it was on Vista.

---

### Post by tjwoosta on 2008-11-17
this is definitely an issue that can be fairly easily resolved and desperately needs to be addressed!

i say it can be fairly easily resolved because the working driver already exists, it just wont compile with this 2.6.27 kernel

the following quote was taken from this FAQ on the working drivers website [http://www.datanorth.net/~cuervo/rtl8187b/FAQ.html]("http://www.datanorth.net/~cuervo/rtl8187b/FAQ.html")

> 
[B]When will this patch be merged into the mainline kernel?
[/B]
After everyone kept telling me there was real support in 2.6.27 for the 8187B, I finally got around to rolling my own kernel and testing it out a bit. I'm pleased to report that it looked good, but I didn't bang on it too hard. Signal strength was properly reported and I didn't see the momentary hangs I've experienced with my patch. I didn't spend too long under .27 because I didn't feel like fixing everything else that went wrong (mostly the X server), so I'll wait for Ubuntu to upgrade the kernel, but those of you under Debian, Slackware, etc., might want to upgrade.



so by the looks of it, he stopped working on his driver, and he didn't make a patch for the 2.6.27 kernel, because the new kernel has built in support  (which we know is greatly flawed)

i have posted a comment here [http://www.datanorth.net/~cuervo/blog/rtl8187b-drivers-and-patches/]("http://www.datanorth.net/~cuervo/blog/rtl8187b-drivers-and-patches/") asking if anybody knows how to compile the driver with the 2.6.27 kernel but i have not received any responses yet

it would be greatly appreciated if somebody with some knowledge of drivers could help us get this driver working on this new kernel by writing a small patch

---

### Post by 3rdalbum on 2008-11-17
Similar problem here. It's getting to the stage that I'm thinking of buying another wireless router, connecting it to my computer via Ethernet cable, and creating a bridged connection between it and my ADSL wireless router.

I can get hours out of it before dropping, but the speeds occasionally go very low and the signal strength shows as being very weak.

To prevent needing to reboot, you could use modprobe to reload the wireless driver. For the last three Ubuntu releases I've had a script on my desktop that modprobes the driver out and in :-(

---

### Post by swoody on 2008-11-17
I'm having the same problem, but with a Linksys WMP110. Even if I leave the computer at idle and don't open any programs my wireless gets disconnected, and I have to reboot.

---

### Post by agwblack on 2008-11-25
> **3rdalbum said:**
> To prevent needing to reboot, you could use modprobe to reload the wireless driver. For the last three Ubuntu releases I've had a script on my desktop that modprobes the driver out and in :-(

I am having the same problem. Being very new to Linux and Ubuntu, could someone tell me how to get/use this modprobe until the problem is either resolved, or until I get a new wireless adapter? Having to reboot all the time when all I want to do is reload the wireless driver is a hassle. While we're on the subject, what is a good well-supported wireless adapter to get?

Thanks in advance

---

