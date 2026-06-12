---
title: "Ekiga can't see pulseaudio"
date: 2008-08-29
forum: General Help
---

### Post by ireneshusband on 2008-08-29
I am trying to set up Ekiga in Hardy, but cannot get the sound working. I have pulseaudio running, but Ekiga can't see it and instead only offers me the hardware devices (the laptop sound card and an external audio interface) as i/o devices.

My setup is slightly unusual in that I have had to modify my /etc/asound.conf to accommodate Skype. I shall paste the contents of the file below, but the basic gist of it is that pulseaudio now runs through dmix, which also has another pair of inputs and outputs set aside for skype. However pulse is still specified as the default in asound.conf.

When I choose the internal sound card as Ekiga's audio device, the sound doesn't work, and when I try to un-zero the volume slider flicks back to zero. This is not 100% surprising. However when I specify the external audio interface the same thing happens, even though that interface is not being used by Pulse and therefore ought to be free.

Is my custom asound.conf (I pulled it off the net somewhere) at fault? Or is something else going on?

And can I just take this opportunity to say how much I am starting to loath skype? It's v4l implemantation is mangled so that all you see of me is a silhouette against a dark grey background, the audio and video quality is crap even over high bandwidth connections, and I still have 5€ of skypeout credit that I can't use because the sound quality of calls to the Belgian PSTN is below abysmal.

But I still need to use Skype so I would be very grateful if anyone could help me get all my stuff playing nicely together again.

As usual, many thanks in advance!


The asound.conf:

pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

pcm.skypeout
{
    type plug
    slave.pcm "dmix"
}
    ctl.skypeout
{
    type hw
    card 0
}
    pcm.skypein
{
    type plug
    slave.pcm "dsnoop"
}
    ctl.skypein
{
    type hw
    card 0
}

---

