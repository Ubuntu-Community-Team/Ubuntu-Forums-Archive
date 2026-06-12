---
title: "Audio card digital out not working [CMI8738]"
date: 2016-06-17
forum: Hardware
---

### Post by xen3 on 2016-06-17
Maybe there are some Audio card Pros here :p.

I have a 7.1 audio card with optical and coaxial digital outs (spdif). The weird thing is that although the thing has always worked in my memory, presently I am not getting any digital output and I have not been able to test it under Windows yet.

So:

Even when I select its "Digital Output" as my playback device, whereas before I would get both Digital AND Analog output using that, these days, I only get Analog output and what's more:

I have TOSLINK Optical cables that show a red glow when connected at the plugs, because the plugs are transparent. So, normally, while connecting to some toslink port, I get an immediate indicator of whether light is getting through. On all of the other toslink ports in my house, the connection always immediately establishes a glowing response.

It doesn't on this audio card. At least not any longer. I have no recollection of it.

So basically
- analog output works
- digital output no signal on both optical and coaxial.

And I have no clue what changed or when. I do not remember this thing not working under Linux.

Last time I remember it working (or must have remembered it working) was on 14.10 or something, or 14.04. Did it break? I don't know. I remember running Kubuntu back in 2015 and if that thing hadn't worked, I would have noticed because I always used that port. So I am a bit baffled here.

It is: Multimedia audio controller: C-Media Electronics Inc CMI8738/CMI8768 PCI Audio (rev 10). It is a "Theatron Agrippa", this one: [http://www.club-3d.com/index.php/products/reader.en/product/theatron-agrippa-dts-71.html](http://www.club-3d.com/index.php/products/reader.en/product/theatron-agrippa-dts-71.html). Basically, I cannot tell whether the thing is actually broken, or whether this is a Linux problem.

---

### Post by xen3 on 2016-06-19
Never mind. Alsa has the outputs muted for s/pdif and I had to enable it using Alsamixer.

[https://ckirbach.wordpress.com/2015/02/21/how-to-enable-iec958-spdif-on-cmi8738-in-ubuntu-linux/](https://ckirbach.wordpress.com/2015/02/21/how-to-enable-iec958-spdif-on-cmi8738-in-ubuntu-linux/)

I'm not sure why there is no real mixer in KDE, but there you have it.

---

