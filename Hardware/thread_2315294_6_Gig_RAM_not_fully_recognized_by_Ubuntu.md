---
title: "6 Gig RAM not fully recognized by Ubuntu"
date: 2016-02-27
forum: Hardware
---

### Post by hosie123 on 2016-02-27
Hello,
I've recently added 4 gig ram to my 2 gig machine, dual booting w windows. Windows recognizes all 6, but Ubuntu only rec 3.4 gig (see screenshot)[ATTACH=CONFIG]267542[/ATTACH]
My searches didn't turn up anything. Any ideas. Thanks in advance.

---

### Post by QIII on 2016-02-27
Hello!

Are you running a 32 bit or 64 bit version of Ubuntu?

---

### Post by tom-bellas3rd on 2016-02-27
The OS is in 32-bit mode, I would advise to backup the data and install the 64-bit version.

---

### Post by weatherman2 on 2016-02-27
PAE is a CPU feature that lets a 32-bit OS address more than 4GB of RAM.  This is typically important when trying to use more than 4GB of RAM on a 32-bit CPU.  You have a 64-bit CPU, so you could just re-install the 64-bit version of Ubuntu instead (there are other advantages to doing that too), but you might be able to force the PAE flag in your existing installation:

[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

You don't need the second "-- forcepae" for an existing installation.  Instead, just reboot and hold down the shift key while booting until you get a Grub boot screen.  Then hit e to edit the Grub options and try adding "forcepae" and then boot.  If that lets you see all 6GB, you can make the change permanent by editing the file /etc/default/grub and adding the option there (or use Grub customizer per another post) then issue the terminal command "sudo update-grub" and reboot.

---

### Post by mörgæs on 2016-02-27
Pardon my French but this is nonsense. 

PAE is only relevant for 32 bit processors so there is no need to use forcepae on this hardware. Forcepae as mentioned in the guide comes into play only for a rare breed of Pentium M processors.

With 6 GB of memory one should install a 64 bit Buntu. Even though PAE gives some advantages over a non-PAE 32 bit operative system (which hardly exist any more) each application can still only access 2 GB.

---

### Post by weatherman2 on 2016-02-27
> **mörgæs said:**
> Pardon my French but this is nonsense. 

PAE is only relevant for 32 bit processors so there is no need to use forcepae on this hardware. Forcepae as mentioned in the guide comes into play only for a rare breed of Pentium M processors.

Perhaps you misunderstood the original poster's issue.  He/she cannot access 6GB of RAM after upgrading the RAM.  Obviously he/she can re-install the 64-bit Ubuntu from scratch, and that is the cleanest approach, but that may be more work than we know.  I made a suggestion that might offer an alternative to avoid hours of work re-installing the OS.

Even modern 64-bit CPUs support PAE, not just Pentium M.  My i3-3240 does.  Curiously, when I booted a 12.04 32-bit Ubuntu installation on my i3-3240 system, it automatically detected all 16GB of RAM without any changes.  The original installation of 12.04 was done on a 32-bit CPU.  Perhaps something is different in 14.04 in regards to using PAE, but forcepae is certainly worth a try.

---

### Post by Yellow Pasque on 2016-02-27
Does Windows say all 6GB is actually addressable/usable?

> Curiously, when I booted a 12.04 32-bit Ubuntu installation on my i3-3240 system, it automatically detected all 16GB of RAM without any changes.

It probably had a newer chipset than the OP's 945 chipset. 945 chipset mobos/BIOS often don't support remapping memory above 3.2GB on 32-bit from what I've seen, even if they are theoretically capable of PAE (along with the CPU).

---

### Post by weatherman2 on 2016-02-27
I don't think the 945 chipset supports more than 4GB total RAM at all, anyway.  Curious then how the OP is able to see it in Windows...

---

### Post by mörgæs on 2016-02-27
> **weatherman2 said:**
> forcepae is certainly worth a try.

Certainly not, it only applies to the few surviving Pentium M's of the first generation. Please read my guide again to see what the option does.

---

### Post by hosie123 on 2016-02-28
Thanks for the replies. I've tried running the 64bit off a dvd and it still only recognizes 3.2 gig of RAM. Would it be different if I install it. It does appear that Bios and Windows recognized all 6.

---

### Post by Yellow Pasque on 2016-02-28
> 've tried running the 64bit off a dvd and it still only recognizes 3.2 gig of RAM. Would it be different if I install it. 
Doubtful. Your BIOS/chipset is the problem.
[https://en.wikipedia.org/wiki/3_GB_barrier](https://en.wikipedia.org/wiki/3_GB_barrier)
[https://en.wikipedia.org/wiki/PCI_hole](https://en.wikipedia.org/wiki/PCI_hole)

> It does appear that Bios and Windows recognized all 6.

The BIOS is going to report the amount of physical memory installed. It does not mean your BIOS can actually remap addresses used for hardware above the 4GB barrier.
I don't really remember how Windows reports memory, but it's probably telling you what the BIOS tells it (physically installed memory rather than how much is actually addressable). You can see the same thing in Linux with dmidecode.

---

### Post by hosie123 on 2016-03-01
Thanks for all the replies. Looks like I'm stuck w the limitations of my particular system.

---

### Post by goofprog on 2016-03-01
There was a secret to using PAE.  There used to be a video card that I know of that utilized PAE for video RAM.  I forgot what video card it was but it was bad ass using the video RAM as RAM too.  or maybe I'm going senile.

---

### Post by mörgæs on 2016-03-02
> **hosie123 said:**
> Thanks for all the replies. Looks like I'm stuck w the limitations of my particular system.

It's not only a matter of how much memory is visible, it's also about speed of computations. I still suggest that you do a fresh install of a 64 bit system, for example after some months when 16.04 is out.

---

