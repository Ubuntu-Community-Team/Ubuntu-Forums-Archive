---
title: "Faulty Hard Disk?"
date: 2010-05-11
forum: Hardware
---

### Post by jhann on 2010-05-11
Hey all, 

Was wondering if you could possible lend me a hand with my laptop, I'm worried I might have a failing disk and have confused myself a little whilst testing.

I'm running 10.4 and have tried using the SMART data disk utility, it looks like theres 19 bad sectors on the disk and whenever I try to run any test It comes back with[COLOR="Red"]**FAILED(read)**[/COLOR] 

[IMG]http://usera.imagecave.com/codball/Screenshot-250%20GB%20Hard%20Disk%20%28ATA%20WDC%20WD2500BEVT-75ZCT2%29%20%E2%80%93%20SMART%20Data.png.jpg[/IMG]

I've tried using the command *sudo badblocks -v /dev/sda1* and it comes back with no bad blocks.

What would the best way to check for errors as i've susspected it's a dodgy disk for a while (dodgy noises) and just want to be sure.

When playing music every now and then rhythem box freezes and says "Cannot play from source" which makes me think disk issue aswell, if anyone has any ideas they would be appreeciated!

Thanks,
James.

---

### Post by frostschutz on 2010-05-11
You're running badblocks on a mounted partition? Wow...

Hope you have a good backup...

Either way, it's a bad disk, get a replacement.

---

### Post by khelben1979 on 2010-05-11
> **frostschutz said:**
> Either way, it's a bad disk, get a replacement.

Agreed.

[SpinRite]("http://en.wikipedia.org/wiki/Spinrite") can repair faulty sectors and hide them so they are not being used, but... as time moves on, more and more sectors will become faulty so as the previous poster mentioned: get a new disc.

---

### Post by jhann on 2010-05-11
Didn't have a clue badblocks would cause issues on a mounted filesystem, the manual for it doesn't say to unmount first - only just upgraded to 10.4 so I dont have anything on it anyway! 

Thanks for the help though guys, will look into getting a new disk.

---

### Post by amsterdamharu on 2010-05-11
I had the same on my laptop since Fedora and lucid 10, I think the program is called palimpsest and it gives faulty results (or is just more picky). Not sure if they fixed it but if one report (palimpsest).

I think I've removed the applet so the notification is not displayed again every time.

---

