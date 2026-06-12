---
title: "APC UPS and using apcupsd"
date: 2006-01-09
forum: Hardware &amp; Laptops
---

### Post by jacrider on 2006-01-09
I have installed an APC USP for my workstation.

I have installed apcupsd as the system to manage the UPS.

When I scan USB devices, I get this for the UPS:

T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=051d ProdID=0002 Rev= 1.06
S:  Manufacturer=APC
S:  Product=Back-UPS ES 500 FW:801.e6.D USB FW:e6
S:  SerialNumber=BB0536025043
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   6 Ivl=10ms

So, it is being detected and the driver is installed (usbhid).

So, I execute a start command:

$ /etc/init.d/apcupsd start
Starting APC UPS power management: apcupsd.

Again, everything looks fine.

Then, I try to do a status query and get:

$ /etc/init.d/apcupsd status
FATAL ERROR in apcaccess.c at line 243
tcp_open: cannot connect to server localhost on port 3551.
ERR=Connection refused


A great assistance in installing apcupsd has been a howto at [http://update.itlab.musc.edu/node/126](http://update.itlab.musc.edu/node/126)

This howto warns that this error might be received, but in a few moments, it should work ... but for me it doesn't seem to.

Any help appreciated.  The UPS could be working, and configured to do a nice quiet shutdown, but I just can't see that now.

Thanks.

---

### Post by talz13 on 2006-01-10
Yes, I'm having the same problem here.  Any help on the issue would be appreciated...

---

### Post by jacrider on 2006-01-11
I have e-mailed APC customer support asking for Linux support.

Looking in their faq's it looks like there was at one point a Red Hat version (rpm) of their power management software, but I couldn't find it in their dowloads section.  

They do have a Caldera version available for download, perhaps a more technical person than me can help with whether this version would work under Ubuntu.

The file is "pcplus_453_caldera.tar" available on their downloads page.  This is most likely a newer version of the version referenced in their faq above.  Opening the .tar in the archive manager didn't reveal a .rpm file, only an executable file.

Their website is [http://www.apc.com/tools/download/](http://www.apc.com/tools/download/)

Thanks.

---

### Post by jacrider on 2006-01-12
Ok, received a response from APC the next day.  Great service.  However, they might have led me into a solution I don't know how to do ... that's why I'm asking anothter question.

I downloaded (on their tech support guidance) from their download site the file: pbeagent-7.0.4-114.i386.rpm.  No problem so far.

After installing alias, I did the following:

sudo alias pbeagent-7.0.4-114.i386.rpm

This seemed to work as it resulted in the following file:

pbeagent_7.0.4-115_i386.deb   (yes the slight changes are right)

Then I did the following:

sudo dpkg -i pbeagent_7.0.4-115_i386.deb

And I didn't copy the screen messages, but no error messages.

Now I can't execute the program.  I tried setting up a launcher, but to no success.

Any ideas where I have gone wrong?

Thanks.

---

### Post by jacrider on 2006-01-19
I finally resolved this.

First, I have gone back to apcupsd.  I downloaded, compiled and installed the latest version of the application found on [www.apcupsd.com](www.apcupsd.com) and the version is 3.12.2.

To compile I was required to add the option --enable-usb to ensure the proper support.

   $./compile --enable-usb

Then:

   $ make

Followed by:

   $ sudo make install


Then I had to set the following options in the apcupsd.conf file:
   UPSCABLE usb
   UPSTYPE usb
   DEVICE 

and you need to ensure the following in the .conf file are also:

   NETSERVER on
   NISPORT 3551

Then, save everything and

   $ sudo apcupsd start.

To check status, do

   $ sudo apcaccess status

Great to have this done.

Andrew.

---

### Post by flange on 2006-01-24
Great.  This worked perfectly except for one small modification:

This line

[QUOTE=jacrider]   $./compile --enable-usb[/QUOTE]

should instead read

```
$./configure --enable-usb
```

Otherwise it worked perfectly for me.  Thanks for posting this.

---

### Post by talz13 on 2006-03-26
Ah, it's nice to see that you got it working!

I've been having a bit of trouble with it, though.  I got the apcupsd version from the site, and tried compiling it, but first it couldn't find a compiler.  No biggie, I just went and installed gcc.

However, now it says that the compiler can't create executables...


Hmm, now this morning it's saying it can't find the c++ compiler again.  I just tried rebooting, but still it can't find the compiler.  I have gcc, gcc-4.0, gcc-4.0-base, and libgcc1 packages installed, but it's not working for some reason.

---

### Post by TheOtherShoe on 2006-05-30
[quote=talz13]However, now it says that the compiler can't create executables...


Hmm, now this morning it's saying it can't find the c++ compiler again. I just tried rebooting, but still it can't find the compiler. I have gcc, gcc-4.0, gcc-4.0-base, and libgcc1 packages installed, but it's not working for some reason.[/quote]

If you are still working on this, try installing build-essential.

---

### Post by bjtuna on 2006-06-08
Ok I think I may have this figured out, my custom kernel didn't have the HID (human interface device) drivers for USB compiled in. If you don't have a custom kernel, you should make sure those modules have been loaded.  This document was VERY helpful:

[http://www.apcupsd.com/manual/USB_Configuration.html#SECTION000101100000000000000](http://www.apcupsd.com/manual/USB_Configuration.html#SECTION000101100000000000000)

---

### Post by rso on 2006-06-22
If you want the nice cgi gui that comes with it, type:

```

./configure --enable-usb --enable-cgi

```

The code of the idea from TheOtherShoe would be:
```

apt-get install build-essential

```

---

### Post by rso on 2006-06-22
The best things is then to add a file named ups to your apache2 conf.d directory and fill it with :

```

Alias /ups /usr/lib/cgi-bin/apcupsd

<Directory /usr/lib/cgi-bin/apcupsd>
  Options ExecCGI
    AllowOverride None
    Order allow,deny
    Allow from all
</Directory>


```

Of course, the CGI Handler needs to be activated before ;)

---

### Post by ringz on 2006-06-28
I don't see this problem after installment. But how can I check the modification of the halt script after make install?

---

### Post by wpshooter on 2006-07-06
[QUOTE=jacrider]I finally resolved this.

First, I have gone back to apcupsd.  I downloaded, compiled and installed the latest version of the application found on [www.apcupsd.com](www.apcupsd.com) and the version is 3.12.2.

To compile I was required to add the option --enable-usb to ensure the proper support.

   $./compile --enable-usb

Then:

   $ make

Followed by:

   $ sudo make install


Then I had to set the following options in the apcupsd.conf file:
   UPSCABLE usb
   UPSTYPE usb
   DEVICE 

and you need to ensure the following in the .conf file are also:

   NETSERVER on
   NISPORT 3551

Then, save everything and

   $ sudo apcupsd start.

To check status, do

   $ sudo apcaccess status

Great to have this done.

Andrew.[/QUOTE]

When I go to the link [www.apcupsd.com](www.apcupsd.com), the version I am seeing is 3.12.3.

Is this the correct version ?

Also, would I download the file shown under the listing of **source** ?

Once the file is downloaded is this basically just a matter of extracting the tar.qz file and then following the remainder of the instructions per above ?

Does the file need to be downloaded and extracted to any particular directory/folder ?

Thanks.

---

### Post by mwillis on 2006-07-11
Hello,

Thanks for figuring that out, jacrider.  I got apcupsd working by installing it with apt-get, then modifying apcupsd.conf according to your instructions.  I didn't have to compile it from scratch (maybe because I'm using Dapper Drake?  I'm not sure.)

Mike

---

### Post by wpshooter on 2006-07-16
> **jacrider said:**
> Ok, received a response from APC the next day.  Great service.  However, they might have led me into a solution I don't know how to do ... that's why I'm asking anothter question.

I downloaded (on their tech support guidance) from their download site the file: pbeagent-7.0.4-114.i386.rpm.  No problem so far.

**After installing alias, I did the following**:

sudo alias pbeagent-7.0.4-114.i386.rpm

This seemed to work as it resulted in the following file:

pbeagent_7.0.4-115_i386.deb   (yes the slight changes are right)

Then I did the following:

sudo dpkg -i pbeagent_7.0.4-115_i386.deb

And I didn't copy the screen messages, but no error messages.

Now I can't execute the program.  I tried setting up a launcher, but to no success.

Any ideas where I have gone wrong?

Thanks.


In this post they said "**After installing alias, I did the following**"

What is installing alias ?

Thanks.

---

### Post by Magister on 2006-08-02
> **jacrider said:**
> Ok, received a response from APC the next day.  Great service.  However, they might have led me into a solution I don't know how to do ... that's why I'm asking anothter question.

I downloaded (on their tech support guidance) from their download site the file: pbeagent-7.0.4-114.i386.rpm.  No problem so far.

After installing alias, I did the following:

sudo alias pbeagent-7.0.4-114.i386.rpm

This seemed to work as it resulted in the following file:

pbeagent_7.0.4-115_i386.deb   (yes the slight changes are right)

Then I did the following:

sudo dpkg -i pbeagent_7.0.4-115_i386.deb

And I didn't copy the screen messages, but no error messages.

Now I can't execute the program.  I tried setting up a launcher, but to no success.

Any ideas where I have gone wrong?

Thanks.


Where did they tell you to find the file?  I have looked everywhere and cant find it. Thanks for any help you give

Magister

---

### Post by cfm on 2006-08-03
I ran into a problem identical to the one the original poster experienced. I can't tell whether he ever resolved his [font=Courier New]apcupsd[/font] error, but I fixed mine by removing and then reinstalling the [font=Courier New]apcupsd[/font] package with [font=Courier New]apt-get[/font]. :)

---

### Post by wpshooter on 2006-08-10
> **jacrider said:**
> Ok, received a response from APC the next day.  Great service.  However, they might have led me into a solution I don't know how to do ... that's why I'm asking anothter question.

I downloaded (on their tech support guidance) from their download site the file: pbeagent-7.0.4-114.i386.rpm.  No problem so far.

After installing alias, I did the following:

sudo alias pbeagent-7.0.4-114.i386.rpm

This seemed to work as it resulted in the following file:

pbeagent_7.0.4-115_i386.deb   (yes the slight changes are right)

Then I did the following:

sudo dpkg -i pbeagent_7.0.4-115_i386.deb

And I didn't copy the screen messages, but no error messages.

Now I can't execute the program.  I tried setting up a launcher, but to no success.

Any ideas where I have gone wrong?

Thanks.

Regarding the above post, I just got off of the phone with APC and they tell me that they do NOT make or support a program named APCUPSD.  

Am I getting something wrong here or is Jacrider receiving information from someone other than APC.

Thanks.

---

### Post by jacrider on 2006-08-15
apcupsd is not a product from APC.  It is a community developed product to manage your UPS and if necessary manage a clean shut-down of your computer in the event of a power failure.

APC did send me pbeagentxxxx.rpm.  It is their linux version of their UPS monitoring system.  I had real difficulty getting it to work.  So, I went back to apcupsd.

When I originally posted how I installed it I was on Breezy and I don't think apcupsd was in the repositories.  Subsequently, I have built a new computer and upgraded to Dapper.

On my new computer, I simply installed apcupsd from Synaptic (as it is now in the repositories) and modified the /etc/apcupsd/apcupsd.conf as I described earlier and in very short order, I was back in business with my UPS being monitored.

---

### Post by BrianK on 2006-08-23
> **wpshooter said:**
> In this post they said "**After installing alias, I did the following**"

What is installing alias ?

Thanks.

I know this is an old question, but if someone else comes searching through...

he meant to type "alien" not "alias".  Alien is the app that converts rpm files into deb files.

rpm = redhat package management
deb = debian (or ubuntu) package management

that said, if you read further, this is not the way to go.  The best way, imo, is to install apcupsd & apcupsd-cgi via synaptic & then edit the config files as posted.

---

### Post by russelld on 2006-09-03
> **rso said:**
> 

Of course, the CGI Handler needs to be activated before ;)

Can you please give more details on how to do this?
I've had a go and still not getting it running from the browser  ](*,)

---

### Post by PurplePenguin on 2007-05-31
Hello everybody!  I just bought an APC battery backup and had a tiny bit of trouble getting apcupsd set up (ok, ok, it took me about 15 minutes - it wasn't too bad at all).

I did find a short HowTo that I thought might help the next guy.  It says Kubuntu/Feisty Fawn, but works fine with Ubuntu Server on Dapper. :D

[https://blueimp.net/linux/howto/apc-ups.txt]("https://blueimp.net/linux/howto/apc-ups.txt")

---

### Post by xelasmada on 2007-07-31
Does this package work with Belkin (or other) UPS, or only APC?
Thx

---

### Post by JockVSJock on 2007-09-08
I'm setting up apcupsd on my Ubuntu 7.04, and I have a UPS, which connects to the PC via USB. 
How do I know how to set this correctly under /etc/apcupsd/apcupsd.conf? 

```

UPSTYPE usb
DEVICE /dev/ttyS0

```

DEVICE is obviously incorrect...so how do I know what is right? 

Also getting this too...

```


root@ladytron:/sbin# ./apctest


2007-09-08 22:04:20 apctest 3.12.4 (19 August 2006) debian
Checking configuration ...
Attached to driver: usb
sharenet.type = DISABLE
cable.type = USB_CABLE

You are using a USB cable type, so I'm entering USB test mode
mode.type = USB_UPS
Setting up the port ...
apctest FATAL ERROR in device.c at line 68
Unable to create UPS lock file.
apctest FATAL ERROR in device.c at line 68
Unable to create UPS lock file.
apctest error termination completed


```

thanks

---

### Post by Compact on 2007-10-13
[Here]("https://help.ubuntu.com/community/apcupsd") there is a how-to about how to configure an APC ups.

---

### Post by JockVSJock on 2007-10-20
Kewl, let me read thru this and I'll report back. 

thanks

---

### Post by JockVSJock on 2007-10-20
I'm still getting the same error as above: 

```


root@ladytron:/sbin# ./apctest


2007-10-20 09:45:59 apctest 3.12.4 (19 August 2006) debian
Checking configuration ...
Attached to driver: usb
sharenet.type = DISABLE
cable.type = USB_CABLE

You are using a USB cable type, so I'm entering USB test mode
mode.type = USB_UPS
Setting up the port ...
apctest FATAL ERROR in device.c at line 68
Unable to create UPS lock file.
apctest FATAL ERROR in device.c at line 68
Unable to create UPS lock file.
apctest error termination completed



```


If you were to look at the file, /etc/apcupsd/apcupsd.conf, it looks like I have that 
correctly setup: 

```


   37 # For USB UPSes, please leave the DEVICE directive blank. For
     38 # other UPS types, you must specify an appropriate port or address.
     39 #
     40 # UPSTYPE   DEVICE           Description
     41 # apcsmart  /dev/tty**       Newer serial character device,
     42 #                            appropriate for SmartUPS models using
     43 #                            a serial cable (not USB).
     44 #
     45 # usb       <BLANK>          Most new UPSes are USB.
     46 #                            A blank DEVICE setting enables
     47 #                            autodetection, which is th best choice
     48 #                            for most installations.
     49 #
     50 # net       hostname:port    Network link to a master apcupsd
     51 #                            through apcupsd's Network Information
     52 #                            Server. This is used if you don't have
     53 #                            a UPS directly connected to your computer.
     54 #
     55 # snmp      hostname:port:vendor:community
     56 #                            SNMP Network link to an SNMP-enabled
     57 #                            UPS device. Vendor is the MIB used by
     58 #                            the UPS device: can be "APC", "APC_NOTRAP"
     59 #                            or "RFC" where APC is the powernet MIB,
     60 #                            "APC_NOTRAP" is powernet with SNMP trap
     61 #                            catching disabled, and RFC is the IETF's
     62 #                            rfc1628 UPS-MIB. Port is usually 161.
     63 #                            Community is "private".
     64 #
     65 # dumb      /dev/tty**       Old serial character device for use
     66 #                            with simple-signaling UPSes.
     67 #
     68 # UPSTYPE apcsmart
     69 # DEVICE /dev/ttyS0
     70
     71 UPSTYPE usb
     72 ## DEVICE /dev/ttyS0



```

Line 68 is coded out...so I wonder where it is making the error? 

thanks

---

### Post by mrkedvz on 2007-10-24
I am trying to get my APC UPS working with 7.10 and I get the following error message:

apcupsd[6765]: apcupsd FATAL ERROR in apcupsd.c at line 260 Apcupsd cannot continue without a valid driver.

Has anyone seen this? I am a newbie, so be gentle.

---

### Post by inkscarab on 2007-10-28
Same problems here after upgrading to Gutsy... can't load...

---

### Post by mrkedvz on 2007-10-29
modified my apcupsd.conf file and loaded gapcmod and it started working.

Thanks.

---

### Post by Tyr_7BE on 2007-11-02
I'm having a problem where it loos like my APC UPS 350 is being picked up by Gutsy on my Compaq Armada M500 laptop, but apcupsd isn't working.  Every time I try to start the daemon, I get the following:

```

conor@jade:~$ sudo /etc/init.d/apcupsd start
/etc/default/apcupsd: 4: UPSCABLE: not found
conor@jade:~$

```

My /etc/default/apcupsd file reads as follows:
```

conor@jade:~$ cat /etc/default/apcupsd
# Defaults for apcupsd initscript

# Apcupsd-devel internal configuration
UPSCABLE usb
UPSTYPE usb
#DEVICE
LOCKFILE /var/lock
UPSCLASS standalone
UPSMODE disable
conor@jade:~$
```

If I replace this file with /etc/apcupsd/apcupsd.conf, I get a similar failure, but on a different line (ie, line 30-something instead of line 4, because teh UPSCABLE option appears on line 30-something of that file).

I've tried this with DEVICE defined but left blank, also with 'DEVICE /dev/usb/hiddev0', and with 'DEVICE /dev/usb/hiddev[0-15]'.  Always the same result.

I'm pretty sure the UPS itself is working, it's just the config file that apcupsd doesn't like.  If I add 'asdf usb' right before 'UPSCABLE usb', it tells me 'asdf: not found'.  If I comment out the UPSCABLE line, it tells me 'UPSTYPE: not found'.  So it seems to hate the entire config file in general.

I know the UPS is working because of the following:

```

conor@jade:~$ ls -l /dev/usb
total 0
crw-rw---- 1 root root 180, 96 2007-10-31 23:13 hiddev0
conor@jade:~$




conor@jade:~$ lsusb
Bus 004 Device 003: ID 067b:3507 Prolific Technology, Inc. PL3507 ATAPI6 Bridge

Bus 004 Device 002: ID 0402:5621 ALi Corp. USB 2.0 Storage Device
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 051d:0002 American Power Conversion Back-UPS Pro 500/1000
/1500
Bus 001 Device 001: ID 0000:0000
conor@jade:~$






conor@jade:~$ sudo apctest


2007-11-02 16:42:36 apctest 3.14.1 (04 May 2007) debian
Checking configuration ...
Attached to driver: usb
sharenet.type = DISABLE
cable.type = USB_CABLE

You are using a USB cable type, so I'm entering USB test mode
mode.type = USB_UPS
Setting up the port ...
Hello, this is the apcupsd Cable Test program.
This part of apctest is for testing USB UPSes.

Getting UPS capabilities...SUCCESS

Please select the function you want to perform.

1) Test kill UPS power
2) Perform self-test
3) Read last self-test result
4) Change battery date
5) View battery date
6) View manufacturing date
7) Set alarm behavior
8) Set sensitivity
9) Quit

Select function number: 6

Manufacturing date: 05/22/2007

1) Test kill UPS power
2) Perform self-test
3) Read last self-test result
4) Change battery date
5) View battery date
6) View manufacturing date
7) Set alarm behavior
8) Set sensitivity
9) Quit

Select function number: 9

2007-11-02 16:42:44 End apctest.
conor@jade:~$

```

So it's detecting the UPS fine, it's creating /dev/usb/hiddev0, and apctest appears to be communicating the the UPS and retrieving the manufacturing date, meaning read and write to the UPS over USB are both working.  The issue appears to be that apcupsd doesn't like the config file.

Any ideas?  Can someone who has this working please post the contents of their /etc/default/apcupsd file, and maybe their /etc/apcupsd/apcupsd.conf file?

---

### Post by Tyr_7BE on 2007-11-03
I was able to get it working.  I deleted /etc/default/apcupsd.  After I did that, /etc/init.d/apcupsd would no longer work (did nothing), but manually running /sbin/apcupsd seemed to start the deamon.  indeed, running apcaccess gives me all kinds of output.  I was even able to confirm that my machine shuts down when the APC thinks there's < 3 min of battery life remaining.  Looks like we're good to go!

---

### Post by dmanbuhnik on 2007-12-11
Hi,

i just got my new UPS with usb connections, i install Apcupsd with apt-get (its the latest version - 3.14.1) but this is the output i get:
```
 sudo apcaccess status
APC      : 001,019,0486
DATE     : Wed Dec 12 00:07:45 IST 2007
HOSTNAME : #####-desktop
RELEASE  : 3.14.1
VERSION  : 3.14.1 (04 May 2007) debian
UPSNAME  : ######-desktop
CABLE    : USB Cable
MODEL    : USB UPS Driver
UPSMODE  : Stand Alone
STARTTIME: Wed Dec 12 00:04:41 IST 2007
STATUS   : 
MBATTCHG : 5 Percent
MINTIMEL : 3 Minutes
MAXTIME  : 0 Seconds
NUMXFERS : 0
TONBATT  : 0 seconds
CUMONBATT: 0 seconds
XOFFBATT : N/A
STATFLAG : 0x07000000 Status Flag
END APC  : Wed Dec 12 00:08:32 IST 2007

```

well the problem is the STATUS line which is empty
how can i get my ubuntu 7.10 (actually its linux mint 4) work with my UPS?

Thx,

---

### Post by dmanbuhnik on 2007-12-12
bump

help? anyone?

---

### Post by Cato2 on 2008-02-06
Here's how I got my APC working with Feisty (7.04) - model is APC Back-UPS CS 650 but I think most Back-UPS models with USB will work the same way:

1. Install the UPS, power system back up from hibernate

2. sudo aptitude install apcupsd  (you can use apt-get if you prefer)

3. edit /etc/apcupsd/apcupsd.conf (as root) to ensure the following lines look like this - the DEVICE line is correct, just DEVICE on a line by itself:

```

    UPSCABLE usb
    UPSTYPE usb
    DEVICE

```

4. Edit /etc/default/apcupsd (as root) and change the ISCONFIGURED=no line - change the no to yes

5. Restart the daemon: /etc/init.d/apcupsd restart

6. Check status - use either sudo /etc/init.d/apcupsd status or (preferably):

     ```
sudo apcaccess status | less
```

This should show details including your model number, time on battery, etc.  If you only see a few details, perhaps your USB connection is not working.

7. Turn off utility power to the UPS - check that apcaccess output changes, and also check /var/log/apc* log files to see the power loss event is detected by the apcupsd daemon.

8. Leave the utility power off for long enough to see if power off is done properly (save any open documents etc before you do this!).  Again, check logs when system is back up.

This is using a standard kernel.  The apcupsd daemon will also automatically shut down the system after the batteries are exhausted - see my next post in this thread for how to make it hibernate instead.

The HOWTO I used is at [https://help.ubuntu.com/community/apcupsd](https://help.ubuntu.com/community/apcupsd)

To get extra docs, and install an optional web frontend (requires some Apache config), do:
```
sudo aptitude install apcupsd-doc apcupsd-cgi
```

To see where files are installed, use this on any package
```
sudo dpkg -L apcupsd | less 
```

---

### Post by Cato2 on 2008-02-06
@dmanbuhnik: it looks from that output that the APC software on your system is not yet communicating with the UPS.  Try checking /var/log/apc* for errors, and any sign that it is communicating.  Also, try another USB device such as a mouse in that USB port to check it's working, and of course check cables are plugged in properly.  Normally you would see some of these parameters from the UPS:

```

CABLE    : USB Cable
MODEL    : Back-UPS CS 650
UPSMODE  : Stand Alone
STARTTIME: Wed Feb 06 21:35:17 GMT 2008
STATUS   : ONLINE
LINEV    : 000.0 Volts
LOADPCT  :  25.0 Percent Load Capacity
BCHARGE  : 099.0 Percent
TIMELEFT :  21.4 Minutes
MBATTCHG : 5 Percent
MINTIMEL : 3 Minutes
MAXTIME  : 0 Seconds
OUTPUTV  : 230.0 Volts
DWAKE    : 000 Seconds
DSHUTD   : 000 Seconds
LOTRANS  : 000.0 Volts
HITRANS  : 266.0 Volts
RETPCT   : 000.0 Percent
ITEMP    : 29.2 C Internal
ALARMDEL : Always
BATTV    : 13.6 Volts
LINEFREQ : 50.0 Hz
LASTXFER : Low line voltage
NUMXFERS : 1
XONBATT  : Wed Feb 06 21:37:34 GMT 2008
TONBATT  : 0 seconds
CUMONBATT: 55 seconds
XOFFBATT : Wed Feb 06 21:38:29 GMT 2008
SELFTEST : NO
STATFLAG : 0x07000008 Status Flag

```

Once you've done those checks and also checked the USB config that you probably have done already (see my post above and HOWTOs), things may start to work.

Failing that, try APC support.

---

### Post by Cato2 on 2008-02-09
I wanted my system to go into Hibernate mode (since ACPI works fine) during an extended power failure, at the point when the UPS battery runs out.  By default, apcupsd will simply shut down the system, losing any unsaved information.

It turns out this is quite simple to do.  

1. Check Hibernate is working by typing this to hibernate your system from the shell: ```
sudo /etc/acpi/hibernate.sh
``` 

2. (Optional) Turn off the screen lock on resume by editing /etc/default/apci-support to set LOCK_SCREEN=false

3.  Create hibernate script for use by apcupsd - create this in /usr/local/bin/hibernate as root:

```

#!/bin/bash
# Hibernate the system - designed to be called via symlink from /etc/apcupsd
# directory in case of apcupsd initiating a shutdown/reboot.  Can also be used
# interactively or from any script to cause a hibernate.

# Do the hibernate
/etc/acpi/hibernate.sh
# At this point system should be hibernated - when it comes back, we resume this script here

# On resume, tell controlling script (/etc/apcupsd/apccontrol) NOT to continue with default action (i.e. shutdown).
exit 99

```

4. Make this script executable
```
sudo chmod +x /usr/local/bin/hibernate
```

5.Create symbolic links from the /etc/apcupsd directory to the script - the result is the apcupd's apccontrol script, in this directory, will call the hibernate script instead of doing the default shutdown action for these operations.

```

sudo bash
cd /etc/apcupsd
ln -s /usr/local/bin/hibernate doreboot
ln -s /usr/local/bin/hibernate doshutdown
ln -s /usr/local/bin/hibernate emergency
ln -s /usr/local/bin/hibernate remotedown
ln -s /usr/local/bin/hibernate restartme

```

6. To test this, set TIMEOUT=20 in =/etc/apcupsd/apcupsd.conf= and then turn off the line/utility power to your UPS (remember to change back to TIMEOUT=0 after test) - after 20 seconds the hibernate should be started

In normal operation with TIMEOUT=0, your system will hibernate instead of shutdown, based on your normal apcupsd parameters.

How the script works - since it does exit 99 the hibernate replaces the default action of shutdown.

Kudos to the apcupsd developers for creating a nice program to handle the UPS and a  flexible way of doing this without having to edit the main apcupsd scripts.  Although it would be nice if this could be supported more seamlessly with a couple of config file options....

One other hint: if you'd like a GUI for your APC UPS like on Windows, just install gapcmon from the Ubuntu repositories - enable the default line that monitors localhost on the default port, and you will see that it tracks your UPS state in a graphical way including a handy graph and a full log of all power events.

---

### Post by zzmegad on 2008-02-22
Thanks to everyone for the good info.  I got my ups running great except I can't get it to restart when power is restored.

I followed the directions to uncomment line10 at 
[https://help.ubuntu.com/community/apcupsd](https://help.ubuntu.com/community/apcupsd)  

it says something like mount: can't find /usr in /etc/fstab or /etc/mtab in the last seconds before shutting down

then a few lines down it says wall:cant open temporary file

any ideas? using ubuntu server 7.10

---

### Post by Cato2 on 2008-02-23
Glad it's working except for this issue.

I think the wiki part about uncommenting line 10 is bogus (now fixed) - in the default Ubuntu setup there is no separate /usr filesystem mount, so mount -n -o ro /usr  will always fail.  Check the output of ```
mount -t ext3
``` - if there is no /usr line that comment is not relevant - but if there is, it is important.

Key question is what's stopping your startup on power on - have a look at the main apcupsd manual online as I think it has tips on how to configure BIOS etc as well.  Did you also remove the '-p' option from /etc/halt as pert that page?

The wall issue is a known one from Debian - apcupsd should be writing messages to all text console users via wall(1) but it's broken in both Debian and Ubuntu apparently.  For a single user system this doesn't matter too much, and there are other ways of alerting users in more complex setups.

---

### Post by Stretsh on 2008-02-29
Hey Cato2,

Thanks for the hibernate workaround. This help me make sure I don't lose important information when there's a blackout when I'm not around.

However, this may still need some tweaking. Maybe I'm missing something, but the following happens:

After I remove the power cord from the wall outlet, my system hibernates normally. 

I then want my system to come back online when the power is restored, in my test case, when I plug the cord back in. But that doesn't happen. I need to turn off the UPS first and then back on, then the system automatically starts.

After boot, *apcaccess status* reports the status of my UPS as SHUTTING DOWN. gapcmon also reports that status, but does show the graph correctly. To get it back to ONLINE I restart apcupsd.

---

### Post by tgalati4 on 2008-02-29
Depending on the features of your UPS, apcupsd can either shut the UPS down after computer shutdown, or it can leave the UPS running.  The downside of leaving it running is that it will get hit with a power spike when power returns.  The upside of leaving it on is that it provides standby power to your motherboard and thus you can come out of hibernate when power returns.

You have to weigh your risks and choose to either have apcupsd turn off the UPS or leave it on after power loss and successful shutdown.

---

### Post by Cato2 on 2008-03-02
Have you already done the "remove -p flag from within /etc/init.d halt" script mentioned on the apcupsd wiki page linked above?  If that's done I don't have any more suggestions - try APC support and/or the apcupsd mailing list.  The APCUPSD manual is also well worth reading, it's very informative.

---

### Post by jhorto1 on 2008-03-15
> **jacrider said:**
> I finally resolved this.

First, I have gone back to apcupsd.  I downloaded, compiled and installed the latest version of the application found on [www.apcupsd.com](www.apcupsd.com) and the version is 3.12.2.

To compile I was required to add the option --enable-usb to ensure the proper support.

   $./compile --enable-usb

Then:

   $ make

Followed by:

   $ sudo make install


Then I had to set the following options in the apcupsd.conf file:
   UPSCABLE usb
   UPSTYPE usb
   DEVICE 

and you need to ensure the following in the .conf file are also:

   NETSERVER on
   NISPORT 3551

Then, save everything and

   $ sudo apcupsd start.

To check status, do

   $ sudo apcaccess status

Great to have this done.

Andrew.

When I check the status, I get:

$ sudo apcaccess status
Error contacting host localhost port 6543: Connection refused

I changed the line in the .conf file to reflect NISPORT 3551 as described above and followed the other directions to the letter (aside from switching compile to configure) and no luck.

Even though the original .conf file had a different NISPORT setting originally, it states:

# NISPORT <port> default is 3551 as registered with the IANA
#  port to use for sending STATUS and EVENTS data over the network.
#  It is not used unless NETSERVER is on. If you change this port,
#  you will need to change the corresponding value in the cgi directory
#  and rebuild the cgi programs.

NISPORT 3551

Strange that it says the default is already 3551 but I had to change it to 3551.
I couldn't find a cgi directory, so I couldn't confirm that a corresponding value matched 3551.
Could this be the problem.

I'm fairly new to linux and would appreciate some expert advice.

Thank you, in advance.

Jim

---

### Post by Cato2 on 2008-03-16
Jim,

It's not clear what you have changed from the default config - I'm using Feisty 7.04 and didn't have to change those lines, which look like this:

```
NETSERVER on
NISIP 127.0.0.1
NISPORT 3551

```

The apcaccess status command works fine for me.  If you just want a basic UPS setup with a USB-connected UPS, you should be able to just use my post of 6th February 2008 - follow the steps there and you should be OK.  In particular, be sure to start the apcupsd daemon (like a Windows service) using the command:
```
/etc/init.d/apcupsd start
```

The post you have quoted is a more advanced setup - you should not need to compile anything to get apcupsd working these days, at least in Ubuntu 7.04 Feisty and I would expect the same in Gutsy (Ubuntu 7.10).

Hope this helps.

---

### Post by dasbooter on 2008-03-31
Hey jorto I had similiar problem but after restart I have it working```
APC      : 001,037,0907
DATE     : Mon Mar 31 15:34:56 CDT 2008
HOSTNAME : fatman
RELEASE  : 3.14.1
VERSION  : 3.14.1 (04 May 2007) debian
UPSNAME  : fatman
CABLE    : USB Cable
MODEL    : Back-UPS XS 1500 LCD 
UPSMODE  : Stand Alone
STARTTIME: Mon Mar 31 15:33:52 CDT 2008
STATUS   : ONLINE 
LINEV    : 118.0 Volts
LOADPCT  :   0.0 Percent Load Capacity
BCHARGE  : 100.0 Percent
TIMELEFT : 785.0 Minutes
MBATTCHG : 5 Percent
MINTIMEL : 3 Minutes
MAXTIME  : 0 Seconds
SENSE    : Medium
LOTRANS  : 088.0 Volts
HITRANS  : 139.0 Volts
ALARMDEL : Always
BATTV    : 26.5 Volts
LASTXFER : No transfers since turnon
NUMXFERS : 0
TONBATT  : 0 seconds
CUMONBATT: 0 seconds
XOFFBATT : N/A
SELFTEST : NO
STATFLAG : 0x07000008 Status Flag
MANDATE  : 2007-11-18
SERIALNO : 8B0746R40983  
BATTDATE : 2072-00-37
NOMINV   : 120
NOMBATTV :  24.0
FIRMWARE : 837.H7 .D USB FW:H7
APCMODEL : Back-UPS XS 1500 LC
END APC  : Mon Mar 31 15:35:30 CDT 2008

```

I havent tested yet though I used the feb "somethin" 2008 mentioned above. I used packages from the repository but there is a newer version than even the one u tried I think. I am not sure that compiling your own would be the problem sometimes newer versions have fixes and the history revision lists a problem with hal that may be fixed.

Hmm can you just simulate a shutdown by sending a command to the ups or is that something only smart models do and is there a way to clear the events.

---

### Post by looping_richard on 2008-04-02
Hello all,
I have been fighting with this thing for more than a week now, and still dont think its working reliably.

Or maybe I should say:
I am not in total control of the process ... ;)

I installed the packages for APC UPS with Synaptic: apcupsd, apcupsd-cgi, apcupsd-doc, and gapcmon.

The first time I connected the USB cable, it didnt want to work at all. I tried to start the daemon, but never got connected. (Connection refused)

I fumbled around with the cable, rebooted, tried to restart the deamon, but no luck.

After some more fiddling it suddenly worked. I dont know how I did that.

One restart later, it stopped working. I could not get the daemon running again, and only got connection refused from 
sudo apcaccess status

So... I left it there. Went back some days later. Connected the cable. Daemon no starti. Went home, connected with VNC... no starti.
Fumbled around with the power settings in "Preferences" -> "Power management" and switched on "always display an icon" on the general tab. 
This gave me a very nice battery icon, with.... surprise: the UPS description! My goodness. Where did that come from?


Immediately went to the shell, and now the APCUPSD starts.
And 
sudo apcaccess status gives all info I ever wanted. Also gapcmon is working.

Hm. Will it still work after a reboot?
I dont know.

How to make the server start automatically and reliably?
Can I not just make the computer treat the UPS like a battery in a laptop? Then I  can just set it to switch off if the battery goes low. This is how it works on Windows too BTW.

I'll try some more. 

Anyone have an idea?

Thanks,
Richard.

---

### Post by looping_richard on 2008-04-02
> **looping_richard said:**
> 

Can I not just make the computer treat the UPS like a battery in a laptop?



Well.... I think just a reboot made it happen. I now have a "On UPS Power" tab in Power management.
:-)

Me = happy.
:)

Not sure if I need all the other tools like APCUPSD anymore.

Richard.

---

### Post by dasbooter on 2008-04-02
[SIZE="4"][COLOR="Red"]errrr....ummmm quoting myself ...did ya read my post ;)[/COLOR][/SIZE]

> **dasbooter said:**
> Hey jorto I had similiar problem but after restart I have it working

---

### Post by tgalati4 on 2008-04-03
The best metric is simply yanking the power cord out of the wall and use a stop watch to time how quickly your system shuts down.  This problem could be a USB compatibility between a high-speed USB 2.0 port and the slower APC 1.0 port.  I recall reading that sometimes the port will not communicate properly.  You can try different cables, or putting a 4-in-one hub to slow down the communication between the computer and the UPS.

You could bypass the USB cable and use a special serial cable (or one you make yourself).  I've had reliable service using serial communication.

I would be concerned that the UPS wouldn't respond reliably when you need it.  Yank the cord 10 times.  If you get 10 successful shutdowns, then you should be OK.

---

### Post by asnd16 on 2008-04-09
> **jacrider said:**
> I finally resolved this.

First, I have gone back to apcupsd.  I downloaded, compiled and installed the latest version of the application found on [www.apcupsd.com](www.apcupsd.com) and the version is 3.12.2.

To compile I was required to add the option --enable-usb to ensure the proper support.

   $./compile --enable-usb

Then:

   $ make

Followed by:

   $ sudo make install


Then I had to set the following options in the apcupsd.conf file:
   UPSCABLE usb
   UPSTYPE usb
   DEVICE 

and you need to ensure the following in the .conf file are also:

   NETSERVER on
   NISPORT 3551

Then, save everything and

   $ sudo apcupsd start.

To check status, do

   $ sudo apcaccess status

Great to have this done.

Andrew.

:guitar:  Sweet only I installed all three packages through synaptic then I went and had to edit the config file with your little addition and walla I skipped the netserver park cuz I dont think I run  a net server.   I am runny hardy and got the following output
I just plugged it in about 30 minutes ago
> moses@moses-liltravler:~$ sudo apcaccess status
APC      : 001,036,0908
DATE     : Wed Apr 09 13:36:23 MDT 2008
HOSTNAME : moses-liltravler
RELEASE  : 3.14.2
VERSION  : 3.14.2 (15 September 2007) debian
UPSNAME  : moses-liltravler
CABLE    : USB Cable
MODEL    : Back-UPS ES 350 
UPSMODE  : Stand Alone
STARTTIME: Wed Apr 09 13:36:22 MDT 2008
STATUS   : ONLINE 
LINEV    : 119.0 Volts
LOADPCT  :   0.0 Percent Load Capacity
BCHARGE  : 100.0 Percent
TIMELEFT :  36.4 Minutes
MBATTCHG : 5 Percent
MINTIMEL : 3 Minutes
MAXTIME  : 0 Seconds
SENSE    : High
LOTRANS  : 088.0 Volts
HITRANS  : 139.0 Volts
ALARMDEL : Always
BATTV    : 13.4 Volts
LASTXFER : No transfers since turnon
NUMXFERS : 0
TONBATT  : 0 seconds
CUMONBATT: 0 seconds
XOFFBATT : N/A
STATFLAG : 0x07000008 Status Flag
MANDATE  : 2007-10-31
SERIALNO : 3B0744X11233  
BATTDATE : 2000-00-00
NOMINV   : 120
NOMBATTV :  12.0
FIRMWARE : 823.B1.D USB FW:B1
APCMODEL : Back-UPS ES 350 
END APC  : Wed Apr 09 13:36:57 MDT 2008


---

### Post by looping_richard on 2008-04-15
> **dasbooter said:**
> [SIZE="4"][COLOR="Red"]errrr....ummmm quoting myself ...did ya read my post ;)[/COLOR][/SIZE]

Hi,
Oh yes, I have read all posts I could find on the APCUPSD .
The problem is that even after the reboots I did, I could not get the deamon to work.

I do not know what DID make it work... and there is my problem. 

Richard.

---

### Post by strikegun on 2008-07-03
hi,
does any one has a ES 550 and got anything unter the UPS load?
It shows me here just 0.0 %
I saw from someone who got a ES 700 where it shows the UPS load.
Doesn't the ES550 got these feature?

---

### Post by dgermann on 2008-07-05
Hi--

Have a new APCUPSD ES 550 connected to my 7.10 box.

Cannot seem to get apcupsd to see the UPS. For instance:
```
sudo apcaccess status
[sudo] password for doug:
Sat Jul 05 11:02:15 EDT 2008  apcaccess: Bogus configuration value (*invalid-cable*)
apcaccess: Bogus configuration value (*invalid-cable*)
Sat Jul 05 11:02:15 EDT 2008  apcaccess: Bogus configuration value (*invalid-ups-type*)
apcaccess: Bogus configuration value (*invalid-ups-type*)
Terminating due to configuration file errors.

```

In addition, I have received this error from gapcmon: "unknown@localhost is NISERR NIS network error...&#8221;

When I point my browser to 124.0.0.1:5331 it reports "unable to connect."

Power Manager can see it, and when I unplug the usb cable, it cannot, so I am guessing my physical connection is good.

I have followed [https://help.ubuntu.com/community/apcupsd]("https://help.ubuntu.com/community/apcupsd") as my guide.

Here is my apcupsd.conf file (its permissions are 644--is that right? I just tried changing it to 777 and that made no difference, still doesn't see it and gives error "invalid-ups-type"):
```
## apcupsd.conf v1.1 ##
# 
#  for apcupsd release 3.14.1 (04 May 2007) - debian
#
# "apcupsd" POSIX config file

#
# ========= General configuration parameters ============
#

# UPSNAME xxx
#   Use this to give your UPS a name in log files and such. This
#   is particulary useful if you have multiple UPSes. This does not
#   set the EEPROM. It should be 8 characters or less.
#UPSNAME

# UPSCABLE <cable>
#   Defines the type of cable connecting the UPS to your computer.
#
#   Possible generic choices for <cable> are:
#     simple, smart, ether, usb
#
#   Or a specific cable model number may be used:
#     940-0119A, 940-0127A, 940-0128A, 940-0020B,
#     940-0020C, 940-0023A, 940-0024B, 940-0024C,
#     940-1524C, 940-0024G, 940-0095A, 940-0095B,
#     940-0095C, M-04-02-2000
#
# UPSCABLE smart
UPSCABLE usb

# To get apcupsd to work, in addition to defining the cable
# above, you must also define a UPSTYPE, which corresponds to
# the type of UPS you have (see the Description for more details).
# You must also specify a DEVICE, sometimes referred to as a port.
# For USB UPSes, please leave the DEVICE directive blank. For
# other UPS types, you must specify an appropriate port or address.
#
# UPSTYPE   DEVICE           Description
# apcsmart  /dev/tty**       Newer serial character device,
#                            appropriate for SmartUPS models using
#                            a serial cable (not USB).
#
# usb       <BLANK>          Most new UPSes are USB. A blank DEVICE
#                            setting enables autodetection, which is
#                            the best choice for most installations.
#
# net       hostname:port    Network link to a master apcupsd
#                            through apcupsd's Network Information
#                            Server. This is used if you don't have
#                            a UPS directly connected to your computer.
#
# snmp      hostname:port:vendor:community
#                            SNMP Network link to an SNMP-enabled
#                            UPS device. Vendor is the MIB used by
#                            the UPS device: can be "APC", "APC_NOTRAP"
#                            or "RFC" where APC is the powernet MIB,
#                            "APC_NOTRAP" is powernet with SNMP trap
#                            catching disabled, and RFC is the IETF's 
#                            rfc1628 UPS-MIB. You usually want "APC".
#                            Port is usually 161. Community is usually
#                            "private".
#
# dumb      /dev/tty**       Old serial character device for use 
#                            with simple-signaling UPSes.
#
# pcnet    ipaddr:username:passphrase
#                            PowerChute Network Shutdown protocol
#                            which can be used as an alternative to SNMP
#                            with AP9617 family of smart slot cards.
#                            ipaddr is the IP address of the UPS mgmt
#                            card. username and passphrase are the
#                            credentials for which the card has been
#                            configured.
#
# UPSTYPE apcsmart
# DEVICE /dev/ttyS0
UPSTYPE usb
# DEVICE 

# LOCKFILE <path to lockfile>
#   Path for device lock file. Not used on Win32.
LOCKFILE /var/lock

# SCRIPTDIR <path to script directory>
#   Directory in which apccontrol and event scripts are located.
SCRIPTDIR /etc/apcupsd

# PWRFAILDIR <path to powerfail directory>
#   Directory in which to write the powerfail flag file. This file
#   is created when apcupsd initiates a system shutdown and is
#   checked in the OS halt scripts to determine if a killpower
#   (turning off UPS output power) is required.
PWRFAILDIR /etc/apcupsd

# NOLOGINDIR <path to nologin directory>
#   Directory in which to write the nologin file. The existence
#   of this flag file tells the OS to disallow new logins.
NOLOGINDIR /etc


#
# ======== Configuration parameters used during power failures ==========
#

# The ONBATTERYDELAY is the time in seconds from when a power failure
#   is detected until we react to it with an onbattery event.
#
#   This means that, apccontrol will be called with the powerout argument
#   immediately when a power failure is detected.  However, the
#   onbattery argument is passed to apccontrol only after the 
#   ONBATTERYDELAY time.  If you don't want to be annoyed by short
#   powerfailures, make sure that apccontrol powerout does nothing
#   i.e. comment out the wall.
ONBATTERYDELAY 6

# 
# Note: BATTERYLEVEL, MINUTES, and TIMEOUT work in conjunction, so
# the first that occurs will cause the initation of a shutdown.
#

# If during a power failure, the remaining battery percentage
# (as reported by the UPS) is below or equal to BATTERYLEVEL, 
# apcupsd will initiate a system shutdown.
BATTERYLEVEL 5

# If during a power failure, the remaining runtime in minutes 
# (as calculated internally by the UPS) is below or equal to MINUTES,
# apcupsd, will initiate a system shutdown.
MINUTES 3

# If during a power failure, the UPS has run on batteries for TIMEOUT
# many seconds or longer, apcupsd will initiate a system shutdown.
# A value of 0 disables this timer.
#
#  Note, if you have a Smart UPS, you will most likely want to disable
#    this timer by setting it to zero. That way, you UPS will continue
#    on batteries until either the % charge remaing drops to or below BATTERYLEVEL,
#    or the remaining battery runtime drops to or below MINUTES.  Of course,
#    if you are testing, setting this to 60 causes a quick system shutdown
#    if you pull the power plug.   
#  If you have an older dumb UPS, you will want to set this to less than
#    the time you know you can run on batteries.
TIMEOUT 0

#  Time in seconds between annoying users to signoff prior to
#  system shutdown. 0 disables.
ANNOY 300

# Initial delay after power failure before warning users to get
# off the system.
ANNOYDELAY 60

# The condition which determines when users are prevented from
# logging in during a power failure.
# NOLOGON <string> [ disable | timeout | percent | minutes | always ]
NOLOGON disable

# If KILLDELAY is non-zero, apcupsd will continue running after a
# shutdown has been requested, and after the specified time in
# seconds attempt to kill the power. This is for use on systems
# where apcupsd cannot regain control after a shutdown.
# KILLDELAY <seconds>  0 disables
KILLDELAY 0

#
# ==== Configuration statements for Network Information Server ====
#

# NETSERVER [ on | off ] on enables, off disables the network
#  information server. If netstatus is on, a network information
#  server process will be started for serving the STATUS and
#  EVENT data over the network (used by CGI programs).
NETSERVER on

# NISIP <dotted notation ip address>
#  IP address on which NIS server will listen for incoming connections.
#  This is useful if your server is multi-homed (has more than one
#  network interface and IP address). Default value is 0.0.0.0 which
#  means any incoming request will be serviced. Alternatively, you can
#  configure this setting to any specific IP address of your server and 
#  NIS will listen for connections only on that interface. Use the
#  loopback address (127.0.0.1) to accept connections only from the
#  local machine.
NISIP 127.0.0.1

# NISPORT <port> default is 3551 as registered with the IANA
#  port to use for sending STATUS and EVENTS data over the network.
#  It is not used unless NETSERVER is on. If you change this port,
#  you will need to change the corresponding value in the cgi directory
#  and rebuild the cgi programs.
NISPORT 3551

# If you want the last few EVENTS to be available over the network
# by the network information server, you must define an EVENTSFILE.
EVENTSFILE /var/log/apcupsd.events

# EVENTSFILEMAX <kilobytes>
#  By default, the size of the EVENTSFILE will be not be allowed to exceed
#  10 kilobytes.  When the file grows beyond this limit, older EVENTS will
#  be removed from the beginning of the file (first in first out).  The
#  parameter EVENTSFILEMAX can be set to a different kilobyte value, or set
#  to zero to allow the EVENTSFILE to grow without limit.
EVENTSFILEMAX 10

#
# ========== Configuration statements used if sharing =============
#            a UPS with more than one machine

# NETTIME <int>
#   Interval (in seconds) at which the NIS client polls the server.
#   Used only when this apcupsd is a network client (UPSTYPE net).
#NETTIME 60

#
# Remaining items are for ShareUPS (APC expansion card) ONLY
#

# UPSCLASS [ standalone | shareslave | sharemaster ]
#   Normally standalone unless you share an UPS using an APC ShareUPS
#   card.
UPSCLASS standalone

# UPSMODE [ disable | share ]
#   Normally disable unless you share an UPS using an APC ShareUPS card.
UPSMODE disable

#
# ===== Configuration statements to control apcupsd system logging ========
#

# Time interval in seconds between writing the STATUS file; 0 disables
STATTIME 0

# Location of STATUS file (written to only if STATTIME is non-zero)
STATFILE /var/log/apcupsd.status

# LOGSTATS [ on | off ] on enables, off disables
# Note! This generates a lot of output, so if         
#       you turn this on, be sure that the
#       file defined in syslog.conf for LOG_NOTICE is a named pipe.
#  You probably do not want this on.
LOGSTATS off

# Time interval in seconds between writing the DATA records to
#   the log file. 0 disables.
DATATIME 0

# FACILITY defines the logging facility (class) for logging to syslog. 
#          If not specified, it defaults to "daemon". This is useful 
#          if you want to separate the data logged by apcupsd from other
#          programs.
#FACILITY DAEMON

#
# ========== Configuration statements used in updating the UPS EPROM =========
#

#
# These statements are used only by apctest when choosing "Set EEPROM with conf
# file values" from the EEPROM menu. THESE STATEMENTS HAVE NO EFFECT ON APCUPSD.
#

# UPS name, max 8 characters 
#UPSNAME UPS_IDEN

# Battery date - 8 characters
#BATTDATE mm/dd/yy

# Sensitivity to line voltage quality (H cause faster transfer to batteries)  
# SENSITIVITY H M L        (default = H)
#SENSITIVITY H

# UPS delay after power return (seconds)
# WAKEUP 000 060 180 300   (default = 0)
#WAKEUP 60

# UPS Grace period after request to power off (seconds)
# SLEEP 020 180 300 600    (default = 20)
#SLEEP 180

# Low line voltage causing transfer to batteries
# The permitted values depend on your model as defined by last letter 
#  of FIRMWARE or APCMODEL. Some representative values are:
#    D 106 103 100 097
#    M 177 172 168 182
#    A 092 090 088 086
#    I 208 204 200 196     (default = 0 => not valid)
#LOTRANSFER  208

# High line voltage causing transfer to batteries
# The permitted values depend on your model as defined by last letter 
#  of FIRMWARE or APCMODEL. Some representative values are:
#    D 127 130 133 136
#    M 229 234 239 224
#    A 108 110 112 114
#    I 253 257 261 265     (default = 0 => not valid)
#HITRANSFER 253

# Battery charge needed to restore power
# RETURNCHARGE 00 15 50 90 (default = 15)
#RETURNCHARGE 15

# Alarm delay 
# 0 = zero delay after pwr fail, T = power fail + 30 sec, L = low battery, N = never
# BEEPSTATE 0 T L N        (default = 0)
#BEEPSTATE T

# Low battery warning delay in minutes
# LOWBATT 02 05 07 10      (default = 02)
#LOWBATT 2

# UPS Output voltage when running on batteries
# The permitted values depend on your model as defined by last letter 
#  of FIRMWARE or APCMODEL. Some representative values are:
#    D 115
#    M 208
#    A 100
#    I 230 240 220 225     (default = 0 => not valid)
#OUTPUTVOLTS 230

# Self test interval in hours 336=2 weeks, 168=1 week, ON=at power on
# SELFTEST 336 168 ON OFF  (default = 336)
#SELFTEST 336
```

1. Do I even need APCUPSD? Will not Gnome Power Manager do everything, such as monitor the status and handle the shutdown of the computer? Am I just wasting my time with apcupsd?

2. If apcupsd is a good idea, what am I missing?

Thanks!

---

### Post by dgermann on 2008-07-05
OK--

I seem to have solved some of my own problem. I will leave the original post up in case someone else has the same issues.

In two places in my original apcupsd.conf file I had originally entered the cable type as "ups" instead of "usb."

Second, after I corrected that, I ran  sudo /etc/init.d/apcupsd start

Then everything seemed to work. 

Except...

I cannot get the web interface to work. I go to 127.0.0.1:3551 and I get problem loading page the connection was reset.

Any help with that?

Thanks!

---

### Post by strikegun on 2008-07-07
The webinterface work for me over 3 cgi scripts.
I can go to [http://127.0.0.1/cgi-bin/upsstats.cgi?host=127.0.0.1&temp=C](http://127.0.0.1/cgi-bin/upsstats.cgi?host=127.0.0.1&temp=C)

The 3551 port isn't it just the communication port?

Did you install the apcupsd over ubuntu sources? then look for the apcupsd-cgi package, else look in the sources for cgi-files and copy them to your apache-CGI dir.

BTW for my issue the the UPS Load.
The Load Value changes when the UPS works on battery. Then it remembers the value it had.
So plug the System to the UPS, and run on battery. After that it shows the load. Running on DC back, it keeps the value, even if there is more.

---

### Post by dgermann on 2008-07-07
strikegun--

Many thanks.

That address you suggested did not work for me either. How did you ever come up with that string?

You mention Apache--is it necessary to have Apache installed for the cgi stuff to work? If so, that is the problem because I do not have apache.

Yes, I installed using synaptic. I did install apcupsd-cgi.

Thanks, strikegun!

---

### Post by strikegun on 2008-07-08
you got it.
these cgi files are like html files, you need a apache for it. You can install it over synaptic aswell.
The string I got out of my browser. And if you installed it all like me, over synaptic, then it should be the same.

What you can also do is, compile the newest version of apcupsd for your self and there is the GAPCMON GUI monitoring tool included. With that you can run it on your gnome. But if you have a just console System without a windowmanager that is no help, or?

---

### Post by dgermann on 2008-07-08
strikegun--

Thanks!

Actually I installed gapcmon via synaptic on 7.10, and that works well.

I think I'll forego apache for now, just to save space and bloat.

Thanks for helping with this, strikegun.

---

