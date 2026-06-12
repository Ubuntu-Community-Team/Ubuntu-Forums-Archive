---
title: "Changing device file permission at startup"
date: 2008-01-20
forum: Hardware &amp; Laptops
---

### Post by tayran on 2008-01-20
Hi. I have been using kubuntu gutsy 64 on my acer aspire 5024 laptop for two months now. It is perfect as an 64 bit operating system and i can find quite bunch of help about installation problems because it is a rather old laptop. I have installed almost all functions properly instead of bluetooth. The bluetooth device itself is running via acer_acpi module but i had to activate it via this command every time:
sudo chmod 666 /proc/acpi/acer/bluetooth
echo 1 > /proc/acpi/acer/bluetooth (echo 0 to deactivate)

i couldn't have my bluetooth key in front work automatically. Even a key code was not defined for it so i decided to do it manually. First i have installed xbindkeys to handle key events. Then put this script to $HOME/.kde/Autostart to start at login:
sudo setkeycodes e058 200  #bluetooth off->on
sudo setkeycodes e057 201  #bluetooth on->off
xbindkeys & 

I have adjusted .xbindkeysrc config file according to key codes above adding these lines:
# bluetooth off->on
"echo 1 > /proc/acpi/acer/bluetooth"
  m:0x0 + c:168

# bluetooth on->off
"echo 0 > /proc/acpi/acer/bluetooth"
  m:0x0 + c:169

Now i can toggle bluetooth with bluetooth key. But still i have to run this command before using:
sudo chmod 666 /proc/acpi/acer/bluetooth

Since it is system device file ever time i reboot the system /proc/acpi/acer/bluetooth file is recreated with 644 properties so as a user i cannot write to it. So i put that command to bootup, tried run level 2-5 but i couldn't make it run run properly. When i login and check the file i see its attributes 644. Does anyone suggest a solution?

---

