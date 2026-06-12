---
title: "Disabling Video Cards, and/or changing when the monitor goes to sleep?"
date: 2010-12-05
forum: Hardware
---

### Post by BlackRat90 on 2010-12-05
Hi there, I am using Ubuntu Server 10.04, and i am a bit new to the whole Unix style OS.

I was wondering if and/or where I would be able to change a setting that my monitor which I have hooked up to the server would not go to sleep as it does after about 15 minutes. So that I do not have to hit the esc key to wake up the monitor.

Also I mostly just need some advice, My server is actually an old computer of mine, that I have Ubuntu installed on, and the mother boards video chip seems to "steal" Memory away from my RAM, I have an older Video card that I believe should work on the computer, but I was wondering if any one knew a way that I could Disable my video card in my mother board, so that the card I have in the PCI port would be the only one for the computer.

I thought that both of the problems might lie in the BIOS but I could not find anything in there about them. So I am just Wondering if the OS could do anything to help my problems.

Thanks a Billion!
~Nate

---

### Post by IcarusR on 2010-12-05
You should be able to alter the monitor 'time out' in 'Power Management Preferences'
System > Preference > Power Management

As for the video card I would expect there to be an option to disable the on board video in the BIOS.
What video cards do you have ? Make & model for both would help. Also mobo details.
You should be able to 'blacklist' the driver for the on board video, which may help.
Need to identify correct driver (module) & add it to 

```
/etc/modprobe.d/blacklist.conf
```

---

### Post by BlackRat90 on 2010-12-06
Sorry for the late reply, ive been having internet problems

> You should be able to alter the monitor 'time out' in 'Power Management Preferences'
System > Preference > Power Management

Where exactly can I find the System Preference???? I dont see this in in any of the file systems...Or is this in the BIOS???

Also thanks for the tip on blacklisting the drivers, Ill look into that.

---

