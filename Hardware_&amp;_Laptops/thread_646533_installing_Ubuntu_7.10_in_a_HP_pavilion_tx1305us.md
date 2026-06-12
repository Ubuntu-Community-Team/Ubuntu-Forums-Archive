---
title: "installing Ubuntu 7.10 in a HP pavilion tx1305us"
date: 2007-12-21
forum: Hardware &amp; Laptops
---

### Post by adrialyra on 2007-12-21
I have a notebook HP Pavilion tx1305us with the configuration bellow.
I'm really in need oh help. It came with Vista installed, and it is just impossible to work with Vista, besides I need Linux to work!!! I've more than 40hours tying to install Suse 32 and 64, Debian 32, and Ubuntu 32 and 64, with no success...

Ubuntu 7.10 32 did not even enter the install screen, but ubuntu 64 entered the install screen and I did as I read in the forums around the Internet. Pressed F6 and in the** Boot Options **I typed **noapic nolapic irqpoll** and the screen was frozen just in the same way when I didn't type anything and just let the installer go with the default definitions!

Best reagrds to you all,
Adria
  	
[COLOR="Blue"]Processor
	  	AMD Turion 64 X2 Dual-Core Mobile Technology TL-58; 1.9GHz
  	
  	
Memory
	  	1024MB DDR2 SDRAM
  	
  	
Graphics
	  	Nvidia GeForce Go 6150 (UMA) with up to 287MB total available graphics memory
  	
Communications
	  	Integrated 10/100 Base-T Ethernet LAN (RJ-45 connector)
  	
Broadband wireless
	  	802.11b/g wireless LAN
  	
Primary CD/DVD drive
	  	LightScribe Super Multi DVD+/-RW with Double Layer Support
  	
Hard disk drive(s)
	  	160GB (5400RPM) SATA Hard Drive [gigabyte is defined as 1,000,000,000 bytes, accessible 
  	

PCI expansion
	  	Notebook expansion port 3
  	
I/O ports
	  	3 Universal Serial Bus (USB) 2.0, 2 Headphone out, microphone-in, VGA, TV-Out, RJ-11, RJ-45, notebook expansion port 3, 2 Consumer IR (1 on notebook and 1 on panel)
[/COLOR]

---

### Post by adrialyra on 2007-12-21
I Forgot to say that I did the partition using the Vista partitioner, since partition magic (the one I used to partitioner all my previous laptops, doesn't work with Vista)

To boot I also tried this:  A) Booting into the LiveCD
If boot hangs or fails, reboot. At the menu press F6 and add these parameters:

Code:
noapic irqpoll noirqdebug

But anything worked till now!!! I'm 2 weeks without workig because of it... Don't nkow what to do anymore... Think I'm going to sell this notebook and buy another one!!!

---

### Post by adrialyra on 2007-12-21
](*,)

---

### Post by adrialyra on 2007-12-21
Can anybody help me?
I just saw in another topic to write in boot options only noapic!
But it didn't work...
](*,)

---

### Post by adrialyra on 2007-12-23
Also tried on the boot options:
noapic nolapic noapci noirqpoll nosmp

But still have no sucess!!!

---

### Post by Sef on 2007-12-23
1) Can you run the Live CD?

2) Did you md5sum the download? (to check the download is ok.)

3) Did you burn the cds at 4x or less? (Faster can corrupt the iso.)

4) Did you check the disk?  (Instead of start/install ubuntu go down the list.)

---

### Post by Elucida on 2007-12-23
> **Sef said:**
> 1) Can you run the Live CD?

2) Did you md5sum the download? (to check the download is ok.)

3) Did you burn the cds at 4x or less? (Faster can corrupt the iso.)

4) Did you check the disk?  (Instead of start/install ubuntu go down the list.)

Just quoting to repeat that you may need to check your disk.

As for all the boot options **noapic irqpoll noirqdebug** works for me using the exact same laptop; with both the i386 and amd64 ubuntu versions.

---

