---
title: "noob root access problem"
date: 2008-09-11
forum: General Help
---

### Post by aaror on 2008-09-11
K, I just bought a Dell with Ubuntu and put a better power supply in, my mistake is easily correctable by re-installing the OS (yes, I am THAT much of a Noob), but I figure I could learn a lot from my mistake, maybe even enough not to repeat it.

I have two problems, one, I don't know how to run gedit in root mode to make a fix on internet, second, I seem to have locked up root mode.

I wanted to install Yahoo Messenger so I could talk with my wife while deployed in the persian gulf, and so I installed Wine.  It ran OK, but could not connect to the server.  Looking in the Wine FAQ I found the exact description of my problem, and tried to implement the fix.  I was told instructions to follow while in a text editor in root mode, and tried several things to get into root mode, including using the terminal to launch gedit in root.  I also tried to create a new admin account (didn't want to try to do this in root, I do know that much), and managed to create it without logging out of the session I was in, where my computer was automatically downloading updates.  Ended up freezing the computer and manually turning it off, now I can't perform any command that requires root access.  It lets me type in my password, but then gives me the error message:

Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '--parent-window-id' '52428803' '-o' 'Synaptic::closeZvt=true' '--progress-str' 'Please wait, this can take some time.' '--finish-str' 'Update is complete' '--set-selections-file' '/tmp/tmpDLJiYw' as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

So, how did I mess up my root access (so I don't do it again)?  How do I fix it?  And last but not least, how do I run my editor in root mode?  Thanks.

---

### Post by cmnorton on 2008-09-11
gksudo gedit.

You can also learn emacs, nano, vi (or another command line text editor) and edit from the X-term.

---

### Post by aaror on 2008-09-12
It worked!!!!  Thank you very much.

---

