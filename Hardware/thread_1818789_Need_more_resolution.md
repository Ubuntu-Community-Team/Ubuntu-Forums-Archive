---
title: "Need more resolution"
date: 2011-08-05
forum: Hardware
---

### Post by ketanmalvankar on 2011-08-05
Hi ,
I am using Ubuntu 11.04,I have intel cantiga graphics controller,My kernel is loading vesa driver,I am getting resolution of 1024x768,Intel cantiga can support up to 1366x768 but I am not getting it. I tried to add new mode also with xrandr but not getting. I have attached xorg log file and output of following commands in their respective file,pls help me.
lspci -v 
sudo lshw

---

### Post by realzippy on 2011-08-05
...Your log file says:
*Using config file: "/etc/X11/xorg.conf"*

..so it is not the kernel choosing the vesa-driver.
Please show the xorg.conf...
Did you create the file?

Btw,1366x768 is not a valid VESA mode,so it cannot work using VESA driver.

---

### Post by ketanmalvankar on 2011-08-07
Yes I have created this file with x -configure command,I have attached xorg.conf file here.  What do I do to set my native resolution.

---

### Post by realzippy on 2011-08-07
The xorg.conf indeed needs some editing....  ;-)
Will post a suggestion in a few hours,in the moment I am busy..

What happens when you boot without xorg.conf ?

---

### Post by ketanmalvankar on 2011-08-07
same thing happens...cant see 1366x768 resolution.

---

### Post by realzippy on 2011-08-07
Can you show output from

```
xrandr -q
```

when booting without xorg.conf ?

---

### Post by ketanmalvankar on 2011-08-07
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0*

---

### Post by realzippy on 2011-08-07
..and your Xorg.0.log without booting xorg.conf ?

---

### Post by ketanmalvankar on 2011-08-07
File attached here

---

### Post by realzippy on 2011-08-07
Try this only (as xorg.conf) :

```
Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
        HorizSync       28.0 - 51.0
        VertRefresh     56.0 - 60.0
        Modeline "1366x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
EndSection

Section "Device"
	Identifier  "Card0"
	Driver      "intel"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     24
                Modes        "1366x768_60" "1024x768"
                Modeline "1366x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
	EndSubSection
EndSection

```

Please also run:
```
mv ~/.config/monitors.xml ~/.config/monitors.xml.old
```
Reboot or restart Xserver..
If it not works,please post Xorg.0.log again..
As mentioned earlier,I am quite busy today in real life,so you might be 
patient.Will also ask [catkiller]("http://ubuntuforums.org/member.php?u=65401") to have a look at this issue
if suggested xorg.conf does not work..

---

### Post by ketanmalvankar on 2011-08-07
I tried with ur xorg.conf file but I got error saying "Parse error on line 24 of section Screen in file /etc/X11/xorg.conf
    "Modeline" is not a valid keyword in this section."
Then I removed that line and tested again, still didn't work, got error as "No devices detected,no screens found"  in log file ,log file is attached here

And one more thing I dont have monitors.xml file in the mentioned path :(

---

### Post by realzippy on 2011-08-07
Wasn't that Xorg.1.log instead of Xorg.0.log ?
Try:
```
Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
        HorizSync       28.0 - 51.0
        VertRefresh     56.0 - 60.0
        Modeline "1366x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
EndSection

Section "Device"
	Identifier  "Card0"
	Driver      "intel"
	BusID       "PCI:0:2:0"
        Option      "ModeDebug"            "True"  #don't know if works on intel,but should give a clue in xorg log file
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     24
                **Virtual	1366 768**
                Modes        "1366x768_60" "1024x768"
	EndSubSection
EndSection
```


..and post Xorg.**0**.log

No monitors.xml is fine,that's what I wanted...

---

### Post by ketanmalvankar on 2011-08-07
it was xorg.1.log file.

---

### Post by ketanmalvankar on 2011-08-07
I tested again with ur changes but got again same error screen not found then I removed the xorg.conf file and started again. both the log files are attached here.

---

### Post by realzippy on 2011-08-07
modify

Driver      "intel"

to

Driver      "vesa"

or

Driver      "fbdev"

what happens ?
As you might have guessed,I am puzzled.

**Edit:**
edited xorg.conf in #12

---

### Post by realzippy on 2011-08-07
found this:
[http://ubuntuforums.org/showthread.php?t=1013929](http://ubuntuforums.org/showthread.php?t=1013929)

...so it used to work in the good old days before KMS.

---

### Post by ketanmalvankar on 2011-08-07
I tried with this, and I was getting 1366x768 resolution but screen was not at all properly visible,I was able to see vertical and horizontal lines with four mouse pointer :( :(  Then I deleted xorg.conf file. I have attached log file here. If u see in log file u can find "Not using mode "1366x768_60" (no mode of this name)" I used vesa driver. For fbdev X was not starting

---

### Post by realzippy on 2011-08-07
Can you post the xorg.conf where 1366x768 worked?


*"Not using mode "1366x768_60" (no mode of this name)" I used vesa driver*

what did xrandr "say" there ?Did you use the modeline?

---

### Post by ketanmalvankar on 2011-08-07
in none of the file 1366x768 worked.

---

### Post by realzippy on 2011-08-07
*I tried with this, and I was getting 1366x768 resolution but screen..*

Ok,screen was garbled,4 mousepointers aso..But which xorg.conf was this?

---

### Post by ketanmalvankar on 2011-08-07
File attached here..

---

### Post by ketanmalvankar on 2011-08-07
sorry driver was vesa instead of fbdev, When I use fbdev X doesn't start

---

### Post by realzippy on 2011-08-07
```
Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
        HorizSync       28.0 - 51.0
        VertRefresh     50.0 - 65.0
EndSection

Section "Device"
	Identifier  "Card0"
	Driver      "vesa"
	BusID       "PCI:0:2:0"
	Option      "ModeDebug"            "True"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Virtual	1366 768
                Modes  "1024x768"
        EndSubSection
EndSection
```


If this starts,show
```
xrandr -q
``` 
output.

---

### Post by ketanmalvankar on 2011-08-07
screen was not still proper but then some how I managed to capture the output, output is as follows

Screen 0: minimum 640 x 480, current 1368 x 768, maximum 1368 x 768
default connected 1368x768+0+0 0mm x 0mm
   1024x768       61.0  
   800x600        61.0  
   640x480        60.0  
   1368x768       61.0*

---

### Post by realzippy on 2011-08-07
Your monitor's DDC reports this modeline in the log:

[  1045.256] (II) VESA(0): Printing DDC gathered Modelines:
[  1045.256] (II) VESA(0): Modeline "1366x768"x0.0   72.33  1366 1414 1446 1526  768 770 775 790 -hsync -vsync (47.4 kHz)

Try:
```

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
        HorizSync       28.0 - 51.0
        VertRefresh     50.0 - 65.0
        Modeline "1366x768"   72.33  1366 1414 1446 1526  768 770 775 790 -hsync -vsync
EndSection

Section "Device"
	Identifier  "Card0"
	Driver      "vesa"
	BusID       "PCI:0:2:0"
	Option      "ModeDebug"            "True"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Virtual	1366 768
                Modes  "1366x768" "1024x768"
        EndSubSection
EndSection
```

---

### Post by ketanmalvankar on 2011-08-07
same bad screen again :( :(

---

### Post by realzippy on 2011-08-07
```
Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
        HorizSync       28.0 - 51.0  # added to make modeline possible (47.5 khz)
        VertRefresh     50.0 - 65.0
        DisplaySize    320 190   #added as act of desperation
        Modeline "1366x768"   72.33  1366 1414 1446 1526  768 770 775 790 -hsync -vsync   #reported from DDC in Xorg.x.log
EndSection

Section "Device"
	Identifier  "Card0"
	Driver      "vesa"
	BusID       "PCI:0:2:0"
	Option      "ModeDebug"            "True"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Virtual	1366 768   #added to increase xrandr maximum size
                Modes  "1366x768" "1024x768"
        EndSubSection
EndSection
```

Added display size.
Please also try "intel" instead of "vesa".Post both Xorg.0.logs..
Sent a pm to catkiller,maybe he has an idea...

---

### Post by ketanmalvankar on 2011-08-07
I tested with both the options as u mentioned, but nothing worked :( I have attached both the log files here.

---

### Post by ketanmalvankar on 2011-08-07
For intel driver X didn't start.

---

### Post by realzippy on 2011-08-07
And for vesa 1366x768  seems not possible,although vesa is
capable of 1440x900 eg...

Can you start without xorg.conf
and show output from:
```
lshw -C display
```

---

### Post by ketanmalvankar on 2011-08-07
*-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:5110(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:d3400000-d34fffff

---

### Post by realzippy on 2011-08-07
Maybe the intel module isn't loaded for your device.
Under configuration it should be something like:

```
configuration: **driver=i915** latency=0
```


Have you ever edited your machine's boot options?
nomodeset or something?Show
```
lsmod | grep i915
```

Eg here your graphics chipset did work fine:
[http://ubuntuforums.org/showpost.php?p=10158105&postcount=1](http://ubuntuforums.org/showpost.php?p=10158105&postcount=1)
so it should be possible somehow.

---

### Post by ketanmalvankar on 2011-08-07
yes I have done following
"options i915 modeset=0" in "/etc/modprobe.d/i915-kms.conf"
If I dont set this, my screen becomes blank :(

---

### Post by ketanmalvankar on 2011-08-07
$ lsmod | grep i915
i915                  450934  0 
drm_kms_helper         40745  1 i915
drm                   180037  2 i915,drm_kms_helper
i2c_algo_bit           13184  1 i915
video                  18951  1 i915

---

### Post by realzippy on 2011-08-07
OMG.
Good that I have asked...
You disabled the intel driver.
You should undo this,and start with an intel xorg.conf,maybe the last one.
If black screen,post xorg log file.
I will be out for about 120 minutes,since I have to watch soccer now...
;-) ..back in the evening.

---

### Post by ketanmalvankar on 2011-08-07
When I remove i915.modset=0.blank display comes up :( I have attached xorg.0.log file here.

---

### Post by ketanmalvankar on 2011-08-07
yahoooooooooooo,
it worked... :) :) :)
I removed i915.modset=0
, I added following two lines to get rid of blank display problem.
gamma 0.8 0.8 0.8
    Option "DPMS"

Thanks alot bro, I really thank u for ur help...thank u so much 

here is my xorg.conf file

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
        HorizSync       28.0 - 51.0  # added to make modeline possible (47.5 khz)
        VertRefresh     50.0 - 65.0
        DisplaySize    320 190   #added as act of desperation
        Modeline "1366x768"   72.33  1366 1414 1446 1526  768 770 775 790 -hsync -vsync   #reported from DDC in Xorg.x.log
    gamma 0.8 0.8 0.8
    Option "DPMS"
EndSection

Section "Device"
    Identifier  "Card0"
    Driver      "intel"
    BusID       "PCI:0:2:0"
    Option      "ModeDebug"            "True"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Virtual    1366 768   #added to increase xrandr maximum size
                Modes  "1366x768" "1024x768"
        EndSubSection
EndSection

---

### Post by realzippy on 2011-08-07
Great.Good job!
..was just about your logfile when I noticed you posted again.
It would be great (for others,me,and the future :D ) if you could
test by outcommenting (#) the options you added one by one so
we know which one did the trick (gamma or dpms).
Btw,where you got the idea from ? (gamma 0.8 0.8 0.8)
Guess it is dpms,but we will see.
Ever thought dpms would only be important for standby-stuff..
Also think the display size and virtual size I added is not necessary..
so if you would like to make the solution perfect... ;-)

---

### Post by ketanmalvankar on 2011-08-08
Sure,I'll find out which one did the trick, rite now I am in office, I'll reach home only after 10hrs from now. Once I reach I'll let u know. 
For gamma 0.8 0.8 0.8, I really dont know what it is:confused:, I just googled and found some where, I don even remember the link....
Thanks again I am bit relaxed now I was working on this issue since past one months finally got resolved :) :P:guitar:

---

### Post by realzippy on 2011-08-22
Just cleaning up my subscribed threads.
Please set thread as solved (ThreadTools)...thanks

---

### Post by umerlone on 2011-08-23
Hi,

I see you were so good to solve the problem.

I have basically the same problem on a Lenovo X220 with Ubuntu 10.04 ( I did not install 11.04 as it does not let me use a dual monitor)

I do not have xorg.conf in /etc/X11. :confused:

As you probably figure I am pretty a caveman on Ubuntu.

Can anybody suggest me a way in my case without having to work through the entire process?
Thanks a lot

Ugo

---

### Post by umerlone on 2011-09-01
Actually my problem was solved on the thread

Ubuntu 10.04 on Lenovo Thinkpad i5 X220

Ugo

---

