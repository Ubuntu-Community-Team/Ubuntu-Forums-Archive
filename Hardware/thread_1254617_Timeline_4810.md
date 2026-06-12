---
title: "Timeline 4810"
date: 2009-08-31
forum: Hardware
---

### Post by tijmz on 2009-08-31
Hi all,

I am considering installing Jaunty on my Timeline 4810, but I only want to do it if it doesn't give too much problems. I've come across mentions of it having to be run in IDE mode for the HDD to work and that the ATI card inside isn't supported. 

I'm interested in the consequences of these problems and also in any experiences you may have running Ubuntu Linux on a Timeline 4810. Please help me decide :)

---

### Post by wilcoxjay on 2009-09-01
Hey, I'm running jaunty on a 4180t, so I thought I'd give some thoughts.

First, I'd just say that the system was usable straight out of the box. A few issues had to be worked on, but the most important tool (the (wireless) internet) worked straight away.

There's tons of info on the forums about fixing the stuff that doesn't work out of the box. The main thread about timeline issues is at [http://ubuntuforums.org/showthread.php?t=1165087](http://ubuntuforums.org/showthread.php?t=1165087) .

The thing with the most potential to annoy, IMO, is the optical (CD/DVD) drive. It works for me if I type ```
eject cdrom
``` in the terminal.

I encourage you to try it out. If you're wary about messing with your partitions, I recommend [WUBI]("http://wubi-installer.org/") .

James

---

### Post by tijmz on 2009-10-09
Thanks for your response :)

I went ahead and ran Jaunty, but it didn't really work out. I couldn't shut down and suspend was failing. Using Karmic fixed this problem, but I have some issues remaining. Right now I am trying to get my BT device recognized. I've read that I should have turned the device on in Windows, but that is not an option for me right now.

Does anyone know of a way to get the 4810TG Bluetooth adapter working? An hcitool dev shows me there's nothing recognized right now...

---

### Post by seppbrandy on 2009-11-18
Hallo
how about the energy saving on the 4810 ?
Running karmic there is no way I can get more than 3.5 hours on battery power, where on vista I get the advertised 8 hours.
May be, that is because the cooling fan is always at high speed ?

Sepp

---

