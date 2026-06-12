---
title: "Can you hear me?"
date: 2007-09-06
forum: Hardware &amp; Laptops
---

### Post by ranfr on 2007-09-06
This may not be the place to post it, but I don't know of any other place sad:

I've recently posted a question about the sound which doesn't work. It doesn't work not only for me but for many others. The only reply I got was from a user who experienced the same. Quick search on the unanswered posts show that another guy with the same problem got zero replies.

I know that ubuntu is open source. I also know that most of the program I use are, and that nobody has any obligation. On the other hand, if things don't work, it's not really useful, is it?

What I'd like to know is if there's anybody in the development of ubuntu who tries to solve the "volume control did not find any elements and/or devices to control" issue.

I'm quite upset and not optimistic about getting any answer but at least I give it a try. I've been using ubuntu for about a year and was quite happy so far.

Ran

---

### Post by dabl on 2007-09-06
I'll speculate that because this is a user forum, not a developers' site, your plea here won't reach the ears of any developers. :(

I'll further speculate that you didn't get any answer because no one is really sure how to tell you to fix it.

But, being a total non-expert, I'm happy to share my two cents' worth  :)

First, did you check your sound chip against the list of supported devices at the ALSA project site?  You find your chip with the command ```
lspci 
```(find it in the list of devices)

or else open "System>Administration>Hardware Information" and find it there, then look at the supported devices on the ALSA site (just google "alsa project" and look for the devices database).

Assuming it's a supported device, which it probably is, then you need to make sure you've installed the relevant ALSA packages in Synaptic.  I'm stuck at a piece of Windows junk at this moment, but from memory they are:

alsa-base
alsagui
alsa-oss (maybe) and maybe some more.

If you search this forum, I know there are many threads on the subject of getting your sound working.  "aplay" is a command that comes to mind.

Then, for reasons unknown, the "sound" icon in the upper right corner of your Ubuntu desktop (looks like a speaker) seems to come with mute on, as a default.  So, right-click the speaker, open the "alsa mixer", and start unmuting things.  Click "Edit", "Preferences", and make sure every box is checked.

I hope something in here helps you get it working!  :)

---

### Post by ranfr on 2007-09-06
Thanks a lot for your reply.

I know that this is a user forum, but where else can I post my questions and remark? I'm not a developer.

I tried what you suggested a couple of days ago. Have the right alsa version, reinstalled it more than once but I can hear nothing yet.

I've seen a new guy posting the same "audio problem". This seems to be a real issue.

Ran.

---

### Post by dabl on 2007-09-06
Which chip do you have?

---

### Post by ranfr on 2007-09-07
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

I looked at the specification for my machine and the sound card should be recognised - and the sound was working till a few days ago.

---

### Post by ranfr on 2007-09-08
The problem is apparently in the kernel:
[http://ubuntuforums.org/showthread.php?p=3316142](http://ubuntuforums.org/showthread.php?p=3316142)

However, I don't know what I should do to roll back. Simply rebooting and reloading the old kernel didn't work.

---

### Post by ugm6hr on 2007-09-09
I have no idea if this will work, but if it is the kernel, then perhaps **upgrading** rather than downgrading might work?

[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)

I used this when the Feisty kernel upgrade disabled my sound, and it reinstated it for me.

---

