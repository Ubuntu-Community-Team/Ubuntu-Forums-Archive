---
title: "I've installed something but how do I find it?"
date: 2008-07-17
forum: General Help
---

### Post by the lemming on 2008-07-17
I have just installed Aircrack -ng from the Synaptic Package manager.  The only problem I have now is finding it on my computer and learning how to run it.

Could somebody please suggest where it might be stored on my computer?

Cheers

---

### Post by stitchmysmile93 on 2008-07-17
most of the time when you install something in ubuntu it's executing command is in /usr/bin

so you can see if it's in there 

ls -l /usr/bin 

That's the first place I check 

If I can't find it there I search for it again in synaptic right click on it go to properties and installed files tab...

---

### Post by igorc on 2008-07-17
# sudo which aircrack-ng
# sudo dpkg -s aircrack-ng
# sudo dpkg -S aircrack-ng

---

### Post by bryncoles on 2008-07-17
it might be one of those annoying programs that doesnt create a launcher. have you tried typing 'aircrack-ng' in a terminal? if that opens then create a launcher for it (i would suggest in the 'internet' menu). 

do this by going to system, preferences, main menu and selecting add item, form there its easy!

---

### Post by stitchmysmile93 on 2008-07-17
igorc nice I like that.. LOL

---

### Post by the lemming on 2008-07-17
Think I've been going about this the wrong way

At first I was typing aircrack -ng and getting an error message.  Then I tried tyoing it all without pressing the space key and hey presto something happened.

I take it that Aircrack-ng is a tool that can only be used in the terminal?

All I have to do is now learn how to use it, and that is where my head is starting to hurt.

---

### Post by Vishal Agarwal on 2008-07-17
use 
> whereis <package name>

It will show u all the location for related package.

---

### Post by igorc on 2008-07-17
Something wrong with the commands i posted? They show where the package has been install and the docs and example files and folders. You have to google the rest there are lot of howto's on the network and this forum. For example:
[http://ubuntuforums.org/showthread.php?t=528276](http://ubuntuforums.org/showthread.php?t=528276)

---

### Post by stitchmysmile93 on 2008-07-17
man aircrack-ng

---

### Post by jonian_g on 2008-07-17
You're right it'a a console application.
It is used to hack wireless networks with WEP protection. Info on how to do that here:

[http://ubuntuforums.org/showthread.php?t=528276](http://ubuntuforums.org/showthread.php?t=528276)

---

### Post by the lemming on 2008-07-17
[QUOTE=igorc;5403179]Something wrong with the commands i posted? 

Hello

There was nothing wrong what so ever.  In fact I've just had a play and got loads and loads of information pop up on the screen.

Thanks for the help

---

