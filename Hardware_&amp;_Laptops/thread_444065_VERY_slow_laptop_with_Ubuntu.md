---
title: "VERY slow laptop with Ubuntu?"
date: 2007-05-15
forum: Hardware &amp; Laptops
---

### Post by elfstone214 on 2007-05-15
Hi all,

I just set up Ubuntu (Feisty) on my Dell Inspiron 9300 and I am having big time CPU slow downs when I do anything. Even opening firefox will make my CPU spike to 100%. This doesn't make sense to me, even my old bloated version of Windows XP ran a lot smoother. Does anyone have any explanation for this?

See my CPU use in this picture for just opening firefox twice. I am not even using beryl yet.

[ATTACH]32627[/ATTACH]

and here is my boot-up-manager, as you can see nothing much is running
[ATTACH]32630[/ATTACH]


My specs are:
CPU - Pentium M 1.86GHz (L1 Cache 32KB+32KB, L2 Cache 2MB)
RAM - 1GB
Video: ATI Mobility X300

---

### Post by girishv on 2007-05-15
Hi,

it may not be a daemon which is consuming all the power. Can you please cut n'paste the result of running
top
This will help in finding which process is actually hogging all the resources. 

Girish

---

### Post by elfstone214 on 2007-05-15
This is a screenshot right after I opened firefox.
[ATTACH]32639[/ATTACH]

Here it is. There is actually nothing sucking up power when on idle but as soon as I click anything even firefox, the cpu load goes through the roof.

---

### Post by atze76 on 2007-05-15
I think I've got the same problem. Ubuntu 6.06 was running smooth on my laptop but after installing 7.04, I 	continuously have more then 50% cpu load just by running firefox and thunderbird.

I am curious whether it is because of the new Xorg (7.2) version.

---

### Post by elfstone214 on 2007-05-15
I am convinced it is a video problem. I don't think my ATI X300 video drivers are correctly installed although I followed these instructions:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

This is what "fglrxinfo" returns:

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

There is nothing there regarding the X300. This is really frustrating because everything else works like a charm, even my wireless worked straight up.

---

### Post by saveryquinn on 2007-05-20
I'm having a very similar problem with Feisty on my Dell Inspiron 6400.  The system spikes the duo core cpu usage up to 100% opening any application.  Running any applciation *and* opening OpenOffice.org is hopeless.  

I had thought this might be due to Automatix and so I did a fresh install, this time not taking the broad and popular route that leads to... umm... perdition?  Easily installed codecs?  Anyway, even without the Automatix goodness and Beryl candy, the processor still spikes to 100%.  I did not have this problem with any previous edition of Ubuntu.  And I'm considering reverting to Edgy.

I am currently triple booting Ubuntu, Windows XP, and SuSe.  While Windows runs the CPU around 45% to 80% at times, it is nothing compared to the Ubuntu slow-down.  SuSe 10.2 runs effortlessly.

Humph.  Maybe all those new Dell users getting stuck with this problem will file enough bug reports for it to be fixed by the next edition... meanwhile they can stare at their non-functioning Ubuntu laptops and twiddle thumbs instead of getting real work done.

---

### Post by atze76 on 2007-05-21
I am convinced that this problem is not Dell specific. I have an Asus laptop and suffering high CPU load with 7.04. I followed various threads, but a lot of people with different hardware have similar problems. It's hard to tell whether it's the 2.6.20-15 kernel, the new Xorg 7.2, the new harddriver module or something else. But the ubuntu developers definitively messed something up.

---

### Post by sebdel on 2007-05-22
Same thing here on a VAIO FS285H. It was running smoothly with previous ubuntu or SLED 10, 
and now in feisty everything is slow :(

EDIT: FIXED ! It works for me with the -386 linux image and CPU frequency stepping is back.
Don't worry, it's parallel installable with the generic kernel. And don't forget the modules as well (nvidia...) or you will loose X ;)

---

### Post by atze76 on 2007-05-22
installing the -386 kernel solved my performance problems as well. thanks

---

### Post by tsumi on 2007-05-23
is there a howto on this? location of the kernel? i am having the same issue on an optiplex 170L

---

### Post by atze76 on 2007-05-23
just select the "linux-386" package with adept (the package manager). It will then automatically select all the necessary packages to have a complete 386 kernel running. After installing the packages and rebooting your system, the 386 kernel should appear in your boot menu.

---

### Post by elfstone214 on 2007-05-27
> **atze76 said:**
> just select the "linux-386" package with adept (the package manager). It will then automatically select all the necessary packages to have a complete 386 kernel running. After installing the packages and rebooting your system, the 386 kernel should appear in your boot menu.

thanks atze76, I tried that but it still running somewhat slow. It is not to the point where it is unusable but ubuntu seems to hog more cpu resources than a bloated Windows XP which just seems very wrong to me.

---

### Post by jerrylamos on 2007-05-27
Well, this is a partly upgraded Gutsy 7.10 so it might not be the best to tell what your systems are seeing, however to change kernels using Ubuntu:

System, Admininstration, Synaptic
Search on linux-image

A couple choices I see:

linux-image-2.6.20-15-i386
linux-image-2.6.20-15-generic

In my case there are some images like 2.6.22-5 which are for Gutsy, not for Feisty.

Right click to Mark what you want to try for Upgrade, then Apply, 

Then do 
ls /boot
You should see vmlunuz-2.6.20-15 generic or i386 or both plus other necessary files.

Look in /boot/grub/menu.lst (where l is lower case L) and look for the first line that says kernel.  That's the one that Grub bootloader will try to use.

Safest way is to use a browser
less /boot/grub/menu.lst
Quit less by entering
q

If you pay attention you can change that to whichever one you want, or even have two choices to pick from when you boot.  You might want to make a backup, like 
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.back
it will ask you for your password

then do
sudo gedit /boot/grub/menu.lst
carefully make any changes you want to try.  Could well be O.K. as is.  If menu.lst gets screwed up, boot might fail, then you bring up Ubuntu CD Live to do the sudo cp in reverse.

then reboot and see what happens....to see what you're actually running, do
uname -a

Cheers, Jerry

---

### Post by Macchi on 2007-06-09
Unfortunately I've also detected a similar problem of a slow Feisty on a Vaio VGN-FS195VP.  The same laptop worked OK with edgy. Now I have switched to the 386 kernel as a _workaround_ and the performance seems to be normal again.


O moment of reflection:
Hope that a _solution_ will be available for the generic kernel line. It is frustrating to find so many new issues and regression problems with new kernel releases and distro packages. We are trying to help business enterprises to switch to Linux and no one wants to see a high frequency of these problems. I will be more conservative with upgrade decisions.

---

### Post by hardyn on 2007-06-09
the i386 kernel solves this problem with P-M based notebooks... Sony and Asus are the most common needing this fix.

the kernel is avalable though synaptic, search for the kernel-386 meta package, but do not forget the headers as well.

cheers.

---

