---
title: "Skype starts automatically each time I boot up, won't go away."
date: 2008-08-07
forum: General Help
---

### Post by arnicainthemembrane on 2008-08-07
I've had this problem before.. I used skype once, and now for some reason there are three Skype windows on the desktop every time I start up ubuntu. How can I get rid of them? I tried removing the program...

---

### Post by jualin on 2008-08-07
Go to System, Preferences, Sessions, and uncheck Skype from there. Hope this helps!

---

### Post by cdtech on 2008-08-07
Go to "System > Preferences > Sessions" and uncheck under startup....

---

### Post by arnicainthemembrane on 2008-08-09
No, those options don't work. I tried "ad/remove" and synaptic to remove th program but I'm told that I don't have it, and yet there it is, every time I start up the computer.

My biggest issue with Ubuntu is that it isn't terribly clear which programs I've got, which ones I'm running, and which ones I can or can't remove. It seems absurd that this is the case because this is a basic function of any computer.

Bear in mind, I'm used to OSX which has a very simple graphic interface. In that way I'm dumbed down.

Is there a simple way to sort this out? Where fore example are all my program files so i can at least remove the ones I don't want or need?

thanks for all your help.

---

### Post by cdtech on 2008-08-09
Synaptic Package Manager is the proper place to add or remove programs. When you first open it, you'll see on the left side a list (All, Installed, Not installed, Not installed). The bottom "Not installed (residual config)" are the leftover configuration files from removed programs.

On a command line you could do "sudo apt-get autoremove && sudo apt-get clean" to clean out your repository. Then I would go to the "Synaptic Package Manager" and remove all of those leftover residual config files. You can hold your "shift" key then use your mouse to highlight all of them. Right click and select completely remove then apply.

If you compiled a program out of Synaptic then you have to manually remove what you installed.

---

