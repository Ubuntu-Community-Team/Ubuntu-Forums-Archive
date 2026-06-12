---
title: "Video blinking and not attaching to windows (fglrx driver, compiz-fusion)"
date: 2008-10-30
forum: General Help
---

### Post by Nitrolinken on 2008-10-30
Hello people of the forums! :KS

I've recently stumbled into a problem I used to experience before on my stationairy computer (before I sadly left it in the dust). I then got a laptop with an nVidia card and the problem disappeared. Now that I got myself a laptop with an ATI (HD 3470) card the problem has returned.

The problem is as follows: any video playback while using Compiz-Fusion (or any other composite manager) "blinks" and doesn't actually attach or stay inside the parent window. This is really annoying and is at times also hurting my eyes, so it's not just a general annoyance. 
I took a peak at the old but probably still working thread over at the Compiz-Fusion forums about setting up the fglrx driver [[http://forum.compiz-fusion.org/showthread.php?t=6794]](http://forum.compiz-fusion.org/showthread.php?t=6794]).

Any help, tips, anything really will be really great as I'd love to get this fixed. Rather not at the expense of using Compiz-Fusion, but that'd depend. :)

My xorg.conf is attached in case it is of any use.

---

### Post by flav0rl3ss on 2008-11-01
Same issue with an ATI Radeon x1650. *bump*

---

### Post by loomsen on 2008-11-02
Try changing Option VideoOverlay on... I slightly remember a friend of mine mentioning sth like this.

And, it's pretty reasonable actually ^^ If Video lay over ^^

---

### Post by arrancaru on 2008-11-02
Try setting x11 video driver in mplayer or vlc media player or in any other video player you are using.

---

### Post by erlguta on 2008-11-03
Same problem with ATI HD Radeon HD3450.

It is a known bug by the PATHETIC support form ATI to linux:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/179042](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/179042)

Collaborate with this feedback form, complaining about it:
[http://support.ati.com/ics/survey/survey.asp?deptID=894&surveyID=508&type=web](http://support.ati.com/ics/survey/survey.asp?deptID=894&surveyID=508&type=web)

---

### Post by kidnapper on 2009-02-26
I solved the problem by removing all packages that are related to compiz.

aptitude search compiz

aptitude remove [...]

---

### Post by Mercury_Alpha on 2009-02-27
Unfortunately, from what I have read, your only option for now is to disable Compiz effects or to use the software renderer (X11).

To disable Compiz effects: System>Preferences>Appearance, click on Visual Effects tab, select None.

It's an ATI-specific problem.

---

### Post by booshire on 2009-02-27
ATI drivers have not been around long. I think they just threw some crap together and said, "Okay, now those linux assholes will quit bitching at us", but sadly, the drivers they gave suck. I have never had 100% with ati drivers, even without the compiz effects. Why not just forgo them for now and find a way to help modify the drivers or give up.

---

### Post by Ze MoreiRa on 2009-03-14
> **arrancaru said:**
> Try setting x11 video driver in mplayer or vlc media player or in any other video player you are using.

That Works
Thanks I owe you

---

