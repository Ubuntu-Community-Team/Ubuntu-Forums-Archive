---
title: "Openoffice 3.0 installation messed up !"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by showman47 on 2009-04-04
Hi

Last year I installed OpenOffice 3 on ubuntu 8.10 without problems from info on this website
[http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

However, I recently installed ubuntu on a new system and decided to put Oo3 on again (as it is better than 2.4). 
This time it's completely messed up, the package is a newer one (from Openoffice.org site) but has resulted in damage to both Oo3 and the previous Oo2.4 version. In both cases, all the top menu items and controls are blanked out, in all the Oo3 and Oo2.4 applications.

I've tried reinstalling Oo2.4 from the synaptic package manager but to no avail. 

Would I need to completely remove Oo2.4 and Oo3 ? (and how would I do this) or is there a simpler solution ?

Any help gratefully received !

---

### Post by showman47 on 2009-04-04
you know what, I think it's the Openoffice wiki page that has allowed me to mess up!

I was searching the net to find a way of installing Oo3 and had forgotten the site previously mentioned.

I beleive the last time I did this (installed Oo3 successfully, I just installed tweak ubuntu and used that to install Oo3.

This time I made the mistake of trying to follow the instructions on this page:
[http://wiki.services.openoffice.org/wiki/Ubuntu_Build_Instructions#Ubuntu_8.10_Intrepid](http://wiki.services.openoffice.org/wiki/Ubuntu_Build_Instructions#Ubuntu_8.10_Intrepid)

I suspect (but not certain) that following the apt-get intructions here has messed things up.

Am now tempted to re-install ubuntu and start again.

Would really like some suggestions before I do this.

thanks in advance

showman47

---

### Post by Vkthor on 2009-04-04
Hi.
It happened to me with ooo 2.4 the hardy installed version. I've just upgraded to intrepid ibex and the open office messed as you say.

A little more information on this (maybe helps anyone to help us!)

How I've upgraded: by changing Applications fonts  > Upgrading > New version [normal versions].

The new 8.10 Ubuntu version was detected, downloaded all files and installed.

After the system reboots I've noticed that the OOo was a mess :-( nothing appears in the menus (fonts, size, cells range, command line, line numbers, column letters, sheet names, etc... even the menu bar disappeared, only the underscores remain, the options only show the icons...  tooltips, only the background, etc...)

With Abiword or Firefox this doesn't happen, everything is normal!  but with Kchart, for instance, it happens too...

The things are there! If I scroll the options I can see them but they disappear in a flash, like if the background moved to the top position.

I've set the Human theme and tried others (no customized) but with no results.

Hint: When I looked at System > Preferences > Appearance (because the new install changed it to the sliding theme (customized) Ubuntu told me that the chosen theme could not work properly because... I don't remember well, but something about a kde manager (could it be?) As I did not want it to work I didn't pay much attention. :-(

BTW: All KDE's programs don't work also... well, I think old KDE's, because my Kaffeine with a no version KDE (three dragons ubunyu style circle) as Kchart or Kword have the some OOo problem, while Gnomo's or 4.1.4 KDE's work fine. Amarok, who doesn't have a KDE's entry on the help > about can't work also.

I think the problem is here, with this KDE thing (I'm a very newbie ubuntu and linux user) but I can't have an idea how to solve it.

Any ideas ppl? I don't need to say that like this my pc is useless :-(

I must say, it was easier to me to go from MS-DOS to old Windows2.11 than from the Windows vista to Ubuntu ](*,)

Thanks

Vkthor.

---

### Post by showman47 on 2009-04-05
Thanks Vkthor for your response.

I'm not convinced that we have identical problems here as my problem only seems to affect Open Office. I installed Kchart and have no problems with it nor with any other KDE apps.

I'm pretty sure it's related to my attempt at installing Oo3 using the instructions in the openoffice wiki page previously mentioned - *openoffice community take note!*

What saddens me most is that a more experienced ubuntu community member hasn't contributed to this thread. This is a real shame, because I really like ubuntu, it's the best linux distro around by far. I've been using it for many months now since the release if 8.10 and found it reliable and productive, having tried out over 30 distros last year.

I wish ubuntu (community) would appreciate that openoffice is one of the key applications that will turn people away from microsoft and focus more effort to getting Oo3 in the package manager by default.

Oo3 is really good (when it works).

It's really amazing that ubuntu exists and that a community of developers have produced an effective competitor to microsoft without the big corporate backing. I appreciate this as a programmer and web developer.

Ubuntu is nearly there aside from a few issues (which I'm going to raise in 'Testimonials and Experiences' part of this forum in a few days, and I want it to succeed in order to give non-enthusiasts a choice and give microsoft something to think about.

Don't give up on ubuntu yet Vkthor, hopefully issues like this will be addressed in the new version coming out at the end of this month. ubuntu 8.10 made a big leap from the previous version (which is why I started using it) so I've got great hopes for the new version.

I've just made a backup of my files and am going to reinstall 8.10 and follow the exact procedure I took when I first installed ubuntu and openoffice 3 previously. I'll post back here when I'm done.

showman47

---

### Post by showman47 on 2009-04-05
Good news.

From a fresh installation of ubuntu 8.10 I followed the instructions from this page:

[http://community.zdnet.co.uk/blog/0,1000000567,10009699o-2000498448b,00.htm](http://community.zdnet.co.uk/blog/0,1000000567,10009699o-2000498448b,00.htm)

The instructions I've pasted here below:

Those who have installed the new Ubuntu Intrepid Ibex (8.10) release have probably noticed that it does not include the new OpenOffice.org 3.0 release. Apparently Canonical decided that the OpenOffice.org release date didn't give them enough time for testing and integration, so they are waiting for the OpenOffice 3.0.1 release, scheduled for the beginning of December. This is a sort of interesting role-reversal with Mandriva, who have typically been the more conservative about including new software in their releases, but they have OpenOffice 3.0.0 in their Mandriva 2009.0 release.

If you absolutely need (or want) OpenOffice 3.0 in Ubuntu 8.10, it is relatively easy to get it. Basically all you need to do is add the OpenOffice repository to your software sources, and then let Ubuntu notice that 3.0 is available, download and install it. Here are the few simple steps:

- Go to System / Administration / Software Sources

- Click the tab for "Third-Party Software", then "Add" (the one at the left, NOT Add CD-ROM at the right)

- Enter the following in the APT line:

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

- Click "Add Source", and then when it tells you that the software information is out of date, click "Reload". Wait for that to finish, it will probably take a minute or two.

- Close the Software Sources window

You should then (or very soon thereafter) see the Update Icon in the panel, and you can then proceed as usual with updates.

-----------------------------------------------------------
This worked perfectly for me. The only glitch was an error message about authentication key when doing the reload, but this did not affect the installation.

Openoffice 3 replaced openoffice 2.4 in the Applications menu and all works fine.

Please note, that following the above instructions previously after it had messed up (see previous posts in this thread) did not fix the problem.

All I can suggest to anybody upgrading to Oo3 in ubuntu 8.10, use the above instructions from the zdnet page mentioned and NOT the OpenOffice wiki page.



showman47

---

### Post by Vkthor on 2009-04-06
Hi showman47.

I want not to give up (yet). :-)
I think my problem is with kde, because all my old programs which use kde can't work properly. The updated programs which use the new kde 4.1.4 work fine. I'm looking for a solution on this: how to know which kde I've in my pc (or how many :p) and how to install the new version without damaging all my system. I like it the way it is (well, better say it WAS) :-)
I think Ubuntu uses gnome, so I don't want to change to kde (I don't know if this is the way I should say... I'm not an expert in Linux, I don't know how it works... I'm just learning LOL)
BTW if I can't fix it, I'll do exactly what you did, a fresh new Intrepid Ibex Ubuntu install and then will try the new OOo in Linux (I use it in my Vista Lap ;) and by now I've copied my files to an usb HD and work with it with my lap).

> **showman47 said:**
> What saddens me most is that a more experienced ubuntu community member hasn't contributed to this thread. This is a real shame, (snip)

Don't worry, maybe they are all busy :-)

Best regards.

Vkthor

---

### Post by showman47 on 2009-04-07
I would stick to ubuntu (gnome desktop) as opposed to kubuntu (kde version), it's faster and I personally prefer it. 

I have tried out many KDE apps in ubuntu with no problems, but all were installed via the synaptic package manager, so maybe these are tried and tested on ubuntu. 

I must admit I am a complete convert to ubuntu (after using windows xp for years). I really like the way it works, and it works great on my PC (pentium 4 with 2Gb ram). I still have windows xp (in a partition) but only use it for browser testing on IE7 and really hate windows xp now (had a try out of vista and hated that as well).

best of luck.

showman47.

---

### Post by Gonzalo_VC on 2009-09-04
[COLOR="Navy"]Hi. I have Ub 8.04 LTS yet (that's why they do a _long_ term support version :P) that still runs OpenOffice.org 2.4. 
I have followed this instructions to try to install OOo 3.x, but didn't work:

[http://ubuntumanual.org/posts/175/upgrade-to-open-office-3-1-in-ubuntu-jaunty-intrepid-hardy](http://ubuntumanual.org/posts/175/upgrade-to-open-office-3-1-in-ubuntu-jaunty-intrepid-hardy)

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

(always doing what says specifically for the **Hardy** version, of course).

But apt-get and other system tools for installing / upgrading packages did NOT find the new OOo nor offer to up-grade anything.

Any other idea, apart from downloading the *.deb* file and doing it manually**?** (and latter manage to put icons in the menu and eliminate OOo 2.4 without compromising the system with some silly language pack or library :().

Thanks!
[/COLOR]

---

### Post by Hagar Delest on 2009-09-04
Why don't you want to install the .debs? It has already worked for me and it haven't wrecked anything. See [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by Gonzalo_VC on 2009-09-04
> **Hagar de l'Est said:**
> Why don't you want to install the .debs? It has already worked for me and it haven't wrecked anything. See [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

[COLOR="Navy"]Yes, thanks.  
I downloaded the last *.deb* package = **OOo 3.1.1**. Then I followed this: [http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04](http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04) using the correct file and path names, of course, but got problems at first.

I manage to solve them by going back, removing everything about OOo 2.4 (and even 3.1) with "apt-get remove openoffice*.*" but had to also check in *synaptic* for some lost OOo 2.4 stuff, since there were a couple of things left.

Then, being "zero" OOo files in the machine, the process worked up to the desktop integration! :D  Thank you Falko Timme! I'll recommend your post.

Cheers! [/COLOR]

---

### Post by Hagar Delest on 2009-09-04
> Your current OpenOffice installation will not be removed unless you uninstall it with Synaptic or on the command line, so you can run both versions in parallel if you like.
That's a big mistake. You _need_ to remove the Ubuntu version first because both versions are incompatible. That's why you had problems.

Edit: in fact, it can work if the previous version is from a different branch (3.x vs 2.x) and perhaps if the other version had been installed through the debs also.

---

### Post by Gonzalo_VC on 2009-09-04
> **Hagar de l'Est said:**
> That's a big mistake. You _need_ to remove the Ubuntu version first because both versions are incompatible. That's why you had problems.

[COLOR="Navy"]Not really... they say you can keep different versions in Linux (I never wanted to, though!)[/COLOR]

> **Hagar de l'Est said:**
> Edit: in fact, it can work if the previous version is from a different branch (3.x vs 2.x) and perhaps if the other version had been installed through the debs also.

[COLOR="Navy"]That's right. They say in different directories. But again, who wants that? (maybe only until you check the new one is working properly... who knows).
Cheers!
[/COLOR]

---

