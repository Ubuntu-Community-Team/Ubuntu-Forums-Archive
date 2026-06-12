---
title: "Solutions for Samsung Laptop problems (Backlight, Sleep, Keyboard issues, Hotkeys)"
date: 2011-02-03
forum: Hardware
---

### Post by armanatz on 2011-02-03
Hey guys,

I am a first-time poster/linux-user and recently made the move to switch from Windows to Ubuntu Linux. Let me tell you, I have never been happier.
Well, a couple of days ago, I purchased a new laptop from Samsung (the RF510) and installed Linux on to it but to my dismay, the laptop had a lot of issues out-of-the-box. I will list the issues I faced in order:

[LIST=1]
[*]**Backlight settings did not work**: My brightness control settings were completely out of whack. They did not work one bit and on the off chance that they did, they would completely disable the backlight rendering the screen unusable.
[*]**Keyboard "got stuck"**: If I ever used the Fn+Up, Fn+Down, Fn+Left or Fn+Right keys, the keyboard would go into an endless loop (apparently not releasing the keys properly) and render the panel bar and almost everything else on screen unclickable.
[*]**Hot keys were not properly set up**: Pretty self-explanatory. The hotkeys on the function keys were not set up to do what they were supposed to.
[*]**Sleep/Suspend function**: The laptop was unable to go into sleep/suspend mode when the laptop lid was closed or when the laptop was put to sleep through the power bar.
[*]**(Unsolved; kernel-related issue) Touchpad not recognized**: The touchpad was not recognized properly as a touchpad but rather as a Logitech PS/2 Mouse. This is an issue at the kernel level which I don't have much expertise in and therefore could not solve. If anyone can take a whack at it then go ahead, be my guest. The touchpad is an ELANTech Smart-Pad and from what I can tell, this touchpad is still not supported in the Synaptics driver modules in Linux
[/LIST]
Anyways, I scoured the internet and found a various array of solutions (most of which did not work for my laptop) and finally settled on the ones that worked. Here are the solutions for each problem.

> 
[SIZE=4]**Backlight Settings:**[/SIZE]

Start here:
Open Applications - Accessories - Terminal

Type this command:
```
 sudo add-apt-repository ppa:voria/ppa
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install samsung-backlight
sudo apt-get install nvidia-bl-dkms 
```Once everything is installed properly, stay in terminal and execute the following command:
```
 sudo gedit /etc/modules 
```Add the line "nvidia_bl" (without "") after the word "lp"
Save and exit.

Terminal command:
```
 sudo gedit /etc/X11/xorg.conf 
```Insert this line, under the **Option "NoLogo"** line

**Option "RegistryDwords" "EnableBrightnessControl=1"**

Save and exit.

Next enter the command:
```
 sudo gedit /etc/default/grub 
```Change the line that says GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to read GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_osi=Linux acpi_brightness=vendor splash" instead.

Save and then in terminal:
```
 sudo update-grub2
sudo reboot 
```That should get your backlight to work (at least it did for me).

[SIZE=4]**Keyboard and Hotkey issues:**[/SIZE]

The keyboard issues were solved using Roadmaster's tip right here on the Ubuntu forums therefore, credit goes to him:
[http://ubuntuforums.org/showpost.php?p=10266620&postcount=6](http://ubuntuforums.org/showpost.php?p=10266620&postcount=6)

Follow his tutorial to solve the keyboard issues and some of the hotkey issues.

For the rest of the hotkey setup, you will need to open up terminal and input:

```
 sudo apt-get install samsung-tools 
```Reboot and enjoy your hotkeys like they were meant to be!

**[SIZE=4]Sleep/Suspend function:[/SIZE]**

The sleep function in Ubuntu apparently does not work well with some devices (especially those with USB 3.0). If you have USB 3.0 and your device can't be suspended, then this is definitely why.

Open up terminal and enter:
```
 sudo gedit /etc/pm/config.d/unload_module 
```*NOTE: This module is not on the system. We are actually creating this module.*

Add the line:
**SUSPEND_MODULES="xhci-hcd"**

Save and exit.

This should get your sleep/suspend function working properly again. Anyways, that should fix all but one issue. The touchpad I am afraid apparently has no fix out yet so here is to hoping that a kernel patch will come soon that would enable ELANTech Smart-Pads to be used in Linux natively.

I am sorry if most of these solutions are rudimentary and hacky but they were the only ways I could find that would fix these issues properly. I also apologize for the way the tutorial was written, I am a newbie at these things.

I thought that I would give back something to the community (however small it may be) as they have given on to me. That is how open-source works and I am glad to be a part of it.

Credits go to voRia from [http://www.voria.org](http://www.voria.org) who set up the repository where all the Samsung related files are being hosted, Roadmaster for his tip on how to fix the keyboard and hotkey issues, and others from the Ubuntu and Voria forums who I may have missed out (forgive me)!

If you guys have any issues, feel free to ask! I will glad to help.

---

### Post by piper827 on 2011-02-03
Hey armanatz!

Thanks for this awesome post. I bought the Samsung qx410 back in November and it seems that all of Samsungs recent lineup has been having the same problems with Ubuntu.

I have also been searching the internet for solutions to the problems and you seem to have found some very good ways to solve the issues.

I have yet to try them out for my own, so I can't validate that they work for the qx410, however, my question is: Is it safe to use Linux on this computer yet?

I've been putting off loading Ubuntu onto my laptop because it seems like there is such instability with the system.

I don't have a necessity to switch anytime soon. I just like Linux more than Windows, but I would like to wait until it is fully functional. I mostly use a wireless mouse with my computer, so the touch pad isn't a problem.

So to your experience is the computer functional with Linux to its fullest potential?

---

### Post by armanatz on 2011-02-04
Thanks for the kind words piper827!

I am glad that this post was, in a way, useful to you. To answer you question, Ubuntu seems to be solid as a rock in terms of stability on my Samsung RF510. It identifies everything (after fixing the issues of course) except for the touchpad. That is, as I mentioned above, cause at the kernel level where the touchpad is incorrectly recognized as a mouse rather than a touchpad.

I haven't had any issues so far with the system, ie no hiccups, bugs, crashes or slowdowns. Just a quick note however. The Intel Turbo Boost functionality does not seem to natively work in Linux for some reason and I think that it is because Linux does not support this function yet. Therefore, you will not be able to get the full potential of your CPU out within the Linux environment. This I think is a small dealbreaker but not one that would make you put off installing Ubuntu.

As far as GPU is concerned, everything works fine and I can play some games within Linux through Wine perfectly. Plus, the system still manages to keep quiet even through games (sometimes making me a bit cautious as I wonder if my system's fans actually work or not).

But all in all, everything in Linux works fine and as I said, apart from the touchpad issues, there are no other problems with the OS on my Samsung.

Hope you install the OS and reap the benefits that Linux has to offer. Thanks again for your kind words!

Have a good day

---

### Post by piper827 on 2011-02-15
Right-oh, thanks again armanatz!

---

### Post by enriqg9 on 2011-03-08
> **piper827 said:**
> Hey armanatz!

Thanks for this awesome post. I bought the Samsung qx410 back in November and it seems that all of Samsungs recent lineup has been having the same problems with Ubuntu.

I have also been searching the internet for solutions to the problems and you seem to have found some very good ways to solve the issues.

I have yet to try them out for my own, so I can't validate that they work for the qx410, however, my question is: Is it safe to use Linux on this computer yet?

I've been putting off loading Ubuntu onto my laptop because it seems like there is such instability with the system.

I don't have a necessity to switch anytime soon. I just like Linux more than Windows, but I would like to wait until it is fully functional. I mostly use a wireless mouse with my computer, so the touch pad isn't a problem.

So to your experience is the computer functional with Linux to its fullest potential?

I have Ubuntu 10.10 on a samsung qx410 and it works ok but you won't get the nvidia graphic card working as it works with the Nvidia Optimus and this is not supported on linux, but you will have graphics through the intel video card but no 3D accel. Everything else works fine.

---

### Post by shmup on 2011-03-10
Lovely guide, man. I will say that my main reason for digging this up was the touchpad, but I'm glad you addressed the other issues.

I have a Samsung RF510 and are any of you experiencing feedback with the built in mic? I'm referring to where you get a high pitched noise if your hand goes near it, or as you're closing the laptop. Very annoying and I'm not sure what to do. I've tried muting the mic, but that's not good enough. Thoughts?

---

### Post by armanatz on 2011-03-12
> **shmup said:**
> Lovely guide, man. I will say that my main reason for digging this up was the touchpad, but I'm glad you addressed the other issues.

I have a Samsung RF510 and are any of you experiencing feedback with the built in mic? I'm referring to where you get a high pitched noise if your hand goes near it, or as you're closing the laptop. Very annoying and I'm not sure what to do. I've tried muting the mic, but that's not good enough. Thoughts?

Thanks for the kind words!
Well, to be honest, I have not experienced this issue on my laptop but there are others who experience it on other brands of laptops. Check the guide out over here and tell me your experiences:

[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

Cheers!

---

### Post by funkyidol on 2011-03-26
Is this issue present in Ubuntu 11.04 as well? I understand that it will be using Linux kernel version 2.6.38.

Im planning to buy Samsung SF510 laptop next month.

---

### Post by josvanr on 2011-04-05
unfortunately, none of the solutions work for samsung SF310....


more specifically:

I don't have the problem with special keys hanging the machine.
The volume fn key combination seems to work, but that worked 
out of the box. The fn key combi for the brightness does pop up
a brightness gauge (ruler indicating brightness) but this stays
at maximum brightness. 

Suspending doesnt work. I do hear some kind of a system sound
indicating that the machine is going to suspend (upon lid close)
but it doesn't actually suspend.... (hdd etc keeps running)

josvanr

---

### Post by josvanr on 2011-04-05
sorry about this: the suspend issue had to do with kde powersave
settings. It works fine now. Keys issue stays....

Also discovered this: in powersave settings one can set the screen 
brightness with a slider. This works well, so the issue is only with
the key binding. When I press fn-up or down, the brightness indicator
does appear, displaying the correct brightness. But the brightness
doesn't change...

I just made another discovery: in the kde settings/global keyboard shortcuts, there are entries for increasing and decreasing the screen brightness. Here I tried to add custom shortcuts for fn-arrow down
and fn-arrow up. The key combinations are recognized, but still the brightness doesnt change as described above. I tried to use other key combinations ie alt-k and alt-j, with the same result. 

So what could be the problem then: the functon keys are recognized and work (I can map them). And also I can actually change the brightness form kde settings. I just can't change it with the keys....


josvanr

---

### Post by jolus on 2011-05-04
Any of you guys have tried to connect this laptop to an external monitor using the VGA or the HDMI port ? any problems with this?

---

### Post by josvanr on 2011-05-08
Bumppad.

Hi

Anyss progress z on the touch pad issue i ye?t? Someone is about.
to be institutionalizjosed here..... 

(I've beenHi selecting textll in gimp all day and the 
cursor keeps jumping aroundHi..)

Worst thing is, that if I do manage to carefully position
the pointer, and the press the right button to select,
the cursor moves again, or jumps to a random location 
on the screen! Who came up whith the idea to 
include the buttons in the touchpad area itself?? 


josvanr



> **piper827 said:**
> Hey armanatz!
 
 .

I don't have a necessity to switch anytime soon. I just like Linux more than Windows, but I would like to wait until it is fully functional. I mostly use a wireless mouse with my computer, so the touch pad isn't a problem.

So to your experience is the computer functional with Linux to its fullest potential?

---

### Post by edjski on 2011-05-10
5/9/11 -just bought a QX410. 
Have not yet installed Ubuntu, ran from a live disc just to test. In Windows, the elan touchpad was frustrating to use until I downloaded the driver (initially I didn't have the Smart Pad managing software). After installing it, I was able to access and adjust all of the multi-touch functions for the touchpad and it seems to be working fine (in Windows).
-Since there are many complaints and criticisms even on the Windows side about the touchpad, perhaps this will help someone experiencing problems but not necessarily running Linux (yet).

Booting into Ubuntu 10.4 live disc, the touchpad worked about as well as  it worked in Windows before I made adjustments in the Smart Pad software.

One of the problems, as far as I see it, is that even with fine tuning the parameters in the Smart Pad software, the left and right click buttons are still part of the touchpad -they are part of the sensor. So, while clicking, if your finger moves or rolls, the cursor may move. I'm going to try putting a piece of tape on the button area of the touchpad and see if that alleviates that problem. If it does, then I'll probably find some sort of thin stick-on chrome-ish looking material (or something more attractive than electrical tape) to put on more permanently. -Just an idea. Will report back with results. Plus, I think it would provide a more positive click action since it would feel different than the rest of the touch pad and therefore be easier to detect.

---

### Post by kia42 on 2011-05-11
I have (maybe quite dumb) question: How can I get backlight to work on Natty (nvidia-bl-dkms is not in voria repository [https://launchpad.net/~voria/+archive/ppa](https://launchpad.net/~voria/+archive/ppa) )?

What about multitouch? Is there any working solution?

I have RF510 and everything else is working :-) And I agree with members above, buttons in touchpad area isn't good idea (once I had it and it was really annoying).

---

### Post by lptr on 2011-05-13
[@armanatz]("http://ubuntuforums.org/member.php?u=1237032"): Your post solved my problems:

Having a Samsung Netbook N145 plus here. Natty and Unity did work out of the box. But its screen was totally dark. Nearly unusable.

I installed Samsung tools and changed Grub default entries to:
"quiet acpi_backlight=vendor acpi_osi=Linux acpi_brightness=vendor splash"

no X11 modifications, but of course
$ sudo update-grub2
$ sudo init 6

After this brightness control worked as expected. 

OT here - but cool feature I found by accident: Two finger gesture on mousepad for scrolling like on my Macbook Pro :)

---

### Post by edjski on 2011-05-15
> **edjski said:**
> 
One of the problems, as far as I see it, is that even with fine tuning the parameters in the Smart Pad software, the left and right click buttons are still part of the touchpad -they are part of the sensor. So, while clicking, if your finger moves or rolls, the cursor may move. I'm going to try putting a piece of tape on the button area of the touchpad and see if that alleviates that problem. If it does, then I'll probably find some sort of thin stick-on chrome-ish looking material (or something more attractive than electrical tape) to put on more permanently. -Just an idea. Will report back with results. Plus, I think it would provide a more positive click action since it would feel different than the rest of the touch pad and therefore be easier to detect.
5/15/11  Well, it seems I know little about capacitive touchscreens...
Electrical tape does not work. In fact, it was as if there was no electrical tape covering part of the touchpad. 
I remain diligent in my search for a solution to make this Samsung work.

---

### Post by quyduy1992 on 2011-07-20
This is very useful to me . I am having some problems with my [laptop ]("http://www.samsung.com/vn/consumer/monitor-peripherals-printers/notebook/index.idx?pagetype=type_p2&")

---

### Post by e.w on 2012-02-05
Has anyone worked more on the touchpad issue? I just installed latest version of Ubuntu (11.1?) on dual boot Samsung RF510 and the touchpad has no functionality at all.  Device is recognized as ps/2 generic mouse but does not respond to touch or click at all.  Plugging external generic usb mouse works just fine. 

Thanks if anyone has any input. 

-Eric

---

### Post by WaNaBePi on 2012-02-16
regarding the Samsung rf510

I need a way to stop the "tap to click" feature or just disable the touch pad on the laptop in ubuntu 11.10.

Do either of these things exist*?

I can't seem to find a person who has found a way to disable the tap to click feature. The disable touch pad advise I found was to difficult for me to attempt*.

**Upgraded** to 11.10 now mouse dosent work at all... Just kidding, it fixed everything, I even have two finger scrolling! 5 hours spent upgrading: time well spent... I don't know about that.

---

### Post by Chang on 2012-04-04
Greetings. Have a Samsung SF310, tried most solutions above. Worked well. Upgraded to 12.04. Back to trackpad and mouse problems. Can't move windows or use the cursor to highlight text. Please help

---

