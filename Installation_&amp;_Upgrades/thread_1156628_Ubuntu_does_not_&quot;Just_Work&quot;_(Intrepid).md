---
title: "Ubuntu does not &quot;Just Work&quot; (Intrepid)"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by Tweak1029 on 2009-05-11
So I put in the CD, boot to the installer, select my keymap, timezone, that stuff, then a popup says that the partitioner is loading.  It loads, goes away, but nothing comes up and my computer is frozen.

Yes, the disc is good.  Yes, I tested the disc.  The machine is a Dell Inspiron 9300.

It is getting really, really frustrating.  Help, please.

> Next time you start a thread, especially about installation, it's imperative that you include a rundown of your hardware (processor type, ram, HDD size, video card, sound card).

Duly noted.

Here:
Intel Pentium M 2.13 GHz
2 GB DDR2 533 MHz RAM (PC2-4200)
160 GB EIDE HDD
ATI Radeon Mobility X300

That ought to cover it.  Anything else just ask.

---

### Post by Ericyzfr1 on 2009-05-11
What kind of partitions you have on your disk?

---

### Post by epswinde on 2009-05-11
1) try booting all the way to the live cd environment to see if your hardware is functional.  There's a way to start the installer there and I've always had better luck doing it that way.

2) try the alternate installation cd.  its a text installer, so there's less to muck up booting wise.  It is a little harder to use the partitioner though.

I would like to add that hardly anything ever "just works".  Try installing windows xp and you'll see what i mean. ;-)

---

### Post by Tweak1029 on 2009-05-11
XP is installed and runs perfectly, but that doesn't mean I like it any more.  I'll give those suggestions a shot.

I'm on the Ubuntu Live CD right now.  First thing I did was to start Firefox and connect to my wireless network.  Firefox didn't even have time to start up and "firefox crashed with SIGSEGV in JS_XDRScript()".

---

### Post by Tweak1029 on 2009-05-11
> **Ericyzfr1 said:**
> What kind of partitions you have on your disk?

A single NTFS partition taking up the entire 160 GB.

I tried running the installer from the live environment but it did a similar thing.  Rather than freezing, though, the installation just stopped and now I have a useless window open that gives me the busy cursor when I mouse over it.

I managed 3 segfaults in about 15 minutes and said screw it and went to try the "safe graphics" installer.  For me, that means staring at a black screen with a blinking cursor for ten minutes waiting for the installer to come up, and then realizing that it was screwing up... again.

---

### Post by epswinde on 2009-05-11
sounds like the iso image you downloaded didn't turn out right.  When you start your system, try the option of 'verifying the disk' or whatever its called.  That'll check the integrity of the disk and make sure that there's no errors.

With no other information about your system this is the best i can do.  Next time you start a thread, especially about installation, it's imperative that you include a rundown of your hardware (processor type, ram, HDD size, video card, sound card).

The alternate install disk is a different cd image (it does not have a live cd environment on it), so you'll have to download another disk -- this isn't the same as the safe graphics mode installer.

---

### Post by Tweak1029 on 2009-05-12
Edited OP with the info you mentioned.

The disk verifies and I've tested it on another machine and it worked fine.

---

### Post by Tweak1029 on 2009-05-12
Bump.

---

### Post by wpshooter on 2009-05-12
Have you tried installing using the safe graphics mode parameter ?

If that does not work, then download the ALTERNATE (text based) CD version of Ubuntu and trying installation from that.

---

### Post by Tweak1029 on 2009-05-14
Didn't work, so I downloaded the alternate (yes, the text based one) CD version of Ubuntu and tried installing from it.

Didn't work.  The screen came up with weird colors and aside from that it was blank.  I took a picture on my phone but won't be able to upload it until I find someone whom I can send it to that can put it on a computer.

---

### Post by ezsit on 2009-05-14
> The disk verifies and I've tested it on another machine and it worked fine.

This tells you that is some hardware issue in the Dell Inspiron 9300. Usual suspects are RAM and video. Is you installed as 2 sticks of 1GB each, or a single 2GB stick? If you have two sticks of RAM, pull one and try booting the machine, and continue testing both sticks in both slots until you hit every combination. 

Once you rule out a RAM problem, look to the video. Is your video built-in the motherboard or a separate card? If you have onboard video, go into the BIOS and make sure you have enough video ram designated, select the highest amount of shared memory possible for video ram. If you have a separate video card and onboard video, pull the video card and use the onboard video and test the live CD like that.

Once you rule out RAM and video problems, the rest of the hardware is probably all on the motherboard and there is just something about your motherboard that Ubuntu does not like.

---

### Post by juancarlospaco on 2009-05-14
***[COLOR="Blue"]Use 9.04 Jaunty![/COLOR]***

---

### Post by upchucky on 2009-05-14
just a bit of a heads up, both intrepid and jaunty are beta, 

hardy 8.04 is the current long term supported release.

there are video issues with both intrepid and jaunty, but these issues do not show up on all machines.

---

### Post by epswinde on 2009-05-16
> **upchucky said:**
> just a bit of a heads up, both intrepid and jaunty are beta

That's wrong.  intrepid and jaunty are both stable releases -- they're not LTS releases, but that doesn't make them beta software.

---

### Post by prostar on 2009-05-16
I learned a long time ago to ALWAYS use the alternate installer. If you try a newer version go with 9.04, because 9.10 is actually beta. If you are saying the alternate install comes up with garbage graphics even before selecting language and install menus, then you have a graphics problem.

---

### Post by erixoltan on 2009-05-16
This is a bit of a radical solution, but if all else fails then you could try to install Ubuntu Server Edition.  Then you can enable the universe and multiverse repositories by editing sources.list and uncommenting those lines.

sudo nano /etc/apt/sources.list

Then you can run an update.

sudo apt-get update

Finally install ubuntu-desktop.

sudo apt-get install ubuntu-desktop

I have done this with success in the past.  I wouldn't recommend it normally, except that in this case it looks like nothing else is working.

---

### Post by Tweak1029 on 2009-05-16
Heh, sorry I couldn't reply sooner.

My RAM is brand new, plus I've tested each stick individually and together using Memtest86+ plus booted to Windows using each configuration.  The tested the old sticks of 512 MB the same way and all four sticks do the same thing.  My current configuration is 2 x 1GB.

> Once you rule out a RAM problem, look to the video. Is your video built-in the motherboard or a separate card? If you have onboard video, go into the BIOS and make sure you have enough video ram designated, select the highest amount of shared memory possible for video ram. If you have a separate video card and onboard video, pull the video card and use the onboard video and test the live CD like that.

This stupid Dell laptop BIOS isn't that configurable.  I'm using a video card, and, as far as I know, the motherboard doesn't have onboard video.  Is there a way to test it without replacing the video card?  I don't have a spare lying around and I'd rather not throw another $50 at this thing.

I need to upload that picture.  I'm not sure how to describe it.

---

### Post by ugm6hr on 2009-05-16
> **Tweak1029 said:**
> So I put in the CD, boot to the installer, select my keymap, timezone, that stuff, then a popup says that the partitioner is loading.  It loads, goes away, but nothing comes up and my computer is frozen.

Does Ubuntu work in the LiveCD (try without making changes) mode?

Is there a reason you haven't tried 9.04 Jaunty?

Have you tried the "Check CD for defects" option?  Did you check md5sum? (Edit: presumably yes, since you say you checked it)

---

### Post by Tweak1029 on 2009-05-16
> **ugm6hr said:**
> Does Ubuntu work in the LiveCD (try without making changes) mode?

Is there a reason you haven't tried 9.04 Jaunty?

Have you tried the "Check CD for defects" option?  Did you check md5sum? (Edit: presumably yes, since you say you checked it)

My internet is crappy 384k DSL so it takes it a few days to download, so I haven't tried it until the other day, when I got the 9.04 alternate installer.

Ubuntu works in the liveCD mode with no changes.  I believe that I made a post from there using this laptop in Ubuntu 8.10 live CD mode.  Things tend to segfault from there, though.  The CD is fine.


Here's the picture:
[img]http://img199.imageshack.us/img199/4016/i3900crap.jpg[/img]

---

### Post by ugm6hr on 2009-05-16
I'd suggest manually partitioning using GParted from the LiveCD, then install using the manual mode (may as well use the 9.04 AltCD).

It sounds like the installer partitioner is where the problems occur; perhaps trying to take that out of the equation might help.

I do wonder whether Ubuntu will run on a Pentium M though....

---

### Post by Tweak1029 on 2009-05-16
I've tried that.  It didn't work.

That picture is what happens (It's never the same, but it looks a lot like that) when I go to install from the Ubuntu alt-cd.  Nothing happens, it just goes to that screen.  It's being checked for defects as I'm typing, on another computer.

About Ubuntu running on a Pentium M: It can.

And another note: Debian Lenny / Etch do the same thing as the Ubuntu 9.04 Alt CD.

---

### Post by Tweak1029 on 2009-05-17
Is there a way to test my video card without replacing it?

---

### Post by ugm6hr on 2009-05-18
> **Tweak1029 said:**
> Is there a way to test my video card without replacing it?

I can't understand how that can be the issue, since you say the LiveCD opens X just fine.

Does GParted work OK?  Perhaps you have a HD problem which is preventing Ubutu from installing correctly.

---

### Post by pawnrocket on 2009-05-18
This doesn't help you any but... 
I saw the same screen on a compaq laptop with ATI graphics. The card was good but 7.04 wasn't easily compatible. Later I reinstalled a 8.04 system. 

Where you don't have the intel graphics card you might be better off trying the 9.04 installer. Even if it takes a little while to get it - there could be a fix in it. 

I don't know them, but ask about boot options. I imagine someone in here is familier with the possibilities..

---

