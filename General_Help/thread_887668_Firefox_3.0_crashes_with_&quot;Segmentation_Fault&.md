---
title: "Firefox 3.0 crashes with &quot;Segmentation Fault&quot;"
date: 2008-08-12
forum: General Help
---

### Post by useResa on 2008-08-12
Before someone makes a comment: I **DID** search the forums and found many threads on this issue. But I seem to find nowhere a solution.

As reported in many other threads, running Firefox from terminal only gives the indication "Segmentation fault".
```
rdrijsen@dell-ubuntu:~$ firefox
Segmentation fault
```

I have seen posts where it was indicated that it may be related to [Seesmic]("http://ubuntuforums.org/showthread.php?t=886152") (I don't know what it is so that will certainly not be the case in my situation). 

Or that it could be related with closing the GMail tab (as posted [here]("http://ubuntuforums.org/showthread.php?t=854887") and [here]("http://ubuntuforums.org/showthread.php?t=822424")), but I was NOT closing the GMail tab. Actually I was trying to reply to another post on this forum when the crash occurred. That is why I am currently posting from Opera.

Furthermore I have found various (possible :confused:) solutions:
[Installation of FF 3.0.1]("http://ubuntuforums.org/showthread.php?t=865757")
However, AFAIK I am running 3.0.1 (see below the result of aptitude show firefox)
```
Package: firefox
State: installed
Automatically installed: yes
Version: 3.0.1+build1+nobinonly-0ubuntu0.8.04.3
Priority: optional
Section: web
Maintainer: Alexander Sack <asac@ubuntu.com>
Uncompressed Size: 123k
Depends: firefox-3.0
Description: meta package for the popular mozilla web browser
 Firefox 3 is the next major release of the standalone Mozilla browser; it is
 written in the XUL language and designed to be lightweight and cross-platform. 
 
 This browser was previously known as Firefox 2, Firebird and Phoenix. 
 
 This is a meta package that will point to the latest firefox package in ubuntu.
 Don't remove this if you want to receive automatic major version upgrades for
 this package in future.
```

[Resolved with July 25,2008 update]("http://ubuntuforums.org/showthread.php?t=854887")
Since it is currently August and my system is up-to-date ... I guess that did not work for me :(

[Removal of the SCIM package]("http://ubuntuforums.org/showthread.php?t=764950")
This seems to have resolved the issue for at least two users. And to be honest ... I have not tried this one yet. If I look up SCIM I get the following from the description
```
Description: smart common input method platform
 Smart Common Input Method (SCIM) is an input method (IM) platform.  Input
 methods are needed to enter complex characters in many non-latin languages.
 SCIM provides a common platform for various plugin modules and independent IM
 programs, as well as a set of modules and programs on its own.  It is highly
 modularized and exposes abstract interfaces, so that plugin modules with
 different functions can easily communicate with each other.  The currently
 supported module types are configuration, IM engine, front end, filter, and
 setup GUI. 
 
 SCIM achieves the communication between IM engines and front ends through both
 shared library linking and server/client mode.  It supports XIM protocol, as
 well as GTK+ IM module and Qt IM module. 
 
 This package is the main binary package of SCIM.  It includes: the main program
 scim (GTK+ based) and other support programs; simple configuration module, X11
 front end module, rawcode IM engine module, simplified/traditional Chinese
 conversion filter module, and their corresponding setup GUI modules; GTK+ panel
 and its setup GUI module; and a GTK+ based setup tool. 
 
 SCIM is a well accepted platform and features various input method engines for
 many languages.  In Debian you can find the following separately packaged IMs
 useful: scim-tables-{additional,ja,ko,zh}, scim-pinyin, scim-uim, scim-m17n,
 scim-chewing, scim-anthy, scim-canna, scim-prime, and scim-skk. GTK+ users
 would also find package scim-gtk2-immodule useful for GTK+ IM module support. 
 
 For development on SCIM platform, please see the description of scim-dev
 package.
Homepage: http://www.scim-im.org/
```
From this I understand it is needed for IM. So I do not like to remove it until I know it is save to remove.
[COLOR="Red"]Can anyone indicate what issues I may run into when removing the package?[/COLOR]

And then there are still a number of threads that indicate the problem still exists. References are made to Flash (which IIRC was an old issue in FF 2).

Does anybody know a proper solution (besides running Opera ;))?

BTW: I am running Hardy 8.04

---

### Post by kelean on 2008-08-12
I have recently done a install of 8.4.1 and I am having the same some of the same issues.  After the install and updating I was not able to start firefox at all.  When I tried from the cli the error posted was segmentation fault.  Today I was able to start firefox for a short time but after a minute or two it just closes.  I started it from the cli and when it closed the error was the segmentation fault.

I am wondering if removing it and reinstalling will have any effect.

I do like opera for the most part.  I do prefer firefox most of the time.

---

### Post by useResa on 2008-08-13
Yesterday I was still able to browse some of the pages but (mainly) got the Segmentation Fault when trying to reply or so on a forum.
Today it crashes at startup. 

Seems I am stuck to Opera until this is resolved   ;)

---

### Post by kelean on 2008-08-13
I am starting to get the same things in opera now.  Shutdowns for no reasons and then I cant start opera at all.  I just get segmentation fault from the cli.  I am seroiusly thinking about tring out Slackware or Arch linux.

---

### Post by jou770d on 2008-08-16
Been having the same problem for a long time. Firefox is annoying the hell of me by crashing all the time with a "segmentation fault".
It's not always flash related, although flash does seems to make things worst (tried every "fix" on the forums and some that aren't but nothing helped).
And please don't "advise" me to use Opera...

---

### Post by geokok1981 on 2008-08-17
I just did a fresh install using the 8.04.1 cd (greek translation version).....5 times!!!

This is not flash related in any way. I have been getting the "segmentation fault" for firefox WITHOUT flash installed - WITHOUT any plugins installed. 
Also I have other apps (such as: terminal, update manager, sources, etc) crashing on the same, sudden, way, although I haven't checked that they are in the same category of "segmentation fault" through a terminal outpout. They sure look the same though. 

And all this on a system that has been running ubuntu for 6 months now without any hick ups so, no it is not hardware related either.

---

### Post by Cato2 on 2008-08-17
> **geokok1981 said:**
> ... 
Also I have other apps (such as: terminal, update manager, sources, etc) crashing on the same, sudden, way, although I haven't checked that they are in the same category of "segmentation fault" through a terminal outpout. They sure look the same though. 

And all this on a system that has been running ubuntu for 6 months now without any hick ups so, no it is not hardware related either.

It's just possible that some hardware has gone bad recently - uncommon but can happen.  One easy thing to do is to reboot Ubuntu and choose the 'memory test' option in GRUB (hit Esc when booting, it should be in there - if not, Google for "memtest ubuntu grub menu.lst" to see what to edit in /boot/grub/menu.lst).  Leave this test running overnight and that will at least help see if memory is involved here.

I did have problems with Firefox crashing a while back, and it's started again, but not very often - possibly because I run with 100+ tabs and 12+ extensions.  However, no other applications crash at all, which makes me think your issue may be hardware.

---

### Post by useResa on 2008-08-22
I have issued a separate bug on this issue, see bug [#260374: firefox 3 crashes with segmentation fault]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/260374")

With the bug report I have also included the result of strace, which for reference is also attached to this post.

---

### Post by geokok1981 on 2008-08-29
> **Cato2 said:**
> It's just possible that some hardware has gone bad recently - uncommon but can happen.  One easy thing to do is to reboot Ubuntu and choose the 'memory test' option in GRUB (hit Esc when booting, it should be in there - if not, Google for "memtest ubuntu grub menu.lst" to see what to edit in /boot/grub/menu.lst).  Leave this test running overnight and that will at least help see if memory is involved here.

I did have problems with Firefox crashing a while back, and it's started again, but not very often - possibly because I run with 100+ tabs and 12+ extensions.  However, no other applications crash at all, which makes me think your issue may be hardware.

It seems that you were correct. Memtest found did find errors so I took out one of the 2 memory dimms. The pc now has 256MB of RAM  and runs xubuntu (low ram would not allow ubuntu) happily. 

Thanks for the tip.

---

### Post by cor2y on 2008-08-29
I believe its related to flash in some form or fashion.
Firefox crashes for me to with that segmentation fault error but its on sites that use flash video/animation.
Why i don't know and it is always random, in most cases, meaning visit the same site with firefox again and it won't crash but try again later and it does.
I also attempted to visit those same sites with opera just to see if it was a firefox problem , what happens is opera refuses to display the flash parts of the site.
So i assume its a flash 10 issue (which is the version i am using) i know while i used 8.04 while it was in beta and then RC and even when it was officially released there was no crashing of firefox while visiting sites, flash 9 was what was in use then.
I only updated to 10 because of the pulse audio fix.

---

### Post by Cato2 on 2008-08-30
> **geokok1981 said:**
> It seems that you were correct. Memtest found did find errors so I took out one of the 2 memory dimms. ...

Thanks for letting us know.  There are a few options apart from the obvious one of buying more RAM (quite cheap at the moment depending on how old the PC is):

1. If you have enough time and Linux skills, you can use the BadMEM patch to the Linux kernel - this can let you use a partially bad memory module, by blocking out the bad chips.  There's clearly some risk of future failures here but it's good if you have more time than cash.  See [http://badmem.sourceforge.net/](http://badmem.sourceforge.net/) for more.

2. If Xubuntu is running a little slowly, you might like to investigate Ubuntulite, which uses a lighterweight desktop environment (LXDE) making better use of memory.  I found Xubuntu was rather slow in 192 MB.  Ubuntulite is still beta but looks promising - [http://ubuntulite.tuxfamily.org/](http://ubuntulite.tuxfamily.org/).  Alternatives include Fluxbuntu.  Or you can just customize Xubuntu, see [https://help.ubuntu.com/community/FVWM-Crystal](https://help.ubuntu.com/community/FVWM-Crystal) for one option.

---

### Post by useResa on 2008-09-02
Today I once more moved my ~/.mozilla directory using the command
```
mv ./.mozilla ./mozilla_old
```
Re-installed Firefox
```
sudo aptitude reinstall firefox-3.0
```

Next I recovered my bookmarks from the earlier created mozilla_old directory.
The AdBlock Plus and StumbleUpon add-on were still installed.
Added a few extra (Answers, Filterset.g and Fast Dial).
Did not any additional Themes or Languages.

Currently running over an hour without a Segmentation Fault.
Which is an amazing record since I first started getting the issue.

---

### Post by leprasmurf on 2008-09-04
I am having this issue as well.  My issue seems to be specific to Flash, segmentation fault only occurs when I try to load a site with alot of flash (I don't even want to try myspace).  I uninstalled anything dealing with flash and the sites load without a problem.  I tried utilizing the flashblock addon and still had the problem.  I imagine this would be because the flash library is still loaded.  I'm going strong for about 10 minutes now after reinstalling Flash.

---

### Post by druciferre on 2008-09-06
I am having the exact same problem. There are certain web-sites I can visit and it will crash instantly when the page is rendered. I've visited other sites and it would crash only some of the time (I believe this may be a result of different ads being displayed). 

Two sites that always crash it are 

[www.johnmccain.com](www.johnmccain.com) (ironically, maybe Linux doesn't want me looking at stupid ****? jk)

and 

[http://www.google.com/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fwww.metrolyrics.com%2Fthats-that-****-lyrics-snoop-dogg.html&ei=VkDASOWqM5DSMf2pkWo&usg=AFQjCNE7Ral4TxVyomwpY03a5Tf0uppoog&sig2=NV_LtHJYz2jw9tx0j_AexA](http://www.google.com/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fwww.metrolyrics.com%2Fthats-that-****-lyrics-snoop-dogg.html&ei=VkDASOWqM5DSMf2pkWo&usg=AFQjCNE7Ral4TxVyomwpY03a5Tf0uppoog&sig2=NV_LtHJYz2jw9tx0j_AexA)


This is not just related to firefox or flash. I've witnessed other applications doing the same thing. Pidgin, Banshee, Audacity, etc.

I've also noticed when shutting down I get some sort of dbus error. I haven't had the chance to record the exact error just yet.

I started looking into what modules and libraries are shared by all these programs. The only one I could find any users have reported is libc6. 

Also this is not an issue with my memory. I ran memtest86 for 3 hours and not a single hint of an issue with the memory. I did have some issue with partitioning my hard drive though. So I plan to run a check on the hard drive. Though I haven't experienced any other issues or errors.

---

### Post by useResa on 2008-09-08
> **useResa said:**
> Currently running over an hour without a Segmentation Fault.
Which is an amazing record since I first started getting the issue.Just as an update ... still running FF 3.0 without any segmenation faults.

> **druciferre said:**
> Two sites that always crash it are 
[www.johnmccain.com]("http://www.johnmccain.com/") (ironically, maybe Linux doesn't want me looking at stupid ****? jk)
and 
[http://www.google.com/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fwww.metrolyrics.com%2Fthats-that-****-lyrics-snoop-dogg.html&ei=VkDASOWqM5DSMf2pkWo&usg=AFQjCNE7Ral4TxVyomwpY03a5Tf0uppoog&sig2=NV_LtHJYz2jw9tx0j_AexA]("http://www.google.com/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fwww.metrolyrics.com%2Fthats-that-****-lyrics-snoop-dogg.html&ei=VkDASOWqM5DSMf2pkWo&usg=AFQjCNE7Ral4TxVyomwpY03a5Tf0uppoog&sig2=NV_LtHJYz2jw9tx0j_AexA")
I could even visit these two sites  ;)

Has anyone else recently tried the same actions as I have done (see post [#12]("http://ubuntuforums.org/showpost.php?p=5714124&postcount=12"))?

---

### Post by Talkless on 2008-09-08
> **useResa said:**
> 
Has anyone else recently tried the same actions as I have done (see post [#12]("http://ubuntuforums.org/showpost.php?p=5714124&postcount=12"))?

I did, but it didn't helped.

For me, as example, [**THIS**]("http://www.effinfunny.com/legend-of-neil") site always crashes ( and not if Flashblock is on).

It's the same with Adobe Flash 9 and 10 Beta.

---

### Post by useResa on 2008-09-09
> **Talkless said:**
> For me, as example, [**THIS**]("http://www.effinfunny.com/legend-of-neil") site always crashes ( and not if Flashblock is on).I tried your site also and I am currently typing this reply with the site you indicated open in another tab. However .... I have tried to open the site you indicated yesterday on a fresh installation of Xubuntu Intrepid and FF crashed immediately with a segmentation fault.

So I am starting to think it may have to do with either Extensions (Add-ons) and/or Plugins.
For reference, the add-ons I have installed on my Ubuntu Hardy installation are:
Ubuntu Firefox Modifications 0.5, StumbleUpon 3.18, Fast Dial 1.90, Answers 2.2.48 and AdBlock Plus 0.7.5.4 and Adblock Filterset.G Updater 0.3.1.3
The Plugins I have installed are shown in the attached image.
I have no additonal Themes or Languages installed.

To be complete, on my Xubuntu Intrepid installation I have installed the following add-ons:
Ubuntu Firefox Modifications 0.5, Answers 2.2.48 and AdBlock Plus 0.7.5.5 and Adblock Filterset.G Updater 0.3.1.3
No additional Themes or Languages and the Plugins are shown in the attachment.

[COLOR=Red]**UPDATE**[/COLOR]: Tried your site again today and also on my Intrepid installation it opens without crashing.
Hmmm .... this is getting more and more confusing by the day.

---

### Post by Talkless on 2008-09-09
My addons are:
[LIST]
[*]AdBlock Plus 0.7.5.5
[*]Download Embedded 0.5
[*]Download Helper 3.2
[*]Save Image In Folder 1.2.2
[*]Ubuntu Firefox Modifications 0.5
[*]User Agent Switch 0.6.11
[/LIST]

Plugins: 
[LIST]
[*]Default Plugin ( ??? )
[*]Demo Print Plugin for unix/linux
[*]Shockwave Flash 10 ( for myself only )
[*]Shockwave Flash 9 ( for all users )
[*]Totem Web Browser Plugin 2.22.1
[*]Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible; Totem)
[*]VLC Multimedia Plugin (compatible Totem 2.22.1)
[*]Windows Media Player Plug-in 10 (compatible; Totem)
[*]DivX® Web Player
[*]QuickTime Plug-in 7.2.0
[*]GCJ Web Browser Plugin (using IcedTea) 1.0
[/LIST]

By having disabled all Add-ons it's the same. I manage to "uncrash" Firefox only by using Flashblock. I'm still thinking it's Flash problem.

Where a Flash in your testing Xubuntu installation?

---

### Post by useResa on 2008-09-09
> **Talkless said:**
> Where a Flash in your testing Xubuntu installation?In my Xubuntu Intrepid installation I have Shockwave Flash 10.0.0 d525, in my Ubuntu Hardy installation I have Shockwave Flash 9.0 r124.

What I still do not understand why the site crashed yesterday on my Xubuntu installation and why it worked without any issues today.

---

### Post by malerv on 2008-12-07
Hi
I had the same issue

I did 
```
mv ./.mozilla ./mozilla_old
```
And without re-installed Firefox, it seems to work fine now.

I m suspecting an addon to mess up ...

I m installing my addons one by one waiting the Great Seg Fault to point the bad boy.

Was my 2 cents

---

### Post by useResa on 2008-12-08
I must admit that since my last post FF has been running very stable.
To me it seems that the issue may have been resolved, although I have no clue yet what the cause actually may have been.

For completeness ... in my Xubuntu Intrepid installation I now use "A Browser" and no longer the "official" FF.

---

