---
title: "Getting Canon Pixma 2920 to Scan"
date: 2015-01-06
forum: Hardware
---

### Post by lizardboy862 on 2015-01-06
I am wondering if someone can walk me through the steps on how to get the printer to scan using other drivers. I am unsure how to scan with this printer because its not being recognized right now through the scan tool in ubuntu. I do not know how to even try and install CanonScanGear to even make the printer work. If someone can walk me through this I would appreciate it.

---

### Post by weatherman2 on 2015-01-06
Try downloading Scangearmp from Canon:

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100627102.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100627102.html)

You may need to install this in a terminal.  Extract the downloaded archive (a set of Debian packages), then in the terminal find the install.sh installer script.  In the terminal, run it this way:

```
sudo sh ./install.sh
```

Then to run it, type in a terminal:

```
scangearmp
```

If it works, you may be able to setup a launcher so you don't have to enter a terminal each time to start it.

---

### Post by lizardboy862 on 2015-01-07
Still does not recongize the scanner. Its just weird because the printer that is the model less 2520 worked with the initial drivers with ubuntu but the model I have no the only difference is that it has wireless for tablets and other items. Both printers just looked exactly the same and I couldn't imagine that the firmware would be that much different.

---

### Post by pdc on 2015-01-08
Hi lizardboy:

1) is your MG2900series printing wirelessly? If so, we can feel the printer is able to communicate with your router;

2) next step is: please copy this command;   ```
dpkg -l | grep scangear
```      then please paste it into a terminal; then please copy the result and paste it back here .......

________________

having followed weatherman2's instructions: what did you do to get [COLOR="#0000FF"]ScanGearMP[/COLOR] to run for you please?

---

### Post by lizardboy862 on 2015-01-13
ii  scangearmp-common                                           2.00-1                                                 amd64        ScanGear MP for Linux.
ii  scangearmp-mg2100series                                     1.80-1                                                 amd64        ScanGear MP for Linux.
ii  scangearmp-mg4200series                                     2.00-1                                                 amd64        ScanGear MP for Linux.
ii  scangearmp2                                                 3.00-1                                                 amd64        ScanGear MP for Linux.


I try runing ScanGear to run in terminal but using scangearmp but I cannot get it to recongize.

I have the printer being recongized if I use my laptop which is running mint. My main computer which is connected by usb is running ubuntu so no big difference. But I am able to print using my usb cable so the computers do recongize the printer.

---

### Post by pdc on 2015-01-14
Dohhhhhhhhhhhhhhhhhhhhhhhhhhhhh

My apologies; I missed this

...... have a look at the file you downloaded [SIZE=4]scangearmp[COLOR="#FF0000"]2[/COLOR]-3.00-1-deb.tar.gz[/SIZE]

Canon have released an updated ScanGearMP so the command in a terminal should be

```
scangearmp2
```

_____________

If that goes well, one can install a launcher ........ if you want a how-to, please ask

---

### Post by lizardboy862 on 2015-01-14
I works now thanks. I don't know how to create a unity launcher. I tried going through creating a .desktop entry

under /usr/share/applications

[Desktop Entry] 
Name=Canon Scanner
Comment=To Scan Documents
Exec=/usr/bin/scangearmp2
Icon=/usr/share/icons/Canon.png
Terminal=false
type=Application
Categories=Utility

I just want to create a unity launcher. Thanks for your help btw.

---

### Post by pdc on 2015-01-14
for a launcher I find

```
sudo apt-get install gnome-panel
```

and then 

```
gnome-desktop-item-edit ~/Desktop/ --create-new
```

then enter as in launcher in the thumbnail

the command must be ```
scangearmp2
```

---

### Post by lizardboy862 on 2015-01-14
Thats what I did but before but I would like to add an icon to unity. I tried following someone on youtube but still did not work out. No biggie. that will do. Thanks for your help.

---

### Post by pdc on 2015-01-15
you followed this?

[https://www.youtube.com/watch?v=GSU9YuE_36w](https://www.youtube.com/watch?v=GSU9YuE_36w)

---

