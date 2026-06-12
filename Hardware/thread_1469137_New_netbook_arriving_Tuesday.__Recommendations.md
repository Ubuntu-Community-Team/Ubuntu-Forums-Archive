---
title: "New netbook arriving Tuesday.  Recommendations?"
date: 2010-05-01
forum: Hardware
---

### Post by VeeDubb on 2010-05-01
So I've got myself a new Asus EeePC 1201n coming from my favorite computer website, and UPS says it will be here Wednesday.

If anybody cares, but doesn't know, it's got a dual core atom, nvidia graphics, 2GB of RAM, and a 250GB HDD.


I've got my little pen drive all ready to go with the latest netbook remix on it to install, plus skype, boxee, the latest flash beta, hulu desktop, and the necessary drivers for the broadcom WiFi/BT chip.

The problem is, the waiting is killing me, and I'm looking for any other stuff I should check out or consider for it, or other stuff I may not have thought of, but will want prepared.

I'm pretty much open to any sane/real recommendations here.

Thanks.

---

### Post by emoguitarist06 on 2010-05-04
You're absolutely going to love it!
The 1201N is by far my favorite laptop/netbook ever!

[COLOR="Red"]Ubuntu Bug: You need to download and install the realtek driver for wifi to work.
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

How to install :
1. download the file archive from previous link; (RTL8191SE-VA2)
2. with File Roller (dbl click on file) you extract the archive content on your Desktop (drag and drop).
3.open Gnome Terminal, and:
    $cd Desktop
    $cd rtl8192se_linux_2.6.0013.1204.2009
    $sudo su
    #make
    #make install
    #reboot

That's it. Now you have an working WIFI card.!
[/COLOR]

I upgraded to 4GB of ram (although only 3.25 usable)
I upgraded to 80GB SSD Intel X25M

As far as cd/rom I recommend the one by ASUS
I haven't tried any other one but I love this one because it's fast, quiet, and worked out of the box with Ubuntu 9.10 & Ubuntu 10.04

BTW Why UNR? I say go full-fledged 10.04 Desktop edition! Why not? 1201N's have full-resolution
I am even playing WoW on Ubuntu using Wine as we speak!!

LOVE IT LOVE IT LOVE IT


As far as Windows I have no clue. I changed to my SSD the day I got my 1201N and ran ubuntu ever since

---

### Post by VeeDubb on 2010-05-05
> **emoguitarist06 said:**
> 
LOVE IT LOVE IT LOVE IT

I'm especially glad to hear that.  A few people in the newegg reviews were less than thrilled with the linux compatibility, but others said it was fine, and I looked all the hardware up myself before ordering.  Of course, direct word from a fellow Ubuntu user settles the matter pretty well.

I seriously considered an entry level 10" netbook with intel graphics and a single core atom instead of the dual core, but I just didn't feel right about it.  "It gave me the 'no' feeling."

I've actually got what 'should' be the correct kernel module source for the WiFi driver on my little pen drive and ready to go, but I'll check out your link and download that one if it's different. since you've got the same model and have it working.

As far as using UNR, I've got a couple of reasons for it, although I may change my mind once I use it for a while on that WXGA screen.  One reason is that I just really like the interface of UNR, but I've never used it except to play with because it's not so practical for my desktop.  Also, there's a good chance this netbook will be spending some time hooked up to a TV as a boxee box when not being used as a netbook.

I'm hoping it shows up in the next 9 hours, because otherwise I'll have to leave for work before it arrives, and since my cat can't sign for packages, I'll miss the delivery and not get it until Thursday.


*edit: The file from your link is a different file after all, so I'm ditching the old one and I'll use that since I know it's working for you.

Thanks again.

---

### Post by emoguitarist06 on 2010-05-05
> **VeeDubb said:**
> I seriously considered an entry level 10" netbook with intel graphics and a single core atom instead of the dual core, but I just didn't feel right about it.  "It gave me the 'no' feeling."

I've actually got what 'should' be the correct kernel module source for the WiFi driver on my little pen drive and ready to go, but I'll check out your link and download that one if it's different. since you've got the same model and have it working.

As far as using UNR, I've got a couple of reasons for it, although I may change my mind once I use it for a while on that WXGA screen.  One reason is that I just really like the interface of UNR, but I've never used it except to play with because it's not so practical for my desktop.  Also, there's a good chance this netbook will be spending some time hooked up to a TV as a boxee box when not being used as a netbook.

*edit: The file from your link is a different file after all, so I'm ditching the old one and I'll use that since I know it's working for you.

Thanks again.

Yeah I understand how you feel. I thought about it too but then I was wait... although I would love the portability netbook as compared to my huge compaq (that i already sold) I cannot deem it "smart" to downgrade in both processor and graphics. With the 1201N I feel that I have entirely upgraded from my Compaq CQ60, I feel this Atom 330 processor is fairly strong. The biggest thing I do that uses a lot of system power is VMWare virtualization for Windows XP and it run's pretty smoothing in conjunction with like WoW or Firefox running as well.

Yeah as far as I know the latest kernel in Ubuntu 10.04 includes version 14 instead of 15. When I initially installed it I had the impression that I had wifi but I could only see one network available instead of all of my neighbors as well. And I knew they weren't that smart to hide their own networks lol. And in actuality it would not even connect so yeah that driver I posted works great.

If you're going to keep the 1201N hoooked up to the TV I'm sure you're going to be using HDMI? and will have the power supply connected?
As I haven't official measured my battery life but I would roughly say 4hours. Of course for HDMI you just need to change the sound settings in System>Preferences>Sound to digital HDMI out
and for the second display System>Administration>NVidia X ServerSettings>X Server Display Configuration..................... Not sure if you already know all this information but thought I'd just say :)

---

### Post by VeeDubb on 2010-05-05
Yeah, it would definitely be HDMI, and AC power with the battery removed.

---

### Post by VeeDubb on 2010-05-06
Could you check and tell me what keyboard model you have selected in "preferences>Keyboard"?

I tried the default, and then I tried setting it to Asus Laptop, and neither one would allow me to access the keyboard volume controls.

Thanks.

---

### Post by emoguitarist06 on 2010-05-06
> **VeeDubb said:**
> Could you check and tell me what keyboard model you have selected in "preferences>Keyboard"?

I tried the default, and then I tried setting it to Asus Laptop, and neither one would allow me to access the keyboard volume controls.

Thanks.

Yeah I just choose whatever Ubuntu recommended

Generic 105-key (Intl) PC

---

### Post by VeeDubb on 2010-05-08
Well, I can't seem to get UNR to recognize Fn F10-F12 as volume controls, so I just set those hot keys to Ctrl instead of Fn.

Everything else seems to work, and in fact most everything worked without me having to do anything.  The toughest was just a little bit of tweaking t get skype to recognize my mic without having to dump pulse.  I wanted to keep pulse because despite the pulse-hate on the forums, I really do find that it works better and provides me with more control most of the time.

---

### Post by VeeDubb on 2010-05-09
I case anybody else finds this thread, I was able to get all of my hot-keys, including the key to turn the touchpad off and on (which rocks if you have an external mouse to use with it) and the volume keys, by adding the following lines to my grub

```
GRUB_CMDLINE_LINUX="acpi_enforce_resources=lax acpi_osi=Linux quiet splash"
```

The tip came from [this thread]("http://ubuntuforums.org/showthread.php?t=1372412&highlight=1201n").

That also suppressed the boot error I was getting, improved boot times, and fixed hibernation which would cause my bios to reset before doing this.

---

### Post by Picro on 2010-05-13
> **VeeDubb said:**
> I case anybody else finds this thread, I was able to get all of my hot-keys, including the key to turn the touchpad off and on (which rocks if you have an external mouse to use with it) and the volume keys, by adding the following lines to my grub

```
GRUB_CMDLINE_LINUX="acpi_enforce_resources=lax acpi_osi=Linux quiet splash"
```

The tip came from [this thread]("http://ubuntuforums.org/showthread.php?t=1372412&highlight=1201n").

That also suppressed the boot error I was getting, improved boot times, and fixed hibernation which would cause my bios to reset before doing this.
Hi ,
This is Jitesh from India. 

Can you please tell me how to add these lines to grub? Sorry for my ignorance.  I knew how to edit legacy grub (menu.lst) of older versions of ubuntu but this new grub2 thing is a bit complicated and I fear I'll break it if I go wrong. 
Thank you for your time.
Jitesh Iyer

---

### Post by VeeDubb on 2010-05-13
> **Picro said:**
> Can you please tell me how to add these lines to grub?

Sorry for the slow reply.  Been a busy couple of days.

It's actually very easy.

1. Open up a terminal and enter the following command:
```
gksudo gedit /etc/default/grub
``` and then enter your password when prompted.

"gksudo" is just like the sudo command, but is used for graphical apps so you don't accidentally do something disastrous as root.  You should always use it when launching a graphical app from the command line.

2. Find the line that starts out ```
GRUB_CMDLINE_LINUX=
```

and change it to ```
GRUB_CMDLINE_LINUX="acpi_enforce_resources=lax acpi_osi=Linux quiet splash"
```
Then just save and close.

3. Back at the terminal, enter the following command
```
sudo update-grub2
```

That's it.

---

### Post by Picro on 2010-05-17
Hi,
Thanks for the detailed reply. It worked perfectly. Now most of the hotkeys are working fine, but still a few dont work. Like Fn+Space for the Powersaving options, Fn+V for the webcam. They're not so critical, though, and the important ones, like the Wifi toggle, volume, playback and brightness all work.
Another issue is regarding Fn+F2. In Windows, it toggles between Wifi as well as Bluetooth, but in Ubuntu, it only toggles Wifi. Is there a way i can configure Bluetooth toggle, to Fn+F2 or any other key combination?
Thanks again!
Jitesh

---

### Post by VeeDubb on 2010-05-17
> **Picro said:**
> Is there a way i can configure Bluetooth toggle, to Fn+F2 or any other key combination?
Thanks again!
Jitesh

As far as I have been able to tell, turning BT completely off throught the BT applette in the panel at the top of the screen, completely turns off the antena and everything.  If you turn it off, reboot, and go into the bios settings, you'll see that it will show BT as disabled.  

I'm sure there must be some way to tie this to the hotkey as well, but I wouldn't know where to begin.

---

### Post by Picro on 2010-05-18
Yes. Another thing is that if I switch off BT while in Windows (Fn+F2), then boot into Ubuntu, there seems no way I can activate BT from Ubuntu. In fact it says there exists no BT adapter. 
I wonder is there is a way to switch on BT from within Ubuntu itself...

---

### Post by VeeDubb on 2010-05-18
Can't help you there.  I haven't dual-booted in years.  There are so few things I turn to windows for that I just keep a VM with windows XP on my desktop.  Of course, the 1201n, as high powered as it is, really isn't high powered enough to be running much of a VM.

---

