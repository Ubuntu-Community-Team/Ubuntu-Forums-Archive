---
title: "Thinkpad T410 Owners Thread"
date: 2010-03-18
forum: Hardware
---

### Post by s_m_c on 2010-03-18
There doesn't seem to be much information about the T410 on these forums yet.  I'll post my status with Karma.

I've got the 5100 WiFi card and integrated graphics.

I'm running Karma with the 2.6.34-020634rc1-generic #020634rc1 SMP x86_64 kernel.  With each release of the kernel things seem to be getting a bit more functional.

Video: Latest Intel Driver compiled from source and installed.  Works at native resolution and successfully driving 2 external monitors through dock at 1920x1280 & 1280x1024

Sound: Works through speakers and headphones but is flaky (described below)

WiFi: Works perfectly

Bluetooth: Haven't tested extensively, but successfully paired a headset and tested with a Skype call.

Other: Volume, Brightness, Mute, ThinkLight, and middle button scrolling all work.

Here is the problem that's been bugging me lately:

When I start up my sound works only through the headphone jack and USB works just fine.
After suspending/resuming the sound works through the speakers but USB is broken.
Suspending/resuming a second time causes the computer to reboot during the resume process.

Anybody else seeing similar issues?

---

### Post by KB1JWQ on 2010-03-24
I have the t510.  Waking from standby is broken.  Wireless (6250) is broken; Intel will be providing firmware "sooner rather than later."

Running Lucid here; things seem to be working well.

---

### Post by zbeekman on 2010-04-08
I'm helping my friend with his T410 and we are having problems with the wireless.  Does anybody have any ideas to fix this?

---

### Post by tylerwylie on 2010-04-12
Lenovo T410 2516CTO here, Intel 6300 wireless works with backported modules, nvidia drivers work too.  Brightness / suspend/resume issues however.

---

### Post by KB1JWQ on 2010-04-12
How did you end up backporting wireless support for the 6300?  If there's a chance it'll work with the 6250 I'm all for trying it.

---

### Post by Gergie on 2010-05-19
The problem of reboot after 2nd resume is fixed by a BIOS update:
[http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-74268](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-74268)

See also:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/532374](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/532374)

The "no USB after resume" problem seems to be fixed in an upcoming kernel patch.

See:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/566149](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/566149)

Greetings,
Jürgen

---

### Post by nomnex on 2010-05-25
> **Gergie said:**
> The problem of reboot after 2nd resume is fixed by a BIOS update:
[http://www-307.ibm.com/pc/support/site.wss]("http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-74268")
[/document.do?lndocid=MIGR-74268]("http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-74268")

How do you update the BIOS when you are in simple boot Ubuntu only?

---

### Post by Gergie on 2010-05-29
> **nomnex said:**
> How do you update the BIOS when you are in simple boot Ubuntu only?

Lenovo provides the update as (bootable) CD image. Simply create the CD from the ISO image and reboot. BIOS updates are critical. Follow the instructions as from

[http://www-307.ibm.com/pc/support/site.wss/MIGR-74269.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-74269.html)

---

### Post by nomnex on 2010-05-29
> **Gergie said:**
> Lenovo provides the update as (bootable) CD image.

Convenient, thanks for the info.

Edit: I had missed the Lenovo link in your first post (#6)

---

### Post by ehabh on 2010-08-15
I had sound on my t410 and now i do not have any sound. Does anyone have this issue?

---

### Post by Waaib on 2010-08-20
I just got given an new PC at work. It's a T410 with 8gb RAM. 

I considering installing Ubuntu 64bit OS primarily because I think it will be fast. Am I being silly?

---

