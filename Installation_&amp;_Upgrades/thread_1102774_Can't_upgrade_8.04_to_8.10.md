---
title: "Can't upgrade 8.04 to 8.10"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by psykojello on 2009-03-22
I'm sorry if this has been asked before, but I tried looking through the threads and didn't see anything similar to the problem I was having.

I'm new to ubuntu and unix, so I need some help with this. I recently bought a Dell mini 12 laptop which comes with ubuntu 8.04 pre-installed. The laptop seemed to be very sluggish - not just the start up time, but even time taken to open applications, stream videos and even type messages (there was often some lag).

What I usually do with dell machines (with Windows) is to format them and do a fresh installation of my copy of Windows so I can install only what I need. Since I don't know my way around ubuntu too well I figured I would try doing the same and install 8.10.

I put in my install disc (external drive) and restarted my computer ; booted with the disc ; chose to "Install Ubuntu". 

When the install process was complete, it left me at a command prompt and I wasn't sure what to do, so I restarted the computer.

When I started up again, I was back in 8.04, not in 8.10. 

I tried doing the ubuntu upgrade (following instructions here: [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading) ), but it just tells me that there are no new updates.

How do I run 8.10 on my laptop? Can I clean out my existing install first? Do I need to?

---

### Post by psykojello on 2009-03-22
Also, has it installed 8.10 somewhere on my computer, but I just don't know of it?

---

### Post by snowpine on 2009-03-22
Hi there, I have a Dell Mini 9, not Mini 12, but I think my advice holds true:

The version of Ubuntu 8.04 that comes pre installed is a special Dell "remix." It uses a special lpia kernel (not i386) and is optimized for the Dell Mini. There is no 8.10 version of this Dell Ubuntu. However, 8.04 is a "long term support" release and will be supported through April 2011.

If you want to install "regular" 8.10, it will run fine on the Dell Mini with one or two minor "tweaks". There's a good how to at this site: [http://www.ubuntumini.com/](http://www.ubuntumini.com/) and you might find this thread useful: [http://ubuntuforums.org/showthread.php?t=1014534&highlight=moblin](http://ubuntuforums.org/showthread.php?t=1014534&highlight=moblin)

Personally, I am sticking with the Dell 8.04 lpia version for now. Compared to i386 8.10, it has a faster boot time and longer battery life due to the lpia kernel. I hear good things about 9.04 (coming out next month), but i386 8.10 is not an improvement over lpia 8.04 for the Dell Mini, in my opinion. The downside to the lpia version is that your choice of applications is limited.

---

