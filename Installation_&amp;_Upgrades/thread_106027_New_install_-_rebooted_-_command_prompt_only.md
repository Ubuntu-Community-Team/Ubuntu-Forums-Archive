---
title: "New install - rebooted - command prompt only"
date: 2005-12-19
forum: Installation &amp; Upgrades
---

### Post by jne on 2005-12-19
Hi I have just installed 5.1 with no reported errors, but after the reboot I get a balck screen with login and password reguests. I can login fine but it just goes to the next line with 

myloginname@theservername:~$ _

Where the above has my actual login name and computer name and the a prompt blinking at the end. 

Thanks for your help

A real newbee

---

### Post by matthewv on 2005-12-19
Your xserver has failed to start. Try running the command "startx" without quotes. If that fails (likely) try running ```
sudo dpkg-reconfigure xserver-xorg
``` to reconfigure your xserver. Then try running startx again.

---

### Post by jne on 2005-12-19
Thanks for your reply. Here's what I got:

typed in  startx

got -bash: startx: command not found


then typed in sudo dpkg-reconfigure xserver-xorg

got: 'xserver-xorg' is not installed and no info is available. Use dpkg --info (= dpkg-deb --contents) to list their contents. /usr/sbin/dpkg-reconfigure: xserver-xorg is not installed jne@ourtestserver:~$

---

### Post by Chris Tucker on 2005-12-19
wow, seems youve managed to install without a gui, try 
sudo apt-get install gdm xserver-xorg ubuntu-desktop
the password it asks for is just a repeat of your own password.

---

### Post by jne on 2005-12-20
Thanks Chris, It did a long update - downloading from the internet - went through set-up (most of which I saw it do during install) and then came back with the cmd prompt. I used your first suggestion "startx" and I am off and running!!!!!

Thank you soooo much for your help!!

---

### Post by mattsledge on 2005-12-20
[QUOTE=Chris Tucker]wow, seems youve managed to install without a gui, try 
sudo apt-get install gdm xserver-xorg ubuntu-desktop
the password it asks for is just a repeat of your own password.[/QUOTE]
I ran into this exact problem yesterday evening. After searching around for an answer for an hour or so, I luckily found it here. 

That tip did the trick. Thanks!

---

