---
title: "Flash Drive Installation"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by AndyP79 on 2009-01-17
Hi All,
 Okay, so I tried using the USB installation application in the menu. It went on the thumb drive. BUT... then when I restart the computer and choose to run as a LiveCD, it starts, gives me the Ubuntu with the time bar, then I get a black screen with this

BusyBox v1.1.3(debian 1:1.1.3-5ubuntu12)
Built-in shell (ash)
Enter 'help" for a list of commands

(initramfs)


What the heck I am I doing here????

Thanks

---

### Post by TonyFordz on 2009-01-17
I just read another post that said they got that same screen & someone offered help with it you can find it here [http://ubuntuforums.org/showthread.php?t=1042132](http://ubuntuforums.org/showthread.php?t=1042132) hope thats helpful to ya.

---

### Post by BoDwayne on 2009-01-30
I've been struggling with a USB install also, and I kept coming up with the BusyBox built-in shell (initramfs) situation - but I seem to have found a work-around.  First, let me add that I was also running into the same problem with a CD install, and that's why I tried using a USB install (well, that and curiosity!)  I have another machine with Ubuntu 8.10 installed, and I found that creating a USB Live Ubuntu "disk" was easy.
 
Here's what I came up with, and so far it's worked for me. I put this together from tips I picked up from several forum threads, which is how I usually find my solutions - bits and pieces.  I'm going to go give some details of my process in case some bits may help others with similar-but-not-quite-the-same problems.

When I hit the BusyBox (initramfs) prompt, I typed "cat /casper.log" and this told me something like 'no media to read files' from.  I found that some others had overcome this by going into BIOS and changing from sata to raid.  But I didn't have that option in my BIOS.  I have an older machine, which I think is part of my problem.  Another fix was to add "all_generic_ide" into the command line.  Some said this worked, and other said it didn't.  When I first tried it, it didn't. 

At the first Ubuntu screen, on install, where you have the options of "run Ubuntu without making changes..." or "Install Ubuntu", etc., there are some F1, F2, etc. options at the bottom.  I hit F1 for Help, then F6 or 7, where I found the full command is:

"generic.all_generic_ide=1"

Choose your option above (Install, or Run Live, etc.) then hit F6.  You'll see the command line.  Go in there and add "generic.all_generic_ide=1" (without quotes) anywhere in that stream, with a space before and after. Then hit ENTER and the disk will install, without hitting the BusyBox hangup.

But for me, when it loaded the desktop screen, I didn't have taskbars above and below. So, I had to do one more thing.

There is a statement in the command line (back at the F6 option) that begins "file=/cdrom/preseed. . . " (sorry I don't have the full statement, I use sketchy notes).  Since I'm not using a CD, I changed it to read "file=/usb/preseed. . ."  This, plus adding the "generic.all_generic_ide=1" statement, got me into the Live CD screen.

I have to say that I've only used this to get into the Live CD option so far.  I'm trying to do some tweaking on my partitions before I actually install, so I don't know if it's a permanent fix or not.  But I've had Ubuntu 7.04 running on this machine for a year and a half, so I'm assuming that once I get 8.10 installed it will work.

---

### Post by frunns on 2009-01-31
Awesome BoDwayne, gonna follow your advice next time I try it out!

---

### Post by BoDwayne on 2009-01-31
Okay, so that's not quite it.  Following the steps I wrote above, I was able to get my LiveUSB to install, but now everytime I run it I drop into the BusyBox shell during the boot process.  However, at the (initramfs) prompt, I can type "exit", then hit enter, and it continues to load.  This is is a pain, and I think there are other problems as well.

The link TonyFordz gives above led me to this - 
"Try this instead:
- Press CTRL-ALT-F7. If you have a graphical interface, it should open then.
- Press CTRL-ALT-F2, CTRL-ALT-F3 and CTRL-ALT-F4 to open your other terminals. See if you see more information, error messages and stuff like that.
- Type 'return' or 'exit' at the prompt and press enter. If you're lucky, the boot process will continue."

I need to go back and look at the errors listed.  There are errors listed on the BusyBox screen, such as "rootdelay=..." and "root=..." suggesting the system isn't waiting long enough for root, or looking in the wrong place.  I think the delay time might by an issue in my case, but I don't know how to fix it.
 
Anyone who knows more, feel free to jump in!?

---

### Post by davec64 on 2009-01-31
When at the busybox prompt have you tried 

```
Exit
```

On my main install Iget the busybox regularly and trying exit (sometimes repeatedly!) boots into the OS. Mind you I haven't found a solution that works yet to fix it permanently!:p

---

### Post by BoDwayne on 2009-01-31
Yeah, typing "exit" works.  Sometimes there's as much as a thirty second delay, and then it will boot.  But there has to be a reason it's hanging there. . .

---

### Post by davec64 on 2009-02-01
You could try adding a boot delay to the boot parameters. Mind you this doesn't solve the problem!

Just a thought, the latest kernel update seems to have fixed my problem of dropping to the Busybox prompt (touch wood!), perhaps try with the latest kernel.

---

### Post by BoDwayne on 2009-02-11
Sorry for the delay in responding, I've been distracted - tweaking by 8.10 install, among other things.

> **davec64 said:**
> You could try adding a boot delay to the boot parameters. Mind you this doesn't solve the problem!

Just a thought, the latest kernel update seems to have fixed my problem of dropping to the Busybox prompt (touch wood!), perhaps try with the latest kernel.

I've upgraded to the latest kernel, 2.6.27-11-generic, and it still went to the BusyBox shell.  So I added "all_generic_ide=1" to /boot/grub/menu.lst  That keeps me out of BusyBox, but there's a full 60 second delay before it proceeds.  The system boots up fine and everything seems to work - there's just that annoying delay.

One thought - I don't understand SATA vs. IDE, but my drives are recognized as /sdb  not /hdb.  Does that make a difference?

davec64 - you said "try adding a boot delay to the boot parameters".  How do you do that?  Of course, I seem to have a boot delay on the natural, but I'm curious.

---

