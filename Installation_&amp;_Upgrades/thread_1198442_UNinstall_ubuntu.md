---
title: "UNinstall ubuntu"
date: 2009-06-27
forum: Installation &amp; Upgrades
---

### Post by thedoommaker on 2009-06-27
Linux noob is here! 
I have installed ubuntu 9.04 on my second harddisk (D). 
(C has Windows.) 
D was not an empty disk 
and I allocated 20 GB of space for ubuntu to install. 
Ubuntu did the rest. 
Now I want to uninstall ubuntu and no trace of it left on D. 
(not that I am sick of it, just because I want to try out different distros) 
The problem is; 
D is also full of 200 gb of various files that I dont want to lose.
 
1- Is it possible to erase/uninstall ubuntu on D completely and not leave a trace? (without doimg damage to the rest of the disk)
2- Will windows once again accept and embrace that 20 gb of space which it ignores at the moment?
3- Once I uninstalled ubuntu, will I get the dual boot screen again? I've read that things like that happen. 
4- Is it a good idea to install XP and any distro of linux, say kubuntu, on the very same disk? 

thanks in advance!

---

### Post by mikewhatever on 2009-06-27
Did you install Ubuntu using the inside Windows option? I;m assuming you did while answering the questions.

> **thedoommaker said:**
> 
 
1- Is it possible to erase/uninstall ubuntu on D completely and not leave a trace? (without doimg damage to the rest of the disk)

That's what Windows uninstaller is for.

> 2- Will windows once again accept and embrace that 20 gb of space which it ignores at the moment?

It should.

> 3- Once I uninstalled ubuntu, will I get the dual boot screen again? I've read that things like that happen.

You shouldn't see it, but things happen, and in that case, you'll need to manually edit the boo.ini file.

> 4- Is it a good idea to install XP and any distro of linux, say kubuntu, on the very same disk? 

thanks in advance!

Hm..., what do you mean by 'good idea'?

---

### Post by philcamlin on 2009-06-27
you can uninstall if you used wubi :popcorn:

---

### Post by raymondh on 2009-06-27
Yes it's possible.  Back up first.... as murphy may show up and create havoc.

If you are now ready to install another distro, you can just point the installation to the ubuntu partition and it will overwrite that.

If not ready, you can use gparted (from the liveCD) or windows' disk management tool to erase the linux partition as well as its' extended partition (if so installed).  From there, you can choose to extend the remaining to occupy the now empty space or leave it unallocated for your next adventure.  

After that operation (deleting), you will have to restore the MBR in order to boot into windows again.  When you installed Ubuntu, it also installed/overwrote the MBR.  Restoring the MBR takes a few steps. Easiest is if you have the original install disc.

In XP,

Boot into the the original install disc > select R (repair) > select your system > you may need to type in a admin password but most often, just press enter > at command prompt and type 'fixmbr' (no quotes) > exit.

In Vista

Boot into the original install disc and go through the language selection > select Computer Repair > select command prompt > type "bootrec.exe/fixboot' and let it happen > type 'bootrec.exe/fixmbr' (no quotes on both) > exit.

If you do not have the orginal install disc ...

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

Some reference materials for reading:

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://members.iinet.net.au/~herman546/p18.html](http://members.iinet.net.au/~herman546/p18.html)

Good luck.  Back up your files first.

EDIT : this is for a true DUAL-Boot with windows and ubuntu installed in its' own partitions ... not WUBI installed

---

### Post by thedoommaker on 2009-06-27
I didnt install ubuntu in windows, I dont see an Ubuntu entry in the windows uninstaller.
Here's what I did: 
I booted into the Ubuntu LiveCD to see what it looks like.
I liked it and clicked on the Install shortcut on the Ubuntu desktop.
I answered some questions about date and time, language.
The partitioner started up. I allocated 20 gb of space for ubuntu in D drive. 
I guess this is not Wubi install if that's what it is called. (Installing ubuntu in windows)
what I was trying to do was to install Ubuntu as a seperate OS. 
now I want to remove it. 

thanks again.

---

### Post by mikewhatever on 2009-06-27
> **thedoommaker said:**
> I didnt install ubuntu in windows, I dont see an Ubuntu entry in the windows uninstaller.
Here's what I did: 
I booted into the Ubuntu LiveCD to see what it looks like.
I liked it and clicked on the Install shortcut on the Ubuntu desktop.
I answered some questions about date and time, language.
The partitioner started up. I allocated 20 gb of space for ubuntu in D drive. 
I guess this is not Wubi install if that's what it is called. (Installing ubuntu in windows)
what I was trying to do was to install Ubuntu as a seperate OS. 
now I want to remove it. 

thanks again.

I see. In that case, you simply need to delete the Ubuntu related partitions, but first, restore the Windows bootloader (raymondhenson posted some instructions in a post above). That done, boot the live cd again, go to System->Admin->Gnome Partition Manager, and delete the unneeded partitions.

---

### Post by thedoommaker on 2009-06-27
> **raymondhenson said:**
> Yes it's possible.  Back up first.... as murphy may show up and create havoc.

If you are now ready to install another distro, you can just point the installation to the ubuntu partition and it will overwrite that.

If not ready, you can use gparted (from the liveCD) or windows' disk management tool to erase the linux partition as well as its' extended partition (if so installed).  From there, you can choose to extend the remaining to occupy the now empty space or leave it unallocated for your next adventure.  

After that operation (deleting), you will have to restore the MBR in order to boot into windows again.  When you installed Ubuntu, it also installed/overwrote the MBR.  Restoring the MBR takes a few steps. Easiest is if you have the original install disc.

In XP,

Boot into the the original install disc > select R (repair) > select your system > you may need to type in a admin password but most often, just press enter > at command prompt and type 'fixmbr' (no quotes) > exit.

In Vista

Boot into the original install disc and go through the language selection > select Computer Repair > select command prompt > type "bootrec.exe/fixboot' and let it happen > type 'bootrec.exe/fixmbr' (no quotes on both) > exit.

If you do not have the orginal install disc ...

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

Some reference materials for reading:

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://members.iinet.net.au/~herman546/p18.html]("http://members.iinet.net.au/%7Eherman546/p18.html")

Good luck.  Back up your files first.

EDIT : this is for a true DUAL-Boot with windows and ubuntu installed in its' own partitions ... not WUBI installed

great! this covers it all
and thank you all for your time

---

### Post by urofan on 2010-02-26
> **raymondh said:**
> Yes it's possible.  Back up first.... as murphy may show up and create havoc.

If you are now ready to install another distro, you can just point the installation to the ubuntu partition and it will overwrite that.

If not ready, you can use gparted (from the liveCD) or windows' disk management tool to erase the linux partition as well as its' extended partition (if so installed).  From there, you can choose to extend the remaining to occupy the now empty space or leave it unallocated for your next adventure.  

After that operation (deleting), you will have to restore the MBR in order to boot into windows again.  When you installed Ubuntu, it also installed/overwrote the MBR.  Restoring the MBR takes a few steps. Easiest is if you have the original install disc.

In XP,

Boot into the the original install disc > select R (repair) > select your system > you may need to type in a admin password but most often, just press enter > at command prompt and type 'fixmbr' (no quotes) > exit.

In Vista

Boot into the original install disc and go through the language selection > select Computer Repair > select command prompt > type "bootrec.exe/fixboot' and let it happen > type 'bootrec.exe/fixmbr' (no quotes on both) > exit.

If you do not have the orginal install disc ...

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

Some reference materials for reading:

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://members.iinet.net.au/~herman546/p18.html](http://members.iinet.net.au/~herman546/p18.html)

Good luck.  Back up your files first.

EDIT : this is for a true DUAL-Boot with windows and ubuntu installed in its' own partitions ... not WUBI installed
Raymondh, you are a life saver. Thanks much for the info on how to fix my Vista install. I was starting to freak out.

---

### Post by raymondh on 2010-02-26
> **urofan said:**
> Raymondh, you are a life saver. Thanks much for the info on how to fix my Vista install. I was starting to freak out.

Glad you have your Vista working.   Happy ubuntu-ing :)

Raymond

---

