---
title: "Help with grub"
date: 2008-07-22
forum: General Help
---

### Post by KEE on 2008-07-22
Ok someone had problem about grub where win has removed it and someone has posted a solution. i though it would be better then the set up i have when i must go to bios and select the drive to startup...its a few steps more and alittle more waiting. so tried  it and i regret i ever did =( but any this was his solution ...





$sudo grub



$find /boot/grub/stage1



$root (hd?,?)





$setup (hd0)



after that my wins was written over and i tired to reinstall wins since i have all data saved on cds to save time. but grub wont let me run it on startup ???? help please !! oO verybad people here :mad:

---

### Post by unutbu on 2008-07-22
Did you type
```

root (hd?,?)
```
literally, or did you substitute numbers for each '?'

If you typed question marks, then boot from the LiveCD, open a terminal, and type the same commands that you posted, except take the output from the

```
find /boot/grub/stage1
```
command (something like (hd0,0))
and use that in the root command (substituting the numbers for the question marks).

Apologies if you already did this...

---

### Post by KEE on 2008-07-22
> **unutbu said:**
> Did you type
```

root (hd?,?)
```
literally, or did you substitute numbers for each '?'

If you typed question marks, then boot from the LiveCD, open a terminal, and type the same commands that you posted, except take the output from the

```
find /boot/grub/stage1
```
command (something like (hd0,0))
and use that in the root command (substituting the numbers for the question marks).

Apologies if you already did this...

yeah i substitute and i made sure its was the ubuntu drive thats was grubed ...i still cant use winsdows anymore >:(

Ok how would I reverse it? cause i need windows back...lol do i need to buy a new mother board or wat lol

---

### Post by Rocket2DMn on 2008-07-22
This is not a security/hacking problem - moved to General Help forum.

---

### Post by zvacet on 2008-07-22
@ KEE

```
sudo fdisk -l
```

Post it here.

---

### Post by sea_monkey987 on 2008-07-22
> **KEE said:**
> yeah i substitute and i made sure its was the ubuntu drive thats was grubed ...i still cant use winsdows anymore >:(

Ok how would I reverse it? cause i need windows back...lol do i need to buy a new mother board or wat lol
Did you run that command from the live CD or the ubuntu installation?  I ask this because, on my computer the actual hard drive hd0 or hd1 referrs to can change if I change the boot device in the bios.
Also, +1 to zvacet.  Post the output of sudo fdisk -l

---

### Post by bodhi.zazen on 2008-07-22
> **Rocket2DMn said:**
> This is not a security/hacking problem - moved to General Help forum.

Title changed to reflect the type of problem ...

---

### Post by KEE on 2008-07-24
> **sea_monkey987 said:**
> Did you run that command from the live CD or the ubuntu installation?  I ask this because, on my computer the actual hard drive hd0 or hd1 referrs to can change if I change the boot device in the bios.
Also, +1 to zvacet.  Post the output of sudo fdisk -l

i ran it in terminal:

GRuB
```
$sudo grub

$find /boot/grub/stage1

$root (hd0,1)

$setup (hd0)

quit
```

well my ubuntu is on hd0 and windows is on hd1 so i used to go to windows by going to bios and switching startup options to what ever drive i wanted but now i get an error 21 from grub when i try to start windows =/

---

### Post by bodhi.zazen on 2008-07-24
> **KEE said:**
> well my ubuntu is on hd0 and windows is on hd1 so i used to go to windows by going to bios and switching startup options to what ever drive i wanted but now i get an error 21 from grub when i try to start windows =/

Why did you do that of all things ? There is no reason to do this and it makes life harder, as you can see.

Boot the HD you installed grub onto or install grub into the MBR of your windows drive.

---

### Post by Potatoj316 on 2008-07-24
If you can currently get to Ubuntu but not windows you will need to add an item to your menu.lst

add these lines to the bottom of the file

# For booting Windows XP
title Windows XP
root (hd1,0)
makeactive
chainloader  +1

---

### Post by KEE on 2008-07-24
> **bodhi.zazen said:**
> Why did you do that of all things ? There is no reason to do this and it makes life harder, as you can see.

Boot the HD you installed grub onto or install grub into the MBR of your windows drive.

 right but the poster question was that he want to use windows and ubuntu but   windows rewritten he's settings and he cannot use ubuntu. the programmer who  mention grub said he uses this to select the drives its sounded easyer then going into bios... or something like that unfortunately i can find the thread  =(

---

### Post by KEE on 2008-07-24
> **Potatoj316 said:**
> If you can currently get to Ubuntu but not windows you will need to add an item to your menu.lst

add these lines to the bottom of the file

# For booting Windows XP
title Windows XP
root (hd1,0)
makeactive
chainloader  +1

where and what file do write this in? whats the # line do i write this under btw? do i have to replace current script? Thanks for the help =D where is meny.lst? is it hidden in user/home?

---

### Post by confused57 on 2008-07-24
I assume you're still able to boot into Ubuntu by selecting that drive first, open a terminal:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
Add this Windows entry to the very bottom of your menu.lst:
```
title  Windows XP
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```
quit & save

menu.lst is short for menu.list, not menu.first

I would recommend downloading a copy of Super Grub Disk & restoring your Window's IPL(Initial Program Loader) to the mbr of your Windows drive:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

There are other ways to restore Windows IPL, but SGD is probably easier:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by zvacet on 2008-07-24
> right but the poster question was that he want to use windows and ubuntu but windows rewritten he's settings and he cannot use ubuntu.

If that is the case then 

```
sudo fdisk -l
```

to see where your ubuntu partition is and after that [reinstall grub.]("http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub")

---

### Post by sea_monkey987 on 2008-07-26
@ KEE, Since you said that you have windows and ubuntu on physically different drives, I don't believe installing grub on the ubuntu drive should have messed up at all your windows drive.

Please note that (hd0) and (hd1) is confusing at this point since the bios changes what (hd0) and (hd1) referrs to.  But, if you boot into ubuntu using the bios method you mentioned, you will always see the ubuntu drive as (hd0).  However, if you boot into windows the same way, windows will refers to its own drive as (hd).  Therefore, here is what I understand so far:

        1.  If you go into your bios and change the boot drive to the ubuntu drive, you are able to get into ubuntu after the a GRUB screen.
        2.  If you go into your bios and change the boot drive to **still the ubuntu drive**, and try to select windows from GRUB, you get the error 21.
        3.  We need to know what happens when you go to the bios and change the boot drive to the windows drive?  Do you even get a grub screen?  Does windows boot?

In option 3, if you get a grub screen or error message, that means somehow GRUB has overwritten the windows' IPL portion of the MBR on the hard drive with windows (you have two MBRs - one on the ubuntu drive and one on the windows drive.  the bios uses the appropriate MBR depending on the drive you select to boot).  What you'll need to do is restore the windows mbr.  Before you restore, unplugging the ubuntu drive from the computer will prevent drive reference errors (you know the question - is (hd0) ubuntu or windows right now) and also prevent windows from overwriting GRUB from the ubuntu drive.

---

### Post by KEE on 2008-07-26
> **sea_monkey987 said:**
> @ KEE, Since you said that you have windows and ubuntu on physically different drives, I don't believe installing grub on the ubuntu drive should have messed up at all your windows drive.

Please note that (hd0) and (hd1) is confusing at this point since the bios changes what (hd0) and (hd1) referrs to.  But, if you boot into ubuntu using the bios method you mentioned, you will always see the ubuntu drive as (hd0).  However, if you boot into windows the same way, windows will refers to its own drive as (hd).  Therefore, here is what I understand so far:

        1.  If you go into your bios and change the boot drive to the ubuntu drive, you are able to get into ubuntu after the a GRUB screen.
        2.  If you go into your bios and change the boot drive to **still the ubuntu drive**, and try to select windows from GRUB, you get the error 21.
        3.  We need to know what happens when you go to the bios and change the boot drive to the windows drive?  Do you even get a grub screen?  Does windows boot?

In option 3, if you get a grub screen or error message, that means somehow GRUB has overwritten the windows' IPL portion of the MBR on the hard drive with windows (you have two MBRs - one on the ubuntu drive and one on the windows drive.  the bios uses the appropriate MBR depending on the drive you select to boot).  What you'll need to do is restore the windows mbr.  Before you restore, unplugging the ubuntu drive from the computer will prevent drive reference errors (you know the question - is (hd0) ubuntu or windows right now) and also prevent windows from overwriting GRUB from the ubuntu drive.

same error when switch drives in bios...i thought getting Grub would have been easyier then going into bios to select drives but i wish i never touched it...I cant load os disks to install uduntu hardy or anyother OS on another drive..i get error 22 for that...

---

### Post by KEE on 2008-08-11
> **KEE said:**
> same error when switch drives in bios...i thought getting Grub would have been easyier then going into bios to select drives but i wish i never touched it...I cant load os disks to install uduntu hardy or anyother OS on another drive..i get error 22 for that...after i change drives in bio's to window xp drive grub says i have an error 5 now =S i did reinstalled windows xp in dos mode, but i cant start it after i boot?!?! grub stops it i am sure and gives me an error 5!! please help!!!

---

### Post by KEE on 2008-08-12
well grub stop loading 7.10 now=S i get error 17 by grub =/ is grub a virus or a horrible bug? i cant get rid of it=/ i tried to change menu.lst but it does frig all and i did the supergrub thing but thats pointless too. i have a new ubuntu installed cause thats the only thing that works but i dont know for how long. luckly i saved all my data but this is a pain in a55. please help here i am dire states and need a rescue =D

---

### Post by sea_monkey987 on 2008-08-12
Well, I'm out of solutions for you since I haven't any experiences with all these grub errors.  Here's my understanding of how GRUB works and how I troubleshoot my GRUB problems (which are caused by my tinckering in the first place BTW).

If all your data is backed up, I can suggest that you remove everything on the drive from gparted and then install ubuntu.  This should fix grub.  This is not an elegant solution but should work.  Sorry

---

