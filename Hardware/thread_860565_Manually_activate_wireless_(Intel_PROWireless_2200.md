---
title: "Manually activate wireless (Intel PRO/Wireless 2200BG)"
date: 2008-07-15
forum: Hardware
---

### Post by JinF on 2008-07-15
Hello.

I have a problem getting my wireless to work. I am using a Travelmate 290 with the Intel Corporation PRO/Wireless 2200BG wireless adapter. It has a switch on the side to activate the thing, but it seems to do nothing anymore. The light on the front indication it is on does not light up and Ubuntu does not allow me to search for wireless networks.

Now lspci lists

02:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

and iwconfig lists

eth1      radio off  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


So I know that it sees the card is there, but how do I activate it? Is there a way to manually activate the adapter or do you have any other ideas that I could try out?

---

### Post by ProbablyX on 2008-07-15
For me, though I use KDE (don't know what you are using), I had to right-click KNetworkManager (of course start it first if it's not in the taskbar) the first time I used my wireless. Then there would be a list of available networks. Just click yours there.

However, if the card isn't on you should be able to hover over "settings" (or similar, third option from the bottom) then "Activate Wireless" and see what it says.
If I recall correctly there might be an option called "Settings" without any menu, just click that then, enter your admin password and then right-click the icon again to access the menu.

---

### Post by sdennie on 2008-07-15
You could see if the wireless radio is on by running:

```

iwlist scan

```

If that doesn't show anything, you could look in your BIOS and see if you can disable the switch so that wireless radio is always on.  Not all BIOS's support that though.

---

### Post by lswb on 2008-07-15
There are also some module parameters you could try:


First unload module 
  sudo modrobe -r ipw2200

Then try 
  sudo modprobe disable=0 ipw2200 led=1

The disable=0 is supposed to be default setting, so it probably won't help, but it won't hurt to try. led=1 is supposed to help with control of the led on some systems. For more info, in terminal try 

   modinfo ipw2200

( the modinfo command returns information about any module)

---

### Post by coffeecat on 2008-07-16
> **JinF said:**
> It has a switch on the side to activate the thing, but it seems to do nothing anymore. The light on the front indication it is on does not light up and Ubuntu does not allow me to search for wireless networks.

You seem to be implying that it was working but now it isn't, or have I misread you? If it was working, this could be a hardware fault. To check whether this is so, you need to try another OS. Have you got Windows on that machine? Is wireless working in Windows? If not, Intel 2200BG now works ootb in practically all the popular Linux distros these days. You could get a CD of Mandriva 2008 Spring - say - and try it live. You don't have to install. If wireless works you have an Ubuntu configuration problem. If not you've probably got a hardware fault.

You don't say which version of Ubuntu you're running. Someone else has already suggested something for Kubuntu. If that's Ubuntu/Gnome you're running, have you tried clicking on the network manager icon and exploring the options in the drop-down menu?

---

