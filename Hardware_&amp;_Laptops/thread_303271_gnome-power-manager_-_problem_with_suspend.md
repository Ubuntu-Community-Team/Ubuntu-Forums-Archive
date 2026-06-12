---
title: "gnome-power-manager - problem with suspend"
date: 2006-11-20
forum: Hardware &amp; Laptops
---

### Post by Serenader on 2006-11-20
Hello All,

I have a problem with gnome-power-manager. I have set it up so that the laptop goes into suspend mode when I close the lid (when its running on AC). It works fine if I reopen the lid in 5 minutes or so. But, if I keep the lid closed too long, and open the lid and press a key, I can see the power light come up, but nothing shows up on the monitor. I am using Acer Aspire 2000. So, I have to power down the machine by pressing the power key and reboot it, which is not what I want to do in the long run. Does anyone know what the problem could be and does it have anything to do with the size of the swap partition. Please let me know.

Thanks.

---

### Post by pitkali on 2006-11-20
I had something similar. I found out that the problem is cpufreq module ondemand. /etc/init.d/powernowd finds the module and uses it to change the cpu frequency. When I commented out looking for that module and thus forced the script to use userspace policy along with powernowd daemon, everything went fine.

NOTE 1: conservative governor also make suspend behave inconsistently.

NOTE 2: If you have ati card, make sure your fglrx module works fine. In case of my X1300 I had to download newer version from ati page, because suspend was not working with the driver in Edgy.

---

### Post by Serenader on 2006-11-20
> **pitkali said:**
> I had something similar. I found out that the problem is cpufreq module ondemand. /etc/init.d/powernowd finds the module and uses it to change the cpu frequency. When I commented out looking for that module and thus forced the script to use userspace policy along with powernowd daemon, everything went fine.

NOTE 1: conservative governor also make suspend behave inconsistently.

NOTE 2: If you have ati card, make sure your fglrx module works fine. In case of my X1300 I had to download newer version from ati page, because suspend was not working with the driver in Edgy.

Thanks for the response. Can you please give me more details about what you have done (probably the steps). I would really appreciate it.

---

### Post by pitkali on 2006-11-20
Well, you could run in terminal ```
sudo gedit /etc/init.d/powernowd
```
Then you should locate the line 'use_ondemand() {' and add new line immediately after this one:

```
return 1;
```
That will ensure that powernowd will set governor to userspace instead of ondemand. The following should apply the changes immediately:

```
sudo /etc/init.d/powernowd restart
```

---

### Post by Serenader on 2006-11-20
> **pitkali said:**
> Well, you could run in terminal ```
sudo gedit /etc/init.d/powernowd
```
Then you should locate the line 'use_ondemand() {' and add new line immediately after this one:

```
return 1;
```
That will ensure that powernowd will set governor to userspace instead of ondemand. The following should apply the changes immediately:

```
sudo /etc/init.d/powernowd restart
```

Hello Pitkali,

Thanks for your response again. I did what you asked me to do, but I still have the same problem. When I close the lid, I guess the system goes to suspend, but it doesn't wake up after I press the enter key. I have to press the power button to reboot it. Any suggestions????

---

### Post by pitkali on 2006-11-21
Well, it's high time for a question worth 100 points - what video card do you have?

---

### Post by Serenader on 2006-11-21
> **pitkali said:**
> Well, it's high time for a question worth 100 points - what video card do you have?

Its SiSM760GX.

---

