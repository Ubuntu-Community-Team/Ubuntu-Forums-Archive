---
title: "Brother HL-1201 printer prints nothing on ubuntu 15.10 64 bit"
date: 2016-02-28
forum: Hardware
---

### Post by sujitrjadhav on 2016-02-28
I recently bought Brother HL-1201 laser printer. The installation of driver was smooth on windows as drivers CD was provided with the printer. But on my laptop I have ubuntu 15.10 and while system is able to detect the printer when directly connected to the laptop, it by default recommend a brother 1230 series driver. When I install the printer with the drivers recommended by default by the system it prints nothing. Whenever I give any print, the paper gets injected in the printer but comes out with nothing printed on it. 

I downloaded both files at [http://support.brother.com/g/b/downloadlist.aspx?c=as_ot&lang=en&prod=hl1201_as&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=as_ot&lang=en&prod=hl1201_as&os=128) and installing them and following instructions at those pages were of no use. 
```
dpkg -l  |  grep  Brother
``` has following output

ii  hl1110lpr:i386                                       3.0.1-1                                    i386         Brother HL-1110 LPR driver
ii  hl1200lpr:i386                                       3.0.1-1                                    i386         Brother HL1200 LPR driver
ii  printer-driver-brlaser                               3-3build1                                  amd64        printer driver for (some) Brother laser printers
ii  printer-driver-ptouch                                1.3-8ubuntu1                               amd64        printer driver Brother P-touch label printers


[FONT=sans-serif][COLOR=#000000]**Please help solve the problem**[/COLOR][/FONT]

---

### Post by justen_m on 2016-02-28
I had the same problem with at Brother HL-2140. Just blank pages came out. Maybe my solution will help you. My problem was choosing the wrong driver. By default, it was picking the Brother HL-2140 (that was good), but it was choosing the PostScript driver. Go to the printer's properties, Then Change Make and Model. Click Forward to select Brother again, like the initial install, In the right column, pic a driver other than Postscript. I actually picked the HL-1250 driver. You want to pic one that uses PCL5 or PCLXL. Another one to try is the HP LJ5 driver.

Maybe this is a kludgy workaround, but it works for me. I share the printer too, and can print from any of the other systems on my network, to. Again, when I set up the printer on the other computers, I select something other than the Postscript driver. I've done this on 14.04.3LTS, 14.10, 15.04, 15.10, and 16.04.

---

### Post by justen_m on 2016-02-28
I just checked my user's manual. My printer doesn't even support Postscript. Just GDI. Ubuntu, however, defaults to using Brother HL-2140 Foomatic/Postscript. Hence the source of my problem, and maybe yours. For Windows, it uses its  GDI driver, too. It did, anyway. This printer is 7 years old. Shrug. It does work fine under Windows 7 and 10, using whatever driver Windows is using. No special tricks required there.

[edit] Since my printer doesn't support any PDLs, just host-based rendering, PCL wouldn't work either. Maybe I tried that too and it those didn't work either? It's been a while.

---

### Post by sujitrjadhav on 2016-02-29
Problem solved. Here is what worked for me

I downloaded Driver Install Tool from [http://support.brother.com/g/b/downloadlist.aspx?c=as_ot&lang=en&prod=hl1110_us_eu_as&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=as_ot&lang=en&prod=hl1110_us_eu_as&os=128). I had tried this option previously too but whenever the tool asked me printer model number I entered hl-1201 and the tool did not find that model number in it's database. This time I entered hl-1250 instead of hl-1201 and it worked! It looks like that it was not about only postscript drivers but about 64 bit architecture too. The tool installed lot of 32bit libs and in the end I found that a new driver now appear in the drivers list- Brother HL-1250 for CUPS. After selecting this new driver the printer finally printed test page succesfully. Huff.

---

### Post by joienguyen on 2016-09-25
- Because driver of this model is built for i386 and you are running on 64bit (amd64) then firstly you need install 32bit (i386) library via:
sudo dpkg --add-architecture i386
sudo apt-get update
sudo apt-get install libc6:i386 libncurses5:i386 libstdc++6:i386
 
- Now you can install driver normally by
Download driver from Brother website for HL-1200/ 1201/ 1211W
Current link:
[http://support.brother.com/g/b/downloadlist.aspx?c=as_ot&lang=en&prod=hl1211w_as&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=as_ot&lang=en&prod=hl1211w_as&os=128)
OR 
select Drive from Ubuntu driver database for this model

Reference,

---

