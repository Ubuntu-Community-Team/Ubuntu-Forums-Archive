---
title: "Notification Area Woes"
date: 2008-10-27
forum: General Help
---

### Post by Xnyper on 2008-10-27
Hey everyone, thanks in advance for your help.  I'm doing some long-overdue customization, and I've hit a snag.  

I have two monitors hooked up to my system.  They're configured, using nvidia drivers, as two separate x-screens.  Xinerama and Twinview aren't really good options for me, so I'm pretty set on keeping it that way.  Ubuntu sees the monitor on the left as my main monitor, which is what I want.

When I say "main monitor" I mean that that's the one that displays the login prompt.  Also, I added a command to my gnome-sessions-preferences to start up a gnome-terminal for me, and it starts it up over there.  Not sure whether this makes it 1, and the other is 2, or this makes it 0 and the other is 1.  Hereafter I am just going to refer to them as lefty and righty.

After playing around with it I have found the following:

If I have each monitor set up with its own notification area Then
[LIST]
[*]The network-manager applet loads in lefty, righty's notification area stays blank
[*]Applications (like pidgin) opened in lefty put their icons in lefty's tray
[*]Applications opened in righty dont put their icons anywhere
[/LIST]

If I have no notification area in Lefty, but I do have one in Righty
[LIST]
[*]The network-manager applet loads in its own little window in lefty
[*]No applications (like pidgin) put their icons anywhere
[/LIST]

Ultimately, I want to have the notification area on my panel in righty, and have it work for all notification icons system-wide.  
At this point I'd just be happy to have a notification area somewhere, that will work for applications opened on righty.

I have been rooting around in gconf-editor looking for some key I can change that will set the notification area to focus on righty, instead of lefty, but I can't find anything.

---

