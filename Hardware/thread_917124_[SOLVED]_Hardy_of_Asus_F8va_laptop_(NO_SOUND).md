---
title: "[SOLVED] Hardy of Asus F8va laptop (NO SOUND)"
date: 2008-09-11
forum: Hardware
---

### Post by life_s_good on 2008-09-11
Alright, so about a week ago I bagan work on getting hard to run on my new Asus F8VA laptop and here is where I have done and here is where I am stuck:

To begin with this is contains some new hardware so naturally there is very little that works out of th box, and the LiveCD will not support an install. When using the Alternate CD to install the network must be disconnected or else grub will fail to install. The Asus recovery discs do not write over the MBR so if you mess up an install and attempt to reinstall on occasion the grub installation will not work and you must use the SuperGrubDisk (or whatever it is called).

After the install the wired connection must be brought up with the 'sudo ifconfig eth0 up' command. Next the ATI fgrlx driver must be downloaded and installed as the proprietary driver that came with Hardy will not work.

After the display is working the wireless card can be installed by downloading the [ath9k]("http://linuxwireless.org/en/users/Drivers/ath9k") driver.

--Need help past this point--

Next up is sound which will not work. The AC662 codec will not play over ALSA. the auto detected device is the lenovo one which does not play any audio. After playing around with it I can get SOME sound to play over OSS (mp3s and the GDM drum sound) but not everything (firefox/youtube system sounds)

Does anyone have any idea how to make everyhtign work, be it over ALSA over OSS with this laptop?!

---

### Post by life_s_good on 2008-09-12
Okay,. I upgraded to 'alsa-driver-1.0.18rc3' and in the documentation there are new models for the ALC-662/663 including alsa-mode1, 2, 3.. etc.

I put the line
'options snd-hda-intel model=asus-mode2'
in 
'/etc/modprobe.d/alsa-base'

but on bootup I run dmesg and get 
[   40.934391] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...

I am sure that the model I put in matches the new one in my alsa-configuration.

```
	ALC662/663
	  3stack-dig	3-stack (2-channel) with SPDIF
	  3stack-6ch	 3-stack (6-channel)
	  3stack-6ch-dig 3-stack (6-channel) with SPDIF
	  6stack-dig	 6-stack with SPDIF
	  lenovo-101e	 Lenovo laptop
	  eeepc-p701	ASUS Eeepc P701
	  eeepc-ep20	ASUS Eeepc EP20
	  ecs		ECS/Foxconn mobo
	  m51va		ASUS M51VA
	  g71v		ASUS G71V
	  h13		ASUS H13
	  g50v		ASUS G50V
	  asus-mode1	ASUS
	  asus-mode2	ASUS
	  asus-mode3	ASUS
	  asus-mode4	ASUS
	  asus-mode5	ASUS
	  asus-mode6	ASUS
	  auto		auto-config reading BIOS (default)
```

So on bootup it looks like alsa isn't seeing the new drivers? Can someone explain to me how I can change this? Where are the new drivers supposed to be located? Is there a way to check the directory being used on boot versus the one that the new package installed to?

Thanks!

---

### Post by life_s_good on 2008-09-12
What file contains the driver information? Maybe the new alsa drivers are bugged and the name of the device was entered wrong somewhere?

---

### Post by mgerdzhev on 2008-09-13
I'm having the same problem except I can't get any sound whatsoever out of my f8va laptop. I've played around with the model in alsa-base and nothing i have tried worked so far. Please let me know if you fix this somehow

---

### Post by life_s_good on 2008-09-13
When I got the sound working a little on OSS I started to get a bunch of errors with ALSA so I reinstalled ubuntu and now I can't make it work again. The new alsa-drivers looks like it will contain the solution for us but I can't make it work. Using asus-mode1 I get the following

```
eric@ubuntu:~$ sudo /etc/init.d/alsasound start
Starting sound driver: snd-hda-intel done
Unknown hardware: "HDA-Intel" "Realtek ALC662 rev1" "HDA:10ec0662 HDA:11c11040" "" ""
Hardware is initialized using a guess method
/usr/sbin/alsactl: set_control:1266: failed to obtain info for control #3 (No such file or directory)
/usr/sbin/alsactl: set_control:1266: failed to obtain info for control #4 (No such file or directory)
/usr/sbin/alsactl: set_control:1266: failed to obtain info for control #5 (No such file or directory)
/usr/sbin/alsactl: set_control:1266: failed to obtain info for control #6 (No such file or directory)
/usr/sbin/alsactl: set_control:1266: failed to obtain info for control #7 (No such file or directory)
/usr/sbin/alsactl: set_control:1266: failed to obtain info for control #8 (No such file or directory)
/usr/sbin/alsactl: set_control:1266: failed to obtain info for control #10 (No such file or directory)
/usr/sbin/alsactl: set_control:1266: failed to obtain info for control #11 (No such file or directory)
/usr/sbin/alsactl: set_control:1266: failed to obtain info for control #12 (No such file or directory)
/usr/sbin/alsactl: set_control:1266: failed to obtain info for control #13 (No such file or directory)
/usr/sbin/alsactl: set_control:1266: failed to obtain info for control #18 (No such file or directory)
/usr/sbin/alsactl: set_control:1266: failed to obtain info for control #19 (No such file or directory)
/usr/sbin/alsactl: set_control:1266: failed to obtain info for control #20 (No such file or directory)
Mixer configuration failed! You have to unmute your card(s)!
```

After I run that I stop getting errors if I switch around the asus mode # until I go to a non-asus mode driver

---

### Post by pjkevm on 2008-09-13
Hey, I have an Asus F6v - with alc662 aswell. This problem pertains to me as well(though i'm very new at linux) GoodLuck!

---

### Post by life_s_good on 2008-09-14
Use OSS4 for now. There is a thread about this in the multimedia forum

---

### Post by mgerdzhev on 2008-09-28
Hey guys,
I was playing today with the options again for alsa and I got my sound working :D
I edited the /etc/modprobe.d/alsa-base and added the following to the bottom of the file:
options snd-hda-intel model=m51va

Restarted and now I HAVE SOUND :)
I guess I should mention that I'm on Intrepid and I have alsa 1.0.17

---

