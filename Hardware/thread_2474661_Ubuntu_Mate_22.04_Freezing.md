---
title: "Ubuntu Mate 22.04 Freezing"
date: 2022-05-05
forum: Hardware
---

### Post by captaincyril on 2022-05-05
Hi,

I have a Dell E6500 which was running without any problems on Ubuntu MATE 20.04 and Ubuntu MATE 21.10. 21.10 was better at speed and the experience was more smooth as the proprietary driver (not nouveau) of NVIDIA was used.

The VGA is [COLOR=#111111][FONT=Roboto]NVIDIA Quadro NVS 160M.

Ever since I upgraded to Ubuntu 22.04 the computer has been freezing specially when I use the browsers FireFox and Chrome. So I downloaded 22.04 ISO and reinstalled it and the problem persisted. Then I reinstalled 20.04 and this time the driver wouldn't install due to the update kernel I guess.

The system is freezing when I use any browser or even when I open many apps at the same time:
Visual Studio Code, FileZilla, System Monitor, Terminal, Telegram.

The system does not turn off the monitor when I put it on sleep or if by mistake it turns off then the system wouldn't turn on. It was working fine on 21.10 with NVIDIA driver.

The driver needed is NVIDIA 340.180 which is no longer support by NVIDIA for 22.04.

[/FONT][/COLOR][COLOR=#111111][FONT=Roboto]What are my options now?[/FONT][/COLOR]

---

### Post by captaincyril on 2022-05-05
The best option right now is to run Chrome OS Flex from a USB stick until I am able to solve the 22.04 issue.

---

### Post by captaincyril on 2022-05-05
It turns out that Google also is reporting minor issues for E6500 that are pending to be resolved. So that's not working.

Vista is running fine on the computer but I cannot update the browsers on Vista.

---

### Post by captaincyril on 2022-05-09
How to Use PipeWire to replace PulseAudio in Ubuntu 22.04
[https://ubuntuhandbook.org/index.php/2022/04/pipewire-replace-pulseaudio-ubuntu-2204/](https://ubuntuhandbook.org/index.php/2022/04/pipewire-replace-pulseaudio-ubuntu-2204/)

The above did the trick. It is not freezing anymore but rather sometimes the video takes a few seconds before it shows but I can still close the browser. Pages without video open regularly. I am using Chrome. FireFox is still not working. I guess I have to remove it and install from another source.

---

### Post by captaincyril on 2022-05-09
I disabled the Hardware Acceleration in FireFox and it worked normally. I didn't have to uninstall it.

---

