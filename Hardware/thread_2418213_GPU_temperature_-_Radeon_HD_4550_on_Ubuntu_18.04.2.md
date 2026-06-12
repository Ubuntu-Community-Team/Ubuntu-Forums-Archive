---
title: "GPU temperature - Radeon HD 4550 on Ubuntu 18.04.2 LTS"
date: 2019-05-03
forum: Hardware
---

### Post by datarubicon on 2019-05-03
Hi,

i would like to ask if temperature of my GPU card i'm curently using is getting normal ranges.
I have installed AMD Radeon HD 4550 graphic card in Fujitsu PRIMERGY TX120 S3P under Ubuntu 18.04.2 LTS.
Using one monitor by display port with 1680x1050 screen resolution.

Sensors shows:

radeon-pci-0100
Adapter: PCI adapter
temp1:        +74.5°C  (crit = +120.0°C, hyst = +90.0°C)

After starting it's 65 grad C, and going to 70-80 range.

Is it normal working temp for this kind of GPU?
How can i lower it?

Thanks for any sugestions.

---

### Post by Autodave on 2019-05-03
I am thinking that you are getting erroneous readings.  If I read your post correctly, you are stating that on startup it is reading 65C?  (147F)  Is it really that hot where you are living??  I doubt it.  The crit =+120 surely doesn't sound correct either: it would melt down long before that temp.

---

### Post by datarubicon on 2019-05-03
Thank you Autodave for reply. I'm afraid it may be not an error in sensor reading - i have no cover on this machine and it's giving lot of heat from this card (trying by my hand).
After starting it's giving 6X Celsius and slowly going up to 75 (after turning monitor off goes back to 65).
It's linux drivers problem may be?
i have found that this card under Windows runs sth like 40-50 Celsius max.

---

### Post by Yellow Pasque on 2019-05-03
Is it passively cooled or does it have a fan? I had a 4550 (passively cooled, Gigabyte IIRC) and I don't remember any temp problems or big differences between Windows and Linux.
See how much load is on the GPU: [https://awesomedetect.com/how-to-monitor-amd-ati-or-radeon-gpu-usage-in-linux/](https://awesomedetect.com/how-to-monitor-amd-ati-or-radeon-gpu-usage-in-linux/)

---

### Post by datarubicon on 2019-05-03
> **Temüjin said:**
> Is it passively cooled or does it have a fan? I had a 4550 (passively cooled, Gigabyte IIRC) and I don't remember any temp problems or big differences between Windows and Linux.
See how much load is on the GPU: [https://awesomedetect.com/how-to-monitor-amd-ati-or-radeon-gpu-usage-in-linux/](https://awesomedetect.com/how-to-monitor-amd-ati-or-radeon-gpu-usage-in-linux/)

Thanks for the link, i have had installed radeontop - my GPU is doing nothing, i have default Ubuntu desktop with terminal + Chrome browser opened.

My card has little fan on radiator:

[IMG]https://d.allegroimg.com/s720/01c7b1/8e7db81d41b584fc070d5b3e0a4d[/IMG]
radeontop results: [https://ibb.co/bQxdmp2](https://ibb.co/bQxdmp2)
sensors results: [https://ibb.co/k4zzScL](https://ibb.co/k4zzScL)

If you have same model, do you know what is idle temperature of this GPU card under linux drivers ?

---

### Post by Autodave on 2019-05-03
> **datarubicon said:**
> Thank you Autodave for reply. I'm afraid it may be not an error in sensor reading - i have no cover on this machine and it's giving lot of heat from this card (trying by my hand).
After starting it's giving 6X Celsius and slowly going up to 75 (after turning monitor off goes back to 65).
It's linux drivers problem may be?
i have found that this card under Windows runs sth like 40-50 Celsius max.

You are not understanding what I am saying: if this card is showing 60C when you start the computer, your reading/sensor is bad: I am sure that the environment around the PC is not 60C!

---

