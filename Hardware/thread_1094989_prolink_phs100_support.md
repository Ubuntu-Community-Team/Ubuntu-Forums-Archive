---
title: "prolink phs100 support"
date: 2009-03-13
forum: Hardware
---

### Post by toxiclung on 2009-03-13
hi all,

i just bought a prolink phs100 hsdpa modem ( website at:
[http://www.prolink2u.com/self/products/datacom/phs100.php](http://www.prolink2u.com/self/products/datacom/phs100.php) )
but i cant find any ubuntu thread on installing this device.

when i insert it to the usb port, it's only recognized as a storage and i can see the windoze drivers in it, but nothing for linux.

has anyone had any success using it on ubuntu?
please help...

tL

---

### Post by laxaman on 2009-04-29
:)see [this]("http://nmlaxaman.blogspot.com/2009/04/prolink-phs100-hsdpa-workout-for-debian.html") link

---

### Post by ajat_su on 2009-06-02
I have similar problem with this modem. 
I can't see 'ttyUSB*' at /dev/ after editing parameters. 
Also got message 'Cannot open /dev/ttyUSB3: No such device or address' after using wvdial.

please help..

---

### Post by mastermind008 on 2009-08-20
Please download this PDF

[http://www.mobitel.lk/pdf/devices/prolink_linux_installation_guide.pdf](http://www.mobitel.lk/pdf/devices/prolink_linux_installation_guide.pdf)
:popcorn:

---

### Post by mastermind008 on 2009-08-21
Yes, That's true. ls -al /dev/ttyUSB* is not working.
Even lsusb doesn't show my Prolink PHS 100 modem.
It shows something like "f0000":confused:

---

### Post by mastermind008 on 2009-09-07
First we have to update Ubunut 9.04 using a a wired connection.
Then I followed Laxmans blog above.
After that I followed the link (Prolink provided PDF) I have published above.

And I could get it connected nicely.
Now I use a launcher with 'bash' scripts to launch 'GNOME PPP' after running all the commands mentioned in Prolink provide PDF. then I can connect my laptop to internet with just a click.

:P

---

### Post by suomaf on 2009-10-12
Hey mastermind008,

Any more hints on how to get it to work? so far I am stuck at the f0000 stage. I read somewhere that you need to be at 2.6.30 for this to work? Any ideas anyone?

Suo

---

### Post by suomaf on 2009-10-24
Hey guys,

Desperately need help. I got a 3G connection and when I am on windows I am able to tell it to use WCDMA only and get about 1mbs but when I switch over to linux I think I am on the GSM band and so max is about 5kb/s. Is there any AT command that I can use in wvdial.conf that will force it to go to WCDMA only?

Really need help. Do not want to use windows. Thanks.

EDIT: Seems that if I get connected to WCDMA or HSDPA then i pluck the modem out and plug it into linux .. it will sort of / sometimes connect at a higher speed. Is there anyway to see what band we are connected at? Is there any way to restrict it to connect only at the higher speeds?

---

### Post by suomaf on 2009-10-25
bumpity bump

---

### Post by mastermind008 on 2010-01-01
I'm sorry '[suomaf]("http://www.uluga.ubuntuforums.org/member.php?u=585240")'
I couldn't visit this forum as I was a little busy for last few months. Are you using Ubuntu 9.10 or 9.04?

---

### Post by rusmawan on 2010-08-07
Yes, I have similar problems, It seem that ubuntu can not read the prolink phs100, please need help, I am using ubuntu 10.04 LTS

---

### Post by DoctorMO on 2010-09-27
I've added the newer debian packages to my ppa so you should just have to add my ppa to your system and install usb-modeswitch:

sudo add-apt-repository ppa:doctormo/ppa
sudo apt-get update
sudo apt-get install usb-modeswitch

Hope this clears up the previous rather complex and dangerous instructions. Let me know if it doesn't work and we'll try and fix it.

---

