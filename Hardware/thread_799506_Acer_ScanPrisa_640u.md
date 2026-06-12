---
title: "Acer ScanPrisa 640u"
date: 2008-05-19
forum: Hardware
---

### Post by Imagine76 on 2008-05-19
Hi,

I am new to linux and yesterday downloaded and installed Ubuntu 8.04.  Everything works like a dream, except my scanner.

I am using a Acer ScanPrisa 640u and when I open xsane image scanner 0.995 and select the scanner I get the following error message:

Failed to open device 'snapscan:libusb:002:003': invalid argument

I have searched the forums and found the following link [http://ubuntuforums.org/archive/index.php/t-495927.html](http://ubuntuforums.org/archive/index.php/t-495927.html) which I followed.  I am still getting the same error message.

Does anyone know how to get the Acer ScanPrisa 640u working in Ubuntu please?

---

### Post by Imagine76 on 2008-05-20
Does anyone have any ideas please?

---

### Post by Imagine76 on 2008-05-28
Is there anyone that might be able to help.  Please!

---

### Post by vgrisham on 2008-12-19
I just came across this post in trying to solve my own scanner problems. I'm surprised that no one ever replied to your thread; Ubuntu users are usually really helpful. Scanners are often very tricky to get working in Linux. Your unit is however listed as "good" at the SANE [website]("http://www.sane-project.org/sane-mfgs.html#Z-BENQ") (you'll find it under benq).

As it's been seven months since your original post, I imagine you've moved on. Just in case you're still holding on to this scanner and/or Ubuntu, make sure you have xsane and xsane-common installed (you can install both from Synaptic). 

Once you've done that, go to the Applications menu and choose xsane from the Graphics sub-menu. You can also access xsane from the GIMP. 

Good luck.

---

### Post by svenskmand on 2010-01-26
I also have the Acer ScanPrisa 640U and when I connect it and open xsane and select the device it is called

"Acer   FlatbedScanner 13 Flatbed skanner [snapscan:libusb:003:004]"

then it only get the following error message:

"Could not open device 'snapscan:libusb:003:004': invalid argument"

PS: in [here]("http://snapscan.sourceforge.net/") they mention something about a program in "tools/find-scanner" but i do not know how to get this/access this program to identify my scanner in /dev/XXXX :S

Any help here would be nice :)

---

### Post by MultiMike on 2010-03-16
Type "xsane" in a terminal and if you see something like this:
```

[snapscan] Cannot open firmware file /usr/share/sane/snapscan/your-firmwarefile.bin.
[snapscan] Edit the firmware file entry in snapscan.conf.

```Then it means you have not set the firmware file correctly.
Download the firmware from Benq's web site, for example:
[http://benq.eu/support/downloads/download.cfm?file=scanner/drivers/usb/mirascanv403u10_bqa.zip](http://benq.eu/support/downloads/download.cfm?file=scanner/drivers/usb/mirascanv403u10_bqa.zip)

Copy the file "u96v121.bin" to your "/usr/share/sane/snapscan/" folder.
(You'll probably need to create the "snapscan" folder.)

Edit the configuration file for the scanner:
sudo nano /etc/sane.d/snapscan.conf

Make sure the line starting with "firmware" is:
firmware /usr/share/sane/snapscan/u96v121.bin

Save the file and everything should work!

---

### Post by svenskmand on 2010-03-27
Thank you so much, it works like a charm :)

That is I tried it on another system, with a fresh install of kubuntu 9.10, where it worked :)

But on my own system xsane now says that it cannot find any devices :S, I suspect that it is cause by me trying to install sane from source, so a reinstall of the OS should help :)

---

