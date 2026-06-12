---
title: "Yahoo Chat"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by frozenfire0808 on 2009-01-23
I'm new in Ubuntu , but here is a problem I faced. The following is a little wordy but is actually easier if you try it.

When in Yahoo mail I click on the button next to Hi, whatever user name I chose in order to get into Yahoo chat since it says I'm offline. A box then appears that says Your browser must have Flash 9.0.115 or higher installed to load the chat feature. You can download and install the latest Flash Player  here When I click here I end up at              [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)     from there I clicked on the Select version to download and chose   .deb for Ubuntu 8.04+   and clicked the Agree and Install now button a window then shows up that says You have chosen to open install_flash_player_10_linux.deb whichs is a: Software package from    [http://fpdownload.macromedia.com](http://fpdownload.macromedia.com)  What should Firefox do with this file? From there there are a few options Open with GDebi Package Installer (default) or firefox-3.0.5 or to save it as the previous two or choose other. I chose open with GDebi Package Installer (I've tried them all but I'm just doing a walk through) anyways I chose ok. It downloaded and the status says it is already installed but I chose the reinstall button but still I can't get into the chat even after restarting the computer. I've tried many combinations but it still won't work. Any help would be appreciated.

---

### Post by karanpals on 2009-01-23
get the flashplayer for linux and install
[http://www.adobe.com/products/flashplayer/](http://www.adobe.com/products/flashplayer/)

---

### Post by bgerlich on 2009-01-23
In (Applications)Add/Remove Programs install ubuntu-restricted-extras

plus (apps->internet)Pidgin works with Yahoo Chat.

---

### Post by jimmyhacker on 2009-01-23
Karanpals dont be dumb!please.Open it with Gdebi Installer andy click install.

---

### Post by frozenfire0808 on 2009-01-23
I might not have mentioned this but when trying to install it automaticaly detected that I am using linux but it does give me the option to choose a different operating system though.

Thanks for trying though.

---

### Post by frozenfire0808 on 2009-01-23
I just installed ubuntu-restricted-extras

plus and reinstalled it again. and tried from yahoo again. It didn't work. Do I need to restart my computer? Or should I try something else?

---

### Post by bgerlich on 2009-01-23
You need to restart firefox, remember to close all firefox windows, including "downloads"

---

### Post by graingert on 2009-01-23
Do not install directly from adobe; you need to use ubuntu-restrected-extras which will download and install flashplugin-nonfree automaticly

---

### Post by frozenfire0808 on 2009-01-23
I just cleared all programs on my screen and deleted all cookies cash history etc.  I tried again from yahoo It didn't work.

---

### Post by frozenfire0808 on 2009-01-23
I'm going to try the Micromedia flash plugin which is below the restricted extras which I already installed.

---

### Post by bgerlich on 2009-01-23
Does your Flash work, or is it a Yahoo issue? Go to youtube, try to view a video.

---

### Post by frozenfire0808 on 2009-01-23
I can watch a video on Youtube

---

### Post by frozenfire0808 on 2009-01-23
someone suggested Do not install directly from adobe; you need to use ubuntu-restrected-extras which will download and install flashplugin-nonfree automaticly      since I tried the Ubuntu-restrected-extras  is there another place I can get adobe flash because I thought yahoo would send me to a website that always works even with linux users but I could be wrong if I am would someone suggest a website.

---

### Post by bgerlich on 2009-01-23
Your flash is working just fine.

Try to install this addon: [https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

It will allow you to spoof your User Agent Identification, your computer will identify as windows, maybe this will help (you can change the identification string in Tools-> User Agent after install).

Plus as I said before Pidgin, which you will find in Applications->Internet works with Yahoo Chat.

---

### Post by frozenfire0808 on 2009-01-23
I tried that addon you mentioned It didn't help. I'll try that Pidgin thing you mentioned next.

---

### Post by frozenfire0808 on 2009-01-23
That Pidgin thing seems really close to yahoo chat I'll use that unless someone thinks they know the answer to my question I check this thread every once in a while.

Thanks for the help.

---

### Post by Sef on 2009-01-23
Flash may not be linked to Firefox.   I'm not sure of the command offhand.  If I find it, I will post it for you.

Update:

1) [Kilz's Tutorial]("http://ubuntuforums.org/showthread.php?t=772490")

2) [Other Post]("http://ubuntuforums.org/showthread.php?t=998957&highlight=link+flash+firefox")

---

