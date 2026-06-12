---
title: "Microphone Volume Auto-Adjusting Out of Range..."
date: 2010-10-19
forum: Hardware
---

### Post by chazdraves on 2010-10-19
Well, little bit of a problem. I've used Ubuntu on-and-off for a few years now and never quite stuck with it because of "little problems" like this.

Presently, I use my laptop for a lot of voice calls now that Google has made U.S. calls free via their Google Talk service and so the functionality of my microphone has become important to me. When I first installed, the Mic was muted for some reason but that was an easy fix. Using the level indicator, I set the volume where I felt was most acceptable and closed out. Now, a few days later, I've had a few phone calls to test it out and people complain of my audio cutting out - almost as if it was clipping. Thinking on it, I checked the level indicator and came to suspect that, indeed, my microphone might be clipping as a result of the auto-adjusting feature that seems to be at play.

What I see is that I have the microphone set where I want it but as I'm talking Ubuntu is constantly re-adjusting the level to where it believes would be best. Unfortunately, during pauses on my end while the other person is speaking, Ubuntu sees fit to crank the volume up since it isn't receiving any input and (apparently) feels it should be. Then, inevitably, when I go to speak again, the volume is far too high and most of my words are cut off until the level is automatically adjusted back down.

Now, a simple fix would be the (usually standard) ability to lock the level in one place, but I don't see any option for that? Am I missing something or is it simply not there?

Thanks for your time!
- Chaz

EDIT/UPDATE:

I did some more searching and found another gent who had this problem but specifically used Skype. In his case, the problem was with a setting in Skype that allows Skype to automatically adjust volume levels. Now, I do have Skype but it is not running by default and was not running during these calls. I don't see a similar option in my Google settings.

---

### Post by chazdraves on 2010-10-20
[http://www.google.com/support/forum/p/gmail/thread?tid=389e3b70988a1711&hl=en](http://www.google.com/support/forum/p/gmail/thread?tid=389e3b70988a1711&hl=en)

The issue is with Google Talk and not with Ubuntu as I discovered last night during a Skype conversation.

As with one of the other responders in that thread, there was no "options" file in my /home/[USERNAME]/.config/google-googletalkplugin folder but all I had to do was create a file called "options" with no file extension and insert that line of code and now it works like a charm.

Hopefully this can help someone else as well.
- Chaz

---

### Post by ToSsMaStR on 2010-12-29
Ran into the same problem, but I am using Skype. The input volume was being constantly adjusted.

It was Skype that was adjusting the settings automatically.


In Skype go:
  Options(Ctrl + O)
  Sound Devices
  Untick allow Skype to automatically adjust my mixer levels

Hope that helps anyone else using skype!

---

