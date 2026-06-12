---
title: "Ubuntu 9.10 login beofre install?"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by harsh2209 on 2009-10-30
Hi Friends,

It’s driving me nuts here...maybe I'm not familiar whether or not it is expected.

I'm trying to clean install ubuntu 9.10 on a desktop which already has OpenSolaris on it. When I out the CD and reboot the computer, the PC boots up from the DVD drive and I get the ubuntu menu. I tried both 'try ubuntu without affecting...hard drive' and 'install ubuntu'. Both times, I encounter a Login screen that asks for Login and Password.....What the heck is that....This is just a live install....Any clues....?

---

### Post by mac9416 on 2009-10-30
I've seen this rather strange behavior before. You can login to a live disc using username "ubuntu" and a blank password.

---

### Post by harsh2209 on 2009-10-30
Damm!....this is nasty....I can't install it without an unknown username and password...that too, nobody at ubuntu has added it into the documentation too...That is very unexpected behavior from ubuntu folks....

I tried all combinations...
Ubuntu and blank pass
root abd balnk pass
previous Os's credentials..

But, no sucess...I have no way to install ubuntu 9.10...bad..

---

### Post by trulytrojan on 2009-11-15
Anyone figured out this username/password yet?

I am trying to install ubuntu 9.10 64bit vmware server 2.0.1 on my window 7.
It even asks for login on live cd...not sure what to do.

Thought of using "passwd" command to reset the password by going on the command prompt (ctrl-alt-f1 i think) but did not get any prompt there. all saw was "authentication failure" messages perhaps becaused I tried logging in several times on GUI prompt.

I also saw other messages "getting the time for networks server..".

Please let me know if someone has been able to go past this login.

Thanks,
TT

---

### Post by mac9416 on 2009-11-15
Hey, y'all,

I think I found the answer. It seems this problem results from a corrupted disc or bad CD drive. Try redownloading and reburning the live CD or creating a USB live install with [Unetbootin]("http://unetbootin.sourceforge.net/"). 

Let me know if it works. Good luck!

---

