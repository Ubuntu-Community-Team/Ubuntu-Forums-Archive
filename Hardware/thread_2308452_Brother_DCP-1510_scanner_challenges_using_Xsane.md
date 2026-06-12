---
title: "Brother DCP-1510 scanner challenges using Xsane"
date: 2016-01-03
forum: Hardware
---

### Post by rich35 on 2016-01-03
I've been working for some hours now to get my USB connected Brother DCP-1510 scanner/printer to work. I've installed the appropriate drivers from the Brother linux support page for the DCP-1510 and can successfully print now from other applications but I still have the following scanner challenges:

1) Simple Scan reports "unable to connect to scanner". I can only run Xsane as root (sudo xsane). If I attempt to run the application normally, I receive an error "Failed to open device "brother4:bus1;dev1".

2) In Xsane Setup->Copy, I am unable to select any printer or PDF, although I can produce a hardcopy from a scan to the same DCP-1510. "cups-pdf" has been installed and PDF is an available printer in other applications.

3) Using Xsane (as root) I can scan and see the image! But the images I save regardless of format (png, jpeg, pdf, etc) are all unreadable "Error opening document: Permission Denied". So close!

OS:  Ubuntu 14.04

Any advice would be appreciated!
Rich

---

### Post by roger_1960 on 2016-01-03
Hi

Have you done these things (from the Brother site [http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=gb&lang=en&prod=dcp1510_eu_as&redirect=on](http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=gb&lang=en&prod=dcp1510_eu_as&redirect=on))

Ubuntu 10.10, 11.4, 11.10, 12.04, 12.10, 13.04, 13.10
1. Click here to download the file.(brother-udev-rule-type1-1.0.0-1.all.deb, ver.1.0.0-1, 2KB)
2. Run the command.
Command: dpkg -i brother-udev-rule-type1-1.0.0-1.all.deb
page top

Ubuntu 9.10, 10.04, 10.10, 11.4, 11.10, 12.04, 12.10
1. Open "/lib/udev/rules.d/40-libsane.rules" file.
2. Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):
If there is "LABEL="libsane_rules_end"", add the following 2 lines before "LABEL="libsane_rules_end"". 

The lines to be added---------------------------

# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
 
3. Restart the OS.

I think those will solve your problems.

Roger

---

### Post by kurt18947 on 2016-01-03
Roger_1960's fix will likely do it for you. If not or in the future, I've had very good success with Brother's installer script found here:

[http://support.brother.com/g/b/downloadend.aspx?c=gb&lang=en&prod=dcp115c_eu_as&os=127&dlid=dlf006893_000&flang=4&type3=625](http://support.brother.com/g/b/downloadend.aspx?c=gb&lang=en&prod=dcp115c_eu_as&os=127&dlid=dlf006893_000&flang=4&type3=625)


The machine model has no bearing, you enter the model # after starting the script. It's done a nice job for me in not having to make any tweaks or adjustments post-install. If you download and store it for instance on a flash drive, you might need to mark it executable. If you download and run, it should run without requiring the execute to be set.

---

### Post by rich35 on 2016-01-03
Roger,
With all my searching for Brother linux support, I missed this page. Thanks!

Kurt,
I downloaded and ran that script which allowed me to run Xsane in root, but I still had problems presumably because I hadn't added the device to the [COLOR=#000000]40-libsane.rules file.[/COLOR]

Now might anybody know how I can remove erroneous devices I added in the process of experimenting with brsaneconfig4?

Thanks again!
Rich

---

### Post by kurt18947 on 2016-01-04
> **rich35 said:**
> Roger,
With all my searching for Brother linux support, I missed this page. Thanks!

Kurt,
I downloaded and ran that script which allowed me to run Xsane in root, but I still had problems presumably because I hadn't added the device to the [COLOR=#000000]40-libsane.rules file.[/COLOR]

Now might anybody know how I can remove erroneous devices I added in the process of experimenting with brsaneconfig4?

Thanks again!
Rich

You should have some 'uninstall' scripts in the same folder where the other Brother .deb files are stored. I'm not sure what would happen if you run Brother's installer script on a system with a flawed install already in place. Hopefully the uninstaller will clean up any flaws.

---

