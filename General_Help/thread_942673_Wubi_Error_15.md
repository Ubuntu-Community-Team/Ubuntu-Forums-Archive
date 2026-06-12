---
title: "Wubi Error 15"
date: 2008-10-09
forum: General Help
---

### Post by ddarkjedie on 2008-10-09
Well, I wanted to give Ubuntu a try, so I decided to test out Wubi.

That didn't work out so well.  LOL!

When I restarted my computer, and attempted to boot up in Ubuntu, I got a message like this:

> Booting 'ubuntu'

find --set-root --ignore-floppies /wubi/boot/linux

Error 15: File not found 

WTF?

Help please!

How do I resolve this error?

Note:  I've already uninstalled Wubi.

Oh, and I've attempted to install Wubi in the past, with an older version, but the results were the same.

---

### Post by ago on 2008-10-09
Is that 


find --set-root --ignore-floppies **/wubi**/boot/linux???

Because Wubi does not install anymore into a folder called "wubi". This must be a very old version you are running. In the new version the kernel will be /ubuntu/install/boot/vmlinuz

---

### Post by ddarkjedie on 2008-10-09
Ok, I'll reinstall it, and I'll see what happens.

---

### Post by MikeEx on 2008-10-10
I have error 15 with Wubi and 8.10 beta.
For some reason the boot script doesn't want to work for any of the boot options.

But when I type in the strings manually in the console

```
kernel /boot/vmlinuz-2.6.27-4-generic root=UUID=AEA0EF49A0EF169D loop=/ubuntu/disks/root.disk
initrd /boot/initrd.img-2.6.27-4-generic
boot
```

the exact strings present in the boot options

I can get into ubuntu 8.10 beta

---

### Post by ago on 2008-10-10
there should be 

root ()/ubuntu/disks

This assuming you are actually using grub4dos and not grub...
You can also hit "c" to get to the grub shell, then use tab completion with echo to navigate the folders.

---

### Post by WWSmith36 on 2008-10-10
I suggest that you do NOT install Ubuntu using Wubi.

The Wubi installer does not create a real linux ext3 filesystem, instead it creates a large filesystem within windows and install ubuntu to that. 

Because its embedded in Windows, if you have any problem with Windows due to viruses or other issues like file corruption. You will also damage you Ubuntu installation. I recommend installing Ubuntu and Windows in dual mode.

Please read following links
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by ddarkjedie on 2008-10-10
Ok, I installed ubuntu with the newest version of wubi.

I restarted my computer, booted up in ubuntu, and then went through the installation process.

After that was over, I was prompted for my username and password.

So, I inputted both of those, I heard the nice ubuntu start up noise.

Then, it took me back to the login screen!!!

So, I retried a few times, but with the same results.

I restarted my computer again.

I attempted to boot up in ubuntu again.

Then, I was welcomed by a command line interface.

WTF?

What do I do?

---

### Post by MikeEx on 2008-10-10
```
root (hd1,0)/ubuntu/disks
```
Is the part that goes through.
Anything after that doesn't.
That's where I hit 'c' and do the manual input to boot.

I don't want to have to manually type this stuff every time I want to use ubuntu.
Is there a way to fix this without clearing my current install?

---

### Post by ddarkjedie on 2008-10-13
Sorry to bother, but I still need help over here.

(Bump)

Note:  Wubi is probably the problem.

I've used Linux live CDs before.

---

### Post by ago on 2008-10-13
> **ddarkjedie said:**
> 
So, I inputted both of those, I heard the nice ubuntu start up noise.

Then, it took me back to the login screen!!!


This is a video driver issue. Press esc at boot after "ubuntu", select rescue mode and fix it from there.

---

### Post by ago on 2008-10-13
> **MikeEx said:**
> ```
root (hd1,0)/ubuntu/disks
```
Is the part that goes through.
Anything after that doesn't.
That's where I hit 'c' and do the manual input to boot.

I don't want to have to manually type this stuff every time I want to use ubuntu.
Is there a way to fix this without clearing my current install?

It should be 

root ()/ubuntu/disks

With nothing inside of the ()

---

### Post by jnbptst on 2008-10-13
Hi,

I get this error 15 in grub after having had to hard reboot my laptop during a crash... I launched a chkdsk in windows but to no avail. What scares me is that there is no longer any "disks" folder in C:\ubuntu...

What is to be done? Did I just lose all the files stored in my ubuntu home folder?

thanks in advance

---

### Post by MikeEx on 2008-10-13
> **ago said:**
> It should be 

root ()/ubuntu/disks

With nothing inside of the ()

You're awesome. Thanked.

---

### Post by Jhedan on 2008-10-14
Hi i tried installing Ubuntu (8.04) via wubi, the problem is that i get the same error as some folks here. i have 3 HDs: 2 SATA disks and an ATA (IDE) one. the Primary SATA is partitioned into C: and D: which i use for windows xp system files and programs, the Secondary SATA is called G: which is for my personal files.
I installed ubuntu on the spare ATA drive called I: everything went smoothly until i restarted and found this error screen which reads exactly like this:

Booting 'Ubuntu 8.04, kernel 2.6.24-generic'

Filesystem type is NTFS, partition type 0x42

kernel /boot/vmlinuz-2.6.24-generic root=UUID=32f49025f48fea05 loop=/ubuntu/disks/root.disk ro quiet splash

Error 15: File not found

Press any key to continue...

-----------------------------------------------------------------
i've tried to fix it however im a noob to ubuntu and linux as well :(

windows xp boots without problems but i just can't get to boot ubuntu

please help me

---

### Post by MikeEx on 2008-10-14
Jhedan:
get to the grub4dos boot list, on the default option (top of the list)
hit 'e'

on the first line you should see root ()/ubuntu/disks/
If you see any thing inside the "()", then you probably have the same problem I did.

Hit enter on the root line and remove anything inside () then hit enter again. this will make a temporary change.

hit 'b',  if ubuntu boots, keep reading. If not, Don't keep reading.

While in ubuntu (because the file you're going to change is hard to read in windows)
navigate to "/host/ubuntu/disks/boot/grub" (might be a different location for you, but try this first)

make a backup of menu.lst

open up menu.lst and at the bottom of the text you'll see your boot options. make the changes to the "root ()" lines and save.

reboot and test again.

---

### Post by Jhedan on 2008-10-14
Hey MikeEx, i followed your instructions and Ubuntu seems to boot fine, any idea of why this happens??

---

### Post by MikeEx on 2008-10-14
No idea. Glad you got it working.

---

### Post by ago on 2008-10-15
For wubi 8.10 please see [http://ubuntuforums.org/showthread.php?t=948083](http://ubuntuforums.org/showthread.php?t=948083)

---

### Post by jnbptst on 2008-10-17
Does anyone have an idea about my problem? Did I lose all my data?

---

### Post by Hates BSOD on 2008-10-18
I was a beta tester for wubi 8.04 and loved it. When the official release came out I uninstalled the beta and installed the official release. With the beta all worked. The official release upon reboot gave me the same error 15 message. Both were downloaded and installed from the web. I uninstalled and reinstalled with a live cd and all worked fine. Hope this helps.

---

### Post by jnbptst on 2008-10-18
My Error 15 problem did not come after a fresh update or install but because of a crash / hard reboot that apparently corrupted my NTFS... when I launched chkdsk apparently it REMOVED the corrupted parts instead of fixing them...

---

### Post by ago on 2008-10-18
Windows probably moved the files into a hidden folder called c:\found000 
You need to change the windows explorer settings so that you can see the hidden files.

---

### Post by jnbptst on 2008-10-18
just checked (showed hidden files, browsed manually + searched) and I can't find that found000 folder...

---

### Post by K_REY_C on 2008-10-20
Hello all,

I've been successfully running a wubi install for about 3 months now... I love it - lots of files saved on there - and I'm getting the error 15 on boot. 

I've read through a great deal of the advice on the forums but have yet to find an answer. Perhaps I'm misunderstanding some instructions. 

At any rate I'm anxious to restore and/or salvage my files and reinstall ubuntu again. 

I ran chkdsk in windows - with no success. I've also been unable to alter or find menu.lst , although I may not be looking in the correct place, OS, or otherwise. Any help appreciated. 

Thanks.

---

### Post by ago on 2008-10-20
Basically run chkdsk /r on the drive where you installed wubi, then look whether you have /ubuntu/disks/root.disk. If you do not see it, look for a hidden folder in C:\ called found000. Make sure you can see hidden files/folders.

---

### Post by K_REY_C on 2008-10-21
Strange thing:

When I defrag I can see C:\found000 being moved - and it is a huge file ... but even when I unhide folders I can't find the folder "found000" ... 

Any thoughts?

Also, when (and if) I do find the folder - what do I need to do with it to restore my ability to boot into ubuntu?

Thanks much.

---

### Post by K_REY_C on 2008-10-21
See above: here is how I can get into "found.000" (through dos).

[http://www.techspot.com/vb/all/windows/t-22483-How-To-Find-CFOUND000.html](http://www.techspot.com/vb/all/windows/t-22483-How-To-Find-CFOUND000.html)

Thanks.

Still need help with above though.

---

### Post by K_REY_C on 2008-10-22
Regaining my thoughts. Thanks for all the help/support so far.

1) What do I have to do with the folder "found.000"?
2) Can I do it through Windows DOS? (I have zero knowledge in DOS)
3) Will that fix the Wubi boot?

Thanks much,

K_REY_C

---

### Post by ago on 2008-10-23
You have to take the files/folders in there and move them to their original place.

In particular you should end up with:

c:\ubuntu\disks\root.disk
c:\ubuntu\disks\boot\grub\menu.lst

---

### Post by ddarkjedie on 2008-10-23
> **ago said:**
> This is a video driver issue. Press esc at boot after "ubuntu", select rescue mode and fix it from there.
Thank you!!!!!

It works fine now!!!!

---

### Post by K_REY_C on 2008-10-24
Here's what I did:

Boot from live ubuntu 8.04 CD

Go to 'places' and 'mount ??.? GB hard drive'

saw "found.000"

Navigated into the folder. This is what I saw:

1) Folder: "boot"
2) Folder: "shared"
3) "root.disk"
4) "swap.disk"

I moved all four of the above files/folders into c:\ubuntu

I rebooted... and got the same error message I did before:

find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst

Error 15: File not found

Press any key to continue...

------------

Any further help or suggestions appreciated.

Is there anyway I can simply salvage my files w/in ubuntu and do a clean reinstall?

Thanks so much,

K_REY_C

---

### Post by K_REY_C on 2008-10-24
Solved my own problem:

Had to create a folder named "disks" into which I placed "root.disk" and the folder "boot" to reflect the advice below.

Thanks for all of your amazing help.

No I'm off to shrinking Windows and creating a true partition for ubuntu. Hopefully less problems with that. 

Thanks again all.

> **ago said:**
> You have to take the files/folders in there and move them to their original place.

In particular you should end up with:

c:\ubuntu\disks\root.disk
c:\ubuntu\disks\boot\grub\menu.lst

---

### Post by jnbptst on 2008-10-26
Thank you so much K_REY_C! You made my day, I'm back on linux now.

I was looking for "found000" instead of "found.000", no wonder I couldn't find it.

I freaked out so much I was gonna lose my data!

Anyway thanks again

---

### Post by K_REY_C on 2011-02-27
> **jnbptst said:**
> Thank you so much K_REY_C! You made my day, I'm back on linux now.

I was looking for "found000" instead of "found.000", no wonder I couldn't find it.

I freaked out so much I was gonna lose my data!

Anyway thanks again

This thread was one of my first -- I thought I'd come back to say that this problem w/ windows is what convinced me to switch to GNU/Linux full time. After I rescued my files I installed ubuntu over the entire windows install. I haven't used windows since.

---

