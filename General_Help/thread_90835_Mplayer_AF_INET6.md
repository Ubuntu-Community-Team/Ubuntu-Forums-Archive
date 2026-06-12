---
title: "Mplayer AF_INET6"
date: 2005-11-15
forum: General Help
---

### Post by iitywygms on 2005-11-15
I have breezy installed on two machines.  One, is older (1.2 pent) and the other is my laptop, (2.8 pent)  My older machine is a standard desktop.  I have Mplayer installed on both machines.  Each machine has MediaPlayerConnectivity installed so when I click on a move in Firefox, it opens up Mplayer. Each machine is fully up to date and the same in almost every way.  The problem is that when I open a movie on my laptop, I always get this error (Couldn't resolve name for AF_INET6  Blah blah.com)  The video is also choppy on my laptop "but it always works".  My older machine works great, no errors and video is smooth.  I have super fast internet on both.  How can I get rid of the Error message on my laptop?

---

### Post by iitywygms on 2005-11-16
fixed my own problem.  Dont know why but if I switch from using Gui mplayer to just mplayer in the configuration, all is well

---

### Post by madjo on 2005-11-16
could you tell me how you did that? I can't seem to get it running either.
Am getting the same problem.

I believe it has something to do with IPv6... not sure how I can disable that in Mplayer though.

---

### Post by iitywygms on 2005-11-17
Set up you mediaplayerconnectivity to look like this.

---

### Post by a212359 on 2005-11-18
[QUOTE=iitywygms]Each machine is fully up to date and the same in almost every way.  The problem is that when I open a movie on my laptop, I always get this error (Couldn't resolve name for AF_INET6  Blah blah.com)  The video is also choppy on my laptop "but it always works".  My older machine works great, no errors and video is smooth.  I have super fast internet on both.  How can I get rid of the Error message on my laptop?[/QUOTE]

I have a laptop and am having the same problems. I changed the settings in  mediaplayerconnectivity like you said, and now the error message is gone - thanks!

But bigger problem for me is that the video is still choppy. I have a fast connection also, and this shouldn't happen...did you manage to fix the choppiness as well?

---

### Post by iitywygms on 2005-11-29
My choppy video went away after I changed the setting.  Not sure why, good luck.

---

### Post by tribaal on 2006-02-27
I might sound silly and newbish (although I probably am), but how do you open up *mediaplayerconnectivity* ?

I'd love to get rid of this annoying "Couldn't resolve name for AF_INET6 Blah blah.com" too! 

Thanks a lot!

- Trib'

---

### Post by sebasgro on 2006-09-14
I'm sorry for bringing this thread back to life, but... ;)

I just found out how to get rid of "Couldn't resolve name for AF_INET6 Blah blah.com" in the most unobtrusive way:
Append the following line to /etc/mplayer/mplayer.conf (or ~/.mplayer/config for the current user only)
> prefer-ipv4 = yes

This doesn't disable IPv6 entirely, but just uses IPv4 as the default and falls back to IPv6 if the server is IPv6 only (or if the host cannot be found).

---

### Post by Peepsalot on 2006-10-27
> **sebasgro said:**
> I'm sorry for bringing this thread back to life, but... ;)

I just found out how to get rid of "Couldn't resolve name for AF_INET6 Blah blah.com" in the most unobtrusive way:
Append the following line to /etc/mplayer/mplayer.conf (or ~/.mplayer/config for the current user only)


This doesn't disable IPv6 entirely, but just uses IPv4 as the default and falls back to IPv6 if the server is IPv6 only (or if the host cannot be found).
I read this exact same thing somewhere else, and tried editing both these files, but it does nothing.  What gives?  Did this actually work for you?

Using mplayer instead of gmplayer works ok, but then you have no controls for pausing or seeking to a different spot.  I'd like to keep those if I could.

---

