---
title: "High definition audio"
date: 2009-03-20
forum: Hardware
---

### Post by kumoshk on 2009-03-20
How do I tell if my high definition audio is working? My laptop makes sound, but it doesn't sound high definition (not even on headphones, although I admit the headphones are normal headphones, but you'd think the speakers on the computer would be high definition if the soundcard is).

Here's what sudo lshw -class sound produces:
  *-multimedia            
       description: Audio device
       product: Realtek ALC1200 8-Channel High Definition Audio Codec
       vendor: nVidia Corporation
       physical id: 7
       bus info: pci@0000:00:07.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
"compaq presario cq60-212us" ubuntu

lspci gives me this for my audio:
00:07.0 Audio device: nVidia Corporation Realtek ALC1200 8-Channel High Definition Audio Codec (rev a1)

I use Ubuntu 8.10 (Intrepid Ibex)&#8212;the 32 bit version (although I have a 64 bit processor).

My laptop is a Compaq Presario CQ60-212US Notebook PC, if that helps at all.

---

### Post by kumoshk on 2009-03-20
I was right in thinking it wasn't working properly. I did some tweaking with my sound preferences (under system, preferences, sound) and changed the devices. I still don't know if it's quite high definition, but it sure sounds a lot better than before.

So, if you have any input, feel free to give it still.

---

### Post by kumoshk on 2009-03-20
> **kumoshk said:**
> I was right in thinking it wasn't working properly. I did some tweaking with my sound preferences (under system, preferences, sound) and changed the devices. I still don't know if it's quite high definition, but it sure sounds a lot better than before.

So, if you have any input, feel free to give it still.

When I test my digital alsa mixer (HDA NVidia Conexant Digital (ALSA)), no sound comes out. Is there a way to fix this? It's HDA NVidia Conexant Analog (OSS) that I was using before&#8212;if you listen carefully, some of the sound sounds a little buzzy (although it's way better than before). I'm wondering if doing this did anything, though&#8212;it might have been some other system update that did it.

Also, my sound capture for audio conferencing doesn't produce anything, either, no matter what setting it's on (except for test sound, although that doesn't even sound great). Is it supposed to produce sound?

---

