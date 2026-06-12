---
title: "R100 ubuntu install error"
date: 2012-04-07
forum: Hardware
---

### Post by Porsche650 on 2012-04-07
I have a Toshiba R100, I just bought a new hard drive, I was planning on dual booting with XP but every time I try to install XP i get the blue screen error.  What i really want to do is just have ubuntu.  The computer has an external Hard drive and usb floppy drive. 

I burned the ISO 11.10 ubuntu to a cd at 4x speed and now i have a 9.10.  Every time I try to install I get the error 
(initramfs)Unable to find a medium containing a live file system :mad:
I can't figure it out anyone have any ideas???

---

### Post by RJARRRPCGP on 2012-04-07
Sounds like ATA communication issues. Also, the optical drive may be bad.

---

### Post by Porsche650 on 2012-04-08
Semi fixed.  Had to install Windows XP then installed ubuntu  from windows I was able to install Ubuntu no with no problem.

For the time being I will dual boot Hrs of working on this I am sick of playing with it.

For reference for anyone else installing Windows XP and Ubuntu on these computers.  I have a usb floppy and a pci card cd rom.

I Booted to the floppy(Using win98 boot disk and used the install with cd rom support so it would install Ram Drive tools) used Fdisk and deleted the partition then recreated the partition and since i have a 60GB hard drive i made a 40 20 partition and made the 20 active.  Then restarted the computer again and booted using floppy again once ram drive installed again I used D: directory that had Ram Drive and put "Format C:".  

Once this was done I got the R100 Factory boost disk from the Toshiba website
([http://aps2.toshiba-tro.de/kb0/TSB5100S70004R01.htm](http://aps2.toshiba-tro.de/kb0/TSB5100S70004R01.htm))

Restarted and loaded which I probably could of did this from the beginning and the tools would of been there.  Once you boot up with this it will give you and invalid error just press Ctrl C and terminate the batch with pressing Y.  Once it puts you back into Prompts enter X: then cd I386 then Winnt, This will install windows xp files to your primary partition generally C:, you can remove floppy's and cds if any in drives once it installs.  It will automatically do the rest.  Once that was done I installed the ubuntu cd and installed from windows which went without a glitch.  

--Only problem I had was when starting up it would prompt me which operating system I would want to use this is the prompt for windows not the dual boot prompt for Ubuntu.  Ones a black screen white lettering with simple format ubuntu has a border small lettering and options for the grub.

I fixed this by going into Control panel,system,advance,edit, and removing 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP
 Home Edition"

This way it boots to Ubuntu dual boot screen instead of getting two of them also after 10sec or so it will automatically boot to Ubuntu.

---

