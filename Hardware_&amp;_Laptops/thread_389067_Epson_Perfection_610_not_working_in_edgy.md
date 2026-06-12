---
title: "Epson Perfection 610 not working in edgy"
date: 2007-03-20
forum: Hardware &amp; Laptops
---

### Post by Devius on 2007-03-20
Hello! 

I'm trying to use my Epson Perfection 610 scanner which is supposed to be supported in sane, but I get an error of _"No scanner device found"_. It's strange since it is detected with the command "sane-find-scanner" like this:

```
found USB scanner (vendor=0x04b8, product=0x0103) at libusb:001:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

```

Using "lsusb" returns this (which appears correct to me):

```
Bus 003 Device 003: ID 0bda:0111 Realtek Semiconductor Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 004: ID 04b8:0103 Seiko Epson Corp. Perfection 610 [COLOR="Red"]<-- Here it is[/COLOR]
Bus 001 Device 001: ID 0000:0000  

```

BUT, when I try XSane I get the mentioned error. Using "scanimage -L" returns this:
```
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```

Any ideas? I tried to compile the source code for the epson driver but I got some errors and gave up on that...

---

### Post by Devius on 2007-03-21
I forgot to mention that it works under Windows although I had to activate the Image Aquisition service. I already searched for such a service in ubuntu but it doesn't exist...

---

### Post by Devius on 2007-03-26
Found the problem. I went to the sane website and took a look at the documentation there (should have done that in the first place). I was able to run scanimage -L as root but nos as the regular user, so it indicated that the regular user didn't have the required permissions to access the scanner (It would be helpful if the program returned an error message stating this!!). I only had to add the regular user name to the scanner group in the file "/etc/group". It's a shame that on almost all ocasions when something goes wrong with linux the user is left on his own to figure out what is wrong... is it that complicated to add meaningful error messages to programs? I guess it must be...

---

