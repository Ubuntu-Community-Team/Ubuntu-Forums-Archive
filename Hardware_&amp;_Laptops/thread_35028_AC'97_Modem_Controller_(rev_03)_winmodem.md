---
title: "AC'97 Modem Controller (rev 03) winmodem"
date: 2005-05-17
forum: Hardware &amp; Laptops
---

### Post by abmcr on 2005-05-17
In my ASUS laptop there is a winmodem. The $lspci command put this output:

0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)

I have used the scanmodem utility and in the ModemData i find this:

Modem candidates are at PCI_buses:  0000:00:1f.6
    
Providing detail for device at PCI_bus 0000:00:1f.6
  with vendor-ID:device-ID
	    ----:----
Class 0703: 8086:24c6   Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
  SubSystem 1043:1826   Asustek Computer, Inc.: Unknown device 1826
0000:00:1f.6 0703: 8086:24c6 (rev 03)
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at e200 [size=256]
	I/O ports at e300 [size=128]
  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 8086:24c6 1043:1826 debian 2.6.10-5-386 3.3.5 3.3.5    i686

       
 The soft modem Subsystem operates under a controller
   8086:24c6 82801DB ICH4 
 capable of supporting under Linux AT LEAST modem Subsystem chips from manufacturers:

	Broadcom
	AgereSystems
	Conexant
	Intel
	Smartlink

As in UbuntuGuide, i have installed the Modem Driver (SmartLink). After i have installed Gnome PPP but if i want to connect, the Gppp don't work. What i do? Thank you

---

### Post by az on 2005-05-17
Did you install both the daemon and the modules?

[http://ubuntuforums.org/showpost.php?p=117356&postcount=34](http://ubuntuforums.org/showpost.php?p=117356&postcount=34)

---

### Post by abmcr on 2005-05-18
Yes i have installed both:with the Gnome-ppp (Configuring it) the modem was found at /dev/ttySL0 and i have the /dev/modem as symbolic link:

lrwxrwxrwx  1 root root           6 2005-05-18 11:04 modem -> ttySL0

The initial string in the configuration of Gnome-ppp is 

ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

and when i try to connect i see in the message window :" Sending password" but any number is composed. :neutral:

---

### Post by az on 2005-05-18
Open a terminal and do
sudo pppconfig and enter all you info.  Save and then quit.

Open another terminal and do
sudo tail -f /var/log/messages

On the first terminal do 

sudo pon.

Post the output from the second terminal.

---

### Post by abmcr on 2005-05-18
There is the output from the second terminal

May 18 16:03:33 localhost pppd[12496]: pppd 2.4.2 started by andrea, uid 1000
May 18 16:03:34 localhost chat[12497]: abort on (BUSY)
May 18 16:03:34 localhost chat[12497]: abort on (NO CARRIER)
May 18 16:03:34 localhost chat[12497]: abort on (VOICE)
May 18 16:03:34 localhost chat[12497]: abort on (NO DIALTONE)
May 18 16:03:34 localhost chat[12497]: abort on (NO DIAL TONE)
May 18 16:03:34 localhost chat[12497]: abort on (NO ANSWER)
May 18 16:03:34 localhost chat[12497]: abort on (DELAYED)
May 18 16:03:34 localhost chat[12497]: send (ATZ^M)
May 18 16:03:34 localhost chat[12497]: expect (OK)
May 18 16:03:34 localhost chat[12497]: ATZ^M^M
May 18 16:03:34 localhost chat[12497]: OK
May 18 16:03:34 localhost chat[12497]:  -- got it
May 18 16:03:34 localhost chat[12497]: send (ATDTreplace_with_number1055421010^M)
May 18 16:03:34 localhost chat[12497]: expect (CONNECT)
May 18 16:03:34 localhost chat[12497]: ^M
May 18 16:03:34 localhost chat[12497]: ATDTreplace_with_number1055421010^M^M
May 18 16:03:34 localhost kernel: codec_semaphore: semaphore is not ready [0x1][0x700300]
May 18 16:03:34 localhost kernel: codec_write 1: semaphore is not ready for register 0x54
May 18 16:03:34 localhost chat[12497]: NO CARRIER
May 18 16:03:34 localhost chat[12497]:  -- failed
May 18 16:03:34 localhost chat[12497]: Failed (NO CARRIER)
May 18 16:03:34 localhost kernel: codec_semaphore: semaphore is not ready [0x1][0x700300]
May 18 16:03:34 localhost kernel: codec_write 1: semaphore is not ready for register 0x54
May 18 16:03:35 localhost pppd[12496]: Exit.


I fail to insert the data of connection? Thank you

---

### Post by az on 2005-05-18
I think you may need a newer versino of the driver.  The licence has changed so get the driver from here:
[http://www.smlink.com/content.aspx?id=135](http://www.smlink.com/content.aspx?id=135)

install build-essential and linux-headers (corresponding to your linux-image) and then compile the driver yourself:

tar xvzf sl*
cd slmodem*
sudo ./configure
sudo make 
sudo make install

If this is incorrect, just read the documentation.  It is usually straightforward.  Let me know...

---

### Post by zeejdeej on 2005-05-18
hello there,

                     i am also trying to run Ubuntu linux on my ASUS Z9000 series laptop. can you tell me how and from where u got your hardware drivers installed? and how to make it fully functional on my ASUS laptop. if you help me step by step that would be highly aperitiated as i am a newbie to ubuntu,.

waiting for reply

regards,

ZeejDeej

---

### Post by az on 2005-05-18
[http://ubuntuforums.org/showpost.php?p=117356&postcount=34](http://ubuntuforums.org/showpost.php?p=117356&postcount=34)

---

