---
title: "MSI Starcam Clip with gspca driver - pink screen!"
date: 2006-12-17
forum: Hardware &amp; Laptops
---

### Post by scuttles on 2006-12-17
Hi, i wonder if anyone can help me

I recently purchased an MSI Starcam Clip and I'm having some trouble getting it to work - all I get is a pink screen output with a small amount of grainyness along the top edge.  This happens in camorama, ekiga and kopete

The specific model of my webcam is not listed in [Michel Xhaard's list]("http://mxhaard.free.fr/spca5xx.html"), however, the bridge and sensor chips (SN9c105 and MI0360 respectively) ARE listed as "Sangha sn-535".  The USB ID also matches my camera (0c45:60c0).

So I then went on, downloaded the gspca driver and compiled the module using module-assist and checked the permissions to make sure my user is part of the video group.

All the webcam apps can access the device fine, and camorama recogises it as Sangha 350, so in theory it should be working, but no, the pink screen :-k 

Any help or pointing in the right direction/pointing out where I've gone wrong is much appreciated. I can provide more info if needed!

cheers in advance!

---

### Post by nicolas.dh on 2007-01-24
Same thing here,
my WEB CAM is:

  MSI, StarCam

I first tried using the webcam directly with Edgy's
spca5xx driver, and got camorama starting, 
using the /dev/video0, but had no image....
(a dotted matrix, with a little colored horizontal
bar on the top)

I then tried with the gspcav1-20070110.tar.gz
[http://mxhaard.free.fr/download.html]("http://mxhaard.free.fr/download.html")

--------------------------
lsusb
Bus 001 Device 005: ID 0c45:60c0 Microdia 

(there is a match on 0c45:60c0) on the site:
[http://mxhaard.free.fr/spca5xx.html]("http://mxhaard.free.fr/spca5xx.html")
Sangha 	154 	0x0c45 	0x60c0 	Sn-535 	  	sn9c105 	Mi0360 	Yes 	jpeg 	spca5xx/LE 	*****

-------------------------
rmmod spca5xx
make
make install
modprobe gspca
--------------------------

tail -500  /var/log/messages |grep gspca

gspcav1-20070110/gspca_core.c: USB SPCA5XX camera found. SONIX JPEG (sn9c1xx) 
gspcav1-20070110/gspca_core.c: [spca5xx_probe:3983] Camera type JPEG 
gspcav1-20070110/gspca_core.c: [spca5xx_getcapability:1189] maxw 640 maxh 480 minw 160 minh 120
usbcore: registered new driver gspca
gspcav1-20070110/gspca_core.c: gspca driver 01.00.12 registered
gspcav1-20070110/gspca_core.c: [spca5xx_set_light_freq:1858] Sensor currently not support light frequency banding filters.
gspcav1-20070110/gspca_core.c: [gspca_set_isoc_ep:881] ISO EndPoint found 0x81 AlternateSet 8
gspcav1-20070110/gspca_core.c: [gspca_set_isoc_ep:881] ISO EndPoint found 0x81 AlternateSet 8

-------------------------

camorama  (snapshot)
(can start, and read from /dev/video0 but image is no good)
(still get the dotted matrix, with little colored bar
on the top, as with the spca5xx initial driver )

[IMG]http://www.wgz.ca/camorama-snapshot.png[/IMG]


seems the problem was also reported on:
[http://www.linux-projects.org/modules/newbb/viewtopic.php?topic_id=248&forum=3]("http://www.linux-projects.org/modules/newbb/viewtopic.php?topic_id=248&forum=3")
and also on:
[http://www.abclinuxu.cz/hardware/vstupni-zarizeni/digitalni-kamery/msi-starcam-370i]("http://www.abclinuxu.cz/hardware/vstupni-zarizeni/digitalni-kamery/msi-starcam-370i")


Is this a "jpeg" compression problem, 
where we would need something like ov51x-jpeg "hack" ????
[http://www.rastageeks.org/ov51x-jpeg/index.php/Main_Page]("http://www.rastageeks.org/ov51x-jpeg/index.php/Main_Page")
but for the scpa5xx/gspca webcam (though it is recognized as a type JPEG) ???
:confused:

---

### Post by scuttles on 2007-01-26
I did the exact same thing, and ended up with the same result - a matrix with grainy horizontal bar.

To be honest, I gave up trying to fix this after a few weeks of frustration as I was unaware of anyone else having the same problem. I remain hopeful, however.

You seem to know more about this than I do, is there any information I can provide to help find a solution?

---

### Post by kvonb on 2007-01-27
-

---

### Post by kvonb on 2007-02-28
-

---

### Post by kvonb on 2007-02-28
-

---

### Post by rebus on 2007-09-30
Hello,
I have got the same problems (pink screen with dots):
[IMG]http://www.abclinuxu.cz/images/screenshots/3/2/95223-msi-starcam-clip-62977.jpg[/IMG].

I have got some small progress - but not much.
I am able to force the cam working using vmware. I am able to do it even without vmware using the usbreplay from snoop usb data from windows. However I still have got problem with the colours in the screen - have a look:
[IMG]http://www.abclinuxu.cz/images/screenshots/3/2/95223-msi-starcam-clip-mini-48165.jpg[/IMG]

Something wrong is probably with the initiation of the camera within the gspca module.

Vmware guide:
1) run vmware (tried with w2k)
2) connect camera
3) rmmod gspca
4) run amcap or other application to capture and stop it
5) stop vmware
6) modprobe gspca
7) now you should be able to use it under linux
for example mplayer -tv driver=v4l:width=320:height=240 tv://

BTW I didn't manage to run it on 640x480.
Please if you manage to get any further I would welcome any additional info, docs about SN9C105R, used sensor etc.

Best regards
Michal Ambroz

---

### Post by kvonb on 2007-10-10
-

---

### Post by vivalant on 2007-10-10
Have you already tried the SN9CXXX binary driver at [http://www.linux-projects.org](http://www.linux-projects.org) ? (Do not confuse with the SN9C1xx v4l2 driver)

---

### Post by rebus on 2007-10-11
> **kvonb said:**
> I compiled and installed the latest version of the spca5xx driver from Michael Xhaard:

[http://mxhaard.free.fr/spca50x/Download/gspcav1-20070508.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20070508.tar.gz)


Yes I am using the same gspca module as you.
On the begining I get dots only.
If I kick it with the usb replay from the iniciation from windows, I get picture which is bit strange in colours - all red is green and rest of the colours is not interesting at all.:(

---

### Post by kvonb on 2007-10-12
-

---

### Post by rebus on 2007-10-14
> **kvonb said:**
> I tried this driver yesterday, it does work but you have to pay for the full version.


I am aware of the effort Luca is putting to development of the closed driver and I respect his decision - it is his right to ask for the driver whatever he wants and have licensing model whatever he decides.

For me personaly - his licensing mode is not acceptable for me. Being obtained with binary driver is no good for me. Being obtained with binary driver strictly linked to one version of kernel is even worse for me and it is against the linux kernel license. I am not going that far to support such people.

I am aware that Luca has released older version sn9c102 and it is in the vanilla kernel and thanks for that.
But binary-only driver sn9cxxx is not way for me.

If you think about donating some of your money - I would recommend to send them rather to Michel Xhaard.  I did so. 

I know his driver might not be perfect now with MSI StarCam (0c45:60c0) , but it is open source (GPL) and already supports more than 200 of webcams. Anybody can benefit from his drivers.
 
I didn't send the money there with expectation that the driver will instantly work with my camera, but as a "thank you" for his effort he is putting in development of the driver.
RESPECT.

Rather than sending money to Luca, think about buying some camera, which is supported by free driver from some other developer. Think about sending the rest of the money, which you would have used for one kernel version binary driver, as a donation to the developper of the GPL driver.

Best regards
Michal Ambroz

---

### Post by kvonb on 2007-12-30
-

---

### Post by riyasmp on 2008-04-02
guys  i  have a MSI starcam 370+ which come up on terminal as microdia with "lsusb"

Bus 005 Device 005: ID 07ab:fcf4 Freecom Technologies 
Bus 005 Device 004: ID 1516:8628  
Bus 005 Device 003: ID 05e3:0606 Genesys Logic, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 1020:000a Labtec Wireless Optical Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0c45:608f Microdia 
Bus 001 Device 001: ID 0000:0000  

i tried installing easy cam and when i put "lauchcam2" on terminal it says no command found ([https://help.ubuntu.com/community/EasyCam?highlight=%28easy%29%7C%28cam%29](https://help.ubuntu.com/community/EasyCam?highlight=%28easy%29%7C%28cam%29))

i tried installing the driver [http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=7](http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=7) but gives srror message at the end and is not installed

can anyone guide me telling wich is the right driver for it pls

---

### Post by bobe84 on 2008-04-03
I patched gspca driver, so now it works out of box in linux, please let me know if you wanna test the driver. 
For now i don't know where to upload driver so if you pm your email i can send you gspca that is WORKING with MSI STARCAM 370i

Regards, Boban

---

### Post by bobe84 on 2008-04-03
I uploaded driver 
[www.pamplast.com/gspca/](www.pamplast.com/gspca/)
Try it and let me know if it is any good

---

### Post by riyasmp on 2008-04-03
thanks for the reply bob

as a newB it was very difficult to compile and install the driver for me. with the help of online support i was able to install the driver and under the applications camorama webcam viewer icon came up. then i connected my webcam and cliked on the icon unfortunately i got an error message telling that no device connected.

i removed the software and re installed the camorama software from ubuntu synaptic update it showed the same message so i again removed and tried to install again from the driver that u have given me.

but now after the installation even the icon is not coming up unfortunatly

:-(

my webcam is MSI starcam 370+ and i think 370i is a similar one i think

thanks

---

### Post by bobe84 on 2008-04-03
My camera is MSI Starcam 370i, 0c45 60c0.
However hardware is different, so i presume it wont work :( 
You can send me your usb sniff log from Win so i can resolve what are the difference.
Again this gspca driver is modified to work with MSI Starcam 370i 0c45 60c0.

---

### Post by bobe84 on 2008-04-03
I just looked in gspca source, your camera vendor and product id are not listed in it, but there is possibility that it is very similiar to mine, so if you can provide me usb logs from windows i could try to make it work.

---

### Post by bobe84 on 2008-04-03
I havent read whole thread but have you tried free driver from linux-project?
[http://www.linux-projects.org/modules/mydownloads/visit.php?cid=2&lid=44](http://www.linux-projects.org/modules/mydownloads/visit.php?cid=2&lid=44)
sn9c1xx-1.48.tar.gz
Your id is listed there...

---

### Post by riyasmp on 2008-04-03
dear bobe

i din get exactly what u ment by usb win log, if u could explain me a bit more i would be able to do it

Bus 005 Device 005: ID 07ab:fcf4 Freecom Technologies
Bus 005 Device 004: ID 1516:8628
Bus 005 Device 003: ID 05e3:0606 Genesys Logic, Inc.
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 1020:000a Labtec Wireless Optical Mouse
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 0c45:608f Microdia
Bus 001 Device 001: ID 0000:0000 

when i type lsusb this is the one which comes up. i don know if it will help u

thanks

---

### Post by bobe84 on 2008-04-04
It's ok, i was wondering if you could go to windows and make usb log of you camera.
That way i can know what was camera talking to you system.

---

### Post by bobe84 on 2008-04-04
[http://groups.google.com/group/microdia/](http://groups.google.com/group/microdia/)
You should go there, it has instructions on how to sniff usb, and program to download also.

---

### Post by riyasmp on 2008-04-04
hi bobe

i am sorry to say that something has gone wrong with that driver.ubuntu start has slowed down a lot and takes around 5-6 minutes to start up and lsusb command is not giving anyoutput,  and it just blinks :(

any help

r

---

### Post by bobe84 on 2008-04-05
With what driver?

---

### Post by riyasmp on 2008-04-05
Hi bob

i tried the driver but unfortunately i was not lucky enough to make my cam work.the camorama web cam viewer appeared in the application menu under graphics. when i clicked on it but showed me an error messages telling the web cam not connected. i tried many times but it din work.:(
my webcam was connected though.

then i removed it through the synaptic but since then when ever i restarted my computer it took 5-6 minutes to boot up and "lsusb" command on terminal din give bak any output.

i had to re install the kernel to make it work again.:(

i am not sure what happened wrong. if u explain me more i would be able to send u the "codes" from windows. i am not very good with  computers so if u could tell me things stepwise manner i would be able to send u the things u asked me b4.

It would be gr8 if i could use my webcam on ubuntu at anypoint

thanks

---

### Post by bobe84 on 2008-04-06
You camera is very has very similiar name with mine, BUT :( it has different bridge and image sensor in it... :( so my driver is patched for 0c45 60c0 id and yours is different i don't belive that it will work at all. 
Not sure how big is your knowledge with linux and programming (mine is not great either), 
but you could try to "record" usb traffic with usb sniffer in windows.

I dunno what is slowing down your system, however you could try to remove driver(modules), you can do it also by modifying /etc/modprobe/blacklist...

---

