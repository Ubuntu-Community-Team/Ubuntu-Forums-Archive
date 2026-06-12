---
title: "Acer 620U Scanner"
date: 2009-12-02
forum: Hardware
---

### Post by blackduck on 2009-12-02
[U]Partially solved.
[/U]
a) [https://wiki.ubuntu.com/HardwareSupportComponentsScannersAcerBenq](https://wiki.ubuntu.com/HardwareSupportComponentsScannersAcerBenq)
b) [http://ubuntuforums.org/archive/index.php/t-317685.html](http://ubuntuforums.org/archive/index.php/t-317685.html)

dbmk (ref b) wrote the below protocol to activate Acer 620U scanner. I followed the procedure, using U96V057.BIN/u96vo57.bin from the install cd, & successfully activated my 620U on a laptop running 9.10 but when I tried the same steps on another laptop using 8.04 the XSANE splash screen appeared offering a choice of: 

Acer FlatbedScanner13 [snapscan;libusb:006:005] Or
Acer crystal eye virtual device; [v4l:/dev/video0]

Selecting either one produced an error msg. The scanner error msg was: Failed to open device 'snapscan:libusb:006:005';Invalid argument. 
I need help here.
------------
dbmk wrote:
download the windows driver zip file mirascanv403u10_bqa.zip
and in a terminal

expand the zip file
"unzip mirascanv403u10_bqa.zip"

change directory to the firmware directory
"cd MiraScan\ v4.03u10_BQA/BIN/"

as root user (sudo) make directory to put firmware in
"sudo mkdir /usr/share/sane/snapscan"

as root user (sudo) copy firmware file to that directory
"sudo cp u96v121.bin /usr/share/sane/snapscan/"

as root user (sudo) use gedit program to edit snapscan.conf file
"sudo gedit /etc/sane.d/snapscan.conf"
and change firmware line to location of file
firmware /usr/share/sane/snapscan/u96v121.bin

---

