---
title: "ASUS N550JV - battery not charging"
date: 2013-09-26
forum: Hardware
---

### Post by Aqlor on 2013-09-26
Just got Ubuntu on my new ASUS N550JV, I am having however some problems.

The most disturbing problem is that the battery is not charging and the battery LED is blinking orange.

** ls /proc/acpi/ ** does NOT list any battery

** acpi ** says "Battery 0: Unknown, 0%"

I updated to Linux 3.11.0-031100-generic, the problem is unchanged.

---

### Post by Kirboosy on 2013-09-26
Was the battery charging under Windows or did you not test it?

Check the BIOS/UEFI and make sure that the laptop is set to charge. Some laptops allow you to tell the laptop to not charge the battery when its plugged in.


Hope that helps!
~Caboose

---

### Post by Aqlor on 2013-10-06
Sorry for taking so long to reply.


No, the battery does not change under windows, ubuntu or any other OS I've tried (tried some live versions)

How can I check the UEFI to see if it is set to charge?

Thank you for your reply

---

### Post by Kirboosy on 2013-10-07
You should be able to shut down the computer all the way and when you turn it back on (when the Asus logo appears) press F2 a couple of times.

I'm starting to believe that the battery or some piece of hardware is wrong with the laptop but checking the BIOS will make sure that there isn't any software preventing it from charging. The Amber blinking light probably means something is wrong with the battery or charging circuit. 

[Battery Troubleshooting ]("http://support.asus.com/Troubleshooting/detail.aspx?SLanguage=en&p=3&m=N550JV&s=529&hashedid=dad5aYI8mC6sfoNV&os=36&no=1800")

You might try updating your BIOS but that is risky and only a last resort. Also you will only be able to update the BIOS from a windows computer.

Hope that helps!
~Caboose

---

### Post by Aqlor on 2013-10-07
I've already updated the BIOS, and the blinking was gone for a while and the computer was charging. 

But this was only temporally, the problem is now back. I've tried, in desperation, to "update" the BIOS again, to the same version so it could reset or something but that is not possible unless it is a newer version.

---

### Post by Kirboosy on 2013-10-07
How old is the laptop? If its still under warranty you might want to contact Asus about it.

If its out of warranty you might want to try getting a new battery online. 


Hope that helps!
~Caboose

---

### Post by Aqlor on 2013-10-07
The laptop has just a few weeks, the problem is I can't get it back to warranty as it is my work computer.

I e-mailed ASUS and looks like this problem is not unusual with Linux, they told me to resit the battery, but I would lose the warranty.

---

### Post by Alexandru_Ionescu on 2013-10-08
> **Aqlor said:**
> The laptop has just a few weeks, the problem is I can't get it back to warranty as it is my work computer.

I e-mailed ASUS and looks like this problem is not unusual with Linux, they told me to resit the battery, but I would lose the warranty.
Two things you should know about:

[LIST=1]
[*]This laptop does not charge the battery if its charge level is above or equal to 95%. (if it has 98% charge it will not charge the battery, at 94% will charge back to 100%)
[*]If you decide to open the unit in order to reseat the battery, you will not loose the warranty. The only seal this unit has is on the cooling assembly, which you won't have to touch. You do need a special screwdriver - with a Torx T5 head - which you can buy at the hardware store if you don't own one already. You can find pictures of what's inside the unit [notebookcheck]("http://www.notebookcheck.net/Review-Asus-N550JV-CN201H-Notebook.98311.0.html"), including the battery. When opening the bottom lid, gently pull the lid on one side while also pushing it from the side - the lid has plastic clips on each side that need to be unhooked. Repeat the process on the other side. It' really easy once you get the hang of it, but first time requires a bit of patience.
[/LIST]
 
I hope the info helps, best of luck.

PS: I'm not a forum user, stumbled upon your thread by accident. Might not reply in the near future :)

---

### Post by Aqlor on 2013-10-08
Thank you Alexandru,

1. My battery is now at 68% so that is not the case.
2. I will consider opening it, I have some Torx screwdrivers I hope one of them is the right size.

I will post later.

---

### Post by benberg00 on 2013-12-04
Did you ever solve this problem?

I have a very similar issue with my N550JV.

Battery was charging fine under Windows8, then I installed Ubuntu 12.04 alongside Win8.

Now amber battery indicator light flashes constantly, and the battery won't charge under either either win8 or Ubuntu!!

Did the Ubuntu install somehow kill the battery charging circuit?

If this is permanent damage then I could return the computer in the next few days.  So I appreciate any responses ASAP!!

B

---

### Post by Aqlor on 2013-12-04
Actually I have, but I do not recommend it.

By accident I left my laptop discharging, when I got back to it it was already turned off. I thought that from that moment since, I would never be able to charge it back and I would have lost every precious minute of battery I would have during a black-out.

Weirdly enough, once I connected the charger, the indicated turned solid amber and it started charging normally, I thought it was a dream!


This has happened to me one more time and I have "solved" it the same way, I left it discharge until it would power off and then connect back the charger.


Why don't I recommend you doing this? Well, because of the risk associated with it...

---

### Post by benberg00 on 2013-12-04
At least 1 other documented case of this same issue:

[http://www.linuxine.com/story/fedora-distroying-asus-n550jv-battery](http://www.linuxine.com/story/fedora-distroying-asus-n550jv-battery)
[COLOR=#000000][FONT=arial]I bought a new ASUS N550JV-DB72T laptop and after installing Fedora and using it for like a day it starting saying that there is no battery installed and the battery LED is blinking orange! After rebooting the machine both Windows and Fedora see the battery but they won't charge it. Even when the laptop is turned off it still won't charge (i think it chargers very very slowly) and the battery LED is always blinking orange with or without the charger, only stops when the laptop is turned off and the charger is unplugged. After sometime and for unknown reason while the laptop was turned off ([/FONT][/COLOR][HowTos]("http://www.linuxine.com/HowTos")[COLOR=#000000][FONT=arial])[/FONT][/COLOR]

---

### Post by cire8312 on 2013-12-30
> **Caboose885 said:**
> You should be able to shut down the computer all the way and when you turn it back on (when the Asus logo appears) press F2 a couple of times.

I'm starting to believe that the battery or some piece of hardware is wrong with the laptop but checking the BIOS will make sure that there isn't any software preventing it from charging. The Amber blinking light probably means something is wrong with the battery or charging circuit. 

[Battery Troubleshooting ]("http://support.asus.com/Troubleshooting/detail.aspx?SLanguage=en&p=3&m=N550JV&s=529&hashedid=dad5aYI8mC6sfoNV&os=36&no=1800")

You might try updating your BIOS but that is risky and only a last resort. Also you will only be able to update the BIOS from a windows computer.

Hope that helps!
~Caboose


Actually, you have to hit F2 prior to the ASUS logo appearing (at least on the brand new (Dec 20th 2013) N550JV-DB72T) .   What works well is you hit the power button and then as soon as the keyboard backlight lights up, hit the F2.   It is well before the ASUS logo appears.    Took me a while of fretting before I figured that out.

This seems to be an intermittent problem with the ASUS batteries.   There have been a few reports of the batteries behaving this way.   I've experienced it as well but haven't figured out the workaroud yet.   There are reports that one needs to disconnect the battery.   This also jives with battery reconditioning that I've read about under Windows when the laptop has exhibited the same behaviour.

We haven't figured out what is going on yet.   And it doesn't happen frequently enough to cause us to figure out what it is...

---

### Post by cire8312 on 2013-12-30
> **Aqlor said:**
> Actually I have, but I do not recommend it.

By accident I left my laptop discharging, when I got back to it it was already turned off. I thought that from that moment since, I would never be able to charge it back and I would have lost every precious minute of battery I would have during a black-out.

Weirdly enough, once I connected the charger, the indicated turned solid amber and it started charging normally, I thought it was a dream!


This has happened to me one more time and I have "solved" it the same way, I left it discharge until it would power off and then connect back the charger.


Why don't I recommend you doing this? Well, because of the risk associated with it...


First, what risk?  These are Lithium-Ion batteries so they need to be fully discharged every once in a while.   From [http://www.techrepublic.com/blog/five-apps/five-tips-for-extending-lithium-ion-battery-life/](http://www.techrepublic.com/blog/five-apps/five-tips-for-extending-lithium-ion-battery-life/):

> 
[COLOR=#333333][FONT=Helvetica Neue]There is one exception. Battery experts suggest that after 30 charges, you should allow lithium-ion batteries to almost completely discharge. Continuous partial discharges create a condition called digital memory, decreasing the accuracy of the device's power gauge. So let the battery discharge to the cut-off point and then recharge. The power gauge will be recalibrated.
[/FONT][/COLOR]


Basically, by accident, you did part of what the following post talks about is needed to work with a flashing battery/battery not charging condition: [http://www.youtube.com/watch?v=Lx62t6qZ34U](http://www.youtube.com/watch?v=Lx62t6qZ34U)

Basically, the missing piece is actually disconnecting the battery and powering the laptop back up.   I suspect that this causes the battery controller (in the laptop) to reset itself so it starts the calibration process over.   For some reason this then allows the battery charging circuits to start back up.   Sounds like a fail safe to me.

I'm in the process of working through these procedures as we speak becaus I have a brand new ASUS N550JV-DB72T that has the flashing orange battery light problem.

---

### Post by ziro360 on 2013-12-31
> **cire8312 said:**
> First, what risk?  These are Lithium-Ion batteries so they need to be fully discharged every once in a while.   From [http://www.techrepublic.com/blog/five-apps/five-tips-for-extending-lithium-ion-battery-life/](http://www.techrepublic.com/blog/five-apps/five-tips-for-extending-lithium-ion-battery-life/):




Basically, by accident, you did part of what the following post talks about is needed to work with a flashing battery/battery not charging condition: [http://www.youtube.com/watch?v=Lx62t6qZ34U](http://www.youtube.com/watch?v=Lx62t6qZ34U)

Basically, the missing piece is actually disconnecting the battery and powering the laptop back up.   I suspect that this causes the battery controller (in the laptop) to reset itself so it starts the calibration process over.   For some reason this then allows the battery charging circuits to start back up.   Sounds like a fail safe to me.

I'm in the process of working through these procedures as we speak becaus I have a brand new ASUS N550JV-DB72T that has the flashing orange battery light problem.

Any news? I had the same problem today and notice that a new bios update was available that wasn't instaled yet. After flashing the problem was gone.

---

### Post by andrey_ on 2014-01-02
I have the same problem with Ubuntu 12.04 , I had to drain the battery to solve the issue , with Ubuntu 13.10 all ok. 

Hope somebody was able to found solution...

---

### Post by roblopes on 2014-01-12
> **andrey_ said:**
> I have the same problem with Ubuntu 12.04 , I had to drain the battery to solve the issue , with Ubuntu 13.10 all ok. 

Hope somebody was able to found solution...

What I've discovered is using the USB port next to the mini DVI port causes random problems with the battery. I use a 7 port USB 3.0 powered hub and had it plugged into that USB port on the laptop. Randomly on powerup the fans will run 100% and the battery indicator will flash orange/amber. The N550JV will NOT charge but will run under AC or until the battery has drained.

The solution:
1. Remove the T5 Torx screws from the bottom to access the battery.
2. Remove the battery.
3. Plug in the AC power and turn on the laptop.
4. Shutdown the laptop and put the battery pack back in and you are good to go.

The battery will NOT reset by just taking the battery out and re-seating it. I've tried, it doesn't work. You have to cycle the AC power first.

DO NOT USE THE USB Port next to the Mini DVI for devices that have external power supplied to them.

As stated, it's random.

I now plug the USB 3.0 powered 7 port HUB to the USB port on the laptop next to the 3.5mm headphone out and I've not had any problems what so ever.

Hope this helps.

Ubuntu 13.10 x64 secure boot
Samsung EVO SSD

This Asus N550JV (non-touch) rocks on Ubuntu!

---

### Post by riccardo.noc on 2014-01-13
Hi all,
I have the same problem. I bought the ASUS N550JV and after few days, after installing Kubuntu 13.10, the battery died. Tomorrow I'll open the pc... let's see the result :(

---

### Post by riccardo.noc on 2014-01-14
> **roblopes said:**
> 
The solution:
1. Remove the T5 Torx screws from the bottom to access the battery.
2. Remove the battery.
3. Plug in the AC power and turn on the laptop.
4. Shutdown the laptop and put the battery pack back in and you are good to go.


DONE AND SOLVED. It works :) Orange led stopped to blink. Thank you.:D

---

### Post by cire8312 on 2014-01-15
> **roblopes said:**
> What I've discovered is using the USB port next to the mini DVI port causes random problems with the battery. I use a 7 port USB 3.0 powered hub and had it plugged into that USB port on the laptop. Randomly on powerup the fans will run 100% and the battery indicator will flash orange/amber. The N550JV will NOT charge but will run under AC or until the battery has drained.

The solution:
1. Remove the T5 Torx screws from the bottom to access the battery.
2. Remove the battery.
3. Plug in the AC power and turn on the laptop.
4. Shutdown the laptop and put the battery pack back in and you are good to go.

The battery will NOT reset by just taking the battery out and re-seating it. I've tried, it doesn't work. You have to cycle the AC power first.

DO NOT USE THE USB Port next to the Mini DVI for devices that have external power supplied to them.

As stated, it's random.

I now plug the USB 3.0 powered 7 port HUB to the USB port on the laptop next to the 3.5mm headphone out and I've not had any problems what so ever.

Hope this helps.

Ubuntu 13.10 x64 secure boot
Samsung EVO SSD

This Asus N550JV (non-touch) rocks on Ubuntu!

I've run all this by my h/w guy who used to run one of Apple's h/w repair units.   And he says it is a problem with the Power Manager h/w that controls how the laptop is powered and controls the battery charging circuits.   Something is getting out of wack and the PM is erring on the side of caution rather than changing a Li-Ion battery pack in a way that could cause problems.

The "fix" is basically resetting the Power Manager.  Normally when the lap top is shutdown, it gets power from the battery.  So one needs to remove both the battery as well as AC power to get the PM to reset.

I've done the procedure where I simply remove the battery, (no AC power applied), and then reinsert the battery and this has also fixed the flashing orange (charge) LED.  You have to make sure that enough time has gone by for the Power Manager to actually reset.

It is more reliable to remove the battery and then plug in the AC.   But the key thing is to get the PM to reset.

---

### Post by kevin45 on 2014-01-18
I just encountered this problem today. I am running Manjaro, with the latest Linux kernel 3.13. I own the Asus N550JV-DB72T and have had Linux on it for about a month (having bought it around that time). It would seem to me that this problem is distro independent, and is a common problem with this model of laptop when in conjunction with Linux.

Tomorrow I will be attempting the above procedures and reporting my findings, but would be more interested in knowing what is causing this to happen in the first place.

I will say that I did in the past weeks have an external USB (that I use for custom ISO testing) plugged into another USB port. Today I plugged it into the USB port nearest the mini Display Port. When I went to use my laptop a few hours later, I was greeted with my fans on full blast and a laptop that would not charge with a blinking orange indicator light. Nice.

**EDIT: I can now confirm that opening the laptop up, removing the battery, plugging it in and turning it on serves as a remedy to the problem. Replacing the battery afterwards will allow the laptop to be used as normal (plugging in and charging work again).**

---

### Post by 20daniele10 on 2014-01-25
> **roblopes said:**
> What I've discovered is using the USB port next to the mini DVI port causes random problems with the battery. I use a 7 port USB 3.0 powered hub and had it plugged into that USB port on the laptop. Randomly on powerup the fans will run 100% and the battery indicator will flash orange/amber. The N550JV will NOT charge but will run under AC or until the battery has drained.

The solution:
1. Remove the T5 Torx screws from the bottom to access the battery.
2. Remove the battery.
3. Plug in the AC power and turn on the laptop.
4. Shutdown the laptop and put the battery pack back in and you are good to go.

The battery will NOT reset by just taking the battery out and re-seating it. I've tried, it doesn't work. You have to cycle the AC power first.

DO NOT USE THE USB Port next to the Mini DVI for devices that have external power supplied to them.

As stated, it's random.

I now plug the USB 3.0 powered 7 port HUB to the USB port on the laptop next to the 3.5mm headphone out and I've not had any problems what so ever.

Hope this helps.

Ubuntu 13.10 x64 secure boot
Samsung EVO SSD

This Asus N550JV (non-touch) rocks on Ubuntu!

Thank you I solved with your instructions! :)

---

### Post by ogenchev on 2014-01-25
Hi everyone,


I had the battery not-charging problem twice. Both times I solved it by opening the laptop, taking the battery out and keeping it out for some time (~3-4 minutes).
The first time, it happened upon restart, immediately after installing Win8 drivers. At the time, my machine was Win8 and Ubuntu 13.30 dual-boot.
The second time was upon restart after using HDMI to send video signal to my TV (Single-boot Ubuntu 13.10).


I have just found out that there is an updated BIOS for the N550JV. Has anyone had the issue with the new BIOS (version 208)? When I had my problems, I had versions 206 and 207.


PS: Aqlor's solutions seems much neater. Next time I have the issue I will definitely try it!

---

### Post by cryos on 2014-01-31
I had the same problem, the battery not charging also with notebook shutted down.
I make the battery power go totally down by keeping the notebook on in the bios setting panel, for few days the problem is not gone but  and after about a week i pugged in the charger, plugged the charger on the power line and battery restarted to charge... after i updated the bios to the 208 version.
I don't know if is just a randomness, but i hope that my experience can help.

UPDATE: 
also with 208 bios it had again the same problem, again I got the battery not charging.
after a few time it restarted to charg again. I don't know what to think.

---

### Post by 20daniele10 on 2014-02-10
Hi everybody, I had this problem again, but I solved without opening it! I don't know if i was lucky or what else, I'll try to explain what I did:

first I have to notice that when it starts to blink, the first time I turn on the laptop, a fan (or both) is spinning too fast; I tried to reboot several times without any success.
I hold the power button till it shuts down and the problem seemed to go away. 
When I reboot the fan again is spinning too fast, I opened kubuntu and I hibernated it.
After few seconds it goes to sleep mode and the problem is gone! 

I know that it's an empirical and dubious procedure but you can try it and write here what happens. 
I believe that going into sleep mode could solve the problem (or holding the power button)
I hope that this helps you with this bastard problem! XD

---

### Post by Mike_Higginbotham on 2014-02-24
I have experienced the battery not charging issue with my ASUS N550JV also. I was test driving various live linux distros on usb. I noticed it following fedora session. 
You have all hear all the tales. my tale is not much different. This forum did inspire my choice of remedy. I selected "restart" from windows 8.1 (shutdown will not do for MS reasons) and power down with 4 second button press when system starts to power up again. I was at 2% on charger for 4 days. 
I powered on and held 'esc' until offered option to select boot device or setup. I went into setup. Now for the really tricky part. I selected restore default settings. saved and restarted. 
As soon as the system started to power back up, .... , the power light illuminated and did not blink as before. within 2 minutes I was already seeing 4% charge. It has been about 15 minutes now following registration so that I could make this post. My charge level is now 19%.

---

### Post by arshad-vayani on 2014-03-23
I have ASUS N550JV and I faced exactly same problem twice. First time I solved this issue through following steps:

> [COLOR=#000000][IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **roblopes** [[IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("http://ubuntuforums.org/showthread.php?p=12898604#post12898604")[/COLOR]
[COLOR=#000000][I]What I've discovered is using the USB port next to the mini DVI port causes random problems with the battery. I use a 7 port USB 3.0 powered hub and had it plugged into that USB port on the laptop. Randomly on powerup the fans will run 100% and the battery indicator will flash orange/amber. The N550JV will NOT charge but will run under AC or until the battery has drained.

The solution:
1. Remove the T5 Torx screws from the bottom to access the battery.
2. Remove the battery.
3. Plug in the AC power and turn on the laptop.
4. Shutdown the laptop and put the battery pack back in and you are good to go.

The battery will NOT reset by just taking the battery out and re-seating it. I've tried, it doesn't work. You have to cycle the AC power first.

DO NOT USE THE USB Port next to the Mini DVI for devices that have external power supplied to them.

As stated, it's random.

I now plug the USB 3.0 powered 7 port HUB to the USB port on the laptop next to the 3.5mm headphone out and I've not had any problems what so ever.

Hope this helps.

Ubuntu 13.10 x64 secure boot
Samsung EVO SS

This Asus N550JV (non-touch) rocks on Ubuntu!

[/I]

Today same issue reappeared. So I decided to trying something else as opening laptop back cover and manually removing and adding battery again involved greater risk of laptop getting damaged. So I tried upgrading bios but my bios was already the latest version and I was unable to update it with older or same version. A new version is required to perform up-gradation. I decided to downgrade bios and I followed instructions mentioned in article below:

[/COLOR]http://rog.asus.com/forum/showthread.php?11438-How-to-downgrade-your-Bios-using-Winflash
[COLOR=#000000]
After down-gradation battery issue resolved automatically. So I would suggest everyone to upgrade bios if there is an update available and if you are already using latest bios update then try downgrading bios. This will resolve this battery issue.
[/COLOR]

---

### Post by perlsite on 2014-04-02
I'm having Asus N550JK which experience the same issue as its cousin. I.e. at some "random" moment the battery starts blinking orange (which according to the manual means - laptop is running on battery and not charging).

However this problem is not mandatory related to whether you use USB flash drive or not. On a system used only with SSD+HDD it also happen. Personally, on my machine I'm booting from USB (Linux Mint/Ubuntu) and I've noticed that problem few times.

My workaround/relieve fix is inspired by what is currently the only way to fix similar issues with smartphones and tables!

What **all you need to do is to power off the laptop by pressing and holding the power button for as long as it takes to become the orange led steady**. Usually it takes 5-7 seconds to reset the battery.

You don't need to remove the battery, you don't need to detach the power cable or reset BIOS to defaults. Even if your battery indicator is green and you keep the power button down for a few seconds you'll notice the battery indicator is reset (the led blinks once).

Let me know if that helps.

---

### Post by ab-fabe on 2014-04-11
> **perlsite said:**
> You don't need to remove the battery, you don't need to detach the power cable or reset BIOS to defaults. Even if your battery indicator is green and you keep the power button down for a few seconds you'll notice the battery indicator is reset (the led blinks once).

Let me know if that helps.

Yes it does the trick !! Thanks for sharing

---

### Post by reasgt2 on 2014-04-14
I have some other horrible symptoms that come along with this issue. Input events on the keyboard and mouse are intermittently ignored, making the machine nearly impossible to use. I caused the bug by plugging my android phone into the usb jack nearest the mini display port, even though I was only using it to charge the phone.

Here's a link to my AskUbuntu question with more details:
[http://askubuntu.com/q/447892/63396](http://askubuntu.com/q/447892/63396)

---

### Post by Remten on 2014-05-20
I have this same problem. BIOS 206, Lubuntu 14.04.

I never plug any powered USB devices into the USB port directly adjacent to the mini DVI port. (I occasionally plug a powered external hard drive into the left port that is closest to the bottom of the keyboard though.)

I have mostly left the AC power plugged in, and not used the battery. Just used the battery a handful of times since purchase, so never fully conditioned it by repeated discharge cycles. I've been doing very frequent reboots in the past few days, fine-tuning the installation. 

Now, I'm not sure whether it is related, but after one of these frequent reboots I noticed the fan turning on very loud (very unusual) during one of these reboots. I immediately held the power key down until the computer turned off, then rebooted. Fan was back to normal. I thought this might be due to having just recently turned on the Nvidia prime performance mode (I believe this activates the mode that renders graphics via the Nvidia gpu rather than just the Intel gpu), so I turned the performance mode off. A few boots later, still on Nvidia Intel gpu mode, and I noticed that I couldn't get the computer to boot on battery alone. I assumed the battery had been fully discharged, so I plugged AC back in, and it booted. Since then, can't get it to boot without AC cable plugged in. Battery led blinks orange when cable plugged in. 

Just tried the holding the power button down until it turns off and the battery indicator led turns on with a steady orange.

---

### Post by Remten on 2014-05-20
A couple of questions:

First, **What is the normal behavior of the battery led indicator** when the computer is turned off and
(a) the AC cable is connected and supplying power?
(b) the AC cable is disconnected?

Second, **What software battery charge state indicators are you using?**

I have only a moment ago activated the default xfce4 power manager that is included with this the Lubuntu desktop environment. It shows the battery at 19% charge (not sure how accurate that is), after I just did the holding down the power button to recycle the charge circuits trick about 15 minutes ago. I guess the battery had been nearly fully discharged. (Right after I held the power button down to recycle the circuit, I still couldn't boot off the battery, although I could boot off AC. I waited 10-15 minutes and now I can boot off battery again.)

---

### Post by plexabit on 2014-05-28
Okay, so with all this talk, I'm gonna make a...drum roll please...
[COLOR=#0000cd][FONT=arial black][SIZE=5]SUPER ASUS TROUBLESHOOTING GUIDE FOR BLINKY ORANGE LIGHTS![/SIZE][/FONT][/COLOR][COLOR=#00ffff][FONT=arial black][SIZE=5]
[/SIZE][/FONT][/COLOR] :popcorn:

Problem: Installing, booting, and/or updating Ubuntu on select ASUS systems (In my case, wasn't even Ubuntu) can cause the battery to not be recognized and the battery light to blink orange. Right before this, the fans will ramp up to over 9000, signaling your impending doom.

Diagnosis: Ubuntu or some other thing causes the BIOS to not recognize the battery in the laptop due most likely to a hardware compatibility issue with ASUS. USB devices plugged into the port next to the DVI port seem to possibly affect it.

Solution: Reset the Power Manager.


Method 1: **Possibly the easiest, most effective method. **Try this first; it's super easy and worked for me. Thanks to perlsite for this simple fix.

a. With the computer plugged in, press and hold the power button until the computer shuts down. Keep holding it until the orange light becomes solid (7 or so seconds). Power on and this may work.

Method 2: Reflash the BIOS. This seems to work most of the time.

   a. If you don't have the latest version, just update it!
   b. If you have the latest version:
        - Use WinFlash to downgrade the BIOS.
        - Upgrade if wanted.


Method 3: Reseat the battery. More involved, but seems to be very effective. Haven't seen anyone say this doesn't work.

   a. Unscrew the laptop base. Torx T5 does the trick.
   b. Unplug the battery.
   c. With the battery unplugged, plug into wall and turn on. Don't be stupid and go electrocute yourself. Not cool, bro.
   d. Turn off the laptop.
   e. Plug battery back in.
   f. Turn on.

Let me know of anything else that might work! :D Hope this helps all you dejected people out there.

---

### Post by krasovsky-evgeny on 2014-06-30
[[COLOR=#000000]plexabit[/COLOR]]("http://ubuntuforums.org/member.php?u=1926571")[COLOR=#000000] , [/COLOR]Thank you very much!!! The first method was successful ! \\:D/

---

### Post by hedwin-koning on 2014-09-14
> **krasovsky-evgeny said:**
> [[COLOR=#000000]plexabit[/COLOR]]("http://ubuntuforums.org/member.php?u=1926571")[COLOR=#000000] , [/COLOR]Thank you very much!!! The first method was successful ! \\:D/

I am using ubuntu 14.04 and the battery charging problem seems to be gone with with one of the latest updates.
I see now for 1 or 2 weeks that the battery is being charged without using the alternative method.

---

