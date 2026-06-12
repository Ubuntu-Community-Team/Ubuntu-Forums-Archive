---
title: "Need to fix dual boot"
date: 2008-07-16
forum: General Help
---

### Post by DaveDoesIT2 on 2008-07-16
Hi people,

OK all my own fault. I installed Kubuntu and after looking at it decided I didn't have time to learn it right now so instead of it automatically booting into Kubuntu, I changed the boot loader file to boot straight through to Vista.

Ahhh, should have read the fine print. <grin>

I'd like to reinstate the bootloader but have it default to Vista.

Problem: In Vista I cannot see the partition for Kubuntu so I cannot change the bootloader text.

Can someone please help this impetuous and naive old fool. 

Thanks in advance

Dave

---

### Post by Het Irv on 2008-07-16
Step 1: Restoring Grub
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Step 2: Changeing Defaul Boot entry

You will need to edit your GRUB file

```
kdesudo kate /boot/grub/menu.lst
```
type that line (or copy/paste if you want) into the terminal.

Then look for the line that says:
```
default 0
```
For me it is under the first commented section

Just change the number to the number that Vista is the boot loader.
There is a list at the bottom of the file if you need it for refrence.

---

### Post by louieb on 2008-07-16
From one old fool to another. Use this and you can use the Ubuntu partition from vista. [Ext2 IFS Win w/write support]("http://www.fs-driver.org/index.html")

BTW: press <esc> when booting to get the GRUB menu.

The above assumes you did a normal dual boot install. If you installed inside of windows via wubi, the above won't work.

good luck.

---

### Post by DaveDoesIT2 on 2008-07-17
> **Het Irv said:**
> Step 1: Restoring Grub

Thanks for that, I will print out the instructions and give it a shot.

Dave

---

### Post by DaveDoesIT2 on 2008-07-17
> **louieb said:**
> From one old fool to another. Use this and you can use the Ubuntu partition from vista. [Ext2 IFS Win w/write support]("http://www.fs-driver.org/index.html")

Thanks Louie, I did a normal install from the DVD so I am assuming this will work. I like the idea of being able to see the partition from within Vista.

Dave

---

### Post by DaveDoesIT2 on 2008-07-17
> **Het Irv said:**
> ```
kdesudo kate /boot/grub/menu.lst
```

Hi,

I used Louie's [Esc} to get the Grub menu.

I hit "c" to go to the command prompt and typed in the above command but I get a #27 error.

Should they be backslashes instead of forward? Or is there something else I am missing.

Thank so far.

One thing I should mention is that before changing the grub file to boot straight through to Vista, I made a copy of the original.

Is there an easier way to just replace the current file with the one I saved?

Dave

---

### Post by Het Irv on 2008-07-17
I meant for you boot into Kubuntu and then type these commands.  Sorry did put that in there

---

### Post by louieb on 2008-07-17
> **DaveDoesIT2 said:**
> ...I hit "c" to go to the command prompt and typed in the above command but I get a #27 error.

The command was meant to be given in a terminal after you boot to Kubuntu. Opps see Het just beat me.   
Good thing you made a backup of /boot/grub/menu.lst. You should be able to use a live CD or the  ext3 fs driver from windows to replace your menu.list with the backup.  


If you edit it from windows with notepad its going to look real strange. Notepad doesn't handle Unix/Linux end of line correctly. get notepad++ its an open sourece text editor and a really nice replace for notepad. [http://notepad-plus.sourceforge.net/uk/site.htm](http://notepad-plus.sourceforge.net/uk/site.htm)

---

### Post by DaveDoesIT2 on 2008-07-18
> **louieb said:**
> You should be able to use a live CD

Hi Louie,

Thanks for that. I tried live cd it booted through to the Linux desktop OK.

I used Kate to find the copied files I had made and tried to rename menu.lst to menu_vista.lst and it insisted on trying to write it back to the CD. 

I clicked "Storage devices" and selected the active Kubuntu device but still it wanted "Save as" (in Kate) back to the damned CD. It returned a disk write error along the lines of "cannot write back to read only media".

Bloody useless as I see it. I cannot understand why "Save as" in Kate did not work since the files loaded into Kate just fine.

I will install the ext3 stuff and go for the brute force approach. I already use Notepad++, but thanks for mentioning it anyway.

As this is my first foray into Linux, I am thinking Bill G does not have much to worry about with Linux stealing the market. This is pretty basic stuff I am trying to do and Kubuntu is handling it very poorly.

Dave

---

### Post by DaveDoesIT2 on 2008-07-18
> **louieb said:**
> or the ext3 fs driver from windows to replace your menu.list with the backup.

Hi Louie,

EFS to the rescue, that all worked thanks. I was able to rename the menu.lst file to menu_vista.lst and then rename the menu_original.lst to menu.lst.

Now all I need to do is find out how to uninstall Kubuntu. From the searches I have done on this site so far, not an easy task it seems. <sigh>

Dave

---

### Post by Potatoj316 on 2008-07-18
Perhaps the hard drive has not been mounted.  The root of the CD looks almost identical to that of the Hard drive.  

Also, this is not something people usually have to do.  That is why it is more difficult than you would like.

---

### Post by Potatoj316 on 2008-07-18
To uninstall boot into the Live CD environment and run gparted.  Then just delete the Linux partition (ext3) Then resize the Windows partition to fill the empty space.  After you have done that, boot with your Vista DVD and choose repair to reinstall the Windows bootloader.

---

### Post by louieb on 2008-07-18
Don't know if your going to replace Kubuntu with something else or give the space back to vista. 
Don't just delete the partition - GRUBs main files are there and the the PC won't boot. Not that hard lots of ways to do just that. 

Replace GRUB 1st.   [IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

Don't judge Linux by the Kubunta live CD. The Ubuntu faminly of live CDs has gotten better. Konppix, Kantoix, Slax, even the lightweight Puppy Linux are  more pollshed live CD.

---

### Post by Potatoj316 on 2008-07-18
My way would have worked, reinstall the windows bootloader.  You just delete the partition and then put the Vista DVD in and tell it to repair. (i think its easier than removing grub)

---

### Post by DaveDoesIT2 on 2008-07-19
> **louieb said:**
> Don't know if your going to replace Kubuntu with something else or give the space back to vista.

Thanks Louie and Potato,

Yes I want to put the laptop back to the way it was. Since I am having to jump through so many hoops to make stuff work I will order the Ubuntu DVD and put in on an older computer.

I'd like to get Vista back to the way it was and I should have done a Restore Point, but I guess you know how that and Hindsight goes. :)

I tried using SuperGrub last night but it just hangs after recognizing 3 files or partition types. 

I rebooted to Vista and downloaded FixMBR but it does not list Vista as a supported system. If I am messing with the MBR I need to be sure it is going to boot to Vista after the fix. I have read where using FixMBR then deleting the Linux partitions worked but I can't find that post again. I am pretty sure it referred to XP though.

Anyway, I will wade through the Uninstall page link and see where that takes me. I had not expected it to be so damned difficult to uninstall Kubuntu and that's why I didn't bother with a Vista Restore Point. <sigh>

I am reading the Uninstall page link you sent. Thanks. My Acer laptop did not come with a recovery CD so I am treading on thin ice with everything I am doing. If grub et al trashes Vista I will have to buy a new copy and I really can't afford $160 right now.

I know I have no one to blame but myself and I should never have put Kubuntu on the portable with Vista. I was expecting it to be much better behaved than it is. Another of life's little lessons. :)

Dave

---

### Post by DaveDoesIT2 on 2008-07-19
> **Potatoj316 said:**
> After you have done that, boot with your Vista DVD and choose repair to reinstall the Windows bootloader.

Hi Potato,

There in lies another problem. The Acer laptop did not come with a Vista DVD. It had a "Make recovery CD" option pop up the first time I used it. 

I went through the steps to make the CD but the system never made all the way through. It was Acer's own software so I contacted Acer Tech Support (a joke in itself) and the upshot from them was basically, "tough sh.t" <sigh>

Anyway I will persevere with the uninstall options on the website Louie pointed me at, but I need to step warily.

Thanks for the help and suggestions.

Dave

---

