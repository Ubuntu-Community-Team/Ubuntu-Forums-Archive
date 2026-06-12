---
title: "Sony VGN-FX490 and suspend/hibernate wakeup"
date: 2009-10-08
forum: Hardware
---

### Post by n2bnt2 on 2009-10-08
Hi,  I have 9.04 on new Sony Vaio laptop. Trying to get everything (most things :^) working. From reading posts, I have the shutdown and restart working (was getting CIFS VFS: Server not responding errors). I did the fix to add umountnfs.sh to the /etc/gdm/PostSession/Default and it seems to work fine. I had a perm mounted Samba share at bootup in my fstab.

Now, I want to get suspend (at least) and hibernate working. I did the suggestion to shut down eth0 and wlan0 in the stop action for alsa-utils. I changed POST_VIDEO to false in /etc/default/acpi-support. I tried the beryl resume and suspend scripts (don't know what these do, and that scares me :^).

With all those settings, when I suspend, it goes to a blank screen with a blinking underline, and then turns off. The power led glows on and off. When I hit enter, it comes up to a display with a garbled colored bar across a few inches of the top (like a top panel), the right most 3" of the bottom panel showing trash and windows, a black screen and a cursor that moves. I cannot click on anything. If I type in my password, or try anything, no response. Have to power cycle. 

On a previous try, which was without the POST_VIDEO change, I got a blank screen with a white box that had a text field (like the password screen). No buttons, no text, and I cannot type into the text field. I do have screensaver set to use password.

Hibernate was the same, showing the "Waking up" message initially and then comes to this mangled desktop.

I'm new to Linux, at least beyond using the command line at work (not playing around with installing things). Can someone give me pointers on how to approach diagnosing this issue? I'm not sure of the steps to try :^(

Thanks in advance,

PCM

---

### Post by n2bnt2 on 2009-10-09
I removed the Samba share from fstab, just to eliminate anything with CIFS (because I had some issues with that and shutdown/restart), but I still get the same result.

I undid the two changes I had made in my previous post, and tried suspend. When I bring it out of suspend, I get a blank screen with a cursor that I can move, but nothing else. No keys work, no panels, nothing.

Any suggestions on how I should troubleshoot this issue (or anyone with a similar model that worked around this issue)?

Thanks.

PCM

---

### Post by n2bnt2 on 2009-10-11
Anyone have any suggestions? I'd really like to get suspend to work on this laptop.

Thanks.

PCM

---

