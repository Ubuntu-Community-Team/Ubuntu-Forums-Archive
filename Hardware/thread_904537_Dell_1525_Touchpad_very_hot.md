---
title: "Dell 1525 Touchpad very hot"
date: 2008-08-29
forum: Hardware
---

### Post by nomemory on 2008-08-29
Everything seems to work fine when running Ubuntu on a Dell 1525 Inspiron, except the fact the touchpad is getting hot (actually very very hot). On Windows I don't have the same issue. Any suggestions ?

---

### Post by nicedude on 2008-08-29
It's not your touchpad that is generating the heat it is your CPU or hard drive that is generating it. You will need to do some research on this one as it gets really complicated to do correctly. For example I made a script for my acer that has two sets of settings 1 for AC and 1 for when I switch to battery to save more power ( I so far am getting an extra 35 minutes uptime with my script but plan to look at eve more stuff ). In general outside of making a custom script for your specific model ( or finding someone else who already has ) You should at least set the CPU to on demand or power savings in the gnome power manager applet, here is the command to open it.

Open a terminal and paste this in it and press enter, that will get you to the few easy CPU settings you can mess with

gnome-power-preferences

To check what is using all the power while on battery ( power use is related to how muxh heat your PC generates in general since low power usually = lower heat ) use a utility called powertop

Command to install it

sudo apt-get install powertop

Command to run it

sudo powertop


While it cannot fix power hog stuff it can give suggestions and will show what is using the most power and system resource wakeups etc 


Hope this helps you figure it out for your laptop :-)

---

### Post by nomemory on 2008-08-30
after i run powertop I get those messages:
[INDENT]
Top causes for wakeups:
  37.5% (277.2)      <kernel IPI> : Rescheduling interrupts 
  17.7% (131.0)   USB device 7-2.1 : BCM2045 (Broadcom Corp) 
  13.5% (100.0)       <interrupt> : ehci_hcd:usb3, uhci_hcd:usb7 
   8.3% ( 61.3)   USB device  5-2 : Basic Optical Mouse (Microsoft) 
   7.5% ( 55.3)       <interrupt> : uhci_hcd:usb1, ehci_hcd:usb4, uhci_hcd:usb5
   5.7% ( 42.2)       <interrupt> : extra timer interrupt [/INDENT]

Any suggestions ?
PS; Thanks for your reply.

---

