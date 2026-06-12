---
title: "Ubuntu-Budgie 17.04 Cannot recognize Wires/wireless nor any Audio devices"
date: 2017-08-15
forum: Hardware
---

### Post by shistar12345 on 2017-08-15
(Please do not move this to Ubuntu-Budgie forums, this is not a Budgie issue it seems, or if it is, the hardware sub-forum would have more idea of the problem)

I am on my windows right now because I cannot even find a wireless or Wired connection for my ubuntu. I cannot find any audio devices.

This is not a first time install, I've had Ubuntu-Budgie 17.04 since April and it has been running smoothly since.

I also do not run wireless ever, I am ethernet hook-up all the time. So this isn't particularly a wireless problem, it just happens to be associated with the issue.]


** Okay let me start out by saying, this problem hasn't happened before.**
My cpu radiator needed a cleaning as well as the graphics card unit heatsink/fan. So I decided to do a cleaning yesterday.
I put it all back together. (water cleaned the heatsinks [ and yes I did wait for it to dry ])
-
During this stage, I also changed the wireless pass-code, just because I usually change it every couple of months.
-
After that I waited a few hours before turning on my PC (in other words I went to sleep for the night).
Logged into windows first. No issues with anything. Audio worked fine. Ethernet normal as ever.
Headed over to my Ubuntu-Budgie 17.04 to find a couple serious problems.

First, the ethernet was not recognizable. For some odd reason it kept saying no networks available and it was specifically trying to 
access my wireless connection (though I've never connected wireless, or even put in a pass-code for the connection). I checked settings and what not; did not run
any diagnosis. Checked to see if all my motherboard connections were still good and they were.

Second, the audio is not detecting any of my devices. I've tried connection speakers and a headset. Neither would be recognized. I get the option for the
output of : Dummy output (null). There really wasn't any option to detect devices (though that is something usually the code has already built in. Another thing,
I've tried to hook up my chasis audio connection ports. That did not seem to work.


Anyways, this may seem like a lot of writing and I do apologize. I just have not figured out why I have either of these issues and why both of them
happened at the same time. Any help would be much appreciated!

-Sir Jesse-David

---

### Post by ajgreeny on 2017-08-15
With no information about your hardware it is impossible for anyone to help you.

It is also much easier to deal with one problem per thread so I suggest you edit your first post above to remove the audio problem, and start a second thread, this time with all details of your hardware and ask there for help with the audio failure.

To get some info which will help us show the output of ```
inxi -Fzx
``` in terminal.  You may need to install inxi first as I am not sure if it is a default install in U-budgie.

Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by shistar12345 on 2017-08-15
I won't be able to install inxi from the repositories since I cannot connect via Internet. But I can, for the most part, provide you with the hardware.
It is on-board audio and LAN. 
To start: 
-It's a Gigabyte GA-F2A88XN-Wifi (rev.30 mini) motherboard.
- [COLOR=#434343][FONT=Arial][B]LAN	
Realtek® GbE LAN chip (10/100/1000 Mbit)

[/B][/FONT][/COLOR]
[COLOR=#434343][FONT=Arial][/FONT][/COLOR]

- Audio	Realtek® ALC892 codec
High Definition Audio
2/4/5.1/7.1-channel
Support for S/PDIF Out.

Now the wireless adapter, though the problem is not here:
INTEL® DUAL BAND WIRELESS-AC 7260
Dual Band 802.11ac 867Mbps + BLUETOOTH 4.0 wireless solution

That should be all the hardware pertaining to the issues.

Here is a full spec sheet of my computer's hardware as well: 

CPU: AMD Athlon X4 880k Quad core (4.0 Ghz, set to 4.2Ghz)
CPU Cooler: Corsair h60 Liquid Cooling
VGA: XfX Rx 480 RS 8gb edition
Memory: 16gb 2x8gb EVGA ddr3 2133mhz XMP CL11
Motherboard: Gigabyte GA-F2A88XN-Wifi (rev.30 Mini)
SSD: 240GB Mushkin (primary for Ubuntu-Budgie 17.04)
SSD2: 128GB Sandisk
HDD: 1TB WD, 500 GB (Primary for Windows 8.1). 500 GB Shared (ext4)
PSU: Corsair 80+ Bronze 500W
Optical: LG GH24NSCO
Display 1: Acer 24" GN246HL 144h.
Display 2: Asus 21.5" [COLOR=#000000][FONT=Arial]VS228H-P 60hz.
Display 2/3: Samsung 43" UHD [/FONT][/COLOR][COLOR=#474747][FONT=Arial]43L621U

Extra Reference for Motherboard/Onboard Audio/LAN:
[/FONT][/COLOR]http://www.gigabyte.us/Motherboard/GA-F2A88XN-WIFI-rev-30#ov[COLOR=#474747][FONT=Arial]

-If I am missing anything else, please ask me! I'll try my best to get it to you.
(gathered most of this info via command "msinfo32" on windows 8.1)

-Thanks, 
Sir Jesse-David[/FONT][/COLOR]

---

