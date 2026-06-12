---
title: "getting rid of lm-sensors and starting over"
date: 2005-11-26
forum: Hardware &amp; Laptops
---

### Post by Brunellus on 2005-11-26
I think I rather ham-handedly did something wrong setting up lm-sensors.

I want to use the ISA bus instead of SMBus.  

I removed lm-sensors completely using synaptic and rebooted.  then I installed lm-sensors again, and executed

sudo sensors-detect

I went through the detection sequence, when, at the very end, I noticed the following output which didn't happen the very first time I ran lm-sensors:

```
Client at address 0x50 can not be probed - unload all client drivers first!
Client at address 0x52 can not be probed - unload all client drivers first!
Client found at address 0x69
```

the summary of sensors-detect read as follows:

```
Sorry, no chips were detected.
 Either your sensors are not supported, or they are
 connected to an I2C bus adapter that we do not support.
```

despite, this, running ```
sensors
``` produced this output:

```
eeprom-i2c-0-52
Adapter: SMBus I801 adapter at 0400
Memory type:            DDR SDRAM DIMM
Memory size (MB):       256

eeprom-i2c-0-50
Adapter: SMBus I801 adapter at 0400
Memory type:            DDR SDRAM DIMM
Memory size (MB):       256

```

I think--I'm not sure-- lm-sensors added a number of modules to be loaded at startup.  lsmod | grep i2c reveals this output:
```
i2c_dev                 9216  0
i2c_acpi_ec             5760  0
i2c_sensor              3456  1 eeprom
i2c_i801                8204  0
i2c_core               19728  5 i2c_dev,i2c_acpi_ec,eeprom,i2c_sensor,i2c_i801

```

putting the output of sensors-detect and lsmod together, I'm guessing I have to remove, somehow the i2c_sensor module to probe again.

can anybody help me get back to where I should be?

---

### Post by ranf on 2005-11-26
[QUOTE=Brunellus]
I think--I'm not sure-- lm-sensors added a number of modules to be loaded at startup. 
[/QUOTE]
It only tells you what to add to `/etc/modules' if I remember correctly.
[QUOTE=Brunellus]lsmod | grep i2c reveals this output:
```
i2c_dev                 9216  0
i2c_acpi_ec             5760  0
i2c_sensor              3456  1 eeprom
i2c_i801                8204  0
i2c_core               19728  5 i2c_dev,i2c_acpi_ec,eeprom,i2c_sensor,i2c_i801

```
[/QUOTE]
You can safely unload any of these i2c modules:
```
sudo modprobe -r <module>
```

---

### Post by metoo on 2005-11-26
Did you allow sensor-detect to make the changes?
Check /etc/modules if there is a lm-sensor section now.

Bad luck if you have an Abit board. Closed source sensor chip. Not supported by lm-sensor.

---

