---
title: "How id Compiz/Kwin @ Intel 845 graphics in Jaunty"
date: 2009-04-17
forum: Hardware
---

### Post by ravi.xolve on 2009-04-17
When I upgraded from Hardy to Intrepid I was shocked:

1) To find that Compiz or Kwin effects are not available. This was the effect of blindly believing that increased version means "more" features.

2) Bluetooth didn't work. (Very minor problem, I could get it working using an older kernel)

Jaunty rc is out there and I want to ask the users those who have tested it on Intel 845 graphics chip. Does the desktop effects work? After so many release notes of Alphas and Betas, rc's release notes say [this,]("https://wiki.ubuntu.com/JauntyJackalope/ReleaseNotes#Performance%20regressions%20on%20Intel%20graphics%20cards") that it has been *resolved*. Is it so?

If so then I will just launch myself into downloading the RC (alternate disk) and upgrading my system.

---

### Post by ravi.xolve on 2009-04-17
Here is the output of lspci on my system:

```
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

---

### Post by theozzlives on 2009-04-19
> **ravi.xolve said:**
> When I upgraded from Hardy to Intrepid I was shocked:

1) To find that Compiz or Kwin effects are not available. This was the effect of blindly believing that increased version means "more" features.

2) Bluetooth didn't work. (Very minor problem, I could get it working using an older kernel)

Jaunty rc is out there and I want to ask the users those who have tested it on Intel 845 graphics chip. Does the desktop effects work? After so many release notes of Alphas and Betas, rc's release notes say [this,]("https://wiki.ubuntu.com/JauntyJackalope/ReleaseNotes#Performance%20regressions%20on%20Intel%20graphics%20cards") that it has been *resolved*. Is it so?

If so then I will just launch myself into downloading the RC (alternate disk) and upgrading my system.

```
Section "Device"
 Identifier "Configured Video Device"
 Driver "intel"
 Option "AccelMethod" "XAA"
EndSection

Section "Monitor"
 Identifier "Configured Monitor"
EndSection

Section "Screen"
 Identifier "Default Screen"
 Monitor "Configured Monitor"
 Device "Configured Video Device"
EndSection
```

This in your xorg.conf will work on Intrepid (be sure to get compiz-check and override the blacklist). I have yet to find a workaround for Jaunty.

---

### Post by glennric on 2009-04-28
I got compiz to run with an intel 845 integrated video card in Jaunty by installing the 2.4 intel drivers from intrepid and using the xorg.conf that theozzlives posted.  Follow the directions on [RevertingIntelDriverTo2.4]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4") to install the older intel driver.

---

### Post by ravi.xolve on 2009-04-29
Can you please post your xorg.conf file.

---

### Post by volneilo on 2009-04-29
> **glennric said:**
> I got compiz to run with an intel 845 integrated video card in Jaunty by installing the 2.4 intel drivers from intrepid and using the xorg.conf that theozzlives posted.  Follow the directions on [RevertingIntelDriverTo2.4]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4") to install the older intel driver.

\\:D/ \\:D/ \\:D/

**glennric** and **theozzlives**, I love you guys!!!

This workaround finally worked for me!!!

This is my card:

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

Thank you so much for sharing this!

---

### Post by ravi.xolve on 2009-04-30
Hey please post your xorg.conf

I am dying for it.

---

### Post by volneilo on 2009-04-30
> **ravi.xolve said:**
> Hey please post your xorg.conf

I am dying for it.


**ravi.xolve**, as for me I did exactly what was instructed in the post #4 by **glennric**, and my xorg.conf is exactly as described in post #3 by **theozzlives**. I'm in Jaunty, of course.

I noticed that my chipset is revision 01, the only case I've seen on forum. Almost all chips i845 are revision 03.

Now I got Compiz working, but the system is very S.L.O.W....:lolflag:

---

### Post by ravi.xolve on 2009-05-02
I checked it with the live cd. It works. Now downloading the alternate cd to upgrade my system.

---

### Post by glennric on 2009-05-03
There is another thing you can do to speed up the system.  That is change your mtrr settings.  See [HOWTO: Jaunty Intel Graphics Performance Guide]("http://ubuntuforums.org/showthread.php?t=1130582") steps 4 and 5 to find out how to do this.

---

### Post by ravi.xolve on 2009-05-04
The performance is way too low though the Kwin effects work, but if enabled the videos are too broken and I can see gears stopping for a moment in glxgears. However with the desktop effects disabled the performance is back.

This is really bad that even with open source drivers we can't work the things out.

---

### Post by ravi.xolve on 2009-05-04
@glennric
I tried the hack given in the link without creating the fixmtrr.sh script. I restarted the X using ctrl-alt-backspace but it didn't work.

---

### Post by glennric on 2009-05-04
In order for the mtrr change to take effect it will have to be done everytime you restart gdm.  If you type
```
sudo -s
echo "base=0xF0000000 size=0x08000000 type=write-combining" > /proc/mtrr
```
(of course with the appropriate base and size for your system), then restart gdm with ctrl-alt-backspace, and then type "cat /proc/mtrr" you will see that nothing has changed.  To make the settings effective you could first stop gdm with "sudo /etc/init.d/gdm stop", from a console type the above commands, and then restart gdm with "sudo /etc/init.d/gdm start" you will see the changes.

What I did to make the changes occur every time gdm starts the x-server is to edit the file /etc/init.d/gdm and put the line
```
echo "base=0xF0000000 size=0x08000000 type=write-combining" > /proc/mtrr
```
before the line containing "start-stop-daemon --start".  This is line 71 in Jaunty.

---

### Post by volneilo on 2009-05-04
> **glennric said:**
> In order for the mtrr change to take effect it will have to be done everytime you restart gdm.  If you type
```
sudo -s
echo "base=0xF0000000 size=0x08000000 type=write-combining" > /proc/mtrr
```
(of course with the appropriate base and size for your system), then restart gdm with ctrl-alt-backspace, and then type "cat /proc/mtrr" you will see that nothing has changed.  To make the settings effective you could first stop gdm with "sudo /etc/init.d/gdm stop", from a console type the above commands, and then restart gdm with "sudo /etc/init.d/gdm start" you will see the changes.

What I did to make the changes occur every time gdm starts the x-server is to edit the file /etc/init.d/gdm and put the line
```
echo "base=0xF0000000 size=0x08000000 type=write-combining" > /proc/mtrr
```
before the line containing "start-stop-daemon --start".  This is line 71 in Jaunty.

**glennric**, if I understood correctly, that inserted line turns the execution of the fixing to become automatic at every new boot? Making unnecessary, thus, any further manual execution?

---

### Post by pluckypigeon on 2009-05-13
I have the i845g rev01 nothing works for me with regard to compiz.

I haven't used compiz since hardy due to bugs.

Intrepid and Jaunty run really slow compared to Hardy for me.

Any other experiences??

---

### Post by volneilo on 2009-05-15
> **pluckypigeon said:**
> I have the i845g rev01 nothing works for me with regard to compiz.

I haven't used compiz since hardy due to bugs.

Intrepid and Jaunty run really slow compared to Hardy for me.

Any other experiences??

**pluckypigeon**, your experience seems to be quite similar to mine. Have you read all posts on this thread? Because I finally got Compiz to work precisely in this card (my box is an ancient Dell Optiplex GX60) thanks to the instructions given here by **glennric** and **theozzlives**. Please see my post (# 6).

The system is slow, but in fact it was never fast for me with Compiz. I got a Celeron 1.8Ghz and 1GB RAM.

Best luck to you ;).

---

### Post by pluckypigeon on 2009-05-15
> **volneilo said:**
> **pluckypigeon**, your experience seems to be quite similar to mine. Have you read all posts on this thread? Because I finally got Compiz to work precisely in this card (my box is an ancient Dell Optiplex GX60) thanks to the instructions given here by **glennric** and **theozzlives**. Please see my post (# 6).

The system is slow, but in fact it was never fast for me with Compiz. I got a Celeron 1.8Ghz and 1GB RAM.

Best luck to you ;).

Thanks but I tried that before. 

My system is even slower. 1.4Ghz with 512mb. It works fine with Hardy + compiz though;)

---

### Post by ravi.xolve on 2009-05-16
Same with me. My system is slower and sometimes KDE suspends the KWin effects.

---

