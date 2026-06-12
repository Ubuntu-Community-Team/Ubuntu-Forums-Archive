---
title: "Installing KDE"
date: 2006-02-16
forum: Installation &amp; Upgrades
---

### Post by mdsmith on 2006-02-16
I did a search on installing KDE and found the command (sudo apt-get instal kubuntu-desktop). I tried the command and it said kubuntu-desktop not found.  I have breeze 5.10 installed. I would like to get KDE so I can use kppp and maybe get this thing to let me use the internet. Thanks Don

---

### Post by byen on 2006-02-16
EDIT: I just realized that you are not connected to the internet. You need an active internet connection to apt-get kubuntu. The only other way to install Kubuntu without the internet connection would be by having the Kubuntu CD.

---

### Post by aysiu on 2006-02-16
When you type the command ```
sudo apt-get install kubuntu-desktop
``` you're actually asking Ubuntu to install Kubuntu **from the internet**.

So if you don't have an internet connection, this isn't going to work, unfortunately.

Doesn't Gnome have a way for you to configure your dial-up?
Go to System > Administration > Networking. Nothing there helps?

---

### Post by anirban.sam on 2006-02-16
add the kubuntu repository to yr /etc/sources.list file and run apt-get again, or use a cd, you can still use apt-get or synoptic package manager, just add cd to yr repository list with adept updater

---

### Post by mdsmith on 2006-02-16
Thanks for the replies. I was afraid the internet was the problem. The internet is configured with what is the correct info and the system seem to connect. The modem makes the appropriate sounds and takes the normal amount of time and says it is connected but neither firefox nor evolution can find an address. If I had KDE I could use kppp which shows a log which would show the connection if it is made. I am going try the connection tommorrow during the hours my Isp's service is available and find out for sure if I am connected. There are other KDE apps I use often, but I much prefer Gnome for normal use. Thanks Don.

---

