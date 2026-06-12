---
title: "motherboard problems"
date: 2015-07-02
forum: Hardware
---

### Post by tbrown122387 on 2015-07-02
I just wanted some confirmation that I should purchase a new motherboard. I used to think it was a memory problem. But that was until I got new memory. The problem remains.

Here are my three symptoms that I've been experiencing that have led me to believe this:

1. Occasionally after I boot up my computer, the login screen won't recognize my password. Sometimes a few days later I'll try again and it will work. 

2. Today it happened to work but my ~/ directory was copied into my ~/Desktop directory. Also I am seeing a lot of old programs on my unity bar. I'm sure I deleted these shortcuts a while ago.

3. If I boot up my computer, sometimes it will get stuck in that Ubuntu screen with the loading bar/line of dots. Sometimes it'll just hang on a black screen. Sometimes it'll spit out some error, but I can't copy and paste that error to show you guys.

The error message would probably be super informative, but can I get some confirmation on my hypothesis before I whip out my pen and paper and jot a bunch of stuff down?

Best, 
T

---

### Post by flocculant on 2015-07-02
>  the login screen won't recognize my password

> my ~/ directory was copied into my ~/Desktop directory

> sometimes it will get stuck in that Ubuntu screen with the loading bar/line of dots

Quite often I've seen these things associated with full / drive or / waiting for fsck to run and/or complete

> The error message would probably be super informative

I'd do that before you do more - no-one's likely to tell you to get a new motherboard without more information.

---

### Post by tbrown122387 on 2015-07-02
Ok, I'll try to get that for you all.

Also it appears I no longer have a ~/Desktop folder. But if I save something to ~/ then that file shows up on my Desktop homescreen.

---

### Post by pfeiffep on 2015-07-02
If these symptoms are actually CAUSED by hardware it wouldn't be my first choice. What leads you to suspect the MB?

---

### Post by weatherman2 on 2015-07-02
Doesn't sound like a motherboard issue to me.  Hard drive seems a more likely culprit.  Has it been tested?  Try GSmartControl and check the Attributes tab to see if any are highlighted in red.  Those are the ones to take special note of - if none are highlighted in red, it's probably not a failing hard drive.

It could be a corruption caused by intermittently failing hardware - hard drive, power supply, RAM, overheating CPU, yes even a bad motherboard.  But there are ways to test each one and rule it out.  I would first run Memtest overnight on whatever RAM you think is good, I'd next boot a live USB of Ubuntu and run some sort of stress test for the CPU.  Usually I open a terminal and type this:

```
sudo -i
dd if=/dev/zero of=/dev/null &
dd if=/dev/zero of=/dev/null &

```

(Yes, that last one twice.  If your CPU has four real cores, I would run it four times.)

That should cause the CPU to run really hot.  Let that go for a few hours; if it doesn't shut off, freeze, or reboot, most likely you don't have an overheating problem.
 
It may not be a hardware issue at all.  Because I have no idea how Ubuntu was installed or what your setup is, I can't say.

---

