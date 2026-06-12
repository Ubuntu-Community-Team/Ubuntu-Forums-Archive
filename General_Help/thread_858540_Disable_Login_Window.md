---
title: "Disable Login Window"
date: 2008-07-13
forum: General Help
---

### Post by guitar4ya on 2008-07-13
Is there a way to disable it from the terminal?  The gui isn't working for me it won't save any changes I make for some reason...

---

### Post by guitar4ya on 2008-07-13
bump

---

### Post by SlalomMan on 2008-07-14
I'm not sure what you mean by it not working, but you could always go into your login window settings and set the auto-login to be one second or something. 

Unless it won't save that change, then in that case I'm not sure. I'm not an advanced user, but that may be a quick and dirty solution. I'm sure one of the pros could give you a cleaner one.

---

### Post by bodhi.zazen on 2008-07-14
```
sudo /etc/init.d/gdm stop
```

This command stops it.

Now to start it :

```
sudo /etc/init.d/gdm start
```

Post any errors and we can de-bug.

To start X (your gui) without the log in screen

```
startx
```

To disable the log in screen permanently :

```
sudo mv /etc/rc2.d/S30gdm /etc/rc2.d/s30gdm
```

To re-enable

```
sudo mv /etc/rc2.d/s30gdm /etc/rc2.d/S30gdm
```

---

### Post by aysiu on 2008-07-14
As others have indicated, probably the best thing to do is figure out why you can't use the GUI to set this up (in other words, what exactly happens when you go to System > Administration > Login Window?). To help diagnose this, paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then post the output back here: ```
gksudo gdmsetup
```

---

### Post by guitar4ya on 2008-07-14
> **aysiu said:**
> As others have indicated, probably the best thing to do is figure out why you can't use the GUI to set this up (in other words, what exactly happens when you go to System > Administration > Login Window?). To help diagnose this, paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then post the output back here: ```
gksudo gdmsetup
```

I did this and the following came up in terminal...

```
jason@jason-laptop:~$ gksudo gdmsetup

(gksudo:6430): Gtk-WARNING **: Error parsing gtk-icon-sizes string:
	'panel-menu=24,24
panel=20,20
gtk-button=18,18
gtk-large-toolbar=24,24'
gdmsetup[6431]: GLib-CRITICAL: g_key_file_to_data: assertion `key_file != NULL' failed
gdmsetup[6431]: GLib-CRITICAL: g_file_set_contents: assertion `contents != NULL || length == 0' failed
gdmsetup[6431]: GLib-CRITICAL: g_key_file_free: assertion `key_file != NULL' failed
gdmsetup[6431]: GLib-CRITICAL: g_key_file_set_string: assertion `key_file != NULL' failed
gdmsetup[6431]: GLib-CRITICAL: g_key_file_to_data: assertion `key_file != NULL' failed
gdmsetup[6431]: GLib-CRITICAL: g_file_set_contents: assertion `contents != NULL || length == 0' failed
gdmsetup[6431]: GLib-CRITICAL: g_key_file_free: assertion `key_file != NULL' failed
gdmsetup[6431]: GLib-CRITICAL: g_key_file_set_string: assertion `key_file != NULL' failed
gdmsetup[6431]: GLib-CRITICAL: g_key_file_to_data: assertion `key_file != NULL' failed
gdmsetup[6431]: GLib-CRITICAL: g_file_set_contents: assertion `contents != NULL || length == 0' failed
gdmsetup[6431]: GLib-CRITICAL: g_key_file_free: assertion `key_file != NULL' failed
gdmsetup[6431]: GLib-CRITICAL: g_key_file_set_string: assertion `key_file != NULL' failed
gdmsetup[6431]: GLib-CRITICAL: g_key_file_to_data: assertion `key_file != NULL' failed
gdmsetup[6431]: GLib-CRITICAL: g_file_set_contents: assertion `contents != NULL || length == 0' failed
gdmsetup[6431]: GLib-CRITICAL: g_key_file_free: assertion `key_file != NULL' failed
gdmsetup[6431]: GLib-CRITICAL: g_key_file_set_string: assertion `key_file != NULL' failed
gdmsetup[6431]: GLib-CRITICAL: g_key_file_to_data: assertion `key_file != NULL' failed
gdmsetup[6431]: GLib-CRITICAL: g_file_set_contents: assertion `contents != NULL || length == 0' failed
gdmsetup[6431]: GLib-CRITICAL: g_key_file_free: assertion `key_file != NULL' failed
gdmsetup[6431]: GLib-CRITICAL: g_key_file_set_string: assertion `key_file != NULL' failed
gdmsetup[6431]: GLib-CRITICAL: g_key_file_to_data: assertion `key_file != NULL' failed
gdmsetup[6431]: GLib-CRITICAL: g_file_set_contents: assertion `contents != NULL || length == 0' failed
gdmsetup[6431]: GLib-CRITICAL: g_key_file_free: assertion `key_file != NULL' failed

```

---

### Post by guitar4ya on 2008-07-14
bigity bump

---

### Post by guitar4ya on 2008-07-15
Anyone?

---

### Post by guitar4ya on 2008-07-16
Well after scouring the internet for this, my buddy found a solution.  Apparently there was a bug in the gdm that he found on launchpad.  Being totally new to this ubuntu stuff I didn't even know about that site.  Anyways, The link is [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/195296](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/195296) if anyone else has had this problem.  I guess there needs to be a gdm.conf-custom file and the gdm.conf and gdm.conf-custom both need to be the same.  Well the gdm.conf-custom file didn't even exist on my computer so I had to create it and copy the contents from the gdm.conf file that was there into that one and save it and voila it worked.

---

### Post by hellzkeeper1216 on 2008-07-16
Click
System>Administration>Login Window
click on the [Security Tab]
and then click on [Enable Automatic Login]
nevermind this post though... didn't read the full post... damn rum.

---

### Post by guitar4ya on 2008-07-17
Haha yea I wish I had a dollar for how many times I actually tried doing that.  I'm glad I got it working now.

---

### Post by djacidjac on 2008-09-24
I had a similar problem; no changes to "Login Window" would save. I deleted /etc/gdm/gdm.conf-custom and then made a copy of /etc/gdm/gdm.conf named gdm.conf-custom. Everything works in "Login Window" now. Just remember that any changes you made in the past will be gone and you'll be left with the default settings.

This took me a while to figure out. I hope this helps.

---

