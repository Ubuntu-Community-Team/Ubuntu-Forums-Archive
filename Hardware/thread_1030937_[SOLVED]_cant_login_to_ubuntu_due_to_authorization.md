---
title: "[SOLVED] cant login to ubuntu due to authorization&amp;quot;acess denied&amp;quot; error"
date: 2009-01-04
forum: Hardware
---

### Post by thingy87654321 on 2009-01-04
i have a toshiba satellite m45-s351 laptop with a 1.73ghz processor and 1024 mb of ram running ubuntu 8.04 hardy heron edition with all updates installed

i powered on my ubuntu laptop this morning, i booted properly, went to the login screen, i was able to enter my username and password, but when i pressed enter to login a error message poped up saying "unable to write to home directory authorization file, this may be caused by being out of space"
it has a details thingy and on the details thingy it says "access denied"

i booted up a live cd of kubuntu 8.10 to see if i was out of space, no, i had 13 gigs of free space left,
i tried deleting some of the files from the documents file but it said "access denied", i have the harddrive with ubuntu 8.04 on my desk intill i find out how to fix it, i am running ubuntu 8.10 on a differnet harddrive that i installed in my laptop shortly after getting tried of trying to figure out what is wrong. i dont want to reinstall but if i have too, i will, i have a 8 gig sdhc memory card and a sd card slot on my laptop so if i have too, i will back up my music and videos, and files, and downloaded things onto my sd and reinstall ubuntu 8.04,(that is if i cant recover the files when i reinstall my os using the ubuntu update thingy on the installation guide) and copy the files, but i really think you guys could figure out what is wrong.

thankyou,
christopher ryan aouate
thingy87654321

---

### Post by pytheas22 on 2009-01-04
The first thing to try in this situation is to see if logging in under a new user account would work.  To create a new user, press control-alt-F2 at the Gnome login screen.  This will bring you to a command prompt.  Log in there using your original account.  Then run this command:
```

sudo adduser testuser
```

Answer the questions on the screen to set a password for the new account.  Then press control-alt-F7 to get back to the Gnome login screen, and try logging in with username 'testuser' and the password that you just set.  Does this work?  If so, fixing your real user account should be pretty easy (I'll give instructions for doing that once we think that it will work).

---

### Post by thingy87654321 on 2009-01-04
i will test it right now

---

### Post by thingy87654321 on 2009-01-04
i tried making a new account but when i entered sudo adduser testuser, it said "must be setuid root", it happens when you enter sudo, or sudo su
any suggestions?

---

### Post by pytheas22 on 2009-01-04
That's weird.  Usually you get that message if the program 'sudo' has misconfigured permissions.  But it's strange for its permissions to go awry suddenly.  I hope this isn't part of a wider problem with your system.

Anyway, to fix the issue, try running these commands, which should restore sudo normal:

```
chown root:root /usr/bin/sudo
chmod 4755 /usr/bin/sudo
```

Then reboot.  After the reboot, try creating a new user again.  Do you still get the same error message?  If not, can you log in using the new user account?

Also, I may not be able to reply again till tomorrow...

---

### Post by thingy87654321 on 2009-01-05
i will try that

---

### Post by thingy87654321 on 2009-01-05
i tried it and i get this

chown: changing ownership of usr/bin/sudo operation not perrmited

chmod: changing ownership of usr/bin/sudo operation not perrmited

if this is telling you that this is a problem that would be difficult to, i could just transfer all the file to my ubuntu 8.10 harddrive, i like ubuntu 8.04 more because skype wont work with my audio harddware properly and i just am used to have ubuntu 8.04

i will reinstall ubuntu 8.04 if i really have but i cant find my ubuntu 8.04 disk i orderd, i found ubuntu 8.10, kubuntu 8.04, kubuntu 8.10 and ubuntu 8.04 64 bit edition, but i cant find any of my ubuntu 8.04 edition disks and really dont want to download it,  i dont think that ubuntu.com is still sending out the ubuntu 8.04 disks.

---

### Post by albinootje on 2009-01-05
> **thingy87654321 said:**
> i tried it and i get this

chown: changing ownership of usr/bin/sudo operation not perrmited

chmod: changing ownership of usr/bin/sudo operation not perrmited


Please boot with the "recovery mode", and try again.

---

### Post by thingy87654321 on 2009-01-05
i will try that then post the results

---

### Post by thingy87654321 on 2009-01-05
i tried that, i was able to make a new account, but...
i tried loging in to my new account and got this
(this is only the first and last line, that was all i could get)

/etc/gdm/xsession: beggining session setup
mkdtemp: private socket dir: permission denied

is it fixable?
without a reinstall?
without losing my files?

---

### Post by albinootje on 2009-01-05
> **thingy87654321 said:**
>  /etc/gdm/xsession: beggining session setup
mkdtemp: private socket dir: permission denied


Can you boot in recovery mode again, choose "drop to root shell prompt" and do the following :
```

chmod 755 /home
chmod 1777 /tmp
chown -R testuser:testuser /home/testuser
chown -R olduser:olduser /home/olduser
telinit 2

```
Where olduser is your old username, and testuser is your new username.

---

### Post by thingy87654321 on 2009-01-05
so it would be this

chmod 755 /home
chmod 1777 /tmp
chown -R testuser:testuser /home/testuser
chown -R chris:chris /home/chris
telinit 2

entered one line at a time?

---

### Post by albinootje on 2009-01-05
> **thingy87654321 said:**
> so it would be this

chmod 755 /home
chmod 1777 /tmp
chown -R testuser:testuser /home/testuser
chown -R chris:chris /home/chris
telinit 2

entered one line at a time?

Yes, press <enter> after each line.

---

### Post by thingy87654321 on 2009-01-05
i tried it, i was able to login, but it came up with thousands of error messages and the panels were missing and it would not mount any media

i am going to reinstall, i am tired of trying to fix it


thanks for all your help

---

### Post by thingy87654321 on 2009-01-06
if there is a quick way to restore ubuntu to before all this happened, or to get the panels back and the error messages to go away please tell me, i would rather now reinstall

---

### Post by pytheas22 on 2009-01-06
Unfortunately there's no automatic 'go-back' feature in Ubuntu.

If you could post the specific error messages that you get when you try to log in, that may help us to fix your existing system.  But at this point it may be simpler just to reinstall...it would only take half-an-hour, after all.  If you need to back up your data and can't mount removable media from the existing system, you should still be able to do it from the live CD.

If you reinstall, you may want to consider putting [/home on a separate partition]("ww.psychocats.net/ubuntu/separatehome"), to make future reinstallations easier.

---

### Post by thingy87654321 on 2009-01-06
ok, i will reinstall, but how would i put the /home folder on a seperate partition, i know how to partition the drive, but how would i move the /home folder to a seperate partition?

---

### Post by pytheas22 on 2009-01-06
First, backup the current contents of your /home directory to an external disk drive or DVD.  Then reinstall Ubuntu, creating a separate partition for /home as explained on [this page]("http://ww.psychocats.net/ubuntu/separatehome").

After Ubuntu is reinstalled, you can simply copy your backed-up home-folder over the new one.  This should restore all of your data and settings.  There will most likely also be permissions issues that will prevent you from logging in at first, but we can straighten out those problems when you get to that point.

---

### Post by thingy87654321 on 2009-01-06
ohh ok,i see, thanks alot dude

---

### Post by thingy87654321 on 2009-01-06
what does you picture say pytheas22

---

### Post by pytheas22 on 2009-01-06
> what does you picture say

'Nous sommes le pouvoir', or 'The power is us'...from the protests in Paris in 1968.  I thought it was a nice analogy for Ubuntu, since the power is the community, not an elite working for Microsoft and Apple.

Let us know how you get on with the reinstall.  As I mentioned, you will probably need to deal with readjusting some permissions on your new /home directory before everything works smoothly again.

---

### Post by thingy87654321 on 2009-01-07
that is cool

---

### Post by thingy87654321 on 2009-01-07
could i install grub bootloader than install ubuntu and windows and make it so i can choose which to boot,without the windows boot manager?
and how would i make windows appear on the grub bootloader?

---

### Post by pytheas22 on 2009-01-07
> could i install grub bootloader than install ubuntu and windows and make it so i can choose which to boot,without the windows boot manager?
and how would i make windows appear on the grub bootloader?

Yes, this should be what the installer on the live CD will do by default.  It will automatically create an option in grub to boot to Windows, as well as Ubuntu.  The fact of having /home on a separate partition won't affect grub in any way.

If you're using wubi to install Ubuntu, that's a different story, but you're using the CD, correct?

---

### Post by thingy87654321 on 2009-01-07
sweet, thanks

---

