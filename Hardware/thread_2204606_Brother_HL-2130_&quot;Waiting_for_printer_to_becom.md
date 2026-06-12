---
title: "Brother HL-2130 &quot;Waiting for printer to become available&quot;"
date: 2014-02-09
forum: Hardware
---

### Post by La46TsPS4n on 2014-02-09
The printer is a Brother HL-2130.
"hl2130lpr-2.1.0-1.i386.deb" and "cupswrapperHL2130-2.0.4-2.i386.deb" were downloaded and installed from here: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2130](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2130)

[http://localhost:631/printers/HL2130](http://localhost:631/printers/HL2130) was used to try to print a testpage: [http://i.imgur.com/p8ijQ9Q.png](http://i.imgur.com/p8ijQ9Q.png)
Output of "System Tools - Printers"r: [http://i.imgur.com/mrAQvNb.png](http://i.imgur.com/mrAQvNb.png)

Output of "lpstat -t":
```

scheduler is running
system default destination: HL2130
device for HL2130: usb:/dev/usb/lp0
HL2130 accepting requests since So 09 Feb 2014 17:45:43 CET
printer HL2130 now printing HL2130-14.  enabled since So 09 Feb 2014 17:45:43 CET
    Waiting for printer to become available.
HL2130-14               anonymous         1024   So 09 Feb 2014 17:45:43 CET


```

Output of "lsusb | grep Brother":
```
Bus 002 Device 017: ID 04f9:003f Brother Industries, Ltd 
```

The printer works fine with Windows 7 32 Bit and 64 Bit.

So the question is: How to make this printer print?

---

### Post by gifford on 2014-02-11
So this is set up to use USB and not a network? What version of Ubuntu are you using?

---

### Post by La46TsPS4n on 2014-02-12
Yes, the printer is plugged in with a USB cable and is listed by lsusb. The lubuntu version is this one: [http://cdimage.ubuntu.com/lubuntu/releases/13.10/release/lubuntu-13.10-desktop-i386.iso](http://cdimage.ubuntu.com/lubuntu/releases/13.10/release/lubuntu-13.10-desktop-i386.iso) (13.10)

---

### Post by Bucky Ball on 2014-02-12
You need to add the printer either in 'Printing' or go to 'localhost:631' and set the printer up there, install the driver there, print a test page from there.

You should get a configuration page at 'localhost:631'. Check out what printers you have set up and what jobs, if any, are queued and what could be the hold up.

---

### Post by La46TsPS4n on 2014-02-15
> **Bucky Ball said:**
> You need to add the printer either in 'Printing' or go to 'localhost:631' and set the printer up there, install the driver there, print a test page from there..

I don't quite understand that sentence. How would I install drivers in a browser?

Anyway, I got it working. The problem was that I skipped step 5a here: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)
[http://localhost:631/printers/HL2130](http://localhost:631/printers/HL2130) had the text:
"Connection: usb:/dev/usb/lp0"
but it should be something like:
usb://Brother/HL-2130%20series?serial=D1N201209
I could set that this way:


[LIST=1]
[*]Modify Printer 
[*]Modify Printer 
[*]This opened a new page where I could select "Local Printers: usb://Brother/HL-2130%20series?serial=D1N201209" 
[*]Continue (Here I could set some text for where the printer is located at, text does not matter) 
[*]Continue (Displays huge list with "Current Driver - Brother HL2130 for CUPS" selected) 
[*]Modify Printer (Displays "Printer HL2130 has been modified successfully.") 
[/LIST]

And then I could print a test page.

---

### Post by Bucky Ball on 2014-02-15
Good news. What I meant was that if you type 'localhost:631' into say Firefox it will show you all printers that are connected via CUPS. You can set up printers there, including installing drivers. ;)

Give it a shot. If your printer is working open Firefox and go that address then click 'Printers'. You should see your printer there functional and idle.

Glad it's working, good luck and enjoy the ride!

---

