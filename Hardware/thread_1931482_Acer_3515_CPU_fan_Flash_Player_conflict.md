---
title: "Acer 3515 CPU fan Flash Player conflict"
date: 2012-02-25
forum: Hardware
---

### Post by Gashog on 2012-02-25
I'm a total newb ok?

I've been battling the CPU fan issue with this laptop since around 9.04 ish with random success and subsequent failure.
Last night, I wiped the HD completely and installed 10.04LTS and the fan worked right from boot splash on up.
I installed Flash Aid plugin for FireFox and it switched the fan off immediately upon FireFox restart. I rebooted the laptop and there was no movement from the fan from power up to splash to log on. It was completely inop.
I ran some commands that I don't understand as per Google search: ls-temp modprobe sensors-detect sensors lm-sensors fancontrol and some others.
I was able to get an Error: Can't read configuration file in regards to lm-temp and fancontrol.

I do have the fan working now.
I typed "temperature" into the software center search box and installed a bunch of random hardware temp related packages, including a Dell utilities package.
I rebooted it and something I did fixed the fan as it works like it did before I installed the Flash Player that broke it.

I don't know if anyone is interested in chasing down what Flash Player has to do with the CPU fan on the Acer Aspire 5315 but I have it up and running right now.

---

### Post by Gashog on 2012-02-25
It's broken again.
All I did was play one YouTube video and reboot and the fan is inop.
When I reboot the laptop now, the fan idles for 10 seconds or so and then shuts off.

---

