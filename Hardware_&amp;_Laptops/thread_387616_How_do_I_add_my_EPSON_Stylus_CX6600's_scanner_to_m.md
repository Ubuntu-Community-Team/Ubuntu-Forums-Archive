---
title: "How do I add my EPSON Stylus CX6600's scanner to my computer?"
date: 2007-03-18
forum: Hardware &amp; Laptops
---

### Post by gnuwtey on 2007-03-18
I'm trying to add the scanner part of my Epson Stylus CX6600 to my computer as a scanner.

I found a post related to the CX7800 and tried what it said, but it didn't work, even though the instructions were generic enough. Could someone point me in the right direction, giving links if necessary? I'm running Kubuntu Edgy...

BTW, XSane currently returns a no-device error.

---

### Post by gjtoth on 2007-03-18
> **gnuwtey said:**
> I'm trying to add the scanner part of my Epson Stylus CX6600 to my computer as a scanner.

I found a post related to the CX7800 and tried what it said, but it didn't work, even though the instructions were generic enough. Could someone point me in the right direction, giving links if necessary? I'm running Kubuntu Edgy...

BTW, XSane currently returns a no-device error.

Does sane see it when run with sudo? If so it could be a permissions issue.  Try:

sudo chmod a+rw /proc/bus/usb/*/*

Then try running Xsane.

---

### Post by gnuwtey on 2007-03-19
Nope. I tried what you said, but it still doesn´t work.

---

### Post by mlester on 2007-03-30
Hey I was having the same problem and I found this
[http://doc.gwos.org/index.php/Epson_CX6600](http://doc.gwos.org/index.php/Epson_CX6600)
it made my scanner work

---

### Post by allensaa on 2007-03-30
Hi Gnuwtey,

The Epson CX / Styls range of scanners don't appear to be automatically detected by XSane. Fortunately, the hardware support is there and it's a straightforward way to enable it. Easy? Yes. Obvious? I wish it was - it took me a while to work this one out. Also note that this can be used for just about any USB scanner that doesn't work with XSane to start with.

**1)** First of all, we need to get the model number and USB id to feed XSane. The list for backends can be found here:

> [http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html)

Scrolling down, we should find your scanner model which is the CX6600, and it's associated info about a third down the page:

> CX-6600	USB	0x04b8/0x0805

**2)**All we need to do now is edit the config file under **/etc/sane.d/** to get it working. For Canon, it's **/etc/sane.d/canon.conf**, for HP it's **/etc/sane.d/hp.conf**, and so on... For Epson, hit Alt-F2 and run the command:

```
gksudo gedit /etc/sane.d/epson.conf
```

And on the bottom of the file underneath the line that says **#usb /dev/usb/scanner0**, simply add the line **usb <first-number> <second-number>**, which in the CX-6600's case is:

```
usb 0x04b8 0x0805
```

Save the file, and the scanner's good to go.

---

### Post by imcoverdinskin on 2007-09-18
tried the above resolve but still no scanner, SANE still does not recognize

---

### Post by sdrawkcaBdepyTI on 2008-01-08
I had this issue, tried the fixes listed in this thread, but still didn't have luck. The solution for me came from: [https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/72506](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/72506)

which advised to do:
```
sudo apt-get install libsane-extras
```

With mine, sane-find-scanner was recognizing my scanner but```
 scanimage -L 
```did not. 

So in summary, I tried the fixes to /etc/sane.d/epson.conf and  /etc/udev/rules.d/45- libsane.rules that are listed on other sites, then when that didn't work, I grabbed libsane-extras from the repository and suddenly scanner worked fine! 

Hope this helps someone!

---

