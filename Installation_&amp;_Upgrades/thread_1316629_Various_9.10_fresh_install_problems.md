---
title: "Various 9.10 fresh install problems"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by ColJep on 2009-11-06
I have two computers using Ubuntu. my main machine is an Asus P5QL-CM motherboard with Intel G43 chipset including Intel GMA4500 graphics and VT17808B 8 channel audio.

The second machine is An Asus P5N73-AM motherboard with Nvidia GeForce 7050 graphics and VIA VT1708B 8 channel audio. At the moment I am using this to test various flavours of Karmic.

Both are partitioned with separate / and /home partitions.

I am having a number of problems with both and on another I tried to run a live install on.

One thing I have found out is that Karmic does not like running via a KVM switch. I have been using this set up for years wiout problems but with Karmic it has caused problems all the way. Live installs produce either 640 x 480 or out of range resolutions on unknown monitors. Sometimes correct or 800 x 600 resolutions on recognised monitors. After installation and setup on the Nvidia drivers the next reboot goes to 640 x 480 and unknown monitor. Basically a desaster. I now have the KVM switch for the Keyboard and Mouse with the P5N73-AM feeding into the analog input and my XP machine feeding into the digital input of the monitor. This works well.

The P5Ql-CM feeds into it's own monitor on a digital input. The latest Intel video drivers are a great improvement except for the fact that in my case if the monitor has been shut down for a long time it will not wake up and I have to press the reset button to get the computer back. A short shut down after the screen saver does recover but see later.

I have been having many sound problems which seems to be a frequent problem for many people. Both machines started with no sound at all and after looking in many threads I tried Alsamixer and running Systen>Admin>System Tests on sound. This suggested I report a bug which I did and was soon advised to install some backports. I did this and soon had sound on the P5QL-CM machine but this did not last after the first short monitor shut down. I now understand the backport only works for a limited number of cases. The P5N73-AM is one of these (VIA sound) and it has sound in some places. Rhythmbox works but no Ubuntu start up intro or exit sound. Sticky keys which I rely on also has no sound.

I appreciate that there have been major changes to sound in Karmic and hope they get sorted soon. I have just found a troubleshooting procedure whch I will follow.

Has anybody any ideas about the failure to wake up after monitor shut down?

The KVM problem is also strange and probably caused problems I had with orher versions of Karmic. Especially Kubuntu and AMD64.

Generally I am very impressed with Karmic but must admit it is probably the least pleasant install yet.

---

