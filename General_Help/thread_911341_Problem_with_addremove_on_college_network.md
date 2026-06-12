---
title: "Problem with add/remove on college network"
date: 2008-09-05
forum: General Help
---

### Post by 1packer on 2008-09-05
I am currently on a Ethernet connection at the University of Wisconsin, everything worked fine until I had to change my network password. Now add/remove and updates don't work. I think I just need to change the password these applications are trying to use, but I can't find where that would be.
Thanks

---

### Post by 1packer on 2008-09-05
Bump, anyone out there know how to change the proxy password that Ubuntu uses?

---

### Post by Shazaam on 2008-09-05
How did you configure your school access password before? You will probably need to change/add the password in System>Administration>Network. And you will probably need to set up the proxy info in Synaptic>Settings>Preferences>Network.

---

### Post by 1packer on 2008-09-06
I think it popped up a little box asking for a password, so I put it in. I have just tried doing those things as admin, but whenever I start something, it asks for the admin password, which I give, then it minimizes, showing on the bottom, and then it disappears. So I can't actually open the synaptic package manager besides from the red arrow saying I have updates...

---

### Post by doas777 on 2008-09-06
> **1packer said:**
> I think it popped up a little box asking for a password, so I put it in. I have just tried doing those things as admin, but whenever I start something, it asks for the admin password, which I give, then it minimizes, showing on the bottom, and then it disappears. So I can't actually open the synaptic package manager besides from the red arrow saying I have updates...

have you tried opening synaptic from the terminal with:
```
sudo synaptic
```

you should see any error messages in the terminal.

good luck,
/franklin

---

### Post by 1packer on 2008-09-06
That opened the updater, and it sucessfully installed those, but I couldn't update anything to make it work if I don't go through the terminal. Also, my add/remove programs feature still is just giving me the error that the following packages couldn't be install.

---

### Post by 1packer on 2008-09-06
bump, anyone have any more ideas?

---

### Post by doas777 on 2008-09-07
> **1packer said:**
> bump, anyone have any more ideas?
How did you set up the proxy for apt? did you install [apt-proxy]("http://apt-proxy.sourceforge.net/")?

I did a google on "use apt though proxy" and got a number of hits. do any of them look familiar? 

whatever your fix is going to be, it will be related to the proxy configuration, so try to remember how you got it set up. I've never tried that so i can't be of much further help.

good luck.
frank

---

### Post by 1packer on 2008-09-07
I am fairly sure a box just popped up and I plugged in the information. My problem seems to be with the configuration of the GUIs, everything in the terminal works fine. For some reason whenever I try to open synaptic from the system menu, it just closes itself.

---

### Post by doas777 on 2008-09-08
> **1packer said:**
> I am fairly sure a box just popped up and I plugged in the information. My problem seems to be with the configuration of the GUIs, everything in the terminal works fine. For some reason whenever I try to open synaptic from the system menu, it just closes itself.

make sure your synaptic launcher uses the command ```
gksu synaptic
```

the problem may be with gksu

---

### Post by 1packer on 2008-09-08
how do I change the launcher command set?

this seems to be fairly strange problem since this stuff worked before,  but now most of my administrative features aren't working as they should.

---

### Post by doas777 on 2008-09-09
just as a test you can hit 'alt + F2' to bring up the "run task" dialog.
then enter 'gksu synaptic'.

if that doesn't work, then your problem is likely gksu/sudoers, especially if you have lost other administrative control. I don;'t know where to start troubleshooting an elevation problem, but at least it will get you on the right track in finding your answer.

good luck,
franklin

---

### Post by 1packer on 2008-09-09
Well that did the same thing that happens when I try to open stuff in the gui, showed it was opening it on the bottom, then closed it.

---

### Post by doas777 on 2008-09-09
ok, so sudo works but gksu does not. 

from a terminal run 'gksu synaptic'. it will likely fail as you have desceibed, so could you pleae post the error messages that the terminal displays as the app is breaking?

also try running 
```

gksu -k synaptic

```

this thread suggested it:
[http://ubuntuforums.org/showthread.php?t=207629](http://ubuntuforums.org/showthread.php?t=207629)

no ider if it'll work

---

### Post by 1packer on 2008-09-11
It trys to start it, but doesn't give an error message. The main difference is that it skips a terminal line when it trys to load it. I do have a seperate partition with all my data on it, so if this is not solvable, I do have the ability to reformat without losing much.

---

### Post by doas777 on 2008-09-11
thats good to hear. i always mount my home from another partition for just this reason. 

I'm usually loathe to suggest a nuke and rebuild approach (because you don't learn anything doing it that way), but if it saves you time and trouble, then nuke away.

otherwise it seems that your problem is that gksu is somehow broken (not a problem with synaptic, apt, the repos, or any proxies) so you could refine your query and start researching gksu failures.

anyway, good luck, and have fun in school,
Franklin

---

### Post by 1packer on 2008-09-11
I'll try that, if I can't find the info it's bye-bye ubuntu, for a few minutes.

Thanks for all the help, I think I'll leave it unmarked though in case anyone comes along at some point.

---

