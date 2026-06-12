---
title: "[SOLVED] how to tell an app to start on boot"
date: 2008-07-28
forum: General Help
---

### Post by Kain000 on 2008-07-28
hey everyone, 
I want to have firestater load on boot,  It didnt show up on the list when I go to admin>system monitor>programs until I actually click the icon to start it.  I know you can set programs to start up on boot under system> Pref> sessions and to add the program i navigate to etc > firestater> and then where?  firestater.sh?

---

### Post by ryanhaigh on 2008-07-28
[This page]("http://packages.ubuntu.com/hardy/i386/firestarter/filelist") indicates that firestarter has a startup script (/etc/init.d/firestarter) which indicates to me that it is probably starting at boot. As far as I know firestarter is a tool to change the iptables rules so once those changes are made, which is probably what the startup script does, there is no need for a running firestarter process.

This page has a bit more explanation and also tells you what changes you need to make if you do still want the GUI firestarter app to load every time you boot.

[http://www.fs-security.com/docs/faq.php#reboot](http://www.fs-security.com/docs/faq.php#reboot)

---

