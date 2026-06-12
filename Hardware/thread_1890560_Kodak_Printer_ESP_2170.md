---
title: "Kodak Printer ESP 2170"
date: 2011-12-03
forum: Hardware
---

### Post by solarcoy on 2011-12-03
I did not read the incompatibility list before I bought this printer and here I am looking for some driver that might work.  
I downloaded the SourceForge c2esp_23-1_i386.deb file and was able to extract the following .pdd files.  I found a mention that the 2170 was a replacement for the 6150 so I installed the 61XX driver but I'ts not working. I'll try the others but I'm not hopeful. Any ideas? Otherwise it will have to go back to Staples.  

Kodak_ESP_32xx_Series.ppd
Kodak_ESP_52xx_Series.ppd
Kodak_ESP_55xx_Series.ppd
Kodak_ESP_61xx_Series.ppd
Kodak_ESP_72xx_Series.ppd
Kodak_ESP_92xx_Series.ppd
Kodak_ESP_C11x_Series.ppd
Kodak_ESP_C1xx_Series.ppd
Kodak_ESP_C31x_Series.ppd
Kodak_Hero_3.1.ppd
Kodak_Hero_5.1.ppd
Kodak_Hero_6.1.ppd
Kodak_Hero_7.1.ppd
Kodak_Hero_9.1.ppd

---

### Post by bluexrider on 2011-12-03
this is from Kodak

     **Use of all-in-one printer with *LINUX* Operating System**

     Published 08/25/2010 11:38 AM          |            Updated 05/25/2011 07:42 AM          |   Answer ID 1698    
     Can I use my all-in-one printer the with *LINUX* Operating System?
                     
              All-in-one printers do not support *LINUX* OS at this time.

The all-in-one printers are designed to work with WINDOWS XP, WINDOWS  VISTA, and WINDOWS 7 Operating Systems and with MAC OS 10.4.8 or higher.:confused:

---

### Post by solarcoy on 2011-12-03
I've gotten the HERO 9.1 AiO driver from SourceForge.org to run the printer but the scanner doesn't work.  Didn't test the fax.  Requested through customer support that Kodak at least assign someone to work with the SorceForge driver group. It's too bad.  Seems like a nice printer and I really like the idea of low cost ink.  Just the kind of thing linux users would like I think. I'll probably take it back and get the HP for which the ink cost 4X as much.

---

### Post by bluexrider on 2011-12-03
> **solarcoy said:**
> I've gotten the HERO 9.1 AiO driver from SourceForge.org to run the printer but the scanner doesn't work.  Didn't test the fax.  Requested through customer support that Kodak at least assign someone to work with the SorceForge driver group. It's too bad.  Seems like a nice printer and I really like the idea of low cost ink.  Just the kind of thing linux users would like I think. I'll probably take it back and get the HP for which the ink cost 4X as much.

actually this issue has been around for some time. it exists in suse, debian and elsewhere.

I did find the latest kodak ESP printer drivers here form [http://sourceforge.net/projects/cupsdriverkodak/files/](http://sourceforge.net/projects/cupsdriverkodak/files/)

its a kick in the teeth by Kodak not to support Linux. HP, Lexmark and Epson do. 


:confused::confused::confused:

---

### Post by solarcoy on 2011-12-03
A Printer designed to run with Windows?  What happened to drivers?  
I wonder if there is some way I could use the MAC OS driver.

---

### Post by bluexrider on 2011-12-03
yeah! its a shame. I cannot answer the question about the MAC drivers. I know there is ALIEN software that can convert RPM and such to .DEB files but I've not run it. 

happy *Buntu

---

### Post by paulnewall on 2011-12-10
Maybe a little background info for c2esp will help:
c2esp can drive printers with two different command and data formats.
There's the ESP xxxx series. for example ESP 5250
And there's the newer models which can be called ESP Cxxx or Hero x.x
 
The many ppd files just enable the different options, like duplex, photo try etc.
Generally any ESP xxxx printer will print with any ESP xxxx ppd file, and any newer model will print with any ESP Cxxx or Hero ppd file.
 
From it's name, I'd expect ESP 2170 to belong to the ESP xxxx group, but it could be an exception, so you could try one of the Hero ppds.

---

### Post by solarcoy on 2011-12-10
Thanks for your reply.  I did get one of the Hero drivers to print but not to scan. I took the printer back to Staples and brought home a Canon Pixma MX410, downloaded the  and am now in the same situation I was in with printing and no scanning.  I won't have time to dig into it until later this week.

---

### Post by paulnewall on 2011-12-22
You are falling into the trap of thinking that there will be a driver that does everything. I think in general an Aio printer is just a printer and scanner in one box. The box is the only thing they have in common. In linux the software for printing is entirely separate from the software for scanning. So to do scanning you need to find a scanner driver. That will probably be a SANE backend.

---

### Post by tom.davidson58 on 2011-12-25
I just recently got the exact same printer and now I'm having the same problem.  I cannot get it to print.  My machine sees the printer and even tries to print (the printer even responds...  sort of - it feeds the paper halfway and then locks up completely).  The printer works in Windows, but I can't seem to get it working in Ubuntu or openSUSE.  I have tried to install the driver mentioned above from sourceforge but can only find a 32-bit version but my machine is 64-bits.  Any suggestions?

---

### Post by paulnewall on 2012-01-14
There is a deb file for 64 bit here
[http://sourceforge.net/projects/cupsdriverkodak/files/](http://sourceforge.net/projects/cupsdriverkodak/files/)
but it will only drive the ESP xxxx printers, not ESP Cxxx or Hero
otherwise there are ideas for 64 bit here
[http://sourceforge.net/projects/cupsdriverkodak/forums/forum/1107085/topic/3821012](http://sourceforge.net/projects/cupsdriverkodak/forums/forum/1107085/topic/3821012)
 
And there is now a scanner driver - (a compile it yourself one) here
[http://sourceforge.net/projects/cupsdriverkodak/files/Scanning%20-%20sane%20backend/](http://sourceforge.net/projects/cupsdriverkodak/files/Scanning%20-%20sane%20backend/)

---

### Post by paulnewall on 2012-01-14
And I forgot. It seems from a post earlier in this thread that the ESP2170 is like a Hero printer, not like an ESP xxxx printer (confused? - so am I)
 
Paul Newall

---

