---
title: "Battery Always Charging"
date: 2010-09-03
forum: Hardware
---

### Post by Heero_Yuy_X on 2010-09-03
Hi guys, 

I have a Lenovo Y560 IdeaPad, A few days ago I noticed my battery indicator applet showing that it's charging while the laptop's not plugged in..

I opened up the power statistics and found that the status of the battery is also charging, even though it reports the amount of energy left correctly ( decreases overtime like it should ) but the whole OS thinks its charging :(

I also found this in the AC Adapter Properties :
Supply : Yes
Refreshed : 0 seconds
Online : No

I even tried running "Powertop" in the terminal and its says no ACPI power usage estimate available... I have also tried updating to the latest versions of all the software on the OS to no result.

I have no idea how all these add up or what to make of all this !
Problem is, the OS runs on maximum brightness and CPU Frequency, thinking its really plugged in, and when I'm outdoors I can't get any estimate for the battery left :(
 
Can anyone help ? :(

---

### Post by Heero_Yuy_X on 2010-09-13
Anyone?? :(

---

### Post by Heero_Yuy_X on 2010-09-16
> Thanks my issue was corrected during an update ! 
Thanks for all those read this !

Sorry the issue still persists, after I upgraded to Ubuntu Meerkat !

---

### Post by Heero_Yuy_X on 2010-11-29
bumpp :(

---

### Post by achilleas.k on 2010-11-30
Hello Heero_Yuy_X,

Sorry if this reply is getting your hopes up but I'm just here to say that I have the exact same issue. Also, interestingly enough, I have the same laptop model (Y560), so maybe it's something related to this.

I do have a question for you:

Do you dual boot Windows? I don't, usually, but I left a Windows partition on for other reasons. Anyway, I noticed that this issue appeared a couple of days ago after I booted into Windows. I played around with some configuration options for battery lifetime. Specifically, there's an option that doesn't allow your battery to charge beyond 80% in order to prolong battery life if you primarily use the laptop on AC power. I don't know if it has anything to do with it, but I did switch that option on for a few hours and then back off. I was thinking it was an OS option that wouldn't affect the battery when the computer is working in another OS (Ubuntu) but now I'm thinking it may switch some hard option on the battery that's messing up the power applet in Ubuntu. This might make sense, considering a software option at the OS level wouldn't stop the battery from charging to 100% when the laptop is on AC and powered off.

---

### Post by achilleas.k on 2010-11-30
Well, &#921; rebooted into Windows, switched that power option I mentioned in my last thread on and off and then came back to Ubuntu. Plugged the AC, unplugged it and it said "Battery Discharging" ... for about 2 seconds. Then it switched back to the AC icon.

---

### Post by Heero_Yuy_X on 2010-11-30
Glad to see another y560 user out there ;)

yea i did the same exact thing with the "battery lifespan" option, and yes it looks like the app hard codes it to the battery or something, thts why it maybe causing problems to gnome power manager..

i did a kernel update back when i used 10.04 but i dont remember which version exactly and it miraclously worked..

anyways looks like we have to wait for the new Natty to fix the issue, though i doubt it will... :(

I will keep fiddling with the battery options in the bios setup and post my findings

---

### Post by achilleas.k on 2010-11-30
Right now I have the laptop running a Battery Gauge Reset in Windows through that same application (it basically jusy drains the battery completely and then recharges it). The whole procedure takes a few hours so I'll let you know if it changes anything when it's done

---

### Post by Heero_Yuy_X on 2010-11-30
ok this is annoying...

i left it on "Lifespan option" that keeps it at 80% last night...

im just booting it up now on the train to check some stuff out, and guess what, it discharged and gave correct estimates for just 2 minutes and just when I was about to write this post that it works.. 

it got back to charging again ! :S

I guess when I get a chance to get back to windows i'll set the option back on and see how it goes :(

---

### Post by achilleas.k on 2010-11-30
The Battery Gauge Reset didn't help.

But I think I solved it.

First I tried a few things that didn't work (BIOS reset, change power profile in Windows from Energy Star to high performance).

In the end I remembered what the manual of my old HP laptop suggests when trying to reset settings (i.e., hard reset stuff):

Shut down the laptop.
Remove AC power.
Remove the battery.
Hold the power button for about 10 seconds.


Try it out and let me know. The lappy's been on for about 10 minutes now and it's still showing a the battery icon properly and warning about low battery and all. I don't know if the last thing did the trick or some combination of the rest. I'm going to go ahead and assume it's the last one and wait for your confirmation.

---

### Post by Heero_Yuy_X on 2010-11-30
Greaaaat Job !!! :KS

That definitely worked ! I ran powertop and acpi and they are working as they should be !!! 
Even the energy rate has dropped, thanks to the OS finally thinking it's on battery ! 

Woow, I would've never arrived at that Hard Reset thingy ! I didn't even know such a thing existed for laptops !! seems the issue turned out to be with the Laptop not the OS after all !

Thanks alot my friend ! couldn't have done it without you ! :KS

It's certainly nice to see that icon back after a longtime !
Finally marking as solved ! :D

---

### Post by achilleas.k on 2010-11-30
Glad it worked
:D

---

### Post by ombako on 2010-12-08
The trick also worked for me! Great! Thank you so much!
By the way, my machine is: Lenovo Z360, running Ubuntu 10.10 64 bits.

---

### Post by Cerasi on 2011-02-26
I've been having the same problem with an IdeaPad Y460 running 10.04. I thought maybe it was related to messing with those battery life settings in Windows 7... Anyway, this fix worked! I'd been living with this problem so long that I wrote a script to make the laptop hibernate when the battery got low, so it wouldn't shut off suddenly. Glad I tried researching the problem again. Thanks man!

---

### Post by bukumayank on 2011-04-03
If u still have windows then reboot and go into windows then in the energy management option of lenovo y560 select reset battery gauge after doing this reboot and start ubuntu.


this worked 4 me....hope it works for u too.:guitar:

---

### Post by ultimatebuster on 2011-06-18
That's craptastic. I have the Y460, and I used windows to change the setting to battery. That windows installation is on a different harddrive, and my ubuntu installation still have issue with the battery icon always saying charging.

The feature where it saves the battery by preventing it to charge to 100% (hover it at 80%) actually works. I have another laptop that gets fully charged and I can see the battery capacity going down gradually overtime. 

Also by reading this thread I'm unsure what exactly I should do. A hard reset, or?

---

### Post by Kenrro on 2011-08-01
Thanks a lot!

achilleas.k's method also works on a Lenovo Ideapad Z470 on Ubuntu 11.04 64 bits (2.6.38-10-generic)

---

### Post by riddlebox on 2011-12-11
> **achilleas.k said:**
> The Battery Gauge Reset didn't help.

But I think I solved it.

First I tried a few things that didn't work (BIOS reset, change power profile in Windows from Energy Star to high performance).

In the end I remembered what the manual of my old HP laptop suggests when trying to reset settings (i.e., hard reset stuff):

Shut down the laptop.
Remove AC power.
Remove the battery.
Hold the power button for about 10 seconds.


Try it out and let me know. The lappy's been on for about 10 minutes now and it's still showing a the battery icon properly and warning about low battery and all. I don't know if the last thing did the trick or some combination of the rest. I'm going to go ahead and assume it's the last one and wait for your confirmation.

I just wanted to say this fix has worked for a Dell 1545 laptop as well, my issue was that ubuntu was reporting 50% on a full charge. I did this fix and now it reports correctly

---

