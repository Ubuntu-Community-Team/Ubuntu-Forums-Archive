---
title: "Wacom Bamboo Pen not working in 9.04"
date: 2009-12-11
forum: Hardware
---

### Post by billdotson on 2009-12-11
I tried the guide here: [URL="http://ubuntuforums.org/showthread.php?t=1038949&page=11"]http://ubuntuforums.org/showthread.php?t=1038949&page=11
[/URL] 

That did not work.

There is some script that is supposed to be run that changes the names of something here:[http://ubuntuforums.org/showpost.php?p=7220343&postcount=247]("http://ubuntuforums.org/showpost.php?p=7220343&postcount=247")

I have not tried it because during the small amount of time I looked it never *specified what type of script it was.* I am assuming bash but the only time I have ever seen includes like that is in C. Therefore, I did not know what to save it as.

I thought that most Wacom tablets were supposed to work out of the box in Jaunty? What is the deal? I'll refrain from *****ing now.

Hardware: Dell D600 and Wacom Bamboo Pen.

Can't upgrade to Ubuntu 9.10. Every time I have tried 9.10 freezes and is unusable.

---

### Post by Favux on 2009-12-12
Hi billdotson,

The HOW TO you were looking at, gali98's, is for usb tablet pc's with touch.  That's why it didn't work for you.

The Bamboo Pen, one of the 5 new Bamboo P & T's, is so new that the linuxwacom drivers do not support it.  However we have developed patches to the linuxwacom driver that should get your Bamboo Pen completely working in Jaunty.  See [post #2]("http://ubuntuforums.org/showpost.php?p=8099002&postcount=2") on the thread for the links.

---

### Post by billdotson on 2009-12-12
Thanks. I assumed that the tablet PC how-to had something to do with it. 

I didn't think the Wacom Bamboo pen was that new, I had just read something recently where someone said it worked out of the box on Jaunty. Guess not. I will check out those threads.

---

### Post by billdotson on 2009-12-13
I tried this link: [http://ubuntuforums.org/showpost.php?p=8129913&postcount=144]("http://ubuntuforums.org/showpost.php?p=8129913&postcount=144")

and 

[http://paste.ubuntu.com/340334/]("http://paste.ubuntu.com/340334/")

Yeah, I have no clue how to proceed.

Edit: [http://ubuntuforums.org/showpost.php?p=8262965&postcount=541]("http://ubuntuforums.org/showpost.php?p=8262965&postcount=541")

solved my problem. I think it was mainly due to dependencies. Thanks for your work on this guys!

---

### Post by Favux on 2009-12-13
Hi billdotson,

You could try kgingeri's version:  [http://ubuntuforums.org/showpost.php?p=8262965&postcount=541](http://ubuntuforums.org/showpost.php?p=8262965&postcount=541)  As you already have noticed the linuxwacom version is now 0.8.4-4.  Be sure to change 0.8.4-3 to 0.8.4-4 where you encounter it.

Oops, never mind.  Good job!

---

