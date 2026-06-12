---
title: "Can't get any driver newer than fglrx-12.100 to work"
date: 2014-01-06
forum: Hardware
---

### Post by a2r on 2014-01-06
Hey guys,

i have a problem with fglrx. Since fglrx-12.100 i can't get any driver newer than that working on my machine. I was running 13.04 with fglrx-updates from the repos (i think)  nearly a year but then I messed up my installation and went back to  12.04 because of stabilty. Here I first installed the driver from the jockey labled "fglrx" but I noticed it was a quite old one then I tried with the fglrx-updates and the experimentals all of them except fpr fglrx-experimental-12 (which I have installed right now) result me booting into either a black screen or a stuck bootscreen (the shiny ubuntu logo). Most of the time I even can't go to a tty.

I tried it with every version of Ubuntu since 12.04, first the problems appeared in 12.10 but I thought it maybe because it wasn't a LTS and 13.04 was a new hope. Then 13.10 again no drivers working (thought it was because AMD was just realease Beta since Catalyst 13.4). 
Now with Catalyst 13.12 released I gave it a shot again (on Trusty) and again stuck on a shiny Ubuntu logo.

I also tried different distro (Arch, Fedora, openSuse) and different DEs (Gnome, KDE, Unity), all the same or similar results.

My Laptop is a Acer Aspire 5820TG with a Mobility Radeon 5650 and a integrated Intel card which I disabled in the BIOS.

Did anyone had similiar issues or knows what I maybe could be doing wrong all the time (Yes, I do a aticonfig --inital after self build installations)? I have a Trusty installation on a second partition if somebody wants me to run some commands for diagnostics.

Thanks for the time and the help!

---

### Post by Bashing-om on 2014-01-07
a2r; Hi !

What I do not know fills a huge book. However, have you considered "switcheroo" ?
[http://planetoss.com/articles/how-to-disable-the-discrete-amd-graphics-card-in-linux/](http://planetoss.com/articles/how-to-disable-the-discrete-amd-graphics-card-in-linux/)
[http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355](http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355)
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

And the mega thread on this graphics configuration, may have some insights:
[http://ubuntuforums.org/showthread.php?t=1930450&highlight=hybrid+graphics](http://ubuntuforums.org/showthread.php?t=1930450&highlight=hybrid+graphics)

[INDENT]not much help but perhaps
[INDENT][INDENT][INDENT]a nudge in the right direction
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by a2r on 2014-01-07
Hi, thanks for the answer.

Maybe I was unclear. I do not care about the switchable/hybrid graphics (because of that I disabled the intel card). 
I just want to install and use a more recent Catalyst driver so I can use a more recent Ubuntu version. 

This is Xorg.0.log [(http://pastebin.com/q4wvekPh]("http://pastebin.com/q4wvekPh")) after the last boot of Ubuntu 14.04 with fgrlx-updates installet. It ends with the shiny ubuntu logo. TTY is not possible. The mighty crtl+alt+REISUB doesn't work either.

---

### Post by Bashing-om on 2014-01-08
a2r; Well !

Looking at your Xorg.0.log files ->
Segmentation faults - stomping on memory - is certainly not a good thing. This is a trial for me, but will do my best to struggle through it with you.
1st, I see that "/etc/X11/xorg.conf.d" is being used, why is not the "->/xorg.conf" config file utilized ? Does it exit ?
```

ls -la /etc/X11/xorg.conf

```

2nd, Have you initialized the radeon driver ?
```

sudo amdconfig --initial

```

Maybe if we can configure "/xorg.conf" will go a long way in resolving the problems (??). Be advised, configuring that file is not at all my long suit.

[INDENT][INDENT]a process of learning
[/INDENT][/INDENT]

---

### Post by a2r on 2014-01-09
You were right /etc/X11/xorg.conf was missing so I ran amdconfig --initial but the issue stays the same. Here is the new Xorg.0.log ([http://pastebin.com/qMtYrWUT](http://pastebin.com/qMtYrWUT)). Here is the xorg.conf ([http://pastebin.com/6dRnjiP0](http://pastebin.com/6dRnjiP0))

I compared xorg.conf from 14.04 with my xorg.conf from 12.04. 12.04 loads "glx" in the modules section which 14.04 does not, I'll add it manually and try it again!

EDIT: Didn't change anything, but as I looked in the logs "glx" is loaded eitherway.

---

### Post by Bashing-om on 2014-01-09
a2r; Hi !

I be look'n !

In the meantime, let's take a gander at what is:
Show us the output of terminal codes:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga

```

To indicate what the system shows for a loaded driver.

Then there is this if you want to try and boot "saucy" -turn on the drivers in bios - (13.10).
[https://launchpad.net/~oibaf/+archive/graphics-drivers/](https://launchpad.net/~oibaf/+archive/graphics-drivers/)
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)
[http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/](http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/)

As a lot has been done in open source to support switchable graphics lately, and a lot has been back ported to 12.04.3.

[INDENT][INDENT]I will be BacK
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-01-09
a2r; Welp ,

Your last log(1):
> 
 [color=red]22.819] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found[/color]
 21.965] (--) PCI:*(0:1:0:0) 1002:68c1:1025:035c rev 0, Mem @ 0xc0000000/134217728, 0xcc000000/131072, I/O @ 0x00003000/256, BIOS @ 0x????????/131072
[    22.632] ukiOpenByBusid: Searching for BusID PCI:1:0:0
##found for 00##
    22.783] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
##card identified:
[    22.857] (--) fglrx(0): Chipset: "AMD Radeon HD 6500M/5600/5700 Series" (Chipset = 0x68c1)
##looking good
23.070] (II) fglrx(0): Adapter AMD Radeon HD 6500M/5600/5700 Series has 6 configurable heads and 1 displays connected.

->##Ouohh, why is the system still searching ? ##
[    23.070] ukiOpenByBusid: Searching for BusID PCI:1:0:0
##but, appears all is happy
    23.070] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    23.070] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
##Still looking GOOD##
 23.070] (II) fglrx(0): Kernel Module version matches driver.

=>##UnGood ! ##
23.071] (EE) fglrx(0): Failed to open CMMQS connection.
##Homework time, what is CMMQS ??? ##

##and same same situation -> segmentation fault, something is stomping all over reserved memory !##
[    23.092] (EE) Segmentation fault at address 0x8a0

->But still, Makes me question the miss match of the PCI indentifications.

From the config file: I presently do not see what the system is screaming about or for:
> 
Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"

Is the 14.04 section the same as this 12.04 one ?

Let me see what conclusions I can draw.

[INDENT][INDENT]I'LL be BaaccKKKk[/INDENT][/INDENT]

---

### Post by a2r on 2014-01-13
I have to confess something, last night I was tinkering around a little and now the installations seems to be more broken then before :-\"
BUT, to make things "easier" I will revert back to 13.10 (install it freshly). I will just run a apt-get upgrade and install the drivers and then I will post Xorg.log and the terminal outputs again.
I will try all three drivers (fglrx, fglrx-updates and build from website) to determine if there is always the same error. 

> Is the 14.04 section the same as this 12.04 one ?

> Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "UseFastTLS" "1"
    BusID       "PCI:1:0:0"
EndSection is the section of the 12.04.4

---

### Post by a2r on 2014-01-17
I opened a new thread to be more specific about the problem. I linked this one in the first post the new one is [http://ubuntuforums.org/showthread.php?t=2200018](http://ubuntuforums.org/showthread.php?t=2200018)

---

### Post by slooksterpsv on 2014-01-17
The latest driver your mobility radeon is compatible with is 13.1, anything past 13.1 isn't compatible

[http://support.amd.com/en-us/download/desktop/previous/detail?os=Linux%20x86&rev=13.1](http://support.amd.com/en-us/download/desktop/previous/detail?os=Linux%20x86&rev=13.1)

---

