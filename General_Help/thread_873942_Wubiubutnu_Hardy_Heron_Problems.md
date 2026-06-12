---
title: "Wubi/ubutnu Hardy Heron Problems"
date: 2008-07-29
forum: General Help
---

### Post by JustinB_Xp on 2008-07-29
Hello I am new here and am looking for a little help 
I would like to begin with that I love Different OS's and not just the prominent Windows and was looking to give Ubuntu a try through Wubi on my Win XP Home edition, all went well the installation of wubi and the download of the ISO file so I rebooted the computer like asked and Chose "Ubuntu" on the boot option and let Ubuntu set itself up, then the problems came after it set up Ubuntu restarted the whole computer and I didn't get a prompt asking for it to happen so after that I chose Ubuntu once again and it asked me for my User name and password so I entered them correctly and pressed enter and it went to the same login screen it didn't say anything was incorrect or anything so I tried to log in again and the same thing happened and i went through this about 15 times before it finally let log in but still had problems the background would load...but nothing else did I let it sit for 5 minutes and still nothing had loaded so I clicked on the background and it brought me to the log in screen again so I had to log in again (once this time) and again nothing loaded so I clicked again and told me to log in again so eventually I just booted back up into windows and uninstalled Ubuntu BUT would still like to give Ubuntu a try if I can get some help on the situation so the same problems do not occur 

Thanks 
-Justin

---

### Post by JustinB_Xp on 2008-07-30
Bump

---

### Post by ago on 2008-07-30
Might be a video driver issue, you can normally find out by pressing ctrl+alt+f2 to get a terminal and exploring the logs in /var/log (particulary xorg.log and syslog) with the command less

---

