---
title: "Suspend hangs if external drive is mounted"
date: 2010-03-21
forum: Hardware
---

### Post by Comrade42 on 2010-03-21
Hello,
I've been having an issue with suspending when I have an external hard drive plugged into my USB port. 
This issue began when I upgraded to Karmic 9.10 a few months ago.

If I try to suspend (or hibernate) and the drive is mounted, the screen will go black and I'll see a blinking cursor, and about a minute later a strange error message will pop up (if needed I can recreate the error and write it down) complaining about I/O blocks and maybe FAT something.

Then I can sometimes sorta fix the problem by using alt-F1 or alt-F7 but my computer runs terribly and usually freezes after that if I don't restart.

I can avoid this issue by manually unmounting the drive before suspend but it's sort of a rub when I forget to do so and suspend fails.

My error might be similar to this one:
[http://ubuntuforums.org/showthread.php?t=1285275&highlight=external+hard+drive+hang+suspend](http://ubuntuforums.org/showthread.php?t=1285275&highlight=external+hard+drive+hang+suspend)

But I tried that hack and it did not fix my problem. (I suppose I could try harder.)

Much thanks to anyone who can help out!

Oh, my specs:
Lenovo T500 ThinkPad notebook running Ubuntu 9.10
Samsung 500GB USB drive (HXMU050DA/M22) using NTFS I believe (Properties says "Filesystem type: msdos")

---

### Post by Comrade42 on 2010-03-22
Bump

---

### Post by Comrade42 on 2010-03-23
> **Comrade42 said:**
> Bump
maybe I'm bumping at odd hours for folks...

---

### Post by fugrank on 2010-03-24
That's brilliant; I had no idea that the external drive was the problem was.  Ubuntu was mostly unusable on my laptop because suspend did not work.  I have an 8 Gb SD card inserted into the card reader all the time, and thanks to you, I found out that's what was causing suspend to fail.  While I can't help you solve your problem, I can confirm that unmounting prior to suspend fixes my problem as well.  That script you linked to should work, but it's obviously a work around.  You're supposed to run that script every time you want to sleep / wake up (actually, I think it remounts on its own upon wake up).  It doesn't really "fix" suspend.

Edit:

Also, if you can edit the script here, I think it can do what you want.  It describes basically the same problem.  
[https://help.ubuntu.com/community/AspireOne/Ubuntu9.10](https://help.ubuntu.com/community/AspireOne/Ubuntu9.10)
I'm not an expert at this, but I think this is the most important line you need to edit:
```
for drive in $( /bin/ls /dev/mmcblk?p* ); do
```
Specifically, the mmcblk?p* part should be whatever your device is.  Let me know how it works out

Edit Edit:

Actually there might be more changes, particularly with the checking if it actually unmounted or not...
Okay, it looks like the if statements do work, just find out where your drive is mounted

---

### Post by Comrade42 on 2010-03-28
Hmmmmm, it worked! It still displayed some error messages (like "FAT: bread failed ..." and "error: sdb block ...") but then it went right into suspend. That's pretty neat. Thanks for the help!

---

### Post by Comrade42 on 2010-03-29
Er, shoot, it doesn't always work.

Here's the specific text of the error when I get the hang on suspend:
```
end_request: I/O error, dev sdb, sector 64
Buffer I/O error on device sdb1, logical block 1
```
Note: The computer successfully suspends if I simply unplug the external drive, though this is a scary solution to have to resort to.


I think the difference this time was that I had a program accessing the external drive.

As a sidenote, the specific text I changed in the script recommended by fugrank was:

```
        for drive in $( /bin/ls /media/GANTRITHOR ); do

```
from
```
for drive in $( /bin/ls /dev/mmcblk?p* ); do

```
Perhaps I should have used "/dev/sdb" instead of the specific name of the drive I was dealing with ("GANTRITHOR")?

Any help would be great! Thanks!

---

### Post by Comrade42 on 2010-03-31
Hmm, I've encountered a new problem: My hard drive doesn't auto-mount when I plug it in anymore, even after multiple restarts and plug/unplugging, and having it plugged in before booting.

I changed the "/media/GANTRITHOR" in my above code to "/dev/sdb*" after thinking about it a little bit.

But the drive not auto-mounting anymore is bothering me. Any advice?
Thanks!

---

### Post by fugrank on 2010-03-31
> **Comrade42 said:**
> Hmm, I've encountered a new problem: My hard drive doesn't auto-mount when I plug it in anymore, even after multiple restarts and plug/unplugging, and having it plugged in before booting.

I changed the "/media/GANTRITHOR" in my above code to "/dev/sdb*" after thinking about it a little bit.

But the drive not auto-mounting anymore is bothering me. Any advice?
Thanks!

Have you tried disabling/deleting the script and seeing if that fixes it?  I think the other problem you mentioned with needing to unplug it before your computer would suspend is because it was busy.  This really is just a work around, and not a real fix.  The drive isn't supposed to unmount when it's busy.

---

### Post by Comrade42 on 2010-04-09
Removing the script doesn't bring back my auto-mounting, oh no. This is kinda lame, eh.

Is there a chance I might've corrupted something when unplugging my drive one of those times to make suspend work? I might need to ask a separate question about bringing back my drive (or wait for Lucid Lynx I suppose).

---

### Post by charlesopondo on 2010-07-09
I've the same issue; the only way out has been to unmount before suspending. Problem is, the reason I have the SD card permanently in is to automatically run regular backups on projects I'm currently undertaking. Manual mounting/unmounting beats the logic of 'automation'...

---

