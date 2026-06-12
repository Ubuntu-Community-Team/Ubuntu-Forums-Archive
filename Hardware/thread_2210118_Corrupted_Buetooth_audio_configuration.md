---
title: "Corrupted Buetooth audio configuration"
date: 2014-03-09
forum: Hardware
---

### Post by launchpad-spudulike on 2014-03-09
I have managed to corrupt the configuration of my Bluetooth headset, a SBH52, and my sound settings.  I am looking for help in manually fixing these, or deleting the setting or  configuration files to a stock install level so I can start again.

Starting with the standard tools in 13.10 I had been able to use my BT21 headset as an audio device.  When I tried to configure my new SBH52 headset I could get it to pair but it would not allow me to set it as an A2DP headset.  Out of curiosity I installed the Blueman package, using the tools there I was able to connect the SBH52 headset as an A2DP headset, streaming audio for a full video.  At the end of my video I turned off the headset, at which point the system broke.

Now, even though I have a headset reported as connected, either the BT21 or SBH52, is does not appear in the sound settings menu to be selected an an output device.  The internal soundcard of the laptop works without issue.

I have uninstalled the Blueman package, but the headsets still do not appear in the sound settings menu.

I have tested the hardware against a live version of 14.04, which I downloaded last night, and all was working well - I was able to stream audio to my new SBH52 headset without issue.  Thinking this might resolve the problem, by flushing out the config files, I then went ahead and did a distribution upgrade, This did not cure the issue though.

I do not know which packages provide the default installations for audio and Bluetooth, otherwise I would have tried to re-install these in search of a fix.

Advice please on how to fix the system.

Thanks.

---

