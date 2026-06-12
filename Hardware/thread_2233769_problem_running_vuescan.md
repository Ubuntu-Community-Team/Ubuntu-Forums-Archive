---
title: "problem running vuescan"
date: 2014-07-10
forum: Hardware
---

### Post by jgw on 2014-07-10
I am running with ubuntu 14.04  I have an epson xp-800 all in one printer.  My problem was getting the scanner to work.  What I did was download and extract the vuescan install file(s)  When I went to /home/greg/VueScan/ and ran the vuescan program it could not find the scanner.  I stopped the vuescan program.   I then went to the vuescan folder and entered "sudo vuescan".  When vuescan came up, this time, it had found the scanner.  I tested and everything was working.  

My problem (if it is one) is, I think, that I should have been able to simply run vuescan and have it find the scanner.  I suspect that libusb (must be installed for vuescan to run) may be the problem but have no idea how I might fix that.  

Anyway, any thoughts on this one are welcome - thank you...................

---

### Post by ajgreeny on 2014-07-10
I wonder if you as user are not a member of the group needed to use the scanner.

Let's see the output of the command **groups** in your user terminal, please.

---

### Post by kurt18947 on 2014-07-10
I'm not sure if Epson has the same issue but Brother's USB scanner driver will only work with SUDO privileges unless I do this:

```
Ubuntu 9.10, 10.04, 10.10, 11.4, 11.10, 12.04, 12.10

**1.** Open "/lib/udev/rules.d/40-libsane.rules" file.

**2. **Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):
If there is "LABEL="libsane_rules_end"", add the following 2 lines before "LABEL="libsane_rules_end"".    
  
  The lines to be added---------------------------          
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
      

**3.** Restart the OS.

```

If you want to try this you'd need to change the {idVendor} to Epson's at the very least.  You could also look through the 40-libsane.rules file to see if there's anything 'interesting' regarding Epson.

---

### Post by jgw on 2014-07-11
thanks for the reply.  Here the the output for groups:

greg@greg-MS-7222:~$ groups
greg adm cdrom sudo dip plugdev lpadmin sambashare

---

### Post by jgw on 2014-07-11
thanks for the reply.

I could do this but I don't have the information necessary, insofar as the scanner on the printer is concerned.  I think my problem is in libusb (necessary to run the scanner) but I am clueless.

---

### Post by jgw on 2014-07-12
OK - got what I wanted.  Thanks for the replies.  Here is what I did.  I edited the sudoers with "sudo visudo" and entered "YOURNAME ALL = NOPASSWD: "/home/greg/VueScan/vuescan" (taken from something I found online)  I then right clicked on the vuescan file and created a link as 'sudo'     I then dragged the link to a programs drawer that I had.  I could have also put it any other place I wanted.  I also checked the sudoers file with "sudo visodo -c" to make sure I didn't screw up.

Marking this one as done.

---

### Post by ajgreeny on 2014-07-13
I am happy that you managed to get this working, and I hope I am wrong about this, but I wonder if you are going to find that any scans that you now save to disk are owned by root and not yourself.

Never having needed to edit my sudoers file in that manner, I may well be incorrect, but thought it worth giving this warning, just in case.

---

### Post by jgw on 2014-07-13
thank you for the thought and I will keep it in mind of I scan anything.  I really don't do much scanning anymore but I had the scanner so I thought I had better hook it up.  My suspicion is that if I setup vuescan properly then the scans will be put in my home system and should probably be permissioned accordingly.  This is, of course, based on my incredible talent for wishful thinking <G>

---

