---
title: "Is there a way to get rid of the Ubuntu log-in sound?"
date: 2008-09-20
forum: General Help
---

### Post by raiderleaf on 2008-09-20
When I log into Ubuntu, It always makes that drum sound and I want to get rid of it. Is there a way I can get rid of that and the noise it makes before the password prompt? Also, can i get rid of the ubuntu logo when the operating system is starting (and the bar is moving back and forth from left to right)?

Thanks,

Raiderleaf

---

### Post by Monotoko on 2008-09-20
Aye you can get rid of the sound

to get rid of the sound:
System -> Administration -> login window -> accessability
uncheck all the sound boxes

As for the ubuntu logo, this may o may not help:
[http://www.foogazi.com/2007/10/27/remove-the-ubuntu-splash-screen/](http://www.foogazi.com/2007/10/27/remove-the-ubuntu-splash-screen/)

---

### Post by raiderleaf on 2008-09-20
I have already tried that and it doesn't work... any other ideas? I'm working on the logo thing, i'll keep you posted.

---

### Post by Brain-free on 2008-09-20
Well, for the system sound, go to System -> Preferences -> Sound click on the "sounds" tag and in the "log in" section select "no sound". That's the case with Ubuntu Hardy at least...

---

### Post by Monotoko on 2008-09-20
Hmm, try:

system -> Preferences -> Sound

Then go to the Sounds tab, and at the bottom there should be "Log in" and "log out" try putting those to "no sound"

EDIT: beaten to it -.-

---

### Post by raiderleaf on 2008-09-20
That seems to have worked for the time being. Any other ideas with regard to removing that ubuntu banner at start up with the orange bar bouncing from right to left? I'm still working with the previous idea... 

Thanks,
raiderleaf

---

### Post by Crystal Red on 2008-09-20
I downloaded and installed the package called startupmanager.

That offers a frontend to grub (so you don't have to edit menu.lst by hand). 

There you can set options like the bootsplash.

---

### Post by raiderleaf on 2008-09-20
How do I find this startup manager? And besides, the first link makes it that if you remove that "Ubuntu" it shows you all the system processes up to that point. Is there a way I can just have the bar and not the "Ubuntu" above it?

---

### Post by Monotoko on 2008-09-20
to get startup manager

"sudo apt-get install startupmanager"

after install you will find it in:
System -> Administration

and i dont think there is a way to do that, unless you modify the coding, which i have no idea how to do :P

---

