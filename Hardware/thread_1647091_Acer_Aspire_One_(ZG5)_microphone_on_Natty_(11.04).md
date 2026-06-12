---
title: "Acer Aspire One (ZG5) microphone on Natty (11.04)"
date: 2010-12-16
forum: Hardware
---

### Post by BrianTheLion on 2010-12-16
Hi,

I just upgraded - format, clean install - to 11.04 and am still having problems with the microphone on my Acer Aspire One (model ZG5) laptop. This problem has been described by a number of people in a number of different threads, but I have yet to see a fix that addresses it directly.

Symptoms: The built-in microphone works under the Sounder Recorder, but does not work under other applications (Skype for example). It can be made to work temporarily by installing pavucontrol and setting left and right mic channels to different levels.

I've tried setting ALSA's "snd-hda-intel model=" option to "auto", "acer", "acer-aspire", etc. Nothing seems to fix the problem permanently. Does anyone have a definite solution for this?

Thanks in advance!
~br

---

### Post by hanexar on 2011-04-27
This has been a problem for way too long... nobody seem interested in fixing it.

Mic through input work tho. But I'd like to see a good fix for this.

---

### Post by Dualta on 2011-06-02
I ran into this problem some time ago, it's been a problem in the last few versions.

You can manually fix the problem with pavucontrol but a better fix is to add the following lines to a script and set to run on startup:

```

amixer set "Mic Boost",0 100%,0%
amixer set "Capture",0 100%,0%

```

Hope this helps

---

### Post by IanRPeachey on 2011-06-16
thanks so much for this - I've just installed 11.04 on an Aspire One (ZG5) machine and ran into exactly the same problem.
Have created the script - just as you have said, runs on start-up ... problem solved.
Thank you  :-)

---

### Post by jurica1104 on 2011-07-13
> **Dualta said:**
> I ran into this problem some time ago, it's been a problem in the last few versions.

You can manually fix the problem with pavucontrol but a better fix is to add the following lines to a script and set to run on startup:

```

amixer set "Mic Boost",0 100%,0%
amixer set "Capture",0 100%,0%

```Hope this helps


How you "set to run on startup" this script? Iam new in Linux so need some help. thnks

otherwise it works until you restart OS

---

### Post by pucouajio on 2011-08-19
Easiest way I guess to run these lines at startup, is ..

First copy the two lines above so they are in your clipboard.

Now go to your Home Folder, then in the View menu, select "Show Hidden Files".  Right-click the file ".profile" and select "Open with Text Editor".  At the end of the file, add an extra line and then paste those two lines so they are two new lines at the end of the file.  Save it.  Now unselect "Show Hidden Files" if you wish.

Next time you login to your computer (as you), these two lines will be executed and you should find that when you go in to Sound Preferences and open the "Input" tab, if you talk in to the microphone you will see the Input Level meter shows how loud you are talking.

The only real disadvantage of this solution is it will only work for you, not for other users of your netbook.  They will need to do the same under their own login if they want to use Skype too.

Many thanks Dualta for the solution btw.  :D

---

