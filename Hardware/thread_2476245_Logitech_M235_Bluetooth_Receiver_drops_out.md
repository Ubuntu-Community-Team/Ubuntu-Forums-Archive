---
title: "Logitech M235 Bluetooth Receiver drops out"
date: 2022-06-21
forum: Hardware
---

### Post by gdesilva on 2022-06-21
[FONT=arial]This the solution for anyone having issues with the Logitech M235 Bluetooth Receiver dropping out regularly and as a result mouse becoming inactive.

I have tried the following solutions;

1. Unplug the receiver and plug back in - this sometimes activates the frozen mouse for a while but then after sometime it freezes. At that time there is no Logitech device listed on the output of the lsusb command.

2. Followed the instructions here   &#8203;[https://askubuntu.com/questions/505932/ubuntu-14-04-mtp-error](https://askubuntu.com/questions/505932/ubuntu-14-04-mtp-error) , in particular the post by Eugen Konkov (the last post) but again the problem appeared to be resolved but on reboot the issue persisted.

3. After going through the syslog and trying to find a solution that matched the error codes on syslog, I stumbled across this post by 'ondoho' [https://www.linuxquestions.org/questions/linux-hardware-18/usb-5-1-device-descriptor-read-64-error-71-a-4175640937/](https://www.linuxquestions.org/questions/linux-hardware-18/usb-5-1-device-descriptor-read-64-error-71-a-4175640937/) which refers to a solution here [https://urukrama.wordpress.com/2009/01/27/usb-drive-not-recognised-error-71/](https://urukrama.wordpress.com/2009/01/27/usb-drive-not-recognised-error-71/) and this solution did work.

4. The solution is simply to add the following line to /etc/modprobe.d/options file
[/FONT][FONT=arial]             options usbcore use_both_schemes=y

and reboot.

[/FONT]5. The rationale for this can be found in [https://www.spinics.net/lists/usb/msg02644.html](https://www.spinics.net/lists/usb/msg02644.html)

Hope this will be useful.

---

### Post by gdesilva on 2022-06-30
UPDATE

While the inclusion of option to use both schemes worked for a little while, upon rebooting the system the old problem of frozen mouse continued to occur.

[COLOR=#000000][FONT=arial]> The solution is simply to add the following line to /etc/modprobe.d/options file
[/FONT][/COLOR][COLOR=#000000][FONT=arial]> options usbcore use_both_schemes=y

Upon further checking, as per the descriptions of Linux kernel parameters in [/FONT][/COLOR]https://redsymbol.net/linux-kernel-boot-%20parameters/3.1/  I tried changed the usbcore option as follows;

options usbcore.old_scheme_first=1

Since this change was done, now for over 3 days I haven't had a single mouse freezing event. Either the initial usbcore option specification is incorrect (NOT 'options usbcore use_both_scheme' but it should have been 'options.use_both_schemes) or this Logitech mouse works only according to the old scheme - more likely it is the latter.

---

