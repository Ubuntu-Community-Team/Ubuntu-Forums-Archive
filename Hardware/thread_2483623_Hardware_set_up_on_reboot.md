---
title: "Hardware set up on reboot"
date: 2023-02-04
forum: Hardware
---

### Post by vbcoen on 2023-02-04
On my in lounge Media TV recorder system and having installed 22.04.1  on a system previously running 20.2.1 with Mythtv possibly as Xubuntu with Xfce (it came from mythubuntu updated,, the sound is not working. 

This  is an issue I had with the previous version but it did offer more than  one than one hardware offering, and the new one does not just one and  that does not work via the sound settings. 

How do I examine the H/w found and or add extra drivers after a system  examination etc.

 
The system is connected to a TV via hdmi cable that also carries  sound. 

The sound o/p from the mobo goes to headphones via a multi way to allow  for 3 different inputs to 2 different headphones setups, plus one  hearing aid bluetooth transmitter.

 It is therefore important that I can get sound via the hdmi cable  into the TV and the sound socket on the mobo (gigabyte) as they are  doing two different jobs / tasks including out for the tv speaker and no  - normally that is turned off as both wife and self are hard of hearing  so use head phones (wife) and me hearing aid or different make of  headphones - hence the need for the extra outputs.

 I tried to find additional packages via the repo manager but with no  success - mind you it would help if I knew what I was looking for.

 
When I installed 22.04.1 I used a monitor instead of the TV as my wife was watching it.
After rebooting and connecting the TV again, the system cannot work out that there is a TV now connected as the resolution is down on the floor how do I set it up as ubuntu does not do a new hardware check on bootup.

I do have another system which is my main work horse but that runs  Mageia v8 KDE X64 and acts as a development, bbs and server system and have  run that for well over twenty years upgrading the distro version over  the years when needed after the new version has been out 3 - 6 months -  to wring the bugs out. I have got too old to try and sort these issues  out !

---

### Post by yancek on 2023-02-05
I've always had better luck with HDMI by turning on the TV first with the HDMI cable connected then turning on and booting the computer.  Have you tried that?  With the computer booted and the HDMI cable cconnected, have you gone to Settings, Sound and checked the options for "Output"?  Do you see multiple options?

---

### Post by ajgreeny on 2023-02-05
Have you made sure that the HDMI is active in the right hand tab of your sound setup from opening pulseaudio-volume-control.

Mine shows about 9 or 10 different HDMI outputs available, only one of which I enable, ie, 2 chanel stereo, as that is the hardware I have.
Check that you have an  HDMI chanel enabled there or you will get nothing.

---

### Post by vbcoen on 2023-02-16
The TV is usually on when the media system is turned on but NO mostly as if I have shut it down before going to bed it will boot around 18:20 each evening.

When installing and setting up 22.04 the TV was on at all times - otherwise I have no computer screen.

If I reboot (while TV on) there is no difference to available sound options.

---

