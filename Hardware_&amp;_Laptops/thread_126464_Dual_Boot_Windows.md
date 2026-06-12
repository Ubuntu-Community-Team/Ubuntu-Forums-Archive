---
title: "Dual Boot Windows"
date: 2006-02-06
forum: Hardware &amp; Laptops
---

### Post by Sape on 2006-02-06
Hey everyone,

I'm being my newbie self and having so idea what I'm doing. I installed Windows, and I've had it on there for a while, but finally i got ticked off enough with it so i installed Ubuntu as a dual boot on a different HD. 

When i start up my computer, the GRUB Loader recognizes that Windows XP is there, but when i select it to boot, my computer just spontaneously restarts... I have no idea what went wrong.. and I'd like to get everything of there, because i don't have the stuff backed up anymore because i had everything backed up on my iPod, but my iPod got into a fight with the washing machine and lost.. so my only copy of the data rests on the windows HD.. so any ideas what i should do..

If you need more information, i can get it as long as you tell me how to get it , Step by step, seeing as i'm an utter newb >.>

Thanks in advance.

---

### Post by Robgould on 2006-02-06
To get your windows back
 
1.  Boot to windows install cd -> rescue mode
2.  type fixmbr
 
If you have an older version of windows, you will need to you use your boot disk and when at the dos prompt do
 
fdisk /mbr
 
Bot of these options erase Grub and restore your master boot record.  Windows will boot as before.  
 
You will have to use the ubuntu disk to boot to ubuntu and then repair/reinstall grub
 
Or just deleted the Ubuntu install from windows and do a complete re-install from the begining.  
 
I hope this helps.

---

