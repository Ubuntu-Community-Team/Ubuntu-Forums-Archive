---
title: "Toshiba M70 left mouse click -&gt; double-clicks..."
date: 2008-11-05
forum: Hardware
---

### Post by wowbaggernp on 2008-11-05
Hi,

Installed Ubuntu 8.10 through Wibu on my Toshiba M70 laptop and been struggling since. I ran into just one, but very annoying, problem:

The left 'mouse' button on my keyboard acts as a double-click.

I have seen the same problem around while searching for it, but haven't found the answer. Apparently a lot of the problems with mice are solved by mucking around in xorg.conf, but since I even had to Google 'how to open xorg.conf' I don't really want to go there (yet). Besides, my USB mouse works fine, it's just that I don't use the mouse a lot.

Any pointers?

Thanks,

Peter.

---

### Post by michaelkeenan on 2008-11-10
I had a similar problem today with a new Kensington Ci70 wireless mouse. I found the solution to my problem in PS5000's post to this thread:
[http://ubuntuforums.org/showthread.php?t=783467](http://ubuntuforums.org/showthread.php?t=783467)

It does involve editing xorg.conf, but I think that's probably the only way. And it's not too scary! Make sure you back it up first.

I will describe exactly how I fixed my problem, but first a big warning: I'm running 8.04 and I read today in a thread someone saying that 8.10 doesn't use xorg.conf to configure input devices. I'm not sure whether that's correct. But if that's the case, doing this might not fix the problem.

(I'm not going to update to 8.10 for a while because I've had too many upgrading regressions in the past.)


So here's what to do, in detail:
-Open a terminal (from Applications/Accessories/Terminal).
-Type (without the quotes) "cd /etc/X11"
-Type "sudo cp xorg.conf backup_xorg.conf" and enter your password when prompted.
-Type "sudo gedit xorg.conf"
This will open xorg.conf for editing. You should find a section like:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection
```

Delete that section and replace it with:
```
Section "InputDevice"
	Identifier	"CorePointer"
	Driver		"mouse"
EndSection
```

-Save and close xorg.conf.
-Restart your computer. Hopefully your mouse will work. It worked for me!

If something goes horribly wrong and, say, your mouse doesn't work at all when you start it up, you need to restore your xorg.conf file from backup. Here's how:
-Open a terminal. If your mouse doesn't work at all, you can use Alt+F1 to open the Applications menu, and then use the arrow keys to open the Terminal.
-Type "cd /etc/X11"
-Type "sudo cp backup_xorg.conf xorg.conf" and enter your password.
-Restart your computer. It should be as it was before.

---

