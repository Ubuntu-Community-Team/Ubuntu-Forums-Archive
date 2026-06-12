---
title: "NVIDIA GeForce 830M not detected"
date: 2015-02-18
forum: Hardware
---

### Post by mohan-kiran on 2015-02-18
I installed Ubuntu 14.10 in my new HP laptop [http://hpshopping.in/HP_Pavilion_Notebook_-_15-p277tx_Laptop](http://hpshopping.in/HP_Pavilion_Notebook_-_15-p277tx_Laptop)
After installation I expected "Additional Drivers" to detect the NVIDIA GeForce 830M graphics card and suggest driver installation. However it didn't. Infact it didn't suggest any drivers.

Question:
1. What could be wrong if it wasn't detected?
2. How to install nvidia drivers?

---

### Post by Bashing-om on 2015-02-18
mohan-kiran; Hi !

Well like this, the 830m is 'new' hardware and linux has not caught up to it to this time ( blame the manufacturer for not taking care of us !). The reason "Additional Drivers" does not find anything is that there is no driver available in the software repository to this time.
Per:
[http://www.nvidia.com/download/driverResults.aspx/81252/en-us](http://www.nvidia.com/download/driverResults.aspx/81252/en-us)
Your card takes the 346 version of the Nvidia driver.

So yeah, ya got to resort to other means to get a graphics driver installed.
3 others that I am aware of.
I often see Michael Marley's PPA highly recommended:
[https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)

Before proceeding with this driver install, insure there are no other proprietary drivers installed. If there are no other proprietary drivers installed, then:
```

sudo apt-get update
sudo apt-get upgrade
sudo add-apt-repository ppa:mamarley/nvidia
sudo apt-get update
sudo apt-get install nvidia-346

```

Reboot to see the full effect.


[INDENT][INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]you can have it your way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mohan-kiran on 2015-02-19
Thanks for the reply Bashing-om.
Michael Marley's PPA worked for me.

---

### Post by Bashing-om on 2015-02-19
mohan-kiran; Great !

We mark up another 10 points for Michael Marley's PPA . He do good work.

[INDENT][INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]1 for all and all for one
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Arav_Agarwal on 2015-07-13
):PHI,
I also bought one of hp's this laptop [http://bit.ly/1HWvEXV](http://bit.ly/1HWvEXV) but gpu was not detecting, how to install this driver?

---

### Post by Bashing-om on 2015-07-13
Arav_Agarwal; Hi ! Welcome to the forum .

From your link I do not see this as a hybrid graphics system, and thus the advise in this thread will not apply in your case.

> 
Graphic Processor	Intel HD Graphics 4400

But just to double check and verify; What returns from terminal commands:
```

lspci -vnn | grep VGA -A 12
sudo lshw -C display

```

As Intel "just works", maybe there is nothing to be done ?

[INDENT][INDENT]Good things can happen
[/INDENT][/INDENT]

---

