---
title: "Kernal Panic"
date: 2010-09-18
forum: Hardware
---

### Post by grnorris on 2010-09-18
My friend just installed Ubuntu 10.04 on his laptop recently and while on the internet and listening to Last.FM it crashed.  When he tried rebooting it came up with the following message:  #.#### kernel panic - not syncing: VFS: unable to mount fs on unknown-block(0,0)

He's using a gateway mx644.

He can only access the net right now with his PSP so he's communicating with me via Facebook (as in we aren't in the same area right now so I can't take a look at it myself).

So far the only idea we have is that it may be RAM related but, we need to know all possibilities and any checks he can do.

Not sure yet if he can actually load a disk or not (Waiting on a reply).

---

### Post by Fafler on 2010-09-18
It's most likely harddrive related. But still, grub is able to load itself, the kernel and the initrd from the drive, so it's not totally broken. Not sure what to make of it this early in the morning. Go into the grub menu and fiddle around with the root= parameter.

---

### Post by grnorris on 2010-09-18
> **Fafler said:**
> It's most likely harddrive related. But still, grub is able to load itself, the kernel and the initrd from the drive, so it's not totally broken. Not sure what to make of it this early in the morning. Go into the grub menu and fiddle around with the root= parameter.

I suppose hard drive is also a good possibility.  I think my friend went to bed cause I'm not getting any responses from him (I'll probably join soon it's like 3 in the morning for me).  Unfortunately there's no telling when I'll be able to visit him in person so solutions like fiddling with root= is not a possibility (He's a linux noob).

---

### Post by grnorris on 2010-09-20
OK, I'm back online again (No home internet so weekends = no connection).  My friend replied to my earlier question and said it won't load any disk.  It just sits at the boot screen.  Personally I'm thinking this is a sign of either bios corruption or RAM.  Any second opinions?

---

### Post by alexandre.schwarz on 2010-09-20
This is EXACTLY what's happening to me right now. I'm using windows 7 to type this though.
I don't know how it could have happened, since this a new netbook.
Any ideas?
 
Thanks in advance.

---

### Post by Dabulewicz on 2010-09-21
its norris's friend. I asked him to start this. I also remembered a few hours before, I was doing the update manager, so would that affect anything? and I only got this o/s so idk how to access a terminal kind of program

---

### Post by drs305 on 2010-09-21
Is there an option to use an older kernel on the Grub2 menu? Does he see the Grub2 menu or just the prompt?

It's possible it's a problem with a kernel update. If so, there may be an an older kernel on the machine. 

The user can check by pressing "c" at the grub menu (if not already at the grub prompt). Once at the prompt:

Type
```

ls /boot

```
to see what files/kernels are available in boot. 

If there is a kernel with a lower number that than the one in the menu (say -23 and -24), note the value (for instance -23) then:

Is there an option to use an older kernel on the Grub2 menu? 

If not, but an older kernel might be on the machine, the user can check by pressing "c" at the grub menu (if not already at the grub prompt).

Then type
```

ls /boot

```
to see what files/kernels are available in boot. 

If there is a kernel with a lower number that than the one in the menu (say vmlinuz-2.6.32-23 and vmlinuz-2.6.32-24), then:

If there was a Grub2 menu:
ESC back to the grub menu.
Cursor to the correct menuentry (normally the first)
Press "e" to edit.
Change the kernel number to the lower number which resides in /boot. (e.g vmlinuz-2.6.32-23 from vmlinuz-2.6.32-24)
CTRL-X to boot.


If there wasn't a Grub2 menu, only a prompt:
Type:
```
linux /boot/vmlinuz-2.6.**<rest of the lower kernel name>** root=/dev/sd**XY** ro
initrd /boot/initrd.img-2.6.32-**<rest of name>**
```
Example: 
linux /boot/vmlinuz-2.6.32-23-generic root=/dev/sda1 ro
initrd /boot/initrd.img-2.6.32-23-generic

Then CTRL-x to boot

---

### Post by Dabulewicz on 2010-09-21
yea figured out much of how to do that. editing then booting cause very loud beeps and showing same error...

---

### Post by grnorris on 2010-10-07
> **Dabulewicz said:**
> yea figured out much of how to do that. editing then booting cause very loud beeps and showing same error...

Hey, it's Greg again.  Stefin (Dabulewicz) still isn't up and running and as I said earlier I can't go and help him in person.  I'm afraid this thread has been buried and will be buried again if it's not resolved soon.

---

### Post by drs305 on 2010-10-07
In the past two weeks there have been a lot of crashes following updates. In many of these instances the update appeared to have corrupted the Grub files.

I wrote a guide on how to purge and reinstall Grub2. If the problem is indeed boot related, the solution has fixed it for those who have used it.

Here is the link:
[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by grnorris on 2010-10-13
> **drs305 said:**
> In the past two weeks there have been a lot of crashes following updates. In many of these instances the update appeared to have corrupted the Grub files.

I wrote a guide on how to purge and reinstall Grub2. If the problem is indeed boot related, the solution has fixed it for those who have used it.

Here is the link:
[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")

He can't boot a disc.  He seems to have Grub2 without the Menu.  I once had a site I used to fix such an issue before but, I've not yet relocated that site.  I'm going to try checking my old post now to see what I can find.  Also, since I can't be there with him there's no way for me to know for sure if he's having the same kind of issue I had before with grub2.

---

### Post by drs305 on 2010-10-13
> **grnorris said:**
> He can't boot a disc.  He seems to have Grub2 without the Menu.  I once had a site I used to fix such an issue before but, I've not yet relocated that site.  I'm going to try checking my old post now to see what I can find.  Also, since I can't be there with him there's no way for me to know for sure if he's having the same kind of issue I had before with grub2.

The message from the first post sometimes means that grub has passed information to the kernel but then system can find the correct files. Does he get a Grub menu if he holds down the SHIFT key as the computer boots? If so, we might be able to alter the menuentry before it continues to boot.

If he can get to any kind of Grub prompt we might be able to get the system booted. I wrote a new guide on the Grub rescue prompt two days ago that might be able to walk him through the procedure.
[Grub Rescue Prompt Megathread]("http://ubuntuforums.org/showthread.php?t=1594052")

---

### Post by Dabulewicz on 2010-10-13
I got that grub while holding down the shift key

---

### Post by grnorris on 2010-10-13
> **Dabulewicz said:**
> I got that grub while holding down the shift key
 
As in I was mistaken.  He does have the grub menu which means it should be possible to use the full extent of the grub2 command line.  I still don't know what commands to try though:  Either a command to re-detect the OSes location (since he can't boot into Ubuntu) or a command to boot a CD.

---

### Post by drs305 on 2010-10-13
> **grnorris said:**
> As in I was mistaken.  He does have the grub menu which means it should be possible to use the full extent of the grub2 command line.  I still don't know what commands to try though:  Either a command to re-detect the OSes location (since he can't boot into Ubuntu) or a command to boot a CD.

The grub2 command line is really only for booting into the system. It is used to point to the Grub files and then boot into a normal installation. You can't really use the grub terminal to change files permanently. It's purpose is to get the OS booted, from which changes can be made permanent.

Without a LiveCD to boot from, his best option is to try to boot from the Grub2 rescue prompt. We could try to edit the existing menu, but without seeing what he has it would probably be easier from the prompt. I recently wrote a guide this week to explain that process:
[http://ubuntuforums.org/showthread.php?t=1594052]("http://ubuntuforums.org/showthread.php?t=1594052")

---

### Post by Dabulewicz on 2010-10-15
I did it word by word as in that guide.... got list of errors.... Greg, we'll just plan a day to check it out

---

### Post by Dabulewicz on 2011-03-24
yep, ever since that day my laptop basicly got worse, where i cant even start it up, i dont blame the OS, i liked it alot

---

