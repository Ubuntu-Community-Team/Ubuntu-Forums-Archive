---
title: "GStreamer plugins missing after upgrade"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by mkbecker on 2009-08-06
After downloading latest upgrades on or about August 1, 2009 my sound has disappeared.  When I click on volume control I get a message that "GStreamer plugins are missing."  What can I do?

---

### Post by jerrrys on 2009-08-06
reinstall **ubuntu restricted extras** in synaptic

system>administration>synaptic package manager

and thats updates, not upgrades

---

### Post by mkbecker on 2009-08-07
I tried Jerrys'fix but ran into further trouble.  I got a message to maually run 'dpkg --configure -a".  When I did that it hung up.  Finally, I booted up in recovery mode which then ran dpkg etc but in turn hung up at

'ëxception Emask 0x0 SAct 0x0 action 0x2 frozen
cmd c8/00:60:50:7C:78/00:00:00:00:00/e8 tag 0 dma 49152 in

Status {DRDY}
Revalidation failed (errno=-2)'.

If I then reboot normally I am able to run synaptic package manager and start reinstall of ubuntu restricted extras.  But that in turn hangs up at the point of configuration.

I am running Hardy Heron 8.04.  However, my Firefox is now inoperable because I foolishly tried to run this morning's update.
I am sending this message, heresy of heresies, using Windows.

---

### Post by jerrrys on 2009-08-07
Hi mkbecker

this is where I been the past hour

[http://www.google.com/search?q=%C3%ABxception+Emask+0x0+SAct+0x0+action+0x2+frozen&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=%C3%ABxception+Emask+0x0+SAct+0x0+action+0x2+frozen&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

[http://www.google.com/search?q=Revalidation+failed+(errno%3D-2)&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=Revalidation+failed+(errno%3D-2)&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

so far there's only been ideas and suggestions, ZERO solutions.

hdd failure, kernel, smart tools so far seem to be the top suggestions.  can you relate to any of this?  after dinner Ill continue researching this...

---

### Post by mkbecker on 2009-08-07
It is now 6 PM PST.  I'll give a shot.

---

### Post by jerrrys on 2009-08-07
1

---

### Post by jerrrys on 2009-08-07
http://www.google.com/search?q=Status+{DRDY}&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a

http://www.google.com/search?q=Status+{DRDY}+Revalidation+failed+(errno%3D-2)+%C3%ABxception+Emask+0x0+SAct+0x0+action+0x2+frozen&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a

can't seem to post a link at the moment, hope it works this time

anyhow further reading took me to the above and still no real answer.  so at this point i thing i would try rolling back the kernel just to see.  sorry i can't be of more help...

---

### Post by mkbecker on 2009-08-08
THanks for trying,  I will take my machine to a geek shop where they can offload all my data, pictures, etc, and reinstall everything.

---

### Post by mkbecker on 2009-08-25
I have finally solved my problem by replacing my defective hard drive and installing on the new drive Ubuntu 9.04, Jaunty Jackalope.

The moral of this story is twofold.  1 Don't ignore failed updates, upgrades and other downloads.  In time they catch up with you and may be indicative of more serious problems.  2 Remember that it could be a hardware not software problem.

---

