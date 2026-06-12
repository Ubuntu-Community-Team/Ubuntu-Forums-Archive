---
title: "&quot;Disable touchpad while typing&quot; NOT working on lenovo ThinkPad E520"
date: 2012-10-05
forum: Hardware
---

### Post by ikapl on 2012-10-05
Hi, 

I just installed Ubuntu 12.04 LTS 64bits on my newly bought Lenovo E520 ThinkPad.

I started to type something, and noticed that the cursor kept moving. This didn't happen with my old laptop. I found this option "Disable touchpad while typing" in the mouse control options, and it was checked. Unchecking and rechecking didn't do any thing. Anyone has any idea?

---

### Post by ikapl on 2012-10-06
Hi, 

I found a partial solution, using the application "Synaptiks touchpad management". This program actually works!

But it has a downside: it crashes whenever the computer is waken from sleep mode. 
Where do I report this?

---

### Post by funicorn on 2012-10-06
Calm down. You don't have to report this bug. The upstream surely know its existence. They just don't talk about it, when they cannot fix it.

---

### Post by ikapl on 2012-10-06
if you say so...

---

### Post by mbbailey123 on 2012-10-07
I am having the same problem with me Dell Studio S1737 Laptop.  I was hoping to find a way to completely disable the touch pad, as it just gets in my way.  There does not seem to be a way to get to the hardware level drivers to disable devices within Ubuntu.

---

### Post by funicorn on 2012-10-19
The linux way to truly 'disable' some device is to edit the udev rules, I wonder whether there is a way to shut the power output down though.

> **mbbailey123 said:**
> I am having the same problem with me Dell Studio S1737 Laptop.  I was hoping to find a way to completely disable the touch pad, as it just gets in my way.  There does not seem to be a way to get to the hardware level drivers to disable devices within Ubuntu.

---

