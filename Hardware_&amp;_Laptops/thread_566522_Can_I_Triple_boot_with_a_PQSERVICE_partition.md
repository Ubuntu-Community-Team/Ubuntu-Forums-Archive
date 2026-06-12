---
title: "Can I Triple boot with a PQSERVICE partition?"
date: 2007-10-03
forum: Hardware &amp; Laptops
---

### Post by tokina on 2007-10-03
hey y'all,

i have a question i hope somebody can help me with. i did a search already, but the result did not quite answer my question. 

I am considering installing ubuntu on my Acer Aspire 5050 I just bought not long ago. The laptop is currently dual booting vista & xp. I would like to triple boot vista, xp & ubuntu linux.

after booting with the liveCD and running gparted, i found out my partitions are set as follows (only one harddrive with 80gig capacity):

sda1: 10 gig (PQSERVICE) ntfs, 7 gig used (Acer recovery partition)
sda2: 35 gig (ACER) ntfs, 20 used (Vista partition)
sda3: 35 gig (DATA) ntfs, 9 gig used (XP partition)

After going halfway through the installer, it seems that ubuntu did not recognize my vista or xp installation. it defaults to trying to partition the whole harddrive for ubuntu (which i had to partition 10 gig from sda3 using gparted, and selected "use largest free continous or something") and the migration assist did not recognize any user settings to transfer. 

at this point i stopped and exited out of the installer. i guess the reason my m$ os are not recognized is because the PQSERVICE partion. Well, if I did go through with the ubuntu installation, will I still retain my windows os's so grub will triple boot?

---

### Post by michalski7777 on 2007-10-08
when installing click advanced on the parittion section it should lead you to a table of partitions where you can decide what you want to use for the installation, or swap (if any). and the rest should (by default) be left 

the overall options are that you can format a partition, create/delete a partition and use that partition for installation (which will wipe out that specific partition).

after installing it will reboot and grub will launch if you dont see an option for windows you may need to configure the grub (see below) 

usually ubuntu doesnt detect trans ferable settings if the is a current windows partition, its not your fault :P you will have to manually create user accounts and transfer document from the ntfs partition (windows/sda2) to the ubuntu partition(sda3) 

configuring grub:

login to a admin capable account (the default account you made on installation) go to 

Applications--->Accesories--->Terminal

and type: *sudo gedit  /boot/grub/menu.lst* 

---dont make the mastake i did when doing this its written menu.LST not menu.1ST letter not number---you may need to enter your password-----

in the very bottom (way at the end)

making sure its another paragraph at the bottom put it the following lines:

[B]title		Windows Vista
root		(hd0,1)
savedefault
makeactive
chainloader	+1[/B]

customize as needed (ie: Windows XP)
since windows is on sda2 it is written as hd0,1 on grub
and sda1 is hd0,0

---you will need to do the same thing for the xp partition with the respective hard drive location
and title---

when your done make sure you made no errors and save it go to the terminal again and type

*sudo update-grub*

and it'll update the grub 
your done

---

### Post by michalski7777 on 2007-10-08
oh and can you please reply to me telling me if it worked ok, and what i could do better next time to help someone with a problem (ie:more detailled, better formatted ect...) this is my first time posting ---thank you good luck

---

