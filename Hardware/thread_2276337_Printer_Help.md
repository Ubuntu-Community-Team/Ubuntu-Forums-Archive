---
title: "Printer Help"
date: 2015-05-01
forum: Hardware
---

### Post by shannon3 on 2015-05-01
Hi Everyone. Ubuntu newbie here. I'm trying to install my Brother MFCJ6920DW printer on my system (LTS 14.04). I've been able to get it installed, and it shows up under printers, but I can't get it to print. It just says "Idle, waiting for printer to become active" (or something like that). Both the printer and my computer are connected to the internet via WiFi, so I'm thinking that's where the issue is. Any help would be greatly appreciated. 

Thank you!

---

### Post by gifford on 2015-05-02
Did you set it up as a network printer?
I assume you downloaded the drivers, cups wrapper and scanner driver from Brother's website.
In my experience, install via the command line is the best way to go.

Please describe in detail what you downloaded, installed, etc.

---

### Post by shannon3 on 2015-05-08
Sorry for the late reply. Yes I'm trying to make it a network printer for our house. I downloaded the driver install tool from here ([http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfcj6920dw_us_eu_as&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfcj6920dw_us_eu_as&os=128)) then I did the following:

Save the downloaded file in the folder Downloads. Don't extract the zipped file, but leave it there just as it is.


 b. Launch a terminal window.
*(You can launch a terminal window like this: [*Click*]("https://sites.google.com/site/easylinuxtipsproject/11"))*


 c. Now copy/paste the following command into the terminal, in order to unzip the downloaded file:

[COLOR=#0000FF]cd Downloads && gunzip -v ~/Downloads/linux-brprinter*[/COLOR]
Press Enter.


 d. Use copy/paste to transfer the following line to the terminal:

[COLOR=#0000FF]sudo bash ~/Downloads/linux-brprinter*[/COLOR]

Press Enter. Type your password when prompted; this will remain entirely  invisible, not even asterisks will show, which is normal.


 e. Follow the steps that the installer script presents you. When asked for the printer model name, type it and press Enter.

An example is best: for a Brother DCP-7065DN you type:
[COLOR=#0000ff] DCP-7065DN[/COLOR]

***Note:*** is there at the end of the model name a letter  between brackets? Then you probably have to omit that letter (including  the brackets).

Example: for the Brother MFC-L9550CDW(T) it becomes:
[COLOR=#0000ff] MFC-L9550CDW[/COLOR]

At the question about the [COLOR=#0000ff]Device URI[/COLOR], you answer **[COLOR=#0000ff]N[/COLOR]** for a USB printer and **[COLOR=#0000ff]Y[/COLOR]** for a network printer.

For a network printer, you select in the next question the last option:
**[COLOR=#0000ff](A): Auto.[/COLOR]** For that, you type the number of that option and you press Enter.


 f. Reboot your computer.


 g. Done! Your printer should work fine now, including the scanner part (when present).

***

Like I said the printer shows up, but I can't actually print to it...

---

### Post by shannon3 on 2015-05-09
Got it to work. I was looking at the printer settings through CUPS and that was saying it was connected via USB. Once I switched it over to network it's working fine.

---

