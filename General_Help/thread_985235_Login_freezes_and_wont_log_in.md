---
title: "Login freezes and wont log in"
date: 2008-11-17
forum: General Help
---

### Post by sdlyr8 on 2008-11-17
I don't remember changing any settings or anything major that would cause this, but I just restarted my computer and now when I try to log in, the login splash screen disappears and just stops at a solid blue screen (which is the set background color). I can log in using the failsafe GNOME session but none of the others work. Any idea what I did or where to even start looking?

---

### Post by icanfly0307 on 2008-11-17
> **sdlyr8 said:**
> I don't remember changing any settings or anything major that would cause this, but I just restarted my computer and now when I try to log in, the login splash screen disappears and just stops at a solid blue screen (which is the set background color). I can log in using the failsafe GNOME session but none of the others work. Any idea what I did or where to even start looking?

Try this at the login screen:

1. Hit Ctrl + Alt + F1 (The X Server should shut down...)
2. At the console prompt, enter your username and password.
3. As soon as the shell appears (username@hostname), type startx and hit enter.

This should bypass the GDM login screen and log you directly into GNOME. You can then poke around for the root of the problem. Give me a shout if you need any other help. :)

---

### Post by sdlyr8 on 2008-11-17
Thanks! That works. But I still don't even have any idea on where to start looking for the issue. Would there be any logs I could check or anything?

---

### Post by icanfly0307 on 2008-11-17
> **sdlyr8 said:**
> Thanks! That works. But I still don't even have any idea on where to start looking for the issue. Would there be any logs I could check or anything?

Try looking at the Login Manager Settings (System --> Administration --> Login Manager). Or, if you're really feeling up to it you could reinstall GDM.

Code:

sudo apt-get remove gdm.

After the removal process is complete, type:

sudo apt-get install gdm.

Reboot.

PS. I probably wont be back until 7:00 tonite. I check back and see if you need any more help. Until then, Good Luck!

---

### Post by sdlyr8 on 2008-11-17
Nope and nope! Tried opening the Login manager to find I don't have one in System > Admin. I have a Login Window option, which when I click on it, it says GDM is not running. So I tried reinstalling gdm which also did not fix anything. So I don't know. Now what? lol

---

### Post by icanfly0307 on 2008-11-17
> **sdlyr8 said:**
> Nope and nope! Tried opening the Login manager to find I don't have one in System > Admin. I have a Login Window option, which when I click on it, it says GDM is not running. So I tried reinstalling gdm which also did not fix anything. So I don't know. Now what? lol

Try this:

sudo apt-get install [FONT="Courier New"]sysv-rc-conf[/FONT]

After that, type: [FONT="Courier New"]sysv-rc-conf[/FONT]

This should show you a list of all the services on your computer. Hit your down arrow key until you come to "gdm". Post what runlevels the 'X's are at for gdm.

---

### Post by sdlyr8 on 2008-11-17
GDM services are at 2, 3, 4, and 5

---

### Post by icanfly0307 on 2008-11-17
> **sdlyr8 said:**
> GDM services are at 2, 3, 4, and 5

Hmmmmmm... That seems to be the way it's supposed to be. The only explanation that seems to fit is a problem with your user account. I know that you said that you didn't make any major changes. However, just to be sure, follow my steps in my first post (The Ctrl+Alt+F1 and all that...). After you're logged in, create a new account like "test" or something and try logging in again. Post what happens and I'll help you out. This will also help us pinpoint the situation more accurately.

Good Luck! :)

---

### Post by sdlyr8 on 2008-11-18
Okay... I created a new user, and it logs in just fine the usual way. So I'm guessing it's gotta be one of my personal settings causing it to stop. (On a side note, I did notice that it does stop before it plays the beginning login sound. maybe that will help us out?)

---

### Post by sdlyr8 on 2008-11-18
Oh wow.... I hang my head in much shame now... ](*,)

It would appear that I had a small script in my .profile that was causing it to stop. I commented that out and now it's working. Thanks a ton for your help and patience though!

I guess this goes down in the book as idiot mistake #3145...

---

### Post by icanfly0307 on 2008-11-18
> **sdlyr8 said:**
> Oh wow.... I hang my head in much shame now... ](*,)

It would appear that I had a small script in my .profile that was causing it to stop. I commented that out and now it's working. Thanks a ton for your help and patience though!

I guess this goes down in the book as idiot mistake #3145...

Glad to know you got it working! And it was my pleasure to help.:D

---

