---
title: "Brother mfc-235c"
date: 2010-10-01
forum: Hardware
---

### Post by stuarttanner on 2010-10-01
Hi all,
        I am having a nightmare with my printer Ubuntu seems to find the printer and installed drivers? but if I try and print nothing happens and if I try and scan in x sane it tells me there was a fatal exception?
any ideas would be great..

stu
oh forgot to mention my printer is a Brother mfc-235c all in one ie fax machine, scanner, printer.

---

### Post by plucky on 2010-10-01
> **stuarttanner said:**
> Hi all,
        I am having a nightmare with my printer Ubuntu seems to find the printer and installed drivers? but if I try and print nothing happens and if I try and scan in x sane it tells me there was a fatal exception?
any ideas would be great..

stu
oh forgot to mention my printer is a Brother mfc-235c all in one ie fax machine, scanner, printer.

Open **Synaptic Package Manager** and search for mfc-235c and you should find ```
brother-cups-wrapper-extra
brother-lpr-drivers-extra
```

Select both and install.Then connect and power on the printer and open **System > Administration > Printing** and select "Add new printer". and install with the correct drivers.

For the scanner go [Here](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html) and download and install the correct driver for your scanner.

You need to use the deb format drivers.The install instructions are also on the website.

Good Luck

---

### Post by stuarttanner on 2010-10-02
hi,
    I did all of this before but i tried again just in case, unfortunately same problems if I try and print it just sits there saying processing?
if I open x sane and try and scan it says failed to open device 'brother:bus2;dev1';invalid argument

:confused:

stu

---

### Post by plucky on 2010-10-02
> **stuarttanner said:**
> hi,
    I did all of this before but i tried again just in case, unfortunately same problems if I try and print it just sits there saying processing?
if I open x sane and try and scan it says failed to open device 'brother:bus2;dev1';invalid argument

:confused:

stu

Is your printer connected by USB?

Post output from a terminal of ```
dpkg -l | grep brother
``` and ```
dpkg -l | grep Brother
``` notice the difference in spelling for "brother".

[color=red]Did you disconnect and reconnect the printer after you installed the drivers?[/color]

---

### Post by stuarttanner on 2010-10-02
hi mate, here is the output from terminal. hope this helps



stu:P
yes i did disconnect and reconnect the printer usb lol

---

### Post by plucky on 2010-10-03
Open **System > Administration > Printing**.

Right click on printer icon and select **Properties**

Is the correct driver selected?
Can you print a test page?
Also check you have the correct setting for paper size.

Another good troubleshooting tool is in your Browser window,to open the CUPS interface,put in the address bar ```
 http://127.0.0.1:631/admin
``` there might be some information in the error log.

For the scanner you need the brscan2 driver,so you can remove the others (brscan & brscan3)
Also install sane-utils ```
sudo apt-get install sane-utils
```

From the Brother website:-

To enable scanning by a normal user > Ubuntu 9.10, 10.04
    1. Open "/lib/udev/rules.d/40-libsane.rules" file.
    2.Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):


    The lines to be added--------------------------- 


    # Brother scanners
    ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
     

    3. Restart the OS. 

Good Luck

---

### Post by stuarttanner on 2010-10-03
hi, how would i go about removing the unneeded drivers, also i cant add the the 2 lines as it wont let me have root permission 


stu

---

### Post by plucky on 2010-10-03
> **stuarttanner said:**
> hi, how would i go about removing the unneeded drivers, also i cant add the the 2 lines as it wont let me have root permission 


stu

Open **Synaptic Package Manager** and search for **brscan** and un-install them from there.

To edit the file ```
gksudo gedit /lib/udev/rules.d/40-libsane.rules
``` Save and then reboot.

Good luck

---

