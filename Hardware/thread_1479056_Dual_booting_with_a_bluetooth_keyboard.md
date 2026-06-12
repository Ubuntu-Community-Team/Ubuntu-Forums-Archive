---
title: "Dual booting with a bluetooth keyboard"
date: 2010-05-10
forum: Hardware
---

### Post by robincawser on 2010-05-10
Hello. 
I am dual booting Ubuntu 10.04 and windows 7 and I use a bluetooth microsoft mobile keyboard 6000 (which is actually quite nice).

So I have my keyboard paired under Ubuntu, and it works fine, but when I boot into windows, I have to use a wired keyboard to login, and then I need to re-pair my bluetooth keyboard (the same process happens when booting back to Ubuntu).

I've come to terms with the fact that I probably won't be able to use a bluetooth keyboard in grub2 to select my OS. But it would be really nice if the bluetooth keyboard just worked in both OSs.

Note: I don't think I can use manual passkeys for the BT keyboard, as both OSs seem to generate random passkeys for me to enter on the keyboard.

Any ideas?

---

### Post by sagarm on 2010-05-10
I'm having the same problem.  I haven't had a chance to try this, but I think that if you manage both OSs to use the same passcode, the keyboard will work without re-pairing.

I think what I'll do is write down the passcode that Windows picks, and then set the passcode in Ubuntu manually--this was possible in 9.10, at least, haven't tried it in 10.04.

One possible issue is that I have to put the keyboard back into discoverable mode for Ubuntu to find it.  Hopefully that won't clear the passcode.  If it does, I'll start over pairing with Windows, switch back to Ubuntu, and try to find where the passcode is stored so that I can just update it manually.

If you try this before I do, let me know how it works for you.

---

### Post by robincawser on 2010-05-15
Yeah I tried using the passkey that windows picked, and using it in Ubuntu, but as you say I had to put the keyboard into discoverable mode, which I think *does wipe* the passkey.

I also tried the passkey that ubuntu gave me and using it in windows, but had the same problem. 

Let me know how you get on though. I'm just using a USB keyboard when I need windows, and sticking to my bluetooth keyboard in Ubuntu.

---

### Post by maxiclo on 2010-05-23
Hi all,
I have the same problem (same keyboard) and I tried to use manually the pass key code in Ubuntu after registering in Windows, without success.
 
Any Idea?
 
Thank you.

---

### Post by harbulot on 2010-05-26
Hi, I got it to work with mine, by copying the bluetooth link key. Here is what I did:


[LIST]
[*]Find the bluetooth address of the PC/dongle (let's say AA:11:11:11:11:11).
[*]Find the bluetooth address of the keyboard (let's say BB:22:22:22:22:22).
[*]Pair the device normally, under Linux (via the Gnome panel).
[/LIST]
There should be a file called /var/lib/bluetooth/AA:11:11:11:11:11/linkkeys, which contains a line like this:

```
BB:22:22:22:22:22 xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx 0 6
```Here, xxxx is 16 bytes written continuously in hexadecimal, that's the link key.

[LIST]
[*]Pair the device normally, under Windows (this will change the key). Get the key from Windows. In my case, it was in this registry entry:
[/LIST]
```
SYSTEM\ControlSet002\services\BTHPORT\Parameters\Keys\aa1111111111\bb2222222222
```Unfortunately, RegEdit says "access is denied" when I get to Keys, even when logged on as administrator. (I suppose it might be in another ControlSet in some cases.)


[LIST]
[*]Reboot under Linux, install chntpw. The version packaged with Lucid (0.99.5) doesn't seem to support registry in 64-bit. The latest version in the Debian repo (0.99.6-2) worked for me.
[/LIST]

[LIST]
[*]To avoid unwanted modifications of the Windows registry from Linux, I've copied the SYSTEM file somewhere else, from: /path/to/Windows/System32/config/SYSTEM
[*]I've then opened it with chntpw (browse registry with ls/cd; help with ?):
[/LIST]
[INDENT]```
chntpw -e SYSTEM

> ls
> cd ControlSet002\services\BTHPORT\Parameters\Keys
> ls
> cd aa1111111111
> ls
> hex bb2222222222
```This produces something like this:
```

:00000 xx xx xx xx xx xx xx
```Here, "xx xx xx" is another 16 bytes, in hexadecimal, represented the link key set up in Windows.

Finally, I copied that (and removed the spaces) to replace the value already in /var/lib/bluetooth/AA:11:11:11:11:11/linkkeys.

I had to disconnect and reconnect (via the Gnome applet), but I had to do that sometimes anyway. (It doesn't seem to work before being logged on either, but that the same, it was happening even with being paired under Linux only. That's probably a different problem.)

It worked for me. It's probably a bit complex for people who are not comfortable editing config files. I think it's safer to work on a copy of the SYSTEM registry file too, just in case something goes wrong.
[/INDENT]

---

### Post by robincawser on 2010-06-03
Thanks for taking the time to reply harbulot. When I have a chance I will give this method a go.
Thanks again!

---

### Post by mbehensky on 2010-08-06
Hi, all-

I can confirm that the technique of copying the link keys does in fact work with my Dell bluetooth keyboard.

I first purchased the Dell BT keyboard/mouse combo a few years ago on EBay for my mythtv media pc (Fedora based).   After pairing it in Windows, it initially just worked in Linux as well.  Last week, however, the USB bluetooth dongle that came with the combo failed, and I purchased a Zoom one at Fry's.

Unfortunately, with the new dongle after I paired it in Windows XP, it didn't work in Linux.  If I paired it in Linux, it then didn't work in Windows.  It never worked in the BIOS or GRUB.

I embarked on an odessy of upgrading distributions, upgrading mythtv, and endless reboots without success until I found the previous post.  I was able to win using that technique, although I ran into some trouble.

First, to get the BTHPORT registry key to exist and work, I had to change my bluetooth driver to the default windows version (not bluesoleil that came with the dongle).  To do this I unplugged the USB Dongle, removed bluesoleil with Add/Remove Programs, and plugged in the dongle again.  I then installed Windows bluetooth.

If you have the WIDCOMM bluetooth driver, you can remove it the same way.  I can't guarantee that the default  windows driver will know about your bluetooth interface hardware (especially if it is built in to a laptop), so this may not work for you.

Next, when I used regedit to look at the registry entry in Windows after my keyboard was paired, I found that the Parameters/Keys entry was empty.  I figured the above post was just wrong and messed around for another few hours until I did a search for "windows hidden registry keys" on google.  If I had just installed the linux registry edit package, I would probably have found the link key right away, but I didn't.

In any case, I found a post describing a way of running regedit under windows as the SYSTEM account, which lets you look at these hidden keys.  First, find the psexec.exe programin the pstools package at

 [http://technet.microsoft.com/en-us/sysinternals/bb897553.aspx](http://technet.microsoft.com/en-us/sysinternals/bb897553.aspx)

Then, copy the psexec.exe file from the zip file into some directory on your computer.

Run cmd.exe, and change to that directory.

type:

psexec -s -i regedit.exe

You will then run regedit as SYSTEM, and be able to find the link key entry from windows.

I copied the key into a text file, rebooted into linux, and edited the /var/lib/bluetooth/linkkeys entry for my keyboard, unplugged the USB dongle, plugged it back in, and the keyboard just worked in linux.  It continued to work when I booted back into windows.

It still doesn't work in GRUB, however.  This is not surprising, since there is no bluetooth driver for GRUB.  I am researching some method of choosing which OS to boot, but for now I just plugged in a PS2 keyboard that I use at boot time.  I am back to remotely controlling my media PC in both Windows and Linux.

:)

---

### Post by duphenix on 2010-09-21
harbulot, you are my new hero.  This worked great.

---

### Post by HeinekenPissr on 2010-10-06
At first glance this looks tougher than it really is.  Actually I'm pleasantly surprised at how well this works on first attempt

thanks again

---

### Post by buntucheck on 2011-07-14
Hi,

I was very happy to find this thread as it seemed to have exactly the solution that I was looking for.

I followed all the steps which harbulot described however the keyboard still does not connect under ubuntu (ubuntu 11.04 with gnome3). Found out the key, which is used under win7 and replaced the original one in the linkkeys file.

Tried to reconnect, replugged the bluetooth stick, turned it on and off in the gnome applet. 
The keyboard is displayed as paired, but inactive. When I switch it to active in the gnome applet, it stays active for about 6 secs and then switches back to inactive.

Any ideas how to resolve this or to find out what it going wrong?

---

### Post by aelohin on 2011-09-29
Perfect, this work absolutely great, thanks harbulot and mbehensky!, the tool you say, made the things very easy.

This also work with the mouse, I just copy the key from windows, and added on ubuntu. Uubuntu don't set a key for the mouse, but I just added the line in the same way as the keyword and work perfect.

Next challenge, do this with the Android so the keyword and mouse are sync in Windows, Ubuntu and Android. 

Thanks.

---

### Post by niksri4 on 2012-08-10
ubuntu is installed in windows 7 like other application
i can not access my bluetooth enable phone from windows 7. but it is working fine in ubuntu 12.04.
from above solutions i had tried to open bluetooth link key but it says "access denied u can not have previlage to open" . 
i had tried from terminal from root@ubuntu but again "permission denied"
so how i open link key file???????:confused:
any other method to see link keys.???:confused:
please help me guys......!!!!!!!!:(:(

---

### Post by elang on 2013-04-12
Hey, first off: Thanks a lot for this method. It worked fine for me for a long time with my bluettoth headset as well.

Now, unfortunately I had to delete pairings and re-pair my bluetooth device (which I seubsequently did in Linux first and Windows second). I went ahead and repeated the whole process. After that, whenever I try to connect the device, I am not successful. In the the bluetooth settings options, I see that whenever I try to connect the headset, the connection tab briefly goes to "ON", but immediately returns to "OFF". The headset works fine when I pair it again with Ubuntu (which of course now messes my settings for windows)

I am flummoxed as to why your method used to work earlier, but not now.
I am using the same version of Ubuntu: 32bit 12.04 LTS

---

### Post by rafaelvega on 2013-10-09
In case someone needs instructions on how to do this for dual booting Ubuntu + MacOS, they are here: [https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1001825](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1001825) (comment #20 and #21)

---

