---
title: "Mozilla problems"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by Rmelze on 2008-12-31
I'm not sure where to post this question. So please move it if I posted in the wrong are. Anyway, last night I installed ubuntu 8.10, and the installation went fine but when I tried to go to diffenent websites the page got stuck on loading the site. Not all sites did this but most of them did. I really want to try ubuntu, and learn about it but it is irritating, that mozilla wouldnt open hardly and web pages. Then I installed windows on the computer and ued the live cd,  then I ran ubuntu over windows and the same thing happened. can you please give me advice on how to fix this problem so I satart using ubuntu. BTW I tried looking for an answer to this but I could not find one.

---

### Post by Just-trevor on 2008-12-31
Do you have a strong internet connection?
Try installing a different web browser like Opera and see if it does the same thing
Do you have the same problem with Windows?

---

### Post by Rmelze on 2008-12-31
My internet connection is good, and I don't have any problems on the other machines I have running in the house. I tried going to the opera site and I couldn't get the page to load. The only page the would load was google.com...When I tried to click on the links from google I got stuck in this loading state.

---

### Post by Just-trevor on 2008-12-31
Did you install the flash plugins and stuff?

---

### Post by Rmelze on 2008-12-31
No, I didn't install any plugins, I couldnt get to any websites to do anything. Can you direct me on how to install the plug ins? Im protty good with how to use and run windows, but completely lost with ubuntu.

---

### Post by skern03 on 2008-12-31
> **Rmelze said:**
> No, I didn't install any plugins, I couldnt get to any websites to do anything. Can you direct me on how to install the plug ins? Im protty good with how to use and run windows, but completely lost with ubuntu.

I don't know what happened to Firefox in 8.04, but it is buggy and crashes a lot.

Try the following instructions in a Terminal window. It will uninstall and reinstall Firefox. I tried a uninstall/reinstall via Synaptic, but it didn't work. These helped, although in 8.04, I had to repeat them a few times over the past several weeks. I just upgraded to 8.10 after purchasing a new DVD drive (the old refused to load 8.10), so time will tell if Firefox is improved any.

> sudo killall -9 -r firefox
sudo apt-get purge firefox firefox-3.0 ubufox
sudo apt-get install --reinstall firefox firefox-3.0 firefox-3.0-gnome-support


---

### Post by Rmelze on 2008-12-31
It doesnt seem that ff is crashing, but more like stuck in a constant state of loading almost all webpages. but then I'll open a new tab and go to google with no problems. I tried to install ubuntu 3 times in all. All with the same problem. I had different hardware in the machine for the last install, but that didn't help any.(I didn't think that it would)

---

### Post by skern03 on 2008-12-31
> **Rmelze said:**
> It doesnt seem that ff is crashing, but more like stuck in a constant state of loading almost all webpages. but then I'll open a new tab and go to google with no problems. I tried to install ubuntu 3 times in all. All with the same problem. I had different hardware in the machine for the last install, but that didn't help any.(I didn't think that it would)

There are quite a few browsers other than FoxFire that don't require you to load a URL into FF just to download - they're available in Ubuntu. From the menu, just select Applications, Add/Remove... and click Internet on the left. In the search bar, type "browser" without the quotes. Maybe try Seamonkey or one of the other high-rated browsers. 

See attached screenshot.

---

### Post by Just-trevor on 2009-01-04
Maybe it's a firewall - what internet provider do you have?
For Verizon if you type your IP Address into the Address bar you can configure your settings, unless of course that doesn't load as well...
You can also usually reset your router by holding the little reset button in the back down for a while to restore default settings
I'm pretty sure you can find your IP Address by going to System -> Administration -> Networking Tools, but I'm really not sure because for some reason it's not loading for me right now.

---

