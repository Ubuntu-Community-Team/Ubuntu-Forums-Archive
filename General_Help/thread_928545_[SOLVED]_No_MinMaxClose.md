---
title: "[SOLVED] No Min/Max/Close?"
date: 2008-09-24
forum: General Help
---

### Post by BGrigg on 2008-09-24
Just over a week using Ubuntu 8.04 and loving it, except all my apps have lost their minimize, maximize and close buttons! Can't double click to maximize or minimize, and can't move by using the mouse alone. Options are available in right-click context menu, 

I'm running the proprietary nVidea driver with Compiz Fusion running so I can do that cube thing. Was working fine until I loaded Google Earth last night.

Is there a rollback feature like in Windows?

Just a dumb (ex) Windows User. So be kind.

---

### Post by ad_267 on 2008-09-24
Try pressing Alt-F2 and run "metacity --replace" to get the default window manager without desktop effects or "compiz --replace" to get all the effects.

I don't think google earth plays well with compiz.

---

### Post by vishzilla on 2008-09-24
Is the title bar present?

---

### Post by kirankumarjupalli on 2008-09-24
hi my name is kiran. i m using tcl/tk for the first time.
actually i m using automation tools like tcl/tk and expect. can anyone help me how to write a throughtput script using different channels in tcl/tk using shell script.

---

### Post by BGrigg on 2008-09-24
> **vishzilla said:**
> Is the title bar present?

No, it's not

> **ad_267 said:**
> Try pressing Alt-F2 and run "metacity --replace" to get the default window manager without desktop effects or "compiz --replace" to get all the effects.

I don't think google earth plays well with compiz.


Alt-F2 did nothing. So I opened Terminal and typed in the metacity instruction. Title bar is back, and now Alt-F2 works as well!

I don't think Google Earth and Compiz plays well either! Me thinks eye candy isn't worth the trouble!

Thanks to you both. Are 1 minute response times normal? :lolflag:

---

### Post by Idefix82 on 2008-09-24
Yep. At least for standard questions. This is not commercial support, this is much better :)

---

### Post by ad_267 on 2008-09-24
Just a caution, if you close that terminal window you will probably lose your window borders again. If you type "metacity --replace" into a terminal you want to put an & after it, i.e. "metacity --replace &" so that the process runs in the background. At least that happens if you run "compiz --replace" from a terminal, I'm not sure about metacity.

I've disabled compiz but I've enabled compositing in metacity so I get shadows and gnome-do looks nice. You can do that if you want by running "gconf-editor" and going to Apps - Metacity - General and ticking "compositing_manager".

---

### Post by BGrigg on 2008-09-24
> **Idefix82 said:**
> Yep. At least for standard questions. This is not commercial support, this is much better :)

It sure is! 

Just for the record, I switched back to Compiz and lost the title bar. Replacing it with Metacity brought them back.

Compiz was working fine (to my eye, at least) until Google Earth was installed. The problem didn't show up until the system was restarted.

---

### Post by BGrigg on 2008-09-24
> **ad_267 said:**
> Just a caution, if you close that terminal window you will probably lose your window borders again. If you type "metacity --replace" into a terminal you want to put an & after it, i.e. "metacity --replace &" so that the process runs in the background. At least that happens if you run "compiz --replace" from a terminal, I'm not sure about metacity.

I've discovered that with other programs, but it seemed to "stick" with Metacity. I shall file that information for future reference.

> **ad_267 said:**
> I've disabled compiz but I've enabled compositing in metacity so I get shadows and gnome-do looks nice. You can do that if you want by running "gconf-editor" and going to Apps - Metacity - General and ticking "compositing_manager".

That restored some prettiness, but I'm thinking I really should go and get a manual for Linux to start learning all *nix stuff. Can't be much harder than the DOS commands I've mostly forgotten. Any suggestions on which book gives the biggest bang?

---

### Post by Idefix82 on 2008-09-24
I think you are best of with online tutorials and with asking questions here. The learning curve is very steep this way. When people tell you "type this, type that" then after you have done it ask them what you have actually done. Most people are very helpful when they see that the person asking the question actually wants to learn.

---

### Post by BGrigg on 2008-09-24
Thanks. I will go and check out the tuturials and tips threads further. I did try Googling and using the forum search with no luck before posting this thread, as I try not to look dumb (but often can't help myself). Learning new stuff is why I installed Ubuntu. I was looking for an easier transition to Linux than recompiling my own kernal!

I had heard so much bad press about "RTFM" on Linux forums (fora?) that I was hesitant, but I've noticed a distinct lack of that attitude here. It's very refreshing!

---

### Post by ad_267 on 2008-09-24
Yeah I haven't seen much "rtfm" on Ubuntu forums, everyone is pretty helpful here. I've only been using Ubuntu/Linux for about a year and the way I've learnt all of the stuff I know so far is by searching with google, reading these forums and trying things out as well as posting for help if I need it and helping others. Just hang around the forums and read the threads that look interesting and you'll learn a lot!

Reading man pages in the terminal "man command_name" is pretty useful if you want to learn the command line and if someone gives a command to enter in the forums you can see what it does that way. There are probably heaps of good guides out there, this one is pretty good: [http://linuxcommand.org/](http://linuxcommand.org/). Sometimes a command doesn't have a man page and you can enter "command_name --help" to get more information about the command.

You don't really need to know the command line at all just to get things done but it can be very powerful and fast.

And I'll second the fact that people are a lot more willing to help when someone is willing to learn.

---

### Post by BGrigg on 2008-09-24
Sorry for not getting back sooner. Work, you know!

Thanks to all for their help and suggestions. I know I've got a lot to learn about Linux, and I'm confident that with the people on these fora, I'll be up and running in no time!

Cheers,

Bill

---

