---
title: "Can't get remote desktop to work in 9.10"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by BossaKungen on 2009-11-02
I did a clean install of 9.10 and enabled remote desktop (I've used this feature on 8.10 and 9.04 before), I can connect from other computers but some times I only see the background image and other times I see the proper screen but it's never updated even if I request a manual refresh.
If I look at the 9.10 computer when the connection is made the mouse moves and the mouse-clicks works, this is not visible on the other end however.
Any ideas on what is going on?

In the "Remote Desktop Preferences" I've checked:
-Allow other users to view your desktop
-Allow other users to control your dektop
-Require the user to enter this password ***
-Configure network automatically to accept connections
-Only display an icon when there is someone connected.

---

### Post by sollyshah on 2009-11-04
Hello

I am having similar issues, i used to use my ubuntu desktop to remote display apps and x installers for oracle and others from our solaris servers, i used to previously uncheck the "Deny X TCP...." on ubuntu 9.04 and would be  able to sudo xhost + then export the display on our solaris servers and remote display the x application i would have like to run on my ubuntu desktop.

Similarly like my fellow poster i have all the remote desktop options enabled but i suspect that these may be only for vnc / rdp etc. Is there anyway i can allow X sessions to be displayed on mu unbuntu desktop enabled again?

Please help, i also done a clean install of ubuntu 9.10.

Thanks

---

### Post by BossaKungen on 2009-11-05
To clarify my post: I never get a normal VNC connection, I said 'some times', but it's always one of the scenarios above.

---

### Post by BossaKungen on 2009-11-07
It turned out to be a broken HD, I got SMART error warnings for the OS-disk, so I bought a new drive and re-installed 9.10 and now it works. :)

---

### Post by BossaKungen on 2009-11-08
After I wrote the last message and tried it a few more times it now behaves in the same way as I wrote in the first post, what is going on?

---

### Post by AnarchyLinux on 2009-11-08
hi [BossaKungen]("http://ubuntuforums.org/member.php?u=941172") Are u behing a router?
did you install the open ssh software?

Regarding the ssh protocol you can put here the result of: [COLOR=Red]**dpkg -l | fgrep ssh**[/COLOR]?
this will say either u have it installed or not....this should be the first step to take.

After this we must analise if your Firewall is blocking people from conecting to you...the fact YOU allow ubuntu to receive "visits" doesnt mean you firewall does the same :)):P

---

### Post by BossaKungen on 2009-11-09
I am behind a router and port 5900 is open as I was using this in earlier Ubuntu versions (8.10 and 9.04). 
I currently don't have openSSH installed, I tried it and got it to work, I could get a terminal window and I also used NXserver through the SSH tunnel.
The problem is that I want to see the current desktop, when using NXclient I got some of the options to work (Unix/Gnome) but that gives me a new log-in so I coulnd't start firefox because it was already started. 
Using the VNC option in NX gives me the same not-updating problem as the other VNC clients.

---

### Post by yankee75 on 2009-11-10
Hello,

I have the exact same problem with Remote Desktop on Ubuntu 9.10 64bit. Is somebody has found a solution for that?

Thank you,
Yanick

---

### Post by sse on 2009-11-10
exactly same problem here, as the original poster described.

karmic amd64 host and guest.

---

### Post by santhony on 2009-11-10
same here too.. this has happend to me on both an upgrade from 9.04 and also a fresh install with karmic amd64..  

If i goto the host, it does show control and what I've clicked on, but not on the remote side...

---

### Post by mr_steve on 2009-11-10
Disable desktop effects from System->Preferences->Appearence, on the Visual Effects tab.

It's a known issue, although the bug number escapes me at the moment.

---

### Post by BossaKungen on 2009-11-17
Sweet it works! :D

I had it disabled in the old version, but I didn't think of that.

Thanks!

---

