---
title: "No Sound - Fujitsu Amilo 1450G - Help a good cause."
date: 2009-12-29
forum: Hardware
---

### Post by Jeconti on 2009-12-29
I'm rehabing some old computers my brother gave to me since he's moving. My plan is to give them away to low income families who just need a machine to surf and type on.

I'm having some trouble getting the sound to work on the aforementioned laptop. I've been doing some research, but the hardware is so old that most of the links are dead or outdated.

Can anyone help?

---

### Post by sparky8251 on 2009-12-29
I just solved a no audio problem myself. Type this in to a terminal:

aplay -l

And post the results.

---

### Post by Jeconti on 2009-12-29
device_list:223: no soundcards found...

---

### Post by sparky8251 on 2009-12-29
Ok. Thats what happend to me. So I downloaded the ALSA drivers source code (the first packages in the list) from here:

[http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download)

and compiled it with these commands (assuming you extracted the .tar.bz2 file to your home directory):

cd alsa-driver-1.0.22.1

./configure

make

sudo make install

Now at the "make" command if you get some errors saying that 
you need certain packages, so use "sudo apt-get install" followed by the name of the packages that it requires. Then re-type type the
commands above to compile the driver and reboot. The volume may be muted so you'll want to check that. This worked for me so hopefully it'll work for you. Have any questions just ask.

---

### Post by Jeconti on 2009-12-29
Recompiled, reinstalled, and still nothing. The system recognises no installed audio hardware. Aplay still yields no results on the soundcard.

---

### Post by sparky8251 on 2009-12-30
Try typing this into the terminal:

lspci -v

Find the audio device and paste what follows in your next post.

---

### Post by Jeconti on 2009-12-30
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
	Subsystem: Fujitsu Technology Solutions Device 10a7
	Flags: fast devsel, IRQ 16
	Memory at ffe38000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

---

### Post by sparky8251 on 2009-12-30
Sorry for the wait, but I had some trouble with my comp. Ok so according to the "lspci -v' command you have the driver for your sound card installed; It just doesn't load at boot time. You need to type this:

sudo gedit /etc/modules

Into a terminal and on create a new line at the bottom that says:

snd-hda-intel

Save the file and reboot. Your driver should now load and you should have audio.

---

### Post by Jeconti on 2009-12-30
No such luck I'm afraid. How do I force grub2 to boot in recovery mode so I can watch what happens when it tries to load the module?

---

### Post by sparky8251 on 2009-12-30
Not quite sure how to do that... but I'll look into it and you should too.

---

### Post by sparky8251 on 2009-12-30
Found a way to boot into recovery mode. In a terminal type this:

sudo apt-get install startupmanager

Then run:

sudo startupmanager

You will see an option called "Default Operating System" Change the setting to recovery mode and close the program. Reboot and you will be in recovery mode. You can use the same program to boot into the normal the operating system by changing the "Default Operating System" back to generic.

---

### Post by manco on 2009-12-30
> **Jeconti said:**
> I'm rehabing some old computers my brother gave to me since he's moving. My plan is to give them away to low income families who just need a machine to surf and type on.

I'm having some trouble getting the sound to work on the aforementioned laptop. I've been doing some research, but the hardware is so old that most of the links are dead or outdated.

Can anyone help?
I don't have a solution to your problem, but I'm having some sound issues with my PC as well.

I noticed that messing with the output on the sound preferences sometimes gave me sound.

Hope that helps

---

### Post by Jeconti on 2010-01-01
Used the startup manager to use recovery mode. It was no more revealing. I did hunt through the logs to see if they had anything to tell. kern.log is the only one with reference to the module at all. Even though /etc/modules.conf has an entry for snd-intel-hda, I can't find any evidence that it's loading, or if the module is installed in the first place.


Dec 31 15:49:42 Laptop kernel: [    7.259162] HDA Intel 0000:00:1b.0: irq 25 for MSI/MSI-X
Dec 31 15:49:42 Laptop kernel: [    7.259192] HDA Intel 0000:00:1b.0: setting latency timer to 64
Dec 31 15:49:42 Laptop kernel: [    7.288062] ALSA hda_intel.c:2571: no codecs found!
Dec 31 15:49:42 Laptop kernel: [    7.288123] HDA Intel 0000:00:1b.0: PCI INT A disabled


That's all I have at this moment.

Thanks for continuing to help. Happy New Year!

---

### Post by sparky8251 on 2010-01-03
How did the audio fail? As in was it never working or was there something you did and then it stopped working? You said these were for low income families so I presume they use dial-up modems. If so what chipset do the dial-up modems use?

---

### Post by peepingtom on 2010-01-03
I believe you can hold SHIFT to have the Grub2 selection menu pop up. By default, it won't display unless you have more than 1 kernel version installed.

Also, please tell us if sound worked when you were using a LiveCD. I don't mean to insult you :D

---

