---
title: "[SOLVED] Custom Live CD creation...or something"
date: 2008-11-01
forum: General Help
---

### Post by fiddler616 on 2008-11-01
Hello,
A few months ago, I crashed Windows' boot sequence on my dual-boot system. At the time I thought it was a real shame, but in hindsight I realize that it made me learn 'harder' things on Ubuntu--since it was the only working OS. I didn't restore Windows then and there because I didn't have a disk.
But, whether I like it or not, certain things need Windows, and besides that, I feel like an idiot with 20GB of my 40GB HD taken up by a non-functional operating system. And I finally found an article detailing how to reinstall Windows with a program called BartPE.
Except I know that installing Windows after Ubuntu causes all manner of problems.
So the question is--what do I do?

Should I make a custom Live CD, off my current distro, and reinstall off that?

I have a massive external HD--can that be used for something?

Should I just burn a standard Intrepid Live CD (the only ones I've had were two Hardys--one of which I gave away, and the other is out on loan), backup my documents, reinstall, and then have a really *fun* time reinstalling packages and settings?

I feel like I've heard that installing Windows after Ubuntu doesn't actually screw Ubuntu up--it just messes up GRUB--is this true?

I've already looked at this thread:
[http://ubuntuforums.org/showthread.php?t=484965](http://ubuntuforums.org/showthread.php?t=484965)
and regret to inform you that I do not have 5GB free. And my swap is only ~512MB--not 1GB.

I'd be more than happy to give you guys any more information, but I don't know what else you want to know, and don't want to bloat this post.

Thanks in advance.

---

### Post by meindian523 on 2008-11-01
> **fiddler616 said:**
> 
I feel like I've heard that installing Windows after Ubuntu doesn't actually screw Ubuntu up--it just messes up GRUB--is this true?

That's true,provided you choose the partition for Windows carefully and ensure that you don't overwrite the Ubuntu partition with Windows.Then you simply reinstall Grub with

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by benner on 2008-11-01
you could certainly remaster the whole system with remastersys or something like that but if you were planning to upgrade anyways you may want to use APTonCD. Then you can select only those packages that you don't want to have to download again and burn them to a dvd. then once you have installed intrepid, you can reinstall things from the aptoncd packages disk.

or you could just install windows in a virtual machine. then you don't have to change a thing.

edit: just reread your post. no point reinstalling ubuntu. just reinstalling grub after windows as suggested above. you can use this:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Alaric on 2008-11-01
Seems like a waste to spend all that time remastering a disk.  Windows XP pulled that overwriting BS on me a few years ago.  You should just be able to pop in a normal livecd, mount you ubuntu as /media/disk and use grub-install --root=/media/disk to get grub back up and running.  Have a nice day :)

---

### Post by meindian523 on 2008-11-01
benner:I think there would be a problem installing APTonCD packages on an upgraded system.I can think of Synaptic complaining that there are more up-to-date packages in the repos,but I'm not sure that's the way to go.

---

### Post by fiddler616 on 2008-11-01
Thank you!

Before I launch into this though:
> find the root partition and install grub to the MBR (hd0,0) 
and
> Using this information, set the root device:

grub> root (hd0,1)

Install Grub:

grub> setup (hd0)
Do they *literally* mean that, or should I changed the (hd0,1) to my main Linux partition, which happens to be sda1. And should I change the MBR reference to the Windows partition--sda3?
While I'm at it, sda3 = (hd0,3) right?

---

### Post by meindian523 on 2008-11-02
They mean you should find your main linux partition(I'm assuming you mean the partition for / ) and change it to whatever it is.Yours is sda1,so the partition in Grub would be (hd0,0)(Grub counts from zero)Therefore sda3 would be (hd0,2),NOT (hd0,3)And no,the MBR is always (hd0),so the setup(hd0) command stays as is.

---

### Post by fiddler616 on 2008-11-02
OK. So I followed the instructions for GRUB--and it seemed to go all right.
Then, when I rebooted, GRUB came up, but it wouldn't boot to Ubuntu because of
> Error 17 : Could not mount the partition
and it wouldn't go to windows because of something-or-other about NLFS or NTFS or something, and to press Ctrl-Alt-Del to restart. Which seems like a Windows error, not a GRUB one.

So now I'm going to play around with menu.lst, but I feel like this isn't expected behavior.

Thanks.

---

### Post by fiddler616 on 2008-11-02
Hoo, boy.
/boot/grub/menu.lst doesn't exist.
for that matter, /boot/grub doesn't exist.
Umm, am I looking in the wrong spot or something?

---

### Post by meindian523 on 2008-11-03
You will probably find it in lost+found on your / partition,if you are looking in the right place.But I can't say for sure,the names might be changed to strange strings of numbers and alphabets.

---

### Post by fiddler616 on 2008-11-03
Hmm.
/lost+found : Not found.
/boot/lost+found : Not found.
Search "lost found" : Not found.
Search "menu.lst" : Found four of them. I'll get back soon.

---

### Post by fiddler616 on 2008-11-03
I got fed up--nothing was working--not even SuperGRUBDisk, so I backed up my documents, and reinstalled Ubuntu.
Which is good--I'm enjoying the silence coming out of my CD drive--but GRUB can't seem to even *find* Windows.
That belongs in a thread of it's own though.
Thanks for all your help anyway!
</thread>

---

### Post by meindian523 on 2008-11-05
Please mark the thread solved,and put a link to the new thread.

---

### Post by fiddler616 on 2008-11-05
> **meindian523 said:**
> Please mark the thread solved,and put a link to the new thread.
Sorry, I was merging the two threads in my mind :/

New thread:
[http://ubuntuforums.org/showthread.php?p=6101841#post6101841](http://ubuntuforums.org/showthread.php?p=6101841#post6101841)

Summary of solution: Added a Windows entry to menu.lst. After that, Windows somehow didn't have three files that are crucial for booting, so somebody sent me a tar.gz of them, along with a modified boot.ini to read them properly.

---

