---
title: "Ubuntu FTDI connection with arduino Pro Mini"
date: 2018-05-04
forum: Hardware
---

### Post by zeedo65 on 2018-05-04
Hi

I am trying to connect my arduino pro mini using a FTDI USB to serial board. My Ubuntu is 18.04. The port is not detected on Arduino IDE and when I try to upload the code to the board, it says:

Arduino IDE: [COLOR=#ff8c00]avrdude: ser_open(): can't open device "/dev/ttyUSB0": No such file or directory An error occurred while uploading the sketch

[/COLOR]Then, I tried this command which I read in the ubuntu forum
[HTML]ls -l /dev/ttyUSB0[/HTML] 
and 
[HTML]ls -l /dev/ttyUSB*[/HTML] 

The result is:
[HTML]ls: cannot access '/dev/ttyUSB8': No such file or directory[/HTML]

I got very tired of dealing with this problem. I managed to solve this problem on 17.10 but I can not find the solution this time. Can you please help if you have any idea what might be the problem?


Thanks

---

### Post by ilpiero on 2018-05-07
May it be that you are just not allowed to access the serial port?

Have a look here:

[https://askubuntu.com/questions/112568/how-do-i-allow-a-non-default-user-to-use-serial-device-ttyusb0]("https://askubuntu.com/questions/112568/how-do-i-allow-a-non-default-user-to-use-serial-device-ttyusb0")

Marco

---

### Post by ismaelteodoro on 2018-05-07
on ubuntu 18.04 udev rules should be add and verify ~#udevadm monitor and ~#ls -la /dev/bus/usb/xxx/ (permission check)

---

### Post by zeedo65 on 2018-05-08
Hi ilpiero

Thanks for your answer, unfortunately non of the things mentioned there worked for me. It is very strange, but that is how it is. :) Probably something wrong with my Ubuntu that I do not understand. As it says, there is no ttyUSB0 file made in my /dev/folder. I tried to become a member of dialout group and I also run most other suggestions in that thread. But, it is not working. The main reason is that this ttyUSB0 is not made at all. Other people said that if I run Arduino IDE as a super user with sudo command this issue will be solved, but, it also did not change the story. So, I think I will skip the idea of connecting to my arduino using this laptop I have. Thanks for your assisstance. In the case you came up with another idea, I will be very grateful to see.

BR

Zeedo

---

### Post by zeedo65 on 2018-05-08
Hi Ismaelteodoro

this was something I never came up with during these days that I am looking for. Could you please explain more with possibly the commands I should put in the terminal?

BR

Zeedo

---

