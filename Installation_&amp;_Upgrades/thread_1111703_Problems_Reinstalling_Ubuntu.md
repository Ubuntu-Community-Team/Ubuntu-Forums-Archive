---
title: "Problems Reinstalling Ubuntu"
date: 2009-03-30
forum: Installation &amp; Upgrades
---

### Post by deeptendu on 2009-03-30
I've been running ubuntu for about half a year now (hardly an expert), but lately I've had a few problems with my computer most likely from a virus. I'm trying to currently reinstall ubuntu but when I put in the disk and select reboot, it never shuts down...and when I select "reboot manually later" and then restart my computer, it just restarts as normal. I tried to install the version of Vista that came with the computer to see if it would work, but it also would neither reboot on it's own or come up if I restarted the computer. When I tried to install Ubuntu without the CD using the terminal I got the following message:

[COLOR="Red"]deeptendu:~$ sudo apt-get install debootstrap
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
[/COLOR]

Does anyone know what I should do?

---

### Post by Mark Phelps on 2009-03-31
You wouldn't have a problem with a virus in Ubuntu; you would only have that in Vista -- which is not a problem for these forums.

You didn't say anything about your current configuration. Are dual-booting with Vista and Ubuntu? Or are you running Vista and have installed Ubuntu inside it using Wubi?

You didn't say anything about the version of Ubuntu you're using.

Did you set the BIOS to boot first from the CD/DVD drive?

The Linux error message indicates that you interrupted it during a package install, or that the machine shutdown during a package install.  The thing to do is open a terminal and enter the command it provided.  Make sure you put "sudo" before the command or it won't work.

---

### Post by deeptendu on 2009-03-31
I don't have Vista or any other OS installed on my computer. 
I thought it was a virus, but I don't know for sure. I downloaded some music-> my computer started acting up-> A virus came up when I scanned those files-> I assumed it was a virus. It is possible that I screwed something up when trying to get my wireless internet card to work (it still doesn't) which I think may have been around the same time.

I'm running Ubuntu 8.04 (64-bit) on an AMD 64.

I don't quite understand your question about booting first from the cd drive. I inserted the cd, selected to install it by rebooting, I left the computer, it never rebooted on it's own. I selected to install it and reboot it manually, I rebooted my computer, it turned on as usual.

I managed to install debootstrap, but gparted won't let me make a new partition. I have 60 gigs of avaliable space, but it won't let me select it. And the options along the top (new, delete, resize, move, ect.) remain grayed out.

I'm sorry I don't quite know what I'm doing (probably why I'm here in the first place), and I'm very gracious for your help.

---

### Post by Mark Phelps on 2009-03-31
> **deeptendu said:**
> A virus came up when I scanned those files-> I assumed it was a virus.

A virus in Linux? What did you scan them with in Linux that claimed it found a virus?

> 
It is possible that I screwed something up when trying to get my wireless internet card to work (it still doesn't) which I think may have been around the same time.

It's possible -- but highly unlikely.

> 
I don't quite understand your question about booting first from the cd drive. I inserted the cd, selected to install it by rebooting, I left the computer, it never rebooted on it's own. I selected to install it and reboot it manually, I rebooted my computer, it turned on as usual.

I got the impression you were saying that you put the CD/DVD in the drive and your machine would not boot from it.  So, I wanted to make sure you set your BIOS to boot from the CD/DVD drive.

> 
I managed to install debootstrap ...

Haven't used this -- can't help. Don't build my own package sets -- just use the ones available through the repositories.

If you need help installing with a custom-built set of packages, that's a lot more than I can handle.

Sorry.

---

### Post by deeptendu on 2009-03-31
It was Avast that found the virus. It's been awhile though so I don't remember anything about it other than it being a music file.

---

### Post by Mark Phelps on 2009-04-01
Sorry, I must not be asking the questions properly because your answers keep confusing me ...

You said 
> I don't have Vista or any other OS installed on my computer. 

But then you said
> 
I'm running Ubuntu 8.04 (64-bit) on an AMD 64.

So if you don't have any OS installed, how can you be running Ubuntu 8.04?

As to the "virus", you said
> 
I thought it was a virus, but I don't know for sure. I downloaded some music-> my computer started acting up-> A virus came up when I scanned those files-> I assumed it was a virus. 

You also said that you scanned the files with Avast -- I'm presuming this was the Avast Linux Home Edition, right?

While it's certainly possible for a virus to infect Linux, it's very difficult to do that and highly unlikely.  What's more likely is that you downloaded music that was copyrighted or otherwise had DRM info in it and Avast flagged this as a virus.  The AV vendors are famous for flagging keygens, cracks, and other such stuff as viruses.

I'm still not clear whether you have your BIOS set to boot first from the CD/DVD drive.  You said
> 
I inserted the cd, selected to install it by rebooting, I left the computer, it never rebooted on it's own. I selected to install it and reboot it manually, I rebooted my computer, it turned on as usual.

Booting from the Ubuntu CD doesn't install anything, it merely presents a menu from which you can choose to run Ubuntu in live mode or install it.  IF you insert the CD while running an OS, it will also launch the CD, but that's not the same as booting from it.  Need to know if you set your BIOS to boot from the CD/DVD drive.

As to the new partition, you said
> 
gparted won't let me make a new partition. I have 60 gigs of avaliable space, but it won't let me select it. And the options along the top (new, delete, resize, move, ect.) remain grayed out.

It's not available space you need, it's unallocated space. In the Partition Edit, the Partion id will have "unallocated" and the Filesystem type will have "unallocated". If you don't have unallocated space, you will have to shrink (resize) and existing partition to make space. The partition actions are greyed out until you select a partition.  

Need to see your partition layout, so please open a terminal and typ[e "sudo fdisk -lu" (that's a lower-case L, not a one).

---

