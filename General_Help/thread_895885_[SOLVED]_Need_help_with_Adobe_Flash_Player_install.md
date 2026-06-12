---
title: "[SOLVED] Need help with Adobe Flash Player installation"
date: 2008-08-20
forum: General Help
---

### Post by colobix on 2008-08-20
I downloaded the package from this website:
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

The installation file was currupted or something coz it won't open.

Can any of u guys plz help me here?

Thank you.

---

### Post by snowpine on 2008-08-20
This is easier (I think). Open the terminal (applications-->accessories-->terminal) and type:

```
sudo apt-get install flashplugin-nonfree
```

Let us know if that works!

---

### Post by colobix on 2008-08-20
Yup that worked perfect.
Thank you so much
U guys r great:)

---

### Post by davidpeace on 2008-08-20
Extract it into the folder (right click, Extract here..)
Open a terminal and change to that folder, for example:
 cd /home/user_name/Desktop/install_flash_player_10_linux

Then in the terminal execute the installer with 

./flashplayer-installer

---

### Post by colobix on 2008-08-20
NO wait.
It didn't work.
I though it would but it didnt.

---

### Post by colobix on 2008-08-20
Hmmm. I really do not understand.
I do not have any problems installing other things, but maybe this flash plugin installer is corrupted or something. hmmm.

---

### Post by mb_webguy on 2008-08-20
If you are using Hardy, then it's well known that there are issues with Flash and PulseAudio.  If you use the version in the repositories (which snowpine suggested you install with the command "sudo apt-get install flashplugin-nonfree"), then you may also have to install the package libflashsupport to resolve these conflicts.  

However, the version available for Intrepid that is in the Hardy backports repository doesn't have these problems.  Enable the backports repository by going to System->Administration->Software Sources, clicking on the Updates tab, and selecting "Unsupported updates (hardy-backports)".  Then type the following in the terminal.
```
sudo apt-get remove flashplugin-nonfree libflashsupport
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```

Also, if you're still having problems with your Flash plugin, make sure you don't have any of the other Flash plugins like Gnash installed.  You can type "about : plugins" (without the spaces) in the Firefox address bar to see what plugins you have installed.

---

### Post by colobix on 2008-08-20
NOpe I don't have gnash installed and it didn't work now either but thanks.

---

### Post by colobix on 2008-08-20
I tried that method u said. I enabled the backports, went to terminal and pasted in the command. It told me that not all of the updates were downloaded and something about they have been ignored or older used.

So what do I do now?

---

### Post by colobix on 2008-08-20
Bump

---

### Post by mb_webguy on 2008-08-20
> **colobix said:**
> I tried that method u said. I enabled the backports, went to terminal and pasted in the command. It told me that not all of the updates were downloaded and something about they have been ignored or older used.

So what do I do now?

That sounds like a server problem.  Go to System->Administration->Software Sources, click the "Download from:" drop-down box, and choose "Other".  Then click the "Select Best Server" button and let it run the tests, then click the "Choose Server" button, and "Close".  It will prompt you to update your sources, so click "Reload".  You should now be able to install the Flash plugin using the command "sudo apt-get install flashplugin-nonfree" in the terminal.

---

### Post by colobix on 2008-08-20
Can't find cdrom ubuntu, can't find http;//etc.. file not found.

That does sounds like an server error to me. BUt in the ubdateing program it says it could be and unfinished update installation and many other things.

---

### Post by colobix on 2008-08-20
Ok now im pretty sure its not a server problem. I seeked for the best server, didnt work. then i seeked for some other servers and no much luck there either.
COuld it b a problem on my PC?
Plz help me out.

---

### Post by colobix on 2008-08-20
OK here's the output I get when I change server. and plz help me with this.
_
Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by colobix on 2008-08-20
BUMP

The same thing happens in generetic mode.

Not all updates can be installed it says when I run the update manager.

---

### Post by anxiousdog on 2008-08-20
> **mb_webguy said:**
> If you are using Hardy, then it us well know that there are issues with Flash and PulseAudio.  If you use the version in the repositories (which snowpine suggested you install with the command "sudo apt-get install flashplugin-nonfree"), then you may also have to install the package libflashsupport to resolve these conflicts.  

However, the version available for Intrepid that is in the Hardy backports repository that doesn't have these problems.  Enable the backports repository by going to System->Administration->Software Sources, clicking on the Updates tab, and selecting "Unsupported updates (hardy-backports)".  Then type the following in the terminal.
```
sudo apt-get remove flashplugin-nonfree libflashsupport
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```

Also, if you're still having problems with your Flash plugin, make sure you don't have any of the other Flash plugins like Gnash installed.  You can type "about : plugins" (without the spaces) in the Firefox address bar to see that plugins you have installed.

This worked for me! Thanks!

---

### Post by Comhra on 2008-08-20
Have a look here, use it at your own risk but I can tell you that it solved the very difficult flash problem in Ubuntu for me.

[http://www.uburocks.com/2008/08/18/flash-is-fixed-in-ubuntu/](http://www.uburocks.com/2008/08/18/flash-is-fixed-in-ubuntu/)

The original is here, but it leaves out that important last step: 
sudo apt-get install flashplugin-nonfree




[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

Make sure that any Flash plugin that you may have installed is removed first.

---

### Post by Comhra on 2008-08-20
Looks like you're double-posting.

---

### Post by mb_webguy on 2008-08-20
> **colobix said:**
> OK here's the output I get when I change server. and plz help me with this.
_
Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Some index files failed to download, they have been ignored, or old ones used instead.

I'm not completely sure about the last one, but the first two errors are because you have the CD checked as one of your sources.  Go to System->Administration->Software Sources, and in the "Installable from 
CD-ROM/DVD" section, uncheck the CDROM entry.  Now try "sudo apt-get update" again.

---

### Post by colobix on 2008-08-20
NO I can't. It's nothing to click on there to disable cd and dvd.
It says: To install from a cdrom or dvd, insert the medium into the driver.
That's all.

---

### Post by mb_webguy on 2008-08-21
Can you post the output of "cat /etc/apt/sources.list" please?

---

### Post by colobix on 2008-08-23
chris@chris-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
chris@chris-laptop:~$

---

### Post by aysiu on 2008-08-23
> **colobix said:**
> ```

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
``` Your backports are commented out (i.e., not enabled).

**Commented out**```
# source
``` **Uncommented**```
source
```

---

### Post by colobix on 2008-08-24
AAh. Thank you.

---

### Post by Robbinski12 on 2008-08-25
> **mb_webguy said:**
> That sounds like a server problem.  Go to System->Administration->Software Sources, click the "Download from:" drop-down box, and choose "Other".  Then click the "Select Best Server" button and let it run the tests, then click the "Choose Server" button, and "Close".  It will prompt you to update your sources, so click "Reload".  You should now be able to install the Flash plugin using the command "sudo apt-get install flashplugin-nonfree" in the terminal.

Thanks, I had the same problem and your post solved it to me!

---

### Post by Jon2288 on 2008-08-30
Thank you, this thread helped a million!

---

### Post by HarmonicaGoldfish on 2008-09-21
> **mb_webguy said:**
> If you are using Hardy, then it's well known that there are issues with Flash and PulseAudio.  If you use the version in the repositories (which snowpine suggested you install with the command "sudo apt-get install flashplugin-nonfree"), then you may also have to install the package libflashsupport to resolve these conflicts.  

However, the version available for Intrepid that is in the Hardy backports repository doesn't have these problems.  Enable the backports repository by going to System->Administration->Software Sources, clicking on the Updates tab, and selecting "Unsupported updates (hardy-backports)".  Then type the following in the terminal.
```
sudo apt-get remove flashplugin-nonfree libflashsupport
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```

Also, if you're still having problems with your Flash plugin, make sure you don't have any of the other Flash plugins like Gnash installed.  You can type "about : plugins" (without the spaces) in the Firefox address bar to see what plugins you have installed.

I did this. Now I do not have any sound when I play videos (youtube, etc...). No Gnash installed. Gecko has been uninstalled as well...

Any idea how I can fix this??

---

### Post by trumpetman95 on 2008-09-25
> **snowpine said:**
> This is easier (I think). Open the terminal (applications-->accessories-->terminal) and type:

```
sudo apt-get install flashplugin-nonfree
```

Let us know if that works!

I am just trying to get videos to play in youtube??? I must be doing something wrong.

I did that and this is what it said.


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
Package libflashsupport is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I did exactly wah tit said...(i think) :)

---

### Post by trumpetman95 on 2008-09-25
> **Robbinski12 said:**
> Thanks, I had the same problem and your post solved it to me!


Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree
 

 This is what it said after I tried this fix.

---

### Post by hadynd88 on 2008-10-26
> **mb_webguy said:**
> If you are using Hardy, then it's well known that there are issues with Flash and PulseAudio.  If you use the version in the repositories (which snowpine suggested you install with the command "sudo apt-get install flashplugin-nonfree"), then you may also have to install the package libflashsupport to resolve these conflicts.  

However, the version available for Intrepid that is in the Hardy backports repository doesn't have these problems.  Enable the backports repository by going to System->Administration->Software Sources, clicking on the Updates tab, and selecting "Unsupported updates (hardy-backports)".  Then type the following in the terminal.
```
sudo apt-get remove flashplugin-nonfree libflashsupport
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```

Also, if you're still having problems with your Flash plugin, make sure you don't have any of the other Flash plugins like Gnash installed.  You can type "about : plugins" (without the spaces) in the Firefox address bar to see what plugins you have installed.
This worked perfectly. There were some errors in Terminal but that was due to incorrect software sources I had. Hardy-Backports loaded fine. Also i had to restart firefox to force the plugin to load.

---

