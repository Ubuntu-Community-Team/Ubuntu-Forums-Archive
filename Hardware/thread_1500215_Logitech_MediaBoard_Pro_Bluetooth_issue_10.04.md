---
title: "Logitech MediaBoard Pro Bluetooth issue 10.04"
date: 2010-06-02
forum: Hardware
---

### Post by boardinary on 2010-06-02
I am currently having problems with my logitech keyboard and bluetooth connectivity.  First, I tried to pair the keyboard with 10.04 and I was not able to get it to work using the bluetooth manager.  I then tried this fix [https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/550288/comments/10](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/550288/comments/10)  and was able to get it to pair and it worked great!

However, as soon as the keyboard goes to sleep (30 min of inactivity), I am unable to reconnect.  I must unplug and replug the bluetooth adapter and go through the process of repairing the device with the bluetooth manager.  Sometimes I even have to restart the computer.

Does anyone have any suggestions?

---

### Post by boardinary on 2010-06-03
bump  :)

---

### Post by boardinary on 2010-06-05
Should I just switch to an RF based keyboard/touchpad combo?

---

### Post by 1mwolfpack on 2010-08-03
BUMP!!!!!! 
Having the exact same issue and it is frustrating. I have found that unplugging the bluetooth dongle for a few seconds and plugging it back in works most of the time. Sometimes it takes a few tries. Would still like to find a permanant fix. Its a great media center setup when it stays connected.

---

### Post by agentstewie on 2010-09-13
bump, need help on this too..
;)

---

### Post by andersja on 2010-11-01
> **boardinary said:**
> as soon as the keyboard goes to sleep (30 min of inactivity), I am unable to reconnect.  I must unplug and replug the bluetooth adapter and go through the process of repairing the device with the bluetooth manager.  Sometimes I even have to restart the computer.

Does anyone have any suggestions?

If you are still affected by this bug under Lucid/Maverick, see this link for more information about how to submit debugging information to the developers:
[https://help.ubuntu.com/community/ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs")
[https://help.ubuntu.com/community/ReportingBugs#Adding%20Apport%20Debug%20Information%20to%20an%20Existing%20Launchpad%20Bug]("https://help.ubuntu.com/community/ReportingBugs#Adding%20Apport%20Debug%20Information%20to%20an%20Existing%20Launchpad%20Bug")

It could be [this bug (#292042)]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/292042"), but please verify and post a new bug if necessary.

---

### Post by andersja on 2010-11-15
also see: 
[http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html](http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html)

---

### Post by bric on 2010-11-22
> **andersja said:**
> also see: 
[http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html](http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html)

Is this method (dated 2007) still valid with today's releases (i.e., lucid/maverick)?

---

### Post by marcio123 on 2011-01-12
Any luck ? Does it work like it should ? 

Please write what works and what does not.
Thanks

---

### Post by bric on 2011-01-12
Check this thread:

[http://ubuntuforums.org/showpost.php?p=10323362&postcount=30]("http://ubuntuforums.org/showpost.php?p=10323362&postcount=30")

---

### Post by marcio123 on 2011-01-12
Does this touchpad work ?

---

### Post by agentstewie on 2011-01-13
Hmm well my mediaboard works now but I did upgrade to 10.10 if that helps

---

### Post by marcio123 on 2011-01-13
Does this mediaboard work like touchpad in laptop ? 

I'm asking about the thing that is on the right of this keyboard.

---

### Post by bric on 2011-01-13
Yes, the touchpad works.  And the keyboard.  BUT, if you see the thread I mentioned then to get it working in Maverick requires a tweak (either through updates or specific bluetooth adapter).

---

