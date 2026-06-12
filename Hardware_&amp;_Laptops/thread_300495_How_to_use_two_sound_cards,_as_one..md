---
title: "How to use two sound cards, as one."
date: 2006-11-15
forum: Hardware &amp; Laptops
---

### Post by hack124x768 on 2006-11-15
I've got a usb subwoofer and my laptop's built-in sound card. I want to use both with one stream, as in I hit play in xmms and they BOTH start playing the same thing. Ive put about 15 hours into googling the crap out of .asoundrc and have come to the conclusion that I don't like alsa much. Please prove me wrong. How should I go about making both devices act as one 2 channel device?

Thanks.

--Andrew

---

### Post by Decade on 2006-11-15
I don't think it should be done, as the laptop's sound chip and the subwoofer have different clock chips and they'll eventually go out of sync. I don't know of USB-attached subwoofers that don't come with their own satellite speakers; use those.

However, if you insist, there are hints on how it can be done.
[http://alsa.opensrc.org/index.php?page=TwoCardsAsOne](http://alsa.opensrc.org/index.php?page=TwoCardsAsOne)

---

### Post by hack124x768 on 2006-11-16
Drifting out of sync... big whoop. :) If I can manually sync them up by running xmms and mpg321 on the two different cards alright, I think it will be fine. I've tried following the two cards as one howto, although it is for making a 4 channel one out of two 2 channel ones. I just need to know how to set up up some kind of copy block in my .asoundrc or something.

About the sub not having tweeters... Its an apple isub. Note the apple part.

---

### Post by Decade on 2006-11-16
Apple didn't make the iSub. Harman Kardon did for Apple. I had forgotten about it. Now, that is quite the odd beast, so I don't know how it syncs, but it can't be normal because the documentation talks of things like hissing sounds if it's not attached directly to the Mac.

Nevertheless, documentation for turning stereo sound into surround sound is much easier to find than to turn multiple sound cards into a single device.
[http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml](http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml)
[http://alsa.opensrc.org/SurroundSound](http://alsa.opensrc.org/SurroundSound)
[http://gentoo-wiki.com/HOWTO_Surround_Sound](http://gentoo-wiki.com/HOWTO_Surround_Sound)

---

### Post by hack124x768 on 2006-11-16
Thank you so much! One of the examples from [http://gentoo-wiki.com/HOWTO_Surround_Sound](http://gentoo-wiki.com/HOWTO_Surround_Sound) (with some minor editing) works great.
Heres my new .asoundrc file (note, I DID have to restart xmms, stoping and starting again wasn't enough to reload the alsa configs)
> pcm.multi {
   type multi;
   slaves.b.pcm "hw:0,0";
   slaves.b.channels 2;
   slaves.c.pcm "hw:1,0";
   slaves.c.channels 2;
   bindings.0.slave b;
   bindings.0.channel 0;
   bindings.1.slave b;
   bindings.1.channel 1;
   bindings.2.slave c;
   bindings.2.channel 0;
   bindings.3.slave c;
   bindings.3.channel 1;
}
pcm.!dmix {
   type plug
   slave {
       pcm multi
       channels 4
   }
}
pcm.!default {
   type plug
   slave.pcm "dmix"
   slave.channels 4
   route_policy duplicate
}

---

