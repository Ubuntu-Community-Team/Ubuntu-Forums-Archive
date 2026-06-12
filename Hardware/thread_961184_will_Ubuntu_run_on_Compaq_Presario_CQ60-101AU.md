---
title: "will Ubuntu run on Compaq Presario CQ60-101AU"
date: 2008-10-28
forum: Hardware
---

### Post by vincirufus on 2008-10-28
Hi,
I'm looking at buying the [Compaq Presario CQ60-101AU]("http://h10010.www1.hp.com/wwpc/in/en/ho/WF06b/321957-321957-3329742-89318-89318-3768152-3809616.html")
The specs include a 16" wide Screen, AMD Athlon and Atheros Wireless card.
 or the Compaq-Presario CQ60-104TU
which is  an Intel Dual Core with a 16 " screen and the same Atheros Wireless card

The Engineers at the made it very clear that Win XP will not run on both of them.. and I'll need to run Vista.. I'm more keen on running Ubuntu on this one, either with Genome or KDE.

Does anybody have an experience of running Ubuntu on anyone of these models, or did you face any issues trying to get Ubuntu working on them..
 
I'll need the wireless, audio, and screen resolutions to be working fine.. at the least

Thanks for your help in advance
Vinci

---

### Post by morkenGNU on 2008-11-02
No, unfortunately not. I tried it with the versions 8.04, 8.10, and even 7.04. I tried both 32bit and 64bit versions, and the wubi installer within Vista. Ubuntu does not start. Same problem with PCLOS 2007 and Mint. Fedora seems to have the same problem with the CQ60, according to this: [http://www.linuxforums.org/forum/installation/132529-linux-installation-compaq-presario-cq60-101au.html](http://www.linuxforums.org/forum/installation/132529-linux-installation-compaq-presario-cq60-101au.html)

For some strange reason Mandriva and Sidux work on this laptop. Those were the only two distributions which worked. I did not try Debian and SUSE, these could work as well.

---

### Post by vincirufus on 2008-11-06
OK I took the risk and bought this one.. and I must say I got lucky...
I installed Ubunutu 8.10 in a separate partition and everything worked, right out of the box, wifi was up and running on first boot and my Nvidia drivers started to work after I installed the updates. Didnt have to open up the terminal window for anything.

I even tried installing Kubuntu but didn't have a lot of luck with it, wifi detected but never managed to get connected, The Network Manager window never opened up. 

I Also tried installing Vista and XP, While Vista installed well except for the NVida graphics, I had a touch time trying to get it work on XP, it didnt detect any of the drivers, and I had to manually select each of the driver and its correct version to get it running.


So out of the 4 OS versions that I've tried, Ubuntu was the easiest and cleanest install..

Cheers
Vinci

---

### Post by anurag_gupta on 2008-11-14
i tried installing on compaq cq60-104Tu which is same as 101AU only difference is that it has intel dual core

couldn't install Linux mint  which is a flavor of ubuntu only. installation failed while loading drivers for lan card. 
error message 
"driver 'sr' needs updating
.....
modprobe abnormal exit"


please help. i have not tried ubuntu till now. i'll try and update u with the results

---

### Post by starcannon on 2008-11-14
I have a HP dv2600 similarly spec'd, and Ubuntu 8.10 clean install made that laptop a linux 100%er; I will note that to get suspend/resume and blank on lid close/open working correctly that I manually installed the nvidia graphics modules(drivers).

On reading the spec's of the Compaq listed at the link by the OP I see nothing that would cause me to think you would have any problems. Go with a clean install, keep /home on its own partition so that you can do clean install upgrades in the future with a very easy way of going back to a previous ubuntu version if you need to.

GL and keep it fun

---

### Post by MeteoriK on 2008-12-30
I can help you with that, cause I took the plunge and did it.  You can get everything to work, BUT..

The driver for the Atheros wifi card in 8.10 (and in Jaunty Alpha 2, which I tried for the hell of it - don't bother - it breaks nvidia graphics by uninstalling it) is out of date, so be prepared to sit on the floor for a couple of hours with an ethernet cable hanging out while you manually compile the latest snapshot of compat-wifi-2.6 into your kernel.  Even then, it's a bit messy, as you're doing this manually.

If you're not savvy enough to compile kernel modules, don't bother.  Otherwise, go for it, and lets hope that Jaunty has the updated drivers in it.

---

### Post by MeteoriK on 2008-12-30
Actually, some other issues - the touchpad disable/disable button creates two keyboard codes, one for on, the other for off.  The latter doesn't have a scancode, so if you want to bind it to whatever toggles the keypad on and off, you'll have to manually give it a scancode in rc.local.

The wifi button doesn't appear to do anything, and doesn't flash blue even when you finally get wifi working (it does in vista).

The brightness keys don't do anything - not played with them yet.

---

### Post by som6673 on 2009-01-23
> **vincirufus said:**
> OK I took the risk and bought this one.. and I must say I got lucky...
I installed Ubunutu 8.10 in a separate partition and everything worked, right out of the box, wifi was up and running on first boot and my Nvidia drivers started to work after I installed the updates. Didnt have to open up the terminal window for anything.

I even tried installing Kubuntu but didn't have a lot of luck with it, wifi detected but never managed to get connected, The Network Manager window never opened up. 

I Also tried installing Vista and XP, While Vista installed well except for the NVida graphics, I had a touch time trying to get it work on XP, it didnt detect any of the drivers, and I had to manually select each of the driver and its correct version to get it running.


So out of the 4 OS versions that I've tried, Ubuntu was the easiest and cleanest install..

Cheers
Vinci
can u plz. help me.........how 2 instal  nvidia drivers ??

---

### Post by alienzrc on 2009-04-01
hi vinci,
me havn the same laptop 101AU, and installed ubuntu 8.10, kernel 2.6.27-14. i have installed on a separate partion and the install was ok. i updated my system from update manager. then from hardware auto detection i installed nvidia 180.11. then sarted the problem of sluggish windows. so plz can u say me the entire steps in brief how did u get everything working. which nvidia version driver did u install and from where? 
thanks in advance.. take care and plz help me

---

