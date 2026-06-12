---
title: "!HELP! Ubuntu Won't Update or Install Anything!!!!!!!!!!"
date: 2008-11-26
forum: General Help
---

### Post by DizzyEwok on 2008-11-26
Hi this is my first post but i have been using ubuntu for about 6 months. 
Currently i am using Hardy.
My problem is that when I try to update ubuntu or install any program through terminal these errors appear:
Installing Through Terminal:

Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing btnx (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

And for the updating:

An error occured, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong.
The error message was: 'Error opening the cache (E:Problem parsing dependency depends, E:Error occurred while processing btnx (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.)' THis usually means that your installed packages may have unmet dependencies


I have tried everything I know(not much)!And have tried everything that it lists in the error message.

Anyone have a solution????????
Thanks

---

### Post by icanfly0307 on 2008-11-26
Have you tried [FONT="Courier New"]sudo apt-get install update[/FONT]? That should refresh the repos list and fix your problem.

---

### Post by philinux on 2008-11-26
I would try removing the app.

sudo apt-get remove btnx

---

### Post by DizzyEwok on 2008-11-26
> **icanfly0307 said:**
> Have you tried [FONT="Courier New"]sudo apt-get install update[/FONT]? That should refresh the repos list and fix your problem.

Did not work and neither did the 1 above. It came up with the same error message as when i try to install stuff!
Thx for the suggestion though

---

### Post by philinux on 2008-11-26
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/282932](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/282932)

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/283541](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/283541)

---

### Post by DizzyEwok on 2008-11-26
> **philinux said:**
> [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/282932](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/282932)

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/283541](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/283541)

I have looked at both links, the 1st link does not give any real answer because i have no 3rd party software(I checked).
The 2nd link May work but I do not know what to do......

---

### Post by linux_tech on 2008-11-26
What does your sources.list look like?
```
sudo nano /etc/apt/sources.list
```

---

### Post by DizzyEwok on 2008-11-26
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main re$
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe

---

### Post by oldos2er on 2008-11-26
You said you're using Hardy, but your sparse menu.list says Gutsy. Which is correct?

---

### Post by DizzyEwok on 2008-11-26
> **oldos2er said:**
> You said you're using Hardy, but your sparse menu.list says Gutsy. Which is correct?

I believe I am using Hardy, when I first installed Ubuntu i installed the Gutsy CD but then It said that I could update to Hardy so I did, It took about 1 hour to update which is longer than a normal update....

---

### Post by philinux on 2008-11-26
What does this give.

 lsb_release -a

---

### Post by DizzyEwok on 2008-11-26
Sorry, I can't help you. I know hardly any ubuntu code. Im a java programmer(beginner). Why do you know?

---

### Post by philinux on 2008-11-26
> **DizzyEwok said:**
> Sorry, I can't help you. I know hardly any ubuntu code. Im a java programmer(beginner). Why do you know?

Applications>Accessories>Terminal 

copy and paste the code

lsb_release -a

Post back the output

---

### Post by DizzyEwok on 2008-11-26
> **philinux said:**
> Applications>Accessories>Terminal 

copy and paste the code

lsb_release -a

Post back the output

KK:
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04
Release:	8.04
Codename:	hardy

---

### Post by linux_tech on 2008-11-27
The sources.list did not get upgraded properly--we're you able to fix this yet?

---

### Post by DizzyEwok on 2008-11-27
> **linux_tech said:**
> The sources.list did not get upgraded properly--we're you able to fix this yet?
Fix it!!!??? I wouldn't be able to fix it if I asked for help in the 1st place!!As I said I hardly know anything.....If you could post what I need 2 change then I would be very grateful!
Thanks

---

