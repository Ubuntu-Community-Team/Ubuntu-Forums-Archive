---
title: "ATI radeon HD 3450"
date: 2008-06-20
forum: Hardware Team
---

### Post by anilmax88 on 2008-06-20
Guys i have a strange problem i had a d101ggc mobo with pentium D 2.8 ghz cpu it used to rum ubuntu 8.04 easily 
now
i purchased a ATI HD3450 card
windows has no probs
but ubuntu couldnt display anything
now when i insert the live CD
even it cant boot up as 
after the splash screen i get no picture on my monitor it displays "sync out of range " man i want to install ubuntu badly but the stranger part is if i disable m,y graphic card from BIOS and switch to onboard it runs fine 
what to do please help me!!!!!!!!!!!1

---

### Post by gzambran on 2008-08-18
Any luck?

I just purchased the same video card and was planning on installing Ubuntu. I guess this may not happen after all.

---

### Post by uhappo on 2008-08-19
I'm receiving my new laptop tomorrow and it has ATI Radeon HD3450.

So any news/tips/success stories would be welcome...

---

### Post by axel1973 on 2008-09-02
any news on this problem ? does it run meanwhile ?

just a guess.. what monitor u have got ? i mean.. u tried to force it using lower resolution/screen refresh rate etc ?

---

### Post by uhappo on 2008-09-08
My laptop is working wonderfully in Ubuntu. Just enable restricted drivers for ATI and everything is smooth. Also WLAN is working 100% with madwifi.

---

### Post by roro100 on 2008-09-17
> **uhappo said:**
> My laptop is working wonderfully in Ubuntu. Just enable restricted drivers for ATI and everything is smooth. Also WLAN is working 100% with madwifi.

Thanks Uhappo for your comment, you gave me some hope. I just orderd dell Studio 15 with ATI HD3450 card. I hope it will work with Ubuntu 7.10 or 8.04. I will let you know when my laptop arrives from Dell.

---

### Post by erlguta on 2008-09-30
Please can you comment on details of how this card works in ubuntu?.
Because I am thinking of buy it.
Thank you.

---

### Post by roro100 on 2008-10-13
> **erlguta said:**
> Please can you comment on details of how this card works in ubuntu?.
Because I am thinking of buy it.
Thank you.

I report on my HD 3450 that it is working fine since I got my Dell Studio 15. Like Uhappo said, you need to activate it in restricted drivers. Once you do that, and reboot, it gives no problem. Although there were couple of glitches when I tried to change my defualt login screens (splash screens?) to one of those. It kicked back to the lower resolution mode (no hardware acceleration). I I had to reanable my card again in the restricted drivers and switch back to a "safe" login screen. Another time I had to restart in safe mode - that was when I tried to use Envy to download ATi driver and isntal it for me. I thought it would be better than the fglrx driver. Envy replaced my fglrx? driver with mesa driver = no acceleration. So I had to uninstall Envy, remove offending packages in safe mode and then restore the fglrx driver. Since then no problems. Mind you all problems were caused by my experimenting with Envy and different login splash screens.

---

### Post by uhappo on 2008-10-15
I haven't done any experimental things with my ATI, because it works so well.

Well, I haven't tried HDMI yet, but for my quite basic needs it works very well.

---

### Post by uhappo on 2009-01-03
HDMI is not working ATM, I get no picture on another screen. Well, I get picture, but it's digital mess. Mouse cursor is working correctly, though, but that's not enough!

---

### Post by uhappo on 2009-03-22
Bump and a question:

Is HDMI working for everyone? I've tried 1920x1080-monitors with HDMI-connection, but picture quality is poor. But when I try it with VGA-connection, everything is ok.

What's up with this HDMI? I've tried it with Ubuntu 8.10, 9.04 (with open drivers and proprietary) and also in Windows. Same with all systems. So, either it's my laptop&HDMI, bad cable or somethings mysterious.

---

### Post by molder on 2009-03-23
I had to upgrade to the latest ATI driver:

[http://wiki.cchtml.com/](http://wiki.cchtml.com/)

To get sound working I used this:

[http://www.mythtv.org/wiki?title=AllensDigitalAudioHowto](http://www.mythtv.org/wiki?title=AllensDigitalAudioHowto)

---

### Post by Maheriano on 2009-03-24
Marking this for when my Dell arrives.

---

### Post by Willleung on 2009-03-29
> **anilmax88 said:**
> Guys i have a strange problem i had a d101ggc mobo with pentium D 2.8 ghz cpu it used to rum ubuntu 8.04 easily 
now
i purchased a ATI HD3450 card
windows has no probs
but ubuntu couldnt display anything
now when i insert the live CD
even it cant boot up as 
after the splash screen i get no picture on my monitor it displays "sync out of range " man i want to install ubuntu badly but the stranger part is if i disable m,y graphic card from BIOS and switch to onboard it runs fine 
what to do please help me!!!!!!!!!!!1

Hey I had exactly the same problem with the 3450, couldn't even boot into the OS or just reinstall (off LiveUSB)

Anyone got it to work?

---

### Post by jc_anthro on 2009-05-03
I've got a Dell studio with an ATI 3450.  I've tried just about everything.  Drivers, flgrx, restricted driver, OSS versus Alsa, reloading sound software, the lot.  I cannot get this $%&^*()$#&* to work.  I was hoping that jaunty would somehow deal with this as a bug, but no such luck.

After a lot of cruising forums it appears there are definitely issues with this card, especially in the Dell.  This pisses me off because I stupidly thought, while buying a computer in a rush that Dell (after their recent lovefest with Ubuntu/Linux) would not release a mainstream computer with such manifest difficulties.

It doubly gets me because I have to leave vista on until I can get this resolved.  I would have thought that the community would try and address these bugs as a priority because it really does affecty perceptions of LINUX when there are such issues with mainstream hardware.

The closest I have to coming to a solution is that when I like at device properties it seems that the computer is trying to use the Intel sound card to run the ATI sound.  This maybe creating some sort of conf;lict.

If anyone has a script for switching this off and getting it to use the ATI driver for sound please let me know. (nothing to complex please, still relative newbie).

---

### Post by Aen107 on 2009-06-14
> **uhappo said:**
> Bump and a question:

Is HDMI working for everyone? I've tried 1920x1080-monitors with HDMI-connection, but picture quality is poor. But when I try it with VGA-connection, everything is ok.

What's up with this HDMI? I've tried it with Ubuntu 8.10, 9.04 (with open drivers and proprietary) and also in Windows. Same with all systems. So, either it's my laptop&HDMI, bad cable or somethings mysterious.

The same situation here.
In Kubuntu the situation is even worse: After the proprietary driver is installed, the screen becomes black with some strange red dots. 

Can any fix be expected? Otherwise, I am going to sell my ati card to get a nvidia card.

---

### Post by Aen107 on 2009-06-14
> **Aen107 said:**
> The same situation here.
In Kubuntu the situation is even worse: After the proprietary driver is installed, the screen becomes black with some strange red dots. 

Can any fix be expected? Otherwise, I am going to sell my ati card to get a nvidia card.

Now, I have a solution, which works quite well for me: Using Ubuntu 8.04, video quality is excellent. Performance is not so good though: Watching a 1080p movie with my Asus EAH3450 uses about 70-80% of my Dual Core @ 2.5Ghz, which is very high. Under winXP, users report a cpu usage of about 10%. 
After doing some research on this forum I think that X Server 1.6 is the reason why my ATI card is not supported properly in Jaunty.

---

### Post by whitethunder on 2009-07-25
Hi guys, 

When I installed the Asus EAH 3450 card on my Ubuntu 9.04 PC, it didn't recognize the card after the first boot. The graphics quality was awful, however, after I went to the hardware drivers menu, it found a hardware driver for it. I installed it and things seem to be good at the beginning but the scan rate or refresh rate of the monitor is still awful. Opening a window takes 10 seconds and I see how the display is refreshed frame by frame! 

Do you know any way to fix this problem?

Thanks

---

### Post by adm1968 on 2009-10-21
> **whitethunder said:**
> Hi guys, 

When I installed the Asus EAH 3450 card on my Ubuntu 9.04 PC, it didn't recognize the card after the first boot. The graphics quality was awful, however, after I went to the hardware drivers menu, it found a hardware driver for it. I installed it and things seem to be good at the beginning but the scan rate or refresh rate of the monitor is still awful. Opening a window takes 10 seconds and I see how the display is refreshed frame by frame! 

Do you know any way to fix this problem?

Thanks

[FONT="Georgia"]According to that cute little programme called sysinfo, I have an ATI Radeon HD 3450, which is the only regular cause of system freeze in my Ubuntu 9.04 installation. It does bother me, but have found no fix as yet ... [/FONT]

---

### Post by hedleylo on 2010-02-25
i know this is a long time since that last post, but i have an asus 3450, and it works under 9.10, using the ati proprietary drivers, but i can't enable visual effects, and visuals can sometimes be choppy (ie. when i move windows around, they don't move smoothly at times).  has anyone found better drivers than the ati proprietary that offer better performance and support?

---

### Post by QiangLi on 2010-03-11
I am using Laptop with ATI RADEON HD3450, on which OS wubi9.1 is runing, everything is OK.

---

### Post by QiangLi on 2010-03-12
but when I want to use Gazebo(robot 3D simulator), the default graphic card driver does not work, so I update the FGLRX driver. it works well.

---

### Post by megabyte1234 on 2010-09-03
Hi guys,

I've got the same problem on a custom-built computer with  the ATI Radeon HD 3450 card.
What i did to get ubuntu is install with cd from karmic koala (9.xx) and then upgraded all to 10.04, but the only thing not working is my bootsplash. hope this helps.

EDIT: Forget to say that i have an  old monitor, Hansol 730e crt.

---

