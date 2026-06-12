---
title: "Sony VAIO UX 390 small problems with ubuntu"
date: 2012-03-21
forum: Hardware
---

### Post by ZionZev on 2012-03-21
Hi guys, 

I wondering are there other members here who using Sony VAIO UX series runs on 10.04 Ubuntu LTS? 

I did able install 10.04 LTS on my Sony VAIO UX390 and runs fine. I really like it how fast boot up and performance wise but there few thing that really annoying with stick pointer mouse it seem always random dragging my files anywhere as I try move the pointer with build-in thumb mouse but no problems with external USB mouse.

It seem its problem with "touchpad" driver and I have done tried edit on "10-synaptics.conf" at (/usr/lib/X11/xorg.conf.d)  by adding the 3 (red colored) lines and nothing helps... :confused:

Section "InputClass"
          Identifier "touchpad catchall"
          MatchIsTouch "on"
          MatchDevicePath "/dev/input/event*"
          Driver "synaptics"
       [COLOR=Red]   Option "TapButton1 "0" 
          Option "MaxTapTime "0"
          Option "MaxTapMove "0"[/COLOR]
EndSection


Also, the touchscreen works quiet nicely, but slightly uncalibrated and bit hard to use the stylus pen. So how I do that to re-calibrate?

---

### Post by darussell1 on 2012-09-21
I'm a new Xubuntu user, having just installed it on my old trusty Sony UX-180P.  Like you, I am having great difficulty using the UMPC when traveling.  I use a ThinkOutside bluetooth keyboard and mouse when working at home, but the portability of the UX-180P (one of its greatest assets) is lost due to the sensitive nature of the finger-mouse button.  If you were able to find a fix, I'd appreciate your sharing.

---

### Post by darussell1 on 2012-09-21
For what it's worth, I'm still searching for a fix.  However, running Xubuntu 12.04.1, I was able to change the StickPointer moouse-button selection from Right to Left, and at least got rid of the pesky problem of dragging files all over the screen.

---

### Post by UltimateCat on 2012-09-22
I have a Sony Vaio and I solved the mouse problem.

I went to Staples office store and purchased a brand new wireless mouse.
Since plugging in the small dongle that came with the mouse and using the mouse I stopped using the touch pad on the Vaio.

It's not a permanent fix but that touch pad is way to fussy for me-

If I find a permanent fix I will post it-

---

### Post by darussell1 on 2012-09-24
Found an excellent fix on Micro PC Talk Forum for our Sony UXs.  While it says partial, it seems to have solved my problems, completely.
 
Here it is:
I don't know if a lot of people use their UX's with linux these days. I bought mine two months ago and have been fighting the over sensitive tapping problem with the Alps DualPoint Stick ever since.

I only use linux on this machine, but didn't want to give up using the mouse just because of a driver problem. When this thing came out there were fixes for 2.6x kernels, using the synaptics driver etc. None of that works anymore. 

So I took the psmouse driver and modified it to almost disable hardware tapping. It still partially works, but at least, I got it to the point where it's almost usable. I thought I'd share it with you [IMG]http://www.micropctalk.com/forums/images/smilies/smile.gif[/IMG]

All of the modified source code I got it from here (thank you veery veeery muuch!!) : [[COLOR=#80aaff]http://xrgtn.livejournal.com/[/COLOR]]("http://xrgtn.livejournal.com/")

[COLOR=red]NOTE[/COLOR]: I've build this using the source code from a 3.5 kernel, which is what I'm running. It should work well with older versions but I can't test it since that's what I'm running in every computer.

Tested on Ubuntu 12.10 (beta) (x86)

You can pick the DKMS tar file from here: [[COLOR=#80aaff]http://www.mediafire.com/download.php?amdhvd0k3fsaa6j[/COLOR]]("http://www.mediafire.com/download.php?amdhvd0k3fsaa6j")
(Sorry, the forum doesn't allow anything but zip files and not anything bigger than 97 kb...come on!)

INSTRUCTIONS (FROM TERMINAL, AS ROOT): 
1. Copy mouse.tar.gz to /usr/src: **cp mouse.tar.gz /usr/src**
2. Go to /usr/src: **cd /usr/src**
3. Gunzip it, and untar it: **tar xzvf mouse.tar.gz**
4. Add the new module to DKMS: **dkms add -m psmouse -v ux**
5. Build the new kernel module through DKMS: **dkms build -m psmouse -v ux**
6. Install the new kernel module through DKMS: **dkms install -m psmouse -v ux**
7. Remove the psmouse module from the running kernel: **modprobe -r psmouse**
8. Activate the newly created psmouse module: **modprobe psmouse**

That's it! Now the mouse will mostly work as expected, and it will keep like that with every kernel update!

---

### Post by acruhl on 2013-05-10
This is my first post, I hope this issue is still relevant to others.

I recently bought a used VGN-UX280P and installed Lubuntu 12.04 after shrinking the Windows XP partition using gparted. I am dual booting Windows XP and Lubuntu.

I noticed that I have the "pointer stick select" problem if I cold boot the machine and boot Linux first. 

However, if I choose Windows XP in grub, then inside Windows I disable the "pointer stick select" (not sure exactly what this is called) using the Alps software in Windows, this setting persists if I reboot the machine (not shutdown) and then choose Linux with grub.

If I shut down the machine and then boot Linux, the change does not persist (I have the pointer problem again). If I shut down and boot Windows, the change does persist, so Windows is probably setting this at boot time.

So I'm sure Windows is able to make a setting in the mouse hardware which persists as long as the machine is not shut down (cold booted).

Linux should be able to do this too, given that someone knows what setting to change. I'd actually prefer not to disable it completely, I just want to drastically reduce it's sensitivity.

Incidentally, if I reduce the sensitivity in Windows and then reboot into Linux (without shutting down), this change persists in Linux as well (as long as the machine is not shut down).

I'm going to research this, however I'm not a kernel or driver savvy person so I'm not likely to find a solution anytime soon. Is there someone who could help me with this?

Thanks.

EDIT: Sorry I should have mentioned that I looked at the driver code above, and it's nice but it's not giving me (us?) an interface to adjust the sensitivity. I am looking at the code to decide if I can change settings in real time instead of having to change the driver.

---

