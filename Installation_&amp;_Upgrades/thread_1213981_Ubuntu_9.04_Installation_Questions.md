---
title: "Ubuntu 9.04 Installation Questions"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by javier10132 on 2009-07-15
My previous attempt to install Linux software was an utter **[COLOR=DarkRed][failure][/COLOR]**- and I honestly could say I had little idea of what I was doing; I was attempting to install Xubuntu on an old Dell Latitude laptop and during installation I got an error saying I didn't have enough hard disk space. I booted Windows to delete some old files to save space, and when I re-booted the CD my laptop had somehow installed as a dual-boot system (which, on an old laptop like that- would make it slower). I attempted to remove Linux from my system and eventually my Hard Drive just gave up, and I couldn't boot onto either one.

I have a newer laptop with these specs:** Intel Pentium M processor 1.60GHz 589 MHz, 1 GB of RAM.** The name of my graphics card is** Intel 82852/82855 GM/GME Graphics Controller**, and the model of my laptop is* Dell Latitude D400*. I'd just like to know if I can run Ubuntu on my computer, and what I could do to prevent any catastrophic mistakes like I made in the past, because next time I might not be so lucky..

---

### Post by zerhacke on 2009-07-15
Yes, Ubuntu will install and run on your machine.  However, given your slower CPU speed, I suggest looking into Xubuntu, as it has lower system requirements than Ubuntu or Kubuntu.

---

### Post by javier10132 on 2009-07-15
Ok great thanks, do you know any tutorials on how to succesfully install Xubuntu so I won't mess up like the last? :l

---

### Post by mikewhatever on 2009-07-15
You should be able to install and run Ubuntu on that machine without issues, provided there is enough disk space. Follow the [installation guide]("https://help.ubuntu.com/community/GraphicalInstall"), and backup your files just in case. If, for some reason, your system becomes unbootable, use a live cd to access the forums and post a help request.

---

### Post by raymondh on 2009-07-15
> **javier10132 said:**
> Ok great thanks, do you know any tutorials on how to succesfully install Xubuntu so I won't mess up like the last? :l

are you wanting to sole-boot or dual boot?

EDIT : I type so slow.  Mike's right.  The install guide should help.  If you wish other set-ups (i.e. separate /home, etc) post back.

---

### Post by javier10132 on 2009-07-15
Thanks for the help guys, and you mentioned that I need a sufficient amount of space-
well I have a 60 GB Hard Drive with 45 GB free space, and do you guys recommend dual booting on my system?

---

### Post by shicy on 2009-07-15
absolutely :D

---

### Post by javier10132 on 2009-07-15
Thanks!

---

### Post by javier10132 on 2009-07-15
> **raymondhenson said:**
> are you wanting to sole-boot or dual boot?

EDIT : I type so slow.  Mike's right.  The install guide should help.  If you wish other set-ups (i.e. separate /home, etc) post back.

Dual Boot, last time it just installed on it's own without giving me options.

---

### Post by raymondh on 2009-07-15
> **javier10132 said:**
> and do you guys recommend dual booting on my system?

My thoughts:

- If one OS fails (or gives me trouble), I have another to back me up and keep me productive.
- If I virtualize and the host OS crashes, neither can I access the guest OS
- I will dual-boot only if I have enough space in my HD

Your preference really.  I always believed that dual-booting is best until you are ready to single-boot Ubuntu (or comfortable with Virtualizing).

Happy Ubuntuing.

---

### Post by raymondh on 2009-07-15
Some tips:

-Read the release notes.
-Back up your files.
-Defrag windows before dual-boot install
-Burn the iso, image as slow as possible
-Boot into the liveCD and check for defects and hash
-Try the liveCD in live session to see how it reacts with your system specs' and hardware
-Read up on install references and have a go.

If you are installing Ubuntu:

[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)
[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)
[http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020)
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

Good luck.

---

### Post by javier10132 on 2009-07-15
> **raymondhenson said:**
> Some tips:

-Read the release notes.
-Back up your files.
-Defrag windows before dual-boot install
-Burn the iso, image as slow as possible
-Boot into the liveCD and check for defects and hash
-Try the liveCD in live session to see how it reacts with your system specs' and hardware
-Read up on install references and have a go.

If you are installing Ubuntu:

[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)
[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)
[http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020)
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

Good luck.

Thanks for the tips :p

---

