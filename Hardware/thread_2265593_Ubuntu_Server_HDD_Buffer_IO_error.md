---
title: "Ubuntu Server HDD Buffer I/O error"
date: 2015-02-16
forum: Hardware
---

### Post by nick168 on 2015-02-16
Hey guys,

Somewhat of a noob here. I built a basic server with Ubuntu, actually this is the third time (had a Linux Oops error that I couldn't figure out how to fix on my last build, so I just wiped the drive and started over). Now I'm getting an error: "**Buffer I/O error on device sda1**". If it helps, this is the only hard drive on the server, it is the boot hard drive, and it is slightly older. The server boots up fine, with no warnings or errors, and runs fine for about 3 or 4 hours. My Apache2 and SSH server work fine for those 3 or 4 hours as well. Then I get that error, and it becomes completely unusable, and I have to hard reboot. 

I've been looking for the error log that would contain this information but I can't find it anywhere in /var/log/. 

YES... I have looked at other forums and posts about this and everyone else is saying they have this problem on bootup, or accompanied with other errors. So I figured I'd post this because I have a feeling it is something different... possibly a dead hard drive. 

I just reboot the server about 30 minutes ago, and I was stupid and forgot to take a picture of the screen with the errors. I will post that as soon as it happens again, in a few hours.

Thanks for any help you're able to give,
Nick T

---

### Post by tgalati4 on 2015-02-17
What are the SMART parameters of that drive?

```
sudo smartctl -a /dev/sda1
```

It's possible that your disk drive gets hot and starts to fail--throwing buffer I/O errors.  Usually, when you don't find log errors, there's a hardware issue that needs to be addressed.  

Check the power supply voltages with a voltmeter and check the SMART parameters of the drive to see if any errors have been logged on the disk drive itself.

---

