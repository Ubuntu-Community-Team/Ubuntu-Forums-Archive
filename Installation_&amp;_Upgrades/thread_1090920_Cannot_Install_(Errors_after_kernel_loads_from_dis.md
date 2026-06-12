---
title: "Cannot Install (Errors after kernel loads from disk)"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by ianmprice on 2009-03-08
To start out im fairly new to linux, however im very experienced with computers.

I recieve these errors when trying to install either 8.10 or 8.04 on the box ive designated as my server.  

[IMG]http://img25.imageshack.us/img25/5994/img0023jwy.jpg[/IMG]

Ive tried a few of the boot modifiers from the disk but it does the same thing. Ive tried the disk on other systems and it works fine.

I've also had 8.04 installed on this box up untill this afternoon when i wanted to reinstall and start over. Ive tried to search for help but im not even sure what the problem is so i am unable to efficiently search for help.

hopefully someone can point me in the right direction.

Thank you for your help.

*edit*
resized annoyingly oversized photo.

---

### Post by Neo_The_User on 2009-03-08
And it just loops those lines over and over and over again? 8.04 and 8.10, same drive, drive works fine in other computer? That cancels out it being a problem with the Ubuntu kernel and a faulty drive. Ummm, flaky motherboard?

---

### Post by ianmprice on 2009-03-08
for a few minutes it does. all the while the left hand number continues to increment. after a few minutes it goes to a black screen. i am able to enter text, but there is no intelligle response from the box. I can however ctrl+alt+del and it will signal a kill and restart.

Possibly a flaky MoBo, but once it was installed the system was running fine. So i would like to try to figure out what conditions allowed it to install.

*side note*

Winxp installs fine.

---

### Post by Neo_The_User on 2009-03-08
See if that drive is supported by any linux kernel. Try (just to see if it works) and see if you can run Fedora, OpenSUSE, Mandriva, or whatever on there. Fedora requires i686 CPU for live cd, Mandriva requires i586, OpenSUSE is i586, I can't think of any 100% i386 OSes ATM besides debian right now.....

---

### Post by ianmprice on 2009-03-08
ok, im gonna try the openSUSE live CD and get back to you.

Any idea what these errors mean?

---

### Post by Neo_The_User on 2009-03-08
Well ATA is a type of connector AFAIK that usually plugs into hard drives. If it works with OpenSUSE then its not a hardware issue, probably the Ubuntu kernels can't talk to something in your hardware so... You can try copying the OpenSUSE kernel on to Ubuntu in /boot and edit menu.lst as necessary.

---

### Post by ianmprice on 2009-03-08
Well i gave the OpenSUSE install disk about 10 minutes. It seems to hang at what would would be the same place as the ubuntu disk. I can't be sure becuase there was a splash screen with a progress bar... the bar didnt move, not even one pixel.

*edit*

right after i posted this it moved a little. so still waiting.

---

### Post by Neo_The_User on 2009-03-08
Hmm... I'm not too great with low-level problems like these but if anybody who knows what they are doing decides to jump into this thread, you'll get some help. My knowledge of these things are not too great.

---

### Post by ianmprice on 2009-03-09
Ok, well it finished loading, but errored out. it says 

It says "invalid signature" however, it's refferenceing a URL, so it seems like the kernel loaded fine. 

I am going to try a plain debian distro and see what happens, failing that I will try substituting the OpenSUSE kernel for the ubuntu kernel and post how it goes. 

Any other suggestions are greatly appriciated!

---

### Post by Neo_The_User on 2009-03-09
Maybe the OpenSUSE kernel has something turned on that the Ubuntu kernel left off. You could compile your own custom kernel as well and turn off all the debugging in the OpenSUSE kernel. The OpenSUSE kernel is pretty big.

---

### Post by ianmprice on 2009-03-09
Ok, well im gonna mess with it more this weekend... Ill post what happens.

Thanks for your help!

---

### Post by ianmprice on 2009-03-16
Sorry for the delay in updating this thread... Life caught up to me for a bit.

Anyway, so i go to mess with my box this evening... and i try just once to see if maybe it will load this time. Much to my surprise it did. The kernel loaded with no errors and went smoothly right in to setup. 

Somehow the SATA HDD i was using had become unplugged from the controller. With out plugging it back in I restarted the box and it worked again. I restarted again with it plugged in this time and bam... Errors.

So to get Ubuntu installed I just ran setup with the SATA disconnected and once the kernel loaded.. reached in and popped it back in. 

Not sure yet if its the whole controller or just the SATA0 port...

Chalk this one up to *shrug*

Thank you so much for your help though.

---

