---
title: "hardw problem with ubuntu 8.04"
date: 2009-09-13
forum: Hardware
---

### Post by jagrock on 2009-09-13
Hi ubuntu users

I have an acer 4535 laptop and i am running ubuntu 8.04 because the performance its much better than ubuntu 9.04 and also it is LTS! =). My problem is with the sound.

The sound driver is not working or something like that, but lspci shows this:

javier@one:~$ lspci | grep Audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller

The sound card chip is an Realtek ALC888.

I don't know what to do.

Please help!

---

### Post by thegreatsnafu on 2009-09-13
Hi,

Did you check the "Hardware Drivers" control panel for a driver?

---

### Post by jagrock on 2009-09-13
Yes, i have activated the graphics ati driver


> **thegreatsnafu said:**
> Hi,

Did you check the "Hardware Drivers" control panel for a driver?

---

### Post by thegreatsnafu on 2009-09-13
Did you check for a sound driver? (You might want to check the repos in synaptic for a driver...)

---

### Post by jagrock on 2009-09-14
Me again.

The problem persist, i have more details... In the system when i open audacious or other player this works fine, the player works, the problem is that i can't hear anything by the speakers and the headphones.

---

### Post by thegreatsnafu on 2009-09-15
Ok, this might solve your problem:


[LIST=1]
[*]Go to "System" -> "Preferences" -> "Sound".
[*]Select different options from the "Sound Playback" menu and click test for each one.
[*]When (and if) you find one that works, then your problem's solved!:)
[/LIST]

---

