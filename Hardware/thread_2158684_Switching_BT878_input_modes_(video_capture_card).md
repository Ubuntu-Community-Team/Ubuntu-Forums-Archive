---
title: "Switching BT878 input modes (video capture card)"
date: 2013-06-30
forum: Hardware
---

### Post by r3g on 2013-06-30
Hi,

I have an old Hauppauge Wint TV capture card that I am trying to use with Zoneminder.

The card is detected fine and the video stream shows up in Zoneminder as /dev/video0.

All good so far.

The problem is that the video stream that it's showing is the TV tuner signal and I want to switch it to use the video-in signal from my camera connected via the phono video-in socket.

I know that the card has several video input modes including TV tuner, video, radio, etc.

I'm guessing that the next step would be to make a configuration file: /etc/modprobe.d/bttv

But all the examples I've found so far are only concerned with using the tuner function for things like Myth TV.

Does anyone know how I configure it to just use the "video-in" mode?

Thanks.

---

### Post by r3g on 2013-07-04
Hi,

Just in case anyone is having the same issue of needing to change input channels on any kind of video capture card (controlled by v4l2), this should do the trick;

v4l2-ctl --set-input=1

The v4l2 driver is where you control the input, not as I thought in bttv config.

You may also need to install v4l2-utils (sudo apt-get install v4l2-utils) if it complains about an unknown command.

The set-input command takes one argument which is the number of the channel that you want to use for capture.

In my case, the channel numbers were;

0 = TV Tuner
1 = Composite video
2 = s-video

Hope this helps someone as it took me a few days to find it.

---

