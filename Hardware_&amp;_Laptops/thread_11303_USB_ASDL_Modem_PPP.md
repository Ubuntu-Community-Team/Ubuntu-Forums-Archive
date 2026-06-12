---
title: "USB ASDL Modem PPP"
date: 2005-01-15
forum: Hardware &amp; Laptops
---

### Post by sztosz on 2005-01-15
Hi,

recently Ubunt had been delivered by the post to me :D , I installed it, works great (and fast  =D>  ) but I have a huge, for me, problem with my Thomson Speedtouch 330 USB ASDL modem. When I try to establish connection via. PPP I'm asked for phone numbers, but I didn't get any from my ISP. I can't enter  "*" which I was told to enter after a short talk with them. And there is no net.

I also tried "program" (a bash with drivers and firmware) that worked fine with Mandrake 10.0 and RH 9.0. But there is info that I cannot establish connection now. But don't say why. The files provided by my ISP were working with other distros but when I try that in Ubunto it says that there is problem with the USB. Trying to figure it out I only managed that I don't have usb-ohcpi (if I didn't screw that name  :confused: )

Please help me, I'm total Newbie to Linux, I don't realy know where to look for the solution. And I want to thank for any replies that will occur here.

---

### Post by hardcandy on 2005-01-16
PPP is used for dialup modems. PPPoE and PPPoA is used for dsl modems. 
Unplug and replug the modem with Ubuntu booted up. Then look in the device manager and see if the modem is listed. If it is then "sudo pppoeconf". See if that works.

---

### Post by sztosz on 2005-01-16
The Device Manager sees my Modem, I even managed somehow to connect to the internet, but every time I want to start the conection It says:
```
Starting ADSL connection:FATAL: Module usb_ohci not found.
```
I have to use installing script wich somehow allow me to connect.

When I used "pppoeconf" it sasy that no interface was found, and ask me to run modconf. Running modconf gives that text ```
/usr/sbin/pppoeconf: line 309: modconf: command not found
```

I have no future Idea how to deal with it.

---

### Post by hardcandy on 2005-01-16
Try 'modprobe ohci-hcd" and see if that lets the modem work.

---

### Post by sztosz on 2005-01-16
Me again

modprobe ohci-hcd did not return any error, I assumed it's allright. after some thinking and doing a litle research I managed to do this:

1. Downloaded package from there: [http://sourceforge.net/project/showfiles.php?group_id=68502](http://sourceforge.net/project/showfiles.php?group_id=68502) 


2. Repleaced in speedtouchconf.sh lines:
```
mount none /proc/bus/usb -t usbdevfs > /dev/null 2>&1
if [ "$USB_TYPE" == "UHCI" ]; then
  USB_INTERFACE=usb-uhci
  modprobe usb-uhci | tee -a $LOGFILE
  if [ "$?" -ne "0" ]; then
    USB_INTERFACE=uhci
    modprobe uhci  | tee -a $LOGFILE
  fi
else
  modprobe **usb-ohci** | tee -a $LOGFILE
  USB_INTERFACE=**usb-ohci**
fi

``` 
With those lines:
```
mount none /proc/bus/usb -t usbdevfs > /dev/null 2>&1
if [ "$USB_TYPE" == "UHCI" ]; then
  USB_INTERFACE=usb-uhci
  modprobe usb-uhci | tee -a $LOGFILE
  if [ "$?" -ne "0" ]; then
    USB_INTERFACE=uhci
    modprobe uhci  | tee -a $LOGFILE
  fi
else

  modprobe **ohci-hcd** | tee -a $LOGFILE
  USB_INTERFACE=**ohci-hcd**
fi
```

3. Runned the script, without any errors 

Now I chek How it is after reboot.

It works :D

Great Thanks to: **hardcandy**. He gives me hint's I realy needed

There is another problem though:

When I ran script first I got:
```
If you have any problems with this script, mail me
(steve at steve-parker dot org) with the files
/tmp/speedtouch.txt and /var/log/messages for diagnosis.
Using speedtouch-1.3-sgp
microcode is KQD6_R204.zip
PPP version 2.4.2 okay.
Linux kernel version 2.6.8 okay.
ls: /dev/ppp: No such file or directory
ls: /dev/ppp: No such file or directory
/dev/ppp cannot be created, or is not device 108
Not ready to install the software at this time. - code 32
```

When I tried to:
```
cd /dev
./MAKEDEV ppp

```
No error where returned but ppp was not created :)

After litle while I ran: Computer -> System Configuration -> Network configuration (I think that's the name, Names are in polish)
Then I added new connection with random content (numbers, usenames and passwords)
It worked, there were no connection but /dev/ppp was created. Then I ran script, it was okay.

BUT:

When I shoot down the Ubuntu I get:```

Shooting down ASDL connection: FATAL: usbcore in use
```

And when Iboot Ubunt I have to wait until computer is connected to the internet, it stops for ~30 seconds trying to connect.

---

### Post by mezzyhandz on 2005-01-19
Hi stosz,

Im having a similar problem as yours, and i followed the steps that you had posted above, but i could not successfully connect my alcatel speedtouch.

When i ran Steve Parker's script, i had a similar, but not exactly the same error as yours:

```
If you have any problems with this script, mail me
(steve at steve-parker dot org) with the files
/tmp/speedtouch.txt and /var/log/messages for diagnosis.
Using speedtouch-1.3-sgp
microcode is KQD6_R204.zip
PPP version 2.4.2 okay.
Linux kernel version 2.6.8 okay.
/dev/ppp cannot be created, or is not device 108
Not ready to install the software at this time. - code 32
``` 

Note that 'ls: /dev/ppp: No such file or directory' is not present in my error.

Could that be why your method isnt workng for me? 
Please advise.  :-(

---

### Post by sztosz on 2005-01-19
So you have device "ppp" in "/dev/' ? Somethimg like /dev/ppp? Well then try to use bulit in to Ubuntu connection manager and make PPP conection with random content. Maybe this will help? Well i don't have no more ideas :( Ubuntu was most problematic Distribution I met, and there is no KDE :(

Try to edit the script, and comment out lines that check if there is /dev/ppp.

I'll think about this at the weekend, now I have too much school on my mind :(

---

### Post by mezzyhandz on 2005-01-19
Hi!

Yes i have made a directory in /dev so it is /dev/ppp. Yea i tried the connection manager thing as well, but didnt work. However, your idea of commenting the lines that check /dev/ppp worked!

Heres what i commented in speedtouchconf.sh:
```
 #  ls -l /dev/ppp|grep -wq 108 
#  if [ "$?" -ne "0" ]; then
#    cd /dev
#    ./MAKEDEV ppp
#    if [ "$?" -ne "0" ]; then
#      echo $"MAKEDEV failed" | tee -a $LOGFILE
#      error=`expr $error + 16`
#    fi
#  fi
#  ls -l /dev/ppp|grep -wq 108 
#  if [ "$?" -ne "0" ]; then
#    echo $"/dev/ppp cannot be created, or is not device 108"
#    error=`expr $error + 32`
#  fi

```

So i got as far as configuring my settings for my ISP, and it even loaded the microcode onto my modem, but just before that...while it was Creating ppp files in //etc/ppp, an error occured.
And the end reult was to display an error that the ppp kernel module cudnt be loaded.

Here is the full log:
```

************************************************
*                                              *
*       speedtouchconf.sh by Steve Parker      *
*                                              *
*    http://speedtouchconf.sourceforge.net/    *
* based on speedtouch.sourceforge.net project  *
*                                              *
************************************************

If you have any problems with this script, mail me
(steve at steve-parker dot org) with the files
/tmp/speedtouch.txt and /var/log/messages for diagnosis.
Using speedtouch-1.3-sgp
The kernel speedtch module is loaded. This is not
compatible with the speedtouch usermode driver.
Removing the speedtch module
microcode is KQD6_R204.zip
  PPP version 2.4.2 okay.
  Linux kernel version 2.6.8 okay.
*******************************************
*                                         *
*     Please select your ISP Settings     *
*                                         *
*******************************************

  Country/ISP           VPI    VCI
  Belgium, ?              8     35
  Denmark, Orang          8     35
  France, wanado          8     35
  France, ?               8     67
  Italy, ?                8     35
  Netherlands, ?          8     48
  Netherlands             0     35
  Poland (NeoStrada)      0     35
  UK, Any                 0     38
  US, BellSouth           8     35
  Singapore Pacificnet    0    100
Please type your VPI VCI numbers (eg, 0 38 for UK)
8 35
Please enter your ISP Login ID (eg another@hg1.btinternet.com)
*hidden*
Please enter your ISP Password
*hidden*
Settings:
  VPI / VCI : 8 / 35
  Login     : *hidden*
  Password  : *hidden*
Are these correct? (Y/N)
y
No further user interaction is required.
Configuring SpeedTouch Driver...
Software Configuration - SUCCESS
Building SpeedTouch Driver...
Software Build - SUCCESS
Installing SpeedTouch Driver...
Software Installation - SUCCESS
Creating ppp files in //etc/ppp
FATAL: Module usb_uhci not found.

   *** Configuration finished. Starting the connection ***

The modem lights should start flashing for approx. 20 seconds...
The lights should both be solid green now.
Running : pppd call adsl
pppd: This system lacks kernel support for PPP.  This could be because
the PPP kernel module could not be loaded, or because PPP was not
included in the kernel configuration.  If PPP was included as a
module, try `/sbin/modprobe -v ppp'.  If that fails, check that
ppp.o exists in /lib/modules/`uname -r`/net.
See README.linux file in the ppp distribution for more details.

ppp0: error fetching interface information: Device not found
*********************************
* Don't seem to have connected. *
*********************************
Please check the username and password in /etc/ppp/*-secrets.
Also check the VPI/VCI in /etc/ppp/peers/adsl
Then run /etc/init.d/speedtouch start
Current settings: *hidden* /*hidden* / 8 / 35

```

Thanks for ur time. Its okay, i understand u can only look it up on the weekend. Im lucky i have hols :) just finished my exams! And yes, Ubuntu is by far the most problematic distribution.... But then again, its linux...it HAS to be problematic!  :D 
(Even getting this scipt to install in Mandrake 10 was a *bit* of a hassle for me)

Later!

---

### Post by Karlos on 2005-01-19
I have a speedtouch 330 (silver one) modem up and running AND firing up on boot.
It was a bitch to get working but I got there in the end
{

---

### Post by Karlos on 2005-01-19
I even e-mailed steve parker
}

i can explain roughly how I did it 

This is from the point of view of a fresh install..ok

first you need to apt-get gcc and g++ from the ubuntu cd

(not sure if you really need g++ but it seems to work if I do it like this)
(I have done this on 3 diferent machines now...with success)

then..
make a directory called usr/local/lib/speedtouch

$ sudo mkdir /usr/local/lib/speedtouch

then..

$ sudo gedit /etc/modules

..in here add the line

pppoatm

<hit save>

I HAVE FOUND THAT THE WHOLE THING SEEMS TO WORK BETTER IF I RE-BOOT THE MACHINE AT THIS POINT...DUNNO WHY...JUST WORKS

once rebooted run the speedtouchconf script again ( I do this bit in /tmp)

(if your using the silver 330 you need the "rev4fw.zip" fimware)

If you manage to connect successfully then good for you hooraaa

..say yes when it asks you about the connecting on reboot sorta blurb at the end

next..do this..

$ sudo gedit /etc/speedtouch.conf

..in here you have to change 2 settings

change LOAD_USBCORE=1  to  LOAD_USBCORE=0

and

change LOAD_USBINTERFACE=1  to  LOAD_USBINTERFACE=0

<hit save>

That should make it fire up on boot

That's basically what I do and it seems to work quite well....

...hope this helps..Karlos

---

### Post by mezzyhandz on 2005-01-20
Yipeeeeeeeeee! Thank u SO much karlos, it works! U da man :D

Im going to save ur mini HOWTO for future reference :) thanks for the help dude.

-mezzyhandz

---

### Post by sztosz on 2005-01-23
[QUOTE=mezzyhandz]Yipeeeeeeeeee! Thank u SO much karlos, it works! U da man :D

Im going to save ur mini HOWTO for future reference :) thanks for the help dude.

-mezzyhandz[/QUOTE]
 Well I wanted to post here that I didn't found solution for you mezzyhandz but since it is solved i just wish you all good luck.

---

