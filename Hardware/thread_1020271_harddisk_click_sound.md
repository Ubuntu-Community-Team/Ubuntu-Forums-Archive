---
title: "harddisk click sound"
date: 2008-12-23
forum: Hardware
---

### Post by talktorishav on 2008-12-23
Hello

I have Intrepid on Lenovo Y510. I hear my harddisk click at some random time. I have ext3 partition. Should I be cautioned or what?

---

### Post by tommcd on 2008-12-24
Make sure you have **laptop mode** enabled. See this thread:
[http://ubuntuforums.org/showthread.php?t=994598](http://ubuntuforums.org/showthread.php?t=994598)
Laptop mode (among other things) will help to save wear and tear on your hard drive.

---

### Post by CrunchyDoodle on 2008-12-24
I have never experienced a zero-seek failure on a laptop or external 2.5" hard drive, but have with several 3.5" hard drives. On a 3.5" hard drive, you will hear a whirring sound followed by a distinct click. This is a hard drive trying to recover its sense of where the head is on the platter. It's caused by having an active area of the hard drive being unreadable, thus the controller gets lost and needs to recover. The whirring is the head being moved across the platter a track at a time and the click is when it hits the mechanical stop at zero. If it finds zero OK, it will continue working, otherwise the drive is toast. I would suggest planning to replace this hard drive soon.

Bye.      :cool:

> **talktorishav said:**
> Hello

I have Intrepid on Lenovo Y510. I hear my harddisk click at some random time. I have ext3 partition. Should I be cautioned or what?

---

### Post by talktorishav on 2008-12-24
Should I enable laptop mode on AC too?

---

### Post by tommcd on 2008-12-24
> **talktorishav said:**
> Should I enable laptop mode on AC too?

I did. I figure it can't hurt. The default is for laptop mode to be off on AC power. If you want to enable laptop mode on AC power edit /etc/laptop-mode/laptop-mode.conf as described in the thread I linked to in my earlier post.

---

### Post by talktorishav on 2008-12-26
I'm totally confused. Some says to enable laptop mode and some says not to do so. 

How is laptop mode solution for this? What are the disadvantages of having laptop mode?

---

### Post by tommcd on 2008-12-26
> **talktorishav said:**
> I'm totally confused. Some says to enable laptop mode and some says not to do so. 
Who said not to enable laptop mode?

> **talktorishav said:**
> 
How is laptop mode solution for this? What are the disadvantages of having laptop mode?
This was discussed in the thread I linked to in my earlier post:
[http://ubuntuforums.org/showthread.php?t=994598](http://ubuntuforums.org/showthread.php?t=994598)
> 
I began using Ubuntu a lot just about two weeks ago. After installing, I noticed that my laptop hard drive was making a strange noise at least a few times per minute. As it turns out, that "noise" is the same as a load cycle. When I used Windows as my primary operating system, I don't recall ever hearing the noise.
So here's the problem: Hard drives are rated for a certain number of load cycles before they are considered "dead". Most hard drives are rated for 600,000 +/- load cycles before they die, but I'm sure there are many that have exceeded that number and lived. Since I was hearing that "noise" quite a few times per minute, I was getting concerned.
After doing some research, I found that laptop mode is disabled by default, which is understandable. I don't know if Ubuntu is primary for desktops or not, but that "laptop mode" setting is critical. Aggressive power settings, either by Ubuntu or through the system BIOS, can cause a massive influx of load cycles.

I have no way of knowing whether the "clicking sound" you hear is the same as the noise that Ispyamoose is referring to in that thread. I was hearing those noises frequently also. After enabling laptop mode those hard drive noises decreased significantly. I don't know of any disadvantages of laptop mode, other than possibly slightly slower hard drive access times.

The other possibility (as CrunchyDoodle mentioned) is that your hard drive is failing and will need to be replaced soon.

---

### Post by talktorishav on 2008-12-29
OK, I have enabled it on both AC and battery mode. I have not hear the sound so far..........

---

