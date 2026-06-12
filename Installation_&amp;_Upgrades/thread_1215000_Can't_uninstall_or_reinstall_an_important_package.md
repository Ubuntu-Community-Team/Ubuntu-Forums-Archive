---
title: "Can't uninstall or reinstall an important package"
date: 2009-07-16
forum: Installation &amp; Upgrades
---

### Post by HardHaley on 2009-07-16
Hi, posting to see if anyone will help me fix a small issue regarding uninstalling or reinstalling a certain package, linux-restricted-modules-2.6.28-13. Synaptic Package Manager tells me that it can't be found. I can't install anything at all because of this. It seems like a really important package. Please help me out?
[http://ubuntuforums.org/images/icons/icon12.gif](http://ubuntuforums.org/images/icons/icon12.gif)





Thanks, Jimmy

I can see the package, but it won't let me change the status of it, i.e I can't reinstall or remove the package. I really love Ubuntu, but this is reeeally annoying :) Never encountered this before on my other installs of the os. Thanks for any replies.

---

### Post by ramnarayan on 2009-07-16
> **HardHaley said:**
> Hi, posting to see if anyone will help me fix a small issue regarding uninstalling or reinstalling a certain package, linux-restricted-modules-2.6.28-13. Synaptic Package Manager tells me that it can't be found. I can't install anything at all because of this. It seems like a really important package. Please help me out?
[http://ubuntuforums.org/images/icons/icon12.gif](http://ubuntuforums.org/images/icons/icon12.gif)



had a similar problem and thought 9.04 was crashing all around me 

try
sudo apt-get install -f

it seemed to work for me

---

### Post by bruno9779 on 2009-07-16
Have you tried :
```

sudo apt-get autoclean
sudo apt-get autoremove
```

most of the times it is enough.

oh, and a 

```
sudo apt-get update
```

to close

---

### Post by HardHaley on 2009-07-16
Thanks alot for the help, I'm trying this out right now, didn't expect a response so soon, even got two people helping me out :D

---

### Post by HardHaley on 2009-07-16
Okay, I tried sudo apt-get install -f but that only shows me the same error as before when I tried installing. Also tried those other commands, and sudo apt-get autoclean does something but I don't think that fixed it, since I then tried sudo apt-get autoremove, and it only prompts me to a partial install, which doesn't help me, sorry:) So still no progress... Posting a little info here that may or may not help; linux-restricted-modules-2.6.28-13-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

Thanks for your continued efforts ;)

---

