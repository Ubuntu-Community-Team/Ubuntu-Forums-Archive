---
title: "Keyboard unresponsive after hitting alt or ctrl"
date: 2016-10-16
forum: Hardware
---

### Post by Moose32315 on 2016-10-16
As the title says I'm having trouble with my keyboard.  Hitting certain keys on my keyboard seem to disconnect my keyboard from the computer and I have to "unplug" the USB and "reconnect" it.  It doesn't happen every time either.  On some occasions it'll happen without me typing anything, but the main offenders are alt, ctrl, and the down arrow.  For that reason I can't copy or paste anything with the keyboard shortcuts, which is really annoying.

It might help to have a bit more background about my keyboard.  I bought a USB mechanical keyboard.  This keyboard has a USB connector from the keyboard to my computer (the power cord isn't hardwired to the keyboard).  Unfortunately, the mini-usb port wasn't attached very well to the circuit board of the keyboard.  So I found directions online to hard wire the power cord to circuit board.  That was the first time I've soldered anything so it was a shoddy job.  On occasion the power cord will get loose and I'll loose power, but I can shift the power cord a bit to restore power.  

When this issue occurs the keyboard appears to have power, but I was wondering if there could be some sort of micro power outage that was causing issues.  When the keyboard looses responsiveness I have to shift the power cord to loose power and then shift it back to regain power. 

I'm somewhat new to linux.  I also have a windows partition on this machine, and I've never had this issue on the windows side.  Does anybody have any ideas?

---

### Post by Moose32315 on 2016-10-16
I noticed that alt acts as a shortcut for unity, and changed it to the windows key instead.  It seems that alt isn't causing me issues anymore, but copy and pasting does.  Perhaps it's something with those commands that are disabling my keyboard.

---

### Post by Moose32315 on 2016-10-16
I did some more searching related to copying and pasting.  I'm not entirely sure why but I seem to have found a solution.

If I open system settings, go to language and text, and turn off most of the features (Auto correction, word suggestions, Auto capitalization, Auto punctuation, and keyboard vibration) the issues seems to be fixed.  I'm not sure why those settings were interfering, but at least it's working.

I've been trying to figure this out all day, and I finally figure it out a few minutes after I posted the question.  Oh well, hopefully this might help somebody else in the future.

---

### Post by Moose32315 on 2016-10-22
That didn't actually seem to help after all.  The next day the issue returned.

I happen to have another issue today in which speakers would mute and un-mute them selves repeatedly.  This problem happened in both windows and Ubuntu.  It seemed to stop when I unplugged the keyboard.  Although, I don't know how that would be caused by the keyboard since I don't have a key to mute the sound.

I reluctantly decided to open up my keyboard, and noticed there happened to be some water in it.  I'm not sure how it got there, but I dried it out.  Since it was opened I tried res-soldering the loose connection.  It was really close to another wire, and I ended up putting a piece of cardboard between the two so the solder wouldn't bridge the gap. 

So far it seems to have worked.  Hopefully that fixed the issue for good.

---

