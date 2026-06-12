---
title: "HP Mini 210 TrackPad Problems...Again"
date: 2010-07-27
forum: Hardware
---

### Post by gunraidan on 2010-07-27
Hello I created a thread about this before, but I eventually (well thought) I figured out how to fix it. I went to [this thread]("http://ubuntuforums.org/showthread.php?p=9250735#post9250735") and changed the mouse set up to PS/2, then unchanged and added two finger scroll to x.config and it worked...for a day or two. After that when restarting the computer it either works fine or acts like it did before at random. It's usually determined whether or not the orange light on the top left is on or not. I mean it will work fine for a bit but 5 minutes later it will start acting strange again. If I put a finger on any edge of the trackpad it will scroll way up for no reason.

If I did what I did before i found that it usually works but only for one session. :(  I notice that HP Mini 210 and Ubuntu aren't exactly friendly to each other just yet, but I'm wondering if any problems have been ironed out since that thread?

---

### Post by gunraidan on 2010-07-28
Not a single reply? 

Come on people this is serious. :(

---

### Post by gunraidan on 2010-07-28
Nobody at all?

---

### Post by Dynaflow on 2010-07-28
I'll probably be buying one later today and paving over most of the hard drive with Ubuntu (pending the approval of the missus, of course).  I'll let you know if I encounter the same problem and, if so, how I solve it.

---

### Post by gunraidan on 2010-07-28
> **Dynaflow said:**
> I'll probably be buying one later today and paving over most of the hard drive with Ubuntu (pending the approval of the missus, of course).  I'll let you know if I encounter the same problem and, if so, how I solve it.

Thanks.

---

### Post by gunraidan on 2010-07-29
Last time I'll bump.

---

### Post by Dynaflow on 2010-07-29
Okay, I have now acquired a former floor model HP Mini 210-1080NR.  I have been playing around with Windows 7 before I install Ubuntu, and I have noticed that the track pad does indeed have a few weird quirks right out of the box.  However, HP seems to have put out a firmware or driver update of some sort for the track pad, and after installing the update through the HP update utility in the OEM Windows 7 installation (this is separate from Windows Update), the oddnesses have gone away.

We shall see whether or not they reappear in Ubuntu (i.e., whether or not the update was merely for the Windows driver, or for the track pad itself's firmware).  Do you still have a Windows partition on your machine, or did you wipe it out in the process of improving your computer with Linux?

---

### Post by Dynaflow on 2010-07-30
I have found that my Mini 210 has the same problem as yours.  I think it's the two-finger scrolling mechanism going haywire.  I suggest you try this:  [http://ubuntuforums.org/showpost.php?p=8989185&postcount=11](http://ubuntuforums.org/showpost.php?p=8989185&postcount=11)

[EDIT]

Actually, experience has now shown me that this approach does not work in Lucid.  However [this]("http://ubuntuforums.org/showpost.php?p=9516270&postcount=54") does seem to cure the trackpad of its worst eccentricities.  Just remember to take the ".txt" off the end of the attached file's name.  If you're not a command-line junkie, it's easy enough to move files around graphically with superuser privileges by typing into the terminal:```
gksudo nautilus
```

---

### Post by bleaked on 2010-07-31
This last suggestion 'works', but it still leaves the trackpad super sensitive.. especially when typing I get lots of jumping and right clicking input, sometimes highlighting and deleting when I barely brushed it.

What can I do to make these settings more sane?  Or could anyone else offer a better touchpad.conf?

Thanks!

[Edit] Also, and almost more importantly, I can't grab and drag or highlight.. This obviously sucks for text, but for resizing columns in nautilus or wherever.

---

