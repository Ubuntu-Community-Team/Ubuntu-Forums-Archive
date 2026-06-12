---
title: "USB accelerometer driver fails with /dev/ttyACM0, not with ACM1"
date: 2013-06-12
forum: Hardware
---

### Post by Calamariman on 2013-06-12
[TABLE]
[TR]
[TD="class: votecell"][/TD]
[TD="class: postcell"]               I'm using a YEI brand TSS-USB-S v2 IMU (a nice robotics  motion sensor) on Ubuntu 12.04 64-bit.  When I plug it in (USB device),  it defaults to /dev/ttyACM0 (since no other devices are attached).   However, the driver I am using to handle position data seems to timeout  too quickly:

  ```

Calibrating gyros...  
timeout: (read 2 bytes) 
time: 1345863791.5342643 s, rate: 0.000000 Hz, temperature: 0.000000 C 
timeout: (read 14 bytes) 
```  etc...


  The "time" line suggests it received an incomplete packet, and these  lines repeat about as frequently as I would expect for the device to  send new messages.  In between are dozens of the "timeout" messages.


  All this is fixed if I plug in something else for ACM0 and then the IMU gets /dev/ttyACM1.  It works as expected with a pleasant
  ```

time: 1345863791.5342643 s, rate: 61.030677 Hz, temperature: 36.000000 C 
```  every couple seconds.  I used 
  ```

sudo fuser /dev/ttyACM0 
```  as suggested elsewhere to see if anything else was using ttyACM0, but no processes showed up.
  Is something interfering with my driver, or could the driver itself be at fault?
  I don't have access to it's code, so if the driver is the problem, is  there a way I can make devices default to ACM1 and higher?  I tried  symlinking the device to /dev/yeisensor, but had the same issues; the  device couldn't be on ACM0 (so I guess the problem is deeper than just  the name).[/TD]
[/TR]
[/TABLE]

---

