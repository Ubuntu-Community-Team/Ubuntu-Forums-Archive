---
title: "Acer Travelmate 380. Boot dies after lucid TLS upgrade"
date: 2010-05-01
forum: Hardware
---

### Post by vsparki on 2010-05-01
Everything was fine on my TravelMate 380 running Lucid beta untill the final upgrades to TLS release. Then on restart the boot process permanently hangs just after the first ubuntu splash screen shows. Just before splash is the message console "acer-wmi: no or unsupported wmi interface, unable to load"
Tried a clean install of the TLS release from usb stick but same thing happens when usb stick boots :-/
Anything documented on this? or fixes known? or any suggestions?
many thanks

---

### Post by dino99 on 2010-05-01
i'm googling around that error and found that its the acer wifi activation mode needed with windows ( so built-in acer hardware) that is generating this problem with Linux  :confused:

acer dont like linux :evil:

as a solution we need to add into /etc/modules some modules, using the command below: 

    sudo gedit /etc/modules

and add in it:

    acer-wmi

    ath5k
The problem now is to be able to do that: find a way to boot in recovery mode or with a live-cd

here is a report bug about that:

[https://bugs.launchpad.net/ubuntu/+source/acerhk/+bug/555828](https://bugs.launchpad.net/ubuntu/+source/acerhk/+bug/555828)

---

### Post by vsparki on 2010-05-01
Tried that - didn't work :(
For the moment i am booting fine with the previous kernel, 2.6.31-21.
I guess it's a problem with the newest kernel, 2.6.32-21. 




 > **dino99 said:**
> 

    sudo gedit /etc/modules

and add in it:

    acer-wmi
ath5k

---

### Post by bob2hh on 2010-05-01
Same problem here: No boot from USB stick, ... 
I finally did the following:

- Fresh 9.10 install
- Upgrade (all night long, plus some nasty questions between first shower and shaving and breakfast ...)

finally, I tried again to boot and ... same problem again.

However, since I had the option to boot with recovery in the grub menu, I tried to boot with recovery, and using the failsafe screen manager option it worked. So I thought it had to do with /etc/X11/xorg.conf somehow.

Hence, this gave me the hints to trace the problem:
- If you go to /etc/X11 you will notice a file named xorg.conf.failsafe, and the fact that xorg.conf is missing. Simply copy this file, just as it is, under xorg.conf (cp xorg.conf.failsafe xorg.conf).

Reboot and it will succeed booting.

It still shows for a brief instant the message console "acer-wmi: no or unsupported wmi interface, unable to load". To get rid of it, I went to /etc/modprobe.d/blacklist.conf and I added there as a last line acer-wmi. This way, the system avoids attempting to load it. As far as I have tried, everything works fine without it (I am using an Atheros-based PCMCIA card for wifi instead of the internal one since I found it quite "deaf" signalreceivingwise).

It is not the best and elegant solution, but it does the job while the kernel is patched. I also confirm that 2.6.31-14 kernel works without needing any change, all the previous is only necessary for 2.6.31-21 kernel.

Regards,
Robert.

PS: My laptop is a quite old Acer Travelmate 2301LMi, but hardwarewise seems like yours as far as this is concerned.

---

### Post by jesgar on 2010-05-01
Acer don't like Linux? But how it is possible that something works on old versions and does't work on the newest? Don't you think someone at kernel team has touched something he musn't?

---

### Post by jmtalarn on 2010-05-02
Hello my friends!

I think I have the same problem with my Travelmate 240 LC. 
I upgraded my Ubuntu 9.10 to 10.04 and doesn't boot with the kernel 2.6.32-XXX and when I boot from the kernel 2.6.31-XXX (Last updated in 9.10) I don't get my SMC8235W Wifi PCMCIA Card running. 
10.4 is worst than 9.10 ?

---

### Post by jmtalarn on 2010-05-03
How we have to install Ubuntu 10.4 to avoid this problem?

I found this:
[https://patchwork.kernel.org/patch/16538/]("https://patchwork.kernel.org/patch/16538/")

it's related with our problem?

There are many bugs related with acer-wmi in launchpad:
[https://bugs.launchpad.net/bugs/+bugs?field.searchtext=acer-wmi&search=Search+Bug+Reports&field.scope=all&field.scope.target=]("https://bugs.launchpad.net/bugs/+bugs?field.searchtext=acer-wmi&search=Search+Bug+Reports&field.scope=all&field.scope.target=")

---

### Post by jmtalarn on 2010-05-03
Both Travelmate 240 and 380 are unsupported by acer-wmi.Then why is loaded?

[http://code.google.com/p/aceracpi/wiki/SupportedHardware]("http://code.google.com/p/aceracpi/wiki/SupportedHardware")

---

### Post by guidoorefice on 2010-05-03
[SIZE=5]**SOLVED!**[/SIZE]

Dear all,
I had the same problem with an Acer TravelMate 382TMi, which was working perfectly with Ubuntu Desktop 9.10, until I updated (from the GUI) to Ubuntu 10.04 LTS.

Googling around, it seems that the problem was actually well-known:

From Ubuntu 10.04 Release Notes:
[http://www.ubuntu.com/getubuntu/releasenotes/1004](http://www.ubuntu.com/getubuntu/releasenotes/1004)

>Intel 8xx X freezes/crashes
>The -intel driver fails with X freezes or crashes on certain i8xx hardware. The issue is 
>known >upstream but solutions are still under development. For now, to work around 
>the issue, boot >with the -vesa video driver. 
>See [http://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](http://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) for further details. 

By reading on [http://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](http://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)
I re-enabled KMS, and Ubuntu 10.04 worked fine again.

To boot, remember to press/release SHIFT (maybe multiple times helps) AS SOON AS Ubuntu starts booting: that is just before the Ubuntu logo appears. 
By doing this, you are asking the boot-loader, Grub, to show you a menu with various boot options.
Choose to boot with the kernel with the the second-highest version number

After having booted up, open a Terminal and type:


```

echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf
sudo update-initramfs -u

```Then reboot normally. 

I just solved the problem in this way.
Also the message "acer-wmi: no or unsupported wmi interface, unable to load" during boot disappeared: I did NOT change /etc/modules or the like.

If this does not solve your problem (maybe you have a different laptop model), 
I would suggest to try out the other methods listed at 
[http://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](http://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)



Hope this helps.

---

### Post by RobC67 on 2010-05-04
Thanks Guidoorifice!
 
That solution worked fine for my old Travelmate 4000, still get the error message about the wmi but it now boots past this and I can get into 10.04 no problems. Hopefully an update will sort this out properly at some point in the future.

---

### Post by pontvil on 2010-05-08
And thanks from me too... Your solution worked for my travelmate 2301LC.

---

### Post by TTown on 2010-05-21
Worked great for Acer Travelmate 660 (TM661LCi // Chipset - Intel 855GM ).
> **guidoorefice said:**
> [SIZE=5]**SOLVED!**[/SIZE]
```

echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf
sudo update-initramfs -u

```Then reboot normally.


Thank you for your post. I still don't understand how it achieves it, but it works.

---

### Post by vsparki on 2010-05-27
echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf
sudo update-initramfs -u 
Worked for me too :)
TravelMate 380 (382TMi) now booting with kernel 2.6.32-22.
Much much thanks.

---

### Post by therezin on 2010-07-05
I tried this on my Travelmate 530 to remove the annoying message (it let me get in fine, but the message at boot annoyed me). Now, when I boot I get a message about Ubuntu running in low graphics mode. The error is:

```

(EE)VESA: Kernel modesetting driver in use, refusing to load
(EE)No devices detected.
```

How do I go about undoing what I did? :-S

---

### Post by IcyAero on 2010-10-29
I tried guidoorefice's method, but unfortunately it did not fix the acer-wmi, unable to load -problem and this was the first possible solution I've found after days of search. I'm pretty new to Ubuntu, and I'm trying to make this on an old Acer Aspire 3003LC -laptop with Ubuntu 10.04 LTS (LXDE desktop). Any ideas?

---

### Post by henrylaw on 2010-11-26
> **guidoorefice said:**
> [SIZE=5]**SOLVED!**[/SIZE]

```

echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf
sudo update-initramfs -u

```Then reboot normally. 


Works for an Acer TravelMate 660 too.  Well done, Guido!:KS

---

