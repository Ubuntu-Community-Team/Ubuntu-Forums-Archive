---
title: "BIOS error on ASUS A7TC"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by donk on 2009-05-04
Yesterday afternoon I went over to my parents for a few hours as I had been given permission to install ubuntu on my Mum's computer - an ASUS A7TC.

When I installed 9.04 i386 I got a bios error - MP-BIOS bug: 8254 timer not connected to IO-APIC.  I ignored the error and then proceeded to install ubuntu, however it took a long time to boot from the live cd but I proceeded anyway.  Most things were recognised so we decided to dual boot and I went about the installation.  This proceeded well (I went and had lunch!) came back and the pc was running out of hdd space even though I had 50GB to spare.   But everthing that we need seemed to work - nvidia graphics card, sound and wifi which is a biggy because this is how she connects to the internet.

The long and short of my problem is that I searched the internet and found that some people put acpi=off or noapic in the sources.list file - this didn't help me on the installed version or on the live cd.  What I really wanted to do was disable the ACPI HPET Support in the advanced bios or at least try this.  However I could only get into a very basic bios by pressing F2.  I tried every other key combination I could think of, but to no avail.  I spent most of my time at her house researching how to get into the advanced bios - Asus website, forums, etc with no luck.

**So does anyone know how to get into the advanced bios on an ASUS A7TC?**  I even flashed an updated bios onto her laptop-desktop replacement but no luck.  I have tried all the key combinations I could find on the internet but perhaps you guys know better?  I am not seeing my Mum for about a month - this is really galling because I really wanted to free her from MS Windows and the hassle of anti-virus software, etc.  The thing I am really sad about is that I can't ssh into her box in order to help her.

Sorry for such a long rant!

If there is anything else anyone can think of to smooth the installation the next time I see my mum - thanks.

---

### Post by donk on 2009-05-09
Anyone got any ideas?

---

### Post by Elfy on 2009-06-07
> some people put acpi=off or noapic in the sources.list fileHave you tried it using the menu.lst - add it to the kernel line

```
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=25035697-3e97-4899-a5e0-2b724556f6dd ro quiet splash _noapic_
``` for example

---

### Post by donk on 2009-06-07
Thanks for your reply I will try this when I get my hands on my Mum's laptop in a couple of weeks time. 

Do you know how to get into the advanced bios on this system?

Thanks once again.

---

### Post by Elfy on 2009-06-07
Afraid not - but usually you can get to the other bits by using enter. You might be better served by trying to find the mobo manual. It must be out there somewhere I would hope.

Good luck

---

### Post by donk on 2009-06-09
I tried that - I searched the internet but haven't found the mobo manual. I  know the manual my mother has doesn't contain the info #?!? because that was my first port of call when I was at her house. 

I'll keep looking - I would have thought it would have been easy :-) I have got until 21 June 2009 when she is bringing her laptop to my house (we're about 50 miles apart).  

It has been suggested at my LUG that I try mint or pclinuxos which I'll try but I would have thought that mint is a ubuntu based distro and so wouldn't be any different - but I'll try them both.

Thanks again...

---

