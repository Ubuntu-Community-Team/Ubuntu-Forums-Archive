---
title: "Ubuntu 7.04 won't install on an older vaio laptop"
date: 2007-05-14
forum: Hardware &amp; Laptops
---

### Post by suchawato on 2007-05-14
Even with the alternate install disc.
fixes?

---

### Post by carlosponti on 2007-05-14
You might include some useful information. like the specs of your laptop and model of sony. also you might post any errors you might get. tell us the situation about what happened when you try installing. does it load the live cd.

---

### Post by suchawato on 2007-05-14
Its a PCG-954A
Pentium 3 processor. 695.6 MHz
254 megs of ram
chipset: intel i815
It won't run the live cd or the text/alternate beyond the initial startup menu .

the cd menu comes up, and when either the live or text install cd is used,
when "install" is selected, it says "loading linux kernel" with the little loader bar, and then it presents a black screen with a little horizontal blinking cursor or "dash" and that's the end of it.
it never gets any farther than that no matter how long I wait.
I am using the correct x86 install version.
I have installed xp Service pack 2 and which works fine if that helps.

the same exact problem comes up with Zenwalk. Exactly the same way.

It was issued with windows ME

---

### Post by suchawato on 2007-05-14
hey, anyone responding to this?

---

### Post by carlosponti on 2007-05-15
if the Pc has a floppy drive you can try installing Debian from floppy. I tried this on an old laptop but the laptop had issues so i couldn't finish but that was after installing to a virtual machine from floppy. not sure what the issue is however. did zenwalk detail any errors in its boot process that you could see?

---

### Post by jerrylamos on 2007-05-15
There are a couple things that work sometimes with older hardware.

First thing I would check is the Bios setting for the Intel graphics video controller.  There is usually a place for shared video memory which might be like 1024 K or 1 MB.  Set this as high as it will go, usually 4096 K or 4 MB.  That has gotten three computers running Ubuntu for me.

Another thing to try when the boot choices come up, push F6 and add these to the end of the line so it will look like:

....quiet splash noapic acpi=off irqpoll

which can work CD Live.  Sometimes just one of the three last settings is needed.  If by chance you decide to do an install, and it does, then those options can be added to the kernel line in /boot/grub/menu.lst (where l is lower case L)

According to the documentation, 256 mb can be enough to run Ubuntu, and Xubuntu.  I find a 1 ghz Pentium to be nice and fast for applications and internet so about 700 khz ought to be O.K.  For install hard disk space absolute minimum about 2 gb + 256 mb for swap.  Some people find CD Live fast enough for useful work, particularly if there's a USB pen drive for saving files, and I've even run CD Live + USB on a computer with no hard drive at all.

Another way to get your feet wet in Linux if the full Ubuntu's don't respond to the above and waiting for a productive posting to help you, is to try a small CD Live Linux Distribution like Puppy:
[http://www.puppylinux.org/user/viewpage.php?page_id=1](http://www.puppylinux.org/user/viewpage.php?page_id=1)

I prefer Ubuntu's which may "just run" or since I like early level pre-releases I'm usually dealing with pre-production bugs....

Cheers, Jerry

---

### Post by whayong on 2007-05-15
Exactly how long did you wait when the black screen came up?

I had the same thing when installing Edgy.  I just kept waiting and it eventually worked.  It's also possible you have a bad burn.

---

### Post by suchawato on 2007-05-17
> **jerrylamos said:**
> There are a couple things that work sometimes with older hardware.

First thing I would check is the Bios setting for the Intel graphics video controller.  There is usually a place for shared video memory which might be like 1024 K or 1 MB.  Set this as high as it will go, usually 4096 K or 4 MB.  That has gotten three computers running Ubuntu for me.

Another thing to try when the boot choices come up, push F6 and add these to the end of the line so it will look like:

....quiet splash noapic acpi=off irqpoll

which can work CD Live.  Sometimes just one of the three last settings is needed.  If by chance you decide to do an install, and it does, then those options can be added to the kernel line in /boot/grub/menu.lst (where l is lower case L)

According to the documentation, 256 mb can be enough to run Ubuntu, and Xubuntu.  I find a 1 ghz Pentium to be nice and fast for applications and internet so about 700 khz ought to be O.K.  For install hard disk space absolute minimum about 2 gb + 256 mb for swap.  Some people find CD Live fast enough for useful work, particularly if there's a USB pen drive for saving files, and I've even run CD Live + USB on a computer with no hard drive at all.

Another way to get your feet wet in Linux if the full Ubuntu's don't respond to the above and waiting for a productive posting to help you, is to try a small CD Live Linux Distribution like Puppy:
[http://www.puppylinux.org/user/viewpage.php?page_id=1](http://www.puppylinux.org/user/viewpage.php?page_id=1)

I prefer Ubuntu's which may "just run" or since I like early level pre-releases I'm usually dealing with pre-production bugs....

Cheers, Jerry
Ok so no bios graphics adjustments possible.
I did enter the commands you suggested and lo in behold, it got past the cursur. however with the live cd, it thought about it more, and made some Cd tray whirring noises for a while and then completely snowcrashed.
When I tried the same approach with the text only installer, it actually installed! But, on the initial bootup it snowcrashed. I then edited the boot kernel command line like you said and rebooted. It still snowcrashed. 
If I boot in recovery mode, it gets to the point of "setting up standard pci resources" where it freezes.
This is the same place every other distro freezes. no go. Zenwalk behaves identically to ubuntu in problems.
openSUSE will install in safe installation mode, but it does not setup a root password during the install (it's supposed to) and because of that, it installs incorrectly and won't let me past the login screen.(no username or password to enter!) so that one installs incorrecty too.
This seems to be a major problem.
I've reported it as a bug. And I will report what I've tried here as an update to the bug.
the command line steps you suggested seems to be a step in the right direction though.

---

### Post by T113 on 2007-05-17
Dumb question, but sometimes we go past the easy answers expecting a hard one.

This is a known, working laptop, right?

---

### Post by suchawato on 2007-05-17
> **T113 said:**
> Dumb question, but sometimes we go past the easy answers expecting a hard one.

This is a known, working laptop, right?

Yes. It runs XP sp2 with no problems.

---

### Post by necro1234 on 2007-07-10
Yes I am having a similar issue, I have an old PCLAPTOPS laptop, which is just a ASUS no name laptop (will post the model when I get home).
Ubuntu Edgy installed fine, but 7.04 will get to the screen with the bar that says it is loading the Kernel, once the bar hits the end it reboots and continues like this in a permanent loop.
I will see what BIOS settings I have and also try those command lines.

Hopefully those get it sorted, will let you all know.

Thanks

---

### Post by josuna on 2007-08-08
I had a very similar problem on a VAIO PCG-fx900 PIII system. I had to use the alternative CD to install Ubuntu since I could not run the live CD. Once it installed I got a black screen so I had to run Ubuntu in recovery mode and modify my xorg.conf in /etc/X11. I removed the higher resolution setting so that it would start with the next lower and that made it work.  

From:
 SubSection "Display"
                Depth   24
                Modes           "1280x1024"     "1024x768"      "800x600"       "640x480"
To:
 SubSection "Display"
                Depth   24
                Modes            "1024x768"      "800x600"       "640x480"

I am not too happy with my resolution but at least I got it to run. 

Try this and see if it works.

---

### Post by phaxda on 2007-09-25
I found this thread because I am mucking about with Kubuntu on a VAIO PCV-LX800, which is a slimline desktop. I'd had Kubuntu 4. something running on it, but made the fateful decision to try and upgrade to 7.04. I got the same blinking dash as the original poster and performed my Google search. The below advice got Kubuntu to load, however the bottom fourth of my screen is mirroring the top half. I don't know if this makes sense to anyone...I could take a picture if that would help. 

I set the memory to 4 MB as suggested at first. When I decreased it to 2MB, I got a similar mirroring, except that it was two smaller windows one on top of the other in the top and bottom left quadrant of my screen. 

I am just goofing around with this, but totally mystified. Any help is appreciated! 

Quick edit: changing these settings caused the display under Windows XP to be much crisper and nicer-looking! So thanks for that! 



> **jerrylamos said:**
> There are a couple things that work sometimes with older hardware.

First thing I would check is the Bios setting for the Intel graphics video controller.  There is usually a place for shared video memory which might be like 1024 K or 1 MB.  Set this as high as it will go, usually 4096 K or 4 MB.  That has gotten three computers running Ubuntu for me.

Cheers, Jerry

---

### Post by suchawato on 2007-09-27
**_UPDATE_**
This is now a CONFIRMED kernel bug with MEDIUM level importance assigned to the Ubuntu kernel team.
If you are interested in updates, you can go here:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/114682]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/114682")
This was confirmed several months ago now (its almost october 07 by this posting)
So expect that it will be fixed in Gutsy Gibbon.
If you cannot wait a week for some reason, then I would suggest trying the workaround posted in this thread regarding screen resolution and see if this works.
-Stu

---

### Post by suchawato on 2007-09-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/114682](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/114682) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/114682](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/114682) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Note:
Thread linked to bugfile.

---

### Post by suchawato on 2007-10-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/114682](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/114682) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Weeeell,
Its not fixed.
Not entirely.
7.10 installed using acpi=off in the safe grafics installation.
The live session loaded, but not withthe correct screen size.
It made a little "box" in the center of the display that was the "screen" while the rest of it was black.
it still displayed, though it did not resize the install windows, and hid the buttons on the bottom of the install menus so that I had to use keyboard navigation blindly in order to install it.
Upon reboot, the display was black, exactly like the 7.04 problem.
Using the grub menu to boot in safe settings, I could see the initial loading text, and then:
black! in flickered once or twice before this and then Black!
Well at least this is progress from the fiesty version of this bug!
-Stu

---

### Post by Agent86 on 2007-12-29
I have a Vaio PCG-953A aka PCG-FX150 laptop that would not boot Ubuntu/Xubuntu. It ran Windows ME fine, and Puppy Linux so-so (I couldn't get the Netgear WPN511 wireless card to work, but everything else was great).

I obtained a BIOS update from the Sony site [http://esupport.sony.com](http://esupport.sony.com) and I was able to finally get the Xubuntu 7.10 alternate disk to boot and install. Lo and behold, now the wireless card works in both Xubuntu and Puppy. I'm still having a video problem in Xubuntu (won't go above 800x600 and shows a black frame around the desktop) but that should be fixable - Puppy has no problem going to 1024x768.

The OP's PCG-954A is known as a PCG-FX140 on the Sony support site. There are BIOS updates from 2003 and 2002 on the website - I recommend the 2002 update as the one from 2003 looks like it's actually a version downgrade. I used the 2002 BIOS update on my Vaio.

---

