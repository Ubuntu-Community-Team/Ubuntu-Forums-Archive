---
title: "OpenOffice 3.0 Installation Question."
date: 2008-11-24
forum: General Help
---

### Post by Roasted on 2008-11-24
So, I wanted OpenOffice 3.0. So I downloaded it from the web site. I got a folder with about 50 DEB's in it. Hmm, problem.

So I resorted to forums to see what I could do, and I was told to add a link to my third party software sources and run an update. Okay, done.

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

Thing is, my version of OpenOffice 3.0 is in some foreign language and I have NO clue where to change it. But these are the only directions I'm finding. Everywhere else I look people are simply linking to the web site I linked above.

What can I do?

I'm running 64 bit edition of Intrepid.

---

### Post by nvikram on 2008-11-24
Instead of installing from the open office main page, instead go to:

System > Administration > Software Sources

Go to the "Third-Party Software" tab

Click on Add and type this in
```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu/ intrepid main
```

Click on OK. It will ask you to reload software sources.

Then go to the update manager, and there should be the open office 3.0 packages for your system. Hope this helps :)

---

### Post by scouser73 on 2008-11-24
Here's an excellent tutorial on installing OpenOffice 3.
[http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

---

### Post by lyni on 2008-11-24
NVIKRAM  does that link download the 'official' oo3 open office or is it the ubuntu modified version?

---

### Post by TeXtonyx on 2008-11-24
Neither of the first two methods worked for me. I'm downloading
OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz from 
[http://download.openoffice.org/other.html](http://download.openoffice.org/other.html)

I'm going to try to use: sudo dpkg -i *.deb or  similar.
Yes, that is working, I changed into the /DEBS directory first.

---

### Post by ad_267 on 2008-11-24
It's a much better idea to install OpenOffice 3 using the PPA repository. That way you get automatic updates, launchers are created automatically, and it is much better integrated with the Gnome desktop. See [http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml). There are 64 bit packages available.

This is the method nvikram posted. Could you explain why it didn't work, instead of just saying that it didn't? There's no reason why it shouldn't work if you follow the steps correctly.

Edit: Sorry I didn't realise you weren't the OP who is using 8.10 64 bit. If you are using 8.04 then this won't work, you have to change the line to "deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main".

---

### Post by TeXtonyx on 2008-11-24
I just used this working method as of Monday Nov 24, provided at
[http://www.tectonic.co.za/?p=3363](http://www.tectonic.co.za/?p=3363)

The OOo installation asks you if you want to enable updates.

Also I downloaded and installed the java jre because the En-dict
complained and also  ooobasis3.0-xsltfilter_3.0.0-9_i386.deb

Yes, Third Party Software packages using the PPA repository was
set to Intrepid and I changed it to hardy and reloaded. 

The following was the step that was missing or maybe I overlooked
it in nvikram's howto, or maybe it's done automatically.

------------------------------------------------

"With that done you should have just one thing left to do: 
Install the desktop integration package. That should be in the 
DEBS folder: 

cd desktop-integration

From that folder install the package:

sudo dpkg -i openoffice.org3.0-debian-menus_3.0-9354_all.deb 

If everything works out you should be able to open 
OpenOffice.org 3.0 from the Applications menu on your desktop." 

-------------------------------------------------- 

Well, maybe the syntax nvikram provided included the step above
since it is a .deb in the /DEBS sub-directory. I'm just accustomed
to installing  *.foo from the directory where the files exist.

---

### Post by blazemore on 2008-11-24
Isn't there a script in the folder?
Untar the tarball.
cd to the directory
```
./update
``` I think that's what it's called.

---

### Post by TeXtonyx on 2008-11-24
> **blazemore said:**
> Isn't there a script in the folder?
Untar the tarball.
cd to the directory
```
./update
``` I think that's what it's called.

Yes, the tail of the update file reported,

--------------------------------

work
      # in our setup (at least not with kdesu)
      rpm -v --freshen `find "$BASEDIR"/RPMS -name '*.rpm'`
    elif [ -d "$BASEDIR/DEBS" ]; then
	  dpkg --install --selected-only --recursive "$BASEDIR"/DEBS
    elif [ -d "$BASEDIR/packages" ]; then
      update_pkg "$BASEDIR/packages"
    fi
  fi
else
  Usage
fi    

-----------------------------------------

TeX: So I suppose --recursive , means that the .deb file in the
/DEBS/desktop-integration sub-directory was selected for installation?

---

### Post by Roasted on 2008-11-24
As I said in the first post I made, I did add that ppa line to my third party sources for OOo3. 

The thing is, it came through in a different language. It seriously looks like wingdings font. So, I'm stuck.

So I need to change the language or else get the US version. But I don't understand why I didn't get the US version in the first place with the installation method I ran.

---

### Post by Roasted on 2008-11-24
I'm really dying here for the English version... if anybody can help...

---

### Post by TeXtonyx on 2008-11-25
> **Roasted said:**
> I'm really dying here for the English version... if anybody can help...

I mentioned how to do it in my contribution(s) to this thread. #7
This method will work for 8.10 also, I don't know why the other method 
didn't although the Third-Party method is not for the Ubuntu 8.04 
repository. I didn't read where you said you were using 8.10.

I used this method: [http://www.tectonic.co.za/?p=3363](http://www.tectonic.co.za/?p=3363)
I think you will need to remove your current OOo because its alien.

---------------------------------------

"First, remove your existing version of OpenOffice.org:

sudo apt-get remove openoffice*.*

Next, download a copy of OpenOffice.org 3.0 
(OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz worked for us) and 
extract the download:

tar -zxvf OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz "

[TeX: sudo dpkg -i -R is also good syntax for installing the *.deb]

------------------------------------------

Just follow the rest of the instructions. Here is the link to Sun

[http://download.openoffice.org/other.html](http://download.openoffice.org/other.html)

I'm going to make a screenshot and attach it.
Notice that you can also choose the English (en-US) Linux x64 deb download.

"Include the Java JRE with this download (This option is not 
available for Linux DEB and Mac OSX)"

TeX: That is why I also installed the java jre separately. The 
filename for the Sun download and the Tectonic download are the same.

[http://distribution.openoffice.org/mirrors/#archive](http://distribution.openoffice.org/mirrors/#archive)  This is another 
way to download the English OOo .deb file, pick a mirror from the U.S.A. 
for instance: U.S.A.  OSU OSL  http  ftp  S  C  L  D   /stable 3.0.0/

-----------------------------------------------------

[http://www.rebelzero.com/ubuntu/installing-ooo-300-onto-hardy-heron/27](http://www.rebelzero.com/ubuntu/installing-ooo-300-onto-hardy-heron/27)

"If you already have OpenOffice.org 2.4.1 installed through Ubuntu&#8217;s 
repos, you will need to remove it. One of the 3.0.0 packages (debian 
menus) has a conflict with one of the 2.4.1 packages, 
openoffice.org-core. Removing openoffice.org-core will also remove OO.o 
2.4.1 from your computer.  Remove OO.o 2.4.1 by using apt-get at the 
command line: 

sudo apt-get remove openoffice.org-core

You&#8217;ll see apt-get prompt you for removing the other 2.4.1 packages as 
well. Just hit enter and apt-get will do the rest. Proceed to Step 3b."

---------------------------------------------- 

TeX: So it seems like one has to remove the previously installed version
of OpenOffice, either 2.4 or in your case 3.0 because of the wrong language.

---

### Post by frankleeee on 2008-11-25
Ubuntu Tweak has a 3rd party section that will install OO3. It loads it into the update manager it is the launchpad repository, it installed in English for me.
[http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)

---

### Post by Pengwyn44 on 2008-11-26
I successfully installed 3.0 on Hardy using a DVD supplied by LinuxFormat magazine.
Only one problem - the dictionary is USA. How can I get an English UK dictionary?
Pengwyn44

---

### Post by TeXtonyx on 2008-11-26
> **Pengwyn44 said:**
> I successfully installed 3.0 on Hardy using a DVD supplied by LinuxFormat magazine.
Only one problem - the dictionary is USA. How can I get an English UK dictionary?
Pengwyn44

[http://extensions.services.openoffice.org/project/AustralianDictionary](http://extensions.services.openoffice.org/project/AustralianDictionary)

[http://extensions.services.openoffice.org/project/AustralianDictionary#comments](http://extensions.services.openoffice.org/project/AustralianDictionary#comments)

The best I could find was an Australian dictionary,
US English thesaurus and the GB English hyphenation dictionary.
I don't know if there is a difference between Windows and Linux
OOo dictionaries.

I also read this comment:

The US English version comes with a GB English dictionary. The interface 
will be in US English but you can create and spellcheck all your 
documents in GB English. I use a Canadian English dictionary with the US 
English version of OO.o 3.0.

---

### Post by Roasted on 2008-11-26
So, I downloaded the 64 bit Deb package for OpenOffice 3.

I extracted it, CD'd into the DEBS directory and ran sudo dpkg -i *.deb

What do I do next? I thought that was it but under apps-office, I only have "dictionary"

---

### Post by TeXtonyx on 2008-11-26
> **Roasted said:**
> So, I downloaded the 64 bit Deb package for OpenOffice 3.

I extracted it, CD'd into the DEBS directory and ran sudo dpkg -i *.deb

What do I do next? I thought that was it but under apps-office, I only have "dictionary"

I posted the link to the instructions I used on page 1, #7, of this
thread. That post also has the following step:

"With that done you should have just one thing left to do:
Install the desktop integration package. That should be in the
DEBS folder:

cd desktop-integration

From that folder install the package:

sudo dpkg -i openoffice.org3.0-debian-menus_3.0-9354_all.deb

If everything works out you should be able to open
OpenOffice.org 3.0 from the Applications menu on your desktop."

---

### Post by Roasted on 2008-11-26
Good news - it worked!

Bad news - it's still in wingdings style font.

Awesome.

And yes, I uninstalled the previous version of OpenOffice.
And yes, I downloaded the US English version of OOo 3.0.

---

### Post by notanxious on 2008-11-26
I have followed your instructions... And after cd desktop-inte...
and sudo dpkg -i openoffice.org3.0-debian-menus_3.0-9354_all.deb

I am still unable to see the application in the APP-Office tab

---

### Post by notanxious on 2008-11-26
anxiety@anxiety-desktop:~/Desktop/OOO300_m9_native_packed-1_en-US.9358/DEBS/desktop-integration$ sudo dpkg -i openoffice.org3.0-debian-menus_3.0-9354_all.deb
(Reading database ... 130785 files and directories currently installed.)
Preparing to replace openoffice.org-debian-menus 3.0-9354 (using openoffice.org3.0-debian-menus_3.0-9354_all.deb) ...
Unpacking replacement openoffice.org-debian-menus ...
Setting up openoffice.org-debian-menus (3.0-9354) ...

---

### Post by Skripka on 2008-11-26
> **notanxious said:**
> I have followed your instructions... And after cd desktop-inte...
and sudo dpkg -i openoffice.org3.0-debian-menus_3.0-9354_all.deb

I am still unable to see the application in the APP-Office tab

It **might** show up under "**other**".  I had this happen when I installed via repos.

---

### Post by notanxious on 2008-11-26
I don't have an 'Other' tab..?

---

### Post by Skripka on 2008-11-26
> **notanxious said:**
> I don't have an 'Other' tab..?

Or lost and found...it was listed under something other than "Office" on KDE4....I was stumped until I went into the menu editor digging -and found it off the beaten path.

---

### Post by Roasted on 2008-11-26
I'm sorry, but has OOo 3 been officially released? Is there a reason there isn't a "double click auto install" option without headaches? I can't ever recall having such an issue with OpenOffice...

---

### Post by notanxious on 2008-11-26
I just checked the menu editor and there is no sign of open office in any of the subdirectories... A little help here guys?

---

### Post by Skripka on 2008-11-26
> **Roasted said:**
> I'm sorry, but has OOo 3 been officially released? Is there a reason there isn't a "double click auto install" option without headaches? I can't ever recall having such an issue with OpenOffice...

Yes, but it is not in the official repos yet-only ppa's....and evidently they pulled OOo3 as it was getting borked by an update :confused:

---

### Post by Skripka on 2008-11-26
> **notanxious said:**
> I just checked the menu editor and there is no sign of open office in any of the subdirectories... A little help here guys?

Hmmmmmmmmm....


If you go to /usr/share/applications do you have any OOo app shortcuts listed?

---

### Post by fooman on 2008-11-26
Roasted...have you tried deleting the .openoffice.org folder in your home directory?

i would give that a shot.  maybe uninstall openoffice first,  then delete .openoffice.org...then reinstall openoffice.

---

### Post by notanxious on 2008-11-26
Yes the shortcuts are listed in [COLOR="Red"]red text?[/COLOR]

---

### Post by Skripka on 2008-11-26
> **notanxious said:**
> Yes the shortcuts are listed in [COLOR="Red"]red text?[/COLOR]

...and....what are they pointed at under Properties?  And if pointed at OOo3, do they actually work?

---

### Post by notanxious on 2008-11-26
/opt/openoffice.org3/share/xdg/writer.desktop
/opt/openoffice.org3/share/xdg/base.desktop
/opt/openoffice.org3/share/xdg/calc.desktop
/opt/openoffice.org3/share/xdg/draw.desktop
/opt/openoffice.org3/share/xdg/impress.desktop
/opt/openoffice.org3/share/xdg/math.desktop
/opt/openoffice.org3/share/xdg/printeradmin.desktop

---

### Post by notanxious on 2008-11-26
The Link "openoffice.org3-printeradmin.desktop" is Broken. Move it to Trash?

Seems like all links are broken

---

### Post by Skripka on 2008-11-26
> **notanxious said:**
> The Link "openoffice.org3-printeradmin.desktop" is Broken. Move it to Trash?

Seems like all links are broken

Don't gedlete things by hand yet,

Refer to Fooman's post(# 28 )....

---

### Post by notanxious on 2008-11-26
That's the method of my first attempt.. I added the new repositories for Hardy... Still nothing showing up in the update manager...

---

### Post by Skripka on 2008-11-26
> **notanxious said:**
> That's the method of my first attempt.. I added the new repositories for Hardy... Still nothing showing up in the update manager...

From what I gather, the OOo3 PPA repos are empty right now-as a result of an update which borked OOo3...and it seems as a precaution they pulled all the OOo3 debs off their repo temporarily.

I'd try going into Synaptic and (completely) removing all the OOo3 debs you installed, and then doing a reinstall that away (with the packages you downloaded)....most of them can be found by just searching for "OpenOffice" in Synaptic.


I'm running out of ideas :(


If all else fails, OOo2 is perfectly usable, until the PPA repos are back up.

---

### Post by TeXtonyx on 2008-11-27
This worked for me, including the last step. It is for I386 en-US

[http://www.tectonic.co.za/?p=3363](http://www.tectonic.co.za/?p=3363)

With that done you should have just one thing left to do: 
Install the desktop integration package. That should be in the 
DEBS folder:

cd desktop-integration

From that folder install the package:

sudo dpkg -i openoffice.org3.0-debian-menus_3.0-9354_all.deb 

If everything works out you should be able to open 
OpenOffice.org 3.0 from the Applications menu on your desktop."

---

### Post by TeXtonyx on 2008-11-27
> **Roasted said:**
> Good news - it worked!

Bad news - it's still in wingdings style font.

Awesome.

And yes, I uninstalled the previous version of OpenOffice.
And yes, I downloaded the US English version of OOo 3.0.

------------------------------------
close all open openoffice apps

open /opt/openoffice/program/soffice
select tools (4th menu)
select options (last menu)
select openoffice/view (first item at tree, then the 4th)
disable Use system fonts for user interface 
(unckeck the first checkbox below the 2 horizontal aligned combobox) 

press accept (the first button of 4 on the bottom of the window)
restart openoffice

TeX: I thought you said you had downloaded a foreign language version.

---

### Post by TeXtonyx on 2008-11-27
> **notanxious said:**
> I have followed your instructions... And after cd desktop-inte...
and sudo dpkg -i openoffice.org3.0-debian-menus_3.0-9354_all.deb

I am still unable to see the application in the APP-Office tab

Still true after rebooting? As I said it worked for me.
Also I installed the java jre but I don't know how important that is.

---

### Post by jdackle on 2008-11-27
> **Skripka said:**
> From what I gather, the OOo3 PPA repos are empty right now-as a result of an update which borked OOo3...and it seems as a precaution they pulled all the OOo3 debs off their repo temporarily.

I'd try going into Synaptic and (completely) removing all the OOo3 debs you installed, and then doing a reinstall that away (with the packages you downloaded)....most of them can be found by just searching for "OpenOffice" in Synaptic.


I'm running out of ideas :(


If all else fails, OOo2 is perfectly usable, until the PPA repos are back up.

Hi everyone,

I'm on Hardy.

I installed OOo3 about a week ago from [ftp://openoffice.caixamagica.pt/stable/3.0.0/OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz](ftp://openoffice.caixamagica.pt/stable/3.0.0/OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz) (it's the official Portuguese mirror for OpenOffice.org, the Portuguese version hadn't been released yet so I actually installed the English one - exactly the same as from the openoffice.org main site).
**TIP:** Use *dpkg -i** -R** *.deb* to automatically install the Debian menu .deb. ;)
**CLUE (?**): Are people who installed this way and having problems with the menu using KDE? The menu-links worked great for me on GNOME. Could it be a problem with integration with **KDE only?**

But now I've seen this **ppa** repository, I thought that'd be a much better way. 8)
Problem is, as already stated by someone else, I get nothing in the update manager (only OOo 2.4 currently intalled on my system).
I did check [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/hardy/main/binary-i386/](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/hardy/main/binary-i386/) and it is **empty**. So is [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/main/binary-i386/](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/main/binary-i386/)
If the reason for that is some kind of package fix... shouldn't the original be left there _until_ the fixed package is out? Isn't that how it's usually done? Doesn't making it otherwise kind of break the logic of a repo? :confused: (NOT being ironical!)

---

### Post by Skripka on 2008-11-27
> **jdackle said:**
> 
**CLUE (?**): Are people who installed this way and having problems with the menu using KDE? The menu-links worked great for me on GNOME. Could it be a problem with integration with **KDE only?**

But now I've seen this **ppa** repository, I thought that'd be a much better way. 8)
Problem is, as already stated by someone else, I get nothing in the update manager (only OOo 2.4 currently intalled on my system).
I did check [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/hardy/main/binary-i386/](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/hardy/main/binary-i386/) and it is **empty**. So is [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/main/binary-i386/](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/main/binary-i386/)
If the reason for that is some kind of package fix... shouldn't the original be left there _until_ the fixed package is out? Isn't that how it's usually done? Doesn't making it otherwise kind of break the logic of a repo? :confused: (NOT being ironical!)

I actually only had menu issues after ripping OOo3 debs off my system and switching to the repos...for some reason Adept (which has a reputation for being broken right now) chose to file the PPA repo OOo software as "Lost & Found" rather than "Office".

I don't know why they pulled OOo3 off their repo....I recall reading someone on *buntuforums saying something about a OOo-GNOME update b0rked OOo3--ergo as a precaution they pulled OOo3....this is 2nd hand rumourmongering on my part though.

To quote from the horses mouth:

[QUOTE=OOo3 repo]
The packages were buggy and crashed when openoffice.org-gnome was installed, they will be reuploaded when the bug has been resolved.
[/QUOTE]

---

### Post by Roasted on 2008-11-27
Considering the amount of confusing work involved with getting this to work, coupled with the fact I've tried every how-to guide on here twice with no luck, I'm going to hold off on OOo 3. I've been told (and agree, since I use it on Windows) that it's nothing that is a "must have" over 2.4 So, considering they pulled it from the repos due to an error, I'll happily wait until it's fixed and get it the easy way.

:guitar::guitar:

---

