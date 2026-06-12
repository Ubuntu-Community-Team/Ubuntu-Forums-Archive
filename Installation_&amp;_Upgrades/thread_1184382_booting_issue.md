---
title: "booting issue"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by SlightlyInsane on 2009-06-11
this is the error I am getting... any ideas?

[http://i96.photobucket.com/albums/l166/hondafox315/Picture2.jpg](http://i96.photobucket.com/albums/l166/hondafox315/Picture2.jpg)

---

### Post by SlightlyInsane on 2009-06-11
Can anyone help me out. bump

---

### Post by PreviousN on 2009-06-11
Oops means kernel panic. Check this out for some more information. [http://en.wikipedia.org/wiki/Linux_kernel_oops](http://en.wikipedia.org/wiki/Linux_kernel_oops)

Several things could be contributing to your "oops." Have you ever been able to successfully boot into ubuntu before? If not, you may have a setting wrong in your bios, or a boot option wrong in grub. You may also try reinstalling ubuntu (since you obviously have successfully installed it once...).

The cool thing about ubuntu is that most of your data is stored in a place located in "/home". This makes it easy to backup. Just backup /home, and reinstall is easy. Takes less than an hour. I can almost guarantee you that trying to fix this the hard way will make you frustrated. On the other hand, you'll likely end up learning something.

Good luck. I can't really read the writing on the screen in the picture. Maybe if you could type the last error and first errors in? Thanks!

---

### Post by SlightlyInsane on 2009-06-11
I've never had ubuntu running successfully on this machine, but it was running windows fine.
I reinstalled with no avail.
What bios settings should I change?

---

### Post by sahabcse on 2009-06-11
Try this...It may help

[http://sahabm.blogspot.com/2009/02/kernel-panic-not-syncing-ubuntu-810.html](http://sahabm.blogspot.com/2009/02/kernel-panic-not-syncing-ubuntu-810.html)

---

### Post by SlightlyInsane on 2009-06-11
*Loading hardware drivers...
[ 8.674278] unable to handle kernal paging request at fffff
[ 8.674412] IP: [<ffffff8041e9f2>] clear_page+0x12/0x40
[ 8.674506] BAD
[ 8.674548] Oops: 000b [#1] SMP
[ 8.674669] last sysfs file: /sys/module/soundcore/initstate
[ 8.674764] Dumping ftrace buffer:
[ 8.674764] BUG: unable to handle kernal paging request at ffff
[ 8.674890] IP: [<ffffff802aa264>] ring_buffer_empty_cpu+04/
[ 8.674980] BAD
[ 8.675022] Oops: 0009 [#2] SMP
[ 8.675142] last sysfs file: /sys/module/soundcore/initstate

---

### Post by PreviousN on 2009-06-11
Thanks for typing that information up! That makes this thread much more useful to other people should they have the same problem. Okay...

When you installed using the livecd (assuming you used that versus wubi), did you successfully boot into the installation session? Did you get the menu and the click through map, etc.?

An anecdote: A machine I built wouldn't boot into the normal ubuntu installation livecd. I had to use the alternate install cd. You may try that. I know it sucks downloading another 600+ megabytes... But it may work!

Before you try that, however, do you get the same error when you hit escp at grub's boot screen and choose to boot into recovery/failsafe?

Also, what kind of hardware are you running? Is this a laptop, desktop, etc.?

If you built this computer yourself, what is the motherboard? I ask because maybe there is a problem associated with hardware. Another anecdote is how one of my laptops had a problem with wireless and I was able to search for the model number + ubuntu in google. I was able to successfuly fix my problem that way. You may be able to as well.

So. What are we working with here? A dell? A home built machine? Etc?

---

### Post by PreviousN on 2009-06-12
Did you try any of the suggestions, and, what is the make/model of your computer?

---

