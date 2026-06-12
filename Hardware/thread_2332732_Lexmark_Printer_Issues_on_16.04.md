---
title: "Lexmark Printer Issues on 16.04"
date: 2016-08-03
forum: Hardware
---

### Post by b1gdan0 on 2016-08-03
New to Ubuntu, starting to fall out of love with it.  I have a Lexmark X5650 and it's basically a "paperweight".  The sad truth is that it wasn't a "paperweight" until I installed Ubuntu.  I spent the entire day yesterday trying to get my printer to work.  I understand the fact that my 64 bit system is an issue for Ubuntu when it comes to printing.  What bugs me is that these older Lexmark printers worked fine in older distributions of Ubuntu.  I would hope that the Ubuntu universe wouldn't change the OS so drastically that it suddenly broke people's working printers with an upgrade.

Can anyone help?  I've installed so many packages based on so many threads in this forum that I don't know what I did.  When I try to run the Lexmark driver installer, I make it to the point that it errors on opening xterm-256color or something.

System Details:

[ATTACH=CONFIG]270550[/ATTACH][ATTACH=CONFIG]270551[/ATTACH]

---

### Post by b1gdan0 on 2016-08-04
Wow.  Not one reply but an edit because of very light language?  double you tee eff

---

### Post by Enigma12 on 2016-08-05
First, I am NOT a seriously competent Linux user, so what I say here may not be of help. Second, I also have read here that Lexmark printers can be problematical in Linux. I have a Lexmark laser that gave me occasional garbage and relegated it to my #2 computer, where it does well enough for the rare times that I use it with that computer. 

As for 16.04, I just a couple of days ago loaded Lubuntu 16.04.1 onto that #2 computer and was not initially able to get the printer installed. Did some Googling and found out that CUPS was left out of Lubuntu 16.04. After I installed CUPS and rebooted, installing the Lexmark went smoothly, and the printer did the few pages that I printed with it just fine. 

So, if CUPS is also missing from Ubuntu, you might try to either install CUPS via Synaptic or via Terminal with "sudo apt install cups" to see if that helps. If that doesn't work, at least I have bumped your post up where it may be seen by someone more knowledgeable than me.

---

### Post by b1gdan0 on 2016-08-05
Thank you.  I read, forgot about, and now that you mention it, recall something about CUPS.  I will give it a shot and let you know.

---

### Post by b1gdan0 on 2016-08-05
Same error:

[ATTACH=CONFIG]270596[/ATTACH]

---

