---
title: "Fan control on amilo pi 2530"
date: 2013-09-01
forum: Hardware
---

### Post by manje2 on 2013-09-01
Hi guys,

I know these forums are overflowing with questions about fan control and here is mine, which I think has not been answered yet (I have searched for this a lot).

I am running a dual boot setup with ubuntu 12.04 and windows 7 on an Amilo Pi 2530 (Fujutsu Siemens). It's running great, but the fan is very annoying. At 40c it's completely quiet, but when the CPU reaches 50c, it starts to blow loudly, until it is down to 40c again and the fan is turned off. In windows, the fan is controlled much more smoothly, so I figure this should be possible in ubuntu as well (?).

I tried fancontrol, but trying to configure using pwmconfig gives the following message:

*/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed*

I'm not sure if it's related, but I also cannot see fan-speed using lm-sensors.

Also in the BIOS I cannot find a way to turn on or off software fan-control, or even anything related to fan-control (I updated to the latest version).

Does this all mean it cannot be changed, or am I missing something?

Thanks for your time!
Cheers,
Manje

---

### Post by Mark Phelps on 2013-09-03
It's not the fan that's being controlled better in Windows, it's the management of the processor speed.  Since Windows allows the processor to drop to idle, it cools down and the fan slows down.  It's a Linux kernel problem that does not provide the same level of support.

To reduce runtime temps, we used to recommend installing Jupiter -- but that has been abandoned.

Instead, you can try usinf tlp instead.

```
sudo add-apt-repository ppa:linrunner/tlp
sudo apt-get update
sudo apt-get install tlp tlp-rdw

```
```

sudo tlp start
```

---

### Post by manje2 on 2013-09-03
Hi, 

Thanks for your answer! I tried it, but unfortunately the problem is still here.

The fan blows at a bit below max speed (by the sounds of it) when the CPUs are ~50c an stops completely when hitting 40c, whereas in windows these speeds gradually decrease or increase if temperatures go up or down.

Also, the CPU gets warmer (~55c) when running windows than with Ubuntu, which I recon is a result of lower fan speeds. I would say that the argument of Ubuntu using more recourses, and thus triggering higher fan speeds, does not hold in my case. Rather it's the steps by which the fan speed is increased that differ in the two OSs.

Lastly, a bit more info: my Amilo pi has a button to lower noise (I believe also by reducing processing power - thus fan speed), but it has no effect in ubuntu.

Cheers.

---

### Post by Yellow Pasque on 2013-09-03
Laptops usually control the fan through ACPI, so they don''t work with fancontrol/lm-sensors scripts.

---

### Post by mathijs3 on 2013-09-30
I recently experienced the same problem as you on my Amilo Pi 2540. What  turned out to be the issue is that the fan you're hearing is from your  graphics chip. Because dynamic power management in the open-source  radeon drivers has not yet been enabled by default (and only recently  implemented in kernel 3.11), the fan state will be binary (either on at  highest speed or off).

To fix this, you'll need to update the kernel to 3.11 or newer and add *radeon.dpm=1 to *GRUB_CMDLINE_LINUX_DEFAULT in the file /etc/default/grub, then run 'sudo update-grub' once. My laptop runs very silent now :D

---

### Post by manje2 on 2013-10-03
Thanks, that sounds like a solution! Will try it and let you know if it's fixed.

---

### Post by mathijs3 on 2013-10-03
Forgot to mention one thing: you'll need newer firmware files too. I fixed this by installing the linux-firmware* packages  from debian, but you can also do this differently as described [here]("http://askubuntu.com/questions/324733/how-to-enable-the-radeon-dynamic-power-management-feature-in-ubuntu-13-04") in the first answer.

---

### Post by manje2 on 2013-10-04
Well, I might be a step further (now I know it's my graphics card), but it still is not working, unfortunately. I think the difference between our laptops is that my ATI card is r550, so an earlier version than r600 - which appears to be the earliest supported version - while yours might be newer. Now let's hope there will be a solution for earlier versions as well. Thanks for your help anyway!

---

