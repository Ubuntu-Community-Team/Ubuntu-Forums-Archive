---
title: "video problems with 7.10 on acer laptop"
date: 2008-02-25
forum: Hardware &amp; Laptops
---

### Post by jsstuart on 2008-02-25
I have an Acer Travelmate 290E.  I just installed Ubunto 7.10 (over an existing installation of Ubunto 6.06 that worked just fine) and I'm having trouble with the display.  During bootup, when the ubuntu logo comes up with the scrolling status bar underneath, it looks great.  Then the screen briefly flashes to text and when it comes back to graphics, it looks terrible.  It continues to look terrible after I log in.  By terrible, I mean it sort of looks like an old television getting a weak signal with lots of noise (though no ghosting).  The colors are all slightly off and streaky looking, and there is lots of speckle noise that moves as I rearrange things on the screen.  Again, the screen looked fine with 6.06, and it looks great briefly during bootup with 7.10, then it goes bad.

I greatly appreciate any help as my wife is anxious to have her kitchen computer back.

Scott

---

### Post by suibhne on 2008-02-25
Did you install from a disk or did you upgrade via the update manager?

---

### Post by jsstuart on 2008-02-26
I installed from CD.  The update manager wasn't seeing the upgrade path.

---

### Post by suibhne on 2008-02-26
Right

I had a similar prob, but not exactly the same, so, the easiest way from my point of view is to do the following first and then if it doesnt work, post me back and We can try something else....

Re-install 6.06

make sure your settings are the desired ones

Update via the update manager


(BTW - do you know how to put you Home folder on a seperate partiton? If not, we can do that later)

---

### Post by jsstuart on 2008-02-26
The reason that I upgraded via CD was that I couldn't get the update manager to find the 6.06 -> 6.10 update.  I'm not sure why it didn't update in late 2006, as I had the update manager running the whole time and have been applying all of the recognized updates.

I think that I will try to go through the X windows configuration files and see if there is anything I can fix in there before I go back to 6.06.  The fact that the startup and shutdown screens look good makes me think it is something in the X setup that is not right.

Scott

---

### Post by jsstuart on 2008-02-27
I compared the xorg.conf file from the new installation of 7.10 to the previous file from 6.06 (which I had stashed on a USB drive along with pretty much the entire hard drive).  The new xorg.conf file was essentially a generic version.  After I set up the device driver, and monitor entries to match what was in the old xorg.conf file, everything works fine.

Thanks for th help.

Scott

---

