---
title: "Fujitsu Scansnap ix500 setup"
date: 2014-12-13
forum: Hardware
---

### Post by linuxthunder on 2014-12-13
Greetings,

I need help setting up this scanner on ubuntu 14.04 64-bit.  I checked the sane-project.org site and it is supported but I'm new at this and need help from start to finish.  

The only thing I've done so far is lsusb in the terminal and it shows up as:  Bus 003 Device 003: ID 04c5:132b Fujitsu, Ltd 

Thank you for your help and let me know if you need more information.

---

### Post by Michael_Schievelbein on 2015-06-22
Did you ever get any support with your ix500?
I just got one and also need some help.

---

### Post by ben147 on 2015-12-12
Hi, I worked with the ix500 until today. I installed the software on my macbook and then connected the scanner to my Lubuntu PC. Last week I deleted the software from my macbook because it constantly wanted to update stuff but couldnt finish it. Today I recognised that - because of that - the scanner does not work any more with Linux. Have not been able to fix it, yet. Awesome scanner, though.

---

### Post by fermin on 2016-01-26
Did any of you have any luck? I'm trying to setup a Fujitsu ScanSnap S1500M on Ubutu 14.04 LTS to no avail. It's supposed to be completely supported by the SANE project drivers:

[http://www.sane-project.org/sane-backends-1.0.23.html#S-FUJITSU](http://www.sane-project.org/sane-backends-1.0.23.html#S-FUJITSU)

with the version currently distributed with the Ubuntu repositories [v1.0.23]("http://www.sane-project.org/sane-backends-1.0.23.html#S-FUJITSU"), but it just doesn't work at all through Xsane, Easyscan, gscan2pdf or sane terminal commands like "scanimage -L", they all report not being able to find the scanner or an I/O error when it intermittently is recognized. I know it is recognized by the USB system because dmesg reports

```
[12343.432592] usb 3-1: new high-speed USB device number 15 using xhci_hcd
[12343.470668] usb 3-1: New USB device found, idVendor=04c5, idProduct=11a2
[12343.470690] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[12343.470692] usb 3-1: Product: ScanSnap S1500
[12343.470694] usb 3-1: Manufacturer: Fujitsu 
```

lsusb in the terminal also reports the scanner is recognized:

```
franco@ensenada:/etc/sane.d$ lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 8087:07da Intel Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 012: ID 04f2:1026 Chicony Electronics Co., Ltd 
Bus 003 Device 017: ID 04c5:11a2 Fujitsu, Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

So it seems to be recognized by linux but somehow not working with the sane drivers as it is supposed to. Trying to solve the problem I tried sane-find-scanner and it says there is no USB device!

```
franco@ensenada:/etc/sane.d$ sudo sane-find-scanner 
[sudo] password for franco: 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
```

The sane-fujitsu backend is active in the fujitsu.conf file in /etc/sane.d/ and the brand and model of this scanner even appears on this list as

```

#S1500 & S1500M
usb 0x04c5 0x11a2
```

In the Easyscan interface it shows up in the scanner selection dropdown list but it says it can't connect when I try to scan. So everything seems to be configured right and it seems like the sane drivers are not doing their job somehow. I know the scanner works because I can scan with it using the proprietary VueScan in the same machine, even in the Ubuntu! Any ideas?

---

### Post by fermin on 2016-01-26
I solved the problem following the instructions in

[https://www.gaggl.com/2013/08/paperless-office-on-a-budget/comment-page-1/#comment-51572](https://www.gaggl.com/2013/08/paperless-office-on-a-budget/comment-page-1/#comment-51572)

It worked like a charm on Ubuntu 14.04 LTS, thanks a lot! I had been looking for a solution for some time!

Two things though:

1) The same "scanbuttond" package file  (scanbuttond_0.2.3.cvs20090713-14_i386.deb) is available now in the  repositories, probably after installing the cited  ppa:rolfbensch/sane-git, so there's no need to download it from the  pkgs.com website, just type "sudo apt-get install scanbuttond".

2) The actual button on the scanner does nothing when pressed so I'm not  sure what the purpose of the "scanbuttond" software actually is, so  probably it is not needed anyway if you don't mind missing this  functionality. If the purpose of the software is just to have this  physical button work then it doesn't though, at least in my case. I  scanned through Easyscan, Xsane and gscan2pdf and all worked perfectly.

I would recommend doing the "Scanner config" and  "Permissions" sections in the reference article and checking if it  works, if it doesn't then go to "Install dependencies" through the PPA  and check again. At last I would install the scanbuttond and configure  it.

By the way I got it running in a Panasonic Let&#8217;s note laptop and  there where no usb port power saving issues here. I hope it helps. Good  luck!

---

### Post by linuxthunder on 2016-04-04
I was able to fix the problem simply by adding the rolfsbench ppa: 
ppa:rolfbencsh/sane-git and then did a ```
sudo apt-get update && sudo apt-get upgrade
``` and it just worked in Ubuntu 14.04

My issue is now with Ubuntu 16.04 64-bit.  This ppa does not work in 16.04 so I'm at a loss for configuration.

```
lsusb
``` shows the scanner and ```
scanimage -L
``` shows:

device `fujitsu:ScanSnap iX500:168008' is a FUJITSU ScanSnap iX500 scanner


That's where I'm stuck right now.

thanks

[COLOR=#373737][FONT=Monaco]
[/FONT][/COLOR]

---

### Post by linuxthunder on 2016-04-15
Ok, I was able to get it working in Ubuntu 16.04 since the Rolf Bensch PPA has been updated.

Just add this PPA:  [https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git](https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git)

Then apt-get update && apt-get upgrade and the scanner should work fine.  I use simplescan.

If a dependency issue shows up in the terminal just type:

apt-get -f install

This will take care of any sane dependency issues.

---

### Post by thomas-zink on 2016-06-15
> **linuxthunder said:**
> Ok, I was able to get it working in Ubuntu 16.04 since the Rolf Bensch PPA has been updated.

Just add this PPA:  [https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git](https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git)

Then apt-get update && apt-get upgrade and the scanner should work fine.

Could you please elaborate on that. It doesn't work for me. Trying to update / upgrade from this PPA always fails with the same error:

```

W: The repository 'https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
E: Failed to fetch https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git/dists/xenial/main/binary-amd64/Packages  404  Not Found

```

The same happens even if I add --allow-unauthenticated to apt-get.

---

