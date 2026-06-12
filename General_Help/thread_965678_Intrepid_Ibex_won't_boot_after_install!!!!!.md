---
title: "Intrepid Ibex won't boot after install!!!!!"
date: 2008-10-31
forum: General Help
---

### Post by vs8 on 2008-10-31
I installed Intrepid a few minutes ago and the live disc booted ok and everything seemed nice for an instalation. So I installed it an an Acer Aspire 5050-5410 and when I restarted the system I got the stupid busybox prompt!

My question is, why does the live disc work so well but when you install the system it wont boot?

Can someone help me?

---

### Post by vs8 on 2008-10-31
Anyone? Please help me!!!

Each time it drops to the shell it gives different errors, the last time it gave me this:
Gave up waiting for root device. Common Problems:
-Boot argd (cat .proc/cmdline)
  -Check rootdelay= (did the system wait long enough?)
  -Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls/dev)
ALERT! /dev/disk/by-uuid/c420f507-9cf4-403a-a99b-695ce283cf4b odes not exist. Dropping to a shell!

BusyBox v 1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

Now I booted the Live disc and it's working perfectly. I don't get this!

---

### Post by vs8 on 2008-11-02
After the install I was able to boot Ubuntu in recovery mode after dozens of times trying. I updated the system, it needed to reboot, knowing that maybe it will never boot back again I rebooted the system to see the busybox thing again. I've been trying to boot again and again but nothing.

It only happens with Ubuntu and Linux Mint, maybe it happens with all Debian based distros. Fedora, PCLinux, openSUSE, Mandriva work great. I've installed all of them flawlessly.

Intrepid RC worked with the kernel 2.6.27-4, but whenever I tried to use kernel 2.6.27-7 it gave me the error (I re-installed again and never worked). I upgraded the system online but it didn't go as expected, so I tried the 8.10 (official release) live disc and it ran smoothly, I decided to install it because the live disc always boots normally, but after instalation it gave me the busybox prompt.

I have all types of busybox errors. I get the root delay thing, 8139 driver thing (or something like that), I also get that some file dev/disk/by uuid doesn't exist blah blah blah. It totally suck's!!!

---

### Post by ugm6hr on 2008-11-02
Did you run the Check CD option on the LiveCD?

I have a 5051AWXMi (a 5050 derivative in UK), and 8.04.1 works flawlessly.  Haven't made the step up to 8.10 yet.

---

### Post by fishacre on 2008-11-07
Hi,

I've had a similar problem after upgrading to 8.10 - ie 
[....]
/dev/disk/by-uuid/[....] does not exist

And it seems to be specific to kernel 2.6.27-7 because after I switch to 2.6.24-21, either by entering the grub menu before booting and changing the selection or by altering /boot/grub/menu.lst, it boots perfectly.

---

### Post by Magnes on 2008-11-07
> **vs8 said:**
> I installed Intrepid a few minutes ago and the live disc booted ok and everything seemed nice for an instalation. So I installed it an an Acer Aspire 5050-5410 and when I restarted the system I got the stupid busybox prompt!

My question is, why does the live disc work so well but when you install the system it wont boot?

Can someone help me?


Wait a minute or two (!) in the busybox then enter: exit and hit enter. The system will boot. Here is the bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/290153](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/290153)

---

### Post by grashdur on 2008-11-09
Some problem here on my Gateway (with SATA drive). It seems that if I keep typing "exit" three or four times, Ubuntu will eventually boot up normally. 

I have a question about the link in that last posting:

> Adding rootdelay=90 to the current kernel line in menu.list gets a good boot. It's at least a work around.

I've found the menu.lst file (correct filename?) in several places, and since I could only install Ubuntu thru Wubi, I'm thinking I should modify the file in /host/ubuntu/winboot rather than the file in /boot/grub. Right? 

And which line is the "current kernel line"? Would I be adding to an existing line or making a new one?

But I get other boot errors too: Sometimes instead of the initramfs (gave up waiting) error, I just get hung up at a blank screen, and sometimes my username and password are not accepted as valid. 

Should I just reinstall Hardy Heron, or continue setting up Itchy Ibex? If I stick it out, will updates fix the problem?

---

### Post by putanitsa on 2008-11-10
Thank you Magnes, I finally managed to boot Intrepid.

Is there something I can do so I don't have to wait 1-2 minutes and type exit everytime I boot? If so, please explain in newbie language :P

---

### Post by vs8 on 2008-11-25
You don't have to wait a minute or two on my laptop, you can boot as soon as the busybox thing appears by typing exit.

Another workaround is typing all_generic_ide in the kernel parameters but it gets you a long delay.

---

### Post by Duroon on 2008-11-25
I have been running Ibex for a couple of weeks now on my acer aspire 6930 with no troubles at all. I shut down the laptop to come to work this morning and when I arrived at work this bug cropped up. It starts to boot and then drops to the busybox ash prompt after stating Alert! /dev/disk/by-uuid/(...) does not exist dropping to a shell etc.

Here is the kicker, it won't boot from the live cd I used for install either. This system has been working flawlessly for over two weeks on a brand new machine. None of the workarounds seem to do anything either. I have tried the rootdelay and typing in exit to try and continue booting, no good. Any new ideas?

---

### Post by Duroon on 2008-11-25
On a further note, I removed the hard drive from the laptop and tried to boot off of the live cd, still drops to the busybox prompt. I do believe this could be a hardware issue.

---

### Post by philinux on 2008-11-25
If you can get a livecd to boot up use

blkid

to check the uuid's and then check that fstab entries match

---

### Post by Duroon on 2008-11-25
Unfortunately the live cd won't boot up either, that's why I think it must be a hardware issue. I returned it to the store I bought it from all of 16 days ago. They have a 14 day return policy of course, so it has to be sent back to Acer to have the hardware tested.

---

### Post by team_milan on 2008-11-29
i had this problem too, tried re-installing and reformatting about 7 or 8 times, and then installing from within windows and that didnt work either. came on here and read that all i needed to do was simply type "exit" 

thank you guys, it works like a charm and i feel like an idiot now.

---

### Post by vs8 on 2008-11-29
Do you guys know what was my workaround?

Instead of typing exit every time I turned the laptop on or waiting for the all_generic_ide delay, I went distro hopping! 

openSUSE is great, and it doesn't have the BusyBox-sreen-of-death (I believe that this is a Ubuntu only problem). the only gripe is the hardware drivers. But they are not impossible to install plus the system is incredibly beautiful.

I'll be using SUSE until Cannonical does something about this problem.


-------

Nevermind SUSE doesn't know how to play nice with drivers!
Sorry, I was mad!

---

### Post by Duroon on 2008-12-10
I have finally received word about my laptop. Acer is shipping it back to the store, according to their tests there is nothing wrong with the hardware and they could not get the machine to duplicate the problem so they did nothing. I have owned it all of 5 weeks now, 3 of which it has been in for service. Needless to say I am going to rip the manager of Best Buy a new one if it doesn't work properly when I get it back in a couple of days.

---

### Post by Duroon on 2008-12-13
Ok, I received my laptop on Thursday from Best Buy. They told me that they had done nothing, Acer also had done nothing as they could not replicate the problem. I fired it up on the counter in Best Buy and it went right to the log in screen, booted up just fine. Nothing was done to it though so what the heck? I am just waiting for it to quit working again at this point.

---

