---
title: "[Internal Modem] Help installing it!"
date: 2007-07-27
forum: Hardware &amp; Laptops
---

### Post by mgiaff on 2007-07-27
Hi there!
I'm trying to install the drivers to use my modem. I followed this guide:
[https://help.ubuntu.com/community/DialupModemHowto/Smartlink](https://help.ubuntu.com/community/DialupModemHowto/Smartlink)

But when I put the following command (after the "Feisty 7.04 Special Instructions"), an error occours:

Command:
```
sudo module-assistant auto-install sl-modem
```

Error (after some seconds of installation):
```
Build of the package sl-modem-source failed!
```

Last portion of code:
```
make[2]: Entering directory `/usr/src/modules/sl-modem/drivers'            
gcc-4.1 -I/lib/modules/2.6.20-15-generic/build/include -o kernel-ver       
kernel-ver.c                                                               
kernel-ver.c: In function ‘main’:                                          
kernel-ver.c:11: error: ‘UTS_RELEASE’ undeclared (first use in this        
function)                                                                  
kernel-ver.c:11: error: (Each undeclared identifier is reported only once  
kernel-ver.c:11: error: for each function it appears in.)                  
make[2]: *** [kernel-ver] Error 1                                          
make[2]: Leaving directory `/usr/src/modules/sl-modem/drivers'             
make[1]: *** [binary-modules] Error 2                                      
make[1]: Leaving directory `/usr/src/modules/sl-modem'                     
make: *** [kdist_build] Error 2  
```

---

### Post by mgiaff on 2007-07-27
None?

Perhaps there's an error in my installing procedure. Is there someone who can help me??

---

### Post by zgornel on 2007-07-27
> **mgiaff said:**
> None?

Perhaps there's an error in my installing procedure. Is there someone who can help me??
Have you installed linux-headers and build-essentials packages ? Seems to me like a missing header error.

---

### Post by Bachstelze on 2007-07-27
If you are sure those are the drivers you need, forget the wiki and do this instead :

Get the drivers from [http://linmodems.technion.ac.il/packages/smartlink/Ubuntu/](http://linmodems.technion.ac.il/packages/smartlink/Ubuntu/) and pick the one matching your kernel. Copy to your Ubuntu, extract and run the setup script. Then, run

```
sudo wvdialconf /etc/wvdial.conf
```

and see if your modem is detected.

---

### Post by mgiaff on 2007-07-28
Thank you for the link, I will try.

To be sure, I post my ModemData.txt file. I downloaded the following package:
[http://linmodems.technion.ac.il/packages/smartlink/Ubuntu/slamr-2.6.20-15-generic.tar.gz](http://linmodems.technion.ac.il/packages/smartlink/Ubuntu/slamr-2.6.20-15-generic.tar.gz)



Let me know please, if I'm installing the correct one!
Thank you
Bye

---

### Post by Bachstelze on 2007-07-28
You are not using the correct drivers.

Download the SmartLink modem daemon from [http://linmodems.technion.ac.il/packages/smartlink/SLMODEMD.gcc4.1.tar.gz](http://linmodems.technion.ac.il/packages/smartlink/SLMODEMD.gcc4.1.tar.gz)

then unpack and run it :
```
tar xzvf SLMODEMD.gcc4.1.tar.gz
cd SLMODEMD.gcc4.1
sudo ./slmodemd -c YOUR_COUNTRY --alsa hw:0,6
```

If it goes well, wvdial should detect your modem :

```
sudo wvdialconf /etc/wvdial.conf
```

---

### Post by mgiaff on 2007-07-28
It doesn't work... This is the error displayed:

> Sorry, no modem was detected! Is it in use by another program? Did you configure it properly with setserial?


What can I do?

---

### Post by Bachstelze on 2007-07-28
Then, most certainly you'll have an error in the terminal you ran slmodemd in. What do you have in there ?

---

### Post by mgiaff on 2007-07-28
Sorry, I don't understand (I'm italian)... Could you please reformulate the sentence. Thank you...:)

---

### Post by Bachstelze on 2007-07-28
Hmm, what commands did you run, exactly ?

---

### Post by mgiaff on 2007-07-28
The commands that you wrote...

I tried to run the command "slmodemd". This is the answer:
> error: mdm setup: cannot open dev `/dev/slamr0': No such device or address
error: cannot setup device `/dev/slamr0'

---

### Post by Bachstelze on 2007-07-28
Please type the commands exactly as you ran them, you certainly made a mistake somewhere.

---

### Post by mgiaff on 2007-07-28
I copy my terminal output:

> 
mauri@Mauri-Ubuntu:~$ sudo -s
root@Mauri-Ubuntu:~# tar xzvf /home/mauri/Desktop/SLMODEMD.gcc4.1.tar.gz
SLMODEMD.gcc4.1/
SLMODEMD.gcc4.1/1st_Read.txt
SLMODEMD.gcc4.1/Changes
SLMODEMD.gcc4.1/COPYING
SLMODEMD.gcc4.1/CountryList.txt
SLMODEMD.gcc4.1/Files.txt
SLMODEMD.gcc4.1/README
SLMODEMD.gcc4.1/scripts/
SLMODEMD.gcc4.1/scripts/slmodem.spec
SLMODEMD.gcc4.1/scripts/mandrake/
SLMODEMD.gcc4.1/scripts/mandrake/slmodemd
SLMODEMD.gcc4.1/scripts/slackware/
SLMODEMD.gcc4.1/scripts/slackware/rc.slmodemd
SLMODEMD.gcc4.1/scripts/slackware/README
SLMODEMD.gcc4.1/scripts/slmodemd.ubuntu.italy
SLMODEMD.gcc4.1/scripts/slmodemd
SLMODEMD.gcc4.1/scripts/suse/
SLMODEMD.gcc4.1/scripts/suse/slmodemd.conf
SLMODEMD.gcc4.1/scripts/suse/slmodemd.SUSE
SLMODEMD.gcc4.1/Slmodem-ALSA.txt
SLMODEMD.gcc4.1/slmodemd
SLMODEMD.gcc4.1/slmodem.txt
SLMODEMD.gcc4.1/Testing.txt
SLMODEMD.gcc4.1/wvdial.conf
SLMODEMD.gcc4.1/Unload.txt
SLMODEMD.gcc4.1/slmodemd.txt
root@Mauri-Ubuntu:~# cd SLMODEMD.gcc4.1
[email]root@Mauri-Ubuntu:~/SLMODEMD.gcc[/email]4.1# sudo ./slmodemd -c ITALY --alsa hw:0,
ALSA lib conf.c:3952:(snd_config_expand) Parse arguments error: Invalid argument
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM hw:0,
error: alsa setup: cannot open playback device 'hw:0,': Invalid argument
error: cannot setup device `hw:0,'
[email]root@Mauri-Ubuntu:~/SLMODEMD.gcc[/email]4.1# sudo ./slmodemd -c ITALY --alsa hw:0,6
SmartLink Soft Modem: version 2.9.11 Feb 15 2007 23:08:19
symbolic link `/dev/ttySL0' -> `/dev/pts/1' created.
modem `hw:0,6' created. TTY is `/dev/pts/1'
Use `/dev/ttySL0' as modem device, Ctrl+C for termination.

[email]root@Mauri-Ubuntu:~/SLMODEMD.gcc[/email]4.1# sudo wvdialconf /etc/wvdial.conf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.
[email]root@Mauri-Ubuntu:~/SLMODEMD.gcc[/email]4.1# 


---

### Post by Bachstelze on 2007-07-28
Sorry, I forgot to mention, you must *not* terminate the daemon, as it is it which makes your modem work. When you have this message :

```
SmartLink Soft Modem: version 2.9.11 Feb 15 2007 23:08:19
symbolic link `/dev/ttySL0' -> `/dev/pts/1' created.
modem `hw:0,6' created. TTY is `/dev/pts/1'
Use `/dev/ttySL0' as modem device, Ctrl+C for termination.
```

you must let it run and open a new terminal to run wvdial.

---

### Post by mgiaff on 2007-07-28
After this will I be able to connect with the connection manager??? What are the settings that I have to configure?

---

### Post by Bachstelze on 2007-07-28
After this, you edit the wvdial config file (/etc/wvdial.conf) with your favourite text editor to fill in your username/passwor and your ISP's phone number. Then you dial with

```
sudo wvdial
```

---

### Post by mgiaff on 2007-07-28
And to connect with the connection manager???

---

### Post by Bachstelze on 2007-07-28
Get a real modem. As far as I know, wvdial is the only dialer that can operate winmodems.

---

### Post by mgiaff on 2007-07-28
Are you sure??

> 
mauri@Mauri-Ubuntu:~$ sudo wvdial
--> WvDial: Internet dialer version 1.56
--> Cannot open /dev/ttySL0: No such file or directory
--> Cannot open /dev/ttySL0: No such file or directory
--> Cannot open /dev/ttySL0: No such file or directory


---

### Post by Bachstelze on 2007-07-28
*You must not terminate the daemon !!*

---

### Post by mgiaff on 2007-07-28
What is the daemon?

---

### Post by Bachstelze on 2007-07-28
> **HymnToLife said:**
> Sorry, I forgot to mention, you must *not* terminate the daemon, as it is it which makes your modem work. When you have this message :

```
SmartLink Soft Modem: version 2.9.11 Feb 15 2007 23:08:19
symbolic link `/dev/ttySL0' -> `/dev/pts/1' created.
modem `hw:0,6' created. TTY is `/dev/pts/1'
Use `/dev/ttySL0' as modem device, Ctrl+C for termination.
```

you must let it run and open a new terminal to run wvdial.

That. You must not press Ctrl+C because it is the daemon that makes your modem work so obviously if you kill it, your modem won't work. If it works, we'll go about making it run in the background but for now, just let it be and run wvdial in another terminal window.

---

### Post by mgiaff on 2007-08-24
This is the message given by the terminal:

```

mauri@Mauri-Ubuntu:~$ sudo wvdialconf /etc/wvdial.conf
Password:
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttySL0<*1>: ATQ0 V1 E1 -- OK
ttySL0<*1>: ATQ0 V1 E1 Z -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttySL0<*1>: Modem Identifier: ATI -- SmartLink Soft Modem
ttySL0<*1>: Speed 4800: AT -- OK
ttySL0<*1>: Speed 9600: AT -- OK
ttySL0<*1>: Speed 19200: AT -- OK
ttySL0<*1>: Speed 38400: AT -- OK
ttySL0<*1>: Speed 57600: AT -- OK
ttySL0<*1>: Speed 115200: AT -- OK
ttySL0<*1>: Speed 230400: AT -- OK
ttySL0<*1>: Speed 460800: AT -- OK
ttySL0<*1>: Max speed is 460800; that should be safe.
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttySL0.
Modem configuration written to /etc/wvdial.conf.
ttySL0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
mauri@Mauri-Ubuntu:~$ 

```

---

### Post by Bachstelze on 2007-08-24
Okay, now edit wvdial.conf to fill in your username, password and your ISP's phone number. Then run

```
sudo wvdial
```

---

### Post by mgiaff on 2007-08-24
Do I have to run the daemon or something like that???

---

### Post by mgiaff on 2007-08-24
```

mauri@Mauri-Ubuntu:~$ sudo wvdial
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT7021055000
--> Waiting for carrier.
ATDT7021055000
NO CARRIER
ERROR
--> No Carrier!  Trying again.
--> Sending: ATDT7021055000
--> Waiting for carrier.
ATDT7021055000
NO CARRIER
ERROR
--> No Carrier!  Trying again.

```
[And so on... hundreds of times!]


In the daemon window (for each of the above messages):
```
error: period size 48 is not supported by playback (64).
```

---

### Post by Bachstelze on 2007-08-24
This is a well knon issue, that has been causing trouble to almost all HDA users for a while. Try she slmodemd available [here](ftp://fkraiem.no-ip.org/pub/smartlink), which will hopefully fix the issue.

---

### Post by mgiaff on 2007-08-25
I tried the following command, but nothing happens...

```
mauri@Mauri-Ubuntu:~$ '/home/mauri/Desktop/BOOOOH/slmodemd' 
error: mdm setup: cannot open dev `/dev/slamr0': No such device or address
error: cannot setup device `/dev/slamr0'
```

How can I use the file (I extracted it)?

---

### Post by Bachstelze on 2007-08-25
You must use the same syntax than for the old slmodemd :

```
cd /home/mauri/Desktop/BOOOOH/
sudo ./slmodemd -c ITALY --alsa hw:0,6
```

---

### Post by mgiaff on 2007-08-25
In the "daemon":
```
mauri@Mauri-Ubuntu:~$ cd /home/mauri/Desktop/BOOOOH/
mauri@Mauri-Ubuntu:~/Desktop/BOOOOH$ sudo ./slmodemd -c ITALY --alsa hw:0,6
Password:
SmartLink Soft Modem: version 2.9.11 Aug  6 2007 22:02:27
symbolic link `/dev/ttySL0' -> `/dev/pts/1' created.
modem `hw:0,6' created. TTY is `/dev/pts/1'
Use `/dev/ttySL0' as modem device, Ctrl+C for termination.
```

In a new terminal window:
```
mauri@Mauri-Ubuntu:~/Desktop/BOOOOH$ sudo wvdialconf /etc/wvdial.conf
Password:
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttySL0<*1>: ATQ0 V1 E1 -- OK
ttySL0<*1>: ATQ0 V1 E1 Z -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttySL0<*1>: Modem Identifier: ATI -- SmartLink Soft Modem
ttySL0<*1>: Speed 4800: AT -- OK
ttySL0<*1>: Speed 9600: AT -- OK
ttySL0<*1>: Speed 19200: AT -- OK
ttySL0<*1>: Speed 38400: AT -- OK
ttySL0<*1>: Speed 57600: AT -- OK
ttySL0<*1>: Speed 115200: AT -- OK
ttySL0<*1>: Speed 230400: AT -- OK
ttySL0<*1>: Speed 460800: AT -- OK
ttySL0<*1>: Max speed is 460800; that should be safe.
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttySL0.
Modem configuration written to /etc/wvdial.conf.
ttySL0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
mauri@Mauri-Ubuntu:~/Desktop/BOOOOH$ sudo wvdial
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT7021055000
--> Waiting for carrier.
ATDT7021055000
NO CARRIER
ERROR
--> No Carrier!  Trying again.
```

Error returned in the daemon:
```
error: cannot setup hw params for playback: Invalid argument
```



Where's the mistake???

---

### Post by Bachstelze on 2007-08-25
Hmm, please paste the output of

```
cat /proc/asound/pcm
```

---

### Post by mgiaff on 2007-08-26
Output of the command above:
```
00-06: Si3054 Modem : Si3054 Modem : playback 1 : capture 1
00-00: ALC861VD Analog : ALC861VD Analog : playback 1 : capture 2
```

---

### Post by gcsrochester on 2007-09-07
Great news for all of us who have struggled to get the AC97 / Intel 82801 modem working in Ubuntu/Kubuntu - there is a solution! I won't bore you with the details but after 3 days of digging I deduced that the Smartlink Driver will never work for this modem. You must use a Conexant HSF driver and Dell has provided a driver specifically for Ubuntu/Kubuntu Feisty. Here's what you do:

1. Using Adept, uninstall both the Smartlink Daemon and the source code.
2. Download the Conexant HSF driver from: [http://support.dell.com/support/down...&fileid=206745](http://support.dell.com/support/down...&fileid=206745)
3. Install the .deb package
4. At the end of the installation, it will say the device can be found at /dev/ttySHSF0. In my case it was not. It was /dev/modem.
5. In your wvdial / kppp / Knet configuration you must set the modem to run unlocked.
6. Enter your account info and you're on your way!

Many thanks to Dell!

---

### Post by Bachstelze on 2007-09-07
Try again with the slmodemd that can be found in this archive :

[http://linmodems.technion.ac.il/packages/smartlink/SLMODEMD.gcc4.1.tar.gz](http://linmodems.technion.ac.il/packages/smartlink/SLMODEMD.gcc4.1.tar.gz)

---

### Post by mgiaff on 2007-09-08
SAME THING!

> --> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT7021055000
--> Waiting for carrier.
ATDT7021055000
NO CARRIER
ERROR
--> No Carrier!  Trying again.
--> Sending: ATDT7021055000
--> Waiting for carrier.
ATDT7021055000
NO CARRIER
ERROR
--> No Carrier!  Trying again.
--> Sending: ATDT7021055000
--> Waiting for carrier.
ATDT7021055000
NO CARRIER
ERROR
--> No Carrier!  Trying again.
--> Sending: ATDT7021055000
--> Waiting for carrier.
ATDT7021055000
NO CARRIER
ERROR
--> No Carrier!  Trying again.
--> Sending: ATDT7021055000
--> Waiting for carrier.
ATDT7021055000
NO CARRIER
ERROR
--> No Carrier!  Trying again.
--> Sending: ATDT7021055000
--> Waiting for carrier.
ATDT7021055000
NO CARRIER
ERROR
--> No Carrier!  Trying again.
--> Sending: ATDT7021055000
--> Waiting for carrier.
ATDT7021055000
NO CARRIER
ERROR
--> No Carrier!  Trying again.
--> Sending: ATDT7021055000
--> Waiting for carrier.
ATDT7021055000
NO CARRIER
ERROR
--> No Carrier!  Trying again.
--> Sending: ATDT7021055000
--> Waiting for carrier.
ATDT7021055000
NO CARRIER
ERROR
--> No Carrier!  Trying again.
--> Sending: ATDT7021055000
--> Waiting for carrier.
ATDT7021055000
NO CARRIER
ERROR
--> No Carrier!  Trying again.
--> Sending: ATDT7021055000
--> Waiting for carrier.
ATDT7021055000
NO CARRIER
ERROR
--> No Carrier!  Trying again.
--> Sending: ATDT7021055000
--> Waiting for carrier.
ATDT7021055000
NO CARRIER
ERROR
--> No Carrier!  Trying again.
Caught signal 2:  Attempting to exit gracefully...
--> Disconnecting at Sat Sep  8 16:27:43 2007


I think that the problem is when it sends this string:" ATDT7021055000"
Because the modem is correctly inizialized... This string is formed by the chars ATDT, followed by the phone number... Perhaps I have to add a prefix to my phone number...

---

### Post by Bachstelze on 2007-09-08
Nope, this is most likely a hardware/driver problem, but it has gone a bit over my head. I suggest you bring the issue to the [email]discuss@linmodems.org[/email] mailing-list (do not forget to attach your ModemData.txt !).

---

