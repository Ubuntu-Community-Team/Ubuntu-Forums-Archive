---
title: "changing partition size with the installer"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by tasmaniasedado on 2009-03-04
hi, excuse if sucky english, its not my native languaje

the thing is

im trying to install ubuntu on a computer withn windows xp as main sys op

i have 26 gigs free for ubuntu

im using the live cd boot install from 8.10 and the automatic utility of using the free space for ubuntu didnt work

i did a defrag in win xp and still isnt working

so now i have the option of changing the partition size with the ubuntu installer

im at there in the installation

but i can change the size to free MORE than the free size, im not gonna do it anyway

im not sure if changing the size cause i think it may corrupt the files of that partition

i know i should backup, but if its 99% safe im not doing it cause the info its not so important

so, im gonna lose data doing this?

---

### Post by InspiredIndividual on 2009-03-04
I think it would be most prudent to find out what went wrong with the automatic utility first. What error message did you encounter? 26 GB should be enough free space to install Ubuntu, so if that didn't work you there might be something wrong.

---

### Post by avtolle on 2009-03-04
I think the OP needs to shrink his Windows partition first; this is apparently where he is in the process.

---

### Post by tasmaniasedado on 2009-03-04
yeah avtolle thats where i´m

inspired:
i dont remember the error message, but was nothing special, just something like "i couldnt be done"
after that, i tried again (rebooted) and the options for resizing the windows partition where gone
so then, i tried drefragmenting in windows
tried again, same error (but resizing option back!)
so i came here to post the problem, and left the house (with some hurry) with the computer waiting in the option for resizing the partition manually
just back, the computer went out of battery, so booted again,
tried again, and AGAIN i dont have the resizing partition optiones anymore
so i dont know what to do

---

### Post by tasmaniasedado on 2009-03-04
ok, now im in the partition manager inside ubuntu running from the live cd, i cant edit the partition
when i double click on it i get "information about /dev/sda1"
as an anomaly i just see these:
cluster accounting failed at 14088 (0x3708): missing cluster in $Bitmap
cluster accounting failed at 14088 (0x3709): missing cluster in $Bitmap
and i think it continues but i cant see any more of the window couse of screen resolution

---

### Post by InspiredIndividual on 2009-03-04
tasmaniasedado: Ah, I misunderstood. I thought the 26 GB free space you mentioned referred to free space in your partitioning table. I think I understand correctly now that you currently have only a single partition for Windows, which you want to downsize to make room for an Ubuntu partition? In this case, the Gparted option to use the largest continuous free space fails for the obvious reason there is no free space in your partitioning table.

Now, for the error. Gparted runs a consistency check on your NTFS Windows partition. As it encounters errors, you should check the consistency and try to correct errors. Someone else has suggested in another thread to defragment twice ([http://ubuntuforums.org/showthread.php?t=363503](http://ubuntuforums.org/showthread.php?t=363503)). As that hasn't helped you, try the following. Boot Windows and run chkdsk  with the /f (fix errors) command line option. If chkdsk asks you about if it should check the drive the next time you restart the computer then answer 'y' (yes) and restart Windows. If you don't specify the /f option then chkdsk will not fix the NTFS consistency problems. See this link for Microsoft's information on the chkdsk command: [http://technet.microsoft.com/en-us/library/bb491051.aspx](http://technet.microsoft.com/en-us/library/bb491051.aspx)

---

### Post by tasmaniasedado on 2009-03-08
thanks for the help, but couldnt make it to work
so in windows i downloaded disk director 
and cropped the windows partition size
with the free size the ubuntu installer finally worked
im running ubuntu right now
still configuring it

---

### Post by InspiredIndividual on 2009-03-08
Good to see you managed to solve the problem! As the consistency problem seemed to be related to the Windows partition, you indeed had to solve it in Windows. I must admit I'm pants at problem solving in Windows, nice to see you could do better...

---

