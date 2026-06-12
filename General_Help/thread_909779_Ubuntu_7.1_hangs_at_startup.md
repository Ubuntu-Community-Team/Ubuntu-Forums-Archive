---
title: "Ubuntu 7.1 hangs at startup"
date: 2008-09-03
forum: General Help
---

### Post by winrowc on 2008-09-03
Hi,
I recently have been having trouble with Ubuntu starting up, and allowing me to log in, but then just hanging after I have been logged in with the beige default background, and no desktop. The mouse can move around and I can do things like Ctrl alt F1 , but it just doesnt show the desktop. I tried logging in as the root user as well and the same thing happened. Im not quite sure what I was messing with when it did this. I think I just like installed flash player and did some updates through synaptic. I tried resetting the xorg.conf file to its previous state but I dont think this problem has anything to do with that anymore, but I could be wrong... Is my problem too vague, or can anyone suggest something for me to try?
Thanks!

---

### Post by ntbutler on 2008-09-03
Hi.
Sorry, i might not be much help, but i'll give it a shot. Can you access any og the error logs (i think they are in /etc/log)
Look for events around the time when you try to log in, see if you can find the point where it hangs and/or what program it is trying to run.

---

### Post by winrowc on 2008-09-04
Okay so I did some searching and looking at daemon.log.0 in /var/log/ I found that at around the time when the error occured something called like `GTK_IS_TREE_VIEW' and `GTK_IS_TREE_Selection' failed. Similar to the 3rd person's error log in [this post]("http://ubuntuforums.org/showthread.php?p=4407127"). The difference is that I can't do anything after I log in and they seem to just have a problem with X rebooting. Is this an X problem? Can I change it back to its default?

---

### Post by ntbutler on 2008-09-04
Hmm. I am sorry, but i am really not sure about this. It does look like an X problem. It looks like (from RadiusXE's post) that a re-installation is in order, although i hate to say it. It's not a problem I have had, and i could find any threads that related to this problem (all of the ones that came up were ones about wireless networking...)
Just a thought, are you using a wireless connection? If so, you could try disabling it (or unplugging it) and seeing if that opens up the login again, (it is possible once you log in the network manager tries to access the network causing the crash. I thought that sort of stuff happened before the login screen, but maybe not, so try that...)
I'll keep looking over the forums to see if i see anything else that helps...

---

