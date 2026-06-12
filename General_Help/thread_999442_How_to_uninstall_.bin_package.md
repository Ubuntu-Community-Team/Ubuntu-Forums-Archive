---
title: "How to uninstall .bin package?"
date: 2008-12-01
forum: General Help
---

### Post by kulturloseramerikaner on 2008-12-01
I installed Google Earth from their site, and ran it OK the first time.  The only option for a 'nix install is a .bin, which I installed fine.  However, the first time I fired up Google Earth, it informed me there were updates available and took me to another site where I downloaded another .bin. 
After installing the upgrade, I'm having nothing but issues.  The server will not connect and now presents me with a black screen.  I don't have a list of layers I can apply in the sidebar as I did before.  There aren't any navigation tools.  It's basically worthless.
I'd like to uninstall both packages and reinstall, but I'm not sure how to uninstall something from a .bin.  What's the procedure for that please?

---

### Post by tuxxy on 2008-12-01
.bin's have uninstallers packaged with them, If you navigate to the googleearth directory there should be a subdirectory or file named something like ./uninstaller which you can run

---

### Post by kulturloseramerikaner on 2008-12-01
```
brian@HAL:~$ sudo chmod 755 /opt/google-earth/uninstall
[sudo] password for brian: 
brian@HAL:~$ cd /opt/google-earth/
brian@HAL:/opt/google-earth$ ./uninstall
Could not find a usable uninstall program. Aborting.
brian@HAL:/opt/google-earth$ 


```
(SIGH)
Is there a hard way?

---

### Post by oldos2er on 2008-12-01
sudo /opt/google-earth/uninstall

---

### Post by kulturloseramerikaner on 2008-12-01
Same error.

---

### Post by oldos2er on 2008-12-01
Why did you change the permissions of /opt/google-earth/uninstall ?

---

### Post by kulturloseramerikaner on 2008-12-01
I had to chmod the install script to run it; it wouldn't run otherwise.  When the uninstall failed the first time I figured the same thing was going on.

---

### Post by kulturloseramerikaner on 2008-12-03
Well, I got sick of trying to mess with it.  I upgraded the drive 'buntu sits on to a 500GB only 2 weeks ago and still have the first 160GB, so  I just recloned it with Clonezilla, reupdated, and reinstalled the newer .bin.  So as a word of warning, the uninstall script for Google Earth doesn't work, make sure you get the new version...

---

### Post by kulturloseramerikaner on 2008-12-03
Another update...
The latest google earth package doesn't seem to work at all.  You can connect just fine right after the install, but close and reopen, and you get nothing; the server won't connect. Is anyone else having this problem?
I'm running Firestarter, and am wondering if this could have something to do with the issue...

---

### Post by kulturloseramerikaner on 2008-12-03
Newest update:
Running the command ```
sudo googleearth
``` from terminal allowed me to run it!  I'm not sure why it needs root privileges, but it works well.  I don't like the idea of being logged in as root for the long periods of time I use it though; I'm looking at what can be done...

---

### Post by deadowl on 2008-12-03
You can install it as .deb from the medibuntu repositories.

---

### Post by kulturloseramerikaner on 2008-12-09
At the time I tried the repos it was the old version.  I like the navigation in the new one better so I tried the upgrade.

---

### Post by Ayuthia on 2008-12-09
Where is the googleearth application:
```
which googleearth
```It sounds like it does not have the right permissions set or else it is in a directory where the permissions don't allow you to run it without admin privileges.

---

### Post by kulturloseramerikaner on 2008-12-12
I got it working as a normal user; pardon my taking so long to call this solved.
What you want to do after installing is run:
```
sudo chown -R user:usergroup .config/Google
```  It'll kick out a couple of error messages that I didn't catch, but afterwards you can open a terminal as a normal user and just run 
```
googleearth
```
and you're off...

---

### Post by Mickeyj4j on 2009-10-06
> **kulturloseramerikaner said:**
> I installed Google Earth from their site, and ran it OK the first time.  The only option for a 'nix install is a .bin, which I installed fine.

the only thing to do is look in mint install and you will now find it in there

 
:KS :guitar: :lolflag: :popcorn: :KS

---

