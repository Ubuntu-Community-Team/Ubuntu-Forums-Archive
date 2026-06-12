---
title: "Installation T61 - Driver Problems"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by Trentor on 2008-12-21
Hello, I have installed Ubuntu 8.10 on my Thinkpad t61 laptop.

The installation went smoothly, no bumps or bruises along the way.  I am only having one major problem.  I am trying to enable Extra visual effects but whenever I try to I get the message "Enable Driver?" and it explains to me how I need to install not open drivers.  I have tried to install the version 177 and 173 drivers for my Nvidia card but they do not solve the problem.

Whenever I try to install the drivers it pops up a smaller box and then shows 0% and then closes.

At first I thought that it was because I was not connected to the internet so I tried connecting to the internet, and tried again once I got connected to my wireless router but the problem still occurs.

If there are any details I missed please let me know.  :P

Trentor

---

### Post by Pumalite on 2008-12-21
You need to be wired to the Internet or at least have a firm connection to your wireless router.
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_ThinkPad_T61#Accelerated_Video_and_Desktop_Effects](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_ThinkPad_T61#Accelerated_Video_and_Desktop_Effects)

---

### Post by Trentor on 2008-12-21
Ok, I went to the weblink that you provided, and it has helped me a little.  I realize that I know I will have to install the program Envy in order for this to work, as I tried it again with a wired connection and it still has the same problem.

However, when I try to install Envy I get the following error:

Error:  Dependency is not satisfiable:  build-essential

I'm wondering if it has something to do with the fact that Envy is meant for Ubuntu 7.10 and I am running 8.10

I'm sorry if error message is something common/unrelated, but I am new to Linux.

I'm not sure if this makes the installation any different, but I did install Ubuntu inside of windows (nor virtual machine, but the option in the installer).

Thanks, Trentor :P

---

### Post by Trentor on 2008-12-22
Nevermind, it took some fixing, but I managed to get EnvyNG working.

I have no idea why it does not appear in my applications pull down menu but as long as it works I am ok with it.

Thanks, go Linux!

Trentor :P

---

### Post by Partyboi2 on 2008-12-22
Hi,
You need to install the   build-essential package which you can do by opening a terminal (Applications>Accessories>Terminal) and typing
```
sudo apt-get install  build-essential
```
then after it is installed try install envy again.

---

