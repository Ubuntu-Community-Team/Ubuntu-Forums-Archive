---
title: "KUBUNTU 7.05 with 2.6.20-16-generic kernel on Thinkpad 600E running 4 times faster"
date: 2008-09-27
forum: Hardware
---

### Post by AndrzejL on 2008-09-27
Hello Everyone!

My name is Andrew and I am addicted... Ooops wrong meeting :) or maybe not as I am PC addict as well...

I own IBM ThinkPad 600E that I have purchased recently. Its an old and slow machine so I was not sure will it run unix-like OS. It does. I have tried all of mine linux install and I have found out that sound and graphic are known and common problem on this machine. PCLOS 2008 MiniMe, Backtrack II and III beta, etc. etc. all of them were very ¨quiet¨ distros. I read many threads on many forums and I have found out that the biggest percentage of solved cases on this machine is with Ubuntu Kubuntu and Xubuntu. I have decided to use Ubuntu in 7.04 or 7.10 that I have in my stack of cds. No way. Boots up with errors and I have read plenty of ¨how tos¨ but still no go. I cant download the text mode installer as I am using very weird internet connection which is preety expensive while downloading a lot of data. I have tried my KUbuntu 7.05 and BINGO. It works. No sound and sluggish graphics were not a problem since I have found this thread [http://www.thinkwiki.org/wiki/Instal..._ThinkPad_600E](http://www.thinkwiki.org/wiki/Instal..._ThinkPad_600E) But then I have rebooted the system and was testing my sound and it seems not only that my 330 MHz 128 MB ram machine can play a sound but it plays it very fast . Maybe even too fast for me. The effect is similiar to an old tape players that someone switched to double speed playback. 2 minutes of a song played in 30 seconds . New world record :P? And then I have realised that this is not only case with sound. When I am typing a command sudo it can look like sssssuuudddddddooooo as my keyboard is trying to beat the world speed record as well. My clock is doing the same thing. 1 normal minute in this world lasts for 60 seconds. Clock on my TP is gone mad as 1 minute = 15 seconds there. I have been testing it with stopwatch.

I am using KUbuntu 7.05 with 2.6.20-17-generic kernel. Tested with uname -r command

The machine is IBM ThinkPad 600E 330 MHz 128 MB Neomagic graphics and problematic sound card

Internet connection? Prepaid Nokia N73 in Irish [www.three.ie]("http://www.three.ie") network connected via USB and dialed by kppp with 1GB for 10euro addons.

Steps to recreate problem?

1) [http://www.thinkwiki.org/wiki/Instal..._ThinkPad_600E](http://www.thinkwiki.org/wiki/Instal..._ThinkPad_600E)
2) Downloading full upgrade (173 updates) via Adept Manager

Does anybody knows how to fix this problem?

Please do not hasitate to ask any additional questions.

Thank you in advance

Andy

Btw [http://ubuntuforums.org/showthread.php?t=75281](http://ubuntuforums.org/showthread.php?t=75281) this doesnt work for me.

Btw 2: Now after each reboot kDessktop keeps crashing with 2 nasty popup windows

EDIT: 

Hi Lads.

I started thinking and trying different options and figured that I was the one that have messed up the previous installation. This time I have skipped 2 things from the instructions as I suspected that they might cause trouble. 


First one was this as my sound is automatically activated.

¨    Note: On some laptops (at least on mine), the sound devices are not automatically activated, even with BIOS quick boot disabled. This may be a result of using APM instead of ACPI. See the Problem with broken sound on some ThinkPads for more info. Adding the following script (not thoroughly tested!) to /etc/rc.local should enable them: 

# activate devices (Thinkpad boots with devices disabled unless "fast boot" is turned off)
# Try the ACPI method first, then if it fails, use APM method.

   {echo 'activate' > /sys/devices/pnp0/00:05/resources} || setpnp 0x0e on
   {echo 'activate' > /sys/devices/pnp0/00:06/resources} || setpnp 0x0f on

# Now that devices are active, use modprobe to load the drivers.
modprobe snd-cs4236

# You may need to load these modules here instead of in /etc/modules.
# modprobe snd-pcm-oss
# modprobe vvsnd-mixer-oss
# modprobe snd-seq-oss

exit 0¨

and this part as my battery is lasting for 3 mins and I am using laptop on the ACDC adapter all the time.

¨  Power Settings

acpi needed to be disabled, need to use apm.

nano -w /etc/modprobe.d/power

add the following bit of code to the new file:

options apm power_off=1 realmode_power_off=1¨


And my machine flies it!!! DVD, avi, mp4 mp3 k3b cia fbi kgb You name it its running it :D

Thank You again for all Your help and God bless thinkwiki www.

Good Luck

Andy

I will check the system after the full upgrade finishes as I dont know will some of the updates not make a mess of my OS :).

The system is up and running after updates :)

---

