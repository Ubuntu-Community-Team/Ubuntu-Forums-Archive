---
title: "Ubuntu Live Cd Problems!!"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by peter_q on 2009-03-19
Hokay. So I Got the live disc. And I wanted to run it from the cd to see if the drivers worked. So i restarted my computer and my bios wasn't set to boot from cd. So I decided I really didn't feel like messing with my bios (Cause I was lazy and didn't wanna change it back) so I clicked on the option of "Help me to Boot from CD" and it installed this stuff.

So when I installed this and rebooted I have the option to boot vista or ubuntu. But after I take the Cd out I have that option every time! So I decide to get rid of it so I notice under programs and stuff in the control panel there's an ubuntu one and I delete it. Now it still happens, except the ubuntu wont boot even with the cd in!

So today I tried to reinstall that program that lets me boot it and it didn't properly install. :( So now I find it in the folders and see uninstall icon. Click it. And it runs but nothing changes. So I think "Maybe restarting will remove these files." And so I do.

Now whenever I start my laptop, I have to select between Vista and Ubuntu and Ubuntu. And neither Ubuntu choices work. Help!

---

### Post by pytheas22 on 2009-03-19
It sounds like you installed Ubuntu via [wubi]("http://wubi-installer.org/"), but you wanted to install it to a dedicated partition (which is the traditional approach--wubi is more convenient because it doesn't require partitioning, but it has some drawbacks).

If you want to do a traditional installation of Ubuntu, you should boot to the Ubuntu CD and run the installer.  On most computers, you should be able to pull up a one-time boot menu right after you turn the machine on to select which boot device to use--this doesn't require you to modify BIOS itself.  To get the boot menu, try pressing the delete of F8 keys right after you turn on the computer.  If they don't work, look at the screen (you can press the pause/break button to pause it) to see which key you need to press.

After you've installed Ubuntu to a dedicated partition, you can remove the two failed wubi systems using Add/Remove Programs in Windows.

---

### Post by peter_q on 2009-03-20
Wubi? Cool...

Well I checked my Programs list in Vista. There was one ubuntu one but no Wubi one. I deleted that... and then I even deleted the whole ubuntu folder in C.


And restarted...

And it still does it.

---

### Post by pytheas22 on 2009-03-20
I guess the wubi uninstaller doesn't clean up as well as it should.  You should be able to remove the Ubuntu boot entries manually if you edit the Windows boot menu, however.  I'm not sure how to do that in Vista, but I'm sure you can figure it out with a few seconds' googling.

---

