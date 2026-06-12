---
title: "[SOLVED] 8.10: Help! Keyboard/Mouse stopped working!"
date: 2008-10-10
forum: General Help
---

### Post by chazdraves on 2008-10-10
Greetings, all! Been a while since I've been stuck this bad...

I was using my computer this morning and everything was peachy. I had to do a partial upgrade to install the latest updates, and that doesn't seem to work well with the Beta (at least on my computer). Every time it would freeze at some point but usually at the end where it says "ldconfig deffered processing now taking place"...

Anyways, I mostly used the console this morning because of the problems I was having with Update Manager, but I wanted to mention it in case it's related.

Well, I got home from work tonight and found Ubuntu won't let me in. The mouse and keyboard are dead-in-the-water with the GUI. Ctrl+Alt+Delete still works, as does Alt+F1-12. I tried manually doing dist-upgrade, upgrade, autoclean, and autoremove to see if something was gunked up. I tried booting from a previous image which didn't work. Lastly, I dug into xorg.conf only to find that it's basically empty. All it specifies is a monitor, but there aren't even any parameters for the monitor.

Anyhow, I see xorg says that many of the functions are now automatically calibrated, so I don't know if it's a problem with that or not. Can anyone help?

Thanks, guys! This is a fairly amazing community.
- Chaz

---

### Post by chazdraves on 2008-10-11
Yikes! Nobody?

I guess I'll know next time not to install a beta on my primary PC.

- Chaz

---

### Post by weatherkid on 2008-10-11
Did you try recovering your system with the Install CD-ROM? Maybe if you recover it that will work.

---

### Post by mick222 on 2008-10-11
this happened to me after the update on wednesday try starting in recovery mode and running dpkg -d that seemed to fix mine . Every boot i had to do this ,the updates today have sorted it i think.

---

### Post by chazdraves on 2008-10-11
Thanks for the prompt replies, guys!I haven't tried recovering from a CD for two reasons. 1) I don't have a CD yet as I updated from 8.04 and 2) I really don't think I should have to. This seems like such a stupid thing, there's gotta be a quick fix for it. That said... what broke it in the first place? Everything was working fine when I shut my computer off...

Anyhow. I tried running in recovery mode and did everything: xfix, fsck, dpkg, etc. I ran every option, but dpkg says it will update 5 packages and then when it attempts to, it fails on all five. I tried running dpkg in the root terminal, but I didn't know what to type, and dpkg -d alone doesn't do it...

This is really irritating. I can see the login screen, but I can't login. Why does X recognize Ctrl+Alt+Delete and Alt+F1-12 but not the keys I need to type with.

I also found something at the official site for Alpha 6 which recommended running sudo dpkg-reconfigure console-setup to fix keyboard issues, but that did nothing.

Thanks for trying, guys. I hope this is fixable. I don't want to lose everything.

- Chaz

---

### Post by jonger on 2008-10-11
at the login in screen:


[INDENT][/INDENT]ctrl+alt+F2

login then type

```
sudo apt-get install xserver-xorg-input-all
```

then restart

ctrl+alt+del

---

### Post by caleb12 on 2008-10-11
So, when you do the alt+f1 and get to the terminal, does the keyboard work there? Just wondering... if that's the case it almost certainly sounds like an issue with evdev. 

You were right when you said that most of the Xserver is auto-configured now, even more so in 8.10 - since they are using Xserver 1.5 and Xorg 7.4... Almost all configuration, especially for input devices takes place with evdev now. 

Here are some links for evdev configuration, it sounds like you can handle it... 

[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Mouse+Buttons&back=HOWTO+INDEX+Hardware](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Mouse+Buttons&back=HOWTO+INDEX+Hardware)

[http://who-t.blogspot.com/2008_07_01_archive.html](http://who-t.blogspot.com/2008_07_01_archive.html)

It's just a matter of editing Xorg to coincide with what HAL is telling EVDEV to do. That's why xorg is left almost blank, because if you specify anything in there chances are you will end up with a conflict between evdev and xorg.conf - both trying to configure the same device. There are also methods of turning off the evdev auto discover and implementing the xorg, this is in case evdev can't identify hardware properly. Which kind of sounds like your situation...

---

### Post by chazdraves on 2008-10-11
Thank you very kindly, everyone!

This: sudo apt-get install xserver-xorg-input-all
did it!

Now, can anyone tell me what that actually does? I see it installed three new packages. Are they going to cause conflicts down the road?

I appreciate the idea above this as well, but I was hesitant to try it because I want to show people how user-friendly Ubuntu is, and if I had to explain how I had to go through all of that just to get my keyboard and mouse working, people may not get the right message.

A great many thanks again!
- Chaz

P.S. Yes, the keyboard works if I hit Alt+F1-12. All the buttons function. It was only in X/Gnome that I had the problem.

---

### Post by sbinkerd1 on 2008-11-02
i get xserver-org-input-all is already at the newest version.
0 upgraded 0 newly installed, 0 to remove, 0 not upgraded

any other ideas?

---

### Post by fattymatty on 2008-11-04
I've got the same problem and done the same work arounds to no avail did you get yours to work and if so how

---

### Post by vyromero on 2008-11-07
I have the same problem and have tries all these solutions.
The only thing that seems to work for me is on each boot I need to unplug the keyboard/mouse wireless USB adapter and plug it back in, then re-connect both the keyboard and the mouse. I'm using Logitech MX 5500.
Any ideas on how to get this solved permanently?
Thanks in advance!

---

### Post by gasilva on 2008-11-08
I already have the newest ```
sudo apt-get install xserver-xorg-input-all
```

But in every single boot I do not have mouse and keyboard and need to press Alt+F2 to get text screen.

To activate them I have in every boot to reconfigure Xorg with ```
sudo dpkg-reconfigure xserver-xorg
```

Is there any permanent solution?

---

### Post by stanna on 2008-11-24
i am also looking for a solution to 8.20 and logitech mx5500 if anyone can help. as it is i cant use it. pain in the **** to unplug the dongle and plug it back in each boot.

---

