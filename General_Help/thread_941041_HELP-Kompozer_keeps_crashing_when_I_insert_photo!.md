---
title: "HELP-Kompozer keeps crashing when I insert photo!"
date: 2008-10-07
forum: General Help
---

### Post by schmindy on 2008-10-07
Distro- 8.10 Beta 32 bit
System- Acer Aspire 4720z
Problem- Kompozer Crashes Whenever I Try To Insert A Photo
Help is needed:sad:,
Alex

---

### Post by schmindy on 2008-10-07
bump...

---

### Post by jtpoole99 on 2008-10-19
I'm having the same problem with Kompozer.  Whenever I add a photo and then click the source tab to make changes to the image link I just added, Kompozer disappears and I have to start over.  Could someone suggest an auto-save feature for Kompozer while fixing this bug????:mad:

---

### Post by mutzinet on 2008-10-27
It's basically unusable for me, crashing all the time, whether I am adding a picture, opening a context menu, adding a link, etc.

---

### Post by jen1963 on 2008-10-31
I'm having the same issue with Kompozer under 8.10 Intrepid too.
Sacrilegious, but I'm stuck having to boot in to XPuke to edit web pages.
What is the fix?? 
:confused:

---

### Post by rbmorse on 2008-10-31
Kompozer is well and truly broken.  I don't think it's being developed anymore, either. 

I've gone to Seamonkey browser (which comes with a barebones editor) for quick and dirty work, and have Adobe Dreamweaver on an XP VMware virtual machine for heavier work.

---

### Post by dcstar on 2008-10-31
I have Kompozer 0.7.10 (20080314) on 8.04 64 bit and I seem to be able to insert pics fine using the Insert-Image function.

I once renamed the (hidden) .kompozer directory to get around some weird issues I had after a previous upgrade, I would suggest people try that as I have had no problems since.

---

### Post by rbmorse on 2008-10-31
Not a bad idea, but it didn't resolve the crash I get when trying to insert a link into a document.

---

### Post by dcstar on 2008-11-01
> **rbmorse said:**
> Not a bad idea, but it didn't resolve the crash I get when trying to insert a link into a document.

Also make sure that any old .nvu folders are also gone - Kompozer seems to use these to "upgrade" previous settings to the new .kompozer folder and you really want a fresh folder with no old stuff.

---

### Post by AndrewS on 2008-11-04
I have the same problem.  I'm using Kompozer 0.7.19 (20080314).  It worked fine in 8.04 and still does, but not in 8.10.

Andrew

---

### Post by AndrewS on 2008-11-04
I just ran Kompozer from a terminal, and got the following error:

[INDENT]pure virtual method called
terminate called without an active exception
Aborted[/INDENT]

Doesn't mean a lot to me though.  Anyone?

Andrew

---

### Post by rbmorse on 2008-11-04
Pretty much the same error for everyone

---

### Post by LeighT on 2008-11-05
Kompozer also crashes when trying to insert an external linked style sheet.
Error message:
pure virtual method called
terminate called without an active exception
Aborted
Also crashes with insert image:
Error message:
Segmentation fault
Is Kompozer still being developed?
If not we need some one to oick up the batten and run with it.
At the moment I am using Kompozer under wine, at least it hasn't crshed yet.
BTW Kompozer worked OK under Hardy.

Leigh

---

### Post by AndrewS on 2008-11-06
As Leigh says, Kompozer (0.7.10) worked fine under Hardy, so is the problem with Kompozer or Ununtu???

Andrew

---

### Post by huangweiqiu on 2008-11-09
:( same problem here,hope this bug can be solved soon! I can't be without Kompozer

---

### Post by AndrewS on 2008-11-10
Bump!

Any likelihood of a solution to this?  It's very inconvenient having to switch to 8.04 just to use Kompozer!

Andrew

---

### Post by crjackson on 2008-11-10
> **AndrewS said:**
> Bump!

Any likelihood of a solution to this?  It's very inconvenient having to switch to 8.04 just to use Kompozer!

Andrew

Well that's exactly what I did. Back to 8.04.1 and problem solved. Since it only happens on 8.10 wouldn't that be a Ubuntu issue rather than a Kompozer bug?

---

### Post by crjackson on 2008-11-10
As a test only you might try running kompozer from the terminal using sudo. I'm at work right now and can't test this or I would. If that works, it would seem to indicate POSSIBLY a permissions issue. If that is the case, you may be able to find the offending folder and change the permissions to fix this.

I'll check it out later this week and see if it works.

---

### Post by AndrewS on 2008-11-12
I tried running Kompozer as sudo from a terminal - still crashes...

AndrewS

---

### Post by houstonbofh on 2008-11-13
It is bugged.  Any submenus using the mouse will crash it. [https://bugs.launchpad.net/bugs/263441](https://bugs.launchpad.net/bugs/263441)  You can work around by using the keyboard to navigate submenus.  Strangely enough I have to use the mouse for cut and paste, however. :(

---

### Post by simplysimple on 2008-11-13
> **dcstar said:**
> I have Kompozer 0.7.10 (20080314) on 8.04 64 bit and I seem to be able to insert pics fine using the Insert-Image function.

I once renamed the (hidden) .kompozer directory to get around some weird issues I had after a previous upgrade, I would suggest people try that as I have had no problems since.


For once the simple fix is to run 64 bit :) too bad I had to run the 32bit for iSeries support at work. I guess virtualbox running xp to get into dreamweaver is the only feasible solution for an easy to use wysiwyg.

---

### Post by simplysimple on 2008-11-19
UPDATE: I've now tried Kompozer on the 64bit of Inrepid Ibex and still have the same issue. Must be related to Ibex somehow.

---

### Post by philinux on 2008-11-19
Crashes immediately when browsing the drop down menu's et al.
Borked I reckon. Fubarred
Segmentation Fault all the time.

[https://bugs.launchpad.net/bugs/+bugs?field.searchtext=kompozer&search=Search+Bug+Reports&field.scope=all&field.scope.target=](https://bugs.launchpad.net/bugs/+bugs?field.searchtext=kompozer&search=Search+Bug+Reports&field.scope=all&field.scope.target=)

---

### Post by PierreDeKat on 2008-11-19
I posted this in another thread a little earlier:

> Just an FYI, I'm using the Seamonkey suite, which includes Composer (with a C instead of a K, so not built around KDE), and it doesn't seem to have the same bug that the KDE version has.

It's definitely not crashed on me, anyway. And I can open "Recent Pages" without a hitch.

I started off, back in the days, with the Netscape suite, and followed it through the Mozilla suite phase, and now I'm using the Seamonkey suite, the closest thing to a descendant of Netscape, by my reckoning.

Never understood why the folks at Mozilla wanted to break the thing up into Firefox, Thunderbird and all that mess, anyway.

So many people have Firefox and Thunderbird installed, and then they're still sitting around thinking: dang, if only I had a program like Frontpage or Dreamweaver to maintain a website...

Well, they can thank the good folks at Mozilla for that puzzlement.

And you know what the funny thing is?

The whole idea about splitting up Netscape/Mozilla was to make the different modules load faster. And then they quickly proceeded to bloat each module up to the point where they take twice as long to load as the suite.

Seriously.

And just so y'all know, I can insert images with no problems, as well.

---

### Post by PierreDeKat on 2008-11-20
For the uninitiated, just some quick miscellaneous info about Seamonkey.

Seamonkey
[http://www.seamonkey-project.org/](http://www.seamonkey-project.org/)
(You can download Seamonkey for various operating systems there, but the easiest way, in this context, is to get Seamonkey from the Ubuntu repos.)

Once you get the Seamonkey suite installed, you can launch each component individually with:

Seamonkey Browser:
```
seamonkey
```

Seamonkey Mail and News:
```
seamonkey -mail
```

Seamonkey Composer
```
seamonkey -edit
```

Note: each component generally uses comparable or less memory than its Firefox/Thunderbird equivalent.

There are a lot of other ways to launch the individual components, things like "seamonkey -profilemanager", "seamonkey -p yourusername" for launching specific profiles, etc., but I won't go into them all.

Seamonkey has several of the same plugins that Firefox/Thunderbird have, but you generally want to make sure that you're installing the Seamonkey version.

To play Flash in Seamonkey, flashplugin-nonfree out of the Ubuntu repos works great, though you might have to temporarily uninstall and reinstall flashplugin-nonfree, just to make sure that a plugin gets created in the appropriate profile folder.

But for Flashblock, I've been using version 1.3.9, available here:
[http://downloads.mozdev.org/flashblock/](http://downloads.mozdev.org/flashblock/)

Some of my favorite Seamonkey themes, like "iCandy Junior" and "Rain", are here:
[http://www.spuler.us/](http://www.spuler.us/)

But there are lots of others available, as well.

It might be possible to share profiles with Firefox/Thunderbird, but it's probably best to create new profiles. Maybe import an old profile, but name it something different in Seamonkey.

Let's see here, what else ... oh yeah, Seamonkey's "Preferences" are a lot like KDE-style preferences, in that you have options for everything but the kitchen sink. Whereas, like Firefox, the "Preferences" are like the Gnome version, where you only have a few of the most desired options available.

So you might have to spend a little extra time figuring out how you want to set things up. For Composer, everything's pretty straightforward, but if you want to adjust the size of your internet cache for Seamonkey Browser, it'll take you a little time to sort through the Preferences to find that particular setting.

What else ... oh yeah, one more thing, since we're focusing on Seamonkey Composer. Your HTML *will* validate. Even if you're coding manually and, like, you forget a closing tag, Composer will add it for you.

I don't think I've ever used Composer and had my HTML fail a validation test.

Anywho, that's just some miscellaneous stuff off the top of my head. But try it. And if you don't like it, uninstall it. No biggie.

---

### Post by simplysimple on 2008-11-20
> **PierreDeKat said:**
> For the uninitiated, just some quick miscellaneous info about Seamonkey.

Seamonkey
[http://www.seamonkey-project.org/](http://www.seamonkey-project.org/)
(You can download Seamonkey for various operating systems there, but the easiest way, in this context, is to get Seamonkey from the Ubuntu repos.)

Once you get the Seamonkey suite installed, you can launch each component individually with:

Seamonkey Browser:
```
seamonkey
```

Seamonkey Mail and News:
```
seamonkey -mail
```

Seamonkey Composer
```
seamonkey -edit
```

Note: each component generally uses comparable or less memory than its Firefox/Thunderbird equivalent.

There are a lot of other ways to launch the individual components, things like "seamonkey -profilemanager", "seamonkey -p yourusername" for launching specific profiles, etc., but I won't go into them all.

Seamonkey has several of the same plugins that Firefox/Thunderbird have, but you generally want to make sure that you're installing the Seamonkey version.

To play Flash in Seamonkey, flashplugin-nonfree out of the Ubuntu repos works great, though you might have to temporarily uninstall and reinstall flashplugin-nonfree, just to make sure that a plugin gets created in the appropriate profile folder.

But for Flashblock, I've been using version 1.3.9, available here:
[http://downloads.mozdev.org/flashblock/](http://downloads.mozdev.org/flashblock/)

Some of my favorite Seamonkey themes, like "iCandy Junior" and "Rain", are here:
[http://www.spuler.us/](http://www.spuler.us/)

But there are lots of others available, as well.

It might be possible to share profiles with Firefox/Thunderbird, but it's probably best to create new profiles. Maybe import an old profile, but name it something different in Seamonkey.

Let's see here, what else ... oh yeah, Seamonkey's "Preferences" are a lot like KDE-style preferences, in that you have options for everything but the kitchen sink. Whereas, like Firefox, the "Preferences" are like the Gnome version, where you only have a few of the most desired options available.

So you might have to spend a little extra time figuring out how you want to set things up. For Composer, everything's pretty straightforward, but if you want to adjust the size of your internet cache for Seamonkey Browser, it'll take you a little time to sort through the Preferences to find that particular setting.

What else ... oh yeah, one more thing, since we're focusing on Seamonkey Composer. Your HTML *will* validate. Even if you're coding manually and, like, you forget a closing tag, Composer will add it for you.

I don't think I've ever used Composer and had my HTML fail a validation test.

Anywho, that's just some miscellaneous stuff off the top of my head. But try it. And if you don't like it, uninstall it. No biggie.

Thanks PierreDeKat...I will give it a try. Hopefully it works out as a solid replacement.

---

### Post by Northsider on 2008-11-24
I get the same errors...  so Kompozer is essentially useless?

---

### Post by AndrewS on 2008-11-24
As far as 8.10 is concerned, that about sums it up :(

---

### Post by mdkaneda55 on 2008-12-03
experiencing the same crap, crashes at random all the time in intrepid.. how lame. =\ how is sea monkey working for everyone? worth installing the whole kit n kaboodle just for html editing?? hehe.

---

### Post by houstonbofh on 2008-12-05
There is a very early port of Komposer with 1.8 geko available. He posted a link in the bug on launchpad.

[QUOTE=kaze@kompozer.net]I've done ~50% of the job (i.e. porting KompoZer to Gecko 1.8.1).

You can grab pre-alpha builds in this directory: [http://kompozer.net/zip/](http://kompozer.net/zip/) (i.e. the 'kompozer-YYYYMMDD.tar.gz files).
Some features haven't been re-implemented yet (e.g. source tab, templates, spell checker).

Please don't report any bug on these snapshots yet, *except* if you find
a way to crash KompoZer with these snapshots. KompoZer's test team
couldn't crash these snapshots so far, so I believe the upcoming version
should be pretty stable.

I'm doing my best to release a public version before the end of this year.
Tony > is there a procedure to replace KompoZer 0.7.10 with KompoZer 0.8 in Intrepid?

-- kompozer crashes in intrepid when opening the recent files menu [https://bugs.launchpad.net/bugs/263441](https://bugs.launchpad.net/bugs/263441) You received this bug notification because you are a direct subscriber of the bug.[/QUOTE]

So all is not yet lost. :D

---

