---
title: "Ubuntu won't load/run on dual boot system"
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by Heavenly Bicorn on 2009-02-19
Hey everyone, 

This is my first foray into Linux so please be patient with me if I don't understand something.

Anyway, here's some background info before I get to the problem: I've built a new computer and have partitioned my 1st hd into 3 partitions; One for WinXP, one for Ubuntu, and one for data. 

Unfortunately, something happened and I had to ship it to an IT specialist who proceeded to install my os'. I've gotten it back but when I turn it on, it goes straight to WinXP, not into the boot manager.

I've looked into my disk partitions and it shows itself having three partitions, all formally named. I've entered the Bios setup as well, and checked where it boots up from but all it shows are the hds and not the partitions.

**I've tried booting from the source cd (live cd?) and it shows the menu but when I choose the "install or start Ubunutu," it shows the kernel starting and then the screen blacks out. Same with choosing the "OEM installation."**

I've looked around online for the past 2 days for a solution and it seems my best bet is to download the Grub Superdisk, but **I don't have any spare cds or flashdrives with me at the moment nor do I have a floppy reader on the computer.** I'm itching to format the 2nd partition where Ubuntu is located and just do a clean install but this is also my first time trying out a dual boot system so I'm a little wary doing anything on my own nor do I want WinXp to implode. 

My hypothesis is that the IT techie installed Linux first then WinXp, thus Grub boot manager was overwritten and the computer will only boot to XP.

Any suggestions/advice?

Thanks for reading. :)

---

### Post by Partyboi2 on 2009-02-19
If you can boot from usb you could download the usb version of super grub and use that. If you cannot boot from usb then you could use [[COLOR=Blue]Unetbootin[/COLOR]]("http://unetbootin.sourceforge.net/") to run supergrub.
If you decide to go with Unetbootin then  at the  Unetbootin setup display you need to select "Distrubtion" as "Super Grub Disk" and at the bottom under "Type" change "Usb Drive" to "Hard Disk" then once its done its thing and you reboot you can select "unetbootin" and Super Grub should start.

---

### Post by crhis on 2009-02-19
What version of the live cd do you have, I thinka fter 7.10 they stopped saying start/install and had 2 options. I would say download 8.10 and try again. But if you don't have any cd's, then I dont know what to say. Just install it over the previous version and grub should be reinstalled, or you can boot into the live environment on your current one if you are able to and follow [this]("http://ubuntuforums.org/showthread.php?t=224351").

---

### Post by Heavenly Bicorn on 2009-02-19
@Partyboi2: Like I said in my first post, I don't have any spare flash drives to run super grub on, and Unetbootin seems to need a flash drive too, unless you mean for me to download it onto my hd and run it from there. 

If so, would it work if I downloaded it to my 3rd partition or do I need to deposit it into my 2nd partition where Ubuntu is located?

@Crhis: The version I have is listed under my forum name; 7.10. So you think a clean install would be preferably? Can you say with over 50% certainty that doing so won't implode my WinXP? 

B/c I'm hearing some problems come up when one re-installs Ubuntu. Like WinXP won't run and MBR code was rewritten, etc. If that happens, then I'm in a deeper hole than the one I'm in now. 

Like my first post said, I can't live boot.

---

### Post by Partyboi2 on 2009-02-20
> **Heavenly Bicorn said:**
> @Partyboi2: Like I said in my first post, I don't have any spare flash drives to run super grub on, and Unetbootin seems to need a flash drive too, unless you mean for me to download it onto my hd and run it from there. 

If so, would it work if I downloaded it to my 3rd partition or do I need to deposit it into my 2nd partition where Ubuntu is located?


You don't need a flash drive to use Unetbootin. You would download Unetbootin for windows, from windows. Once you have started up Unetbootin you would select "Super Grub" under "Distribution" and change "type" to "Hard Disk" as previously mentioned.

---

### Post by dabomb1022 on 2009-02-20
Get virtual box and run any ISO's that you need!

---

