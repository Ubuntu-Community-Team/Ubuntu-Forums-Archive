---
title: "Video/Game capture advice needed for Ubuntu 15.04"
date: 2015-10-10
forum: Hardware
---

### Post by dangoo87 on 2015-10-10
Hello All,

I am a recent adopter of Linux and things are going relatively well,  however I am having some issues with capturing video footage from my  home consoles and I thought I would come here and seek some advice.


  First of all I am trying to obtain footage through HDMI (Wii U) and  RGB (Everything before hand). I have an Elgato video capture device for  the HDMI console but there is absolutely no linux support for this from  the manufacturer and the community development for a driver is in the  "experimental" stage, so I would rather not use this. 

For the RGB side I  currently have an eZcap model 116, this captures video fine but the  sound doesn't work at all!


  ***Could someone point me in the right direction of video capture  devices that 100% work with linux and captures good quality audio and  video for HDMI and RGB?***

Many thanks

Daniel

---

### Post by TheFu on 2015-10-10
Don't know what "rgb" is.

For HDMI stuff, I use a standalone device - [http://www.amazon.com/AGPtek-1080P-Click-Recorder-Capture/dp/B00MQQKDYE/](http://www.amazon.com/AGPtek-1080P-Click-Recorder-Capture/dp/B00MQQKDYE/) - about $80.  Audio will only be stereo and the recordings are HUGE, but you can transcode  those down to 1/4 size easy. I know it does HDMI, it may support component, but I don't have any component devices.

If RGB is s-video or VGA, there are lots of TV capture devices that support analog inputs.  There must be something like a 950Q which has Linux support.

If you need component video, then the Hauppauge 1212 is probably the only answer. I have a 1512 and the beta drivers for Linux don't support the specific version I have, so I'm stuck with Windows.  The 1512 does support 5.1 DTS/DD audio, however.  The 1512 box says component is supported - to get 5.1 DTS/DD audio, toslink (optical audio) is required.

Of course, if there is HDCP in the video signaling over the HDMI, you'll need to solve that. The gamer forums will provide $30-$50 solutions for that.

I've replied to other similar questions here - do a little forum searching to get more info.

---

### Post by mcduck on 2015-10-11
> **TheFu said:**
> Don't know what "rgb" is.

Most likely RGB SCART, pretty common connector for analog component video (but using RGB as the components instead of YPbPr) used around Europe.

Not sure how easy it would be to fine a capture device for it, but in the worst case it can be captured through a VGA connector with a bit of tinkering.

Another option would be to just get a RGB SCART to HDMI adapter and then use the same capture device for both.

---

### Post by myromance123 on 2015-10-16
There is the Magewell XI100DUSB-HDMI capture card that is confirmed to support Linux 100%. However, it is not without bugs apparently. There is audio synchronization issues from past problems others have posted, whether or not these issues have been overcome in recent driver updates is unknown to me.

Here is the official homepage of the company:
[http://www.magewell.com/usb-capture-family]("http://www.magewell.com/usb-capture-family")

Here is the official page of the device itself:
[http://www.magewell.com/usb-capture-hdmi]("http://www.magewell.com/usb-capture-hdmi")

How this will work in your setup is entirely up to you, but if you plan to view what you're recording at the same time, then you will need a HDMI splitter in addition to this device to my understanding.

The device itself is pretty pricey (USD $300), I do not have one myself but I'm saving up to afford one (RM1400 in Malaysia). The company is pro-Linux and even heavily mention their devices are compatible with Linux on their pages.

Depending on where you live in the world, this device could be easy to come by or hard. It is available on Amazon here for those in the states/uk:
[http://www.amazon.com/Magewell-XI100DUSB-HDMI-Video-Capture-Dongle/dp/B00I16VQOY](http://www.amazon.com/Magewell-XI100DUSB-HDMI-Video-Capture-Dongle/dp/B00I16VQOY)

For your RGB devices I'm assuming you mean RCA cables? (red white yellow). You could use a converter like this one (calls itself enko Devices):
[http://www.amazon.com/Mini-Composite-CVBS-Converter-Input/dp/B00I482KZI/ref=sr_1_7?s=electronics&ie=UTF8&qid=1445005459&sr=1-7&keywords=rca+converter]("http://www.amazon.com/Mini-Composite-CVBS-Converter-Input/dp/B00I482KZI/ref=sr_1_7?s=electronics&ie=UTF8&qid=1445005459&sr=1-7&keywords=rca+converter")

It will take your AV input and output it to HDMI. Then from there, you could plug the HDMI end into your HDMI splitter. From the splitter, you would put one HDMI cable into a screen/monitor/TV for viewing, and the other in the Magewell for recording purposes.

How well this overall setup will work is outside of my knowledge. Hopefully some of this information is useful to you or others.

---

### Post by TheFu on 2015-10-16
If you must have a Linux computer solution and price isn't an issue, there are expensive devices non-USB from Blackmagic that do this - look at the "Intensity" line. 
[https://www.blackmagicdesign.com/products/intensitypro4k](https://www.blackmagicdesign.com/products/intensitypro4k) US$200.
The USB version  doesn't mention Linux.
I don't think either deal with audio all that well.

It is hard to beat the $80 solution posted above, IMHO, if price matters.

---

### Post by Bucky Ball on 2015-10-16
*Thread moved to **Hardware**.*

---

