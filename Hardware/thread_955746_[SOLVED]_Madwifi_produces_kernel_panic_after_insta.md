---
title: "[SOLVED] Madwifi produces kernel panic after installing new kernel"
date: 2008-10-22
forum: Hardware
---

### Post by athrpf on 2008-10-22
Hey everyone,

recently ubuntu prompted me to upgrade my kernel from 
2.6.24-19-generic
to
2.6.24-21-generic

which I thought was fine so I went ahead with it. After installing that kernel, my wireless LAN didn't work anymore. I use a special branch of madwifi (madwifi-hal-0.10.5.6-r3861-20080903) that supports my atheros 5007 card. So I again followed the instructions in unloading all loaded wlan modules, and compiled and installed the driver again. This special branch of madwifi needs me to restart my system. After I restarted, the system crashed saying something like 
........(a lot of adresses)..... wlan.....
kernel panic: not syncing fatal exception on interrupt

I could get my system to start up again using the recovery mode and uninstalling the drivers. 

Now my question: 
- has anyone encountered this problem before?
- did I do something stupid (I am still kind of new to linux)?
- does anyone have any ideas on how to get both my system and the wifi to work?

Any help would be greatly appreciated!

---

### Post by rlogan on 2008-10-25
I did exactly what you have done on our laptop and killed the kernal. So I uninstalled the 2.6.24-21 kernal and resumed usage of the 2.6.24-19. I will watch this link on the hope of finding a solution. But could be all in vain with Intrepid out in 5 days.

I am hoping that the 2.6.27 included in Intrepid will fix our woes, not holding my breath as the beta/alphas were not looking good. Will have to try the RC now that its out.

---

### Post by Faryshta on 2008-10-26
First of all, what MadWifi driver are you using?

Because there was a "special" branch which is now unsoported, and not recommended.

I have your same card and I use madwifi hal [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/)

Any information you can add my GTalk [email]angeldelcaos@gmail.com[/email]

---

### Post by malleus74 on 2008-10-28
A lot of people are having similar problems to you. Take a look at: [http://ubuntuforums.org/showthread.php?t=948584](http://ubuntuforums.org/showthread.php?t=948584) 

A general consensus seems to be to boot with the .24-19 kernel until a solution is fixed. Also, beware the 'security update' download for this kernel...

---

### Post by Rocket on 2008-10-28
Same happened to me as the first poster, earlier kernel (19) works fine. Running Asus EEE 701 with Ubuntu on USB external 160g Sata drive. 
I will try other kernels when I get time. Do you run the Atheros wireless? I suspect it is something to do with this hardware, it crashes when detecting the Wlan hardware. I removed the madwifi, then removed and reinstalled the crashing Kernel(21). The problem still remains. This kernel did work ok before installing madwifi drivers.
Regards
Rod
edit: I also used madwifi-hal-0.10.5.6-r3861-20080903

---

### Post by malleus74 on 2008-10-29
[I]"DKMS (by Dell) is included in Ubuntu 8.10, allowing kernel drivers to be automatically rebuilt when new kernels are released. This makes it possible for kernel package updates to be made available immediately without waiting for rebuilds of driver packages, and without third-party driver packages becoming out of date when installing these kernel updates. "

I think this is why they're not seeming to worry about kernel issues. [/I]

I posted this over in the other thread, but it's relevant here. If you can post your hardware, ubuntu version, problem with .24-21 in the other thread, all of you, please do it! :) We're trying to get the developers' attention...

I have atheros 5007EG wireless. I *need *wifi, or I'm stuck booting into Vista to do pretty much anything productive, search the threads, and then reboot into Ubuntu and try a fix... not fun.

---

### Post by athrpf on 2008-10-29
I am sorry I didn't reply - for some reason I didn't get notification emails.

I just installed ubuntu 8.10 with Kernel 2.6.27-7 , and that works fine with madwifi 10.5.6 

Thanks for all your support!

---

