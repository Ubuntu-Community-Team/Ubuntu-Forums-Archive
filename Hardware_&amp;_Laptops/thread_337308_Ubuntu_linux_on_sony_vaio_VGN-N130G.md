---
title: "Ubuntu linux on sony vaio VGN-N130G"
date: 2007-01-12
forum: Hardware &amp; Laptops
---

### Post by arashbi on 2007-01-12
Hi every body!
I am new to ubuntu and his is my first post here (so welcome me)! I just bought  Sony vaio and decided to try Ubuntu on it instead of my favorite distro Debian.
Anyway it seems that  removing the widows from vaio box will remove the waranty of the box and on the other hand, Sony does no ship with a windows CD. You got to create rescue DVD's to be able to recover your system lately in case of a windows crash ( Sony ever understand how to handle the market, remember the BetaMax?) 
So I booted to ubuntu which was perfect and create my partitions by resizing the windows partition and go to installation. The only point was that I did not want grub to install on MBR and i wanted it on my third partition. Installation is nearly successful, it went all the way but could not install the grub nor copied any of it's files to the hard drive. i did the rest of installation by hand and made the windows boot loader to recognize the ubuntu. The functionality is nearly perfect: graphic, sound, wireless and ethernet is working out of the box and perfectly. I did not check the modem.

However there is some small problems you may please help me. 
1-When I choose to boot in my linux box from boot loader, it loads the grub shell and i got to boot in my box by  hand every time. i tried to write a grub.conf but it didn't help and I still got to boot manually
2-I found out how to make touchpad scrolling work on it [http://ubuntuforums.org/archive/index.php/t-77359.html]("http://ubuntuforums.org/archive/index.php/t-77359.html")
but the problem is every time I reboot or restart the X, strangely the event number of ALP changes! 
3-The battery meter of gnome shows the percentage of the remaining power correctly but it makes funny mistakes about the time. A popup apears warning that my power would be finished at 4 minutes but when I go to the applet at the panel, it says i have for example 2 hours to go!

Well thank you ubuntu guys great job!

---

### Post by re49togood on 2007-03-14
I also am running on a vaio n130g. I don't know the solution to your problems. Grub works fine for me. My problem was the wireless, it didn't work out of the box for me. However, it does detect the card but I cannot access any networks. Any suggestions?

---

### Post by re49togood on 2007-03-14
Nevermind my post. Wireless is working great!

---

