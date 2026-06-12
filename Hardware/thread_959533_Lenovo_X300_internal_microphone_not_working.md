---
title: "Lenovo X300 internal microphone not working"
date: 2008-10-26
forum: Hardware
---

### Post by toskala on 2008-10-26
Hi there,

I just read through all those posts that claim to have a solution on how getting that internal microphone working, but none of those solutions worked for me.

When I start alsamixer I only have the microphone-jack listed as input devices. When I hit the <tab> key there is an entry displayed with the name "Internal" which represents the internal microphone, I suppose. At least the alsa-information displayed in the top left corner say so.

However, that internal thing doesn't display any volume controls I could adjust. Hitting cursor-up doesn't turn up anything.

Anybody got any hints?

Cheers,
toskala

---

### Post by toskala on 2008-10-27
Again... solved by myself.

Here is how it works:

[LIST=1]
[*]Manually upgrade alsa-drivers to something 1.0.17 or greater. I downloaded the snapshot 1.0.18 from [www.alsa-project.org](www.alsa-project.org) but according to the changelog 1.0.17 should do the trick. ([http://www.alsa-project.org/main/index.php/Changes_v1.0.16_v1.0.17](http://www.alsa-project.org/main/index.php/Changes_v1.0.16_v1.0.17))

[*]Modify /etc/modules.d/alsa-base and load snd-hda-intel with the argument "model=thinkpad".

[*]Reboot, or reload kernel module
[/LIST]


Now start "alsamixer" and set the following:

[LIST]
[*]- Mic = Mute
[*]- Capture = CAPTUR (hitting space)
[*]- Internal = CAPTUR (hitting space)
[/LIST]

Now set Capture to some value so it's not muted (green here) and set the internal microphone boost to some value (green here).

Start audacity and record, you should hear yourself.

Hope this helps...

Cheers,
toskala

---

