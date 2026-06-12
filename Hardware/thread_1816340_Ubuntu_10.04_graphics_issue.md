---
title: "Ubuntu 10.04 graphics issue"
date: 2011-08-01
forum: Hardware
---

### Post by xlandonlinux on 2011-08-01
Hello linux community, I've missed you dearly, as it's been over a year since I've been here.

Anyways, my problem is this;  I just installed Ubuntu 10.04 Lucid Lynx onto an ancient dinosaur, and I'm having graphical issues.  Although the issues lie more in aesthetics than anything, I still observe a lot of window and flash applet flickering.

Also, the "monitors" tool will not detect my monitor.
The computers specs are as follows:

Memory - 1002.3 MiB
Processor - AMD Athlon(tm) XP 2700+
Available disc space - 29.0 GiB


--I can't find any other information because I forgot terminal command to pull all of it up--
     ^ so this would be step one.

Any help is appreciated.

---

### Post by Metaxa on 2011-08-01
Can you please post the output of : 


sudo lshw -C display; lsb_release -a

This should help us understand what we are dealing with.



Metaxa

---

### Post by xlandonlinux on 2011-08-02
> **Metaxa said:**
> Can you please post the output of : 


sudo lshw -C display; lsb_release -a

This should help us understand what we are dealing with.



Metaxa


xlandonlinux@josh-desktop:~$ sudo lshw -C display; lsb_release -a
[sudo] password for xlandonlinux: 
  *-display               
       description: VGA compatible controller
       product: NV34 [GeForce FX 5200]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 bus_master cap_list rom
       configuration: driver=nouveau latency=64 maxlatency=1 mingnt=5
       resources: irq:18 memory:fd000000-fdffffff memory:e8000000-efffffff(prefetchable) memory:fe000000-fe01ffff(prefetchable)
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.3 LTS
Release:    10.04
Codename:    lucid

---

### Post by Metaxa on 2011-08-03
Do you know if you are using the Nvidia drivers or the open source ones? 

Under System->Admin-> Additional drivers is anything listed?

If you use Nvidia's driver you need to use their graphic card program for the settings of your card not the default one in Ubuntu.



Metaxa

---

### Post by xlandonlinux on 2011-08-03
> **victor1234 said:**
> Wow this such a great post and the tips are very comprehensive. For sure many entrepreneurs with small and big businesses are going to benefit from this. Thanks for sharing your comments

Thank you, kindly.  :D

---

### Post by xlandonlinux on 2011-08-03
> **Metaxa said:**
> Do you know if you are using the Nvidia drivers or the open source ones? 

Under System->Admin-> Additional drivers is anything listed?

If you use Nvidia's driver you need to use their graphic card program for the settings of your card not the default one in Ubuntu.



Metaxa


Here's a picture of what came up.
I'm sorry for not knowing much about this issue.  I really wish I could make this easier for you.

[[IMG]http://img402.imageshack.us/img402/5849/driversu.png[/IMG]]("http://imageshack.us/photo/my-images/402/driversu.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")

I hope thats the right thing to pull up, there is no location called "Additional Drivers."

---

### Post by xlandonlinux on 2011-08-03
Okay, so I did some research to see if I could fix this.

I went to the nVidia website and used the driver selection tool.  I downloaded the driver relative to the card I'm using.

Now another issue.  I have a ".run" file.
I've been google'ing for about 30 minutes, and I can't find out any DETAILED information on how to execute this ".run" file.

Sorry if I sound aggravated, I'm pissed beyond belief,  


*haven't had my morning cigarette yet.

---

### Post by realzippy on 2011-08-03
?
why don't you install the driver offered (as your screenshot shows) ??

---

### Post by xlandonlinux on 2011-08-03
> **realzippy said:**
> ?
why don't you install the driver offered (as your screenshot shows) ??

Because then my resolution wont exceed 600x800.

---

### Post by realzippy on 2011-08-03
> **xlandonlinux said:**
> Because then my resolution wont exceed 600x800.

...this is to fix easily.Install the 173.xx driver,reboot,and post again.
Tell us which monitor model you use then.

---

### Post by xlandonlinux on 2011-08-03
> **realzippy said:**
> ...this is to fix easily.Install the 173.xx driver,reboot,and post again.
Tell us which monitor model you use then.


Completely butchered resolution and display, cannot do anything easily because resolution is terrible.  Have a look.


[[IMG]http://img18.imageshack.us/img18/1210/resolution.png[/IMG]](http://imageshack.us/photo/my-images/18/resolution.png/)

Uploaded with [ImageShack.us](http://imageshack.us)


Really losing my patience with this issue.
:|

---

### Post by realzippy on 2011-08-03
Which monitor model do you use?
I need to know this to help you ....

---

### Post by xlandonlinux on 2011-08-03
It's an old ViewSonic Professional Series PF775.

But when I was running windows, I was open to almost any resolution on the same card.

---

### Post by realzippy on 2011-08-03
run in terminal
```
gksudo gedit /etc/X11/xorg.conf
```

and post file 's content.

---

### Post by xlandonlinux on 2011-08-03
> **realzippy said:**
> run in terminal
```
gksudo gedit /etc/X11/xorg.conf
```and post file 's content.

It's empty.
The file has nothing in it.  This is so bothersome.

---

### Post by realzippy on 2011-08-03
Did you reboot after installing the driver?

If so,
close the empty file and run:

```
sudo nvidia-xconfig
```

when done,open xorg.conf again.
Note that you can use the cursor up/down keys to browse through already typed commands in the terminal.

---

### Post by xlandonlinux on 2011-08-03
I'm also going to upgrade from 10.04 to 11.04.

Don't know how long that will take.

---

### Post by xlandonlinux on 2011-08-03
> **realzippy said:**
> Did you reboot after installing the driver?

If so,
close the empty file and run:

```
sudo nvidia-xconfig
```when done,open xorg.conf again.
Note that you can use the cursor up/down keys to browse through already typed commands in the terminal.

I will do it asap, I uninstalled the driver for the duration of time it would take for a solution, give me 45 minutes.

---

### Post by realzippy on 2011-08-03
No!!!!!!!!!!
This command **will not work if you uninstall the** driver.
If you have already,then I do not wonder why there is no xorg.conf.
Do exactly what I tell you if you want to get this solved.

---

### Post by xlandonlinux on 2011-08-03
> **realzippy said:**
> No!!!!!!!!!!
This command **will not work if you uninstall the** driver.
If you have already,then I do not wonder why there is no xorg.conf.
Do exactly what I tell you if you want to get this solved.

Okay.
Give me some time.

Sorry, I'm trying to juggle 5 tasks at once, so my head is full.

---

### Post by realzippy on 2011-08-03
We can solve this also with uninstalled driver,but
I have to know then **if** it is already installed or **not**.
Relax....

---

### Post by xlandonlinux on 2011-08-03
> **xlandonlinux said:**
> Okay.
Give me some time.

Sorry, I'm trying to juggle 5 tasks at once, so my head is full.

Okay, so this is the result of xorg.conf:

```
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

```

---

### Post by realzippy on 2011-08-03
Ok,now add:

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Viewsonic"
    ModelName      "PF775"
    HorizSync       30.0 - 97.0
    VertRefresh     50.0 - 180.0
EndSection

so it looks like:

```
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Viewsonic"
    ModelName      "PF775"
    HorizSync       30.0 - 97.0
    VertRefresh     50.0 - 180.0
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection
```

Close file saving changes.
Reboot (or restart Xserver)
Your resolutions should be available then in nvidia-settings.

---

### Post by realzippy on 2011-08-03
> **xlandonlinux said:**
> I'm also going to upgrade from 10.04 to 11.04.


This is a bad idea.
The 173 driver is blacklisted in 11.04..
You will not be able to run Unity,and you will not be able
to have desktop effects in classic mode.
You could upgrade to 10.10... (but why?)
Note that your graphics card reaches EOL....

---

### Post by xlandonlinux on 2011-08-03
> **realzippy said:**
> This is a bad idea.
The 173 driver is blacklisted in 11.04..
You will not be able to run Unity,and you will not be able
to have desktop effects in classic mode.
You could upgrade to 10.10... (but why?)
Note that your graphics card reaches EOL....

Thank you for the notice.

I just turned the computer back on, my resolution is still terrible and I cannot change it.
This is all quite confusing.

*sorry I took so long, made lunch.

---

### Post by realzippy on 2011-08-03
Please show me the edited xorg.conf ....maybe typo?

```
gedit /etc/X11/xorg.conf
```

---

### Post by xlandonlinux on 2011-08-03
> **realzippy said:**
> Please show me the edited xorg.conf ....maybe typo?

```
gedit /etc/X11/xorg.conf
```

Here you go;

```
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Viewsonic"
    ModelName      "PF775"
    HorizSync       30.0 - 97.0
    VertRefresh     50.0 - 180.0
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection
```

---

### Post by realzippy on 2011-08-03
Please run
```
sudo nvidia-xconfig
```

post the terminal's output when you run the command.
Also post xorg.conf again (it should have changed then)

---

### Post by xlandonlinux on 2011-08-03
> **realzippy said:**
> Please run
```
sudo nvidia-xconfig
```post the terminal's output when you run the command.
Also post xorg.conf again (it should have changed then)


Terminal output;
 
```
xlandonlinux@josh-desktop:~$ sudo nvidia-xconfig
[sudo] password for xlandonlinux: 

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Undefined Device "(null)" referenced by
                  Screen "Default Screen".

Backed up file '/etc/X11/xorg.conf' as
'/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

xorg.conf;

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder75)  Sun Nov  8 21:50:38 PST 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by realzippy on 2011-08-03
That looks good.
Reboot...

---

### Post by xlandonlinux on 2011-08-03
> **realzippy said:**
> That looks good.
Reboot...


You have just fixed an issue I have been having for days.

Thank you so very much, I wish I could show my thanks.

Ah, everything looks so much better and smoother.  :D

---

### Post by realzippy on 2011-08-03
No,*you* did solve your issue (with a little help) :)
*If* you should upgrade to 10.10,uninstall the nvidia -driver before doing so.
Imho,I see no advantage in 10.10 for you.Remember:
Never change a running system....

---

