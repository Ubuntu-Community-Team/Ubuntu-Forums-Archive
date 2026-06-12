---
title: "I need Help Installing Windows... Bear with me! Its for Dual Boot!"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by gta117 on 2009-05-07
Ok, I have Ubuntu 9, but I need really bad to install my windows xp back on the other hardrive. I have several partitions set up because I was going to dual boot, but got lazy. Now I have run into a problem.

My problem is this: I have a HP computer with its hidden recovery drive active still. When I select it for my start up to get things going, it says it can not even partition. I do not have all the CD's, as someone moved a few a long time ago and now there gone for good. Its a OEM computer.


It wants a NTFS part. to mount, but when I was trying to part. stupid ubuntu would not let me split the NTFS, instead I had to delete it, and make a bunch of parts. Then when I wanted to make a NTFS part for the dual boot back when I was installing Ubuntu, it would not let me!


Full swing around: Now When I try and change this fat32 drive that was set up for windows, it will not format to ntfs. Its in grey. How gay.


So I am so stuck, and I really need to get xp up by tomorrow. Any help with be a Big help. I still want ubtuntu! :D



Thank you!!!

-gta117

---

### Post by HyRax on 2009-05-07
What do you need Windows for? Aside from games, there should be little reason to reinstall it.

---

### Post by gta117 on 2009-05-07
> **HyRax said:**
> What do you need Windows for? Aside from games, there should be little reason to reinstall it.


OMG I knew I would get this response first. >_< Gah!


Ok, its for a game, and some important things I need that only works on Windows. 

So this is very important, and I do need it up. Thank you, and sorry if I sound pushy, I do not mean to!!!


-gta117

---

### Post by HyRax on 2009-05-08
OK, is this game of yours OpenGL? If so, then consider using Windows in a Virtualbox VM instead - Virtualbox 2.2 can do OpenGL 3D quite well, and when it gains official DirectX support, there will be no need to ever have a dual-boot installation ever again.

I maintain a dual-boot setup purely for games, but of late I haven't touched Windows in ages because i now have a PS3. I fire up my Windows VM on occasion to deal with stuff for work, but that's it.

---

### Post by gta117 on 2009-05-08
> **HyRax said:**
> OK, is this game of yours OpenGL? If so, then consider using Windows in a Virtualbox VM instead - Virtualbox 2.2 can do OpenGL 3D quite well, and when it gains official DirectX support, there will be no need to ever have a dual-boot installation ever again.

I maintain a dual-boot setup purely for games, but of late I haven't touched Windows in ages because i now have a PS3. I fire up my Windows VM on occasion to deal with stuff for work, but that's it.


No, it is M.A.N. 2, and I have some things that will not work on ubuntu that I need for mothers day, and I need to finish some things up on it. :/ Time is my enemy right now.


Do you think you might be able to help me? or anyone for that matter?

-gta117

---

### Post by HyRax on 2009-05-08
> **gta117 said:**
> No, it is M.A.N. 2, and I have some things that will not work on ubuntu that I need for mothers day, and I need to finish some things up on it. :/ Time is my enemy right now.


Do you think you might be able to help me? or anyone for that matter?

-gta117

OK, well obviously you don't need the game for Mothers Day. The fastest way to get up and running again will be to install Virtualbox and get Windows running inside that. Do the stuff that you need to do that is Windows specific and then sort out your native boot issues later.

However, your problem at the moment is that you do not have the Windows CD's and clearly the HP Factory Recovery partition is stubborn enough to assume that you won't repartition your drive.

Some recovery partitions give you the option to create the Windows CD(s) so that you can install that way instead of via the recovery partition. If you have that option then do that, otherwise trot down to your local PC shop and ask if they have an OEM copy of Windows handy. It should be legal for them to give you the disc because you actually buy the CD key, not so much the software itself.

In my case, I keep an OEM WinXP SP3 install disc from a Dell PC handy. I don't use it on a Dell, but it installs perfectly well on anything I use it with. All I then do is apply the purchased CD key for that installation and it makes it nice and legal.

---

### Post by gta117 on 2009-05-08
> **HyRax said:**
> OK, well obviously you don't need the game for Mothers Day. The fastest way to get up and running again will be to install Virtualbox and get Windows running inside that. Do the stuff that you need to do that is Windows specific and then sort out your native boot issues later.

However, your problem at the moment is that you do not have the Windows CD's and clearly the HP Factory Recovery partition is stubborn enough to assume that you won't repartition your drive.

Some recovery partitions give you the option to create the Windows CD(s) so that you can install that way instead of via the recovery partition. If you have that option then do that, otherwise trot down to your local PC shop and ask if they have an OEM copy of Windows handy. It should be legal for them to give you the disc because you actually buy the CD key, not so much the software itself.

In my case, I keep an OEM WinXP SP3 install disc from a Dell PC handy. I don't use it on a Dell, but it installs perfectly well on anything I use it with. All I then do is apply the purchased CD key for that installation and it makes it nice and legal.

OMG dude I took your advice and now I can not start with Ubuntu :(

I went to extra options in the HP recov, it wanted me to restart to get extra options. I did it and now every time I start up Hp recov comes on, not grub so I can select ubuntu!

NOOOOOOOO!!!!!!!!! Please help me out of this mess! >_< Gah, I hate my luck man.

-gta117

---

### Post by HyRax on 2009-05-08
> **gta117 said:**
> OMG dude I took your advice and now I can not start with Ubuntu :(

I went to extra options in the HP recov, it wanted me to restart to get extra options. I did it and now every time I start up Hp recov comes on, not grub so I can select ubuntu!

NOOOOOOOO!!!!!!!!! Please help me out of this mess! >_< Gah, I hate my luck man.

-gta117

Wow - how old is your PC? That recovery partition is doing the crappiest method of starting up by installing a new bootloader to start the recovery partition process and then restores a Windows one to allow WIndows to start again - geez. No fault on your part - it's badly written software that assumes you'd never use anything other than Windows on that box.

You need to reinstall GRUB. There are other threads on this forum that illustrate how to do this. You will need to boot up on an Ubuntu LiveCD to do this.

---

### Post by felicat on 2009-05-08
he is correct, you may call to HP to ask for a OEM disk for Windows installation. It's what my friend did last month and she got hers on hand now (heard like she was ordering 1 more disk for me too XD though i am not HP user). But Mother's day is coming up this weekend, can HP mail you the disk on time? I wonder... but you may try to get one from your nearest HP service center or call their hotline or try local retail store (but i wonder whether the retail shop keeps a disk for people like you)

---

### Post by gta117 on 2009-05-08
> **felicat said:**
> he is correct, you may call to HP to ask for a OEM disk for Windows installation. It's what my friend did last month and she got hers on hand now (heard like she was ordering 1 more disk for me too XD though i am not HP user). But Mother's day is coming up this weekend, can HP mail you the disk on time? I wonder... but you may try to get one from your nearest HP service center or call their hotline or try local retail store (but i wonder whether the retail shop keeps a disk for people like you)


I got my computer 4 years ago. Its a pavilion you know? 643n or what ever. 64 amd. 


Anyways, how do I install grub? 

Also, how can I install windows? Can I just format the hardrive all but the recov and then install windows, then install ubuntu again?

Thanks!

-gta117

---

### Post by HyRax on 2009-05-08
> **gta117 said:**
> Also, how can I install windows? Can I just format the hardrive all but the recov and then install windows, then install ubuntu again?


Yes, yes and yes. But you don't have to format - just let the Windows installer do its thing and then let the Ubuntu installer do its thing.

---

### Post by felicat on 2009-05-08
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

or if you really indeed reinstall windows, get windows 7 RC then redo everything again. at least you can have a disk to do all those install-remove-reinstall steps.

---

### Post by Sef on 2009-05-08
For dual booting read  [Psychocats]("http://psychocats.net/ubuntu").

---

### Post by felicat on 2009-05-08
> **Sef said:**
> For dual booting read  [Psychocats]("http://psychocats.net/ubuntu").

good src! thanks a lot.

---

