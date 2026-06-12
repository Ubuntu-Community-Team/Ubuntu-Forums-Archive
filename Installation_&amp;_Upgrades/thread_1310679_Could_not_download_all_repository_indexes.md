---
title: "Could not download all repository indexes"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by klausner on 2009-11-02
I get errors whenever I try to update my repository info. I'm running 9.10 which I installed from the last beat CD, then upgraded online. (The CD has since been removed from /etc/apt/sources.list).

The errors are:
```
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/Release  Unable to find expected entry  karmic/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/Release  Unable to find expected entry  karmic/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/Release  Unable to find expected entry  karmic/binary-i386/Packages in Meta-index file (malformed Release file?)
```

I've tried several different repositories, but no better luck. I found some old bug reports dating back to Intrepid, and lots of suggestions to try:
```
sudo apt-get update
```
which makes no difference.

Suggestions? :(

---

### Post by jweaver28 on 2009-11-20
I'm a near-newbie and have the same problem. I tried unchecking various boxes in Synaptic/Repositories, as well as the clearing and apt-get suggestions on other threads, to no effect. Hardy had been working, then I did the internal upgrade to karmic, which worked for a couple of days. 

I think I added a bad repository after adding medibuntu 9 days ago, although the medibuntu repository is the only one that seems to work. I also tried changing the repository server from Main to United States, with similar non-effect.

Here are my error messages: 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release](http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release)  Unable to find expected entry  karmic-updates/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/Release](http://security.ubuntu.com/ubuntu/dists/karmic-security/Release)  Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release)  Unable to find expected entry  karmic-backports/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/Release](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/Release)  Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-proposed/Release](http://us.archive.ubuntu.com/ubuntu/dists/karmic-proposed/Release)  Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

So Update Manager says my computer's not been updated in 9 days, despite my repeated update attempts.

---

### Post by drs305 on 2009-11-20
> **jweaver28 said:**
> I think I added a bad repository after adding medibuntu 9 days ago, although the medibuntu repository is the only one that seems to work. I also tried changing the repository server from Main to United States, with similar non-effect.

It looks like your /etc/apt/sources.list has "Releases" in the address that is messing up the file. If you copy the contents of your sources.list file we can help you fix it up.

---

### Post by Enlightened Shadow on 2009-11-20
Has anyone found a answer to this problem? 

I am sort of new to linux. I have been using Ubuntu for two months now. I started out with 9.04 then upgraded to 9.10 almost 2 weeks ago. 

I am now getting an error in my panel saying that my upgrade info is outdated. When I try to update the package info I get an error saying that it could not download all the repository indexes.

Here are my error messages:
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/karmic/Release.gpg](http://wine.budgetdedicated.com/apt/dists/karmic/Release.gpg)  
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/karmic/main/i18n/Translation-en_US.bz2](http://wine.budgetdedicated.com/apt/dists/karmic/main/i18n/Translation-en_US.bz2)  
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/jaunty/Release.gpg](http://wine.budgetdedicated.com/apt/dists/jaunty/Release.gpg)  
Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [http://www.geexbox.org/debian/dists/unstable/main/binary-i386/Packages.gz](http://www.geexbox.org/debian/dists/unstable/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ubuntu.tribler.org/dists/karmic/main/binary-i386/Packages.gz](http://ubuntu.tribler.org/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Like I said I am still kinda new and have not edited my sources file before. So if someone would be so kind to lend me a hand it would be most appreciated.

---

### Post by drs305 on 2009-11-20
> **Enlightened Shadow said:**
> 
I am sort of new to linux. I have been using Ubuntu for two months now. I started out with 9.04 then upgraded to 9.10 almost 2 weeks ago. 

Your sources.list also looks like it has a bunch of problems.

1. There are still references to Jaunty. If you really are using Karmic, either these lines should be eliminated or the name changed to Karmic.

2. It still references your Jaunty CD. You should disable this, either by placing a comment symbol (#) in front of the "cd-rom" line or opening Synaptic > Settings > Repositories > Ubuntu Software and unticking the CD-Rom reference in the bottom section. Otherwise you will always be asked to insert it any time you do an update (and since it's Jaunty it wouldn't do you any good anyway).

3. The wine repositories aren't connecting, but I'm not familiar with how they are structured. You could at least stop the error messages initially by unticking them in Synaptic. They are probably under the Third Party or Other Software tab.

For general information, if you want to manually edit your sources, in Ubuntu it's done with:
```

gksu gedit /etc/apt/sources.list

```

4. It's not your post, but if you copy the contents here someone would be glad to help you sort it out.

Here's the community doc with information about repositories and how they are structured:
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by beloved88 on 2009-11-20
I'm fairly new, using Easy Peasy's jaunty nbr on a brand spankin new HP Mini 1101, and everything seems to work great except this,  similar to the others, synaptic doesn't seem to work right, and i certain apt-get commands don't find the packages.  if i run $ sudo apt-get update, this is the readout
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US          
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg [189B]                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US      
Ign [http://archive.geteasypeasy.com](http://archive.geteasypeasy.com) jaunty Release.gpg                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US   
Ign [http://archive.geteasypeasy.com](http://archive.geteasypeasy.com) jaunty/main Translation-en_US              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                                
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                                
  
Get:2 [http://archive.geteasypeasy.com](http://archive.geteasypeasy.com) jaunty Release [1245B]                   
Hit [http://archive.geteasypeasy.com](http://archive.geteasypeasy.com) jaunty/main Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Fetched 190B in 1s (105B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems






here's the contents of my sources.list file

#deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Easy Peasy security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Easy Peasy 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Easy Peasy security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Easy Peasy users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse

---

### Post by drs305 on 2009-11-20
> **beloved88 said:**
> 
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Update: Actually, I just tried re-importing the key. It appears there is a problem with the server. If it doesn't work, try again later.

You can try to import the public key with the following:
```

gpg --keyserver keyserver.ubuntu.com --recv-keys 437D05B5 && gpg --export --armor 437D05B5 | sudo apt-key add - 

```

If you still get a BADSIG error, open Synaptic, Settings, Repositories: Authentication. Delete the 437D05B5 key, and try running the command again.

---

### Post by beloved88 on 2009-11-21
I still can't seem to do anything, the server must still be down as you said.  Is there a way to install new packages and from a USB?  I do have desktop running UbuntuStudio Jaunty, is there anything i can do to with that?

---

### Post by Enlightened Shadow on 2009-11-22
Hi, I just wanted to give an update on my problem and thank everyone for their support. I was able to get rid of the error message. I didn't realize that once I upgraded that I needed to remove the old repositories from the previous release. Now that I know that I don't think this will be a problem again.

Thanks, Mike.

____________________________________________________________________________________

Another day has gone by and I'm glad to say that I'm just a little bit smarter.

---

### Post by cybercookie72 on 2009-12-09
Greetings

I was having the same error (malformed?) and found a sources.list here in
the forums that worked for me::
(remember to back up first)


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main universe multiverse restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main universe multiverse restricted

# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main universe multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main universe multiverse restricted


that got rid of the errors for me...but I also found a website that makes
a sources.list from a form

[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)

this is the sources.list I am using because it updates pidgin and VLC :P

hope this helps

---

### Post by beloved88 on 2009-12-09
I was actually able to do it using this:
```
gpg --keyserver subkeys.pgp.net --recv-keys 437D05B5
```
I got it from this thread [http://ubuntuforums.org/showthread.php?t=1271353&highlight=NO_PUBKEY+40976EAF437D05B5]("http://ubuntuforums.org/showthread.php?t=1271353&highlight=NO_PUBKEY+40976EAF437D05B5")

---

### Post by greeneca on 2010-11-22
I am having a similar problem. When I update my package manager of update manager i get an error "Could not download all repository indexes" most of which Im sure don't exist.

Here they are:

Failed to fetch http:/arcive.canonical.com/dists/lucid/Release.gpg  Unable to connect to :http:
Failed to fetch http:/arcive.canonical.com/dists/lucid/partner/i18n/Translation-en.bz2  Unable to connect to :http:
Failed to fetch http:/arcive.canonical.com/dists/lucid/partner/i18n/Translation-en_CA.bz2  Unable to connect to :http:
Failed to fetch http:/arcive.canonical.com/dists/lucid/partner/source/Sources.gz  Unable to connect to :http:
Failed to fetch http:/arcive.canonical.com/dists/lucid/partner/binary-i386/Packages.gz  Unable to connect to :http:
Failed to fetch [http://arcive.canonical.com/dists/lucid/partner/source/Sources.gz](http://arcive.canonical.com/dists/lucid/partner/source/Sources.gz)  403  Forbidden
Failed to fetch [http://arcive.canonical.com/dists/lucid/partner/binary-i386/Packages.gz](http://arcive.canonical.com/dists/lucid/partner/binary-i386/Packages.gz)  403  Forbidden
Some index files failed to download, they have been ignored, or old ones used instead.

---

