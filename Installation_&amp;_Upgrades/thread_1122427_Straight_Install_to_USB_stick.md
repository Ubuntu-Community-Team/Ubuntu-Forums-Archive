---
title: "Straight Install to USB stick"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by ddalley on 2009-04-11
I think I may have caused myself a big headache by trying to install Xubuntu normally (not as a Live install) to a USB mem-stick on one computer for use on another.

I installed Xubuntu not as a Live install but as a normal install, as if the mem-stick was a hard drive, through a normal laptop. The stick is to be mainly used on an Acer Aspire One, but I'd like to use it with a normal laptop, too, though. The AAO has a short screen and some config panels are too large to use properly (hence using the other laptop).

It seems the installer looks for the wireless hardware differently and now Xubuntu's NetworkManager doesn't see the wireless device, and I have no idea how to fix this. It connects to the Internet fine through a cable. Can I somehow make N-M find the current AAO wireless device, configure it and just move on? N-M instructions for doing this don't really exist.

Who knows what other weird problems may be lurking for me, too, such as not finding the laptop's hard drive partitions.

Or should I avoid a mess, start over and just try to live with a Live mem-stick? (I've been having troubles with Live mem-stick installs actually surviving. Two installs have completely broken down on me recently.)

Your advice is appreciated.

---

### Post by lindsay7 on 2009-04-11
Have you looked or tried "Unetbootin".  Look it up on the Internet. You can get it from the Synaptic Package manager.

---

### Post by ddalley on 2009-04-11
Yes, Lindsay, I have used Unetbootin for making a typical persistent USB stick when other better tools weren't available, but I didn't think it applied here.

---

### Post by Herman on 2009-04-11
> I think I may have caused myself a big headache by trying to install Xubuntu normally (not as a Live install) to a USB mem-stick on one computer for use on another.

I installed Xubuntu not as a Live install but as a normal install, as if the mem-stick was a hard drive, through a normal laptop. The stick is to be mainly used on an Acer Aspire One, but I'd like to use it with a normal laptop, too, though. The AAO has a short screen and some config panels are too large to use properly (hence using the other laptop).I doubt if the fact that you installed in a memory stick as a normal hard drive install has anything at all to do with your problems.
I have installed Ubuntu in lots of USB flash memory sticks and as far as I can tell it works just as well or better with the conventional install method. And it's quicker and easier too.

---

### Post by ddalley on 2009-04-11
Did you ever have problems switching between different computers, though, or was the one install always used with the same computer?

---

### Post by Herman on 2009-04-11
> Did you ever have problems switching between different computers, though, or was the one install always used with the same computer? With modern versions of Ubuntu, say Hardy Heron and later, I haven't had any problems moving between most ordinary computers. Everything just works.
Having said that though, I do know that there can still be some special hardware that can be troublesome to get working properly in some computers.

Use these command to get more information about the networking cards in the computer you're having trouble with,
```
sudo lshw -C network >> problemhardwarefile
``````
iwconfig >> problemhardwarefile
```Go look in your /home/username folder after you run those commands, and you should find a file named 'problemhardwarefile', with some information in it.

Armed with that information you should be able to run a search in the Ubuntu Web Forums and hopefully find where someone has solved the same problems already.
You might need to go to [Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336") and start a thread there if you can't find anything.

---

### Post by Herman on 2009-04-11
You might also want to paste the brand of wireless card in the search bar in 'Applications'-->'Add/Remove', or else in 'System'-->'Administration'-->'Synaptic Package Manager' to see if there are any special drivers or software available for your wireless card in the repositories that you can easily install. :)

---

### Post by tamas305 on 2009-04-21
Try post 3 on this [thread]("http://ubuntuforums.org/showthread.php?t=1116206").

-tamas

---

