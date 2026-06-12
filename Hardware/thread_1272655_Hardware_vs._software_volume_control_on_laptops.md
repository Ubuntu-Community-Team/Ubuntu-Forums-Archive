---
title: "Hardware vs. software volume control on laptops"
date: 2009-09-22
forum: Hardware
---

### Post by knowname on 2009-09-22
Hi,

I've searched around quite a bit and am frustratingly close to figuring this out, but can't get the final step. I have a ThinkPad T400 running jaunty.

There appears to be both a hardware and a software setting for the volume. I noticed that if I boot into Windows XP, I can get the speakers to play a lot louder. This is despite the fact that I have turned all the volumes up that I can find on the system (pretty much all the devices and options in "Volume Control", plus the volume on whatever program I'm using). By searching around, I found that there is a hardware volume on the ThinkPad that I can get the status of with:

```
cat /proc/acpi/ibm/volume
```

which returns

```

level:		7
mute:		off
commands:	up, down, mute
commands:	level <level> (<level> is 0-15)

```

So it seems to be that there is a volume control that is stuck at 7, and can go as high as 15. It seems from the above output that there is some command I can type to make it change: level 10, or volume 10, or something. I can't figure out what this can be.

(Note that most of what I know about this problem comes from [this thread]("http://ubuntuforums.org/showthread.php?t=966588"); however, I don't have the same problem that user was having with coupling of the hardware and software drivers.)

I would appreciate any help -- if anyone knows the commands or procedure to change that hardware volume.

---

### Post by nbotticelli on 2009-11-20
I would also like to know how to get the T400 a bit louder. This would be greatly appreciated if someone could figure this out and possibly post it on thinkwiki.org!

---

