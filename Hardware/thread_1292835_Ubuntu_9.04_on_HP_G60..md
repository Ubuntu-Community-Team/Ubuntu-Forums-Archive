---
title: "Ubuntu 9.04 on HP G60."
date: 2009-10-16
forum: Hardware
---

### Post by Jguy on 2009-10-16
Hi.

I just purchased a used HP G60 Laptop. 3 GB of RAM and a Dual Core AMD Turion processor. 

right now, I'm having a little problem. I first tried to install kubuntu on it, but when I ran the live CD, I a) don't care much for kde, and 2) noticed that one of my cores was at a constant 100%. I first thought it was the live CD, so I went ahead with installation but cancelled at the last second.

Now, I booted up ubuntu liveCD and began the installation, thinking the 1 core at 100% was just the fact that everything was being read from the liveCD.

But, everything installs fine but for some reason, even after rebooting and running jaunty from the HDD, the one core is at 100% usage, and load averages average around .50, .30, .20. Looking at the system monitor, the cores 'switch off' at who gets to be at 100% and who gets to be at 0%. Every so often, the CPU balances off and each core goes to around 50%...

Looking at the process tab, the CPU column is full of '0', there is no process eating up that much CPU usage, so what might be going on?

thanks for any help you can provide for me. I would not like to system restore to Vista. It seems everything worked directly out of the box, no additional things needed. All the shortcut buttons, all the components...it's the best install of Ubuntu yet ;_;

EDIT: Forgot to mention, I have installed the 32bit version of jaunty.

---

### Post by Jguy on 2009-10-16
Sorry to bump.

I have not installed any drivers for the NVidia card I have in here. I will do that and report. Visual Effects is stuck in the 'off' position and I used top to check xorg's CPU usage, it's at a constant 20+.

I also have 125 processes running...far more than even my server at home running Jaunty Desktop, that also has LAMP attached.

---

### Post by Jguy on 2009-10-16
That did it. The installation of the drivers fixed the issue. Sorry to take up space. :)

---

