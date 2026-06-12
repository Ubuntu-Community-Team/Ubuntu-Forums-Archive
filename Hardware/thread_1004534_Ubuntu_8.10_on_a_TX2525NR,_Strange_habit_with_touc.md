---
title: "Ubuntu 8.10 on a TX2525NR, Strange habit with touchpad."
date: 2008-12-07
forum: Hardware
---

### Post by robm06 on 2008-12-07
Greetings once again, after my last post where I said, "Oh everything is fine." I've come to find out that everything isn't perfect, and since then I've removed Windows Vista from my system so I'm fixing this!

I have a strange problem that I can't figure out though, I've got the sound, wifi(worked OOTB), digitizer, graphic drivers, and such working.

I don't have the Webcam working, but I'm not in any hurry to work on that.

My question right now is on the touchpad below the keyboard. It seems that every now and then, not every time, but it will have strange behavior. I would push the right button to open the menu and it would instead perform a function such as open up "Bookmark this Page" or the "Save Link As" dialog boxes and I'm confused as to why it would do this.

Anyone have any idea what might be causing that? :)

---

### Post by Favux on 2008-12-10
Hi robm06,

I have also noticed since updating to 8.10 on my TX2110us that the Synaptic TouchPad seems "touchy" or "flaky".  My guess is this has something to do with HAL (Hardware Abstraction Layer) introduced with 8.10.  The Synaptic TouchPad is now run by a "script" in a fdo file with HAL.  Intrepid commented out by Synaptic TouchPad in xorg.conf.  I suppose I could remove those comments in xorg.conf and see if the TouchPad then behaves better, but I haven't.  I figure that somewhere in the continuing updates a fix will appear.

You could check your xorg.conf and see if there is a TouchPad section and whether it has been commented out.  If it is not there or has been commented out it is running through HAL.

---

