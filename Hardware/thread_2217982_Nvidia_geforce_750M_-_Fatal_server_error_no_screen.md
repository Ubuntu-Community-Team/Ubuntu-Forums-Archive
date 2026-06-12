---
title: "Nvidia geforce 750M - Fatal server error: no screens found"
date: 2014-04-19
forum: Hardware
---

### Post by The-Master on 2014-04-19
Hi.

You'll have to excuse the username. I made the account when I was quite young.

I've had ubuntu 12.04 installed since July last year. I had a problem at the time getting my graphics card to work correctly but eventually got it working by using the nvidia 331 driver and bumblebee. I tend to put my computer to sleep rather than turning it off so when I needed windows for something I turned it off and have been unable to get it back on since. So the problem could have been an update 2 or 3 weeks ago up until yesterday.

It boots up into tty1. startx and failsafex don't work and exit with:

Fatal server error:
no screens found.

I have pasted the full error log here:
[http://paste.ubuntu.com/7282390/]("http://paste.ubuntu.com/7282390/")

Since I had issues with the nvidia graphics I've tried removing all nvidia drivers and deleting the xorg.conf but it still doesn't load. I've tried re-installing both the current versions and the 331 driver and using only the nouveau drivers but I've never managed to get beyond the command line.

What options do I have? Is there anything else I can try? What would the best way to backup be if I need to start again?

Thanks in advance.

Edit: I gave up trying to fix this problem and just installed ubuntu 14.04 and kept all my settings.

---

