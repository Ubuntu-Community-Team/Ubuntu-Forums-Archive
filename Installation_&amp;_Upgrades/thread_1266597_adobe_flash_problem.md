---
title: "adobe flash problem"
date: 2009-09-14
forum: Installation &amp; Upgrades
---

### Post by tony06 on 2009-09-14
after i upgrade firefox 3.0.14 to 3.5.3 in ubuntu 9.04 x 64 firefox cheap telling my that i must instal adobe but in provius version adobe flash it was working and anador problem seems that after i upgrade firefox the defult programs in ubuntu ar chenged how can i get back ubuntu programs default with firefox 3.5 exeption?   sorry for my bad english but pls i need help i am noob in ubuntu switched from windows

---

### Post by tony06 on 2009-09-15
nobody help???

---

### Post by David-IT on 2009-09-15
well i am no pro so i probably should not try to help but its worth a shot have you tried updating your PC? like with
> sudo update-manager
or
> gksudo update-manager
if that does not work then you can try to reinstall Firefox? by going to 
system>administrator>synaptic package manager>then searching Firefox and right click mark for re-installation.then click apply i am not sure if i helped you any but GL man!

---

### Post by oboedad55 on 2009-09-15
> **tony06 said:**
> after i upgrade firefox 3.0.14 to 3.5.3 in ubuntu 9.04 x 64 firefox cheap telling my that i must instal adobe but in provius version adobe flash it was working and anador problem seems that after i upgrade firefox the defult programs in ubuntu ar chenged how can i get back ubuntu programs default with firefox 3.5 exeption?   sorry for my bad english but pls i need help i am noob in ubuntu switched from windows

Did you uninstall 3.0? I just installed 3.5 from the repos without removing 3.0 and flash, etc. works. FWIW, I use the add-on FEBE to back up my FF profile. I just extracted it to my new FF 3.5 directory and all the add-ons and so forth now work.

---

### Post by tony06 on 2009-09-15
> **oboedad55 said:**
> Did you uninstall 3.0? I just installed 3.5 from the repos without removing 3.0 and flash, etc. works. FWIW, I use the add-on FEBE to back up my FF profile. I just extracted it to my new FF 3.5 directory and all the add-ons and so forth now work.
  i  uninstall 3.0

---

### Post by oboedad55 on 2009-09-15
> **tony06 said:**
> i  uninstall 3.0

Odd. Try reinstalling the adobe flash.

---

### Post by tony06 on 2009-09-15
> **oboedad55 said:**
> Odd. Try reinstalling the adobe flash.
I just installed flashplugin-nonfree via synaptic and it didn't  work

---

### Post by oboedad55 on 2009-09-15
> **tony06 said:**
> I just installed flashplugin-nonfree via synaptic and it did work

That's the one. Good job! Now you can pass on what you've learned.

---

### Post by tony06 on 2009-09-15
> **oboedad55 said:**
> That's the one. Good job! Now you can pass on what you've learned.
it not worked any suggestion

---

### Post by oboedad55 on 2009-09-15
> **tony06 said:**
> it not worked any suggestion

"I just installed flashplugin-nonfree via synaptic and it did work"

Not sure, it looks like you said it did work and now it doesn't work? Confused...

---

### Post by tony06 on 2009-09-15
> **oboedad55 said:**
> "I just installed flashplugin-nonfree via synaptic and it did work"

Not sure, it looks like you said it did work and now it doesn't work? Confused...
it not worked :(:(:(:(:( help pls!!!

---

### Post by tony06 on 2009-09-15
this is the comand line i used what i do wrong ??? if [[ ! -f /usr/bin/firefox ]]; then sudo apt-get update && sudo apt-get install firefox; fi && if [[ -e ~/.mozilla ]]; then cp -R ~/.mozilla ~/.mozilla.backup; fi && sudo tar -jxvf firefox-3*.tar.bz2 -C /opt && rm firefox-3*.tar.bz2 && sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup && sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins && sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox && sudo ln -s /opt/firefox/firefox /usr/bin/firefox

---

### Post by oboedad55 on 2009-09-15
> **tony06 said:**
> this is the comand line i used what i do wrong ??? if [[ ! -f /usr/bin/firefox ]]; then sudo apt-get update && sudo apt-get install firefox; fi && if [[ -e ~/.mozilla ]]; then cp -R ~/.mozilla ~/.mozilla.backup; fi && sudo tar -jxvf firefox-3*.tar.bz2 -C /opt && rm firefox-3*.tar.bz2 && sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup && sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins && sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox && sudo ln -s /opt/firefox/firefox /usr/bin/firefox

Wow, where did you get this? I just installed 3.5 from the repos and everything was carried over from 3.0. The only thing I did was using the FEBE add-on I extracted a backup to the new 3.5 directory under /home/user/.mozilla.

---

### Post by tony06 on 2009-09-15
i get this from [http://jaxov.com/2009/09/install-upgrade-firefox-3-5-3-in-ubuntu-linux/comment-page-1/#comment-1240](http://jaxov.com/2009/09/install-upgrade-firefox-3-5-3-in-ubuntu-linux/comment-page-1/#comment-1240) and  now nobody can't help my

---

### Post by oboedad55 on 2009-09-15
> **tony06 said:**
> i get this from [http://jaxov.com/2009/09/install-upgrade-firefox-3-5-3-in-ubuntu-linux/comment-page-1/#comment-1240](http://jaxov.com/2009/09/install-upgrade-firefox-3-5-3-in-ubuntu-linux/comment-page-1/#comment-1240) and  now nobody can't help my

I see basically what you did. You replaced 3.0 with 3.5. As I said, I used the repos which I think is safer. I wish I could offer you further assistance but I'm at the end of my reliable knowledge. Hang in there and someone else will jump in.

---

### Post by Khakilang on 2009-09-15
I install adobe flash plugin and it work even i upgrade to Firefox 3.5.

---

### Post by tony06 on 2009-09-16
pls help

---

### Post by tony06 on 2009-09-18
i manage to go back to 3.0.14   sudo rm /usr/bin/firefox && sudo dpkg-divert --rename --remove /usr/bin/firefox && sudo rm -r /opt/firefox thx all for all suggestion

---

### Post by Khakilang on 2009-09-18
I just go to add/remove and use the show all available software, than go to sound and video and look for Adobe Flash Plugin and click the small box, than click apply changes and it install by itself. I don't have problem even upgrading to firefox 3.5.

---

### Post by oboedad55 on 2009-09-18
> **tony06 said:**
> i manage to go back to 3.0.14   sudo rm /usr/bin/firefox && sudo dpkg-divert --rename --remove /usr/bin/firefox && sudo rm -r /opt/firefox thx all for all suggestion

Tony, glad to hear you got it. I was all out of ideas...

---

