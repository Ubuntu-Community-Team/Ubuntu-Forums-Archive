---
title: "Mystery ARM926 7&quot; netbook - need help researching it"
date: 2010-01-03
forum: Hardware
---

### Post by egrep on 2010-01-03
A few days ago my local laptop repair place showed me what I thought was an eee pc 7". I grabbed it yesterday and it turns out to be something else. Could be really promising methinks, don't know for sure. I currently runs embedded Windows CE.

o AKARM ARM926EJ-S [sysinfo says ARM926-AKCHIP] 248Mhz
o Windows says 800x480 resolution, but google tranlations of some csdn.net forum pages says maybe 1066x600 in native lcd mode.
o Going into the audio player reveals thet the OEM info is: Anyka AK780x. This is what led me to csdn.net and dicussions of the Anyka dev kit [much like the sheevaplug dev kit].
o Has 2 usb 2.0 ports, one port labeled USB which is not 2.0 and could be the JTAG interface to the proc.
Has ethernet and wireless. No video out. SD memory slot that is "supposed" to be where the user stores data.

I guess it is like a overgrown mobile phone with a full sized keyboard. Retail was US $135. Store owner says if he could oder "enough" [that would be 30-40 in this town], the price could be down in the $80+ range.

Is this worth messing with? I cannot find squat on ARM926 except dev boards of various flavors.

Worst part? As it goes through POST, it says "hit F1 to update system". When you do it asks for a password. No one knows what it is. Random shipment bought at auction maybe? I have tried resetting in various fashions to see if I can get console access via the mystery usb port, but all I have accomplished is to have it ignore me now when I try to hit F1 ;-[ Guess I tried the password too many times... oops.

--egrep

---

### Post by egrep on 2010-01-03
Here is what I have tried besides not outsmarting the bios.
o Tried making Fat16 USB boot stick - zip
o Tried booting off of a remix install on an SD card - nada
o Built a FAT16 SD card iso installer - again, nope

It just won't look anywhere but the write protected 2GB flash disk. I _do_ have the option of formatting these, so since I have bricked it anyway, this might be the next thing to try ;-]

I will take pics and post them on picasaweb. It is a cute little thing...

--egrep

---

### Post by garryknight on 2010-01-03
> **egrep said:**
> I have tried resetting in various fashions

What have you tried? Is there a reset hole (usually on the back or the side)? Is the battery removable, and if so, have you tried removing it for 10 minutes or so? Is there a CMOS battery on the PCB?

---

### Post by snailmf on 2010-01-12
Try ZTK as password for F1 setup.

I haven't been able to get an ip with dhcp. So the thing is useless for me.

---

### Post by tlk23 on 2010-01-15
You likely have an Lan Yu EBook (LY-EB01) or some version of it. (Me too).There are a number of 7" netbooks on the market right now, most of which use the same case, but have different processors.
 
The 7" Netbooks sold with LINUX seem to all be running MIPS processors (quite a bit different from the ARM-based processor in the the eb01).
 
There is another thread ([http://ubuntuforums.org/showthread.php?t=1349626&highlight=cnmbook](http://ubuntuforums.org/showthread.php?t=1349626&highlight=cnmbook)) currently discussing running linux on the version of this netbook that runs the ARM-based Via VT8500 processor.  That netbook and the EB01 are not EXACTLY the same.  But whatever they discover will provide some clue to what can be done.
 
If your computer is bricked, you might try the recovery procedure at [http://www.cnmlifestyle.com/](http://www.cnmlifestyle.com/)
 
([http://194.150.201.35/cnmlifestyle/cnmbook/CnMNB7SEsupport.htm](http://194.150.201.35/cnmlifestyle/cnmbook/CnMNB7SEsupport.htm))
 
I believe the CnMbook Silver (Windows CE) is the same computer as ours.    I suspect the other CnMbook (Linux) uses a different (MIPS-based) processor and that the linux firmware won't work on our computers.
 
 I haven't tried the recovery procedure on my own computer, as I don't have the right USB cable.  So I can't say whether it will work, or just make matters worse.
 
Good luck.

---

### Post by Shabadage on 2010-01-16
I have one of these too.  It's kind of peculiar though.  Mine came in a package similar to the CnM Book.  It however only has 2 GB of Flash, and a "normal" as far as I can tell ARM processor.

Let me boot it up now.

ARM926EJ-S 248Mhz

DPOI
Lan
Serial
SPI 
Backlight
Touchpad
PCL
USB374

Properties under "My Computer" reveal this
Microsoft?Windows?CE
Version 5.00 (Build 1400)

Processor Type: AKARM, ARM926-AKCHIP


More telling is the USB Boot jumper.  Open your battery compartment and carefully remove the battery.  About 1.5 CM to the Left, you'll see something labeled USB_BOOT.  Judging from the CnM instructions, you'd need to short this connection to get a USB Boot.  Not sure if it will attempt to boot from SD in this manner.  I'll have some (bad) pictures up later tonight.

This is coming completely out of left field, but I remember a boot loader I had to use to get jLime running on an old HP 6xxx series.  It ran from within CE.  Might be worth looking into.

[http://www.jlime.com/mw4/index.php/Main_Page](http://www.jlime.com/mw4/index.php/Main_Page)

Also I have a blog where I'm posting all sorts of information/software compatibility on these style netbooks at shabadage.blogspot.com .  Just because there really isn't a main source of information about these type of netbooks.  Any info you guys could provide about your configurations would be extremely helpful.

---

### Post by tlk23 on 2010-01-16
Here are some details about my computer:
 
----
Boot messages:
 
Version:1.90
Hardware Version:3.0
CPU: ARM 926EJ-S 248MHz
Release SV122
RAM: 128M
Video decode:1
 
Press F1 key to update system
 
----
 
System properties (reported by Windows CE)
System:
Microsoft?Windows?CE
Version 5.00 (Build 1400)
 
Computer
Processor Type: AKARM, ARM926-AKCHIP
Expansion Slots:
Memory 128M
 
----
 
System Specs:
Processor: ANYKA AK7802TQ21605
NAND Flash: K9GAG08U0D  (2GB)
Ethernet Controller: Davicom DM9008AEP
Wireless NIC: Prolink RT2070L  (Realtek RT2870 clone?)
 
 
Number on Motherboard:  ZT_NT670_V88_FPC_1018
 
I've attached two pictures of the motherboard

---

### Post by PC-Geek on 2010-01-29
Have one of these cute little machines. I was not even 30 days old and the keyboard quit. Nothing. (No, didn't spill coffee, coke, tea or milk in it)

Looking for the service manual, or tips to take it down and change the keyboard.

And, where to get a keyboard.  Any in the states? or do I have to go to China.  No branding on it, so not sure if it is an LY-EB01, or CnMbook.  No model, nothing.  System info shows what was mentioned earlier in the blog.

---

### Post by tlk23 on 2010-01-29
To remove the keyboard, first remove the two screws adjacent to the label on the bottom of the case. (one of the screws may be covered by a round sticker, mine was.).  There are four tabs along the top of the keyboard that need to be pressed in to release the keyboard.  They are above the esc key, between f4 and f5, between f9 and f10 and above the delete key.  The keyboard is attached to the mother board with a ribbon cable, perhaps yours has just come loose.

Complete disassembly instructions are here -> [http://ubuntuforums.org/showpost.php?p=8649958&postcount=131](http://ubuntuforums.org/showpost.php?p=8649958&postcount=131)

I'd be surprised if you found replacement parts anywhere for one of these computers.

Good luck

---

### Post by PC-Geek on 2010-01-30
Thanks so much for the link and info.  I see the tabs now.  Label on the bottom?  WOW, yours had a label? No label, no markings, no info at all on the unit.  Found this on matching processor and screen.  Will work on the keyboard today.  I'll post what I find out.

---

### Post by PC-Geek on 2010-01-30
Keyboard update on the mystery box.

Pulled keyboard, removed and reconnected ribbon cable.  Got a good seating on connection, but alas, still a keyboard that makes no input on anything.  Rest of the machine works fine, and when need characters can use the little virtual keyboard to put in websites, but no keyboard.  I've looked for a 'keyboard on/off button in Win CE but couldn't find one.  Not being a Windows CE user, didn't know if there was such a thing.  Nothing to test keyboard with either to see if it is keyboard or mobo.

---

### Post by darthmill on 2010-02-07
I`ve picked one of these 7" netbooks running win ce 5 which is crap need ubuntu on it , has any one done it and does the usb boot thing work.


Julian

---

### Post by nlsantos on 2010-02-10
good friends I have a netbook with these characteristics and formatted the disk inadvertently XIP now the notebook does not start how do I LiveCDs the new XIP disk I tried with the usb cable but failed 13 seconds ha any way to install all over again is who do not find anything on the net.
tanks
 
help

---

### Post by kshade on 2010-02-14
> **tlk23 said:**
> If your computer is bricked, you might try the recovery procedure at [http://www.cnmlifestyle.com/](http://www.cnmlifestyle.com/)
 
([http://194.150.201.35/cnmlifestyle/cnmbook/CnMNB7SEsupport.htm](http://194.150.201.35/cnmlifestyle/cnmbook/CnMNB7SEsupport.htm))

I tried that out with mine but it didn't work, the flash tool fails with "fail to init usb", just like [this guys]("http://translate.google.de/translate?hl=de&sl=es&tl=en&u=http%3A%2F%2Fwww.todoumpc.com%2Fforum%2Fforum_posts.asp%3FTID%3D11044%26PID%3D104079").

---

### Post by radu.moisan on 2010-02-25
Hello there, I'm a new one among you guys. I just bought such kind of device an looking forward to boot some flavor of Linux on it. I'll continue to dive with my friend Google on this matter and keep you in the loop. Hope I'll find something usefully about this gadget.

---

### Post by radu.moisan on 2010-02-25
entered twice the same, sorry

---

### Post by dhay on 2010-02-28
ey Hello!

Is there any new about linux in this netbook? 
I read this:
[http://www.mandriva.com/enterprise/en/company/press/mandriva-joins-arm-connected-community](http://www.mandriva.com/enterprise/en/company/press/mandriva-joins-arm-connected-community)

and this: [http://tails92.sepwich.com/easypc_linux/](http://tails92.sepwich.com/easypc_linux/)

But this VT8500 is not our netbook.

Do you think it would run?

regards,

dha

---

### Post by radu.moisan on 2010-03-01
Hello guys,
At this point I'm trying to dissect the Windows installation the it has on it and see if it's possible to isolate some drivers. I'm thinking, maybe it is possible to port somehow the BSP  drivers (maybe as black boxes). If this is achievable, than any distribution of linux may be in theory ported on these king of devices. Good luck with your findings ;)

---

### Post by openanky on 2010-03-02
> **radu.moisan said:**
> Hello guys,
At this point I'm trying to dissect the Windows installation the it has on it and see if it's possible to isolate some drivers. I'm thinking, maybe it is possible to port somehow the BSP drivers (maybe as black boxes). If this is achievable, than any distribution of linux may be in theory ported on these king of devices. Good luck with your findings ;)
 
if you have an mini netbook with cpu of "AKARM 926EJ-S AKCHIP" ,you are lucky. now i have some important docment to share for you, yes,it is about BSP and BCPA and all source code, 
you can read it and understand 
HOW to port linux, HOW to burn OS,
HOW to enable H.264, H.263, RMVB hardware video codec,
HOW to increase battery life
.... 
**we open a Project**-**Open Forum** on this page [http://mininetbooks.your-board.com]("http://mininetbooks.your-board.com/") 
 
Happy Play,geeks. [IMG]http://illiweb.com/fa/i/smiles/icon_biggrin.png[/IMG] 
 
I nearly forgot:
[http://rapidshare.com/files/357834038/zt-n760_with_ANKY.rar](http://rapidshare.com/files/357834038/zt-n760_with_ANKY.rar)

---

### Post by softdurga on 2010-03-28
i buy one net book arm 926ej version 1.90 . due to my ignorence i press formatte on nand drive no prob is only loading image .........any healp

---

### Post by anjers on 2010-04-23
Are these mini netbooks really worth paying $80-98 for one?

---

### Post by bgloudon on 2010-06-28
[hi
I have this netbook that does nothing the os is wince .....iwant to change to linux here is some info please help [http://www.arm.com/community/software-enablement/linux.php](http://www.arm.com/community/software-enablement/linux.php)

---

### Post by sterken64 on 2010-12-19
----
 
Computer
Processor Type: AKARM, ARM926-AKCHIP
Expansion Slots:
Memory 128M
 
----
 
System Specs:
Processor: ANYKA AK7802TQ21605
NAND Flash: K9GAG08U0D  (2GB)
Ethernet Controller: Davicom DM9008AEP
Wireless NIC: Prolink RT2070L  (Realtek RT2870 clone?)
 
 
Number on Motherboard:  ZT_NT670_V88_FPC_1018
 
----------------------------------------------------------------------

ZT_NT670 is a notebook from [www.zenithink.com](www.zenithink.com) .
I have one as well !
There is no recovery from zenithink, but due to lack in support for this notebook i debricked my notebook with software from cnmbook windowsCE version 1.63
Works like a charm !

some things are important if you want to reflash your notebook.
Get a good shielded USB male-male cable.
Use the driver provided in the zip file.
read the manual very carefull !

when you reflashed your notebook back to life, then download MIO version 3 (not version 4, because this is for touchscreens)
this gives the winCE a supergoodlooking skin and additional CE gadgets and software!

Here are the links:

[http://www.cnmlifestyle.com/](http://www.cnmlifestyle.com/)
Goto support and choose CnMbook silver 7"
choose version 1.63 ( this works for this notebook)
download the manuals and relevant stuff.

[http://www.gpspassion.com/forumsen/topic.asp?TOPIC_ID=136798](http://www.gpspassion.com/forumsen/topic.asp?TOPIC_ID=136798)
This is the link for mio 3.0
I use R59, and this works very well.

So good luck with your notebook.

Greeting from the dutch guy

---

### Post by banderkin80 on 2011-02-09
> **sterken64 said:**
> ----
 
[http://www.gpspassion.com/forumsen/topic.asp?TOPIC_ID=136798](http://www.gpspassion.com/forumsen/topic.asp?TOPIC_ID=136798)
This is the link for mio 3.0
I use R59, and this works very well.

So good luck with your notebook.

Greeting from the dutch guy

Give step-by-step instruction for dummie how to unstall mio 3 to this netbook. Did u use installing from sd card or the second method ?

---

### Post by Gillyl on 2011-04-22
I have one of these little CnMBooks but pwer pin has come away and I would like to know how to resolder it back to the motherboard please. A diagram/photo would help me.

---

### Post by Gillyl on 2011-04-22
Sorry forgot to mention that the CPU is a ARM920if that makes any difference

---

