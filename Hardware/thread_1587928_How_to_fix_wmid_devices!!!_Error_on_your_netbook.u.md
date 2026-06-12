---
title: "How to fix wmid devices!!! Error on your netbook.ubuntu systems"
date: 2010-10-04
forum: Hardware
---

### Post by san_antonio9.10 on 2010-10-04
** [HOW TO FIX WMID DEVICES!!! ERROR ON YOUR NETBOOK...]("http://viva-opensource.blogspot.com/2010/10/how-to-fix-wmid-devices-error-on-your.html") **

   
  
This tutorial will help you on how  to fix **Acer-wmi** unable to detect available WMID devices error on UBUNTU NETBOOK and all Operating System run by UBUNTU



The error appears on most of  NETBOOKS  build  by Acer, like  as Acer Aspire One or Acer eMachines, after a  system update.

This bug has been tested  with the Easy Peasy 1.6 and Ubuntu NETBOOK   Remix 10.04 LTS (Lucid Lynx) operating systems. After the installation  there seems to be no problems at all, and everything works perfectly .  But, if the end user updates the machine, after a reboot, the above  issue will appear on your screen..

The "acer-wmi: unable to detect available WMID devices" error is very  annoying because it will also break your boot splash screen. So, if you  are one of those who instead of looking at a nice splash screen while  your NETBOOK reboots Ubuntu, get the "**acer-wmi**: unable to detect available WMID devices" error, follow the next steps to  get it fix.

- Hit the ALT+F2 key combination;
- On the "Run Application" dialog that is going to  appear, make sure you check the "Run in terminal" option;


Type this following command:
[COLOR=black]
[/COLOR]
[SIZE=4][COLOR=black]*gksu echo blacklist acer-wmi | sudo tee -a /etc/modprobe.d/blacklist-acer-wmi.conf*[/COLOR][/SIZE]

- Click the "Run" button to execute the above command.

After this, a terminal window will appear and you will be asked for your  password. Input the password, hit Enter, and the terminal window should  dissapear  instantly, and everything  should  be taking care of!!!!

What will this fix do?  it will blacklist **acer-wm****i **and you will no longer see the** "acer-wmi:**  unable to detect available WMID devices" error! From now on, your   NETBOOK  should reboot  the operating system in a normally without any  issues  , and all you should  see the nice splash screen.

 You can check more info in the following site



[WWW.VIVA-OPENSOURCE.BLOGSPOT.COM]("http://WWW.VIVA-OPENSOURCE.BLOGSPOT.COM")

---

### Post by guimaster on 2010-12-04
I just want everyone to know that I get this same error message booting my Dell Latitude C610 laptop. It is not an Acer only problem.

 GuiMasTER

---

### Post by engine on 2010-12-05
Thanks for the info, but before I try it out ... what does the acer-wmi component do: in other words, what might stop working if I blacklist it?

I see from a quick web-search that some helpful individuals have been looking at this question and offering patches since 2007. Perhaps something to consider including in the distro ...

---

### Post by Robert Frittmann on 2011-02-13
I am also getting this message on an Acer Aspire One (AAO) D250 with Ubuntu Desktop 10.04.2 installed. Everything still seems to work fine on my machine, including the WiFi. I have read several threads about this and seen a couple of solutions including the [FONT="Courier New"]**fsck**[/FONT] one (not recommended and doesn't seem to help) and the one mentioned above. While the solution recommended above appears to resolve the breaking of the splash screen, it doesn't actually fix the problem, does it? A bit like cutting the wires to the oil light in your car, so that you don't get that pesky reminder all the time. Is there an actual fix to this problem?

First of all, let's look at some facts. What exactly is WMID? I assumed (correctly, it seems) that it had something to do with the [**Advanced Configuration and Power Interface**]("https://secure.wikimedia.org/wikipedia/en/wiki/Advanced_Configuration_and_Power_Interface") (ACPI), which was designed to resolve the inadequacies of Plug'n'Play BIOS and Advanced Power Management. According to [**this page**]("https://code.google.com/p/aceracpi/"), WMI is in fact a replacement for ACPI.
> acer_acpi has now been deprecated in favour of acer-wmi, and is in bug-fix mode only for pre 2.6.25 kernels. 
A quick [FONT="Courier New"]**uname -r**[/FONT] command confirmed for me that I am running kernel 2.6.32, so I should be using WMI instead of ACPI. My [FONT="Courier New"]**dmesg**[/FONT] output still shows a lot of ACPI messages, however, so I assume that ACPI is still in current usage, despite the "deprecated" state.

[SIZE="4"]**Acer Laptop WMI Extras Driver**[/SIZE]
In searching for a real solution to this WMID error, I came across [**this page**]("http://ww2.cs.fsu.edu/~rosentha/linux/2.6.26.5/docs/laptops/acer-wmi.txt") which appears to be relevant. There is a disclaimer on it, which I will copy here...
> [COLOR="Red"]As such, I do warn that this could break your hardware - this is extremely unlikely of course, but please bear this in mind.[/COLOR]


The following quote seems to clarify what exactly this WMID is all about...
> On Acer laptops, acer-wmi should already be autoloaded based on DMI matching. For non-Acer laptops, until WMI based autoloading support is added, you will need to manually load acer-wmi. acer-wmi creates /sys/devices/platform/acer-wmi, and fills it with various files whose usage is detailed below, which enables you to control some of the following (varies between models):

* the wireless LAN card radio
* inbuilt Bluetooth adapter
* inbuilt 3G card
* mail LED of your laptop
* brightness of the LCD panel


I have owned two AAO D250's. The first one had inbuilt Bluetooth, and the second one doesn't. Both come up with the WMID error, so I assume it is not Bluetooth related. Neither of my AAO's had inbuilt 3G. I cannot see any mail LED on my AAO. This leaves the WLAN card and the LCD brightness as possible suspects from the list above. My WLAN card is working perfectly, I can turn the radio on and off with the front-mounted slider control, and I can control the brightness of my display using the Fn+Right and Fn+Left arrow keys. So, nothing seems to be affected, despite the error message still coming up. I see now why people are so keen to snip the wires from their malfunctioning oil light. :-)

[SIZE="4"]**dmesg tells me "No or unsupported WMI interface, unable to load"**[/SIZE]
It seems to me that there may be something else trying to use WMI, or dependent on WMI, that the Acer machines are trying unsuccessfully to use. From reading the [**aceracpi FAQ**]("https://code.google.com/p/aceracpi/wiki/FAQ"), I found this relevant comment, which seems to support my theory...
> 5. dmesg tells me "No or unsupported WMI interface, unable to load"

Your laptop does not have the WMI-ACPI interface we use to control the hardware. There may be an alternative interface we don't know about - in order to find it, we'll need to do some disassembly of your ACPI DSDT.

From the "Acer Laptop WMI Extras Driver" page, I see that there is a way to send the DSDT to someone, as follows...
> To send me the DSDT, as root/sudo:

cat /sys/firmware/acpi/tables/DSDT > dsdt

And send me the resulting 'dsdt' file.


I am sending the DSDT file to carlos(@)strangeworlds.co.uk (Carlos), along with a link to this post, and I will post back here when I get a reply.

---

### Post by unc0nn3ct3d on 2011-10-18
few days turned into a few months.. Any updates?

---

### Post by Robert Frittmann on 2011-10-18
> **unc0nn3ct3d said:**
> few days turned into a few months.. Any updates?Unfortunately, I never heard back about this. I'm still seeing that annoying oil warning light, and still considering snipping the wires to it myself.

---

