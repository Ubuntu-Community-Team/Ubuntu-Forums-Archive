---
title: "Network printer works in Ubuntu but not lubuntu"
date: 2015-12-20
forum: Hardware
---

### Post by beenny on 2015-12-20
Hello All,

I recently switched my desktop over to lubuntu and have been happy with the general speed. One problem I've had though is printing. I have a Brother HL-2270DW. The printer is hooked up to my router. I had no problem printing from my desktop when i ran ubuntu. i also have no problem printing from my ubuntu laptop. I just can't print from the new lubuntu install.

when i go to set-up the printer, i look for network printer and it seems to find the device uri in the network. but when i go to print a test page the printer state is  first: "Processing - Connecting to printer." then  "Processing - The printer is not responding." 

i don't really want to switch back to ubuntu (more an annoyance than anything else) but will if i can't get this resolved.

any tips would be greatly appreciated.

best,

bg

---

### Post by Bucky Ball on 2015-12-20
Silly question: Have you installed the driver for it? 

Grab the Driver Install Tool from [here]("http://support.brother.com/g/b/downloadlist.aspx?c=au&lang=en&prod=hl2270dw_all&os=128").

Once installed, Add Printer and when you get to the bit that asks you to select a driver the correct one should now be in the list.

---

### Post by beenny on 2015-12-21
No not a silly question but I did install the drivers. The printer comes up in my list and when I try printing it first says "trying to connect"  and then says can't connect.

---

### Post by SeijiSensei on 2015-12-21
It's puzzling that it should depend on which "flavor" of Ubuntu you choose.  Have you tried installing from [http://localhost:631/](http://localhost:631/) which is my usual method of configuring CUPS?  My Brother appeared in the list of autodetected printers and worked right away.  I'm using Kubuntu 14.04.

---

### Post by beenny on 2015-12-21
i will try that later tonight when i get home. but i did try installing it directly from the brother site as well as through autodetect. both times it installed - just won't print...

---

### Post by beenny on 2015-12-21
So when i go into CUPS the printer is listed there and if i try printing a test page nothing happens. It says "connecting to printer" and then eventually times out...

Any other thoughts on how to fix this?

bg

---

### Post by SeijiSensei on 2015-12-22
It doesn't make any sense to me.  CUPS operates at a level "below" the desktop environment.  You haven't told us what version of Lubuntu you're using.  Is it 14.04.3, or something newer?  If it's newer, have you tried [Lubuntu 14.04.3]("http://cdimage.ubuntu.com/lubuntu/releases/14.04.3/release/")?  14.04LTS is the most stable version with long-term support until 2019.

What flavor and version is the working desktop running?

---

### Post by beenny on 2015-12-23
yes it's 14.04.3 and it's the gnome desktop

i agree it really doesn't make sense to me. but the printer is clearly recognized - it just won't print and other ubuntu computers are able to print from the network

---

### Post by Bucky Ball on 2015-12-23
If you are using straight Lubuntu, it is not the Gnome desktop, unless you've intentionally installed it and switched to a Gnome session. It is lxde. :)

---

### Post by beenny on 2015-12-24
fair enough - i just presumed it was gnome since it reminded me of the old gnome.

any thoughts on how to get printing working?

bg

---

### Post by Bucky Ball on 2015-12-24
None here, unfortunately, and I have exactly the same printer and have installed another for a friend. :|

I'm not near either to have a look at the moment (about 750kms away in fact). I'll dig in when I get back to them in a few days, but hopefully you'll have it fixed by then. If not, I'll shoot my exact settings to you and see if we can't work something out.

---

### Post by beenny on 2015-12-24
thank you - much appreciated. it was very odd b/c i've in general had no problems installing this printer with three other computers...

---

### Post by beenny on 2015-12-30
BB - I was wondering if you were able to get a read on the printer in lubuntu

thanks,

bg

---

### Post by Bucky Ball on 2015-12-30
I don't have Lubuntu, but no matter. The printer settings would be the same regardless. Check the screen shot below from my Printer setup for that printer. If there's anything specific, just ask and I'll see if I can dig it up.

Sorry for the delay. Been on the road and very busy since I got back home. Just sitting down to this and a few other things now. :)

Basically, if the wireless is working on the printer, you should be able to 'add printer> Network printer' and it should be discovered. Go for the one that is showing an entry similar to the entry in 'device URI'. Choose the driver as you go through the process.

The same can be achieved by opening a browser, in the address bar 'localhost:631', which should bring up the CUPS interface, and adding the printer that way. 

But you must have the correct driver installed and ready to select for the printer when you get to that bit which means installing it prior to that bit, not during. 

Good luck.

---

### Post by beenny on 2015-12-31
So I think I see part of the problem - but can't say I understand it.

My laptop has the same URI as the one you provided: 

dnssd://Brother%20HL-2270DW%20series._pdl-datastream._tcp.local/

(and I've found other websites that indicate the same).

However, when I use that URI on the desktop I get a message that the printer can't be found.

When I search for the network printer the URI that comes up is:

lpd://BRW002258955922/BINARY_P1

This computer is attached to the network via ethernet while the laptop is wifi - i'm not sure if that should make a difference.

I also tried this Ubuntu 14.04 via a bootable USB and was still having issues - so i'm wondering if this is a 14.04 issue? The laptop was 14.04 but I don't believe the desktop was when I had it working before.

Thank you again for any more thoughts and happy new year...

bg

---

### Post by Bucky Ball on 2015-12-31
You say you are running a Live session from USB? Not sure how you are going to go with that. Where would you install drivers? The only place is to RAM. On reboot all will be lost. I've never tried to get the printer going from a Live session and wouldn't bother personally. 

Do you have the printer set with a static IP (so the router doesn't serve it a new one everytime it connects). This will make life a lot easier.

---

### Post by beenny on 2016-01-02
> **Bucky Ball said:**
> You say you are running a Live session from USB? Not sure how you are going to go with that. Where would you install drivers? The only place is to RAM. On reboot all will be lost. I've never tried to get the printer going from a Live session and wouldn't bother personally. 

- Yes I tried that as a test. unforntunately didn't seem to work

>  Do you have the printer set with a static IP (so the router doesn't serve it a new one everytime it connects). This will make life a lot easier.

It should be - it is connected directly to my wireless router.

This is quite odd and frustrating. i had no problem installing this printer in the past...

bg

---

### Post by Bucky Ball on 2016-01-02
Are you currently connecting to the printer with any other device and able to print wirelessly?

It is connected to your wireless router wirelessly, yes, but you need to manually set a static IP address on the printer itself. At least that is the way I have done it. You plug in with a USB cable and do it that way. I'm going to check the thread to see what's been said.

* Please run the driver install tool from [post #2]("http://ubuntuforums.org/showthread.php?t=2306978&p=13409719&viewfull=1#post13409719"), printer in with a USB cable. From memory, you will get the opportunity to set the IP then. If you hit the big GO button on the front of the machine five times (or three?) quickly, you'll get the details of the printer, including wireless settings. Have a look. Make sure they're on and check the IP. Is there one?

---

### Post by beenny on 2016-01-02
So I am able to print wirelessly from my laptop running Ubuntu 14.04 (why I originally thought it was a lubuntu problem).

The main difference is that the URI on the laptop is the same as the one you posted while when I use that URI from the desktop it says can't be found. While the "found" URI is much different.

I actually don't have a printer USB. I suppose i can purchase that and theoretically it would solve this issue...

bg

---

### Post by Bucky Ball on 2016-01-02
You don't have a printer USB? There is a USB socket on the printer. Plug that into your computer with a regular USB cable. That's it. Run the driver install tool.

When you add printer, use whatever URI it gives you when it discovers the network printer. 

But first, step one. Grad a USB cable, plug the printer into the computer, run the driver install tool, add printer.

---

### Post by beenny on 2016-01-04
so printing does work fine with USB cable. Odd it wouldn't work on network - but not going to lose too much sleep over fit.

thanks for the help!

bg

---

