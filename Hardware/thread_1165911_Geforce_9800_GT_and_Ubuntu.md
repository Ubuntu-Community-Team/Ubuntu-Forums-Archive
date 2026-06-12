---
title: "Geforce 9800 GT and Ubuntu"
date: 2009-05-21
forum: Hardware
---

### Post by docdraino on 2009-05-21
i've done some searching and i haven't found anything that really pertains to my problem. after i found out my ATI graphics card wasn't supported fully by Ubuntu Jaunty, i thought it would be a good idea to finally get a new graphics card. however, after i installed my new Galaxy Geforce 9800 GT 512 mb card, jaunty and intrepid cease to work.

both seem to crash on start up, the progress bar moves a little bit and just stays there forever. when i had jaunty on my system i tried going into safe mode, but the problem persisted. also, when i try the TRY OUT option with the cd, it does the same thing.

i'm currently running windows right now and i'm sorely missing my ubuntu fix. if anyone could help a guy out it would be GREATLY appreciated.

---

### Post by docdraino on 2009-05-26
i'm bumping this thread because it seems that both fedora and ubuntu 8.04 have a problem with this card.

am i the only person who can't even run linux live cds with this card? :(

---

### Post by docdraino on 2009-07-07
can anyone help me? i haven't been able to use ubuntu for months on my main computer because of this. i've tried using the driver cd, but it was a no go.

---

### Post by docdraino on 2009-07-13
i'm bumping this once again because i can't seem to find anything like this problem. my system simply refuses to boot any linux distros (at least, any distro i'd think about using outside of ubuntu). 

if anyone could guide me to where i can get help it would be greatly appreciated.

---

### Post by docdraino on 2009-07-15
Ok, so i've been messing around with boot options. I haven't got anywhere outside of getting the kernel messages and I've found that it seems on boot the kernel hangs of this:

```
[55.037374] ivtv 0000.03.04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
```

i've tried vga, xforcevesa, irqpoll, but nothing seems to change the hang up. it has to be hardware related because this has only happened because i got a new video card. :(

---

### Post by SeePU on 2009-07-15
Can you re-install?  

Xorg files or files to do with the graphics drivers (X included) probably still have some leftover files to do with the past ATI card or something.

Nvidia cards are much better supported in Linux even if it is a binary driver.

Your GeForce 9800 GT card will work fine in Ubuntu but if you re-installed X or started fresh, you would probably have an easier time of it.

If you don't want to re-install, you could try installing the latest Nvidia driver and it might re-write Xorg for you.   You have to go to the command line to do this, however.  I've done it before so I recommend reading up on it.  Install the drivers the 'Nvidia way' and install the latest driver from Nvidia's driver downloads site.  You choose the Linux version and I think they are at ver. 185 or something like that.  

The re-write of the driver from the Nvidia utility (it will run when you enter the required commands in a full-screen terminal) should fix the problem.  

If you can't boot up at all and are willing to re-install, try the System Rescue CD and use GParted on it.  You'll need a computer that boots to download the iso file and then burn system rescue cd.  Make sure your BIOS settings is set so that the CD/ROM or DVD Burner will boot as 1st priority and HDD is second.

Edit:  try this.... A good idea was presented by a poster for solving a similar problem...

> At worst, just rename your /etc/X11/xorg.conf file to something else. The next time X starts up, it will see there is no xorg.conf file and generate a default one. By default, X autodetects the card and applies the most appropriate (non-proprietary) driver. In the case of Nvidia, this will be the free "nv" driver.

You can't boot up to do this so use a LiveCD and enter into CLI and become root.  So just 'sudo' and rename that file above.  Then reboot and see if that file is rewritten for you.  You'll use either VESA driver or the nv driver, I forget what exactly.  That would allow you to start over without re-installing.

---

### Post by docdraino on 2009-07-16
so i reinstalled ubuntu and it's still not working, neither will the recovery mode as it just hangs as well. however, i've done some research and i believe it's an IRQ problem. i've tried most of the common irq options though, so i am at a lost at how to fix this.

---

### Post by Maheriano on 2009-07-16
I'm running a GeForce 8400GT and an ATI HD3450 on 2 different systems with no problems. I'm pretty sure my parents have a 9800GT though it may be a 9600GT and I know they were running on the LiveCD for 2 weeks or so while I swapped out a dead drive for them. Then it was back to Windows for them unfortunately.

---

### Post by latev on 2009-07-29
I'm running Jaunty on my EVGA 9800 GT card and aside from the TV Out issue /see my other post on the subject/ it's running flawlessly, the contrast between this card and my old crappy ATI Saphire is enormous!

I would suggest you give it a try with a bunch of live distros out there and see if you can find one that works with your card.
/It may be worth tweaking it in the BIOS as well/

---

