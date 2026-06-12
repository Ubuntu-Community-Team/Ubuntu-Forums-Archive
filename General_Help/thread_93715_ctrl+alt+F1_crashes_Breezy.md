---
title: "ctrl+alt+F1 crashes Breezy"
date: 2005-11-22
forum: General Help
---

### Post by Huffers on 2005-11-22
at least, it does for me.

In Hoary ctrl+alt+F1 switched from X to a terminal.  Since I updated to Breezy ctrl+alt+F1 causes the monitor to go blank, and I can't get back into X by pressing ctrl+alt+F7.

In this state I end up having to reset my machine.

Has anyone got any idea whats going on? Has this ever happened before? Is there any more info I should include to aid diagnosis?

---

### Post by gapplewagen on 2005-11-22
After ctrl-alt-f1, try pressing just alt-f2 (no ctrl needed).  anything happen?  alt-f1 through f6 should switch you into tty1-6 with f7 sending you back to X.

Also, you say the screen is black but does it flash and do you have a cursor at all?

---

### Post by Huffers on 2005-11-23
alt-f2 does nothing, alt-f1 through alt-f6 does nothing, thanks for the ideas though.

the screen goes black, there is no cursor, then my monitor says "no signal" and turns itself off.

I'm going to try and get a friend to log in via ssh, then I'm going to press ctrl-alt-f7 and see if his session dies too.

---

### Post by Huffers on 2005-11-23
I logged in with ssh from another computer,
pressed ctrl-alt-f7 on my machine,
but the ssh session stayed working fine -- so the whole machine hadn't crashed.

---

### Post by ranf on 2005-11-23
[QUOTE=Huffers]I logged in with ssh from another computer,
pressed ctrl-alt-f7 on my machine,
but the ssh session stayed working fine -- so the whole machine hadn't crashed.[/QUOTE]
To diagnose this problem you could (over ssh) look at the kernel log:
```
tail -f /var/log/messages
```

Then hit Ctrl+Alt+F1 on your machine and see if there appear any new lines in the log (over ssh).
You stop this tail with Ctrl+C.

---

### Post by utcamperj on 2005-11-25
I have the same problem with ctrl+alt+f2, etc.  I just booted, logged in, and when I pressed ctrl-alt-F1 I got a text login prompt, but when I pressed ctrl-alt-F2 the screen went blank (looks kind of like it powers down but the backlight is still on....I'm on a Dell C400 laptop).  But then it's frozen.  Ctrl-alt-f1 does nothing, as do ctrl-alt-f2, 3, 4....12.

The log snippet I get immediately following pressing ctrl-alt-f2 is:

Nov 25 18:30:26 localhost gconfd (bxncjts-6833): Received signal 15, shutting down cleanly
Nov 25 18:30:27 localhost gconfd (bxncjts-6833): Exiting
Nov 25 18:30:28 localhost kernel: [4294861.661000] mtrr: base(0xe0020000) is not aligned on a size(0x1e0000) boundary
Nov 25 18:30:42 localhost kernel: [4294875.892000] mtrr: base(0xe0020000) is not aligned on a size(0x1e0000) boundary
Nov 25 18:30:57 localhost kernel: [4294890.266000] mtrr: base(0xe0020000) is not aligned on a size(0x1e0000) boundary

And then nothing.

---

### Post by ranf on 2005-11-26
[QUOTE=utcamperj]
Nov 25 18:30:28 localhost kernel: [4294861.661000] mtrr: base(0xe0020000) is not aligned on a size(0x1e0000) boundary
[/QUOTE]
I have never had something like this. I'd search google with:
"mtrr: base is not aligned on a size boundary"

---

### Post by Huffers on 2006-01-31
I've kinda worked out what was going on for me...

it was because I was using the "fglrx" graphics driver..

but thats the only one I know of that supports 3d acceleration on my card (an "ATI Technologies, Inc. Radeon X800 Pro (R420 JI)")

-- edit: incase anyone reads this with the same problem, the fix is to use a 24 bit framebuffer for the tty's (fglrx only supports 24 bit colour).

I got this to work easily by changing the bit of /boot/grub/menu.lst (making a backup first) that says:

title           Ubuntu, kernel 2.6.12-10-k7
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-10-k7 root=/dev/sda3 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-k7
savedefault
boot

to make it say:

title           Ubuntu, kernel 2.6.12-10-k7
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-10-k7 root=/dev/sda3 **vga=792** ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-k7
savedefault
boot

---

### Post by tedrogers on 2006-10-28
Thanks a lot. This little gem of information has been plaguing me for ages.

See my post here [http://www.ubuntuforums.org/showthread.php?p=1678045#post1678045](http://www.ubuntuforums.org/showthread.php?p=1678045#post1678045) for my symptoms. CTRL+ALT+F1 used to hang my machine and I had a fuzzy ubuntu boot logo...but not any more.

You're a lifesaver. Thanks.

---

### Post by Amt0571 on 2006-10-28
I had no luck using a Radeon 8500... I added the vga thing to menu.lst, but the system still crashes with fglrx. Sigh...

---

### Post by tedrogers on 2006-10-29
Make sure you've added the VGA entry exactly as described...then try adding the following code to your xorg.conf file...just add it at the bottom if it's not already there.

```
Section "Extensions"
        Option  "Composite" "0"
EndSection
```

Fingers crossed for you.

---

### Post by Amt0571 on 2006-10-29
It didn't work also :( sigh... I think Edgy and my vid card don't go well together...

---

### Post by tedrogers on 2006-10-29
I'm coming to the end of my knowledge on this one now...sorry I can't make any more sensible suggestions.

I might try reconfiguring the x-server as a last resort, but other than that I have no more ideas.

---

### Post by ampop on 2007-02-13
> **Huffers said:**
> I've kinda worked out what was going on for me...

it was because I was using the "fglrx" graphics driver..

but thats the only one I know of that supports 3d acceleration on my card (an "ATI Technologies, Inc. Radeon X800 Pro (R420 JI)")

-- edit: incase anyone reads this with the same problem, the fix is to use a 24 bit framebuffer for the tty's (fglrx only supports 24 bit colour).

I got this to work easily by changing the bit of /boot/grub/menu.lst (making a backup first) that says:

title           Ubuntu, kernel 2.6.12-10-k7
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-10-k7 root=/dev/sda3 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-k7
savedefault
boot

to make it say:

title           Ubuntu, kernel 2.6.12-10-k7
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-10-k7 root=/dev/sda3 **vga=792** ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-k7
savedefault
boot

It works with me. Thanks a lot

Issue [http://ubuntuforums.org/showthread.php?t=304942&page=2](http://ubuntuforums.org/showthread.php?t=304942&page=2) solved. Thanks to Huffers.

---

