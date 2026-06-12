---
title: "Latest updates screwed fglrx.  ATI Drivers failing to install/update."
date: 2010-06-02
forum: Hardware
---

### Post by Shekibobo on 2010-06-02
In my most recent attempt to keep my system up to date, I ran a system update and installed all options.  Of course, I had no idea that ATI's drivers were trying to update, and that if they failed, my system is effed.  I tried the whole 'delete /usr/share/ati' solution.  No dice.  Here's what I get when I run 'sudo apt-get upgrade':

```

$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up fglrx (2:8.732-0ubuntu0sarvatt2~lucid) ...
update-initramfs: deferring update (trigger activated)
Removing old fglrx-8.732 DKMS files...

------------------------------
Deleting module version: 8.732
completely from the DKMS tree.
------------------------------
Done.
Loading new fglrx-8.732 DKMS files...
Building only for 2.6.32-22-generic
Building for architecture x86_64
Building initial module for 2.6.32-22-generic

Error! Application of patch arch_fglrx_2.6.34.patch failed.
Check /var/lib/dkms/fglrx/8.732/build/ for more information.
dpkg: error processing fglrx (--configure):
 subprocess installed post-installation script returned error exit status 6
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-22-generic
Processing triggers for python-support ...
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Same thing whether /usr/share/ati is there or not.  Then I get a crash report saying "Sorry, the package "fglrx" failed to install or upgrade.  You can help the developers fix the package by reporting the problem."  Which I'm all for.  But, when I click "Report Problem...", it pops up with a new info message: "This problem cannot be reported: This is not a genuine Ubuntu package". 

BS.

I installed 64-bit Lucid from scratch on my Toshiba Satellite L550 with an ATI Mobility Radeon HD 4570, copied important files from my old home directory stored on a flash drive, and everything was working just fine.

But of course, the major problem here is that the latest ATI update screwed my system.  Can anyone help me out here?  All the other posts on similar topics had the same solution and it's not working here.

---

### Post by freelancer1995 on 2010-06-02
i have a similar problem

```

christian@ub001:~$ sudo dpkg --configure -a
Setting up fglrx (2:8.723.1-0ubuntu3) ...

update-alternatives: error: alternative path /usr/lib/fglrx/ld.so.conf doesn't exist.
dpkg: error processing fglrx (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle

```

but, i am just trying to get it to stop upsetting the software centre, because every time, i add a package this message appears.

---

### Post by within on 2010-06-02
same problem here, got this error message after every update check:

```
E: fglrx: subprocess installed post-installation script returned error exit status 6
E: fglrx-amdcccle: dependency problems - leaving unconfigured
```

The worse is I can see my screen quality is affected: when I move the windows or click in a menu, the display is far slower and not smooth as it was before!

if anyone has an idea how to fix that...

---

### Post by within on 2010-06-02
Hi again,

I've found this subject has been SOLVED here:

[Fixing screwed fglrx]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver")

I did it and it works. I followed the more aggressive way: Need to fully remove -fglrx and reinstall -ati from scratch

the first one didn't bring me success.

By the way, after you restart, you might have a X-conf message. I just use default and then restart X option and... ta da!!!!!! it works again, with proper drivers!!!!!!!

Origanl poster of this thread should try and if it's ok, should mentioned [SOLCED] in the topic

Cheers,
within

---

### Post by freelancer1995 on 2010-06-02
not exactly a fix but...

i found that by opening "synaptic package manager" searching for fglrx, fglrx-amdcccle and fglrx-modaliases plus any other fglrx packages and setting for uninstall, quick restart... end to error messages, but effectively reduced graphical effects. :(

---

### Post by freelancer1995 on 2010-06-02
> **within said:**
> 
[Fixing screwed fglrx]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver")


yeah, that worked after two restarts and it seems i was half right removing the fglrx packages, but check your "Hardware Drivers", i have no proprietary drivers now... i wonder if that is right, or is the problem masked?

freelancer1995

---

### Post by within on 2010-06-02
@ freelancer1995:

I don't believe the problem is masked. I really see my graphical effects back to normal. I also set the Visual Effects to "Extra" and it really works smooth and fine now. That's the reason why I mentioned it as a 'Fix'.

I hope after many reboots & updates the problems will not come back. On my laptop, I don't often reboot, I like suspend mode, so I have to wait...

Cheers,
within

---

### Post by Shekibobo on 2010-06-02
I did the fix, the second, more aggressive one, and I've got my graphics back.  However, every time I restart, I have to restart X.  That's a pain.  And when I go to Administration >> Hardware Drivers, and nothing shows up at all.  And my ATI Control Panel disappeared.  

Not exactly the fix I was hoping for - it works, sort of.  But now I've got a bunch of hassles.  Any ideas?

---

### Post by within on 2010-06-03
> **Shekibobo said:**
> Not exactly the fix I was hoping for - it works, sort of.  But now I've got a bunch of hassles.  Any ideas?

I haven't restarted yet, I will see, but I believe it could be interesting to check the install of the ATI card again, as usual way...

I'll try later today or this week end.

---

### Post by within on 2010-06-03
@ Shekibobo:

I did shutdown my laptop and restart it, I did not have to restart X. Everything was back to normal.

Do you remember the options related to X you had just after having executed the commands and then did your first boot? Maybe the options you chose was not good at that time...

---

### Post by bigtony2tone on 2010-06-04
I updated fglrx through the x-updates ppa with Ubuntu Tweak.  I had the same issues as you all.  In that ppa I found ppa-purge, a great little script that I used to revert fglrx back to Ubuntu-stock.  It's worked for me twice now.

Here it is on Launchpad: [https://launchpad.net/ppa-purge](https://launchpad.net/ppa-purge)

Of course this will only help if you updated fglrx like I did.

---

### Post by bijanafx on 2010-06-04
Yes! Thanks bigtony!! Mark it solved!
Previously, I had tried the aggressive fix suggested by within, but I was in the same boat as everyone else, without the proper drivers to run compiz. I had completely forgotten about that x updates repo....

So I ran:
```
sudo aptitude install ppa-purge
sudo ppa-purge ppa:ubuntu-x-swat/x-updates
sudo aptitude install fglrx
aticonfig --initial -f
```

Then logged out, and turned the extra visual effects back on.

---

### Post by within on 2010-06-06
Hi there,

good to read this issue is properly fixed now! :popcorn:

---

### Post by Shekibobo on 2010-06-06
I haven't marked this as solved yet, because I'm still getting the warning "Ubuntu is running in low graphics mode," followed by the option screen, at which point I have to select "Restart X."  After that, my graphics are beautiful, and everything seems to be working great, but I think it's stupid that I have to go through that low graphics problem before I can get to the login screen.  

The "low graphics mode" is displaying at 1600x900 resolution, so I don't know what the problem is.

---

### Post by Shekibobo on 2010-06-28
It's been about three weeks, and this problem still hasn't gone away.  I've gone through the posted fix several times now, and every time it ends up the same.  And now, possibly related, when I log in, a message pops up that says my power manager is not responding, one of the options being to "logout anyway."

My ubuntu is just all sorts of messed up right now, and I can't figure it out.

Any other ideas?

---

### Post by Yellow Pasque on 2010-06-29
> And when I go to Administration >> Hardware Drivers, and nothing shows up at all.
You may need to log out or restart after running it, but this command should restore the ATI proprietary driver option in that GUI.
```
sudo apt-get install fglrx-modaliases
```

---

### Post by Shekibobo on 2010-06-29
> **Temüjin said:**
> You may need to log out or restart after running it, but this command should restore the ATI proprietary driver option in that GUI.
```
sudo apt-get install fglrx-modaliases
```

yeah, all that did was eliminate my desktop effects.

---

### Post by Yellow Pasque on 2010-06-29
The command doesn't actually install or touch the driver. It should have no effect on your desktop effects.

---

