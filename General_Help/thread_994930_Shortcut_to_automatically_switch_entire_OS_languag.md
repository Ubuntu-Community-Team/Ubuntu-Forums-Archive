---
title: "Shortcut to automatically switch entire OS language"
date: 2008-11-27
forum: General Help
---

### Post by hashbrowns on 2008-11-27
Hi everyone, I have a question regarding the ability of Ubuntu to switch languages on the fly, hopefully someone can give me some advice for what could be something totally simple to do.

I've already been impressed by Ubuntu's ability to almost perfectly switch between languages. I am an American computer-hardware repair teacher in Jordan, and I'd like to have Ubuntu running on all of our general-use lab machines, for our students to be able to write documents, check email - basic things like that.

All of our students are almost exclusively Arab speakers, but a lot of them know English computer-words from their time in Windows. I already have installed Arabic (Jordan) on the machine, as well as American English, and they know how to switch languages by logging out, changing the language on the login screen, and then log back in.

I want to make it easier for them though; **I'd like to create a shortcut/command on the account desktop that when executed, will switch the entire system's language from English to Arabic, or vice versa. Barring that, a command that will log out, switch the language automatically, and then log back in.** Of course, I realize that I might need to have two shortcuts (one to go from Arabic to English, and one from English to Arabic) but that's no big deal.

Is this convenience possible in some way? :) Your assistance is greatly appreciated; I've been a Windows instructor for half a decade but my experience with Ubuntu, and Linux in general, is very small.

---

### Post by Bucky Ball on 2008-11-27
System->Preferences->Keyboard->Layout Options->Layout Switching

... that might be what you are after.

---

### Post by hashbrowns on 2008-11-27
> **Bucky Ball said:**
> System->Preferences->Keyboard->Layout Options->Layout Switching

... that might be what you are after.

Thanks Bucky, but what I'm looking for is a way to switch the entire OS language, including all of the menus, from English to Arabic, in as few steps as possible for my students.

I already have it set so that pressing Ctrl and Shift at the same time will switch from typing in English to typing in Arabic, but that doesn't change the language of the rest of the system.

What I love about Ubuntu is that by logging in and out, the entire layout of the screen switches to be Semitic-language friendly :) all of the buttons and options switch from left, to the right side of the screen. What I'm looking for is the simplest possible way to get from English to Arabic, without the logout-change language-log back in again that they currently have to do.

---

### Post by Bucky Ball on 2008-11-27
I can't seem to find anyway of doing that 'on the fly'. You will find this of interest though, you are not alone ...

[http://brainstorm.ubuntu.com/idea/8440/](http://brainstorm.ubuntu.com/idea/8440/)

---

### Post by CatKiller on 2008-11-27
As a temporary workaround, having two accounts - one English, one Arabic - and using the Fast User Switcher to change between them might work. Synchronisation of the user profiles might be a pain though.

Your shortcut to log out and log back in would probably pass options to GDM or gdmflexiserver, but I have no idea how this works.

I know that it's possible to have more than one X or GDM session running at once, so it might be possible to automatically start two concurrent sessions, one English and one Arabic, and change between them with the virtual console method. Again, synchronisation with running applications might be a problem.

Sorry I couldn't give you a more concrete solution. If you manage it, post your solution here. As Bucky Ball says, you aren't the only person to want to do this kind of thing. You might be the solution to the Brainstorm that he posted.

---

