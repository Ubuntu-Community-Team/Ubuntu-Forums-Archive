---
title: "Toshiba Qosmio G40 How to get Ubuntu 10.4 Going"
date: 2010-05-07
forum: Hardware
---

### Post by toogooda on 2010-05-07
**Ubuntu 10.10 Update:**

Every works except sound on 10.10 and here is how you fix it:

Fix Sound

The secret to getting sound cards to work if they are supported is the options line.
which looks something like:

Code:
options snd-hda-intel model=x
where x is the compatible key word, there are hundreds to try and I tried many, some about 5 of them fixed the sound but at the same time stooped the internal mic from working, as I like using skype I kept trying.


The following is how you fix both sound and mic at the same time.

Code:
sudo gedit /etc/modprobe.d/alsa-base.conf
add the following line to the bottom of the page


Code:
options snd-hda-intel model=auto
Then reboot and all is fixed (you just saved three days testing)



[SIZE=3]**What works out of the Box With Ubuntu 10.4**[/SIZE]

1) Video looks good but still recommend Nvidia driver 
2) Webcam just install cheese and try it out Webcam = /dev/video0
3) Volume controller
4) Touch-pad
5) Wireless
6) LAN
7) Most of the touch buttons including all the media ones
8 )  Microphone but see section below about getting sound and mic going at the same time
9) All the ports except tv tuner

**[SIZE=3][COLOR=black]What doesn't work on first Boot[/COLOR][/SIZE]**

1) Sound no errors just no sound like it is muted
2) TV Tuner

**[SIZE=3]After Nvidia Driver 195.... this also doesn't work[/SIZE]**

1) Cannot change Back-light
2) Really bad looking boot and shutdown screens

[SIZE=3]**What I have Fixed So far**[/SIZE]

**[SIZE=4][COLOR=Lime]Fix Ugly Boot[/COLOR][/SIZE]**
                                           
**Step 1**


You must edit the /etc/default/grub file.

Open a terminal and paste this:
  Code:
 $ sudo gedit /etc/default/grub On line #18, uncomment (uncomment = remove the &#8220;#&#8221; in front of the line &#8220;#GRUB_GFXMODE=640×480&#8221; and change the resolution to whatever you want 

  Code:
 GRUB_GFXMODE=1920x1280 
**Step 2**


edit the /etc/grub.d/00_header file.
  Code:
 $ sudo gedit /etc/grub.d/00_header And find the following line: &#8220;gfxmode=${GRUB_GFXMODE}&#8221; (it&#8217;s line 103 on my computer) and under it, paste this:
  Code:
 set gfxpayload=keep 
**Step 3**


update Grub 2:

To update the GRUB, simply run the following command:
  Code:
 $ sudo update-grub Once you complete the above steps, restart the computer and you should see the nice Plymouth screen.
 
**[SIZE=4][COLOR=Lime]Fix Sound[/COLOR][/SIZE]**

The secret to getting sound cards to work if they are supported is the options line.
which looks something like:

                                 ```
options snd-hda-intel model=x
```where x is the compatible key word, there are hundreds to try and I tried many, some about 5 of them fixed the sound but at the same time stooped the internal mic from working, as I like using skype I kept trying.


The following is how you fix both sound and mic at the same time.

```
sudo gedit /etc/modprobe.d/alsa-base.conf
``` add the following line to the bottom of the page
 

 ```
options snd-hda-intel model=hp-bpc
``` Then reboot and all is fixed (you just saved three days testing)




**[COLOR=Lime]Have not been able to fix Backlight or TV-tuner yet[/COLOR]** but I do have the following information:

**[COLOR=Lime]Backlight problem[/COLOR]** only happens with the new Nvidia driver 195.36.15 if I use the Ubuntu defualt driver (the one on the startup disk) it functions properly.

[COLOR=Lime]**TV-Tuner**[/COLOR]
I have discovered the chip-set is cx23418 and the kernel treats it as cx18 more detail if you try
```
lspci -v
```its the last item on the list

Also this particular card does not have the correct API's to work with tvtime so don't bother trying. need to use mythtv or mplayer, try this:

```
cat /dev/video2 | mplayer -
```it won't be tuned but you can see it working.
I will keep posting as I learn more.

Hope this helps someone!

---

### Post by eldarskiy on 2010-11-13
Create job! Thanks!

---

### Post by Dolphin2011 on 2011-01-10
Hi,
 
I am new to Linux and any help you can provide would be greatly appreciated. I have 2 laptops and I have tired to install Ubuntu 10.10 Maverick Desktop Edition and having various issues. The laptop that is relevant to this thread is my Toshiba Qosmio G40-10E. I encounted all the above issues and your suggestions have fixed most of them, but the one I am struggling with is installing the driver for the nVidia graphics card. I have tried installing it using the 'Additional Drivers' and rebooting after the installation is complete I get a black screen and I can't do anything. I have tired repeating the whole process a few times but the result is the same.
 
My graphics card details are:
[B]manufacturer : NVIDIA® 
type : NVIDIA® GeForce® 8600M GT supporting TurboCache™ technology 
[/B][B]mmanufacturer : NVIDIA® 
type : NVIDIA® GeForce® 8600M GT supporting TurboCache™ technology 
memory : 512 MB dedicated VRAM (up to 2303 MB total available graphics           memory using TurboCache™ technology with 4 GB system memory) 
memory type : DDR Video RAM (resp. DDR Video RAM and DDR system memory combined) 
connected bus : 16x PCI Express 
emory : 512 MB dedicated VRAM (up to 2303 MB total available graphics memory using TurboCache™ technology with 4 GB system memory) 
memory type : DDR Video RAM (resp. DDR Video RAM and DDR system memory combined) 
connected bus : 16x PCI Express 
[/B]
Please can you help - I don't know what else to try!
 
Thanks

---

### Post by toogooda on 2011-01-11
> **Dolphin2011 said:**
> Hi,
 
I am new to Linux and any help you can provide would be greatly appreciated. I have 2 laptops and I have tired to install Ubuntu 10.10 Maverick Desktop Edition and having various issues. The laptop that is relevant to this thread is my Toshiba Qosmio G40-10E. I encounted all the above issues and your suggestions have fixed most of them, but the one I am struggling with is installing the driver for the nVidia graphics card. I have tried installing it using the 'Additional Drivers' and rebooting after the installation is complete I get a black screen and I can't do anything. I have tired repeating the whole process a few times but the result is the same.
 
My graphics card details are:
[B]manufacturer : NVIDIA® 
type : NVIDIA® GeForce® 8600M GT supporting TurboCache™ technology 
[/B][B]mmanufacturer : NVIDIA® 
type : NVIDIA® GeForce® 8600M GT supporting TurboCache™ technology 
memory : 512 MB dedicated VRAM (up to 2303 MB total available graphics           memory using TurboCache™ technology with 4 GB system memory) 
memory type : DDR Video RAM (resp. DDR Video RAM and DDR system memory combined) 
connected bus : 16x PCI Express 
emory : 512 MB dedicated VRAM (up to 2303 MB total available graphics memory using TurboCache™ technology with 4 GB system memory) 
memory type : DDR Video RAM (resp. DDR Video RAM and DDR system memory combined) 
connected bus : 16x PCI Express 
[/B]
Please can you help - I don't know what else to try!
 
Thanks

Hey buddy that is the same card I have and I have no issues, can you please tell me the driver it is recommending?

is it 260.19.06?

can you please explain who you installed it?

---

### Post by Dolphin2011 on 2011-01-11
> **toogooda said:**
> Hey buddy that is the same card I have and I have no issues, can you please tell me the driver it is recommending?
 
is it 260.19.06?
 
can you please explain who you installed it?
 
Thanks for your quick response. It listed 2 drivers and I think one of them was '173' (hope that makes sense) and the 2nd one was the one it recommended and I think that said it was the most current. I have tried both and both caused my laptop to black screen after a reboot. I downloaded a driver from the nVidia website, but it must have been athe wrong one because the same thing happened.
 
I was stuck on the black screen and I am now in the process of reinstalling Ubuntu so I can be a bit more specific on the 2 drivers it provides once the installation is complate. I am not sure what I am doing wrong.
 
I have also been adviced to start a seperate thread which I have now created, so if you could reply to that one that would be great.

---

