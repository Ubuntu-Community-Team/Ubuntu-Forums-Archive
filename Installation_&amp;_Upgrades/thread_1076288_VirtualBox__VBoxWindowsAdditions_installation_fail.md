---
title: "VirtualBox / VBoxWindowsAdditions installation failure"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by nfoto on 2009-02-21
Hello !

I just installed Ubuntu as a SUN VirtualBox Guest on my Windows machine. Installtion was not a problem. But: I cannot get any screen resolution higher than 800x600. Looking into the forum, I found that I have to install the so-called "Guest Additions".

I try to do so by starting the "Install Guest Additions" option in my virtual machine. 

This creates VBOXADDITIONS_2.1.2_41885, wich I can see on my workplace as my CD drive. And it should - but does not - autostart this CD an install some software. When I say "Start as autostart" I get a "file not found" error.

When I try to start the file VBoxWindowsAdditions.exe manually. I get an archive error: End-of-central-directory signature not found [...]


Does anybody know how to install the guest additions properly ?

I would appreciate any kind of help.

Best regards, Martin

---

### Post by konqueror7 on 2009-02-21
you have to manually install guest additions via terminal...
```
cd /media/cdrom
```
```
sudo ./VBoxLinuxAdditions-x86.run
```

---

### Post by nfoto on 2009-02-21
Thank you , that's it !

Of course, I have to install [COLOR="Red"]Linux[/COLOR] additions for Ubuntu, not Windows additions ...

And - I anbody else should have that problem - found that I have to say "sudo SH" before installation because if I don't, the installation will fail because of missing admin authorisation ...

Thank you again !

---

### Post by konqueror7 on 2009-02-21
glad to help!:D

---

### Post by ramrodewe on 2009-07-06
Just like to add my thanks as this post saved me some considerable time. Oddly (to me at least) I was able to install GuestAdditions from the GUI in the last incarnation of Virtualbox. Not sure what's changed

---

