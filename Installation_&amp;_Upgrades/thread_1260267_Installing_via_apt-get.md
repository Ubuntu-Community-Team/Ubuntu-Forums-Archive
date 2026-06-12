---
title: "Installing via apt-get"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by Motorhead Kaze on 2009-09-07
Howdy. I am trying to install a Japanese version of Firefox, but the Firefox page only provides a .tar.bz2 file. So I grabbed it, opened it, and there is a file named "firefox". 

Tried sudo apt-get install ./configure and ...there is no file called .configure in the (firefox) directory.
I tried sudo apt-get install firefox and of course, I was told that a recent version was already installed. So I thought I would be tricky and rename the file from "firefox" to "firefox-3.5" (which it is) and then ran sudo apt-get install firefox-3.5. That seemed to work, but all I got when running alt+f2 firefox-3.5 was an English version of Shiretoko Firefox 3.5. 

So, what would be the proper way to install Firefox 3.5.2 Japanese version, when I have no .configure file,and the above did not work?

Help? Thanks.

---

### Post by oldos2er on 2009-09-07
> **Motorhead Kaze said:**
> Howdy. I am trying to install a Japanese version of Firefox, but the Firefox page only provides a .tar.bz2 file. So I grabbed it, opened it, and there is a file named "firefox". 


 That's the file you need to run. Double-click on it.

---

### Post by Ratscallion on 2009-09-07
By default, Jaunty won't let you install firefox 3.5.. You have to do he following:
Download the file you've obviously already downloaded, and put it in your home folder.
Go to [http://psychocats.net/ubuntu/firefox](http://psychocats.net/ubuntu/firefox)
There's a chunk of code there which basically just installs it for you, just copy it into your Terminal, hit enter and BAM! Installed. Open firefox, press help, about and done.

Try this video if you need more help: [http://www.youtube.com/watch?v=GW1MVXVReys](http://www.youtube.com/watch?v=GW1MVXVReys)

---

### Post by Motorhead Kaze on 2009-09-07
Thanks for the replies

Oldos2er, clicking "firefox" does *run* Firefox but it doesn't install it. Meaning that I cannot run it from alt+F2, and it does not appear in applications/internet, and I want it to.

Ratscallion, I am not on Jaunty, but that rockin' code on [http://psychocats.net/ubuntu/firefox](http://psychocats.net/ubuntu/firefox) worked like a charm on Hardy (and on Mint too). All I had to do was to change the code slightly to reflect the version I am using, and thar I go. Thanks for pointing me to that page.

This command creates a diversion from the actual Ubuntu installed version, and renames the "stock" Firefox to "firefox.ubuntu" so I can still use that one if I like. Cool.

Thanks a bunch.

---

### Post by Motorhead Kaze on 2009-09-07
May as well post that code here: ```
if [[ ! -f /usr/bin/firefox ]]; then sudo apt-get update && sudo apt-get install firefox; fi && if [[ -e ~/.mozilla ]]; then cp -R ~/.mozilla ~/.mozilla.backup; fi && sudo tar -jxvf firefox-3*.tar.bz2 -C /opt && rm firefox-3*.tar.bz2 && sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup && sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins && sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox && sudo ln -s /opt/firefox/firefox /usr/bin/firefox
```

---

### Post by Ratscallion on 2009-09-08
Glad I could be of assisstance :) I used that myself and constantly do so when I re-install/use different Ubuntus/Linuxes and it works like a charm.. And I've recently got the Alpha 5 of Karmic, 3.5.2 is on there.

---

