---
title: "Suspend issues and ACPI"
date: 2005-10-28
forum: Hardware &amp; Laptops
---

### Post by lerrup on 2005-10-28
I am at present running breezy on a Samsung laptop.  Most of the laptop specific features work including niceties such as brightness and volume control alongside more fundamental things such as cpu frequency scaling.

What it doesn’t do is suspending/hibernating.  It powers down and powers up but the screen is permanently blank and the keyboard appears to be non-functional as no ctrl-alt f1 type terminals are available to try and find out what is wrong.

I have followed the Hoarypm instructions and those that relate to suspending with a nvidia card that are in the wiki but unfortunately these have not made any difference.

My question would be whether trying a new DSDT table would be likely to make a difference to this?  Also, is there anything else that someone might suggest as something to try to sort this out?

---

### Post by kashms on 2005-10-28
Did you try putting "acpi_sleep=s3_bios" as a kernel boot option?

---

### Post by lerrup on 2005-10-28
[QUOTE=kashms]Did you try putting "acpi_sleep=s3_bios" as a kernel boot option?[/QUOTE]

No I haven't - are you able to tell me how to do that?

---

### Post by kashms on 2005-10-28
[https://wiki.ubuntu.com/GrubHowto](https://wiki.ubuntu.com/GrubHowto)

Add "acpi_sleep=s3_bios" (without quotes) to the end of the line starting with "# kopt" in file /boot/grub/menu.lst.

---

### Post by lerrup on 2005-10-28
[QUOTE=kashms][https://wiki.ubuntu.com/GrubHowto](https://wiki.ubuntu.com/GrubHowto)

Add "acpi_sleep=s3_bios" (without quotes) to the end of the line starting with "# kopt" in file /boot/grub/menu.lst.[/QUOTE]

Thanks, I did add "resume=/dev/hda2 ro" to that line - do you know if they'll play well together?

---

### Post by kashms on 2005-10-28
there should be no problem with that

---

### Post by lerrup on 2005-10-28
still no luck.

Is there anything else I could try?

---

### Post by epb613 on 2005-10-28
My cl56 had the same simptoms you describe. To fix it, all I had to do was turn off framebuffering - ie: remove the words **splash** and **vga=771** from my kernel command line in the menu.lst file.

---

### Post by GoodPanos on 2005-10-28
[QUOTE=epb613]To fix it, all I had to do was turn off framebuffering - ie: remove the words **splash** and **vga=771** from my kernel command line in the menu.lst file.[/QUOTE]

You can just remove the *vga=771* and that will work.  Here's how you do it:

go into a terminal
*sudo nano /boot/grub/menu.lst*
look for the *# kopt=* line and add *vga=771* to the end
*Press Ctrl-X*
*Press Y*
*Press Enter*
*sudo update-grub* (this will append the vga=771 to the kernel lines)
*reboot*

Caution on some notebooks, like my Dell Inspiron 6000, the screen flashes or goes blank when booting.  Soon as Gnome is loaded the screen comes up fine.  So you can't see what's going on during boot.

Is there another setup where you can both see the booting process and also have Stand By/Hibernate?

---

### Post by hedge on 2005-10-28
You may like to try a software suspend if you not using a smp kernel. There is a howto on this subject using Suspend2. [http://www.ubuntuforums.org/showthread.php?t=75443](http://www.ubuntuforums.org/showthread.php?t=75443)
If you have a nvidia video card then you want this one too. [http://ubuntuforums.org/showthread.php?t=79295](http://ubuntuforums.org/showthread.php?t=79295)
And here is the official Suspend2 site. [http://www.suspend2.net](http://www.suspend2.net)

cheers

---

### Post by epb613 on 2005-10-29
[QUOTE=GoodPanos]You can just remove the *vga=771* and that will work.  Here's how you do it:

go into a terminal
*sudo nano /boot/grub/menu.lst*
look for the *# kopt=* line and add *vga=771* to the end
*Press Ctrl-X*
*Press Y*
*Press Enter*
*sudo update-grub* (this will append the vga=771 to the kernel lines)
*reboot*

Caution on some notebooks, like my Dell Inspiron 6000, the screen flashes or goes blank when booting.  Soon as Gnome is loaded the screen comes up fine.  So you can't see what's going on during boot.

Is there another setup where you can both see the booting process and also have Stand By/Hibernate?[/QUOTE]
You just described how to add the line; I was saying you have to remove it.

And yes, it should work even with framebuffering enabled - this was the case in the preview version of Breezy. I filed a bug report and someone else confirmed that it doesn't work in Breezy final, and people are working on fixing it.

---

### Post by lerrup on 2005-10-30
The VGA line isn't there in any case.

Interestongly, hibernation works (with lots of weird screen stuff at the beginning) and with a few probs with network manager, etc.

Suspend is just dead.

---

### Post by colgate on 2005-11-06
[QUOTE=lerrup]
Interestongly, hibernation works (with lots of weird screen stuff at the beginning) and with a few probs with network manager, etc.

Suspend is just dead.[/QUOTE]

I got a Fujitsu-Siemens Amilo M1420 and i have the same problem! Hibernation works flawlessy, but suspend don't! When I suspend the notebook goes down fine, when i wake it up it restore X, and almost everything (network, usb,services) but NO PS2 devices like my integrated keyboard e touchpad!
I've tried everything but I haven't found any way to get the keyboard working after suspend (though after hibernation it works perfectly!).

I've tried to recompile the kernel with ps2 devices modularized (module atkbd or similar) and forcing the module down (and the up) when suspending. But it didnt' worked. Though my usb mouse works perfetcly after suspend!
I've tried the swsusp2 patch to the kernel, too, without improvements (except that hibernation is much faster!)

I think that we need something like VBEtool for the keyboard, a piece of software that save and restore the state of ps2 devices (vbetool does the same for video card, AFAIK)

Do you think that we have to fill a bugzilla report with our DSDT table? or what? i need suspend....:cool: 

bye

Federico

---

### Post by strawman on 2005-11-08
Does your laptop have an ATI video card and are you using the fglrx video driver?  If you are then that is maybe why your suspend does not work; stick with the xorg supplied ati driver.

---

### Post by colgate on 2005-11-08
[QUOTE=strawman]Does your laptop have an ATI video card and are you using the fglrx video driver?  If you are then that is maybe why your suspend does not work; stick with the xorg supplied ati driver.[/QUOTE]

Yes, my laptop has a Radeon 9600 pro, but i've managed to make hibernation work with fglrx, too! (thanks to vbe tool) 
anyway i always make my tests with the open source driver (ati), I know that the proprietary one doesn't like very much suspend :p 

do you have any other hints?

bye

Federico

---

### Post by Patsoe on 2005-12-08
[QUOTE=GoodPanos]You can just remove the *vga=771* and that will work.  

[...]

Caution on some notebooks, like my Dell Inspiron 6000, the screen flashes or goes blank when booting.  Soon as Gnome is loaded the screen comes up fine.  So you can't see what's going on during boot.

Is there another setup where you can both see the booting process and also have Stand By/Hibernate?[/QUOTE]

Hi, if you're still interested: if I also remove the 'splash' option, I do see the booting messages, and also have working standby / sleep.

Apparently, if you remove 'vga=771' and not remove 'splash', the video mode is switched during booting, trying to show a splash screen, and that doesn't work out well without the 'vga=771' option. As a result the screen goes blank.

Bottom line: just remove both, who cares about the splash screen?

---

### Post by ewinslow on 2005-12-10
[QUOTE=Patsoe]
Bottom line: just remove both, who cares about the splash screen?[/QUOTE]

Hmmm. I've an Inspiron 6000, standard ATI drivers. I did remove the splash and the vga=771
Lost the pretty boot screen, of course, but did get to view all the boot messages.

It did come back from a suspend. Nice. Funny thing was on the first come back (I closed lid, and then opened it back up) I was navigating to this thread to post this response and it just went to sleep on its own. I woke it back up with a touch to the power button and it seems to be fine.

We'll see how it behaves in the near future, but heck, this is better than it was.

Thanks for the tip.

---

### Post by GoodPanos on 2005-12-11
[QUOTE=epb613]You just described how to add the line; I was saying you have to remove it.[/QUOTE]
I apologize for that.  I meant for the removal.  You follow the same steps but instead of adding it you remove it.

But now I'm wondering, **Patsoe** from what lines did you remove the *vga=771* and *splash*?

---

### Post by ewinslow on 2005-12-12
[QUOTE=GoodPanos]But now I'm wondering, **Patsoe** from what lines did you remove the *vga=771* and *splash*?[/QUOTE]
*vga=771* is from the ```
#kopt
``` line and *splash* is from the ```
#nonaltoptions=quiet
``` line.

---

### Post by Patsoe on 2005-12-12
...what ewinslow said :)

I tried these settings first by pressing 'e' (for edit) in Grub, and when that worked, I changed the configuration file.

---

### Post by GoodPanos on 2005-12-13
Thank you **ewinslow** for the information.  I finally got suspension to work.  It will not work with the ATI drivers though but that's okay.

---

### Post by tmcg on 2005-12-20
@lerrup: I'm having the same problem on my samsung m40.

1. Suspend to disc works (with strange things on textscreen,
modem does not work after resume).

2.Suspend to ram does not work. Display & keybord (e.g. caps lock)
are dead after resume.

I found out the following:
Without running X-server the keybord works after resume on the
text console (try 'du /' ^C or reboot for example). But display is dead.
By playing around with vbetool i could restart the display ('vbetool post'),
but all it shows is a gray screen.

If you get any further please let me know.

---

### Post by Patsoe on 2005-12-20
On my system, now running the 'ati' drivers provided by xorg (important note: this applies to Dapper, in Breezy I could only run 'vesa'), I find that resume from suspend only works when I have the boot options 'noapic nolapic'. 

background info: I tried to remove these options because I included them in Breezy as a workaround for the 'double clock speed' problems; in the newer kernel coming with Dapper, this is no longer needed, so I removed the options - then I found my resume from suspend functionality broken. I do not understand their relation though.

---

### Post by knatten on 2005-12-21
FYI: On my ThinkPad Z60t, suspend works when activated from the menu or by Fn+F4, but not when activated by closing the lid. To make it work,  uncomment ACPI_SLEEP=true from /etc/default/acpi-support.

---

### Post by neuweiler on 2006-03-14
I experienced the same problems, followed the same hints in all possible configurations but what finally helped me on my HP nc8000 was this post from strawman:

[http://www.ubuntuforums.org/showthread.php?t=106564]("http://www.ubuntuforums.org/showthread.php?t=106564")

it was the WLAN configuration and not the gfx config ! 

neuweiler

---

