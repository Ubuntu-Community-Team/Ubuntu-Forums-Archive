---
title: "Synaptic Touchpad - Configuration Question"
date: 2006-05-26
forum: Hardware &amp; Laptops
---

### Post by TriZz on 2006-05-26
I have a Compaq Presario V2000

Breezy Badger

I'm new to the Linux thing, and have had a BLAST learning how to get the wireless card working (ndiswrapper) and the upgraded ATI graphics card (fglrx) working...I love this sort of thing - research, implement and pray!  This community is awesome and very helpful to eager beginners (silly newbs).

At any rate:  The problem that I'm having (although some may consider it a blessing since it works well) is that the touchpad is far too sensitive.  That damn cursor moves so fast, like it's running from the police!!

I haven't been able to find anything on configuring the speed of the synaptic touchpad (sensitivity and acceleration).  Everything that I find is in regards to jerky usage or weird behavior.

I appreciate any suggestions you may have.

Thank you,
TriZz

---

### Post by badrinarayan on 2006-05-26
[This]("http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad") should help (or get you started).  Run ```
man synaptics
``` for a detailed discussion of the various options. synclient command should help you change all the values on the fly once the driver works - so you don't have to restart your X each time. ;)

---

### Post by TriZz on 2006-05-26
When I type
 
```
man synaptics
```
 
I get 

> No manual entry for synaptics
 
Any ideas where I'm going wrong?

Thank you for your help - it's truly appreciated.

---

### Post by badrinarayan on 2006-05-26
I just [found]("http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=xfree86-driver-synaptics&version=breezy&arch=i386") that the version in breezy does not have that man page! I have attached mine. See it using ```
man -l synaptics.5.gz
```
For you, ```
man synclient
``` should work.

---

