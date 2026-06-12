---
title: "Sound suddenly missing in Dapper"
date: 2006-11-12
forum: Hardware &amp; Laptops
---

### Post by Ameet on 2006-11-12
Hey, I have Dapper on my Gateway 600YGR laptop (pentium 4).  All recent upgrades marked and installed. I lost sound at some point in the past week, might have been in connection with updating the system, I am not sure. The volume applet in gnome-panel has an "X' next to it (as if sound is muted).  But when I right-click, the "mute" option on the menu is not selected.  Selecting "Open volume control" gives the following message:

```
No volume control GStreamer plugins and/or devices found
```
 			 		 	 	 
When I try to open alsamixergui, I get this:

```
alsamixer: function snd_ctl_open failed for default: No such device
```

Here is my sound card:

```

~$ lspci | grep -i audio
0000:02:03.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)

```
	 	 	 
Anyone have any ideas?  I am medium Unix-savvy so please be specific about what commands to try or what additional information to present.  Thanks!

---

### Post by Ameet on 2006-11-12
I figured out my problem! :smile:
 
I didn't have proper user authorization. So I went to System > Administration > Users and Groups, picked my account, and enabled audio access. Then I logged out and back in, and *presto!*.

---

### Post by PurplePenguin on 2006-11-14
I'm glad that you figured it out!  I had a similar problem today.  After a crash, my sound was gone.  I tried what you did, but I already had authorization.  I was desperate, so decided to go into alsamixer and just put (nearly) everything at 100%.

This worked!  I figured out that my PCM volume had somehow been put back down to 0.  Now I've got it at around 65%, so I've still got a nice range of volume to choose from with my volume control applet.

Anyway, I don't mean to hijack your thread, but just in case somebody else follows in our footsteps, hopefully, between the two of us, they'll solve their problem in minutes!

---

