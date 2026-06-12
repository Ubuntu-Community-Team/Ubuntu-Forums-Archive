---
title: "Recent troubles with OpenOffice 3 in Intrepid Ibex, after updates"
date: 2008-11-25
forum: General Help
---

### Post by HPVOHHR on 2008-11-25
Recently Installed OpenOffice 3.0 in Intrepid Ibex as follows:
[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)
(add OpenOffice repositories in 3rd party apps of software sources)

New updates for OpenOffice showed up this evening.  Thinking nothing of it, I went ahead and installed the updates.

Now, when I open any of the OpenOffice 3 applications, I get the following dialogue box error:

"Openoffice.org 3.0 Fatal Error - The application cannot be started"

Has anyone else seen this?  Any ideas?

Thanks for any assistance.

---

### Post by OrangeCrate on 2008-11-25
You installed security updates for 2.4

[http://ubuntuforums.org/forumdisplay.php?f=13](http://ubuntuforums.org/forumdisplay.php?f=13)

I could be wrong, but, I don't believe there's anything you can to do, but reinstall 3.0

---

### Post by HPVOHHR on 2008-11-25
d'oh... silly me.  I should pay more attention to the list of updates.

What is the best method for me to uninstall & then reinstall 3.0?

---

### Post by druhboruch on 2008-11-25
Same problem here.
Packages in ppa repo are broken.
Just wait for a fix.

---

### Post by TeXtonyx on 2008-11-25
[http://www.tectonic.co.za/?p=3363](http://www.tectonic.co.za/?p=3363)
sudo apt-get remove openoffice*.*

I used the method provided on this webpage to install OOo, but I've
seen other methods on the forum.

---

### Post by yugrotavele on 2008-11-25
> **druhboruch said:**
> Same problem here.
Packages in ppa repo are broken.
Just wait for a fix.

If you uninstall the openoffice.org-gnome package openoffice will run without errors.
sudo apt-get remove openoffice.org-gnome

I found this in another thread but now I can't find it to provide the link! :confused:

---

### Post by m.musashi on 2008-11-26
Just to clarify, OO.o v3 updates are broken if you are using the PPA repo. Is this correct? I attempted to install updates tonight and get an error about not being able to download them. Hopefully this means they are aware and took them down to prevent further issues.

---

### Post by accesshater on 2008-11-26
> **yugrotavele said:**
> If you uninstall the openoffice.org-gnome package openoffice will run without errors.
sudo apt-get remove openoffice.org-gnome

I found this in another thread but now I can't find it to provide the link! :confused:

Thanx this worked for me. =)

---

### Post by ivan0921 on 2008-11-26
Thanks, your suggestion worked for me.

---

### Post by Yeti can't ski on 2008-11-26
> **yugrotavele said:**
> If you uninstall the openoffice.org-gnome package openoffice will run without errors.
sudo apt-get remove openoffice.org-gnome


Same problem. Perfect and simple solution. Thanks so much. 

Does anyone knows if the removal of gnome openoffice prevents new "accidental" downloads of updates for OOO 2.4?

---

### Post by jakenn-linux on 2008-11-26
> **accesshater said:**
> Thanx this worked for me. =)

And it worked for me just as well.  The "Forum" is the best tech support anywhere.

---

### Post by yosumi on 2008-11-26
I should have search before uninstalling. now i have to reinstall Openoffice 3. XD

---

### Post by HotShotDJ on 2008-11-26
> **yugrotavele said:**
> If you uninstall the openoffice.org-gnome package openoffice will run without errors.
sudo apt-get remove openoffice.org-gnomeExcellent.  You saved me from hours of pulling out my hair.  Just to confirm, here is the "official" notification of the issue:  [https://launchpad.net/~openoffice-pkgs/+archive](https://launchpad.net/~openoffice-pkgs/+archive)

---

### Post by chazpaw on 2008-11-26
I removed openoffice.org-gnome but now openOffice crashes, and will not start.

---

### Post by accesshater on 2008-11-26
> **chazpaw said:**
> I removed openoffice.org-gnome but now openOffice crashes, and will not start.

you can try to remove openoffice and install 2.4 from the repos. Or download 3.0 from the openoffice.org site.

3.0 from the repos seems to be broken. Tnx for the link HotShotDJ =)

---

### Post by chazpaw on 2008-11-26
> **accesshater said:**
> you can try to remove openoffice and install 2.4 from the repos. Or download 3.0 from the openoffice.org site.

3.0 from the repos seems to be broken. Tnx for the link HotShotDJ =)

I found a solution. I uninstalled office packages, removed openoffice from third party repositories and reinstalled openOffice 2.4. Now it is working.

I will try to upgrade back to 3.0 after the problem is fixed.

Thanks.

---

### Post by HPVOHHR on 2008-11-26
> **yugrotavele said:**
> If you uninstall the openoffice.org-gnome package openoffice will run without errors.
sudo apt-get remove openoffice.org-gnome

I found this in another thread but now I can't find it to provide the link! :confused:

Thank you!  This worked for me too.  Much appreciated.

---

### Post by tich on 2008-11-26
removing openoffice.org-gnome worked for me too!  

what does the package do?

---

### Post by xiphosurus on 2008-11-26
it's the interface between gnome and OO. if u click on open file, u wont see the gnome interface to view files. u also lose gtk themes. just uglier but will do for now.

---

### Post by yugrotavele on 2008-11-27
> **xiphosurus said:**
> it's the interface between gnome and OO. if u click on open file, u wont see the gnome interface to view files. u also lose gtk themes. just uglier but will do for now.

The openoffice.org-gtk is a separate package although you may lose the gtk themes in Openoffice. I plan to reinstall the openoffice.org-gnome package when the current problems are fixed.

---

### Post by yugrotavele on 2008-11-27
> **HotShotDJ said:**
> Excellent.  You saved me from hours of pulling out my hair.  Just to confirm, here is the "official" notification of the issue:  [https://launchpad.net/~openoffice-pkgs/+archive](https://launchpad.net/~openoffice-pkgs/+archive)

Yup, that was the link!

---

### Post by zika on 2008-11-27
> **chazpaw said:**
> I found a solution. I uninstalled office packages, removed openoffice from third party repositories and reinstalled openOffice 2.4. Now it is working.

I will try to upgrade back to 3.0 after the problem is fixed.

Thanks.

please, can You be more specific how did You uninstall office packages. I've been playing whole day and no success.

i've tried reinstalling from several files from several url-s but ... :(

openoffice.org-gnome is not installed on my machine ...

---

### Post by Popoi on 2008-11-28
I hope they fix the problem soon.

---

### Post by HotShotDJ on 2008-12-08
> **Popoi said:**
> I hope they fix the problem soon.New OpenOffice packages just hit the Scribblers repository for Intrepid.  As soon as my video project finishes rendering, I'm going to upgrade and see if it works!

---

### Post by caraboy on 2008-12-09
> **HotShotDJ said:**
> New OpenOffice packages just hit the Scribblers repository for Intrepid.  As soon as my video project finishes rendering, I'm going to upgrade and see if it works!


I uninstalled OpenOffice3 using this command:
[php]sudo apt-get remove openoffice*.*[/php]Then I installed the latest package using:
[php] sudo apt-get install openoffice.org[/php]Now it works, I can run the updater with no problems.
Hope it works for you.

---

### Post by aztalon on 2008-12-09
> **caraboy said:**
> I uninstalled OpenOffice3 using this command:
[php]sudo apt-get remove openoffice*.*[/php]Then I installed the latest package using:
[php] sudo apt-get install openoffice.org[/php]Now it works, I can run the updater with no problems.
Hope it works for you.

That worked for me!!

Thanks!

---

### Post by frankleeee on 2008-12-09
> **caraboy said:**
> I uninstalled OpenOffice3 using this command:
[php]sudo apt-get remove openoffice*.*[/php]Then I installed the latest package using:
[php] sudo apt-get install openoffice.org[/php]Now it works, I can run the updater with no problems.
Hope it works for you.

Thanks for this valuable info on clearing the OO 3 I had installed from add remove after deleting the OO 2.4 when the ppa download was not working for some reason on a laptop, while working fine on two other computers.

---

### Post by fragos on 2008-12-09
The OO 3 I got before it was removed from the repositories updated today.

---

### Post by ashwinhgtx on 2008-12-10
I am on Kubuntu 8.10 and OpenOffice 3.0 broke yesterday after I installed some updates. It shows me a box asking me if I want to recover an untitled document. It crashes if I hit either cancel or OK. How do I fix this?

---

### Post by caraboy on 2008-12-10
> **ashwinhgtx said:**
> I am on Kubuntu 8.10 and OpenOffice 3.0 broke yesterday after I installed some updates. It shows me a box asking me if I want to recover an untitled document. It crashes if I hit either cancel or OK. How do I fix this?

Did you try to remove and uninstall OO3, like I did in my post? Try purging the package to remove also the config files, like this:

[php]sudo apt-get --purge remove openoffice*.* [/php]Beware, first read what is going to uninstall, you must not remove the metapackage ubuntu-dekstop!! There should be only OO3 related packages selected.

Run some cleaning:
[php]sudo apt-get autoremove && apt-get autoclean && apt-get clean[/php]Then, as I stated 3 posts above, reinstall the latest OO3 from launchpad:

[php]sudo apt-get install openoffice.org  [/php]Just tested it again on another computer, and OO3 now works.

---

### Post by ashwinhgtx on 2008-12-10
> **caraboy said:**
> Did you try to remove and uninstall OO3, like I did in my post? Try purging the package to remove also the config files, like this:

[php]sudo apt-get --purge remove openoffice*.* [/php]Beware, first read what is going to uninstall, you must not remove the metapackage ubuntu-dekstop!! There should be only OO3 related packages selected.

Run some cleaning:
[php]sudo apt-get autoremove && apt-get autoclean && apt-get clean[/php]Then, as I stated 3 posts above, reinstall the latest OO3 from launchpad:

[php]sudo apt-get install openoffice.org  [/php]Just tested it again on another computer, and OO3 now works.

I did that. Now OO3 works but the menus only have text and no icons. Plus it's as ugly as hell. I had upgraded from 2.4 to 3.0 using instructions from softpedia:
[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

I had made some edits in my sources list according to what the site said. Is this the cause of the problems? Am i installing OO3 from the wrong repositories now?
And why exactly did those updates break my awesome OO3 install???

---

### Post by ashwinhgtx on 2008-12-10
I tried installing the openoffice.org-kde package thinking that would give me my icons back. It also installed openoffice.org-style-crystal stating it as a dependency. 
Now I am back to square one. The dialogue box for recovering an untitled document comes up and then the apllication quits no matter what i do...

What am i doing wrong here? Advice guys??
Ummm...did i just kill this thread?? :confused:

---

### Post by MistralWind on 2008-12-10
> **ashwinhgtx said:**
> I tried installing the openoffice.org-kde package thinking that would give me my icons back. It also installed openoffice.org-style-crystal stating it as a dependency. 
Now I am back to square one. The dialogue box for recovering an untitled document comes up and then the apllication quits no matter what i do...

What am i doing wrong here? Advice guys??
Ummm...did i just kill this thread?? :confused:
Judging from what I've read so far and the problems I'm having myself, it has something to do with how OpenOffice is interacting with the OS integration packages, openoffice-kde and openoffice-gnome. If you install either of those packages, OpenOffice will crash as soon as you open it. When I uninstalled just openoffice-kde, I at least got the thing running again.

I got my icons back when I installed the style packages, and it works -- but without the KDE-style menus and colors I like. :(

---

### Post by 4logon on 2008-12-10
hi, the problem is simple to fix. there is a bug in openoffice.org-kde_3.0.0-6_i386.deb.

with these steps
A) Install ooo 3 from PPA with your paket-manager
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
B) uninstall openoffice.org-kde_3.0.0-6_i386.deb with your paket-manager
C) download old version of these package from: [ftp://194.94.120.8/pub/debian/pool/main/o/openoffice.org/openoffice.org-kde_3.0.0-5_i386.deb](ftp://194.94.120.8/pub/debian/pool/main/o/openoffice.org/openoffice.org-kde_3.0.0-5_i386.deb)
D) install these package with dpkg as follow...
dpkg -i --force-all  openoffice.org-kde_3.0.0-5_i386.deb

now you are ready to take off...
bye wolfgang.:guitar:

---

### Post by MistralWind on 2008-12-10
> **4logon said:**
> hi, the problem is simple to fix. there is a bug in openoffice.org-kde_3.0.0-6_i386.deb.

with these steps
A) Install ooo 3 from PPA with your paket-manager
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
B) uninstall openoffice.org-kde_3.0.0-6_i386.deb with your paket-manager
C) download old version of these package from: [ftp://194.94.120.8/pub/debian/pool/main/o/openoffice.org/openoffice.org-kde_3.0.0-5_i386.deb](ftp://194.94.120.8/pub/debian/pool/main/o/openoffice.org/openoffice.org-kde_3.0.0-5_i386.deb)
D) install these package with dpkg as follow...
dpkg -i --force-all  openoffice.org-kde_3.0.0-5_i386.deb

now you are ready to take off...
bye wolfgang.:guitar:
Well, that does fix the openoffice-kde issue, and it's nice to see OpenOffice looking and working like it should. Unfortunately, when I went to install something else in Synaptic, it listed the openoffice and openoffice-kde packages as broken. I won't let me do anything unless I upgrade the latter to the newer [non-functioning] version.

---

### Post by alakin on 2008-12-10
I have not yet installed any OOo packages yet, I have been waiting to install OOo3. Having found this thread I have added the launchpad repo to my sources list and ran an update. Sure enough, OOo3 is now there. When I go to run the installation I get a warning that several of the packages are not authenticated. Is this correct? Following the warning I have still not installed anything.

BTW: I am running Xunbuntu Intrepid so I guess I will not experience some of the KDE and Gnome issues that others have encountered?

Alan

---

### Post by frankleeee on 2008-12-10
> **alakin said:**
> I have not yet installed any OOo packages yet, I have been waiting to install OOo3. Having found this thread I have added the launchpad repo to my sources list and ran an update. Sure enough, OOo3 is now there. When I go to run the installation I get a warning that several of the packages are not authenticated. Is this correct? Following the warning I have still not installed anything.

BTW: I am running Xunbuntu Intrepid so I guess I will not experience some of the KDE and Gnome issues that others have encountered?

Alan

It is a 3rd party download you will see this at times, but launchpad is a reputable source, I have 3 computers running the 003 from them.

---

### Post by lanzen on 2008-12-10
Right, so the hack wolfgang suggested worked fine and yes, I've got two packages marked as broken. If I try updating Adept/Synaptic want to fix these and update to the buggy openoffice.org.kde launchpad package; if I want a usable OpenOffice 3 I'll have to forget about upgrading for a while.

Well... now this needs to be sorted out!  ;)

Thanks anyway.

---

### Post by zika on 2008-12-11
It seems that we **must** say that the people from Ubuntu were **right** when they did not include Oo3 in Intrepid and that there is a reason Oo3 is **not** in the official repositories yet. Launchpad upgrade proved itself to be very problematic and, now, I feel very stupid that I have tried it. I suspect that I will not be able to upgrade as easily as I would have that I have just waited Ubuntu repositories version. *_Lesson learned_*. When I try launchpad repo I get warning that I will get only partial upgrade and (as other threads confirm, I did not embark on that Titanic) only partial Oo3 installation.

---

### Post by frankleeee on 2008-12-11
OO3 is actually in add remove but you have to add gtk to get the systray quick-load and the English and British/help in synaptic to get the help section working. This worked in Ubuntu intrepid I don't know about kde or others.

---

### Post by lanzen on 2008-12-11
I still think the new openoffice.org-kde is the source of our problems; the old one works fine.

Anyway, I have downgraded to 2.4 and installed Sun's OOo3 in /opt. They live happily together and I wonder why I didn't do that sooner.

---

### Post by 4logon on 2008-12-12
hi, 

there is another (better way) to fix the kde-problem:

A) Install ooo 3 from PPA with your paket-manager
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
B) also install openoffice.org-kde_3.0.0-6_i386.deb with your paket-manager
C) download the old version of these package from: [ftp://194.94.120.8/pub/debian/pool/main/o/openoffice.org/openoffice.org-kde_3.0.0-5_i386.deb](ftp://194.94.120.8/pub/debian/pool/main/o/openoffice.org/openoffice.org-kde_3.0.0-5_i386.deb)
D) extract the files kdebe1.uno.so and libvclplug_kdeli.so from these package
E) replace the two files in folder /usr/lib/openoffice/basis3.0/program (rename the existing files befor)

now you can use openoffice without having problem with the package-management.

bye wolfgang.:guitar:

---

### Post by zika on 2008-12-12
What about the situation when You get warning that it will make only partial upgrade? On a second computer that is for backup purposes I forgot to check out ppa repositories for OO3. Today I started update and got that warning. Of course, I checked them out and did the regular update. But, what if I have said Yes? Did anybody try that road? Is there a way I can get update from ppa and still be OK with regular Ubuntu package-management? I like 4logon's solution for kubuntu but I'm on "pure" ubuntu 8.10. This warning made me want to try it but up to now my "sense" is stronger than my fingers ... ;)

---

### Post by lanzen on 2008-12-12
Oh, well, I have a spare k/ubuntu on a usb disk that  can use for experiments. Maybe I'll have time later today for Wolfgang's #2 hack and see what it does.  :-)

---

### Post by randcoop on 2008-12-12
4logon's post here (#42 in the thread) works perfectly to fix the problem.  For those who want to try, but don't know how to get to the files in the DEB, DEB files are archives.  To extract them, run ```
ar x [filename.deb]
```.  You'll get three files: data.tar.gz, control.tar.gz, and debian binary.  The actual files are in data.tar.gz.  So extract that file: ```
tar -xvzf data.tar.gz
```

Now you'll have a new folder (directory) called usr.  Inside usr, you'll find the lib directory (also one called share), and inside the lib directory, there's an openoffice directory, and inside the openoffice directory, there's a basis3.0 directory (also one called program) and inside the basis3.0 directory, there's a program directory and that's where you'll find the two files that you need to copy to your openoffice installation per 4logon's suggestion.  

Remember to first back up the original files (just rename them by adding .original or whatever to the end of the name).  

Next time you run OpenOffice, it should look right again.

---

### Post by FiReSTaRT on 2008-12-12
> **alakin said:**
> I have not yet installed any OOo packages yet, I have been waiting to install OOo3. Having found this thread I have added the launchpad repo to my sources list and ran an update. Sure enough, OOo3 is now there. When I go to run the installation I get a warning that several of the packages are not authenticated. Is this correct? Following the warning I have still not installed anything.

BTW: I am running Xunbuntu Intrepid so I guess I will not experience some of the KDE and Gnome issues that others have encountered?

Alan
I'm having update issues with it. Basically I get the same message when I try a general system update and I get a list of a bunch of ooo packages listed.

EDIT: I just solved the problem by updating through synaptic. Works like a charm.

---

### Post by zika on 2008-12-12
to FiReSTaRT:Thank You veru much for encouragement! Also for the important tip to use Synaptic. It seems it worked OK. Again I have quick OpenOffice... ;) I do not get it why there are more than one update-engines ... nevertheless every day I learn something ... ;)

subsequent update gives me this:

> The following packages will be REMOVED:
  bsh{u} bsh-gcj{u} libgda3-3{u} libgda3-bin{u} libgda3-common{u} 
  libgdl-1-0{u} libgdl-1-common{u} libsensors4{u} libxalan2-java{u} 
  libxalan2-java-gcj{u} 

Did I make an error by removing them?

---

### Post by calc on 2008-12-12
It sounds like the trouble with the openoffice.org-kde package is probably due to switching the KDE support from 3 to 4. I will have to investigate the issue and see if it is correctable without having to fall back to KDE3 support instead.

---

### Post by mia1dolfan on 2008-12-12
I've taken the answers from two posts above and rolled them into one set of commands to run at the terminal to work around this.  It uses wget to download the older openoffice-kde package, alien to concert the deb package to a tarball, and then tar to extract to the proper place.  Make sure you have the broken openoffice-kde package installed prior to running this.

```
cd ~
sudo -v
[ ! -f /usr/bin/alien ] && sudo apt-get install alien
wget ftp://194.94.120.8/pub/debian/pool/main/o/openoffice.org/openoffice.org-kde_3.0.0-5_i386.deb
alien -t openoffice.org-kde_3.0.0-5_i386.deb
( cd / ; sudo tar xvfz ~/openoffice.org-kde-3.0.0.tgz \
./usr/lib/openoffice/basis3.0/program/kdebe1.uno.so \
./usr/lib/openoffice/basis3.0/program/libvclplug_kdeli.so )


```

Now test, if everything went well Openoffice should be functioning as before, and you can continue updating.  Once a updated package of openoffice-kde package gets released it will overwrite this, but hopefully the next update will address the issue.

---

### Post by lanzen on 2008-12-12
Does anybody know where to get the AMD64 version of the old openoffice.org-kde?

---

### Post by lanzen on 2008-12-12
While we're waiting for the real fix I did test what was here suggested and it worked.

Nice, thank you all! :)

---

### Post by daflame on 2008-12-16
> **lanzen said:**
> Does anybody know where to get the AMD64 version of the old openoffice.org-kde?

Yeah does anyone have previous packages for Intrepid AMD64?  I did a recent update like so many others and only realized today that it is broken.  I found this page, but there is only a solution for i386.  I only use it twice a month or less so I didn't notice till now.  Removing the -kde package fixed it for now, but now openoffice is ugly looking and doesn't match my theme.  Thanks for the workarounds though.

---

### Post by tfy on 2008-12-16
Thanks, your suggestion worked for me.

---

### Post by 4logon on 2008-12-25
if you work a little with my solution in OO3 you see that the filepicker not works (file open...). To fix this you have to replace all files of the listed package. Here the full solution:


A) Install ooo 3 from PPA with your paket-manager
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
B) also install openoffice.org-kde_3.0.0-6_i386.deb with your paket-manager
C) download the old version of these package from: [ftp://194.94.120.8/pub/debian/pool/m...0.0-5_i386.deb](ftp://194.94.120.8/pub/debian/pool/m...0.0-5_i386.deb)
D) extract the files kdebe1.uno.so, libvclplug_kdeli.so and  fps_kde.uno.so from these package
E) replace the two files in folder /usr/lib/openoffice/basis3.0/program (rename the existing files befor)
F) extract the file kdefilepicker from these package
G) replace these file in folder /usr/lib/openoffice/program (rename the existing files befor)

by the way, it makes me wonder that launchpad not fix the problem. maybe the are on christmas-vacation ;-))) happy new year!!!-

bye, wolfgang

---

### Post by Norm24 on 2008-12-25
I also installed oo3 via the same way as HPVOHHR.Everything works perfectly fine except that I have only the programs that came in 2.4 and generally speaking everything looks exactly the same.

When load for example say the spreadsheet its says its loading 3.0.

Curious as to why I didn't get the full upgrade.

---

### Post by kiba95 on 2008-12-27
> **4logon said:**
> if you work a little with my solution in OO3 you see that the filepicker not works (file open...). To fix this you have to replace all files of the listed package. Here the full solution:


A) Install ooo 3 from PPA with your paket-manager
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
B) also install openoffice.org-kde_3.0.0-6_i386.deb with your paket-manager
C) download the old version of these package from: [ftp://194.94.120.8/pub/debian/pool/m...0.0-5_i386.deb](ftp://194.94.120.8/pub/debian/pool/m...0.0-5_i386.deb)
D) extract the files kdebe1.uno.so, libvclplug_kdeli.so and  fps_kde.uno.so from these package
E) replace the two files in folder /usr/lib/openoffice/basis3.0/program (rename the existing files befor)
F) extract the file kdefilepicker from these package
G) replace these file in folder /usr/lib/openoffice/program (rename the existing files befor)

by the way, it makes me wonder that launchpad not fix the problem. maybe the are on christmas-vacation ;-))) happy new year!!!-

bye, wolfgang

I hope the guys in PPA launchpad do get it fixed.
Caused yesterday I got my OOo 3 crashed after update too! :(

---

### Post by zika on 2008-12-27
in some other threads we solved problems with update-ing OO3 by using Synaptic to do the update instead of apt-get or aptitude. it simply better copes with that ...

(Synaptic, Reload, Mark all upgrades, Apply) ...

it worked for me for sure eventhough apt-get and aptitude complained about partial upgrade.

---

### Post by jaydoc on 2008-12-28
The file openoffice.org - kde 3.0.0.5 .deb seems to have been deleted from all mirrors.

Is there any other way to fix this issue...?

Or can someone put the file up at some server so that we can downlod it..?

---

### Post by Lek130 on 2008-12-30
> **zika said:**
> It seems that we **must** say that the people from Ubuntu were **right** when they did not include Oo3 in Intrepid and that there is a reason Oo3 is **not** in the official repositories yet. Launchpad upgrade proved itself to be very problematic and, now, I feel very stupid that I have tried it. I suspect that I will not be able to upgrade as easily as I would have that I have just waited Ubuntu repositories version. *_Lesson learned_*. When I try launchpad repo I get warning that I will get only partial upgrade and (as other threads confirm, I did not embark on that Titanic) only partial Oo3 installation.

Well, it works well in Mandriva 2009, Windows, and MacOS. To me it seems more to be a (K)Ubuntu Issue. Without doing any debugging but it feels like the system config for oo3 is not right (installers not setting it up correctly) ...

---

### Post by fragos on 2008-12-30
I've had no problems with the launchpads OO 3.0 in the Ubuntu 8.10 Gnome environment with perhaps one exception with impress. A friend sent me a power point file with a .wav file background track. The sound stops and starts. I tried converting the .wav to .mp3 and the problem was still there. Audacity will play the resulting .mp3 without problems.

---

### Post by zika on 2008-12-30
> **Lek130 said:**
> Well, it works well in Mandriva 2009, Windows, and MacOS. To me it seems more to be a (K)Ubuntu Issue. Without doing any debugging but it feels like the system config for oo3 is not right (installers not setting it up correctly) ...

that is **exactly** what I've said:

> Launchpad upgrade proved **itself **to be very problematic

OpenOffice, once it got installed, on one machine, or reinstalled on others, works OK in Ubuntu. Also in Windows XP and Vista, all are dual-boot. Truth is that I did not test it on Win boots of machines ... ;) other did.

---

### Post by lanzen on 2009-01-10
Here we go again! Updated to 3.0.0.1 and openoffice.org-kde is _still_ broken.

And this time 4logon's hack doesn't seem to fix it.   :(

---

### Post by randcoop on 2009-01-11
It's unbelievable that the people who put out updates insist on doing this.  My OpenOffice update today broke it again.  At first, it would crash before even starting.  Now, having copied over the KDE files mentioned in Post #42 here, it works, but with the ridiculously large fonts for the menus and everything else (except the documents themselves).  

Why the hell can't people check the updates before promulgating them?  Since this has been a known problem for more than a month, how is it possible that it was ignored for this most recent update?  

I suppose I'm partly at fault for installing the updates, but to be honest, it didn't occur to me that they'd put out a new update without fixing this problem.

---

### Post by 4logon on 2009-01-12
:(:(:(yes of course, it's unbelievable!!!
I think it's better to go back do the ubuntu packages and use the old version of OO.
It's better to spend the time in other thinks than patching the bad sources from ppa.launchpad.net
bye 4logon

---

### Post by Pintenman on 2009-01-12
I read that things are working OK with the debian repository, including the integration with KDE.

deb [http://http.at.debian.org/debian/pool/main/o/openoffice.org/](http://http.at.debian.org/debian/pool/main/o/openoffice.org/)

Haven't been able to test it myself, though.

---

### Post by fragos on 2009-01-12
Makes me glad I'm an 8.10 Gnome user. I've had no trouble with OO 3.0. I once was a KDE user. After a failed release of SUSE I gave Ubuntu 6.04 and Gnome a try and have been happy since. KDE and Gnome having different UI approaches I gave myself 2 weeks to adjust. No doubt, many KDE users would never consider a change to Gnome.

---

### Post by MistralWind on 2009-01-12
> **fragos said:**
> Makes me glad I'm an 8.10 Gnome user. I've had no trouble with OO 3.0. I once was a KDE user. After a failed release of SUSE I gave Ubuntu 6.04 and Gnome a try and have been happy since. KDE and Gnome having different UI approaches I gave myself 2 weeks to adjust. No doubt, many KDE users would never consider a change to Gnome.
I actually started with Gnome. I liked KDE better, though (personal preference; nothing more), so I switched to that.

I "fixed" OpenOffice last week by using Crossover to install Office 2007. Strangely, Word works even better in Linux than it does in Windows. For the most part, I like OO just fine (and I'll keep using the older version of their nice, simple spreadsheet program), but the "Updates breaking stuff" issue has gotten rather silly.

---

### Post by Pintenman on 2009-01-14
Fortunately they solved the problem themselves this time, by a new update. :D

---

### Post by 4logon on 2009-02-01
:popcorn: OO3 ist back on track. with the last update (fr. 30.01.) the problem with kde is fixed.
I have tested OO3 with KDE 4.2. Everything works fine!!!.
Many thanks to our friends from PPA.

for more details look here -> [https://launchpad.net/%7Eopenoffice-pkgs/+archive/ppa/+index#]("https://launchpad.net/%7Eopenoffice-pkgs/+archive/ppa/+index#")

bye 4logon.

---

