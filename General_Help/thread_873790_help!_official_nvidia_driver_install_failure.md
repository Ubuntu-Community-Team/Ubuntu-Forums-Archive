---
title: "help! official nvidia driver install failure"
date: 2008-07-29
forum: General Help
---

### Post by logos34 on 2008-07-29
I am SO close to getting the NVIDIA-Linux-x86_64-173.14.05-pkg2.run driver to go in, but it fails inexplicably at the very end!
> 
[COLOR=Green][ 1226.068812] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  173.14.05 
   Mon May 19 00:03:22 PDT 2008
-> Installing both new and classic TLS OpenGL libraries.
-> Installing both new and classic TLS 32bit OpenGL libraries.
-> Install NVIDIA's 32-bit compatibility OpenGL libraries? (Answer: **Yes**)
-> Searching for conflicting X files:
-> done.
-> Searching for conflicting OpenGL files:
-> done.
-> Installing 'NVIDIA Accelerated Graphics Driver for Linux-x86_64'
   (173.14.05):
   executing: '/sbin/ldconfig'...
   executing: '/sbin/depmod -aq'...
-> done.
-> Driver file installation is complete.
-> Running post-install sanity check:
-> done.
-> Post-install sanity check passed.
-> Shared memory test passed.
-> Running runtime sanity check:[/COLOR]
[COLOR=Red]ERROR: The runtime configuration check failed for the library
      'libnvidia-tls.so.173.14.05' (expected:
       '/usr/lib32/tls/libnvidia-tls.so.1', found:
       '/usr/lib32/libnvidia-tls.so.1').  The most likely reason for this is
       that conflicting OpenGL libraries are installed in a location not
       inspected by `nvidia-installer`.  Please be sure you have uninstalled
       any third-party OpenGL and/or third-party graphics driver packages.
-> done.
-> Runtime sanity check failed.
ERROR: Installation has failed. [/COLOR] Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com]("http://www.nvidia.com").Whether i answer 'yes' nor no to 32-bit compatiblity OpenGL libraries, it still complains about 'libnvidia-tls.so.1' business.

I've tried uninstall, cleaning out the /usr/lib32 and /usr/lib32/tls of libnv* and reinstalling, but same error.  I faintly remember having a similar error way back in Suse, which I solved by creating a softlink or somethign.  But in this case it complains about the files it put there! I clean out the dirs, run the install again, get the error, then check the folders, and sure enought there are the offending files!  It creates these files 
[COLOR=Black]
[/COLOR]> [COLOR=Black]/usr/lib32/libnvidia-tls.so.1-->[/COLOR][COLOR=Black]libnvidia-tls.so.173.14.05[/COLOR]
[COLOR=Black] /usr/lib32[/COLOR][COLOR=Black]/[/COLOR][COLOR=Black]libnvidia-tls.so.173.14.05

[/COLOR][COLOR=Black]/usr/lib32/tls/libnvidia-tls.so.1[/COLOR][COLOR=Black]-->[/COLOR][COLOR=Black]libnvidia-tls.so.173.14.05[/COLOR]
[COLOR=Black] /usr/lib32[/COLOR][COLOR=Black]/tls/[/COLOR][COLOR=Black]libnvidia-tls.so.173.14.05
[/COLOR][COLOR=Black]
[/COLOR][COLOR=Black]/usr/lib/libnvidia-tls.so.1[/COLOR][COLOR=Black]-->[/COLOR][COLOR=Black]libnvidia-tls.so.173.14.05
[/COLOR][COLOR=Black] /usr/lib[/COLOR][COLOR=Black]/[/COLOR][COLOR=Red][COLOR=Black]libnvidia-tls.so.173.14.05

[/COLOR][/COLOR][COLOR=Black]/usr/lib/tls/libnvidia-tls.so.1[/COLOR][COLOR=Black]-->[/COLOR][COLOR=Black]libnvidia-tls.so.173.14.05[/COLOR]
[COLOR=Black] /usr/lib[/COLOR][COLOR=Black]/tls/[/COLOR][COLOR=Red][COLOR=Black]libnvidia-tls.so.173.14.05[/COLOR][/COLOR][COLOR=Red]

[COLOR=Black]and then throws the error.

So I'm not sure what to do here.

Any ideas?  

The kernel module refuses to even build when I tried the NVIDIA-Linux-x86_64-177.13-pkg2.run and NVIDIA-Linux-x86_64-173.14.09-pkg2.run

EnvyNG (173.14.09) goes in but I just get a blank screen at startup.  
[/COLOR][/COLOR]

---

### Post by Growbag on 2008-07-29
1. Run Synaptic and search for **nvidia**, remove any drivers that may be installed, then try again.  If you can't get into a GUI, switch to vesa mode temporarily by running:

```
sudo dpkg-reconfigure xserver-xorg
```

....keep all defaults but select **vesa** as the driver.

2. Don't try and install a 32bit driver on a 64bit OS, nasty things can happen!

3. It's definitely the correct driver for your card?  Did you check it against the "supported" list on the nvidia site?  I think you can get your card version by typing:

```
lspci
```

4. If you are adventurous, you could try installing the driver on the liveCD.  You will need a working internet connection, I would try envy, if that works  then I guess there's something odd with your install (sorry, no further advice there apart from re-install!).

Other than that, no further help here, sorry :(.

Good luck

---

### Post by logos34 on 2008-07-29
hi Growbag,

I'm running 'buntu Studio x64 8.04.  Got the right driver.

Vesa works in a pinch (what I've been using to get to my gnome desktop), but it doesn't solve the prob of why nvidia driver builds the kernel module properly, but fails the final check.

dpkg-reconfigure unfortunately has been deprecated and you can't use it on Hardy for anything beyond resetting keyboard prefs! (it was a great tool while it lasted though).  

I finally managed to restore a backup image of my /, and seem to back in business with the nvidia-glx-new.  I'm just about ready to give up trying to get the official driver to go in.  The only reason I was trying was in order to enable move to custom compiled kernel.

---

