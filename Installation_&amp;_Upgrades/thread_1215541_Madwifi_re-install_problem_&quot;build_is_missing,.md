---
title: "Madwifi re-install problem: &quot;build is missing, please set KERNELPATH&quot;"
date: 2009-07-17
forum: Installation &amp; Upgrades
---

### Post by bdev on 2009-07-17
For some reason my WIFI on my AcerAspireOne stopped working.

So I decided to re-install **Madwifi **driver from source (which I had installed successfully 5 months ago after I installed Ubuntu on this laptop).

But I have a problem by getting this error, after I try [FONT=Courier New]"$make clean"[/FONT] in the package directory:

[FONT=Courier New]"build is missing, please set KERNELPATH"[/FONT]

so i re-installed the following packages to make sure i had all the right prelim stuff:
[B]linux-headers-2.6.27-7
build-essential_11.4[/B]

But still no luck--I get the same error [FONT=Courier New]"build is missing, please set KERNELPATH"[/FONT]

So I am confused about what to try next?

In case it helps: I am running *Ubuntu 8.10 Intrepid Ibex on a Acer Aspire One* subcompact notebook.

Thanks Much

---

### Post by csabo2 on 2009-07-17
Found this:


[http://www.linuxforums.org/forum/wireless-internet/82489-dwl-g520-madwifi-troubles.html](http://www.linuxforums.org/forum/wireless-internet/82489-dwl-g520-madwifi-troubles.html)

---

### Post by bdev on 2009-07-19
I looked over the info at this URL in the last reply but could not find anything---sorry perhaps I missed something?

It seems like the solution in the URL link above is some sort of script to build the driver for Linux Fedora, not Linux Ubuntu, what I have.

Again, I am confused as to why after installing linux-headers and build-essential after I do this:

[FONT=Courier New]madwifi-hal-0.10.5.6-r4031-20090529$make
[/FONT]
I am getting this:

[FONT=Courier New]"...build is missing, please set KERNELPATH. Stop"[/FONT]

And I am confused as to how to [FONT=Courier New]"set KERNELPATH"[/FONT].

Thanks again.

---

### Post by vexeddemon on 2011-11-15
> **bdev said:**
> I looked over the info at this URL in the last reply but could not find anything---sorry perhaps I missed something?

It seems like the solution in the URL link above is some sort of script to build the driver for Linux Fedora, not Linux Ubuntu, what I have.

Again, I am confused as to why after installing linux-headers and build-essential after I do this:

[FONT=Courier New]madwifi-hal-0.10.5.6-r4031-20090529$make
[/FONT]
I am getting this:

[FONT=Courier New]"...build is missing, please set KERNELPATH. Stop"[/FONT]

And I am confused as to how to [FONT=Courier New]"set KERNELPATH"[/FONT].

Thanks again.

Not sure if you figured it out, but you can set KERNELPATH within Makefile.inc, mine on BackTrack5R1 which is Ubuntu 10.4 was /usr/src/linux-headers-`($uname -r)`

After that was set properly it compiled with no problems. Hope this helps. :D

---

