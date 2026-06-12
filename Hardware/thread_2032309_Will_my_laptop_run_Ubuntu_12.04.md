---
title: "Will my laptop run Ubuntu 12.04?"
date: 2012-07-23
forum: Hardware
---

### Post by ShivaIsLord on 2012-07-23
HP Pavilion g4-1318dx
Microprocessor	2.10 GHz Intel Pentium Processor B950
Microprocessor Cache	2MB L3 Cache
Memory	4GB DDR3 SDRAM (1 DIMM)
Memory Max	Maximum supported = 8GB
Video Graphics	Intel HD Graphics
Video Memory	Up to 1696MB total graphics memory
Hard Drive	320GB 5400RPM hard drive
Multimedia Drive	SuperMulti DVD Burner
Display	14.0-inch diagonal HD BrightView LED-backlit display (1366 x 768)
Network Card	10/100BASE-T Ethernet LAN (RJ-45 connector)
Wireless Connectivity	802.11b/g/n WLAN
Sound	SRS Premium Sound with Altec Lansing speakers
Keyboard	Full-size keyboard
Pointing Device	Touchpad with on/off button

---

### Post by sammiev on 2012-07-23
Looks like it should. Burn a boot-able CD/DVD/USB and try 12.04 live. Then you will know. :)

---

### Post by vasa1 on 2012-07-23
> **ShivaIsLord said:**
> HP Pavilion g4-1318dx...
Two points.
Is it UEFI?
Do you want to dual-boot?

---

### Post by ShivaIsLord on 2012-07-24
> **sammiev said:**
> Looks like it should. Burn a boot-able CD/DVD/USB and try 12.04 live. Then you will know. :)

I tried, but it won't.  When I run ubuntu from the live USB, it just goes to a black screen.  I tried editing boot parameters (acpi=off and noapic), but then it would just boot to a terminal screen.

Edit: By the way, this is both 64 and 32 bit.  I tried both.  64 bit would be my choice, since I have a 64 bit processor and 4GB or ram. 

> **vasa1 said:**
> Two points.
Is it UEFI?
Do you want to dual-boot?
No, it has BIOS.
I don't know.  At first, yes, to make sure it all works.  Later, no, I want to remove Windows.

---

### Post by sammiev on 2012-07-24
Have you tried running it in "nomodeset" yet? Pls give it a try a post back.

---

### Post by ShivaIsLord on 2012-07-25
> **sammiev said:**
> Have you tried running it in "nomodeset" yet? Pls give it a try a post back.

nomodeset has worked.  I am posting this from the live USB.  Things seem to be working so far.  I have found one annoyance, though.  Whenever I click on something, the mouse goes invisible on me.  It shows up again when I move it around, but it's just a little annoying.  Is there a fix for this?

Also, on the topic of nomodeset, are there anythings I should be concerned about?  For example, with acpi=off, you do not want to keep it that way for a long time because it turns off vital functions such as the fan.  Is there anything I should know about nomodeset?  What exactly does it do?  

Thanks so much for your help, I really appreciate it.  :)

I'll just play around for a little bit on here and see if I can find anything else that doesn't work.  If not, it's bye bye Windows.

---

### Post by sammiev on 2012-07-25
Your likely good to go then and for the mouse, there maybe an update for it. You will find when you install that there will be many updates. Nomodeset is used for some video cards.

---

