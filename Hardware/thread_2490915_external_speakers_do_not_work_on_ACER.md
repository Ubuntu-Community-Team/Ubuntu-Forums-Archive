---
title: "external speakers do not work on ACER"
date: 2023-09-20
forum: Hardware
---

### Post by bengao51 on 2023-09-20
Hello everybody,
  I have just installed ubuntu 22.04 on my Acer PC reference REVO RN96.
I put external speakers wired to the sound jack.
Unfortunately, they don't work and I haven't found the solution for many days.
  I even had to reinstall Ubutu following this procedure [http://linuxconfig.org/how-to-install-pipewire-on-ubuntu-linux](http://linuxconfig.org/how-to-install-pipewire-on-ubuntu-linux) 

  If anyone knows the problem.

  Thanks in advance.
  Ben

---

### Post by TheFu on 2023-09-20
There are 3 different speaker connection types that use 2.5mm jacks.  Ensure you have the correct converter for your specific Acer model.
Also, ensure that the audio output is set to use the speakers, not the lineout.  **pavucontrol** is the full GUI to manage PulseAudio. I don't know if it is installed or not on 22.04.  Different 22.04 versions have jack, pulse, pipewire, so if your setup is using something other than pulseaudio, you'll want to find the equivalent for the other audio stacks.

---

