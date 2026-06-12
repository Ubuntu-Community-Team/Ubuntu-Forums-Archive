---
title: "constant cups/printing issues"
date: 2020-03-08
forum: Hardware
---

### Post by nrs1 on 2020-03-08
Hi all,
trying to keep this as short as I can:   I am in a conventional dell/canon printer environment, and while not an expert, and not completely new to linux either.

shortly after this fresh install of ubuntu...18.04......i experienced this:

cups installed and confirmed.

canon mfc634 showing up, along with some ghost of it (and a message that this ghost could not accept jobs)

tried to eliminate the ghost, but it never goes away, unless I unplug the printer (hooked up via its ethernet connection)

canon printer then disappeared (after working once) and now cups does not seem to be operating, despite a reinstall.

also just tried to install cups/pdf, and as what I believe to be an important "tell", got the following in terminal when I did:

Setting up printer-driver-cups-pdf (3.0.1-5) ...
CUPS failed to reload its configuration!
Skipped automated creation of the PDF queue.
Processing triggers for cups (2.2.7-1ubuntu2.7) ...

no amount of trying to get the local host to come up via the browser, brings anything but an error, and I never can get to it.....and one poor wretch with the same problem, suggests a host corruption file, but I am afraid to mess with that, even if I can get to it.

I have tried numerous times to look for cups (which does appear to be still, installed, but unusable as the printer dialogue box  says "it does not appear" that it is running.....used, literally, a half dozen "solutions" from others who have reported exactly the same situation, but to no avail....nothing I do allows me to print to anything but "file"..although that does seem to be working.

HELP..PLEASE......I am in a mission critical environment......the legal business where I do free work for people in trouble (let me pse leave it at that)....and I desperately need to fix this....coming here as I did from win 7, for obvious reasons.

I love ubuntu....and am so glad I am finally using it....but this is driving me insane as it is preventing me from doing my job.

thank you in advance for any assistance!

robert the appreciative

---

### Post by wildmanne39 on 2020-03-08
*Thread moved to **Hardware a more appropriate sub-forum**.*

---

### Post by nrs1 on 2020-03-08
ps trying the canon printer, mf634, with usb, just resulted in lots of activity when I used this command:   tail -f /var/log/syslog.....with the following end result:

Mar  8 20:08:30 parmad-Precision-7720 colord-sane: io/hpmud/pp.c 627: unable to read device-id ret=-1

---

### Post by brian_p on 2020-03-09
Put the printer on the network and give the outputs of ```
avahi-browse -rt _ipp._tcp 
``` ```
avahi-browse -rt _uscan._tcp 
```

---

### Post by nrs1 on 2020-03-09
thank you, Brian,

below:

$ avahi-browse -rt _ipp._tcp
+ enp0s31f6 IPv4 Canon MF632C/634C                             Internet Printer     local
= enp0s31f6 IPv4 Canon MF632C/634C                             Internet Printer     local
   hostname = [Canone1ab44.local]
   address = [192.168.50.17]
   port = [631]
   txt = ["mopria-certified=1.2" "print_wfds=T" "rfo=ipp/faxout" "kind=document,envelope,postcard" "URF=ADOBERGB24,CP255,DM1,PQ4,RS300,SRGB24,W8-16,FN3,IS1-4,OB10-40,V1.4" "Fax=T" "Scan=T" "TLS=1.2" "usb_CMD=LIPSLX,CPCA" "UUID=6d4ff0ce-6b11-11d8-8020-f80d60e1ab44" "PaperMax=legal-A4" "Punch=0" "Staple=F" "Sort=F" "Collate=F" "Bind=F" "PaperCustom=T" "Duplex=T" "Copies=T" "Color=T" "TBCP=F" "Binary=F" "Transparent=F" "usb_MDL=MF632C/634C" "usb_MFG=Canon" "adminurl=http://Canone1ab44.local:80/airprint.html" "pdl=application/octet-stream,image/urf,image/pwg-raster,image/jpeg,application/pdf" "product=(CNMF632C/634C)" "ty=Canon MF632C/634C" "priority=10" "qtotal=1" "note=" "rp=ipp/print" "txtvers=1"]

avahi-browse -rt _uscan._tcp:

$ avahi-browse -rt _uscan._tcp
+ enp0s31f6 IPv4 Canon MF632C/634C                             _uscan._tcp          local
= enp0s31f6 IPv4 Canon MF632C/634C                             _uscan._tcp          local
   hostname = [Canone1ab44.local]
   address = [192.168.50.17]
   port = [80]
   txt = ["Duplex=T" "is=platen,adf" "UUID=6d4ff0ce-6b11-11d8-8020-f80d60e1ab44" "cs=color,grayscale" "pdl=application/octet-stream,application/pdf,image/jpeg" "representation=http://Canone1ab44.local/en/media/dev_icon_128x128.png" "adminurl=http://Canone1ab44.local:80/airprint.html" "rs=eSCL" "vers=2.62" "note=" "ty=Canon MF632C/634C" "txtvers=1"]

---

### Post by brian_p on 2020-03-09
The device URI for your printer is **ipp://Canone1ab44.local:631/ipp/print**. Substitute this in the next command. A print job may be sent to this URI by setting up a print queue like this: ```
lpadmin -p mf634 -v URI -E -m everywhere
``` Test printing with ```
lp -d mf634 /etc/nsswitch.conf
```

All is ok?

---

### Post by nrs1 on 2020-03-09
just getting back to my desk, and have a medical procedure tomorrow, so  not sure when I can make sure I understand exactly what you are telling  me to do, but kindly stand by. 

meantime, can you please tell me why the normal print setup and use  process for those of us less used to command line....click and  print....which mean a lot to me here in the legal business.....are not  working. to wit, how is it that the printer shows up after looking via  terminal, but not any other way in a fresh install of ubuntu......  AND,  please, why am I not able to invoke any localhost indicator via my  browser?

again, thanks so much for your help.

---

### Post by CelticWarrior on 2020-03-09
I thought you're asking about CUPS because you had to use/configure the printer there. But now you say "click and print"?  :confused:
Normal users actually want exactly that and it should be easy, as easy as in Windows if not more.

Canon printers require proprietary drivers. Download and install them and the printer should be listed in "Printers" and you should be able to print from any software.

---

### Post by nrs1 on 2020-03-09
ok, decided to at least try this:

lp -d mf634 /etc/nsswitch.conf

the result was nothing...no activity at all...unless I am missing something. i put this in terminal exactly as you sent it....and it went right back to the basic prompt.

at risk of repeating, as I do appreciate what you are doing...i switched from mint to ubuntu figuring I would find more people to help me with issues......but even if all of this via terminal works, i need to understand why all the failures....per my questions, above, so I hope you will kindly take the time to address all that.

---

### Post by nrs1 on 2020-03-09
i was asking about that...sorry for confusion...as I have learned that front end GUI aside, CUPS is the basis for being able to print....and my attempts at reinstalling it have gone to naught when I look for this to show up in "click and print"...so i figured I ought to hit the basic, so to say, when asking for help.

and I figured that if cups....and the messages I am getting in the gui are that printing service does not "appear" to be present.......were made to work in the background, that all my click and print, etc., would naturally come back...so that is why i referred to it as i did.

---

### Post by nrs1 on 2020-03-09
ps as to the proprietary driver, it worked right out of the shute without that and then disappeared.

r u saying that while it showed up to start with, the proprietary driver is necessary for gui use (i have downloaded the one linux driver they have but wanted not to install it until I heard back from you...again, looking at this as a kind of building block scenario

---

### Post by CelticWarrior on 2020-03-09
You need to install drivers, not reinstall CUPS.

---

### Post by brian_p on 2020-03-10
> **nrs1 said:**
> ok, decided to at least try this:

lp -d mf634 /etc/nsswitch.conf

the result was nothing...no activity at all...unless I am missing something. i put this in terminal exactly as you sent it....and it went right back to the basic prompt.

The two-line setup I gave you is the most fundamental way of getting a modern printer printing. There is nothing more fundamental available. If it does not work, you have either a broken printing system or a broken printer. (BTW, your avahi-browse outputs show that your printer does not require any Canon drivers).

> at risk of repeating, as I do appreciate what you are doing...i switched from mint to ubuntu figuring I would find more people to help me with issues......but even if all of this via terminal works, i need to understand why all the failures....per my questions, above, so I hope you will kindly take the time to address all that.

It's like this: I read **HELP..PLEASE......I am in a mission critical environment.....and I desperately need to fix this....** and thought a 5-minute solution would be appropriate. Addressing the cause of failure would take much longer.

I will give you one diagnostic to try: execute ```
driverless
``` and give us the output.

---

