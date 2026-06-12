---
title: "nForce 4?"
date: 2006-06-08
forum: Hardware &amp; Laptops
---

### Post by maddog39 on 2006-06-08
Hello all,

I just built a new comp and havn't gotten linux on it yet so I am running XP Pro atm. So I was curious. Well I have several questions actually. I have a Pentium D 3.0GHz Dual Core w/ 64 Bit and an nForce 4 SLI motherboard. Although I am no using SLI I heard that the nForce 4 chipset was highly uncompatible. So I was curious what I should do about sound and networking. I do have a compatible WiFi PCI card and an extra Creative SoundBlaster lying around but is nForce 4 supported at all in Dapper? Also is 64 bit worth it. I want to do some gaming and I dont run many 64 bit apps because I cant ever find them lol.

Thanks!
-maddog39 :D

---

### Post by d.j.schroeder on 2006-06-08
I just installed Dapper on an Asus A8N-SLI board (AMD 939 socket) it also uses Nforce 4 chipset.  It ran fine, mostly.

Immediately found LAN and internet.  The only issue I have is that the built in gigabit ethernet will not operate at full speed, only 100 Mbs.

I am using the 32-bit version even though I also have a 64-bit processor because I was concerned about compatibility reading other linux forums and I don't really need 64-bit for anything I do.

---

### Post by sirclaudio on 2006-06-09
You connected your computer to a gigabit lan (router)? If not, it will automatically switch to 100Mbits...

---

### Post by d.j.schroeder on 2006-06-09
It is connected to a gigabit switch.  The XP boxes on the same LAN are able to transfer between each other at above 100 Mbits.  They don't hit 1000 on file transfers, I think because of hard drive limitations but they are above 300 Mbits.

---

### Post by maddog39 on 2006-06-09
Okay well I am not concerned about gigabit eithernet. I am on a 4.4Mbps cable connection and I dont do any networking. By the way if you installed 64bit edition on ur AMD it wouldnt make much of a difference since AMDs are x86_64 meaning they can simultaniously run 32 and 64 bit modes. However I wasnt sure about intel.

---

### Post by futz on 2006-06-09
[QUOTE=maddog39]and an nForce 4 SLI motherboard. Although I am no using SLI I heard that the nForce 4 chipset was highly uncompatible. So I was curious what I should do about sound and networking. I do have a compatible WiFi PCI card and an extra Creative SoundBlaster lying around but is nForce 4 supported at all in Dapper?[/quote]
Here is my Ubuntu machine. Dapper runs great on it. Everything works fine, including both LAN connections and onboard sound. The wireless card is just in there for my amusement. I use it occasionally, for no good reason (because it's there):
1 - DFI LANPARTY UT nF4 Ultra-D Mainboard
1 - OCZ EL Platinum REV.2 (TCCD) PC3200 1GB 2X512MB DDR CL 2-2-2-5
1 - Athlon 64 X2 4200+ Dual Core
1 - WD360GD 36GB Raptor HD
1 - WD740GD 74GB Raptor HD
1 - Maxtor 250GB 7200RPM 16MB SATA-2 HD
1 - Benq DW-1640 DVD Writer
1 - Old Toshiba DVD-ROM
1 - MSI NX6600GT-TD128E 128MB PCI-E w/Video-in TV &DVI
1 - Gigabyte Wireless LAN Card (came with a Gigabyte mainboard)
1 - Enermax 460W w/Dual Cooling Fan power supply
1 - Antec Super Lanboy case

> Also is 64 bit worth it.
In my opinion, no. Not yet.

---

