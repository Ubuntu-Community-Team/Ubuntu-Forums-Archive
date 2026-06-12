---
title: "Upgrade issues."
date: 2009-01-16
forum: Installation &amp; Upgrades
---

### Post by birdmartin on 2009-01-16
Hello, Ussually my updates take 20 -40 minutes. A couple days ago I went to install my updates and it was taking longer than i anticipated or could wait at the time. So i closed out of it. Since i did that i cannot connect to the internet let alone my own network or network settings. Everytime i try to reload the updates this error comes up:

"An error occured. 
  The following details are provided:

E: dpkg was interrupted, you must manually run 'dpkg --configure - a' to correct the problem.
E: _cache->open()failes, please report."

Please help!!

---

### Post by iaculallad on 2009-01-16
Do as the error message say's. On your terminal, issue the command:

```
sudo dpkg --configure -a
```

EDIT: And, don't worry if the characters you're inputting does not echo back on your monitor (for security purpose). Just enter your password and hit the Enter key.

---

### Post by birdmartin on 2009-01-16
You're going to laugh at my ignorance ... how do i issue a command from my terminal? Pull out the puppets and explain it as if you were tryin to explain it to a 6 year old please. :p

---

### Post by Partyboi2 on 2009-01-16
> You're going to laugh at my ignorance
Just a learning curve :)

To open a terminal on the top panel  click on "Applications" then go to "Accessories" on the drop down menu and click on "Terminal" then enter the command as iaculallad has posted remembering that when you enter your password you will not see it displayed on screen.

---

### Post by birdmartin on 2009-01-17
Thanks alot, both of you. : )

---

### Post by birdmartin on 2009-01-17
I did that and then it went through a bunch of update loading and eventually got to this message at the bottom .. 

Processing triggers for libc6 ...
Ldconfig deffered processing now taking place
processing triggers for initramfs-tools ...
update-initramfs: generating /boot/initrd.img-2.6.24-19-lpia
Errors were encountered while processing:
 capplets-data

---

### Post by birdmartin on 2009-01-17
updated then rebooted ... then another error occured.

W: Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/d/deskbar-applet/deskbar-applet_2.22.3-0ubuntu1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/d/deskbar-applet/deskbar-applet_2.22.3-0ubuntu1_lpia.deb)
  Could not resolve 'dell-mini.archive.canonical.com'

Then a bunch of the same error underneath it repeated.

---

### Post by Partyboi2 on 2009-01-17
Would you please be able to post the whole output to 
```
sudo dpkg --configure -a
``` seems that there is a problem with   capplets-data package.

---

### Post by birdmartin on 2009-01-17
How would i find the whole output for that? I edited my previous post with the new error that is occuring at the moment.

---

