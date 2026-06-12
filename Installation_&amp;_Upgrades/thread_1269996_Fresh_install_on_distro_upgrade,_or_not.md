---
title: "Fresh install on distro upgrade, or not?"
date: 2009-09-19
forum: Installation &amp; Upgrades
---

### Post by humphreybc on 2009-09-19
I'm thinking of reinstalling my whole system when each new release comes out, and just backing up my home directory then copying it over to the new installation. But I have a few questions regarding this:


1) When I do a fresh install, obviously I won't have all my original software. When I copy over my old home folder, does it have a list of software that I had installed and will Ubuntu download all the packages of the old software? Does it do this after you restart or run apt-get update?

2) Will my panel, background, font, appearance settings all be restored?

3) What about my proxy settings?

4) What will happen to programs that I didn't install through the repositories, such as Google Earth, Skype, Picasa, Google Chrome etc...

5) My wine and wine-doors set up is very complicated and messy, but it works... what will happen to this? Will I have to re-install wine and Office 2007 and Photoshop/Dreamweaver etc?

6) What about my virtualbox Windows XP computer?

7) Are there any real benefits associated with doing a complete fresh install when each release comes out, instead of just upgrading?


Thanks,
Benjamin


---------------

---

### Post by stlsaint on 2009-09-19
i will try and answer all questions to the best of my ability...
1)backing up the home folder will not cause ubuntu to download all programs byitself upon fresh install...you can try and go thru synap and in the file tab choose save markings and it will create a document that synap can read. not sure about going from jaunty to karmic using that tho.
2)no your desktop will be the default that comes with the distro of your choosing...you will have to change all that back to the way you want it.
3)proxy also must be changed back
4)my suggestion is to save the sources.list so that you will now what .deb's you had and also go thru sources manager to save the keys you added because yes you will need to reinstall these!
5) yes those too must be configured again.
6)vbox is in /home under .virtualbox so it will be saved via a full backup of home.
7) yes there are benefits to doing fresh install...1) clean slate...no scattered packages floating around you may have missed. 2) fresh install is much "cleaner" compared to an upgrade which has a high chance of cause issues.

Overall i recommend you make your /home a seperate partition at installation so that whenever you want to re-install you can without touching your files, music, pics etc etc! there are many howtos on this. you can see my sig for installation directions.
Hope this helped.

---

### Post by earthpigg on 2009-09-19
> I'm thinking of reinstalling my whole system when each new release comes out, and just backing up my home directory then copying it over to the new installation. 

that's what i do.

> 1) When I do a fresh install, obviously I won't have all my original software. When I copy over my old home folder, does it have a list of software that I had installed and will Ubuntu download all the packages of the old software? Does it do this after you restart or run apt-get update?

no. but when you install the software and run it for the first time, it will look for the dotfiles, find they already exist, and use them. dotfiles are the hidden files/folders in your /home that start with a dot (.) and contain config options and whatnot.
> 
2) Will my panel, background, font, appearance settings all be restored?

yes. the dotfile for most of that is ~/.gconf and its subdirectories.

> 3) What about my proxy settings?

im not sure, but i can tell you how to find out:

if you create a new user on your existing install and your proxy settings are kept, then the answer to the question is no. 

if you create a new user on your existing system and the proxy settings are *not* kept, then that means the config stuff for that is saved in your /home folder, which means it will be backed up/restored by the method we are discussing.

> 4) What will happen to programs that I didn't install through the repositories, such as Google Earth, Skype, Picasa, Google Chrome etc...

you will need to download/install them again. but, assuming they are designed the same way 99.9999% of linux userland programs are, the same thing regarding the settings will apply as in question #1 and #3.

> 5) My wine and wine-doors set up is very complicated and messy, but it works... what will happen to this? Will I have to re-install wine and Office 2007 and Photoshop/Dreamweaver etc?

see #3 for the test you want to run.

> 6) What about my virtualbox Windows XP computer?

i know from experience this is saved in /home, but the test outlined in #3 can apply here if you want to test for yourself.

> 7) Are there any real benefits associated with doing a complete fresh install when each release comes out, instead of just upgrading?

an upgrade will **probably** work and not break anything. over 50% of the time.

a fresh install **will** work.

in rare circumstances, a newer version of a given program may be unable to read dotfiles from previous versions of that program. in that case, hopefully it will (like firefox) have a "i found information from an older version of myself. use settings from previous version of this program?" option to import it. if not (and this is *very* rare) than you will be SOL.




now that your questions are answered, i will tell you what i do:

i back up my entire /home, do a fresh install, then *selectively* restore the settings from *certain* programs.

just to de-clutter my /home.

---

### Post by oldfred on 2009-09-19
I created a fresh install of 64 bit since I use 32bit and wanted to see if I would have any issues with a clean install and with the 64 bit version. I did the package list and reimport, but found I was reimporting some old packages like python 2.4 & 2.5 which I did not want. Next time I may manually select or edit the package list. Totally obsolete packages do not get updated or I should have done a houseclean before saving the package list.
I also backup separately many config files that I have edited. I would not restore these but may want to refer to them for settings. I found my updates kept settings that are now not optimal and kept a lot of Nvidia files that gave me problems when the clean install worked immediately.

---

