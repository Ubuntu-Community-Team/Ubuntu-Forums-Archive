---
title: "Acerhdf"
date: 2011-11-05
forum: Hardware
---

### Post by blackmail on 2011-11-05
Hello, I have an Acer 5715Z laptop, and i have moved it from Windows 7 to Ubuntu, and all works like a charm, of course that i have the Ubuntu 11.04 installation since the new one just crashed, so this means Kernel 2.6
Well anyway i have had some problems with overheating due to the fact that the fan would not turn on, for this i thought i would try to use the acerhdf tool, i have created the config script and also loaded the module, or anyway here is what i did:

```
gedit /etc/modprobe.d/acerhdf.conf
```

```
# fan control for acer aspire one fan

# according to: http://piie.net/files/acerhdf_README.txt

# check status with: dmesg|grep acerhdf

# read temperature with: cat /sys/class/thermal/thermal_zone0/temp

options acerhdf interval=5 fanon=60000 fanoff=55000 kernelmode=1
```

and of course i have loaded the whole damn thing with

```
sudo modprobe -r acerhdf
```

but it did not help, the laptop doesn't turn off when at startup the cooler starts and remains spinning while the OS is loading. Also another thing is that when i do a:

```
sudo dmesg | grep acerhdf
```

and don't get anything, meanind that the module is not working, so any suggestions on this?

I would really consider not flashing the BIOS since that would require a reinstall of a windows OS, and the laptop was already through quite a lot.

---

