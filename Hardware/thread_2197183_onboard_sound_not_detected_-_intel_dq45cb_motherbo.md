---
title: "onboard sound not detected - intel dq45cb motherboard"
date: 2014-01-02
forum: Hardware
---

### Post by compiz addict on 2014-01-02
I recently attained a new computer with an intel dq45cb motherboard. I have a 64-bit install of Ubuntu 12.04 installed on it, and the onboard sound isn't detected. Intel's website says Linux has native support for the audio, tested in Ubuntu 8.04.

The volume control shows "Dummy Output", which I'm assuming means no audio hardware is even detected.

So, before I mess anything up removing and reinstalling packages, what should I do about this?

---

### Post by compiz addict on 2014-01-03
*bump*
I'm really at a loss as to how to fix this. It seems to me that there just isn't a lot of support for onboard sound...

---

### Post by Yellow Pasque on 2014-01-03
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by compiz addict on 2014-01-03
Thanks. Here's the info: [http://www.alsa-project.org/db/?f=68345308b0470413746f73dd63f6210006f155e0](http://www.alsa-project.org/db/?f=68345308b0470413746f73dd63f6210006f155e0)
The USB audio device is most likely the microphone on my Logitech webcam.

---

### Post by Yellow Pasque on 2014-01-04
Is the onboard audio enabled in the BIOS?

---

### Post by compiz addict on 2014-01-04
Oh, wow... Thanks :D
I'm glad I asked before breaking things.

---

