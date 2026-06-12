---
title: "[SOLVED] Failed to initialize HAL!"
date: 2008-11-11
forum: General Help
---

### Post by xX-Felipao-Xx on 2008-11-11
Hi guys,

I'm using Ubuntu Hardy Heron 8.04 and this error appears to me as soon as I log into Ubuntu. I've searched a lot about this, so many "solutions" but none of them worked for me.

Problems that this error caused (or at least, they weren't before):

[http://hosting07.imagecross.com/image-hosting-12/5687ubuntuforums.gif]("http://hosting07.imagecross.com/image-hosting-12/5687ubuntuforums.gif")

Look at the net icon, it got a cross of error, I dont know why, and it left me without internet connection (I don't have lan, or something, just connected directly to the modem).

And When I click in the Green little man running, which is the exit button nad it should show the "Restart", "Turn Off", "Suspend" button and that stuff, the GUI gets stucked and I cant click anywhere or do anything, just press Ctrl+Alt+Backspace and then, I restart or whatever from the Log-in screen.

Thanks !!

---

### Post by xX-Felipao-Xx on 2008-11-11
Up up?
Anyone?

---

### Post by xX-Felipao-Xx on 2008-11-11
Up! up!

---

### Post by xX-Felipao-Xx on 2008-11-14
UP?

Help please, still with no solution and I cant use Ubuntu (at least with internet ^^)

---

### Post by Yellow Pasque on 2008-11-14
- Make sure dbus has a lower "S number" than HAL in /etc/rc2.d/
- Go to terminal and try starting HAL manually:
```
sudo sh /etc/init.d/hal start
```
- Look for HAL/hal related messages with dmesg:
```
dmesg | grep HAL
dmesg | grep hal
```

Also: [https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931)

---

### Post by xX-Felipao-Xx on 2008-11-14
Hey, really thanks for your answer... lets see..
About the S number, it does. Hal is bigger (34) than dbus(12).

Here I post the outputs I got when I used those commands:

felipao@felipe-desktop:~$ sudo sh /etc/init.d/hal start
 * Starting Hardware abstraction layer hald   



felipao@felipe-desktop:~$ dmesg | grep HAL
felipao@felipe-desktop:~$ dmesg | grep hal
[   52.281222] hald[5444]: segfault at 0bf8a95b eip 08056e76 esp bff5c130 error 4


[  135.706462] hald[6338]: segfault at 0bf5e95b eip 08056e76 esp bfd63730 error 4
[  211.549036] hald[6703]: segfault at 0bf1395b eip 08056e76 esp bfcbce90 error 4

Thanks for helping me :)
Any idea now?

---

### Post by Yellow Pasque on 2008-11-14
> About the S number, it does. Hal is bigger (34) than dbus(12).
What is the S number for gdm? It should be bigger than 34. If it's not, post the output of:
```
ls /etc/rc2.d
```

---

### Post by xX-Felipao-Xx on 2008-11-15
Well, it doesn't. It has the number 30.

Here you are, the output of ls /etc/rc2.d :

README
S01policykit
S05vbesave
S10acpid
S10powernowd.early
S10sysklogd
S10xserver-xorg-input-wacom
S11klogd
S12dbus
S18avahi-daemon
S20apport
S20cupsys
S20dkms_autoinstaller
S20hotkey-setup
S20inetutils-inetd
S20nvidia-kernel
S20powernowd
S20rsync
S24dhcdbd
S24hal
S25pulseaudio
S30gdm
S89cron
S98usplash
S99acpi-support
S99laptop-mode
S99rc.local
S99rmnologin
S99stop-readahead


I tryied to rename it and I put S35gdm ^^ just trying, but it didn't work :(

Once again, thanks :)

---

### Post by xX-Felipao-Xx on 2008-11-24
Anybody??????
I still can't use Ubuntu because I have no internet there :S

Thanks :)

---

### Post by xX-Felipao-Xx on 2008-11-24
Up?

I need help ! :S

---

### Post by xX-Felipao-Xx on 2008-12-04
I solved it by reinstalling hal (the package is called "hal", selected it for reinstall and then, apply) from Synaptic. I thought that I couldn't do it because I did not have access to the internet, but then I tryied thinking that it may already have the package... that was happened, and I can use Ubuntu now again.

---

