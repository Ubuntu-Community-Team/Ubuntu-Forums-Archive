---
title: "Ubuntu on a diet"
date: 2009-07-21
forum: Installation &amp; Upgrades
---

### Post by TBerk on 2009-07-21
Well, this might belong here in Installs & Upgrades, or it might belong over in Desktop Environments, but still here is my Question:

- How can we best remove non-essential apps and services, reduce the OS 'footprint' (my definition being the amount of resources required to actually run the computer), and is there already a good FAQ/Sticky somewhere?

Procedures might involve recompiling a new kernel to suit the individuals' needs, but I'd also thing incremental (cumulative?) improvements can be found in other ways as well; (Plain Vanilla package includes a _lot_ of stuff.)

(I personally don't need BlueTooth support at all.) 

Can we kick this one around a bit, or point towards the place this has already been discussed?


TBerk

---

### Post by iaskedalice09 on 2009-07-21
You could make your own Live CD. Also, you can simply go to terminal and type sudo apt-get remove bluetooth -y to remove bluetooth. :)

---

### Post by tommcd on 2009-07-21
You can go to: system > preferences > startup_applications, and uncheck anything you don't need runing automatically at bootup.
I disabled: 
bluetooth, 
"check for new hardware drivers" (I've read that is a big resources hog, and nobody needs that running all the time anyway), 
"update notifier" (I check for updates manually every day)
You can save a few mb of RAM and maybe a little of your CPU resources this way.

---

### Post by Mighty_Joe on 2009-07-22
Ubuntu is a "kitchen sink" distro. It's aimed at getting as many users up and running with as little trouble as possible.  As such, it's probably a bad choice for your goal.  If you are want an OS tailored to your system you should probably look at a distro like [Gentoo]("http://www.gentoo.org/"), which has tools and procedures for building the system from the kernel up.
I used to run Gentoo and it's a *lot *of work.  I never knew if a problem I was seeing was an application bug, a configuration issue, or some module I'd forgotten in the kernel (or compiled into it when I should have left it as a module, or loaded it before some other dependency, and so on and on).  It was maddening and I really can't tell the performance difference between it and Ubuntu. For the most part, the kernel only loads the modules it needs, so manual tinkering is of questionable value.
Another option is this howto I spotted a while ago: [Ubuntu Desktop Minimal]("http://ubuntuforums.org/showthread.php?t=1155961").  It doesn't cover the kernel, just starting from as bare a system as possible and building up.

---

### Post by Simian Man on 2009-07-22
I agree with Joe.  If you want a skinny distro, why try to put the fat one on a diet?  Just go with one that is already skinny.



I really wanted to take this metaphor further, but I'm trying to be nice :).

---

### Post by oldos2er on 2009-07-22
> **TBerk said:**
>  - How can we best remove non-essential apps and services, reduce the OS 'footprint' (my definition being the amount of resources required to actually run the computer), and is there already a good FAQ/Sticky somewhere?


 To remove applications, I use aptitude or Synaptic. To stop services, I use sysv-rc-conf. If there's a module I know I'm never going to use (e.g. Bluetooth, I don't need that either), I blacklist it.

 There are many FAQs listing ways to speed up Ubuntu, or make it more lean. Look in the Tips & Tricks tutorials subforum, or google. Just make sure the FAQ is reasonably up-to-date, and if you are unsure about changing any service or setting, ask here in the forum first. Also, I make a backup copy of a file before tweaking it.

---

### Post by TBerk on 2009-07-22
> **Simian Man said:**
> I agree with Joe.  If you want a skinny distro, why try to put the fat one on a diet?  Just go with one that is already skinny.

I really wanted to take this metaphor further, but I'm trying to be nice :).


Don't be nice, be funny.


> iaskedalice09

You could make your own Live CD. Also, you can simply go to terminal and type sudo apt-get remove bluetooth -y to remove bluetooth. 



Well. bluetooth was just a single example.  I'm off to Tips & Tricks to 
scrounge around.


TBerk

---

### Post by lukeiamyourfather on 2009-07-22
Default install uses less than 200MB of memory and sleeping services and processes don't consume any processor resources. My point is why bother? Unless you're on a machine with less than 200MB of memory the benefits are a moot point.

Like already mentioned you can remove or disable whatever you want. What already comes on the system is what's considered the minimum or base for the average user. Cheers!

---

### Post by RedSquirrel on 2009-07-23
Install an Ubuntu command-line system and build up from there, adding only the packages you want. For example:

[http://psychocats.net/ubuntu/minimal](http://psychocats.net/ubuntu/minimal)

Once the command-line system is installed,  I often do something similar to:

```
sudo apt-get install xorg fluxbox
``````
startx
```and carry on from there.

A custom kernel might make a *small* difference, but Ubuntu's generic kernel seems to work pretty well in most cases.

As **oldos2er** mentioned above, you can use [sysv-rc-conf]("http://packages.ubuntu.com/jaunty/sysv-rc-conf") to turn off services. You can also manually rename the symlinks under /etc/rc?.d/ and tweak files under /etc/event.d/. You do have to be careful about the things you turn off, of course. ;)

---

