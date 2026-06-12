---
title: "Conexant ADSL usb modem"
date: 2007-05-14
forum: Hardware &amp; Laptops
---

### Post by manjula.mh on 2007-05-14
How to configure ADSL USB modem running on Conexant accessrunner chipset.
This is the type of modem i used [http://www.cnet.com.tw/product/cnad800-ef.htm](http://www.cnet.com.tw/product/cnad800-ef.htm)

I am assuming you are running a linux kernel 2.6 or above which recognize the USB modem with out any trouble. if not do a kernel upgrade.

Ubuntu ,FC6 and openSuse 10.2 are the Distros i tried an in each one it works perfectly.

Do not procede without fully reading and downloading all the files necessay. For your convenitinet i have uploaded all the files necessary here in winrar archive. but i have provided the links for original sites from which i downloaded if you wish to download them directly from the site.

[http://www.4shared.com/dir/2705414/b826a6a4/sharing.html](http://www.4shared.com/dir/2705414/b826a6a4/sharing.html)

You will have to be root.

get 'Makefile' and 'cxacru-fw.c' file from here. [http://accessrunner.cvs.sourceforge.net/accessrunner/utils/](http://accessrunner.cvs.sourceforge.net/accessrunner/utils/)

and compile them using a c compiler (like gcc)
e.g. $gcc -c cxacru-fw.c 



then you get the file cxacru-fw.o

then type $ make cxacru-fw

you will get a execuable file name make cxacru-fw ( this file will help you to extract the firmware from your manufracturer)

get the file CnxEtU.sys .It is in the CD your manufacture gave with the modem.Find it but i have provided a file for [http://www.cnet.com.tw/product/cnad800-ef.htm](http://www.cnet.com.tw/product/cnad800-ef.htm) modem. ( this file has firmware data of the ADSL modem or there will be a similar file. if you don't have this type of a file search the internet for what file is containing your firmware info for your type of modem and replace the name as accordingly)

type $ ./cxacru-fw CnxEtU.sys cxacru-fw.bin

will get output like this
found firmware in `CnxEtU.sys' at offset 0x41c0

Sometimes this command will give you errors.So for my type of modem the file i provided will do. IF not try to find the rite file or ask from a friend. even the file in my manufacturers Cd didn't work and i get the file from Dileep.(the person who help me to get this rite)

will get a file cxacru-fw.bin

copy this file to /lib/firmware

Opne the chap-secrets & pap-secrets files located in /etc/ppp

delete all  the content in them and repalce with( replace username and password with yours)

'username@isp' * 'password'

For FC6 ,suse and i think for all the other distros using rpm packages you should install the following rpm before proceding

'linux_a2.rpm' & 'linux_AT.rpm' (maybe one of them will do maybe you will need the both.) ignore dependencies

only in distros using rpm i encountered this not in distros like ubuntu but if u get a error telling some lib is missing read the out put and install the library missing by searching the internet.

this is for PPPoE only

get the file br2684ctl ([http://linux-usb.sourceforge.net/SpeedTouch/mandrake/br2684ctl](http://linux-usb.sourceforge.net/SpeedTouch/mandrake/br2684ctl))


and install the file by
$install -m 755 br2684ctl /usr/sbin

now make a file named 'access' and put the following script. replace username@isp with  your username

noipdefault
defaultroute
user 'username@isp'
noauth
updetach
usepeerdns
plugin /usr/lib/pppd/2.4.4/rp-pppoe.so
nas0

### If the firmware loads but pppd won't
### connect, uncomment this option to make
### pppd be more verbose in the system log

# debug

### For more details (and more options)
### Read man pppd

copy this file to /etc/ppp/peers

sometimes rp-pppoe.so is not in the location i have given. So find the location. It should be somewhere.:-)

create a new file named 'dial' and keep it in your folder and put the follwing script in it

#!/bin/bash
modprobe ppp_generic
modprobe pppoatm
modprobe br2684

br2684ctl -b -c 0 -a 8.35 
# here the number 8 is for the VPI and 35 for VCI
sleep 3
#correct script
ifconfig nas0 up 

sleep 5
pppd call access



here 8.35 stand for your  vc and vci and u may have to modify according to your providers requirement


now type in console

$chmod +x dial


Restart the computer

to activate the connection type 

$./dial

to see whether it is configured well type (you don't have to type this to get connect just to make sure everything is in order)

$ifconfig



nas0 and ppp0 should be there

This should work for ubuntu, suse but in FC sometims this doen't work.
So go to /etc/resolv.conf and put this

nameserver "Priamary DNS"
nameserver "Secondary DNS"

put  your primary and secondary DNS there . you will see them when you type ./dial to connect along with your IP address. just put them there in that file.

This has worked on Ubuntu ,openSuse 10.2 and FC6.
So any toruble contact me [email]manjula.mh@gmail.com[/email]

If you get errors telling of missing packages just install them.

This is for USB ADSL modems in PPPoE only. Configured to work with CNet ADSL usb modem and to all the setting are for SRI LANKA Telecom ADSL connections
So your ISP's setting might be different and therefore just read through the script and you be able to figure out which values should be chabged.
Thanks to Dileep who help me to configure the modem.

please share the information and problems you encounter while configuring these divices in different platforms and different kernels and distros so others will understand this better.

One problem i encountered is when i copy all the files neccessary for this in to a cd it chaged most names of the files and gave erros therefore if you do the same i advice you not to copy files directly to a cd or dvd but as rar archives which will preserve the names. or you can simply rename on the files by looking at this guide. 

Make sure u are log as root or if not use su command in console when u execute dial because errors tend to come.
If any problems encounteres feel free to contact me at [email]manjula.mh@gmail.com[/email]

---

