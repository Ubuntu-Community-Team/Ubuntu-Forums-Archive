---
title: "Need HELP desperately."
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by sham08 on 2009-05-06
Hello.I'm a newbie in the forum and hoping also in future to the Ubuntu.Its have been 5 days till now,and I am still stuck in the installation process of Ubuntu 9.04.I've downloaded the iso image from Ubuntu. com and successfully burned it using Infra Recorder.All goes well,until I inserted the CD into my 'HL-DT-ST DVDRAM GH20NS10 ATA Device' (as the sole CD/DVD driver on my PC)and expected the installation will go smooth and simple (as all other previous users mentioned).Unfortunately it didn't goes well.Nothing happened,instead the screen brought me back to 'Vista'(the OS that I hoped to get rid off completely from my PC).I made some 'googling' and found out that I have to set the BIOS sequence of the drive.With a little/nil knowledge on what I was about to do, I opened the BIOS (Phoenix-AwardBIOS V6.00PG) and found out the default setting were already the CD-ROM.I wonder why on the earth the CD (Ubuntu 9.04) that I've installed didn't boot on the start.I am sure the CD that I've burned and inserted in the drive isn't the cause of the problem.I'm hoping anyone out there could help me on the matter.Till this moment the enthusiasm and determination are still high (to be a part of Ubuntu users),and I'm really hoping at the end of the day I'm in front of my desktop using Ubuntu as the OS.Thanks in advance for any possible help.

---

### Post by AlanR8 on 2009-05-06
Sorry to hear of your issues.

Are you sure the boot sequence is correct in the machine's bios? Providing the CD/DVD is listed as the first boot device all should be fine.

However as a suggestion, when the machines boots, the first black screens, before it gets to the Windows screens, does it give an option to "Press any key to boot from CD ROM"?

---

### Post by Bartender on 2009-05-06
Take that CD to someone else's PC, check their BIOS, restart that PC, and let6's see what happens.  The easiest thing right now is for you to apply some basic problem-solving steps such as trying a different PC.
Let's think about this for a second.  You believe your PC is actually set up to look at the optical drive first.  How would we test that?
I'd drop a music CD in the tray and restart the PC.  If you try this simple experiment and you do NOT hear the optical drive spin the music disc up, and you DON'T see the little LED on the front od the optical drive flashing, then we have to assume that you don't have the BIOS set up correctly.
If the PC does spin the music CD up, then either locks up with an error message or moves on to Vista, at least we know the BIOS is right.
Plopping the Ubuntu CD into another PC or two should help to isolate the problem.  Did you burn it slowly or let the burn software spin it at maximum speed?  Did you use a CD-RW instead of a CD-R?  Are you absolutely sure you created an image instead of merely copying the download?  Boot into Windows, toss the CD in the optical drive and "Explore" it.  If you see one huge file you didn't do it right.  If you see several folders and a handful of files, at least you made an image.  Doesn't necessarily mean it's a good image but you're on the right track.

---

### Post by sham08 on 2009-05-08
> **AlanR8 said:**
> Sorry to hear of your issues.

Are you sure the boot sequence is correct in the machine's bios? Providing the CD/DVD is listed as the first boot device all should be fine.

However as a suggestion, when the machines boots, the first black screens, before it gets to the Windows screens, does it give an option to "Press any key to boot from CD ROM"?Hello Alan, thanks for responding and sorry for late reply.Yes,there was a message "boot from CD",not "Press any key and etc...".And these are the chronologies for more specific.Firstly,I inserted the CD into the drive,then restart the PC.Out the message "Boot from CD".If I didn't pressed any key,the screen took me to start Vista normally (Welcome message and the password box).But if I pressed others key (space or enter),it appeared the Windows Boot Manager with the option- start Microsoft Windows Vista and Tools :Windows Memory Diagnostic.I'm really in the dark right now.Please,help me to solve the problem.

---

### Post by sham08 on 2009-05-08
> **Bartender said:**
> Take that CD to someone else's PC, check their BIOS, restart that PC, and let6's see what happens.  The easiest thing right now is for you to apply some basic problem-solving steps such as trying a different PC.
Let's think about this for a second.  You believe your PC is actually set up to look at the optical drive first.  How would we test that?
I'd drop a music CD in the tray and restart the PC.  If you try this simple experiment and you do NOT hear the optical drive spin the music disc up, and you DON'T see the little LED on the front od the optical drive flashing, then we have to assume that you don't have the BIOS set up correctly.
If the PC does spin the music CD up, then either locks up with an error message or moves on to Vista, at least we know the BIOS is right.
Plopping the Ubuntu CD into another PC or two should help to isolate the problem.  Did you burn it slowly or let the burn software spin it at maximum speed?  Did you use a CD-RW instead of a CD-R?  Are you absolutely sure you created an image instead of merely copying the download?  Boot into Windows, toss the CD in the optical drive and "Explore" it.  If you see one huge file you didn't do it right.  If you see several folders and a handful of files, at least you made an image.  Doesn't necessarily mean it's a good image but you're on the right track.Hello,thanks for your reply.Yes,you were right.I just found,if I inserted a CD into the drive (HL-DT-ST DVDRAM GH20NS10 ATA Device),nothing happened.Instead,the PC acted strangely (stop responding).I assumed it was the same problems that I've encountered before (when I swapped OS from XP to Vista).But,back then, I solved the matter by just uninstalled the drivers and reinstalled it back.By the way,I've also have downloaded a DVD version of Ubuntu 9.04,Desktop i386.As you said,I inserted into the drivers tray (the same drives),and I can see the content of the DVD (in good form),but still can't boot it from the drives.Have any suggestion?Thanks in advance for your efforts.

---

### Post by swisstone198 on 2009-05-08
What did you use to burn the ISO?

---

### Post by albinootje on 2009-05-08
> **sham08 said:**
> All goes well,until I inserted the CD into my 'HL-DT-ST DVDRAM GH20NS10 ATA Device'

Do you have a fairly recent computer that can boot from an usb stick ?
If so, try this to produce a bootable usb stick to do the Ubuntu installation :
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by sham08 on 2009-05-08
I used Infra Recorder as stated in the official Ubuntu.com.

---

### Post by sham08 on 2009-05-08
> **albinootje said:**
> Do you have a fairly recent computer that can boot from an usb stick ?
If so, try this to produce a bootable usb stick to do the Ubuntu installation :
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)You mean a pen drive?

---

### Post by albinootje on 2009-05-08
> **sham08 said:**
> You mean a pen drive?

Yes. You have one which is 1 Gb or bigger ?

---

### Post by sham08 on 2009-05-08
No,unfortunately I only have a Kingston 512Mb pen drive.Oh!What a day.

---

### Post by albinootje on 2009-05-08
> **sham08 said:**
> No,unfortunately I only have a Kingston 512Mb pen drive.

No problem, you can most probably still choose the net install during the preparation with unetbootin, see screenshot attached.

This assumes that you'd have a working internet connection during the Ubuntu installation, to download the missing packages.

---

### Post by sham08 on 2009-05-08
> **albinootje said:**
> No problem, you can most probably still choose the net install during the preparation with unetbootin, see screenshot attached.

This assumes that you'd have a working internet connection during the Ubuntu installation, to download the missing packages.Thanks albinootje.Seems to me,I left with no other options.What should I do now?

---

### Post by albinootje on 2009-05-09
> **sham08 said:**
> Thanks albinootje.Seems to me,I left with no other options.What should I do now?

You can also try Wubi, see here :
[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)
[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by sham08 on 2009-05-09
Hello guys,for all who ever has replied and respond to my thread (Alan R8,Bartender,Swisstone198 and Albinootje) thanks a lot for all the efforts.Finally,I've resolved the problem.Its was all about the CD that weren't burned properly.I really appreciate all the recommendations and knowledge that I've gained.Makes me think,there's always somebody in the Internet that always willing to give a hand when you're in trouble.I also realize that these are only the start to a whole new world (open source).Thanks once again.

---

### Post by albinootje on 2009-05-09
> **sham08 said:**
> Its was all about the CD that weren't burned properly.

Glad to see you sorted that out.
> 
Makes me think,there's always somebody in the Internet that always willing to give a hand when you're in trouble.I also realize that these are only the start to a whole new world (open source).Thanks once again.

Welcome to Ubuntu! :)

---

### Post by AlanR8 on 2009-05-09
Enjoy and welcome

---

