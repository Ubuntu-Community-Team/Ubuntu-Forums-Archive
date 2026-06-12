---
title: "My ongoing battle against Sound"
date: 2017-11-02
forum: Hardware
---

### Post by yurikirejian on 2017-11-02
Hello friends, i'm new to the forum and I home to help those who face the same problems as I'm facing right now. I bougth a new MOBO (M5A78 LM USB3 PLUS). After installing all drivers and updating windows 7, as usual, i'm not new to this, I struggled to make my sound work in both rear and front ports.

I know i'm talking about windows but it will get to ubuntu soon, sorry but I think it's relevant.

After days i managed to make the rear ports work by overwriting all audio drivers using the amd catalyst for managing audio and video drivers. After reading about this issue for days I was told to change my bios setup from HDAUDIO to AC97 even though i was using the HDAUDIO cables connected to the mobo. The audio died in all ports so I changed the bios setting back to HDAUDIO and restarted.

Oddly, both front and rear ends started working normally and i noticed that windows asked for an update that I had already installed before, something about AMD advanced drivers. So I did not installed it again. I restarted my pc, the sound kept working in both ends but that strange update was now installed, even though I did not do it.

So I installed ubuntu but here the sound only works by the front connectors, not the rear ones. Since I use Ubuntu for College and I'm still learning to use it, I need the sound to work propperly.

I checked and rechecked my mobo's manual for anny mistakes I may have commited but it is a verry straightfoward installation. I really hope my mobo is not deffective. I hope the problem is me being verry stupid.

Sorry for anny english mistakes.

Thank you.

---

### Post by gsahli on 2017-11-02
Read this and install pavucontrol.
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

### Post by Yellow Pasque on 2017-11-03
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by yurikirejian on 2017-11-05
I installed pavucontrol. I gave a look to it but the only audio I get is the one coming out from the front jacks.

Here is the link to my alsa:

[http://www.alsa-project.org/db/?f=4d7d4e2a5615864e4373aa3e33cd159549123bf7](http://www.alsa-project.org/db/?f=4d7d4e2a5615864e4373aa3e33cd159549123bf7)

---

### Post by Yellow Pasque on 2017-11-07
The only idea I have is to try disabling "Auto Mute" in alsamixer.

---

### Post by yurikirejian on 2017-11-08
The option where already disabled. Please, I don't know what to do now. Is it possible for my mobo to have compatibility issues in linux?

---

