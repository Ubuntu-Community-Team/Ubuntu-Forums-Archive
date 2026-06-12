---
title: "[SOLVED] Proprietary driver installer just dorta hangs"
date: 2008-12-28
forum: Installation &amp; Upgrades
---

### Post by y0diggity on 2008-12-28
Hey guys, sorry if this has been answered before, but I tried searching and just couldn't come up with anything.

I just got 8.10 installed on one of our laptops (brings us to 2 total Linux machines :) ) and I'm trying to enable the proprietary nvidia drivers on it. The problem is that the hardware driver application will run and it will show me the 3 available drivers but when I tell it to activate one it pops up the progress box, says it's downloading and installing the driver, and then just sits there at 0% until it apparently times out. If I close the hardware driver application and then try to reopen it, it won't even load up. I have to reboot to get it to pop up again. If I try to install another driver without closing the hardware driver application, it still won't do anything.
It gives me 3 options for drivers, and it doesn't matter which one I pick, it does the same thing.
I hope this is sort of clear. I could sure use some help. I'm not sure exactly which video card it is and I'm even less sure about how to go about finding that information out. Any help in solving this problem would be appreciated.
Thanks, you folks here are great!

---

### Post by pytheas22 on 2008-12-28
The most obvious thing to check, since you say that it hangs at 0% when download, is to be sure that you have a working Internet connection on the machine.  You verified that, right?

If you're sure that the network is connected, I'd recommend using [envy]("http://www.albertomilone.com/nvidia_scripts1.html") to install your drivers.  It usually does a better job than the native Ubuntu utility.  You can install envy by typing in a terminal:

```
sudo apt-get update
sudo apt-get install envyng-gtk

```
Then run it with:
```

sudo envyng-gtk
```

It will automatically download the best driver for your card.  It doesn't work 100% of the time, but in general I've had very good luck with it.

If that doesn't work, let us know.

---

### Post by y0diggity on 2008-12-28
I tried running envy like you said. 
I started it from the command line and it fired up just fine, but then when I selected the driver, it popped up the window that shows its progress and it hung. I looked over at the terminal window that was still open and it was just streaming "command could not be parsed" all the way up and it was a continuous and fast stream of this same statement.

Any ideas?
Here's a screenshot.
[IMG]http://digitalmonotony.com/wp-content/uploads/envyng.jpg[/IMG]

---

### Post by y0diggity on 2008-12-28
Also, if it helps at all, I ran the envyng app in the CLI and here was the response:

 ```
+------------------------------------------------------------------------------+
 | Number | Candidate Version    | Installed Version | Compatible | Recommended |
 |------------------------------------------------------------------------------|
 | 0      | 177.80-0ubuntu2      | -                 | +          | -           |
 |------------------------------------------------------------------------------|
 | 1      | 173.14.12-1-0ubuntu4 | -                 | +          | +           |
 |------------------------------------------------------------------------------|
 | 2      | 96.43.09-0ubuntu1    | -                 | +          | -           |
 |------------------------------------------------------------------------------|
 | 3      | 71.86.04-0ubuntu10   | -                 | -          | -           |
 +------------------------------------------------------------------------------+
Please select the number corresponding to the desired driver and press ENTER 
(or type another number and press Enter to go back to the previous menu): 
0

Dowloading the packages...
[===================================57.1%====>                                 ]result could not be parsed
Error in function pulse
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/Envy/packagemanager.py", line 75, in pulse
    self.newObject.updateUi(percent)
  File "interface.py", line 65, in updateUi
    numHashes = int(round(numHashes))
TypeError: an integer is required
/usr/bin/envyng: line 4:  5978 Segmentation fault      sudo python interface.py
xxxxx@xxxx-laptop:~$ 
```

---

### Post by pytheas22 on 2008-12-28
hmmm, this is weird.  I don't know if it's a coincidence that both envy and the Ubuntu utility are failing.

Please post the output of this command:
```

lspci -nn
```

I think that googling around a bit for information on your graphics card might be the most logical next step, instead of trying to fight anymore with these programs.  Hopefully someone else has had problems with your card in the past and figured out how to solve them.

---

### Post by y0diggity on 2008-12-28
here's the output.
```
00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f3] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation MCP51 PCI-X GeForce Go 6100 [10de:0247] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
06:09.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185] (rev 20)

```

---

### Post by pytheas22 on 2008-12-28
This [bug report]("https://bugs.launchpad.net/ubuntu/+source/restricted-manager/+bug/99291") sounds like it hits your problem on the head--you have the same exact graphics card.

One user there says that following the instructions [here]("https://help.ubuntu.com/community/MythTV/Install/Live/Feisty+/Hardware/Video_Nvidia?highlight=(feisty)|(nvidia)") got the proprietary drivers installed manually.  That information is for Ubuntu 7.04, but I think it should still work in 8.10.  Could you please give it a try?

---

### Post by y0diggity on 2008-12-28
Thanks. I was out looking as well and [found this page]("http://ubuntuforums.org/archive/index.php/t-897344.html") that is basically a walkthrough of getting rid of any old attempts that had previously failed and then installing the nvidia driver from their website. Worked like a charm. Thanks so much for taking the time to look at this with me and help me navigate through it.

---

