---
title: "ErrorS after trying to install"
date: 2008-01-26
forum: Hardware &amp; Laptops
---

### Post by wolterh on 2008-01-26
Hi. This is quite complicated.
I had a normal, exellent windows pc on xp sp2. 
I decided to try-out ubuntu, so I downloaded the disc image file.
I bought a brand new 700MB CD.
I burnt it with ISO recorder, a tool they recommend at ubuntu.com
I booted from CD and my test-drive is awesome.
I tried to install ubuntu, and in the first part they ask you about partitions i chose guided space, that will use whatever amount you want in free space of any of your drives (I have 2, one of 20GB, were windows is installed, and one of 120GB, where i have some files, like games and aplications of windows.)
So, I chose the guided space thing, and selected i wanted 40GB. Alright.
At 52% of the installation, it prompts me with some error:
Failed to copy files. It mentions something about me having a faulty cd/dvd or hardisk.
I've used the hardisk for a lot of time, and it hasn't prompted me with errors, before this installation. I thought it might be the CD, now that they mention it in the error, they say to burn the cd at a lower speed. So, i quit ubuntu and pulled out the CD. Rebooted, and this error appears:

Error loading Operating System

I thought it might be ubuntu, by not being 100% installed, but still trying to boot. So, i deleted all partitions of ubuntu, ut 50GB were labeled as unallocated. (Can i fix that? I don't want to loose 50gb....)

So, now, everytime I boot without the CD, the computer prints:

Reboot and select a proper device or Insert a bootable media

something like that.

What do I do? Currently, I'm going to download a CD virtual thing, and install it from the ISO....

---

### Post by shutslar on 2008-01-27
You might want to try this:
[LIST=1]
[*]Boot from Win XP Cd (you will get setup inspecting hardware configuration)
[*]You will come to screen to setup or repair existing install press R to enter recovery console
[*]You will be asked to choose install to repair enter number and you will get prompt for admin password followed by C:WINDOWS>
[*]at this point type FIXMBR
[/LIST]

If you still can't boot XP, then you might do the same above but instead of typing FIXMBR in step #4 this time you will want to type: fixboot x:  where x: is the drive letter your XP is installed on.

To give XP back the space (better to go ahead and try to get ubuntu installed), you can always boot from the LiveCD you created and then install and run the program:  gparted.

Hope this helps.

PS...I have a dual boot Ubuntu/XP system.  I use Ubuntu and my wife uses XP....she is slowly starting to use Ubuntu more and more and likes it....I hope soon I can wean her off of MS Office so that I can get rid of the XP partition.  It is worth the time to figure out how to get Ubuntu installed.  Faster, hardware lasts longer because it doesn't need as much power to run, safer surfing the net with Linux than with XP,  easier to keep EVERYTHING updated with the latest fixes (my 9 yr old keeps her machine updated by herself).

---

### Post by wolterh on 2008-01-27
Problem gets worse...
I tryed to press R, but the Setup didn't find any hard drives, so it rebooted my computer.
The harddisk is well conected, because I can access it from ubuntu. Do you have any IM so you can help me on this thing? mines are [email]whellmundv@gmail.com[/email], [email]whellmundv@hotmail.com[/email], [email]whellmundv@yahoo.com[/email]

Please help me.

---

### Post by wolterh on 2008-01-27
Now, how do I fix my partitions? Do I create a new partition of 50GB in size? How do I restore the 20GBs I stealed from the D: drive?

---

### Post by wolterh on 2008-01-27
I fond on my American Megatrends BIOS that there was no Primary IDE Master detected, nor a Secondary IDE Slave detected. Is this bad?

---

