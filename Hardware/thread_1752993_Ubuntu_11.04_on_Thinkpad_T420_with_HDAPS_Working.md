---
title: "Ubuntu 11.04 on Thinkpad T420 with HDAPS Working"
date: 2011-05-08
forum: Hardware
---

### Post by le_gudeg on 2011-05-08
I've got Thinkpad T420 with the Core i5 2410 2.4 GHZ and Intel HD 3000 (not the dual graphic model)

Laptop Review:

+ Great Build
+ Super Keyboard
+ Good Performance (for working, not gaming)
+ Quite ok battery life

- LCD has bad vertical quality (washed out if you look at it slightly from above) 

Weight is around Unibody MBP 15

**Working Out of The Box:**
  
Suspend
Hibernate
All of the fn-function keys
Trackpoint
Trackpad
Bluetooth
Wifi
Card Reader
Intel HD 3000
DVD Drive 
Sound

** Working But Need Some Hacking:**

**  Active Protection System:**

what you need: thinkpad_ec (tp_smapi, hdaps) and hdapsd

tp_smapi  from apt is not working, when you do "modprobe tp_smapi" it will return error: device not found 

**Solution**:

1.```
 sudo apt-get install module-assistant
```2.```
 apt-get source tp-smapi-source #no sudo here 
```3.```
 cd tp-smapi-0.40
```4. open "thinkpad_ec.c" with your favorite code editor 

around line 475 there are:

```

if (!check_dmi_for_ec()) {
        printk(KERN_WARNING
               "thinkpad_ec: no ThinkPad embedded controller!\n");
        return -ENODEV;
}

```Just put comment around it (or you can just comment the return -ENODEV)

```

/*
if (!check_dmi_for_ec()) {
        printk(KERN_WARNING
               "thinkpad_ec: no ThinkPad embedded controller!\n");
        return -ENODEV;
 }*/

```One more thing: around line 459 there are struct:

```

struct dmi_system_id tp_whitelist[] = {
        TP_DMI_MATCH("IBM", "ThinkPad A30"),
        TP_DMI_MATCH("IBM", "ThinkPad T23"),
        TP_DMI_MATCH("IBM", "ThinkPad X24"),
        TP_DMI_MATCH("IBM", "Thinkpad T420"), // add this line here
        { .ident = NULL }
    };

```5. After done patching the source code you can do this: 

```


cd ../

apt-get --build source tp-smapi-source
```6. It will generate tp-smapi-dkms.deb and tp-smapi-source.deb, for the sake of simplicity just install the   dkms: 

```
sudo dpkg -i tp-smapi-dkms_0.40-9_all.deb
```7.  ```
sudo modprobe tp_smapi
```and 

```
sudo modprobe hdaps
```8. ```
 lsmod | grep -i thinkpad_ec
```it should return thinkpad_ec with tp_smapi and hdaps listed.

9. Edit /etc/rc.local and put:
 
```

modprobe tp_smapi
modprobe hdaps

```10. Install hdaps-gl if you wanted to test the sensor (it needs freeglut dev to compile)

11. if you don't want to bother with source file, just install the  attached tp-smapi.tar.gz (extract it first, and go to step 6).

That's all for tp-smapi now let's go to hdapsd

**HDAPSD**

hdapsd handle the disk parking features:

```
sudo apt-get install hdapsd
```Run "sudo hdapsd" and spank your thinkpad real hard, see whether hdapsd return "parking" in your console. 

Another way to test is to run "find /" on the console and move your laptop during the process, it should stop for a while and then resume.

** Power Management:**

Do what mentioned on the link if you want to conserve battery:
[COLOR=DarkOrange]
[https://help.ubuntu.com/community/PowerManagement/ReducedPower](https://help.ubuntu.com/community/PowerManagement/ReducedPower)[/COLOR] 

I managed to get between 10 watt - 13 watt when running on battery (from powertop) 

**Fingerprint Reader**

fprint in Ubuntu is obsolete

```


sudo add-apt-repository ppa:fingerprint/fprint

sudo aptitude update

sudo aptitude install libfprint0 libpam-fprintd

```Change you fingerprint login from About Me

**Trackpoint scrolling**

```


cd /usr/share/X11/xorg.conf.d/

sudo vim 20-thinkpad.conf # can use gedit instead of vim but error on emacs :P


```Add this into the new file:

```

Section "InputClass"
    Identifier    "Trackpoint Wheel Emulation"
    MatchProduct    "TPPS/2 IBM TrackPoint|DualPoint Stick|Synaptics Inc. Composite TouchPad / TrackPoint|ThinkPad USB Keyboard with TrackPoint|USB Trackpoint pointing device|Composite TouchPad / TrackPoint"
    MatchDevicePath    "/dev/input/event*"
    Option        "EmulateWheel"        "true"
    Option        "EmulateWheelButton"    "2"
    Option        "Emulate3Buttons"    "false"
    Option        "XAxisMapping"        "6 7"
    Option        "YAxisMapping"        "4 5"
EndSection

```[B]

Better Intel HD 3000 Driver

[/B][http://phoronix.com/forums/showthread.php?50038-Updated-and-Optimized-Ubuntu-Free-Graphics-Drivers](http://phoronix.com/forums/showthread.php?50038-Updated-and-Optimized-Ubuntu-Free-Graphics-Drivers)
[B]

Not Yet Working:[/B]

External Monitor

Somehow hot left palm rest (overactive HDD??)
[B]
Bibliography:[/B]

[http://www.thinkwiki.org/](http://www.thinkwiki.org/)
[http://lists.freebsd.org/pipermail/freebsd-current/2008-March/084573.html](http://lists.freebsd.org/pipermail/freebsd-current/2008-March/084573.html)
[http://forum.thinkpads.com/viewtopic.php?f=45&t=95974](http://forum.thinkpads.com/viewtopic.php?f=45&t=95974)
[https://help.ubuntu.com/community/PowerManagement/ReducedPower](https://help.ubuntu.com/community/PowerManagement/ReducedPower)

---

### Post by bsomers on 2011-05-13
Thanks a lot!!

I have problems with changing screen resolution after docking the T420. When I get home, I dock my laptop and after booting the resolution of my laptop is back to default (1024x768), instead of the normal 1600x900. Do you have the same problem?

Regards

Bram

---

### Post by le_gudeg on 2011-05-14
My problem is the laptop just goes hang when I connect the VGA cable and press Fn-F7. The external monitor just didn't show anything, I am using Samsung SyncMaster 2233sw. Fedora 15 is almost released, hope things work more smoothly there.

---

### Post by bsomers on 2011-05-15
yes, mine hangs too then.

But I do not want to change my screen resolution after _each_ reboot (when connected to docking station).

So far I didn't find a solution on google :(

---

### Post by le_gudeg on 2011-05-16
I hope it will be solved with the newer Intel graphic driver for Linux. It's quite possible that the driver will be backported to 11.04, if not then we have to wait until 11.10 or compile it from sources. Other solutions is to add custom ppa described in [http://phoronix.com/forums/showthrea...aphics-Drivers]("http://phoronix.com/forums/showthread.php?50038-Updated-and-Optimized-Ubuntu-Free-Graphics-Drivers")

I got glitch (no panel and dock) the last time I try the phoronix ppa mentioned on the link above, maybe they already update it now, haven't tried it again.

---

### Post by le_gudeg on 2011-05-16
I think the docking station you mentioned also somehow trigger similar event like connecting external VGA cable. If I'm not mistaken the docking station also has extra VGA / DVI port rite? (I don't have the unit now). Maybe you can try to thinker with xorg to set the fixed resolution.

---

### Post by bsomers on 2011-05-17
yes it has an external vga/dvi port.

What do you mean with:

"Maybe you can try to thinker with xorg to set the fixed resolution."?

Regards,

Bram

---

### Post by le_gudeg on 2011-05-17
On the older version of Ubuntu it is usually hard to get the correct screen resolution for your monitor so you have to edit the xorg.conf file manually to get it right. But now it can detect automatically most of the time. Instead of using single xorg.conf file now Ubuntu use many small xorg file located in /usr/share/X11/xorg.conf.d/ to handle various settings and devices. Try to get the documentation about xorg.conf.d or search/ask the forums about it. It deserve another thread of its own.

---

### Post by chx1975 on 2011-06-07
HDAPS might work but power doesn't. (Force discharge, thresholds etc)

---

### Post by chasetoys on 2011-07-13
followed instructions but now i see:

'LilArooni ~/tp-smapi-0.40: sudo modprobe tp_smapi
FATAL: Error inserting tp_smapi (/lib/modules/2.6.38-8-generic/updates/dkms/tp_smapi.ko): No such device"


LilArooni ~/tp-smapi-0.40: sudo modprobe hdaps
FATAL: Error inserting hdaps (/lib/modules/2.6.38-8-generic/updates/dkms/hdaps.ko): No such device
LilArooni ~/tp-smapi-0.40: 

.. any ideas what to do now?  t420 with 11.04 here.

---

### Post by mejo on 2011-07-13
> **chasetoys said:**
> followed instructions but now i see:

'LilArooni ~/tp-smapi-0.40: sudo modprobe tp_smapi
FATAL: Error inserting tp_smapi (/lib/modules/2.6.38-8-generic/updates/dkms/tp_smapi.ko): No such device"


LilArooni ~/tp-smapi-0.40: sudo modprobe hdaps
FATAL: Error inserting hdaps (/lib/modules/2.6.38-8-generic/updates/dkms/hdaps.ko): No such device
LilArooni ~/tp-smapi-0.40: 

.. any ideas what to do now?  t420 with 11.04 here.

you need to patch tp_smapi first, and rebuild the module.

1. install tp_smapi sources: 'sudo apt-get install tp-smapi-dkms'

2. edit the file at /usr/src/tp-smapi-0.40/thinkpad_ec.c, add the following line at line 463:
                TP_DMI_MATCH("LENOVO", "ThinkPad T420"),

3. remove the installed kernel module: 'sudo dkms remove -m tp-smapi -v 0.40 -k $(uname -r)'

4. build the kernel module with modified sources: 'sudo dkms build -m tp-smapi -v 0.40 -k $(uname -r)'

5. install new built kernel module: 'sudo dkms install -m tp-smapi -v 0.40 -k $(uname -r)'

6. load the new installed kernel module: 'sudo modprobe tp-smapi'

---

### Post by jhahoneyk on 2011-07-31
Hi, I am trying to use tp_smapi on my ThinkPad Edge 15, I did the patching and building as detailed, but I still get the error-

```

shaan@shaan-laptop:~/Desktop/tp-smapi$ sudo modprobe tp_smapi 
FATAL: Error inserting tp_smapi (/lib/modules/2.6.38-10-generic-pae/updates/dkms/tp_smapi.ko): No such device or address
```

I tried both TP_DMI_MATCH("LENOVO", "ThinkPad Edge15") and TP_DMI_MATCH("LENOVO", "ThinkPad Edge 15").

Any suggestions?

---

### Post by mejo on 2011-08-02
I posted a status summary about Natty on T420:

[http://ubuntuforums.org/showthread.php?t=1816071](http://ubuntuforums.org/showthread.php?t=1816071)

greetings,
 jonas

---

### Post by le_gudeg on 2011-08-25
> **jhahoneyk said:**
> Hi, I am trying to use tp_smapi on my ThinkPad Edge 15, I did the patching and building as detailed, but I still get the error-

```

shaan@shaan-laptop:~/Desktop/tp-smapi$ sudo modprobe tp_smapi 
FATAL: Error inserting tp_smapi (/lib/modules/2.6.38-10-generic-pae/updates/dkms/tp_smapi.ko): No such device or address
```I tried both TP_DMI_MATCH("LENOVO", "ThinkPad Edge15") and TP_DMI_MATCH("LENOVO", "ThinkPad Edge 15").

Any suggestions?

Hi, could you just download the attached file? Then do: ```
sudo aptitude remove tp-smapi-dkms
``` Next extract the file and install the extracted file: ```
sudo dpkg -i tp-smapi-dkms_0.40-9_all.deb
```Tell me if it's working.

---

### Post by jkrez on 2011-09-07
[Deleted]

---

### Post by adnanyumer on 2012-01-19
How to know it's really working well?

---

### Post by CAPS LOCK CARL on 2012-02-19
Great HDAPS instructions, worked like a charm.

Thinkpad T520
Ubuntu 11.10
tp_smapi is at 0.41 now.

The tp_whitelist in 0.41 now contains an entry for ("LENOVO", "ThinkPad"). I took a guess and added ("IBM", "ThinkPad T520") and ("LENOVO", "ThinkPad T520"). I don't know if this change was necessary, I don't know which of those two, if any, are correct, I don't know if it works without this modification -- I didn't try it. =) But, for reference, mine is:

```

	struct dmi_system_id tp_whitelist[] = {
		TP_DMI_MATCH("IBM", "ThinkPad A30"),
		TP_DMI_MATCH("IBM", "ThinkPad T23"),
		TP_DMI_MATCH("IBM", "ThinkPad X24"),
		TP_DMI_MATCH("IBM", "ThinkPad T520"), /* added */
		TP_DMI_MATCH("LENOVO", "ThinkPad"),
		TP_DMI_MATCH("LENOVO", "ThinkPad T520"), /* added */
		{ .ident = NULL }
	};

```

I did have to install debhelper, quilt, and dkms -- they all worked as-is.

Thanks again!

---

### Post by CAPS LOCK CARL on 2012-02-19
> **adnanyumer said:**
> How to know it's really working well?

Do "find /" and watch it stop when you bump the machine.

As for working **well**... I suppose you could take two identical ThinkPads, load hdaps on one of them, and count how many times you need to throw each one down the stairs before the hard drive crashes. If all goes well, you should get a few more tosses out of the one with hdaps.

---

