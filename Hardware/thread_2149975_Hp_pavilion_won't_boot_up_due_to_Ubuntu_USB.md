---
title: "Hp pavilion won't boot up due to Ubuntu USB"
date: 2013-05-30
forum: Hardware
---

### Post by So13eit on 2013-05-30
Hi all,


This is my first post on this forum, so my apologies If its in the wrong place or incorrect format.


Just yesterday I got Ubuntu 12.04 running on an adata 16gb USB 3.0 for the first time and ran it, booting it from startup. Today I tried it on another laptop, a hp pavilion that uses windows 7. I ran Ubuntu successfully, but when I restarted it, I unplugged the flag drive before it finished restarting- i saw a bunch of error line fly al, all starting with "unable to..."
Now the laptop won't even boot up. I can shut it down by holding down the power button and turn it back on, but all it ever shows is a black screen, no booting up.


Does anyone hve any experience with this kind of problem? Any help is greatly appreciated!

---

### Post by sudodus on 2013-05-30
Welcome to the Ubuntu Forums :-)

- Can you boot the computer without the USB pendrive inserted?

In that case you damaged the file system on the USB drive by pulling it out before it had finished writing during shutdown. At least this is what I guess.

- Or is it impossible to boot the computer also without the USB pendrive? Then you must describe in detail, what you did, when you were running from the USB pendrive (before you shut it down)?

. was the internal drive mounted?
. did you try to install something?
. did you edit any partition?
. did you write anything to the internal drive?
...

---

### Post by So13eit on 2013-05-30
Hi, thanks for the reply.

i would guess that the first is the case. Nothing will boot up, with or without te flash drive.
As for what I did on Ubuntu, I didn't do anything at all. I logged on, saw that I didn't have wifi, and then instantly restarted te laptop to use the windows installed on it

---

### Post by sudodus on 2013-05-31
Is this correct?

1. You have an Ubuntu ***desktop*** iso file, and you have used it to make a bootable USB pendrive.

2. The first day you ran it successfully in one computer.

3. The next day you tried it on another laptop, a hp pavilion that uses windows 7. Ubuntu booted like it should and you had a graphical desktop. You might have unplugged the pendrive too early.

4. After that no operating system works on the computer.

Or

- Have you got an Ubuntu ***server*** iso file, made a bootable USB pendrive and installed Ubuntu ... ?

-o-

- Did you change the boot order in the BIOS menu system?

- What kind of BIOS system is it (standard or UEFI)?

- Was Windows 7 working like it should before you tried Ubuntu?

I can understand that Windows will not boot if you changed something in BIOS or UEFI. Then try to remember what you changed and reset it.

If you installed Ubuntu Server, Windows should be available via the grub menu, but that might fail, and you need to repair it.

But if you only ran a live session of Ubuntu, Windows should not be touched at all (unless you did it deliberately). And this is what I think happened, so I am very puzzled. [COLOR=#ff0000]I think we need help from other people at the Ubuntu Forums to understand the problem.[/COLOR]

---

### Post by Yellow Pasque on 2013-05-31
The HP support site has good instructions on doing a BIOS/hardware reset. Generally, you unplug everything, take out the battery and hold the power button for 15-20 seconds. I'd highly recommend looking at the HP support site for your specific model though.

---

### Post by So13eit on 2013-05-31
@Sudodus: It is exactly the first scenario... a desktop i384 .iso image. I unplugged it early and now it's not working. I did not change any settings, nor did I even open up any settings menu.

@Temujun: Thank you for giving me some phrases to work with. I've spend the past hour though, trying all the advice I could find on the internet about rebooting the BIOS (taking out battery, pressing button combinations, unplugging everything, even attempting to remove the CMOS battery), but no luck at all. I guess this forum isn't the right place to ask, I will try the hp forums some more.

Thanks to both of you for your replies!

---

### Post by sudodus on 2013-05-31
1. Did you change anything in BIOS or UEFI? (I can understand that Windows will not boot if you changed something in  BIOS or UEFI. Then try to remember what you changed and reset it.)

- If you did not change anything, you should not need any resetting.


2. Was Windows 7 working like it should before you tried Ubuntu?

---

### Post by So13eit on 2013-05-31
Windows was working fine. I literally logged on, opened firefox, found that the internet didn't open. Opened the wireless button on the top right to not see any connections I could connect to. Then I restarted the laptop and pulled out the flash drive. Believe me, if I did tinker around with system settings, I would have remembered it... not like I even know how to do such a thing on Ubuntu yet.

After more research and calling up customer support as well, I found out that the *motherboard was damaged*. I have no idea how this could have happened... or why it was so extreme. Is using a Ubuntu USB that dangerous?? If so, I better be careful about how and where I use my Ubuntu USB...

---

### Post by sudodus on 2013-05-31
I have never experienced anything like this before. And I have done a lot with many different linux and other operating system 'distros'. Once I bricked an old graphics card with DSL, and once I bricked a USB to IDE and SATA adapter connected to a system in Virtualbox, but that was years ago, and I was doing much more risky things compared to what you were doing. Ubuntu should not break any motherboard. It is probably 'only' coincidence in time (the mobo was ready to fail, and would have failed running any operating system).

---

