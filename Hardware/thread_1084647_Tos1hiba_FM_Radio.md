---
title: "Tos1hiba FM Radio"
date: 2009-03-02
forum: Hardware
---

### Post by dimothy10 on 2009-03-02
Have installed Ubuntu on my toshiba A305-S6861 and have been more than chuffed with it all.  Under Vista I had access to an FM tuner built in to the laptop.  Was wondering if anyone knew of a generic linux driver that might be available for this type of hardware?  or indeed should i remove the aerial and store it for, heaven forbid, the day i move back to vista lol.

thanks

---

### Post by fabricator4 on 2009-04-08
> **dimothy10 said:**
> Have installed Ubuntu on my toshiba A305-S6861 and have been more than chuffed with it all.  Under Vista I had access to an FM tuner built in to the laptop.  Was wondering if anyone knew of a generic linux driver that might be available for this type of hardware?  or indeed should i remove the aerial and store it for, heaven forbid, the day i move back to vista lol.

thanks

I'd like to find the answer to this question also. I have a Toshiba A300. My understanding is that the drivers should be loaded and the tuner should appear as /dev/radio0 or similar.  However loading Gnomeradio results in the message that it can't communicate with the radio which makes sense since there's no /dev/radio in the system. As far as I can find out, video4linux (is supposed to) provides the support required to recognise the hardware.

At this point it gets a little hard as I can't find video4linux in the synaptic package manager, however some of the related libraries etc appear to be already installed.  Searching the forums seems to bring up very little information on configuring video4linux if it is not recognising an fm tuner.

You might be more lucky than me: if you check your filesystem and find /dev/radio0 then you're practically laughing.  Make sure you have read access to it, and load Gnomeradio.

Chris.

---

