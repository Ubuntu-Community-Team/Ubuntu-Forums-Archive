---
title: "Canon Pixma Mp460 seems to work!"
date: 2007-06-25
forum: Hardware &amp; Laptops
---

### Post by Sohum on 2007-06-25
Thanks to easy_target for posting brilliant instructions for mp600 [ here ]("http://ubuntuforums.org/showpost.php?p=2763437&postcount=4")

It's basically the same, except you use the mp160 drivers instead.

Download the files "cnijfilter-common-2.70-1.i386.rpm" and "cnijfilter-mp160-2.70-1.i386.rpm" from [here]("http://canon.com.au/products/all_in_one_printers/all_in_one_printers/mp160_support.aspx")

Produce deb packages with alien
```
sudo alien cnijfilter-common-2.70-1.i386.rpm
sudo alien cnijfilter-mp160-2.70-1.i386.rpm --scripts
```

Install required packages
```
sudo apt-get install libxml1
sudo apt-get install libglib1.2
sudo apt-get install libtiff4
```

Use dpkg for installing the debs you produced with alien
```
sudo dpkg -i cnijfilter-common_2.70-2_i386.deb 
sudo dpkg -i cnijfilter-mp160_2.70-2_i386.deb
```

Create some symbolic links
```
sudo ln -s /usr/lib/libpng12.so.0 /usr/lib/libpng.so.2
sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
```

Restart CUPS
```
sudo /etc/init.d/cupsys restart
```

Setting up the printer:

Go to System -> Administration -> Printing

1. Double-click "New Printer"
2. Select option "Canon MP160 (USB Printer #1 with status readback for Canon IJ)" , click forward
3. If the driver option "MP160 Ver.2.70" is not available in the list, select "Install driver" at the bottom and locate it at "/usr/share/cups/model/canonmp160.ppd"

Follow the remainder of the process to completion and print a test page to make sure that it is working.

I haven't tried much printing, but it seems to work perfectly.

---

### Post by jtp51 on 2007-07-02
I followed the instructions as written, however I cannot print out a test page.

Plus, I've rebooted and turn the printer on and off.

I think we're on the right track, just don't know what else to try.

Thanks,

---

### Post by letubenaiah on 2007-07-05
I've also followed the instructions listed and I can't print a test page either...anyone have any other ideas?

---

### Post by monkeytech on 2007-07-06
I am having the same issue, cant print after following these insructions, the print que icon apares the is gone again.. no action on printer, i have tried the feww turbo linux drivers and they work great, 

also anyone know how to get the scanner to work without having to use xsane as root?

---

### Post by attunezero on 2007-08-30
Try this guide. Worked for me on kubuntu 7.04 when the above guide didnt.

[http://benaiah41.wordpress.com/tag/linux/](http://benaiah41.wordpress.com/tag/linux/)

---

### Post by onero on 2007-09-10
Argh, for some reason I can't find the files in the given Canon Australia site. Could someone upload them here or give me an alternative download link? Please? :D

My printer is actually an MP450, but I figured I might as well try this ^^ Unless someone knows of alternative instructions for the MP450? Thanks! :D

---

### Post by metapaso on 2007-09-11
> **onero said:**
> Argh, for some reason I can't find the files in the given Canon Australia site. Could someone upload them here or give me an alternative download link? Please? :D

My printer is actually an MP450, but I figured I might as well try this ^^ Unless someone knows of alternative instructions for the MP450? Thanks! :D


I found the files on:

[http://www.canon-asia.com/index.jsp?fuseaction=support&prod_type=bj_aio&country=S](http://www.canon-asia.com/index.jsp?fuseaction=support&prod_type=bj_aio&country=S)

Haven't got home yet to try with the printer, but no internet at home either....here goes!

---

### Post by almalaci on 2007-10-10
None of the guides worked for me. I'm actually trying to use this printer on an AMD64 ubuntu machine. Managed to make the deb's from rpm's using a 32-bit live CD, followed the instructions but instead of the test page there's just a row of black and red lines instead of a test page and no prints.. Any help?

---

### Post by discoade on 2007-12-13
sohum yout a genius you saved my life!:guitar:

---

### Post by CycTim on 2008-03-25
I just used the MP150 driver and it seems to be fine on Gutsy - only thing is some of the margins were a little off on the first pdf I printed, but I'll look at the details later..

Could just be a 'fit to page' or zoom problem, but I can't be bothered trying to fix it right now..

---

### Post by almalaci on 2008-03-25
I bought turbolinux, so that's the end of messing about for me. 
Cost quite a bit to learn to choose the right hardware before buying next time..

---

### Post by tenroc2o0o on 2008-04-27
[MP160 driver]("http://support-au.canon.com.au/contents/AU/EN/0900705501.html")
[Common driver]("http://support-au.canon.com.au/EN/search?v%3aproject=ABS-EN&v%3afile=viv_0tpRDc&v%3astate=root%7croot&opener=full-window&url=http%3a%2f%2fsupport-au.canon.com.au%2fcontents%2fAU%2fEN%2f0900718411.html&rid=Ndoc4&v%3aframe=redirect&&sid=6")
There are the two download links for the two drivers required. The "common" one is actually the 3rd "Mp160 Printer Driver Ver. 2.70" link listed on the site and doesn't seem to differentiate between each one. I had to just try all the links until i found the right filename.

I had tried another method listed here but didn't work for me. When I printed it said there was a filter missing or something. Then I tried these directions in this post and it worked! 

Printed beautiful Ubuntu test page from Ubuntu Hardy with Canon MP460!

Ironically on the last step when I restarted CUPS my printer woke up and started printing. :P

---

