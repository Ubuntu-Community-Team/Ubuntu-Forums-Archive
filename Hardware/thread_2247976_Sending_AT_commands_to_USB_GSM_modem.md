---
title: "Sending AT commands to USB GSM modem"
date: 2014-10-11
forum: Hardware
---

### Post by soxterix on 2014-10-11
I want to write a c++ code to send AT commands to USB GSM modem. Before that I tried to send some commands via terminal so I displayed /dev/ content and I have ttyUSB0, ttyUSB1, ttyUSB2 created after I plugged modem. I executed commands (one for one terminal window):
cat /dev/ttyUSB0
cat /dev/ttyUSB1
cat /dev/ttyUSB2
and tried to send AT commant to USB0:
echo 'AT+CUSD=1,"AA182C3602",15^M' > /dev/ttyUSB0
and I got "OK" answer in USB0 terminal and answer I wanted to get in USB2 terminal.
But now I want to write it in c++ and I need to know which /dev/ttyUSB I should write to and which should be the one I can read from. Is there a way to check this?

---

