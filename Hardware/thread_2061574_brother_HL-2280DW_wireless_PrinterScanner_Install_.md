---
title: "brother HL-2280DW wireless Printer/Scanner Install on 12.04 LTS"
date: 2012-09-22
forum: Hardware
---

### Post by Imagery on 2012-09-22
Hi everyone,

I just got a Brother HL-2280DW laser printer and scanner and I luckily had no issues installing the printer with Ubuntu and using the 32bit .deb packages from Brother's website.

The only issue I have no is getting the scanner to work.

I did download the following .deb packages and installed them:

Brscan4.deb 32bit  and  scan-key-tool.deb  32bit


Also this is being used over my wireless connection if it makes a diffrence. But Simple scan cannot see a scanner connected.

I went ahead and added the following lines to my \lib\udev\rules.d\40-libsanerules file:


# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
 
Saved then rebooted.  Still no luck.

I've attached my file view review.  Anyone have any idea how I can get this working with Ubuntu 12.04 32bit?

---

### Post by Imagery on 2012-09-23
^bump^

---

### Post by pdc on 2012-09-24
SimpleScan uses "sane" as its backend

if you look at the sane site, 

[http://www.sane-project.org/sane-mfgs.html#Z-BROTHER](http://www.sane-project.org/sane-mfgs.html#Z-BROTHER)

you will see the Brother devices are not supported;

Canon provides a programme called ScanGear for its MF devices; one uses that;

.........for Brother; ........brscan is the equivalent;

for ScanGear in Canon; one needs to create a launcher to easily fire it up each time...........

Brother tell you how to start it;

> **_[COLOR="Red"]How to Run Scan-key-tool automatically on PC startup[/COLOR]_**
[COLOR="Blue"]Add brscan-skey command to the startup programs list.
Example on Ubuntu8.04
1. Open "Startup Programs" (System > Preference > Sessions > Startup Programs)
2. Click "Add"
3. Type "brscan-skey" and click ok[/COLOR]

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn5.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn5.html)

I will check back later and subscribe to this thread; have you subscribed?

---

### Post by Imagery on 2012-09-24
Hi PDC,

Not only were you absolutely right, but I'm also a major tard and freaking didn't use the brscan4config file in terminal to "add" my scanner.

After doing that, it worked like a charm.

Thanks for the help and all, appreciate it. Sometimes I just forget the simple stuff as I'm so use to Ubuntu being too easy at times.

Thanks again. Making this solved.

---

### Post by pdc on 2012-09-25
great! glad all is working well; when I googled on the brscan programme, there wasn't a lot; I wondered if there were screenshots of it

---

