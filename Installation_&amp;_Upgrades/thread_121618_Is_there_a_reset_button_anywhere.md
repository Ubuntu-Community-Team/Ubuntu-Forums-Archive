---
title: "Is there a reset button anywhere?"
date: 2006-01-25
forum: Installation &amp; Upgrades
---

### Post by Lord_MiL on 2006-01-25
Hey all!

I recently took the plunge into Ubuntu land and have been really enjoying it.  I've been setting up various packages but came across one I couldn't get to work.

So a guy who lives down the hall and is a self proclaimed Linux expert decided he'd handle the problem for me.

After about an hour of tinkering and installing all sorts of packages he finally gave up.  I asked him what all he installed but he couldn't remember.

Now I realize this might sound a bit OCD, but I don't like having dozens of random packages installed that I don't know about or need.  I like to keep track of everything on my system so I can keep it nice and clean.

Is there any easy way to restore my system to just the base packages that come on the Ubuntu DVD without doing a total reinstall?

Thanks in advance!

---

### Post by Sutekh on 2006-01-25
I can think of ways to get rid of the packages he installed, but they are laborious.

Do you know how he setup these packages?  

Did he use 'Synaptic' - the package manager used for installing stuff the easy way?  If so you can access the history and see what has been installed by date and time.  Then you can choose what you want to keep and what to uninstall.  

If he installed applications using the command line you can also access the history using ```
history | grep install
```
this will return all commands entered with the word install in them.  You can try searching for other terms, like configure, make, or just type history and get everything.  Unfortunately you'd have to manually uninstall anything you didn't want, which may not be easy.

---

