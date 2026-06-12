---
title: "AMD FX-8350 Asus M4A89TD PRO USB3 Only using 1 core"
date: 2015-05-26
forum: Hardware
---

### Post by philip10 on 2015-05-26
So I have upgraded to this CPU about a year or more ago and have only just noticed I'm actually just using 1 core in Ubuntu. At 5Ghz, it's not a bad single core machine but why not use all 8? especially moving into winter. I should point out that my MOBO does not officially support the CPU but it seems to work in Windows ok. When I first installed the cpu I had to add "nolapic" as a boot option or it would get stuck on bootup.

I have seen this thread
[http://ubuntuforums.org/showthread.php?t=2233301](http://ubuntuforums.org/showthread.php?t=2233301)

and also this thread
[http://ubuntuforums.org/showthread.php?t=2204498](http://ubuntuforums.org/showthread.php?t=2204498)

I have tried setting acpi=off, acpi=force, and unplugging all my USB devices except the mouse. Nothing I have tried has enabled the remaining 7 cores. Any other ideas?

Edit: I'm on Ubuntu 14.04

---

### Post by QIII on 2015-05-26
That CPU works just fine for me on a board that supports it.

What do you mean by it "seems" to work in Windows?

---

### Post by Yellow Pasque on 2015-05-26
Are you running the 3027 beta BIOS that supposedly adds (beta) support for the FX CPU's?

---

### Post by philip10 on 2015-05-27
I mean windows shows 8 cores in task manager.

yes, running 3027. It adds beta support for the bulldozer CPUs but not the vishera (FX-8350). I just thought I'd try it out anyway and it worked in windows.

---

### Post by QIII on 2015-05-27
One of the links you gave above deals with virtual machines.

Are you running Ubuntu bare metal in dual boot, or in a VM?

---

### Post by philip10 on 2015-05-27
dual boot. "bare metal" lol.

---

### Post by QIII on 2015-05-27
Hmmmm...

The things you have already tried are the things I'd suggest.

Do you by chance have an SD card reader that is attached to a USB header on your mobo?

(" ... on bare metal ... " would have been more appropriate.)

---

### Post by philip10 on 2015-05-27
nope.

I booted to a different ubuntu 14.04 install and it does the same thing. Just checking it's not my specific install messed up.

---

### Post by philip10 on 2015-06-02
Fixed!
  
It turns out  the problem was caused by the nolapic boot option. So how did I manage to boot ubuntu without specifying the nolapic boot option you ask?

Well I started by flipping all of those bios options I don't understand to their opposite value. That worked. So for the benefit of you readers, I then painfully exercised the process of elimination to deduce which option causes the issue.

[COLOR=#ff0000]All you need to do is disable C1E support in bios then remove the nolapic boot option from grub[/COLOR].

---

### Post by QIII on 2015-06-02
Excellent!  I will file this in my rusty trap of a mind!

Congrats!

Would you please mark this thread a solved to help others who may come along with a similar problem ... and help a grey-haired man find it later?

Thanks.

---

