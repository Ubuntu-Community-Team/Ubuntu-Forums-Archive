---
title: "Mouse problems with touchpad on Acer Aspire R5-471T"
date: 2016-03-30
forum: Hardware
---

### Post by jdkcarlson on 2016-03-30
I've installed Ubuntu 14.04. Initially I couldn't use the touchpad at all (fortunately, there's a touchscreen, but it's usually less easy), but I found an option in BIOS that I changed from "Advanced" to "Basic" on a hunch and then was able to use the touchpad again. 

1) I can't enable two-finger scrolling. It doesn't appear in my options. I tried adding a line to /etc/X11/xorg.conf (which I created for this purpose, based on [this]("http://askubuntu.com/questions/463898/ubuntu-14-04-two-finger-scroll")), but it hasn't changed anything yet.

2) Clicks seem to go missing. At times I want to shift focus from one window to another and it takes several clicks to get the system's attention. 

What can I do about these things?

---

### Post by mörgæs on 2016-03-30
How does it work in a live boot of 16.04 (development version)?

---

### Post by jdkcarlson on 2016-03-30
Not sure. What would I do, download it and boot off a stick?

---

### Post by mörgæs on 2016-03-30
Yes, please do as it also might help on your other problems, too. Maybe there is no need for the massive posting.

---

### Post by jdkcarlson on 2016-03-30
Sorry, I don't mean to be a disruptive influence here. I was just encouraged to start on an older version, for reasons I don't remember.

---

### Post by howefield on 2016-03-31
> **jdkcarlson said:**
> Sorry, I don't mean to be a disruptive influence here. I was just encouraged to start on an older version, for reasons I don't remember.

You are using the current Long Term Support release so please don't feel that you need to justify why, and don't be put off posting your issues by other forum members.

Having said that, there is merit in trying the latest 16.04 from a Live media - which won't be released till the 21st April, so is still in development.

---

### Post by jdkcarlson on 2016-04-01
> **howefield said:**
> You are using the current Long Term Support release so please don't feel that you need to justify why, and don't be put off posting your issues by other forum members.

Having said that, there is merit in trying the latest 16.04 from a Live media - which won't be released till the 21st April, so is still in development.

Thank you for the kind words. I'll try out the new version in a few days. Will I be able to use the stuff on my current Ubuntu partition, when I'm booting off the stick?

---

### Post by howefield on 2016-04-02
> **jdkcarlson said:**
> ... Will I be able to use the stuff on my current Ubuntu partition, when I'm booting off the stick?

Depends on what you mean by "stuff", if you mean access your data then for the most part yes, if you mean use applications then probably not.

I'd guess that the idea of booting into a Live session of the current release is that you will find out if the newer software stack resolves your issues. You will only need to use it for a short while.

---

### Post by jdkcarlson on 2016-07-08
I did ultimately upgrade to 16.04 for much more serious reasons, but the trackpad problems mostly didn't resolve. They did change some. Here's a list of what I believe the current ones are.

At times when I suspend, especially when shutting the lid, the trackpad doesn't work as well. Often shutting the lid and reopening it solves this problem.

Two-finger scrolling typically works when I start up and eventually stops working. Eventually the trackpad tends to stop working altogether and I restart. 

Sometimes there's a variant where the cursor does move with the trackpad, but doesn't interact with the rest of the system: clicks and the keyboard don't work. That also leads to a restart.

---

### Post by jdkcarlson on 2016-07-13
To reiterate my tale, this Synaptics trackpad works fine on the partition holding the original Windows installation, but initially, didn't work at all in Ubuntu. I fixed that by switching a trackpad setting in BIOS from "Advanced" to "Basic." It's had many problems since, however.

If I touch it with a slightly moist finger, the cursor will dance erratically for several minutes. Cleaning with an alcohol solution tends to ameliorate this, though there have been times I've turned off the device and left the trackpad covered with rice overnight. I've never experienced such sensitivity to water.

The two-finger scroll generally works when the computer starts up, but used to often stop working sometime later. Lately, it's been working, despite there having been no intervening changes.

It is common that when I return from a suspension, the trackpad is nonresponsive. The touchscreen still works in this instance. Often suspending again and unsuspending solves this. It seems to be governed partially by chance. 

On the other hand, sometimes the trackpad continues responding, but clicking or typing no longer have any effect. This sometimes happens after a suspension I've induced to try to make the trackpad responsive again. In this case the touchpad also is nonresponsive and the only remedy I know is a hard restart.

The nonresponsive trackpad happens every day, and the the noninteractive cursor happens at least twice a week, and so far twice today. It's a serious drain on my productivity having to constantly suspend and restart. What can I do to make this trackpad get along with Ubuntu?

---

### Post by Bucky Ball on 2016-07-13
*Threads merged*

... as your second thread provides further information to this one, where you are already receiving support for the same issue. Please do not duplicate post with same issue. Thanks.

If you feel your thread is not getting any attention after twelve hours or so, simply post 'bump' on the thread rather than starting a new one. 

Good luck.

---

