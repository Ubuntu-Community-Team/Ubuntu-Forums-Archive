---
title: "How to uninstall ubuntu and grub system"
date: 2008-08-26
forum: General Help
---

### Post by Vegito on 2008-08-26
Hi there,

I want to uninstall ubuntu and get everything back to normal (no more grub system,I just want it to load back to vista when it starts straight away).

So how do I do it.

I'm a beginer so basic stuff please.

Thanks,

Vegito

P.S,I dual booted ubuntu 8.04 with vista this way:

[http://netcashingin.blogspot.com/2008/05/how-to-dual-boot-windows-vista-and.html]("http://netcashingin.blogspot.com/2008/05/how-to-dual-boot-windows-vista-and.html")

---

### Post by Elfy on 2008-08-26
With wubi it should be as simple as uninstalling with your add/remove, but I've not actually used wubi as I have a normal pc without windows :D

[https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

If you get a problem post back here.

---

### Post by Cobra_Fast on 2008-08-26
EDIT: This is NOT for Wubi-Systems

well, thats an easy one.

Just hit in a bootable CD (like the ubuntu one) and format the partitions of your old ubuntu as NTFS or FAT32 (also the /boot partition!).

And now dont panic cause you will not be able to boot any OS on your computer, but to fix that, we boot from the Windows XP/Vista install CD and choose "Rescue System" (or something like this) instead of the install option.
Then it should provide you an MS-DOS like shell.

There you type in
```
fixmbr
```
it should install your old Windows XP/Vista Boot-Manager.

Then you are done! You got back your unstable, slow and n00bish Windows computer! Congratulations! ;o)

---

### Post by Inane_Asylum on 2008-08-26
Hey hey, play nice...:p

---

### Post by caljohnsmith on 2008-08-26
> **Cobra_Fast said:**
> 
There you type in
```
fixmbr
```
it should install your old Windows XP/Vista Boot-Manager.

Actually that command is only for Windows XP; the geniuses at Microsoft of course had to change things with Vista, :) so the equivalent command for Vista is:
```
bootrec /fixmbr

```

---

### Post by Vegito on 2008-08-26
I bought a laptop and it did not have an installation disc.

I uninstalled ubuntu using add or remove programs and restarted the computer but the grub system is still up with vista and ubuntu and I then went back to the uninstall add or remove bit and there is no ubuntu in it,whats going on?

---

### Post by caljohnsmith on 2008-08-26
You'll need to download a [Vista Recovery CD]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/") then and run that command I gave if you want to restore Vista to the master boot record and delete Grub.

---

### Post by Vegito on 2008-08-26
> **caljohnsmith said:**
> You'll need to download a [Vista Recovery CD]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/") then and run that command I gave if you want to restore Vista to the master boot record and delete Grub.

Should I backup my discs when before I put the restore disc in or will all my documents etc be unharmed?

Which vista recover should I download x64 or x86

---

### Post by Elfy on 2008-08-26
If you have 64 bit get x64 or x86 for 32 bit, you should always have backups anyway of important data.

---

### Post by Vegito on 2008-08-26
> **forestpixie said:**
> If you have 64 bit get x64 or x86 for 32 bit, you should always have backups anyway of important data.

erm how do I found out how many bits is my vista?

---

### Post by Elfy on 2008-08-26
Run this in a terminal

```
sudo lshw -C cpu | grep width
```

---

### Post by Vegito on 2008-08-26
Thanks,looks as thoguh I have 32 bit good thing I installed the x86 one.

---

### Post by Elfy on 2008-08-26
Glad you're sorted , but why are you actually uninstalling ubuntu, any problems or just not liking it?

---

### Post by Vegito on 2008-08-27
The laptop I'm selling to one of my friends,and they do not want ubuntu on it,I tried to explain that its better than vista.

So basically all I have to do is insert the disc and press F8 (when should I press it though)and then eneter the command and evrythings fine then,am I right?

---

### Post by caljohnsmith on 2008-08-27
Yes, just do whatever you need to do to boot that Vista Recovery CD you downloaded, and if you have any more questions about doing that command I gave earlier, see [this tutorial]("http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD") first.

---

### Post by Vegito on 2008-08-27
Okay,so I've read the tutorial but a bit confused which one should I pick to enter the command is it command prompt option?

---

### Post by Vegito on 2008-08-27
Okay so this is what I have to do,correct me if I'm wrong at any point thanks:

Delete partition with ubuntu-DONE

Make vista recovery disc-DONE

Restart windows vista with recovery disc-NOT DONE

Go to repair and command prompt and type in command-NOT DONE

Once this has been done restart and everything should be okau-NOT DONE

Is what I said okay?

Thanks,

Vegito

---

### Post by Inane_Asylum on 2008-08-27
Correct.  Note that after doing so, you will still have unallocated partition space from the deleted ubuntu partition.  Vista has a pretty good partition editor, so that shouldn't be a problem, though.

---

### Post by Vegito on 2008-08-28
> **Inane_Asylum said:**
> Correct.  Note that after doing so, you will still have unallocated partition space from the deleted ubuntu partition.  Vista has a pretty good partition editor, so that shouldn't be a problem, though.

How do I get onto this vista partiton editor?

---

### Post by Elfy on 2008-08-28
It's here [http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista](http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista)

---

### Post by Vegito on 2008-08-28
So done that,now to put the recovery disc in.

Wish me luck

Thanks,

Vegito

---

### Post by Vegito on 2008-08-28
I did all the recovery disc disc stuff typed in the code etc restarted the computer and the grub system was still on.

What do I do?

---

### Post by Elfy on 2008-08-28
I'd say do it again - if grub is still there then the command didn't do it, have to say I've not tried it with vista as I've never dealt with it.

---

### Post by Inane_Asylum on 2008-08-28
What did it say when you typed in the 'bootrec /fixmbr' command?

---

### Post by Vegito on 2008-08-28
It said the command completed sucessfully

---

### Post by waggingwabbit on 2011-09-14
I'm sorry for bringing this thread back from the dead but I just searched in google and this thread popped up. You guys mention the windows 7 recovery CD, but it seems that website is charging 10 dollars for it... is it possible to just use my regular windows 7 install CD for the process instead? Just want to make sure before I continue with this.

---

### Post by cariboo on 2011-09-14
If you have a regular Win 7 install disk, you don't need the recovery disk.

Now lets's put this tread back to sleep. Closed.

---

