---
title: "Install programs from live CD?"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by GNU Gnerd on 2009-05-24
Greetings all.

I'm using 8.04 and recently upgraded my OpenOffice from 2.4.1 (the one that came on my live CD) to 3.1 to fix a few problems I was having.  Well, it fixed the problems I had, but now I have a different, more annoying set of problems...and quite honestly, I hate the new 3.1 look.

I looked for an installer for 2.4.1, but on the OpenOffice website there's only a version in German (and ich don't sprech Deutsch), and the repositories only have 3.1 packages so far as I could find.

So, the only idea I have now is to try to install 2.4.1 from my CD: *Is* there a way to use my live CD to only install OpenOffice, without messing with anything else about my installation?  Or do I have to suck it up and stick with 3.1?

Thanks in advance for any assistance.

---

### Post by zeex on 2009-05-24
> **GNU Gnerd said:**
> Greetings all.

I'm using 8.04 and recently upgraded my OpenOffice from 2.4.1 (the one that came on my live CD) to 3.1 to fix a few problems I was having.  Well, it fixed the problems I had, but now I have a different, more annoying set of problems...and quite honestly, I hate the new 3.1 look.

I looked for an installer for 2.4.1, but on the OpenOffice website there's only a version in German (and ich don't sprech Deutsch), and the repositories only have 3.1 packages so far as I could find.

So, the only idea I have now is to try to install 2.4.1 from my CD: *Is* there a way to use my live CD to only install OpenOffice, without messing with anything else about my installation?  Or do I have to suck it up and stick with 3.1?

Thanks in advance for any assistance.

Hi, 

See that's the cool thing about Linux it never sucks :). Here is what you do.

1) make a backup of /etc/apt/sources.list
```
$ sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```
2) Un-install Openoffice 
```
$ sudo apt-get remove --purge openoffice.org*
```
```
$ sudo apt-get autoremove 
```
3) Remove the file /etc/apt/sources.list
4) Make an empty file with same name /etc/apt/sources.list
5) insert your CD and open System -> Administration -> Software sources
6) In the first tab "Ubuntu Software" there is a line at the bottom "Installable from CD-ROM/DVD". Your CD should appear here. Check the check box and close.
7) open /etc/apt/sources.list and check there should be a line someting like this 
```
deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
```
8) update the repository. 
```
$ sudo apt-get update 
```
9) Install Openoffice
```
$ sudo apt-get install openoffice.org
```
*This time it'll be installed from CD.*

10) once you are done restore the repository file.
```
$ sudo mv /etc/apt/sources.list.backup /etc/apt/sources.list
```

11) Run update 
```
$ sudo apt-get update 
```

and you are done ...

Good luck :)

---

### Post by GNU Gnerd on 2009-05-24
Thanks for the quick response!  Unfortunately, your suggestion isn't quite working.  When I get to step 6...

> **zeex said:**
> 6) In the first tab "Ubuntu Software" there is a line at the bottom "Installable from CD-ROM/DVD". Your CD should appear here.

...the CD doesn't appear; when I put in the live CD, it just says "To install from CD-ROM or DVD, insert the medium into the drive."  Is there anything special I need to do to make it see the CD?

---

### Post by zeex on 2009-05-24
> **GNU Gnerd said:**
> Thanks for the quick response!  Unfortunately, your suggestion isn't quite working.  When I get to step 6...



...the CD doesn't appear; when I put in the live CD, it just says "To install from CD-ROM or DVD, insert the medium into the drive."  Is there anything special I need to do to make it see the CD?

Hi, 

sorry my mistake :P.

Failed to mention a few details :) . Insert the CD and open software sources .  In the tab "Third party softwares" there is a option "Add CD ROM". Add your CD. After this check sources.list to make sure CD is added as repository. 

If for any reason this doesn't work. Open terminal and add manually 

```
$ sudo apt-cdrom add
```

then proceed from step 8

*:: in short what you need is to provide apt with only those repositories which as older version of OpenOffice.org before issuing the command apt-get install. That's the basic idea*

---

### Post by Kareeser on 2009-05-24
Hmmm... why exactly does the theme not integrate well with Ubuntu? Have you tried installing openoffice.org-gtk?

---

### Post by GNU Gnerd on 2009-05-25
> **Kareeser said:**
> Hmmm... why exactly does the theme not integrate well with Ubuntu?

The theme integrates just fine; the actual problems I'm having are different.  The issue with the theme is that I'm using a gray and black theme and all of the icons are red or dark blue, making it impossible to tell what any of the buttons do at a glance.

[quote=zeex]:: in short what you need is to provide apt with only those repositories which as older version of OpenOffice.org before issuing the command apt-get install. That's the basic idea[/quote]

So close, and yet so far!  I added the CD (through both the GUI and the command line, just to be sure).  The entry in sources.list is

```
deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted

```

Here's what I get when I try to install it:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openoffice.org is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  ttf-opensymbol openoffice.org-writer openoffice.org-common
  openoffice.org-calc openoffice.org-draw openoffice.org-core
  openoffice.org-math openoffice.org-impress
E: Package openoffice.org has no installation candidate
```

Trying to install Writer or one of the others individually gives me more of the same:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openoffice.org-writer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package openoffice.org-writer has no installation candidate

```

Any ideas?

---

### Post by zeex on 2009-05-25
Hi, 

Please post the output of 
```
$ dpkg --get-selections | grep -i openoffice
```

check a few things. 

1) Source.list file should only contains the Hardy CD rom repository and nothing else. IF there is something else remove it.
2) Check manually in the CD for packages in 
```
Ubuntu 8.04 i386 -> pool -> main -> o
```
The openoffice packages should be there.
3) Remove openoffice 
```
$ sudo apt-get --purge remove openoffice*
```
4) Clean your apt cache
```
$ sudo apt-get clean
```
This will remove everything from cache, every packages you 've. If you wanna keep some packages you downloaded earlier run
```
$ sudo apt-get autoclean
```
5) Update index 
```
$ sudo apt-get update
```
Check if apt is reading index from the CD. This is important.
6) Install open office.
```
$ sudo apt-get install openoffice.org
```

If this doesn't work you could try copying all the required packges in folder /var/cache/apt/archives/ and then install office

---

### Post by GNU Gnerd on 2009-05-25
> **zeex said:**
> Please post the output of 
```
$ dpkg --get-selections | grep -i openoffice
```

```
openoffice.org-calc				deinstall
openoffice.org-common				deinstall
openoffice.org-core				deinstall
openoffice.org-draw				deinstall
openoffice.org-hyphenation			deinstall
openoffice.org-hyphenation-en-us		deinstall
openoffice.org-impress				deinstall
openoffice.org-math				deinstall
openoffice.org-thesaurus-en-au			deinstall
openoffice.org-thesaurus-en-us			deinstall
openoffice.org-writer				deinstall

```

> 1) Source.list file should only contains the Hardy CD rom repository and nothing else. IF there is something else remove it.

It just had the CD in it.

> 2) Check manually in the CD for packages in 
```
Ubuntu 8.04 i386 -> pool -> main -> o
```
The openoffice packages should be there.

The two packages there are *oem-config_1.37.2_i386.deb* and *oem-config-gtk_1.37.2_i386.deb*...are those the right ones?

> 5) Update index 
```
$ sudo apt-get update
```
Check if apt is reading index from the CD. This is important.

When I do this, the output starts with

```
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Translation-en_US

```

which I assume means it's ignoring the CD.  That might be the problem.


Thanks for all your help so far; this has been a good learning experience for me.

---

