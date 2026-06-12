---
title: "The dreaded &quot;UNABLE TO MOUNT LOCATION&quot; problem (usb)"
date: 2008-08-02
forum: General Help
---

### Post by Schallplattenparade on 2008-08-02
I've been a happy ubuntu user for over a year now ... 
I'm not the biggest computer and programming expert, hence I don't have the time to go digging in a thousand forums to find the solution for my problems , I just like things to work as they should ( and have always done)

So the main problem is that NONE of my USB-devices is recognized , Sometimes it pops up, but when trying to open the volume I get the "unable to mount location" error , but no worries , most of the times my usb devices don't even show up.... I know this is a known problem and there's a thousand threads dealing with it but none of them gives a simple soulution or answer ... I'm a bit surprised this isn't been solved by now ....
Funny thing is that in every case I found after googling is that everybody declares everything worked fine under the previous version "7.whatever"

So , I thought , let's have a fresh install and try my luck.... the only thing I want to know is : will all my data still be there or will everything be overwritten ....

---

### Post by doorman on 2008-08-19
If you don't mess with your partition table, sure, the data will still be there.

To make sure the data is there, during the installation process, when the partitioning step comes up, choose the manual configuration. You should then be able to see your partitions. The crutial step is to make sure all the format fields are UNCHECKED! For obvious reasons, the swap partition can be formatted safely, but please, do not format the /home partition (if you have one, if not, the / partition).

As far as the usb problem goes, i had that unable to mount problem once. For me it turned out it was a gnome permissions problem - it can be configured in the gnome administration pannel ( sorry, can't tell you more because i don't use gnome any more and forgot the exact name of the section, but it's at least a hint :P ).

And, finally, concerning the not-recognizing-devices problem: BUMP...

---

### Post by cleopete on 2008-08-20
My USB drives were mounting like zoo pandas under 8.04, but for some reason it stopped working a few weeks ago. I don't know why. I'm new to Ubuntu, and pretty reckless with my experimentation and installation of shiny new packages.  I couldn't really hazard a guess as to what I might have specifically done.  I've been playing a lot with Apache, PostgreSQL, and Amarok...

Like a lot of people, my thumb drives will work if they are installed at boot, but not if you remove/install any.  They always show up in the file browser, but just won't mount.

I've tried several suggestions, but so far no good.

---

