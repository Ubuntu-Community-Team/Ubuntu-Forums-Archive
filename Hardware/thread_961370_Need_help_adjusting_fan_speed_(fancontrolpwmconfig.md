---
title: "Need help adjusting fan speed (fancontrol/pwmconfig)"
date: 2008-10-28
forum: Hardware
---

### Post by clonek on 2008-10-28
I have a Ubuntu box setup as a firewall/router, everything works perfectly except my chipset fan runs a bit loud. Currently it's running at it's max speed of ~5100rpm. At about 4800rpm, the noise level gets much better. It seems to be stressing itself too much at 5100rpm and almost make a faint grinding type noise. 

I have lm-sensors installed and have tried using pwmconfig to setup the fan control but it hasn't work perfectly. When I enable run fancontrol, the fan speed lowers to the speed I want, but it will rev up and down between say, 4800-4950rpm even though the temperature limits I set are not near the actual temp. I tried disabling smart fan options in bios but it didn't make a difference.

Is there anyway to fix this or is there a way to just manually set the fans pwm? I don't really care much about having the fan speed lower/raise according to temperature. I'd prefer to just set it to a safe but low noise speed and have it stay constant.

Any help would be great!

---

