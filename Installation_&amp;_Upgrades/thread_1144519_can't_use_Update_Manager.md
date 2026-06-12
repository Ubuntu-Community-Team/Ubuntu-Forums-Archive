---
title: "can't use Update Manager"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by disx on 2009-04-30
i just installed ubuntu today. i'm new to linux entirely. i did the inside windows install cos i can't get my stupid mobo to boot from CD. anyway, there were what, 300 updates after i first installed? so i started downloading them all and somewhere along the way it screwed up, i don't remember what it said and now the update manager icon has that ohno explosion style to it and if i leave the cursor over it it says, 'a problem occurred when checking for the updates.' but if i double click the icon, the update manager pops up for a second then goes away before i can do anything. so basically i just can't access the update manager at all. i've tried right-clicking the icon and using the different options there, nothing helps.

i went to terminal and tried a few commands i saw reccommended on other threads like,

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f

the first one i did was update and it did this:

disx0d@ubuntu:~$ sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
Segmentation faultsts... 0%


every other command just gives me that last line.
i don't know what it means.


any ideas? oh, when i installed, i did the 8.whatever version, whatever was previous to this 9.04 release of Jaunty. upgrading to that was an option on my update manager when i could access it before and i was going to do that after the updates (should i have done that straight away?) but now i have no access to UM.

thanks!

---

### Post by theozzlives on 2009-04-30
Have you tried System > Administration > Update Manager?

---

### Post by disx on 2009-04-30
yeah, sorry i should have stated that in my first post. i tried that and it does the same thing. a window pops up like hey i'm the update manager and then just goes away before i can do anything. =/

---

### Post by disx on 2009-05-01
so since i had just installed ubuntu and didn't have anything going yet really and couldn't get this problem resolved i decided to just go ahead and uninstall it and re-install it. tried doing the update again and it worked fine. i think last time i tried to upgrade to 9.04 too or something, i don't remember exactly, but i'll just stay away from jaunty for now until i get the hang of my current version.

---

