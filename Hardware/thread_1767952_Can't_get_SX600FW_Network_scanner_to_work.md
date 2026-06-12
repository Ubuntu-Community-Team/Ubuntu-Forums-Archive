---
title: "Can't get SX600FW Network scanner to work"
date: 2011-05-26
forum: Hardware
---

### Post by waqasahmed on 2011-05-26
Hi all,

A bit of background info: My names Waqas, I like tinkering with hardware and networks, on a few other forums where I help others and I've been looking in to Ubuntu for the past 6 months or so

I've been wanting to switch to Ubuntu, so I played with it in a virtual machine. I've managed to get my network printer to print however I can not get it to scan over the network. I've googled this again, and again. I eventually found something which I thought may help me which was here:
[http://ubuntuforums.org/showthread.php?t=1089972&page=2](http://ubuntuforums.org/showthread.php?t=1089972&page=2)

However unfortunately the files in the said tutorial no longer exist. I've had a look through other forums, rephreased my search words etc... but still no avail :(

Just wondering if any one can help me get my Epson SX600FW (WiFi) scanner working in Ubuntu? :confused:

Thanks in advance for your help

---

### Post by IcarusR on 2011-05-26
Download iscan from [www.avasys.jp]("http://avasys.jp/eng/linux_driver/download/") select printer catogry, then scroll down & select your model & download all the iscan.deb files & install them.

---

### Post by waqasahmed on 2011-05-26
I did that, but I still get Ubuntu telling me that it can't send a command to the printer. I edited the IP to 192.168.2.5 to match that of my SX600FW. The scanner is switch on, and working within Windows so it's not an issue of simply flicking the switch. I also rebooted the VM, but that didn't do much for me.

EDIT:I've had a look at the drivers again, and there seems to be a network backend for the SX515 but not the SX600FW? , even though people have succeeded with using an SX600FW as a scanner on the network?

---

### Post by demonipuch on 2011-05-27
Hi

Open a terminal and run this command 
```
echo "net 192.168.2.5 1865" | sudo tee -a /etc/sane.d/epkowa.conf
```Restart saned server :
```
sudo /etc/init.d/saned restart
```You should be able to use your scanner over the network now.

---

### Post by waqasahmed on 2011-05-27
Thanks for trying to help, but I used both those lines of code within Ubuntu, then restarted the whole machine just for good measure. I then thought I was getting some success, as I heard the scanner(as before), but this time it gave me a popup which showed my actual printer. Shortly after, I was told that the command could not be sent, so I'm back to square 1

---

### Post by demonipuch on 2011-05-27
Please return the output of this command :
```
cat /etc/sane.d/dll.conf | grep epkowa
```

---

### Post by waqasahmed on 2011-05-27
Hi,

I did that, but it just shows nothing on the next line, so does that then mean that I have some missing files?

Thanks for your help

---

### Post by demonipuch on 2011-05-27
Try :
```
echo epkowa | sudo tee -a /etc/sane.d/dll.conf
```Restart saned server
```
 sudo /etc/init.d/saned restart
```See if your network scanner is detected :
```
 scanimage -L
```

---

### Post by waqasahmed on 2011-05-28
> **demonipuch said:**
> Try :
```
 scanimage -L
```

Thanks for your help, but I did that(and the above), and I got something that said
"device `epkowa:net:192.168.2.5' is a Epson Stylus BX600FW/SX600FW/TX600FW/ME Office 700FW/WorkForce 600 flatbed scanner
device `epkowa:net:192.168.2.5:1865' is a Epson Stylus BX600FW/SX600FW/TX600FW/ME Office 700FW/WorkForce 600 flatbed scanner"

So my scanner is quite obviously being detected. After doing the above commands, I still get told that the command could not be sent to the scanner and to check it's status

I am also able to ping the device through the terminal as well

---

### Post by waqasahmed on 2011-05-30
> **demonipuch said:**
> Please return the output of this command :
```
cat /etc/sane.d/dll.conf | grep epkowa
```

I've now got Ubuntu 11.04 as my real OS now. I used that command again, and the system simply outputted ```
epkowa
```

I'll also be a bit more careful with compiz now, as I broke unity earlier and had to reinstall gnome lol. Got me slightly scared

---

### Post by waqasahmed on 2011-06-24
Hey a bit of an update. Simple scan seems to work fine with KDE, so I've no idea why it wasn't working with Gnome. Maybe people could use that as a workaround, if needs be(provided that your computer is not too old)

---

