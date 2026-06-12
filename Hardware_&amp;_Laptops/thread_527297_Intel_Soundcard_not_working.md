---
title: "Intel Soundcard not working"
date: 2007-08-16
forum: Hardware &amp; Laptops
---

### Post by bigH on 2007-08-16
Hi

I hope someone can help me here I have tried all the forums, wikis and tweaks I can find but nothing seems to work.

I have 7.04 loaded on an old Fujitsu/Siemens Scenic 100.  Everything fine except no sound just the speaker icon with a "No Entry" symbol.  If I click on the speaker I get this error message:
[COLOR="Silver"]
"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu."[/COLOR]

I know my soundcard is installed because typing >sudo lshw -class sound gives:

  *-multimedia UNCLAIMED  
       description: Multimedia audio controller
       product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@00:1f.5
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: ioport:2400-24ff ioport:2000-203f iomemory:d0080c00-d0080dff iomemory:d0080800-d00808ff irq:20

IDEAS?
bigH

---

### Post by bigH on 2007-09-06
3 weeks & no response, but never mind because I finally figured it out myself.  So, in case it helps someone else here's how I fixed it:

I mainly followed the instructions here [https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28sound%29](https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28sound%29)

But digging in the Alsa website & forums I found I found out that my machine needed the intel8x0 module instead of snd-hda-intel so replace

cd alsa-driver-1.0.14
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install

with

cd alsa-driver-1.0.14
sudo ./configure --with-cards=intel8x0 --with-sequencer=yes
sudo make
sudo make install

Then when you edit the file /etc/modprobe.d/alsa-base add the following to the end:

options snd-intel8x0 ac97_quirk=1 xbox=1

This should load the correct module and options when you reboot.  Don't forget that you need to run alsamixer and unmute the speakers the first time.

Hope this helps.

---

