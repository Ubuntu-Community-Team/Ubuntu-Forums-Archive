---
title: "Jaunty won't install on my Dell Laptop"
date: 2009-10-05
forum: Installation &amp; Upgrades
---

### Post by hoosemon61 on 2009-10-05
I've got a Dell Latitude Cpx (on boot is says CPt V433GT) with a Celeron 433 and 512 MB Ram.

I've tried several times to install Jaunty with a known good disc (2 different ones actually) it hangs every time.

Is it just a lost cause?

Hoosemon

---

### Post by overdrank on 2009-10-05
Hi and have you tried the [alternate cd]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

---

### Post by Bartender on 2009-10-06
Dells often have 4 primary partitions from the factory.  How many yours got?

---

### Post by hoosemon61 on 2009-10-06
*Hi and have you tried the alternate* cd

I haven't tried the alternate CD with this one, but I will

[I]
Dells often have 4 primary partitions from the factory. How many yours got? [/I]

It has just one Partition, only a 5.5GB HDD

I'm also going to try running live to see if that works.  I was going to try the persistent 9.04 thumb drive I have, but this Laptop's BIOS doesn't have an option for boot from USB.

Thanks Hoosemon

---

### Post by mick55 on 2009-10-06
hi 

boot problems are common on older laptops.

Try these boot options

Press F4. Graphics Modes. select the "Safe graphics mode" 

If that doesn't work

Press F6. Other Options. select acpi=off  and noapic.

If that doesn't do it check this site

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

cheers
mick

---

### Post by hoosemon61 on 2009-10-06
I tried safe graphics mode without any luck - same as before.

The two choices you suggested after F6 seemed to get me further along, but it still hung.

I'm trying alternate install disc and it seems to be working so far.

Thanks,

Hoosemon

---

### Post by hoosemon61 on 2009-10-07
So...I tried the Alternate disk twice before I realized I had burned a bad copy.  I burned a new one and it installed fine (had to choose the F6 options you recommended).

Now I've tried to boot off the hard drive and it hangs at exactly the same place as when I was trying to boot from the desktop CD,

It gets the Ubuntu logo and title, with the little side to side Cylon eye thingy underneath (original Battlestar Gallactica), that seemed to work fine.

When it changes to the progress bar that actually fills in left to right, it freezes at about the first 1/10 of the way.

Anyone have ideas, or should I bag it and try a different distro?

Thanks,

Hoosemon

---

### Post by mick55 on 2009-10-07
hi again

Now that Ubuntu is installed to your hard drive you still need
 to disable the same things that prevented the live cd from booting.

Once your computer boots up you can edit your menu.lst
to make the changes permanent.

The link i gave in my post above gives detailed instructions on 
how to enable/disable features at boot time, and also how to
make the changes permanent.

And it explains it far more eloquently than i could.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

good luck
mick

---

### Post by hoosemon61 on 2009-10-10
Mick,

Great info resource, thanks!

Interestingly enough, I went the temporary boot options route first, and the acpi=off and noapic options are already in the list.  I added nolapic and it seemed it would boot because it got past the hang point it was hitting before. both from HDD & CD.

Now it got to thge following point before it stopped booting:

Starting AppArmor
Mounting securityfs on /sys/kernel/security...                {OK} 
Loading AppArmor profiles...
Segmentation fault
(repeated 19 more times)
init: rc-default main process (1692) terminated with status 139


Any idea where to go from here?

Hoosemon

---

### Post by mick55 on 2009-10-10
hi again

This would help me with the diagnosis.

Boot the live cd, open terminal and issue this command

```
lspci
```This will list all your hardware.Post the results here and 
we will see what we can do.

You probably have an [FONT=Arial]ATI Mobility M1 video card, and as you
have probably noticed ATI and Linux don't play nice together.

Also, which specific Ubuntu version are you installing?
The name of the ISO you downloaded is what i am after.

cheers
mick

[/FONT]

---

### Post by hoosemon61 on 2009-10-10
Mick,

The laptop won't boot from the CD - it does basically the same thing when I choose the desired boot options along with safe graphics mode.

The live CD I tried booting from was burned from ubuntu-9.04-desktop-i386.iso

The disc I was able to install on the hard drive was ubuntu-9.04-alternate-i386.iso

Hoosemon

---

### Post by mick55 on 2009-10-10
Bummer.

Look i know you want to run ubuntu, so i recommend you try
this distro - pclinuxos-lxde-2009.4.

It's based on Ubuntu but runs a lightweight desktop and 
is really fast.the ISO weighs in at just over 300mb.

I use it on one of my slower pc's, and it works great.

[html]http://www.pclinuxos.com/index.php?option=com_content&task=view&id=70[/html]give it a shot , you've nothing to lose.

If that doesn't work you might want to try another flavor of linux
like puppy linux or antix.they both work well and are
extremely small packages.

Go here for more linux than you can shake a stick at.

[html]http://distrowatch.com/[/html]good luck
mick

---

### Post by hoosemon61 on 2009-10-11
Thanks Mick,

I actually went to distro watch and downloaded both Mint and Fedora.

Neither will install.

I will try PC Linux OS and Puppy, I was looking at both of those.

It's not critical so it's fun poking around till I find one that works.

This is a laptop that got tossed at work because the serial port has a busted pin.  I'm just doing this so I don't have to watch reality TV.

Thanks for all your help.

Hoosemon

---

