---
title: "Freezing after reset, &quot;GPU has fallen off the bus&quot; Ubuntu 20.04, nvidia-driver-440"
date: 2020-05-24
forum: Hardware
---

### Post by Hyenaz on 2020-05-24
Hello,

I have a persistent error with my laptop.
After suspend, I get the error message "GPU has fallen off the bus". See image attached. The only solution is a hard reset.
This has been happening since Ubuntu 19.10 and continues with 20.04

My laptop is a Lenovo W451 with a Nvidia GK106GLM [Quadro K2100M] graphics card.
I am using the nvidia-driver-440 version from the official repositories.

Would love any advice with this.  Thank you!

[ATTACH=CONFIG]285998[/ATTACH]

---

### Post by CelticWarrior on 2020-05-24
440 is incorrect. According to Nvidia the latest driver for Quadro K2100M is 418: [https://www.nvidia.co.uk/Download/driverResults.aspx/153781/en-uk](https://www.nvidia.co.uk/Download/driverResults.aspx/153781/en-uk)

---

### Post by Autodave on 2020-05-24
Yes: the 418 driver is what you should be using.  There is even a note on nVidia's site explaining that it fixed a bug about when the laptop is suspended.

Do NOT go to the site to d-l the proper driver: use the one in the repositories.

---

### Post by Yellow Pasque on 2020-05-24
The actual 418 driver is not in the Ubuntu 20.04 repositories (because 418 is neither a current nor legacy branch). If you try to install 418 driver, you just end up with 440 driver, because 418 and 430 are empty transitional packages that pull in 440.
What the OP wants in this case is the nvidia 390 legacy driver.

---

