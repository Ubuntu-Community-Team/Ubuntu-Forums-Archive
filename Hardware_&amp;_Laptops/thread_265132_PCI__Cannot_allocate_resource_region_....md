---
title: "PCI : Cannot allocate resource region ..."
date: 2006-09-25
forum: Hardware &amp; Laptops
---

### Post by lfys on 2006-09-25
Somewhere in the very beginning of the  start-up of Ubuntu 6.06 I get the following message:

```
[17179571.952000] PCI : Cannot allocate resource region 7 of bridge 0000:00:1e.0
[17179571.952000] PCI : Cannot allocate resource region 8 of bridge 0000:00:1e.0
```

Does anybody know what it means?

_________________________________________

Had a quick search on the web. Seems there 's a lot of laptop users having the same issue, all without any further consequences.
Doesn't matter then, I suppose. :neutral:

---

### Post by mrojas73 on 2006-09-29
> **lfys said:**
> Somewhere in the very beginning of the  start-up of Ubuntu 6.06 I get the following message:

```
[17179571.952000] PCI : Cannot allocate resource region 7 of bridge 0000:00:1e.0
[17179571.952000] PCI : Cannot allocate resource region 8 of bridge 0000:00:1e.0
```

Does anybody know what it means?

_________________________________________

Had a quick search on the web. Seems there 's a lot of laptop users having the same issue, all without any further consequences.
Doesn't matter then, I suppose. :neutral:

I don't know what it means, I get the same error on my Aspire 5601 AWLMI.  The computers seems to function just fine.

---

### Post by pmilin@ptt.yu on 2006-10-13
I got the very same problem on my HP nx8220. I had even posted a thread, asking about this problem: [http://www.ubuntuforums.org/showthread.php?t=247801](http://www.ubuntuforums.org/showthread.php?t=247801).
However, none responded. On Ubuntu-chat I got an answer that 'everything is working, so why bother'. But, this is anoying for me, and the answer from chat is shalow-like: Plain lost left wing, but we are still flying! Why bother! :-k But, I do bother!

Sincerely,
Petar Milin

---

### Post by MrSoussey on 2007-01-14
try a bios update... worked for me

---

### Post by Healey on 2007-01-27
Hi

Did you fix this problem  ??????

I have the same situation even with the newest bios for my laptop

Regards

Healey

---

### Post by Healey on 2007-01-27
Hi 

Just thought I would add some more infomation

I have a Compaq Presario C310EA using dapper but I had the same problem with Edgy

I also have the LATEST BIOS from the HP Compaq site

Regards

Healey

---

### Post by J0Sb31R on 2007-02-25
same "problem" here with Acer Aspire 1641WLMI, everything else works like a charm :)

---

### Post by RamiroS on 2007-03-02
Same problem here with Acer Aspire 5100-5033

---

### Post by bvmou on 2007-03-17
I have the same boot message with a Presario c304nr ($450 at bestbuy!) but I dont think it is actually a problem.  If you look at other laptops in the same family, there is a PCI port next to the USB females.  My guess is that on the budget models they used the same motherboard but left out the PCI hardware and didn't modify the bios since all that stuff would be invisible to most users.  Strictly a guess, but seems likely to me.

---

### Post by drmanzi on 2007-03-18
I have an Acer Aspire 3680 with Ubuntu 6.10 and it shows the same problem.
My notebook has a Bluetooth integrated but disabled for this model.
So it's likely that the problem.

---

### Post by casposa on 2007-04-12
> **drmanzi said:**
> I have an Acer Aspire 3680 with Ubuntu 6.10 and it shows the same problem.
My notebook has a Bluetooth integrated but disabled for this model.
So it's likely that the problem.

Same here with a Acer Travelmate 4020 series laptop...bluetooth is also integrated but disabled.
Everything works fine and I can't find any answer in other forums/wikis/...

---

### Post by gvigorus on 2007-07-31
I'm on Powerbook G3 Lombard running Xubuntu Feisty Fawn. I get this at boot:
PCI: Can not allocate resource region 1 of device 0000:00:11.0
My Wifi Lucent Technologies B does not work It's a PCMCIA card. Please help.

---

### Post by hillyu on 2007-10-02
acer 5573 same problem

---

### Post by stickey on 2007-10-23
Had same issue with Asus M2A-VM HDMI board.  Flashed bios to version 1001 and seems to be OK now.

---

### Post by elnerdo on 2007-10-23
I have the same problem, however my laptop does NOT boot.  After I get the error, my computer screen turns black and nothing happens.

---

### Post by orphe on 2007-10-24
This is a Kernel IRQ problem. I don't know ow to fix it but i looked where this happens
in the kernel source code

---

### Post by bsmith on 2007-10-25
Hey, I'm getting the same problem, the error line is repeated like 10 times, I wouldn't mind so much if I couldn't see it :P

On a benq s41

---

### Post by aletomsic on 2007-10-27
got the same problem with hp pavillion zd8000 latest bios...

---

### Post by GingerAlex on 2007-10-31
I have an Aspire 5612ZWLMi and the same problem.

This never happened when I was on 7.04 but has happened ever since I was on Gutsy, so I'm not so sure that this is a hardware problem.

I have also had terrible problem with suspending and hibernating the laptop - its never worked since I upgraded, but obviously I have no idea if this is connected to the PCI message, so I'll pursue it elsewhere.

---

### Post by Nesmontu on 2007-11-05
Same "problem" here. I also used to have it on my old eMac, and I seem to recall finding somewhere on the PPC forums that it had to do with ATI graphics cards -- can't find that info anymore though, was a couple of years ago.

@GingerAlex: The suspend/hibernate thing is due to the Gutsy upgrade, has nothing to do with that error message. Apparently something changed in the way the kernel handles suspend/hibernate, and the video drivers from ATI and nVidia don't like it... more info here
[http://ubuntuforums.org/showthread.php?t=579781](http://ubuntuforums.org/showthread.php?t=579781)

---

### Post by raninaki on 2007-11-28
same problem, acer aspire5600..

---

### Post by MoparMark on 2007-12-10
I'm experiencing a similar problem on boot...

Dell Optiplex 755
Core 2 Duo  1.8Ghz
4GB ram
Ubuntu 7.10 64bit

pci cannot allocate resource region blah blah blah

I flashed the bios from A03 to A04 and it had no effect.

:popcorn:

---

### Post by HeWhoE on 2008-01-14
As the kernel loads on my laptop, I get the messages too!

Mine are as follows:

> 
[   12.116603] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[   12.116669] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[   12.116730] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[   12.116791] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[   12.116880] PCI: Cannot allocate resource region 0 of device 0000:06:00.0


I use a Compaq Presario C300.

---

### Post by Healey on 2008-01-14
Hi

I have a Compaq Presario C310EA and I am using Feisty and it works fine. I had the same issues as you with both Dapper and Edgy but Feisty is OK. I did not upgrade to Gutsy because it was rubbish on my desktop and when I tried the live CD on this laptop it was also no good !!!!

I will stay with Feisty for as long as it is supported then try the next version and see what happens - i think the next version wil be a long term support so it should be good !!!

I hope it will be better than Gutsy

Could be worth a try for you

Regards

Healey

---

### Post by pavan.ngs on 2008-03-05
same problem

and also getting some extra line under it

buffer i/o error on device sr0, logical block.............some thing like this

i am using acer aspire 5570z laptop

---

### Post by philpool on 2008-03-09
same problem here:
[INDENT]acer aspire 5920[/INDENT]
this model doesn't come with bluetooth while others do....

---

### Post by Reonarudo on 2008-03-10
I have the same problem, and since it slows down the booting it is more than I need to not use ubuntu at all while I can boot windows faster and do the same thing...

---

### Post by BixMix on 2008-03-13
I get the same message:
PCI: Cannot allocate resource region 7 of bridge 
PCI: Cannot allocate resource region 8 of bridge 
PCI: Cannot allocate resource region 9 of bridge 

I have an HP laptop--Pavilion zd8000 with a Pentium 4 CPU 3.00GHz 

It has taken me a week (and a 2nd install) to get the wireless working, so I haven't spent much time on this, and I'm not too sure where to turn right now.

---

### Post by feistybill on 2008-03-18
Same problem here, Acer Travelmate 6292. Everything works, but I hate that message popping up each time I boot my Linux...

---

### Post by 1ll3xc on 2008-03-24
Same "problem" here on my Fujitsu-Siemens M3438 running Gutsy seemingly with no negative consequences though...

Cheers!

---

### Post by deputysalty on 2008-03-30
> **BixMix said:**
> I get the same message:
PCI: Cannot allocate resource region 7 of bridge 
PCI: Cannot allocate resource region 8 of bridge 
PCI: Cannot allocate resource region 9 of bridge 

I have an HP laptop--Pavilion zd8000 with a Pentium 4 CPU 3.00GHz 

It has taken me a week (and a 2nd install) to get the wireless working, so I haven't spent much time on this, and I'm not too sure where to turn right now.

Got the same issue with the same laptop, HP Pavilion zd8000, same regions...ugh!

---

### Post by nroussi on 2008-04-11
well mine IS a problem and not a "problem". I just install 7.10 server on a poweredge 4300 with a PERC2 adapter and it gave me the error "cannot allocate resource" but it never boots. It is giving another error after that: 
aacraid: host adapter abort request. SCSI hang?

anyone knows what that means?

---

