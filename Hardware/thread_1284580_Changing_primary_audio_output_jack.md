---
title: "Changing primary audio output jack?"
date: 2009-10-06
forum: Hardware
---

### Post by Grimhound on 2009-10-06
I have an issue where my desktop has a damaged primary audio jack, and so I have to use one of the others repurposed as the primary. Windows Vista and 7 have this option available with relative ease with the Realtek sound manager(?), but I was curious if there was any way to repurpose one of the 4 other audio jacks on my motherboard to act as the primary audio out for Ubuntu.

Basically: Instead of Green Jack (broken) being the main audio out, I want Gray Jack (not broken) to be the main audio out.

---

### Post by markbuntu on 2009-10-07
If you are wanting to move the sound from the jack fro the front speakers to the rear speaker jack you can use the pulsaudio module module-remap-sink. You can add a line to do that in the etc/pulse/default.pa file

This is from the pulseaudio wiki which will give you an idea how to do it.

> 
module-remap-sink ¶

Since 0.9.7. This allows one to route streams' channels to arbitrary channels in a sink, for example to route stereo streams to rear channels. One common use case is to use one surround sound card as multiple virtual stereo cards.

In order to configure the remapped sink, you'll have to decide two things: what channels the new sink will accept, and where each of them will be relayed to.

    sink_name

        The name for the new virtual sink.

    master

        The name of the sink of which channels you're remapping.

    channels

        Channel count of the new sink.

    channel_map

        List of the channels that this sink will accept.

    master_channel_map

        The channels in the master sink, where the channels listed in channel_map will be relayed to. channel_map and master_channel_map must have equal number of channels listed, because the channels will be mapped based on their position in the list, i.e. the first channel in channel_map will be relayed to the first channel in master_channel_map and so on.

    remix

        Allow remixing of the mono or stereo streams to multiple channels (default is yes; set to "no" if you don't want the stereo stream to be up-mixed to all channels except subwoofer and channels named aux0-aux15).

An example to split a surround sound card to two stereo devices (remember to disable automatic device configuration first, by commenting out module-hal-detect and module-detect):

# Use aux channels so that the channels won't be used for anything
# else than the rear_stereo sink.
load-module module-alsa-sink sink_name=front_stereo device=hw:0 channels=4 channel_map=front-left,front-right,aux0,aux1

load-module module-remap-sink sink_name=rear_stereo master=front_stereo channels=2 master_channel_map=aux0,aux1 channel_map=front-left,front-right


---

