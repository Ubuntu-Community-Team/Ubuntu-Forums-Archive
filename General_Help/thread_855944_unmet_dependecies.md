---
title: "unmet dependecies"
date: 2008-07-11
forum: General Help
---

### Post by ethonhawk on 2008-07-11
Hello Community,

I am a brand new user to Ubuntu and I absolutely love it!  The only thing is I tried to do a bit of upgrading this evening and things just did not work out the way I thought they would, so I am calling on the community to help me out of this sticky situation.  
See, what happen is I had a friend install Ubuntu on my laptop and started using it with ease, but when I tried to watch a DVD, the player would not work, so I tried to do some updating, install RealPlayer, some codecs, and other stuff like GoogleEarth while I was on the page with the codecs apt-get screen.  I apologize if I do not make much sense, again I am brand new to this operating system.  
After typing in the codecs from the ubuntu forum on the apt-get terminal and rebooting, I got a message like this (along with a European do not enter street sign in my task bar) stating this-
"An error occurred, please run Task Manager from the right-click menu or apt-get terminal to see what is wrong.  The error message was: 'Error: Opening the cache (E:Type '<!DOCTYPE' is not know on line 1 in source list /etc/apt/sources.list.d/medibuntu.list, E:The list of sources could not be read.)'This usually means that your installed packages have unmet dependencies
Either way I have unmet dependencies and need some help.  Anyone care to lend a hand?

---

### Post by Bubba64 on 2008-07-11
This link has been a great help to many make sure you read carefully and understand.
[http://ubuntuforums.org/showthread.php?t=766683&highlight=reassuringly+offensive](http://ubuntuforums.org/showthread.php?t=766683&highlight=reassuringly+offensive)

---

### Post by FuturePilot on 2008-07-11
It looks like there's something messed up with the Medibuntu sources list. I've seen this a number of times on the forum.
Assuming you're using Ubuntu 8.04.
First get rid of the current list.
```
sudo rm /etc/apt/sources.list.d/medibuntu.list
```
Then get a new one
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
Then get the gpg key for it.
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
If it gives you a warning about authentication just say yes.

Taken from
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by p_quarles on 2008-07-11
Moved to General Help.

---

### Post by aysiu on 2008-07-11
First tip: never retype commands into the terminal. *Paste* them in instead. Less work. Less room for error.

That said, it sounds as if your /etc/apt/sources.list.d/medibuntu.list file is messed up: ```
'Error: Opening the cache (E:Type '<!DOCTYPE' is not know on line 1 in source list /etc/apt/sources.list.d/medibuntu.list, E:The list of sources could not be read.)'
``` Can you post the output of this command? ```
cat /etc/apt/sources.list.d/medibuntu.list
```

---

### Post by ethonhawk on 2008-07-11
I really appreciate everyone involved in helping me.  I am trying to remedy the problem now.  Again, thank you.

---

