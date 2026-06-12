---
title: "Can't get Brother scanner to work"
date: 2010-08-05
forum: Hardware
---

### Post by jedson3 on 2010-08-05
Hi

I have hooked up a Brother MFC-495CW  printer/scanner/copier/fax machine to my computer with a USB cable. I use Ubuntu 10.04. Followed the instructions at the Brother Solutions Center. Printer works fine, but I can't seem to get Xsane to connect with the scanner. Get the message “Failed to open device brother3; bus5; dev1 invalid argument.” What might that mean?

jedson

---

### Post by phoenixcor on 2010-08-05
following, same problem

---

### Post by phoenixcor on 2010-08-05
this link my help you

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

i just cant edit the script for some reason

---

### Post by jedson3 on 2010-08-06
Yes, that's where I went already, and tried to follow all their instructions. Either I did something wrong, or the instructions aren't quite right. We don't seem to be getting much help here at the moment. Where do you think we go from here? Repost? Try the Linux forum? This site is often very helpful, but you can get lost in the shuffle. 

jedson

---

### Post by jedson3 on 2010-08-06
PS. Re editing the script, most often when I have had that problem its because I needed to be in root. 

jedson

---

### Post by roger_1960 on 2010-08-06
Hi

Have you done this

> Ubuntu 9.10, 10.04
    1. Open "/lib/udev/rules.d/40-libsane.rules" file.
    2.Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):


    The lines to be added--------------------------- 


    # Brother scanners
    ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
     

    3. Restart the OS. 

Taken from the Brother site and called "Setting for normal users"  I found that Brother scanners are not recognised without it.  You do need to open the file to edit with gksudo gedit (or equivalent)

---

### Post by jedson3 on 2010-08-06
Worked like a charm. What a relief. Can't tell you how much I appreciate your help on this!! It should be marked as "solved" but I don't see where to do this. 

Jedson

---

### Post by roger_1960 on 2010-08-06
Hi

Glad it worked, took me ages to find it a couple of years ago!

To mark solved, click on "thread tools" in red at the top of the post and select it...

---

### Post by popaclay on 2010-12-31
> **roger_1960 said:**
> Hi

Glad it worked, took me ages to find it a couple of years ago!

To mark solved, click on "thread tools" in red at the top of the post and select it...

Thanks very much, worked great!

---

