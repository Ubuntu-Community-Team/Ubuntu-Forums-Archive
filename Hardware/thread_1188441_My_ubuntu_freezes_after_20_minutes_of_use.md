---
title: "My ubuntu freezes after 20 minutes of use"
date: 2009-06-15
forum: Hardware
---

### Post by DieHards77 on 2009-06-15
Hello,
I run Ubuntu 9.04 and have been using Ubuntu ever since Hardy and have never had this type of problem.  I always run it with the highest level of desktop effects but about 5 days ago out of nowhere my computer froze and the screen got all staticky.  Wheni tried to move my mouse or press a button on the keyboard the screen just became fully filled with random multicolored mess.  I restarted my computer and it was fine for about 20 minutes of being idle, then I began to use it again and this happened within a minute of use.  I was using the nvidia 180 driver.

I later reformated my computer and everything was working fine for about a day and then the same exact symptoms started up again.  Sometimes my computer wont even boot without me letting it sit turned off for a while.  I have a Dell Latitude D830.

Does anyone know what might be the problem?  Also does this sound like it might be a software/driver issue or something with the hardware?

Thanks a lot for the help guys, im posting this right now while running a ubuntu live cd as it is the only thing that will work.

---

### Post by BrMBr on 2009-06-15
I had the same problem, but with a desktop. Did you check temperatures? If driver works wrongly, temperature rises and everything colapses.

---

### Post by skymera on 2009-06-15
> **DieHards77 said:**
> Hello,
I run Ubuntu 9.1 and have been using Ubuntu ever since Hardy and have never had this type of problem.  

Ubuntu 9.10 is ALPHA. So yes it WILL crash.

---

### Post by DieHards77 on 2009-06-15
> **BrMBr said:**
> I had the same problem, but with a desktop. Did you check temperatures? If driver works wrongly, temperature rises and everything colapses.

no I didnt check it Ill try to boot back into it and monitor the temperature, how did you stop it from happening to you?

---

### Post by DieHards77 on 2009-06-15
> **skymera said:**
> Ubuntu 9.10 is ALPHA. So yes it WILL crash.

I meant 9.04 my mistake

---

### Post by BrMBr on 2009-06-15
> **DieHards77 said:**
> no I didnt check it Ill try to boot back into it and monitor the temperature, how did you stop it from happening to you?

Updated MoBo drivers and everything worked fine. Really, check temps, even video processor temp.

---

### Post by pizmooz on 2009-06-15
Could be genuine hardware failure.  Have you tried another OS on the machine since this started happening.  Get a new live cd from another distro, boot to it and see if it fails.  If it doesn't compare video card driver versions from the live cd and see if you can narrow it down.

---

### Post by DieHards77 on 2009-06-15
> **pizmooz said:**
> Could be genuine hardware failure.  Have you tried another OS on the machine since this started happening.  Get a new live cd from another distro, boot to it and see if it fails.  If it doesn't compare video card driver versions from the live cd and see if you can narrow it down.

ive tried fedora and it worked fine until I hit the "enable desktop effects" button and then my screen went entirely like a peach color until i hit the space bar or any button and it would return to normal without the effects enabled.  Im going to try booting back into it and watching the temp

---

### Post by DieHards77 on 2009-06-22
> **BrMBr said:**
> Updated MoBo drivers and everything worked fine. Really, check temps, even video processor temp.

hey im still having this same problem, how did you update your MoBo drivers? I cant seem to figure out how

---

### Post by BrMBr on 2009-06-22
> **DieHards77 said:**
> hey im still having this same problem, how did you update your MoBo drivers? I cant seem to figure out how

The first thing you should consider doing is a dual boot with another OS and check how things are going to work. I really think you have a video driver issue.

If you find it's not a physical hardware issue, then you can try:

1) Installing an updated version of a proprietary driver;

2) Installing an updated version of a community driver;

3) Installing older versions of any of the above.

After all these you keep having issues, forget video effects (at least for now) :(

---

### Post by Villiam on 2009-06-22
In my computer I had this issue which I resolved by opening up the casing. Actually the processor was heating up too much. Just thought to share.

[ubuntu]("http://www.linux-archive.org/ubuntu-user/")

---

