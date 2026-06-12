---
title: "Which drivers for Brother DCP-L2540DW printer/scanner/copier"
date: 2016-03-07
forum: Hardware
---

### Post by joverstreet1 on 2016-03-07
Can anyone tell me if it is necessary to install any of the individually listed printer & scanner drivers on the Brother website for the Brother model DCP-L2540DW printer or should all of the necessary drivers, etc. be installed by the DRIVER INSTALL TOOL which is listed at the top ?

See this link

[http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=dcpl2540dw_us_as&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=dcpl2540dw_us_as&os=128)

The reason I ask is the when installing the Driver Install Tool, so far, I can not get the printer to perform any SCANNING functions.
Thanks.

---

### Post by davidvandoren on 2016-03-08
[SIZE=2]After installing the drivers for printer and scanner. 

If not installed,[/SIZE][SIZE=3][SIZE=2]install [/SIZE][/SIZE][SIZE=2]gksudo[/SIZE][SIZE=2] or nano and open the [COLOR=#111111][FONT=Ubuntu]40-libsane.rules file. 

To do that, open the terminal from the menu or press ctrl+Alt+t and the terminal will open. 
[/FONT][/COLOR][/SIZE] 
[COLOR=#111111][FONT=Ubuntu]Then type or copy and paste.

[/FONT][/COLOR]```
gksudo gedit /lib/udev/rules.d/40-libsane.rules
```[COLOR=#111111][FONT=Ubuntu]

Type your administrator password, probably the one you use for your account. 
Enter
Gedit will open up!

Now[/FONT][/COLOR]
read this carefully: 
# To add a USB device, add a rule to the list below between the
# LABEL="libsane_usb_rules_begin" and LABEL="libsane_usb_rules_end" lines.

So, find the libsane_usb_rules_begin line
[SIZE=2][COLOR=#111111][FONT=Ubuntu]
Then type or copy and paste the following below that begin line.
And before the end line. 


[/FONT][/COLOR][/SIZE]```
# Brother scanners[SIZE=2][COLOR=#111111][FONT=Ubuntu]
[/FONT][/COLOR][/SIZE]
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
```[SIZE=2][COLOR=#111111][FONT=Ubuntu]
Save the changes within gedit and close the application.

Restart your pc.

The scanner should work.[/FONT][/COLOR][/SIZE]

---

### Post by joverstreet1 on 2016-03-09
David:

Thanks for your reply.  This worked just fine.

Can you tell me if the # Brother scanners line info would be the same for all models of Brother printers/scanners or would the 04f9 be something different for various models ?

Thanks.

---

### Post by Edison_James on 2016-03-17
> **joverstreet1 said:**
> David:

Thanks for your reply.  This worked just fine.

Can you tell me if the # Brother scanners line info would be the same for all models of Brother printers/scanners or would the 04f9 be something different for various models ?

Thanks.
Glad it worked out for you. Here is a very handy link if you ever need to install Brother drivers again.

[https://sites.google.com/site/easylinuxtipsproject/15](https://sites.google.com/site/easylinuxtipsproject/15)

---

### Post by kurt18947 on 2016-03-18
> **joverstreet1 said:**
> David:

Thanks for your reply.  This worked just fine.

Can you tell me if the # Brother scanners line info would be the same for all models of Brother printers/scanners or would the 04f9 be something different for various models ?

Thanks.

I'm pretty sure the line info would remain the same. 04f9=Brother. If there were model specificity, it might look like 04f9:xxxx where x are alphanumerics designating the model.

---

### Post by fh-faraz-hussain on 2016-05-02
I have been using a brother hl2270dw with my ubuntu (over wireless) for many years. I have decided to order a DCP-L2540DW because I also want scan/copy functions. Therefore, I'm glad people are already using this printer or something similar.

A question: if I am able to set things up so that all scanned documents are emailed to me, do I sill need to install the scanner drivers? Thanks.

---

### Post by fh-faraz-hussain on 2016-05-06
In case this helps someone, I have Ubuntu 15.10 and my Brother DCP-L2540DW works great. I even gave it a static IP (using 'LAN setup' on my netgear router) and it easily prints over the wireless.

I had to use the WLAN setup wizard to connect it to my wireless network. This video was very helpful:  [https://www.youtube.com/watch?v=O0ZGN3yUan8](https://www.youtube.com/watch?v=O0ZGN3yUan8) ("[BrotherGlobalSupport] faq00100107_004_en DCP-L2520DW Wireless Setup without having a CD drive").  Note: use the + and - keys to scroll through the alphabet and numbers 0-9.

---

### Post by fh-faraz-hussain on 2016-05-15
Here's another problem I had with this printer on Ubuntu 15.10 and 16.04:

After switching on the printer, it would print absolutely fine over wireless until the printer went into deep sleep mode. After that, it I would get the message: "Unable to locate printer".

I changed the time to deep sleep from 1 min. to 30 minutes, but this did not help. I then tried, without success, various modes of adding/modifying this printer with CUPS. 

Finally, this is what worked: 
CUPS -> Administration -> Add Printer ->  [B]AppSocket/HP JetDirect  ->     socket://the.static.ip.of.my.printer:9100

[/B](h/t to kurt18947 from this thread: [http://ubuntuforums.org/showthread.php?t=2038708](http://ubuntuforums.org/showthread.php?t=2038708))

---

