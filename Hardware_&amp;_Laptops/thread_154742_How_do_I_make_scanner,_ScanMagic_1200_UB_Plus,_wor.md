---
title: "How do I make scanner, ScanMagic 1200 UB Plus, work?"
date: 2006-04-03
forum: Hardware &amp; Laptops
---

### Post by Crochetchick on 2006-04-03
I own a ScanMagic 1200 UB Plus scanner made by Mustek. This was a gift from Earthlink awile back.

When trying to open xsane scanner program an error box appears:
Failed to open device 'gt 68xx:libusb:001:006':Invalid argument

The Device Manager lists the scanner as:
Artec Ultima 2000 (GT6801 based)/Lifetec LT9385 Scanner

I am clueless on how to continue or even approach the problem. I wasn't able to find any information that is understandable to me. Will someone please help me through this?

---

### Post by Sef on 2006-04-03
Read this and it has some links to help you more:

[http://linux.about.com/library/cmd/blcmdl5_sane-mustek_usb.htm]("http://linux.about.com/library/cmd/blcmdl5_sane-mustek_usb.htm")

---

### Post by claydoh on 2006-04-04
basically you need to copy a firmware file to /usr/share/gt68xx, or possibly edit a config file telling sane where to look for the file

[http://www.meier-geinitz.de/sane/gt68xx-backend/]("http://www.meier-geinitz.de/sane/gt68xx-backend/")
has what you need, there are firmware downloads and more details way at the bottom of the page, look for ScanMagic in the models section for the download link


The correct path for the gt68xx.conf is /etc/sane.d/gt68xx.conf

---

### Post by Crochetchick on 2006-04-12
Okay, I went to the Sane site that you directed me to, claydoh.

Reading through and from what I understand I need to download and put in the firmware to directory /usr/share/sane/gt68xx.conf, then change the gt68xx.conf file.

So, I changed the /etc/sane.d/gt68xx.conf with gedit to reflect my scanner:

Mustek ScanExpress 1200 UB Plus:
override "mustek-scanexpress-1200-ub-plus"
firmware "sbfw.usb"

But, I don't know how to put the firmware in the directory, it won't let me drag it in. What do I do to put it in?

---

### Post by claydoh on 2006-04-12
you can do this one of 2 ways:

open a filemanager with sudo privileges:
```
gksudo nautilus
``` 
and drag the file to he correct directory.
from the command line:
```
sudo cp /path/to/sbfw.usb  /usr/share/sane/gt68xx.conf/sbfw.usb
```

or, edit the gt68xx.conf to reflect whichever directory you want:

Example: If your sbfw.usb is in your home directory edit the firmware line to read:
>  firmware "/home/<your-username>/sbfw.usb"

---

### Post by Crochetchick on 2006-04-13
I used the file manger like you said, claydoh, and dragged the firmware into directory:
/usr/share/sane/gt68xx.cont

The edited file is:
/etc/sane.d/gt68xx.conf
Looks Like:
Mustek ScanExpress 1200 UB Plus:
override "mustek-scanexpress-1200-ub-plus"
firmware "sbfw.usb"
(for this one i just removed the # marks in front of the lines and added firmware line)

Even after a restart, still getting the error message when opening Xsane:
Failed to open device 'gt 68xx:libusb:001:006':Invalid argument

Thanks for your help, what should I do now?

---

### Post by claydoh on 2006-04-14
**terrible oops on my part,** the correct path should be 
/usr/share/sane/gt68xx/sbfw.usb, so the correct command is
```
sudo cp /path/to/sbfw.usb  /usr/share/sane/gt68xx/sbfw.usb
```
and **not  **/usr/share/sane/gt68xx.conf/sbfw.usb

It probably won't hurt to have it there, but you most likely will not need the "firmware" line unless you want to put the file somewhere else

---

### Post by Crochetchick on 2006-04-14
This is the path I used for the firmware:

/usr/share/sane/gt68xx/sbfw.usb

I just miss typed in my previous post.

So the firmware is in the correct place and I edited the gt68xx.conf file again to take out the firmware line.
Now it looks like this:

Mustek ScanExpress 1200 UB Plus:
override "mustek-scanexpress-1200-ub-plus"

It still doesn't work  :-k In the Device Manager it shows up as the Artec Ultima, the same as when I started. What else do I need to do?

---

### Post by Crochetchick on 2006-04-19
I have an idea to get this to work, but not sure.

Since linux is listing the scanner as Artec Ultima 2000 (GT6801 based)/Lifetec LT9385 Scanner, maybe that is what the internal chip really is and for some reason they put a different name on it. (Leftover parts???)

My idea is to install it as the Artec Ultima scanner which calls for firware files
ePlus2k.usb or Gt681xfw.usb

Where can I get the firmware files, they are not at the sane website?

Is this a good idea? Please someone help!

---

### Post by franzmaximilian on 2006-10-13
I also have a Mustek 1200 UB Plus scanner and faced all the mentioned problems and tried all solutions offered along this thread, with no success.
Xsane always refused to start.

Only today i found on Ubuntu Documentation this page:
[https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)

At this page I found this instruction:

If your scanner is a Mustek 1200 UB Plus you will need this file [WWW] sbfw.usb then rename it to "PS1fw.usb" then put the file in the directory "/usr/share/sane/gt68xx" (remember to give read permission to all users)

Ok, I renamed my sbfw.usb and something changed: xsane now starts, but.... no way I can perform a scan! When I hit the Scan or the pre-scan buttons I get an error message saying there is an invalid argument.
I also tried downloading the true PS1fw.usb file and using it, but nothing changed: still an invalid argument. At a second attempt to scan, I get a "device busy" error.
Last attempt was to rename as PS1fw.usb the original SBfw.usb file from the Mustek drivers CD for WinXP. Something different again happens this time: only 1 out of the usual 3 windows of xsane opens. Hitting the scan button I get an I/O error message.

Now, it seems that Mustek 1200 UB Plus works for someone and not others (including me). I think someone should investigate which are the differences.

Hoping someone could come out with a winning solution, I gratefully thank in advance for any help!
Franz

---

### Post by Crochetchick on 2006-10-13
Thank you for your post franzmaximilian, it was very helpful for me!

I followed the directions at the link in your post and now I am able to scan.

So sorry you were not at as lucky. I thought there wasn't a solution and gave up for a bit and was suprised to see a post! I really hope someone will come through for you too.

---

