---
title: "Problem installing USR 5610B Modem (Real Hardware Modem, not Winmodem)"
date: 2005-08-20
forum: Hardware &amp; Laptops
---

### Post by darkstar5680 on 2005-08-20
Please bear with me, as I am new to linux, but pretty experienced with computers in general.

The facts:
-I just purchased a US Robotics 5610B PCI modem.  

-This is a full Hardware 56K modem, not a winmodem and should have full suppoprt for linux distros.

-My system is set up as a dual boot, WinXP/ Ubuntu 5.04.

-The modem already works in WinXP, in fact that's how i'm posting here.

-In WinXP, the modem appears on COM3, with an IRQ=11.  This leads me to believe that the modem should be found at /dev/ttyS2.

-PPPconfig doesn't autodetect the modem.

-The output of **sudo lspci** is:
0000:00:09.0 Serial controller: 5610 56K FaxModem 56K FaxModem Model 5610 (rev 0 1)

-I have downloaded and installed minicom.  When I run minicom, I have tried multiple times point it to the different possible modem locations: /dev/ttyS0, /dev/ttyS1, /dev/ttyS2, and /dev/ttyS3 

-With the modem location set to each of those possible serial locations, I have tried to initialize the modem in minicom with the AT command, however I get no response.

-I have also tried to set up the modem from the Networking application in gnome, with no success.

Please help me get a response from my modem, so I know it's working.  I will worry about setting up my PPP connection after that.  For now, I just want to know that the modem works in Ubuntu.
Thanks everyone!

---

### Post by heimo on 2005-08-20
Well... Don't know if this will help you at all, but I know that I have two serial ports (no modems).  /dev/ttyS0 and /dev/ttyS1, if I run:
 ```
sudo cat /etc/ttyS0
``` 
I get nothing, it just stays there, waiting for something to come from serial port.

If I enter:
 ```
sudo cat /etc/ttyS3
``` 
I get:
 > cat: /dev/ttyS3: Input/output error 
because I don't have serial #4.

Now, if I knew that my modem was there on ttyS1, I could open two terminal windows and on first one I'd enter:
 ```
sudo cat /etc/ttyS1
``` 
and on the second one I would enter:
 ```
sudo echo "ATZ" > /etc/ttyS1
``` 
and I'd expect to see OK on the first window.

Just something to debug with - and to compare. This doesn't solve anything, but maybe we can get some information.

---

### Post by darkstar5680 on 2005-08-20
Okay heimo, i'll boot back in Ubuntu and try this out.  I'll be back with some results.  Thanks.

---

### Post by darkstar5680 on 2005-08-20
Allright then, 

I tried: **sudo cat /dev/ttyS0**, and it just stayed there.
Then tried:    **sudo cat /dev/ttyS1**, and it just stayed there.

Next:    **sudo cat /dev/ttyS2**, and it returned *cat: /dev/ttyS2: Input/output error*
Next:    **sudo cat /dev/ttyS3**, and it returned *cat: /dev/ttyS3: Input/output error*

That makes me believe that I have devices on serial S0 and S1, but not on S2 and S3 (which should correspond to windows COM1 & COM2, but not COM3 and COM4)


So next I tried: **sudo cat /dev/ttyS0** in one terminal and **sudo echo "ATZ" > /dev/ttyS0** in another terminal.
The first window did not return an "OK".  In fact it did not return anything, just sat there in the same state.

I repeated this for /dev/ttyS1, but got the same results.

What could this mean?

---

### Post by heimo on 2005-08-20
No idea.

Did you see this?
[https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto)

Especially the part that suggests creating symbolic link (ln -s)  /dev/modem? I don't see how this would help in this case, but after all, I'm not too well "on map" with analog modems anymore. One thing I'd do, is install setserial (sudo apt-get install setserial) and check port / IRQ settings, maybe compare those to the ones on Windows.

Sad to say, but to me this doesn't look to promising and personally I wouln't use too much time trying to get it work - I'd buy an external modem and use that one instead. (very low prices nowadays, especially if you can buy second hand).

---

### Post by darkstar5680 on 2005-08-20
Yeah, I did try creating a symbolic link to /dev/modem, but it didnt seem to do anything to help the problem.  I will try setserial though.

---

### Post by darkstar5680 on 2005-08-20
Well, many hours later, and a lot of tinkering, but I finally have my modem working.  In the end I had to download a program called setserial, to get the serial port working.

First I ran: **sudo lspci -vv which told me the IRQ=11 and address =a000**.

For the hexidecimal address I had to prefix the address with 0x.

Next ran: **sudo setserial  /dev/ttyS2 irq 11 port 0xa000**

Here's where it gets weird: I next ran **sudo pppconfig** and it was able to autodetect the modem on the serial port, but it saw it on **/dev/ttyS14**, not on **/dev/ttyS2**. But hey, nonetheless it works.

Now if I could figure out how to connect to my ISP, peoplePC.  In winxp, you use a propriatary dialer app, which looks like a blackbox operation to me.  I'm sure that I can connect to them with a standard dialer, but I don't know how. Any ideas are appreciated, but I'll post this in another forum. Thanks for the help folks. :-)

---

