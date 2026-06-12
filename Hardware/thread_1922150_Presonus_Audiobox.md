---
title: "Presonus Audiobox"
date: 2012-02-08
forum: Hardware
---

### Post by cowboystitching on 2012-02-08
Hi everybody, I hope I'm posting this in the correct section of the forum, if not, mods, feel free to move it.

Right now I'm using a laptop I recently converted over from Windows (Compaq Presario, can't remember the year or model number; it's not my computer to start with) to the newest version of Ubuntu and like it so much that I want to switch from my Mac OSX based machine.  Long story short I do lots of music recording and would like to experiment further with programs like Ardour and whatnot.

However, my current audio interface is a Presonus Audiobox, which some people have said works flawlessly with this distro and other people have been having issues with.  I plugged it in and under system settings/sound it's recognized as "Presonus Audiobox" and the mic input checks out great, and sound is able to be played back through the interface as well.  The issue I'm running into is that JACK or in my case qjackctl is not recognizing the interface as an audio in, and under the ALSA tab it only comes up as a midi input/output.  Do I need to manually set the soundcard as the Audiobox?  If so, how do I go about doing that?  Would a program like Alsamixer help?  It doesn't seem like a compatibility issue since the computer was able to recognize and receive/send audio through the interface.  This is a fairly common interface and quite a good one, so I'd like to keep using it.  Anybody who has solved the predicament or has general advice about syncing an interface with JACK would be greatly appreciated.

-Andrew

---

### Post by cowboystitching on 2012-02-15
So after alot of searching and some trial and error I can say I've successfully configured this interface to run with Ubuntu.  

First plug the unit in and then you can type "sudo alsamixer" and then you can hit F6 to see what number your Audiobox has been assigned; though this is totally not necessary it is nice.

Next open qjackctl and open the setup panel, and from there MAKE ABSOLUTELY SURE YOU DON'T SAVE THE SETTING AS DEFAULT. This happened to me, and boy where did those 6 hours of reconfiguring defaults go? After that you probably won't be able to set the interface but that's OK, you just need to configure the input and output devices as Presonus Audiobox USB or whatever it's coming up as in the panel.  (Which is accessible by the little > signs next to the device listings) Then set your input and output channels to 2. Also make sure you set Periods/Buffer to 3.  I also set my sample rate at 48k as opposed to 441, but that seems to be what my machine likes.  I also set Frames/Period at about 512 and that seems to be as low as I can get it before I start getting "choppy/clippy" audio.  It's very low latency, 8 msec, not even noticeable when recording.

Overall this unit seems to work just as good or better with this borrowed crummy Compaq Presario laptop running Ubuntu 11.10 and Ubuntu Studio as it does on my Macbook running Tiger and Logic Pro 7.  Looking forward to making the plunge into my own Ubuntu recording system.:popcorn:

---

