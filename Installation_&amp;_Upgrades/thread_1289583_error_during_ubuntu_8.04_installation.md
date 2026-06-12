---
title: "error during ubuntu 8.04 installation"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by xyoen on 2009-10-12
Hello, when I tryied to install ubuntu 8.04 on my notebook I get this error: "an error as occured during the writing operation on the memory device, the resizing operation will be termineted" (probably it is not the exact message in english because it was in another language). 
I have an acer aspire 3630 intel celeron m370 1.5ghz 512mb ram. 
I actually have windows xp but I tryied to install ubuntu in a different partition that I previously had. Is it important that the filesystem of this partition is ntfs and that it's also very fragmented? At the moment I prefer to don't format/ erase it because I don't have any way to back-up my files... Could ubuntu do the installation without delete it? When I tryied to install ubuntu the free space was 7gb. 
I also asked in various irc chan but I don't have more time to wait, so I hope someone can help me, I'll be very gladly for any suggestions. I really like ubuntu and I'm getting very annoyed by using win xp...:P

---

### Post by kiridude on 2009-10-12
When you install Ubuntu in a partition it will erase everything there and reformat it to ext3 or ext4 depending on what you choose. 

At what step of installation did you receive the error?

---

### Post by ajgreeny on 2009-10-12
You could just about get ubuntu to install onto a 7GB partition, but if that is all the free space available on your windows partition I don't think you will manage to shrink windows enough.  Windows will always ensure that there is sufficient space free on its partition for system activities, so even though you have a theoretical 7GB, quite a lot of that will not be available to you for the ubuntu partition, and hence, I suspect, your error message.  I don't think there is any way around this apart from deleting some of your windows files and programs to free some more space and then defragging a couple of times to make sure the space is used most economically.

As for your question regarding not deleting the windows system or your current files, a dual boot system does just that, putting ubuntu on a separate partition, and leaving everything else as it is.  However, things can go wrong, and I strongly advise you NOT TO PROCEED without good backups of everything important to you.  I have installed dual boot systems many times and so far all has been well, but it can and does sometimes go badly wrong, particularly for people who have never done it before and don't understand the linux partition naming etc etc.

---

### Post by xyoen on 2009-10-13
About back-up, I don't understand what kind of files it applies: documents, OS files or all the files? I also have the official red book guide to ubuntu and it just suggest to backup the most important files for the case of a bad event occours, it not say move all your data away...
The error during installation appeared when I proceeded next to step 4 (when it ask how install ubuntu). I had 3 options: use the entire disk, wizard or manual. I choosen the option "wizard: resize partition and use free space" and I moved the orange bar of ubuntu space until 6.8 gb (even if I couldn't move it over 7gb...). Another question: why there isn't any "use the largest continuos free space" option in my installation? 
For clearness, I try to explain better what are the partitions of my pc:
1) with windows xp installed, fat32 and 5gb free
2) with NO OS installed, ntfs, 7gb free and some data

I tryied to install ubuntu on the second one. I think some images will speak better than me so I'll try to post some. I read in a guide that ubuntu cannot manage or also resize ntfs partitions during install: is that true? Do I have to install it on another file system? :confused:

---

### Post by kiridude on 2009-10-13
Ok, as far as I understand, Windows is on partition 1, so we needn't worry about it for now. Partition 2 is where you want to install Ubuntu, right?

If this is the case, make a copy of everything you want from partition 2 as everything will be deleted from this partition upon the installation of Ubuntu. Partition 1 will remain untouched (if you don't make any mistakes). This is why backing up your important files from Windows is suggested. Only copy what you will not be able to get back with a fresh installation of Windows. This is in case you delete Windows by accident.

There is no problem with what the current formatting of partition 2 is as it will be re-formatted to ext3 or ext4 (as I said above).

7 GB of free space in partition 2 is more than enough space for Ubuntu. It will get tight later on when you add alot of programs and download movies, music, etc from the Internet.

It is possible that you are trying to cut the Windows partition to close and that is causing the error. Experiment with leaving a little extra space for the Windows partition.

---

### Post by xyoen on 2009-10-13
Sorry I haven't understood well: Do I have to free a litlle extra space for the windows partition or for the other one? Because I already had 5gb free space in the first one...

---

### Post by kiridude on 2009-10-13
let's have a look at what's going on on your disk to avoid misunderstandings. Run the live CD and choose the first option to try Ubuntu without affecting your system. Once Ubuntu opens, goto Applications > accessories > terminal. In the terminal, type

```
sudo lshw -C volume -short
```

print the output of this here so we can have a look.

---

### Post by xyoen on 2009-10-18
I have used defraggler with the partition and then the installation succeded! :) Thank you very much for the help

---

