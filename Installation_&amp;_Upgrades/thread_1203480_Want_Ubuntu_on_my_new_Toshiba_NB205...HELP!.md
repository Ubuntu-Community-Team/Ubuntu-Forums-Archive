---
title: "Want Ubuntu on my new Toshiba NB205...HELP!"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by Doctor_Gonzo on 2009-07-03
So i picked up this sweet little netbook yesterday and the first thing i did was repartition the hard drive and slap an ubuntu dual boot on her...

Unfortunately, Jaunty so far is no bueno...the boot time is horrendous...no wifi...and even the simple tasks seem to handle like a pregnant ox...

I'm a semi-noob when it comes to linux. Although I've been running ubuntu for years now, I became accustomed to everything just working and never being a few minor tweaks away from a somewhat perfect system...

At the moment I'm forced to use XP (which as much as I hate to say it, runs rather well so far), but since ubuntu has always been my preferred OS, I'm wondering if anyone out there has managed to get Jaunty working on the Toshiba nb205 (or whatever other brands it's selling under overseas). I liked the idea of setting up UNR and all that jazz, but with the current performance I'm just not feeling it.

Please help me get away from Windows!

The netbook has your typical specs:

1.66 n280 atom
1 g ram
intel 945 chipset
160 g hd
atheros wireless
0.3 mp webcam
etc.

---

### Post by solidus126 on 2009-07-10
Hello Doctor_Gonzo.

I am having a very similar experience with my NB205 as well and have the exact same hardware configuration as yourself. I am using Kubuntu instead of regular Ubuntu, and have had no luck with wireless either, and programs are running extremely slow. Like yourself, my XP install is running great, and I am confused as to what is causing things to go awry.

I have been testing [Ubuntu Netbook Remix]("http://www.ubuntu.com/GetUbuntu/download-netbook") this morning, and while it is a rather dissimilar setup from the regular desktop edition, I think it may serve fairly well for quick tasks.  It runs much faster than my attempted install of Kubuntu did, but just a heads up, I still have no Wifi.

If you come up with any progress, please let me know and I will re-post if I come up with anything.

-solidus126

---

### Post by Mark Phelps on 2009-07-10
You should really NOT be installing the regular Ubuntu distro for use on Netbooks.  You should use the previous mentioned Ubuntu Netbook Remix, or also check distrowatch.com for Moblin and other such netbook-oriented distros.

---

### Post by solidus126 on 2009-07-10
**HOWTO: Wifi in Ubuntu Netbook Remix for Toshiba NB205**

I got the wireless card to work!  I had to use Ubuntu Netbook Remix, and have not tested my method using regular Ubuntu or Kubuntu.

After scouring the internet, I found a solution from a post on Ubuntuforums.org. I have since lost the link to the forum post, but still have the link they had posted in the forum:

[http://tjmcgrew.com/](http://tjmcgrew.com/)

Here is an adapted and condensed series of instructions:

1. Install Ubuntu Netbook Remix. I did not really stray from default install options.

2. Do a full system update by going to Administration -> Update Manager. Check for updates first, then install them. You will likely need to reboot your computer... do so. You should see a new option in GRUB, probably kernel 2.6.28-13-generic, which is the one you want to boot back into.

3. Now, go to Administration -> Software Sources. In the Updates tab check "Unsupported updates (jaunty-backports)". I also checked everything in the Ubuntu Software tab with the exception of the Cdrom box, and the two boxes in Third-Party software, but I am fairly certain they are not needed for fixing wifi.

4. Repeat step 2. My reasoning for not doing 3 first is because it seems to download extra fluff and adding excessive GRUB menu entries if you do it out of this order.

5. Issue the following command in a terminal window (found in the Accessories tab)

```
sudo apt-get install linux-backports-modules-jaunty
```

After accepting the request to install the packages, reboot.

6. In my case, after logging in my network was automatically detected and my connection was live!

If anyone has any questions about a step, I am happy to clarify any small detail I may have missed.

---

### Post by Doctor_Gonzo on 2009-07-10
All is good so far...except no sound...any ideas on that fix?

---

### Post by harty83 on 2009-07-10
Sound, bluetooth, and hibernate are all not working for me.  Any ideas on how to get these working?  I've applied to work around to get sound from my headphones jack.  I really need bluetooth to work and hibernate would be really nice.

Thanks!
Alan

---

### Post by solidus126 on 2009-07-11
**Doctor_Gonzo**: As far as sound goes, I have not had any luck yet. The author of the link I posted in the howto thinks it may be an ALSA bug, which I think he is right about.

**harty83**: I have the NB205-N210 which does not come with Bluetooth, so I am afraid I cannot help you there. Sound still is a bust ATM, and hibernate is still untested as of yet, but I would not be surprised if it did not work (have almost always had problems with it in this release and older). Where you able to get headphones sound working, and if so, how?

-solidus126

---

### Post by harty83 on 2009-07-11
> **solidus126 said:**
> **Doctor_Gonzo**: As far as sound goes, I have not had any luck yet. The author of the link I posted in the howto thinks it may be an ALSA bug, which I think he is right about.

**harty83**: I have the NB205-N210 which does not come with Bluetooth, so I am afraid I cannot help you there. Sound still is a bust ATM, and hibernate is still untested as of yet, but I would not be surprised if it did not work (have almost always had problems with it in this release and older). Where you able to get headphones sound working, and if so, how?

-solidus126

To get the headphones to work add the following to /etc/modprobe.d/alsa-base.conf:

```

options snd-hda-intel model=asus-mode4

```


I haven't tried it yet, but people have reported getting their sound to work on nb200 using OSS instead of alsa.  Here is the how to: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound).  System sounds do not work unless you recompile somethings but you can at least get the app sounds to work.  I'll probably be doing this myself within a couple of days.

I really wish I could get bluetooth to work :-(  Gotta  love open source but at times...gotta hate it as well ;-)

Thanks!
Alan

---

### Post by harty83 on 2009-07-11
Just as an update, I was able to get basic sound to work using OSS4 per the instructions in the above link.  Of course I had to use the skype-oss-static package to get skype to work.  I haven't got my mic working yet though....one step at a time :-)

Thanks,
Alan

---

### Post by harty83 on 2009-07-13
Sound and mic are working with OSS.  

Hibernate is working with s2disk (suspend works out of the box) (see [http://jrobbo.com/blog/?p=37](http://jrobbo.com/blog/?p=37) for instructions). And make sure you also add resume=/dev/sda6 where sda6 is your swap drive to the kernel boot options in /boot/grub/menu.lst. Then run sudo update-grub.

Now if I can just get bluetooth to work; I'd be all set!!

---

### Post by solidus126 on 2009-07-14
harty83,

Thanks for your continued updates on your setup progress!  I wish I could help out on the bluetooth side of things, but my model comes sans-bluetooth. I am starting to think this thread should be compiled into a nice single howto for ease of use.  Care if I put it together including your parts?

Cheers,

-solidus126

---

### Post by harty83 on 2009-07-14
Sure.  Be my guest.

Thanks,
Alan

---

### Post by Doctor_Gonzo on 2009-07-14
Hey Hardy can you give a simple step-by-step to get the OSS drivers working for the mic and sound? 

Also, my camera seems to lag really bad through cheesy...is anyone else seeing this? It works pretty well through XP...

---

### Post by harty83 on 2009-07-15
> **Doctor_Gonzo said:**
> Hey Hardy can you give a simple step-by-step to get the OSS drivers working for the mic and sound? 

Also, my camera seems to lag really bad through cheesy...is anyone else seeing this? It works pretty well through XP...

Well I just followed the instructions laid out from that URL above. Then to get the mic working, I ran ossxmix and changed the int-mic mode to input. This turned the mic on.  Change it back to mix2 or anything other than input to turn it off.

Its not the best quality but at least it works :-)

Thanks,
Alan

---

### Post by Doctor_Gonzo on 2009-07-15
That worked...and yeah, quality sucks, but i suppose beggars can't be choosers right now...I find UNR works great overall and is very responsive, but if I want to do any heavy browsing/skype/etc. I'm still stuck using XP...Hopefully by the time university starts up there will be better support...

---

### Post by jhh09 on 2009-07-17
How is the sound volume in Ubuntu compared to XP?  I've heard the speaker volume in the NB205 is too low.

---

### Post by awynne on 2009-07-18
Yep, the speaker is awful in XP and Linux

---

### Post by Doctor_Gonzo on 2009-07-18
I get a slight cracking in UNR...not there in XP...but yeah either way, the speakers are useless unless maybe you're in the library...and even then you'd be hard pressed to even piss off the librarian...

---

### Post by solidus126 on 2009-07-19
Pretty much the only way to go is to have a nice pair of headphones/earbuds, or an external pair of speakers. I was a little surprised to see how quiet the speaker is when I got it, I think Doctor_Gonzo described it the best, ha!

-solidus126

---

### Post by harty83 on 2009-07-20
Looks like someone started a how to guide [here]("http://ubuntuforums.org/showthread.php?p=7648784"). We should probably keep this conversation in a single place and thus suggest posting questions/work arounds in that thread.

Thanks,
Alan

---

### Post by Raymone50 on 2009-10-15
Hi, i have a Toshiba NB205-210 i tried ubuntu remix and it ran too slow, so i put Mint 7 on my computer, (it runs much faster now), yet i had the same problems with the wireless so i followed the steps and installed the juanty backports, my wireless works now, but its shaky, sometimes it doesn't want to connect to the internet and i can no longer connect to a wired connection, does anyone know how to fix this?

---

### Post by aegl on 2009-11-09
> **Raymone50 said:**
> Hi, i have a Toshiba NB205-210 i tried ubuntu remix and it ran too slow, so i put Mint 7 on my computer, (it runs much faster now), yet i had the same problems with the wireless so i followed the steps and installed the juanty backports, my wireless works now, but its shaky, sometimes it doesn't want to connect to the internet and i can no longer connect to a wired connection, does anyone know how to fix this?

Using "pci=nomsi" boot option seems to fix some of the boot speed options here.

---

### Post by MikeCamel on 2010-01-04
For those using Ubuntu 9.10 (and therefore grub2), things are a little less pleasant than before if you want to add this option.  I had to do a good amount of searching to find out how to add options to grub's new config file (/boot/grub/grub.cfg), as things have changed somewhat, so I thought I'd record the steps here for posterity.  Oh - and adding it has significantly improved boot time.

NOTE: as with all changes to boot loaders, any changes you make which are incorrect may leave you with an _unbootable_system_.  Caveat emptor.

I suggest that you back up the original /boot/grub/grub.cfg file somewhere, just for safety.

[LIST=1]
[*]Edit /etc/grub.d/10_linux as root ('sudo gedit', or whatever).
[*]Find the line "{$GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}"
[*]Edit it to the following:  "{$GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT} pci=nomsi"
[*]run 'update-grub' as root (e.g. 'sudo update-grub).
[/LIST]
At this point, I did a diff between the new /boot/grub/grub.cfg file and the old one, just to check that the only difference was the "pci=nomsi" addition, and it looked good.  IIRC (I'm a different machine), this should leave the recovery options without this change, which is a nice safety net.

Now, reboot, and cross your fingers (probably for a nice, short time, as things should be much quicker) now.

---

