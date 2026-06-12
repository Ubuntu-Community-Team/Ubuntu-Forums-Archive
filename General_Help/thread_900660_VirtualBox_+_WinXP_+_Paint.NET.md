---
title: "VirtualBox + WinXP + Paint.NET?"
date: 2008-08-25
forum: General Help
---

### Post by Znupi on 2008-08-25
Welp, the only application I miss in Linux is Paint.NET (although I'm starting to learn Inkscape, but Paint.NET still rocks). I tried installing mono-paint a while ago and it was pretty much a disaster. It was reeaaaally slow and the top toolbar was inexistent. Now I just found out about VirtualBox (I only knew about VMWare which isn't free) and thought maybe I could run a Windows XP VM when I need Paint.NET. I have a few questions:

1) How fast would this work? Would it be really sluggish? My PC spec: Intel Pentium DualCore 2.80Ghz, 512MB RAM, ATI Radeon X550 512MB RAM Video Card.
2) Do I need a special partition for the VM? From what I know I don't need one, but just making sure.
3) How would I exchange files between the guest OS and the host OS? Do I have to use SMB or some file-sharing program?

I'll post other questions when and if they hit me :)

---

### Post by blop on 2008-08-25
VM server and player are both free, and there is an excellent guide to installing them on the web somewheres..

1. With 512mb of system ram quite slowly, ram wise i would recommended minumum 1gb to run the host and a guest OS. I

2. No...if you end up VM'ing full time get another harddisk to hold the guest OS makes a significant performance boost. But for what you are doing sharing the disc with the host will be fine.

3. You can create shared folders between the host and guest or you could set up a network share on the XP machine and browse to it in the network menu as normal....or set yourself up a samba share on your ubuntu box.

---

### Post by Znupi on 2008-08-25
> **blop said:**
> VM server and player are both free, and there is an excellent guide to installing them on the web somewheres..
So which one is recommended? Which one would be faster? I don't know why but my gut tells me to go for VirtualBox (although my gut can be wrong at times).
> **blop said:**
> 1. With 512mb of system ram quite slowly, ram wise i would recommended minumum 1gb to run the host and a guest OS. I
I know that's pretty low, it's the only thing that bugs me about my system. But I can't upgrade it right now. I suppose I could split the ram and give 256mb to each OS? Would that be OK?
> **blop said:**
> 2. No...if you end up VM'ing full time get another harddisk to hold the guest OS makes a significant performance boost. But for what you are doing sharing the disc with the host will be fine.
Thanks. But does it make any difference what file system the partition on which the VM will run uses? Does it have to be NTFS?

Thanks a lot for the reply! :)

---

### Post by Znupi on 2008-08-26
Well, I went with VirtualBox, and it works so good!! Well, it didn't work the first time, after installing Windows I tried installing the .NET framework at which point Windows gave an "Unknown Hard Error" and shut down. I tried restarting and it would say that it can't find WINDOWS\system32\hal.dll. So I booted a Ubuntu Live CD in the VM to try and see what was the problem, and the WINDOWS, Documents and Settings and Program Files folders appeared empty. When I tried to ls in them it said I/O Error. I tried reinstalling Windows on the same virtual disk but it would say it can't format the partition because there was some I/O Error :-\. I deleted the virtual disk, created another one and installed Windows on that, made backups, and now everything works (including Paint.NET -- EXCELLENT!!) :-) It was easy like pie really, I was expecting it to be a lot harder.

If anyone's interested, I'm giving Windows 192MB RAM (that's what vbox recommended) and 64MB Video (vbox recommended 4 :-\).

---

### Post by Garratt on 2008-08-26
VMware server is good, VMWare player only "PLAYS" virtual machine's it doesn't create them. So to use a XP VM you would need to download one.

Vmware supports drag and drop, unfortunately VBOX is not quite there yet, but you can share folders like the above poster stated.

Personally i'd go vbox cause its 'sun' and anything they make is awesome, or turns out awesome after a few years of dev.

but on the other hand vmware has been around a lot longer and is more stable than Vbox, so really it's just personal preference.

> Well, I went with VirtualBox, and it works so good!! Well, it didn't work the first time, after installing Windows I tried installing the .NET framework at which point Windows gave an "Unknown Hard Error" and shut down. I tried restarting and it would say that it can't find WINDOWS\system32\hal.dll. So I booted a Ubuntu Live CD in the VM to try and see what was the problem, and the WINDOWS, Documents and Settings and Program Files folders appeared empty. When I tried to ls in them it said I/O Error. I tried reinstalling Windows on the same virtual disk but it would say it can't format the partition because there was some I/O Error :-\. I deleted the virtual disk, created another one and installed Windows on that, made backups, and now everything works (including Paint.NET -- EXCELLENT!!)  It was easy like pie really, I was expecting it to be a lot harder.

If anyone's interested, I'm giving Windows 192MB RAM (that's what vbox recommended) and 64MB Video (vbox recommended 4 :-\).

Yea vm's don't actually partition disks, its just an emulated partition(i think) on a real partition, so reinstalling is a bad idea, usually a lot better to just delete and re-install.

I would up the ram a bit to about half of whatever ram you have, usually it's good to double whatever is the suggested specs.
but in your case i think 256mb ram would be good... depends if it's working fine then theres no real need to play with it.

---

### Post by Znupi on 2008-08-26
> **Garratt said:**
> Vmware supports drag and drop, unfortunately VBOX is not quite there yet, but you can share folders like the above poster stated.
I never actually use drag & drop, so no loss for me :P.
> **Garratt said:**
> Personally i'd go vbox cause its 'sun' and anything they make is awesome, or turns out awesome after a few years of dev.
Yeah that's what I thought, too.
> **Garratt said:**
> but on the other hand vmware has been around a lot longer and is more stable than Vbox, so really it's just personal preference.
VBox seems pretty stable so far, except for the first mishap. It's pretty fast, too.
> **Garratt said:**
> Yea vm's don't actually partition disks, its just an emulated partition(i think) on a real partition, so reinstalling is a bad idea, usually a lot better to just delete and re-install.
I know, they basically create a file which the guest OS sees as a partition. Probably that file got corrupted somehow :-\. I'm starting to wonder if it was a Windows or a VBox bug :P.
> **Garratt said:**
> I would up the ram a bit to about half of whatever ram you have, usually it's good to double whatever is the suggested specs.
but in your case i think 256mb ram would be good... depends if it's working fine then theres no real need to play with it.
It's pretty snappy so far, plus I don't use it intensively (I just keep Paint.NET open and that's pretty much it). If it'll start to slow down I'll give it some more :). It's curious that it works so well since the Paint.NET website specifies minimum 256MB and 512MB recommended. Probably the dual core CPU makes up for it :)

I also found VirtualBox to be extremely easy to use :)

---

