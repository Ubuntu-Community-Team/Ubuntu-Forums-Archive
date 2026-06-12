---
title: "Upgrade Problem"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by dovael on 2009-10-08
When I try to upgrade to 9.04 from 8.10 I get following notice:
W:Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, E:Some index files failed to download, they have been ignored, or old ones used instead.

What can I do?

---

### Post by mikewhatever on 2009-10-08
It looks like you have lines for 8.04 in your sources.list. How about the output of 
**cat /etc/apt/sources.list**

---

### Post by dovael on 2009-10-08
tried your suggestion
dov@dov-desktop:~$ cat /etc/apt/sources.list.
cat: /etc/apt/sources.list.: No such file or directory
dov@dov-desktop:~$ 

actually I am a newbie with terminal

---

### Post by mikewhatever on 2009-10-08
Try again:

gedit /etc/apt/sources.list

or

cat /etc/apt/sources.list

---

### Post by dovael on 2009-10-08
Did gedit as suggested and got a whole megila of info in second terminal window which I do not understand. For example, what do I have to "uncomment".
 
deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security multiverse


deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted

---

### Post by mikewhatever on 2009-10-08
I asked for the output because of the error you got, and sure enough, the lines for Hardy Heron cd are at the bottom of the list.

> deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted 

Open the file for editing with **gksudo gedit /etc/apt/sources.list** and delete the last two lines, then save and exit.

---

### Post by dovael on 2009-10-09
Hi.
Deleted last two lines as instructed, but still can't upgrade. I get
W:Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, E:Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by mikewhatever on 2009-10-09
Right, there is a third one at the top of the list, beneath the Jaunty cd-rom line. I guess it also needs to go.

---

### Post by dovael on 2009-10-10
Thank you Mike. Your advice eiminated notices when using update manager. I can now update to 9.04. But it states that it will take 10 hours according to server rate. I am wondering if there is a quicker alternative and if it is worth the trouble and will I be jeopardizing my firefox and thunderbird bookmarks and settings as well as other programs running.

---

### Post by slakkie on 2009-10-10
Although this problem is already solved, an easy way to fix this is:

```

sudo perl -p -i -e 's/^(deb cdrom)/#$1/' /etc/apt/sources.list

```

This will just comment the line out.

---

### Post by mikewhatever on 2009-10-11
> **dovael said:**
> Thank you Mike. Your advice eiminated notices when using update manager. I can now update to 9.04. But it states that it will take 10 hours according to server rate. I am wondering if there is a quicker alternative and if it is worth the trouble and will I be jeopardizing my firefox and thunderbird bookmarks and settings as well as other programs running.

I'd say 10 hours is a bit risky. The connection might drop and you'll be stuck with a half upgraded system. Try picking a different server from System->Administration->Software Sources. Regardless, it's a good idea to backup your Firefox and Thunderbird profiles.

---

