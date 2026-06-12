---
title: "connect sensor to rs232 serial port under ubuntu and/or dosbox"
date: 2015-06-08
forum: Hardware
---

### Post by dieter-erich on 2015-06-08
Hi,
     aiming at changing from WindowsXP to ubuntu I am trying to get a (and later several) temperature/humidity sensor to work: Under XP there is a little DOS program that reads the data from the serial port and displays the values (I am having 4 instances of this running in parallel right now). According to the sensor description (note this is an old sensor and the manufacturer does not exist any more) the output is a continuous ASCII string cotaining channel, type of sensor, serial number, and the two values:

 @<CR> 
I01010100B00725030178<CR>
V010892A1<CR>
etc. with the settings 4800 BAUD, 8 data bits, no parity, and one stop bit.
 
To test this I installed the DOS-program in question under DOSBOX and I definitely get some values but these are completely wrong (and e.g. humidity is not shown). 
Neither do I get anything with "cat /dev/ttyS0" or minicom (note that the sensor is connecto to ttyS0 and DOSBOX sets it to COM1:, which I am addressing by the program (like under WinXP). 
Can anybody please advice me of how to test whether any signal comes in and if not to find out why! 
Tnks, D-E

---

