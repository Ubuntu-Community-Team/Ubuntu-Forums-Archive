---
title: "&quot;Starting Ubuntu...&quot; takes 2+ minutes"
date: 2005-08-11
forum: Hardware &amp; Laptops
---

### Post by Peppone on 2005-08-11
Hi,
I've installed Ubuntu and everything seems to be working but the startup is really slow. The computer halts at "Starting Ubuntu...", it just sits there for two to two and a half minutes.
Is that normal?

My hardware
Motherboard: ASUS A7V
CPU: AMD Thunderbird 1.1GHz
IDE:
Maxtor DiamondMax 250GB <-- First cable, these are detected by the ATA100 after the bios has loaded
Western Digital Caviar 80GB <-- See above
NEC DVD+-R (will be replaced with a IBM Deskstar 120GB) <-- Second cable, detected as seconday IDE in the reguar bios startup
Western Digital 120GB <-- See above
Graphics card: Geforce MX440 128MB
TV Tuner: Terrarec CinergyTV 400 (I haven't checked if it's detected)
Soundcard: Soundblaster Live! 5.1

I suspect it's the strange ATA detection which is causing this.
I can connect two IDE cables to the moterboard and if ATA100 is disabled both are detected in the bios (primary and secondary). But if ATA 100 is enabled then the bios won't find anything on the primary and after the regular bios has loaded some ATA100 is detected where the primary is found but not the secondary..

I'm new to Linux so I don't know how to check if this is the cause.

/ Peppone

---

### Post by brim4brim on 2005-08-11
Really, really should not be that slow.  Ubuntu starts in less than half the time of windows on my laptop.

1.7GHZ
128MB ATI X600 Mobility (not detected properly)
512MB Ram

---

### Post by varunus on 2005-08-11
I believe this is ATA detection as well.  I've noticed that sometimes I get a delay at Starting Ubuntu... as well, and the computer sits for a little while before booting up.  The light on my CD drive is active during this process.

Maybe file a bug report?  Low priority though, as its more of just a nuisance...It might be a BIOS setting too that's causing the delay..

---

### Post by Peppone on 2005-08-11
Is there anyway to see what is happening 'behind the scenes' so to speak? What does Linux try to do when it says "Starting Ubuntu..."?

If it is the ATA then where should I file the bug? To Ubuntu, the kernel guys or somewhere else?

---

### Post by gb25 on 2005-08-11
[QUOTE=Peppone]Is there anyway to see what is happening 'behind the scenes' so to speak? What does Linux try to do when it says "Starting Ubuntu..."?

If it is the ATA then where should I file the bug? To Ubuntu, the kernel guys or somewhere else?[/QUOTE]
 You can edit /boot/grub/menu.lst and remove or comment out the "quiet splash" part then it will show you what's going on.   You can either edit it after it boots, or you can change it through the editor at the grub loader.  Hit escape when it's counting down and it'll give you an option to edit.

---

### Post by Peppone on 2005-08-11
Do you mean "nonaltoptions=quiet splash"? It was already commented.

When I boot it says "Uncompressing ...", then "audit( ..." and after that it says "Starting Ubuntu..." and it halts there. After around 2 minutes it continues to load things as normal with description to the left and an [ok] on the right.

---

### Post by gb25 on 2005-08-11
No, it'll be at the end of the kernel line for whatever boot entry that you choose.  Here's mine:

```

title           Ubuntu, kernel 2.6.10-5-686-smp
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.10-5-686-smp root=/dev/sda1 ro **quiet splash**
initrd          /boot/initrd.img-2.6.10-5-686-smp
savedefault
boot

```

---

### Post by Peppone on 2005-08-11
Yep, it was the IDE.

It said "IRQ probe failed" and "no response (status=0x0a), resetting drive" a couple of times for hda and hdb.

Ubuntu doesn't need to search for them there since they are found on the ATA100 somewhere somehow (I think). So, how do I disable this?

---

### Post by trigg on 2005-08-11
I think this is the bug that is causing it. I had the same problem Try building your own kernel and disabling the module as indicated in the bug report.

[https://bugzilla.ubuntu.com/show_bug.cgi?id=8899](https://bugzilla.ubuntu.com/show_bug.cgi?id=8899)

---

### Post by aveline on 2005-08-11
two options come to mind

edit grub when it boots by hitting ESC, at the bottom will be instructins on how to edit the file temporarily & pass it new/diff paramaters.  So on the kernel line try these in this order (after each fail you'll have to redit the file  b/c the changes won't stick, then when one does work, add it to the file once in ubuntu):

noacpi
nolacpi
noapic
pci=irqroute
hw-detect/start_pcmcia=false *if this is a laptop don't do this, but on one desktop i have it let me detect a NIC properly if i put this line in*

You may have to use some of those in combination too... the most common options to put together are:

noacpi noapic nolacpi ... and sometimes noapm

aveline

---

### Post by Peppone on 2005-08-11
Thanks for your help everyone!

I will build my own kernel with CONFIG_EDD disabled.

I'm a newbie and have absolutely no idea how to do it but after asking Google I ended up on [this page](https://wiki.ubuntu.com/KernelHowto). I haven't read it through yet but I suspect this is a good place to start.

If there is any way which is more easy than this, let me know or else I'll try my luck with that tutorial in the next few days.

Edit: the bugzilla page said the bug has been fixed in Breezy. How easy is it to upgrade to that one? Maybe that's an option?

---

