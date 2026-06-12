---
title: "xubuntu addon cd - why not? a quick dirty howto this is"
date: 2005-12-10
forum: Installation &amp; Upgrades
---

### Post by towsonu2003 on 2005-12-10
hi,
I'm not sure whether this is the right place to post this. I looked around for another similar post, but it was no where to find (bad keywords??). 
I wanted to suggest a addon CD iso file, in the form of a repository, for those who want to install xubuntu. 

The howto for this CD would be very simple. 

1. Find a spare computer
2. install ubuntu in server mode (boot:server for install CD) Step # 5 & 6 has to be done in this server-setup computer to deal with #$% dependencies.
3. Configure network
4. Uncomment repos under /etc/apt/sources.list
5. Run ```
sudo apt-get clean
sudo apt-get -d install xubuntu-desktop
``` -d for download only (which means, apt-get wont install xubuntu)
6. Copy all .deb files under /var/cache/apt/archives/ to a local folder ```
mkdir ~/xubuntu
cp /var/cache/apt/archives/*.deb ~/xubuntu
``` **NOTE**: not sure about cp command there, be careful- (I confess, I used nautilus for that copying... ;) )
7. Follow this howto ( [http://ubuntuforums.org/showthread.php?t=42862](http://ubuntuforums.org/showthread.php?t=42862) ) till end of step four to turn ~/xubuntu into a local repository
---
At this stage, you can apt-get ubuntu-desktop from install CD to server-setup computer if you need X to do the rest
---
8. Burn ~/xubuntu to a cd / make it a .iso
9. Change /etc/apt/sources.list on server install computer by following this howto ( [http://ubuntuforums.org/showthread.php?t=42862](http://ubuntuforums.org/showthread.php?t=42862) ) from step 5 onwards /// After mounting CD, the path will be file:///media/cdrom/ xubuntu/
10. Test on server install computer by doing ```
sudo apt-get install xubuntu-desktop
```

I would do this myself but I do not have spare computer with internet access.  Tried it with spare very old computer which does not have internet access by using this computer to build repo, but dependencies were not resolved as this computer (where I built repo) included gnome install + whoknowswhat => not enough packages were 'apt-getted' in step 5 in this howto....

11. Put .iso to a server and we will download & use with joy :)

NOTES: 
a) Please do not expect me to update this howto much, because I will not be able to test suggestions almost at all... If you succeed coming up with a successful CD .iso, write a howto on installing xubuntu using your .iso to the appropriate forum at [http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)
b) I may be able to test your .iso file in my spare computer, but I have DIAL UP network....... and I have no idea how big the .iso will be :)
c) I am assuming you are not a complete newbie :) (I am)
d) **let us know** if you succeed :)

---

### Post by towsonu2003 on 2005-12-19
did anyone tried this? sorry to bump :)

---

### Post by az on 2005-12-19
I did it using
[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

---

### Post by towsonu2003 on 2005-12-20
[QUOTE=azz]I did it using
[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)[/QUOTE]

looks much easier :) -bookmarked for future use-

any reason the (any) xubuntu iso file isn't distributed (copyright or something else?)?

---

### Post by az on 2005-12-20
[QUOTE=towsonu2003]looks much easier :) -bookmarked for future use-

any reason the (any) xubuntu iso file isn't distributed (copyright or something else?)?[/QUOTE]
"Release early, release often."


They have not made one yet.

---

### Post by petervk on 2006-01-06
If your computer is fast enough you can just install VMware Player and install ubuntu server into that.

[http://johnbokma.com/mexit/2005/11/07/vmware-player-ubuntu-installation.html]("http://johnbokma.com/mexit/2005/11/07/vmware-player-ubuntu-installation.html")

You'll need ~2G of free space, and just don't run anything else on your computer while VMware is operating.

---

### Post by mohapi on 2006-01-09
Hello everyone. I wanted to post a success story for this thread. I managed to install Xubuntu on an ancient CTX laptop (128MB/2GB/475Mhz) without an Internet connection, in hopes of bringing up the wireless after getting some sort of GUI in place.

I suppose it goes without saying that I have next-to-nothing for Linux experience. And without going into too many details, suffice to say that straight Ubuntu and Kubuntu installations crapped out in mid-install, along the lines of [this]("http://www.ubuntuforums.org/showthread.php?t=103104"). I even tried Drake versions, but met with no success.

I managed to muddle my way through the steps in this thread, with a couple of variations. I used VMWare WorkStation to test and download the Xubuntu files. VMWare has presets for Ubuntu installations, and is free under a 30-day trial. (You have to give them some info, though.)

After a server install, I did

```
sudo apt-get update

```
but _**NOT**_ *sudo apt-get upgrade*. Don't ask me why; I had it in my mind that upgraded files might conflict with the basic server install I had waiting on the laptop. Then

```
sudo apt-get clean
```

just to be safe, then 

```
sudo apt-get -d install xubuntu-desktop
```

Then copied the downloaded packages into a folder called xubuntu-desktop in my home directory with

```
cd ~
mkdir xubuntu-desktop
cp /var/cache/apt/archives/*.deb ~/xubuntu-desktop/
```

After that, things became a little less graceful. I followed [this thread]("http://ubuntuforums.org/showthread.php?t=42862") for turning those files into a repository, through step four, but stopping before step five.

Then I did

```
sudo apt-get clean
sudo apt-get install ubuntu-desktop
```

but the only reason for the second command was my own ignorance on creating an ISO without a GUI and Gnomebaker. :confused: Perhaps you know a better way.

After Ubuntu installed (and still inside WorkStation), I created an ISO of the files on a USB key so I could keep them off the simulated drives in WorkStation. 

Dropping back into Windows, I burned the ISO and moved put the CD into the ancient laptop, where I had already finished a server install. I did NOT modify the sources.list file, but instead did

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```

for a backup, just for safety's sake. Then 

```
sudo apt-cdrom add
```

and gave it the name 'xubuntu-desktop'. Unless I'm mistaken, that adds the mounted CD to the sources.list file for you. Then

```
sudo apt-get install xubuntu-desktop
```

I answered yes to the subsequent messages, and after about an hour and a half of building, setting up and configuring, I had the lovely blue XFCE desktop. :cool:

As I mentioned earlier, I'm very new to Ubuntu and Linux, and I'm sure there are more elegant and more effective ways of getting this done. But this one worked for me, and if you're in the same boat, it might work for you.

Next stop: Getting the doggone wireless going! :shock:

Cheers!

[SIZE="1"]----------
(Edited for a small typo in one of the code sections.)[/SIZE]

---

### Post by towsonu2003 on 2006-01-09
hey very nice! good luck with the wireless :)

---

### Post by mohapi on 2006-01-09
[QUOTE=towsonu2003]hey very nice! good luck with the wireless :)[/QUOTE]

Thanks! I'm going to need it. It seems I have that WPC54G version 2 that stumps everyone. Sigh. :???:

---

### Post by John.Michael.Kane on 2006-03-01
mohapi WPC54G version 2=Linksys Notebook Adapter which you might have to use ndiswrapper to get the drivers for it to work..

---

### Post by majikstreet on 2006-03-02
ok - I will give you a short command line way to make an iso (hopefully it will do!)

get all your files into a folder
then do
```

mkisofs -r -R -J -l -o whatever.iso /home/username/folder

```
I haven't tested the resulting iso, but the command works for me :D

---

### Post by DIEDIE on 2006-04-14
Hello,  i'm new here and from europ so sorry if i type fome folds.

I'm stuk with this command:
sudo apt-get -d install xubuntu-desktop 
i get this respons:
Reading package lists...Done
Building dependency traa...Done
E: Coulden't find package xubuntu-desktop
What can i do?


edit: i't a install without internet on mij portable PII 500 mhz
Thx for the respons

---

### Post by az on 2006-04-14
[QUOTE=DIEDIE]Hello,  i'm new here and from europ so sorry if i type fome folds.

I'm stuk with this command:
sudo apt-get -d install xubuntu-desktop 
i get this respons:
Reading package lists...Done
Building dependency traa...Done
E: Coulden't find package xubuntu-desktop
What can i do?


edit: i't a install without internet on mij portable PII 500 mhz
Thx for the respons[/QUOTE]

"4. Uncomment repos under /etc/apt/sources.list"

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

You need to enable universe.

---

### Post by oneyoudontknow on 2006-06-16
[QUOTE=azz]"4. Uncomment repos under /etc/apt/sources.list"

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

You need to enable universe.[/QUOTE]

no this does not work at my Laptop. I am not able to create any directory.

---

