---
title: "Java problem"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by Kmob810 on 2009-05-18
Reasonably new to Ubuntu and using 8.10
I run a website and recently I added a chat page. When I try to open the page I am advised that I need a Java Plugin. I have downloaded this but cannot open the .bin file as the installation process asks me to choose which programme to open it with and I haven't got a clue! can someone advise me how best to run this plugin? Thanks

---

### Post by vikkikanhaua on 2009-05-18
you don't have to download the plugin separately
just type in terminal:
sudo apt-get install sun-java6-plugin

---

### Post by ad_267 on 2009-05-18
What vikkikanhaua said, or you can install the sun-java6-plugin from System - Administration - Synaptic Package Manager. See [Installing Software in Ubuntu]("http://www.psychocats.net/ubuntu/installingsoftware").

---

### Post by Kmob810 on 2009-05-18
Thank you Vikki, I' off to work now but I will do as you suggest when I come back home.
Thanks again

---

### Post by Kmob810 on 2009-05-18
Thanks AD. I will bear your comments in mind.

---

### Post by Kmob810 on 2009-05-19
> **vikkikanhaua said:**
> you don't have to download the plugin separately
just type in terminal:
sudo apt-get install sun-java6-plugin
Well Vikki, I did as you suggested and everything loaded (slowly) but there is no difference, when I tried again to open the chat room I was informed that I needed a 'Java Plugin@.
I tried the other suggestion from below and I've now found that I have a problem with Synaptic Manager. On clicking it opens with "e. dpkg was interruted you must manually run 'dpkg --configure -a" to correct the problem. When I tried to input that into a terminal I was told that I need to be superadmin (or something like that). Any ideas on how to sort this???????

---

### Post by Kmob810 on 2009-05-19
> **vikkikanhaua said:**
> you don't have to download the plugin separately
just type in terminal:
sudo apt-get install sun-java6-plugin
Vikki, I managed to get Syn Man working with help from the forum and have now intalled the java6. Everything is working great. Thanks for your help.

---

### Post by ad_267 on 2009-05-19
You get that error if you have a crash or shut down your computer while an update is in progress. You need to put a "sudo" before the command and then enter your password to run it as root: "sudo dpkg --configure -a"

If you've installed that package then you should have a working java plugin, I'm not sure why you'd still be getting that error.

Edit: Never mind, looks like you got it sorted :)

---

