---
title: "not used to touchpad behavior using kernel 5.x"
date: 2020-10-12
forum: Hardware
---

### Post by ronbu on 2020-10-12
I am using Lubuntu 18.04.4 Bionic.  The behavior of the touchpad has changed in kernel 5.0 .  Using the left side of the touchpad behaves as usual.   When I use the right side, it scrolls when moving a single finger up or down.   When moving the finger sideways it changes pages.  Sometimes it acts in other strange ways such as scrolling in or out while using a map.  I don't know how to go back to the classic behavior without going back to the 4.x kernel and going back to the older xorg that is used if the user has not enabled hwe.

---

### Post by ronbu on 2020-10-16
When I went and installed the latest 4.15 kernel and booted into it, I can't get wireless to work.  The touchpad has the classic behavior with that kernel.  An Ubuntu MATE install with the 4.15 kernel does work with wireless.  I'll check to see if I need any extra packages to get wireless to work with the 4.15 kernel.

---

### Post by ronbu on 2020-10-23
I decided to switch the Ubuntu MATE install to Lubuntu and the Elantech touchpad on the Acer works well with it.  I installed on the other partitions, Ubuntu MATE 20.04 with the 5.4 kernel.  The touchpad works well with the classic behavior on it.  I will check if an extra package brings back the classic behavior on the touchpad with a 5.x kernel.

---

### Post by Holger_Gehrke on 2020-10-23
I don't think it's a matter of the kernel. Elantech touchpads like yours and mine used to use the Synaptics driver and where switched to the libinput driver in a recent update to 18.04. This changed my touchpad from edge-scrolling (which is what you describe) to two-finger scrolling (which I don't really like). It also disabled 'tap to click', which made me look into things. With the old driver there were a lot of options that could be controlled from the GUI in the device tab of the 'Mouse and Touchpad' settings applet on XUbuntu which are gone with libinput. 

It's possible to change the scrolling method by using 'xinput' on the command line. Use 'xinput -list' to get the name and device number libinput uses for your touchpad. You can see what properties can be changed with 'xinput -listprops "device name"' (substitute the name found with '-list' for device name in that command; the quotes around the name are necessary if it contains spaces; using the name is better than using the number because the numbers don't necessarily stay the same from one boot of the system to the next). If you pad is like mine, there will be a property named 'libinput Scroll Method Enabled' with multiple numbers as parameter. The command 'xinput -set-prop "devicename" "libinput Scroll Method Enabled" 1 0 0' sets two-finger scrolling while 'xinput -set-prop "devicename" "libinput Scroll Method Enabled" 0 1 0' sets edge-scrolling. Setting this property to '0 0 0' disables all scrolling methods.

Holger

---

