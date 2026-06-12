---
title: "Upgraded to 9.10 Karmic and I have problems :("
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by ekual on 2009-10-29
Hi I have 8.9 inch acer aspire one ZG5,

I have just upgraded to 9.10 Karmic and I have come across one problem so far: I have an external monitor 15 inch NEC AccuSync LCD montior attached. It was working with 9.04 Jaunty perfectly but now that I have upgraded I can't use it as the main display and worse yet when I select resolution 1024 x 768 (4:3) it causes some kind of error (Please see 3.png) I can only select 800 x 600 (4:3) and below.

1

[img]http://img.photobucket.com/albums/v314/ekual/1.png[/img]

2

[img]http://img.photobucket.com/albums/v314/ekual/2.png[/img]

3

[img]http://img.photobucket.com/albums/v314/ekual/3.png[/img]

All suggestions are appreciated.

Thank you

---

### Post by ekual on 2009-10-29
bump

---

### Post by Newfoundlander on 2009-10-29
I had a similar problem with my wife's system where it only offered one screen resolution.

In the terminal, I typed
sudo gedit /etc/X11/xorg.conf

and added a line that said *Virtual 2048 790*

Perhaps take a look at your xorg.conf and see if it has a screen resolution listed (if not, try adding one or search the forms for other posts about xorg.conf).  Good luck with your screens.

Cheers,

Steve

---

### Post by ekual on 2009-10-30
Hi thanks for your reply. I just tried that it didn't work. I don't think that would be the problem as it was wroking in Jaunty fine and as soon as I upgraded this happens :(

---

### Post by scotty2 on 2009-10-30
Two thoughts:

1)  Have you tried the "Detect Monitors" option?

2)  I think the refresh rate should be 60Hz, not 75Hz.

---

### Post by ekual on 2009-10-30
Yes I have and it detects the monitor obviously as mentioned in the first post I can select resolutions anything below 1024 x 768 but not 1024 x 768  it self.

It was 75Hz before on Ubuntu 9.04 Jaunty. It's a newer operating system why isn't it capable of simple things?

The laptop screen itself is 60Hz but the external monitor is 75Hz, this worked on Jaunty.

---

### Post by scratman on 2009-10-30
This is a shot in the dark, but it might be that the drivers you are using causing the problem.  Go to System > Administration > Hardware Drivers and see whether there are any alternative drivers for your video card.

---

### Post by ekual on 2009-10-30
Hey thanks for replying.

I checked there are no alternate drivers suggested. I though that Karmic was suppose to have better support for Intel drivers? I mean with Jaunty everything worked well except for the fact that playing movies was choppy. I thought that upgrading could only get better but this is making this so hard. Why is Ubuntu so hard to work with I mean for simple things to not work like this and having to use your spare time researching on how to make your extended desktop (using the external monitor) work!

Anyway ignore my rant my graphics are an integrated Graphics Media Accelerator 950 processor on an Acer aspire one ZG5 AOA150 netbook (please don't recommend UNR, I've tried it and didn't like it)

---

### Post by ekual on 2009-10-30
bump bump

---

### Post by skotos on 2009-10-30
A quick and dirty solution/suggestion: you may probably simply reuse the 9.04 /etc/X11/xorg.conf.
Look inside /etc/X11 and see if you can find the old file that has been replaced/renamed.
If you find it or even an old working version, you might simply rename the files to start X with the old xorg.conf.

If this does the trick, you might later run meld and compare the files to understand what has changed...

---

### Post by ekual on 2009-10-30
I have just got home to find when I boot up in Ubuntu it just loads Terminal and not the full desktop environment. I tried to boot up in recovery mode and it failed to fix or find any errors.

So I have reinstalled ubuntu 9.10 as clean install. I have found the same error as posted in the first post.

I am unable to retrieve the old file because it is now been erased with 9.04. :(

---

### Post by ekual on 2009-10-30
bump

---

### Post by ekual on 2009-10-30
Could this be an issue with Karmic not having xorg.conf anymore? There must be someone out there with the same problem?

---

### Post by ekual on 2009-10-30
bump bump bump

---

### Post by ekual on 2009-10-30
I just booted in both Windows 7 and Mac OS X Leopard. Both have the correct resolutions and both are set to 75Hz and working brilliantly.

Why is Ubuntu doing this to me :(

---

### Post by ekual on 2009-10-31
hmm

---

### Post by ekual on 2009-10-31
Bada bing,

---

### Post by ekual on 2009-10-31
bummmmmmmp

---

### Post by ekual on 2009-10-31
Is it time to give up and revert back to Windows?

---

### Post by ekual on 2009-10-31
So many people are having problems with Karmic, I think it's time for an update!

---

### Post by ekual on 2009-10-31
Tut

---

### Post by ekual on 2009-10-31
I am not giving up until someone helps me! :D

---

### Post by X1R1 on 2009-10-31
Dude....posting like that makes the thread harder to read and understand, you now have to go back 2 pages to see your first post, I forgot what was your real problem cause of those "bump bump", "tut" posts. I bet you people stopped replying not because they don't know how to solve it but instead because they get annoyed for the post.

That being said, try to reconfigure your xorg.conf file:

> $ sudo dpkg-reconfigure xserver-xorg

If that doesnt help, download and install ubuntu tweak application, get it [HERE]("http://ubuntu-tweak.com/downloads")

after you install, open ubuntu tweak, inside ubuntu-tweak go to applications-> third party software sources and check "Ubuntu X" DONT check the ubuntu x unstable, just the normal one. Then open the updater and see if there are updated packages, if they are continue with the install and then try again.

---

### Post by grinaldi on 2009-11-03
> **ekual said:**
> Hi I have 8.9 inch acer aspire one ZG5,

I have just upgraded to 9.10 Karmic and I have come across one problem so far: I have an external monitor 15 inch NEC AccuSync LCD montior attached. It was working with 9.04 Jaunty perfectly but now that I have upgraded I can't use it as the main display and worse yet when I select resolution 1024 x 768 (4:3) it causes some kind of error (Please see 3.png) I can only select 800 x 600 (4:3) and below.

1

[IMG]http://img.photobucket.com/albums/v314/ekual/1.png[/IMG]

2

[IMG]http://img.photobucket.com/albums/v314/ekual/2.png[/IMG]

3

[IMG]http://img.photobucket.com/albums/v314/ekual/3.png[/IMG]

All suggestions are appreciated.

Thank you

If you have not resolved your display problem.

I got the same problem with my display, shown in your third picture, when I upgraded my elonex webbook with Ubuntu 9.10 and saw your post when I was looking for a solution. I have now solved this problem in the following way:

I started my Webbook in recovery mode, by pressing ESC key when the screen showed "press ESC to entre menu", then selected one of the recovery modes.

When the "Recovery Menu" appeared I selected "resume  Resume normal boot"

Finally I got an "ubuntu login:" prompt and logged in.

I had problems editing the /etc/X11/xorg.conf file

However, thanks to Hygaphunkik, who suggested using:

sudo nano /etc/X11/xorg.conf

I was able to edit the said file and insert:

Section "Device"
Identifier "Configured Video Device"
Driver "OpenChrome"
option "PanelSize" "1024x600"
option "ForcePanel"
EndSection

Being suggested by Hygaphunkik from [http://webbookblog.com/](http://webbookblog.com/)

This cured my display problems

I know you have a different machine, but the above might work directly, or after a tweak?

As you will notice I am a novice, willing to learn.

Let me know how you get on.

---

