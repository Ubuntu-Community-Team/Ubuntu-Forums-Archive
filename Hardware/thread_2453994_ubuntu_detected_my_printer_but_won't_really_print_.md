---
title: "ubuntu detected my printer but won't really print after clicking the print button"
date: 2020-11-20
forum: Hardware
---

### Post by ronjjjg8885 on 2020-11-20
it is also not appears in any queue or something
i'm adding a screenshot of the printer settings
[ATTACH=CONFIG]287399[/ATTACH]
what can be done?

(Ubuntu 20.10)

thanks!

---

### Post by Autodave on 2020-11-20
For anyone trying to help, that is a Canon Pixma printer.

Did you install any driver for the printer?  If so, what one and where did you get it from?

---

### Post by ronjjjg8885 on 2020-11-21
well thanks!
i connected the printer and it installed it by itself

---

### Post by brian_p on 2020-11-21
> **ronjjjg8885 said:**
> well thanks!
i connected the printer and it installed it by itself

That's interesting. The device uses a USB connection? Give the outputs of ```
lpoptions -l iP2800-series
``` ```
lsusb -v | grep -A 3 bInterfaceClass.*7
``` ```
systemctl list-units "ippusbxd*" | grep service
```

---

### Post by Autodave on 2020-11-21
I'm sorry, but you will have to wait for someone with Canon experience to wander by.  I learned a long time ago to stick with HP printers since they just seem to always work.

---

### Post by ronjjjg8885 on 2020-11-21
> The device uses a USB connection? Give the outputs of

yes!

[https://pastebin.com/93i5T7yP](https://pastebin.com/93i5T7yP)
```
lpoptions -l iP2800-series
```


[https://pastebin.com/picVf5qN](https://pastebin.com/picVf5qN)
```
lsusb -v | grep -A 3 bInterfaceClass.*7
```

and
```
systemctl list-units "ippusbxd*" | grep service
```
doesn't show any output

---

### Post by brian_p on 2020-11-21
```
lsusb -v | grep -A 3 bInterfaceClass.*7
```

does not show any printer connected. This could be why there isn't any output from the third command. Is the device connected and switched on?

---

### Post by ronjjjg8885 on 2020-11-22
hi
i did it again when the printer is on (and connected)
```
lsusb -v | grep -A 3 bInterfaceClass.*7
```
[https://pastebin.com/mpTvdFFQ](https://pastebin.com/mpTvdFFQ)

---

### Post by brian_p on 2020-11-22
Thanks for the info. I had an idea. It didn't work out. Sorry.

---

### Post by VMC on 2020-11-22
What does this command show?
```
[FONT=monospace][COLOR=#18B218]**$**[/COLOR][COLOR=#000000] systemctl list-unit-files --state=enabled --no-pager|grep cups[/COLOR]
org.[COLOR=#FF5454]**cups**[/COLOR][COLOR=#000000].[/COLOR][COLOR=#FF5454]**cups**[/COLOR][COLOR=#000000]d.path                enabled disabled      [/COLOR]
org.[COLOR=#FF5454]**cups**[/COLOR][COLOR=#000000].[/COLOR][COLOR=#FF5454]**cups**[/COLOR][COLOR=#000000]d.service             enabled disabled      [/COLOR]
org.[COLOR=#FF5454]**cups**[/COLOR][COLOR=#000000].[/COLOR][COLOR=#FF5454]**cups**[/COLOR][COLOR=#000000]d.socket              enabled disabled
```

Same as mine?

Also do you still have this file?
```
[/COLOR][/FONT]/usr/lib/systemd/system/org.cups.cupsd.service
```[FONT=monospace][COLOR=#000000]
[/COLOR]
[/FONT]

---

### Post by Autodave on 2020-11-22
I know that Canon has a Linux driver on their website, but, again, I know nothing about those printers.

---

### Post by ronjjjg8885 on 2020-11-22
thank you all!!!

[https://pastebin.com/5MENfLXu](https://pastebin.com/5MENfLXu)
the file isn't there

i will try to look for a driver on the canon website.
anything to know about the installation or the uninstallation if it doesn't works?

---

### Post by tokyobadger on 2020-11-23
Just out of interest, is this a printer that supports printing over wifi?

I just bought a Canon TS8430 (printer/copier/scanner) 1 week ago. I connected it to the wifi and then both Groovy and Hirsute (dev branch) just picked it up, no drivers required for printing or scanning.

I previously had a Canon MG-something between 2010 and 2014 connected by USB to a Ubuntu box, my recollection is also that it "just worked", no additional drivers etc.

---

### Post by ronjjjg8885 on 2020-11-23
i don't think that it has a wifi

---

### Post by tokyobadger on 2020-11-24
Can you give us the exact model number. Also could you confirm that you're running 20.10 as per your signature

---

### Post by ronjjjg8885 on 2020-11-26
didin't see your response earlier

YES
i'm running 20.10[ATTACH=CONFIG]287460[/ATTACH]
i think it's k10399
as seen in the photo
on the printer itself it says (IP2800)

---

### Post by kema77 on 2020-11-26
You have a dual boot setup. Are you able to print from Windows? This appears to be the driver for the IP2800 series:

[https://ph.canon/en/support/0100668804/2](https://ph.canon/en/support/0100668804/2)

---

### Post by ronjjjg8885 on 2020-11-26
when i use windows i can definitely use the printer

---

### Post by kema77 on 2020-11-26
This is what Ubuntu shows for my Canon printer. It gives the specific model, rather than "generic printer" like yours says. It's been awhile since I set up the printer, so I don't recall if Ubuntu automatically installed it. It shows I am using the gutenprint printer drivers for CUPS for the MX310, so I suspect I did that manually, but I am really not sure. I can't tell you if that driver package would work for your model. I'm not much help, am I?:( Did you try the driver for the ip2800 series that is available on the Canon support site?

---

### Post by ronjjjg8885 on 2020-11-27
the strange thing is that i'm almost sure the when i bought the printer a while back, it detected it and also printer once.

since then. nothing.

i'm not sure where to find the linux driver you are talking about. 

maybe this? [https://in.canon/en/support/0100586502](https://in.canon/en/support/0100586502)

edit:
i've typed ```
sudo install.sh


```
in the extracted files directory but i get ```
sudo: install.sh: command not found

```

edit 2:
i'm following this [https://www.wikihow.com/Execute-INSTALL.sh-Files-in-Linux-Using-Terminal](https://www.wikihow.com/Execute-INSTALL.sh-Files-in-Linux-Using-Terminal)
and trying to install it now...

edit 3:
it's working!
after following the instructions on the screen i can now print...
thank you

---

### Post by kema77 on 2020-11-27
Yep, that was the driver I was referring too. Sorry I didn't link it. Glad you got the printer working.

---

