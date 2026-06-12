---
title: "Need just a tad of modprobe help"
date: 2005-05-16
forum: Hardware &amp; Laptops
---

### Post by Calimus on 2005-05-16
Alright.  I'm running 5.04 on a Dell Inspiron 9100.  I was able to activate my wireless card using ndiswrapper + modprobe and where is where I come off like a moron.

How do I get the system to hang onto the wireless card?  I can't find proper info that tells me what file and string to use so that I don't have to type "modprobe ndiswrapper" every time I want to use my wireless connection.

Someone told me to add the line 'alias modprobe ndiswrapper' to modprobe.conf in /etc.  Problem was the file didn't exist, so I created it, added the line and on reboot it didn't load the card.  I don't know what log files I can check to see what went wrong so any help would be appreciated it.  I've been away from linux for a little over 6 years and don't rememebr much of anythign I knew then.  I know I'm an idiot, but I'm trying to learn. :razz:

---

### Post by dave9191 on 2005-05-16
You'll want to add ndiswrapper to 

/etc/modules

That contains the modules that are loaded at boot :)

Dave

---

### Post by Calimus on 2005-05-17
So will I just want to add the line ndiswrapper or will I need to add modprobe ndiswrapper?

I'll give both a shot and see what happens.

*edit*
Looks like just adding ndiswrapper works, get some funky errors on boot, but it's there.  Have to test better when I'm within range of a wap.

---

### Post by dave9191 on 2005-05-17
Just ndiswrapper. The rest of the things in that file are a list of modules that are being loaded into the kernel.

---

### Post by svanac on 2005-05-17
ndiswrapper -m

That set ndiswrapper to /etc/modprobe.d/

I have a question, why gnome-session starts so long when I set ndiswrapper -m (modprobe)?
At time when I log on to then when xsession load need 5min.??

---

### Post by mr_ed on 2005-05-20
[QUOTE=svanac]
That set ndiswrapper to /etc/modprobe.d/
[/QUOTE]

Sorry, but could you explain what you mean by that?  Thanks.

---

