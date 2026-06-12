---
title: "dell latitude E6510 -- won't boot off CD"
date: 2010-09-26
forum: Hardware
---

### Post by Muster Mark on 2010-09-26
Hi all,

I have a brand new dell latitude E6510 and naturally want to get Ubuntu on here.  I try to boot up off the CD, but, after an initial purple screen, it just goes black and nothing happens (except a lot of whirring and such, but that quiets down after about a minute).

The machine has an nVidea nvs 3100M, which is the heart of the problem, I think (based on web searches).  All the help articles I have found assume that you have gotten further than a blank screen when booting off the CD.  Any ideas?

Thanks a million.

---

### Post by 0N3 on 2010-09-26
Did you run a disk check for errors? And what speed did you burn the ISO image @ typically burning ISO images you should burn them at lowest speed possible sounds like a disk error to me. Try reburning the image to a new disk at low speed. Also where did you download the image from.

---

### Post by 0N3 on 2010-09-26
[http://www.youtube.com/user/LinuxForDummies?feature=mhum](http://www.youtube.com/user/LinuxForDummies?feature=mhum)
This may also help two videos one on burning CD's other on making bootable USB

---

### Post by Muster Mark on 2010-09-27
Thanks for the suggestions, but the CD is bootable.  I can boot my mac mini from it, so the CD is fine.  Anything else I should try?

Again, many thank for any ideas.

---

### Post by powerslave12r on 2010-09-27
I was trying this exact same thing and on my exact same laptop with the same graphic card. I got it new a couple days ago and was having some youtube related trouble with the Nvidia 3100m.

So I thought I would boot up in the Ubuntu live cd and see what's going on. I ended up with exactly the same results as the OP.

Tried this multiple times, with multiple versions (10.04 and 9.04) to no avail. Both CDs have been tested and used multiple times in the past to successfully install ubuntu on various machines.

Could someone with any solutions look into this please?! Thanks a lot!

---

### Post by costantino.amato on 2010-10-07
Hi There,
I received my new E6510 yesterday and experienced the same issue which was solved buy pressing F6 in the Ubuntu 10.04 amd64 Installation/Try menu and select modeset and noacpi. It booted-off perfectly.
Cheers
C.

---

### Post by spohn on 2010-10-08
Hi Costantino,

Do you have the NVIDIA NVS 3100M running on 10.04?

Thanks,
Marcelo

---

### Post by Stang75 on 2010-10-08
I have a brand new Dell Latitude E6510 and I am having the exact same problem - nothing but a blank screen of frustration. 

There is nothing wrong with the CD I created. 

If anyone knows a fix please reply. I need to have Ubuntu on this laptop for my work.

---

### Post by Muster Mark on 2010-10-10
10.04 now working almost perfectly!  Basically all I needed to do was press shift-F6 just as it's starting off the CD (of maybe it just F6).  This brings up the installer menu, and I followed costantino.amato's instructions to select modeset and noacpi immediately after selecting language.  After that, installation was normal, however it wouldn't boot until I followed HardLuck's instructions here [http://ubuntuforums.org/showthread.php?t=1509957](http://ubuntuforums.org/showthread.php?t=1509957)

Now everything is working smoothly. I haven't upgraded yet to 10.10, so I have yet to see about that.

Thanks everyone!

---

### Post by dvandyck on 2010-10-11
I have the same problem but with the intel i915 integrated graphics card with Ubuntu 10.10. It is reported as
"Intel Corporation Core Processor Integrated Graphics Controller (rev 02)"

I assume it is a i915 chipset because I get the following error message during boot:
"intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled"

I tried several boot options without success. Using
nomodeset -> I can login in text mode, no X
i915.modeset=0 xforcevesa -> I get text on CTRL-ALT-F7 but no graphics and can switch to terminals using CTRL-ALT-F1 to F6 (I cannot do this if I boot normally)

It appears to be a known bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/600453](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/600453)

For the moment I give up the fight and will wait until the bug is fixed through an update or a straightforward step-by-step how-to is posted. 

Strangely enough, I could perform the install grapically by pressing F6 and using the "nomodeset" option provided by the installer. I do not understand why the installer can do its thing graphically but I cannot boot graphically even with the "nomodeset" option -- why is the working graphics configuration DURING installation not used AFTER installation? 

With Ubuntu 10.04.01 I could install graphically without problems, first  boot without problems but after installing updates every thing I did  yielded a black screen (including recovery-mode or using "text" as boot  option -- including the previous kernel). With 10.10 I can at least log in in text mode.

I have been away from Linux for 6 years (worked on Mac which I used as a Linux more or less) and it seems that the core problems are still the same: you need to be a hacker to get your hardware working *sigh* I was hoping that Linux passed that phase...

I would appreciate if someone would be so kind to post a link to a non-hacker-solution here if one appears somewhere. Until then I'll stick with Windows 7 :-/

---

### Post by nair on 2010-10-11
I tried installing Ubuntu 10.04 x64 on one of these machines last week.  I experienced all of the same problems everyone else has with the screen going black when booting from a LiveCD.  I got the onboard graphics, and then finally the graphics card, working by following the methods posted in this thread:

[http://ubuntuforums.org/showthread.php?t=1509957&page=2](http://ubuntuforums.org/showthread.php?t=1509957&page=2)

This method ultimately requires a proprietary nVidia graphics driver for getting the graphics card to work.  Once that is setup correctly, following the steps in the thread, Ubuntu will function normally.  Grub will function normally.

The one single difference you will notice, or that I have noticed so far, is the loading screen for the OS (which says "Ubuntu" and has the five little orange and white dots that change colors) will be displayed using the onboard graphics, and not the graphics card which uses the nVidia graphics driver.  As a result, the resolution will be off and the loading screen will look like crap.

---

### Post by dvandyck on 2010-10-12
> **nair said:**
> 

This method ultimately requires a proprietary nVidia graphics driver for getting the graphics card to work.
 

This thread is all about the same laptop model but with different options: mine does not have an nVidia card, only an Intel integrated graphics Controller with i915 chipset. 

Good for you guys having an nVidia card that there is a solution. Should we start a different thread for the i915-problem?

---

### Post by dvandyck on 2010-10-14
Apparantely, there is a temporary solution for us guys having the integrated intel controller (i915)  by patching a vanilla 2.6.36-rc6 kernel with:
 [https://bugs.freedesktop.org/attachment.cgi?id=38868](https://bugs.freedesktop.org/attachment.cgi?id=38868)

I did not check it out -- I have no experience in kernel patches

Source:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/600453](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/600453)

---

### Post by Alfe on 2011-01-20
Running Ubuntu 10.10 with the current kernel 2.6.35-24 on a Dell 6510 with intel graphics 1920x1080 ... having the same problems as described above:  The computer boots and then goes dark.  Besides the dark screen, most things (sound, disk-access, computing, network, etc.) work fine.

I have a kind-of-solution which is not perfect but applicable for me:
- Attach an external screen (1600x1200) via display port (using an adapter to DVI).
- Boot the computer.
  => The attached screen shows what should be shown on the built-in screen.
- Wait for the login screen to appear on the external screen.
- Attach the external screen *also* via VGA.
  => :D The *built-in* screen suddenly turns okay (shows what it should) and stays that way until the screen settings are changed again (e. g. by games).

After this you can work normally with a dual-screen setup.  You also can disconnect the VGA again.  Connecting or disconnecting it seems to trigger something which turns on the built-in screen.

:( Main disadvantage: You can only work with an additional screen at hand.

Additional problems I've got:
- Display looks like it's in 16bit-mode (but 'wish' and 'winfo depth .' shows 24).
- Some applications (mostly graphics-related) break the situation up to hanging up the computer completely.
- Neither hibernate nor sleep mode works properly.
- Touch pad is only supported as simple mouse (I cannot disable the touch-click or use any of the special functions like scrolling).

I'm now gonna try to install an up-stream kernel.  Any information on this procedure is welcome.

Alfe

---

