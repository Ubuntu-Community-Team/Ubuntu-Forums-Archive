---
title: "Temperature display on CPU fan's screen"
date: 2023-03-30
forum: Hardware
---

### Post by jonathanubian on 2023-03-30
Hello everyone,

I use Ubuntu 20.04.6 LTS, my motherboard is a GigaByte B460M Aorus Pro (with built-in temperature sensors) and bought a RGB CPU fan Alseye model M120D Plus which has a tiny screen to display the CPU temperature.

The problem is that the CPU fan displays 24C and the temperature doesn't move, and it should go up and down as the workload changes.

The RGB works well using OpenRGB.

I've looked for official drivers for this fan but none available so far.

Does anyone know how to get the temperature reading right on the fan's display or ever faced a similar problem and know what tweaks to do?

Many thanks.

---

### Post by MAFoElffen on 2023-03-31
I have the same MB... Or at least a model very similar.

Please post the output of this, within CODE Tags:
```

mafoelffen@Mikes-B460M:~$ [COLOR=#ff0000]for i in /sys/class/thermal/thermal_zone[0-9]/temp /sys/class/hwmon/hwmon[0-9]/temp[0-9]_input /sys/devices/platform/coretemp.[0-9]/hwmon/hwmon[0-9]/temp[0-9]_input; do [[ -e $i ]] && echo "$i : $(<$i)"; done[/COLOR]

/sys/class/thermal/thermal_zone0/temp : 16800
/sys/class/thermal/thermal_zone1/temp : 16800
/sys/class/thermal/thermal_zone2/temp : 27800
/sys/class/thermal/thermal_zone3/temp : 27000
/sys/class/thermal/thermal_zone4/temp : 45000
/sys/class/hwmon/hwmon0/temp1_input : 16800
/sys/class/hwmon/hwmon0/temp2_input : 16800
/sys/class/hwmon/hwmon0/temp3_input : 27800
/sys/class/hwmon/hwmon1/temp1_input : 32850
/sys/class/hwmon/hwmon2/temp1_input : 27000
/sys/class/hwmon/hwmon2/temp2_input : 26000
/sys/class/hwmon/hwmon2/temp3_input : 24000
/sys/class/hwmon/hwmon2/temp4_input : 26000
/sys/class/hwmon/hwmon2/temp5_input : 25000
/sys/class/hwmon/hwmon2/temp6_input : 25000
/sys/class/hwmon/hwmon2/temp7_input : 24000
/sys/class/hwmon/hwmon2/temp8_input : 25000
/sys/class/hwmon/hwmon2/temp9_input : 27000
/sys/class/hwmon/hwmon3/temp1_input : 45000
/sys/devices/platform/coretemp.0/hwmon/hwmon2/temp1_input : 27000
/sys/devices/platform/coretemp.0/hwmon/hwmon2/temp2_input : 26000
/sys/devices/platform/coretemp.0/hwmon/hwmon2/temp3_input : 24000
/sys/devices/platform/coretemp.0/hwmon/hwmon2/temp4_input : 26000
/sys/devices/platform/coretemp.0/hwmon/hwmon2/temp5_input : 25000
/sys/devices/platform/coretemp.0/hwmon/hwmon2/temp6_input : 25000
/sys/devices/platform/coretemp.0/hwmon/hwmon2/temp7_input : 24000
/sys/devices/platform/coretemp.0/hwmon/hwmon2/temp8_input : 25000
/sys/devices/platform/coretemp.0/hwmon/hwmon2/temp9_input : 27000

```

---

### Post by jonathanubian on 2023-03-31
> **MAFoElffen said:**
> I have the same MB... Or at least a model very similar.

Please post the output of this, within CODE Tags:
```

mafoelffen@Mikes-B460M:~$ [COLOR=#ff0000]for i in /sys/class/thermal/thermal_zone[0-9]/temp /sys/class/hwmon/hwmon[0-9]/temp[0-9]_input /sys/devices/platform/coretemp.[0-9]/hwmon/hwmon[0-9]/temp[0-9]_input; do [[ -e $i ]] && echo "$i : $(<$i)"; done[/COLOR]

/sys/class/thermal/thermal_zone0/temp : 16800
/sys/class/thermal/thermal_zone1/temp : 16800
/sys/class/thermal/thermal_zone2/temp : 27800
/sys/class/thermal/thermal_zone3/temp : 27000
/sys/class/thermal/thermal_zone4/temp : 45000
/sys/class/hwmon/hwmon0/temp1_input : 16800
/sys/class/hwmon/hwmon0/temp2_input : 16800
/sys/class/hwmon/hwmon0/temp3_input : 27800
/sys/class/hwmon/hwmon1/temp1_input : 32850
/sys/class/hwmon/hwmon2/temp1_input : 27000
/sys/class/hwmon/hwmon2/temp2_input : 26000
/sys/class/hwmon/hwmon2/temp3_input : 24000
/sys/class/hwmon/hwmon2/temp4_input : 26000
/sys/class/hwmon/hwmon2/temp5_input : 25000
/sys/class/hwmon/hwmon2/temp6_input : 25000
/sys/class/hwmon/hwmon2/temp7_input : 24000
/sys/class/hwmon/hwmon2/temp8_input : 25000
/sys/class/hwmon/hwmon2/temp9_input : 27000
/sys/class/hwmon/hwmon3/temp1_input : 45000
/sys/devices/platform/coretemp.0/hwmon/hwmon2/temp1_input : 27000
/sys/devices/platform/coretemp.0/hwmon/hwmon2/temp2_input : 26000
/sys/devices/platform/coretemp.0/hwmon/hwmon2/temp3_input : 24000
/sys/devices/platform/coretemp.0/hwmon/hwmon2/temp4_input : 26000
/sys/devices/platform/coretemp.0/hwmon/hwmon2/temp5_input : 25000
/sys/devices/platform/coretemp.0/hwmon/hwmon2/temp6_input : 25000
/sys/devices/platform/coretemp.0/hwmon/hwmon2/temp7_input : 24000
/sys/devices/platform/coretemp.0/hwmon/hwmon2/temp8_input : 25000
/sys/devices/platform/coretemp.0/hwmon/hwmon2/temp9_input : 27000

```

Thank you to reply me.
As you requested, the output is the next

```

jonathan@Nubian:~$ for i in /sys/class/thermal/thermal_zone[0-9]/temp /sys/class/hwmon/hwmon[0-9]/temp[0-9]_input /sys/devices/platform/coretemp.[0-9]/hwmon/hwmon[0-9]/temp[0-9]_input; do [[ -e $i ]] && echo "$i : $(<$i)"; done
/sys/class/thermal/thermal_zone0/temp : 16800
/sys/class/thermal/thermal_zone1/temp : 16800
/sys/class/thermal/thermal_zone2/temp : 27800
/sys/class/thermal/thermal_zone3/temp : 28000
/sys/class/hwmon/hwmon0/temp1_input : 16800
/sys/class/hwmon/hwmon0/temp2_input : 16800
/sys/class/hwmon/hwmon0/temp3_input : 27800
/sys/class/hwmon/hwmon1/temp1_input : 28000
/sys/class/hwmon/hwmon1/temp2_input : 24000
/sys/class/hwmon/hwmon1/temp3_input : 26000
/sys/class/hwmon/hwmon1/temp4_input : 26000
/sys/class/hwmon/hwmon1/temp5_input : 25000
/sys/devices/platform/coretemp.0/hwmon/hwmon1/temp1_input : 28000
/sys/devices/platform/coretemp.0/hwmon/hwmon1/temp2_input : 24000
/sys/devices/platform/coretemp.0/hwmon/hwmon1/temp3_input : 26000
/sys/devices/platform/coretemp.0/hwmon/hwmon1/temp4_input : 26000
/sys/devices/platform/coretemp.0/hwmon/hwmon1/temp5_input : 25000

```

:-D

---

### Post by yorakal on 2023-04-01
If you look on that fans [makers website]("https://www.alseyecorp.com/product-item/m120d-plus/") it appears to say that their windows companion software is what sends the data to the display on the fan.

On the download page for the BEM v2.0 software it also says

> **NOTICE:  Please make sure that the CPU cooler&#8217;s USB cable is properly connected to the USB port of the motherboard and that the &#8220;BEM&#8221; software is running during your use. Or the CPU cooler will remain to display 24°c \ 0°c**

---

