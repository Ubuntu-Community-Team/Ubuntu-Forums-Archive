---
title: "Nvidia 8600 Drivers broken after Upgrade to 9.04"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by raashell on 2009-05-11
I upgraded to Jaunty yesterday and have been unable to enable my NVidia 8600 graphics card.  Before I can login I get an error:

"(EE)Failed to load module "type1" (module does not exist, 0)
Failed to load module "freetype" (module does not exist, 0)
NVIDIA(0): Failed to initialize the NVIDIA kernel module!"
....more...
"(EE)Screen(s) found, but none have useable configuration."

The xserver log file shows normal opertaion up until a "Failed to initialize the NVIDIA kernel module"

The start up configuration has an interesting error:

"Error: API mismatch: the NVIDIA kernel module has version 96.43.05, but this NVIDIA driver component has version 180.53.  Please make sure that the kernel module and all NVIDIA driver components have the same version."

Previously, I had the option to select one of two drivers 180 and 173.  I selected 180, and ran nvidia-xconfig after restarting.  This did nothing to fix the problem.  I tried 173 also without success.  I uninstalled and re-installed the nvidia packages and nvidia-settings packages and ran nvidia-xconfig again without success.  I also tried installing the driver from Nvidia's site without success(after jumping through multiple hoops to even get it to go all the way through the installer).  

Now I only have one option in the driver selection area ("nvidia") and it still reproduces the same error.  It's an all around suck-fest. :)  As this is the computer that I work off of, I would very much appreciate any help.  

/*=== Edit:  I just tried using Envy to fix this.  It said that my driver (180.53) is recommended and installed but when I clicked apply, it gave me the error message, "EnvyNG has detected that the headers for your kernel are missing and cannot be installed."

Thanks,

John

---

### Post by orange-wedge on 2009-05-11
run this to install the linux headers:
[HTML]sudo apt-get install linux-headers-`uname -r`[/HTML]

---

### Post by raashell on 2009-05-11
Thanks orange-wedge.  This might be part of the problem?  It says my linux headers have no installation candidate because they're:

2.6.24-22-generic

In synaptic, when I search for them, it shows 2.6.28-11.42 as the installed version.

---

### Post by orange-wedge on 2009-05-11
> **raashell said:**
> Thanks orange-wedge.  This might be part of the problem?  It says my linux headers have no installation candidate because they're:

2.6.24-22-generic

In synaptic, when I search for them, it shows 2.6.28-11.42 as the installed version.

ok... just trying to clear this up.   what is the output of the following:
[HTML]uname -r[/HTML]

if it is 2.6.24-22 that is a pretty old kernel... i think around 8.04 time frame.

and when you say 2.6.28-11.42 is the installed version those are the headers that are already installed or is that the kernel?

---

### Post by raashell on 2009-05-11
Uname -r output 2.6.24-22-generic, but when I looked in Synaptic all the linux kernel stuff was the latest version, so no clue what is going on there.  As I mentioned earlier, because this is my workstation I really needed to get it up, so I threw some money at it and went out and bought a new hard drive and did a fresh install which fixed it.  My older drive has suffered from me putting various software on it, several different *buntu installs and a lot of stuff built from source.  I think all of this made it messy and problematic.  One of the very few complaints I have with Linux is that it's hard(*for me*) to know how to keep a system clean.  I'm never sure what libraries that are installed are needed, what the dependencies are, how to clean up a software that has been compiled from source, and etc.  Something for me to work on.  Anyways, enough rambling.  Thank you for taking the time to try and help-- it's a big forum and there are lot more people asking than giving and I appreciate it.

John

---

