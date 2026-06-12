---
title: "Built-in Microphone Not Working on Ubuntu 22.04.2 LTS"
date: 2023-06-27
forum: Hardware
---

### Post by damc4 on 2023-06-27
Hello Ubuntu community,


I've been experiencing an issue with my built-in microphone on Ubuntu Ubuntu 22.04.2 LTS. It works fine when I'm using Windows, which means it's not a hardware issue. I've been through various troubleshooting steps, but nothing seems to work. I'd appreciate any help or advice you could provide.


Here's what I've done so far:


[LIST=1]
[*]Checked the Sound Settings in Ubuntu and made sure the input device is selected and not muted. 
[*]Used alsamixer in Terminal. 
[*]Installed PulseAudio Volume Control and confirmed that my microphone is detected. The correct device is selected in the 'Input Devices' tab and it's not muted. The volume level is set appropriately. 
[*]Checked the Additional Drivers tab in the Software & Updates application. The only device I see is a "Realtek Semiconductor" device which appears to be a PCIe Wireless Network Adapter. 
[/LIST]
Here are my system details:

[LIST]
[*]Ubuntu Version: Ubuntu 22.04.2 LTS 
[*]Laptop Model: VivoBook_ASUSLaptop X515JAB_X515JA 
[*]Audio Device: Intel Corporation Ice Lake-LP Smart Sound Technology Audio Controller 
[/LIST]

Does anyone have any idea what I can try next?


Thank you in advance for your help.

---

### Post by Autodave on 2023-06-27
In pavucontrol, go to configuration and make sure that  "Analog stereo duplex" is selected instead of "Analog stereo output".

---

### Post by damc4 on 2023-06-28
It is selected. Unfortunately, it still doesn't work.

---

### Post by hedaetul on 2024-03-02
I am also suffering from this problem for 1 months. anyone know the solution help me please...

---

