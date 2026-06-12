---
title: "Hoary problems with Dell Latitude Cpx"
date: 2005-04-10
forum: Hardware &amp; Laptops
---

### Post by Romu on 2005-04-10
Hi all,
I installed without any problem Hoary on my Dell Inspiron 8600c, everything seems to work  well.

I installed without any problem on my wife's Dell Latitude Cpx (PIII 450 MHz, 320 MB of RAM, ATI RageMobility 8MB, Dexlan PCMCIA Wi-fi adapter), but Ubuntu doesn't start correctly.

Sometimes I reach the login screen, sometimes not, and in all cases, the screen becomes dark and flicks with some vertical dark color stripes and bands.

Any help is greatly appreciated.

Thanks.

---

### Post by Romu on 2005-04-15
I've finally found the problem came from a kind of conflict with the Dexlan PCMCIA Wi-Fi adapter.

I unplugged the card, rebooted the PC and How !! It worked. So I decided to hot-plug the card and Re-How !! It worked, the network, Internet connection, all fine.

So I decided to reboot the PC with the card plugged and Re-Re-How, it worked.

So now, no problem, eveything works fine.

I someone understands something, thanks to light my way.

---

### Post by brianburnham on 2005-04-16
I just updated my CPx to Hoary, and now my CD-ROM sounds like a lawn mower. Does Hoary drive your CD-ROM well? 

I get a sound like a somethings scraping. Booting in WinXP, so scraping sound.

[UPDATE]

Turns out I had a CD in the CD-ROM. Once removed, things went well. I have not tried another CD in it.

---

### Post by SanderAnt on 2005-04-20
I recently acquired a CPX from a relative who was told it was no good from Dell, and when I replaced the memory it worked again, but there's a dead key on the keyboard (the Enter key  ](*,) ) I was considering getting a new keyboard for $60 and trying it out, but googling the CPX it doesn't seem very reliable.
Have you had good luck with this laptop?

Thanks

---

### Post by Deusiah on 2005-04-20
I have used the CPx with both Warty and now with Hoary. There were some APCI boot up issues with Warty but they were not too much of a problem and Hoary has resolved them.

These laptops are great, they work very well with Ubuntu and they are still much smaller/slimmer than most laptops.

I originally started off with a 2.6GHz Pentium laptop, brand new. Once I had switch to Linux (a few months after I brought this laptop) I decided it was overkill for Ubuntu so sold it and downgraded :)

If you get one make sure you update the BIOS to add APCI support! ;)

---

### Post by brianburnham on 2005-04-24
Wow, thanks for the tip on the BIOS. That could be behind my suspend problems.

I would agree, CPX's a fine laptops and run Ubuntu well. Even with the small HD I manage a dual boot XP and kubuntu. 

Laptops for less (I am in no way affiliated, BTW) has CPx compatible keyboards for $19, as long as you don't need the cap-eraser mouse nubin thing. Here: [http://store.l-f-l.com/cgi-bin/cp-app.cgi?pg=prod&ref=89741](http://store.l-f-l.com/cgi-bin/cp-app.cgi?pg=prod&ref=89741)

To replace the keyboard you'll need to take out all the screws marked K on the bottom. After that its easy. I thought I'd have to replace mine, but found out the connector was loose.

---

### Post by loopymonkey on 2005-04-25
Hey Ubur's, I recently got Ubuntu (hoary, actually the Kubuntu version) setup on a Dell CPI 400mhz Pentium II 128 megs of ram.  Everthing seems to be running fantastic except for 2 small things.  

1 is the boot time seems a bit long.  It's the ony OS on the computer.  
Completely reformated to just run UBU.  Is there any tips on speeding up the boot process?  

2 The biggest issue is the video driver seems to be a bit slow.  When I'm in Firfox or Konq, and I scroll the page the screen redraws are horribly slow.  not smooth but very jumpy like struggling to redraw.  I tried a LiveCd version of knoppix and Linspire and it was pretty smooth to scrool around.  I'm thinking ubuntu doesn't have the correct video driver installed.  It's neomagic I'm pretty sure.

Other then that I'm a happy ubur. \\:D/

---

### Post by ddowdall on 2005-04-25
I am also having problems with the video drivers.  I install everything okay, but then when ubuntu reboots and tries to show to desktop, everything gets messed up.

I have problems on dell CPX laptop and on this old P2 300MHz server i tried to install it on. 

on the laptop, the live cd of ubuntu worked ok but it seemed a bit slow while trying to use the desktop programs.  When i installed ubuntu to the hard drive, there was a problem with the video drivers .

i did not try the live cd on the server yet.  When i tried to install to the hard drive install went okay the after ubuntu tries to load gnome the monitor say there is not signal input.

how can i fix this?
 ](*,)


UPDATE: In my server I put in a different video card and now that works.

---

### Post by alex_l on 2005-05-05
Hallo!

I think i try UBUNTU on my Dell CPi too! Only one question.
Wou it is with CD and floppy block changing on the fly? Is it working like on WinXP hotplug?
On Mandrake i didnt found how to set it up. I need to reboot and only then Mandrake detect that there is other hardware!
Have somabady experience like this?

P.S. Sorry for my english.

---

### Post by Deusiah on 2005-05-05
As far as I know there is no way of getting hotplug support for the modular CD/DVD or Floppy Drive.

Admittedly I have not tried this in Hoary but I never had any luck with it in Warty.

---

### Post by kwunderlich on 2005-05-08
I have a latitude CPxJ and installed Ubuntu (basic install of everything -- added ssh and ftp server) without a problem.  It seems to work very well except for a problem when moving the mouse (either the built-in mice or an attached mouse -- ps/2).  It seems that when I move the mouse every so often, the mouse seems to freeze for a second and then reappear at the bottom right corner of the screen and if I continue to move the mouse (once I see it freeze), it will just start opening/closing/minimizing applications that are open.  Some typical applications that I might have open are eclipse, firefox, thunderbird, file browser, and several instances of gnome terminal.  I did watch the CPU utilization through the system monitor and it does show that the CPU is at 100% during the time the mouse/cursor seems to have the issue, and I can easily reproduce the issue if I go to a web site in firefox and quickly switch to another app (without waiting for the page to display).  I had Debian - testing running on this up until recently and never saw this problem at all.  The system is a CPxJ with a 650MHz CPU and 512MB of memory.  The fact that this laptop did not have this problem with Debian testing seems to indicate there is an issue with Ubuntu.

Any ideas?

---

### Post by SanderAnt on 2005-05-08
[QUOTE=brianburnham]Wow, thanks for the tip on the BIOS. That could be behind my suspend problems.
Laptops for less (I am in no way affiliated, BTW) has CPx compatible keyboards for $19, as long as you don't need the cap-eraser mouse nubin thing. Here: [http://store.l-f-l.com/cgi-bin/cp-app.cgi?pg=prod&ref=89741](http://store.l-f-l.com/cgi-bin/cp-app.cgi?pg=prod&ref=89741)
[/QUOTE]

Thanks for the tip. I found one on ebay for $19 and the laptop's been working fine. Clarifying from my sister-in-law the laptop was reliable over it's lifetime, it was only towards the end that it developed all the problems.

I installed Kanotix as test and suspend works fine with that 2.6.11 kernel, even with a PCMCIA card installed. I'm going to try Hoary when I get my CDs in.

Thanks everyone for the responses!

---

### Post by Deusiah on 2005-05-09
[QUOTE=kwunderlich]I have a latitude CPxJ and installed Ubuntu (basic install of everything -- added ssh and ftp server) without a problem.  It seems to work very well except for a problem when moving the mouse (either the built-in mice or an attached mouse -- ps/2).  It seems that when I move the mouse every so often, the mouse seems to freeze for a second and then reappear at the bottom right corner of the screen and if I continue to move the mouse (once I see it freeze), it will just start opening/closing/minimizing applications that are open.  Some typical applications that I might have open are eclipse, firefox, thunderbird, file browser, and several instances of gnome terminal.  I did watch the CPU utilization through the system monitor and it does show that the CPU is at 100% during the time the mouse/cursor seems to have the issue, and I can easily reproduce the issue if I go to a web site in firefox and quickly switch to another app (without waiting for the page to display).  I had Debian - testing running on this up until recently and never saw this problem at all.  The system is a CPxJ with a 650MHz CPU and 512MB of memory.  The fact that this laptop did not have this problem with Debian testing seems to indicate there is an issue with Ubuntu.

Any ideas?[/QUOTE]


Well I don't think it's specific to the CPx. I have exactly the same problem with my Desktop machine which is a self built machine (Athlon 64 3200+, 1GB DDR SDRAM). Until now I have never heard of anyone having the same problem as me.

I'm afraid I have no idea of it's cause and no idea how to fix it and since there seems to be no extra information on how to fix it I don't hold very high hopes on fixing the issue.

This problem was not present with Warty until I upgraded something so perhaps this is a problem with the kernel?

---

### Post by vassie on 2005-05-09
[QUOTE=kwunderlich]I have a latitude CPxJ and installed Ubuntu (basic install of everything -- added ssh and ftp server) without a problem.  It seems to work very well except for a problem when moving the mouse (either the built-in mice or an attached mouse -- ps/2).  It seems that when I move the mouse every so often, the mouse seems to freeze for a second and then reappear at the bottom right corner of the screen and if I continue to move the mouse (once I see it freeze), it will just start opening/closing/minimizing applications that are open.  Some typical applications that I might have open are eclipse, firefox, thunderbird, file browser, and several instances of gnome terminal.  I did watch the CPU utilization through the system monitor and it does show that the CPU is at 100% during the time the mouse/cursor seems to have the issue, and I can easily reproduce the issue if I go to a web site in firefox and quickly switch to another app (without waiting for the page to display).  I had Debian - testing running on this up until recently and never saw this problem at all.  The system is a CPxJ with a 650MHz CPU and 512MB of memory.  The fact that this laptop did not have this problem with Debian testing seems to indicate there is an issue with Ubuntu.

Any ideas?[/QUOTE]

I am having the exact same problem on the same machine, any help would be greatly appreciated

Ben

---

### Post by kwunderlich on 2005-05-09
Well, here is a work-around... is not specific to Dell or CPx (or laptop for that matter), but is rather a bug in the mouse driver or kernel but is caused at the moment by the powernowd daemon:

[http://ubuntuforums.org/showpost.php?p=146009&postcount=9](http://ubuntuforums.org/showpost.php?p=146009&postcount=9)

---

