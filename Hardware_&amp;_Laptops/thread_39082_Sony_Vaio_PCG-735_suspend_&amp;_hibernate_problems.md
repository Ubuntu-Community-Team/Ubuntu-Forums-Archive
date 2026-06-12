---
title: "Sony Vaio PCG-735 suspend &amp; hibernate problems"
date: 2005-06-03
forum: Hardware &amp; Laptops
---

### Post by mjgumbley on 2005-06-03
All,
Have recently replaced Red Hat 7.3 with a "server" installation of Hoary. (System is low spec, low RAM).
The suspend and hibernate keys no longer do anything, except beep.

Where do I start to diagnose this?

Regards,
Matt

---

### Post by mjgumbley on 2005-06-06
To reply to my own message... installed acpi, and laptop-mode.
tail -f /var/log/acpid
showed messages when the power and suspend buttons were pressed - but they didn't trigger any actual activity.

Started looking at /etc/acpi/events - the power button should effect a shutdown, but doesn't seem to do anything.

When pressing the power button, I see:
received event button/sleep SLPB 00000080 00000001
completed event button/sleep SLPB 00000080 00000001
When pressing the suspend button, I see 
received event button/sleep SLPB 00000080 00000002
completed event button/sleep SLPB 00000080 00000002
When pressing this hibernate button, I get a beep, that's all.

Why is acpid seeing the power button as a sleep button?
Why is the hibernate button not being detected?

lsmod shows that sony_acpi is loaded.

Have seen elsewhere (on a Debian forum, IICR) that there's a separate hibernate package. Will investigate....

Also,
[http://www.techfak.uni-bielefeld.de/%7Eicschlei/vaio/](http://www.techfak.uni-bielefeld.de/%7Eicschlei/vaio/)
suggests that you need a separate hibernate storage partition, which I haven't got. Strangely, this wasn't present either when RedHat was on the laptop, although I think RH uses apmd.


Other oddities about this laptop: 
1) The NVRAM battery is dead. If it's in the machine, it doesn't boot at all, so I removed it, and am searching for a replacement. If you reconnect it while the laptop's on, it's as if there's some dead short insuide, and everything powers off instantly.

2) Not sure if this is related to the lack of NVRAM battery or not, but the laptop refuses to do anything when the power is turned on, when there's no AC Adaptor inserted and connected to the mains. If I plug it in, it'll turn on fine. It isn't a problem with the battery not holding charge, as if I boot with the adaptor in, then disconnect it, it'll stay up for a reasonable time.

Investigation continues.... any help gratefully accepted!

---

### Post by mjgumbley on 2005-06-08
Apparently you can use APM on Ubuntu...

[http://ubuntuforums.org/archive/index.php/t-47.html](http://ubuntuforums.org/archive/index.php/t-47.html)

I didn't know that.... pity!

I've just reinstalled RedHat 7.3, after creating a hibernation partition at the end of the disk, a little larger than the maximum amount of RAM I'm intending to upgrade to (128MB), of type 0xA0.

Suspend and hibernate work perfectly (so far as I've been able to tell).

So if I reinstall Ubuntu, I'll give it a go...

---

