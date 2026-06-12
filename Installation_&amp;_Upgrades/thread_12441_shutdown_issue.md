---
title: "shutdown issue"
date: 2005-01-24
forum: Installation &amp; Upgrades
---

### Post by stevetxt on 2005-01-24
I installed Ubuntu (warty) yesterday on my laptop.  Things seemed to go pretty well.  But when I shutdown, it seems to shutdown and turn off the power, but when I close the lid of the laptop it restarts.  Any ideas how I can fix this?  Should I report it as a bug?

Thanks.

Steve

---

### Post by az on 2005-01-24
There are plenty of things you can try.  Try doing
sudo modprobe apm
and shutting down.
If that works, add apm to /etc/modules
(apm needs to be enabled in your bios for this to work)

You can try adding acpi=force to your kernel line in grub`s menu.list.

You need to enter your bios to see what is supported and enabled by your machine.

---

### Post by stevetxt on 2005-01-24
Here is what I get:

skt@runt:~ $ sudo modprobe apm
Password:
FATAL: Error inserting apm (/lib/modules/2.6.8.1-3-386/kernel/arch/i386/kernel/apm.ko): No such device
skt@runt:~ $

The relevant section of /boot/grup/menu.lst, if I understand correctly, is:
title		Ubuntu, kernel 2.6.8.1-3-386 
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda6 ro quiet splash
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

Do I add a new line starting with kernel, such as

kernel        acpi='force' ?

I looked through my bios (Phoenix) and under Power found entries like

Advanced power management features:

suspend/resume switch    enabled
lid close suspend                   on
lid open resume                     on
resume on Lan                      off

This is the way it's been with Debian stable that I've been using.

Thanks,

Steve

---

### Post by stevetxt on 2005-01-24
Ok, I figured out that the acpi=force has to go in the same kernel line.  I revised my /boot/grub/menu.lst file section to look like the following:

title           Ubuntu, kernel 2.6.8.1-3-386
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda6 ro quiet splash acpi=force
initrd          /boot/initrd.img-2.6.8.1-3-386
savedefault
boot

But there is still the same problem.  I shut down, it seems to be powered off, but turns on the moment I close the lid.

Please let me know if you have any more ideas I might try.  

Thanks.

Steve

---

### Post by az on 2005-01-24
Aha!

You are successfully loading the acpi module, but your laptop uses apm. (Advanced Power Management).  You need to remove the acpi module before you can load the apm module.  One prevents the loading of the other.

If it complains about removing the module because it is in use, try booting with acpi=off.

Then you should be able to load the apm module and shut down like a real computer.

---

### Post by stevetxt on 2005-01-24
Azz,

Could you please clarify the steps for me?  I replace the acpi=force with acpi=off in the grub menu.lst, right?  Then how do I get and load apm, given that it does not seem to be there now when I try modprobe?

Thanks.

Steve

---

### Post by az on 2005-01-24
Yes.  It is not loading now because the acpi module is loaded (this is what I am assuming without seeing the output of an lsmod.
One prevents the other.  Its one or the other.

---

### Post by stevetxt on 2005-01-24
Azz,

I understand that, and I am pretty sure you are right.  I'm just asking how exactly to turn the one off and load the other, when it appears the apm module is not here in my system yet.  Do I need to get it as a package first or what?

Thanks very much.

Steve

---

### Post by Buffalo Soldier on 2005-01-25
```
sudo gedit /etc/modules
```Add **apm** at the end of the list in the file.

---

### Post by nocturn on 2005-01-25
[QUOTE=stevetxt]I installed Ubuntu (warty) yesterday on my laptop.  Things seemed to go pretty well.  But when I shutdown, it seems to shutdown and turn off the power, but when I close the lid of the laptop it restarts.  Any ideas how I can fix this?  Should I report it as a bug?

Thanks.

Steve[/QUOTE]


What laptop is it?  This can help us determine if it has ACPI or APM and if anyone else here is using it successfully.

---

### Post by stevetxt on 2005-01-25
It's a Fujitsu P2040, a three pound thing with a Transmeta processor.  I found that this problem - restarting when the lid is shut - is listed on the Ubuntu hardware support page and a bug report already filed.

I have added apm to the modules list and changed the end of the kernel line of /boot/grub/menu.lst  as follows:

title           Ubuntu, kernel 2.6.8.1-3-386
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda6 ro quiet
splash apm=on acpi=off nolapic
initrd          /boot/initrd.img-2.6.8.1-3-386
savedefault
boot

None of this has worked so far.  I still see a message on startup something like "starting advanced configuration and power integration" or whatever exactly acpi stands for, so I don't seem to be stopping it sucessfully.

Steve

---

### Post by stevetxt on 2005-01-26
Thanks everyone.  I seem to have it fixed now, in that apm is loaded, not acpi, it shuts down properly and doesn't restart when the lid is closed.  

Here is what worked:

In /boot/grub/menu.lst,
added "apm=on acpi=off noacpi" to the kernel line,
added "apm=on" to the commented line #kopt,
added "acpi=off noacpi" to the #noaltoptions line.

Added apm to /etc/modules.

Ran "update-grub"

This worked with my Fujitsu P2040.  From looking around the forums, it appears that somewhat different changes may be needed for other computers.  For me, "apci=force" did not work.  It did not work if I did not change the commented lines in menu.lst.  It did not work if I did not run update-grub, though I had thought this would happen automatically.  I added a couple of things to the hotplug blacklist file on someone's suggestion, but don't know if that made a difference in my case.

I don't know if every feature of the advanced power management is working.

Steve

---

### Post by LongTooth on 2005-01-26
I don't have a laptop but I've been closely following this thread  in the hopes I could solve my power-off problem. Would these tips also work with a desktop that won't shut off? 

On my way to work. I'll get back with some more info. Thanks.

---

### Post by az on 2005-01-26
"Would these tips also work with a desktop that won't shut off"

Yup.  However, each machine is different.  What is enabled in your bios?  What relevant messages do you see with dmesg?  lsmod?

---

