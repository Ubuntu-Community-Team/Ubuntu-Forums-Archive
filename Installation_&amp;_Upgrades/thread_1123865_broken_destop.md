---
title: "broken destop"
date: 2009-04-12
forum: Installation &amp; Upgrades
---

### Post by dcates1 on 2009-04-12
I need to ask for some help as I'm an absolute novice at Ubuntu.

I was sure that I did this by loading something that I should not have.
The error I got was

"Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager."

I could not use most of the pulldown menu options becuse of this.

So I completely reloaded Ubuntu from the setup disk and everything worked just fine, then I clicked on the auto update icon and let it apply the updates. When it said to restart I let it. Now the desktop is broken again, with the same error.

If I  remember correctly this happened the first time right after an update. But I had been messing with stuff and didn't connect the two. 

Many thanks for any help you can give me.

Dan

---

### Post by tommcd on 2009-04-12
What version of Ubuntu are you using? Are you using Gnome or KDE?
If using Gnome, boot to recovery mode. Then run:
```
sudo mv /home/your_user_name/.gnome2 /home/your_user_name/.gnome2.bak
```
Then reboot. This will create a new .gnome2 directory with the default settings. If this doesn't clear up the problem, boot to recovery mode again and run:
```
sudo apt-get install --reinstall ubuntu-desktop
```
This only applies if you use gnome.

---

### Post by dcates1 on 2009-04-12
I'm using 8.10  with the standard gnome desktop. I'll give these suggetions a try. 

Thanks Dan

---

### Post by dcates1 on 2009-04-13
I tried these fix's but didn't change anything, still not working.

 Was there a particular update that shouldn't have loaded? 

If so can some one tell what it was so i can by pass it.( there were 297 updates for the initial install)

---

### Post by tommcd on 2009-04-13
There was a bug report about this. It was supposed to have been "fixed" with an update somewhere along the line:
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/272093](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/272093)
As a possible work around, try opening a terminal and run:
```
gnome-settings-daemon
```
and see if that gets your desktop back in order. If you can't open the applications > accessories menu, then hit alt + F2 and enter gnome-settings-daemon there and hit enter.
Another possible fix is described in post #15 of this thread:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=955679](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=955679)
That thread may be a bit out of date for this issue; but you could try it if nothing else works. Undo that fix if it does not help.

---

