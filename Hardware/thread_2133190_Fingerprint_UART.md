---
title: "Fingerprint UART"
date: 2013-04-07
forum: Hardware
---

### Post by axmarvin on 2013-04-07
Hello guys, i'm new here. i have a fingerprint UART reader and i wanna communicate with it through serial port. 

To set the serial port configuration i used this command:

stty -F /dev/ttyUSB0 cs8 -cstopb -ixon raw speed 19200

To send command to the device:

perl -e'print "\xF5\x01\x00\x01\x03\x00\x03\xF5"'>/dev/ttyUSB0

To retrieve the data from the device and put it into .txt file:

cat </dev/ttyUSB0 > output.txt

problem: i got the incorrect format for the output which is this =>>   . i've attahced the photo along with this thread[ATTACH=CONFIG]241061[/ATTACH] ( the output in the image quite blur, is actually /F5/'box'/00/00/00/00/'box'/F5)

p/s: its HEX input and output. whenever i get 01,02.03 or other than 00,then it will appear as boxes. please help me experts!

---

