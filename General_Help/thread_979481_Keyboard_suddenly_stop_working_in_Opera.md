---
title: "Keyboard suddenly stop working in Opera"
date: 2008-11-12
forum: General Help
---

### Post by gabylastar on 2008-11-12
Hello,

I'm using Ubuntu 8.04 and today I noticed a new and very unpleasant problem with Opera 9.62.

As I surf in Opera, the keyboard randomly stop to respond, I can't type anything, the first solution I discovered was to close and restart Opera. I wouldn't mind if I haven't to do that every 30 seconds !

So far I discovered a temporary but still unpleasant solution :
- I start opera using the terminal
- When the keyboard stop responding, I switch to the terminal, click one time on it, then switch back to Opera : the keyboard is back.

I tried to find when the keyboard stop to respond and I have a good example :
- Go to the User Control Panel of the Ubuntu forum
- Click on Edit details on the menu
- You can now check that your keyboard is working if you want. It should.
- Choose a month for your birth date. Keyboard dead. Idem for choosing a day.

Have any of you already get this problem ? That's weird and only happening with Opera so far... And does somebody know how to fix this ? Any advice to find what's wrong ? Maybe there's a magical command line.

Thanks for any help !

---

### Post by ellgor on 2008-11-12
Hi,

I too get this happening, I've found that clicking on the refresh button MOSTLY works, otherwise it's as you say, restart Opera, keeping a lookout for a fix.

Regards, Ellgor.

---

### Post by gabylastar on 2008-11-13
So there isn't a known solution for that ? It really comes from nowhere ?
Thanks for the the Refresh button trick, but that can't be used so much because when you find that the keyboard freeze, you're in the middle of that looooong form and you don't want to fill in all again :)

---

### Post by Lomas on 2008-11-23
I got the same problem too...I cant type anything on Opera... the keyboard just stopped working by itself, it is so annoying.

:(

---

### Post by epictetus on 2009-01-25
Hey,  I've had the same problem in Opera and in Qt Creator.  My initial `fix' was to move to a different workspace, click on the desktop there, and move back.  Rather lame, yes.

At some point, I found something that seems to work with Opera somewhere in these forums (I think).  I've tried to find it again so I could give proper credit, but without any luck.  If someone finds the post, please post a link to it.  Anyway, it was as follows:

Go to Tools > Preferences
Open the Advanced tab
In the selection list on the left, choose Shortcuts
There will now be two lists:  Mouse Setup and Keyboard Setup
In Keyboard Setup, select ``Opera 9.x Compatible''

Like I said, that fixed the problem in Opera.  However, it might not be confined to Opera if you are using scim.  If you use scim, I recommend checking this workaround:  [http://bugs.launchpad.net/debian/+source/scim/+bug/66104]("http://bugs.launchpad.net/debian/+source/scim/+bug/66104")

---

### Post by gabylastar on 2009-01-26
Thank you for this solution ;)

---

### Post by argraff on 2009-01-27
> **epictetus said:**
> Go to Tools > Preferences
Open the Advanced tab
In the selection list on the left, choose Shortcuts
There will now be two lists:  Mouse Setup and Keyboard Setup
In Keyboard Setup, select ``Opera 9.x Compatible''


That did it for me! Thanks for helping me get my Opera back!!!

---

