---
title: "CPU Temperature on Intel D102GGC2 with ATi Xpress 200 chipset"
date: 2007-07-22
forum: Hardware &amp; Laptops
---

### Post by Self_za on 2007-07-22
Hi

I'm a newbie Linux user and would really appreciate some help.  I have an Intel D102GGC2 mobo with ATi xpress 200 chipset and I'm trying to set up lm-sensors to monitor things like CPU temperature and fan speeds.  I followed this [[COLOR="Red"]_HOW TO_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2780&highlight=sensors+detect"), but it didn't work for me.  This seems to be a common problem with ati chipsets.  I installed lm-sensors and ran sensors-detect. 

This is the summary I get:
```

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `eeprom' (should be inserted):
  Detects correctly:
  * Bus `NVIDIA i2c adapter 0 at 1:00.0'
    Busdriver `UNKNOWN', I2C address 0x50 (and 0x51 0x52 0x53 0x54 0x55 0x56 0x57)
    Chip `EDID EEPROM' (confidence: 8)
  * Bus `SMBus PIIX4 adapter at 2010'
    Busdriver `i2c-piix4', I2C address 0x50
    Chip `eeprom' (confidence: 6)

  EEPROMs are *NOT* sensors! They are data storage chips commonly
  found on memory modules (SPD), in monitors (EDID), or in some
  laptops, for example.

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To make the sensors modules behave correctly, add these lines to
/etc/modules:

#----cut here----
# I2C adapter drivers
# modprobe unknown adapter NVIDIA i2c adapter 0 at 1:00.0
# modprobe unknown adapter NVIDIA i2c adapter 1 at 1:00.0
# modprobe unknown adapter NVIDIA i2c adapter 2 at 1:00.0
i2c-piix4
# Chip drivers
eeprom
#----cut here----
```

I inserted it into /etc/modules.  Did sudo sensors and keep getting the following;

```
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
```

Can someone please point me in the right direction?

---

### Post by w4ett on 2007-07-22
Try loading the xsensors package from Synaptic,  it gives you a gui interface.   I never could get sudo sensors to work properly.

---

### Post by Self_za on 2007-07-22
Nope already tried all the GUI apps.  The sensors have to be detected and working before anything will work really.  :confused:

---

### Post by w4ett on 2007-07-22
If I remember correctly, I had to remove lm-sensors and then reinstall it, run sensors-detect, but in my case I let the script modify  /etc/modules itself,  then I ran xsensors.  after that it worked.*

*Your mileage may vary.  :)

---

### Post by Self_za on 2007-08-01
I also reinstalled lm-sensors and let it modify /etc/modules.  I also tried loading the modules in reverse order like some tutorials suggest, but still no joy.  I'm hoping the new release of lm-sensors will help.

---

