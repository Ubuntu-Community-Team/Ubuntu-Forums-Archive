---
title: "Sensors and Xsensors"
date: 2008-10-26
forum: General Help
---

### Post by Aries0777 on 2008-10-26
Hello all,

I'm kind of new to Linux , only 6 months, playing and working with Linux. 
I have installed different distros and I like Ubuntu the most .... honestly :-))

I have been trying to get sensors to work on my system but so far has succeeded in only getting it yo display the default values but not the actual values on my system. If I launch Xsensors. I get a very tiny window which when maximized shows a blank window with nothing in it.

Any help would be greatly appreciated.

Thx in advance

---

### Post by cariboo on 2008-10-26
You  have to setup lm-sensors before you get any output from sensors. In a terminal type:

```
sudo sensors-detect
```

answer yes to all the questions, at the end of the process you should see something like this:

```
To load everything that is needed, add this to /etc/modules:

#----cut here----
# I2C adapter drivers
i2c-nforce2
# Chip drivers
# no driver for Fintek F75383S/M yet
w83627ehf
k8temp
#----cut here----

Do you want to add these lines automatically? (yes/NO)
```

Answer **yes** to the final question. Not knowing what the result will be I can't advise you any further, so just reboot and the mosules that were found will be installed. Once you've rebooted you should now see results when you type in a terminal:

```
sensors
```

I use sensors-applet to monitor cpu and hd temps.
See attached screenshot.

Jim

---

### Post by wpshooter on 2008-12-21
> **cariboo907 said:**
> You  have to setup lm-sensors before you get any output from sensors. In a terminal type:

```
sudo sensors-detect
```

answer yes to all the questions, at the end of the process you should see something like this:

```
To load everything that is needed, add this to /etc/modules:

#----cut here----
# I2C adapter drivers
i2c-nforce2
# Chip drivers
# no driver for Fintek F75383S/M yet
w83627ehf
k8temp
#----cut here----

Do you want to add these lines automatically? (yes/NO)
```

Answer **yes** to the final question. Not knowing what the result will be I can't advise you any further, so just reboot and the mosules that were found will be installed. Once you've rebooted you should now see results when you type in a terminal:

```
sensors
```

I use sensors-applet to monitor cpu and hd temps.
See attached screenshot.

Jim

Where does one find this "sensors-applet" ?

Thanks.

---

### Post by dcstar on 2008-12-22
> **wpshooter said:**
> Where does one find this "sensors-applet" ?

Thanks.

Right-click the top Panel area, select "Add to panel" and drag the Hardware Sensors Monitor to where you want it on the panel area.

---

