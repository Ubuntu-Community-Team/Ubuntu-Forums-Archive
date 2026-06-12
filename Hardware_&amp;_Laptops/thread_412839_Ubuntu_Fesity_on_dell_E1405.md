---
title: "Ubuntu Fesity on dell E1405"
date: 2007-04-18
forum: Hardware &amp; Laptops
---

### Post by analyzer123 on 2007-04-18
Hi, 
        I just installed Ubuntu Feisty (alternate CD) on my dell E1405. My experience has been OK, nothing really great. I am having major problems with 3 things:

1. **The network manager applet **- I finally got the wireless going after following the instructions in this forum. The wifi is working fine, the only problem is that the applet in the notification area onyl displays the 2 screens icon, and not the wireless bars icon with the bars. When i move between networks, I should be able to graphically see a list of networks and easily select the correct one, but when i click on this applet I only see "manual configuration"
My "wired' network is turned off. If I actually go into the manual configuration mode and click on edit preferences, I can indeed see the list of wifi nodes around, but I want to see them without all this hassle.
Any idea how I can make the icon display wireless nodes and signal strength?

2. **cisco VPN **- this is really buggy in linux. My problem is - I want to be able to select if I want to use VPN or no, and if yes then which profile. But its clumsy not having a GUI. I tried using the gvpndialer gui but its not compiling correctly.

3. **The synaptics touchpad **- the touchpad itself is working fine, but I am not happy with the single click sensitivity of the touchpad - i feel I am having to hit it down harder than I do in XP. Any GUI which allows me to adjust settings like in XP?

Thanks.
- A

---

### Post by ski309 on 2007-04-25
I've noticed #3 as well, ever since I installed Edgy on my E1405.  I just got used to it, though there should be a 'Synaptic Touchpad' selection in the System->Administration menu that might help you.

My biggest problem when installing Edgy was that the X server failed to load unless I manually editted new modelines before installing.  Did you have any problems starting up the X server when installing Feisty?

---

### Post by strabes on 2007-04-25
There is no GUI for configuration of synaptics touchpads; it has to be done through manually editing the xorg.conf. Here's the site: [http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad). The good thing is that you can tweak the settings on the fly and once you have them the way you like them you can write them to the xorg.conf so you don't have to keep restarting the X server each time you make a change. I have an E1705, here's the relevant part of my xorg.conf if you want to try mine out. (since we have almost the same type of laptop):

> Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "SHMConfig" "true"
        Option      "MinSpeed" ".1"
        Option      "MaxSpeed" ".3"
        Option      "AccelFactor" ".0017"
        Option      "MaxTapTime" "150"
        Option      "MaxDoubleTapTime" "150"
        Option      "VertEdgeScroll" "1"
        Option      "HorizEdgeScroll" "1"
        Option      "VertScrollDelta" "300"
        Option      "HorizScrollDelta" "250"
        Option      "BottomEdge" "4300"
        Option      "RightEdge" "5250"
        Option      "TapButton2" "2"
        Option      "TapButton3" "3"
        Option      "RTCornerButton" "0"
        Option      "RBCornerButton" "0"
        Option      "LTCornerButton" "0"
        Option      "LBCornerButton" "0"
EndSection

---

