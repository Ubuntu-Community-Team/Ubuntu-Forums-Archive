---
title: "wahhh ubuntu will not work on new hp laptop"
date: 2008-08-17
forum: Hardware
---

### Post by donald7777 on 2008-08-17
Hello everyone. I recently had o replace my gateway mt6451 laptop, which I had no problems with ubuntu, to a new HP dv5-1003nr. Now I have tried to install or even boot a ubuntu cd but everything fails. I believe it has something to do with the new ati hardware in it (RS780m). I can not even get to the desktop. Ubuntu always stops at the run_program: '/sbin/modprobe' abnormal exit error.
Please help.

I disks I have tried.
ubuntu 7.04 live cd and Alt cd
7.10 live cd and Alt cd
8.04 live cd and alt cd
now dling 8.04.1 dvd
everyone stops at the nice error of run_program: '/sbin/modprobe' abnormal exit
I have tried the no acpi options and the generic.all_generic_ide=1 command (sorry if its typed wrong)

Im ready to go throw this laptop away.

---

### Post by Crafty Kisses on 2008-08-17
Can you give us your system specs?

---

### Post by scorp123 on 2008-08-17
> **donald7777 said:**
>  I have tried the no acpi options and the generic.all_generic_ide=1 command (sorry if its typed wrong) Try a 8.04 live CD and press F6 ... when GRUB shows its boot command line make sure you remove the entries "**quiet splash**" ... but please make sure you leave everything else intact.

When the Live CD boots now it will not show the Ubuntu logo screen, instead it will show Linux kernel messages. You should be able to see more details now and it should be easier to troubleshoot what is going on.

As for the parameters you tried: Please see this post:
[http://ubuntuforums.org/showpost.php?p=4207558&postcount=17](http://ubuntuforums.org/showpost.php?p=4207558&postcount=17)

The parameter is  **all_generic_ide** ... just that, no '=' signs or anything. But maybe that's not even the problem in your case, we'd need to see where the boot process is hanging to be sure.

---

### Post by donald7777 on 2008-08-17
ok i did that and heres what it give me. udevd-event[1626] run_program: '/sbin/modprobe' abnormal exit error.
here are the specs.

Product Name  dv5-1003nr  
Product Number  FE764UA#ABA 
Microprocessor  2.00 GHz AMD Turion X2 RM-70 Dual-Core Mobile Processor 
Microprocessor Cache  1 MB L2 Cache 
Memory  3072 MB 
Memory Max  Up to 8GB DDR2 (Up to 5 GB may not be available due to 32-bit operating system resource requirements) 
Video Graphics  ATI Radeon HD 3200 Graphics RS780M 
Video Memory  Up to 1406 MB 
Hard Drive  160 GB (5400 rpm) 
Multimedia Drive  Blu-Ray ROM with SuperMulti DVD±R/RW Double Layer 
Display  15.4" WXGA High-Definition BrightView Widescreen (1280 x 800) 
Fax/Modem  High speed 56K modem 
Network Card  Integrated 10/100 Ethernet LAN 
Wireless Connectivity  802.11b/g WLAN 
Sound  Altec Lansing speakers 
Keyboard  101-key compatible 
Pointing Device  Touch Pad with dedicated vertical and horizontal Scroll Up/Down pad 
PC Card Slots  One ExpressCard/54 slot (also supports ExpressCard/34) 
 
External Ports  5-in-1 integrated Digital Media Reader for Secure Digital cards, MultiMedia cards, Memory Stick, Memory Stick Pro, or xD Picture cards 
4 Universal Serial Bus USB 2.0 
1 VGA (15-pin) 
1 HDMI 
1 RJ-11 (modem) 
1 TV-Out (S-video) 
1 RJ -45 (LAN) 
1 eSATA 
2 headphone-out 
1 microphone-in 
1 notebook expansion port 3 
1 Consumer IR 
 
I have tried the command of all_generic_ide and the new one that the help says to use which is generic.all_generic_ide=1

---

### Post by donald7777 on 2008-08-17
YEAAAAAAAA I got ubuntu to install i downloaded the 8.04.1 release DVD and ubuntu installed perfectly. Only problem now is with the touch sensitive buttons I can not turn on my wireless card.

---

### Post by c2rjay on 2008-08-20
> **donald7777 said:**
> YEAAAAAAAA I got ubuntu to install i downloaded the 8.04.1 release DVD and ubuntu installed perfectly. Only problem now is with the touch sensitive buttons I can not turn on my wireless card.

Any success with the wireless card? Im just curious because i am about to buy the same laptop with almost the same specs.

---

### Post by donald7777 on 2008-08-20
Yes i got it to work. The only thing I found is the radeon 3200 HD has a few gaming problems, and the sound is a bit weird but will probably be fixed in a kernel update. Also you can not change the cpu speed yet. the cpu is too new.
How I had to install ubuntu is with the new release dvd 8.04.1 and it worked fine.

---

### Post by instantkarma on 2008-08-27
Donald, please share with us how you got your wireless button to work because I just installed ubuntu 8.04 on my new dv5z machine and the button wont work.

---

### Post by donald7777 on 2008-08-27
my button still doesn't work. but the wireless does. Im trying to find the link I used to get the wireless card working. try searching for atheros wireless card hp or something like that in the ubuntu forms, that's how I found it. Also I have noticed that high pitched sound comes from the speakers no matter if its disabled or headphones are plugged in. the sound is not loud but the frequency just drives me crazy. I have tried the new ALSA files but I could not get them to install properly. Also The new ATI Radeon 3200 HD drivers hates all 3d games right now, just warning you. Open Gl works great though.

---

### Post by instantkarma on 2008-08-28
> **donald7777 said:**
> my button still doesn't work. but the wireless does. Im trying to find the link I used to get the wireless card working. try searching for atheros wireless card hp or something like that in the ubuntu forms, that's how I found it. Also I have noticed that high pitched sound comes from the speakers no matter if its disabled or headphones are plugged in. the sound is not loud but the frequency just drives me crazy. I have tried the new ALSA files but I could not get them to install properly. Also The new ATI Radeon 3200 HD drivers hates all 3d games right now, just warning you. Open Gl works great though.

Can you give basic step by step instructions on how to get wireless on the hp pavillion dv5z running?
Thanks.

---

### Post by Bucky Ball on 2008-08-28
Hey, Donald.

> Also I have noticed that high pitched sound comes from the speakers no matter if its disabled or headphones are plugged in. the sound is not loud but the frequency just drives me crazy.You are could be experiencing a feedback loop. Your mic is on and playing back live through your speakers, mic picks up speakers noise and plays it back out the speakers ... and the beat goes on, if you know what I mean ... 

If you double click on your speaker icon you should see a gui for your sound. If you mute the mic, does the squealing stop? If so, that is the prob, not drivers. :)

---

### Post by fballem on 2008-08-28
You may find the following tutorial useful. The author attached as a zip file, which you will need to unpack somewhere. The hyperlink in the article was not working as of this morning.

[http://ge.ubuntuforums.com/showthread.php?p=4953480](http://ge.ubuntuforums.com/showthread.php?p=4953480)

I found the link useful for configuring an HP 9231ca laptop, including getting the wireless adapter light to work.

---

### Post by donald7777 on 2008-08-28
> **Bucky Ball said:**
> Hey, Donald.

You are could be experiencing a feedback loop. Your mic is on and playing back live through your speakers, mic picks up speakers noise and plays it back out the speakers ... and the beat goes on, if you know what I mean ... 

If you double click on your speaker icon you should see a gui for your sound. If you mute the mic, does the squealing stop? If so, that is the prob, not drivers. :)
its not feedback. I always have the mic muted. its like if you turn you speakers up really high and it picks interference thats high pitched thats what it sounds like.

---

### Post by Bucky Ball on 2008-08-28
> if you turn you speakers up really high and it picks interference thats high pitched

There must be an input happening for a feedback loop to occur. It doesn't happen out of thin air and the speakers themselves have no way of creating a feedback loop without an input. If you are turning your speakers up really high with no input happening (signal in) and they are making a high pitched noise you are right, that is not feedback but a problem with the speakers (honestly can't think what). Is there a mic plugged in or you have muted the mic *plug* (with no mic plugged in) but not the speakers on the screen of the laptop? The *in-built mic* on the computer itself would be what I am meaning here. :)

---

### Post by donald7777 on 2008-08-31
everything including the mic is disabled but still i get that sound. I also happens when i switch to xp but at such a low level it doesn't bother me.

---

