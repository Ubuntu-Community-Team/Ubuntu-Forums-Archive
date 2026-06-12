---
title: "Avantree/VMware Workstation/Sound"
date: 2023-06-27
forum: Hardware
---

### Post by stamper-brian on 2023-06-27
Might be a long shot here given all the parts in play but I have a couple of Avantree USB Bluetooth adapters (leaf and DG80).  I pair a couple of headsets with them.  In windows as an OS I can then connect the USB devices to a windows VM I use for some work and the headset works in the VM. Now that I've switched my base OS from windows to Ubuntu I'm trying to perform the same.  What I'm finding is that it "appears" Ubuntu is picking these devices up as actual soundcards rather than USB devices to some degree.  When in Ubuntu I can use Pulse or the settings to configure them as my sound device and it works just fine.  However, when I go to connect these to the VMWare workstation VM like I did in windows they don't show there at all.  They do however show up as options to set the sound card of the VM.  

If I choose to use it as the soundcard "ALSA: Avantree DG80" for the VM on bootup of the VM I get "The specified device is claimed by another driver (snd-usb-audio) on the host operating system.  The device might be in use. To continue, the device will first be disconnected from its current driver".  I've tried blacklisting the device etc. but no matter what I don't get anything out of the VM OS when booted. 

In addition I have a Jabra Speak 810 that is plugged in via USB too and that oddly enough shows up as a USB device I can connect to the VM and it works just fine.  

I guess my end goal is any ideas that would let me get the Avantree device to work in the VM (I like to walk around when I'm on calls).

---

