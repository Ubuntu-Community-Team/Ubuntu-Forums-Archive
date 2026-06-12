---
title: "Grub Error 22 Need Help!!"
date: 2008-11-15
forum: General Help
---

### Post by eaks on 2008-11-15
Hey guys and girls.. I dont use my ubuntu too often but use it when I know i will be using my computer for a long period of time without the need of a windows application.. 

Im running an older toshiba satellite laptop
3.1ghz p4
xp pro
linux (both on the same hdd but partitioned by ubuntu when i installed it)..

So everytime i would boot up my system grub would load up and ask me which OS i wanted to run.. I would pick and go on.. but tonight i was using windows and it crashed on me.. i was unable to boot to CD so started researching what i could try..

So in grub i went to the edit or whatever and i told it to 
"
hide (hd0,0)
hide (hd0,1)
hide (hd0,2)
hide (hd0,3)" (thinking that maybe grub was not allowing my computer to boot from CD and figured if i hide all the partions it will boot from there possibly"
without really understanding what i was doing.. upon restart grub opened up with error 22.. i was unable to hit e/c/esc/ect to get it to go into the command line or anything.. Im assuming all i need to do is tell it to unhide all the partitons.. but i was unable to do this anything i tried.. i eventually got my laptop to boot from cd by using an external dvd drive (although now the internal drive works fine) and booted to the ubuntu live cd.. i opened terminal and typed in "sudo gedit /boot/grub/device.map" and it opened a blank document.. i tried to insert 
hd0,0 /dev/sda
hd0,1 /dev/sdb
ect
but was unable to save the file so I couldn't really change anything..

My question is how can I somehow get grub to see all the partions again (i dont think it should be too hard but my searching brought up nothing that worked)..

Thanks.. 

PS: Im on the same laptop now with an extra 160gb hdd i had laying around with a fresh install of xp pro.. but need to fix up that other hdd as it has all my important information on it!!

---

### Post by caljohnsmith on 2008-11-15
You can unhide each of your partitions with:
```
sudo grub
grub> unhide (hdX,Y)
```
And replace (hdX,Y) with each of the partitions you hid. You can check if you successfully "unhid" the partitions with:
```
sudo fdisk -l
```
And make sure your Windows partitions is type "7" under the "ID" heading, and also make sure your Ubuntu partition is "83" under ID. After you are done unhiding your partitions, if you want to post the output of the fdisk command above, I can check to make sure all your partitions look OK if you want. Otherwise let me know how it goes.

---

### Post by eaks on 2008-11-15
hey man.. i tried to type in the code "sudo grub" and i got an error saying something about grub is not a command or something..  i tried a few other combinations with everything and couldn't get it working.. 

This is sopose to work in terminal off the live cd??

Thanks

---

### Post by TeXtonyx on 2008-11-15
PS: "Im on the same laptop now with an extra 160gb hdd i had laying around with a fresh install of xp pro.. but need to fix up that other hdd as it has all my important information on it!!"

Is the important information on the XP partition or both the XP and
Ubuntu partition? If it's just on the XP partition, fix XP so that
it boots normally again without grub. You need a real XP install cd

[http://www.simplyguides.net/guides/recovery_console/recovery_console.shtml](http://www.simplyguides.net/guides/recovery_console/recovery_console.shtml)

This guide has pictures. After you have XP working use a USB stick
and copy the important data to it. If you have more data than the
capacity of the usb stick, transfer the data to another hard drive
and repeat the operation as often as necessary. 

After this is done, you can try to get your Ubuntu installation
working again. XP has now written the MBR. If you have important
files on the Ubuntu partition, you can't boot to it. Download
Super Grub Disk and see if you can boot Ubuntu, use the SGD option
with help. Transfer the data from Ubuntu to the usb stick again.
If booting from SGB deosn't work, you can try mounting the Ubuntu
partition from the live cd. Then burn a cd or use the usb stick.
But that might fail too.

Then it depends on how much customization effort you've put into
Ubuntu and how important the data files/emails that are on it.
You can try to make grub work if it does matter. Or, you can
delete the Ubuntu partition and reinstall Ubuntu. Choose largest
free space (guided) from the live cd install. It will install 
Ubuntu into the unallocated space you just made for it by deleting
the Ubuntu partition. Now you have a choice at Step 7, Advanced,
to install grub to the MBR which is the default, or to the Ubuntu
/boot partition. If you install grub to the /boot partition, then
this problem *never* happens of (temp) losing the XP boot capacity.
You will need to download and run Bootpart (free) which installs
a 512 byte boot segment to the XP C:\ and writes to boot.ini
the option of booting is written to boot.ini and you can boot
either XP or Ubuntu from XP or Ubuntu separately from SGD.
Or if you like grub, don't change anything at Step 7.
As I said, you can try to fix grub and the Ubuntu install before
reinstalling Ubuntu, it depends on how much effort you've invested.

---

### Post by eaks on 2008-11-18
The above won't work for me as my XP has an issue with booting (even from CD) I get a bsod even when I try and load an XP install disc and run the recovery console!

---

### Post by 73ckn797 on 2008-11-18
You could go here: [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) and download Super Grub Disk and burn a CD. Boot from that and let it fix things. Read any instructions for using it.

---

