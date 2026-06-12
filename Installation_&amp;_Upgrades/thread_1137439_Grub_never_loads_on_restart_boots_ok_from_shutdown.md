---
title: "Grub never loads on restart boots ok from shutdown"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by dajasc on 2009-04-25
I don't really understand what's going on here or what information would be useful so if there's more needed let me know.

This is a fresh install of 9.04 on an AMD AM3 socket system.  It also dual boots with XP.  I installed XP first on its own hard drive.  Then I set the empty disk that was to have Ubuntu installed on it as the first hard disk to boot from in the BIOS.  Then I installed Ubuntu on it.

If I shut the system completely down it loads GRUB and then into Ubuntu fine.  If I restart the system it hangs at the spot just before it normally says that it is loading GRUB.  Then it just sits there.  If I use the power switch to force it off and then start it up it loads GRUB normally from there and things are fine.

Anyone have any thoughts on this?  It isn't a complete killer but it is a serious irritant.

A little more info.  When I restarted, selecting the Windows disk as a boot disk, Windows also refused to boot.  However, if I shut down boot into Windows and then restart it's fine.  So, somehow Ubuntu itself is doing something that is stopping anything from booting on a restart but completed shutdown is ok.

---

### Post by dajasc on 2009-04-27
I don't know if this is related but I have noticed that when booting into ubuntu I get softreset failed errors on all the drives but then it goes ahead and boots anyway.  I have searched this error and it appears to be a known bug.

I haven't seen people reporting this error also reporting inability to restart like what I'm seeing.

Anyone?  Ideas?

---

### Post by lvleph on 2009-04-27
Does it happen on both a restart from Windows and a restart from Ubuntu?

---

### Post by ronparent on 2009-04-27
I disagree with you conclusion. It appears more to be a bios thing. Try posting your motherboard and bios versions to see if anyone with direct access to the same hardware has experienced your problem.

---

### Post by dajasc on 2009-04-29
No, it does not happen on restart from windows.  However, if I have booted into Ubuntu and then shut completely down and restart the system clock is hours off.  It also does not happen if I just use windows.

The motherboard is a GIGABYTE GA-MA790XT-UD4P AM3 DDR3 AMD 790X ATX AMD Motherboard

BIOS is Award Software International F2, 1/16/2009

---

### Post by dajasc on 2009-05-05
I should also mention that on boot there are "softreset error device not ready" one message for each hard drive.  It still boots but I wonder if this is connected somehow to the problem.

---

### Post by dajasc on 2009-05-10
Even though no one is answering anything on this thread I thought I'd post what little I've found out.

Debian 5.01 behaves identically to Ubuntu.  They both give softrestet errors on the drives on startup and neither can be restarted.

Puppy 4.01 (also based on Debian) starts and restarts fine with no errors.  I think it uses an older version of the linux kernel which may mean the bug is only in more recent versions.  It may have nothing to do with that, I really am totally out of my league on troubleshooting this and will probably just give up and go windows only on this machine shortly.

Anyway, still very irritating.

---

### Post by gamblor01 on 2009-05-10
I have seen this error happen sometimes with my Ubuntu virtual machine (running on my Mac) but never with my physical Desktop (which boots Ubuntu, WinXP, Fedora, and up until recently, Slackware.  Now I just use that "Slackware" partition as my test partition, to try out all sorts of distros).

I have never seen this problem on my physical system, but certainly the VM requires me to send it a hard reboot signal.  My VM is Ubuntu 8.04 and I always shut it down properly when I'm done with it, but I still have the issue sometimes.

Strange that you only seem to get this problem if you don't shut down completely.  I have a Gigabyte GA-MA770-UD3 board in my system so it's not too terribly different than yours.

---

### Post by dajasc on 2009-05-11
I only get the completely-lock-on-boot problem on restart.  But, there is some weirdness even with a complete shutdown.  When I start after having shut Ubuntu down, my system clock is off by hours.

---

### Post by orange-wedge on 2009-05-11
the clock problem has nothing to do with the boot issue...  have you enabled ntp on your ubuntu system.  you may need to install the package.

---

### Post by PRC09 on 2009-05-11
I have had this exact problem.I have been experimenting on various systems and different drives and configurations such as dual and triple boots and such and when this occured it was only after added the third hard drive.The only way I could solve it was to put in a higher output power supply.So it might be that or the connector to the drive.Also check the jumper settings on the drives themselves ie:master,slave or cable select are set properly.

---

### Post by dajasc on 2009-05-14
I did upgrade the power supply (750 W Corsair) so that should be fine.  Drives are all SATA, so no jumpers to set.  The error occurs on all 5 drives, so I don't think lose cable could be the cause.

---

### Post by dajasc on 2010-01-17
In case anyone stumbles on this old thread.  The problem is a linux kernel bug that has just recently been assigned to someone.  Hopefully it will be fixed.

---

