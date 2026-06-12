---
title: "Asus eee touchscreen"
date: 2011-01-22
forum: Hardware
---

### Post by vootele on 2011-01-22
Greetings
I have Asus EEE PC 900 with screen digitizer, that causing the trouble.
It worked with Windows XP, but now when I installed latest Ubuntu Netbook edition (10.10), it kinda works, but I think it needs calibration. When I touch screen on any position, cursor jumps to left upper corner and clicks ubuntu menu.
The digitizer is that one:
[http://www.dealextreme.com/p/9-usb-touch-screen-digitizer-diy-mod-kit-for-asus-eee-pc-900-umpc-laptops-18490](http://www.dealextreme.com/p/9-usb-touch-screen-digitizer-diy-mod-kit-for-asus-eee-pc-900-umpc-laptops-18490)

It includes extra usb-hub, that connects to webcam connector and has serial(?) port for digitizer.

---

### Post by vootele on 2011-01-22
Solution found.
It was really easy, just download driver:
[http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm](http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm)
Unpack it, run sudo sh install.sh from same folder
Reboot
run eGalaxTouch utility from terminal.

---

