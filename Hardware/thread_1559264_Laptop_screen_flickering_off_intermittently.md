---
title: "Laptop screen flickering off intermittently"
date: 2010-08-23
forum: Hardware
---

### Post by hmarr on 2010-08-23
Hi,

I've installed Ubuntu 10.04 on a new Dell Latitude E4310 - everything works fine except the laptop screen. It intermittently appears to switch off for a split second (not entirely sure if it's just the backlight or not...)

I saw a post about a similar issue ([http://ubuntuforums.org/showthread.php?t=1505712](http://ubuntuforums.org/showthread.php?t=1505712)) that suggested installing the new drm-intel kernel, but that has not solved the problem. I'm running out of ideas so I'd hugely appreciate some input!

```

~$ glxinfo | grep -i direct
direct rendering: Yes
~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

```

Let me know if any other info would help.

Many thanks in advance

EDIT: I forgot to mention, if I plug in an external monitor, it is only the laptop monitor that flashes. This behaviour does not seem to occur under Windows.
EDIT2: Tried the powersave=0 fix that seems to work for similar problems, doesn't seem to have helped...

---

### Post by lpchouinard on 2010-09-04
I have the exact same problem, but it's a new issue. It's either the upgrade to the A04 bios or some updates because Ive been running the same install for 3 months now and it just start happening.

hmarr could you tell what version of the bios are you using, also here's a glipse of my Xorg log file

(II) intel(0): EDID vendor "LGD", prod id 589
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   75.50  1366 1414 1446 1581  768 771 777 793 +hsync -vsync (47.8 kHz)
(II) intel(0): Modeline "1366x768"x0.0   50.30  1366 1414 1446 1576  768 771 777 793 +hsync -vsync (31.9 kHz)
(II) PM Event received: Capability Changed
I830PMEvent: Capability change
(II) intel(0): EDID vendor "LGD", prod id 589
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   75.50  1366 1414 1446 1581  768 771 777 793 +hsync -vsync (47.8 kHz)
(II) intel(0): Modeline "1366x768"x0.0   50.30  1366 1414 1446 1576  768 771 777 793 +hsync -vsync (31.9 kHz)
(II) intel(0): EDID vendor "LGD", prod id 589
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   75.50  1366 1414 1446 1581  768 771 777 793 +hsync -vsync (47.8 kHz)
(II) intel(0): Modeline "1366x768"x0.0   50.30  1366 1414 1446 1576  768 771 777 793 +hsync -vsync (31.9 kHz)
(II) PM Event received: Capability Changed
I830PMEvent: Capability change
(II) intel(0): EDID vendor "LGD", prod id 589
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   75.50  1366 1414 1446 1581  768 771 777 793 +hsync -vsync (47.8 kHz)
(II) intel(0): Modeline "1366x768"x0.0   50.30  1366 1414 1446 1576  768 771 777 793 +hsync -vsync (31.9 kHz)

EDIT: The flickering doesn't happen if i use the dock staion and an external monitor(DVI)

---

### Post by hmarr on 2010-09-07
I'm using the A03 BIOS. Still haven't found a fix for it.

Got in touch with Dell about the issue - spent over 6 hours on the phone to various customer support people and was finally told by the last person that as the laptop was bought through a business they have no interest in the issue (or any other issues I ever encounter).

Have you made any progress?

---

### Post by AlexZaim on 2010-09-07
there is a ppa called [best-intel]("https://launchpad.net/~guido-iodice/+archive/best-intel")
Add it. Install la latest kernel from it and upgrade the drivers (or just do the update). It may fix something... These are thelatest developements of gpu drivers and kernels. Post back results.

---

### Post by hmarr on 2010-09-07
Is there a way of getting that PPA working on Maverick? I'm trying 10.10 beta now in the hope that it'll fixed sooner here than Lucid.

Cheers

---

### Post by hmarr on 2010-09-07
Also, I'm not sure if this is X-related - I tried Arch briefly and encountered the problem even before I started X.

Cheers,
Harry

---

### Post by AlexZaim on 2010-09-08
yes, it should work with 10.10. But 10.10 has a quite good kernel... i'm surprized it didn't worked. You can still try the ppa though.
Add this line to your repositiories
deb [http://ppa.launchpad.net/guido-iodice/best-intel/ubuntu](http://ppa.launchpad.net/guido-iodice/best-intel/ubuntu) lucid main

In case you don't know, search the net on how to do that.

then do an update.

---

### Post by mijnomrah on 2010-09-08
I was having the exact same problem and with my latitude E4310. I upgraded to the A04 bios and so far  (less than a day) the problem seems to be fixed. Upgrading the bios without windows turned out to be much more of a pain than I expected, i ended up reinstalling windows just to upgrade the bios.

---

### Post by hmarr on 2010-09-09
Trying the new kernel and BIOS now - seems slightly better so far but I'm pretty sure I've still seen it flicker a couple of times...

mijnomrah: How's the new BIOS going for you?

---

### Post by scottuss on 2010-09-09
You are absolutely sure the problem doesn't occur outside of an OS (BIOS) or in Windows?

---

### Post by hmarr on 2010-09-09
Pretty sure - I've tried Windows for as long as I could bare and didn't notice any flickering. The new BIOS seems to have helped a bit - the flickering seems to start when I play around with external monitors - this can also freeze the laptop.

Edit: the flickering has definitely reappeared - regardless of whether an external monitor is present..

---

### Post by mijnomrah on 2010-09-09
Ok, still having the flicker with the 0A4 bios.  I also upgraded the kernel  to 2.6.35 to solve the problem of the screen staying black when you shut/open the laptop which did fix that problem.  The flickering doesn't seem as bad but it's still pretty annoying. 

I have not seen the screen flicker outside of linux, both windows and the bois screen seem fine.

---

### Post by Laborifer on 2010-09-15
Hi,

I have the same problem that you describe on this thread when i'm running on latitude E4310 an Ubuntu 10.04 with 2.6.32.24 kernel the laptop screen flickering off intermittently.

but when i use 2.6.32.21 or 2.6.32 22 kernel, i don't have any problem...

Cheers

---

### Post by AlexZaim on 2010-09-16
try going to 
```
sudo gedit /etc/default/grub
```
 and edit this line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
into this
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_backlight=vendor"
```
save it and reboot.

If the above will not work i just want to say that:
this bug is being worked on , [acording to launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/543045")'s bug tracker.

---

### Post by the big e on 2010-09-16
I have a similar problem. Thinkpad T500 dual boot ubuntu/vista. I get one flicker every several minutes or so in Ubuntu but not when I am running Windows.

---

### Post by mijnomrah on 2010-09-17
> **AlexZaim said:**
> try going to 
```
sudo gedit /etc/default/grub
``` and edit this line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```into this
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_backlight=vendor"
```save it and reboot.

If the above will not work i just want to say that:
this bug is being worked on , [acording to launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/543045")'s bug tracker.

I will try this and report back. None of the other fixes have worked for me so here's hoping.

---

### Post by AlexZaim on 2010-09-18
> **mijnomrah said:**
> I will try this and report back. None of the other fixes have worked for me so here's hoping.

OH! I forgot to add 1 more line at the end

```
sudo update-grub
```

execute it after you save the changes to the file. Then reboot.

---

### Post by hmarr on 2010-09-19
I'll give this a go tomorrow when I'm back in the office and report back.

Cheers

---

### Post by mijnomrah on 2010-09-20
> **mijnomrah said:**
> I will try this and report back. None of the other fixes have worked for me so here's hoping.

Appears to cause major problems, the the ubuntu splash screen gets garbled and then freezes. This is with kernel 2.6.32-24.

---

### Post by AlexZaim on 2010-09-21
ok. you can change the line back to it's default and do update-grub.
Let's hope that in the final 10.10 this will be fixed.

---

### Post by mijnomrah on 2010-09-27
Just thought I'd give an update. I still have the flicker with ubuntu 10.10. I also tried Fedora 13 and OpenSuse and have the exact same problem.

---

### Post by mijnomrah on 2010-09-28
> **Laborifer said:**
> Hi,

I have the same problem that you describe on this thread when i'm running on latitude E4310 an Ubuntu 10.04 with 2.6.32.24 kernel the laptop screen flickering off intermittently.

but when i use 2.6.32.21 or 2.6.32 22 kernel, i don't have any problem...

Cheers

I have confirmed this too, both kernels 2.6.32.21 and 2.6.32.22 do not have the flickering issue. Both kernels will not wake from suspend either.

---

### Post by AlexZaim on 2010-09-30
> **mijnomrah said:**
> I have confirmed this too, both kernels 2.6.32.21 and 2.6.32.22 do not have the flickering issue. Both kernels will not wake from suspend either.

i've sent a bug report to kernel.org, but have no answers from them yet.

---

### Post by alexM11 on 2010-10-04
I guess I have the same problem with a DELL Latitude E4310 laptop. The screen is fine with windows7 but with ubuntu 10.04 I have this screen flickering. Note that with an external screen I don't have the problem.

Did you sort out this issue ?

---

### Post by solofs on 2010-10-14
I have a DELL E4310 and I have found a work-around for this problem on ubuntu 10.10 (kernel 2.6.35-22-generic): I simply set the computer to standby mode and then wake it up. 

After boot the flickering is unbearable (at least for me) but after having made a cycle of standby - wake up there are no more any flickers! 

The computer is really nice running ubuntu 10.10, however there are still some problems remaining:

- If the screen is switched off by the power management the flickers restarts when it's turned on again.

- If I let the computer sleep for a longer time (>1 h) I cannot wake it up again.

- The touch pad still can't be configured... :(

I hope this helps!

Olof

---

### Post by xycmu on 2010-10-19
> **solofs said:**
> I simply set the computer to standby mode and then wake it up. 

After boot the flickering is unbearable (at least for me) but after having made a cycle of standby - wake up there are no more any flickers! 

The computer is really nice running ubuntu 10.10, however there are still some problems remaining:

- If the screen is switched off by the power management the flickers restarts when it's turned on again.


I tried this and it worked for me as well. At least I can use the OS now using this work-around without having a seizure.

I also confirmed that after powering off the display via power management that the flickering resumes.

Note to all those who have asked: I never saw this happen within Windows or outside of the X11 server.

---

### Post by Fischmuetze on 2010-10-26
Have the same problem since 10.04 kernel >22 and also in 10.10 ... 

<22 no sound
>22 no stable screen
aaaaaaaaaaaarghhh

The screen flickers always... we have a lot of this Computers on our institute and are not able to supply it to the users... What painful .. 
The screen flickers always... we have a lot of this Computers on our institute and are not able to supply it to the users... That's absolutely  angrily .. Never had before such problems...

---

### Post by mpbio01 on 2010-11-22
I've got the same issue with E4310 running Ubuntu 64 bit 10.10

---

### Post by learst on 2010-12-02
Hi,

I posted this in another similar thread, but thought I'd post here too:

I'm using a Dell Inspiron 1420 with nVidia GS8400 M. 

Short history, I have been using Windows  Vista Then once  there was a problem where there was no display even though the monitor  was lighted. This was April 2010 , and I was given a new motherboard  

After that I did a clean format to use a dual-boot Windows/ Ubuntu  10.04. And I noticed the flickering started in Ubuntu. It was very brief  and rare, but then it got more frequent. The flickering also occured  when I use Windows. I contacted Dell technical support, and they thought  it was a motherboard problem so I was given a new motherboard again (3  weeks ago). 

With this new motherboard, I did a clean reinstall of Windows and Ubuntu  10.04. After a few days, the flickering started again and I can't get  it to stop. Since some posters suggested updating to Ubuntu 10.10, I  formatted my drive to reinstall Win/Ubuntu. I noticed the flickering  persisted throughout the installation of Windows and Ubuntu, and even  while starting up. I really doubt this is a hardware problem with the  motherboard as I've just got a new one. 

Right now the flickering occurs every randomly around every 10 seconds, while booting up, running Windows and Ubuntu 10.10. I have no idea how to solve this, other than call Dell technical support again. They'll probably give me a weird look as if this will be the third time I'm changing my motherboard this year!

---

### Post by xycmu on 2010-12-02
> **learst said:**
> The flickering also occured when I use Windows.

I'm quite certain that your particular issue is not related to the issue described above.  The issue that had been described only affects Linux, not Windows at all.

It sounds like the issue that you describe is hardware related. Perhaps your video controller is not part of your motherboard and are therefore not actually replacing a potentially defective part.  Perhaps try replacing the actual video controller, not just the motherboard - and secondly perhaps your LCD backlight is defective?

Either way, your issue is different and not something that pertains to Ubuntu or even Linux.

---

### Post by learst on 2010-12-03
Hi,

Just an update on something I found recently which said that my  flickering screen could be due to hardware problem (Dell 1420 with  nVidia) rather than anything to do with Ubuntu at all.

[http://en.community.dell.com/dell-blogs/Direct2Dell/b/direct2dell/archive/2008/08/08/latest-on-the-nvidia-gpu-issue-for-dell-laptop-customers.aspx](http://en.community.dell.com/dell-blogs/Direct2Dell/b/direct2dell/archive/2008/08/08/latest-on-the-nvidia-gpu-issue-for-dell-laptop-customers.aspx)

---

### Post by xycmu on 2010-12-03
> **learst said:**
> my flickering screen could be due to hardware problem (Dell 1420 with  nVidia)

Quite possibly, but the issue in this thread specifically deals with the Intel HD integrated video controller, not nVidia.  Your issue is something else entirely.  I would tell you to create a new thread with your specific issue, but it's not appropriate for this Ubuntu forum.

```
~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
```

---

### Post by AlexZaim on 2010-12-04
Guys, i have a toshiba t135 and the problems that i encounter are:
1. Can't change screen brightness. (in 10.04 i had a workaround, doesn't work anymore in 10.10)
2. I get the flickering in games, but not on desktop.

I just wanted to share that with you.

---

### Post by Bartzy on 2010-12-10
Just to let you know that on Debian Squeeze, Kernel 2.6.36-trunk-amd64, 64-bit.

It's SO annoying.. do you think it's Intel Drivers problem?

---

### Post by xycmu on 2011-01-21
I found this similar thread over at RedHat:
[https://bugzilla.redhat.com/show_bug.cgi?id=580276](https://bugzilla.redhat.com/show_bug.cgi?id=580276)

Seems to describe the same issue

---

### Post by Dean_A on 2011-01-26
Hi All,

One thing I have realized is that if you boot into kernal 2.6.32-21 you don't have any screen issues, or touchpad issues.  When I tried kernal 2.6.35-24 I had sceen issues and touchpad issues.  Quick solution is to install "startupmanager" and select the right kernal to load on startup.

I am still having audio issues though.

---

### Post by Dean_A on 2011-01-28
Another update, adjusting the settings on the boot screen works to a point.  I cannot get the VGA out enabled.  When I look at the refresh rate setting for the laptop display it is set to "0" instead of "60".  Without the boot script tampered with I can get VGA working and it seems like monitor settings are all as they should be, but the laptop screen still blacks out.  I have a conference coming up where I will require dual screens.  If anyone else has some suggestions I would appreciate it.

---

### Post by trondhuso on 2011-10-25
What you have to do to stop the flickering is to upgrade to any kernel above 2.6.36. I got in touch with some kernel guy on irc and he told me to get the 2.6.38-kernel, so I downloaded it and it works.

I fixed this a while back so I cannot remember where and how to do it, just to tell that get away from any 2.6.36 or which ever 10.04 comes with.
Or just upgrade to one of the later ubuntu distros that has any of the newer kernels.

I wanted to stick with the lts and so I did. alas they have not fixed the flickering in the kernel series that the lts is running... it seems...

---

### Post by amira-kitten on 2011-10-26
Firstly, thanks for posting this. I had flickering problems on 11.04 and they got worse when I upgraded to 11.10 (therefore I'm a little confused about the whole thing about it working if you upgrade to a certain kernel because it didn't for me.)
Needless to say solving one problem has caused another. Changing grub has fixed my very irritating flickering issue but has now completely messed up the screen resolution in KDE and there are no options in the monitor/display setting to change res. I am going to look into sorting that later but I thought I'd pass it on in case it was of interest to anyone else. I have a screenshot if anyone wants to see but basically its set itself to 800x600 and now looks horrible.

---

