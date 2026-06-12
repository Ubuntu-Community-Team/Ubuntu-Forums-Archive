---
title: "Brother 2140 Printer just keeps kicking out empty sheets"
date: 2017-09-12
forum: Hardware
---

### Post by Richard-S on 2017-09-12
I run Ubuntu 16.04. I loaded the driver from Brother, successfully as far as I can tell. But when I went to print a page, the printer began kicking out blank paper and I can't stop it. I deleted the print queue but it still empties out the paper bin. It doesn't print a word or a mark of any kind. 

I am not sure where to go next.

Richard

---

### Post by pdc on 2017-09-13
so if I was starting from the beginning, I would go here [http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=hll2300d_us_eu_as&os=128&dlid=dlf006893_000&flang=4&type3=625](http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=hll2300d_us_eu_as&os=128&dlid=dlf006893_000&flang=4&type3=625) and download the Brother installer tool.

I would click to DOWNLOAD and SAVE it; and by default it should end up in one's Downloads directory as [color=#0040FF]linux-brprinter-installer-2.1.1-1.gz[/color]

If one opens a terminal, ...... TV screen on bottom toolbar ........ and pastes in the commands below; one by one and hit ENTER after each paste ........ to paste in a terminal, right-click at the text prompt and look for PASTE in the menu that appears
```
cd Downloads
```

```
gunzip linux-brprinter-installer-2.1.1-1.gz
```

the next command starts the installer script; watch as it runs as it may ask you questions you need to answer; 

```
sudo bash linux-brprinter-installer-2.1.1-1 HL-2140
```

_______________
As your existing setup does not work, I suggest you open the PRINTERS folder; delete the existing Brother icon, then do what I suggest above.

---

### Post by Richard-S on 2017-09-13
Thanks pdc. That is exactly the way I installed it. I will do what you suggest and install it again.

Richard

---

### Post by Richard-S on 2017-09-13
[SIZE=3]One more thing: should I have the printer connected to the computer while I am loading the driver? I did not the first time. Most printer drivers in Windows I have used tell me to not connect the printer until the driver is installed.

Richard[/SIZE]

---

### Post by pdc on 2017-09-14
thanks Richard; it doesn't seem to matter too much if you leave the printer on or not ..... if you turn it on before installing drivers, whatever is set up in Mint may jump in and attempt to install a proxy driver; sometimes that is fine, and sometimes not; so I guess if you leave the printer, you get first shot at loading your preferred driver into the system! If one has more than one icon for the printer in the PRINTERS folder, if you right-click on the icon and look in the MAKE & MODEL window, you can see what the system has set up;

if I look at the pre-installed options for Mint, it offers a variety of foomatic drivers for the HL-2140: foomatic is one of the open source drivers, so not one that Brother provides;

---

### Post by Richard-S on 2017-09-14
I left the printer plugged in this time and did what you said and it works now.

I did two things that the Brother support documents suggested as well:

   **4.** Copy brlpdwrapperXXX files under /usr/lib/cups/filter/ to /usr/lib64/cups/filter/
  	**Command: cp 	/usr/lib/cups/filter/brlpdwrapper* /usr/lib64/cups/filter**
 
 
**5.** Copy libbrXXXX files under /usr/lib/ to /usr/lib32/ if /usr/lib32 exists.
  	**Command : cp /usr/lib/libbr* 	/usr/lib32/**
 
 Whether or not that helped I have no way of knowing. It looked harmless, so I did it before I re-loaded the driver.
 


Thanks again.

Richard

---

### Post by pdc on 2017-09-14
well done Richard; glad it is all working now; you did well to work through the Brother support documents as well; copying between libraries certainly appears in the Scanning advice; I must re-read the printing support as well if they mention it; 

as it is your thread, you can go to tools at top-right and mark as SOLVED: folks may well find it useful for similar problems

---

