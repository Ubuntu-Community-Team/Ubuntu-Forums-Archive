---
title: "My HP notebook won't wake up from standby or hibernation"
date: 2008-12-20
forum: Hardware
---

### Post by dserodio on 2008-12-20
I have a **HP Pavillion DV5-1160BR** notebook (AMD Turion X2) running Intrepid. With the stock **2.6.28-9-generic** kernel, if I try to put it to standby or hibernate it won't wake up. When I hit Power, the screen stays blank, and the Caps Lock and Scroll Lock keys keep blinking.

I tried compiling a **2.6.28-3** kernel, and it got a little better: it woke up from standby, but the keyboard and touchpad are dead. I was able to plug in a USB mouse and it worked thou, but it's useless as the keyboard doesn't work.
What's weird is that it's broken even after a reboot, forcing me to revert to the previous 2.6.27 kernel.

What can I do to make it work? Using a notebook without being able to standby sucks, I end up using Windows much more that I wanted to...

---

### Post by AlexBellisBrown on 2008-12-20
Ive always had a problem with suspend/hibernation on Ubuntu, Windows works fine, but its just one of those things they keep trying to fix. I read on Linus´s blog the other week that they had found the cause or something, and had fixed/trying to fix it. Lets just hope the updates bring the goods next time.

---

### Post by dserodio on 2008-12-20
> **AlexBellisBrown said:**
> Ive always had a problem with suspend/hibernation on Ubuntu, Windows works fine, but its just one of those things they keep trying to fix. I read on Linus´s blog the other week that they had found the cause or something, and had fixed/trying to fix it. Lets just hope the updates bring the goods next time.
Yeah, I read it too, but since he mentioned an Intel motherboard and mine is AMD-based I didn't get so hopeful. :-(

---

### Post by AlexBellisBrown on 2008-12-20
Ive got an intel motherboard and it still doesnt work. Lets live in hope :)

---

### Post by nelliott71 on 2008-12-20
I have an HP (intel/nvidia) and found that I could not suspend/resume unless I was using the non-Free NVidia driver... and I had to REBOOT (not just restart X) before this worked.

Sometimes I still have problems with my WIFI (iwl3945) working after suspend/resume.

---

### Post by ShokTHX on 2008-12-20
Was just searching to see if there was a solution for this. I've never gotten the suspend/hibernate/sleep working on mine (HP dv8000). This is just about the only part of Ubuntu that has not worked completely on this machine.
On the other hand, a straight up boot in Ubuntu is just as fast as a return from hibernate in Windows XP (probably why this has not been a priority for me). I can only imagine how convenient a hibernate in Ubuntu will be.
One odd thing I have noticed is that a boot to Ubuntu will force XP to do a complete start even if it was closed to hibernate. I wonder if the dual/triple boot has something to do with it.

---

### Post by IQRules on 2008-12-20
It can't be dual boot or triple boot.
Search on ACPI on/off with grub.
I have IBM R32, old laptop, spent hours on wifi/lan/bluetooth; it works great.

---

### Post by gabriel2007 on 2008-12-25
with my vostro 1700 laptop standby does not work, if I close the lid , you can feel how it gets sooooooooooo hot near the battery at the beggining and after a while the whole laptop is burning, be sure not to close the lid without manually clicking on standby or hibernation.

greetings

---

### Post by satellitex86 on 2009-01-04
I have a Toshiba Satellite A105-s2061. When I tell it to hibernate or go into standby and then try to resume, the computer seems to turn back on, but the screen stays black, and nothing else seems to happen. 
There is no response from the toucpad or keyboard.

---

### Post by archeryguru2000 on 2009-01-23
> **satellitex86 said:**
> When I tell it to hibernate or go into standby and then try to resume, the computer seems to turn back on, but the screen stays black, and nothing else seems to happen. 
There is no response from the toucpad or keyboard.

I have this identical problem on my HP Pavillion dv6000.  I am eventually required to do a hard shut down, which I hate!    I was simply searching online for some assistance on this issue and ran across this forum.  I hope somebody has some insight to this.  I'm running U-8.04 with NVidia display and AMD Turion 64 X2.  Some guidance in resolving this situation would be greatly appreciated.

Thanks
~~archery~~

---

### Post by jcoppala on 2009-01-23
Hi
I have an HP Pavilion dv2707TX with nvidia and intel cpu & motherboard... ubuntu 8.10 anyway I had the some issue but then I read those post and I cant remember what I did but know its working suspend/hibernate good luck...

[http://en.opensuse.org/S2ram](http://en.opensuse.org/S2ram)
[http://en.opensuse.org/Disk_Power_Management](http://en.opensuse.org/Disk_Power_Management)
[http://lwn.net/Articles/257426/](http://lwn.net/Articles/257426/)
[https://wiki.kubuntu.org/DebuggingKernelSuspend](https://wiki.kubuntu.org/DebuggingKernelSuspend)
[http://ubuntuforums.org/showthread.php?t=750216](http://ubuntuforums.org/showthread.php?t=750216)

---

### Post by waxxey on 2009-02-01
i have an hp compaq 6715b running on 1g ram and mobile AMD semphron with ubuntu 8.10. i can't seem to get the hibernation or suspend to work at all i have tried to turn of apic and i put iommu=soft, but both stil frezes on resume. everyone else semes to atleast have the suspend option partialy working. does anyone know what to do?

---

### Post by eigenman on 2009-02-10
Hey Archery,

I have a similar laptop (hp dv6607), running U-8.10, and suspend seems to work when I'm connected to the AC outlet, and fails badly when I'm not connected. I've actually been able to rescue my laptop from a hard reset by connecting it to the power outlet few times. I'm not sure if your situation is similar, but figured just in case it helps.

Best,
Eigenman

---

### Post by archeryguru2000 on 2009-02-13
> **eigenman said:**
> Hey Archery,

I have a similar laptop (hp dv6607), running U-8.10, and suspend seems to work when I'm connected to the AC outlet, and fails badly when I'm not connected. I've actually been able to rescue my laptop from a hard reset by connecting it to the power outlet few times. I'm not sure if your situation is similar, but figured just in case it helps.

Best,
Eigenman

Thank you very much for that bit of info.  I am certain that my power cord has something to do with it.  If I put it to sleep with power cord connected and **then** unplug the cord... PERMANENT SLEEPY TIME!  :(  I've even gone so far as to contact HP and ask if anybody else has contacted them about this.  They promptly stated that the sleep command must not have anything to do with the problem.  I beg to differ.  Anyway, I will try your little trick.  Does anybody know where the logs/records for processes are kept.  I wanna say they are in /var/log but I cannot seem to find which one I'm looking for.  Thanks again for your tip, I'll keep everyone posted on my progress.

---

### Post by Vegetarianrage on 2009-04-23
After fiddling around with this issue on my HP Pavillion DV6000 (6736nr) I discovered that certain things hang during both suspend and boot.

It seems to be related to certain processes starting/ending such as smb-daemon etc.

I noticed however that simply pressing the power button once and waiting will spur it on to finish sleeping/waking up. Sometimes i have to push it once, wait a second to see if it finishes, and then press again if necessary.

you may have to blacklist the "button" module if you find that pressing the button causes it to shutdown after it wakes up.

---

### Post by whitethunder on 2009-04-24
Hi All, 

I have a desktop which I put together myself. I have the ASRock G43Twins-FullHD motherboard. Things work fine (except the display resolution) when I shut down and turn on again. 

When I suspend or hibernate, I get a black screen and my mouse and keyboard don't work. The computer turns on though. I am running Ubuntu 9.04 and have installed all updates. 

I am amazed that this problem still exists after these many years!

---

### Post by ladr0n on 2009-05-28
> **Vegetarianrage said:**
> 
I noticed however that simply pressing the power button once and waiting will spur it on to finish sleeping/waking up. Sometimes i have to push it once, wait a second to see if it finishes, and then press again if necessary.


I've noticed the same thing on 9.04 with my dv6000 (AMD/nVidia). Also, when it resumes after I tap the power button again, the "shut down" dialog is being displayed as though the computer had fully resumed when I pressed the button.  It seems like getting it to work correctly from this point should definitely be possible, especially since it worked in 8.04.

I've tried a couple different combinations of the proprietary drivers, it seems to only even get this far using the nVidia 180 driver and the Broadcom STA.

I never got suspend to work on 8.10 so I just continued using 8.04 (in which suspend worked effortlessly) but I would like to switch to 9.04 if this issue can be fully resolved.

---

### Post by Valde_91 on 2009-06-30
Same problem on my hp compaq nx7000. I'm running the kernel 2.6.29-4, but the problem is still there and ubuntu 9.04. The problem is even worse with the new kernel. With kernel 2.6.28 I've the problem of blank screen on resuming only if I put the machine in stand-by and then I unplug or plug the AC cord. Now I have always this problem.

I've also a hp mini 2140, with 2.6.29 kernel and ubuntu 9.04. If you stand-by the machine mannually, the resuming is working fine on this machine. But is impossible to get stand-by by closing the lid. 

anyone has filled a bug report in launchpad?

bye bye Valde

---

