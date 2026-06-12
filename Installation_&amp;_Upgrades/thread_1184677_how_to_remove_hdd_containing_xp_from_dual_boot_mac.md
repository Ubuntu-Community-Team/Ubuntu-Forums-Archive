---
title: "how to remove hdd containing xp from dual boot machine"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by wolfee1 on 2009-06-11
Hi

I've been running ubuntu (currently 9.04) for a couple of months now in a dual boot machine along with XP on 2 seperate hard drives and have decided I have no need for XP any more :D, So now I wish to remove the hard drive with xp so that I can use it in a hdd enclosure as an external drive on a laptop.  I naively thought I could just remove the xp drive, but now realise that ubuntu won't load without it.

So how do I go about doing it?  Having searched the problem it seems it's something to do with grub (?) which is a bit beyond me, is there a simple way of sorting this?

thanks in advance

---

### Post by jimv on 2009-06-11
You need to setup Grub on your Ubuntu drive. To do this, remove the XP hard drive, then boot from the Ubuntu live cd.  Open a terminal and type:

```
sudo grub

root (hd0,0)

setup (hd0)

quit
```


Then reboot.

---

### Post by wolfee1 on 2009-06-11
Thanks, i'll give it a go.  I just need to identify the xp drive first,  I'm using 2 identical maxtor 80gb drives, so how do I tell which one to unplug?

will it matter if I use the 8.10 live cd?, I've upgraded to 9.04 since first installation.

---

### Post by merlinus on 2009-06-11
As long as you can get to a terminal, it does not matter which live cd you are using.  In fact, you can do this from your ubuntu install:

```

sudo fdisk -l

```should show which is which.

---

### Post by jimv on 2009-06-11
Pull out a drive.  When you're logged into the live cd, browse the remaining drive.  If you see a Windows folder, is is the Windows drive.  :)

---

### Post by wolfee1 on 2009-06-11
Thanks guy's, all sorted now.

:D

---

### Post by wolfee1 on 2009-06-13
since doing this i've rebooted a few times with no problems, however earlier when i started my pc it stopped on the bios screen and didn't automatically enter the grub boot options as normal.  There was also an extra option as well as the usual f2>set up and f11>boot options, there was also an Esc>skip memory test (or something like) which I've never seen before.  As far as I could tell there was no memory test or anything else happening and the screen just stayed that way until I hit the Esc button which then bought up the text "GRUB Loading stage1.5."  Again that stayed that way until i hit enter at which point grub loaded as normal (still with the option to boot xp despite the hdd containing it being removed!?).

After rebooting again I realised [SIZE=2]I[SIZE=3]Cannot now enter set up on the bios screen, [SIZE=2]if i do the screen goes black, nothing happens and I have to reboot again.  I can enter the boot options menu though.  So is this related to installing grub or just a coincidence? should I start a new thread?  [/SIZE][/SIZE][/SIZE]Is there anything I can do to recover it? 

cheers

Wolfee1

---

