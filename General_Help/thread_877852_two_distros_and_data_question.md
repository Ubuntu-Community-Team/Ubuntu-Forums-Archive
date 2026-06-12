---
title: "two distros and data question"
date: 2008-08-02
forum: General Help
---

### Post by ihatetryingtopickaloginna on 2008-08-02
I have Ubuntu 8.04 and openSUSE 11.0 on the same hard drive. Is there a way to have one copy of a program and be able to use it in either distro? And only have one copy of say, a picture folder? Instead of having to duplicate on each distros partition. Or is it too late now that I already have both distros up and running, and I should have done it earlier?

---

### Post by coffeecat on 2008-08-02
You can't share application files between different distros. The way they are compiled and configured are different from distro to distro. Besides, the constituent files for various apps are liberally showered amongst different folders in /usr and /etc (and sometimes /bin or /opt) and if you tried to merge those system folders from Suse and ubuntu you'd end up with an unbootable mess - I would imagine. :? At least I personally wouldn't try it.

But shared personal files such as pictures and text files are a different matter.

> **ihatetryingtopickaloginna said:**
> Or is it too late now that I already have both distros up and running, and I should have done it earlier?

Possibly, possibly not. There are two ideal ways to do this and both require a separate partition, so if you don't have room for this it may well be too late. The first way is a shared /home partition. There are advantages and disadvantages to this. Search the forum and you will probably find some howtos.

The way I prefer is to have a shared data partition (which has to be mounted at bootup) and set up symlinks in my home folders. For example, say I have 'Pictures' and 'Videos' folders in my data partition, I would simply setup symlinks to them from both the Ubuntu and Suse home folders also called 'Pictures' and 'Videos'. Clicking on the symlinks (which look like folders with curly arrows) transparently transfers me into the folder on the data partition.

One warning: if you use a Linux filesystem on the data partition, you will trip over permissions problems if your UUID in the two distros is different. Fortunately, both Suse and Ubuntu allocate an UUID of 1000 to the first created user, but you need to check this.

If you can't set up a separate data partition, one way would be to keep all your shared files in your Ubuntu home folder (say) and set up symlinks in your Suse home to your Ubuntu home. Again, you must check the UUIDs, and you must make sure that Suse mounts your Ubuntu partition when it boots up otherwise the symlinks will fail.

---

### Post by ihatetryingtopickaloginna on 2008-08-02
Okay, thanks for the advice. That's a lot to digest.

---

### Post by tinachen1010 on 2008-08-02
How to quickly find your model
The network sale is an essential part. Electronic products' transaction platform has also become the most main transaction pattern  in the IC sale platform
Welcome to [http://www.chinaicmart.com/](http://www.chinaicmart.com/)

---

### Post by coffeecat on 2008-08-02
> **ihatetryingtopickaloginna said:**
> That's a lot to digest.

Yes, there is - sorry about that.

One question. You said you had Ubuntu and openSUSE on the same drive. Have you got Windows on that machine as well? And, if so, do you have a separate partition for Windows - separate from the Windows C: drive that is? (Er - that's two questions, isn't it? :wink: )

The reason I ask is that Linux has had reliable read-write access for the Windows filesystem FAT32 (the one used by Windows 98 ) for some time now, and now has reliable read-write access for NTFS (the filesystem used by Windows 2000, XP and Vista). Both openSUSE and Ubuntu support NTFS read-write out of the box with the ntfs-3g driver. If you have one or more Windows partitions, you might be able to use them to share data between the two Linux distros and indeed with Windows itself. One advantage with a Windows filesystem is that it does not support Linux/Unix permissions and you can forget all I said about UUIDs. (Amazing, isn't it, that a lack of a feature can sometimes be an advantage?)

---

### Post by ihatetryingtopickaloginna on 2008-08-02
This is my first store bought computer in years, and it came with Vista on it. I left it on long enough to see that the box was functional and then booted an Ubuntu cd and formatted the drive. I partitioned it so that I could install another distro if I saw one that was interesting, but had never done this before so didn't really know what I was doing. I had tried XP and was totally turned off by it and wanted to try something else. Too bad IBM deserted OS/2, that's what I would be using if it would run on modern hardware.

But Linux is working great for me. I'm just having to learn new ways of doing things.

Al

---

