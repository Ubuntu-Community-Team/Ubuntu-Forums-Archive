---
title: "Brightness control using command"
date: 2012-01-04
forum: Hardware
---

### Post by mr.akik on 2012-01-04
Hi all,
I am using ubuntu 11.04 on my netbook. 
Every time I boot my netbook , I have to reduce it's brightness pressing Fn+f6. It's very annoying and I thing after some days my netbook's keyboard will be damaged. Can anyone tell me how I can do this using a command? Then I will make a bash script and control it's brightness by just a mouse click.Thanks in advance.

---

### Post by Toz on 2012-01-04
There are a number of ways that this can be done:

1. xbacklight (available in the Software Centre) 
example:
```
xbacklight -set 50
```
...where *50* is the desired backlight %

2. setpci command - you will need to know address of video card:
```
lspci | grep VGA
```
example:
```
sudo setpci -s 00:02.0 F4.B=7f
```
...where *00:02.0* is the device id and *7f* is the hexidecimal equivalent of the brightness value that you want

3. Echo a brightness value directly into backlight interface brightness file:
First, you will need to identify your backlight interface:
```
ls /sys/class/backlight
```
...and hopefully you will get only one interface listed.
example:
```
echo 5 | sudo tee /sys/class/backlight/intel_backlight/brightness
```
...where *5* is the value (between 0 and the contents of /sys/class/backlight/intel_backlight/max_brightness) and /*sys/class/backlight/intel_backlight/brightness* is the backlight interface brightness file

---

### Post by mr.akik on 2012-01-05
Nothing could give me a solution.
This is the output of "xbacklight -set 50" command:

> No outputs have backlight property

This is the output of "lspci | grep VGA"
 :
```
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller


```
Nothing happens with this: "sudo setpci -s 00:02.0 F4.B=7f" .
Nothing happens with this: "ls /sys/class/backlight" .
And this is the output of : "echo 5 | sudo tee /sys/class/backlight/intel_backlight/brightness": 
```
tee: /sys/class/backlight/intel_backlight/brightness: No such file or directory
5

```

---

### Post by Toz on 2012-01-05
Interesting that you don't have a backlight interface. Can you try booting with the **acpi_backlight=vendor** kernel parameter to see if you get an interface listed in /sys/class/backlight? Information on how to temporarily boot with this kernel parameter can be found here: [https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot]("https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot").

What is the make/model of your netbook?

---

### Post by mr.akik on 2012-01-05
Sorry Toz, I didn't find anything related my issue in that page.
My netbook is made in Bangladesh. It's made by Bangladeshi Government. So, it may be unfamiliar to you.
Video card : Intel GMA3150
Display: 10.1" W.X.G.A LED backlight.

---

### Post by Toz on 2012-01-05
I was suggesting that you try booting your computer with the **acpi_backlight=vendor** kernel parameter to see if it creates a backlight interface for you (that you can then directly manipulate to set the brightness on boot-up). The procedure to test out the parameter is shown in that link and it involves editing your grub kernel line to add this parameter on boot-up.

---

### Post by mr.akik on 2012-07-15
Thanks to all .
After a long time I am writing in this post because now I have upgraded my ubuntu version. It's now 12.04 and I finally my backlight driver is detected.
This is the output of "ls /sys/class/backlight" command: 
```
intel_backlight
```
In my previous version of ubuntu , I didn't find this "intel_backlight".
But no command worked to reduce or change the brightness.
I did everything suggested in this thread. These are the commands and outputs: 

akik@akik-Pine-Trail-M-CRB:~$ xbacklight -set 50
akik@akik-Pine-Trail-M-CRB:~$ lspci | grep VGA00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
akik@akik-Pine-Trail-M-CRB:~$ sudo setpci -s 00:02.0 F4.B=7f
akik@akik-Pine-Trail-M-CRB:~
 
Nothing changed.

This is the entry with my grub4dos: 

title Ubuntu 12.04 
find --set-root --ignore-floppies /boot/vmlinuz-3.2.0-23-generic-pae 
kernel /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=9a700d1e-14ba-4c35-a2c3-9597e1749900 acpi_backlight=vendor ro 
initrd /boot/initrd.img-3.2.0-23-generic-pae

Please help me.

---

### Post by Toz on 2012-07-15
What are the results of the following commands:
```
cat /sys/class/backlight/intel_backlight/brightness
```
```
cat /sys/class/backlight/intel_backlight/actual_brightness
```
```
cat /sys/class/backlight/intel_backlight/max_brightness
```
```
sudo dmidecode -s system-manufacturer
```
```
sudo dmidecode -s system-product-name
```

---

### Post by mr.akik on 2012-07-15
> **Toz said:**
> What are the results of the following commands:
```
cat /sys/class/backlight/intel_backlight/brightness
``````
cat /sys/class/backlight/intel_backlight/actual_brightness
``````
cat /sys/class/backlight/intel_backlight/max_brightness
``````
sudo dmidecode -s system-manufacturer
``````
sudo dmidecode -s system-product-name
```Here are the results:

akik@akik-Pine-Trail-M-CRB:~$ cat /sys/class/backlight/intel_backlight/brightness
13046
akik@akik-Pine-Trail-M-CRB:~$ cat /sys/class/backlight/intel_backlight/actual_brightness
13046
akik@akik-Pine-Trail-M-CRB:~$ cat /sys/class/backlight/intel_backlight/max_brightness
13046
akik@akik-Pine-Trail-M-CRB:~$ sudo dmidecode -s system-manufacturer
Intel Corporation
akik@akik-Pine-Trail-M-CRB:~$ sudo dmidecode -s system-product-name
Pine Trail - M CRB
akik@akik-Pine-Trail-M-CRB:~$

---

### Post by Toz on 2012-07-15
Try this command:
```
echo 6000 | sudo tee /sys/class/backlight/intel_backlight/brightness
```
Does it adjust the brightness?

If not, try removing **acpi_backlight=vendor** from the kernel line and then the above commands ( post #8 ) again.

---

### Post by mr.akik on 2012-07-16
> **Toz said:**
> Try this command:
```
echo 6000 | sudo tee /sys/class/backlight/intel_backlight/brightness
```Does it adjust the brightness?

If not, try removing **acpi_backlight=vendor** from the kernel line and then the above commands ( post #8 ) again.Sorry Toz. Nothing happened with this command. Then I removed  **acpi_backlight=vendor from the kernel line b**ut no result.

---

### Post by Toz on 2012-07-16
Can you post back a copy of your /var/log/dmesg file? Try using pastebinit:
```
pastebinit /var/log/dmesg
```
...and post back the link it generates.

---

### Post by mr.akik on 2012-07-17
This is the output :
akik@akik-Pine-Trail-M-CRB:~$ pastebinit /var/log/dmesg
[http://paste.ubuntu.com/1096642/](http://paste.ubuntu.com/1096642/)
akik@akik-Pine-Trail-M-CRB:~$

---

### Post by Toz on 2012-07-17
There is nothing in your dmesg file that helps with this issue. Can you also post back /var/log/Xorg.0.log:
```
pastebinit /var/log/Xorg.0.log
```

And, can you try 2 more kernel parameters?

- **acpi_osi=Linux**
- **acpi_osi=Linux acpi_backlight=vendor**

With each boot of the added kernel parameters, can you run the following script (reports out on backlight interfaces and current values) and post back the results:
```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/actual_brightness; cat $interface/max_brightness; cat $interface/brightness; done
```

---

### Post by mr.akik on 2012-07-17
Here are the results:

akik@akik-Pine-Trail-M-CRB:~$ pastebinit /var/log/Xorg.0.log
[http://paste.ubuntu.com/1096931/](http://paste.ubuntu.com/1096931/)
akik@akik-Pine-Trail-M-CRB:~$ 

akik@akik-Pine-Trail-M-CRB:~$ for interface in /sys/class/backlight/*; do echo $interface; cat $interface/actual_brightness; cat $interface/max_brightness; cat $interface/brightness; done
/sys/class/backlight/intel_backlight
13046
13046
13046
akik@akik-Pine-Trail-M-CRB:~$ 


akik@akik-Pine-Trail-M-CRB:~$ for interface in /sys/class/backlight/*; do echo $interface; cat $interface/actual_brightness; cat $interface/max_brightness; cat $interface/brightness; done
/sys/class/backlight/intel_backlight
13046
13046
13046
akik@akik-Pine-Trail-M-CRB:~$

---

### Post by Toz on 2012-07-17
Interesting. Although it seems to have created a backlight interface, you can't seem to manipulate it. Unfortunately, I am out of suggestions. I recommend that you create a bug report against the linux package (kernel):
```
apport-bug linux
```
...and have the developers take a look at it.

---

