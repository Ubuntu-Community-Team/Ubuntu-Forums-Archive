---
title: "Issues with the serial ports of my PC/104"
date: 2010-12-13
forum: Hardware
---

### Post by Jack_Rabbit on 2010-12-13
Hey All,

I have been struggling with this issue with my PCM-9588 PC/104 where I'm not able to use all of its serial ports using Ubuntu.  The PC 104 has six serial ports that I would like to be able to access so I can interface the sensors of the ground vehicle I am building.

I am only able to get readings from ttyS2 but none of the others. I realize that Ubuntu only initializes ttyS0-3 but I know how to set up 4 and 5.    The tty0, 1 and 3 all give 0's for an output at about 1 b/s.  Some other people had this issue but they were able to solve it by verifying their port address' and IRQ's between the bios and setserial.  I did this and unfortunately found that everything was set up correctly.

I'm fairly certain my baud rates are set up correctly and I am addressing the com ports right.  The PC 104 was built as a Windows embedded board but I am running Ubuntu 10.04 from a flash drive.  I did the OS installation on the PC104.  The fact that I'm getting one of the ports to work tells me that this isn't causing the problem.  

If anyone has any insight into this I would appreciate some guidance.  I'm hoping that the solution is something that can be changed in the software and not the hardware

Regards,
Tyler

---

