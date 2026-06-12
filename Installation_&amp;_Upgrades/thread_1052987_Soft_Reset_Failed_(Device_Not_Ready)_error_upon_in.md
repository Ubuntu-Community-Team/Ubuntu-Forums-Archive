---
title: "Soft Reset Failed (Device Not Ready) error upon installing Ubuntu, Please help!"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by Gp. on 2009-01-28
Hi all,
My system is:
Gigabyte EP45 DQ6 Motherboard
Nvidia 8800GTS 640mb Graphics Card
4GB Corsair Ram
Intel Core 2 Duo 2.2ghz

I boot into the DVD, choose "Install Ubuntu", and after the loading bar does it's thing, I'm presented with this screen and errors saying: Soft Reset Failed (Device Not Ready)

It's nothing to do with the Hard Drive brands I'm using. I've tried both Seagate and Western Digital of different capacities and I've tried booting without a Hard drive to install ubuntu. Same errors everytime.

Please let me know what to do! I can't figure it out.

[IMG]http://i307.photobucket.com/albums/nn297/KyleGP/IMG_2343.jpg[/img]
[IMG]http://i307.photobucket.com/albums/nn297/KyleGP/IMG_2341.jpg[/img]

---

### Post by Gp. on 2009-02-07
and people wonder why Windows dominates.
I can't even install Ubuntu!

---

### Post by ghettofreeryder on 2009-02-07
You need to burn the disc as DAO, not TAO.  Once you do this, it will work.  What burning software are you using?

---

### Post by Gp. on 2009-02-19
I think I used Imgburn or something....

What should I use, and how do I burn as DAO?

---

### Post by loser72555 on 2009-02-21
> **Gp. said:**
> and people wonder why Windows dominates.
I can't even install Ubuntu!

It is because windows was made for morons.  A chimpanzee could install Ubuntu...., well, at least a fairly bright chimpanzee.

Stick with an OS that is designed for your IQ.  Enjoy those licensing fees while you are at it, ok?

PS, if you don't want flames, then don't interject mindless confessions of your own idiocy and incompetence into a technical discussion, and then pretend that this is a denigration of an OS

---

### Post by loser72555 on 2009-02-21
> **ghettofreeryder said:**
> You need to burn the disc as DAO, not TAO.  Once you do this, it will work.  What burning software are you using?

Actually, the issue is not one of DAO.  I burned a copy of another version of linux (MEPIS).  Of course I burned it DAO.  I was able to install the system completely.  The system goes past CMOS and begins to boot Linux, and then I get the above error msg.  However, the system will go ahead and boot.

I think this is a kernel issue with ATA drives, but I am researching it.  It should not be a death sentence to booting or installing, though.

---

### Post by Gp. on 2009-02-21
Fixed it!
I turned off Sata/IDE in bios for this motherboard.

---

### Post by Gp. on 2009-03-01
Hmm but if I re-enable the IDE controller it won't boot, giving me these messages.

---

### Post by Gp. on 2009-04-10
Anyone know? bump!

---

### Post by Stoodle on 2009-04-11
Windows dominates because Bill Gates is great at marketing and shoved it down people's throats. Also, Linus Torvalds doesn't give a crap if the world is in love with Linux or not.

---

### Post by lavinog on 2009-04-11
I get a similar message.
I used to have just a sata hd and an ide dvdrom...I would get a ata1 softreset failed message immediatly at boot.
Now my dvdrom drive is a sata drive and I get a message for both ata1 and ata2
Other than than everything seems fine.
I am using a Gigabyte GA-MA78GM-S2H rev1.0 (ati 780 chipset)

---

### Post by oakTree26 on 2009-04-26
I get the same message. After I updated from 8.10 to 9.04 I first get the 'ata1 softreset failed' message, then the whole boot up process turns to custard and I'm left with a patches of colour on my screen, and with me not being able to boot at all. I get the same softreset message when using a LiveCD, even though it at least lets me boot up the computer.

Does anyone have an idea what this is all about? Should I reinstall 9.04 from the CD?

---

### Post by mactece on 2009-04-26
Also getting the same thing. I'm glad I've got two computers! 

Have also booted with the older kernel and still get the custard but not the message about soft resets. I can boot to the terminal in recovery mode and see the world from there so I'm thinking its some kind of graphics problem.

---

### Post by luvr on 2009-04-26
Nothing to worry about: It's caused by a workaround for a hardware bug in certain AMD chipsets.
See, e.g., the thread [*"Is this startup error important: ata1: softreset failed (device not ready)"*]("http://ubuntuforums.org/showthread.php?t=1052912"); specifically, [*Post #17*]("http://ubuntuforums.org/showpost.php?p=6990421&postcount=17") there. The post refers to source file [*"ahci.c"*]("http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.26.y.git;a=blob_plain;f=drivers/ata/ahci.c;hb=HEAD")--which includes the following comment:
```
	/*
	 * Soft reset fails on some ATI chips with IPMS set when PMP
	 * is enabled but SATA HDD/ODD is connected to SATA port,
	 * do soft reset again to port 0.
	 */
```

---

### Post by mactece on 2009-04-26
If you are not able to boot because the login screen is custard (see above) it does seem to be an ATI graphics problem and you may like to read this thread

[http://ubuntuforums.org/showthread.php?t=1133931&page=3](http://ubuntuforums.org/showthread.php?t=1133931&page=3)

I couldn't get 9.04 to boot after upgrade but I could boot into recovery mode and start a netroot session. Then I followed 
I followed this advice which got me into a normal session. 


> **Muchacho_Gasolino said:**
> 
```
sudo apt-get remove xorg-driver-fglrx
```



I then reinstalled the proprietary driver and all seems to be ok now. However I haven't tried to do anything fancy yet. I'm running a gigabyte mobo with 780 chipsey and built in HD3400 graphics, btw.

---

### Post by Gp. on 2009-05-12
Is there any light on this situation at all since 9.04? it still occurs.

---

### Post by lavinog on 2009-05-12
> **Gp. said:**
> Is there any light on this situation at all since 9.04? it still occurs.

It still occurs, but as said by luvr, it doesn't look like an error, but a debug message.
I wouldn't worry about it.

---

### Post by Gp. on 2009-05-14
Well I have to worry about it because I can't boot into Ubuntu!
These messages show up and that's it. It just stays on that screen.

---

### Post by luvr on 2009-05-14
> **Gp. said:**
> Well I have to worry about it because I can't boot into Ubuntu!
These messages show up and that's it. It just stays on that screen.

A few questions, just to recapitulate:
[LIST]
[*][This web page]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2831") shows your motherboard, right?
[*]The *"softreset"* failure messages appear, and won't go away? Nothing visible happens after that?
[*]If you disable the IDE interface, then the system **will** boot Ubuntu normally (apart from the *"softreset"* failure messages)?
[*]What type of RAM is installed into your computer (e.g., 4x1GB, or 2x2GB, and what speed)?
[*]The motherboard product overview mentions something about *"ATI CrossFireX"* support. I'll admit that I have no idea what that means, but the following note draws my attention:
> In case of unable to get Crossfire Technology working normally, please make sure to use ATI graphic cards that have hardware Crossfire bridge.
Since you say that you're using an nVIDIA, instead of an ATI, graphics board, I guess that means that *"CrossFireX"* won't work. Do you happen to know if there's any way (most likely through BIOS setup) to disable it?
[/LIST]

---

### Post by lavinog on 2009-05-15
Does the live cd work?

do you know how to disable the splash screen and enable verbose output?

---

### Post by Gp. on 2009-05-15
> **luvr said:**
> A few questions, just to recapitulate:
[LIST]
[*][This web page]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2831") shows your motherboard, right?
[*]The *"softreset"* failure messages appear, and won't go away? Nothing visible happens after that?
[*]If you disable the IDE interface, then the system **will** boot Ubuntu normally (apart from the *"softreset"* failure messages)?
[*]What type of RAM is installed into your computer (e.g., 4x1GB, or 2x2GB, and what speed)?
[*]The motherboard product overview mentions something about *"ATI CrossFireX"* support. I'll admit that I have no idea what that means, but the following note draws my attention:

Since you say that you're using an nVIDIA, instead of an ATI, graphics board, I guess that means that *"CrossFireX"* won't work. Do you happen to know if there's any way (most likely through BIOS setup) to disable it?
[/LIST]

That is my motherboard. The ram is 800mhz, 4gb.
The problem goes away if I disable the IDE interface.
If its enabled, those messages appear and nothing else happens after.

Ati Crossfire has nothing to do with the issue I assure you. It's definately the IDE part of this motherboard.

---

### Post by Gp. on 2009-05-15
> **lavinog said:**
> Does the live cd work?

do you know how to disable the splash screen and enable verbose output?

Live Cd does not work.
And these errors appear if I install Ubuntu then turn the IDE back on in the bios.

Simply, I don't think Ubuntu likes the IDE controller for this motherboard....

---

### Post by lavinog on 2009-05-15
> **Gp. said:**
> Live Cd does not work.
And these errors appear if I install Ubuntu then turn the IDE back on in the bios.

Simply, I don't think Ubuntu likes the IDE controller for this motherboard....
when you boot into grub: highlight the ubuntu boot listing (you might have to press esc first if it says to), press 'e' to edit it, then select the kernel line and press 'e' again.
Change 'quiet splash' at the end of the line to 'verbose'
press esc, then 'b' to boot.
Let us know if it gives you any other information.

---

### Post by luvr on 2009-05-19
Would it be possible for you to try and boot from a **Slackware** CD?

See [The Slackware Linux Project: Get Slack]("http://www.slackware.com/getslack") to download it; you need only the Slackware 12.2 Install CD 1 (*"slackware-12.2-install-d1.iso"*).

Boot from the CD, and at the
```
boot:
``` prompt, just hit the *<ENTER>* key. See if that gets you to the login prompt. If it doesn't, then it may be a question of passing the appropriate kernel parameters (which the Slackware CD allows you to type at the *"boot:"* prompt). Of course, we will still have to find out what *"the appropriate kernel parameters"* really are, but let's take this one step at a time...

---

### Post by sonofusion82 on 2009-05-23
> **mactece said:**
> If you are not able to boot because the login screen is custard (see above) it does seem to be an ATI graphics problem and you may like to read this thread

[http://ubuntuforums.org/showthread.php?t=1133931&page=3](http://ubuntuforums.org/showthread.php?t=1133931&page=3)

I couldn't get 9.04 to boot after upgrade but I could boot into recovery mode and start a netroot session. Then I followed 
I followed this advice which got me into a normal session. 




I then reinstalled the proprietary driver and all seems to be ok now. However I haven't tried to do anything fancy yet. I'm running a gigabyte mobo with 780 chipsey and built in HD3400 graphics, btw.

i had graphics problem too, screen corrupted after upgrading to 9.04, but i just ssh into my machine and did "aticonfig --initial" to reset my xorg.conf

as for the soft reset, i am still getting it but it doesn't seems to cause any problem, SATA and NCQ is still working fine.

---

### Post by rajeev1204 on 2009-06-11
I have this exact same message and my cd/dvdrom is not seen by the kernel.

I have an ASUS AMD 690 G chipset .

I couldnt boot live cd in intrepid ,so i added a few lines to boot like pci=nomsi etc and it booted live cd.Once i installed 8.10 the problem went away and dvd rom was read.

But i upgraded to 9.04 and i have the soft reset message and no dvdrom now.
I have filed a bug report.

---

### Post by richm8028 on 2009-07-07
:lolflag:  Microsoft is such a pile, I get that same error, it only does it in Kubuntu 9.04, I've used other Linuxes and didn't get that message once..  I bet it's the kernel..  Microsoft is an entire virus, IMO!  It'll never be like Linux, the day Microsoft stops taking full control of your pc is the day I switch back..

---

### Post by gkh6 on 2009-07-08
Hi all. I found this while doing a google session:

"
**Solution: softreset failed (device not ready)**

ata1: softreset failed (device not ready)
ata2: softreset failed (device not ready)
ata3: softreset failed (device not ready)
ata4: softreset failed (device not ready)

this is about errors happened on AMD motherboard SB600/SB700.
[COLOR=#cc0000]all you need to is that, re-compile your kernel with [/COLOR][COLOR=#cc0000]CONFIG_SATA_PMP=n (default is [/COLOR][COLOR=#cc0000]CONFIG_SATA_PMP=y)[/COLOR]
[http://cateee.net/lkddb/web-lkddb/SATA_PMP.html](http://cateee.net/lkddb/web-lkddb/SATA_PMP.html) "

Can someone tell me how to accomplish this?

---

### Post by richm8028 on 2009-07-08
Hum, well I have no idea how to recompile my linux, LOL..  Is it because i burnt it as tao instead of dao?

---

### Post by gkh6 on 2009-07-08
> **richm8028 said:**
> Hum, well I have no idea how to recompile my linux, LOL..  Is it because i burnt it as tao instead of dao?

I guess we will have to wait for one of the more learned members to explain this.

---

### Post by luvr on 2009-07-08
> **richm8028 said:**
> Is it because i burnt it as tao instead of dao?
No, this has nothing to do with the how you burned the CD.
It is solely an issue with the hardware on the motherboard--which, apparently doesn't support something called the *"SATA Port Multiplier"* option. That, in turn, is where the suggestion to turn off the *"CONFIG_SATA_PMP"* setting in the kernel comes from.

I perfectly used to know how to compile a custom 2.4 kernel under Slackware, but I haven't compiled my own kernel ever since Linux moved to 2.6 (although the procedure hasn't really changed that much). There are special instructions for Debian and its derivatives (like Ubuntu), to ensure that your custom kernel gets registered into the *"deb"* package management system. I have the documentation available, and I may give it a try one of these days; if I do, then it is my intention to document it here as well.

**One caveat:** If you do compile your own kernel, then you will have to redo this whenever the kernel gets updated. (Any kernel update will install the new kernel with its default configuration, as provided by the distribution that you are using.)

---

### Post by lavinog on 2009-07-08
> **luvr said:**
> 
**One caveat:** If you do compile your own kernel, then you will have to redo this whenever the kernel gets updated. (Any kernel update will install the new kernel with its default configuration, as provided by the distribution that you are using.)

That is not entirely true.
The update manager will not interfere with a compiled kernel.

A good resource for compiling kernels in ubuntu is here:
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

---

### Post by e2Xpi on 2009-07-09
I get the same error message(s) when I run 9.04 from the harddrive.  I had no problem with the install.  Here is a section of dmesg:

                                 [FONT=Nimbus Sans L, sans-serif][    2.632027]  ata1: softreset failed (device not ready) [/FONT] 
 [FONT=Nimbus Sans L, sans-serif][    2.632068]  ata1: failed due to HW bug, retry pmp=0 [/FONT] 
 [FONT=Nimbus Sans L, sans-serif][    2.796031]  ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300) [/FONT] 
 [FONT=Nimbus Sans L, sans-serif][    2.796905]  ata1.00: ATA-8: Hitachi HTS543225L9SA00, FBEOC43C, max UDMA/133 [/FONT] 
 [FONT=Nimbus Sans L, sans-serif][    2.796908]  ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32) [/FONT] 
 [FONT=Nimbus Sans L, sans-serif][    2.797983]  ata1.00: configured for UDMA/133 [/FONT] 
 [FONT=Nimbus Sans L, sans-serif][    3.116036]   ata2: SATA link down (SStatus 0 SControl 300) [/FONT] 
 [FONT=Nimbus Sans L, sans-serif][    3.600021]  ata3: softreset failed (device not ready) [/FONT] 
 [FONT=Nimbus Sans L, sans-serif][    3.600059]  ata3: failed due to HW bug, retry pmp=0 [/FONT] 
 [FONT=Nimbus Sans L, sans-serif][    3.764033]  ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300) [/FONT] 
 [FONT=Nimbus Sans L, sans-serif][    3.765417]  ata3.00: ATAPI: MATSHITADVD-RAM UJ880ES, 1.90, max UDMA/33 [/FONT]
[FONT=Nimbus Sans L, sans-serif][    3.767082]  ata3.00: configured for UDMA/33[/FONT]
[FONT=Nimbus Sans L, sans-serif]
[/FONT]I notice in dmesg that in the line following softreset failed (device not ready) is a "retry pmp=0" and following that is a line that appears to indicate that the retry with that parameter was successful and the boot is moving on without a problem.  The same for ata3.  

[FONT=Nimbus Sans L, sans-serif]ata1: softreset failed (device not ready) [/FONT]  
[FONT=Nimbus Sans L, sans-serif]ata1: failed due to HW bug, retry pmp=0 [/FONT] 
 [FONT=Nimbus Sans L, sans-serif]ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300) [/FONT] 

I am a newbie to Linux.  

Have I, possibly, correctly interpreted the log as to mean that the kernel encountered a problem, attempted a work around and was successful?   I have noticed no problems with my machine though I have not run anything I would call extensive tests.  

[FONT=Nimbus Sans L, sans-serif]My system:[/FONT]

[FONT=Nimbus Sans L, sans-serif]Ubuntu 9.04[/FONT]
 [FONT=Nimbus Sans L, sans-serif]Kernel Linux 2.6.28-13-generic[/FONT]                        [FONT=Nimbus Sans L, sans-serif]
[/FONT]
[FONT=Nimbus Sans L, sans-serif]Toshiba Satellite Laptop L355D-S7901[/FONT]
 [FONT=Nimbus Sans L, sans-serif]Processor:  AMD Turion X2 Dual-Core Mobile Processor RM-72 [/FONT] 
 [FONT=Nimbus Sans L, sans-serif]Vista Home Premium (SP1, 32-bit) [/FONT] 
 [FONT=Nimbus Sans L, sans-serif]RAM: 3 GB PC6400 DDR2 800MHz SDRAM [/FONT] 
 [FONT=Nimbus Sans L, sans-serif]250GB SATA Hitachi HTS54322 HDD [/FONT] 
 [FONT=Nimbus Sans L, sans-serif]ATI SB700/SB800 SATA controller (AHCI mode)[/FONT]
 [FONT=Nimbus Sans L, sans-serif]Graphics Engine:  ATI Radeon 3100 [/FONT] 
 
 ):P

---

### Post by luvr on 2009-07-10
> **e2Xpi said:**
> Have I, possibly, correctly interpreted the log as to mean that the kernel encountered a problem, attempted a work around and was successful?
Yes--that's absolutely correct.
In fact, the *"retry pmp=0"* seems to confirm that the problem has to do with the Port Multiplier option, and that the retry *without* this setting was successful.

This makes me wonder: Instead of *recompiling* the kernel, would it be possible to specify a kernel option--perhaps **"pmp=0"** or some such--to prevent the kernel from trying this Port Multiplier feature?

---

### Post by e2Xpi on 2009-07-11
Thanks, Luvr, for your help!  

Regarding your suggestion, I tried tonight to find a boot option (to feed on the command line to the kernel when loading) and so far nothing.

I also noticed that even though I have the boot option 'quiet' specified, I found a documentation entry that states that 'quiet' will not suppress all output, just most.  I'd give you a reference/location documentation entry for that but I have temporarily misplaced it.

For what I am doing, if I could at least suppress the error message (for now) I would be happy.

I am going to continue to look for a boot option that will have the effect of setting pmp=0.  If/when I find one or any clues worth posting I will do so.

Thanks again for the help!  :p

---

### Post by manicmike66 on 2009-08-09
I found the answer to this on another part of the forum. To clarify what has been happening, here is my experience:

Problem: Hardware is brand new (upgrade). 4GB RAM, GigaByte Motherboard with the SB700 southbridge and AMD 64 bit CPU. When I run virtualbox, IO increased beyond the critical point, and the disk thrashes away ad infinitum. The CPU usage goes to 100% and stays there. Dmesg reveals the dreaded softreset message repeated millions of times.

Solution (assume you have build tools installed): 
1. Download the kernel source that matches your running system. I used "sudo apt-get install linux-source-2.6.28".
2. Open up an xterm and log in as root with "sudo su -".
3. cd /usr/src
4. tar -jxvf linux-source-2.6.28.tar.bz2
5. cd linux-source-2.6.28 && make mrproper
6. make oldconfig (copies your running kernel's kernel config file to the current directory as .config)
7. vi .config (and stay in edit mode)
8. /PMP (takes you to the line containing the line SATA_PMP=y)
9. Go to the "y" and change it to "n" ("$" will get you to the end of the line, and "r n" while on "y" will change it to "n")
10. :wq (saves then quits)
11. make (this will take a while)
12. make modules_install install
13. mkinitramfs -o /boot/config-2.6.28.8 2.6.28.8 (mine came up as this version, yours may not. If you "ls /lib/modules" you will see the version listed - it will be the one ending in a number, not "generic" etc.)
14. Edit grub to match the new kernel details (copy and edit the first one in the list).
15. Reboot

I'm working from my own memory here, so may not be 100% (feedback welcome) but I did it on Friday night and the problem just went away after the reboot. Obviously you should make sure the new kernel boots with no problem. If it has problems, you then have a tremendous learning opportunity.

Mike Williams

---

### Post by Slywire on 2009-08-13
I have the problem of trying to install 9.04, but while booting from the CD, I get the ata1 softreset failed message and my laptop hangs right there. I do not have another installation on a harddrive as I am running Gutsy(7.10) from an SD memory card at the moment and it installs without any problems. (done it about 9 times successfully before). Now support for 7.10 was stopped so I need to upgrade. 
I am using:
LG LW20 Express laptop
8GB SD drive
1.5GB RAM
1.7 Ghz Centrino cpu
intel 915 gpu chipset

I tried installing Intrepid Ibex as well, but on boot, whether from the live cd or alternate cd installation I only got a white screen withno response whatsoever. Hitting alt+f2 and typing a command also did not work. I did try logging in before typing any commands, but as the screen remains white I can't give any response. Please help

---

### Post by imasickboy on 2009-08-26
I had the same problem. Kind of.

My setup:
2 IDE HDD's
1 SATA HDD
2 IDE optical drives

I had 9.04 installed on an IDE drive, and all was well. I did get the soft reset message upon boot, but it quickly went away, and booting continued, and the OS and all devices worked properly.

Now, moving on, the IDE drive that had my OS on it failed. I replaced it with a new SATA drive.

Install went fine, but trying to boot, it gave the error, and dropped to a black screen. No busybox, just a black screen. 

Now, for the fix:

AMI BIOS 2.61:
Onchip SATA Channel: ENABLED
Onchip SATA Type: Legacy IDE
SATA IDE Combined Mode: DISABLED <---This is the key pice of the puzzle. I switched this last, and the problem went away.

Now, it boots, briefly displays the soft reset error, (once for each SATA drive), and commences booting, and all hardware works properly.

Original kernel upon install: 2.6.58-11
After updating: 2.6.28-15

All still works as it should, with just the brief soft reset error at boot. No other issues.

---

### Post by kavoura on 2010-06-01
I am having a similar problem. Well, it was not really a problem at all until today.
When I ran Ubuntu 8.04 on this PC I never had this problem. 
Then I installed Ubuntu 9.04 and it always gives me the message, 4 times, in the format 
[ x.xxxxxx] ata1: softreset failed (device not ready)


But today, it gave a whole load more similar errors and some new ones, such as 
[ x.xxxxxx] ata8: exception Emask ...{some other stuff, numbers mostly}
[ x.xxxxxx] ata8: SError: {PHYRdyChg Linkseq DevExch}
 which occured a few times. 
Eventually it booted to the login screen, but most of my drives were not mounted.

I rebooted and now everything is okay again, but still with the usual 4 times error of softreset failed.

I have all SATA drives in my PC (although I used to have 2 IDE drives and so there is an IDE connector on the mobo), 5 internal SATA HDD, 1 internal SATA DVD-RW, 1 external SATA HDD using an eSata connection.

What are those strange errors after the softreset ones and what is the cause?

---

### Post by richm8028 on 2010-06-01
I only gotten that message on earlier Ubuntu, my Kubntu 9.10 is fine, I think it was just something with SATA Drives.

---

### Post by mattlach on 2010-08-31
When it displays this message and retries successfully, does PMP work?

I ask as I was planning on getting a rather expensive (for me) external unit that requires PMP and if it's not going to work I'd rather know up front...

[See this thread for details](http://ubuntuforums.org/showthread.php?t=1565112)

Thanks,
Matt

---

### Post by Gp. on 2010-10-09
I never found a solution to this issue.
Did anyone ever submit a bug report or something?

Is it worth trying 10.10 when it comes?

---

### Post by mattlach on 2010-10-12
> **gkh6 said:**
> 
[COLOR=#cc0000]all you need to is that, re-compile your kernel with [/COLOR][COLOR=#cc0000]CONFIG_SATA_PMP=n (default is [/COLOR][COLOR=#cc0000]CONFIG_SATA_PMP=y)[/COLOR]


Great solution...   Fix the problem by disabling the feature... :roll:

Q: I'm having problems using my monitor at native resolutions.
A: Disable your native resolution.

For those of us that NEED PMP this solution is utterly useless.

---

### Post by mattlach on 2010-10-12
> **Gp. said:**
> I never found a solution to this issue.
Did anyone ever submit a bug report or something?

Is it worth trying 10.10 when it comes?

My understanding is that this is in the AMD errata (that I have been unable to find) and that it is  native incompatibility problem, and can not be fixed.

I could be wrong though, and would love to be corrected.  USB2.0 just is not fast enough for my NAS server to communicate with my storage array.  I spent extra money for the eSATA version and upgraded my entire home network to gigabit, only to be foiled by this...

---

### Post by nyteryder79 on 2010-10-28
I can confirm that the issue still exists in 10.10.  It actually prevents my machine from rebooting successfully, causing a hang in the BIOS when the machine restarts.  On shutdown, it hangs as well.  When in the BIOS or in Windows 7 x64, the blu-ray drive works as expected, eject button ejects the tray and so on.  When Ubuntu 10.10 amd64 is booted, the eject fails to work because the drive has no power.  I get the following message in dmesg:


[   11.810854] ata3: softreset failed (device not ready)
[   21.820854] ata3: softreset failed (device not ready)
[   32.430018] ata3: link is slow to respond, please be patient (ready=0)
[   56.850018] ata3: softreset failed (device not ready)
[   56.850022] ata3: limiting SATA link speed to 1.5 Gbps
[   62.080018] ata3: softreset failed (device not ready)
[   62.080020] ata3: reset failed, giving up


ata3 port is my blu-ray drive.  I was about to blame it on the fact that this is a relatively new machine, and new blu-ray drive, but now that I see it's happened as far back as this thread began, I'm blaming Canonical.  Apparently it doesn't happen on the 32-bit version of Ubuntu 10.10, but when you have 8GB RAM, you wanna use it.

---

