---
title: "Feisty boot - CD drive accesses"
date: 2007-05-27
forum: Hardware &amp; Laptops
---

### Post by msemtd on 2007-05-27
I'm loving Feisty on my Medion laptop but I have a question about the boot process: my CD makes a low beep-beep noise when first accessed (entirely by design I must add) which usually happens when the CD/DVD is changed and I assume is some sort of reset occurring. During Feisty boot this happens 5 times which I find mildly annoying. I didn't notice it at all with Edgy or Dapper boot so I'm guessing it used to happen once or maybe twice.
I'm assuming that either some module is repeatedly resetting the drive or it's different modules doing their own thing. Nothing stands out in dmesg. 
Any ideas what can be one about this? 
BTW: during XP Pro MCE boot I get the beep once.

---

### Post by msemtd on 2007-05-31
OK, when booting to recovery mode it seems to start beeping at the same time that LVM reports that it is starting up. I read up on lvm.conf, looks fine, ran vgscan, all fine, still bbeps although /dev/cdrom is set to "rejected" and not listed in the cache. I may be barking up entirely the wrong tree!

---

### Post by msemtd on 2007-06-05
hmmm, just a thought: do I need to have lvm installed?

---

### Post by msemtd on 2007-07-11
Bump!
I don't know the package under which I should file this as a bug - anybody? Hello? :(

---

### Post by msemtd on 2007-07-17
Hmmm, I removed lvm2 and lvm-common and it still makes 5 noisy CD accesses each boot :(

---

### Post by msemtd on 2007-07-24
OK, solved: the offender was evms - I don't see any relevant bugs reported against the evms package though :confused:

[https://bugs.launchpad.net/ubuntu/+source/evms/](https://bugs.launchpad.net/ubuntu/+source/evms/)

or in the evms faq...

[http://evms.sourceforge.net/faq.html](http://evms.sourceforge.net/faq.html)

I'm wondering if this inclusion by default of enterprise baggage into a seemingly desktop-oriented distro is a symptom of what drove Con Kolivas to abandon kernel development ([http://apcmag.com/6735/interview_con_kolivas](http://apcmag.com/6735/interview_con_kolivas))

Or... am I messing up my machine by removing lvm2 and evms? (yeah, I know I'm talking to myself :) ) -- they don't seem to be needed but I guess I'll find out eventually if anything has broke!

---

