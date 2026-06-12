---
title: "No jack detected in Lenovo Laptop"
date: 2019-11-17
forum: Hardware
---

### Post by modernman2 on 2019-11-17
Hi, I've currently posted this in [https://answers.launchpad.net](https://answers.launchpad.net) ([https://answers.launchpad.net/ubuntu/+question/685934](https://answers.launchpad.net/ubuntu/+question/685934))
But it doesn't seems to be noticed. I will copy'n'paste my post so you will not have to click it:

Hi,
I've recently bought new laptop and installed Ubuntu 19.10 on it. Internal speakers work great, but jack output isn't recognized by the system (when I plug in my headphones the sound still goes trough internal speakers, also I can only see internal speakers in "output" section of pavucontrol). I also tried Debian sid previously to this Ubuntu with same result. Jack output is running properly on dualbooted Windows 10.


Result of alsa information script:
[http://alsa-project.org/db/?f=02a3603341a7009b2c0a69e5e6459ced8fb40784](http://alsa-project.org/db/?f=02a3603341a7009b2c0a69e5e6459ced8fb40784)


I've tried (without luck):
1. "alsa restore"
2. mesing with /usr/share/pulseaudio/alsa-mixer/paths/ (then restored to previous configuration)
3. modifying /etc/modprobe.d/alsa-base.conf (also restored after)


If you would like any other info I will try to provide it asap.


Thanks a lot!

---

### Post by Autodave on 2019-11-17
Try this: I have had it work about 50% of the time...

Power off machine. Connect headphones or speakers into the headphone jack. Power up.  Chances are that whatever you have plugged into the headphone jack will now be recognized and work properly.  Unplugging them, then, *should *cause the sound to go through internal speakers.  Pluggung headphones in again will probably cause them to function now.

I have one machine that I had to do this to twice before it worked.  That was over a year ago and it is still working properly.

---

