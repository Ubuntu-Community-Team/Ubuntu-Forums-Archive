---
title: "KDE 3.5 final"
date: 2005-11-25
forum: General Help
---

### Post by Wizzard on 2005-11-25
Did anyone tried newer KDE than RC1? I found some new packages at kubuntu.org/packages two days ago and though that directory kde35 contains final version. Then they renamed it to non-kde35 and added another kde35 directory. Today it seems that they renamed kde35 to kde35rc2, but there is still no news on the KDE website. I added all the KDE repos to my souces list, but some packages could not be installed, but most of them did. It feels a little faster and KDE identifies itself as 3.5.
I welcome anyone's experiences with these latest versions.

---

### Post by DoeRayMe on 2005-11-25
Hmm and at the bottom of this page, they have RC2 known bugs, but no announcement was made

[https://wiki.ubuntu.com/KubuntuKDE35BetaKnownProblems](https://wiki.ubuntu.com/KubuntuKDE35BetaKnownProblems)

---

### Post by vh1 on 2005-11-25
I was waiting for word on this too

[the KDE ftp](ftp://ftp.kde.org/pub/kde/unstable/3.5-rc2) has had an RC2 folder for a few days now, but it just contains the sources, not the kubuntu and suse dirs like it normally does

maybe they're just building the packages and will announce when they're done?

---

### Post by JPatrick on 2005-11-25
Kubuntu packages are being tested - here's what you need to add to your /etc/apt/sources.list:

'deb [http://kubuntu.org/packages/kde35rc2](http://kubuntu.org/packages/kde35rc2) breezy main'

And then update and you should have 3.5 RC2 installed. :)

I'll make it clear that these packages are in testing and haven't been announced yet. (Have asked Riddell if I could post this tho.)

---

### Post by Wizzard on 2005-11-25
Well, it seems that they are really testing only. They already removed the "not-kde35" directory and the problems persist... At least RC2 is almost done.

---

### Post by Brando569 on 2005-11-26
i just went to kde.org a few hours ago to see if rc2 is out, im using rc1 and it seems really stable hasnt crashed or screwed up on me at all..

---

### Post by skyboy on 2005-11-26
Just upgraded to RC2, and it works like a charm. Didn't get any bug yet :)
it rocks !!

---

### Post by Wizzard on 2005-11-26
[QUOTE=skyboy]Just upgraded to RC2, and it works like a charm. Didn't get any bug yet :)
it rocks !![/QUOTE]

Dont you have any dependency problem or problem with upgrading some packages?

---

### Post by skyboy on 2005-11-26
i just had a problem with metabar, but I forced the installation of the new package (konq-plugin I think) , then sudo apt-get upgrade to finish the upgrade.
Otherwise, perfect

---

### Post by Wizzard on 2005-11-26
Yeah, I had to download a .deb file konq-plugins and install it with force, now it is all installed. I just don't know why I have a lot of packages marked as local or absolete in Kynaptic...

---

### Post by Paulus on 2005-11-26
Hey I've just installed KDE from gnome, for the 3.5 beta and release candidates should I add all the previous beta and RC resporitories to my souces.list?  or just the most recent 3.5RC2?

any advice would be appreciated. :)

---

### Post by JPatrick on 2005-11-26
Add the most recent one:

deb [http://kubuntu.org/packages/kde35rc2](http://kubuntu.org/packages/kde35rc2) breezy main

It's in Dapper now.

---

### Post by Firetech on 2005-11-26
I think RC2 was announced in one of the mailing lists (I got the announce somehow...)
It's not announced anywhere else though...

EDIT: It was announced in the kde-cvs-announce mailing list.

---

### Post by Paulus on 2005-11-26
thanks, so far my impressions are excellent.  Very smooth, fast and stable kompmgr (w/o shadows).  generally the fastest i've ever seen kde run.  very very good!

btw terminal sessions bug has gone, still no superkaramba installed by default,  but thats just cosmetic.

---

### Post by didit on 2005-11-26
I upraded kde last night. However, i found my kde gets slower. I have no idea whether it is caused by new XOrg or is because I enable EXA in xorg.conf get composite accelerated. But, i havent tried kompmgr yet. Btw, Is there any differences between these two? I mean xcompmgr and kompgr.

---

### Post by Paulus on 2005-11-26
xcompmgr is used with gnome, xfce etc.   kompmgr is the kde equivelent (hence the k), which is in my opinion more stable. 

btw to enable kompmgr right click on some windecco- like the one your reading now select "configure window behaviour" then select "Translucency" and the rest is intuitive!

---

### Post by didit on 2005-11-26
Oh oke, thanks for the answer :) . I'll try kompmgr then :D

---

### Post by vh1 on 2005-11-26
juk doesn't seem to remeber my column widths. and trying to set "resize column headers automatically" doesn't do anything

other than that I haven't noticed any problems.

---

### Post by skyboy on 2005-11-26
when translucency enabled, kopete's bubble message from system tray, when clicked on, crash the system totally !! any solution ?
Am i the only one having that trouble ??

---

### Post by ewschone on 2005-11-26
My sound still doesnt work properly. I just turned off all system sounds which ofcourse isnt a real solution :o . Sound in XMMS and Amarok and such works fine... Can anyone give me a hint ?

---

### Post by ltmon on 2005-11-26
[QUOTE=ewschone]My sound still doesnt work properly. I just turned off all system sounds which ofcourse isnt a real solution :o . Sound in XMMS and Amarok and such works fine... Can anyone give me a hint ?[/QUOTE]

I stopped dealing with aRts (the official sound system) altogether and did the following:

1. install mplayer
2. kmenu -> System Settings -> Sound & Multimedia -> System Notifications
3. Then click on "Player Settings" and "Use an external player".  Enter "mplayer" into the dialog box.

This should be a lot more workable that aRts ever is.

L.

---

### Post by Manny C on 2005-11-26
Works like a charm for me. The panel does not redraw itself under certain circumstances. Will be filing a bug.

Furthermore, the new Plastik window decor has been revamped and looks very slick.;)

---

### Post by artnay on 2005-11-26
- kded keeps crashing on me (probably there's a bug in kat 0.6.4 with sqlite 3.2.1, should test it on another machine and ubuntu's 0.6.3 before filing a bug report), I get error msg: yaddayadda *** glibc detected *** malloc(): memory corruption (fast) yaddayadda

- automounting is still broken with HAL or ivman, needed to configure /etc/fstab in order to get iPod working. GNOME handels all hotplug devices correctly.

- mouse gestures in konqueror go to default values every logon time (can be activated via kcontrol -> disabling global gestures and then activating). mouse gestures still broken on JS pop-ups. no undo action after closing a tab. :( (all those do happen wheter I'm surfing the web or local/remote file system)

umh, what else? Breezy 5.10 and a few kernels tried, no luck yet. in spite of the problems, KDE 3.5 is the best DE that's available on GNU/Linux (a bit flaming in the end doesn't hurt, now does it?) Thanks!

EDIT: Upgrading both libsqlite3 and sqlite3 to 3.2.7 only made things worse. Kded crashes now every 5 secs, not funny at all. Any suggestions? "File a bug report?" ;)

---

### Post by lerrup on 2005-11-27
[QUOTE=ewschone]My sound still doesnt work properly. I just turned off all system sounds which ofcourse isnt a real solution :o . Sound in XMMS and Amarok and such works fine... Can anyone give me a hint ?[/QUOTE]

I had the same problem with rc1 and found that going into system settings=>sound & multimedia=>hardware and changing the select audio device to "autodetect" let the audio work properly.

---

### Post by ewschone on 2005-11-27
[QUOTE=ltmon]I stopped dealing with aRts (the official sound system) altogether and did the following:

1. install mplayer
2. kmenu -> System Settings -> Sound & Multimedia -> System Notifications
3. Then click on "Player Settings" and "Use an external player".  Enter "mplayer" into the dialog box.

This should be a lot more workable that aRts ever is.

L.[/QUOTE]

/cheer 

Thanks a lot for this one, it was getting really annoying, wish i had seen this option earlier. Someone should put this in an FAQ somewhere :rolleyes: 

:D

---

### Post by ewschone on 2005-11-27
[QUOTE=lerrup]I had the same problem with rc1 and found that going into system settings=>sound & multimedia=>hardware and changing the select audio device to "autodetect" let the audio work properly.[/QUOTE]

This didnt work for me :(. The other option did work though, so i am happy.

---

### Post by oobuntoo on 2005-11-27
There is blog that claims that KDE 3.5 RC2 IS the 3.5 final, pending name change only. You can read it at [http://digg.com/linux_unix/KDE_3.5.0_final_silently_released]("http://digg.com/linux_unix/KDE_3.5.0_final_silently_released")

---

### Post by artnay on 2005-11-27
To reply to myself: it's not a bug in KDE 3.5, it's a bug with kat and sqlite3. Well, it's a bug in Debian's/Ubuntu's sqlite3 package. More information [here]("http://kat.mandriva.com/index.php?option=com_simpleboard&Itemid=26&func=view&id=46&catid=7") [mandriva.com]. I guess I go for SVN version first, and if that doesn't work, just grab the copy of sqlite3, compile it and mess your system. ;)

EDIT: Ok, the SVN version won't even complete as it doesn't make katdaemon or kat. Tried compiling sqlite3 but even that didn't do the trick. I guess I've fooled around enough already, something is very broken with kat at the moment.

---

### Post by Wizzard on 2005-11-29
At last, KDE 3.5 is released at [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) :cool:

---

### Post by GoldBuggie on 2005-11-29
seesms rc2 and final were the same. I get no upgrade at all

---

### Post by dentaku65 on 2005-11-29
[QUOTE=GoldBuggie]seesms rc2 and final were the same. I get no upgrade at all[/QUOTE]

yes they are the same, same files and same dates

---

### Post by atoponce on 2005-11-29
[quote=Wizzard]Did anyone tried newer KDE than RC1? I found some new packages at kubuntu.org/packages two days ago and though that directory kde35 contains final version. Then they renamed it to non-kde35 and added another kde35 directory. Today it seems that they renamed kde35 to kde35rc2, but there is still no news on the KDE website. I added all the KDE repos to my souces list, but some packages could not be installed, but most of them did. It feels a little faster and KDE identifies itself as 3.5.
I welcome anyone's experiences with these latest versions.[/quote] 
I have heard that Konqueror in KDE 3.5 passes the [Acid2 test]("http://www.webstandards.org/act/acid2").  Can anyone confirm?

---

### Post by haaglin on 2005-11-29
[QUOTE=atoponce]I have heard that Konqueror in KDE 3.5 passes the [Acid2 test]("http://www.webstandards.org/act/acid2").  Can anyone confirm?[/QUOTE]
It does.

---

### Post by atoponce on 2005-11-29
[quote=haaglin]It does.[/quote]

Sweet!  First Safari, then Konqueror, now Opera 9.  When is Firefox going to join the race?

---

### Post by Jeff Eklund on 2005-11-29
[QUOTE=atoponce]Sweet!  First Safari, then Konqueror, now Opera 9.  When is Firefox going to join the race?[/QUOTE]
AFAIK, Konqueror passed the Acid2-test a while ago (before Safari), and since Safari uses KHTML and KJS for its rendering, the konqueror team should be held responsible for Safari passing the test. I might be wrong, if so can anyone correct me?

---

### Post by e45rpm on 2005-11-29
How do I add a repository to Ubuntu 5.10 so that I can install KDE 3.5?

**UPDATE:**
Ahh, I got it.  Add:
> deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main
To the repository in the Synaptics package manager.

---

### Post by tikal26 on 2005-11-29
KDE 3.5 has been released. You can download the KDE packages from any of these sources (add to /etc/apt/sources.list):

These packages have been digitally signed using Jonathan Riddell's key. A copy of they key is also kept on people.ubuntu.com for verification. To add this key do:

 wget [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg)
 sudo apt-key add kubuntu-packages-jriddell-key.gpg

Kubuntu 5.10 (Breezy)

    * deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main


or you can go adept and go to manage my sources or repos. (I am not at home now) and it's pretty much it askes you for the url.

---

### Post by atoponce on 2005-11-29
[quote=Jeff Eklund]AFAIK, Konqueror passed the Acid2-test a while ago (before Safari), and since Safari uses KHTML and KJS for its rendering, the konqueror team should be held responsible for Safari passing the test. I might be wrong, if so can anyone correct me?[/quote]

[Dave Hyatt]("http://webkit.opendarwin.org/blog/") fixed the Safari code, [making Safari first to pass the test]("http://www.webstandards.org/buzz/archive/2005_04.html").  Becuase Safari uses the KHTML rendering engine from Konqueror, the KDE team borrowed the code that Dave fixed and applied it to Konqueror making it the second browser to pass Acid2.

---

### Post by jadugarr on 2005-11-29
[QUOTE=tikal26]KDE 3.5 has been released. You can download the KDE packages from any of these sources (add to /etc/apt/sources.list):

These packages have been digitally signed using Jonathan Riddell's key. A copy of they key is also kept on people.ubuntu.com for verification. To add this key do:

 wget [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg)
 sudo apt-key add kubuntu-packages-jriddell-key.gpg

Kubuntu 5.10 (Breezy)

    * deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main


or you can go adept and go to manage my sources or repos. (I am not at home now) and it's pretty much it askes you for the url.[/QUOTE]

Woot, upgrading now :).

---

### Post by jounihat on 2005-11-29
Does anyone know when will the PPC version be available? And have they finally fixed the annoying KDED crash with video-DVDs?

---

### Post by JPatrick on 2005-12-08
PPC verison is being made.

---

### Post by uten on 2005-12-12
i get an error installing:
Preconfiguring packages ...
(Reading database ... 123008 files and directories currently installed.)
Preparing to replace konq-plugins 4:3.4.3-0ubuntu1 (using .../konq-plugins_4%3a3.5.0-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement konq-plugins ...
dpkg: error processing /var/cache/apt/archives/konq-plugins_4%3a3.5.0-0ubuntu0breezy1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kde3/konqsidebar_metabar.la', which is also in package metabar
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/konq-plugins_4%3a3.5.0-0ubuntu0breezy1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


what does this even mean? from what i can see its an error overwriting files, but the thing is why cant it replace them?

---

### Post by Zaventh on 2005-12-12
odd... try installing it from runlevel 3?

---

### Post by skyboy on 2005-12-12
[QUOTE=uten]i get an error installing:
Preconfiguring packages ...
(Reading database ... 123008 files and directories currently installed.)
Preparing to replace konq-plugins 4:3.4.3-0ubuntu1 (using .../konq-plugins_4%3a3.5.0-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement konq-plugins ...
dpkg: error processing /var/cache/apt/archives/konq-plugins_4%3a3.5.0-0ubuntu0breezy1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kde3/konqsidebar_metabar.la', which is also in package metabar
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/konq-plugins_4%3a3.5.0-0ubuntu0breezy1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


what does this even mean? from what i can see its an error overwriting files, but the thing is why cant it replace them?[/QUOTE]

do :
```

sudo dpkg -i --force-overwrite /var/cache/apt/archives/konq-plugins_4%3a3.5.0-0ubuntu0breezy1_i386.deb

```
i add the same problem.

---

