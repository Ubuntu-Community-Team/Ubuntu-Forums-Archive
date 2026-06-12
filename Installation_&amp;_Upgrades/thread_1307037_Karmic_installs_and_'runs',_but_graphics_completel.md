---
title: "Karmic installs and 'runs', but graphics completely broken (even login screen)"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by BetterSense on 2009-10-30
So I burninated a fresh alternate, amd64 disk ran it and it worked, for certain values of 'worked'. It installed and now on grub i can see my old system and boot it just fine. That's what I'm on right now. But the new system that I actually just installed is broken. It boots, but when it is supposed to switch to the login screen, everything completely breaks and the monitor is like a color test pattern of noise, and my monitor says "out of range". Nothing is visible.

I can switch to a terminal with ctrl+alt+F2, but that is a monochrome test pattern of noise, and I can't see anything.

Luckily, I can touch type, and entering my username+enter, then password+enter, then "sudo reboot"+enter, then my password, will reboot the system. So it's running, I just can't see anything.

I have no idea what to do; re-reinstalling is going to do the same thing. When I installed, I did NOT have tubes because I only have a wireless card. Do you think updating would fix it? What are the chances that if I plug my box in with a network cable, boot to an invisible terminal, and run "sudo apt-get update && sudo apt-get upgrade && sudo reboot", without making a keystroke error, that it will be fixed? 

Or any other suggestions?  How can I make my system boot, but not run X and maybe just give me a terminal that I can see?

---

### Post by markbuntu on 2009-10-30
You should be able to do a CTRL ALT F2 to get a terminal. CTRL ALT F2-F6 are terminals.

CTRL ALT F7 to get back to your kludged desktop.

What gpu do you have?

---

### Post by JBAlaska on 2009-10-30
"out of range" usually means the video card is trying to overdrive your refresh rate higher than your monitor can handle. Try renaming /etc/X11/xorg.conf to /etc/X11/xorg.conf.bak and rebooting.

---

### Post by BetterSense on 2009-10-30
> You should be able to do a CTRL ALT F2 to get a terminal. CTRL ALT F2-F6 are terminals.

CTRL ALT F7 to get back to your kludged desktop.


It's not just the desktop that's kludged! When I switch to F2, even the terminal window is a mess of noise and weird static. I've confirmed that it IS a terminal window though, because I can reboot from it, if I can type without making any mistakes.

> 
"out of range" usually means the video card is trying to overdrive your refresh rate higher than your monitor can handle. Try renaming /etc/X11/xorg.conf to /etc/X11/xorg.conf.bak and rebooting. 

Do you have any tips on how to do this without being able to see anything at all, and without a labeled keyboard (I type dvorak, but use a qwerty keyboard). 

Really, I wish there was a way to boot into stoneage mode so that I could at least get a terminal that I could use.

> What gpu do you have?

I have a Biostar motherboard with the built-in 7000-series gpu.

---

### Post by markbuntu on 2009-10-30
Boot into the recovery kernel and try the fix x option.

---

### Post by BetterSense on 2009-10-31
I found out on another forum that I could add the word "single" to the kernel entry in grub to get a plain terminal. Didn't know what to do because there is no xorg.conf anymore. I lsmod, and didn't find anything that looked like a graphics driver. Running startx just returned me to sploded graphics. What I ended up doing is installing envyng, which builds and installs the latest nvidia kernel. I ran that and rebooted and the system is up and running now. It's as if there were no graphics drivers installed or something.

---

