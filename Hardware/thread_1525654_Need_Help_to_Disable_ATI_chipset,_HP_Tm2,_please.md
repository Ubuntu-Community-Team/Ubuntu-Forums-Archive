---
title: "Need Help to Disable ATI chipset, HP Tm2, please"
date: 2010-07-07
forum: Hardware
---

### Post by Mr. Teal'c on 2010-07-07
I have a HP Tm2 (the old version) with two video chipsets, a high power ATI  and a low power Intel. For Ubuntu (10.04 32-bit) I want to disable the ATI, so that it is "off", not making heat/ consuming power. I've seen this thread [http://swiss.ubuntuforums.org/showthread.php?t=1410752](http://swiss.ubuntuforums.org/showthread.php?t=1410752), but I can't figure out how to get it working. 

I could really use some help here (please) I usually can find my way around Ubuntu, but I can't seem to get this working. I need (and would very much appreciate) a simpleton's walk through of what I have to do, I've never done this before, so don't know what commands to use/ what they are. ](*,)

 I run " lspci -v" and get:
[PHP]01:00.0 VGA compatible controller: ATI Technologies Inc M93 [Mobility Radeon HD 4500 Series]
    Subsystem: Hewlett-Packard Company Device 3661
    Flags: fast devsel, IRQ 16
    Memory at c0000000 (32-bit, prefetchable) [disabled] [size=256M]
    I/O ports at 3000 [disabled] [size=256]
    Memory at e4400000 (32-bit, non-prefetchable) [disabled] [size=64K]
    Expansion ROM at e4420000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel modules: radeon[/PHP]Thanks in advance :)

---

### Post by Jojoba86 on 2010-08-24
*bump*

I have exactly the same problem, I'd also appreciate any advice on how to disable the ATi card, it makes my laptop run horribly hot and the battery life rubbish.

I've tried the 'lenovo' fix, but that just stopped Ubuntu from booting. I've no idea how to get vga_switcheroo working.

---

### Post by phaedrus54 on 2010-10-02
Try this link:

[http://ubuntuforums.org/showpost.php?p=7933876&postcount=11](http://ubuntuforums.org/showpost.php?p=7933876&postcount=11)

It worked for me.

If you try to follow it and can't, PM me and I'll try to help.

Cheers.

---

### Post by phaedrus54 on 2010-10-02
> **Jojoba86 said:**
> *bump*

I have exactly the same problem, I'd also appreciate any advice on how to disable the ATi card, it makes my laptop run horribly hot and the battery life rubbish.

I've tried the 'lenovo' fix, but that just stopped Ubuntu from booting. I've no idea how to get vga_switcheroo working.

PS - Switcheroo is my next project... :)

---

### Post by EmilioLargo on 2010-11-08
Hi folks,
I'm having roughly the same problem with my HP Touchsmart tm2, but I don't want to deactivate the ATI card permanently, just switch between Intel and ATI (if that's possible). I'm running a fresh install of 10.10
```
pepeg@Pegasus:~$ uname -r
2.6.35-22-generic
```and I think everything is working fine:
```
pepeg@Pegasus:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
01:00.0 VGA compatible controller: ATI Technologies Inc M93 [Mobility Radeon HD 4500 Series]
``````
pepeg@Pegasus:~$ dmesg | grep switche
[    4.898941] VGA switcheroo: detected switching method \_SB_.PCI0.OVGA.ATPX handle
[    5.091582] vga_switcheroo: enabled
``````
pepeg@Pegasus:/sys/kernel/debug/vgaswitcheroo$ ls
switch
```My question is how to switch between cards from command line. I know that in Ubuntu, there exists a graphical interface in the UCC but I'm running Kubuntu and unfortunately, in kubuntuforums.org, searching for "vga switcheroo" doesn't yield any results.

The above mentioned lenovo fix is not what I'm looking for since it is not my goal to shut down the ATI card completely. I assume the answer to my question is in here
[http://kerneltrap.org/mailarchive/git-commits-head/2010/3/4/28037](http://kerneltrap.org/mailarchive/git-commits-head/2010/3/4/28037)
but I can't figure out how to make use of it.

Thanks in advance for your help.

---

### Post by Faoesch on 2010-12-06
Hi Guys,
I've got a HP Touchsmart tm2 as well and my problem starts with the booting. I can't even get to the login screen. Or I'll better say it this way, it was working for about 5 restarts and after that it stopped. I think because it is booting with my ati graphic card and it looks like my kubuntu doesn't like to boot with the ati. 

So if you've got any solutions for this I'd be very very thankful :)

---

### Post by EmilioLargo on 2010-12-07
> **Faoesch said:**
> Hi Guys,
I've got a HP Touchsmart tm2 as well and my problem starts with the booting. I can't even get to the login screen. Or I'll better say it this way, it was working for about 5 restarts and after that it stopped. I think because it is booting with my ati graphic card and it looks like my kubuntu doesn't like to boot with the ati. 

So if you've got any solutions for this I'd be very very thankful :)

Hi Faoesch,
first question: which version of kubuntu are you using? 10.10?
Second question: are you using an external monitor? I sometimes experience the same problem after having used an external monitor. The solution is to disconnect the monitor and reboot the TM2 several times, kubuntu's log in screen usually shows up after the 2nd or 3rd reboot.
If this doesn't solve your problem, you may want to have a look at this documentation of Grub2, assuming that you are using a recent version of kubuntu, which offers detailed information on trouble shooting (see "Command Line and Rescue Mode")
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) 

On a related note regarding the discrete ATI graphics card in the TM2:
I managed to turn off the ATI card, but still, it seems to impossible to switch between cards. Shutting down the ATI can be achieved as intended by vga_switcheroo:
```
sudo chown "user" /sys/kernel/debug/vgaswitcheroo/switch
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```This turns off the card not in use, which is in my case the ATI - I don't know if that holds for all TM2. The corresponding commands for switching between cards don't have any effect, unfortunately.
Please note that the above commands have to be executed after each reboot, hence it is advisable to use a shell script.

---

### Post by Faoesch on 2010-12-08
> **EmilioLargo said:**
> Hi Faoesch,
first question: which version of kubuntu are you using? 10.10?

Yes, I'm using the 10.10
> **EmilioLargo said:**
> 
Second question: are you using an external monitor? I sometimes  experience the same problem after having used an external monitor. The  solution is to disconnect the monitor and reboot the TM2 several times,  kubuntu's log in screen usually shows up after the 2nd or 3rd reboot.
No, I've never used it with an external monitor. Well I just tried it now and guess what. it works... kinda strange I think. So I can't see anything on the laptop itself but at least I can navigate it. Strangley my touchscreen works as well xD.

Thanks in advance :)

---

### Post by EmilioLargo on 2010-12-10
Hi,
so, just to get this right: now, you are using an external monitor and you can see your desktop on the external monitor but not on the screen of the laptop? If no, I don't understand what you did ;-)
If yes, how is the external monitor connected? Via VGA port or HDMI? Are you sure you activated the laptop screen (K-Menu -> Settings -> System Settings -> Display and Monitor Settings, activate both screens)? Is the laptop screen at least listed in the "Display and Monitor settings"?

Cheers,
EmilioLargo

---

### Post by Faoesch on 2010-12-11
Sry for not being very concrete. So it works, when I'm having an external monitor connected via VGA. My screen on my laptop has to be switched on because when I start it shows only on my laptop screen. But as soon at it starts to start the kernel it goes black and the next thing I see is the login screen of kubuntu on my external monitor. Even my touchscreen works. So I can press on my laptop screen and it moves around on my external screen. So I still think it's the graphicscard. So I do think I have to find a way how to start my laptop without using the ATI.
Yes my laptop screen is listed there.

Thanks for the patience :)

---

### Post by diphda on 2010-12-11
Hi,
I have the newer TM2 with the Core i5 and hybrid graphics.
It happens quite often that the internal screen LEDs are switched off during boot. The only thing I need to do is switching it back on with fn+f3 or only f3 depending on the BIOS settings.

---

### Post by Faoesch on 2010-12-12
Firstly I think you meant f4 (at least on my keyboard) because it's the button if you have like multiple screens. Sadly, it didn't work. So I tried it with f3 as well (which is the brighterscreen-key) that one doesn't work AT ALL. Well, so I'm having a lot of troubles with my tm2.
A small list xD.
I can't use the right button
The screen is still black all the time
the ATI is still makes my laptop extremly hot
The resolution (maybe it's because I always have to use an external screen) changes to 1024x786 every time I restart my laptop

Well I think that are the worst problems I've got with my laptop at the moment. So I suppose you can think that it's impossible to work with it.

Thanks for any further suggestions :)

---

### Post by EmilioLargo on 2010-12-12
> **Faoesch said:**
> Firstly I think you meant f4 (at least on my keyboard) because it's the button if you have like multiple screens. Sadly, it didn't work. So I tried it with f3 as well (which is the brighterscreen-key) that one doesn't work AT ALL. Well, so I'm having a lot of troubles with my tm2.
A small list xD.
I can't use the right button
The screen is still black all the time
the ATI is still makes my laptop extremly hot
The resolution (maybe it's because I always have to use an external screen) changes to 1024x786 every time I restart my laptop

Well I think that are the worst problems I've got with my laptop at the moment. So I suppose you can think that it's impossible to work with it.

Thanks for any further suggestions :)

Regarding the right button:
It works (at least in my case) if you press VERY slightly on the lowest right corner of the touchpad; just touch it, do not press so hard that you hear the *click* of the touchpad. Also, scrolling with the touchpad works if you sweep with your finger along the right edge of the touchpad (and then at the lower end, there is the spot to hit for right-click).

Regarding resolution:
Yeah, 1024x768 is the standard res set after each reboot; it might be possible to set a standard for your specific monitor, but I don't know how that works.

Regarding ATI:
It sounds very strange since your laptop monitor is not broken (you see the bios messages during startup on it, right?), I don't see why there should be more trouble in your case than in mine. What is the output of the following command:
```
pepeg@Pegasus:~$ cat /sys/kernel/debug/vgaswitcheroo/switch
```
So we can at least check which graphics card is active after startup.

Regarding brightness of screen:
I can second that, adjusting screen brightness does not work, neither using hardware keys nor using KDE's software settings.

---

### Post by Faoesch on 2010-12-12
Thanks for all the advice.
Right button: Yeap it seems to work when I gently push on the right lower corner :)

ATI: 
```

cat /sys/kernel/debug/vgaswitcheroo/switch 
0: :Pwr:0000:01:00.0
1:+:Pwr:0000:00:02.0

```

Screen brightness:well that sucks

I just found a blog of "Fred" it looks like he's got a tm2 as well and wrote some scripts for it :) My problem is that I'm not that good at using linux so I can't really test if it works :P.
[http://linuxquirks.blogspot.com/search?updated-max=2010-10-30T08%3A51%3A00-07%3A00&max-results=7](http://linuxquirks.blogspot.com/search?updated-max=2010-10-30T08%3A51%3A00-07%3A00&max-results=7)

---

### Post by EmilioLargo on 2010-12-12
Hi,
just tried the thing about the touchpad in Fred's blog - it works (using his values) as he described it, but unfortunately it seems to deactivate the right button. Personally, I prefer having a right click than being able to put one finger on a button while navigating the cursor with a second finger.

@Faoesch
Ok, looks like your laptop is actually running with the Intel graphics (the "+" sign indicates that) but both graphics cards are powered. So, you should be able to deactivate the ATI card which reduces the heat pressure/fan noise (I described the method that works for me on the previous page).
To simplify matters: I attached a small script, download it to your computer (say, to your home directoy), replace "user" in the 4th line of the script with your username (without the quotes, edit it with your favourite editor like Kate), save the changes and then type the following at the command prompt (where you put the script, so e.g. in your home directory)
```
sudo ./ATI_OFF.sh
```and post the output here. If it shuts down the ATI card correctly and your are still not able to use your laptop screen, it is probably not due a problem with the ATI card...

---

### Post by diphda on 2010-12-13
Hi Faoesch,
I have some more Questions regarding the screen:
Did you check the monitor preferences? Did you see your screen? was it turned off or On?

There is a solution to activate the middle and right mouse buttons.
Just follow the instructions is the link:
[http://bigbrovar.aoizora.org/index.php/2010/10/10/how-to-enable-right-middle-click-on-clickpads-ubuntu-10-10/](http://bigbrovar.aoizora.org/index.php/2010/10/10/how-to-enable-right-middle-click-on-clickpads-ubuntu-10-10/)
You can also activate horizontal mouse scrolling in the Mouse/touchpad preferences, which uses the  lower edge for scrolling.

Regoarding EmilioLargo's ATI_OFF.sh script: You need to make it executable to run (easy way: right click on the file - properties - permission tab - activate "allow executing file as program)

---

### Post by EmilioLargo on 2010-12-13
@diphda
Thanks for the link, I'll try that some time soon.
Regarding the script: right, forgot to mention that, thanks for the hint...

---

### Post by diphda on 2010-12-13
@EmilioLargo
I have another link, maybe this works with vga-switcheroo and KDE:
[http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/)
but you could also just use the terminal and manually log off/on
or make custom launchers with shell scripts for switching to either card

---

### Post by Faoesch on 2010-12-13
@diphda
> I have some more Questions regarding the screen:
Did you check the monitor preferences? Did you see your screen? was it turned off or On?
Yeap it is listed in the display section. Thanks for the button problem. I'd love to try it but I'll discribe the problem I've got a bit further down.

@EmilioLargo
Thanks for the Script and it worked. I acctually could see stuff on my laptop. So I was thinking:"Why should I always have to make the script execute?" So what I did was I listed it in the PRE-KDE Booting section and rebooted my laptop to see if it works propperly.
Guess what? Now I can't get past the login screen. I can type my password in and then it starts to log in but after a sec the mouse changes to a cross and I come back to the login screen.
I wanted to see if I actually could change it back with a live usb but I failed.
So now I'm having a computer where I can't even go past the login screen xD. It gets worse and worse.

Faoesch

---

### Post by diphda on 2010-12-13
@ Faoesch
still got your live usb/cd?
boot it into a live session
open dolphin - make hidden items visible, browse to your home folder on your notebook and delete script in the /.kde4/Autostart folder. (I don't use KDE so maybe the name is different, you have to look. If you don't find it you could delete the whole /.KDE folder which will be rebuilt the next time you log in. If you delete the folder you will lose your custom KDE settings!!
Now you should be able to login again.
The problem with the script is that it needs root password to execute.
Please try this and afterwards I can tell you where and how to put the script command
good luck

---

### Post by diphda on 2010-12-13
@ Faoesch
Hopefully you got your system working again here is where to put the vga-switcheroo command:

use alt+F2
type: ```
kdesu kate /etc/rc.local
```this will open a file which is read when ubuntu starts up.
scroll down till you see: exit 0
before this line insert:
```
chown put-your-username-here /sys/kernel/debug/vgaswitcheroo/switch
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```Save the file and close Kate.

What this does:
the first line changes the ownership of the file switch which is located in /sys/kernel/debug/vgaswitcheroo/ to you (you need to substitute put-your-username-here with your name). Now you can change the mode of your videocards without using sudo. You don't need this line if you don't want to use the ati-card

The second line switches off the ati-card.

Restart your computer and it should work.

---

### Post by Faoesch on 2010-12-13
I managed to delete the .kde file. Was a bit difficult because I couldn't delete it with sudo so I deleted it as root. Was firstly very lucky that I didn't delete the wrong file and secondly that my friend told me about "sudo su" xD. Now my screen works. Which is f**king awesome. 
Thanks everybody who helped me get there :).

Now I just have to do the small stuff like, the touchpad and the turning of the screen :). I'll try that myself but if I get a problem. At least I know where to ask :)

Thanks one more time

---

### Post by Faoesch on 2010-12-13
I suppose I cheered to early because I've still got a problem. So that you'll know what I've just found out I'm trying to summarize what I did.

So as I restarted my laptop the screen on my laptop turned on as supposed (the resolution is wrong but I suppose that's cos of the external screen). Then I plugged the external screen off and it still worked, which wasn't really a surprise.
So I thought I wanna try to restart my laptop to see what's gonna happen. So... the laptop screen didn't turn on. So I tried to plug it in to the external screen which didn't do anything. I could even log in (I heard the login sound). I restarted my laptop one more time but with my external screen plugged in from the beginning again and it worked again.

Allow me to summarize. My screen doesn't work when I don't have my external screen plugged in but works when it is.

I hope I could help you with the information :)

---

### Post by Faoesch on 2010-12-17
Hi Together :),
I got some new updates from my laptop :P. So I actually can work with my laptop now :). Which is great thanks to you guys. It still has problems with the booting but if it doesn't show anything I just reboot and try again. Eventually it works :).
If though anyone has a new idea then I'd appreciate to hear about it :) Thanks

Faoesch

---

### Post by kristera1 on 2010-12-30
Hi
I also have a similar problem and have been having it since I bought my TM2.
I found a workaround (which annoying as it is I have been living with now for quite sometime) - 
I disconnect the power cable, boot into Windows (which I use for this purpose only btw), restart (do not even have to login just reboot from the login screen) (making sure I do not use shutdown), then select Kubuntu from the GRUB menu and it works.
I have rc.local setup to disable the ATI graphics card using vgaswitcheroo and I have a script for adjusting the screen brightness to enable me to save power. Whenever I try to boot with the power cable I have a lot of problem so use the above method all the time nowadays.
I was looking through the Lucid TM2 testing thread as well as keeping my eyes open but have not been able to find anything more about this so I have assumed that this is specific to my model in combination with KDM. When I did a fresh install of 10.10 Ubuntu it worked for a while and when I booted Mint 10 recently it also seems to cope better. My HP TM2 is a 1010ea BTW.
Faoesch I hope this can be of some help and if someone out there has some ideas it would be highly appreciated.

rgds Krister

---

### Post by riyasmp on 2011-01-16
.

---

### Post by riyasmp on 2011-01-16
.

---

### Post by riyasmp on 2011-01-16
hi guys I have more or less the same problem with my HP 3150sa laptop (ubuntu 10.10 64 bit). 

When I ask vga switcheroo (from UCC) to switch to high perfomance graphics card it logs me out and in again and I loose my compiz. I checked UCC>HARDWARE>System information>display after the switch which doesn't  show up the ATI card at all.

I tried this link but no joy

[http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/)

please find the following info


rmp@ocn:~$ uname -r
2.6.35-24-generic
rmp@ocn:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]
rmp@ocn:~$ dmesg | grep switche
[   13.504555] VGA switcheroo: detected switching method \_SB_.PCI0.GFX0.ATPX handle
[   13.506253] vga_switcheroo: enabled
rmp@ocn:~$ cat /sys/kernel/debug/vgaswitcheroo/switch 
0:+:Pwr:0000:00:02.0
1: :Pwr:0000:01:00.0

---

### Post by Michael S Corigliano on 2011-01-25
Hey guys, believe it or not, a quick fix for when your screen "doesn't work" is to actually close the lid and open it. This always works for me when I boot up to a blank screen. Hope it works for you!

---

### Post by riyasmp on 2011-05-15
hi guys

I know that its quiet an old post. I am just trying to get some more help from the form if it can sort out my problems with the issue.

At present I am using Ubuntu 10.10 on my hp fv6 3150sa which has got a switchable graphics ATI HD 5000 series with intel. 

I installed ubuntu control centre so that I can switch the chip set with the vga switcheroo. the one thing what I noticed was when I choose my high perfomance graphic i loose my compiz efffects. switching back to the power saver GPU makes the compiz work again.

as i have been seeking help for this at difffret place and no real help, please answer some of my queries

1) does switching really works on ubuntu with vgaa switcheroo? or is it just the one card which could work on ubuntu?

2) If I can successfully install fglrx while switching the card to intel which driver is supposed to make the intel one? if there is a another driver exist for intel does this vga switcheroo programe off load and upload the required driver automatically?

3) my laptop is heating up more when i use ubuntu than when I use win 7, is that something related to it.

with regards

---

### Post by colorprint on 2011-08-11
Have somebody tried the new fglrx drivers with switching?
[http://en.gentoo-wiki.com/wiki/Fglrx-hybrid-graphics](http://en.gentoo-wiki.com/wiki/Fglrx-hybrid-graphics)
It should works since April 2011, but I can't get it working :(

---

