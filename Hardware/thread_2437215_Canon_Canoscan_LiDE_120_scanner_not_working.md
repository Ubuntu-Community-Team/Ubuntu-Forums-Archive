---
title: "Canon Canoscan LiDE 120 scanner not working"
date: 2020-02-20
forum: Hardware
---

### Post by sussexlad on 2020-02-20
Using 18.04

I'm hoping I can get this working with Simplescan. When you plug it into a USB port, the scanner appears in Settings/Device Colour Profiles but there is no ON/OFF switch as with the other devices, it just says 'Not calibrated' and apparently requires a Profile file added. Where do I find this and how is it installed? I've tried several suggestions but don't really understand what I'm doing !

If you do try and do a scan, it says 'Failed to scan, unable to connect to scanner'.

Cheers

---

### Post by rbmorse on 2020-02-20
The error message about the scanner not being calibrated is inconsequential, at the moment. 

real problem is the software can't find your scanner, although some of the hardware apparently can. 

Open the terminal application and run the command: 

```
sane-find-scanner
```

The output should contain a line that starts with "found".  Post that line in a reply using code tags (may be easier to used advanced editor by clicking on "go advanced" near the bottom of the reply window).  

Do you get a different result if you run: 

```
sudo sane-find-scanner
```

---

### Post by rbmorse on 2020-02-20
If there is no line that starts with "found" from the sane-find-scanner command, run this command from a terminal: 

```
[COLOR=#242729][FONT=Consolas]sudo apt -y install sane libsane libsane-common sane-utils libsane-extras
```

and try the sane-find-scanner command again.  If you get a "found" result, try simplescan. [/FONT][/COLOR]

---

### Post by dragonfly41 on 2020-02-20
Join the club. My Canon LIDE 600F does not work either. although above test command gives this.

found USB scanner (vendor=0x04a9 [Canon], product=0x2224 [CanoScan]) at libusb:001:009

---

### Post by sussexlad on 2020-02-20
Thanks for the reply

Only when using the sudo command I get...

found USB scanner (vendor=0x04a9 [Canon], product=0x190e [CanoScan], chip=GL848+) at libusb:003:005
found USB scanner (vendor=0x0b05 [Broadcom Corp], product=0x17cb [BCM20702A0]) at libusb:003:004

If I do try Simplescan I get 'Failed to scan, unable to connect to scanner'.

---

### Post by rbmorse on 2020-02-20
Likely a permissions issue.  What happens when you open a terminal and run:

```
sudo simple-scan
```

---

### Post by kurt18947 on 2020-02-20
No details but some scanners require adding a couple lines to a udev file when connected via USB. You might be able to do a temporary bypass by running simple scan in Administrator mode, something like "sudo simple-scan" or similar. It's been years since I've had to mess with this so I'm not up to speed.

---

### Post by sussexlad on 2020-02-20
The Simplescan window opens with 'Ready to Scan', a little latter it adds Canon LiDE 120

If I then click the 'Scan' button, the terminal shows.

[bjnp] create_broadcast_socket: ERROR - bind socket to local address failed - Address already in use
[bjnp] create_broadcast_socket: ERROR - bind socket to local address failed - Address already in use

Simplescan shows the same 'Failed to scan, unable to connect to scanner'.

---

### Post by rbmorse on 2020-02-20
OK...we know that SimpleScan detects and recognizes the scanner when run in administrator mode.  

And now, for the life of me, I have simply forgotten to troubleshoot this.  Used to have to do it all the time but today I'm drawing a blank.  Apologies and I hope someone else who's brain still works will jump in here. Please?

---

### Post by dragonfly41 on 2020-02-20
I looked back through my past notes in trying to get my scanner to work (no joy) but [this might relate to your scann]("https://askubuntu.com/questions/814137/canoscan-lide-120-on-ubuntu-16-04-scan-completely-black")[er]("https://askubuntu.com/questions/814137/canoscan-lide-120-on-ubuntu-16-04-scan-completely-black").

You could experiment with [VueScan]("https://www.hamrick.com/vuescan/canon.html#scanner-drivers") (in above thread) but again it does not work for me.

---

### Post by kurt18947 on 2020-02-20
> **dragonfly41 said:**
> I looked back through my past notes in trying to get my scanner to work (no joy) but [this might relate to your scann]("https://askubuntu.com/questions/814137/canoscan-lide-120-on-ubuntu-16-04-scan-completely-black")[er]("https://askubuntu.com/questions/814137/canoscan-lide-120-on-ubuntu-16-04-scan-completely-black").

You could experiment with [VueScan]("https://www.hamrick.com/vuescan/canon.html#scanner-drivers") (in above thread) but again it does not work for me.

VueScan is a good thought which I'd forgotten about. It does require purchase to remove watermarks on the images but at least one can be sure it works with their device prior to purchase. Canon makes Linux printer drivers for some printers available on Canon's Asia web site. I wonder if the same is true of scanner drivers?

---

### Post by sussexlad on 2020-02-21
> **rbmorse said:**
> 
And now, for the life of me, I have simply forgotten to troubleshoot this.  Used to have to do it all the time but today I'm drawing a blank.  Apologies and I hope someone else who's brain still works will jump in here. Please?

That's OK, thanks for the pointers. I'll carry on digging around. In my case, it's not an essential. Cheers.

---

### Post by rbmorse on 2020-02-21
I just received a notification from VueScan that the latest version (9.7.23), released today, contains a fix for the Canon LiDE 120.  If you tried it before and it didn't work you might give it another look. 

[https://www.hamrick.com/vuescan-versions/9.7.23.html](https://www.hamrick.com/vuescan-versions/9.7.23.html)

---

### Post by slickymaster on 2020-02-21
*Thread moved to **Hardware**.*

---

### Post by sussexlad on 2020-02-22
> **dragonfly41 said:**
> You could experiment with [VueScan]("https://www.hamrick.com/vuescan/canon.html#scanner-drivers") (in above thread) but again it does not work for me.

Well I tried Vuescan and it works !  :-)   Thanks for that.

I downloaded the version for the Canon LiDE 120 and installed it directly from the Download folder. It's icon appeared on the home screen. The only thing I had to change was give root ownership to the file in    /home/~/.profile/ibus/bus/

I also changed the USB cable to a shorter one as suggested but I've not proved whether or not this had any effect.

I'm no expert and will have to fiddle with the settings but I have got both a good image of a photo and another of some text. I've now paid for the standard version which does away with the watermark.

Cheers.

---

### Post by rbmorse on 2020-02-22
Good news.  I've used VueScan for years and find it well worth the purchase price.  It's the best front end for scanning I've seen.  Well supported, too.

---

