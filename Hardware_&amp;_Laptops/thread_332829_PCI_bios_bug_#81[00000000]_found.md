---
title: "PCI: bios bug #81[00000000] found"
date: 2007-01-06
forum: Hardware &amp; Laptops
---

### Post by anmb on 2007-01-06
I have installed 6.10 on a fujitsu-siemens Amilo Pro V2055.
Everything has gone fine and working OK - really pleased (my first trouble free install)

I have one small problem though.
When booting I get the message:
PCI: bios bug #81[00000000] found

the laptop still boots and I can use it as normal but I have NO idea what the message is telling me.
I have updated my bios and searched google and the ubuntu forums but can find nothing.

What does this error message mean ? and how can I solve it ?
thanks Roy :-?

---

### Post by teaker1s on 2007-01-06
I'm guessing that it relates to motherboard bios, it would be worth checking with the manufacturer if there is bios update;)

---

### Post by anmb on 2007-01-06
I have downloaded and installed bios uodate from futitsu-siemens and still the same
thanks Roy

---

### Post by teaker1s on 2007-01-06
Did you try acpi=off ? this thread it's talked about
[http://www.ubuntuforums.org/showthread.php?t=257912]("http://www.ubuntuforums.org/showthread.php?t=257912")

---

### Post by anmb on 2007-01-06
noacpi gives the same message
acpi=off gives a stream of "unknown bus type 2"

I assume I am doing it correctly and editing grub as it boots with the noacpi or acpi=off
thanks Roy

---

### Post by llelkes on 2007-01-19
Hi!

I have a same noetbook, also bios bug, but i did not care... but I would have some questions according to the NB:

Did You tried the WIFI? Does it work for You? I can see the WIFI network, but I can not connect (default driver what is in ubuntu 6.10) :( any idea?

A secound think what I'd like to ask how is it with the cooler? It seems to be that all the time going on full RPMs :( it's quite loud :(

And a graphic is also a bit slow (e.g. listing in mozzila a page is not going fluently, jumping - same in openoffice) is it normal with that shared memory graphic card?

Thanks, regards,

llelkes

(AMILO PRO V2055, UBUNTU 6.10, last update around 1.jan. - no special driver just what is from the package)

---

### Post by miaviator278 on 2007-02-13
This is an older post so i am not sure if the issue still exists but for future googlers,   

Try recompiling your kernel and under the pci access mode option choose direct instead of any. 

JD

---

### Post by ChrisNiemy on 2007-09-04
Hi!
There are also some kernel options for /boot/grub/menu.lst You can also edit this on the fly in grub before booting. I also tried pci=biosirq, but error remains. I will give pci=direct a try. But this works only when kernel is recompiled with this.

Have the same error message on a HP G6050EG notebook. In my experience the system seems to be a little unstable sometimes. Having trouble switching consoles with Ctrl+Alt+Fx (framebuffer issue?) and sometimes the system is out for lunch and won't come back. Not sure if this comes from this PCI #81 bug.

The error with irq 7 I get also. Kernel messages show "try "irqpoll" option".

I'm wondering if ```
pci=direct irqpoll
``` might help. Will give it a try.

(also try: ```
pci=direct irqpoll noapic nolapic
``` But with the last two, power management won't be available.


Edit: Found on google: [http://lists.infodrom.org/linux-stammtisch/2006/0554.html](http://lists.infodrom.org/linux-stammtisch/2006/0554.html)
maybe it's an issue on irq 7 with the wlan stuff. She says that when no wlan is needed bootoptions are **irqpoll**
when wlan is needed bootoptions used: **pc=noacpi usepircmask**

You can also check: ```
man bootparam
```
more in the kernel doc: /<path to kernel source>/Documentation/kernel-parameters.txt (or install the -doc package for your kernel)

---

### Post by Lal2017 on 2007-09-04
Using a HP Pavillion DV6000 series (6258se) Laptop, Nvidia GeForce Go 6150, 1.8GHz Turion 64 X2 Dual Core with 2gb RAM. After using Ubuntu 6 then upgrading sucessfully to 704 for a few weeks, my Laptop suddenly began to hang during boot. Suspecting a recent Ubuntu update within the last few days did it. 

Also the battery no longer charges whether Laptop is off or on. whereupon I started paying more attention to the error messages on launch. Bios Bug #81 is a new message which I have not noticed before. I perfomed a BIOS upgrade to F38 in the very beginning before dumping Vista and going to Linux Ubuntu 6 and didn't notice this error. I think this is something new with my recent upgrade to Fiesty 704. I just did a fresh re-install using the install disc for Fiesty 704 and now have Kernel 2.6.20-15 generic. Same error and still can't boot despite the install disc working. 

I am new to Linux (although a Wintel Techie), so having a terrible time getting Ubuntu back up. Laptop still hangs on bootup & recovery mode. I believe my problem is compounded with the video driver hanging the machine on bootup. 

So one problem at a time....Bios Bug#81: Any Ideas anyone? Happy to test this step by step.

---

### Post by Lal2017 on 2007-09-04
Just to update folks from my earlier post. I have isolated the HP DV6000 series Laptop Battery recharging problem to HP Power Management (probably BIOS). I have fixed it. However still get the Bios # Bug81 error. Still investigating.

---

### Post by ChrisNiemy on 2007-09-04
Have a HP G6000 with Athlon 64bit  X2, Nvidia, Broadcom. Nearly the same problems.

Hangs always when doing perodically e2fsck on boot. Also when switching from runlevel 1 to user run level, for example. So when switching from graphical X to framebuffer console or vga console.
It only works with "**noapic nolapic fb=false vga=normal**" and removing "splash". Though it's sad because then cpufrequency-scaling won't work anymore.

Sorry, can you explain again, what you did with the battery to get this hang ups on boot time fixed? Thanks. :-)

"Hoping" this problem occurs more often, so probably there will be a workaround in next kernel releases.

---

### Post by AnthonyW on 2007-09-05
I have a presario F560US with the GeForce Go6150.  I also get the Bios Bug 81 error and was having trouble installing a booting Ubuntu.

My system was also hanging on boot due to Ubuntu not liking my video card and/or display.  I was able to get ubuntu 7.04 to boot by adding vga=0x33d to the kernel loading line in GRUB.  Ubuntu now boots up fine but I get 'Internal error - Failed to Initialize HAL'  ARGGGHGHGHGHG

This is a fresh install of 7.04 and I have not tried to fix or update any more drivers as of yet (took me all night just to get the thing to boot!)

---

### Post by ChrisNiemy on 2007-09-07
I was quite bored and frustrated ;-) and tried booting with the edgy eft live cd to see how this might be different through kernel versions. In default it won't even boot. (feisty does at least)

At least it worked with the kernel boot options
```
pci=biosirq pnpbios=off mem=nopentium irqpoll
```

I guess "mem=nopentium" is not that important (e.g. if you have an Intel processor leave it out, though it's actually for older kernels). 
But it seemes to work better somehow with all these options. But can't quite tell if this is so on the long run.

Keyboard typing is now a bit buggy though. I guess that comes from "irq=poll". Try to leave this out, if it's not essential to solve the problem.


Conclusion:
Here some of the errors it got/get:
- "PCI BIOS BUG #81 found"
- "Disabling IRQ 7: nobody cared" (or so)
- "calling WQBA"

typical error behaviour:
When switching from Xserver to consoles (with Ctrl+Alt+1, e.g.) the system would freeze. Display turns off, the fan turns up, then off again. HD writes something out, than absolutely nothing more. Until It boot with "noapic nolapic". This sucks because frequency scaling etc etc won't work anymore then.

When doing e2fsck while booting (interval of 30 max mounts) the system would definetely freeze as described above.  Again until booted with "noapic nolapic". Or extracting something   in the console would let the system go out to sleep or to lunch. ;-) :-(

Mhm, a little bit sad, because I thought HP had somehow best linux  compatibility. A more silent one in comparism with Dell (which of course is in a leading role) but.... ahhh, no I gut this BIOS bug. :( Phoenix BIOSes...


EDIT/PS:
The kernel can access PCI devices through so called MMConfig or direct or through the bios. MMconfig seems not to worked. And bios is a little buggy. Don't know anything   about this, but perhaps somebody can use this information.

Links:
**Check also this thread here**: [application go black, then notebook dies!](http://ubuntuforums.org/showthread.php?t=469158)

---

### Post by ChrisNiemy on 2007-09-08
[offtopic]
some kind off-topic, but great news and helpful:
new ubuntu search engine (customized google):
[http://us.cypherbios.org/browser-extension.htm#](http://us.cypherbios.org/browser-extension.htm#)
[http://us.cypherbios.org/index.htm](http://us.cypherbios.org/index.htm)
[/offtopic]


I searched on it on this BIOS BUG:
[http://us.cypherbios.org/index.htm?cof=FORID:11&cx=002072379199720138921:9m-bgfzutzq&q=PCI+BIOS+BUG+%2381](http://us.cypherbios.org/index.htm?cof=FORID:11&cx=002072379199720138921:9m-bgfzutzq&q=PCI+BIOS+BUG+%2381)


Perhaps this link is helpful to this topic here:
[https://answers.launchpad.net/ubuntu/+question/3623](https://answers.launchpad.net/ubuntu/+question/3623)

---

### Post by Vic! on 2007-09-08
i have the same problem with the bios bug #81 but so far the only buggy behavior my computer has is sometimes at shutdown it wont fully turn off it will close all windows and the screen will go black after the ubuntu screen finishes shutdown but the computer just doesnt turn off. then i use the power button. most of the time though it switches off without a problem. and the hibernate and suspend work pretty well .

i have a toshiba satellite a135 s4656 

is there anywhere i can report this so that like chris niemy said it is known that this is a commom problem and it can be fixed in newer versions>

Thanx 
V

---

### Post by skidzo on 2007-09-10
> **Vic! said:**
> 
is there anywhere i can report this so that like chris niemy said it is known that this is a commom problem and it can be fixed in newer versions>


I think this is kernel related so it should be no bios but a software bug!

 I erased my actually perfect working Ubuntu 7.04 64 bit (upgraded from edgy eft and wanted to do a clean install of 7.04) never had this bios error message and just gave kubuntu 7.04 a try, from the first boot after a nice installation session it showed this error. Kubuntu works a bit buggy when shuting down somehow the mouted partitions can not be released.

Quite anoying! Dont have time to investigate this further atm.

My dates: Acer Aspire 5103WLMi LXAX90... also with 64 X2 and i installed the x86 version.

Maybee this is also processor related as i changed from an 32bit to an 64bit kernel....

Good Luck, I hope I could help you...

---

### Post by ChrisNiemy on 2007-09-11
@skidzo: Thanks for the idea. When I have enough time and my bandwith connection back, I will give it a try. Currently running Feisty in x86.

Currently to this topic, I stumbled upon this thread about a Compaq Laptop:
[http://ubuntuforums.org/showthread.php?t=458164](http://ubuntuforums.org/showthread.php?t=458164)
There's the option **noirqdebug** which one could add to the previous (see above) options. Will give it a try.

Then a queistion to Lal2017:
> **Lal2017 said:**
> Just to update folks from my earlier post. I have isolated the HP DV6000 series Laptop Battery recharging problem to HP Power Management (probably BIOS). _I have fixed it_. However still get the Bios # Bug81 error. Still investigating.
Could you explain this again more detailed, how you fixed the power management? thanks a lot. :-)

---

### Post by Lal2017 on 2007-09-12
> **ChrisNiemy said:**
> ...Sorry, can you explain again, what you did with the battery to get this hang ups on boot time fixed? Thanks. :-)

"Hoping" this problem occurs more often, so probably there will be a workaround in next kernel releases.

The battery issue I had seems to be coincidental with the other problems I had with Ubuntu 704.  The HP Pavillion dv6000 series (dv6258se) had a discharged battery through std use, which would not recharge either in Ubuntu, XP or when switched off. From the net I tried the following which worked:
1. Ensure the battery is fully discharged by trying to run the laptop without the power plugged in. 
2. Disconnect the battery (and power cord) from the laptop and leave for 5 minutes.
3. Keep the power button pressed for over a minute. 
4. reconnect the battery ONLY and press the power button down for a minute ...again. 
5. Reconnect the power cable and the unit should begin re-charging per normal after about 5 minutes. Allow to fully recharge over 2hrs +.

Regards,
Raj

---

### Post by ChrisNiemy on 2007-09-12
@Lal2017: Hey, thanks a lot!! :-) I also was wondering why battery life is so short. Perhaps my battery isn't that powerful. But will try that. Would be great, if it works for me. thx again.

---
here's on last thing I found out:
> **skidzo said:**
> I erased my actually perfect working Ubuntu 7.04 **_64 bit_** (upgraded from edgy eft and wanted to do a clean install of 7.04) never had this bios error message
On the community docs on [http://help.ubuntu.com](http://help.ubuntu.com) I found this topic:
[Installation/32bitonAMD64]("https://help.ubuntu.com/community/Installation/32bitonAMD64")  What is said there underpins, that when installing x86_64 ubuntu an your AMD64 you might will have less of these problems or none of them at all. Thanks for this hint.

---

### Post by ATrentino on 2007-09-15
I have an HP dv9408 with AMD Turion 64x2m nVidia Geforce Go 6150 and 1 GB of RAM. As many of you have reported, I too get the bios bug #81 when I boot.

---

### Post by ChrisNiemy on 2007-11-02
hey people,

found a new boot option: ```
pci=conf1
```

The error or warning message seems to be gone. :-)

Possible options are pci=conf1 or pci=conf2. conf2 for me is not working, it won't boot. pci=confX implies automatically pci=nobios, so you might should erase other options like pci=biosirq.

PS:
Unfortunately this did not solved the bug or whatever, that the system on my hp laptop ALWAYS crashes when switching to a virtual terminal with ctrl+alt+f1 etc after a while.

---

### Post by slaykristian on 2007-11-03
Hy guys!
Most probably everyone in this post have a notebook with a AMD cpu and "Phoenix Bios".
This is a problem of TRUSTED COMPUTING. Phoenix bios lock the acpi control of your O.S.
The concequences are continues freezes and crashes... 'Cause Ubuntu Can't controls this features...

The solution... Sad but true... change of notebook... :(

Bye from Italy!

---

### Post by dptxp on 2007-11-07
I too get this message on ACER 5101, Turion 64 bit

0.248778] PCI: BIOS BUG #81[49435000] found
[ 0.522793] PCI: Failed to allocate mem resource #6:100000c0000000 for 0000:0
1:00.0

Did not get in Feisty, but get with both 32 bit and 64 bit Gutsy.
Can we live with this ?

It is a 6 month old laptop, can not afford another.

---

### Post by dptxp on 2007-11-10
Got to be Kernel problem. It is there with other distros too

[http://forums.fedoraforum.org/showthread.php?t=153310](http://forums.fedoraforum.org/showthread.php?t=153310)

---

### Post by hums07 on 2007-11-26
A friend of mine got the same problem. His computer is HP pavilion tx1209 AMD Turion64 X2, PhoenixBIOS 4.0 Release 6.1, NVIDIA GeForce Go 6150.

---

### Post by bradmayne on 2007-11-28
im getting a BIOS bug message also.  it happens during boot up.  i'm now using gutsy gibbon. the rest of my info is at the bottom.

---

### Post by ChrisNiemy on 2007-12-22
try it again with the boot option
```
pci=nommconf
```

But make sure, that is is not overwritten by other pci options you set before.

For now I can't say if it helps. Just try it.

The thing which drives me quite mad is that I'm getting tired of trying different kernel boot options combinations. However, notebook is usable and runs ok. But why did HP selected such a crappy BIOS on their notebooks?

---

### Post by gsb521 on 2007-12-26
I have an Acer Aspire 5100 series with the same problem (49435000).  It's got Turion 64, and Phoenix Bios.  I'm wondering if this is one of the things which are leading to my inability to suspend or hibernate in linux.

---

### Post by ozPATT on 2008-01-06
same bug here on my compaq v3000 series. I have had it since installing Gutsy, never had it before. but as has been mentioned, it doesnt seem to affect the running of the computer at all... just comes up each time it starts.... only 12 weeks or so until the next release, so maybe not worth trying to fix?

---

### Post by VereVa on 2008-01-11
In 7.04 and 7.10 all works good (but, video 3D not work normal) i have V2055
please post to
[http://www.tkarena.com/forums/linux-arena/33267-via-unichrome-pro-fujitsu-siemens-amilo-pro-v2055-ubuntu-7-04-a-3.html?=#post230026](http://www.tkarena.com/forums/linux-arena/33267-via-unichrome-pro-fujitsu-siemens-amilo-pro-v2055-ubuntu-7-04-a-3.html?=#post230026)
so that developers can filter driver

---

### Post by Daelyn on 2008-01-12
I do wonder if this is something similar to my experiences.
I have two Graphic cards in my computer that are selected with a switch on it.

When I'm switching to the Intel card and reboot I do not get this PCI bla bla bla stuff, but, as soon as I switch to the nVidia card and reboot I get that message. Although, everything works absolutley fine so I'm not worried the slightest. Just recognized this.

Could it be some shared memory allocation thingy that can not be found/decided?
Maybe I'm just out of my league here, who knows? 

Cheers / newbie n00b

---

### Post by VereVa on 2008-01-15
sorry I wanted to say that the bug is stayed, but, system works stable

---

### Post by Mizzou_Engineer on 2008-02-26
> **slaykristian said:**
> Hy guys!
Most probably everyone in this post have a notebook with a AMD cpu and "Phoenix Bios".
This is a problem of TRUSTED COMPUTING. Phoenix bios lock the acpi control of your O.S.
The concequences are continues freezes and crashes... 'Cause Ubuntu Can't controls this features...

The solution... Sad but true... change of notebook... :(

Bye from Italy!

I have a Gateway S-7125C (aka E-155C/C-120X) with an Intel Core 2 Duo U7500 and Phoenix BIOS and get the BIOS BUG #81 at boot also, except it's not [00000000] but [4-and-a-bunch-of-digits.] Yes, there is also a TPM chip in there as it's a business computer with a fingerprint reader. However, I have the TPM stuff all disabled in the BIOS and as a result, the TPM is invisible to the OS and should not cause any problems. Here's the dmesg:

Here's what I think the relevant line from dmesg is:

[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0

I hope that helps...

---

### Post by killer_d76 on 2008-02-29
i have " PCI: bios bug #81[00000000] found " error too when trying to install ubuntu 7.10 at my Neo Empriva, and it did not allow me to install Ubuntu on my laptop, but when we try to install it on my colleage u Neo Centrino, we were able to install it without any problem :(.. i really wanted to install this one on my laptop and i need your help really bad!.. thanks

note: when i run AVG on my computer i found this..
kernell32.dll  - changed
shell32.dll - changed

can anybody explain to me what this means?.. i badly needed all the help i can get! thanks in advance.

---

### Post by Daelyn on 2008-03-08
> **Mizzou_Engineer said:**
> I have a Gateway S-7125C (aka E-155C/C-120X) with an Intel Core 2 Duo U7500 and Phoenix BIOS and get the BIOS BUG #81 at boot also, except it's not [00000000] but [4-and-a-bunch-of-digits.] Yes, there is also a TPM chip in there as it's a business computer with a fingerprint reader. However, I have the TPM stuff all disabled in the BIOS and as a result, the TPM is invisible to the OS and should not cause any problems. Here's the dmesg:

Here's what I think the relevant line from dmesg is:

[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0

I hope that helps...

I have TPM and Fingerprint reader on mine also.

This has been concurrent now though. Done a few reinstallations and it is ALWAYS the same.
When I use the built in the chipset GFX card, Intel, I do not get any errors.
As soon as I switch to use the Nvidia card instead (also built in, switched with a switch) I get this error. 

So, seems to be related to my GFX card. How it is connected and how it allocates resources.

---

### Post by dptxp on 2008-03-10
The " ... Unable to allocate resources......" error is with other OS sidux and kanotix too. If you do a search, it is with many other distros. Users have started ignoring it as a kernel problem that does no harm.

---

