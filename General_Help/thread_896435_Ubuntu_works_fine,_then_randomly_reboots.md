---
title: "Ubuntu works fine, then randomly reboots"
date: 2008-08-21
forum: General Help
---

### Post by junkemailmenot on 2008-08-21
I just got ubuntu running yesterday, on an external USB hard drive, as a dual boot with Vista on my Dell Vostro 1400.

Everything seems to be working fine (graphics, wireless, sound, etc...), but then randomly as I'm working, it will reboot itself.  It's not a full reboot (rebooting the whole computer, going through the boot loader, etc...) but rather, it flashes to black screen with white text going across it quickly, and then I have to login again, and begin a new session.

The errors I found that I think are causing it are the pulseaudio...Stale PID file, overwriting:

Aug 21 10:44:28 Gir pulseaudio[21879]: pid.c: Stale PID file, overwriting.
Aug 21 10:57:15 Gir -- MARK --
Aug 21 11:07:57 Gir syslogd 1.5.0#1ubuntu1: restart.
Aug 21 11:22:11 Gir pulseaudio[30463]: pid.c: Stale PID file, overwriting.
Aug 21 11:29:18 Gir kernel: [ 3625.954386] gtk-gnash[31070]: segfault at 085872a0 eip b5595f5b esp b3ffd974 error 6
Aug 21 11:30:14 Gir kernel: [ 3662.976871] gtk-gnash[31105]: segfault at 085966e0 eip b5b72eef esp b5828974 error 6
Aug 21 11:30:57 Gir kernel: [ 3698.562078] gtk-gnash[31164]: segfault at 08565090 eip b5435f28 esp b483b974 error 6
Aug 21 11:38:36 Gir pulseaudio[31639]: pid.c: Stale PID file, overwriting.
Aug 21 11:57:15 Gir -- MARK --
Aug 21 12:17:15 Gir -- MARK --
Aug 21 12:37:15 Gir -- MARK --
Aug 21 12:47:31 Gir Cleanup, done. Exitting... 
Aug 21 13:08:17 Gir pulseaudio[5349]: pid.c: Stale PID file, overwriting.
Aug 21 13:09:51 Gir Failed to open the panel socket 
Aug 21 13:09:51 Gir Failed to open the panel socket 
Aug 21 13:09:59 Gir pulseaudio[6002]: pid.c: Stale PID file, overwriting.

I'm completely new to this...  Can anybody out there help me out?

---

### Post by hermes0710 on 2008-08-21
No idea about what it might be happening but is there any case your drive has an automatic shutdown function when not in use?

---

### Post by madhusker on 2008-09-03
This seems to be a common problem with ubuntu and nobody has the answer.

---

### Post by lucho64 on 2008-09-04
That is not a reboot. X is crashing. You should look in the /var/log/Xorg.*.log It seems to me that gnash segfaulting is more likely to bring X down than whatever pulseaudio is complaining about. But in any case, you need to look in the X logs.

---

### Post by madhusker on 2008-09-04
I will be sure to check it right after a reboot next time.  I don't see much in any of the xorg logs.  They all end with this...

```

(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetClientVersion: 0 9
SetGrabKeysState - disabled
```

---

### Post by lucho64 on 2008-09-04
> **madhusker said:**
> I will be sure to check it right after a reboot next time.  I don't see much in any of the xorg logs.  They all end with this...


I was actually referring to junkemailmenot's problem. Given what you've posted elsewhere, it seems that it might be something to do with your raid drivers. You should post your lspci -v and lsmod but in a thread that is more appropriate to your problem. I think it's not in good etiquette to hijack junkermailmenot's thread, that is unrelated. OTOH, it's two weeks old, so I guess it's not good etiquette to leave it unresolved ...

---

### Post by bodhi.zazen on 2008-09-04
> **madhusker said:**
> This seems to be a common problem with ubuntu and nobody has the answer.

LOL, it is not a common problem and it is a complex problem.

Basically it is either a hardware problem or a software problem :)

If it is a software problem, you need to look at your logs (software usually leaves error messages in the logs).

If it is a hardware problem, the logs are clean (hardware problems usually do not generate error messages).

The problem is reading the logs, there are a lot of them and you need to know what is normal and what is not.

[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

If I were going to take a guess, I think the most common cause of random reboots is actually a hardware problem, over heating. Clean your box and monitor your core temp.

---

### Post by madhusker on 2008-09-04
> **bodhi.zazen said:**
> LOL, it is not a common problem and it is a complex problem.

Basically it is either a hardware problem or a software problem :)



It is for certain software but can't pinpoint it. It default install so it's not like anything has been changed or configured really. This machine is rock solid on other distros. As far as the hijacking; our logs are very similar with a random X reboot as reported by syslog. Just need to isolate why it's causing an X crash with nothing in Xorg logs.

---

### Post by bilijoe on 2008-09-04
> **madhusker said:**
> This seems to be a common problem with ubuntu and nobody has the answer. I don't recognize this as a "common problem" with Ubuntu.  

How did you install Ubuntu?
Did you download an .iso file?
If so, did you perform the MD5SUM check on it?
If not, run the MD5SUM check on the .iso file NOW.

If the MD5SUM does not match the published value, destroy the installation disk you created, delete the .iso file you downloaded, and download another copy.

Check the MD5SUM value for the new download, before doing anything else.
If the MD5SUM values match, continue--if not, delete the .iso file, download another copy, and repeat the process.

When you get a match between the MD5SUM value generated from the .iso file, and the one published for the ***exact version you downloaded***, burn the .iso to disk.

After burning the CD, boot from it and select "Check Disk For Errors."
If there are no errors, proceed.  Otherwise, destroy the disk, and burn another one.

When you get a disk where the Error Check reports no errors, boot from the disk and select "Install".

Once the install is complete, ***before you do anything else***, run the Update Manager.
Install ALL the updates--no matter how many there are--install _ALL_ of them!  

You should now have a "clean Install" and your system should run, trouble free, as long as you always install the updates when you get the little notification in the top panel that alerts you that updates are available.

It is amazing how often transmission errors result in a corrupted .iso file.
It is also amazing how often copy errors result in corrupted files on the install disk.

If you follow this procedure every time you download a new .iso file, you should ALWAYS end up with a clean running system (save for hardware compatibility problems--which are another matter entirely).

---

