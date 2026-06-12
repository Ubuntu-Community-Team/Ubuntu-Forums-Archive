---
title: "USB problem Virtualbox 2.2.2 &amp; ubuntu 9.04"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by crakup on 2009-05-11
Hi everyone, 

i had ubuntu 8.04 and sun virtualbox 2.2.2 installed without problems, i could import the USB memories and USB ipods from the guest virtual machines (solaris 10, opensolaris and windows xp), but this week i reinstalled mi lap with ubuntu 9.04 (jaunty) and i installed a virtualbox 2.2.2 and imported my old virtualmachines....  all works fine, but i can't import the usb memories or ipods from the guest vm like in the last ubuntu version installed on my lap.

Do you know if this is a version bug?.....   any ideas?...

thks.

---

### Post by TransitMan on 2009-05-11
Did you install VirtualBox from the repos or from the website?
If from the repos, USB support is not available.
If from the repos, USB support is available and should be working without any need for any further intervention.
All my USB devices work, both from Ubuntu 9.04 and in WinXP in VirtualBox 2.2.2

---

### Post by crakup on 2009-05-11
i test with two versions:  from site of sun  and from repos with the synaptic.

i'ts a good new know that it's working for you.... i'm going to install the version from the site again.

did you do something additional to the installation of virtualbox?

---

### Post by TransitMan on 2009-05-11
I just made sure that when I installed and set up Windows that I had the USB controller checked off and put a USB device into the active position in SETTINGS.

---

### Post by crakup on 2009-05-11
Mabe the version that i installed first was scrabled....  the last version that i tested was the repos version.

Now i uninstall the virtualbox and reinstalled the version from the sun site.... All work fine, i can import the usb devices.

Thank you very much TransitMan...

---

### Post by Gatita78 on 2009-05-12
I did the instructions above and my USB port are not working. In the menu I can see all the USB devices but they are blocked so I cannot enable them.

---

### Post by peredur on 2009-05-12
Hi,

I have the same problem.  Ubuntu 9.04 64bit on a Lenovo laptop.  Using VirtualBox 2.2 (not the OSE version).  Followed the instructions in the user manual - i.e. added myself to the vboxusers group.

When I start VirtualBox, the Settings menu option is greyed out and I can find no way of activating it.

I, too, would be grateful for any help.

Cheers


Peter

---

### Post by peredur on 2009-05-12
Grovelling apologies.  My mistake.

After adding myself to the vboxusers group and then returning to the VM, I found that the installed interfaces (e.g. the webcam) were no longer greyed out.  So I stuck a USB stick into one of the interfaces and it came up in the Devices --> USB Devices menu just fine, and I could select it.

I then checked it out in Windows file explorer and it's OK.

So, it appears that I, at least, don't need to alter the settings at all, just add myself to the vboxusers group and enable the interface (when something's attached to it) in the Devices --> USB Devices menu.

I don't know what the Settings menu is for.  It's always greyed out for me.

Hope I haven't wasted anyone's time.

Cheers


Peter

---

### Post by ruelle on 2009-05-13
I have the same issue with virtualbox 2.2.2 and ubuntu 9.04..
any ideas?...

thanks!!

edit:
if I lunch Vbox with sudo there is no probelm!!

---

### Post by rfs1970 on 2009-05-18
I was facing the very same problem and none of the tutorials that I found could help me to fix this issue.

So finally I came across [this post]("http://falasca.com.br/index.php/configurando-conexoes-usb-no-virtualbox-220-no-linux-ubuntu-intrepid-ibex/") (in brazilian portuguese) and the solution was very easy:


1) # sudo gedit /etc/fstab
at the end of the file add this line:
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
(46 is the standard ID group for plugdev in ubuntu 9.04)

2) save the file
3) # sudo mount -a

That is it!

Now you can start your virtualbox with all your usb devices.

---

### Post by anteloop on 2009-05-26
> **rfs1970 said:**
> I was facing the very same problem and none of the tutorials that I found could help me to fix this issue.

So finally I came across [this post]("http://falasca.com.br/index.php/configurando-conexoes-usb-no-virtualbox-220-no-linux-ubuntu-intrepid-ibex/") (in brazilian portuguese) and the solution was very easy:


1) # sudo gedit /etc/fstab
at the end of the file add this line:
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
(46 is the standard ID group for plugdev in ubuntu 9.04)

2) save the file
3) # sudo mount -a

That is it!

Now you can start your virtualbox with all your usb devices.

rfs1970, That solve my problem, thank you very much!

---

### Post by dotdot on 2009-05-29
cheers for the vboxuser tip - caught me out YET again.

---

### Post by ssully on 2009-05-29
> **rfs1970 said:**
> 
1) # sudo gedit /etc/fstab
at the end of the file add this line:
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
(46 is the standard ID group for plugdev in ubuntu 9.04)

2) save the file
3) # sudo mount -a


Worked great for me: Jaunty 9.04, virtualbox-2.2, Thinkpad T43, USB devices no longer grayed out.  Thanks!

---

### Post by jhouse59 on 2009-05-30
> **rfs1970 said:**
> I was facing the very same problem and none of the tutorials that I found could help me to fix this issue.

So finally I came across [this post]("http://falasca.com.br/index.php/configurando-conexoes-usb-no-virtualbox-220-no-linux-ubuntu-intrepid-ibex/") (in brazilian portuguese) and the solution was very easy:


1) # sudo gedit /etc/fstab
at the end of the file add this line:
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
(46 is the standard ID group for plugdev in ubuntu 9.04)

2) save the file
3) # sudo mount -a

That is it!

Now you can start your virtualbox with all your usb devices.

Thanks rfs1970 that worked for me also. I had posted my problems at Kubuntu's Forums. then I came across this fix. I posted it there to help other people. But, I gave you the credit. Thanks again.

---

### Post by Grukmuck on 2009-05-31
> **rfs1970 said:**
> I was facing the very same problem and none of the tutorials that I found could help me to fix this issue.

So finally I came across [this post]("http://falasca.com.br/index.php/configurando-conexoes-usb-no-virtualbox-220-no-linux-ubuntu-intrepid-ibex/") (in brazilian portuguese) and the solution was very easy:


1) # sudo gedit /etc/fstab
at the end of the file add this line:
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
(46 is the standard ID group for plugdev in ubuntu 9.04)

2) save the file
3) # sudo mount -a

That is it!

Now you can start your virtualbox with all your usb devices.

Worked for me too, thanks.

-gruk

---

### Post by zerny89 on 2009-06-12
Hi,
how about me??
I'm still cannot attach my devices using that method..
please...
I'm using virtualbox 2.2.4 Jaunty fresh install.. 
(virtualbox-2.2  2.2.4-47978_Ubuntu_jaunty)

please help me...
thanks..

---

### Post by loveandequality on 2009-06-14
> **rfs1970 said:**
> I was facing the very same problem and none of the tutorials that I found could help me to fix this issue.

So finally I came across [this post]("http://falasca.com.br/index.php/configurando-conexoes-usb-no-virtualbox-220-no-linux-ubuntu-intrepid-ibex/") (in brazilian portuguese) and the solution was very easy:


1) # sudo gedit /etc/fstab
at the end of the file add this line:
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
(46 is the standard ID group for plugdev in ubuntu 9.04)

2) save the file
3) # sudo mount -a

That is it!

Now you can start your virtualbox with all your usb devices.


It work but you need to quit the app first before it works i had to do it twice so everyone that has trouble do it several times to make sure is not working.

---

### Post by ubuntoooooo on 2009-07-01
I don't mean to bump but I did all the fixes, added myself to the user group. What worked was running it as root.

---

### Post by dardack on 2009-08-30
Know this is an old bump, but felt I should respond, that this worked for me, adding the plugdev to the fstab i had added the vboxusers group originally, in 64 bit Jaunty.  I don't need this entry in my 32 bit Jaunty, but for some reason i do in 64bit.  Thanks for this fix.

---

### Post by RoyaleTee on 2009-09-17
SUCCESS!!! I do have to comment though. The file, fstab, already has a line in it:
none /proc/bus/usb usbfs devgid=124,devmode=664 0 0
 
I had to delete this line and add in the new one in order for it to work, for those of you who couldn't get it to work, you only need that line in this thread, not the one above. Again, THX!!!:guitar:

---

