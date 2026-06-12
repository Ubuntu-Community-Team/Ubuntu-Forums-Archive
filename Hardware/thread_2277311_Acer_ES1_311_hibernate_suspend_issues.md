---
title: "Acer ES1 311 hibernate suspend issues"
date: 2015-05-08
forum: Hardware
---

### Post by svesjo on 2015-05-08
Hi, bought a Acer ES1 311 laptop this week. Kicked out Win 8 and installed Lubuntu 15.04 instead.
Everything works quiet ok but not the 'sleep and wake up' functions, shutdown command stops Lubuntu but hardware still running.
I have changed acpi=off in grub but that didn't change the sleep and wake up behavior .

Another issue is the touch pad, it works but it's doing strange moves, now using external mouse instead.

I'm not sure where to start digging in this.

//BR Svesjo

---

### Post by svesjo on 2015-05-10
I have tried some of the Kernel parameters as mentioned in [http://blog.mdda.net/oss/2014/11/16/acer-e11-es1-111-c3nt-linux/](http://blog.mdda.net/oss/2014/11/16/acer-e11-es1-111-c3nt-linux/)
but no success. There is something that is not sync with the kernel and the Acer ES1 311 motherboard. Is this something that is possible to get sorted out?
[h=2][/h]

---

### Post by svesjo on 2015-05-13
Downgraded to linux-image-3.14.0-031400-generic_3.14.0-031400.201403310035_amd64 kernel but no improvements of the system sleep functions

---

### Post by leunam12 on 2015-05-14
My experience in the past has been that sleep problems are related to the video card most times. Try to install proprietary video drivers drivers. start jockey-gtk from terminal or find  "Additional Drivers" in menu.

---

### Post by svesjo on 2015-05-25
Hi.
Well, my opinion is now that this is a no can do this acer es1 311 and proper handling. I'm now running kernel 4.0.4, loaded Intels propertary driver for the Intel CPU but shutdown does not power off, powersave bugs out, restart bugs out. The graphics is some integrated Intel stuff with the moterboard for the celeron/atom cpu.  The touchpad is terrible, worst ever., must use external mouse to not go nuts.

---

### Post by mattharris4 on 2015-05-25
^ Frankly this sounds like a touchpad driver issue.  There are many laptops that have touchpads that don't work at all or work poorly in Linux (including my Toshiba in which the touchpad does not work at all although everything else seems to work fine including the buttons under the pad), that is the one thing developers tend to not develop fully as most people use an external mouse with their laptops and hardly ever use the touchpad anyway.  According to this link on an Acer forum they are having trouble with the touchpad on Win 8.1 installs as well:  [http://community.acer.com/t5/Notebooks-Netbooks/Acer-Aspire-ES1-311-touchpad-does-not-work/td-p/328483](http://community.acer.com/t5/Notebooks-Netbooks/Acer-Aspire-ES1-311-touchpad-does-not-work/td-p/328483) .  Below is some advice from the same Acer forum thread on how to alter the UEFI to possibly allow your touchpad to work (there is a poster there that said his works without any additional driver installs in Ubuntu).

You can enable touchpad on ES1-311 by doing below steps:

 
go to the cmos (F2 key press) and then find touchpad option, it may be 'advanced'.
change with 'basic' for the touchpad option value.
 
I think you can use touchpad.

Good luck with this issue.

---

### Post by svesjo on 2015-05-26
Hi the pad is working sort of... but it's a pain. The pad sensitivity zones  is a nightmare, the left/right integrated buttons as well. You must  keep the fingers about 4cm away when using left/right and pad zone at  same time or  the cursor goes to universe or other you get right click  or some other functions. That is a vendor issue I think when they don't  provide linux drivers for their closed pad hardware...

---

### Post by Niclas_Persson on 2015-06-19
Hi

I think i can help you on both of your issues, I have a Acer Aspire E3-112-C28H. I had same touch-pad issues that you describes, in windows the mouse cursor freezes and in linux it jumps around like crazy sometimes. Thats a HW fault and its linked to poor touch pad grounding. i replaced mu unit and now it works fine with same linux mint dist as before, and no freeze in windows.     

The hibernation issue i have not yet solved but i think im on the right track. This file [FONT=courier new]$sudo vim /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla[/FONT] contains faulty values for the specific HW. And thats what i need to figure out whats needs to be in there. Hope this helps. ;)

---

### Post by bernd6 on 2015-09-01
Hi,

I also have an Acer ES311 and I also had this hibernation problem. I also installed the new 4.2 kernel today. But again no success. Then I started trying weird things.
The solution was turning off "xHCI Support" in the BIOS Configuration. With this option you can enable/disable the external USB3.0 controller.

Now the hibernate mode and turning off works perfectly fine.

Regards,
Bernd

---

### Post by mörgæs on 2015-09-01
Thanks for your solution. Could you also post it in the [compatibility list]("http://ubuntuforums.org/showthread.php?t=1543006"), please? Then there is greater chance that people will find it.

---

### Post by Tom_Slab on 2015-12-24
On my *Acer es1-111* is suspend working only once, then it does not switch to suspend mode any more. I ran suspend from terminal using command: 

  sudo pm-suspend
  First suspend ok, after second I become this answer in terminal:

  "sudo: unable to open /var/lib/sudo/tomas/0: No such file or directory /usr/sbin/pm-suspend: 276: /usr/sbin/pm-suspend: cannot create /var/log/pm-suspend.log: Read-only file system"

and even more couple of minutes after first suspend system freeze

My approach is that I don't use suspend anymore :-)
With touchpad I have exactly the same issue as [**[COLOR=#000000]Niclas_Persson[/COLOR]**]("http://ubuntuforums.org/member.php?u=1988603") I think let replace the touchpad

---

