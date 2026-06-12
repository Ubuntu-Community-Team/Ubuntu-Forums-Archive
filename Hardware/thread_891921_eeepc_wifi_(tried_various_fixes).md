---
title: "eeepc wifi (tried various fixes)"
date: 2008-08-16
forum: Hardware
---

### Post by ashadocat on 2008-08-16
I decided I wanted my eeepc to use xubuntu.
I tried the madwifi workaround [here]("https://help.ubuntu.com/community/EeePC/Fixes"). I did not try the ndiswrapper fix because I would prefer to use actual drivers. although madwifi packages are there I still don't have any wifi.

next thing I did since that didn't work was I installed the eeepc ubuntu kernal found [here]("http://www.array.org/ubuntu/index.html"). once again the wifi doesn't work but the madwifi does. I also appended the modules config file(/etc/modules) to what the kernals site told me to.

what information do you need to help me and how do I get it?
is it possible that newer eeepc's use a different wifi chip set? (I bought it about 1 week ago)

help. please.

---

### Post by ashadocat on 2008-08-16
terribly sorry about this, I wouldn't normally but I really need help so without further ado, bump.

---

### Post by miabe on 2008-08-17
hi, I am ubuntu newbie so I can't help you in detail but maybe a fresh install with this guideline could be a quick solution:

[http://wiki.eeeuser.com/ubuntu:eeexubuntu:home#detailed_usb_installer_instructions](http://wiki.eeeuser.com/ubuntu:eeexubuntu:home#detailed_usb_installer_instructions)

[http://wiki.eeeuser.com/ubuntu:eeexubuntu:customization](http://wiki.eeeuser.com/ubuntu:eeexubuntu:customization)

cheers,
mia

---

### Post by ashadocat on 2008-08-18
Unfortunately that won't fix the problem. I'm already running eeexubuntu and have done 2 installs of it (when the wifi solutions didn't work I re installed it). sorry I should have opened that in the opening post. anybody have any idea?

---

### Post by VMan on 2008-08-18
Which model are you using.  I have a 1000H.  I installed from a stock Ubuntu 8.04.1 i386 (the currrent ISO download) CD and then installed adamm's custom kernel and modules from that site.  All of my hardware works just fine.  Let me know if I can help. . .

---

### Post by alohadiaz on 2008-08-18
Not only do I have a eee pc but I want to install ubuntu on all py computers and I have no clue what I am doing. I have tried the running the cd and installing it like that. I have tried booting from the cd. I dont want to get frustrated cause I know once I get it installed I will love as opposed to Microsft Crap but I need mad help. I dont have a External cd rom drive for my eee pc so that is ine problem I tried booting it from a thumb drive that didnt work I have looked at alott of links trying to get instructions and they just dont work. I have downloaded multiple copies of 8.4 ubuntu with know luck. I orderd one but who knows how long that will take. Anyway thanks!!!!!!!!!!!!:confused:

---

### Post by miabe on 2008-08-20
did you see the note about wireless on bottom of this page?

[http://wiki.eeeuser.com/ubuntu:eeexubuntu:home#detailed_usb_installer_instructions](http://wiki.eeeuser.com/ubuntu:eeexubuntu:home#detailed_usb_installer_instructions)

the eeexubuntu 7.10 works really perfect on my eeepc 4G. hope you will get yours to work. any problems with the default xandros linux?

---

### Post by henrimarc on 2008-09-16
Hello,

I have a problem : EEEpc 1000 loaded with Xandros.
I myself installed eeexubuntu 7.10 on it from a USB key.
Dual boot is ok.
Xandros still functions Ok : mail is ok, web connection are both ok : wireless and ethernet.

But when logged on in Ubuntu, there is no possible connection neither by wireless nor ethernet.

iwconfig says :
lo    no wireless extensions

no word about eth or ath.
What should I do ^
Thanks

---

### Post by ZarathustraDK on 2008-09-27
> **henrimarc said:**
> Hello,

I have a problem : EEEpc 1000 loaded with Xandros.
I myself installed eeexubuntu 7.10 on it from a USB key.
Dual boot is ok.
Xandros still functions Ok : mail is ok, web connection are both ok : wireless and ethernet.

But when logged on in Ubuntu, there is no possible connection neither by wireless nor ethernet.

iwconfig says :
lo    no wireless extensions

no word about eth or ath.
What should I do ^
Thanks

I have the exact same problem on the 901. Ethernet and wireless works in Xandros, but are somehow nonexistent in any other distro I try out. It's like some kind of switch that needs to be turned on that I don't know about.

---

### Post by michaelkahl on 2008-09-27
I'm using Ubuntu Eee and everything seems to work out of the box with netbook remix.  xfce4 is listed in the repos.  I'm not a fan of ubuntu's xfce setup out of the box so I usually choose plain xfce4.
Anyway you can try Ubuntu Eee, and if you don't like netbook remix simply install xfce4 and customize as you like.
[http://www.ubuntu-eee.com/](http://www.ubuntu-eee.com/)
Note I haven't tested the web-cam with this distro, but thats because I don't use it and have it disabled to save power.  Everything else works.

---

### Post by ZarathustraDK on 2008-09-28
> **henrimarc said:**
> Hello,

I have a problem : EEEpc 1000 loaded with Xandros.
I myself installed eeexubuntu 7.10 on it from a USB key.
Dual boot is ok.
Xandros still functions Ok : mail is ok, web connection are both ok : wireless and ethernet.

But when logged on in Ubuntu, there is no possible connection neither by wireless nor ethernet.

iwconfig says :
lo    no wireless extensions

no word about eth or ath.
What should I do ^
Thanks

Hey again, this one fixed it for me [http://www.array.org/ubuntu/setup901.html](http://www.array.org/ubuntu/setup901.html) . It's Ubuntu Hardy though, not eeeXubuntu. Still it's perfectly good and snappy with Compiz, bells and whistles enabled on my 901.

Cheers

---

