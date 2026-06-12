---
title: "Incomplete shutdown issue"
date: 2007-02-11
forum: Hardware &amp; Laptops
---

### Post by L14UX_1NS1D3 on 2007-02-11
Hi.
when I shutdown my desktop computer it does not shutdown fully, the system halt and I have to press the power button.
when I was using dapper I did not have this problem. 
Is there a workaround for this problem?

---

### Post by ridgeland on 2007-02-19
I'm searching for an answer to the same question.
I'm setting up a very old PC with Xubuntu to use as a loaner.  When I choose 'Shut Down' the logo shows then hangs.  I have to push the Power Button in for 7 seconds and it halts.
Somewhere I once saw a post that said they had fixed this with a simple flag in GRUB.  Anyone know what that was?  I can't find that post again.  I'll post back if I can fix it.

---

### Post by ridgeland on 2007-02-19
I'll post again although I could not get it to work.
I found several older threads and bug-reports that suggest adding to the kernel line in 
/boot/grub/menu.lst
The suggestions were to add one of the following:
acpi=off
acpi=power_off
acpi=force lapic
acpi=off apm=power_off
None worked on my PC, a 1997 Gateway2000 GP5-200 with 192MB of RAM, 200 MHz Pentium.
I also tried    acpi=off apm=off  still no luck.
apci=off did eliminate a boot error message of "ACPI: unable to locate RSDP"
Since this is a problem/bug that seems to only be with old equipment I agree that it's a very low priority.  My new (2002) PC doesn't have this problem.
Oh well.

---

### Post by L14UX_1NS1D3 on 2007-02-21
thank you for researching this problem.
I don't know where I would put the extra line is the menu.lst

---

### Post by ridgeland on 2007-02-21
It is not an extra line.  It is an addition to the kernel line.
When you boot your PC GRUB displays a few options such as:
Ubuntu, kernel 2.6.17-11-generic
Ubuntu, kernel 2.6.17-11-generic (recovery mode)
If you look in /boot/grub/menu.lst you will find a lot of comment lines ## then several sections for the different boot options.  Each section will have lines like
title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,10)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda11 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
Notice the title line is what GRUB displayed when you booted.  Test the acpi options by adding them to the kernel line.  In the above just type the acpi=off etc after the word splash on the same line and save the file.  Boot again and see if that fixed it.
In the terminal do these
$ sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.original
This copies the original menu.lst in case of problems.  Always back up a system file before playing with it.
$ sudo gedit /boot/grub/menu.lst
Then be sure the section you edit is the same one you chose or default to in GRUB.  In my case this is the "Ubuntu, kernel 2.6.17-11-generic.  Add one of the apci= lines after splash save and reboot the system.  Repeat the process until you win or run out of options.
Have fun.

---

### Post by L14UX_1NS1D3 on 2007-02-22
Thanks very much for you research, I will try to see if t will work and report back.    ;)

---

### Post by xmastree on 2007-02-22
One thing about this (or any boot option), if you install a new kernel (as happens from time to time) your grub config will be overwritten, so I suggest you make a backup from which to copy your changes to the new one.
Otherwise, you'll forget what you did, and wonder why it's suddenly stopped shutting down again. I did...

---

### Post by Redeyes_Gambit on 2007-02-23
I too have this issue with two machines. 

If you are using an old Dell (gx1/gxa etc) chances are it is an option in the BIOS that is preventing your shutdown. You need to activate ACPI. Turn that on in your BIOS and VIOLA! working shutdown. 

If, however, you have a different machine without an ACPI option, chances are it's a genuine glitch that is preventing proper shutdown. I have a machine like that and I'm still looking for a solution.

---

### Post by L14UX_1NS1D3 on 2007-03-01
yay, I've upgraded. I have a beautiful dell optiplex GX400 nothing to fancy but it's a step up from using my old PIII. no more shutdown issues, it was probably something to do with the bios as you guys said. but now I have to press F1 if I want to boot up because it can 't see the default ide  hard drives I removed and replaced with an old scusi hd. It sees the scusi drive and boots up after I press F1 but I would like to just have it boot up without any interaction. so I'll see if I can fix it and report back later of I run into some problems.

---

### Post by Redeyes_Gambit on 2007-03-07
For anyone else having these issues:

I've fixed it! No more annoying shutdown problems. The answer is kinda spaced out over a couple of posts:

[http://www.ubuntuforums.org/showthread.php?t=314258&highlight=hang](http://www.ubuntuforums.org/showthread.php?t=314258&highlight=hang)

[http://ubuntuforums.org/showthread.php?t=298595&highlight=shutdown](http://ubuntuforums.org/showthread.php?t=298595&highlight=shutdown)

Basically I combined steps from both posts into this:

Step 1: Add 

```
apm power_off=1
```

to your /etc/modules

Mine already had an entry so I just added the code directly below it and then hit enter to add 1 blank space at the end of the file. Basically it should look like this:

```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
apm power_off=1


```

You may have other modules like fuse or p4_clockmod or whatnot. That's ok. So long as you put in "apm power_off=1" and keep a blank entry at the end of the file you should be ok. The blank entry might not be needed, but it was there when I started so I kept it.

Step 2: Add

```
acpi=off apm=power_off
``` 

to your /boot/menu.lst so it looks like this:

```

## ## End Default Options ##

title Debian GNU/Linux, kernel 2.6.18-3-k7
root (hd0,1)
kernel /boot/vmlinuz-2.6.18-3-k7 root=/dev/hda2 ro [COLOR="Red"]acpi=off apm=power_off[/COLOR]
initrd /boot/initrd.img-2.6.18-3-k7

```

You probably have other entries in your boot stanza like quiet splash and the like, but that's ok. So long as the [COLOR="#ff0000"]acpi=off apm=power_off[/COLOR] is there it should work.

Please note that just about all the code and what not are shameless rips from Kross's excellent posts. PM him a pat on the back if this worked for you, since it looks like he really took initiative and tracked this problem down well.

---

### Post by Glucose52 on 2007-03-07
Redeyes_Gambit, that fix works absolutely perfectly on my GX1, I now no longer have any pet peeves about my system :)
It works on mine with only editing /etc/modules. I did not need to change the kernel options.
Thanks for the informative posts.

I am using Bios revison A04 with ACPI on.

---

### Post by ridgeland on 2007-03-07
I tried it on my old PC. /etc/modules and /boot/grub/menu.lst
Not lucky though.  It still hangs rather than powering off.
So I changed a BIOS setting to PowerManagement=enabled (AMIBIOS 1996)
Now when it shuts down it boots back up :) shutdown now = restart :)
Oh well... 
I set it back to just hanging, not re-booting.

---

### Post by dinkoarun on 2007-03-18
I had this problem in my Kubuntu Edgy.

I added the **acpi=force lapic** in the boot parameters and it solved the problem.

---

### Post by Haim on 2007-03-20
If you are using APM then this site explains it nicely.

[http://www.togaware.com/linux/survivor/APM_Power.html](http://www.togaware.com/linux/survivor/APM_Power.html)

Note that ubuntu uses apm as a module rather than in kernel.

The modules addition then is as stated ealier with the power_off parameter in the modules file.

---

### Post by John_W on 2007-05-03
**Redeyes_Gambit** - Your solution fixed my 10 year old Super-Micro motherboard shutdown hang problem. 
Thanks for the information!

---

### Post by GerryB on 2007-05-19
Fantastic answers. It gave me another idea and I'll see if it works. The most comforting one was that this does not happen on newer computers. Since Feisty is going to be installed on a relatively recent computer it won't be an issue. Thank you all, especially Kross who started the ball rolling. :)


I remembered a section in the BIOS on Power Management. It does have a ACPI section but no choices on enabling or disabling. So I followed these wonderful instructions and the problem is solved. Thanks again.

---

### Post by Richhard on 2007-06-25
Hi Redeyes_Gambit

your advice was the final step to solve my problem :D !! Perhaps to help somebody else, 
I like to tell my story:

1) my soundcard did not work. After a long trial and errorphase, I find out, a simple:
acpi=off   in /boot/menu.lst helped, the sound was perfect.

2) but now the shut down is hanging. This I could correct with:
acpi=off apm=on    in /boot/menu.lst  and additionally
apm power_off=1   in /etc/modules

---

### Post by Richhard on 2007-06-25
I forget the following remarks:

- my PC is an old one, where in the BIOS only APM is implemented

- therefore don't forget to enable this option in the BIOS !!

---

