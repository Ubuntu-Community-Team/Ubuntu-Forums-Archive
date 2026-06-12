---
title: "NeoMagic 2160 Video"
date: 2005-07-27
forum: Hardware &amp; Laptops
---

### Post by DementedTed on 2005-07-27
I just loaded Ubuntu onto an old laptop (Dell Latitude CPi D266XT).  The actual install went great, compared to other distros I had previously tried.  I am, however, having some video issues.  The laptop uses the NeoMagic 2160 video chip, which Ubuntu was able to recognize.  However, I can only get 800x600 out of it right now, and the font is very funky looking... one side of some letters is thicker than normal.  The specs for the laptop should allow for 1024x768, so I'm not sure how to go about fixing this.  Anyone have any suggestions?  Thanks!


~Ted

---

### Post by svetzy on 2007-12-26
I have the EXACT same problem -- any info about how to fix it?

Thanks
(I am a 100% noobie)

---

### Post by cufflynx on 2008-01-19
Newbie as well, same problem, lost on how to edit the Xorg.conf file to allow 1024x768 resolution. seems to be there. What's a boy to do?

Laptop, Solo 2500 Neomagic chipset, 256M  mem, 5.2 Gb HD, no sound, some video corruption on load. (do I need to exclude some memory locations?) seems to run well with no crashes.

Help with direction to solutions to sound card and PCI card modem internet connection. Thanks in advance.

I know a lot about Windows, networking and internet connections. This baffles me. Be gentle!

---

### Post by easygoingtodd on 2008-01-22
I have the same trouble with my Maximus laptop using a neomagic chipset.  I got the solution from my brother.  Here is what he wrote to me.

------------------------------

Here's another thing you should try:
1) Ctrl + Alt + F1  (this will go to a fullscreen terminal)
2) sudo dpkg-reconfigure xserver-xorg (this will start the
reconfigure of the X11, giving you the options of whether or not to
probe the hardware or just to use a specific resolution)
3) sudo shutdown -r now


I am thinking that when it probes the hardware, it doesn't get a
repsonse that let's it know that the screen CAN handle the desired
resolution.  So, I would say "no" to the probe question.  And then it
will ask you which resolutions you want available.  Put an asterisk
next to the ones you want, then tab down to the OK button and hit
ENTER.

------------------
He was right on target!  Although the first time I tried it the resolution came out only at 640X480.  The next time I allowed the program to autoprobe "the video hardware", but not the monitor.  Try entering those values using the "medium" skill level settings, where you only have to choose the "1024 X 768 @ 60Hz" option, and it worked perfectly for me.  I have a Maximus Laptop using a Pentium 266MHz with 128 MB RAM.  Thanks, Bro!

---

### Post by cufflynx on 2008-02-14
Thank you! After a few attempts (all operator errors) I was able to make it work perfectly. Off to work on the next thing!

---

