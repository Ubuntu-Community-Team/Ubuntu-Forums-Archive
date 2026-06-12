---
title: "&quot;Add/Remove&quot; Application List Empty"
date: 2008-11-30
forum: General Help
---

### Post by captainskyhawk on 2008-11-30
When I go to "Applications > Add/Remove...", and the window pops up, the list is empty.  There is only one category on the left side ("All"), but no applications appear anywhere, no matter what I do.

I'm now seeing this same problem on two computers, one running 8.04 and one running 8.10.

---

### Post by taurus on 2008-11-30
Maybe there is something funny going on with your /etc/apt/sources.list.  Open a terminal and post your /etc/apt/sources.list.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by john183 on 2008-11-30
have you tried opening a terminal window and running
```
sudo apt-get update
```
That should update the software listings from the repos.

---

### Post by captainskyhawk on 2008-11-30
> **taurus said:**
> Maybe there is something funny going on with your /etc/apt/sources.list.  Open a terminal and post your /etc/apt/sources.list.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

```
# added by the release upgrader
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main restricted
#
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted
deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse

deb http://dl.google.com/linux/deb/ stable non-free
deb http://dl.google.com/linux/deb/ testing non-free

```

> **john183 said:**
> have you tried opening a terminal window and running
```
sudo apt-get update
```
That should update the software listings from the repos.

Did that -- no change.  I can update just fine from "System > Administration > Update Manager" of course, and the Synaptic Package Manager works just fine.

However, I maintain these computers for other people, and I need that "Add/Remove..." option to work!  :biggrin:  Synaptic's just too confusing for the novice user.

---

### Post by captainskyhawk on 2008-12-05
Honestly, no one else is seeing this behaviour?  I'm now seeing this on three separate installations -- do I need to go make an official bug report?

---

### Post by chris.h on 2008-12-18
I have the same problem on 8.10 amd64

---

### Post by chris.h on 2008-12-18
I fixed mine:

```

sudo apt-get remove gnome-app-install
sudo apt-get install gnome-app-install apturl ubufox ubuntu-desktop

```

---

### Post by mosimea on 2008-12-18
I just had this happen to me.  Don't know why I should have to, but uninstalling/re-installing  gnome-app-install solved it.

---

### Post by x001 on 2008-12-20
Fresh install of 8.10 and I experienced the same problem. Reinstalling solved it.

---

### Post by budgallant on 2009-01-01
Chris' solution worked for me, as well... thankfully.
1 day old install of 8.10...  disappeared for seemingly no reason. Got em back... Only thing I was doing was changing themes and colors today... not sure how that could have had an effect... also ran pidgin... could be a connection, but i don't see how.

First time linux user. Enjoying it so far.

Glad I found this thread through google.

---

### Post by Agent Smith on 2009-01-02
I also had this problem with nothing being shown in add/remove. It started after installing Adobe Air for BBC iplayer. I had to reinstall gnome-app-install to fix it. Oh im using Hardy by the way.

---

### Post by budgallant on 2009-01-02
> **Agent Smith said:**
> I also had this problem with nothing being shown in add/remove. It started after installing Adobe Air for BBC iplayer. I had to reinstall gnome-app-install to fix it. Oh im using Hardy by the way.

Hmmm...  actually, i had just installed adobe air the night before....
using it to run tweetdeck.  I wonder if that could be why mine were gone, too.... I hadn't checked since the install. We may have discovered the issue.

---

### Post by rhatton on 2009-01-02
I had exactly the same problem with my brand new 8.10 installation too.  The first thing I installed was Adobe Air (for the BBC iPlayer).

Thanks for the fix - re-installing 'gnome-app-install' sorted the problem for me

---

### Post by GingerAlex on 2009-01-02
Hmm, I have this problem and guess what? The last thing I installed was Adobe Air / BBC iPlayer. This is not what I pay my licence fee for..

---

### Post by budgallant on 2009-01-02
> **GingerAlex said:**
> Hmm, I have this problem and guess what? The last thing I installed was Adobe Air / BBC iPlayer. This is not what I pay my licence fee for..

Well, I didn't install BBC iplayer, but I did install Adobe Air and had this same issue...  I suspect it is Adobe Air that is doing this somehow, though I can not see why it would be...  Looks pretty definitive that we've discovered the cause. I wonder if Adobe is aware of it yet.

---

### Post by Sims12345 on 2009-01-03
> **budgallant said:**
> Hmmm...  actually, i had just installed adobe air the night before....
using it to run tweetdeck.  I wonder if that could be why mine were gone, too.... I hadn't checked since the install. We may have discovered the issue.

I think we just discovered a bug! Same thing, I installed Air for tweetdeck and boom, it's gone!

---

### Post by z0r1k on 2009-01-04
Hi! Same to me! Just installed Adobe AIR for twhirl yesterday and mine "Add/Remove" application starts to show nothing!
After re-installation everything seems to work fine!
Thank you very much!

---

### Post by oospunkey on 2009-01-05
Yea chris.h thanks for the advice. That worked for me as well.

---

### Post by foundhistory on 2009-01-05
Same thing happened to me after *uninstalling* Twhirl (Adobe Air Twitter client). Solution offered above seems to have fixed it for me as well.  Many thanks.

---

### Post by terryandtaotao on 2009-01-05
I had the same problem after installing Adobe AIR and twirl.

Reinstall gnome-app-install did fix the problem.

It seems that the installation of AIR apps corrupted the add/remove stuff.

---

### Post by estebistec on 2009-01-07
I also experienced this after installing adobe air (to run twhirl).

---

### Post by redandwhite on 2009-01-14
**+1 against Adobe Air**. I just installed Adobe Air (using chmod) and Add/Remove disappeared.

Reinstalling Install or Remove Programs worked. Thank you Chris and thank you Google :)

---

### Post by mybluevan on 2009-01-14
Same issue here, Adobe Air messed mine up too. A reinstall from Synaptic fixed it just fine. Anybody submitted a bug report yet?

---

### Post by jojmoj on 2009-01-15
also installed bbc iplayer (and hence adobe air) earlier today

adobe and/or bbc's coders can naff off for braking my lovely little add/remove program

lol

bug reports ftw

---

### Post by ShokTHX on 2009-01-17
This is a bug!
Installing TweetDeck did it for me (and still won't work).
You can reproduce the bug by trying to reinstall the Air app also. Would be really nice if Air would work properly and easy (or someone could make a decent Twitter client like Tweetdeck for Ununtu).

Now if this had been Windows - I would probably be reformating the HD instead of typing this right now. 
Thanks for the Terminal commands to fix the problem. Ubuntu rocks!
Adobe Air on Ubuntu AMD64 on the other hand, not so good yet.

*Added- Removing Adobe Air will also cause the problem.

---

### Post by captainskyhawk on 2009-01-21
Yep -- definitely Adobe AIR!  Same things happens whenever you re-install or update an AIR app, too, even after running the reinstall gnome-app-install command line.

---

### Post by darkteckno on 2009-01-25
This will fix it!

```
sudo apt-get --reinstall install gnome-app-install
```

---

### Post by daqron on 2009-02-04
> **terryandtaotao said:**
> 
Reinstall gnome-app-install did fix the problem.

It seems that the installation of AIR apps corrupted the add/remove stuff.
Same problem, same solution, running Intrepid. How the heck do I *uninstall* Adobe AIR now? It's not listed in Add/Remove even after I fix my list.

**UPDATE:** I received the following message today from Adobe tech support:
[QUOTE=Adobe Tech Support]
Thanks for reporting this. We have fixed this in the upcoming release of AIR.
[/QUOTE]

---

### Post by MystaMax on 2009-02-09
I've had the same exact problem for some time now. I didn't bother to fix it, or look for a fix b/c I usually use aptitude or synaptic to install/uninstall applications.  

I searched Google for "Ubuntu add/remove applications empty", and came directly to this post. Should of done this a long time ago.

I typed the following to resolve

```

sudo aptitude reinstall gnome-app-install

```Thanks chris.h

---

### Post by mb_webguy on 2009-02-09
This command should also work, I believe.```
sudo update-apt-xapian-index
```

---

### Post by rohit_kewlani on 2009-02-13
"sudo update-app-install" fixed the issue on my Ubuntu 8.10

---

### Post by srijesh on 2009-02-13
Thanks everyone for bringing this issue to our notice and sorry about the trouble you went through restoring the list. The issue of empty Add/Remove list would be resolved in the next available public release of AIR on Linux. 

-SRijesh
Adobe Systems.

---

### Post by kyleabaker on 2009-02-19
Thanks everyone. I had the same problem, caused by AIR I assume, but now it's fixed.

---

### Post by noahsachs1 on 2009-02-19
Same problem here, on a fresh install of 8.10 from the CD, I installed the restricted packages, then all the updates, then activated the Nvidia restricted drivers, configured dual screens, set up the repository for Wine, installed Wine, set up the repository for Google apps, installed Google desktop and Picassa. Installed Adobe Air, Installed Twhirl, and then lost my Add/Remove Application.  The solution was to do what Chris said, to uninstall and reinstall

sudo apt-get remove gnome-app-install
sudo apt-get install gnome-app-install apturl ubufox ubuntu-desktop

---

### Post by nickbuntu on 2009-02-23
I had this problem too. One more way to fix it is with

```
sudo dpkg-reconfigure gnome-app-install
```

Glad I found this thread! Was getting fed up of the app list being empty all the time.

---

### Post by b33god on 2009-02-26
thanks Chris your post [http://ubuntuforums.org/showthread.php?p=6396412](http://ubuntuforums.org/showthread.php?p=6396412) fixed issue for me also

---

### Post by GZ Expat on 2009-03-07
It's what I love about Ubuntu...if I have a problem, I am not out in the cold somewhere with a machine that pointlessly works, unless I fork over tons of $$ for someone on the phone to 'fix' it for me.  Pop on to Ubuntu Forums, type in the problem and, 'Presto'...and answer.

Thanks to all...

---

### Post by kadjette on 2009-03-09
Latest update of Adobe Air did not fix the problem. Had to reinstall Add/Remove application yet again.

---

### Post by ukblacknight on 2009-03-18
This happened to me too after installing twhirl on Adobe Air.  Like everyone else, reinstalling gnome-app-install did the trick :)

Wonder how Air manages to disable gnome-app-install? weird bug...

---

### Post by Naz_Drala on 2009-04-18
Bug repros on Air 1.5.1 in Ubuntu 8.04 32 bit

---

### Post by mdmadph on 2009-05-15
> **Naz_Drala said:**
> Bug repros on Air 1.5.1 in Ubuntu 8.04 32 bit

I second this -- bug is now happening again on Air 1.5.1 with Ubuntu 8.04 32-bit.

---

### Post by studiogrynn on 2009-06-28
Yes, I too get this bug again with Air 1.5.1 and Ubuntu 9.04

---

### Post by Sp4 on 2009-08-29
Still happening, thanks for the solution

---

