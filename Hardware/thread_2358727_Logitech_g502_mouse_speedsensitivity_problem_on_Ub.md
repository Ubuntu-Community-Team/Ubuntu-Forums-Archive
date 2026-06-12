---
title: "Logitech g502 mouse speed/sensitivity problem on Ubuntu 17"
date: 2017-04-16
forum: Hardware
---

### Post by rahidz on 2017-04-16
I have a Logitech g502 mouse, on Windows it has a bunch of different profiles that control mouse speed and acceleration and all that jazz. When I switched to Ubuntu, it had none of that, so I was stuck with a jerky-moving mouse until I found a set of instructions allowing me to manually set mouse settings to fix the issue.

Instructions: [http://wiki.linuxquestions.org/wiki/Set_up_Gaming_Mouse](http://wiki.linuxquestions.org/wiki/Set_up_Gaming_Mouse)

This worked great, though I was never able to get it to work automatically on restart, so I just typed the commands in the terminal after booting up. No big.

After upgrading to the latest Ubuntu (17), this no longer works.

Specifically, typing in* xinput --set-prop 8 "Device Accel Profile" 6 *gives me an error of 

> property 'Device Accel Profile' doesn't exist, you need to specify its type and format


Any way to bypass this error and get my mouse back to normal?

Cheers!

---

