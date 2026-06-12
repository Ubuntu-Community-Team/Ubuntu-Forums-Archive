---
title: "unable to log in after install"
date: 2009-07-17
forum: Installation &amp; Upgrades
---

### Post by electromagn3to on 2009-07-17
I am trying to install ubuntu 9.04 on a iMac G3, 320MB RAM, 20GB HD, and Power PC G3 500MHz, I am using the Alternate install CD with the cli-powerpc install. Once it finishes the installation, restarts and prompts me for a name and password I enter what I set in the installation and it tells me Login incorrect.

I have tried to install multiple times each with this result, I have used 2 separate downloads and CDs, to eliminate the possibility of a bad CD.

When I go into recovery mode and try to adduser it tells me there is Perl warning that my LC_ALL = (unset) then it continues and asks me to set a password and says that there is a Authentication token manipulation error. I have tried this with both and install of shadowed passwords and an install of no shadowed passwords, with a root account and with no root account.

Also on in recovery mode i noticed there was no folders in /home

I would be grateful if anyone could help me,
thanks.

---

### Post by khelben1979 on 2009-07-17
[In this thread]("http://ubuntuforums.org/showthread.php?t=405934") they try to make things easier for those who tries to install Ubuntu on the hardware which you're on.

Maybe you'll find something useful which can help you out in your present problem?

I suspect that you may haveto do a reinstallation.. Let's see if anyone else have something.

---

### Post by electromagn3to on 2009-07-17
Thanks I was using that my main sourse of instuctions the promblem i'm having is between.

> cli-powerpc

Now this install uses a debian type of graphic install and will walk you through the rest of the install with various choices given to you, my only suggestion here would be to read the options and select them from there.

After this has been completed the Mac should ask you to reboot and eject the CD. On reboot we will be left with a Command Line. Now the task is to log in using the name and password you used for the install, at this point you should be at the prompt.


Thanks

---

### Post by electromagn3to on 2009-07-17
Update: After making sure the clock was right (after resting the pram it was set to 1904) I can now add a users, I'm doing another install with this correct clock and crossing my fingers.

---

### Post by electromagn3to on 2009-07-17
After the install and some tinkering with the sudos file I now a working sudo-able user
:) horray

---

