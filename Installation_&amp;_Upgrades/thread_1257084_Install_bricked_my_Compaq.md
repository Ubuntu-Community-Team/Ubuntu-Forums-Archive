---
title: "Install bricked my Compaq"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by WASHAD on 2009-09-03
Well, probably bricked is too strong of a word since I imagine it can be fixed. 

My work gave me an old Compaq 1200 that they didn't need, so I thought it would be good for my 9-year old. Of course, my logical choice was to get rid of Window's 2000 and instal Ubuntu entirely. 

After two failed tries with Ubuntu, and Ubuntu CE, I finally was able to get the install to work with the alternate CD - so I thought. 

Now, the computer gets to the pretty Ubuntu welcome screen, the line gets all the way to the right, and the screen goes blank. It never recovers from there. This is the same thing that happened during my failed install attempts, by the way. 

I don't expect that is enough information for you, but perhaps someone could help me diagnose the problem. 

Thanks so much. 

Steve Jackson

---

### Post by lykwydchykyn on 2009-09-03
Do you have the specs on this thing?  From what the great Google tells me, it might not be capable of handling Ubuntu.

Sounds like a problem with the video driver.

If you hit "esc" during boot and get to a boot menu, see if it will boot in "recovery mode".  If so we can do some basic troubleshooting at least.

---

### Post by WASHAD on 2009-09-03
[QUOTE=lykwydchykyn;7892096]Do you have the specs on this thing?  From what the great Google tells me, it might not be capable of handling Ubuntu.
QUOTE]

We certainly don't want to offend the Great Google now do we :). Shame on me for not checking specs first. Perhaps Xubuntu would be a better choice? I'm surprised, though, that it can run Windows 2000 and not Ubuntu. 

It does boot to recovery mode. Should I try troubleshooting or just realize that it wasn't meant to me and move to something a little more friendly to the ol' beast. 

SteveJ

---

### Post by lykwydchykyn on 2009-09-03
> **WASHAD said:**
>  I'm surprised, though, that it can run Windows 2000 and not Ubuntu. 

Windows 2000 was released when a pentium 2 with 128 MB of RAM was considered a decent spec.  It's a pretty tight OS running by itself.

Keep in mind when I say "Ubuntu" I'm talking about the default install with GNOME, compiz, et al.  With a lighter weight desktop environment like LXDE Ubuntu can get competitive with the older OS's.

> 
It does boot to recovery mode. Should I try troubleshooting or just realize that it wasn't meant to me and move to something a little more friendly to the ol' beast. 

SteveJ

Well, that's up to you.  If it's a driver issue, you're going to have to address that in any Linux distro.  I'm fairly certain you CAN make this hardware work with Linux (I've rarely seen hardware that can't be made functional), it's a matter of how much of a project you're interested in having.

If you decide to troubleshoot, I'd say the first thing to check is the Xorg error log:
```

grep EE /var/log/Xorg.0.log 

```

---

### Post by WASHAD on 2009-09-03
Forgive my ignorance. 

- What is LXDE Ubuntu? I assume that L is for light. Is this what I get with XUbuntu or am a to look for a different distro?
- Below is my response to requesing the error log. 

(WW) Warning, (EE) error, (NI) not implemented, (??) Unknown. 
(II) Loading extension MIT-SCREEN-SAVER

Thanks, 

SteveJ

---

### Post by lykwydchykyn on 2009-09-03
> **WASHAD said:**
> Forgive my ignorance. 

It's ok; There's a lot to know here, I didn't know what your background is.
> 
- What is LXDE Ubuntu? I assume that L is for light. Is this what I get with XUbuntu or am a to look for a different distro?

LXDE means "Lightweight X11 Desktop Environment"; it's an alternative to GNOME, KDE, or XFCE (the desktop environments of Ubuntu, Kubuntu, and Xubuntu respectively) which is far less demanding than any of them.  There isn't (yet) an official "Lubuntu" using LXDE as its desktop (there's one in progress), but you can still install the desktop environment in Ubuntu and use that instead of GNOME.

Thinking about it, though, the current issue is to get X11 working, because you're not even to the login screen from what I understand.

> 
- Below is my response to requesing the error log. 

(WW) Warning, (EE) error, (NI) not implemented, (??) Unknown. 
(II) Loading extension MIT-SCREEN-SAVER


Hmm.... yeah, that's not really turning up anything.  Can you run the following commands and give the output (or at least a summary of the output)?  These will give us the specs at least:

```

grep -i memtotal /proc/meminfo
grep -i "model name" /proc/cpuinfo
lspci |grep -i vga
grep -i "driver" /var/log/Xorg.0.log

```
I tried to filter those commands down for minimum output.  Basically:
 - The first one tells you how much RAM is in it.
 - The second tells you what the CPU model/speed is
 - The third should tell you the video hardware
 - The fourth (hopefully) tells you what video driver it's trying to load.

---

### Post by lisati on 2009-09-03
The specs at [http://en.wikipedia.org/wiki/Compaq_Presario_1200](http://en.wikipedia.org/wiki/Compaq_Presario_1200) suggest to me that there's probably not enough ram, and that you'd be lucky to get Ubuntu to work. 

I've managed to get Puppy Linux working on a machine with similar specs, although it ran a little slow.

---

### Post by lykwydchykyn on 2009-09-03
> **lisati said:**
> The specs at [http://en.wikipedia.org/wiki/Compaq_Presario_1200](http://en.wikipedia.org/wiki/Compaq_Presario_1200) suggest to me that there's probably not enough ram, and that you'd be lucky to get Ubuntu to work. 


That's what I was looking at too, though I think it's worth checking the actual machine; if this thing was in use at a company for a long time, it may have had some upgrades from the original specs.

---

### Post by WASHAD on 2009-09-03
> grep -i memtotal /proc/meminfo

311340 Kb



> grep -i "model name" /proc/cpuinfo

Celeron (Coppermine)




> lspci |grep -i vga

01:00.0 VGA Compatible controller: Trident Microsystems CyberBlade i1 (rev 6a)




> grep -i "driver" /var/log/Xorg.0.log

Big response there, but

X.Org Video Driver: 5.0
X.Org XInput driver: 4.0

driver for Trident chipsets: tvga9000, tvga900i, tvga8900c:
{4 entries of} ABI class: X.Org Video Driver, version 5.0




At any rate, I'm ok (and a little embarrased for not checking first) with accepting that the machine won't handle a full-on version of Ubuntu. What should I use instead?

Thanks, 

SteveJ

---

### Post by lkraemer on 2009-09-03
Why don't you download a copy of CrunchBang 9.04.1 and see if it works.
I am running CrunchBang on an OLD Compaq 1672 AMD K6-2 350MHZ with
192 Meg of RAM and it works good.

lkraemer

---

### Post by lykwydchykyn on 2009-09-03
> **WASHAD said:**
> 
At any rate, I'm ok (and a little embarrased for not checking first) with accepting that the machine won't handle a full-on version of Ubuntu. What should I use instead?

Thanks, 

SteveJ

Actually it's not near as bad as I thought.  Ubuntu would be slow on there but it should at least boot and launch a login window.

And there's no need to reinstall at if you're going to stick with an Ubuntu derivative; just install a different desktop environment.

Though, come to think of it, it might be useful to see if you can get something like the crunchbang liveCD to boot.  Then you'd at least know if it was just a lack-of-resources issue or if X is not working with your video card.

---

### Post by WASHAD on 2009-09-03
I'm downloading CrunchBang limited edition now. I'll report back. 

SteveJ

---

### Post by WASHAD on 2009-09-03
> Though, come to think of it, it might be useful to see if you can get something like the crunchbang liveCD to boot. Then you'd at least know if it was just a lack-of-resources issue or if X is not working with your video card.

CrunchBank seems to have the same problem from the live CD. It runs for a while then freezes. 

SteveJ

---

### Post by lykwydchykyn on 2009-09-03
> **WASHAD said:**
> CrunchBank seems to have the same problem from the live CD. It runs for a while then freezes. 

SteveJ

Does it actually get to the desktop though?

If the liveCD is freezing, that typically means one of three things:
 - Bad RAM.  Run memtest (from the liveCD boot menu) on it for an hour or so and see if any errors are detected.
 - Bad CD or CD drive.  Run "dmesg" from the liveCD command line and see if you see any ATA related errors.
 - Heat issue.  Boot to the BIOS (aka CMOS) setup and let it sit for a while.  If it has temperature readings, all the better.  If not, see if it locks up sitting in the BIOS config.  If it does, you have a heat issue.

---

### Post by WASHAD on 2009-09-05
> Does it actually get to the desktop though?

No, it stops before that. 

> - Bad RAM. Run memtest (from the liveCD boot menu) on it for an hour or so and see if any errors are detected.

Ran the test, all passed. 


> - Bad CD or CD drive. Run "dmesg" from the liveCD command line and see if you see any ATA related errors.

Not sure where to run this from; at any rate, CD drive handled entire install of Ubuntu Alternate edition. 



> - Heat issue. Boot to the BIOS (aka CMOS) setup and let it sit for a while. If it has temperature readings, all the better. If not, see if it locks up sitting in the BIOS config. If it does, you have a heat issue.

It made it through the hour long memory test.

---

