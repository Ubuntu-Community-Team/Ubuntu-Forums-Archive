---
title: "Problems installing Brother MFC-J470DW Printer / Scanner"
date: 2014-07-11
forum: Hardware
---

### Post by maxws43 on 2014-07-11
Tried to install th MFC-J470DW using the script from [http://support.brother.com/g/b/index.aspx#u9.10](http://support.brother.com/g/b/index.aspx#u9.10).  Printer installed, scanner did not.  Contacted their email help service, they told me to run the script. After three tries I looking in the forum.  I found:

Ubuntu 9.10, 10.04
    1. Open "/lib/udev/rules.d/40-libsane.rules" file.
    2.Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):


    The lines to be added--------------------------- 


    # Brother scanners
    ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
     
I have Ubuntu 12.04.  Do I need to do this?

I am a newbie to Ubuntu, my programming skills are in Basic, DOS, Fortran.

I made this change using gedit, but it would not allow me to save it in the "rules.d" directory.  I saved it in "Home".
How do I get the new file to the "rules.d" directory?

---

### Post by davidvandoren on 2014-07-12
Open the terminal.
or
Ctrl+Alt=T

In the terminal window ```

[COLOR=#000000]gksudo gedit [/COLOR][COLOR=#000000]/lib/udev/rules.d/40-libsane.rules[/COLOR]
``` 

make your changes in the file that opens.
Save and close the file.
restart your pc.

should wiork

---

### Post by maxws43 on 2014-07-12
Thanks.  Your code allowed me to update the [COLOR=#000000]/lib/udev/rules.d/40-libsane.rules[/COLOR] file but that did not fix my problem.

I am running a dual boot Windows / Unbuntu 12.04.  The MFC-J470DW install under Windows, prints and scans.  Under Unbuntu it prints but will not scan.  If I try to scan using the key pad "scan" botton it says "Conneting to PC", the lights flash for about 20 seconds, and then it goes back to input screen without the scanner starting.

I have varified that the change to 40-libsane.rules is as shown above, rebooted, re-ran the Bother script, rebooted, but no scan.

Any suggestions would be appreciated.

Max

---

### Post by kurt18947 on 2014-07-13
> **maxws43 said:**
> Thanks.  Your code allowed me to update the [COLOR=#000000]/lib/udev/rules.d/40-libsane.rules[/COLOR] file but that did not fix my problem.

I am running a dual boot Windows / Unbuntu 12.04.  The MFC-J470DW install under Windows, prints and scans.  Under Unbuntu it prints but will not scan.  If I try to scan using the key pad "scan" botton it says "Conneting to PC", the lights flash for about 20 seconds, and then it goes back to input screen without the scanner starting.

I have varified that the change to 40-libsane.rules is as shown above, rebooted, re-ran the Bother script, rebooted, but no scan.

Any suggestions would be appreciated.

Max

The install script does not (unfortunately) fix two scanner install problems.  One is the 40-libsane.rules which you have fixed, the other is installing some files in the wrong location. That problem is addressed in this Brother FAQ solution:

[http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101)

---

### Post by maxws43 on 2014-07-13
Scanner is working, but I still have an issue.

The problem at [http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101) was not it.  The files that were listed to be copied to user/lib were already there.

But I had never seen the Linux FAQ.  When I went to the Brother FAQ link I had jumped on "scan", missing "Linux Information".  Reading the Linux Scan FAQ I found a statement that for the scan key to work you must open port 54925.  I had been checking the scanner using the scan key since that is easier than XSANE.   Using XSANE my scanner works.  

I would like to get the scan key to work.  The directions at [http://support.brother.com/g/s/id/linux/en/before.html?c=us_ot&lang=en&redirect=on#103](http://support.brother.com/g/s/id/linux/en/before.html?c=us_ot&lang=en&redirect=on#103)  Procedure (9) are beyond my newbie skills.  Would appreciate someone walking me through it.

---

### Post by kurt18947 on 2014-07-14
I'm glad to hear your scanner is working. I believe procedure 9 only applies to network connections and I'm not certain it's applicable to Ubuntu, only Open SUSE and Fedora are mentioned.  I did set up scan-key-tool one time using a USB connection and don't recall opening any firewall ports.  The shortcoming I found with scan key was I didn't see an obvious way to assign a file name or choose the destination for the resulting file.  I also spent very little time on it so there may be a way to fix those issues.

---

