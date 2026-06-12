---
title: "Firefox suddenly slow to close"
date: 2008-07-22
forum: General Help
---

### Post by imbjr on 2008-07-22
Quite often now, Firefox displays briefly the "Force Quit or Wait" dialog when closed down. This has only started happening within a day or so.

Anyone else getting this?

---

### Post by unutbu on 2008-07-22
Occassionally my Firefox seems to hang too. I don't have a true fix, but can get things working again by opening a terminal and typing
```

% pgrep firefox
6004
6020
% kill 6020

```
The numbers that appear are process ID numbers (PID) (yours will in general be different than the ones I show above.) Select the largest PID and try to kill it first. (last to be spawned, first to be killed). 

If the process refuses to be killed (though I don't think that will happen with firefox), you can ensure its destruction with

```
kill -9 PID
```

Once the firefox windows disappear, simply restart firefox and you should be good to go.

---

### Post by imbjr on 2008-07-23
Thanks, but I'm talking about Firefox closing but not gracefully. It closes way before I'd be able to kill it, but it does now occasionally moan about "Wait or Force Quit".

---

### Post by linux6994 on 2008-07-23
I have noticed that if I have a page that has not yet filling in or streaming audio when closing firefox I will see that message. If I do not force quit and just wait until it ready, it closes fine on it own.

---

### Post by imbjr on 2008-07-23
> **linux6994 said:**
> I have noticed that if I have a page that has not yet filling in or streaming audio when closing firefox I will see that message. If I do not force quit and just wait until it ready, it closes fine on it own.

Yep, if I'm not quick enough (and the dialog is only apparent for a brief time), it does close. I don't know if filling in or some such is the cause here tho - I shall keep an eye on it.

Odd how this has just started to happen. I'm also getting slower bootup now. The notifications part of the top panel takes a while to appear and I noticed that the trash can too took a while. I think I will empty the trash actually - I have 3700+ items in it. Wonder if that's not helping.

---

### Post by foe83 on 2008-08-05
Same thing here, I see this happens more often when multiple tabs are open, or heavier websites... I have also tried to create a new profile (firefox -ProfileManager) and Firefox seems to close much faster (have not seen the message yet), perhaps it's some add-ons that cause the problem :confused:, I have installed AdBlocker plus, Foxmarks, Image Zoom, Ubuntu Firefox Modifications, what about you guys?

---

### Post by imbjr on 2008-08-05
Just Adblocker and the Ubuntu mods.

It's still happening but not in any particularly predictable way.

---

### Post by volanin on 2008-08-06
I am having this problem as well, with Firefox 3 in Hardy.
It's quite slower to open than Firefox 2...
... and a lot slower to close.

I don't get the Force Quit message.
But sometimes Firefox takes up to 5 seconds to close here.

I have moved the .mozilla folder and created a new profile,
but although things have improved, you can still see that
it's quite slower then Firefox 2, even if it's the only
program running.
:(

---

### Post by surfed on 2008-09-18
Any updates on this?

---

### Post by imbjr on 2008-09-19
It has stopped doing it!

However, I am now getting more instances of Firefox just suddenly dying upon visiting a page. Not much (and the session is usually restored), but still it's a noticeable change in behaviour.

---

### Post by tw805 on 2008-11-18
I had this exact issue. About 50% to 75% of the time it would display the "wait" or "force quit" dialog, just as you've described.

Looking for new java plugins due to (completely unrelated) issues I have on certain pages, I installed sun-java6-jre and sun-java6-plugin from synaptic, and this seems to have fixed it, leading me to think its some java-related bug...

let me know if it works for you.

(a whole bunch of dependent packages are downloaded with the two listed above as well)

tom

---

### Post by imbjr on 2008-11-19
Since installing 8.10 I have not seen Firefox delay in closure or crash.

---

### Post by Aearenda on 2008-12-06
I have been getting very annoyed by this issue (using 8.10) - but removing Google Gears has fixed it for me.

---

### Post by ElDave on 2008-12-07
Like a few other posters, I also have AdBlocker installed and Firefox hangs when I try and close the program. Disabling AdBlocker has helped speed up closing, so I don't know if there was a recent update that takes up more resources than before or what. Anyone have any ideas?

---

### Post by latecomer on 2008-12-21
Same problem here, and the only extension I have is Adblock Plus. I seem to remember there were a few Adblock updates recently. Does anyone not using Adblock have this problem?

---

### Post by imbjr on 2009-04-06
Well, looks like Firefox is doing this again!

I have the odd feeling that when I install Jaunty, this will stop.

---

### Post by endotoxin on 2009-04-13
I've seen Firefox paging a LOT of data to disk on close. I guessed it might be FF writing it's memory cache to disk, took a chance, and disabled disk caching. Bing, problem solved! The easiest way to accomplish this is to pull up about:config, search for browser.cache.disk.enable, and set it to false.

---

### Post by imbjr on 2009-04-14
> **endotoxin said:**
> I've seen Firefox paging a LOT of data to disk on close. I guessed it might be FF writing it's memory cache to disk, took a chance, and disabled disk caching. Bing, problem solved! The easiest way to accomplish this is to pull up about:config, search for browser.cache.disk.enable, and set it to false.

Isn't that destroying your capability to cache web pages any their contents though? Every time you re-visit a site it will have to all be downloaded.

---

### Post by rescyou on 2009-04-16
I had the same problem with 8.10 and firefox and I found this little trick:

 _[http://weblog.savanne.be/153-performance-tip-of-the-day:](http://weblog.savanne.be/153-performance-tip-of-the-day:)_

Basically

*EDIT*  Install SQLITE3 first: **sudo apt-get install sqlite3**  *EDIT*

1. Close firefox
2. Open terminal and manually type: 

** for f in ~/.mozilla/firefox/*/*.sqlite; do sqlite3 $f 'VACUUM;'; done**

*(copy/paste may not work right for some reason so you may have to manually type it)*

After that firefox shuts down a lot faster.

---

### Post by imbjr on 2009-04-16
> **rescyou said:**
> I had the same problem with 8.10 and firefox and I found this little trick:

 _[http://weblog.savanne.be/153-performance-tip-of-the-day:](http://weblog.savanne.be/153-performance-tip-of-the-day:)_

Basically

1. Close firefox
2. Open terminal and manually type: 

** for f in ~/.mozilla/firefox/*/*.sqlite; do sqlite3 $f 'VACUUM;'; done**

*(copy/paste may not work right for some reason so you may have to manually type it)*

After that firefox shuts down a lot faster.


Well, I gave that a whirl. Should be interesting to see if I get the slow-down again. I notice that I still have one sqlite file at 14Mb.

---

### Post by StuartN on 2009-04-16
From 3.0 I had occasional hangs with disk thrashing that lasted 30-60 seconds. I tried several forum suggestions, but in the end I backed up my bookmarks, uninstalled Firefox, deleted the ~/.mozilla folder and re-installed. It works fine now.

---

### Post by fbobraga on 2009-06-06
> **rescyou said:**
> I had the same problem with 8.10 and firefox and I found this little trick:

 _[http://weblog.savanne.be/153-performance-tip-of-the-day:](http://weblog.savanne.be/153-performance-tip-of-the-day:)_

Basically

1. Close firefox
2. Open terminal and manually type: 

** for f in ~/.mozilla/firefox/*/*.sqlite; do sqlite3 $f 'VACUUM;'; done**

*(copy/paste may not work right for some reason so you may have to manually type it)*

After that firefox shuts down a lot faster.

same issue here... the trick above seems ti fixed that :P

---

### Post by surfed on 2009-06-06
> **rescyou said:**
> I had the same problem with 8.10 and firefox and I found this little trick:

 _[http://weblog.savanne.be/153-performance-tip-of-the-day:](http://weblog.savanne.be/153-performance-tip-of-the-day:)_

Basically

1. Close firefox
2. Open terminal and manually type: 

** for f in ~/.mozilla/firefox/*/*.sqlite; do sqlite3 $f 'VACUUM;'; done**

*(copy/paste may not work right for some reason so you may have to manually type it)*

After that firefox shuts down a lot faster.


Works for me.

---

### Post by Abhinav Gupta on 2009-06-14
The following has worked for me: I checked my firefox add-ons, and discovered a mysterious add-on: 'Ubuntu Firefox Modification'. I disabled it, and things are lightning quick, no 'wait/force quit' messages, etc.

---

### Post by endotoxin on 2009-07-02
> **Abhinav Gupta said:**
> The following has worked for me: I checked my firefox add-ons, and discovered a mysterious add-on: 'Ubuntu Firefox Modification'. I disabled it, and things are lightning quick, no 'wait/force quit' messages, etc.

And this works brilliantly for me as well. Thanks for the recommendation Abhinav Gupta!

---

### Post by linfidel on 2009-07-02
I've had problems with Firefox for a pretty long time now; it sometimes will hang for several seconds when playing a video, and it consistently takes too long to shut down (five or ten seconds, causing the dialog offering to kill it before finally quitting).

I tried all the suggestions I've seen, unsuccessfully.  I went into the profile manager, and created a new profile, and then it seemed to shut down right away, but I had no addons.

So, I went back to my old profile, to disable addons; the first one I disabled was Google Toolbar, and it started shutting down quickly.  Then, I enabled it, thinking I would see if an option made a difference.  Right away, on the restart, it was slow to shut down.

I disabled the option for sending usage statistics, and that sped it up, so far.

I haven't had enough time to see if other problems still occur, though.  Could be the usage statistics has some problem on my system.

The only other addons I have is Duplicate Tab, and the Ubuntu addon that they always add.  I'm not really sure what that one does, but it's hard to believe that it makes a difference like some has indicated.

At one point, I even uninstalled Compiz to see if that mattered - it didn't.  Since I use Firefox so much, this problem has been severe enough to keep me from using Ubuntu as often as I used to.  :(

---

### Post by gbuntu55 on 2009-07-17
> Originally Posted by rescyou;
I had the same problem with 8.10 and firefox and I found this little trick:

[http://weblog.savanne.be/153-perform...ip-of-the-day:](http://weblog.savanne.be/153-perform...ip-of-the-day:)

Basically

1. Close firefox
2. Open terminal and manually type:

for f in ~/.mozilla/firefox/*/*.sqlite; do sqlite3 $f 'VACUUM;'; done

(copy/paste may not work right for some reason so you may have to manually type it)

After that firefox shuts down a lot faster.

This also worked great for me after installing sqlite3:

```
sudo apt-get install sqlite3
```

Thanks, rescyou!

---

### Post by linfidel on 2009-07-17
> **gbuntu55 said:**
> This also worked great for me after installing sqlite3:

```
sudo apt-get install sqlite3
```Thanks, rescyou!I'll bet it didn't work so great before installing sqlite!  :)

I think I may have tried that a while back, but I'm trying it again, just in case.  But, I have another work around that I've been using.  I open Firefox to a blank or static page, then move it to my last virtual desktop, minimize it, and forget about it.  I then go back to my original desktop, and open/close a new Firefox window whenever I need it.

At least this way, I only have to wait once, if I shut down or restart.

---

### Post by bbyam on 2009-07-23
I second the google toolbar issue.

I had the problem where 99% of the time, even only opening firefox to Google.com homepage, when I close firefox it would take about 5 seconds to close, thus popping up the Force Quit dialog, then everything went away on its own every time.

I went to Tools->Add-Ons, and the Preferences for Google Toolbar.  In there, at the bottom of the "Search" options, was an option called "Send usage statistics to Google" that was checked.

I unchecked it, and now Firefox shuts down immediately in 10 of 10 tries so far.

---

### Post by digao45 on 2009-08-09
Clean the profile, this may help
[http://robert.accettura.com/blog/2006/05/03/cleaning-a-firefox-profile/]("http://robert.accettura.com/blog/2006/05/03/cleaning-a-firefox-profile/")

Rodrigo Travitzki
[digao.bio.br]("http://digao.bio.br/")

---

### Post by digao45 on 2009-08-11
*Quite often now, Firefox displays briefly the "Force Quit or Wait" dialog when closed down.*

Try to clean the personal data (menu>tools) in firefox. this work to me

Rodrigo Travitzki
[digao.bio.br]("http://digao.bio.br")

---

### Post by ancientpaint on 2009-11-29
> **rescyou said:**
> I had the same problem with 8.10 and firefox and I found this little trick:

 _[http://weblog.savanne.be/153-performance-tip-of-the-day:](http://weblog.savanne.be/153-performance-tip-of-the-day:)_

Basically

1. Close firefox
2. Open terminal and manually type: 

** for f in ~/.mozilla/firefox/*/*.sqlite; do sqlite3 $f 'VACUUM;'; done**

*(copy/paste may not work right for some reason so you may have to manually type it)*

After that firefox shuts down a lot faster.


I am using karmic.  This fixed my problem. Thanks

---

### Post by Clancy_s on 2009-11-30
> **ancientpaint said:**
> I am using karmic.  This fixed my problem. Thanks

Mine too, I think (it wasn't everytime): but first I had to install sqlite3 - using synaptic, from standard sources.

Thanks from me too.

---

### Post by imbjr on 2009-11-30
Well, I never had this problem for juanty; we shall see if karmic can keep up the good run.

---

