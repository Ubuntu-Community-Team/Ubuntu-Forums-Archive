---
title: "Installing application problem with unresponsive Hardy Heron disk"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by rpete on 2008-12-04
I understand there are three ways to install an application: add/remove, synaptics package manager, or .tar files. I have two problems. The application may be in the repository and I can apply it when using add/remove, but often after hitting apply I am asked to insert the cd with Ubuntu 8.04 and press enter. When I do so, nothing happens and I have to press cancel. Then I get a message "error occurred...failed to fetch cdrom labeled Ubuntu 8.04 [with file such and such needed for the application].  The second problem is when I use the command line. During the installation of an application the cd also must be engaged and it fails to function. For example, I want the utility subversion in order to use the MyPlayer application.  I type sudo get-apt install subversion and enter my password. I get the message "Reading package lists...done..Building dependency tree..."etc. Then I get the query, "Do you want to continue y/n? I type y and press enter and am prompted with "media change, please insert disk labeled Ubuntu 8.04 in the drive and press enter".  The disk is already in the drive. I press enter and often get the same prompt: media change. I may press enter six times and get the prompt each time until I press enter and nothing happens. Sometimes I get a series of numbered tasks completed, such as 1.Get....2. Get...then the prompt for media change, then 3.Get...

It is frustrating because I start a process and everything seems to be going well and then am asked to insert the cd and then the process fails to run to completion.

---

### Post by utsuprainfra on 2008-12-04
is the disc mounted? 

do:

mount 

and paste the output

---

### Post by rpete on 2008-12-04
> **utsuprainfra said:**
> is the disc mounted? 

do:

mount 

and paste the output
Hi, I believe it is. The cd is listed under places and I can click on it and open it showing all the folders.

---

### Post by rpete on 2008-12-04
> **utsuprainfra said:**
> is the disc mounted? 

do:

mount 

and paste the output
Sorry I don't know how to paste the output, but it seems fine, it begins with "/dev /sda3 on / type ext3" and ends "/dev/ scd0 on /media/cdrom1 type iso9660"

---

### Post by oldos2er on 2008-12-04
Can you please post the output of "cat /etc/apt/sources.list"?

---

### Post by jerrykenny on 2008-12-04
Stick with oldos2er, hes taking you along the right way to fix this.

---

### Post by rpete on 2008-12-05
> **oldos2er said:**
> Can you please post the output of "cat /etc/apt/sources.list"?
Hi, thanks for your reply. The output is lengthy, but the gist is "hardy main restricted" "N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu team." I'm not sure what this means. The cd is from Canonical. It is labeled Ubuntu 8.04 LTS DVD.  It came with the computer I bought in October, 2008. Other key lines: "Software in backports will not receive any review or updates from the Ubuntu security team." "Uncomment the following two lines to add software from Canonical's partner..." Then there are six lines (not two).  

1.  "deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner"
2.  "deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner"
3.  "deb [http://ppa.launchpad.net/dell-team/ubuntu](http://ppa.launchpad.net/dell-team/ubuntu) hardy main"
4.  "deb src [http://ppa.launchpad.net/dell-team/ubuntu](http://ppa.launchpad.net/dell-team/ubuntu) hardy main"
5.  "deb [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) hardy-proposed restricted main multivers universe"
6.  "deb-src [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) hardy-proposed restricted main multiverse universe"

---

### Post by jerrykenny on 2008-12-05
I'm still sure theres a line in there saying something like

deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Alpha i386 (20060504)]/ dapper main restricted

You need to disable this line by adding a # in front of it . . . 

Then at a terminal type

sudo apt-get update

---

### Post by jenkinbr on 2008-12-05
I've had problems using apt from a CD too, as well as any CD that contains apt-complient software.  I recommend disableing this entry entirely by commenting out the line that starts with "deb cdrom:///" in /etc/apt/sources.list.  To do this, just add a single '#' (without quotes) to the beginning of the line.  To edit the file, you will need to be root, so type ```
gksudo gedit /etc/apt/sources.lst
```

It would be useful if you could post the complete output of ```
cat /etc/apt/sources.list
```

To paste output from the terminal, first select the output, then press <ctrl>+<shift>+<c> (NOT <ctrl>+<c>) and paste (<ctrl>+<v>) the output inside BBCode tags -- [code.][/code.] ***Remove the period in the tags - I put it there to make the forum ignore these tags***

---

### Post by rpete on 2008-12-05
> **jenkinbr said:**
> I've had problems using apt from a CD too, as well as any CD that contains apt-complient software.  I recommend disableing this entry entirely by commenting out the line that starts with "deb cdrom:///" in /etc/apt/sources.list.  To do this, just add a single '#' (without quotes) to the beginning of the line.  To edit the file, you will need to be root, so type ```
gksudo gedit /etc/apt/sources.lst
```

It would be useful if you could post the complete output of ```
cat /etc/apt/sources.list
```

To paste output from the terminal, first select the output, then press <ctrl>+<shift>+<c> (NOT <ctrl>+<c>) and paste (<ctrl>+<v>) the output inside BBCode tags -- [code.][/code.] ***Remove the period in the tags - I put it there to make the forum ignore these tags***

There is an entry like that referred to. I am not sure how to add a # to the beginning of the line. The up arrow doesn't seem to work.

---

### Post by rpete on 2008-12-05
You give instructions on how to paste the output from the terminal, but I am used to Windows moving the cursor to a point and pressing enter, then pressing and holding down shift and the down arrow to select. I don't know how to select. Then pasting involves pressing ctrl + v but what are the BBCode tags? Are they brackets?

---

### Post by oldos2er on 2008-12-05
"The output is lengthy"

 That's ok. It would really help to see the whole file, please.

---

### Post by rpete on 2008-12-05
Hi oldos2er.  Someone else pointed out that I needed to uncomment, insert a "#" where one was lacking.  There must be an easy way to copy and paste the output, but I don't know it. I have started to write down by hand each line and then will type it in a reply.

---

### Post by rpete on 2008-12-05
> **oldos2er said:**
> "The output is lengthy"

 That's ok. It would really help to see the whole file, please.
## deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to 
# newer versions of the distribution.
deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted #Added by software properties
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive](http://us.archive) ubuntu.com/ubuntu/ hardy restricted main multiverse universe #Added by software-properties
## Major bug fix updates produced after the final release of the 
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates restriced main multiverse universe #Added by software properties
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team and may be under a free license. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as 
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT  receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is 
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb [http://ppa.launchpad.net/dell-team/ubuntu](http://ppa.launchpad.net/dell-team/ubuntu) hardy main
deb src [http://ppa.launchpad.net/dell-team/ubuntu](http://ppa.launchpad.net/dell-team/ubuntu) hardy main
deb [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) hardy-proposed restricted main multivers universe
deb-src [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) hardy-proposed restricted main multiverse universe

---

### Post by nandemonai on 2008-12-05
From terminal:

```
gksudo gedit /etc/apt/sources.list
```

Enter your password.

Move to the line:
```

deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
```

Add a # (Shift 3) ;)
```

#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
```

Save the file and close gedit.

Then back in terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

It shouldn't bug you about the CD anymore.

As a sidenote, to copy/paste in terminal use: Ctrl-Shift-C / Ctrl-Shift-V

---

### Post by rpete on 2008-12-05
Nandemonai, thanks for the help. It seems to be working now. I was not asked to insert cd and all packages were opened and the output ran through to the prompt again. What a relief!

---

### Post by oldos2er on 2008-12-06
> **rpete said:**
> Hi oldos2er.  Someone else pointed out that I needed to uncomment, insert a "#" where one was lacking.  There must be an easy way to copy and paste the output, but I don't know it. I have started to write down by hand each line and then will type it in a reply.

 Swipe (or mark) the output with your mouse, right-click and hit Copy. Open a new post here, right-click and hit Paste.

 Edit: Nevermind, I see you got it fixed.

---

