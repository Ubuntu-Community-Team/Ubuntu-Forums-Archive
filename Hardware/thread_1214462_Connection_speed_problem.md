---
title: "Connection speed problem"
date: 2009-07-15
forum: Hardware
---

### Post by Kansasguy on 2009-07-15
Actually Linux Mint, which is based on Ubuntu Jaunty

Don't know even where to post this, could be hardware or software, please direct me to the proper place.  Thanks


I dual booted my laptop with XP and Linux Mint (basically Ubuntu Jauntu). WIRELESS SPEED in the house is now the problem.

Best example I can give is that Firefox works well (FAST) in both XP and Linux Mint when the computer is hooked directly to the router, and it also works fast in XP when wireless,   BUT,  Firefox works very slow on Linux Mint.

Have been to about:config   regarding  disabling IPv6,   but haven't (don't know how to) blacklist. 

Have been to these links, so I know the problem is out there
(Got these by Googling:    linux slow wireless)

[http://ubuntuforums.org/showthread.php?t=260733](http://ubuntuforums.org/showthread.php?t=260733)

[http://www.linuxforums.org/forum/debian-linux-help/24608-wireless-internet-so-slow-please-help.html](http://www.linuxforums.org/forum/debian-linux-help/24608-wireless-internet-so-slow-please-help.html)

[http://www.overclock.net/linux-unix/368589-solved-slow-wireless-speeds-ubuntu-but.html](http://www.overclock.net/linux-unix/368589-solved-slow-wireless-speeds-ubuntu-but.html)

[http://ubuntuforums.org/showthread.php?t=888696](http://ubuntuforums.org/showthread.php?t=888696)

[http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/wireless-slow-on-802.11b-normal-speeds-on-802.11g-and-windows-ubuntu-edgy-intel-522158/](http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/wireless-slow-on-802.11b-normal-speeds-on-802.11g-and-windows-ubuntu-edgy-intel-522158/)

Any help greatly appreciated,

---

### Post by Kansasguy on 2009-07-19
For those having trouble with WIRELESS SPEED, I have found at least a partial answer, especially when you have a dual boot system, and Windoze is fast, but Linux is slow.  The problem is likely due to drivers, or the wlan card itself.  Mine is a Ralink RT2500 based wireless card, but there are also sites that describe Broadcom drivers with same problem.  The fellow at the link below used it with Jaunty and Xubuntu, and it worked for me with Linux Mint on my Averatec laptop.

TRY THIS

1)  How to solve the problem temporarily, but quickly (you'll love it if it works.
This is the only part I have done so far because I have a lot going on right now.

Open a terminal, and enter the code:

sudo iwconfig wlan0 rate 11M

The next line will probably ask you for your password, and when you enter it it will not show, even dots, but go ahead and enter it.  Now check your speed by going to your browser and seeing how fast pages download.

The problem with this "fix" is that you must do it everytime you turn on the computer, therefore, fix number two, which I haven't done yet, but I will send the link to the page where it is described.  If you do do it, and it works well, let me know the problems you found, as I am a newby.


2)  How to change the system

the link is:
[http://ubuntuforums.org/showthread.php?p=7605785#post7605785](http://ubuntuforums.org/showthread.php?p=7605785#post7605785)


If this forum won't let me post link cuz I'm too new, Google the following, WITH QUOTES, and you should get the link.

"laptop with integrated Ralink RT2500 based wireless card"


Hope this helps, let me

---

### Post by BJ_Covert_Action on 2009-07-19
I actually have a question regarding your fix. Do you know which file iwconfig edits? I imagine it has to edit a configuration file somewhere and I am curious which one it edits. Does anyone know?

---

### Post by Kansasguy on 2009-07-23
I can't answer your question, too new at linux.  ht

---

