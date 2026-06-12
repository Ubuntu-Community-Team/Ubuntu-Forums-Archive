---
title: "Avermedia Volar HX (A827) + Ubuntu 12.04"
date: 2012-05-06
forum: Hardware
---

### Post by welcomejn on 2012-05-06
Hello!

I've been trying to properly instal DVB-T tuner on new Ubuntu.
I followed the instruction in ubuntu wiki, but with no success.

The problem is, when I installed drivers, in DEV folder is created file video1 (when I tried to play this file in VLC, the light in tunner turns on, but VLC cannot play this file - obviously - and than light turns off - so drivers work. But in "dev" folder should be a "dvb" folder and in this folder some others files to handle the tunner - and the "dvb" folder isn't here at all.

I followed this instruction [http://linuxtv.org/wiki/index.php/AVerMedia_AverTV_Hybrid_Volar_HX_(A827)]("http://linuxtv.org/wiki/index.php/AVerMedia_AverTV_Hybrid_Volar_HX_(A827)") 

Thnx for help.

---

### Post by TomasF on 2012-05-18
Hi guys,
it might help someone - the installer for AVERMEDIA AVerTV Hybrid Volar  HX fixed for kernel 3.2.0 (Ubuntu 12.04). It contains fixes described  here - [http://linuxtv.org/wiki/index.php/AVerMedia_AverTV_Hybrid_Volar_HX_%28A827%29](http://linuxtv.org/wiki/index.php/AVerMedia_AverTV_Hybrid_Volar_HX_%28A827%29)

[http://dl.dropbox.com/u/2381236/AVERMEDIA-Linux-x86-H826D-0.10-beta-kernel3.2.0.sh](http://dl.dropbox.com/u/2381236/AVERMEDIA-Linux-x86-H826D-0.10-beta-kernel3.2.0.sh)

Just copy the file to any folder, check whether it's executable and run following command:
```
sudo ./AVERMEDIA-Linux-x86-H826D-0.10-beta-kernel3.2.0.sh 
```(Original dirver - [http://www.avermedia.com/Product/ProductDetail.aspx?Id=293&tab=APDriver](http://www.avermedia.com/Product/ProductDetail.aspx?Id=293&tab=APDriver))

---

### Post by welcomejn on 2012-05-21
Thnx, but I cannot test it, because I'm currently running on x64... Don't you have the x64 version of this?

---

### Post by jmore9 on 2012-05-21
Have you tried kaffeine or metv ?  I use both on my wintv hvr 1600 and pinnacle 800i.

---

### Post by TomasF on 2012-06-19
x64 version. Not tested.

[http://dl.dropbox.com/u/2381236/AVERMEDIA-Linux-x64-H826D-0.10-beta-kernel3.2.0.sh](http://dl.dropbox.com/u/2381236/AVERMEDIA-Linux-x64-H826D-0.10-beta-kernel3.2.0.sh)

---

### Post by wlodarek1 on 2012-06-21
Today i am tested this 64-bit wersion .
Tested in Kubuntu 12.04 and Fedora 17 [64-bit .
But a have a bugs ; in fedora ;
[[IMG]http://img803.imageshack.us/img803/8779/64bitowysterownikaverme.th.png[/IMG]](http://imageshack.us/photo/my-images/803/64bitowysterownikaverme.png/)
and *buntu ;
[[IMG]http://img849.imageshack.us/img849/3255/avermedia64bitbladnakub.th.png[/IMG]](http://imageshack.us/photo/my-images/849/avermedia64bitbladnakub.png/)
:mad::mad:
Fedora 17 have a kernel 3.4 series , ubuntu standard kernel 3.2.0.25

---

### Post by Nostromo2GE on 2012-06-28
Thx for your great job TomasF and testing

Maybe  mistake comes from.
-->
For kernel 3.2.0, additional change is needed:
Modify driver-core.c, and add the line
#include <linux/module.h>
after line 77
#include <linux/types.h>
<--

Can you check this ?

++

---

### Post by TomasF on 2012-06-28
You are right, I  omitted the very last fix for 3.2 kernel. Unfortunately I have no x64 machine/system for testing. So it's up to you folks. Hopefully we will get it running after a couple of trials and errors :)

Here is the latest trial:
[http://dl.dropbox.com/u/2381236/AVERMEDIA-Linux-x64-H826D-0.10-beta-kernel3.2.0.sh](http://dl.dropbox.com/u/2381236/AVERMEDIA-Linux-x64-H826D-0.10-beta-kernel3.2.0.sh)

---

### Post by Nostromo2GE on 2012-06-30
I just realized a test on a virtual machine (VirtualBox) running on Mythbuntu (3.2.0) 64bit   and everything seems to work.
I set-up "mythtv-backend" and try xmbc-pvr frontend...
 
[ATTACH]220466[/ATTACH]
[ATTACH]220467[/ATTACH]

---

### Post by omzoo89 on 2012-07-02
I have problems for installing the driver [IMG]http://http://twitpic.com/a30not[/IMG]
The end of the message is : fatal error ........: invalid argument

---

### Post by keeper24 on 2012-07-02
I use Ubuntu LS 12.4 and I cannot even get as far as you can. Upon 

sudo: ./AVERMEDIA-Linux-x86-H826D-0.10-beta-kernel3.2.0.sh

I get the error message "Befehl nicht gefunden" which means "Command not found". Is there any extra software required for the installer? How did you do it?

---

### Post by zsasha2 on 2012-07-03
> **TomasF said:**
> You are right, I  omitted the very last fix for 3.2 kernel. Unfortunately I have no x64 machine/system for testing. So it's up to you folks. Hopefully we will get it running after a couple of trials and errors :)

Here is the latest trial:
[http://dl.dropbox.com/u/2381236/AVERMEDIA-Linux-x64-H826D-0.10-beta-kernel3.2.0.sh](http://dl.dropbox.com/u/2381236/AVERMEDIA-Linux-x64-H826D-0.10-beta-kernel3.2.0.sh)

Tomas, you are great! Works on Ubunto Serv 12.04 x64 excellent!
Well, at least I finally found /dev/video0 device.
Thanks a lot!!!

---

### Post by zsasha2 on 2012-07-03
> **keeper24 said:**
> I use Ubuntu LS 12.4 and I cannot even get as far as you can. Upon 

sudo: ./AVERMEDIA-Linux-x86-H826D-0.10-beta-kernel3.2.0.sh

I get the error message "Befehl nicht gefunden" which means "Command not found". Is there any extra software required for the installer? How did you do it?

I just did "sudo su", then did "apt-get install kernel-package"and then run the script. EVerything went well for me.

---

### Post by wlodarek1 on 2012-07-03
Yes , driver is istalled very well and working ok):P
But there is a problem;
In console is that ;
> darek@darek-JV71TR:~$ kaffeine
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.


---

### Post by moocow1452 on 2012-07-19
I'm having trouble with Lubuntu 12.10 with the new 32 bit installer. Although technically the installer works fine, I just can't use the device with GPlayer or VLC. What should I try next?

---

### Post by wlodarek1 on 2012-11-19
In UBUNTU 12,10  driver for kernel 3.2 installing properly, new modules loaded , but not working.
In  console I have that ;

darek@darek-JV71TR:~$ w_scan -ft -c PL -X >> channels.conf
```
w_scan version 20120605 (compiled for DVB API 5.5)
using settings for POLAND
DVB aerial
DVB-T Europe
scan type TERRESTRIAL, channellist 4
output format czap/tzap/szap/xine
output charset 'UTF-8', use -C <charset> to override
Info: using DVB adapter auto detection.
        /dev/dvb/adapter0/frontend0 -> "A827[0] DVB-T" doesnt support TERRESTRIAL -> SEARCH NEXT ONE.
main:3220: FATAL: ***** NO USEABLE TERRESTRIAL CARD FOUND. *****
Please check wether dvb driver is loaded and
verify that no dvb application (i.e. vdr) is running.
darek@darek-JV71TR:~$ 

```
Whereis the bug ?:confused:

---

### Post by wlodarek1 on 2012-11-22
Could someone make a driver developed by TomasF this patch;
[http://patchwork.linuxtv.org/patch/9492/]("http://patchwork.linuxtv.org/patch/9492/"):confused:

---

### Post by Greggi on 2012-12-01
Anyone got working solution for 12.10 and kernel 3.5? / Any way to get working under 12.10?
Ubuntu 12.10 x64 kernel 3.5.0-19-generic

---

### Post by mmmmmm on 2012-12-20
I have the same issue, i upgraded because of some other hardware to 12.10 and kernel 3.5.0.19 and the tuner Aver Volar Hx stopped working.
I have certain patched version (either from this or similar thread) for 64bit working on kernels 3.2.0  in 12.04 which was working fine.
This version compiles fine, but when the player app tries to tune te frequency (as i assueme from VLC log) in dmesg appears bunch of following lines:
[FONT="Courier New"]
[  319.052320] dvb_frontend_ioctl_legacy: doesn't know how to handle a DVBv3 call to delivery system 112[/FONT]

The output from VLC is following:
[FONT="Courier New"]
[0x7f1f80004b28] dtv access error: cannot set frontend tuning parameters: Invalid argument                                                                  
[0x7f1f80004b28] dtv access error: tuning to 666000000 Hz failed                                                                    
[0x7f1f9c010038] main input error: open of `dvb://' failed  [/FONT]

Any help would be appreciated. I am not sure if it correspons with the post two messages ago with patch in dvb-core.

---

### Post by skvedo on 2013-06-17
Does someone running this tunner in 13.04 (3.8 kernel)? I would like to upgrade, but already in 12.10 using 3.2 kernel to make tunner works.

---

### Post by rvojcik on 2013-07-16
> **skvedo said:**
> Does someone running this tunner in 13.04 (3.8 kernel)? I would like to upgrade, but already in 12.10 using 3.2 kernel to make tunner works.

Hi , 

I am using this with xubuntu 13.04 but not with 3.8 kernel ( no success with this). I'am using kernel package from 12.10 (kernel 3.5) Can be downloaded here: [http://packages.ubuntu.com/quantal/kernel/](http://packages.ubuntu.com/quantal/kernel/)

---

