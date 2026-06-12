---
title: "Firfox 3.5 released! How to upgrade in Jaunty?"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by bhagwad on 2009-06-30
Firefox 3.5 final has just been released. I'm using Jaunty and want to install the latest (and greatest). Will it automatically appear in the updates a day or so from now?

If not, I want to install it manually some other way. Any thoughts on this from the community? I don't want to use the betas or the RCs

---

### Post by jreyes33 on 2009-06-30
If you check in the repos, there's the beta 4 version of firefox 3.5. I think we should wait, it shouldn't take more than a day to have it officially in the repositories.

---

### Post by secdroid on 2009-06-30
> **jreyes33 said:**
> If you check in the repos, there's the beta 4 version of firefox 3.5. I think we should wait, it shouldn't take more than a day to have it officially in the repositories.

My understanding was that FF 3.5 would not be the default for Jaunty.  What repository will get the official Ubuntu version of FF 3.5, as required for Jaunty?

Would I be correct in assuming that I will not be able to simply upgrade FF 3.0.11 and will have to install FF 3.5, import the 3.0.x bookmarks, install the desired add-ons, and somehow change the menu and panel shortcuts to point to 3.5?  Is there any info/docs on the FF upgrade process for Ubuntu Jaunty users?

---

### Post by bhagwad on 2009-06-30
I found this useful: [http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html](http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html) and am using the latest version now - It's called Shiretoko though (it's not a beta or a RC) and can be started using the command firefox-3.5.

---

### Post by secdroid on 2009-06-30
Thanks, bhagwad!

[http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/dists/jaunty/Release]("http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/dists/jaunty/Release") gives
> Origin: LP-PPA-ubuntu-mozilla-daily
Label: Ubuntu
Suite: jaunty
Version: 9.04
Codename: jaunty
Date: Tue, 30 Jun 2009 16:36:54 UTC

Looks like the right stuff.  I'll give it a try.

---

### Post by secdroid on 2009-06-30
OK, following the instructions bhagwad cited worked for me.  I'm running "version 3.5 Mozilla Firefox for Ubuntu canonical 1.0", aka "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1) Gecko/20090622 Ubuntu/9.04 (jaunty) Shiretoko/3.5".

Rather than mess with the /usr/bin/firefox link (change target from firefox-3.0 to firefox-3.5), I modified the menu and panel shortcuts to point to "firefox-3.5 %u" rather than "firefox %u".  You may prefer to hack the link.

Bookmarks were automatically imported.  Some add-ons were flagged as incompatible -- Firefox (en-GB) 3.07 and mediaplayerconnectivity 0.9.1.  My other add-ons (No Script, User Agent Switcher and Netcraft Anti-Phising Toolbar) were either compatible or were upgraded automatically as part of the post-install config.

All in all, relatively painless.  However, if the bit about menus, links, and add-ons doesn't make sense to you, you might be better off waiting for an "official" solution that flattens the last few speedbumps.

I've been running Google Chromium 3.0.191.0 (0).  I have to agree with the Technologizer review of FF 3.5.  It is slower to startup than Chrome/Chromium, but it does handle javascript-heavy sites almost as quickly as Chromium.  Nice job, Mozilla!

---

### Post by MattiJ on 2009-06-30
CLI> firefox-3.5
*NOTICE* No previous firefox-3.5 profile found, we'll initialize a profile using a copy of your existing 'firefox' profile.
Transfering... done.
Segmentation fault
CLI> firefox-3.5
Segmentation fault
CLI> firefox-3.5 -safe-mode
Segmentation fault
CLI> uname -a
Linux jauntu 2.6.28-12-generic #43-Ubuntu SMP Fri May 1 19:31:32 UTC 2009 x86_64 GNU/Linux

Any suggestions?

---

### Post by giorgosts on 2009-06-30
```
firefox-3.5 --safe-mode
```

---

### Post by MattiJ on 2009-06-30
> **giorgosts said:**
> ```
firefox-3.5 --safe-mode
```

```
CLI> firefox-3.5 --safe-mode
Segmentation fault

```

---

### Post by MattiJ on 2009-06-30
Maybe there is something broken in the profile? Can I make it start on a new profile, not copying the old one?

---

### Post by bhagwad on 2009-06-30
> **MattiJ said:**
> Maybe there is something broken in the profile? Can I make it start on a new profile, not copying the old one?

Try firefox-3.5 --profilemanager - does that help?

---

### Post by MattiJ on 2009-06-30
Nope same Segmentation fault even if I delete the profile dir it just copy it back and Segmentation fault!

```
CLI> firefox-3.5 --profilemanager
*NOTICE* No previous firefox-3.5 profile found, we'll initialize a profile using a copy of your existing 'firefox' profile.
Transfering... done.
Segmentation fault
CLI> firefox-3.5 --profilemanager
Segmentation fault
CLI> firefox-3.5 --version
Segmentation fault
```

---

### Post by NikAmi on 2009-06-30
I just tried the renaming and linking method and it killed my browsing. It would not load any pages at all. Thankfully, I remembered the main things I had changed and was able to undo them and revert back to 3.01 which thankfully allowed me to browse again. I will be waiting for someone to add the update to a repository or release a .deb.

---

### Post by l-x-l on 2009-06-30
The only problems I've had with "Shiretoko" are:

1. When I download a file & try to open the file or open the directory the file was saved in I get an application launcher. Seems like Shiretoko doesn't remember what apps to use to open files. It doesn't even remember to use Nautilus as a file manager.

2. The "Ubuntu Firefox Modifications" extension doesn't work. Not sure if it's related to issue 1.

---

### Post by MattiJ on 2009-06-30
I installed it from 
```
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main
```

---

### Post by secdroid on 2009-06-30
> **MattiJ said:**
> CLI> firefox-3.5
*NOTICE* No previous firefox-3.5 profile found, we'll initialize a profile using a copy of your existing 'firefox' profile.
Transfering... done.
Segmentation fault
<snip>
Any suggestions?

When I installed, I didn't invoke the profile manager specifically.  The install did give the "initialize" message you got and the profile was copied from 3.0.11.  No problems.

Maybe a dumb suggestion, but try install from scratch again.  Suggest trying first with existing Firefox (and other Mozilla library users like Thunderbird) closed.  If that fails, try again with existing FF open.

---

### Post by MattiJ on 2009-06-30
I did sudo apt-get remove --purge firefox-3.5
and re-install but same, it does no difference if other FF is open.

---

### Post by secdroid on 2009-06-30
"FAQ - WHERE CAN I GET FIREFOX 3.5 FOR UBUNTU?"
[http://www.asoftsite.org/s9y/archives/160-FAQ-Where-can-I-get-firefox-3.5-for-Ubuntu.html]("http://www.asoftsite.org/s9y/archives/160-FAQ-Where-can-I-get-firefox-3.5-for-Ubuntu.html")

"Firefox add-ons: Which work in 3.5?"
[http://download.cnet.com/8301-2007_4-10276017-12.html]("http://download.cnet.com/8301-2007_4-10276017-12.html")

---

### Post by secdroid on 2009-06-30
> **MattiJ said:**
> I did sudo apt-get remove --purge firefox-3.5
and re-install but same, it does no difference if other FF is open.

Another dumb suggestion: Are you up-to-date?  (Ubuntu Update Manager?)

Yet another dumb suggestion: Reboot and try again (I know, I know, but last resort...)  Do _***all***_ of the steps in the post bhagwad cited.

Really, really dumb suggestion: Run the memory diagnostic off of a live CD ([http://www.memtest86.com/](http://www.memtest86.com/)).  Browsers can be tough on marginal boxes and new browsers may have different memory layouts and/or sizes.

Super silly suggestion: Install immediately after a ***_cold_*** boot, before running anything else.

Thousands of folks have been running the various FF 3.5 Betas and RCs on 'buntus, Debians, and various other Linuxes.  What could be wrong with your 'buntu?

---

### Post by saf-t scissors on 2009-06-30
Could be a bad install. I've downloaded the tar files three times, every one had errors.

---

### Post by Endolith on 2009-06-30
Doesn't the version in the repositories install alongside the main version, though?  What if I want it to replace the version I've got?

---

### Post by MattiJ on 2009-06-30
> **secdroid said:**
> Another dumb suggestion: Are you up-to-date?  (Ubuntu Update Manager?)

Yet another dumb suggestion: Reboot and try again (I know, I know, but last resort...)  Do _***all***_ of the steps in the post bhagwad cited.

Really, really dumb suggestion: Run the memory diagnostic off of a live CD ([http://www.memtest86.com/](http://www.memtest86.com/)).  Browsers can be tough on marginal boxes and new browsers may have different memory layouts and/or sizes.

Super silly suggestion: Install immediately after a ***_cold_*** boot, before running anything else.

Thousands of folks have been running the various FF 3.5 Betas and RCs on 'buntus, Debians, and various other Linuxes.  What could be wrong with your 'buntu?

I did remove and purge, update, reboot and test memory and then before starting anything and no compiz.

Then a new FF 3.5 install but still all I get is Segmentation fault. I can't even get version from it all i say is Segmentation fault!

Otherwise all is working ok on this box and nothing is like this.

Then Install **FF 3.6** and that works including Flash! but gives this 
```
LoadPlugin: failed to initialize shared library /usr/local/lib/personal/libplugins.so [/usr/local/lib/personal/libplugins.so: wrong ELF class: ELFCLASS32]
```

The package name is firefox-3.5 (3.5~rc2+nobinonly-0ubuntu2~umd1~jaunty)

I also test FF3.5 in Virtualbox Jaunty (running on this box) 32bit and works...

---

### Post by running_rabbit07 on 2009-06-30
I installed by searching Synaptic Package Manager. It was there.

---

### Post by Merk42 on 2009-06-30
> **running_rabbit07 said:**
> I installed by searching Synaptic Package Manager. It was there.

Karmic or Jaunty?

As of this writing, Jaunty only has beta 4 in its default repositories.

---

### Post by running_rabbit07 on 2009-06-30
Jaunty. I searched Firefox 3.5.

It didn't say beta but it could have been.

It says Shiretoko.

---

### Post by Merk42 on 2009-06-30
> **running_rabbit07 said:**
> Jaunty. I searched Firefox 3.5.

It didn't say beta but it could have been.

It says Shiretoko.


Shiretoko = beta


3.5~b4~hg20090330r24021+nobinonly-0ubuntu1 to be more precise

---

### Post by lovinglinux on 2009-06-30
For instructions on how to install Firefox 3.5 or upgrade the 3.0.11 version, check the [color=#CC0000]**Firefox Alternatives & Newer Versions**[/color] section of the [**[color=#CC0000]Firefox optimization and troubleshooting thread[/color]**](http://ubuntuforums.org/showthread.php?t=1193567).

For a list of other threads talking about the same subject, visit [http://ubuntuforums.org/showthread.php?t=1200781](http://ubuntuforums.org/showthread.php?t=1200781)

---

### Post by running_rabbit07 on 2009-06-30
> **Merk42 said:**
> Shiretoko = beta


3.5~b4~hg20090330r24021+nobinonly-0ubuntu1 to be more precise

Cool, good to know not to set it up any further. Guess I get to dump this one and get the right upgrade.

---

### Post by djuliette on 2009-06-30
I'm confused. I'm not sure if I have the latest or not.  I added:
deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main 
to sources.list

and installed firefox-3.5.  But it is coming up as shiretoko.

Was shiretoko strictly the beta, or is it also the name of the daily dev builds?

The 'about' shows it as this:
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.1pre) Gecko/20090701 Ubuntu/9.04 (jaunty) Shiretoko/3.5.1pre

---

### Post by MattiJ on 2009-06-30
Now got it updated and works!
So I think the 64bit package was broken.

```
CLI> firefox-3.5 --version
Mozilla Firefox-3.5 3.5.1pre, Copyright (c) 1998 - 2009 mozilla.org

```

Thanks for helping ):P

---

### Post by crandon on 2009-07-01
For the segfault check out:

[https://bugs.launchpad.net/bugs/346691](https://bugs.launchpad.net/bugs/346691)

if it applies to you, make a bakckup of your system asap.

---

### Post by MattiJ on 2009-07-01
> **crandon said:**
> For the segfault check out:

[https://bugs.launchpad.net/bugs/346691](https://bugs.launchpad.net/bugs/346691)

if it applies to you, make a bakckup of your system asap.

Na don't think so it was on 2.6.28-11. I'm on 2.6.28-12 and its very stable 2.6.28-13 was unstable for me so I use 2.6.28-12. And that was the only app that segfaults for me. But thanks for the info.

---

### Post by ak331 on 2009-07-01
Well folks,

I did this by accident but now I have firefox 3.5.

I tried installing using add/remove and this did not work.

I followed the terminal mode as in one of the threads but I lost firefox 3.0.

I had downloaded from mozilla.com site and expanded to /user/home directory and tried everything to get it to work but no help here.

I went to toolbar where the icon for firefox was there. I right clicked the properties and in command I browsed to /user/home/firefox directory and selected firefox and double clicked and presto it worked without hitch.

there you have manual method of installing firefox 3.5.

Enjoy firefox 3.5.

---

### Post by lovinglinux on 2009-07-01
> **ak331 said:**
> Well folks,

I did this by accident but now I have firefox 3.5.

I tried installing using add/remove and this did not work.

I followed the terminal mode as in one of the threads but I lost firefox 3.0.

I had downloaded from mozilla.com site and expanded to /user/home directory and tried everything to get it to work but no help here.

I went to toolbar where the icon for firefox was there. I right clicked the properties and in command I browsed to /user/home/firefox directory and selected firefox and double clicked and presto it worked without hitch.

there you have manual method of installing firefox 3.5.

Enjoy firefox 3.5.

Firefox 3.0.11 is in the folder /usr/lib/firefox-3.0.11. 

I don't know what you mean by /user/home/firefox.

---

### Post by ak331 on 2009-07-01
When I downloaded firefox 3.5 and extracted to folder /user/home where firefox folder is and just by changing the property of the firefox icon and pointing to /user/home/firefox/firefox it worked.
Whether it replaced the original firefox I do not know but under @about mozilla firefox it tells me it is running firefox 3.5.
I hope this helps.

I also found a version of firefox in /user/lib/firefox3.5 and I changed the file to this version as this also works.

---

### Post by abhiroopb on 2009-07-01
does anyone know when doing: "sudo apt-get upgrade" will update firefox to 3.5? I have other ppa's to update to 3.5, but I' rather wait for my package manager to do it automatically.

---

### Post by lovinglinux on 2009-07-01
> **ak331 said:**
> When I downloaded firefox 3.5 and extracted to folder /user/home where firefox folder is and just by changing the property of the firefox icon and pointing to /user/home/firefox/firefox it worked.
Whether it replaced the original firefox I do not know but under @about mozilla firefox it tells me it is running firefox 3.5.
I hope this helps.

I don't have any problems installing Firefox 3.5. I have compiled it from source and it's working great. But was intrigued with /user/home/ because that path doesn't exist. Now I see that you meant /home/user/. I'm not sure, but I think is not a good idea to keep firefox on your home directory, due to permissions.

Try this: [http://ubuntuforums.org/showthread.php?p=7541196#post7541196](http://ubuntuforums.org/showthread.php?p=7541196#post7541196)

This should put firefox in /opt/firefox with the proper permissions and link the launcher to it.

> **ak331 said:**
> I also found a version of firefox in /user/lib/firefox3.5 and I changed the file to this version as this also works.

That one is Firefox 3.5 Beta, installed from the repositories. If you update that version using the semi-official *ubuntu-mozilla-daily* PPA repository ([instructions](https://help.ubuntu.com/community/FirefoxNewVersion)), then you can delete the Firefox 3.5 final version from your home directory. This will ensure that you get the latest release and also avoid security risks of running Firefox from home.

---

### Post by RenoDTD on 2009-07-01
> **ak331 said:**
> When I downloaded firefox 3.5 and extracted to folder /user/home where firefox folder is and just by changing the property of the firefox icon and pointing to /user/home/firefox/firefox it worked.
Whether it replaced the original firefox I do not know but under @about mozilla firefox it tells me it is running firefox 3.5.
I hope this helps.

I also found a version of firefox in /user/lib/firefox3.5 and I changed the file to this version as this also works.


Ok seriously...I've been trying everything to get firefox 3.5 to work, tried out the shiritoko version and when I went to some sites it said I was using an old version of firefox and I need to upgrade.  I've gone through all kinds of threads trying to do what you did in just a few simple steps.

So I just want to say..... THANK YOU......  The process works perfectly and I now have the final version of firefox 3.5 working in ubuntu.

---

### Post by lovinglinux on 2009-07-01
> **RenoDTD said:**
> Ok seriously...I've been trying everything to get firefox 3.5 to work, tried out the shiritoko version and when I went to some sites it said I was using an old version of firefox and I need to upgrade.  I've gone through all kinds of threads trying to do what you did in just a few simple steps.

So I just want to say..... THANK YOU......  The process works perfectly and I now have the final version of firefox 3.5 working in ubuntu.

You are welcome. Glad it worked. My Firefox 3.5 is flying here. Now the only issue is the damn flash :)

---

### Post by Apreche on 2009-07-01
I want real Firefox, not Shiretoko. What should I do?

---

### Post by lovinglinux on 2009-07-01
> **Apreche said:**
> I want real Firefox, not Shiretoko. What should I do?

That one is Firefox 3.5 Beta, installed from the repositories, just a different name. If you update that version using the semi-official *ubuntu-mozilla-daily* PPA repository ([instructions](https://help.ubuntu.com/community/FirefoxNewVersion)), then you have Firefox 3.5 final version, but I'm afraid it will still be named Shiretoko.

You can install Firefox 3.5 final without the Shiretoko name with the method described in the link below. It would be wise to remove Shiretoko first, just in case:

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by SatanzJudge on 2009-07-02
Guys, the latest firefox-3.5 package from the [Mozilla Daily PPA]("https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa") is 3.5[COLOR="Red"]**.1 Alpha**[/COLOR]!

The firefox-3.5 package in Universe is Beta 4. I still haven't found a way to install 3.5 final through a repository.

---

### Post by lovinglinux on 2009-07-02
> **SatanzJudge said:**
> Guys, the latest firefox-3.5 package from the [Mozilla Daily PPA]("https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa") is 3.5[COLOR="Red"]**.1 Alpha**[/COLOR]!

The firefox-3.5 package in Universe is Beta 4. I still haven't found a way to install 3.5 final through a repository.

Yes, It is. I guess since it is ubuntu-mozilla-daily it will continue to increase according to Mozilla's updates. If Mozilla releases 5.1, then the daily repository should be updated to 5.2 Alpha just after the official release.

You can install 3.5 final using [Ubuntuzilla](http://ubuntuzilla.wiki.sourceforge.net/). It's pretty straight forward and works like a charm.

BTW, I have updated [my tutorial](http://ubuntuforums.org/showthread.php?t=1193567) to include a warning about this. Thanks for pointing that out.

---

### Post by -jay- on 2009-07-02
> **lovinglinux said:**
> That one is Firefox 3.5 Beta, installed from the repositories, just a different name. If you update that version using the semi-official *ubuntu-mozilla-daily* PPA repository ([instructions](https://help.ubuntu.com/community/FirefoxNewVersion)), then you have Firefox 3.5 final version, but I'm afraid it will still be named Shiretoko.

You can install Firefox 3.5 final without the Shiretoko name with the method described in the link below. It would be wise to remove Shiretoko first, just in case:

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

thx followed the steps updated without any problems just need to update my plugins is all again thx

---

### Post by RenoDTD on 2009-07-02
Ok so the simple method of changing the command under properties to point to the newly downloaded firefox 3.5 works great.....except now I'm not getting any sounds...for example playing a hulu video...video works great....just no sound...Any ideas?

---

### Post by lovinglinux on 2009-07-02
> **-jay- said:**
> thx followed the steps updated without any problems just need to update my plugins is all again thx

Go to [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). There are instructions there on how to disable extension version checking until you get all the updates. Be careful tho, since some extensions might cause problems or work improperly.

---

### Post by -jay- on 2009-07-02
> **lovinglinux said:**
> Go to [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). There are instructions there on how to disable extension version checking until you get all the updates. Be careful tho, since some extensions might cause problems or work improperly.

ok will do i notice i have no plugins now on 3.5

---

### Post by priegog on 2009-07-02
Guys, have a little patience before you start hacking your menu links and all, it will come down eventually in the backports.

> **abhiroopb said:**
> does anyone know when doing: "sudo apt-get upgrade" will update firefox to 3.5? I have other ppa's to update to 3.5, but I' rather wait for my package manager to do it automatically.

Yes, over the course of today that should happen. See [https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/393978/comments/6](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/393978/comments/6)

---

### Post by lovinglinux on 2009-07-02
> **-jay- said:**
> ok will do i notice i have no plugins now on 3.5

Which method did you used? I recommend using Ubuntuzilla. It's easy to install and remove. It also worked like a charm, with plugins and all.

---

### Post by mad_squirrel on 2009-07-02
What about downloading tar.bz2 package from official site?
[http://www.mozilla.com/en-US/firefox/firefox.html](http://www.mozilla.com/en-US/firefox/firefox.html)

---

### Post by -jay- on 2009-07-02
> **lovinglinux said:**
> Which method did you used? I recommend using Ubuntuzilla. It's easy to install and remove. It also worked like a charm, with plugins and all.

i used the method in the 1st post i quoted you , i tried using the method you said to use & still have a blank plugin screen

---

### Post by vivatsemiramis on 2009-07-02
i also had the same issue then i found this one:

[http://gaarai.com/2009/07/01/upgrade-to-firefox-3-5-on-ubuntu-9-04-jaunty-jackalope/](http://gaarai.com/2009/07/01/upgrade-to-firefox-3-5-on-ubuntu-9-04-jaunty-jackalope/)

you may consider looking at his instructions, they worked perfectly for me. :)

hope that helps

---

### Post by lovinglinux on 2009-07-02
> **-jay- said:**
> i used the method in the 1st post i quoted you , i tried using the method you said to use & still have a blank plugin screen

Ok. I see, you updated using the PPA repository right?

If yes, then run this command:

```
sudo apt-get purge firefox-3.5
```

and follow the method at [Ubuntuzilla](http://ubuntuzilla.wiki.sourceforge.net/)

---

### Post by mencial on 2009-07-02
> **SatanzJudge said:**
> Guys, the latest firefox-3.5 package from the [Mozilla Daily PPA]("https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa") is 3.5[COLOR="Red"]**.1 Alpha**[/COLOR]!

The firefox-3.5 package in Universe is Beta 4. I still haven't found a way to install 3.5 final through a repository.

I found it in Fabien Tassin's personal repository. He seems to be the maintainer of ubuntu-mozilla-daily:

deb [http://ppa.launchpad.net/fta/ppa/ubuntu](http://ppa.launchpad.net/fta/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/fta/ppa/ubuntu](http://ppa.launchpad.net/fta/ppa/ubuntu) jaunty main

I do not know how long those packages will last there, I think someone should ask him...

---

### Post by lovinglinux on 2009-07-02
Nevermind. Useless comment.

---

### Post by pjalegria on 2009-07-02
I can find a way to install FF3.5 PT-pt on jaunty....

---

### Post by lovinglinux on 2009-07-02
> **pjalegria said:**
> I can find a way to install FF3.5 PT-pt on jaunty....

You can download the PT version from [Mozilla](http://www.getfirefox.com) and follow [these instructions](http://www.psychocats.net/ubuntu/firefox).

---

### Post by suseno on 2010-01-15
**Help > Check for Updates**
Uupss... it's grey out and you can't click that.

Run Firefox as root. Open Terminal and type:
```

sudo firefox
```

Then enter your password. Try **Help > Check for Updates** again.

_Note:_ [COLOR="Red"]Never[/COLOR] run firefox as root for your regular internet surfing activity. Doing so can compromise your security.

---

### Post by lovinglinux on 2010-01-15
> **suseno said:**
> **Help > Check for Updates**
Uupss... it's grey out and you can't click that.

I'm sorry to say this, but please don't run commands without understanding what they do and the implications of using them. Running Firefox with **sudo** will only cause problems, because you will loose the ownership of Firefox profile folder to root. If you need to run Firefox with administrative privileges to enable the auto-update feature (a method that I don't recommend), then use gksudo instead. In fact, you should only use gksudo for graphical interfaces. Please correct your post so other users don't read the wrong instructions and make the same mistake.

---

