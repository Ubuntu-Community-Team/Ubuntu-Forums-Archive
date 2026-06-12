---
title: "Kodak ESP-C310 Not Working"
date: 2015-02-17
forum: Hardware
---

### Post by benrob0329 on 2015-02-17
I have a Kodak ESP-C310 , and I can't get it to work right. USB worked for a day, then it just didn't print anything. Ubuntu asks for a password when I try to connect over Wifi. Any Ideas?

---

### Post by paulnewall on 2015-02-20
I don't think you can connect directly PC to printer with wifi. You need a wifi router. Then you connect the PC to the wifi using the wifinetwork  password, and you connect the printer to the wifi network on the printer front panel, again you have to enter the wifi network password. Then cups should be able to detect the printer via the wifi.

---

### Post by benrob0329 on 2015-02-20
What I was trying to say was, it doesn't work with USB or over my home network. Yes I'm connected to the network. It's my printer's Samba network that it can't connect to.

---

### Post by paulnewall on 2015-02-22
Here are some suggestions for debugging with USB:

1. Check the printer is connected to USB by running the command lsusb in terminal. You should see the printer listed.

2. Use the printer setup tool system-config-printer (you can access it in the ubuntu menus at Settings manager - printers, Or you can start it from terminal). Try to create a new queue for the usb connected printer. Is the printer detected?

3. In system-config-printer navigate to the printer properties window for your printer. In the Settings area it has a text box called "Printer State" which displays messages from the driver. Try and print something and note the messages that get displayed. They may give some clue about the problem.

4. Edit the file /etc/cups/cupsd.conf  Change the "LogLevel" from "warn" to "debug"
Then try to print something.
Then look at the file /var/log/cups/error_log. It is usually horribly large, but may indicate where the problem is occurring.

---

