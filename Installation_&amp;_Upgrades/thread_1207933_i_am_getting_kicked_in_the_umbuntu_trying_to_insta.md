---
title: "i am getting kicked in the umbuntu trying to install"
date: 2009-07-08
forum: Installation &amp; Upgrades
---

### Post by silycyber on 2009-07-08
Hi all,

I have been plugging away at trying to install Ubuntu on my computer for 3 daysz now. I ordered a a cd, i also downloaded and made an .ISO and have even tried Xbuntu. For one i get no splash screen when it loads instead i get this white squares blinking i can get as far as to where it will say ubuntu@ubuntu:~1
for Xbuntu i get no splash screen again and i get to a login and password in the scripting and nothing. please bare in mind I am completly new to this software and would love some help.

Thnaks

Silycyber

---

### Post by merlinus on 2009-07-08
A few suggestions:

check the cd for errors at the opening menu.

do a checksum for your downloaded .iso --

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

and burn at no more than 4x speed.

try safe graphics mode -- press F4 at the opening menu for this option.

---

### Post by silycyber on 2009-07-08
I have done this in the safe graphics mode and I still can not get this software to work even in the demo version. 

here is excatly what happens
it has a boot_ (blinking) I hit Enter
from there i chose install either way no ubuntu
then white boxes randomly blinking on screen
then an underscore blinking
then stuff starts checking out 
everything is saying [ok]
from there I 4 blue bars on the  right and 4 on the left 
with information below loading/casper/vmlinuz...
I then hit enter and I am at the ubuntu@ubuntu:~$

---

### Post by merlinus on 2009-07-08
What about my other suggestions?

---

### Post by silycyber on 2009-07-08
All three are correct the Xubuntu.iso and the Ubuntu.iso and the cd that I recieved from Ubuntu

---

### Post by silycyber on 2009-07-08
if I select ubuntu to load instead of XP Pro I get Ubuntu 9.04 ubuntu tty1 then underneath I have ubuntu login:  i then enter my username and password and hit enter past the no warrenty and to access official ubuntu documentation, then I get my username@ubuntu:~1
thanks
silycyber

---

### Post by merlinus on 2009-07-08
Did you check the cds for errors at the opening menu?  Can you try running them on another computer, as this will ensure your cd drive is ok.

---

### Post by silycyber on 2009-07-08
I installed ubuntu on another computer this past weekend. so I know the cd's are ok.

---

### Post by merlinus on 2009-07-08
That leaves your cd drive as the probable culprit.  If your computer can boot from a usb flash drive, you might try that route.

---

### Post by earthpigg on 2009-07-08
> **merlinus said:**
> That leaves your cd drive as the probable culprit.  If your computer can boot from a usb flash drive, you might try that route.

+1. 

cd drives are funky. most things are either 'broken' or 'not broken'. not so with cd drives, based on my experience.

i have experienced a cd drive that works fine for anything *but* trying to boot from..... i used to be able to boot from that same cd drive without issue, but now its 'semi broken' and i cannot. what goes wrong varies in exact details, except that it only happens if bootable media is in the cd drive.

system -> administration -> usb startup disk creator

best of luck

---

### Post by Kunin on 2009-07-08
> **silycyber said:**
> if I select ubuntu to load instead of XP Pro I get Ubuntu 9.04 ubuntu tty1 then underneath I have ubuntu login:  i then enter my username and password and hit enter past the no warrenty and to access official ubuntu documentation, then I get my username@ubuntu:~1
thanks
silycyber

Sounds like an xorg issue to me, what you have is the CLI that you get if X fails to start properly (everytime my installs have had problems screen would blink a few times before it let me type in my login).

What hardare are you using in this box?  How many graphics cards?

What does your /etc/X11/xorg.conf look like?  What about /var/log/Xorg.0.log?

For those files you can put them in pastebin and give us the url here.

$ sudo apt-get install pastebinit
Then
$ pastebinit /etc/X11/xorg.conf
$ pastebinit /var/log/Xorg.0.log

---

