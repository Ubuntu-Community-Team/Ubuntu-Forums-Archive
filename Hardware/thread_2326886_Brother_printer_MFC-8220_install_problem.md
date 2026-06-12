---
title: "Brother printer MFC-8220 install problem"
date: 2016-06-05
forum: Hardware
---

### Post by gweedoh on 2016-06-05
I downloaded the brother installer tool (linux-brprinter-installer-2.0.0-1)

As root, I have tried:
bash ./linux-brprinter-installer-2.0.0-1 MFC-8220
bash ./linux-brprinter-installer-2.0.0-1 MFC8220
bash ./linux-brprinter-installer-2.0.0-1 8220
bash ./linux-brprinter-installer-2.0.0-1 Brother MFC-8220
bash ./linux-brprinter-installer-2.0.0-1 Brother MFC8220
bash ./linux-brprinter-installer-2.0.0-1 Brother 8220

Every one gave me:
"Driver-packages cannot be found.
 Confirm the model name."

I don't see anything in the code of the installer script identifying various models, so I'm wondering if it's looking for a ppd (or some other file) on my system.

If not, I don't think this tool is made for this printer.  Is there another model that is close enough to the 8220 that would let me print?

---

### Post by $yl9pAR%t on 2016-06-05
Type only:

```
[COLOR=#000000]bash ./linux-brprinter-installer-2.0.0-1[/COLOR]
```

About the model you will be asked later.

---

### Post by gweedoh on 2016-06-05
> **mefisto888 said:**
> Type only:

```
[COLOR=#000000]bash ./linux-brprinter-installer-2.0.0-1[/COLOR]
```

About the model you will be asked later.

No dice.  It asks for the model straightaway and none of the 6 things I listed above work.

---

### Post by $yl9pAR%t on 2016-06-05
OK, try my way:

```
sudo sh linux-brprinter-installer-2.0.0-1
```

Edit:
Sorry, I have just realised you have problem with model name only, not a script.

---

### Post by gweedoh on 2016-06-05
> **mefisto888 said:**
> OK, try my way:

```
sudo sh linux-brprinter-installer-2.0.0-1
```

Edit:
Sorry, I have just realised you have problem with model name only, not a script.

Just for giggles, I tried it your way and got this result:
"sh: 0: Can't open linux-brprinter-installer-2.0.0-1"

Edit: Disregard that.  I wasn't in the right folder that time.  When I went to where the script was i got the same result as before: driver packages cannot be found".

---

### Post by gweedoh on 2016-06-06
I installed the drivers for the MFC-8420 (mine is 8220) and that all seemed to go well until I told it to print a test page.  Nothing happened.  I tried again so now there are two jobs in the print queue and the CUPS admin panel ([http://localhost:631](http://localhost:631)) says "Processing - "Waiting for printer to become available.""

I ran 'sudo tail -f /var/log/syslog' and unplugged the USB cable and reconnected it and this was the output:

```
Jun  5 22:04:44 Ubuntu-01 kernel: [213445.720777] usb 1-3: USB disconnect, device number 5
Jun  5 22:04:44 Ubuntu-01 udev-configure-printer[25738]: remove /devices/pci0000:00/0000:00:12.2/usb1/1-3
Jun  5 22:04:49 Ubuntu-01 colord-sane: io/hpmud/pp.c 627: unable to read device-id ret=-1
Jun  5 22:05:45 Ubuntu-01 kernel: [213506.321450] usb 1-3: new high-speed USB device number 6 using ehci-pci
Jun  5 22:05:45 Ubuntu-01 kernel: [213506.457649] usb 1-3: New USB device found, idVendor=04f9, idProduct=0150
Jun  5 22:05:45 Ubuntu-01 kernel: [213506.457657] usb 1-3: New USB device strings: Mfr=0, Product=0, SerialNumber=3
Jun  5 22:05:45 Ubuntu-01 kernel: [213506.457662] usb 1-3: SerialNumber: 000J6J341923
Jun  5 22:05:45 Ubuntu-01 kernel: [213506.459437] usblp 1-3:1.0: usblp0: USB Bidirectional printer dev 6 if 0 alt 0 proto 2 vid 0x04F9 pid 0x0150
Jun  5 22:05:45 Ubuntu-01 mtp-probe: checking bus 1, device 6: "/sys/devices/pci0000:00/0000:00:12.2/usb1/1-3"
Jun  5 22:05:46 Ubuntu-01 mtp-probe: bus: 1, device: 6 was not an MTP device
Jun  5 22:05:46 Ubuntu-01 systemd[1]: Starting Automatic USB/Bluetooth printer setup (-devices-pci0000:00-0000:00:12.2-usb1-1\x2d3)...
Jun  5 22:05:46 Ubuntu-01 udev-configure-printer[25778]: add /devices/pci0000:00/0000:00:12.2/usb1/1-3
Jun  5 22:05:46 Ubuntu-01 udev-configure-printer[25778]: device devpath is /devices/pci0000:00/0000:00:12.2/usb1/1-3
Jun  5 22:05:46 Ubuntu-01 udev-configure-printer[25778]: MFG:Brother MDL:MFC-8220 SERN:- serial:000J6J341923
Jun  5 22:05:49 Ubuntu-01 kernel: [213510.800668] usblp0: removed
Jun  5 22:05:50 Ubuntu-01 colord-sane: io/hpmud/pp.c 627: unable to read device-id ret=-1
Jun  5 22:05:52 Ubuntu-01 hp[25797]: io/hpmud/pp.c 627: unable to read device-id ret=-1
Jun  5 22:05:52 Ubuntu-01 python3: io/hpmud/pp.c 627: unable to read device-id ret=-1
Jun  5 22:05:54 Ubuntu-01 udev-configure-printer[25778]: no corresponding CUPS device found
Jun  5 22:05:54 Ubuntu-01 systemd[1]: Started Automatic USB/Bluetooth printer setup (-devices-pci0000:00-0000:00:12.2-usb1-1\x2d3).
Jun  5 22:06:00 Ubuntu-01 kernel: [213521.801282] usblp 1-3:1.0: usblp0: USB Bidirectional printer dev 6 if 0 alt 0 proto 2 vid 0x04F9 pid 0x0150
Jun  5 22:06:05 Ubuntu-01 kernel: [213526.807391] usblp0: removed
Jun  5 22:06:16 Ubuntu-01 kernel: [213537.808835] usblp 1-3:1.0: usblp0: USB Bidirectional printer dev 6 if 0 alt 0 proto 2 vid 0x04F9 pid 0x0150
Jun  5 22:06:21 Ubuntu-01 kernel: [213542.817332] usblp0: removed
Jun  5 22:06:32 Ubuntu-01 kernel: [213553.816401] usblp 1-3:1.0: usblp0: USB Bidirectional printer dev 6 if 0 alt 0 proto 2 vid 0x04F9 pid 0x0150
Jun  5 22:06:37 Ubuntu-01 kernel: [213558.826395] usblp0: removed
Jun  5 22:06:48 Ubuntu-01 kernel: [213569.827819] usblp 1-3:1.0: usblp0: USB Bidirectional printer dev 6 if 0 alt 0 proto 2 vid 0x04F9 pid 0x0150
Jun  5 22:06:53 Ubuntu-01 kernel: [213574.832374] usblp0: removed
Jun  5 22:07:04 Ubuntu-01 kernel: [213585.831306] usblp 1-3:1.0: usblp0: USB Bidirectional printer dev 6 if 0 alt 0 proto 2 vid 0x04F9 pid 0x0150
Jun  5 22:07:09 Ubuntu-01 kernel: [213590.837184] usblp0: removed
Jun  5 22:07:20 Ubuntu-01 kernel: [213601.834675] usblp 1-3:1.0: usblp0: USB Bidirectional printer dev 6 if 0 alt 0 proto 2 vid 0x04F9 pid 0x0150
Jun  5 22:07:25 Ubuntu-01 kernel: [213606.844511] usblp0: removed
```

---

### Post by gweedoh on 2016-06-07
bump

---

### Post by him610 on 2016-06-07
Recommend you review and study this tutorial to install Brother MFC machines...
[http://ubuntuforums.org/showthread.php?t=2322192]("http://ubuntuforums.org/showthread.php?t=2322192")

---

### Post by gweedoh on 2016-06-09
> **him610 said:**
> Recommend you review and study this tutorial to install Brother MFC machines...
[http://ubuntuforums.org/showthread.php?t=2322192](http://ubuntuforums.org/showthread.php?t=2322192)

Yep.  If you notice, I'm getting hung up here:
```
Command: bash linux-brprinter-installer-*.*.*-* Brother machine name
Step6. The driver installation will start. Follow the installation screen directions.
``` 

You see, as I said in my first post, it doesn't accept anything that I can think of to put for "Brother machine name" and I never get to Step 6.

---

### Post by hey2 on 2016-06-09
> **gweedoh said:**
> Yep.  If you notice, I'm getting hung up here:
```
Command: bash linux-brprinter-installer-*.*.*-* Brother machine name
Step6. The driver installation will start. Follow the installation screen directions.
``` 

You see, as I said in my first post, it doesn't accept anything that I can think of to put for "Brother machine name" and I never get to Step 6.

Hi.

Have you seen this video? [http://www.youtube.com/watch?v=gT_wTytQzak&t=2m30s](http://www.youtube.com/watch?v=gT_wTytQzak&t=2m30s)

The guy in the video seems to put the model number without capital letters or dashes.

Have you tried it?

---

### Post by gweedoh on 2016-06-11
> **hey2 said:**
> Hi.

Have you seen this video? [http://www.youtube.com/watch?v=gT_wTytQzak&t=2m30s](http://www.youtube.com/watch?v=gT_wTytQzak&t=2m30s)

The guy in the video seems to put the model number without capital letters or dashes.

Have you tried it?

```
dave@Ubuntu-01:~/Desktop$ sudo bash linux-brprinter-installer-2.0.0-1 mfc8220
Driver-packages cannot be found.
 Confirm the model name.


```
Incidentally, I tried a different model (MFC8420) and managed to get the installer script to complete.  The problem is jobs I send to the "8420" timeout and because I'm not using the correct drivers, I don't know if it's a driver problem or something else.  There were a couple things in my [syslog tail]("http://ubuntuforums.org/showthread.php?t=2326886&p=13499883#post13499883") that seemed like they might be a problem and I was hoping someone could confirm that and give me a fix.

---

### Post by kurt18947 on 2016-06-11
Hmmm, curious indeed. I looked here:

[http://support.brother.com/g/s/id/linux/en/download_prn.html](http://support.brother.com/g/s/id/linux/en/download_prn.html)

I found only a .ppd file, no .deb files so the installer script would not work. There are directions on how to install the .ppd file. 

[http://support.brother.com/g/s/id/linux/en/instruction_prn1c.html?c=us_ot&lang=en&comple=on&redirect=on](http://support.brother.com/g/s/id/linux/en/instruction_prn1c.html?c=us_ot&lang=en&comple=on&redirect=on)

I haven't worried about the "pre-required procedures" in some years but then I've never done a .ppd file install. Those "pre-required procedures" also talk about Ubuntu 8.04 and Fedora  10 so I'm not sure if they're still required, I sorta doubt it.

Edit:  If all else fails, that machine seems to understand PCL6 so perhaps you could install as some sort of (older?) generic HP laser for printing.

                                 Main Features                             
                             
[LIST]
[*]Fast printing and copying. Offers print and copy speeds of up to 21 pages per minute.
[*]Superior quality laser output. With up to 2400 x 600 dpi print resolution, you can produce professional documents.
[*]30-page capacity auto document feeder&#8225;. A quick and easy way to copy, fax or scan multi-page documents.
[*]Large, expandable paper capacity.  Features a 250-sheet paper tray adjustable for letter or legal size  paper. You can also install an optional 2nd 250-sheet paper tray&#8225; to  increase your total paper capacity to 500 sheets.
[*] **PCL6 and BR-Script 3 emulations&#8225;**. It can handle all of your printing, including documents with a variety of fonts and graphics.
[/LIST]

---

### Post by him610 on 2016-06-11
Yes, I can see how you might be frustrated. I went to the Brother support site, using your MFC-8220 model, downloaded linux-brprinter-installer-2.0.0-1.gz, gunzipped the file, assumed su, executed the file using bash, entered [MFC-8220 | mfc-8220 | MFC8220 | mfc8220] all without success. I got the same error that you did.

Evidently there is a problem within the script of linux-brprinter-installer-2.0.0-1

My suggestion is to contact Brother support and detail your unsuccessful struggles.

Another method you might try is to download the individual *.deb driver files from the brother support page then install them locally. I used this method successfully the first couple of times for my MFC-7360n.

Good luck.

---

### Post by rbbwana on 2016-06-20
I just installed brother MFC7420 --don't use the MFCxyzz ensure you are running terminal from the Download folder and then try this
bash linux-brprinter-installer-2.0.0-1---if it likes you, it will ask for the model number.

I must have done something wrong the first time---but installed correctly ---(for printing) on the second try.

---

### Post by kurt18947 on 2016-06-20
> **rbbwana said:**
> I just installed brother MFC7420 --don't use the MFCxyzz ensure you are running terminal from the Download folder and then try this
bash linux-brprinter-installer-2.0.0-1---if it likes you, it will ask for the model number.

I must have done something wrong the first time---but installed correctly ---(for printing) on the second try.

Either way works. For the script to work Brother has to have .deb files available for each model. The thread originator had the rare Brother model that didn't appear to have .deb file drivers available, just a .ppd file. The installer script won't work with just a .ppd file. There were directions on how to install the .ppd file.

---

