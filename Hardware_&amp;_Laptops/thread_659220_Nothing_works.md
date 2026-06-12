---
title: "Nothing works"
date: 2008-01-05
forum: Hardware &amp; Laptops
---

### Post by Volpix on 2008-01-05
I installed Ubuntu 7.10 with the noacpi option. 

The sound board is a Analog Devices AD1988 @ nVIDIA MCP61, and the network adapter is NVIDIA nForce (192.168.250.2).

The mother board is a Asus M2N. How do I install the sound board and the network adapter? I use a router connected directly in the computer, without the network adapter It doen's work :(

---

### Post by shad0w_walker on 2008-01-05
Both of those devices should be supported out of the box. I have the MCP55 and they were supported straight of the box.

---

### Post by Volpix on 2008-01-05
Ah, ok. So, whi I can't listen musics and connect to internet? Maybe because the noacpi option? My DVD-ROM Drive is not suported on ubuntu I think. It's a HL-DT-ST DVDRAM GSA-H44N ATA Device, from LG.

Please help me :(

---

### Post by shad0w_walker on 2008-01-05
I just reread your original post. I managed to miss the noapci option you mentioned. I would suggest you check around for a BIOS update. I had to use noapic due to a bug in the factory shipped BIOS, updating fixed it up nicely and I could get rid of the noapic option.

---

### Post by Volpix on 2008-01-06
If I don't use the noacpi option, It says "The timer is not connected do ACPI, but with the no acpi It works. I will try to upgrade the BIOS :)

---

### Post by Levander on 2008-01-06
I'm having the same problem.

I just upgraded to the 0804.ROM file on Asus's web site.  There was also a M2N-MOTHERBOARD-0804.ROM file in the same zip file that I downloaded.  They were the same size, so I just assumed they are the same file...  I actually called Asus and the idiot I got on the phone said just to use the smaller of the two files, and he emphasizes.   I asked what the other one was and he said he didn't know, but he empathizes...  Idiot.  So, I look at them and their both the same size.  I call back and I get a message saying the Asus offices are closed...

I'm getting the same "Timer doesn't work" problem on the new motherboard even after upgrading to the 0804 BIOS.  

The 0804 BIOS is listed as beta.  Think I'm going to go to the 0803 BIOS that wasn't listed as beta.  I'm guessing the next step after that is returning the motherboard though.

I haven't tried the noacpi option.  With the noapic option, I am getting the computer to boot, but the network card isn't working.  I haven't tried the sound card yet.  noacpi and noapic are two separate options that you can pass to the kernel.  Both are valid options.  No idea the difference between the two.

---

### Post by Levander on 2008-01-06
I actually have a kink in my stuff here.  I had Linux installed on a computer before I built this one.  I tried just moving the hard drive into this new one and booting in without reinstalling, where I got the same problems as the original poster.

However, when I boot from the Mythbuntu LiveCD, I have to use the noapic option to get past that "IO APIC timer doesn't work" error.  However, when using noapic, my network card is now working.

There was some thing where when I was using the 0804 BIOS that upon booting the Mythbuntu LiveCD I had to "sudo /etc/init.d/networking restart" to get it working.  But now, with the 0803 BIOS in my M2N motherboard, the network card is working right off of boot.

And yes, even now that I've flashed to the 0803 M2N BIOS, I am still having to use the noapic kernel option to get it to boot.

I wonder what I'm losing using noapic as a kernel option?

---

### Post by Levander on 2008-01-07
Well, I'm wondering if Volpix is still interested in this thread or not.  I'd like to see what you find.

I just did a fresh install of Mythbuntu on that system.  Putting noapic in grub's menu.lst file, it boots fine.  The network card, sound card, and everything else I've tested run fine.  

I am running the 0803 BIOS for the M2N motherboard.

But, now I'm trying to decide if I should return this motherboard or just put up with having to use the noapic option.  I have no idea how much performance I'll lose using noapic even though I've asked in several places.

Plus there's the concern that because I do have to use noapic that this board isn't well supported under Linux.  I've had issues in the past where when I dist-upgrade I've lost a network card or a sound card.  I really don't want to lose my motherboard to a dist-upgrade.

From what I've read this is a problem with the motherboard's BIOS, but that doesn't seem a definitive answer.  I've seen mentions of what are at least "work arounds" in the kernel for this issue.  If I knew one or the other would be fixed in the near future, it wouldn't be an issue for me.  But of course you can't really know that, so I've got to guess whether or not to return this motherboard...

---

