---
title: "Need Help configuring Brother Wireless Printer"
date: 2015-06-26
forum: Hardware
---

### Post by Jeannine on 2015-06-26
My laptop runs Lubuntu and it can find the wireless printer, but when I send a print job it doesn't print. The printer says "receiving data", but then it just stops and doesn't actually print the document.

Thanks in advance

---

### Post by Bucky Ball on 2015-06-26
Welcome. More info. Model of printer please. Have you installed a driver from Brother for it? Post any information about anything you've done to try and fix this. Provide link if pertinent. Thanks.

PS: You generally need to set up the wireless printer with it plugged into your machine via USB first. Set the IP address of the printer and a couple of other things. Brother has an app that can do all that 'automagically'. You'll have a tough job getting it to 'just work' wirelessly on your LAN without going through some steps first, even on Windows.

---

### Post by Jeannine on 2015-06-26
The printer model is MFC J470DW

I tried plugging the laptop to the printer with a USB. The same thing happened. The print job is sent and the printer displays "receiving data", then just stops. Nothing prints.
There are no jobs in the print queue, either. I searched for the printer driver, but could not find one that matches the model of the printer.

Thank you for your help.

J

---

### Post by weatherman2 on 2015-06-26
You might need to download drivers from the Brother website:

[http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfcj470dw_us_eu_as&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfcj470dw_us_eu_as&os=128)

Probably grab the "Driver Install Tool."

---

### Post by kurt18947 on 2015-06-26
+1 on the install tool. I haven't had Brother problems for quite some time but once I was sorta where you are. I'm not certain which distro you're running. I'm running Ubuntu-gnome and have played with several others. Ubuntu-Gnome & Unity (I believe) have opted to 'simplify' the printers app but in doing so have made them not very informative. One of my first steps post-install is to install "system-config-printer" from the repositories. This is installed by default on many Ubuntu offshoots, often labeled just 'printers'. If I open the app then right-click on the Brother printer icon then left-click on properties, I get a windows with the following choices:

[LIST]
[*]Settings
[*]Policies
[*]Access Conrol
[*]Printer Options
[*]Job Options
[*]Ink/Toner levels
[/LIST]

Ink/Toner levels doesn't show anything for Brother printers. The item that confounded me was 'Policies'. For who knows what reason 'accepting jobs' was disabled. Once i checked that I was in business. On my machines 'Enabled', 'Accepting jobs' & Shared are all checked.

---

### Post by Bucky Ball on 2015-06-26
> **weatherman2 said:**
> You might need to download drivers from the Brother website:

[http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfcj470dw_us_eu_as&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfcj470dw_us_eu_as&os=128)

Probably grab the "Driver Install Tool."

+1. That's what you want. Install the driver before anything will happen. Set it up with it plugged into the USB. 

Once that done, go wireless. Ping it using a terminal to make sure it is there:

```
ping ***.***.***.***
```

... where ***.***.***.*** is the IP address you have given the printer (you should set it with a static IP address), and if it responds, print something.

---

### Post by emillspaw on 2015-07-16
I had the same problem with a Brother MFC-8840D printer connected via ethernet to DSL modem/DHCP server on home network using Linux Mint 17.1 (based on Ubuntu).  I assigned the printer a Static IP on the DSL router/DHCP server's subnet (192.168.1.135)  I tried all of the driver options that came with the native Brother driver.  It recognized the printer, but would never print.  Printer stuck with Yellow light blinking denoting receiving data, but would always just print an error page.  It seems that the native driver does not send the correct EOF character?

I followed the instructions from the forum:   ***[http://ubuntuforums.org/showthread.php?t=2246878](http://ubuntuforums.org/showthread.php?t=2246878)***

downloaded Brother's new All In One driver, and it works great:
   
 Go to the Brother Linux website and download their '**all in one' driver**
 [[SIZE=1]http://support.brother.com/g/b/downloadend.aspx? c=us&lang=en&prod=mfcj410w_us&os=128&dlid=dlf00689 3_000&flang=4&type3=625[/SIZE]]("http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=mfcj410w_us&os=128&dlid=dlf006893_000&flang=4&type3=625")
     
Since my printer was on the home WiFi network, I chose the 'Y' option for assigning a device URI, then used choice '10: socket://192.168.1.135'

---

