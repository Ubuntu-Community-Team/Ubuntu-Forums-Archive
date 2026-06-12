---
title: "Linux dcpp crashes (something with memory)"
date: 2005-12-01
forum: General Help
---

### Post by Kataxu on 2005-12-01
Hi!
I have installed last version of it and it works perfect excepting one thing.

Dc++ crashes after some hours/minutes of working and in terminal I have message, that there has been interruption of memory protection... or something... I don't remember this message but it just crashes.

If anybody could help, I'd be grateful.

---

### Post by runlevel0 on 2005-12-01
I can't understand what Dc++ means.

What exactly are you doing? What is Dccp? 
Are you talking about c++  or cpp (the compilers)?

What does crash and why? 

Are you compiling something or is this error returned by the libstdc++ ?

Please give us more info. If you could write the error down and post it here we will surely be able to help you. Else we don't even know what you were intending to do.

Feed our minds, please ;)

---

### Post by Kataxu on 2005-12-01
DC++ Is a program used for downloading from hubs (in my opinion this is the best program ever... ) :].
names: dcpp/dc++/direct connect/...
And I installed linux version of it.
There is also dcgui and valknut but I don't like both.

---

### Post by runlevel0 on 2005-12-01
Aaaw!

I thought it was C++, the compiler!

Can you pleas post the error message, I think it's a segmentation fault. So we could at least tell you if error is something you can fix or it needs to file a bug report.

I have just tryed dcgui and it gives no error, I haven't used it much more than the time of starting it and clicking rendomly around to see if it crashes... I don't know if DC++ has a better interface but the GTK one is pretty complex. Cool program.

I'm going to download the last DC++ in part for telling you if I got problems (and was able to solve them) and in part because the app seems really kick ass.

---

### Post by ewoox on 2006-10-31
linux dcpp uses a lot of memory while downloading/uploading... i don't know if this a bug, but i can't whatch a movie while dcpp is running :(

---

### Post by stevensheehy on 2006-11-01
> **Kataxu said:**
> Hi!
I have installed last version of it and it works perfect excepting one thing.

Dc++ crashes after some hours/minutes of working and in terminal I have message, that there has been interruption of memory protection... or something... I don't remember this message but it just crashes.

If anybody could help, I'd be grateful.

"Last version" doesn't really tell me anything. Check the Changelog.txt to see the last date mentioned. I hope you didn't install from a package, as it's no doubt quite old since I update ldcpp often. I recommend installing from cvs by following my  [guide]("http://www.ubuntuforums.org/showthread.php?t=193984") if you haven't already. By the way, I just updated today so even if you did compile from cvs, you might want to update.

There's known issues with the download queue, so don't keep it open while you download. Otherwise, compile in debug mode and get a backtrace as mentioned in our [manual]("http://openfacts.berlios.de/index-en.phtml?title=Ldcpp_Manual").

---

