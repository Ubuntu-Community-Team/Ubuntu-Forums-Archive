---
title: "Firefox is glitching - happened on two comptuers"
date: 2008-08-31
forum: General Help
---

### Post by itsjareds on 2008-08-31
For some reason, Firefox messed up. Hadn't done anything that would have caused it to, all I did was try to open an HTML file on my computer. It said "Firefox is open but not responding. End this process first". I did that and reloaded it, and then Firefox didn't load my home page or any of the saved session tabs.

It's really messing up, the address bar doesn't work anymore, it just stays as whatever I put into it, but doesn't change when I change pages. Another thing to note would be that random menu items aren't there anymore -- my bookmarks are gone and there is no history. I think it might have somehow removed all of my user settings, but why and how? I didn't do anything to give it a reason to.

This happened on two computers, this is the second time. On the first computer, Firefox messed up about a day after I installed Ubuntu. I can't remember how I fixed it, I tried completely re-installing Firefox with no avail. Somehow it got fixed, but this was a while ago, so I don't remember.

I'm using Ubuntu 8.04.1 with Firefox 3.0.1 -- both computers.

---

### Post by wolfen69 on 2008-09-01
the proper way to uninstall and re-install would be to go to synaptic and *completely* remove firefox. then go to your home folder and do ctrl+H. that will bring up your hidden folders. find your .mozilla folder and delete it. (backup your favs before this, if it's important to you) open a terminal and:
```
sudo apt-get clean
```
then
```
sudo apt-get autoremove
```
then re-install firefox. you should have no problem after this.

---

### Post by itsjareds on 2008-09-01
Thanks, that did it. I re-installed but I guess it was a problem with the .mozilla folder.

Now I can't find where to put my backup of the bookmarks, do I put it in my profile folder? It's a .json file, is this right?

---

