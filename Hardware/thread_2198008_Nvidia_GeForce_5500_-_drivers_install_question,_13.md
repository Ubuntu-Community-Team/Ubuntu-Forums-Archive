---
title: "Nvidia GeForce 5500 - drivers install question, 13.10 vs. 12.04, manual?"
date: 2014-01-06
forum: Hardware
---

### Post by BostonLinux99 on 2014-01-06
Hello kind folks,

I have a 13.10 install and a GeForce FX 5500 PCI video card on a Dell Dimension P4 3ghz with 2GB Ram

To make a long story short, in 13.10 no proprietary drivers are recognized as being needed.
However, I get no OPENGL and only 2D unity, etc.  Other 13.10 flavors of Ubuntu xu, lu - do the same thing.
I have a couple drives with 13.10 installed for experiments, etc.

I've spent hours searching forums and google looking for how to install the manual drivers, or what to do.
Maybe being in 13.10 vs. 12.04 LTS might be making it worse with kernel versioning - I'm not sure, I'm a noob but trying very hard to get smarter about how it all fits together.

I can get into the console and run commands, shut down the gui, etc. but I've tried a number of things and no dice.
I've sucessfully trashed my drivers, and had to remove them. I learned about how to get the machine back from this state.

At this point, any idea - how I can get the 173.x.x driver I need installed, or do I need to go to 12.04, or just look for a different card.
I really need some basic 3D to work, and I have this card so was hoping to get it to run.  I'm not expecting the world, but at least the proper NVidia display drivers would be great.

Any help apprec.

---

### Post by marcus.pearlman on 2014-01-06
Did you try: "sudo apt-get install nvidia-173"??  I am pretty sure this version exists in the repository.

---

### Post by BostonLinux99 on 2014-01-06
Yes, and I ended up with 3 seconds of nVidia logo, and then scrambled black and green screen and no screen response.
Now to be honest, I tried a lot of different things, so I can't recall my exact steps at this point.

If I was to run that, it will install the drivers automatically?
And do I have to be out of the UI and in a console only environment to run - [COLOR=#000000]sudo apt-get install nvidia-173[/COLOR]?

---

