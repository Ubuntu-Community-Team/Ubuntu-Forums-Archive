---
title: "Right File System For External Hard Drive"
date: 2011-03-24
forum: Hardware
---

### Post by mohtasham1983 on 2011-03-24
Hi,

I just found a good deal on B&H and ordered a 2TB Western Digital external hard drive, which is going to be arrived in a few days.

I am planning to use this hard drive to store my movies and pictures on it. The biggest movie I own is currently around 3GB, but if I get this hard drive, I'm gonna have store 5GB+ movies and videos as well. 

This hard drive will be shared between my Ubuntu laptop, mostly Arch Linux desktop and possibly my android phone. I may even try to connect this hard drive to my Asus router which runs dd-wrt firmware. 

Since, I don't use non-Linux operating systems and I don't think I would ever use one, not being able to access the data using Windows and Mac is not an issue for me. 

I was wondering if anyone can recommend me the most appropriate file system for my external hard drive. Also, do you recommend partitioning it to have different file systems for bigger and smaller files?

Thanks in advance

---

### Post by VastOne on 2011-03-24
EXT4 is all I have ever used and swear by it..

Nary an issue....

---

### Post by Learning Linux 2011 on 2011-03-24
The most universal file system, read by Mac, Windows and Linux, is FAT32, but it has a limit of 32GB and you cannot copy files larger than 4GB each.

If you really don't need Windows to access the drive, then some version of ext should be ok (like ext3 or ext4)

---

### Post by mohtasham1983 on 2011-03-25
With ext3 and ext4, I'm not going to have problems with permissions if data is shared between multiple computers?

---

### Post by oldfred on 2011-03-25
I only have Ubuntu and related verisons.

But I saved this link in case I do install something else.

Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

---

### Post by smoothwoven on 2011-03-26
Good day!

After much searching and seeming (green bean?) inability to post my own threads; this is the most related post to the problem I am having.

I have just received a Western Digital 1TB external. I am currently running 7.04 and have been very tardy about updating it. My intention is to use the external to back everything up, update to some new beautiful Ubuntu in the 10 or 11 range, then mess with finding some compatible USB wifi key...
but one thing at a time...
I know little/nothing in the way of code but I seem to enjoy toiling over forums for long periods of time to fix things. This whole ordeal may even just drive me into a position where I finally get around to learning. I look forward to being able to fix it all myself one day. This is my understanding so far:

I have access to a room mate's laptop with vista. **I've gone through using Swissknife to format it as FAT32, and even renamed the drive "MITTEN" but my Ubuntu is treating it as read-only and I can't change any permissions.**

I never intend to use MITTEN with any windows machine, and I am aware of other linux-only formatting (EXT4? i think).

**Really, I'd prefer a windows-dependency-free way of formatting my new external to love and cherish for the forseeable future.**

Can it be done? I bow before your finite wisdom!

LOVE,
jcs

---

### Post by coffeecat on 2011-03-26
@mohtasham1983, first question. Is the WD drive a USB drive or a network attached storage device, such as a MyBookWorld? The fact that you want to connect it to your router suggests the latter. Or has the router a USB connection? I believe some asus routers do but I have no experience of these. If your WD drive is a MyBookWorld then you don't format it. The filesystem is what the MyBookWorld uses and is irrelevant to what it connects to. However, if that's a USB drive...

> **mohtasham1983 said:**
> This hard drive will be shared between my Ubuntu laptop, mostly Arch Linux desktop and possibly my android phone. I may even try to connect this hard drive to my Asus router which runs dd-wrt firmware. 

I'd agree with the others to use ext3 or ext4 but you need to check what your android can do. Do you mean connect the android directly? Can it read USB drives? You'd need to check what filesystems the android phone can read. Ditto the dd-wrt firmware if the asus router can connect to a USB drive.

> **mohtasham1983 said:**
> With ext3 and ext4, I'm not going to have problems with permissions if data is shared between multiple computers?

Yes you are with a freshly formatted ext3/4 partition. It will be owned by root. If the UID of your accounts on all your Linux machines is the same, you can mount the drive and:

```
sudo chown yourusername: /media/mountpoint
```For good measure, and if you have different UIDs on different Linux accounts:

```
sudo chmod 777 /media/mountpoint
```Both of these have the interesting effect of chowning and chmodding the filesystem, not the mountpoint, so the changed permissions will "stick" when you attach the drive to another system.

===

@smoothwoven, welcome to the forum, but..

Please start your own thread rather than hijacking another. It gets very confusing when more than one person's problems are being addressed in one thread. You have a different issue from the OP.

---

### Post by ottosykora on 2011-03-26
>but it has a limit of 32GB a<

not quite true, I have here 1TB drive formated with fat32, no probem with that. It is only MS limitation, only windows refuses to format larger drives with fat32.

---

### Post by mohtasham1983 on 2011-03-26
> **coffeecat said:**
> Is the WD drive a USB drive or a network attached storage device, such as a MyBookWorld? The fact that you want to connect it to your router suggests the latter. Or has the router a USB connection? I believe some asus routers do but I have no experience of these.

Actually, it is a USB drive. My router has a USB port, that I'm not too sure how to work with it.

My USB hard drive will be primarily connected to my desktop workstation, which is on 90% of the time. Connecting my USB hard drive to the router gives me the ability of having access to my movies, if I get a PS3 in future without a need to have my computer on all the time. 

> 
Both of these have the interesting effect of chowning and chmodding the filesystem, not the mountpoint, so the changed permissions will "stick" when you attach the drive to another system.

I guess I will make the permission of the root directory on the external hard drive to public and add all users to a certain group according to [http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381) and create subdirectories in it for private, read-only, and public permissions in it.

---

### Post by smoothwoven on 2011-03-27
> 

@smoothwoven, welcome to the forum, but..

Please start your own thread rather than hijacking another. It gets very confusing when more than one person's problems are being addressed in one thread. You have a different issue from the OP.

Thank you.
maybe I was really tired when i posted, but i didn't seem to have permission to start new threads. I will look closer at this and try again.

i am aware of thread etiquette, it seemed like i had no other option and this thread seemed the most relevant.

---

