---
title: "I trusted automatic updates now my desktop is broken"
date: 2009-07-19
forum: Installation &amp; Upgrades
---

### Post by davemays on 2009-07-19
So after a few years, of installing the updates when requested, I grew a trust of the Ubuntu powers that be and about a month ago, just told it to install whatever it needed. Well now I am jacked up.

I am Jaunty 9.04, Nivdia card. Working perfect yesterday, This morning the X screen pauses then whatever I click on the screen seems to queue, then 5-6 seconds later it does everything, then pauses and the loop repeats. When in text mode (ctrl-alt-f1) there is no pauses, and top shows no load. Back to X and is freezes then runs then freezes. I uninstalled compiz, and stopped desktop effects as long ago had an issue with that, no avail. 

No errors in debug, dmesg, syslog, or messages. 

Any idea? is there a way to roll back updates? or find the ones that might have goofed it?

Please help.

Thanks
Dave

---

### Post by davemays on 2009-07-19
So it seems that it updated all the pulseaudio garbage yesterday. Is it possible to go to an older version from the command line?

---

### Post by Whiffle on 2009-07-19
You can look through 

/var/log/apt/term.log 

and it should tell you what was done.  As far as I know, the apt system has no automatic rollback functionality (yet).

---

### Post by davemays on 2009-07-20
So I renamed /usr/bin/pulseaudio to /usr/bin/pulsecrap, and now it is working, but I have no sound. I try to downgrade via Synaptic the previous version, and it tells me I am holding on to broken packages and wont let me do it. Anyone know how to force it to downgrade?

---

### Post by iponeverything on 2009-07-20
You can install the previous version by going to:

 /var/cache/apt/archives/

the Previous version will be in there.

To do the downgrade:

dpkg -i <package name>

Also a better way of seeing what was upgraded and when would be to look in:

/root/.synaptic/log

---

### Post by davemays on 2009-07-20
okay, fixed it. Got the files to downgrade, then locked the version. Now to open a bug report with the pulseaudio folks....

---

