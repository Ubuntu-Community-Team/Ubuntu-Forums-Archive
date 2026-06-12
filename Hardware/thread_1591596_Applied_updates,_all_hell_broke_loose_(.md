---
title: "Applied updates, all hell broke loose :("
date: 2010-10-09
forum: Hardware
---

### Post by pyromidget on 2010-10-09
Hey all, really hoping someone can shed some light.  I've tried running searches through the forum, but nothing really comes up.

My Internet connection can be quite intermittent, so i tend to update my computer sporadically.  Last night was one of the times when the connection was fairly reliable, so i fired up update manager, went to bed and rebooted this morning.  I'll hold my hands up and say i didn't actually check which updates were being applied, but I'd never run into problems before.

Now I'm having all manner of problems, and there've been a lot of changes to my UI that I didn't make myself:

I now need to input my password when i boot, whereas before it was only on a screen lock that i had to.  All the icons / menus have changed size on me, and there appear to be added desktop effects.  I can't mount any external storage - i keep getting messages saying "unable to mount 1TB filesystem - Not authorized".  Plus, my speakers seem to have stopped working.  I can still change the volume, but nothing comes out regardless.

I'm using an acer aspire one 250D with UNR 10.04, and i really hope someone can help me out with this.  I'm not a complete newbie, but i'm not an expert either, and i'm totally stumped :(

EDIT:  Oh, and i've just realised i can't use the 'unlock' button in some dialogue to allow editing.  i click it, and nothing happens.

EDIT 2:  And when i open a terminal, it defaults the path to: /usr/share/icons/Humanity/emblems/48

This is getting stranger by the minute! :(

---

### Post by solar george on 2010-10-09
That sounds very, very odd. I can't imagine what kind of updates would have caused some of those changes (esp. the path one) even if they were seriously mucked up, however the file system mounting and unlock button ones are probably related to a damaged policykit install.
Of course I wouldn't expect that kind of breakage from an ordinary package update, only if something had interrupted the update part way through (you did check it had finished before rebooting didn't you?)
Just on the off-chance it helps try running;
```
sudo apt-get -f install
```
and rebooting. However I have to say that I would be inclined to recommend a fresh install in your case, while it is probably possible to fix any damage it may be less hassle to start from scratch.

---

### Post by pyromidget on 2010-10-09
Thanks for the advice.  Everything was definately finished when i got up this morning - was just sitting at the "Reboot required" box.

Tried updating again, no success:

```
martin@martin-laptop:/usr/share/icons/Humanity/emblems/48$ sudo apt-get -f install
[sudo] password for martin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
martin@martin-laptop:/usr/share/icons/Humanity/emblems/48$ 
```

I can understand updates messing up sound / permissions etc, even if its rare.  The bit that confuses me the most are the cosmetic changes, as i can't think of any update that would alter fon/icon sizes etc :confused:

I'm loathe to try a fresh install, as without being to access external storage, I can't back up the hundred-odd gig of media i've downloaded recently.  Hell, even if i did want to try one i'm stuck as i can't format a USB stick...

---

### Post by solar george on 2010-10-09
Just to check - you're not running a vnc server or ssh server on your laptop are you? Would you say that you have a strong password? There's not anyone around who might try and muck around with your computer and muck stuff up through a lack of understanding?

---

### Post by pyromidget on 2010-10-09
Neither, and i really doubt it - the only other people i live with are windows users and have no concept of Linux at all.  I'd say its a fairly secure password considering there's nothing sensitive - 9 digit random alphanumeric...

---

### Post by solar george on 2010-10-09
OK, just wanted to make sure. Can you create a new user and login as them to see if the changes are just in your settings or if the theme files themselves are corrupted.

---

### Post by pyromidget on 2010-10-09
the users & groups dialogue will open, but none of the buttons work :(

---

### Post by solar george on 2010-10-09
Try from the command line;
```

sudo adduser testuser
sudo passwd testuser

```

---

### Post by pyromidget on 2010-10-09
done,all the same issues apply, and also the "unable to mount..." box was present when i switched back to my normal user.

Thank you for the help, by the way - really appreciated.

---

### Post by solar george on 2010-10-10
Well it looks like for some reason you've got corrupted packages installed (very odd thing to happen). AFAIK that leaves you with two choices, 
1. reinstall (there are ways you can do this from your position even without loosing the media you've downloaded)
2. try and work out which packages are damaged and reinstall them. This would be quite a long process and there's no guarantee you'll get everything fixed.

---

### Post by pyromidget on 2010-10-10
Well I'm downloading the 10.10 upgrade just now (at all of 37.0 kB/s!) so if nothing's sorted after that I'll look into a fresh install.  Hopefully it won't be too hard to keep all my media - it'd be a real pain to have to get it all again.  I tried transferring it all over to a windows partition that's went unused since i got the netbook, but i'm just getting the same "Can't mount...Not authorized" error. :(

---

### Post by solar george on 2010-10-11
You should be able to mount the partition if you launch nautilus (the file manager) as root.
**ONLY** do this while your install is mucked up and double check everything you are doing while you have nautilus running as root because this bypasses all of the protections which normally stop you from deleting essential files.
You can launch nautilus as root by running (either in the terminal or the run dialog)
```
gksudo nautilus
```

---

### Post by pyromidget on 2010-10-11
Woop woop.  Whatever the problem was, the 10.0 upgrade seems to have fixed everything :)

Not sure i like the new interface though...

---

