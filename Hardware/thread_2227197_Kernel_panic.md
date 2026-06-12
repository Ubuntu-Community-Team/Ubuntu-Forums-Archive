---
title: "Kernel panic"
date: 2014-05-31
forum: Hardware
---

### Post by neke123 on 2014-05-31
I have very strange problem with PC,it refuses to boot any OS on market.
I am not sure where is problem but this is log:

[IMG]https://onedrive.live.com/redir?resid=291A137EF260FA7%212175[/IMG]
[https://onedrive.live.com/redir?resid=291A137EF260FA7%212175](https://onedrive.live.com/redir?resid=291A137EF260FA7%212175)

Specs:

MB - MSI MS-7592
RAM - Kingston 2Gb DDR3 (I did mem test,it passes without errors)
CPU - Intel E5700
BIOS - latest

---

### Post by codingman on 2014-05-31
Have you tried going into BIOS setting and setting the boot order to a USB/CD/DVD that contains Ubuntu? Can you please explain how you have attempted to run these OSes and which OSes/distributions you have tried?

---

### Post by Joel_Ross on 2014-05-31
you might have a hardware problem, if no OS is installing for you I can only imagine it's a hardware issue.

---

### Post by mörgæs on 2014-05-31
You have a kernel panic, not a booting problem. Changed the title accordingly.

---

### Post by matt_symes on 2014-05-31
Hi

Are you getting that error while booting from a LiveCD/USB ?

If not, how did you install Linux.

Please list all your hardware and its specs.

Kind regards

---

### Post by codingman on 2014-05-31
> **neke123 said:**
> *<snip>*it refuses to boot any OS on market.*</snip>*

What *precisely* do you mean by this?

---

### Post by neke123 on 2014-05-31
> **matt_symes said:**
> Hi

Are you getting that error while booting from a LiveCD/USB ?

If not, how did you install Linux.

Please list all your hardware and its specs.

Kind regards


That was LiveCD (tried from phone using DriveDroid and real CD,two Ubuntu versions one was 12.04 and the other one 14.04 both 32-bit)
Windows install but none wants to boot (Windows 8,8.1,7,Vista)

About hardware,its all new,most of components are few months old but they did work yesterday on old motherboard but not everything crashes.

P.S. I underclocked processor and RAM so its not problem in these parts,im really running out of ideas.

---

### Post by neke123 on 2014-05-31
> **codingman said:**
> What *precisely* do you mean by this?

Not one single OS is booting.

---

### Post by codingman on 2014-05-31
Make sure your boot order is correct in BIOS by setting the CD/DVD drive first.

---

### Post by neke123 on 2014-05-31
> **codingman said:**
> Make sure your boot order is correct in BIOS by setting the CD/DVD drive first.

I used F11 to select device I wanted to boot HDD is empty,it opens EFI shell.

---

### Post by codingman on 2014-05-31
So, you're saying even Windows does not boot? This is very odd if this is the case, because if even *Windows* isn't working on the computer, then it is probably a hardware issue.

---

### Post by matt_symes on 2014-05-31
Hi

Start by removing all the hardware you can and boot using a LiveUSB.

So remove everything but the graphics card and 1 stick of memory from the motherboard. This includes disconnecting all the drives on the system.

Boot into the BIOS and disable every piece of on board hardware that is not directly required to boot the system so disable onboard sound, networking etc.

Remove all the sticks of memory but 1.

Then try to boot using the LiveUSB.

Does it still crash ?

If it does still crash then please list all the hardware you have disconnected or disabled in the BIOS and list all the hardware that you think is still connected.

Remember, you're trying to boot up with the absolute minimal hardware needed to boot the system.

Kind regards

---

### Post by neke123 on 2014-05-31
> **matt_symes said:**
> Hi

Start by removing all the hardware you can and boot using a LiveUSB.

So remove everything but the graphics card and 1 stick of memory from the motherboard. This includes disconnecting all the drives on the system.

Boot into the BIOS and disable every piece of on board hardware that is not directly required to boot the system so disable onboard sound, networking etc.

Remove all the sticks of memory but 1.

Then try to boot using the LiveUSB.

Does it still crash ?

If it does still crash then please list all the hardware you have disconnected or disabled in the BIOS and list all the hardware that you think is still connected.

Remember, you're trying to boot up with the absolute minimal hardware needed to boot the system.

Kind regards

Disabled ACPI,Onboard LAN controller,HD audio controller,On-Chip IDE and SATA controller,PCI IDE busmaster,CD drive,HDD.

Here is log,pretty much same to me.

[http://m.imgur.com/9diUYXJ](http://m.imgur.com/9diUYXJ)

Can I do anything else?

---

### Post by Joel_Ross on 2014-05-31
> **neke123 said:**
> About hardware,its all new,most of components are few months old but they did work yesterday on old motherboard but not everything crashes.

Are you saying that all your new hardware components work on the old motherboard and not the new motherboard? If so, thats your problem the new motherboard must be faulty. It wouldnt be the first time a new motherboard is faulty. Do you have warranty?

---

### Post by neke123 on 2014-06-01
> **Joel_Ross said:**
> Are you saying that all your new hardware components work on the old motherboard and not the new motherboard? If so, thats your problem the new motherboard must be faulty. It wouldnt be the first time a new motherboard is faulty. Do you have warranty?

Yes it is under 3 year warranty,but everything works expect operating systems.

---

### Post by newbie2244 on 2014-06-01
"Google is your friend" -- -- --> What is kernel panic?


[http://en.wikipedia.org/wiki/Kernel_panic](http://en.wikipedia.org/wiki/Kernel_panic)

[http://en.wikipedia.org/wiki/Assertion_%28computing%29](http://en.wikipedia.org/wiki/Assertion_%28computing%29)

ALso, look up "sync", "init"

"Google is your friend" . . .

BTW, is your system a 32-bit system or a 64-bit system?  Is the software 32-bit or 64-bit??   Did you migrate SW from another (older) system to your new hardware?  Are you in Russia?  

Pls specify your entire system - brand name of computer, 64 or 32 bit, BIOS name and version, brand name of hdd, type of RAM, USb ports 2 or 3, etc.

---

### Post by matt_symes on 2014-06-01
Hi

I also say bad hardware. 

Looks to be the motherboard if that is hardware and is the only major hardware that has changed.

EDIT: The only other thing i think it could be is the power supply.

Kind regards

---

