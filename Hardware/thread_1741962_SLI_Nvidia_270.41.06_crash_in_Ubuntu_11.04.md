---
title: "SLI Nvidia 270.41.06 crash in Ubuntu 11.04"
date: 2011-04-28
forum: Hardware
---

### Post by pkara on 2011-04-28
Hi,

I was previously running Ubuntu 10.10 and just recently used the update manager to upgrade to 11.04.  Note I am running the 64-bit version.

I also have a dual video card setup: 2x Nvidia Geforce 8800 GTS SLI mode

As I understand things, I needed to update my video driver to  Nvidia version 270.41.06.

Now when I boot the x-server it crashes.  This crashed USED to occurr if I didn't have BusID "PCI:1:0:0" and "PCI:2:0:0" in my xorg.conf (these are the video card busid's).  However, now it crashes even with the same xorg.conf file that used to work fine before.

Any thoughts?  I have seen something on the web implying that this is a known bug/problem with the new Nvidia driver 270.41.06, but I am not certain.

-Paul

---

### Post by Trophy on 2011-04-29
If you take the secondary video card out does the system boot okay running the new nvidia driver

---

### Post by johnkok on 2011-04-29
Hello, 

I am facing a similar problem in ubuntu 11.04.
After upgrading to 11.04 the system does not boot with 2.6.38-8 kernel (if I try to boot with my old 2.6.35 kernel the system boots but is very unstable). 
After removing my second SLI card (2x GTX460) everything works ok.
Before updating to 11.04, everything was ok in ubuntu 10.10 with 270.41.06 nVidia driver.

thx,
John

---

### Post by Lachinchon on 2011-04-29
You guys are a step beyond me, because I cannot even enable sli in Ubuntu 11-04. Using this terminal command: 
nvidia-xconfig --sli=Auto
I get a message that "Data incomplete in file /etc/X11/xorg.conf. Device section "Default Device" must have a Driver Line."
Huh?
Why should we even have to go to the terminal to enable sli anyway?
So, I guess I would like to get some advice about enabling sli in the first place, so I could then have my machine crash like you guys.

---

### Post by Rody on 2011-05-01
I am not having any luck enabling sli on 11.04 ether. I am not getting any errors, and my xorg has sli enabled but no dice on it actually working.

rody

---

### Post by Zpiff on 2011-05-14
Hi,

Im not running SLI but anyway have problem with the latest Nvidia 270.41.06 driver for my GeForce GTX 470.
The X-server hangs sporadic, and also the whole system some time.
Running Ubuntu 10.04 kernel 2.6.32-31

All works fine with my previous driver Nvidia 260.19.44

---

### Post by Trophy on 2011-05-18
Hi [Lachinchon]("http://ubuntuforums.org/member.php?u=656375"), i had the same problem. If you open your Nvidia X server settings, under the X server Display Configuration menu, choose to "save to X configuration file". Once this is done i rebooted ... then ran the "sudo nvidia-xconfig --sli=On" command and it worked ... rebooted again and i had Sli.

I have had to turn it off again though as it does crash the system at times. Not sure why, think it is a bug with the 270.41.06 version

---

### Post by cRACKmONKEY421 on 2011-06-26
I have the same problem with a GTX 460 1GB in SLI. Everything works great on one card, but as soon as I but in the other one, the GUI fails to show up. Computer doesn't completely freeze; when I ctrl+alt+delete it still runs some commands and reboots. It works fine if I load fail safe video drivers, but that's too ugly. Is there any way to load the old drivers? I tried the new ones from nvidia's website, but that failed too (maybe for other reasons). Generated an xconfig file in the nVidia driver's GUI, then set 'nvidia-xconfig --sli=Off' but that didn't seem to help either. I tried 'sli=On' first. I'll keep trying things, but I'm running out of ideas.

**Edit:
Fixed the problem by adding vmalloc=256M to the right spot in GRUB. Here is info on that: [http://ubuntuforums.org/showthread.php?t=1684460](http://ubuntuforums.org/showthread.php?t=1684460) (check the bottom)
Now I just need to fix my resolution again.. but it appears to be working. This is the first time I've had Unity + both cards plugged in.

---

### Post by cRACKmONKEY421 on 2011-06-26
Here's what I did to get mine to work. This is just as much for me as anyone else:

1) Installed Ubuntu with just one Graphics card in the system. I'm not sure how required that step is, but I had already pulled it anyway because OS X required it and I was installing that around the same time.

2) Installed the nVidia driver using 'Additional Drivers' built in GUI utility.

3) Rebooted and everything worked fine, except I didn't have my usual resolution and refresh rate (1280x960@85) as an option.. So to fix that I used 'NVIDIA X Server Settings' to generate and saved an /etc/X11/xorg.conf by clicking 'Save to X Configuration File', then I edited that file with these changes:
Inside of 'Section "Monitor"' I changed to these refresh rates
    HorizSync       31.0 - 101.0
    VertRefresh     60.0 - 160.0
Inside of 'Section "Screen"' I added these metamodes (line following 'DefaultDepth')
    Option         "metamodes" "1280x960 +0+0; 1024x768 +0+0; 800x600 +0+0; 640x480 +0+0"
And in 'Selection Screen' there is a 'SubSection "Display"' in which I added this line right after the 'Depth' line
      Modes      "1024x768_85.00" "1600x1200_80.00" "1280x960_85.00" "640x480_75.00" "800x600_75.00"

4)Rebooted, and everything looked great. Now for SLI. Popped in my other card, rebooted, and the Ubuntu GUI never started.

5)Rebooted Ubuntu into recovery mode without the GUI. Ran this command to make sure my computer was seeing both cards (which it was):
lspci | grep -i vga

6)Running this command put both GPU devices into the xorg.conf. I'm sure that's important:
sudo nvidia-xconfig --enable-all-gpus

7)I ran this command at some point to put the flag in xorg.conf that turns SLI on. It's probably not required get you booting, but of course it'll be needed if you want to USE the SLI.
sudo nvidia-xconfig --sli=On

8****)I tried rebooting at that point, and it still failed, so once again I got back into recovery mode without the GUI and did:
sudo pico /etc/default/grub

9)Found and replaced this line 'GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"' with this line 'GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vmalloc=256M"' <---change 256M to 192M if that doesn't work.

10)Then update GRUB like this:
sudo update-grub

11)That's pretty much it. I rebooted and it came back up, but I had to once again fix my resolution the same way I did above. However, my xorg.conf file now has two entries for 'Section "Monitor"' and 'Section "Screen"', so I just put in all that data twice (once for each entry). Now everything's great :D

Hopefully this will help someone, or at least it will help me if I ever have to re-install.

---

