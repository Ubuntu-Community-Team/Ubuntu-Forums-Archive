---
title: "Need Touchpad Help!"
date: 2011-05-19
forum: Hardware
---

### Post by andddlay on 2011-05-19
Hello all!

I'm having trouble getting my touchpad of my Samsung Series 9 laptop to function properly again.  Here's what happened.  To see if I could get the touchpad to work better with Linux, I found this code and tried it out:

> sudo su
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
reboot

After the reboot, my laptop told me that there was no touchpad found (it still tells me this).  I do kinda like how the right click works now, but ultimately I'd like to undo these changes.  Could somebody please help me do this? 

Thanks :D

---

### Post by andddlay on 2011-05-20
Could somebody please help me?  Also, I dunno if this is related, but also I can't install/remove applications properly.

---

### Post by andddlay on 2011-05-22
Still lookin for help :o I'd like to not have to reinstall kubuntu.

---

### Post by andddlay on 2011-05-23
Still looking for help...

---

### Post by Zorael on 2011-05-30
```
sudo su
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
reboot
```
This creates a file at **/etc/modprobe.d/psmouse.modprobe** with the contents '**options psmouse proto=exps**'. Undoing it should be as simple as removing that file.
```
$ sudo rm /etc/modprobe.d/psmouse.modprobe
```
What functionality did you want to achieve with this?

Also, this should not cause any issues when installing stuff.

---

### Post by tarahmarie on 2011-07-01
bump; I need this option set in psmouse.modprobe to get right-clicking to work, but I can also now (just like the OP) no longer see my touchpad detected in options.

[http://ubuntuforums.org/showthread.php?t=1737086](http://ubuntuforums.org/showthread.php?t=1737086)

That's where the code comes from that the OP used; I used it too to enable right clicking. 

Anyone have any ideas on how to enable BOTH right clicking and edge scrolling on a Samsung Series 9 in Kubuntu?

---

### Post by insession on 2011-11-29
mind passing it on if anybody figured out how to do this?

Edit: forgot to reboot, this did just fine:

```
sudo rm /etc/modprobe.d/psmouse.modprobe
```

---

