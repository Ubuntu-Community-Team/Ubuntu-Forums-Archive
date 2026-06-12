---
title: "Firefox 3 Right-Click issue"
date: 2008-08-30
forum: General Help
---

### Post by lotrkev on 2008-08-30
I am running Ubuntu Hardy, and am having a minor problem in Firefox 3. The problem is that **_sometimes_**, when I right-click on any web page (such as to use some of my extensions like Remove it Permanently), Firefox automatically selects a random command from the right click menu, which never pops up. Other times, it pops up normally. I see no consistency of when this problem occurs, so it appears to be random.

Thanks in advance,
lotrkev

---

### Post by fedex1993 on 2008-09-01
yes i have been having the same problem but if i hold it down for a second it works fine i don't know the problem with it.

---

### Post by nickgaydos on 2008-09-01
I for one like to use Konqueror or Opera...try one of those :-) (maybe not Konqueror for Ubuntu users, but Opera may be good)

---

### Post by jdzzle8086 on 2008-09-20
wake up people, this is a serious bug. i'm a web developer and i've been dealing with this bs for long enough. i absolutely need to use firebug and the web developer plug-in or i would've switched to something else a long time ago. just cut the crap, quit asking questions and debug it.

---

### Post by adult swim on 2008-09-20
EDIT:  welcome to the forums.  maybe instead of telling people to debug it, you could explain how to do that.

---

### Post by peakshysteria on 2008-09-20
> **lotrkev said:**
> I am running Ubuntu Hardy, and am having a minor problem in Firefox 3. The problem is that **_sometimes_**, when I right-click on any web page (such as to use some of my extensions like Remove it Permanently), Firefox automatically selects a random command from the right click menu, which never pops up. Other times, it pops up normally. I see no consistency of when this problem occurs, so it appears to be random.

Thanks in advance,
lotrkev

Post which FF version you have and which addons you have installed. [Infolister]("https://addons.mozilla.org/en-US/firefox/addon/447") helps you to gather this info. It might be an addon incompatibility. One of your addons don't play well together with one or more of your other addons. Post the info and we'll help you.

Like this:
My Firefox Information

Last updated: Sat, 20 Sep 2008 05:41:30 GMT
User Agent: Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1

**Extensions** (enabled: 18, disabled: 1; total: 19)
[list]
[*][Dictionary Switcher](http://en.design-noir.de/mozilla/dictionary-switcher/) 1.0 
[*][Dictionary Tooltip](http://www.rjonna.com/ext/dictionarytip.php) 1.3 
[*][DownloadHelper](http://www.downloadhelper.net) 3.2.2 
[*][FireFTP](http://fireftp.mozdev.org) 1.0.2 
[*][Flashblock](http://flashblock.mozdev.org/) 1.5.6 [disabled]
[*][Forecastfox](http://forecastfox.mozdev.org/) 0.9.7.7 
[*][Full Fullscreen](http://emsearcy.org) 3.1 
[*][Greasemonkey](http://www.greasespot.net/) 0.8.20080609.0 
[*][InfoLister](http://mozilla.doslash.org/infolister) 0.10 
[*][last.fmCode](http://mll2.free.fr/?p=42) 0.7a 
[*][Linkification](http://yellow5.us/firefox/linkification/) 1.3.5 
[*][Nightly Tester Tools](http://www.oxymoronical.com/web/firefox/nightly) 2.0.2 
[*][Norsk Bokmål ordliste]() 2.0.10.0 
[*][Norsk Nynorsk ordliste]() 2.0.10.0 
[*][Tab Mix Plus](http://tmp.garyr.net) 0.3.6.1.080416 
[*][Text Link](http://piro.sakura.ne.jp/xul/_textlink.html.en) 2.0.2008052801 
[*][Tiny Menu](http://trac.arantius.com/wiki/Extensions/TinyMenu) 1.4.9 
[*][Ubuntu Firefox Modifications]() 0.5 
[*][Update Channel Selector](http://www.oxymoronical.com/web/firefox/updatechannel) 1.0.3 
[/list]

**Themes** (6)
[list]
[*]BlackX 2 
[*]Camifox [selected]
[*]Default 
[*]Firefox-Plus 
[*]MidnightFox 
[*]PitchDark 
[/list]

**Plugins**
[list]
[*]Default Plugin
[*]Demo Print Plugin for unix/linux
[*]DivX® Web Player
[*]GCJ Web Browser Plugin (using IcedTea) 1.0
[*]Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible; Totem)
[*]iTunes Application Detector
[*]QuickTime Plug-in 7.2.0
[*]Shockwave Flash
[*]Totem Web Browser Plugin 2.22.1
[*]VLC Multimedia Plugin (compatible Totem 2.22.1)
[*]Windows Media Player Plug-in 10 (compatible; Totem)
[/list]

---

### Post by Knacker on 2008-09-20
yup, i've been getting exactly the same thing for a while. it's infuriating...but firefox just seems to get less and less stable for me. it's crashing more and more often (some pages are not possible to open without crashing FF), it seems impossible to get a version of flash that all sites are happy with,cookies seems to just randomly not "work" anymore (nothing changed)...i love firefox, when it works. 

the right-click thing is a real bug. 

From Infolister:
Last updated: Sat, 20 Sep 2008 07:00:35 GMT
User Agent: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1
Extensions (enabled: 2, disabled: 1):

    * Greasemonkey 0.8.20080609.0 [disabled]
    * InfoLister 0.10
    * Ubuntu Firefox Modifications 0.5

Themes (1):

    * Default 3.0.1 [selected]

Plugins (10):

    * Default Plugin
    * Demo Print Plugin for unix/linux
    * DivX® Web Player
    * GCJ Web Browser Plugin (using IcedTea) 1.0
    * Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible; Totem)
    * QuickTime Plug-in 7.2.0
    * Shockwave Flash
    * Totem Web Browser Plugin 2.22.1
    * VLC Multimedia Plugin (compatible Totem 2.22.1)
    * Windows Media Player Plug-in 10 (compatible; Totem)

---

### Post by bingoUV on 2008-09-20
It won't help to post your add-ons here. All developers of all your add-ons will have to sit together with mozilla developers to analyze the possible cause. Even then it could be a configuration specific issue.

Disable all add-ons, themes etc by quitting firefox, and run
```

firefox -safe-mode

```

Browse this way for a while. If your problem comes back, file a bug on Ubuntu's firefox package. If not, you will have to disable one add-on at a time and check which one is causing the problem.

Try mozilla's build of firefox to see if that build has this problem: [http://www.mozilla.com](http://www.mozilla.com). Just download it, double click to unpack in a temporary directory and run the "firefox" executable from there.

---

### Post by peakshysteria on 2008-09-20
> **bingoUV said:**
> It won't help to post your add-ons here. All developers of all your add-ons will have to sit together with mozilla developers to analyze the possible cause. Even then it could be a configuration specific issue.

Disable all add-ons, themes etc by quitting firefox, and run
```

firefox -safe-mode

```

Browse this way for a while. If your problem comes back, file a bug on Ubuntu's firefox package. If not, you will have to disable one add-on at a time and check which one is causing the problem.

Try mozilla's build of firefox to see if that build has this problem: [http://www.mozilla.com](http://www.mozilla.com). Just download it, double click to unpack in a temporary directory and run the "firefox" executable from there.

My point was ofcourse if someone knew about problematic addons they could tell if he posted his FF version and addons etc here. Also [mozillazine]("http://forums.mozillazine.org/index.php") would be the best place to get help or find info on problematic addons (if this is the problem).

As you say running safemode will show if one or more addons are the cause of the problem. Run an update o your whole system before running FF in safemode. Good call man. I had the same problems two weeks back but my FF is now running smooth as ever again. Not sure what the problem was really.

---

### Post by utkjamie on 2008-11-20
There's an open bug report on this at [https://bugs.launchpad.net/ubuntu/+source/mozilla-firefox/+bug/148381. ]("https://bugs.launchpad.net/ubuntu/+source/mozilla-firefox/+bug/148381")

And yes...it is *extremely *annoying.

---

### Post by digitalbrain on 2008-11-20
This problem was also discussed here: [http://ubuntuforums.org/showthread.php?t=830676&highlight=firefox+click+bug](http://ubuntuforums.org/showthread.php?t=830676&highlight=firefox+click+bug)  
And the solution seems like using this add-on: [https://addons.mozilla.org/en-US/firefox/addon/39](https://addons.mozilla.org/en-US/firefox/addon/39)  (again from the same thread)
I'm using Firefox 3.0.4 and have been using this add-on for about 2 weeks and I _never_ had this problem again. Thanks to mouse gestures redox...

---

### Post by jocose on 2008-11-20
> **digitalbrain said:**
> This problem was also discussed here: [http://ubuntuforums.org/showthread.php?t=830676&highlight=firefox+click+bug](http://ubuntuforums.org/showthread.php?t=830676&highlight=firefox+click+bug)  
And the solution seems like using this add-on: [https://addons.mozilla.org/en-US/firefox/addon/39](https://addons.mozilla.org/en-US/firefox/addon/39)  (again from the same thread)
I'm using Firefox 3.0.4 and have been using this add-on for about 2 weeks and I _never_ had this problem again. Thanks to mouse gestures redox...

Thanks, I'll look into it, but such a solution may frustrate many of the newbie users I manage. Can you tell us how this resolves the issue? Why does this issue remain to begin with? Is it a Firefox specific bug (I experience it, too) or just something with Firefox in the repos?

---

### Post by digitalbrain on 2008-11-20
> **jocose said:**
> Thanks, I'll look into it, but such a solution may frustrate many of the newbie users I manage. Can you tell us how this resolves the issue? Why does this issue remain to begin with? Is it a Firefox specific bug (I experience it, too) or just something with Firefox in the repos?

:) I have no idea about the answers of your questions. Just install the add-on and give it a try. I wish I could have been more helpful.

---

