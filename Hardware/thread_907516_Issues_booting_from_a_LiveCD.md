---
title: "Issues booting from a LiveCD"
date: 2008-09-01
forum: Hardware
---

### Post by Twitster on 2008-09-01
I recently bought Hacking: The Art of Exploitation, the 2nd edition. It comes with a ubuntu liveCD that works in my desktop from 97, on my dad's computer, but NOT on my laptop?
To be more specific about the error, the initial bootup menu is displayed on screen, and when I select "Boot from LiveCD" (or whatever it is) here is the output..

```

[    0.243554] PCI: Failed to allocate mem resource #6:20000@e00000000 for 0000:01:00.0
Loading, please wait

(PAUSES HERE FOR A BRIEF MOMENT)

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs) _

```
And that's it.

"The only requirement is an x86 processor". I'm pretty certain that I have an x86 processor, but I cannot think of anything else the issue could be with..
The specs of the processor are here: [http://processorfinder.intel.com/details.aspx?sSpec=SLAP9](http://processorfinder.intel.com/details.aspx?sSpec=SLAP9)
Other details..
The laptop is a Dell Vostro 1710, 2x2048GB ram, 256mb 8600m nvidia graphics card, the OS is Vista Business, and a 250GB (5400rpm) SATA hard drive.

I have done quite a bit of research on this bug.. Two possible fixes were (1) to change the video settings to work from a smaller more common resolution and (2) to add 'reserve=0xe0000000,0x20000' to pre-reserve the kernel memory.

Both have failed. To try and double check the video fix, I started the kernel with the graphics in "Safe Graphics Mode". This didn't work.

Has anyone encountered anything like this? For some reason, I haven't found any issues with any AMD processors. Could this be specifically a bug for Intel?

---

