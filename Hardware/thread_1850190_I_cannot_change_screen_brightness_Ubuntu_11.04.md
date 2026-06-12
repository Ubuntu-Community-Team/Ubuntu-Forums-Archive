---
title: "I cannot change screen brightness Ubuntu 11.04"
date: 2011-09-26
forum: Hardware
---

### Post by gustokonyan on 2011-09-26
Hi,

I just purchased a new laptop, Acer 4830TG. I installed ubuntu 11.04 right away. Problem is no matter how i set screen brightness, it does not work. My laptop keeps on max brightness i think.

Fn key displays the brightness  bar changing as i press the left and arrow keys, but the brightness does not change.

I also tried battery preferences as well as Ubuntu tweak, nothing works.


Can anyone please help? Thank you

---

### Post by gustokonyan on 2011-09-26
anyone please...?

---

### Post by Redblade20XX on 2011-09-26
Can you list your graphics card? Do you have it's proprietary driver installed or the Ubuntu defaults?

---

### Post by matt_symes on 2011-09-26
Hi

Open a terminal and type

```
sudo bash -c "echo -n 50 > /proc/acpi/video/*/LCD/brightness" 
```

Does this change the brightness ?

Type this to put it back if it does.

```

sudo bash -c "echo -n 100 > /proc/acpi/video/*/LCD/brightness" 
```

Kind regards

---

### Post by gustokonyan on 2011-09-26
> **Redblade20XX said:**
> Can you list your graphics card? Do you have it's proprietary driver installed or the Ubuntu defaults?

Hi, here's what lspci says

```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 3 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df4 (rev a1)
02:00.0 Ethernet controller: Atheros Communications Device 1083 (rev c0)
03:00.0 Network controller: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)
04:00.1 SD Host controller: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)
05:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
```

I did not install any additional drivers (it was prompted though). So i am using ubuntu default drivers

---

### Post by gustokonyan on 2011-09-26
> **matt_symes said:**
> Hi

Open a terminal and type

```
sudo bash -c "echo -n 50 > /proc/acpi/video/*/LCD/brightness" 
```Does this change the brightness ?

Type this to put it back if it does.

```

sudo bash -c "echo -n 100 > /proc/acpi/video/*/LCD/brightness" 
```Kind regards

hello, i tried this but gave the following error:
```
bash: /proc/acpi/video/*/LCD/brightness: No such file or directory
```

---

### Post by gustokonyan on 2011-09-26
Thank you guys for replying, but i have to go to bed now. it is 30mins to midnight here :)

I will reply back as soon as possible.

Again, thanks!

---

### Post by matt_symes on 2011-09-26
Hi

> **gustokonyan said:**
> hello, i tried this but gave the following error:
```
bash: /proc/acpi/video/*/LCD/brightness: No such file or directory
```

What is the result of 

```
ls /proc/acpi/video/
```

Kind regards

---

### Post by gustokonyan on 2011-09-26
It says "No such file or directory".

ls on /proc/acpi says
```
ac_adapter  battery  button  event  wakeup
```

---

### Post by matt_symes on 2011-09-26
Hi

On my machine (ubuntu 10.04)

```
matthew@matthew-laptop:/sys/bus/usb$ ls /proc/acpi/
ac_adapter  battery  button  dsdt  embedded_controller  event  fadt  fan  info  power_resource  processor  sleep  thermal_zone  video  wakeup
matthew@matthew-laptop:/sys/bus/usb$ 

```

I can only assume you have a different version of Ubuntu.

Lets try with /sys.

```
matthew@matthew-laptop:/sys/bus/usb$ sudo bash -c "echo -n 5 > /sys/class/backlight/acpi_video0/brightness"
matthew@matthew-laptop:/sys/bus/usb$ sudo bash -c "echo -n 9 > /sys/class/backlight/acpi_video0/brightness"

```

You might have to change acpi_video0 if it is different on your machine.

Kind regards

---

### Post by Toz on 2011-09-26
This link: [http://ubuntuforums.org/showthread.php?t=1836945]("http://ubuntuforums.org/showthread.php?t=1836945") suggests using the **acpi_osi=Linux** kernel parameter to solve the brightness issue.

---

### Post by gustokonyan on 2011-09-27
Thank you guys for taking your time to help me with this problem. I originally planned to use ubuntu as my primary OS (as i did on my previous lappy) but i do not want to work with max brightness all the time. So I have now set up my system using win7 and installed all the apps i need for work. I seem to enjoy win7 so far.

I will look into fixing this when time permits..


Again thank you all for your help. It is highly appreciated ;)

---

### Post by gustokonyan on 2011-09-30
> **Toz said:**
> This link: [http://ubuntuforums.org/showthread.php?t=1836945](http://ubuntuforums.org/showthread.php?t=1836945) suggests using the **acpi_osi=Linux** kernel parameter to solve the brightness issue.

thank you. this solution worked!

---

### Post by Toz on 2011-09-30
Glad to hear it worked. Can you please mark the thread as solved from the Thread Tools link above?

---

### Post by ranger1021994 on 2012-07-23
> **gustokonyan said:**
> Hi,

I just purchased a new laptop, Acer 4830TG. I installed ubuntu 11.04 right away. Problem is no matter how i set screen brightness, it does not work. My laptop keeps on max brightness i think.

Fn key displays the brightness  bar changing as i press the left and arrow keys, but the brightness does not change.

I also tried battery preferences as well as Ubuntu tweak, nothing works.


Can anyone please help? Thank you


[http://wilmor24.wordpress.com/2010/05/11/change-screen-brightness-from-terminal-ubuntu-10-04/](http://wilmor24.wordpress.com/2010/05/11/change-screen-brightness-from-terminal-ubuntu-10-04/)

The process maybe same because terminal commands do not change with new releases

---

### Post by Toz on 2012-07-23
This thread is 10 months old and resolved. Closing.

---

