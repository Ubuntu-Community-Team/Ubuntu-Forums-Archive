---
title: "Problems with Brother MFC250C under Xubuntu 17.10"
date: 2018-01-01
forum: Hardware
---

### Post by raphaell2 on 2018-01-01
I'm trying to get a Brother MCF250C combined printer/scanner to work under Xubuntu 17.10.

I downloaded two deb files from the Brother website ( [http://support.brother.com/g/b/downloadtop.aspx?c=us&lang=en&prod=mfc250c_all](http://support.brother.com/g/b/downloadtop.aspx?c=us&lang=en&prod=mfc250c_all)  ), then I followed all the applicable instructions on another brother website ( [http://support.brother.com/g/s/id/linux/en/before.html?c=us&lang=en&prod=mfc250c_all&redirect=on](http://support.brother.com/g/s/id/linux/en/before.html?c=us&lang=en&prod=mfc250c_all&redirect=on)   ), and then I installed the two deb packages. 

Now, the scanner side of the device doesn't work at all under Xubuntu, but that's not my main problem. On the printer side, it's apparently a matter of luck whether something gets printed out correctly, or perhaps it depends on the type of file I'm trying to print. The printer test page prints out perfectly fine. When I tried to print a fairly colorful pdf file, it was printed in monochrome or near monochrome (and I checked the settings; the printer wasn't set to greyscale). When I tried to print a small text file directly from the text editor (mousepad), only the lowest parts of the letters in the last line were printed at the very top of the "printed" page. Then I opened the same text file with LibreOffice Writer, and I could print it just fine. 

It's not really a serious problem for me - I dual boot, so I can always just print stuff under Windows. But it would be nice if I could print reliably from Xubuntu as well.

---

### Post by kurt18947 on 2018-01-01
I wonder if 17.10 has some sort of issue with SANE or something. I have two networked Brother printers installed and both work as expected for printing but scanningg? Nope, no how. I also have a Samsung SL-M2870 (I think that's the model) and it won't scan either but will print as expected. The fact that the Samsung doesn't work either makes me suspect it's an Ubuntu problem not a Brother or Samsung problem. All the machines scan as expected under 16.04 using the same manufacturer provided drivers.

---

### Post by raphaell2 on 2018-01-02
For the record, I've now switched to Xubuntu 16.04, and it's still the same - scanning doesn't work (neither through Simple Scan nor Skanlite nor Xsane), and the colorful pdf file still gets printed less colorful than under Windows.

---

### Post by pdc on 2018-01-02
you don't mention if this is a wireless connection; when one uses the Brother Installer Tool, I think it covers the several hurdles one needs to cross with a Brother scanner

Brother provide an FAQ [http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on)

1) install libusb ..... even if wireless

2) copy the files that are covered here [http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101)

3) if wireless this may not apply [http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04](http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04) but I suspect still worth doing

---

### Post by gifford on 2018-01-03
Are you setting this up as a network printer or is it attached to your computer? Sometimes Brother printers/scanners can be finicky and require using the terminal to set them up.

---

### Post by raphaell2 on 2018-01-03
It's not a network printer - it's directly connected to my pc through USB. Sorry for not mentioning those things before. I've now followed all the instructions in the links posted by pdc (except installing libusb - when I tried that, I was told that it is already installed), but it's still not recognized as a scanner and the printing is still less than perfect.

---

### Post by gifford on 2018-01-04
The only suggestion I can offer is to go through the process of installing drivers again using the command line following the instructions on the Brother site. When you download the drivers, the site will offer instructions on how to install using the terminal command line. In my experience of using several Brother MFC devices in Ubuntu, I have always used the terminal to install drivers and configure the OS for installation. Although there are several tools for installing, it seems that often you find in the forum that using them can cause issues. As I indicated before, I have never had a problem installing using the command line for printing or scanner use.

---

### Post by kurt18947 on 2018-01-04
You have to use the command line to install Brother's drivers or to use Brother's installer. If I wanted to install Brother's .deb files I'd just keep the page with examples open and open a terminal on top. Copy/Paste while making any required modifications works just fine and prevents typos.

---

### Post by raphaell2 on 2018-01-04
Thank you, everyone. I have now deinstalled the special Brother packages, and reinstalled them using the script provided by Brother, and it still won't scan. Sigh.

---

### Post by pdc on 2018-01-05
there seems to be something special about 17.10 whereby quite a few folks have reported scanning issues; if you report this as a bug to Ubuntu; we can only hope that by April; with 18.04 as the LTS; that all is resolved;

---

### Post by raphaell2 on 2018-01-05
Thank you. As I mentioned earlier in this thread, I switched to 16.04 a few days ago, with no different results. Now, how and where can I report a bug of this type?

---

### Post by sccman on 2018-01-05
The printing problems seem to be an issue at the application level, not the driver level.

For the text file, it may be a problem with mousepad itself because LibreOffice Writer prints the text file perfectly fine. Are you open to using a different text editor like gedit or even LibreOffice Writer?

Also I have a few questions about the other problems:
1) Does sane or the Brother drivers detect the scanner at all? Not the printer but the actual scanner itself.
2) What application did you use to print the PDF?

---

### Post by raphaell2 on 2018-01-05
> For the text file, it may be a problem with mousepad itself because  LibreOffice Writer prints the text file perfectly fine. Are you open to  using a different text editor like gedit or even LibreOffice Writer?

Sure, I've already installed kate (I'm using some other KDE apps anyway, so why not?). Just test-printed a very short txt file with it - the first sign of the one line is missing, and so is most of the header and footer stuff (the metadata that's not in the file itself, but added by kate for the printing). I don't have any problems with using LibreOffice to print files.

> Also I have a few questions about the other problems:
1) Does sane or the Brother drivers detect the scanner at all? Not the printer but the actual scanner itself.

Not sure about sane, but the three scan apps I tried (Simple Scan, Skanlite, and Xsane) all report that they can't find a scanner, so I assume that sane doesn't detect it. 

> 2) What application did you use to print the PDF? 				

Evince.

---

### Post by raphaell2 on 2018-01-06
**I've now gotten it to work as a scanner under Xubuntu! **Ok, there's still a bit of a problem where it cuts off a bit of the edge, but generally it scans fine. I copied all the files one of the links in pdc's post called me to copy, and then reinstalled sane. I hadn't planned to reinstall sane, but I had accidentally deleted a sane-related file while copying the files, so I thought a reinstall was the safest bet.

---

### Post by raphaell2 on 2018-01-06
Here are some photos to demonstrate the printing issues, if I can link to them here correctly. 

First, printouts of the pdf I talked about under Windows (left) and Xubuntu (right) (I'm not showing you the whole page for privacy reasons): 
[https://ibb.co/dS5y9w](https://ibb.co/dS5y9w)
Second, an excerpt from the left edge of the same page under Windows (right) and Xubuntu (left):
[https://ibb.co/gJbS2G](https://ibb.co/gJbS2G)
Third, for comparison, a printout of the standard Ubuntu test print page. I don't know how it's supposed to look like, but this is how my printer has always printed it:
[https://ibb.co/kxWuhG](https://ibb.co/kxWuhG)

(Sorry, I couldn't get the pictures to show up here directly.)

Oh, and for the record, the sounds the printer makes when printing that pdf file under Xubuntu are different from the ones it makes when printing it under Windows. Under Xubuntu, it sounds like "wheeewheeewheeewheeewheeewheee", while under Windows it sounds more like "wheeeeeeeeeeeeeeeewheeeeeeeeeeeeeeewheeeeeeeeeeee".

---

