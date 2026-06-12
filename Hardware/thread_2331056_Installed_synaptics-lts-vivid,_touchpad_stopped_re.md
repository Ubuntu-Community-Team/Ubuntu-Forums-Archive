---
title: "Installed synaptics-lts-vivid, touchpad stopped responding"
date: 2016-07-17
forum: Hardware
---

### Post by jdkcarlson on 2016-07-17
I have a Synaptics SynPS/2 TouchPad with a growing variety of problems on an Acer Aspire R5-471T laptop running Ubuntu 16.04. I have another thread where I've asked about those problems, but this is a new one.

Since installing 16.04 I've noted that I wind up pasting a lot of text I don't want to and accidentally closing tabs, and I realized today both of these unwanted behaviors were due to a middle click that doesn't appear in the trackpad options in the System Settings. I found this advice for disabling right clicks

[http://askubuntu.com/questions/217835/how-do-i-disable-the-right-click-when-pressing-the-right-side-of-my-trackpad](http://askubuntu.com/questions/217835/how-do-i-disable-the-right-click-when-pressing-the-right-side-of-my-trackpad)

and thought I would follow along the first part but disable the middle click instead of the right. So I did

sudo apt-get install xserver-xorg-input-synaptics-lts-vivid

The touchpad immediately stopped responding. I did uninstall, but nothing changed. I typically suspend and unsuspend or restart to get this trackpad responding again (it stops maybe once a day lately, so this was not obviously unusual), but trying to suspend, restart, or shut down via the menu items were unsuccessful. So I did a hard reset. When things came back, the desktop icons were blown up to a huge size and the trackpad was still nonresponsive. Clicks do nothing and the cursor doesn't move.

What can I do to get the trackpad up and running again?

---

### Post by jdkcarlson on 2016-07-18
[bump]

For example, is there a standard suite of drivers one uninstalls and reinstalls in this instance? I've found an external mouse more or less works fine, but the trackpad is just not responding anymore.

---

### Post by jdkcarlson on 2016-07-20
bump

---

### Post by jdkcarlson on 2016-07-21
bump

If anyone has any ideas how to get this touchpad working, it'd be very much appreciated. Please.

---

### Post by jdkcarlson on 2016-07-30
The solution was to press Fn+F7.

---

