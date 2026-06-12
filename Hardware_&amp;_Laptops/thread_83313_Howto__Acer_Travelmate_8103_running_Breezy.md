---
title: "Howto:  Acer Travelmate 8103 running Breezy"
date: 2005-10-28
forum: Hardware &amp; Laptops
---

### Post by dcardamo on 2005-10-28
It's on my site.  Feel free to copy it and put it on the ubuntu pages or on your own sites.

[http://www.hld.ca/archives/2005/10/27/desktop-running-ubuntu-510-linux-breezy-badger/]("http://www.hld.ca/archives/2005/10/27/desktop-running-ubuntu-510-linux-breezy-badger/")

---

### Post by athem on 2005-10-29
Thanks for pulling this together and posting it.  I installed Breezy on a new Acer Travelmate 8104WLMi and saw some of the same problems.  One thing I noticed is that the Network Administration utility doesn't work properly w/WEP.  If you enter a an ASCII string as the WEP key, it doesn't seem to get properly written as the wireless-key entry in /etc/network/interfaces.  So if you use the utility, and need to configure WEP, then use a Hexidecimal key (check your router settings to get the string).  Note that I did "downgrade" my ipw2200 drivers to 1.0.0 (from Breezy's 1.0.6, as recommended by other) before discovering this, but I suspect it was the problem all along.

Also, in order to get sound working, I had to do this from the main panel menu:

Applications-->Sound & Video-->Volume Control

Then, in the Volume Control application menu I changed the device:

File-->Change Device-->Realtek ALC880 (OSS Mixer)

and got sound for the first time. I'm not sure why the ALSA device didn't work, but the Realtek one seems to work OK. 

I'm curious what others' experience has been with these on the Acer Travelmate 8103/4 running Breezy.

---

### Post by Asraniel on 2005-10-29
nice, have to check the dynamic cpu freq fix :-)

could someone burn a cd? doesent work here

---

### Post by strandlooper on 2005-10-30
cd burning works fine for me.
For example: Gnomebaker as root, audio cd. speed 24, writing time 193s. The same file burned on cd in MS XP: speed 24 writing time 237s. Good speed!

---

### Post by Asraniel on 2005-10-30
hmm. ok. could you show me your fstab? because i changed which device is mounted as cdrom, like i found it in another thread that suggested to do that to burn cds. now i dont remember which was the original device i have to mount.

So you can only burn as a root? thats not very userfriendly, is it?

---

### Post by strandlooper on 2005-10-31
You are right cd burning for everybody shouldn't be an issue but obvously Gnombebaker thinks different. As user with cdrom group rights I didn't manage to burn even though I tried hard. Funny things happend with permissions which is not in line with my Linux knowledge. I got different permission data from the terminal and the nautilus file manger so I gave up. I think its a bug. There is a newer Gnomebaker version available but not as deb file and from source I failed to install. 
However to burn a cd just use a different burn program. I tested Graveman as user which works very straightforward for me. Before you start burning procedure just check out you have installed externall programs under preferences otherwise you get an error massage. A green or red lap indicates the status. I had to add the flac tool than Graveman worked perfect.
I hope this helps

---

