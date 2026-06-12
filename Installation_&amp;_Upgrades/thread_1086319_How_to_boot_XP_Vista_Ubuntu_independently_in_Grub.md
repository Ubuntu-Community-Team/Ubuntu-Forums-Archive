---
title: "How to boot XP Vista Ubuntu independently in Grub"
date: 2009-03-03
forum: Installation &amp; Upgrades
---

### Post by jee_bee on 2009-03-03
First im new in linux (2day) but i ave very good knowledge in win.....

i just want to know what line to add or mod to boot XP and Vista 
from grub 1.5 independently bcuz now it send me to vista bootloader in either case         



> ## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		f67a0ad2-9946-4491-8e07-68461cf5d660
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f67a0ad2-9946-4491-8e07-68461cf5d660 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		f67a0ad2-9946-4491-8e07-68461cf5d660
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f67a0ad2-9946-4491-8e07-68461cf5d660 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		f67a0ad2-9946-4491-8e07-68461cf5d660
kernel		/boot/memtest86+.bin
quiet

title		Windows XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1
 
title           Windows Vista
root            (hd0,4)
savedefault
makeactive
chainloader     +1

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by jee_bee on 2009-03-04
so??? I realy need help please guy   !!!!!!


If u need more info just let me know what u need.... !!!!!

---

### Post by konqueror7 on 2009-03-04
you can install *Start-Up Manager* from the Add/Remove, this will enable you to customize your boot, including selecting a default OS upon boot...

---

### Post by jee_bee on 2009-03-04
now when i start my pc everything is find it show grub 1.5
if i chose to boot Ubuntu everything is cool... 
windows XP      = vista bootloader.
windows Vista   = vista bootloader.
And i ave to make a choice AGAIN
when i chose xp i want to go str8 in xp...
and vista str8 in vista.. .
i use Grub want to keep using Grub

---

### Post by Mark Phelps on 2009-03-04
The solution, as you can guess, is not entirely within Linux because what you really want to do is have MS Windows boot behave differently.

Basically, you will have to do the following:
1) Move the Vista boot folder and files from the XP partition to the Vista partition.  Since XP was already present when you installed Vista, it installed its loader files into the XP partition.
2) Download and install EasyBCD from the NeoSmart.com website into Vista.  This is a graphical tool for managing the Vista boot loader
3) Boot into Vista and use EasyBCD to remove the XP entry from the Vista boot loader.
4) Reboot into Vista.  Since there is only one entry, I believe that it will no longer show you a boot menu for Vista & XP.

If all this was done correctly, your individual GRUB stanzas should now work as you expect: the XP entry will boot into XP, the Vista entry will boot into Vista.

---

### Post by jee_bee on 2009-03-04
it been more than 5hrs than i try to fix all my boot setup
like u said and i cant figurite out how i find that...

i fond those instruction  \|/\|/\|/\|/\|/
[URL="http://themudcrab.com/separatevistaxp.php"]
http://themudcrab.com/separatevistaxp.php[/URL]


......my crapy xp cd ave no repair option
  
and im pretty sure than there is a better way to do it

[COLOR="Red"]PLEASE any sugestion?????????????????????????????????[/COLOR]

---

### Post by Mark Phelps on 2009-03-05
I gave you some suggestions -- appears you have no interest in following them.

---

### Post by jee_bee on 2009-03-05
[COLOR="DeepSkyBlue"]Mark Phelps[/COLOR]  u give me the exact right instruction and thanks....
But my vista boot file dont want to move copy anything....
and they are all mix up whit xp boot file so im not totaly shure what is what like i say in the last message my xp cd dont ave repair option
i say dat in case i need it but like i tell you im not able to move the vista file. do i move it while im in xp ? or did i ave to do that in a
command promp im new in multi boot i never realy work around whit my all startup file b4 ! [COLOR="Navy"]So if u teel me how to move the vista boot file and confirm me what to move it will be realy cool [/COLOR]for the easybcd part it's ok

---

### Post by Mark Phelps on 2009-03-05
OK ...

The following are in your XP root folder and are used by the Vista boot loader:
1) bootmgr file
2) boot folder
3) BCD file inside the boot folder

Since you can't mess with these from inside Vista, what you will need to do is the following:
1) Boot into XP
2) Open a file manager app for the XP OS partition (probably C:)
3) Open a second file manager app for the Vista OS partition (probably D:)
4) Copy the files and folders indicated above from the XP OS partition to the Vista OS partition
5) Close the file manager apps and exit from XP
6) Boot into Vista using the stanza in Grub that points to Vista. It should work because you've copied the boot loader files and folder to the Vista OS partition.
7) Download and install EasyBCD from the NeoSmart website
8) Run EasyBCD
9) Go into the boot menu using EasyBCD and make some cosmetic change
10) Save and exit Vista
11) Boot your machine, again, using the stanza in Grub that points directly to the Vista OS. You should see the changes you made in step 9). IF you do, that means that Vista is now booting from the loader files you copied to its OS partition.
12) Using EasyBCD again, remove the XP entry from the boot menu
13) Exit and reboot into Vista -- again, using the Vista only entry
14) If there is now only one entry in the Vista boot menu, it's likely that you won't see a boot menu anymore and will go straight into Vista
15) you can now remove the Vista loader files and folder from your XP OS partition.
16) When you reboot Grub using the XP entry, you should now boot directly into XP.

---

### Post by jee_bee on 2009-03-06
Thanks a lot [COLOR="Red"]**Mark Phelps**[/COLOR] you solved my problem !!!!!!
exept i was unable to move or copy the file under **[COLOR="SeaGreen"]XP[/COLOR]** or **[COLOR="Indigo"]Vista[/COLOR]**
Under my new best friend, [COLOR="DarkOrange"]***Ubuntu***[/COLOR] i was able to copy them trough
my USB thumb and copy in **[COLOR="Indigo"]Vista[/COLOR]** under **[COLOR="Indigo"]Vista[/COLOR]** and i didn
delete the **[COLOR="Indigo"]Vista[/COLOR]** boot in **[COLOR="SeaGreen"]XP[/COLOR]** i ave use **EasyBCD** in **[COLOR="Indigo"]Vista[/COLOR]**
to remove the **[COLOR="SeaGreen"]XP[/COLOR]** entry - and in **[COLOR="SeaGreen"]XP[/COLOR]** also with **EasyBCD** i remove the [COLOR="Indigo"]**Vista**[/COLOR]
entry ....   welldone   [COLOR="Blue"]!!!!![/COLOR] =D> [COLOR="Blue"]!!!!![/COLOR]

---

