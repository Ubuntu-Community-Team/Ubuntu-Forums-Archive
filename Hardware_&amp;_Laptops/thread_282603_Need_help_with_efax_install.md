---
title: "Need help with efax install"
date: 2006-10-23
forum: Hardware &amp; Laptops
---

### Post by kent41 on 2006-10-23
Hi all

I am trying to send a FAX in Breezy  5.10

I have installed efax and efax-gtk and I have followed some of the [post ]("http://www.ubuntuforums.org/showthread.php?t=234456&highlight=efax-gtk")for the install.

However when I try to send a fax from oo I get the following message:
```

Socket running on port 9900
Print job received on socket
efax-0.9a: 44:15 opened /dev/ttyS1
efax-0.9a: 44:15 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 44:15 failed -> /home/kent/efax-gtk-server/efax-gtk-server-YQsDd5.001
efax-0.9a: 44:15 Error: fax device write: Input/output error
efax-0.9a: 44:17 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 44:19 Error: fax device write: Input/output error
efax-0.9a: 44:21 sync: dropping DTR
efax-0.9a: 44:21 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 44:21 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 44:21 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 44:23 Error: fax device write: Input/output error
efax-0.9a: 44:25 sync: sending escapes
efax-0.9a: 44:25 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 44:25 Error: fax device write: Input/output error
efax-0.9a: 44:25 Error: fax device write: Input/output error
efax-0.9a: 44:25 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 44:25 Error: fax device write: Input/output error
efax-0.9a: 44:25 Error: fax device write: Input/output error
efax-0.9a: 44:27 Error: fax device write: Input/output error
efax-0.9a: 44:29 Error: fax device write: Input/output error
efax-0.9a: 44:31 Error: sync: modem not responding
efax-0.9a: 44:31 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 44:31 done, returning 2 (unrecoverable error)
```

Do I neeed to init the modem     (8280 1DB/DBL/DBM (ICH4/ICH4-L/ICH4M) AC'AC97 Modem Controller which is internal)   or something?

One of the err is **modem not responding**
Is there someone who has installed xfax that can help me get this going?

Thanks

---

### Post by kent41 on 2006-10-23
UPDATE:
:-D 
I am making progress I think.

I have progressed to the point where I am able to open efax-gtk GUI and attempt to send a FAX.

I do not get the errors listed in the previous post now.

What I mean is I can create a text file in oo then send it to the FAX cue then open the modem and DIAL out, and the phone at the other end rings but I do not hear any FAX hand shaking tones or other noise coming from my computer.

The modem just holds the connection open until I stop the Fax sending.

The following is the log I get from the fax trying to send.


```

Socket running on port 9900
Print job received on socket
efax-0.9a: 31:04 opened /dev/ttySL0
efax-0.9a: 31:06 using modem:1 in class 1
efax-0.9a: 31:06 dialing T7237511
efax-0.9a: 33:06 Error: dial command failed
efax-0.9a: 33:06 failed -> /home/kent/efax-gtk-server/efax-gtk-server-TsYl8j.001
efax-0.9a: 33:08 done, returning 2 (unrecoverable error)
```

Has anyone else gotten this far ?  Any ideas what I need to do next ?

---

### Post by kent41 on 2006-10-24
Since the GUI efax did not work I thought I would try the command line method. After making some changes to the file /etc/efax.rc I was able to start the efax program but I was only able to get the fax to dial out. the program never seemed to provide the hand shaking tones to the fax at the other end.

This is what the command line output looks like
```

kent@GPS-3:~$ sudo fax send 7459599 /home/kent/linux-test.ps
Password:
/home/kent/linux-test.ps.nnn is up-to-date
efax: Tue Oct 24 09:20:02 2006 efax v 0.9a-001114 Copyright 1999 Ed Casas
efax: 20:02 opened /dev/ttySL0
efax: 20:03 using modem:1 in class 1
efax: 20:03 dialing T7459599

```

Does anyone know what starts the hand shaking tones in the fax program?

---

### Post by kent41 on 2006-10-24
UPDATE;

When using the command line I was able to use the verbose switch to show was going on when I try to send a FAX using efax. I am not sure what is right or wrong with the info presented.

Hopefully someone will see something wrong.

The fax command starts out ok by finding the correct file to fax and then dials the phone number and the phone at the other end rings and answers but no tones are heard only silence.

As you will see ther are a lot of "response OK"

```
kent@GPS-3:~$ sudo fax -v send 2620989 /home/kent/abc.ps
/home/kent/abc.ps is postscript...
efax: Tue Oct 24 16:59:02 2006 efax v 0.9a-001114 Copyright 1999 Ed Casas
efax: 59:02 TIFF version 4.2 file (little-endian)
efax: 59:02 TIFF directory at 8 with 20 tags, last image.
efax: 59:02 page 1 : /home/kent/abc.ps.001 + 338 : 1728x2156 @ 204x196 dpi TIFF/FAX
efax: 59:02 argv[0]=efax
efax: 59:02 argv[1]=-v
efax: 59:02 argv[2]=chewmainrxtf
efax: 59:02 argv[3]=-v
efax: 59:02 argv[4]=chewmainrxtf
efax: 59:02 argv[5]=-d/dev/ttySL0
efax: 59:02 argv[6]=-x
efax: 59:02 argv[7]=/var/lock/LCK..ttySL0
efax: 59:02 argv[8]=-iZ
efax: 59:02 argv[9]=-i&FE&D2S7=120
efax: 59:02 argv[10]=-i&C0
efax: 59:02 argv[11]=-iM1L0
efax: 59:02 argv[12]=-l
efax: 59:02 argv[13]=+1 800 555 5555
efax: 59:02 argv[14]=-kZ
efax: 59:02 argv[15]=-h
efax: 59:02 argv[16]=2006/10/24 16:59 +1 800 555 5555 Put Your Name Here p. %d/%d
efax: 59:02 argv[17]=-t
efax: 59:02 argv[18]=T2620989
efax: 59:02 argv[19]=/home/kent/abc.ps.001
efax: 59:02 created text lock file /var/lock/LCK..ttySL0
efax: 59:02 opened /dev/ttySL0
efax: 59:02 command  "Q0V1"
efax: 59:02 waiting 2.0 s
efax: 59:02 .427 [ATQ0V1<CR><CR><LF>]
efax: 59:02 .427 [OK<CR><LF>]
efax: 59:02 response "OK"
efax: 59:02 command  "Z"
efax: 59:02 waiting 5.0 s
efax: 59:02 .527 [ATZ<CR><CR><LF>]
efax: 59:02 .527 [OK<CR><LF>]
efax: 59:02 response "OK"
efax: 59:02 command  "&FE&D2S7=120"
efax: 59:02 waiting 5.0 s
efax: 59:02 .627 [AT&FE&D2S7=120<CR><CR><LF>]
efax: 59:02 .627 [OK<CR><LF>]
efax: 59:02 response "OK"
efax: 59:02 command  "&C0"
efax: 59:02 waiting 5.0 s
efax: 59:02 .727 [OK<CR><LF>]
efax: 59:02 response "OK"
efax: 59:02 command  "M1L0"
efax: 59:02 waiting 5.0 s
efax: 59:02 .827 [OK<CR><LF>]
efax: 59:02 response "OK"
efax: 59:02 command  "E0"
efax: 59:02 waiting 5.0 s
efax: 59:02 .927 [OK<CR><LF>]
efax: 59:02 response "OK"
efax: 59:03 command  "I3"
efax: 59:03 waiting 5.0 s
efax: 59:03 .027 [modem:1<CR><LF>]
efax: 59:03 .027 [alsa modem driver<CR><LF>]
efax: 59:03 .027 [OK<CR><LF>]
efax: 59:03 response "OK"
efax: 59:03 command  "+FCLASS=?"
efax: 59:03 waiting 5.0 s
efax: 59:03 .127 [0,1,8<CR><LF>]
efax: 59:03 .127 [OK<CR><LF>]
efax: 59:03 response "OK"
efax: 59:03 command  "+FCLASS=1"
efax: 59:03 waiting 5.0 s
efax: 59:03 .227 [OK<CR><LF>]
efax: 59:03 response "OK"
efax: 59:03 using modem:1 in class 1
efax: 59:03 command  "+FTM=?"
efax: 59:03 waiting 5.0 s
efax: 59:03 .327 [24,48,72,73,74,96,97,98,121,122,145,146<CR><LF>]
efax: 59:03 .327 [OK<CR><LF>]
efax: 59:03 response "OK"
efax: 59:03 dialing T2640989
```

---

### Post by Wolf-Ekkehard on 2006-11-23
I just installed a brand new 29 Dollar winmodem (Sterling Communications, S20, with a SL 2800 PCI chipset), a smartlink driver and efax with efax-gtk, and it worked "out-of-the-box". So I feel guilty... :-)

As far as I can tell, there is not much new info between your second and the last post.  All this says is that you can contact your modem and send some initialization sequences to it, but for some reason it doesn't do the fax connect trick after dialing.  You should look for a "connected" status before you can go any further.

What did you do between post 1 and post 2?

Are you sure your modem works?  Under M$ Windoze for fax or at least under Ubuntu for any sort of dial-up?  

I'm not familiar with your particular modem, but did you run scanModem ([https://help.ubuntu.com/ubuntu/desktopguide/en_GB/hardware.html#modems]("https://help.ubuntu.com/ubuntu/desktopguide/en_GB/hardware.html#modems"))?  If so, what did the ModemData.txt file say?  

What driver did you install?  

With this additional info maybe I (or somebody more qualified) can help more.

---

### Post by life4himsq on 2006-12-04
I am running Mepis 6 on an IBM T20 using the internal modem, and I get the same error. 

Socket running on port 9900
ESP Ghostscript 815.02: Unrecoverable error, exit code 1
Not valid postscript file
efax-0.9a: 56:12 opened /dev/modem
efax-0.9a: 56:13 using LT V.92 Data+Fax Modem Version 8.31 in class 1
efax-0.9a: 56:14 dialing T4262020
efax-0.9a: 56:14 Error: dial command failed
efax-0.9a: 56:14 failed page /user/kscan_0001.eps.001
efax-0.9a: 56:14 finished - unrecoverable error


I can use KPPP to dial out just fine. I don't have a dialup account so I called a phone to check it. When I picked up on the phone I could hear it "talking" so that is what I call working. I tried the adding 1 and area code an all with efax and got the same error. Hope some one can figure it out. I will keep trying.

---

### Post by life4himsq on 2006-12-04
So after playing with the init string with everything I found with google, I added D"phone number" and I heard the dialtone and it dialed the whole number. Then gave me ths error.

efax-0.9a: 52:43 opened /dev/modem
efax-0.9a: 52:50 Error: modem command (D4262020) failed
efax-0.9a: 52:50 failed page /root/kscan_0001.eps.001
efax-0.9a: 52:53 finished - invalid modem response

Is efax not initializing the winmodem correctly for fax use? I assume there is a difference between fax and data initial strings. I think it would be easier to get an old fax machine from the goodwill... but now I must make this work.

---

