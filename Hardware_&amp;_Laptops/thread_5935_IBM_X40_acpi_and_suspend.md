---
title: "IBM X40 acpi and suspend"
date: 2004-11-23
forum: Hardware &amp; Laptops
---

### Post by boobis on 2004-11-23
Has anyone tried out [Daniel Stones](http://people.ubuntu.com/~daniels/x40/) IBM X40 ACPI packages?

I installed them on my X40, and now i can suspend to ram, but my laptop wont wake up. Or rather it wakes up, but then immediately suspends again (and turns the screen of). Nothing to do but reboot.

Has anyone got it working?

/boobis

---

### Post by daniels on 2004-11-23
[QUOTE=boobis]Has anyone tried out [Daniel Stones](http://people.ubuntu.com/~daniels/x40/) IBM X40 ACPI packages?

I installed them on my X40, and now i can suspend to ram, but my laptop wont wake up. Or rather it wakes up, but then immediately suspends again (and turns the screen of). Nothing to do but reboot.

Has anyone got it working?[/QUOTE]They work alright for me ... did you add 'acpi_sleep=s3_bios' to the kopt line in /boot/grub.conf (keeping the initial #), and run update-grub?

---

### Post by boobis on 2004-11-24
I did add the > 'acpi_sleep=s3_bios'  to my grub.conf and regenerated, so it shows up as an option to the kernel when I boot.

Two things I can think of is that I have the latest bios and embedded controller from IBM (BIOS 1.42), and I installed the generic acpi.tar.gz that I found on the Ubuntu wiki _before_ i found and installed your package.

---

### Post by boobis on 2004-11-30
Problem solved. I _think_ it had to do with me installing the acpi.tar.gz mentioned on the ubuntuwiki, because i wiped the /etc/acpi directory and reinstalled the acpi-packages, and now it actually works.

/joel

---

### Post by nburns on 2004-12-02
Anyone know if these packages (or any others) support the ibm x31?

---

### Post by boobis on 2004-12-02
[QUOTE=nburns]Anyone know if these packages (or any others) support the ibm x31?[/QUOTE]

No idea. To be honest it doesn't work for me on my x40 atm.

Upon resuming it hangs after bringing up the eth0 interface. It nevet gets around to  bring up X, or if it does it hangs before making any progress. The only thing the laptop responds to is Alt+F1-F6 which switch consoles, but if you switch to F7 where X is supposed to be it gives you a blank screen, and you cant go back (not with the usual ctrl+alt + Fx combo anyway).

How can I debug this? Anyone got experience with fixing ACPI related stuff? I'd love to help out, but I'm quite clueless in kernel/hardware debugging ...

/joel

---

### Post by castrojo on 2004-12-03
Just got my X40 today (yay!) and the packages all work for me. At first I thought it wasn't waking up, but it was just the screen locked and a blank screensaver.

Anyone have the X dock? If I plop the X40 on the dock, and then try to wake up, the docked monitor doesn't seem to want to display anything. Still messing around with it though, I'll keep trying to find some way to break it, heh.

---

### Post by boobis on 2004-12-04
Thanks for your reply Whiprush. What version of the bios and the embedded conroller do you have on your x40? I suspect my problems might be related to my bios version which is quite new (1,4x).

/boobis

---

### Post by boobis on 2004-12-05
Solved again ;) At last I think I know what's wrong. After spending some time trying to unload modules it started working when I removed the e1000 and ipw2100 modules prior to suspending. I have not done any further tests but my initial guess is that that the e1000 module is safe since all x40 share the the intel nic that uses the e1000 module, but many x40 have a different 802.11 card from Atheros, which uses some athXXX module.

So for now I just make sure the suspend.sh script unloads the modules.

/boobis

---

### Post by nburns on 2005-01-03
Ok.  I installed these packages on my x31 and everything worked great except for 1 thing.  1 little thing.

When the laptop suspends to ram, it appears that the screen is still on.  The screen is black, but still appears to be on (it is still lit up).  I have a feeling that I'm going to be wasting battery life if I leave it like this.

Does anyone else have the same problem?

---

### Post by nburns on 2005-01-12
*bump*

---

### Post by tkrag on 2005-01-21
[QUOTE=nburns]Ok.  I installed these packages on my x31 and everything worked great except for 1 thing.  1 little thing.

When the laptop suspends to ram, it appears that the screen is still on.  The screen is black, but still appears to be on (it is still lit up).  I have a feeling that I'm going to be wasting battery life if I leave it like this.

Does anyone else have the same problem?[/QUOTE]

It is a known problem, with the x31 and suspend. Luckily the solution is pretty simple. The x31 uses a Radeon graphics card, unlike the x40's intel card. You need a tool called radeontool, which I installed from a debian packlage I found here:
[ftp://debian.marlow.dk/dists/woody/laptop/pool/vga/radeontool_1.5-1_i386.deb](ftp://debian.marlow.dk/dists/woody/laptop/pool/vga/radeontool_1.5-1_i386.deb)

It works fine under Warty Warthog. 
Then you need to add the line

radeontool light off

to /etc/acpi/suspend.sh

and 
radeontool light on 

to /etc/acpi/resume.sh

I haven't tried this with the x40 ubuntu package mentioned, but have used oit successfully to suspend my x31 under mandrake. I will be testing the ubuntu x40 packages on the x31 over the next few weeks.

hope this helps

/tomas

---

### Post by nburns on 2005-02-16
Sorry for the delay, but I just got around to trying what you recommended.  It worked great!

Thanks for the help.

---

### Post by nburns on 2005-02-17
Well, I *thought* everything was working flawlessly.

I let it sit in *suspend-to-ram* mode and it drained about 80% of my battery life in about 15 hours.  From what I understand, it should've only drained about 10-15%, and certainly much less if I was suspending to disk.

Any ideas where I can look next?

---

### Post by boobis on 2005-02-20
[QUOTE=nburns]Well, I *thought* everything was working flawlessly.

I let it sit in *suspend-to-ram* mode and it drained about 80% of my battery life in about 15 hours.  From what I understand, it should've only drained about 10-15%, and certainly much less if I was suspending to disk.

Any ideas where I can look next?[/QUOTE]

I was under the impression that suspend-to-RAM drained about 5% of your battery per hour. In that case 80% in 15 hours about what you could expect.

/boobis

---

### Post by Manuel Siggen on 2005-03-15
[QUOTE=boobis]Solved again ;) At last I think I know what's wrong. After spending some time trying to unload modules it started working when I removed the e1000 and ipw2100 modules prior to suspending. I have not done any further tests but my initial guess is that that the e1000 module is safe since all x40 share the the intel nic that uses the e1000 module, but many x40 have a different 802.11 card from Atheros, which uses some athXXX module.

So for now I just make sure the suspend.sh script unloads the modules.

/boobis[/QUOTE]

Thanks ! I had the same problem  and adding 

[INDENT]
rmmod ipw2100
rmmod e1000[/INDENT] 

to suspend.sh and

[INDENT]
modprob e1000
modprob ipw2100[/INDENT] 

to resume.sh did solve the problem (as you stated) :-D

    Manuel

---

### Post by boobis on 2005-03-19
[QUOTE=Manuel Siggen]Thanks ! I had the same problem  and adding 

[INDENT]
rmmod ipw2100
rmmod e1000[/INDENT] 

to suspend.sh and

[INDENT]
modprob e1000
modprob ipw2100[/INDENT] 

to resume.sh did solve the problem (as you stated) :-D

Manuel[/QUOTE]

Technically I think you can leave the e1000 module loaded, but since the laptop IFAIK doesn't use the network when suspended it doesn't matter that much.

/J

---

### Post by daniels on 2005-03-19
If you don't unload e1000 around suspend/resume, it will just silently fail to send/receive any packets.  Making you think that the network you're on has no DHCP, and swear and hunt around for the admin, who insists it does.

---

### Post by Manuel Siggen on 2005-03-22
[QUOTE=daniels]If you don't unload e1000 around suspend/resume, it will just silently fail to send/receive any packets.  Making you think that the network you're on has no DHCP, and swear and hunt around for the admin, who insists it does.[/QUOTE]

By the way, I see that your repository on [http://people.ubuntu.com/~daniels/x40](http://people.ubuntu.com/~daniels/x40) is empty (no file at all). Is that intended ?

Thanks for your work !

Manuel

---

