---
title: "Dual booting Ubuntu and Vista on a Packard Bell laptop"
date: 2008-09-08
forum: Hardware
---

### Post by jmmL on 2008-09-08
I've ordered a Packard Bell MB88-P-003 (here's a [**link**]("http://www.packardbell.co.uk/products/notebooks/easynote-mb-white/easynote-mb88-p-003/productsheet-PC03Q00101-1240.html")) for university work, which will hopefully arrive on Thursday.

It comes with Vista, but obviously I'd like to install Ubuntu! Ideally, I'd end up with a dual-boot set up. However I've read around more today about installing Ubuntu (or any other OS) on modern laptops, and it would seem that a lot of manufacturers "tattoo" their laptops, so that only the OS that came with the system can be installed. It seems to work by having information stored in a hidden partition of the hard drive (usually /dev/sda1, with Vista on sda2), that is checked against the MBR for changes. Therefore, if you alter the MBR, Vista can refuse to load properly. Packard Bell is apparently particularly guilty of this, and apparently so are a lot of other laptop manufacturers - but notably not Lenovo and Dell.

Does any of this sound remotely right? Has anyone had to deal with this "tattoo" business? Are there any useful guides online? Searches of these forums don't turn up anything, and Google searches tend to be clogged with results of other kinds of tattoos. I found [**this page**]("http://www.google.com/translate?u=http%3A%2F%2Fpagesperso-orange.fr%2Fvschultz%2FPB-SB89-P-008W-FR.html&hl=en&ie=UTF-8&sl=fr&tl=en") that mentions ways around the problem (it's after the table). However, the site's in French, and Google's translation isn't brilliant. It would seem that it's do-able to have a working dual-booting system, but I don't want to mess anything up in case I need to return the system in the condition that it came in.

Can anyone shed any light on the situation? I'm quite close to canceling the order...

---

### Post by jmmL on 2008-09-09
Just to keep anyone who's watching updated; I've cautiously decided to go along with the order. I'm going to make sure I image the HDD so that it can be returned "as new" if needed.

This page ([**link**]("http://www.google.com/translate?u=http%3A%2F%2Fpagesperso-orange.fr%2Fvschultz%2FPB-SB89-P-008W-FR.html&hl=en&ie=UTF-8&sl=fr&tl=en")) has details about running Ubuntu with a similar Packard Bell, and has a quick guide to installing Ubuntu and keeping Vista at the same time. The original page is in French, but the link is to Google's translation.

I plan to write a quick guide or HowTo, regardless of how my experience goes. Hopefully it might guide the small number of people who have these laptops, and the even smaller number who wish to try out Ubuntu (or any distro) on them! Any replies to the original are still welcome!

---

### Post by pelle.k on 2008-09-21
I'm very interested in how things went? Maybe you haven't got it yet?
Either way, does everything work out-of-the-box? Can you suspend/hibernate?

How is the screen (my god i'm sensitive to this), good/bad viewing angles?
No silk screen effect (or grainy white)?
Does it get hot, and also is it noisy?

I apologize for all the question marks. Couldn't help it. :)

---

### Post by jmmL on 2008-09-22
Yep, I got it last Friday. I really must write the guide soon, but other things have taken precedence!

Suspend seems to work perfectly out of the box: everything comes back on perfectly afterwards - sound, compiz, wifi - everything! I haven't tried hibernating yet - but i can if that would help you?

The screen is pretty good. It's glossy, and has a good viewing angles. 

> No silk screen effect (or grainy white)?

I don't understand what you mean here...
It sounds like I'm not quite as exacting about you in terms of screen quality - so if it's really important, you might want to find a way to see it in real life. I could take a picture and upload it, if that would help?
One thing I would say about the screen: it's pretty dull-looking out-of-the-box, but installing nvidia-settings and turning up the digital vibrance brings life into it.

Everything else worked out of the box - I can't think of any particular things I've had a problem with. It doesn't get hot really.

The CPU idles at 52C, load at 55C - but I have undervolted it. The VIDs are 19, 19 and 19 for the 3 frequencies, in case you're interested. I followed [_this guide_]("http://ubuntuforums.org/showthread.php?t=786402"). The GPU is the main source of heat - it's usually at 65C regardless of load. I'd like to reduce this if possible, but I don't know how - I suspect it's eating into the battery life. The battery is supposed to last for 2 hours, however I get more like 2:20 - 2:30 once I run some power-saving scripts from these forums. The keyboard and touchpad area only get hot if you have the row of LEDs on at the front - I always turn them off, I think they're pointless. 

It's not really noisy at all; only for about 2 seconds when all the fans turn on at start-up, but after that it's still very quiet (bordering inaudible just surfing the web), even under load. Again, it's the GPU making most of the noise. Using the DVD drive can be fairly noisy - I don't keep any discs in there.

The speakers are pretty good quality as well, and there's a dedicated subwoofer. However - don't expect miracles from them - they're still not as good as stand alone speakers, and aren't as loud.

The wifi antenae seems very good - I get good signal all over the house, even though the router is only broadcasting on the "g" standard. The hardware wifi switch also works perfectly out of the box, as do all the other hardware switches, except mute, for some weird reason.

I haven't tried the eSATA, HDMI or Firewire ports - but I think I tried the card-reader and that worked out of the box. However, I'm not sure about that, so don't hold me to it!

Anything else you'd like to know?

---

### Post by pelle.k on 2008-09-22
Thankyou so much!
My GPU (on my current lg r500) is also around 60 degrees (mostly under, but it's a 8600m GS, not GT) so that's no too bad. Doesn't bother me at least.
Did you take a look at nvidia-settings "powermizer"? Mine is in Performance level "0" fore the most part. It does clock dynamically when it is needed though. About that, when i use compiz-fusion (or desktop effects if you will), i always have a slight stutter when maximizing/minimizing windows. My desktop with a GF 8600 GT doesn't, so that's why i'm asking you if you have that? (question 1).

Also, you said most media/hot-keys work. Those that didn't, do they at least send keycodes to X (you can check that with "xev" in a terminal window). Or, as a last resort, do they at least send scancodes to the kernel? (you may check "dmesg" ouput in a terminal window) (question 2)

And last of all, this is not necessary, but if you feel you have the time, could you check the BIOS DSDT for errors? The procedure is rather easy, and will show how good of a job packard bell did with ACPI compability and such (question 3);
```
sudo apt-get iasl
cp /proc/acpi/dsdt .
sudo iasl -d dsdt
sudo iasl -tc dsdt.dsl
```

Thankyou for thaking the time to respond :)

---

### Post by jmmL on 2008-09-22
That's not a problem!

I should note here that I have a 8600M GS in my MB88, which is what it was advertised as having on the website. However I think they should have more correctly called it a MB85 - that's what the BIOS says it is. My card is usually at Performance level 0 as well. I *very rarely* get stutters, when minimising / closing etc, but it does happen.

**EDIT: Scratch that.**
I just checked nvidia-settings again and it's on level 2 and 1 mostly. I'm not doing anything unusual - just firefox, synaptic and a terminal open. I've got the highest level of compiz effects on, but the cube and reflection are turned off. Any idea how to reduce the level?

EDIT AGAIN
It seems to have calmed down now, and the GPU fan has stopped whirring. Hmm

The ones that don't work are Fn + F1 (don't know what this one does, it has a really weird symbol), Fn + F4 (Bluetooth - don't have a module) and Fn + F6 (mute). F1 is caught by xev, but F4 and F6 aren't. I don't know what I'm doing with dmseg, there's a lot of output, and it's in the attached zip (along with the dsdt.dsl file). If you can tell me how to get it in a more readable format, I can post that. I just used 
```
echo `dmesg` > dmesg.txt
```

Whilst I ran dmesg I had a mouse and an external hard drive also plugged in. I was on AC power.

Output of the iasl stuff:

```
jamie@hardy-laptop:~$ sudo iasl -tc dsdt.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20061109 [May 16 2007]
Copyright (C) 2000 - 2006 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl    71:             Acquire (\_SB.PCI0.LPCB.EC0.MUT0, 0x5000)
Warning  1103 -               Possible operator timeout is ignored ^ 

dsdt.dsl    80:             Acquire (\_SB.PCI0.LPCB.EC0.MUT0, 0x0100)
Warning  1103 -               Possible operator timeout is ignored ^ 

dsdt.dsl   483:                     Acquire (\_SB.PCI0.LPCB.EC0.MUT0, 0x5000)
Warning  1103 -                       Possible operator timeout is ignored ^ 

dsdt.dsl   566:                     Acquire (\_SB.PCI0.LPCB.EC0.MUT0, 0x5000)
Warning  1103 -                       Possible operator timeout is ignored ^ 

dsdt.dsl   724:                     Acquire (\_SB.PCI0.LPCB.EC0.MUT0, 0x5000)
Warning  1103 -                       Possible operator timeout is ignored ^ 

dsdt.dsl   753:                     Acquire (\_SB.PCI0.LPCB.EC0.MUT0, 0x5000)
Warning  1103 -                       Possible operator timeout is ignored ^ 

dsdt.dsl   796:                     Acquire (\_SB.PCI0.LPCB.EC0.MUT0, 0x5000)
Warning  1103 -                       Possible operator timeout is ignored ^ 

dsdt.dsl   832:                 Acquire (\_SB.PCI0.LPCB.EC0.MUT0, 0x5000)
Warning  1103 -                   Possible operator timeout is ignored ^ 

dsdt.dsl  1017:                     Acquire (\_SB.PCI0.LPCB.EC0.MUT0, 0x5000)
Warning  1103 -                       Possible operator timeout is ignored ^ 

dsdt.dsl  1984:                             Acquire (\_SB.PCI0.LPCB.EC0.MUT0, 0x5000)
Warning  1103 -                               Possible operator timeout is ignored ^ 

dsdt.dsl  1992:                             Acquire (\_SB.PCI0.LPCB.EC0.MUT0, 0x5000)
Warning  1103 -                               Possible operator timeout is ignored ^ 

dsdt.dsl  3998:                         Acquire (MUT0, 0x5000)
Warning  1103 -        Possible operator timeout is ignored ^ 

dsdt.dsl  4008:                         Acquire (MUT0, 0x5000)
Warning  1103 -        Possible operator timeout is ignored ^ 

dsdt.dsl  4317:                         Acquire (MUT0, 0x5000)
Warning  1103 -        Possible operator timeout is ignored ^ 

dsdt.dsl  4326:                         Acquire (MUT0, 0x5000)
Warning  1103 -        Possible operator timeout is ignored ^ 

dsdt.dsl  4377:                         Acquire (MUT0, 0x5000)
Warning  1103 -        Possible operator timeout is ignored ^ 

ASL Input:  dsdt.dsl - 5856 lines, 205592 bytes, 2391 keywords
AML Output: dsdt.aml - 21922 bytes 585 named objects 1806 executable opcodes

Compilation complete. 0 Errors, 16 Warnings, 0 Remarks, 935 Optimizations

```
Is that good/bad for ACPI compliance?

Now could I ask you for a little help?
I've been experimenting playing HD video. I used a 720p .MKV file and tried totem, VLC and Mplayer. Mplayer and VLC were the best, but it was still a bit stuttery in parts. If you know of any way of getting hardware acceleration, or any better codecs to install, that'd be great. I tried it in Vista as well; it was slightly better there, but I still don't think it was hardware-accelerated. As far as I can tell .MKVs can't be accelerated, YET. But I'd love to be proved wrong :D
If it becomes too much of an issue I'll post a new thread.

---

### Post by pelle.k on 2008-09-22
> Any idea how to reduce the level?
Sure. This is an interesting read;
[http://owened.net/2008/04/23/how-to-force-nvidia-powermizer-performance-in-linux/](http://owened.net/2008/04/23/how-to-force-nvidia-powermizer-performance-in-linux/)
Basically, open up /etc/X11/xorg.conf and add
```
Option  "RegistryDwords"    "PowerMizerLevel=0×3"
```
in the nvidia card section.

Dmesg is just raw kernel output, so if a key was pressed, and X didn't catch it, the kernel would basically say something like;
"scancode XXXXX received, use setkeycodes xxx xxx to make it known".
I didn't see anything, maybe you hadn't pressed any keys before you made the "dmesg"? Not very important though, i was just a bit curious.

> Is that good/bad for ACPI compliance?
Quite good actually. No errors, just 16 warnings. I had like a thousand warnings and a couple of erorrs, which may or may not have asignificant impact on ACPI and stability in general. That's why you see people booting with acpi=off parameters in grub and such. It works, but it's not that fun to have to turn off ACPI to make the computer boot. :/

> As far as I can tell .MKVs can't be accelerated, YET. But I'd love to be proved wrong 
Actually, "matroska video" or MKV in short, is not a codec per se, but a container for audio and video streams (as well as for subtitles etc), so it's up to what codec that is in that particular MKV file you've got there.
Usually it's h.264, but it may also be some something else like real video 9/10.
Unfortunately, it would seem that only mpeg2 is supported by nvidias "purevideo" in linux as of yet i'm afraid. That said, i usually have no problems playing HD content, but to be honest, i've only tried a few clips here and there.
I did encode some of my own HDV movies in 720p, and those clips did play nicely though. Maybe they werent as compressed? (less to decode?)

---

