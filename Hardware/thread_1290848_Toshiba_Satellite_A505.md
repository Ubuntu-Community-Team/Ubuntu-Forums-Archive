---
title: "Toshiba Satellite A505"
date: 2009-10-14
forum: Hardware
---

### Post by CommonClone on 2009-10-14
Today I just bought a Toshiba Satellite A505 laptop from a big blue box store.  It was the display model so the manager gave me 10% off.  It seems that they are trying to get rid of all the laptops with Vista installed to make way for Win 7.  Anyways, I took it home and installed Ubuntu 9.04 right away.  

Everything works with no hassle!  I have been using Ubuntu since Dapper and I have never had such an easy installation experience.  No proprietary drivers, no weird video or wireless problems.  It was a beautiful experience.

Congrats to the devs, and congrats to Toshiba for building a laptop that linux works so wonderfully on.

---

### Post by milesfromnowhere121 on 2009-11-08
I just got a Toshiba A505 S6980 from Bestbuy and the wireless isn't working on the live CD of Ubuntu 9.10. Any ideas?

---

### Post by pablo.aguilar on 2009-11-16
Take a look at this page:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126)

The driver rtl8192se_linux_2.6.0010.1020.2009_64bit + Method 2 worked for me

---

### Post by Woodbadger on 2009-11-23
I have a Satellite M105-S1021 with XP and a Celeron M Processor and ATI chipset. I cannot get Ubuntu to install (either 8.10 or 9.10). It simply won't load. It starts and stalls with the following information:

Completing the Ubuntu installation.
For more installation boot options, press 'ESC' now. . .
(Countdown clock)
[Linux-bzImage, setup=0x3400, size=0x3b26e0]
[Initrd, addr=0x149a2000, size=0x57d098]

Any idea what's going on? I'm a relative newbie, so make an explanation detailed. Assume I know nothing.

---

### Post by poligarcia on 2009-12-07
I'm on a Toshiba Satellite A505-S6980 and this worked for me:

* Download the driver attached [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126/comments/28").
* Extract to a temporary folder.
* Switch to super user (sudo su).
* Run make and make install on the driver's directory.
* Restart your system.

---

### Post by el_iddler on 2009-12-11
hi, well i do all the steps you say and it work, but then in the wireless options apeear one signal with a rare name like if it  was a wireless signal, then my computer became to black, all i can see in the screen was balck and the mouse, that i can't move, so i have to restart.
what happened? can you help me please.
thanks

---

### Post by MichaelLam on 2009-12-17
Hi,

I'm also having the wireless receiver problem with the same laptop model (A505-S6980).

Is the black screen problem after using the  [driver]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126/comments/28") a one-off issue or is it systematic?

---

### Post by jeff_gaer on 2010-04-22
I just got a new toshiba a505 with windows 7, did the wubi install of 9.10. Everything seemed to go ok, the entries in grub are their as expected. but when I boot to linux, the screen goes blank. I was thinking the device was not supported but it looks like others did not have this problem. The init messages scroll off the screen to fast to read. Where to start?

---

### Post by zmjb1 on 2010-05-02
I have exactly the same issue, same computer and tried 9.10, 9.04 and 8.10
 
I see a new version, 10.04 and am going to try to see if by some chance this works. will let you know if I have any success.
 
 
 
> **jeff_gaer said:**
> I just got a new toshiba a505 with windows 7, did the wubi install of 9.10. Everything seemed to go ok, the entries in grub are their as expected. but when I boot to linux, the screen goes blank. I was thinking the device was not supported but it looks like others did not have this problem. The init messages scroll off the screen to fast to read. Where to start?

---

### Post by zmjb1 on 2010-05-02
Jeff,
Update. I installed Ubuntu 10.04 and the graphics issue is gone (ie, able to load Ubuntu without a black screen).
 
I still can not get teh wireless to work yet, it does not recognize my nework. I've still got some work to do. Any help one could offer would be appreciated. 
 
I know nothing aobut Linux, so please speak english. :)
 
I did do the:
 
lshw -C thing and did not see anything indicating it recognized my wireless card in the laptop.
 
> **jeff_gaer said:**
> I just got a new toshiba a505 with windows 7, did the wubi install of 9.10. Everything seemed to go ok, the entries in grub are their as expected. but when I boot to linux, the screen goes blank. I was thinking the device was not supported but it looks like others did not have this problem. The init messages scroll off the screen to fast to read. Where to start?

---

