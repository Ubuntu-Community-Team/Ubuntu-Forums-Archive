---
title: "samsung x460 doesn't boot amd64 isos but i386"
date: 2009-01-02
forum: Hardware
---

### Post by kybKenny on 2009-01-02
G'evening everybody,

for a strong 8 hours or so i'm a happy owner of a samsung x460 laptop.

the most part of this time i'm staring onto this hideous Vista-desktop that's shown to me.

This is why:

I was trying to install from the ubuntu-8.10-desktop-amd64.iso, but this computer just wouldn't boot that cd. nor would it boot from an USB-stick prepared with  [unetbootin]("http://unetbootin.sourceforge.net/") (which is by the way pretty cool).
After successfully trying to boot from an old Puppy-Linux CD, tried the mini.isos. 
And say what, my computer can boot the i386 (mini-)iso of intrepid without any complaint.

Now: why is that? the x460 sports an intel P8600, which is a Core2Duo and by that should be able to execute 64-bit code shouldn't it? :confused:

I would be very happy, if somebody could shed some light on this issue. I have 4Gigs of RAM in this machine and i'd feel bad not to be able to use them.

Your all's truly,
kybKenny

---

### Post by jabbermacy on 2009-04-07
Yes, it will run 64bit code since all their drivers have a 64bit version.  I don't have mine yet, but have you tried a different x64 disto (like kubuntu)?  Just asking since I will be installing the previous (9 beta) as soon as it's here ;)  Let me know what you tried!  thanks!

---

### Post by Barry Carroll on 2009-04-07
I have a Samsung Q210 which has a similar architecture - P8xxx CPU and the same chipset I believe.  I have not been able to boot Ubuntu live media without disabling APIC and ACPI on the kernel options line.

Once I managed to boot I found a lot of instability though.  Interestingly Vista x64 is just as buggy on my machine so I suspect it could be a general problem with Samsung BIOS code.

One example that happens in both Ubuntu x64 and Vista x64 is an instant machine reboot that happens often, but not every time, when I use the fn + arrow keys to change lcd brightness.

---

### Post by lesscode on 2009-05-24
Does it work ok with you guys now? I plan to install Ubuntu 64 bit on my laptop.
I installed Ubuntu 32 bit, and it works fine. Not sure what really gain when I am using Ubuntu 64 bit.

Please let me know. Thanks.

---

