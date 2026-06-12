---
title: "Geforce 9600 GT, Ubuntu dies when drivers are installed."
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by Zondana on 2009-05-06
I have a problem with my drivers that i need help with. I have been seatching these forums and Google for 2 days now, and have found NOTHING that helps.

I install Ubuntu, and everything seems fine, Until i install the Nvidia drivers. After i do that i can no longer restart the computer since if i do that i can't get in to the GUI anymore.

This goes for Ubuntu 8.04, 8.10, AND 9.04
I have also used 3 different Nvidia drivers with the same result.

I get a whole lot of long and undescribing error messages including a few that can be writen here.

"Fatal servere error: No screens found"
xinit: (errno2)
xinit: (errno3)
xinit: (errno111)

I have 2 screens and 2x Nvidia GeForce 9600 GT, set up in SLI.

i have looked at the Xorg file and it seems fine from what i have seen on other forum threads.

Another thing i should mention is that if i try to stop or restart GDM it uses about a minute to restart GDM and nothing changes.

I have tried to purge add uninstall GDM and Nvidia*
Used Envy, downloaded drivers from the site, used  the built in Driver manager. All the same.

I have tried everything i have come across and have come to the point where i have more or less given up and just accepted that Linux drivers don't support my hardware or are just majorly faluty in design. 

Can someone help me plz?

---

### Post by Mark Phelps on 2009-05-06
See the similar thread: 

[http://ubuntuforums.org/showthread.php?t=1125415]("http://ubuntuforums.org/showthread.php?t=1125415")

---

### Post by Zondana on 2009-05-06
Well yea... the problem is, i have tried that as well, with no improvements. I have used 3 different drivers downloaded and installed in 3 different ways. Just keep getting the same bug... =/

Edit: also all tries have been on clean and new installations.

---

### Post by Zondana on 2009-05-07
/bump

Please help...
I have tried both solutions stated in that thread and none of em made any difference..... :(

I would very much like some help with this problem. I can't use Ubuntu at all while i have this problem and so i have to use my damn Windoooze... -_-

---

### Post by duffrecords on 2009-05-11
Not that this solves your problem, but relax... You can still accomplish virtually any task without the GUI.  Here are three commands that will help you find your way around in the dark:
```
sudo shutdown -r now
```
```
sudo apt-get install lynx
```
```
lynx http://ubuntuforums.org
```

---

