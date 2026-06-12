---
title: "Dual-booting and shared drives"
date: 2008-11-18
forum: Hardware
---

### Post by Mostly Harmless Eccentric on 2008-11-18
Hello, all. Glad to meet you, and more than relieved to find there's a nice, active community. I'm not really a newbie anymore, but I'm certainly less than a seasoned master. So go slow, please. :) Anyways, I've got a little project in mind I'd like your esteemed input on. 

First, what I've got here to start: I've got one laptop running Hardy. At the moment, there's about 8GB swap space, and just shy of 250GB in Ubuntu's partition, with about 60GB actually occupied.

Second, what I'm doing and why: I've been very satified with Linux's functionality as a media sort of system, and want to keep it on as such, since it's very useful to have most things organized and friendly the way Ubuntu tends to arrange it, but to be able to access that extra power and customizability when it's needed. But a couple years ago, I'd started picking up some languages and writing some basic code, before other obligations squeezed out my new hobby. I've been wanting to get back into it, and so I wanted to dual boot with another distro, likely Red Hat, since I wanted something a little more specialized for the job, and something where that wouldn't have all my music and PDF books and games to distract me. I want essentially Ubuntu for playing around and media, Red Hat for technical tasks. However, I need them to share files. For example, I make a sound effect in Audacity on Ubuntu, then I'll want to send it to Red Hat to be used in whatever I'm working on. I don't want to have to copy all this stuff and have it exists in two places on the hard drive and waste space. So I decided on an extra partition just for data, that'll be ext3.

So what I'm planning to do is to have Ubuntu and Red Hat (probably. Not set in stone, any other distro suggestions are appreciated!) in their own partitions, then the swap partition (likely containing two logical partitions, one for each distro, since I'm on a laptop) and then the fourth partition to be my shared data. I'll mount that shared drive, thus having only one copy of the data accessible to both.

So, before I jump right in on this, I'd just like to ask a couple questions, please:

First and foremost, does anyone see any glaring errors in my plan, potential issues down the road, or otherwise have any suggestions? I'm particularly concerned about permissions on the shared files, and problems I've heard of with Grub regarding setups like this (usually something aout an error 22?)

Second, I'd like the Ubuntu that will reside on the new partition to be (nearly) exactly the same as now. I just got it working the way I like it. :) I'd like to be able to do a more efficient backup than simply saving all my various files and folders I'll need to transfer. Ideally, I'd like to be able to mirror the entire thing, say to an external hard drive, then mirror it back on to the new partition, producing a copy what I have now. Is this possble? If so, would I need one to fit the entire ~250GB partition, or just the 60GB of actual used space? If not, what would you suggest?

Third and lastly, about mounting the shared drive in the active one. Would I need to do this myself each time I boot into Ubuntu or Red Hat, or would I be able to have them mount it at start-up automatically?

I think that about covers it (finally!) so thanks for reading, and thanks in advance for any hints, tips, or helping hands! :)

---

### Post by snkiz on 2008-11-18
interesting I tried something a little similar awhile back with PclinuxOS.
1) > **Mostly Harmless Eccentric said:**
>  about 8GB swap space 
That a lot does your system use even half of that? and still on the subject of swap
> **Mostly Harmless Eccentric said:**
> then the swap partition (likely containing two logical partitions, one for each distro, since I'm on a laptop)
Not necessary they can both use the same swap, along with live cds.
2)> **Mostly Harmless Eccentric said:**
> First and foremost, does anyone see any glaring errors in my plan, potential issues down the road, or otherwise have any suggestions? I'm particularly concerned about permissions on the shared files, and problems I've heard of with Grub regarding setups like this (usually something about an error 22?)
I experienced trouble having to grubs installed. So I only installed it in the first Linux install then manually wrote a grub entry for the second Linux install.
3)> **Mostly Harmless Eccentric said:**
> However, I need them to share files. For example, I make a sound effect in Audacity on Ubuntu, then I'll want to send it to Red Hat to be used in whatever I'm working on. I don't want to have to copy all this stuff and have it exists in two places on the hard drive and waste space. So I decided on an extra partition just for data, that'll be ext3.> **Mostly Harmless Eccentric said:**
> Third and lastly, about mounting the shared drive in the active one. Would I need to do this myself each time I boot into Ubuntu or Red Hat, or would I be able to have them mount it at start-up automatically?
I have one of those formated fat32 to share with windows. I set it up in the alt-install cd so it mounts as part of the file system "/winshare"
I made sure that I had the same user/group Id number in both distros I tested sharing the home folder between them, no major hiccups but if I was going to try it for a longer period of time I think I'd want to use like distros ie: Debian based, fadora based, or even better a stripped down ubuntu. that however is at your own risk.
4)> **Mostly Harmless Eccentric said:**
> I'd like to be able to do a more efficient backup than simply saving all my various files and folders I'll need to transfer. Ideally, I'd like to be able to mirror the entire thing, say to an external hard drive, then mirror it back on to the new partition, producing a copy what I have now. Is this possble? If so, would I need one to fit the entire ~250GB partition, or just the 60GB of actual used space? If not, what would you suggest?
Very possible I believe ddrescue is what you would use for that. But may I sugest you just boot a live cd and shrink your ubuntu partition? My current setup is as follows across three drives:
sda0 windows
sda1 ubuntu
sdb0 ubuntu home folder
sdb1 /usr/local (custom icons, themes, wallpapers, etc.)
sdc0 swap
sdc1 winshare (also used to boot live cds I'm playing with :) )
well thats my two cents hope It helps.

---

### Post by Mostly Harmless Eccentric on 2008-11-19
> That a lot does your system use even half of that? and still on the subject of swap

I don't recall having made it so high, and in fact had never had occasion to look into it until now. I assume it was set that way by default at install. Or I did it at the time, and don't remember why. At any rate, no, there's no particular reason.

> 
Not necessary they can both use the same swap, along with live cds.

Really? I'd read a few places it was safe to do give each one its own when on a laptop, though I admit, I didn't really understand the reasoning behind that.

> 
I experienced trouble having to grubs installed. So I only installed it in the first Linux install then manually wrote a grub entry for the second Linux install.

Perhaps this is a silly question, but it didn't give you any grief over doing it that, right?

> 
I have one of those formated fat32 to share with windows. I set it up in the alt-install cd so it mounts as part of the file system "/winshare"
I made sure that I had the same user/group Id number in both distros I tested sharing the home folder between them, no major hiccups but if I was going to try it for a longer period of time I think I'd want to use like distros ie: Debian based, fadora based, or even better a stripped down ubuntu. that however is at your own risk.

I's already intended to use the same user ID, etc, in both, though what they're sharing isn't the home folder. I'd considered it, briefly, and the issues associated with it are why I decided on the mounted partition.

---

### Post by Mostly Harmless Eccentric on 2008-11-19
(Sorry, missed this bit.)
> 
Very possible I believe ddrescue is what you would use for that. But may I sugest you just boot a live cd and shrink your ubuntu partition?

I considered doing that, but had been assuming that the effect/process would be pretty much the same. Would it not?

---

