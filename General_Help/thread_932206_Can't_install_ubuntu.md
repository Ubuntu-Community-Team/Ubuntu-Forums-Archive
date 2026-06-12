---
title: "Can't install ubuntu"
date: 2008-09-28
forum: General Help
---

### Post by destructaball on 2008-09-28
Hi there,
I have an old laptop with XP installed and I want to install ubuntu on it but I am locked out of windows because it is an old work laptop which seems to need a network connection to login and I can't log in locally. Whats worse is that there is no floppy, or CD drive and it cannot boot from USB as far as I can tell. I'm fairly handy with computers and I have no idea how to solve this any help would be greatly appreciated.

---

### Post by lian1238 on 2008-09-28
> **destructaball said:**
> Hi there,
I have an old laptop with XP installed and I want to install ubuntu on it but I am locked out of windows because it is an old work laptop which seems to need a network connection to login and I can't log in locally. Whats worse is that there is no floppy, or CD drive and it cannot boot from USB as far as I can tell. I'm fairly handy with computers and I have no idea how to solve this any help would be greatly appreciated.

How did you install Windows XP in the first place?? I don't know if you can take the harddisk out, install in on another computer, and put it back. Would it mess up the drivers, I don't know.

---

### Post by MunkyJunky on 2008-09-28
You could always try a network install? Presumably it has an ethernet port. I don't know the details of network boots though, so I ca't help much more than that. Try having a read around it, see it if could work for you.

---

### Post by kokkus on 2008-09-28
It's not possible with a laptop without a CD Rom driver.
And it's not possible to have windows xp on it without a CD rom.
OK double check if you are right about the facts.
A laptop without a cd rom driver sounds really strange.
You could use a memory stick to install ubuntu.
Since you are not able to boot from your PC I would format it first.

Could you take a video with your mobile when you start the PC and how everything goes there, upload it to youtube with the PC you are logged on now and post the link here? That could help.

---

### Post by destructaball on 2008-09-28
Its an old work laptop that they didn't need any more and god only knows why it doesnt have a CD drive. The only thought I've had is that it can log into windows networks and maybe if i make a windows network i could make myself an admin account on that PC and then use the Wubi installer but i have no idea how to acheive that (and this probly isnt the right forum to ask about that. Any other ideas is it possible to change the bios so it accepts booting from USB or put a CD drive in (I'm not quite sure how that would work. And I already tried to put the hard drive into a different laptop to put ubuntu on it but the hardrive didnt fit in even though they were both made by dell.

Sorry i may not have been clear earlier I can boot but only into the login screen of windows. Thanks for the help so far.

---

### Post by lian1238 on 2008-09-28
Go into the bios setup and look for boot order. If there is a USB option, there may still be luck. But since it's old, I don't think they had it back then. Won't hurt to check though.

---

### Post by fooman on 2008-09-28
are you able to get into safemode (press f8 as it boots to get to boot menu options) ?

---

### Post by destructaball on 2008-09-28
Yes I can go into safemode and no it doesnt boot from USB but it was worth a try.

---

### Post by kokkus on 2008-09-28
Don't u have any usb ports on your laptop?
BUt tell us, how did u install winxp on it in the first place?

And another thing. If you do not have cdrom, usb, floppy or any kind of inputs on your pc, I can't really see why you wanna install ubuntu on it and how the pc can be usefull.
Well, that's your business but I would buy a new one insted of going thrue all these problems.

---

### Post by destructaball on 2008-09-28
It does have USB it just doesn't have a boot option for USB like all fairly old laptops and I'm a little short of money joys of student life :P. I didn't install XP (who in their right mind would) my dad got it from his old work and they didnt want it back but my dad doesn't know the password so he gave it to me. Its a very long story.

---

### Post by fooman on 2008-09-28
can you change the admin password in safemode?

...if its home version,  you may be able to.  if its pro (most likely since its from your dads work),  then probably not.

---

### Post by taladan on 2008-09-28
It was probably initially installed via a network install of XP using an RIS or something similar, or even from a usb cdrom drive.

I can see plenty of use for a laptop without cdrom/floppy/usb if you wanted to use it as a general netbook and with SSH or NFS over to a main system/desktop it's not a problem to get files to and from it.

What I would suggest is looking into doing a network install of ubuntu, it'll take a little more configuration (and probably a good bit of your known supply of curse words ;) ) to get it installed, but as a sunday project, it's a good one. 

First thing though, you need to check the bios and see if:
[LIST]
[*]Does it have the usb boot capability - this will be easier than a network install
[*]Does it have an option to boot from the ethernet port - pxe or something similar
[*]Does it have a working ethernet port
[/LIST]

If you don't have a bootable USB option and you do have network boot capability and a NIC that works on that laptop, then you'll want to do something like this:
[http://ubuntu-tutorials.com/2007/10/08/how-to-install-ubuntu-locally-over-the-network/]("http://ubuntu-tutorials.com/2007/10/08/how-to-install-ubuntu-locally-over-the-network/")

Or follow any of the other varied network install tutorials out there on the web.

Hope this helps,

Tal

---

### Post by kokkus on 2008-09-28
I guess theres only 1 way for u to install ubuntu.
If u have a memory USB stick or a external hard disk driver you can put Wbui (windows based ubuntu installer) on it, and install it from your windows xp. [http://wubi-installer.org/](http://wubi-installer.org/)
But go buy you self an external USB CD Rom driver.

---

