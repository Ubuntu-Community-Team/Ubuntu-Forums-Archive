---
title: "Mouse not recognized"
date: 2014-02-22
forum: Hardware
---

### Post by jv69 on 2014-02-22
Hello,  I installed/uninstalled  Xubuntu 12.04 then installed 13.10 on a Dell Optiplex GX620. I was given a Gateway Keyboard and Mouse to use temporary. 
The keyboard works, but no mouse. Searched many web pages on mouse problem.  Went through BIOS, and all of the USB ports are enabled.
I opened a tty (CTRL-ALT F1)  and performed the following:
sudo -update -usbids 
sudo modprobe -r psmouse;
sudo modprobe ehci-hcd  ( ehci-hcd is not installed) 


Then I went to Applications -> Settings, , using F10 and arrow keys on the 
keyboard but there is no mouse configuration options. Currently running updates
to see if something was missed. 

Any help is appreciated.
thanks

---

