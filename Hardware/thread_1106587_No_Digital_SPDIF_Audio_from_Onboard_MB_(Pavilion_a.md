---
title: "No Digital SPDIF Audio from Onboard MB (Pavilion a6000)"
date: 2009-03-25
forum: Hardware
---

### Post by cssetti on 2009-03-25
Hello All!

Long time lurker (big linux fan, albeit a big newb)

Anyway, I have an old HP pavilion a6000 that i rarely ever used (ran vista 32 bit pre sp1) vista crapped its pants (partition is now all screwed up, but thats another story all together!). I am running an older bios firmware on the computer (5.04) and can't upgrade it to 5.13 because i can't get into vista!

So that being said, this sucker has an asus m2n68-la motherboard. It has onboard SPDIF. I have a relatively fresh copy of intrepid ibex running on this machine (32bit install i believe for compatibility sake)

Anyway, i have tried the ubuntu documentation for sound troubleshooting, and here are the results of the output from "lspci -v | less"

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
        Subsystem: Hewlett-Packard Company Device 2a58
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

My question is how the heck do i get digital audio out??

I tried alsamixer and tried to select the audio output for the SPDIF but i can't access it, the only two options i have are master and capture.

I have searched the forums, and searched the net but can't find anything for my mb and my symptoms.

Suggestions? :confused:

Thanks!!

---

### Post by m_duck on 2009-03-25
Try double clicking the volume icon up in the top right to open the mixer. From there open preferences (Edit -> Prefences) and find and check the entry for IEC958. Close the preferences window and then find the new IEC958 entry and tick it. Then the digital out should work.

Sorry the instructions are a bit all over the place, I've not got a linux box in front of me at the moment so take this with a pinch of salt. It should be something like I said though.

---

### Post by cssetti on 2009-03-26
Thank you! that helped!

Shame this forum doesn't have a Thanks! counter

---

### Post by m_duck on 2009-03-26
Glad it was useful! It used to have a thanks function but was removed a while back because it made the forums unstable or something. I think the general way is adding "solved" as a tag for the time being...

---

### Post by cssetti on 2009-03-26
> **m_duck said:**
> Glad it was useful! It used to have a thanks function but was removed a while back because it made the forums unstable or something. I think the general way is adding "solved" as a tag for the time being...

Cool, thanks for the info!

---

