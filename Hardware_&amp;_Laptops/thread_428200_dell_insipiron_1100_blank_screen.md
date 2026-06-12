---
title: "dell insipiron 1100 blank screen"
date: 2007-04-30
forum: Hardware &amp; Laptops
---

### Post by marknewlyn on 2007-04-30
Hi All

I just installed 7.04 on my Dell Inspiron 1100 (bios upgraded to A32) from CD and when it boots I just get a completely blank screen and nothing responds - I think it boots, not text at all comes up the entire boot process has a blank screen but the hard drive seems to do a lot.

Am I competely alone on this? Not sure whats up - maybe its an X thing but the CD shows up at least.

Please help!

Mark

---

### Post by wilberfan on 2007-07-14
> **marknewlyn said:**
> Hi All

I just installed 7.04 on my Dell Inspiron 1100 (bios upgraded to A32) from CD and when it boots I just get a completely blank screen and nothing responds - I think it boots, not text at all comes up the entire boot process has a blank screen but the hard drive seems to do a lot.

Am I competely alone on this? Not sure whats up - maybe its an X thing but the CD shows up at least.

Please help!

Mark

I'm having this exact problem.   I CAN get X to start--IF I change the driver from i810 to "vesa", and leave the default depth to 16.  

Anything else does NOT work...   :confused:

**[edit]  Well, I've solved my problem!   Turns out I had to install the "915resolution" modification tool (from Synaptic).    After following the directions in the readme, everything worked fine!**

---

### Post by dougleduck on 2007-07-23
I think I have the same problem. Ubuntu boots up; I know as I here the login screen sound. But the screen is blank. This is only occasional for me though. 1/10 of the time.

---

### Post by moire76 on 2007-07-30
Hi there!
I am a brand new Ubuntu user from Hungary! So far I used debian on my dell inspiron.

The same problem ocured for me I think. I also have Inspiron 1100 with i810 driver and used Ubuntu 7.04 Live CD for installation. I have 640MB ram (512+128 )

I got the blank screen after "Starting up..." and hard drive is working for a while, as it were do its job.
But after a while, it stops working. I can only hard reset the machine.
The only way to boot normally to x, if I select the recovery mode at grub list, and after boot, I  type a "startx".
It works perfectly then.  Because of this, I think that my xorg.conf is correct.

But why can't I boot normally? What's wrong?

I can try this 915recovery, but it is about to be able to use "unusual" resolutions, which makes no sense for me I guess, because my resolution is OK (after working on a lot to stop using 640x480:))

Please help:confused:

---

### Post by moire76 on 2007-07-30
I'm sorry, I have now recognized that cddot already wrote my solution earlier here: [http://ubuntuforums.org/showthread.php?t=488235](http://ubuntuforums.org/showthread.php?t=488235)
SO it seems it's not new anymore, but anyway, I leave it here:

Hi there!
Working around for a while brought me up a solution.
Despite that I still not understand the problem itself, I have found a possible solution to my blank screen problem described above.

Here is what I did:

Since I noticed that I can smoothly start x if I choose recovery mode at GRUB menu, I have changed the grub config file at /boot/grub/menu.lst

From the first menu point I have removed the quiet and splash properties, so the original menuitem is  changed like this (removed the red text):

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=5469bbdf-88f7-44be-a2ea-1e009bb5e4cc [COLOR="Red"]quiet splash[/COLOR] ro
initrd          /boot/initrd.img-2.6.20-16-generic [COLOR="Red"]quiet[/COLOR]
savedefault

after this let it reboot

it will continue to write out the system messages until it starts up the login window.

This method still doesn;t bring up the framebuffer driver, so you still won't have the nice splash screen during the boot, but it will work.
And at least you can see the system booting up which can be useful if you experience problems later...

I hope that it helps others as well!!

br,
Moire

---

### Post by nickware on 2007-08-05
To fix this problem:
1. When you start your computer, hit F2 to enter Setup.
2. Alt-P (Turn the page) until you get to the page with the video memory.
3. Change the video memory from 1MB to 8MB
4. Reboot

Enjoy your working Ubuntu laptop!

Note: Your resolution will still be 640x480 until you apply the fix of changing the Monitor section of your /etc/X11/xorg.conf to:

[FONT="Courier New"]Section "Monitor"
        Identifier      "Generic Monitor"
        ModelName       "Dell 1024x768 Laptop Display Panel"
        HorizSync       31.5 - 48.5
        VertRefresh     59.0 - 75.0
        Option          "DPMS"
EndSection[/FONT]

(See [https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell) for more info)

Hope this helps!

Nickware

---

