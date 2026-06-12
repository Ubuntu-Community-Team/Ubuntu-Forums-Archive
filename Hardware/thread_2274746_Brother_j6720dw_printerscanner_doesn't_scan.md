---
title: "Brother j6720dw printer/scanner doesn't scan"
date: 2015-04-22
forum: Hardware
---

### Post by hansmex on 2015-04-22
[http://ubuntuforums.org/showthread.php?t=2246878](http://ubuntuforums.org/showthread.php?t=2246878)

Following this thread, I was able to install my printer.

Unfortunately, the scanner doesn't work. Both Simple Scan and Skanlite report that they can't find a scanner.
My printer is connected using a USB cable. 

Operating system = Kubuntu 14.04

Any help would be greatly appreciated.

---

### Post by dino99 on 2015-04-22
check that you have installed it as expected
[http://tutorialforlinux.com/2015/01/14/how-to-easy-install-the-brother-mfc-j6720dw-printer-driver-on-ubuntu-linux/](http://tutorialforlinux.com/2015/01/14/how-to-easy-install-the-brother-mfc-j6720dw-printer-driver-on-ubuntu-linux/)

---

### Post by kurt18947 on 2015-04-22
There are two common gotcha s with Brother scanners. Here is a somewhat useful FAQ. Somewhat because it's a bit dated.

[http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on)

One problem has been that some files are installed in the wrong location. I'm guessing your machine is a brscan4, being pretty new but make sure. Here are the files to check:[INDENT]
[/INDENT]

[LIST=1]
[*][INDENT]Install the scan driver.
[/INDENT]
 
[*][INDENT]Copy the following files under /usr/lib64/ to /usr/lib/.[/INDENT]
 
[/LIST]
[INDENT]
**For brscan4 Users:**
/usr/lib64/sane/libsane-brother4.so.1.0.7
/usr/lib64/sane/libsane-brother4.so
/usr/lib64/sane/libsane-brother4.so.1[/INDENT]
 
The second issues shows up when scanning as a normal user using a USB connection. This problem does not show itself when scanning with SUDO privileges or when using a network connected machine.

I have not used this fix. It's simpler than what I've used.[INDENT]
Ubuntu 10.10, 11.4, 11.10, 12.04, 12.10, 13.04, 13.10**1. **[Click here to download the file.]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brother-udev-rule-type1-1.0.0-1.all.deb&lang=English_lpr")(brother-udev-rule-type1-1.0.0-1.all.deb, ver.1.0.0-1, 2KB)**2. **Run the command.
   **Command:** dpkg -i brother-udev-rule-type1-1.0.0-1.all.deb
[/INDENT]

I've used this method. It works with current versions as well as older.
[INDENT]Ubuntu 9.10, 10.04, 10.10, 11.4, 11.10, 12.04, 12.10**1.** Open "/lib/udev/rules.d/40-libsane.rules" file.**2. **Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):
If there is "LABEL="libsane_rules_end"", add the following 2 lines before "LABEL="libsane_rules_end"".    
  
  The lines to be added---------------------------          
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
      **3.** Restart the OS.
[/INDENT]

It's too bad the installer script doesn't address these but the last time I used it, it did not. I had to edit manually.

 


 

[RIGHT]
[/RIGHT]

---

### Post by hansmex on 2015-04-22
Thank you **very much** for your answers.
> check that you have installed it as expected
[http://tutorialforlinux.com/2015/01/...-ubuntu-linux/]("http://tutorialforlinux.com/2015/01/14/how-to-easy-install-the-brother-mfc-j6720dw-printer-driver-on-ubuntu-linux/")
This is exactly how things went. Same dialogue, same colours even.
> /usr/lib64/sane/libsane-brother4.so.1.0.7
/usr/lib64/sane/libsane-brother4.so
/usr/lib64/sane/libsane-brother4.so.1
These files were present in lib64; I copied them to [B]usr/lib/sane
[/B]> If there is "LABEL="libsane_rules_end"", add the following 2 lines before "LABEL="libsane_rules_end"".
I found this text, and tried to add 
[B][I]# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"[/I][/B]
Unfortunately I cannot save the file. I guess I have to be root to do that, but Kate (name of the editor) doesn't allow me to log in. I don't know how to edit this from a command line.

I will post this answer, restart my computer, then see if anything has changed, and report back.

---

### Post by hansmex on 2015-04-22
Hurray!! It works. :p
Even without adding the two lines, both Simple Scan and ScanLite now see my scanner.

Once again,** thank you very much** for your help!!

---

### Post by dino99 on 2015-04-22
> **hansmex said:**
> Hurray!! It works. :p
Even without adding the two lines, both Simple Scan and ScanLite now see my scanner.

Once again,** thank you very much** for your help!!

Great :p prepare a beer ):P

---

### Post by hansmex on 2015-04-22
Hometown = 's-Hertogenbosch, Netherlands
You're welcome! Lots of beer here!!

---

### Post by kurt18947 on 2015-04-22
Excellent! Each iteration of Ubuntu seems to work a little more smoothly, and perhaps Brother isn't treating linux quite so much like the crazy uncle in the attic:D. In order to edit system files such as udev, you would need sudo privileges.

---

