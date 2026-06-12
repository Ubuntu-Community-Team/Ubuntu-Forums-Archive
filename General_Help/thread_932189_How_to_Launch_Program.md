---
title: "How to Launch Program"
date: 2008-09-28
forum: General Help
---

### Post by SBFree on 2008-09-28
I ran an install script to install a program. This is really embarrassing, how do I start and top the program it installed? The readme file isn't helpful. It is a text based front end that 'speaks' it's output for use by the blind called, LinuxSpeaks. There is a Uninstall script that removes a few directories, one of which is named 'Linuxspeaks'. Does that sound like the place to look? What should I look for to execute the program? Thanks.
Scott

---

### Post by Naiki Muliaina on 2008-09-28
Is the program actually called LinuxSpeaks? The thing for blind people learning linux or something like that. 

If yes was it the tarball installer for 1.10?

---

### Post by mrog on 2008-09-28
Hi Scott:

Typing MainMenu should start the application.

I just tried installing and it appears that it didn't work the first time. It just named the packages it was trying to install but didn't actually do anything. I ran ./install.sh againcould see apt-get producing it's normal output in the terminal as the installer goes through the package names.

---

### Post by Naiki Muliaina on 2008-09-28
Agreeing with what he said, didnt work untill after a 2nd reboot for me oddly. But MainMenu works.

---

### Post by SBFree on 2008-09-28
Yes, it was the 1.10 tarball. Where did you type 'mainmenu'? Was it in a terminal window? Thanks.
Scott

---

### Post by SBFree on 2008-09-28
Where do I enter the 'MainMenu' text? Is it in the terminal window? Thanks

---

### Post by Naiki Muliaina on 2008-09-28
Sorry for late reply, yes. Open terminal and type ```
MainMenu
```

Works fine :)

---

### Post by SBFree on 2008-09-29
Thanks for getting this running for me. Can I ask where I should have looked to learn this on my own? How did you figure this out? Thanks again.
Scott

---

