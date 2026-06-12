---
title: "Ubuntu 9.04 &amp; UbuntuStudio 9.04"
date: 2009-08-01
forum: Installation &amp; Upgrades
---

### Post by jadhav333 on 2009-08-01
I am a 3d Animator and planning to install Ubuntustudio 9.04 on my m/c

1) Is there any difference in the core system files / features / functionalities between Ubuntu 9.04 and UbuntuStudio 9.04 (other than the pre-installed multimedia applications in ubuntustido 9.04)

2) Are all the automatic / recommended  updates in Ubuntu applicable to UbuntuStudio as well? How well supported is it..

3)Has anybody used UbuntuStudio? Can you pls share your experiences..

---

### Post by zvacet on 2009-08-02
1. No

2. Yes

3. I will let this one to somebody else.

---

### Post by snowpine on 2009-08-02
1) Yes; Ubuntu studio uses a different kernel, 'linux-rt', which is a real time kernel optimized for low latency when processing audio.
2) Yes
3) I used UbuStu 8.04 briefly, but the rt kernel didn't play nice with my hardware. I have not tried newer versions.

---

### Post by jadhav333 on 2009-08-02
Anybody else who use/has used ubuntustudio 9.04.. Pls share your experiences..

---

### Post by jadhav333 on 2009-08-03
Can I  Install ubuntu 9.04 and then install ubuntustudio 9.04 on Virtual Box :? Will it affect the way ubuntustudio works.

---

### Post by lisati on 2009-08-03
I have Ubuntu Studio 9.04 on my desktop (dual boot with XP) but don't use it much. It comes with a different set of applications installed by default, aimed more at multimedia production than those included by default with regular Ubuntu. Along with the kernel, the theme is different as well.

---

### Post by snowpine on 2009-08-03
> **jadhav333 said:**
> Can I  Install ubuntu 9.04 and then install ubuntustudio 9.04 on Virtual Box :? Will it affect the way ubuntustudio works.

Yes, definitely. But I think you would get better performance by simply installing the applications you need in Ubuntu. They are all available in Synaptic as ubuntustudio-audio, ubuntustudio-graphics, ubuntustudio-video, etc. In other words, an existing Ubuntu install can be easily converted to UbuntuStudio, in whole or in part.

---

### Post by jadhav333 on 2009-08-03
And how important is the linux-rt kernel update.. 

From the entire list of applications installed in ubuntustudio, which applications specifically require this (realtime) kernel update..

---

### Post by snowpine on 2009-08-04
> **jadhav333 said:**
> And how important is the linux-rt kernel update.. 

From the entire list of applications installed in ubuntustudio, which applications specifically require this (realtime) kernel update..

The real time kernel is useful for audio production where low latency is a must (for example avoiding glitches when multitrack recording in Ardour). I am not sure if it's needed for 3D animation work. None of the UbuntuStudio applications strictly depend on linux-rt as far as I know.

---

### Post by madnessjack on 2009-08-04
> **jadhav333 said:**
> Anybody else who use/has used ubuntustudio 9.04.. Pls share your experiences..
I'm an avid user of Jaunty Studio, works great, but I can't get my GeForce 5500 FX to work at all. Since I'm using it mainly for music production, this isn't such a problem. It's an oldish computer and I'm using on-board sound. Had no problems with packages or tutorials not specifically aimed at Ubuntu Studio.

If you're fairy tech savvy, I'd recommend it :)

EDIT: Actually just got the drivers working, they had issues with the RT kernel

---

