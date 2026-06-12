---
title: "Dell Precision T7500, adjusting fan speed"
date: 2014-03-02
forum: Hardware
---

### Post by MakOwner on 2014-03-02
I just picked up an off-lease Precision T7500 dual 6 Core L5639 system.  I'm running one enterprise class SATA drive in the 3.5 "extra" bay in place of the card reader, and one consumer class desktop drive in one of the internal 4 bay enclosure.
Both drives are running in the 102 - 107 Fahrenheit range. 

I typically control my environment and airflow in both Dell rack mount servers, external disk enclosures and all of my previous workstattions to keep my disk temps under 100F, in an attempt to extend life.
Anecdotal evidence of my small sample shows that drives running over 100F as reported by the SMART data will fail considerably faster than drives running under 100F.


The T7500 is _really_ quiet, with barely any airflow evidenced in the rear or front of the case.

Is there any way to increase the speed of the fans to increase the airflow, or am I just relegated to cooking hard drives?

---

### Post by MakOwner on 2014-03-03
Bueller? Bueller? Anyone?

---

### Post by Yellow Pasque on 2014-03-04
First, please don't cross post: [http://ubuntuforums.org/showthread.php?t=2209099](http://ubuntuforums.org/showthread.php?t=2209099)

Second, what are the extended load temps? If they're <= 130F, then there's really nothing to worry about, as that's still within spec.  Saying that the drives are bubbling and boiling at 120F is completely ridiculous...

> Anecdotal evidence of my small sample shows that drives running over 100F as reported by the SMART data will fail considerably faster than drives running under 100F.
Google did a study a while back using a much larger sample. It actually found that temps had much less correlation to failure rates than a lot of people thought. Even more surprising, drives < 3 years were more likely to fail running at colder temps...
[http://static.googleusercontent.com/media/research.google.com/en/us/archive/disk_failures.pdf](http://static.googleusercontent.com/media/research.google.com/en/us/archive/disk_failures.pdf)

As far as the fans go, you should give more info on how the fans are attached. Are they using Molex connectors or are they plugged into the motherboard? Have you tried using pwmconfig/fancontrol scripts yet?

---

### Post by MakOwner on 2014-03-04
> **Temüjin said:**
> First, please don't cross post: [http://ubuntuforums.org/showthread.php?t=2209099](http://ubuntuforums.org/showthread.php?t=2209099)

Second, what are the extended load temps? If they're <= 130F, then there's really nothing to worry about, as that's still within spec.  Saying that the drives are bubbling and boiling at 120F is completely ridiculous...


OK, well, I don't want to hold them in my bare hand after they run like that.  
I'm accustomed to running all my drives at 100F or less, and if they get higher increasing airflow/ventilation/cooling as needed.
Probably a little paranoid about heat, but hey, I'm in Texas.  Gets hot here.


> 
Google did a study a while back using a much larger sample. It actually found that temps had much less correlation to failure rates than a lot of people thought. Even more surprising, drives < 3 years were more likely to fail running at colder temps...
[http://static.googleusercontent.com/media/research.google.com/en/us/archive/disk_failures.pdf](http://static.googleusercontent.com/media/research.google.com/en/us/archive/disk_failures.pdf)

As far as the fans go, you should give more info on how the fans are attached. Are they using Molex connectors or are they plugged into the motherboard? Have you tried using pwmconfig/fancontrol scripts yet?

It's a Dell T7500 - I have tried fancotrol and pwmconfig and pwmcofngi doesn't find any controllable fans, so I've no idea what to put in the fancontrol config file.
I have found some information about a utility called ik8, but tracking it down is taking more time thn I'd like.  I see it (ik8utils) in the desktop repo for Mint Mate 14, but not 16. 

Any pointers to that, or to the physical temp sensors on this thing so I can mask them and raise the local temps to increase the fan speed would work too.

---

### Post by MakOwner on 2014-03-04
This is a set of disks that are running what I would consider within a "normal" range. 
These are 7200RPM SATA disks that are beat on pretty hard every day.


```

1.1          1      0         0             25 C   77 F
1.2          2      0         0             26 C   79 F
1.3          3      0         0             29 C   84 F
2.1          0      n/a       0             31 C   88 F
2.2          1      n/a       0             30 C   86 F
2.3          2      n/a       0             31 C   88 F
2.4          3      n/a       0             30 C   86 F
2.5          4      n/a       0             29 C   84 F
2.6          5      n/a       0             30 C   86 F
2.7          6      n/a       0             30 C   86 F
2.8          7      n/a       0             30 C   86 F
2.9          8      n/a       0             29 C   84 F
2.10         9      n/a       0             29 C   84 F
2.11         10     n/a       0             29 C   84 F
2.12         11     n/a       0             30 C   86 F
2.13         12     n/a       0             30 C   86 F
2.14         13     n/a       0             31 C   88 F
2.15         14     n/a       0             31 C   88 F
3.1          0      n/a       0             30 C   86 F
3.2          1      n/a       0             31 C   88 F
3.3          2      n/a       0             31 C   88 F
3.4          3      n/a       0             31 C   88 F
3.5          4      n/a       0             30 C   86 F
3.6          5      n/a       0             30 C   86 F
3.7          6      n/a       0             30 C   86 F
3.8          7      n/a       0             30 C   86 F
3.9          8      n/a       0             30 C   86 F
3.10         9      n/a       0             29 C   84 F
3.11         10     n/a       0             30 C   86 F
3.12         11     n/a       0             31 C   88 F
3.13         12     n/a       0             31 C   88 F
3.14         13     n/a       0             31 C   88 F
3.15         14     n/a       0             31 C   88 F
4.1          0      n/a       0             30 C   86 F
4.2          1      n/a       0             30 C   86 F
4.3          2      n/a       0             30 C   86 F
4.4          3      n/a       0             31 C   88 F
4.5          4      n/a       0             30 C   86 F
4.6          5      n/a       0             30 C   86 F
4.7          6      n/a       0             30 C   86 F
4.8          7      n/a       0             30 C   86 F
4.9          8      n/a       0             29 C   84 F
4.10         9      n/a       0             29 C   84 F
4.11         10     n/a       0             29 C   84 F
4.12         11     n/a       0             29 C   84 F
4.13         12     n/a       0             30 C   86 F
4.14         13     n/a       0             30 C   86 F
4.15         14     n/a       0             31 C   88 F

```

---

### Post by Yellow Pasque on 2014-03-04
^ I have no idea what that last post is supposed to show?

Anyway... if pwmconfig won't control the fans, either the BIOS already has control of them or the motherboard doesn't have the proper circuitry to control them.

---

### Post by MakOwner on 2014-03-04
> **Temüjin said:**
> ^ I have no idea what that last post is supposed to show?

Anyway... if pwmconfig won't control the fans, either the BIOS already has control of them or the motherboard doesn't have the proper circuitry to control them.

It shows 60 drives running under load at less than 100F.
One file system, by the way.

Critical details masked to hide the source.

---

### Post by tgalati4 on 2014-03-04
Dell BIOS tends to be basic, but are there any fan-related switches in BIOS?  Sometimes changing "Quiet" mode to "Normal" or "High Performance" will change the fan speed trigger points.

Also, check for BIOS updates at the Dell support website.  Sometimes updates fix things like this.

How old is the machine?  It could be that the fans are worn out.  Try oiling the bearing under the sticker.

---

### Post by MakOwner on 2014-03-05
The BIOS is at the latest version available on the Dell website - I don't see any options in the BIOS related to fans or cooling - at least not obvious ones.
The fans all appear to be turning, with no obvious issues in regards to physical performance (The fans all ramp up to full speed when connecting power and then ramp down immediately.)

---

### Post by IvoGuerreiro on 2014-03-05
Hello, sorry if i will write something silly but, relatively about the past #5, that seems normal a 7200 rpm SATA have a range of temperature in work ideally between 25 - 35 º. :-k

---

### Post by MakOwner on 2014-03-05
This T7500 is allowing the drives in the internal bays creep up to 122F (~50C) before I shut it down.  And that's just sitting idle.
I'm downloading the latest bios from Dell and I'm going to reload it, but everything else seems to be working, so I don't thing this will help much.

---

