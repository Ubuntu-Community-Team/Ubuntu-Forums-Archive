---
title: "Dell Inspiron 1200 installation"
date: 2008-07-26
forum: Hardware
---

### Post by cocobrotha1 on 2008-07-26
Wassup, people. I'm a noob, obviously.  But, i need some help with a few things with this new operating system. First off, I need a list of all the commands for the x terminal in Ubuntu 8.04. I also need help with viewing videos from youtube or any site that shows videos, I can't regulate this at all. and last but not least i downloaded a theme for ubuntu OSX 3.3 and I CANNOT FIND THE DAMN THING IN HERE. I know that my Firefox is setup to download to the tmp folder, but i still can't find it. Can anybody pleeeeeeeeeeeeease help a brotha.  I'd appreciate it very much. One last thing. I DO NOT Want to hear any flack about where i'm posting this thread at. LIKE I SAID IN THE BEGINNING, I'M A NOOB. so, please ease back with the comments.

---

### Post by northern lights on 2008-07-26
> **cocobrotha1 said:**
> First off, I need a list of all the commands for the x terminal in Ubuntu 8.04[Learning the shell]("http://www.linuxcommand.org/learning_the_shell.php")


> **cocobrotha1 said:**
> I also need help with viewing videos from youtube or any site that shows videosRun```
sudo apt-get install ubuntu-restricted-extras flashplugin-nonfree
```
Should sound still not work, install PulseAudio - follow [https://wiki.ubuntu.com/PulseAudio]("https://wiki.ubuntu.com/PulseAudio")


> **cocobrotha1 said:**
> i downloaded a theme for ubuntu OSX 3.3 and I CANNOT FIND THE DAMN THING IN HEREOpen firefox, navigate to "Edit > Preferences" and under the "main" (first) tab either set downloads to "Always ask" or select "Save to" and put some folder you will find, for instance "/home/USER/downloads", where USER needs to be replaced by your username.

---

