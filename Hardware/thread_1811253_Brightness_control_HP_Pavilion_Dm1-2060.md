---
title: "Brightness control HP Pavilion Dm1-2060"
date: 2011-07-24
forum: Hardware
---

### Post by RH+ on 2011-07-24
I been using Ubuntu as primary OS in my notebook for last 2 months, all works fine except the keyboard brightness control (The panel control doesnt work either), I can configure it from the ATI control center but Im not getting the same effect, the best way is to go into windows, change brightness and then reboot to linux (hate to do that only to change the brightness when I have fn+F3/F4 to do that in a very simple way).
This is the output of the lspci command, please let me know if you need any other information. I'm using Ubuntu 11.04 x64.
Thanks!


00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: ATI Technologies Inc Device 43a0
00:15.1 PCI bridge: ATI Technologies Inc Device 43a1
00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
09:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

---

### Post by Toz on 2011-07-24
Check your bios first. Is there a backlight setting there that can be changed?

Try booting with the following kernel parameter:
```
acpi_backlight=vendor
```HowTo instructions [here]("https://help.ubuntu.com/community/Grub2#Editing the GRUB 2 Menu During Boot")


If that doesn't work, open a terminal window and if the following command doesn't generate an error:
```
cat /sys/devices/virtual/backlight/acpi_video0/brightness
```
then try:
```
echo 3 | sudo tee -a /sys/devices/virtual/backlight/acpi_video0/brightness
```

If that doesn't work, then try:
```
sudo setpci -s 01:05.0 F4.B=96
```

---

### Post by RH+ on 2011-07-24
> **Toz said:**
> Check your bios first. Is there a backlight setting there that can be changed?

Try booting with the following kernel parameter:
```
acpi_backlight=vendor
```HowTo instructions [here]("https://help.ubuntu.com/community/Grub2#Editing the GRUB 2 Menu During Boot")

Its already set to:
ro   quiet splash acpi_osi=Linux acpi_backlight=vendor vt.handoff=7

> 
If that doesn't work, open a terminal window and if the following command doesn't generate an error:
```
cat /sys/devices/virtual/backlight/acpi_video0/brightness
```
then try:
```
echo 3 | sudo tee -a /sys/devices/virtual/backlight/acpi_video0/brightness
```

first code throus: Not such file or directory

> 
If that doesn't work, then try:
```
sudo setpci -s 01:05.0 F4.B=96
```
I dont get an error with that command but nothing happens.

Any other idea?
thanks!

---

### Post by Toz on 2011-07-24
Try booting _without_ the **acpi_backlight=vendor** parameter and see if the two commands work.

Does the acpi_osi=Linux parameter fix anything for you?

You might also want to try the parameters as such:
```
ro quiet splash acpi_osi=\"Linux\" vt.handoff=7
```

---

### Post by RH+ on 2011-07-24
> **Toz said:**
> Try booting _without_ the **acpi_backlight=vendor** parameter and see if the two commands work.

Does the acpi_osi=Linux parameter fix anything for you?

You might also want to try the parameters as such:
```
ro quiet splash acpi_osi=\"Linux\" vt.handoff=7
```
Ok, removing **acpi_backlight=vendor** and changing to **acpi_osi=\"Linux\"** make the first 2 comands work and when I get to the login screen the brightness changes itself 1 or 2 times, so the OS is controling the brightness that also changes in the grub menu screen when I reboot. And now the screen turn darker when I not use it (great!).

Now, is there a way to make the FN+F3/F4 change the brigthness? (im used to use FN keys, so it would be better to use them, but if that work with any shortcut im happy for now)

Thanks again!

---

### Post by Toz on 2011-07-25
If the setpci command worked, have a look at the script at: [http://ubuntuforums.org/showpost.php?p=10926719&postcount=6]("http://ubuntuforums.org/showpost.php?p=10926719&postcount=6").

Try implementing that script but make sure you change the **setpci** command in the script to match the one that worked on your system. Change the setpci command towards the end of the script to read:```
setpci -s 01:05.0 F4.B=$hex_b
```

---

### Post by RH+ on 2011-07-25
> **Toz said:**
> If the setpci command worked, have a look at the script at: [http://ubuntuforums.org/showpost.php?p=10926719&postcount=6]("http://ubuntuforums.org/showpost.php?p=10926719&postcount=6").

Try implementing that script but make sure you change the **setpci** command in the script to match the one that worked on your system. Change the setpci command towards the end of the script to read:```
setpci -s 01:05.0 F4.B=$hex_b
```

setpci is not working.

This code works:
```
echo 3 | sudo tee -a /sys/devices/virtual/backlight/acpi_video0/brightness
```
is there anything I can do with this?
thanks!

---

### Post by Toz on 2011-07-25
I can through together a script for you that you can assign to your brightness keys. Can you try and see if xbacklight works for you? You'll need to install the package. Look for it in the Software Centre or via the command line:
```
sudo apt-get install xbacklight
```
(It'll make things easier)

Once its installed, try running:
```
xbacklight -set 50
```

Let me know if it works.

---

### Post by RH+ on 2011-07-25
It worked at first try :)

---

### Post by Toz on 2011-07-25
Great. Here is the script.

1. Create a file named brightness in your home directory:
```
gedit ~/brightness
```

2. Copy/paste the following code:
```
#!/bin/bash

current=`xbacklight -get | sed -e 's/\..*//g'`
echo -n "Debug: "$current" / "

case "$1" in
	up)
		echo -n "up / "
		if [ $current != "100" ]; then
			new=$(($current + 10))
		else
			echo "exit"
			exit 1
		fi
	;;
	down)
		echo -n "down / "
		if [ $current != "0" ]; then
			new=$(($current - 10))
		else
			echo "exit"
			exit 1
		fi
	;;
	*)
		exit 1
	;;
esac

#now set the new value
xbacklight -set $new
echo $new
exit 0
```

3. Save the file.

4. Make the file executable:
```
chmod +x ~/brightness
```

5. Run some tests just to be sure.
```
~/brightness down
```
```
~/brightness down
```
```
~/brightness up
```
```
~/brightness up
```

If all is good so far, let's assign the brightness keys to this script. (You'll have to excuse me here, I use the xfce version of ubuntu and I hope my instructions are correct).

6. Start gnome-keybinding-properties:
```
gnome-keybinding-properties
```

7. Click "Add" an enter as the Name **Brightness Up** and the command as **~/brightness up**, then click Apply.

8. Click the newly entered line on the word 'Disabled' and type in your Fn+code to increase brightness.

9. Click "Add" an enter as the Name **Brightness Down** and the command as **~/brightness down**, then click Apply.

10. Click the newly entered line on the word 'Disabled' and type in your Fn+code to decrease brightness.

11. Click close and test your Fn brightness keys.

---

### Post by RH+ on 2011-07-25
I cant use the FN key to assign a shortcut, so I try CTRL+F3/F4

When I press the keys (after configuring them) It gives me this error:

"Error while trying to run (~/brightness down) which is linked to the key (<Control>F3)"

I try it with control and with F3/F4 without control, same error.
Any idea?
Thanks again!

---

### Post by Toz on 2011-07-25
Does it work from the command line?

Try changing the command to: /home/userid/brightness down where userid is your userid. Something like **/home/me/brightness down**

---

### Post by RH+ on 2011-07-25
> **Toz said:**
> Does it work from the command line?

Try changing the command to: /home/userid/brightness down where userid is your userid. Something like **/home/me/brightness down**

it works without problems from command line. changed the command in keybindings, works great, little laggy, but I dont care I dont change the brightness constantly.
Thanks a LOT Toz!!!

---

### Post by Toz on 2011-07-25
Glad to hear it worked out for you. Can you please mark this thread as solved from the Thread Tools link above? Thanks.

---

### Post by RH+ on 2011-07-25
Done!
Its strange that it let me bind some fn+F keys (the ones that already have a function) but it doesnt let me bind Fn with other keys (that have a function in this case brightness not detected by OS).
But Im happy with this solution, hope some day it works like it should.
Thanks again!

---

