---
title: "[SOLVED] Nothing happens after login"
date: 2008-08-07
forum: General Help
---

### Post by Crowchild on 2008-08-07
Help! When I try to login I type my name and password and then get a blanks screen with a mouse pointer and nothing more. I tried reverting to a back up xorg.conf but that didn't help.

---

### Post by overdrank on 2008-08-07
> **Crowchild said:**
> Help! When I try to login I type my name and password and then get a blanks screen with a mouse pointer and nothing more. I tried reverting to a back up xorg.conf but that didn't help.

Hi and can you tell us what model of graphics card, Did you recently update your system or anything before this issue?

---

### Post by tuxxy on 2008-08-07
Did you recently edit any video settings? if you can pull up a terminal by pressing CTRL + ALT + F1 then you could try reconfigure the xorg now by entering

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Crowchild on 2008-08-07
I have a Nvidia graphics card. I've tried "sudo dpkg-reconfigure xserver-xorg"

---

### Post by overdrank on 2008-08-07
> **Crowchild said:**
> I have a Nvidia graphics card. I've tried "sudo dpkg-reconfigure xserver-xorg"

Ok a little more info would help. What is the model? What version of ubuntu are you using, Hardy, Gutsy? Where you using compiz (desktop effects)

---

### Post by tuxxy on 2008-08-07
Have you tried

```
startx
```

---

### Post by Crowchild on 2008-08-07
When I typed startx I get:> 
Fatal server error:
Server is already active for display 0
         If this server is no longer running, remove /tmp/X0.lock
         and start again.

So I removed the file and started X again. Now I have a black and white zig zag pattern for a back ground and I have a pointer. Nothing else.

---

### Post by Crowchild on 2008-08-07
> **overdrank said:**
> Ok a little more info would help. What is the model? What version of ubuntu are you using, Hardy, Gutsy? Where you using compiz (desktop effects)

 I am using Hardy. 
 I don't know how to tell what model I am using.
 I do have compiz.

---

### Post by tuxxy on 2008-08-07
Try reconfigure xorg again now

---

### Post by Crowchild on 2008-08-07
> **tuxxy said:**
> Try reconfigure xorg again now

Didn't help.

---

### Post by tuxxy on 2008-08-07
Is this the same issues?

[http://ubuntuforums.org/showthread.php?t=882803](http://ubuntuforums.org/showthread.php?t=882803)

---

### Post by ElCubano07 on 2008-08-07
I am having the same issue.  After waiting a while I get an error message saying that the Gnome Settings Daemon is not responding and that my themes, backgrounds, etc... are not available.  However, I am able to use Gnome.  This started happening after an update this morning.  Not sure what packages were updated though; I'll try to figure it out and repost.

Hardy 8.04
NVidia 8800 GTS

---

### Post by overdrank on 2008-08-07
Try booting into recovery mode and using the xfix option. Hopefully this will correct the issue.

---

### Post by Crowchild on 2008-08-07
> **tuxxy said:**
> Is this the same issues?

[http://ubuntuforums.org/showthread.php?t=882803](http://ubuntuforums.org/showthread.php?t=882803)

Yeah. This worked great. Sorry for taking up your time when there was a solution out there. I just couldn't find it.

Thank you!

---

