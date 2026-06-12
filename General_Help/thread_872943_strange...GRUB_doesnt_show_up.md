---
title: "strange...GRUB doesnt show up"
date: 2008-07-28
forum: General Help
---

### Post by benbenny on 2008-07-28
Hi, I tried searching a solution to this but couldnt find anything analogous.

I installed Ubuntu 8.04 LTS last night for the first time in Dual boot with win Vista. At first everything worked perfectly. GRUB menu would launch at startup showing Ubuntu, Ubuntu recovery and Ubuntu memtest. I booted into Vista and Ubuntu a couple of time to see that everything was working fine, it was. 

Last things I did last night was install some updates that I was prompted to in Ubuntu upon the completion of the installation, enabled my graphics card (NVIDIA), installed flash, and enabled extra software repositories. 

Since this morning though, after I push the startup button all I get is a dark screen, GRUB menu doest show-up, and after a few minutes I go straight into Ubuntu. I dont get any of the usual startup screens such as when you have the possibility to push F12 to go to the boot menu and as I said no GRUB menu, just a dark screen. Then if I try to  restart ubuntu from within Ubuntu all I get is the dark screen again and the computer doesnt shut down by itslef. 

Ubuntu seems to work fine otherwise, all the partitions seems to be in place and functioning. I can mount the Vista partition and access it.

Going into sudo gedit/boot/grub/menu.slt  I made sure there was a hash infront of hiddenmenu. there is. Thats all I know what to do so far. I thought about changing the default in the GRUB menu to vista to see if it would boot Vista but then I thought that i had no idea how to edit the GRUB menu from vista so then I would be stuck without being able to return to Ubuntu and in any event its not a solution to the problem. So im just going to hope someone smarter than me gives me some advise. 

System im running on is a Toshiba Satellite A100-543 laptop. I dont know what other info I should give - just let me know and Ill provide it. 

would really appreciate any help cause I really have no idea what to do.

---

### Post by Vakman on 2008-07-28
This site should help you [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
Follow what it says to do. If that does not work then come back here :)

---

### Post by louieb on 2008-07-28
Thats a new one to me.  See what the** timeout** value is? 
Did you try to add a splahimage? 

Press the <esc> during boot to see if that gives you the menu.

My favorite way to make widows the default OS is to copy the windows menu entry  between  the lines that read.  
```

# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
 
```
You'll see some examples just before these lines. 

Haven't tried **startupmanager **but have heard it offers a GUI way of modifying menu.lst

Welcome to Ubuntu:)

---

### Post by benbenny on 2008-07-28
thnks!

treid to press esc during startup - doest work. the strange thing is that everything was working fine before. the grub menu did launch and in boot/grub/menu.lst there is a hash before "hiddenmenu"

im not trying to make windows boot by default. thats not the problem. but I would like to be able to access the normal startup windows upon startup, and to be able to access the grub menu to chose between ubuntu and windows...

louieb,    in   [https://help.ubuntu.com/community/Re...tallingWindows](https://help.ubuntu.com/community/Re...tallingWindows) which one of these methods should I use? 
I tried "from inside Ubuntu" and "recovering Grub manually" (cant do the automatic recovery cuase I dont have a /boot partition)   but in the former the command  "./grub" was not found  and in the latter   sudo /sbin/grub  command was not found (I have a feeling im making a stupid mistake here).

I havent treid using the Live CD method yet cause I dont have it here and I would have to wait till later tonight to get it, and besides I was hoping there would be a simpler fix to this.....?

cheers

---

### Post by louieb on 2008-07-28
Don't think that page really address you problem since it boots Ubuntu.
That means GRUB is installed and setup correctly - Ubuntu can't boot without it. (or some other boot manager).   

Sound more like GRUB is having some video problem. Changing the  default to boot VISTA would confirm that.

Since I've never seen your problem. 1st thing I would do is get a [Super Grub Disk  ]("http://forjamari.linex.org/projects/supergrub/") and make sure it works. 

Then go into System>Applications>Synaptic Package Manager. 
Search for and reinstall the GRUB package.  
Just a shot in the dark but maybe after a reinstall GRUB will get its video problems straightened out. 
Good Luck.

---

### Post by Vakman on 2008-07-28
No, it does not address the problem but on that page it talks about using a Super GRUB disk. I figured it was easier to go there where it would at least explain the disk to him a little bit. [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) is the site for the disk if you like.

---

### Post by benbenny on 2008-07-29
thanks guys, everyting is back to normal now. Dont khow how it got fixed but something that I did when trying to follow the instructions on [https://help.ubuntu.com/community/Re...tallingWindows](https://help.ubuntu.com/community/Re...tallingWindows)   did the trick.  No idea what but im happy as long as it stays this way . cheers. im off to figuring out something else... Linux is a lot of work! hope it pays off... :)

---

### Post by louieb on 2008-07-29
> **Thisislaw said:**
> This site should help you.. []("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

> **louieb said:**
> Don't think that page really address you problem ...
:guitar: Looks like I've stuck my foot in mouth again. 

Glad you got it going again benbenny.

---

### Post by Vakman on 2008-07-30
> **louieb said:**
> :guitar: Looks like I've stuck my foot in mouth again.
:lolflag: 
Glad you got it to work :)

---

