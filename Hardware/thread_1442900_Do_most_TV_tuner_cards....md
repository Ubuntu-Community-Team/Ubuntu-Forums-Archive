---
title: "Do most TV tuner cards..."
date: 2010-03-30
forum: Hardware
---

### Post by Moozillaaa on 2010-03-30
...have an output for the monitor as well?

---

### Post by Moozillaaa on 2010-04-04
Anybody have recommendations here? Ideas?

---

### Post by srs5694 on 2010-04-04
No, very few TV tuner cards have TV or monitor outputs. If you want to build a DVR (MythTV or something similar), you'll need to use a computer or video card with an appropriate output for your TV. Sometimes adapters can be used, but their efficacy depends on what you're connecting to what. Post details if you need advice.

---

### Post by Moozillaaa on 2010-04-12
> **srs5694 said:**
> No, very few TV tuner cards have TV or monitor outputs. If you want to build a DVR (MythTV or something similar), you'll need to use a computer or video card with an appropriate output for your TV. Sometimes adapters can be used, but their efficacy depends on what you're connecting to what. Post details if you need advice.

Thanks for input there srs...

I'm still building a new machine.

I wasn't knowing if I'd need a separate TV tuner card, AND, a video card...

I need to bring vids IN from the satellite DVR into the computer, WITH MPEG encoding.

I bought [ this board ]("http://www.foxconnchannel.com/product/motherboards/detail_spec.aspx?ID=en-us0000402"), with these inputs:

1 x VGA port  (onboard video, I suppose)
1 x HDMI port (input? output?)
1 x DVI-D port (input & output?)

After importing 300 movie files, then I'll look into setting up PC-to-TV connection. Just wondering what hardware I'll need down the road...

---

### Post by cascade9 on 2010-04-12
> **Moozillaaa said:**
> I bought [ this board ]("http://www.foxconnchannel.com/product/motherboards/detail_spec.aspx?ID=en-us0000402"), with these inputs:

1 x VGA port  (onboard video, I suppose)
1 x HDMI port (input? output?)
1 x DVI-D port (input & output?)

After importing 300 movie files, then I'll look into setting up PC-to-TV connection. Just wondering what hardware I'll need down the road...

Those ports (VGA, HDMI, DVI-D) are all outputs from the onboard video. You wont need a video card....but its probably a good idea, the ATI hardware video decoder drivers are getting better, but still nothing on the nVidia hardware video deocder (VDPAU).

---

### Post by srs5694 on 2010-04-12
You'll need a video capture card to do your encoding. I'm not very familiar with what's currently available, so I can't offer suggestions, except this: If you plan to record HD content off of a satellite hookup, you'll need either a very expensive hacked satellite receiver with FireWire connector or a Hauppauge HD-PVR. Lots of cards will record SD content from satellite receivers, though.

Whether you'll need something else for TV output depends on your TV. If you're using an old NTSC TV, it probably won't handle any of your computer's outputs. If you're using a newer HD TV, it will probably handle at least one of those outputs you mention, but you'll need to check your TV's manual to be sure.

The VDPAU feature that cascade9 mentioned is an advanced video decoder available on most of the latest nVidia chipsets. It can offload some of the CPU load of playing back video, and some people say it produces better quality output. (I can't comment, since I've never seen its output, particularly not side-by-side with anything else.) If you put anything but the most anemic current CPU in the motherboard, chances are you won't need VDPAU to keep up with even very high-quality HD content; however, VDPAU's ability to reduce CPU load could still be useful if you want to do other things while watching video (say, transcode recordings or compile a big program).

---

### Post by Moozillaaa on 2010-04-13
Thanks again on the tips...

---

