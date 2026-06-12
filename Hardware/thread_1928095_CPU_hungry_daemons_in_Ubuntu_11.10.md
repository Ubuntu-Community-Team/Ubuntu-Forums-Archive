---
title: "CPU hungry daemons in Ubuntu 11.10"
date: 2012-02-19
forum: Hardware
---

### Post by xizzling on 2012-02-19
I have previously used Ubuntu 10.10 and 11.04, which never slowed my laptop. As soon as I got my new Lenovo L520, i installed the 11.10 ubuntu, thinking it will be stable.

Now, not just a few but so many processes eat my CPU usage, e.g.:
So any of the following processes keep eating my CPU for no good reason:


1. update-apt-xapi
2. chromium-browser
3. gtk-gnash
4. ubuntuone-syncd

I wonder what has severly gone wrong with this release. 

For 1, I know people have posted some ways to disable or make it to weekly update.

For 2,My old release with chromium with 14 tabs open (youtube videos etc.) would only consume less than 15% of CPU, while this one takes to 100%

Any clues to 3, or 4. ??

I am seriously thinking of downgrading my ubuntu release after all this mess !!


Regards,

---

### Post by 2F4U on 2012-02-19
Chromium is certainly not a daemon. It is a web browser you chose to install and use (since the default is Firefox).
4 is the Ubuntu One thing which I never used. The directory /etc/xdg/autostart holds the entries for autostarted application, but by default, they are hidden (don't ask me why). There is a lot of stuff in it which I never use. Here is how to make these applications visible, which then allows to disable them:

[http://www.upubuntu.com/2011/10/how-to-view-and-disable-hidden-startup.html](http://www.upubuntu.com/2011/10/how-to-view-and-disable-hidden-startup.html)

---

### Post by xizzling on 2012-02-20
Thank you for your input and correcting my terminology. Let me restate the question:

I run chromium in gnome shell, on oneiric release, with 4 GB memory and Core i5 2520M 2.5GHz processor.

I am only viewing a youtube video and chromium browser is consuming 70% of the CPU on constant basis. Do you think its normal ? Should it not be something like 20-30% max ?


Regards,

---

### Post by xizzling on 2012-02-20
And just some more update:

As I was browsing using chrome through in GNOME 3 shell, with no videos this time, the laptop got so slow that the mouse would hardly move. 

The system monitor and "top" would not show any strange process activity, except that when I minimized chrome, to see system monitor, i found it taking 90% of my CPU constantly for some very strange reason.


I have restarted my laptop once but same thing repeated. So finally i have logged on using Gnome classic (with no effects), and I am relieved to see my fast CPU :)

So what do you think is very wrong here with Gnome 3 shell?

---

### Post by xizzling on 2012-02-20
OK, on top of all some more debugging found this: (posted in a new thread)

[http://ubuntuforums.org/showthread.php?p=11705569#post11705569](http://ubuntuforums.org/showthread.php?p=11705569#post11705569)

---

