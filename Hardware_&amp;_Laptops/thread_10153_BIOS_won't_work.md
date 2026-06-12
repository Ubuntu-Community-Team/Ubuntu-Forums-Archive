---
title: "BIOS won't work"
date: 2005-01-05
forum: Hardware &amp; Laptops
---

### Post by labbe on 2005-01-05
After I installed Ubuntu I can't access BIOS.
I boot up and the manufactor picture comes up. So the screen goes black, and the next tekst I see is something like, GRUB loading....
I use GRUB 1.5( I think) and I have an Elitegroup G556e laptop.
I have a dual boot with Ubuntu And Microsoft Windows XP.
Can somebody help me with accessing BIOS?

---

### Post by nemin on 2005-01-05
[QUOTE=labbe]After I installed Ubuntu I can't access BIOS.
I boot up and the manufactor picture comes up. So the screen goes black, and the next tekst I see is something like, GRUB loading....[/QUOTE]
I don't think it's likely ubuntu causes such problems, it sounds very strange to me. How did you always access the bios? Press a certain key I think, are you sure that doesn't work anymore? 
You could try to remove the HD or reset the bios, but that's not really easy with a laptop I think  :-(

Good luck.

---

### Post by labbe on 2005-01-05
It happened after installing Ubuntu..
I think it was after the GRUB was installed....
Like I told you, The screen is black, nothing work before the text, grub loading shows up...
I have no Idea...
Emailed the manufactor today, but the laptop is "designed for microsoft Windows XP" so I dont think they will help me...
Somebody ever heard of that?

---

### Post by a.stefanou on 2005-01-05
sounds normal... have you ever try before to enter to your bios?

about the logo "designed for microsoft Windows XP" it's just came with your laptop coz you have already pay for windows... is just a simple tredmark...

which laptop do you have?

---

### Post by nemin on 2005-01-05
[QUOTE=labbe]It happened after installing Ubuntu..
I think it was after the GRUB was installed....
Like I told you, The screen is black, nothing work before the text, grub loading shows up...
I have no Idea...[/QUOTE]
hmm, the only think I can imagine is that your MBR is messed up. But that's probably not the case, since windows and ubuntu boot correct, don't they?
You can alway try to reinstall grub or install lilo, but I don't give that much chance...

---

### Post by labbe on 2005-01-05
I'm willing to try everything...
How can I install Lilo or GRUB?
And what is MBR?


> about the logo "designed for microsoft Windows XP" it's just came with your laptop coz you have already pay for windows... is just a simple tredmark...
I have an Elitegroup G556e....
And the picture is is a picture of the Elitegroup Logo..


if this wont work, I will delete alle and try to boot with windows and see If I can access BIOS....

---

### Post by angrylittleman on 2005-01-05
As soon as you turn on the computer, try hitting delete, f1, f2, f8, or f12.  Hit each button once per second as soon as the computer is powered on.  If one button does not work, try another while you reboot again.  Tedious, I know.  If you have the manual for the laptop see if you can find the key that enables you to enter the BIOS.  If the screen is black and then goes to GRUB or LILO and then allows you to boot an OS, then the BIOS is working, you are just not seeing the splash screen for the BIOS while it POSTS.

Hope this helps, let us know what happens.

ALM

---

### Post by nemin on 2005-01-05
[QUOTE=labbe]I'm willing to try everything...
How can I install Lilo or GRUB?
And what is MBR?
[/QUOTE]
You can install lilo by entering:```
sudo apt-get install lilo
```
You can reinstall GRUB by:```
sudo grub-install [device]
```
MBR means Master Boot Record. It determines wich partition to use for booting.
You can boot with a windows (yes, I'm sorry ;)) bootfloppy, and then enter ```
FDISK/mbr
```
Before starting to play with you're MBR or you bootmanager, I'd create good backups first ;-)

Maybe I'm **completly **wrong with these solutions and in fact I don't really think you can fix the problem this way, but good luck anyway :) 
Before trying all these thing, try to access your bios the normal way, or even by pressing all keys, again and again :)

---

### Post by a.stefanou on 2005-01-05
for your laptop press "del" to enter to bios....

...And the picture is is a picture of the Elitegroup Logo..
\

it's say ECS which is the company... don't make thinks so complicate....

if windows and linux works fine then your system is fine...

---

### Post by az on 2005-01-05
You never mentioned what you did before you installed Ubuntu to access your bios.  Is it by hitting a key when you boot?  What happens now when you hit the key.

Also, to be completely sure we are all talking about the same thing, what do you mean by accessing the bios?

---

### Post by labbe on 2005-01-05
Before I installed Linux I had a "Normal" boot up. I think i used esc to access bios...
I think we take about same thing..
I want to chech up boot device and that sort of thing from BIOS but I can't get there..
And My system Is NOT fine when I cant go into BIOS. 
I will try angrylittleman method first, and if that aint working, I will reinstall grub and so maybe install LILO....

---

### Post by hardcandy on 2005-01-05
I just looked at the manual online which on page 50 says the bios is accessed by pressing the delete key when the laptop is first booted up. I wonder if the original poster has read his copy of the manual?

And why does he need to access the bios? Or is he talking about the WinXP progress bar when it loads?

> And My system Is NOT fine when I cant go into BIOS.  
Which means it was NOT ALL RIGHT before installing Linux, since he was pushing the wrong key!!!!    :D The best post of all week.  :D  :D  :D

---

### Post by labbe on 2005-01-05
Okay...
So when do I push delete for going to BIOS?
I dont have a manual, I never had it.
But I've been in Bios, and I touched the delete button when a text like "Touch delete for setup(or something like that" appears on the screen.
Okay, maybe I'm wrong, but If you have the same pc as I, when do you touch delete?

---

### Post by hardcandy on 2005-01-05
When it first starts booting and keep pressing until you get into the bios. On laptops, it can be very quick to boot into the bootloader so just keep pressing. And you can download the manual form the Elite website under support for your model laptop. There's some other software updates for your WinXP installation ifd you still have it on the laptop.

---

### Post by Urian on 2005-01-26
I have a similar problem with my Compaq Armada 1750: after installing Ubuntu the Bios menu is gone.

So Bios is still there ;-) But I cannot acces it. Normally the Bios menu is on a (hidden) partition on the HD.

I think I know what happened; when I installed Ubuntu I did confirm the question to use / erase / format the whole harddisk. I think this deleted the hidden partition. 

Solution would be to go to the Compaq site and download the software to create a bootflop that includes the Biosmenu. Unfortunately my laptop doesn't have a (working) floppy drive anymore.

Maybe you can find such a flop for your laptop

---

### Post by nemin on 2005-01-26
[QUOTE=Urian]I have a similar problem with my Compaq Armada 1750: after installing Ubuntu the Bios menu is gone.

So Bios is still there ;-) But I cannot acces it. Normally the Bios menu is on a (hidden) partition on the HD.[/QUOTE]
That sounds a bit strange to me, a bios menu on a hidden partition. I know about vendor creating hidden "recovery" partitions, but never heard of a bios menu on a partition.  But if you're sure about it, it'd be a good explaination :)

---

### Post by Haohmaru on 2005-06-26
I can honestly say I -am- sure because I own a Compaq Armada 1750 myself. When I got it, it had win98se preinstalled on it. I could not get to the BIOS using the preferred method - on the 'compaq' bootscreen, wait for a blinking cursor to appear and whack F10 - so I did some googling and found that the 'BIOS menu' is on a special partition on the harddisk, for which the machine looks for during boot. If it's gone, it will still work, you just can't get to the BIOS in the nicest way ;).

Owners of a Compaq Armada 1750 should take a look at [the offical Compaq/HP software and driver page for the Compaq Armada 1750 family](http://h18007.www1.hp.com/support/files/Armada/us/family/208.html?locale=en_US&prodSeriesId=96222).

My model is a *6366/T/6400/D/0/3* according to the sticker on the bottom of the machine. On the 'select operating system' page, I went for win98.

The downloads of interest are **Computer Setup for Portables** and **Personal Computer Diagnostics**. With these, you can access your BIOS and install the BIOS menu partition. That is, if your diskdrive is working ;). The sting is you need DOS or win9x to install the software to some spare 1.44M disks.

I hope this will get you a bit further in your quest to run a decent OS on your system ;).

---

### Post by nocturnal_shadow on 2005-10-23
Labbe

I don't know if your problem has been solved by now.
I had a similar problem with my pc.

AMD Athlon 64, Asus K8VSE deluxe.

Win XP and Kubuntu 5.04.

So a total different system than yours.

After installing Kubuntu it took 3 days before my system wouldn't boot either.
It hangs at GRUB... loading stage 1.5

And i also can't access bios.

I found that the problem was indeed caused by the MBR, Ubuntu and Win XP use a different table to access the boot records(or something like that, i'm not completely sure about this part). Which screws up the MBR.

My machine worked fine again after removing the primary master HDD.

There is a solution to fix the MBR, i didn't use it though, this solution is on this forum somewhere. I'll see if i can find it.

I fixed the MBR by installing GAG (A graphical boot loader).

Hope this helps.

---

