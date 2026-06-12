---
title: "Log off, hibernate and suspend gone after upgrade"
date: 2007-04-17
forum: Hardware &amp; Laptops
---

### Post by rytmisk on 2007-04-17
If it ain't broken don't fix it... But I just can't stop it. 

Anyway - upgrading from edgy to feisty worked fine except - login button in gnome stopped working properly as well as the physical powerbutton. :( 

The natural thing to think then - at least for me - is that powersupport somehow has stopped working, but it works just fine - from the gdm login window. There I can choose suspend, hibernate and turn off, but the red log-off button in the corner of my gnome just logs me off directly. I have of course tried to change the setting in powercontrol to ask me. I have even tried to change settings in gconf-editor under apps/gnome-power-manager, but frankly I do not really know what to change (see screenshot)[IMG]http://ubuntuforums.org/attachment.php?attachmentid=29903&stc=1&d=1176794611[/IMG]

I have also tried to make a new user to avoid the problem with old files in my user dir, but that didn't change anything.

Does anyone know how to fix this? I'm not using beryl, xgl or anything else but metacity/gnome

I'd be really happy if someone could help!!

Best regards
Ketil

---

### Post by rytmisk on 2007-04-18
Anyone?

---

### Post by kverde on 2007-04-19
I have the same problem.  I use suspend all of the time.  I would love to know a way to get it back up there!

---

### Post by rytmisk on 2007-04-19
I actually just solved it. 

In my case it was a case of the upgrade not having completed properly since apt believed I had a kernel left which I had removed long ago. If t is the same for you try to install anything from the command line (not from synaptic as it will not give a complete error message). f there are errors see if they reference a kernel image which it cannot find. If they do open make a symlink to the existing folder/image with the referenced name.

Or it can be that you only need to install a small programme called gtweakui. Then you can tick a box "show logout menu" which for me really only got me back my dialogue box, but without hibernate/suspend. It was only after I managed to fix the upgrade like described above that everything worked.

Hope it works for you!

Ketil

---

