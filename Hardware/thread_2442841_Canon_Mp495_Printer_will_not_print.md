---
title: "Canon Mp495 Printer will not print"
date: 2020-05-08
forum: Hardware
---

### Post by roberthipp3 on 2020-05-08
Hello, I have a canon Mp495 printer that will not print. I'm using the new Ubuntu LT release from this month.  My printer is listed in Hardware and it downoaded  drivers for it. Whenever I try to print anything ,it acts like it is going to do it , but the printer does absolutely nothing. Ive tried everything I can think of to get it working and nothing fixes it. The worse part is that I really need it. I have to print a return label to send back a defective item i purchased and i can"t because it wont print! I'm desperate to get it working because I have a very limited amount of time to send back the item that i need the return label for! 
Thank you in advance for any help!
Robert

---

### Post by guiverc on 2020-05-08
Are you talking about printing from everything? or just for example LibreOffice?

To bypass the issue in your hurried circumstance, you could boot a 'live' session (eg. a different or older release using the "Try/Start" option) and print from there.

---

### Post by brian_p on 2020-05-08
Say whether the MP495 is connected by USB or wireless and provide the output of ```
lpinfo -v
```

---

### Post by roberthipp3 on 2020-05-08
Hello, My printer is connected by USB.  I'm new to Ubuntu coming from windows , so I have no idea what you nice fellows are talking about..lol What I can Tell you is that I want to print a return label from amazon that is online. and that my printer is supposedly installed by ubuntu and it had me download generic driver for it. When i try to print anything , the dialogs work like it is sending it to the printer but absolutely nothing happens. this was so much easier on windows...it just worked lol.

---

### Post by roberthipp3 on 2020-05-08
file cups-brf:/
network beh
network lpd
network http
serial serial:/dev/ttyS0?baud=115200
network ipps
network socket
network ipp
network https
direct hp
direct usb://Canon/MP495%20series?serial=A22ED6&interface=1
direct parallel:/dev/lp0
direct hpfax

---

### Post by brian_p on 2020-05-08
> ```
usb://Canon/MP495%20series?serial=A22ED6&interface=1
```

This is the URI for your printer. You will substitute for it later on. It is a critical parameter.

Now you need a PPD to go with the URI. Do ```
sudo apt install printer-driver-gutenprint
```

The PPD is in this package and is found with```
lpinfo -m | grep MP495
``` The name begins with *gutenprint* and ends with *expert*.

Now substitute in ```
lpadmin -p PRINTER_NAME -v URI -E -m PPD
``` and execute the command. PRINTER_NAME can be anything you want; I would use *mp495*. Test printing with ```
lp -d PRINTER_NAME /etc/nsswitch.conf
```

---

### Post by gja on 2020-05-09
I had an issue with usb printing in 20.04.
Printer registers itself multipe times and doesn't always print.

[https://ubuntuforums.org/showthread.php?t=2442142&page=2&p=13953836#post13953836](https://ubuntuforums.org/showthread.php?t=2442142&page=2&p=13953836#post13953836)

Found a solution on German forum:
[https://forum.ubuntuusers.de/topic/hp-photosmart-5525-konfigurationsproblem-unter/4/](https://forum.ubuntuusers.de/topic/hp-photosmart-5525-konfigurationsproblem-unter/4/)

Apparently ippusbxd causes problems and can simply be removed.

Try this instruction:
sudo apt purge ippusbxd

---

### Post by kurt18947 on 2020-05-09
For a one-off job, you could use "print to file" which creates a pdf. Then take/send the pdf to an office services firm - in the U.S. I'd use Staples or FedEx office and print it there. You of course want to get your printer working but if time is critical ..........

Here is something new to me. 
[https://www.usa.canon.com/internet/portal/us/home/products/details/software/device-management/codehost-unix-linux-printing-with-brightq-pro](https://www.usa.canon.com/internet/portal/us/home/products/details/software/device-management/codehost-unix-linux-printing-with-brightq-pro)
I have no idea if or how well it works.

---

### Post by brian_p on 2020-05-09
> Apparently ippusbxd causes problems and can simply be removed.

This advice is definitely worth a try. I passed it on to another user at

[https://answers.launchpad.net/hplip/+question/690549](https://answers.launchpad.net/hplip/+question/690549)

As can be seen there - it worked. :D

It would be good if Robert first followed my advice on setting up a print queue and, if there is no printing, then used gja's recommendation.

---

### Post by brian_p on 2020-05-09
I would not normally do this but I responded to this post partly because you (Robert) said:

> The worse part is that I really need it.

Two expert replies have been contributed but as yet, in spite of the urgency you wrote about, there hasn't been any response from you. We wonder whether you would report on the advice received. At the very least, it would help other users.

---

