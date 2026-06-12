---
title: "Suspend problems on Dell C400"
date: 2005-05-24
forum: Hardware &amp; Laptops
---

### Post by psilo on 2005-05-24
I'm having getting suspend-to-ram to work on a Dell C400 with a fresh install.  The Fn-Esc key sequence get detected and it seems to suspend with no problems (as long as the wifi card isn't inserted, I'll get that sorted out once I get s2r working without it).  When I hit the power button to bring it back the power light comes back on, I get a second of disk activity, but the screen stays dark and the machine completely locks up.  The HoaryPMResults page reports that other Latitude C series laptops seem to get this working with no problem.  What am I missing?

---

### Post by psilo on 2005-05-26
anyone...

anyone...

I'll be using this machine for some 3-hr lecture classes and not having s2r is a showstopper.

---

### Post by Chunk of Earth on 2005-05-26
Have you tried adding the **nolapic** option to your kernel boot parameters in /boot/grub/menu.lst?

```
kernel	    /boot/vmlinuz-2.6.10-5-686 root=/dev/hda3 ro nolapic acpi_irq_isa=7 quiet splash

```

---

### Post by psilo on 2005-05-27
Just tried the nolapic kernel option and it seems like it had no effect.  Exactly the same thing happens.  Thanks for giving it a shot though.  Any other suggestions out there?

 ](*,)

---

### Post by GOwin on 2005-08-18
Have you managed to resolve this?

---

### Post by bala on 2005-08-18
Do you have nvidia graphics card? I have one and i'm facing the same problem. I searched for solution and it looks like currently there are no solution for "official nvidia driver". if you use "nv" driver then it will work fine(colours are not good, however). 

some people suggested using 6xxx series of driver instead of 7xxx. i haven't tried that yet...

Anyone having some other simple solution?

---

### Post by SwinginStan on 2005-10-13
I would also very much like a solution to this problem, i have the intel accelerated graphics card. Suspend to ram is a very valuable feature, and I would love to have it in linux!

---

### Post by rgrosz on 2005-10-26
I recently installed kubuntu Breezy on my C400. I haven't been able to get either suspend to RAM or suspend to disk (hibernate) to work (I am a real noob).

I can right click on the battery icon, and choose hibernate. Then it takes a few minutes writing to disk. Then I am sitting at a ubuntu login prompt. 

Is that what I should see? :confused:

Now I see that there are [known problems with suspend on the Dell C400]("https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeC400")

---

### Post by ramkiraman on 2005-11-18
Here are some steps I have put together that helped me get suspend/resume working on my hoary system on a dell c400:

It also appears that the suspend  problem is connected to getting an external monitor working - that was also fixed with the below actions.
(these actions are compiled from various help forums and nothing is my own - thank you to everybody who helped.)  

1. Edit /boot/grub/menu.lst to have following options in kernel line
nolapic  acpi_irq_isa=7
2. Edit /etc/defaiult/acpi-support
allow ACPI_sleep = true
3. Apply the Hezekiah fix: ([http://ubuntuforums.org/archive/index.php/t-76357.html](http://ubuntuforums.org/archive/index.php/t-76357.html))

Edit etc/acpi folder in the following way:
sudo mv lid-sh lid-sh.ORIGINAL
sudp ln -s sleep.sh lid.sh

these actions led to:
1. suspend /resume working great on lid close
2. Suspend option appearing on the logout menu and actually working fine
3. It does not fix the fn+suspend issue.

hope it helps some of you
Ramki

---

### Post by utcamperj on 2005-11-25
I have been beating on the suspend to ram and hibernate issue on a Dell C400 using Ubuntu Breezy now off and on for a week.  Having NEVER had suspend or hibernate work under Linux, it has been difficult to say the least.  None of the recommendations so far have made any difference on this machine.

It's a standard C400 with the integrated Intel i8xx video chipset (i830?  using i810 driver).  I've only tried 2.6 kernels (2.6.386 by default, and just tried 2.6.686).  When you suspend via any method (log out, suspend, or hacking the lid.sh script and closing the lid) there is some disk activity, the screen blanks really quickly, and it powers down with no green lights left on.  Closing/reopening the screen kicks the power back on, the hard drive light flashes for a second and then you hear the hard drive power up, and that's about it.  I don't think it actually reads the drive, and the screen stays black.:confused:

---

### Post by Joeak on 2005-11-30
FYI, see my posts on [http://ubuntuforums.org/showthread.php?p=531943#poststop](http://ubuntuforums.org/showthread.php?p=531943#poststop) for how I fixed hibernate.

---

