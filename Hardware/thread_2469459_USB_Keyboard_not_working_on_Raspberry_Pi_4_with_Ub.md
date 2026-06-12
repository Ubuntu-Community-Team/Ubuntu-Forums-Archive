---
title: "USB Keyboard not working on Raspberry Pi 4 with Ubuntu 18.04"
date: 2021-11-30
forum: Hardware
---

### Post by jherzfel on 2021-11-30
Hello,

I am trying to setup a Raspberry Pi 4 with Ubuntu 18.04 for a robotics  project, though I am not able to login as the connected USB keyboard is  not working and seems not even powered as none of the LEDs is on.

The problem must be a software issue because:
- I read that there are quite a few problems concerning power supply  with keyboards though I use a Logitech K120 which is on the list of  keyboards that work and a colleague also used this exact keyboard with  another Raspberry Pi. On my Laptop the keyboard is working as well.
- I tried flashing Ubuntu 21.10 on the same Raspberry Pi and the keyboard works without problems.
- I get a "Failed to start Load Kernel Modules" during startup

What I tried:
- I tried connecting the keyboard to all USB ports and rebooting
- I tried flashing the image multiple times
- I also tried adding "total_mem=3072" to the usercfg.txt as suggested here: [https://ubuntu.com/blog/roadmap-for-off ... berry-pi-4]("https://ubuntu.com/blog/roadmap-for-official-support-for-the-raspberry-pi-4") (Even though in the Ubuntu image that I flash the file is not in /boot/firmware/ as described but in a system_boot partition)

Does any of you have another idea what could be the problem and how I can get it to work? I am thankful for any ideas!
For context, I am trying to flash this ROS Melodic image on the Raspberry Pi
[https://emanual.robotis.com/docs/en/pla ... sbc_setup/]("https://emanual.robotis.com/docs/en/platform/turtlebot3/sbc_setup/")

---

