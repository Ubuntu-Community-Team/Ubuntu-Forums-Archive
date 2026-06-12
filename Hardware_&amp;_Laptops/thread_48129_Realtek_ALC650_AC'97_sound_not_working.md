---
title: "Realtek ALC650 AC'97 sound not working"
date: 2005-07-11
forum: Hardware &amp; Laptops
---

### Post by djsimba on 2005-07-11
My Realtek ALC650 AC'97 sound is not working.

I went to Realteks website, and downloaded the driver for it.

It seems to be an alsa module.

It whined when I tried to ./configure, so I pointed it it at /usr (as it needed that to find the kernal sources).

```

root@aphex:/home/danny/realtek/alsa-driver-1.0.9rc4a # ./configure --with-kernel=/usr
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/danny/realtek/alsa-driver-1.0.9rc4a
checking cross compile... 
checking for directory with kernel source... /usr
checking for directory with kernel build... 
checking for kernel version... 2.6.0-test7
checking for GCC version... Kernel compiler:  Used compiler: gcc (GCC) 3.3.5 (Debian 1:3.3.5-8ubuntu2)

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... "yes"
configure: error: You have built-in ALSA in your kernel.


``` 

I have ALSA built in to my kernel? uh.. so?

I don't know what the problem is, if I have to rebuild my kernel just to use this damn soundcard then I'm going back to Windows, as it seems pretty damn stupid to spend hours stuffing around to get a sound card to work.  ](*,)

---

### Post by varunus on 2005-07-11
Your sound card is integrated onto your motherboard, right?  If so, it should work with Linux out of the box.  One thing that should fix your problems is the "Happy ALSA, ESD" howto in the tips and tricks section.  (I have an AC97, and it worked for me).  After doing that, all sound worked.  However, you can skip step 1 of that howto, as it is not necessary with this card.

Good luck.

---

### Post by RJARRRPCGP on 2005-07-11
>  checking for built-in ALSA... "yes"
configure: error: You have built-in ALSA in your kernel.

What is that supposed to mean?

---

### Post by varunus on 2005-07-11
What this is doing is checking for whether ALSA is compiled as a module or into the kernel source.  If you're using a stock Ubuntu kernel, then ALSA should be compiled as a module.  If you're using a custom kernel, you need to recompile.

---

### Post by djsimba on 2005-07-11
I'm using the stock ubunto kernel.

I modified the configure script so that it assumed alsa was a module, but then it gave an error saying it couldn't find the module source?

I have the kernel headers installed.

It can find the rest of the kernel though. I'm guessing it is whining because no "make modules" has been done - which I can't do unless I roll my own kernel (which I am avoiding out of laziness).

That said, it sounds like I should try that guide first. I was trying to use the realtek driver in the hope I will get surround sound, which I guess I won't get using the standard AC97 driver.

*sigh* apart from this issue I love ubuntu!

---

### Post by varunus on 2005-07-11
Hm...complains you don't have the module source?  Try installing "alsa-source" through synaptic.  Does that make the ./configure command succeed?

---

### Post by djsimba on 2005-07-12
ok, some progress.

I didn't end up compiling.

I followed that ALSA/OSS guide on here - still nothing.

Then I opened XMMS and set it to use ALSA - still nothing.

Then I went to the XMMS ALSA settings and changed Audio device from
"default"
to
"NVidia NForce2 (hw:1,0)

I now get playback in XMMS!  :) 

Nothing else can play sound though.

I'm guessing that for some reason the system thinks there is 2 sound cards, and the Nforce2 is set to the secondary? I can possibly fix this with a symlink?

Where are the ALSA devices configured? help?!?  ](*,)

---

### Post by varunus on 2005-07-12
If ALSA is detecting two sound cards, you'll need to set up a ~/.asoundrc file to force it to use the nforce sound card.  You can find more information on the file format at the ALSA home page, but I think it'll need to look something like this:

```

        pcm.!default {
	type hw:1,0
	card 0
	}

	ctl.!default {
	type hw:1,0  
	card 0
        }

```

You can create one in gedit, and save it as .asoundrc in your home folder.  Then type "sudo /etc/init.d/alsa restart" from a terminal.  You may also want to install the libesd-alsa0 package from synaptic.

---

