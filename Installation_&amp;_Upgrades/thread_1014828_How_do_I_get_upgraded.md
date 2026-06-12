---
title: "How do I get upgraded?"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by coffeecups on 2008-12-18
Hello, I've been using ubuntu feisty fawn for the last year or so and love it but now need to upgrade to 8.10 in order to use the usb dongle for mobile broadband, there is no other broadband available where I live, at the moment, and dial up is just painful!! Update manager only offers me update to 7.10 so thought maybe I have to go up to 8.10 in stages but when I clicked on upgrade I got this message
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-amd64/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-amd64/Packages.gz) 404 Not Found
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-amd64/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-amd64/Packages.gz) 404 Not Found
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz) 404 Not Found
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz) 404 Not Found
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-amd64/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-amd64/Packages.gz) 404 Not Found
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz) 404 Not Found
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-amd64/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-amd64/Packages.gz) 404 Not Found
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz) 404 Not Found

So tried
sue@sue-desktop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied) got a similar 'unable to lock' message when I ran apt-get autoclean
E: Could not open lock file /var/cache/apt/archives/lock - open (13 Permission denied)
E: Unable to lock the download directory

I am still such a newbie at all this and not sure what to do next? My computer has really begun to slow down lately and am not sure why as update manager tells me system is up to date! Any help, please!

---

### Post by gjoellee on 2008-12-18
> **coffeecups said:**
> Hello, I've been using ubuntu feisty fawn for the last year or so and love it but now need to upgrade to 8.10 in order to use the usb dongle for mobile broadband, there is no other broadband available where I live, at the moment, and dial up is just painful!! Update manager only offers me update to 7.10 so thought maybe I have to go up to 8.10 in stages but when I clicked on upgrade I got this message
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-amd64/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-amd64/Packages.gz) 404 Not Found
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-amd64/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-amd64/Packages.gz) 404 Not Found
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz) 404 Not Found
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz) 404 Not Found
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-amd64/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-amd64/Packages.gz) 404 Not Found
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz) 404 Not Found
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-amd64/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-amd64/Packages.gz) 404 Not Found
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz) 404 Not Found

So tried
sue@sue-desktop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied) got a similar 'unable to lock' message when I ran apt-get autoclean
E: Could not open lock file /var/cache/apt/archives/lock - open (13 Permission denied)
E: Unable to lock the download directory

I am still such a newbie at all this and not sure what to do next? My computer has really begun to slow down lately and am not sure why as update manager tells me system is up to date! Any help, please!

it is recommended to add the files you need to an external HDD/memorystick and then do a clean install of 8.10, you will in most cases get a lot of bugs if you do the net upgrades.

NOTE: "404" means that the page does not exist...may i see your sources.list?

```
sudo gedit /etc/apt/sources.list
```

---

### Post by lovelyvik293 on 2008-12-18
> **coffeecups said:**
> Hello, I've been using ubuntu feisty fawn for the last year or so and love it but now need to upgrade to 8.10 in order to use the usb dongle for mobile broadband, there is no other broadband available where I live, at the moment, and dial up is just painful!! Update manager only offers me update to 7.10 so thought maybe I have to go up to 8.10 in stages but when I clicked on upgrade I got this message
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-amd64/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-amd64/Packages.gz) 404 Not Found
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-amd64/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-amd64/Packages.gz) 404 Not Found
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz) 404 Not Found
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz) 404 Not Found
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-amd64/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-amd64/Packages.gz) 404 Not Found
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz) 404 Not Found
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-amd64/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-amd64/Packages.gz) 404 Not Found
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz) 404 Not Found

You can try to change the sever.In the Software sources.
If you are using any proxy server?
> 

sue@sue-desktop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied) got a similar 'unable to lock' message when I ran apt-get autoclean
E: Could not open lock file /var/cache/apt/archives/lock - open (13 Permission denied)
E: Unable to lock the download directory


I think you have two package managers like the synaptic and update manager working simultenously.

---

### Post by _noob_ on 2008-12-18
> **coffeecups said:**
> Hello, I've been using ubuntu feisty fawn for the last year or so and love it but now need to upgrade to 8.10 in order to use the usb dongle for mobile broadband, there is no other broadband available where I live, at the moment, and dial up is just painful!! Update manager only offers me update to 7.10 so thought maybe I have to go up to 8.10 in stages but when I clicked on upgrade I got this message
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-amd64/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-amd64/Packages.gz) 404 Not Found
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-amd64/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-amd64/Packages.gz) 404 Not Found
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz) 404 Not Found
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz) 404 Not Found
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-amd64/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-amd64/Packages.gz) 404 Not Found
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz) 404 Not Found
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-amd64/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-amd64/Packages.gz) 404 Not Found
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz) 404 Not Found

So tried
sue@sue-desktop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied) got a similar 'unable to lock' message when I ran apt-get autoclean
E: Could not open lock file /var/cache/apt/archives/lock - open (13 Permission denied)
E: Unable to lock the download directory

I am still such a newbie at all this and not sure what to do next? My computer has really begun to slow down lately and am not sure why as update manager tells me system is up to date! Any help, please!

I am but a noob but what I'd do is burn a live CD of Ubuntu 8.10 and just boot *shrug*. But if you don't have the speed to dl the 8.10 .ISO file I really don't know what to say. Also try to root the apt-get command.

- _noob_

---

### Post by coffeecups on 2008-12-18
Thanks to all of you for the quick replies, ran the sources list 
What does it mean?
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END

---

### Post by coffeecups on 2008-12-18
Thanks for suggestions, tried the apt-get with root command and got this message about a key which I've had before and thought i'd fixed !?
 
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by lovelyvik293 on 2008-12-18
The lines with the "#" sign are comments.
and the lines with the "deb" are the address for the repositries.

---

### Post by gjoellee on 2008-12-18
You know....I just realized that Fiesty is no longer supported, therefore some  parts of the repo may be deleted, and with them goes the GPG keys (you GPG keys to run a repo)

to fix the synaptic problem reboto, that type in terminal ```
update-magaer -d
```, and run the updates (if you are not sure about the removal of some files after the upgrade do not remove the files).

If this does not work you can do this:
```
sudo gedit /etc/apt/sources.list
```and replace "fiesty" with "intrepid" if you want to go to 8.10,
or replace "fiesty" with "hardy" if you want to go to 8.04
or replace "fiesty" with "gutsy" if you want to go to 7.10

after thats done, save and exit.
now use this command:
```
sudo apt-get upate && sudo apt-get upgrade
```


(If you have file you abselutely must have add them do an other HDD in case of a crash)

---

### Post by coffeecups on 2008-12-18
OK, thanks for reply, I've just burned a CD of 8.10 as per suggestion by noob and being as feisty fawn is not supported anymore would I be better off, saving my files and doing a new install from the CD?

---

### Post by coffeecups on 2008-12-18
Thanks for all your help gjoellee, like you said earlier a clean install of 8.10 is recommended so will give it a try :-)

---

