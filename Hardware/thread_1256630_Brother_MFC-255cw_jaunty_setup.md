---
title: "Brother MFC-255cw jaunty setup"
date: 2009-09-02
forum: Hardware
---

### Post by bijanafx on 2009-09-02
How I setup my Brother MFC-255cw printer/scanner in Jaunty. I could not find these instructions elsewhere, so maybe this will help someone.

PRINTING/
Download the latest driver from: [http://solutions.brother.com/linux/en_us/](http://solutions.brother.com/linux/en_us/)
direct link: [http://solutions.brother.com/linux/en_us/download_prn.html#MFC-255CW](http://solutions.brother.com/linux/en_us/download_prn.html#MFC-255CW)

You will need both the LPR & cupswrapper drivers. Install the LPR driver first.

Note that since only the 32-bit driver is available, use the --force-architecture option for 64-bit systems.

```
sudo dpkg -i --force-architecture pkg.deb
```


SCANNING/
Download latest driver from: [http://solutions.brother.com/linux/en_us/download_scn.html](http://solutions.brother.com/linux/en_us/download_scn.html)

Turn off the scanner, and install sane, xsane, libsane, libsane-extras and sane-utils.

```
sudo aptitude install sane xsane libsane libsane-extras sane-utils
```

You need the brscan3 driver and scan-key-tool (at the bottom of the page of the link above).

Note that the MFC-255cw is not listed as supported with brscan3. You will use the MFC-250c settings instead. I have not had any problems using them so far.

Install the brscan3 driver and scan-key-tool debs.

Turn the scanner back on, and configure brsane (mine was connected to my wireless router):
```
brsaneconfig3  -a  name=(name  your  device)  model=(model  name)  ip=xx.xx.xx.xx
```
```
brsaneconfig3  -a  name=MFC-255cw  model=MFC-250C  ip=192.168.1.124
```

Also (I am not sure if this is necessary), you may need to set user permissions for the device:

```
sudo gedit /lib/udev/rules.d/50-udev-default.rules
```

And change the following line:

```
# libusb device nodes
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", NAME="bus/usb/$env{BUSNUM}/$env{DEVNUM}", MODE="0664"
```

to:

```
# libusb device nodes
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", NAME="bus/usb/$env{BUSNUM}/$env{DEVNUM}", MODE="0666"
```

---

### Post by dethmeggle on 2009-09-08
Just so you know, you're awesome. Thanks for putting these up. You've helped me out a lot.

I do have one question, tho. The scanner won't connect to the PC. Do you know off the top of your head what I might be able to do to fix that? I'm running 8.04, but that didn't seem to make a difference with regard to the rest of the setup.

Thanks again. You rock out loud.

---

### Post by bijanafx on 2009-09-09
What do you mean by that? The scanner won't connect? So, the printer will "connect," but the scanner will not? Are you connected with a USB cable or your through a router? I am not sure I can help you, but some specifics might help.

---

### Post by dethmeggle on 2009-09-10
I'm connected via USB cable. When I attempt to scan something, the readout on the scanner/printer says "Connecting to PC" for about two or three minutes before it gives up and goes into sleep mode. The printer works fine and receives info from the computer easily, but I can't scan in information.

---

### Post by bijanafx on 2009-09-10
When scanning in a document, all I have to do is open XSane from Applications > Graphics > XSane. It detects the scanner automagically. It sounds like you are pressing the scan button on the printer itself. That shouldn't be necessary. Sorry I left that out of the original post. Hope that helps.

---

### Post by dethmeggle on 2009-09-11
XSane just brings up a small box that says "scanning for devices," then tells me it's an invalid argument. So I think I did something wrong, lol. Is the IP connection necessary when it comes to scanning, or shouldn't the USB be enough?

Sorry I'm such a n00b.

---

### Post by bijanafx on 2009-09-11
Based on that, I think your trouble is with getting sane configured with the scanner. In my original post, the brsaneconfig3 command is what accomplishes that. Do you see how that command specifies an IP address for the scanner (where it says IP=xx.xx.xx.xx)? That is necessary because my scanner is connected to my router. Unfortunately, I couldn't find the syntax to configure it connected via USB (there is not a man page for brsaneconfig3). You might be able to search around for that. Again, you are looking for the parameters for "brsaneconfig3" to configure it for a USB connection. Alternatively, you could try the exact same command without the "IP=" specification. It might work, but it might not, either.
```
brsaneconfig3  -a  name=MFC-255cw  model=MFC-250C
```
Of course, another solution would be to connect it to a router and specify the IP address per the instructions in the original post.
I hope that makes sense. Also, check the links below, and follow the instructions for setting up via USB, if you haven't already...
[http://solutions.brother.com/linux/en_us/instruction_scn1.html](http://solutions.brother.com/linux/en_us/instruction_scn1.html)
[http://solutions.brother.com/linux/en_us/instruction_scn3.html](http://solutions.brother.com/linux/en_us/instruction_scn3.html)

---

### Post by dethmeggle on 2009-09-16
Cool, thanks! I'll give that a shot. Seriously appreciate your time on this. ^.^

---

### Post by Simon741 on 2009-11-22
I managed without too much difficulty to install the printer (a MFC-6490CW). However, I'm stuck with the scanner. First of all, I don't really know how to find the IP address? I've tried with 192.168.1.1, but that doesn't work, and now I can't even manage to change that.

---

### Post by snowsquirrel on 2010-08-24
Is it possible to scan from the MFC's control panel, and just have a file show up on the linux box? Or do you have to scan from desktop?

~S

---

### Post by dylaneddies on 2011-09-11
Hey there, is it possible to scan using wireless? because a USB Cable did not come with my printer.
thanks in advance.

---

### Post by jsavga on 2012-01-28
> **bijanafx said:**
> 
```
brsaneconfig3  -a  name=(name  your  device)  model=(model  name)  ip=xx.xx.xx.xx
``````
brsaneconfig3  -a  name=MFC-255cw  model=MFC-250C  ip=192.168.1.124
```Also (I am not sure if this is necessary), you may need to set user permissions for the device:
The MFC -255CW is supported by brsane3 now so your above would be:
```
brsaneconfig3  -a  name=MFC-255cw  model=MFC-255CW  ip=x.x.x.x
```

---

### Post by brokenhorse on 2012-05-04
OK I have tried everything. I'M trying to get my mfc-9320cw to work. the printer would sporadically work and would keep print pages with nothing on it. so I did would brother says [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html)
on the pre-required procedures then installed the drivers multiply time with different ways to do it then I get to yours and did what you said i enter the name=MFC-9320cw and it say invalid model name. 
Im new at Ubuntu 12.4. I'm willing to learn.
also it shows my printer the problem is Im trying to connect it at a network printer ( I don't want to print from the web or leave any ports open) 
if I hit find print in device uri then network printer i get no printer was found.
before I did all this at least I could print now I cant even do that please help help help

---

### Post by brokenhorse on 2012-05-04
ok I did the brsaneconfig3 and -q pinged it it after entering what jsavga post it showed the printer/ scaner but it still doesn't show it in network printer. SO I deleted that printer and tryed to add another one and got  There was an error during the CUPS operation: 'client-error-not-possible'.
so anyone have a simple why to install my network printer I really need help don't know why its not seeing it i have firestarter turned off so I don't think its a firewall. not sure how to open any ports for that printer
im using ubuntu 12.4 64

---

