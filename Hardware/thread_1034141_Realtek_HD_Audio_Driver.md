---
title: "Realtek HD Audio Driver"
date: 2009-01-08
forum: Hardware
---

### Post by kennyizcool on 2009-01-08
Hello everyone. I'm kinda new to linux. I can't seem to get my audio to work. I downloaded the driver off of Realtek's site. Followed the readme, and still no fix. Google'd and searched this forum and still no fix. 

When I "sudo lshw -c multimedia" this is what I get:
       description: Audio device
       product: MCP51 High Definition Audio
       vendor: nVidia Corporation
       physical id: 10.1
       bus info: pci@0000:00:10.1
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel

The audio is an onboard RealTek ALC888 (I THINK its an 888).

I have no clue if I installed the driver wrong, or its something else.

Any help will be awesome.:D

---

### Post by blazemore on 2009-01-08
Why did you need to install the Realtek drivers?
They're included in the kernel and work out of the box in all versions of Ubuntu.

---

### Post by kennyizcool on 2009-01-08
> **blazemore said:**
> Why did you need to install the Realtek drivers?
They're included in the kernel and work out of the box in all versions of Ubuntu.

My sound did not work out of the box. :confused:

Weird....

Any suggestions?

---

### Post by clackey on 2009-01-08
> **blazemore said:**
> Why did you need to install the Realtek drivers?
They're included in the kernel and work out of the box in all versions of Ubuntu.

They may be included in the kernel, but after scouring these forums and the rest of the internet, i've noticed there have been some problems with Realtek's drivers working in Intrepid. 

I have a Realtek ALC268 sound card onboard my Toshiba Satellite L300D laptop and despite all efforts I still haven't found a way to fix its sound capture issues (low levels and major DC offset using both the built-in and external mics).

kennyizcool, maybe you could be more specific about the problems you're having with the sound card? is there simply no sound coming out or is it another issue?

---

### Post by kennyizcool on 2009-01-08
> **clackey said:**
> They may be included in the kernel, but after scouring these forums and the rest of the internet, i've noticed there have been some problems with Realtek's drivers working in Intrepid. 

I have a Realtek ALC268 sound card onboard my Toshiba Satellite L300D laptop and despite all efforts I still haven't found a way to fix its sound capture issues (low levels and major DC offset using both the built-in and external mics).

kennyizcool, maybe you could be more specific about the problems you're having with the sound card? is there simply no sound coming out or is it another issue?

Clackey, theres absolutely no sound coming out.:confused:

---

### Post by markbuntu on 2009-01-08
I have a ALC 888 sound chip on my mobo and it worked out of the box on Hardy and Intrepid so I doubt that the driver is the problem. For sound troubleshooting and configuration go here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by deth4uall on 2009-01-21
I have a Toshiba L35-S2194, not sure what the model is on it, but its built in... The problem I am having with it is that is only putting sound through jack, not through on board speakers...

---

