---
title: "Problem with lm sensors"
date: 2009-09-13
forum: Installation &amp; Upgrades
---

### Post by trexgrec on 2009-09-13
Hello

I am trying to install lm sensors in ubuntu 8.10 64b and I have the following problems:

a) I installed sensors applet, but the only sensor it displays (and is capable of enabling) is the "hddtemp". How can I install the rest?

b) I read some posts and I tried to run sensors-detect, but the only result I got is the following:

################################
I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
# no driver for AMD K10 thermal sensors yet
#----cut here----

#################################

So now, what can I do, how do I proceed?

Thanks in advance

---

### Post by earthpigg on 2009-09-13
> # no driver for AMD K10 thermal sensors yet

that says it all -- but recall that you are using ubuntu 8.10.... which is using the most up-to-date packages as of about 2-3 months before the _10_th month of 200_8_.

i recently had a similar problem with a new intel i7 motherboard/processor. lm-sensors that comes with 9.04 does not work well with that CPU/mobo... but with the 9.10 alpha, it works fine.

your options:

-continue without lm-sensors working well.
-try installing/configuring/testing lm-sensors from a 9.04 LiveCD. if it works, go ahead and upgrade.
-go to the lm-sensors official website and look for an up to date version to install, preferably a .deb.

---

### Post by trexgrec on 2009-11-01
A bit late, but thanks a lot for your quick reply! I will just wait for the 9.10 version

---

