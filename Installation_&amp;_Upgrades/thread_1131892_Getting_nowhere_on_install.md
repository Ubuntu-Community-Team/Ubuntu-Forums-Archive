---
title: "Getting nowhere on install"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by lactosedave on 2009-04-21
I'm getting nowhere on installation.  Got the latest version, burned it to a disk, rebooted and select install.  Then I get the Ubuntu logo but after a while it breaks up or skews the logo, the disk no longer runs and nothing happens.  I downloaded twice and burned two disks and keep getting this result.

---

### Post by Sef on 2009-04-21
What happens if you use the Live CD?  Does it work? Are there problems?

---

### Post by lactosedave on 2009-04-21
LiveCD does the same thing.  The "working bar" fragments around the screen and eventually freezes.

---

### Post by lactosedave on 2009-04-21
also my hibernate option is gone in vista.

---

### Post by apparle on 2009-04-21
Live CD should not do anything to the vista or any HDD.

What's the computer configuration.

When the progress bar fragments and freezes.....give it some time (a lot of time around 30min).After that maybe it should continue. Booting from live CD is a slow process.
If it doesn't work then try alternate CD

---

### Post by tamas305 on 2009-04-21
Is the blinking bar at the top left of the screen visible? If it is it may be just very slow and you would have to wait about ten minutes or so for it to finish. This is not, however, a normal thing and should only happen once.

-tamas

---

### Post by lactosedave on 2009-04-21
ok, I'm going to try again.  I'll give it a couple of hours.

---

### Post by lactosedave on 2009-04-21
This is all I get, you can hear the disk running until it freezes after about 5 minutes and then nothing.  Result is the same for Live CD and install.

[IMG]http://lactoselactose.com/images/ubuntu.JPG[/IMG]

---

### Post by cariboo on 2009-04-21
I would suggest starting in safe graphics mode, at the menu press F4 and select safe graphics mode from the menu then try to boot.

Jim

---

### Post by lactosedave on 2009-04-21
Tried that.  It ran for a long time, eventually it got to a command prompt, after a hour or so. I got confused.  I believe that is when it took away my Vista hibernate option.

---

### Post by cubeist on 2009-04-21
> **lactosedave said:**
> Tried that.  It ran for a long time, eventually it got to a command prompt, after a hour or so. I got confused.  I believe that is when it took away my Vista hibernate option.

100% impossible, live cd does not write to the hard drive... runs in ram.

Can you provide us with some specs of your hardware?  Brand, processor, video card, ram, etc...

---

### Post by lactosedave on 2009-04-21
that was an install in safe graphics mode.  I should have been more clear.

Computer is a Gateway laptop
1.6 Ghz Pentium
1 gig RAM
unsure on the video card

---

### Post by cubeist on 2009-04-21
Even in the install mode, if you have not reached the partitioner, then no files have been written, thus Vista should be *completely* untouched. Anyway, two ideas...

1.
Are you trying to install a 64-bit OS on a 32 Bit computer?

2.
Try these boot options:
noapic nolapic noapci nosmp noirqpoll

---

### Post by lactosedave on 2009-04-21
ubuntu 8.10

here where I got in the latest attempt.

[IMG]http://lactoselactose.com/images/ubuntu1.JPG[/IMG]

[IMG]http://lactoselactose.com/images/ubuntu2.JPG[/IMG]

[IMG]http://lactoselactose.com/images/ubuntu3.JPG[/IMG]

---

### Post by lactosedave on 2009-04-21
In the latest LiveCD attempt, I tried some of these options. noapic nolapic noapci I believe.  Didn't see the other two.  I think I got farther than before. The progress bar actually filled up rather than just bouncing/disintegrating.  Then the screen went blank and now the capslock light and some other suitcase light are flashing on the keyboard.  I think it may have a bad fuel pump.

---

### Post by lactosedave on 2009-04-21
More attempts:

[IMG]http://lactoselactose.com/images/ubuntu4.JPG[/IMG]

[IMG]http://lactoselactose.com/images/ubuntu5.JPG[/IMG]

---

### Post by lactosedave on 2009-04-21
This flashes breiflyeach time I try to install.  It seems I have some sort of BIOS problem.  Does anyone know how to fix this.

[IMG]http://lactoselactose.com/images/ubuntu6.JPG[/IMG]

---

### Post by cubeist on 2009-04-21
thanks for posting that

this boot option should turn off that pnpbios

```
pnpbios=off
```

try this first, and then some of the other boot options as well, which help with older hardware.

---

### Post by lactosedave on 2009-04-21
I typed line in the boot options, that same screen flashed before trying to run the live CD. I did manage to make it to a tan screen with a frozen mouse cursor.  That feels like progress or at least the postponement of failure.

---

### Post by lactosedave on 2009-04-21
holy Pete! I think it's working Cubeist!  Let's explore this fella.  I feel like I've just landed on the Martian surface.

---

### Post by lisati on 2009-04-21
> **lactosedave said:**
> This is all I get, you can hear the disk running until it freezes after about 5 minutes and then nothing.  Result is the same for Live CD and install.

[IMG]http://lactoselactose.com/images/ubuntu.JPG[/IMG]

I've had similar "fragmentation" of the screen on one machine. I'd suspect that amongst other things, the CD is choosing the "wrong" graphics mode. On the machine I've had this effect on, the install process works, but when booting the freshly installed Ubuntu the monitor complains about "signal out of range" when the progress bar would normally be displayed. The workaround I've done for this machine is to disable the splash screen in grub's menu.lst file. There are other options as well, some of which will involve researching the proper graphics settings.

---

### Post by cubeist on 2009-04-21
The very first time I installed ubuntu on a laptop (years and years ago) I had the same experience as you... there is always some combo of commands that will get things going, it just takes a lot of trial and error.

---

