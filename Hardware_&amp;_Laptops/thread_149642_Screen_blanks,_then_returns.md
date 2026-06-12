---
title: "Screen blanks, then returns"
date: 2006-03-24
forum: Hardware &amp; Laptops
---

### Post by Dragonbite on 2006-03-24
This is something that I don't know if it's video drivers, bad configuration, resoution or even a hardware problem and I don't know how to figure this out.

[CENTER]:D [......... Background .........][/CENTER]

The system is a **[COLOR="Blue"]Dell Dimension 4100 [/COLOR]**(P3 1GHz) I got when somebody was throwing it out (*something about it being too slow?!* :D ).  The video card in it is an **[COLOR="Blue"]S3 Trio 3D/2x[/COLOR]**. I am running 5.10 on it with the 686 kernel and have it hooked up to a 17" Sony CRT monitor.

[CENTER][.......... Situation .........]](*,) [/CENTER]

There are 4 parts to this situation which may or may not be related

[LIST=1]
[*]Every so often the screen will blank out into a brown background with few vertical shapes a different shade of brown. It returns after about or just under 1 second of being blanked.  If my resoultion is higher (85 MHz) it happens more frequently than if I lower it (60MHz).  Slowly, if I am using the system for a few hours, it happens sooner and sooner as time goes on, but I don't remember it happening when I leave it in the login screen.
 .
[*]If I'm on for a long time, usually with a lot of processes going on (or in other words a couple Firefox browsers with a number of tabs open on each) it has even blanked out as described above and never recovers (after leaving it for about an hour that way) and I cannot switch (Cntrl + Alt + F2) over to a console.
 .
[*]I've gone through [Restricted Formats ]("https://wiki.ubuntu.com/RestrictedFormats") and it does run some of the formats listed there, except that it has a flicker on the right-half of the video ( .mpg, .avi and .wmv) and ghost-images in that one half if I expand the player / video larger than the default size. I guess the best way to describe it is it as if random "strips" of the video are being moved around somewhere up-or-down the right half of the video.
 .
[*]Sometimes a movie will play, sometimes it pops open Totem and it looks like once the video is loaded it crashes Totem.
[/LIST]

[CENTER]:-k [........... Summary ..........][/CENTER]

Like I said, I don't know if it is the card, the installation, the drivers or what (could be PEBKAC [SIZE="1"](Problem Exists Between Keyboard And Chair[/SIZE]even).

A solution would be wonderful, but I'm even just looking for "how do I troubleshoot this?":confused:   and where to start!

If it is a hardware (video-card) issue then I just need to know that and look at getting a new card (may look at doing that anyway, but if it isn't the card then I'm stuck with the same problem again).

Thank you for your suggestions, hints and ideas!

~Drew

---

### Post by Dragonbite on 2006-03-27
Just a quick update, the issue with the screen blanking may be related to Gnome specifically.  

When I switched over to use Xfce instead of Gnome I haven't see the screen-blank yet.  The video still is messed up but I feel better knowing the system won't blank/freeze on me.

---

### Post by Dragonbite on 2006-04-28
Ok, another update just in case anybody runs across this.  I think I've fixed the screen-blanking issue though video playback is still not right.

At the same time I was having these issues I was also having problems with my USB Pen Drive, and I thought they were unrelated.

A couple nights ago I got so frustrated because I needed to copy something over to take with me to work because sending a 5MB file over dial-up internet is dreadfully slow and timed-out!

](*,) 

The system has 2 USB ports, one is pluged into the monitor which also sports a 4 port hub.  The Printer and Scanner are on the monitor (hub) and work.

I moved the USB drive from port to port trying to get any reaction (even the built-in light!) and eventually unplugged the monitor(hub) and put the USB drive there.

VIOLA! :D 

It came up completely as it should have (guess I DID have the right settings in /etc/fstab), popping up on the desktop even!

I moved the hub to the other port in the back of the case and tested it to make sure it works, which it does.

I was so happy to get that working and after using the system for a while I noticed it wasn't flickering anymore! 

So I  think there was some sort-of conflict going on with the USB which I have no idea how to find out but at least it seems to no longer be an issue.

---

