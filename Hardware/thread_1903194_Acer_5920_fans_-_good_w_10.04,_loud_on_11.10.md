---
title: "Acer 5920 fans - good w/ 10.04, loud on 11.10"
date: 2012-01-01
forum: Hardware
---

### Post by Bartender on 2012-01-01
Good morning!
My Acer 5920 fans would cycle between slow (virtually silent) & medium speeds with 10.04.  

I've tried several newer Ubuntu or Ubuntu-based distros in the past week and they all spin the fans faster.  I was hoping Xubuntu would be better than full-blown distros, but no.  They'll ramp the fans up when the CPU's busy, but only ramp down to some medium speed instead of virtually silent.

top shows negligible CPU use when fans are running at half-speed.  There are numerous confusing hits when googling fan speeds and I'm hesitant to go chasing down the wrong paths.

I disassembled the lappy a week ago to replace the CMOS battery, which is cleverly buried in the deepest depths.  While in there I replaced the original CPU thermal pad with a dab of Arctic Silver.  Also blew out the grille at the tail end of the heat tube (downstream of the exhaust fan), though there was minimal fuzz trapped in the fins.

---

### Post by essexboyracer on 2012-11-03
I have the same issue woth 11.10 on a 3GB Core 3 Duo T9400 2.53ghz 3.0.0.26-generic. Fan spins up at nearly doing anything and never seems to slow right down? Like you I have not seen anything specifically related to this release and excessive fan usage

---

### Post by jonnyboysmithy on 2012-11-03
It could be your fans have slightly blocked with dust. Wouldn't be a bad idea to clean/blow it out.  See if that makes a difference. It can be surprising how dusty it can get in there.. especially on machines that are a few years old.

---

### Post by essexboyracer on 2012-11-03
I looked inside at the fans and they dont seem that dusty (I have seen much worse). Its an Asus G71v gaming laptop. I did find another thread on here that pointed to a bug in 11.10 kernel overheating issue - I should really upgrade to 12.04. I have Vista on it as well and that doesn't use excessive fans

---

### Post by 2F4U on 2012-11-03
Did you check if there is a newer BIOS version available? Helped considerable on my Acer Extensa 5635Z. But be careful since flashing the BIOS may brick the machine and, as far as I know, you need Windows to flash the BIOS, because Acer only provides a flash program that runs on Windows.

---

### Post by essexboyracer on 2012-11-03
I have a phoenix bios, I am not sure that is the issue as the lappy fan is quiet under Windows (dual boot) and the fan was fine a couple of months ago, its only recently it has started and I imagine this was from some updates that were installed. Am upgrading to 12.04 as we speak

---

### Post by essexboyracer on 2012-11-04
Upgrade to 12.04 went well and it appears to have solved the fan issue on one user account, but weirdly not the other? (time will tell) now on 3.2.0-32-generic-pae

---

### Post by essexboyracer on 2012-11-11
[Bummed]("http://ubuntuforums.org/showthread.php?t=2071520"), have ordered a can of air...

---

### Post by Bartender on 2012-11-18
I'm not comfortable diving into the OS's inner works and tweaking stuff.

Fortunately, our Acer 5920's CPU fan acts just about like I'd expect it to running 12.04.  I'm more of a hardware guy than software; the 5920's been opened up and cleaned out.  It wasn't very dusty inside.

BTW, our 5920 is the Intel onboard graphic, not the "G" model with discrete graphics.

Is there consensus whether the fan is reacting to heat that's really there because the parts are running harder than they should be?  Or is the kernel sending a signal to spin the fans harder even if there's no need to remove excess heat?

---

