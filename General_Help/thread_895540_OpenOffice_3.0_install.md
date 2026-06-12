---
title: "OpenOffice 3.0 install"
date: 2008-08-20
forum: General Help
---

### Post by jarome on 2008-08-20
I am new to Ubuntu and debian packages. I downloaded the OpenOffice 3.0 beta and untarred it into a set of directories. 

But if I go into the DEBS directory and do
apt-get install *.deb
it fails looking for a package that is in that directory.

So how does one do such installs?

Thanks,
Jim

---

### Post by coffeecat on 2008-08-20
I don't quite follow you. You say untarred, which usually implies a .tar.gz source file, but I can see only .rpm and .deb files in the Open Office 3 Beta page.

If you did download a .deb file, don't unwrap it. Just place it on your desktop, double-click the icon and a GUI app to install it *should* open up for you.

**Edit:** I'm an idiot. :oops: Just had another look. Yes, there is a source file, a .tar.bz2. Is this what you downloaded? If so, you need the .deb file.

---

### Post by jarome on 2008-08-20
It says it was a debian file, but it has no .deb before the .ter.gz. That is the only choice. What to do?

---

### Post by coffeecat on 2008-08-20
> **jarome said:**
> It says it was a debian file, but it has no .deb before the .ter.gz. That is the only choice. What to do?

My apologies. I thought it was an ordinary .deb file. I tried clicking on the download link and it wants to give me *VeryLongFilename*_deb.tar.gz.

What I would do (no promises this will work), is to put the file on my desktop and double-click it which will cause the file-roller app to open. Click on extract. Close file-roller and, hopefully, there will be the original _deb.tar.gz and also a new folder on your desktop. Open the folder and see if there is a file with a .deb extension. Also look to see if there is a README file. Read that but try double-clicking on the .deb file. **That** *should* open up the graphical installer (can't remember its name offhand) and you just follow the prompts.

If it installs OK you can delete all the stuff on your desktop. It's analagous to getting a .zip file followed by an .exe file in Windows.

**Edit:** I see that you were more-or-less doing that, but trying to use apt-get instead of the easier option of a double-click. :wink: Maybe the contents of the .tar.gz are more - ahem - baroque than I'm expecting. I'm downloading the file myself - I'm intrigued enough to look - and when I've untarred it myself I'll post back.

---

### Post by coffeecat on 2008-08-20
It's me again. :) Baroque, did I say? That's a stinker. :(

Untarring the file gave me a BEB......9328 folder, in which there are DEBS, licenses and readmes folders. The readme says nothing about installing and the DEBS folder has no less than 51 .deb files in it.

OK. Third try - here's what I would do. Untar the downloaded file on your desktop. Open a terminal and:

```
cd Desktop/BEB...9328/DEBS
sudo apt-get install *deb
```Obviously, type out the full BEB...9328 folder name otherwise cd won't work.

Now that I've downloaded the package, and it's sitting on my Mac Mini desktop (don't ask! :p) I'll try installing it myself in my virtualised Ubuntu that I have with MacOS as the host. I'll let you know how I get on.

---

### Post by DJ_Peng on 2008-08-20
They actually went way off standard for this. When a Linux user sees "deb" they think it's a package but this isn't, it's really a .tar.gz. It bugged the daylight out of me when I started trying the beta. You need to open a Terminal (command prompt, use Applications > Accessories > Terminal), navigate to the directory you extracted it to and run > sudo sh update That will set up OpenOffice.org 3 Beta 2. You'll need to set up your own launchers to run it though since it doesn't create launchers for you. 

You may want to stick with OpenOffice.or 2.4, which comes with Ubuntu. I've had OOo3b2 crash on me enough when working with embeded images that I found it completely useless. Beta 1 was more stable, and I hope beta 3 is coming soon.

---

### Post by kaboodle_fish on 2008-08-20
> **jarome said:**
> I am new to Ubuntu and debian packages. I downloaded the OpenOffice 3.0 beta and untarred it into a set of directories. 
 
But if I go into the DEBS directory and do
apt-get install *.deb
it fails looking for a package that is in that directory.
 
So how does one do such installs?
 
Thanks,
Jim
 
Go here [http://tombuntu.com/index.php/2008/05/08/test-drive-openoffice-3-beta-in-ubuntu/](http://tombuntu.com/index.php/2008/05/08/test-drive-openoffice-3-beta-in-ubuntu/) and follow the instructions but change the file name to the new one that you have downloaded 
 
That worked for me last night and I have OpenOffice3.0 Beta2 now

---

### Post by coffeecat on 2008-08-20
> **DJ_Peng said:**
> They actually went way off standard for this. When a Linux user sees "deb" they think it's a package but this isn't, it's really a .tar.gz. It bugged the daylight out of me when I started trying the beta.

I'm glad I'm not the only one. :(

**jarome**, apt-get gives an error. Use the shell script that DJ_Peng refers to or kaboodle_fish's link.

---

### Post by jarome on 2008-08-20
I at first used file-roller, and it extracted things in the same way that tar did. :-(

---

### Post by jarome on 2008-08-20
Close, but it says all the packages are skipped:

jar@jarhp:~/download/BEB300_m3_native_packed-1_en-US.9328$ sudo sh update
[sudo] password for jar: 
Skipping deselected package ooobasis3.0-core06.
Skipping deselected package ooobasis3.0-dict-fr.
Skipping deselected package ooobasis3.0-en-us-base.
Skipping deselected package openoffice.org3-calc.
Skipping deselected package openoffice.org3-writer.
Skipping deselected package ooobasis3.0-headless.
Skipping deselected package ooobasis3.0-core05.
Skipping deselected package ooobasis3.0-images.
Skipping deselected package ooobasis3.0-en-us-writer.
Skipping deselected package ooobasis3.0-base.
Skipping deselected package ooobasis3.0-ooofonts.
Skipping deselected package ooobasis3.0-writer.
Skipping deselected package ooobasis3.0-en-us-draw.
Skipping deselected package ooobasis3.0-en-us-help.
Skipping deselected package openoffice.org3-base.
Skipping deselected package ooobasis3.0-core08.
Skipping deselected package ooobasis3.0-pyuno.
Skipping deselected package ooobasis3.0-en-us-onlineupd.
Skipping deselected package ooobasis3.0-draw.
Skipping deselected package ooobasis3.0-dict-en.
Skipping deselected package ooobasis3.0-core02.
Skipping deselected package ooobasis3.0-testtool.
Skipping deselected package ooobasis3.0-emailmerge.
Skipping deselected package ooobasis3.0-graphicfilter.
Skipping deselected package ooobasis3.0-core04.
Skipping deselected package ooobasis3.0-gnome-integration.
Skipping deselected package openoffice.org3-en-us.
Skipping deselected package ooobasis3.0-en-us-res.
Skipping deselected package ooobasis3.0-dict-es.
Skipping deselected package ooobasis3.0-math.
Skipping deselected package ooobasis3.0-core07.
Skipping deselected package ooobasis3.0-core01.
Skipping deselected package ooobasis3.0-ooolinguistic.
Skipping deselected package ooobasis3.0-calc.
Skipping deselected package ooobasis3.0-core03.
Skipping deselected package openoffice.org3-math.
Skipping deselected package ooobasis3.0-javafilter.
Skipping deselected package openoffice.org3.
Skipping deselected package openoffice.org3-impress.
Skipping deselected package ooobasis3.0-en-us-math.
Skipping deselected package ooobasis3.0-en-us-binfilter.
Skipping deselected package ooobasis3.0-xsltfilter.
Skipping deselected package openoffice.org3-draw.
Skipping deselected package ooobasis3.0-onlineupdate.
Skipping deselected package ooobasis3.0-kde-integration.
Skipping deselected package ooobasis3.0-en-us-calc.
Skipping deselected package ooobasis3.0-en-us-impress.
Skipping deselected package ooobasis3.0-binfilter.
Skipping deselected package openoffice.org-ure.
Skipping deselected package ooobasis3.0-en-us.
Skipping deselected package ooobasis3.0-impress.

---

### Post by jarome on 2008-08-20
That link worked. Thanks. I think I have beta 3 installed now. OO 3.0 is infinitely faster than 2.x on my spreadsheets, so this is a nust.

Thank you kaboodle_fish!

---

### Post by kaboodle_fish on 2008-08-20
No problem

Tombuntu is a good site, well worth putting in your bookmarks in my opinion.

---

### Post by ezsit on 2008-08-20
> cd Desktop/BEB...9328/DEBS
sudo apt-get install *deb

apt-get is a command for installing programs from repositories. To install individual .deb packages dpkg is the command to use:

sudo dpkg -i package-name.deb

---

### Post by kahlil88 on 2008-08-23
Do I really need to install all of the DEB packages? Is there a way to just upgrade what's already installed?

---

### Post by quixote on 2008-09-14
I tried to install RC1, and kept getting the stupid "unmet dependencies" BS.

What finally worked was, as DJ_Peng suggested:

cd to uppermost unpacked files dir named OOO-interminable-name/
run: sudo sh update
don't let any "skipping" messages worry you
then cd into the DEBS dir, and as the good folks above said,
run: sudo dpkg -i *.deb

And it does install.  However, when you try to start it up, it just crashes, tells you it's recovering the file, crashes again, and so on.  Not worth it.  Stick with OO 3.02b (second beta), [at tombuntu's site]("http://tombuntu.com/index.php/2008/05/08/test-drive-openoffice-3-beta-in-ubuntu/") as in kaboodle_fish's link earlier.

Honestly.  What is Sun thinking?  OO is a good product, and it's nice of them to help the community that has helped them.  But producing such a crappy *Release Candidate* is just unprofessional.

---

### Post by DJ_Peng on 2008-09-14
I upgraded to the RC yesterday and while I can get writer working the spreadsheet simply won't run. I'll have to try and chase that down in a day or two once I can clear some things from my todo list.

---

