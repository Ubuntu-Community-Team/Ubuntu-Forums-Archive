---
title: "Stuck at &quot;Checking battery state&quot;."
date: 2005-09-21
forum: Hardware &amp; Laptops
---

### Post by snoochems on 2005-09-21
Hi all.    

I'm trying to install ATI drivers.  

I'm following a guide that has me using the command** "sudo /etc/init.d/gdm stop"**  after "CTRL-ALT-F1 " to get to the console.

But it gets stuck at "checking battery state".  

So, i can't continue.  This is happening in both Hoary and Breezy.

What is it, and how can i get the stupid thing to stop looking for my non-existant battery!

---

### Post by Heretushi on 2005-10-07
Exact same problem here. Exactly at that point, when I try to install my video drivers too!

---

### Post by providence on 2005-10-08
You're not alone. I'm trying to kill gdm to install the Nvidia drivers and I'm met with the same "Checking Battery State" message.

I'm assuming this is a module loaded for notebook computers. Seeing that I'm using a desktop computer could I somehow disable that specific module as a workaround? Not that I'd know how to perform such an operation though...

Any thoughts, folks? I sure would like to kill gdm and get those drivers installed.

---

### Post by malacoda on 2005-10-14
I've caught the bug too...

After using Hoary a wee bit and the Kubuntu Breezy RC for about a week, I installed - full fresh & clean install, not an update - the Kubuntu Breezy 5.10 release last night.  

Installed fine (after several attempts due to incorrect repository changes on prior installs).  Uncommented all the repositories except for the backports line. Update Adept - went fine.  Make sure all nVidia drivers were set up right by ensuring the necessary options were selected in Adept, installing them, and entering terminal to make sure 'driver' line in xorg.conf was set to 'nvidia'.  Still no problem.  Installed Mplayer and VLC via Adept and everything seemed fine.  Stopped there and went to bed.

Got home from work today, started up PC - boot hangs after providing an 'OK' on Checking Battery State.  Can boot by choosing 'recover mode' in GRUB but don't have the slightest idea what to do from the root prompt.

Anybody figure out what might be causing this or how to fix it... I really don't want to install a fifth time...:( 

Malac

---

### Post by malacoda on 2005-10-16
Think I found a way around this.

My initial install would go well, but once I installed the nVidia drivers via the Adept Pkg manager my system would hang up each time I booted right after finishing 'Checking Battery Status'.

After a bit of research and some input from others, I came to suspect the nVidia drivers I was using from the repositories via Adept Pkg Mgr had a bug that locked up X11 (or xserver or what ever you want to call it...).

I decided to install from source by following tseliot's how-to:
[http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia]("http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia")

Before you do though I recommend installing Mozilla Firefox first.  When I tried downloading the driver he recommends (from the nVidia website) my desktop would become corrupt (due to not having the video driver installed yet) if I used Konqeror.

Installing the driver per this how-to resolved my 'boot hang' issue.

---

