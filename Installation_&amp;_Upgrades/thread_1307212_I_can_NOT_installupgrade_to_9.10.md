---
title: "I can NOT install/upgrade to 9.10"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by opower95 on 2009-10-30
I have tried and tried again to install or upgrade to 9.10. I have 9.04 and when I use the update manager to upgrade it always fails in the middle of "fetching file # out of #". When I try to use Terminal with "sudo do-release-upgrade" it gives me this > sudo do-release-upgrade
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool  
Done downloading            
extracting 'karmic.tar.gz'
authenticate 'karmic.tar.gz' against 'karmic.tar.gz.gpg' 

Reading cache

Checking package manager
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg
Done [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
Done [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Done [http://archive.canonical.com](http://archive.canonical.com) karmic Release
Done [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources
Done [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Done [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Done [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
Done [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
Done [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release
Done [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Done [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Done [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Done [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Done [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Done [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Done [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Done [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Done [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release
Done [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Done [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Done [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Done [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Done [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Done [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Done [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Done [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Done [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Done [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Done [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Done [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Done [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Done [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Done [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Done [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Ignored [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Failed [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Ignored [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Failed [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Done [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Done [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Ignored [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Failed [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Ignored [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Failed [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Failed [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Failed [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Done downloading            
Reading package lists: Donekarmic-security/multiverse Packages: 96   
Reading state information: Done
Reading state information: Done
Reading state information: Done

Updating repository information
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Done [http://archive.canonical.com](http://archive.canonical.com) karmic Release
Done [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Done [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release
Done [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Ignored [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Failed [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Ignored [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Failed [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Ignored [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Failed [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Ignored [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Failed [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Failed [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Failed [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Done downloading            
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Done [http://archive.canonical.com](http://archive.canonical.com) karmic Release
Done [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Done [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release
Done [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Ignored [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Failed [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Ignored [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Failed [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Ignored [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Failed [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Ignored [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Failed [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Failed [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Failed [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Done downloading            
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release
Done [http://archive.canonical.com](http://archive.canonical.com) karmic Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Done [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Done [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release
Done [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Ignored [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Failed [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Ignored [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Failed [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Ignored [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Failed [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Ignored [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Failed [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Failed [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Failed [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Done downloading            

Error during update 

A problem occurred during the update. This is usually some sort of 
network problem, please check your network connection and retry. 

W:Failed to fetch 
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources) 
404 Not Found [IP: 130.239.18.165 80] 
, W:Failed to fetch 
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages) 
404 Not Found [IP: 130.239.18.165 80] 
, E:Some index files failed to download, they have been ignored, or 
old ones used instead. 


Restoring original system state

Aborting
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done


I have burned a CD of 9.10, and yes it is burned 100% correctly, it doesn't work either. First of all, when I just restart it with the CD in the drive it boots normally. When I change the BIOS settings to boot from CD it still doesn't do it and it boots normally. 

I have explored the CD from the desktop in nautilus and when I try the "wibu.exe" it reports that an error has occurred and it can't find a file.

I am very stressed out I have been trying to upgrade for close to 24 hours now. I have a feeling that it's something very simple and I just sound like an idiot. 
Sorry for the novel, but I'd *greatly* appreciate some help. Thank you ahead of time.

---

### Post by Arkanon on 2009-10-30
I'm at the same point. I'd love to move to 9.10 from 9.04, but at this rate, I'm pretty disappointed. I've tried copying to URLs from the messages into a browser tab, and sure enough, I'm getting 404s on them.

Perhaps the solution is to give up on 9.10 until late next week.

---

### Post by MC707 on 2009-10-30
I have read that upgrading to 9.10 is not a good idea for various reasons, however some of the most important being that you cannot fully switch to ext4 if you were not using it previously, as well as the fact that there is a brand new GRUB menu (from scratch IIRC), and that the system cannot update fully to this new grub. 

I would suggest getting a good 'ol ubuntu CD and getting a fresh install. It would have taken me days to update my three machines (desktop, laptop, netbook) to karmic with regular update, while CDs are a much more fresh start, most updates already come inside the CD, and you save canonical many Gigs'o'bandwidth :P

---

### Post by morphodone on 2009-10-30
you might want to try an alternate repository source...


System > Administration > Software sources

Click on 'download from' and select other - find a repo near you

---

### Post by macogw on 2009-10-30
The 404s mean your mirrors aren't fully sync'd.  Please try a different mirror.

---

### Post by Arkanon on 2009-10-31
Hm...

Not to be daft, morphodone and macogw, but perhaps I don't understand the way the mirrors are handled. Please enlighten me so that I may go forth and sin no more. The name in the URL is us.archive.ubuntu.com - why would the US archive not be fully up to date? Is the name just an alias for any one of a number of machines that get hit depending on some algorithm?

Next, MC707: You're making assumptions about the machines we're upgrading that may or may not be valid. I respect the suggestion, and have considered it. I've decided to avail myself of a feature that is offered - to wit, network upgrade. 

To the point of "saving bandwidth," both I and the OP indicate that we **did** attempt to download the alternate CD ISO. The directions provided on the site for using the alternate CD weren't just a little off base, they were flat wrong. There is no file on the alternate CD called cdromupgrade, so it is kind of hard to execute the following command:

[INDENT]gksu "sh /cdrom/cdromupgrade"[/INDENT]

I understand that this is an open source project and a free (as in beer) product. My prior post is not about complaining. It is about trying to find a solution using the network upgrade feature. 

Right now it seems like my best alternative is to wait until the mirrors are synchronized and the surge of upgrade traffic has died down. I'm OK with that. Thanks to everyone for their time!

---

### Post by opower95 on 2009-10-31
I agree with Arkanon, I think I'll just wait a week or so and hope for the best.

---

### Post by pizza-is-good on 2009-10-31
If you have a free USB drive, use the Ubuntu Startup Disk Creator, and try to install it from there.

I installed it from that, but I am actually doing an install right now, because I needed to fix some partitions.

I can't actually write a review or say that I like Karmic yet, even tho I'm using the Live USB of it right now. I haven't used it enough.

Anyway, hopefully it helps.

By the way, I didn't find a md5 sum for the karmic, so I can't be sure that I downloaded it correctly...
Did anyone find one?

---

### Post by macogw on 2009-10-31
> **Arkanon said:**
> Hm...

Not to be daft, morphodone and macogw, but perhaps I don't understand the way the mirrors are handled. Please enlighten me so that I may go forth and sin no more. The name in the URL is us.archive.ubuntu.com - why would the US archive not be fully up to date? Is the name just an alias for any one of a number of machines that get hit depending on some algorithm?
US archive is load-balanced across a handful of machines, yes.  It's also possible that the servers were starting to reject connections due to being overloaded.

---

### Post by decoherence on 2009-11-04
I'm having the same issue. I've tried several mirrors as well as archive.ubuntu.com. In every case I get the error

```
W:Failed to fetch 
http://ubuntu.mirror.rafal.ca/ubuntu/dists/karmic/universe/binary-amd64/Packages 
404 Not Found 
, W:Failed to fetch 
http://ubuntu.mirror.rafal.ca/ubuntu/dists/karmic/universe/source/Sources 
404 Not Found 
, E:Some index files failed to download, they have been ignored, or 
old ones used instead. 
```

Yes, the formatting is strange like that. And no, there is no such thing as "http://ubuntu.mirror.rafal.ca/ubuntu/dists/karmic/universe/source/Sources" though there is a "http://ubuntu.mirror.rafal.ca/ubuntu/dists/karmic/universe/source/Sources.gz"

huh. well i'm going home for the day so maybe we'll have a look at it tomorrow.

---

### Post by decoherence on 2009-11-05
Double-huh. I tried again this morning and it worked. But as far as I can tell, there is still no .../Sources on the server I'm using, still just a Sources.gz and Sources.bz2.

I wonder what changed? The obvious answer is that this mirror got updated and I had really bad luck in picking them over the last few days. Still, the errors it spit out before should still be occuring, AFAIK, as the file it was 404-ing on is still not present.

Oh well. More of a curiosity for me, at this point.

---

### Post by sunny10 on 2009-11-05
I cant update ubuntu 9.10
it repeatedly downloading same updation file
terminal view:
sunny@sunny-laptop:~$ sudo apt-get upgrade
[sudo] password for sunny: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  binutils brasero checkbox checkbox-gtk empathy empathy-doc f-spot firefox
  firefox-3.5 firefox-3.5-branding firefox-3.5-gnome-support
  firefox-gnome-support info install-info kerneloops-daemon libbrasero-media0
  libempathy-common libempathy-gtk-common libempathy-gtk28 libempathy30
  libpoppler-glib4 libpoppler5 libpython2.6 libusplash0 nvidia-common
  poppler-utils python python-minimal python-ubuntuone-client python2.6
  python2.6-minimal ubuntu-xsplash-artwork ubuntuone-client
  ubuntuone-client-gnome update-manager update-manager-core usplash
  xserver-common xserver-xorg-core xsplash xulrunner-1.9.1
  xulrunner-1.9.1-gnome-support
42 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 24.9MB of archives.
After this operation, 233kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main libpython2.6 2.6.4-0ubuntu1 [967kB]
0% [1 libpython2.6 241664/967kB 24%]                         24.4kB/s 16min 53s^Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main libpython2.6 2.6.4-0ubuntu1 [967kB]
Get:3 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main libpython2.6 2.6.4-0ubuntu1 [967kB]
Get:4 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main libpython2.6 2.6.4-0ubuntu1 [967kB]
1% [4 libpython2.6 253952/967kB 26%]                          63.0kB/s 6min 31s^C
sunny@sunny-laptop:~$ 





&
kernal problem
compaq presario cq60 pc
linux-backports-modules-2.6.31-14-generic N/A
linux-firmware 1.24
plz help me

---

### Post by AV8R on 2009-11-05
I'm totally new to the Ubuntu experience and I'm having trouble with the installation as well.  A couple of people in this thread mentioned waiting a week and then trying again.  What happens in a week?  Are some of the bugs worked out?

---

