---
title: "Ubuntu 18.04.3 on Thinkpad T480s - thunderbolt 3 dock not working"
date: 2019-10-01
forum: Hardware
---

### Post by strattonbrazil on 2019-10-01
I recently installed Ubuntu 18.04.3 on a new Thinkpad T480s.  The Thinkpad Thunderbolt 3 Dock doesn't seem to charge the battery.  Ethernet and HDMI seem to work, but no power.  

I tried changing some settings in bios (screenshot below), but that doesn't seem to have any effect.  

[IMG]https://i.imgur.com/lCQZsAQ.jpg[/IMG]

kernel: 5.0.0-29-generic

Are there any additional drivers or configuration changes I need to make to allow power over the Thunderbolt 3 dock?

---

### Post by John Jason Jordan on 2019-12-21
> **strattonbrazil said:**
> I recently installed Ubuntu 18.04.3 on a new Thinkpad T480s.  The Thinkpad Thunderbolt 3 Dock doesn't seem to charge the battery.  Ethernet and HDMI seem to work, but no power.  I tried changing some settings in bios (screenshot below), but that doesn't seem to have any effect.  kernel: 5.0.0-29-generic
Are there any additional drivers or configuration changes I need to make to allow power over the Thunderbolt 3 dock?

I hear your pain. I have a brand new Thinkpad P73 with Xubuntu 18.04.3, which I upgraded to the 5.3 kernel. I also have the Thunderbolt 3 dock (40AN0230US), and it sort of works, sometimes. For example, I usually leave the computer running 24/7, but when I got up this morning the computer was shut down. I booted it and saw that the battery level was 85%. Apparently sometime during the night the dock stopped supplying power to the computer, which eventually shut down when the battery died. But then once the computer was shut down it must have started supplying power again. And as I type this the battery is now down to 50%. The USB ports work most of the time, but sometimes they stop working also. 

Searching the net revealed that you need bolt or tbt if you don't use Gnome or KDE. I installed bolt (it's in the repos), but there is no man page and I can't find documentation anywhere. Typing 'bolt' at the command line gives me 'command not found.' I have no idea what to do with bolt. As for tbt, I can't find it anywhere.

I could really use some help here.

---

### Post by oldfred on 2019-12-21
I seem to have bolt installed, but no Thunderbolt devices.
But it then shows Thunderbolt in System Settings, devices.

Several with Dell Thunderbolt based docks needed firmware update from Dell.
Do you have firmware updates available?

---

### Post by John Jason Jordan on 2019-12-21
> **oldfred said:**
> I seem to have bolt installed, but no Thunderbolt devices.
But it then shows Thunderbolt in System Settings, devices.
Several with Dell Thunderbolt based docks needed firmware update from Dell.
Do you have firmware updates available?

1) I can't find System Settings. Is this a GUI? Maybe I don't have it because I have Xfce.

2) There does exist a firmware update for my dock, available from Lenovo. Last night I downloaded it and then discovered that it requires Windows to install it, and there is no Linux version. However, the Lenovo page listed the things that it fixes, and none of them had anything to do with my problems.

3) I did finally find a tiny bit of documentation for bolt. Apparently the command is boltctl. Here is what it gave me:

```
boltctl
 &#9675; Lenovo ThinkPad Thunderbolt 3 Dock
   &#9500;&#9472; type:          peripheral
   &#9500;&#9472; name:          ThinkPad Thunderbolt 3 Dock
   &#9500;&#9472; vendor:        Lenovo
   &#9500;&#9472; uuid:          00cc88a9-7426-0801-ffff-ffffffffffff
   &#9500;&#9472; status:        disconnected
   &#9500;&#9472; authorized:    Sat 21 Dec 2019 04:40:08 AM UTC
   &#9500;&#9472; connected:     Sat 21 Dec 2019 04:40:08 AM UTC
   &#9492;&#9472; stored:        Sat 21 Dec 2019 04:40:09 AM UTC
      &#9500;&#9472; policy:     auto
      &#9492;&#9472; key:        no

 &#9679; Lenovo ThinkPad Thunderbolt 3 Dock #2
   &#9500;&#9472; type:          peripheral
   &#9500;&#9472; name:          ThinkPad Thunderbolt 3 Dock
   &#9500;&#9472; vendor:        Lenovo
   &#9500;&#9472; uuid:          004148d5-c451-0801-ffff-ffffffffffff
   &#9500;&#9472; status:        authorized
   &#9474;  &#9500;&#9472; domain:     domain0
   &#9474;  &#9492;&#9472; authflags:  boot
   &#9500;&#9472; authorized:    Sat 21 Dec 2019 06:36:09 PM UTC
   &#9500;&#9472; connected:     Sat 21 Dec 2019 06:36:09 PM UTC
   &#9492;&#9472; stored:        Sat 21 Dec 2019 04:22:36 PM UTC
      &#9500;&#9472; policy:     auto
      &#9492;&#9472; key:        no
```

Now, I must explain. I actually have two of these docks. When I first started having problems I called Lenovo and they sent me out a replacement 65w power cable. When that didn't solve anything I called again, and this time they sent me out a new dock. I really owe them a return of the second dock and power cable, since I now realize that the problem is software on Ubuntu, not hardware. 

And re bolt, the web page for bolt ([URL=https://gitlab.freedesktop.org/bolt/bolt[/URL]) says that it allows the user to configure Thunderbolt devices, so apparently there are more options than I have discovered so far. [Side note: Why do coders never seem to realize that when the code is done their job is only half finished?]

---

### Post by oldfred on 2019-12-21
It looks like Lenovo is finally allowing UEFI updated from Linux.
[https://fwupd.org/lvfs/devices/](https://fwupd.org/lvfs/devices/)
Shows T490 added 17 days ago.

The Dell user were able to update:
#Does this show your system & dock?
       sudo fwupdmgr get-devices
#then you should be able to update:
sudo fwupdmgr get-updates

---

### Post by John Jason Jordan on 2019-12-21
> **oldfred said:**
> The Dell user were able to update:
#Does this show your system & dock?
       sudo fwupdmgr get-devices
#then you should be able to update:
sudo fwupdmgr get-updates

Both commands executed without error. First I got this:

```
sudo fwupdmgr get-devices
P73 Thunderbolt Controller
  DeviceId:             fab64704f1db074867e4d59c677d103353bc570b
  Guid:                 ff8f129c-a63b-57b3-acf9-f701cc9dcb06
  Summary:              Unmatched performance for high-speed I/O
  Plugin:               thunderbolt
  Flags:                internal|updatable|registered
  Vendor:               Lenovo
  VendorId:             TBT:0x0109
  Version:              43.00
  Icon:                 computer
  Created:              2019-12-21

ThinkPad Thunderbolt 3 Dock
  DeviceId:             fc7b0c1813cde22de2e6ec51e3a925a2ca8462ce
  Guid:                 75039175-c354-5df9-a798-5da41461c007
  Plugin:               thunderbolt
  Flags:                updatable|registered
  Vendor:               Lenovo
  VendorId:             TBT:0x0108
  Version:              39.00
  Icon:                 audio-card
  Created:              2019-12-21
```

And then the get-updates command executed with no messages. I don't know if it did anything or not.

When I got up this morning the computer was dead and not connected. I rebooted it and it remained disconnected from the dock. When the battery got down to 40% or so I pulled the connector out of the computer and then plugged it back in. Suddenly everything reconnected. But then a few hours later the USB port connected to a large external drive stopped working. I unplugged it and then plugged it back in again and the drive reconnected. This is ridiculous. Things need to stay connected.

I also discovered a couple more tidbits about bolt. 'boltctl list' gives you the same list as I posted above, and then 'boltctl authorize <UUID>' (using the UUID from the list command) will authorize the dock. I don't know if that actually did anything, since they were already authorized before.

---

### Post by oldfred on 2019-12-21
Reading this you may need one more command?man fwupdmgr 

Try this also
sudo        fwupdmgr update

There also seem to be UEFI settings, may vary somewhat by vendor:
[https://ubuntuforums.org/showthread.php?t=2431141&page=2](https://ubuntuforums.org/showthread.php?t=2431141&page=2)

---

### Post by John Jason Jordan on 2019-12-22
> **oldfred said:**
> Reading this you may need one more command?man fwupdmgr 
Try this also
sudo        fwupdmgr update
There also seem to be UEFI settings, may vary somewhat by vendor:
[https://ubuntuforums.org/showthread.php?t=2431141&page=2](https://ubuntuforums.org/showthread.php?t=2431141&page=2)

I hate to say this out loud, but it has now been 24 hours and no problems at all. Just now I rebooted and it all came back with everything working. Of course, now that I've said that something will probably break. :( I'm hesitant to say 'solved' just yet, because this dock can be working and then suddenly something loses its connection.

And another problem is that, even if it really is now permanently fixed, I don't know which of the various commands that I have used is the one that really did the job. For future people who may be afflicted with Thunderbolt 3 dock issues, just install bolt (sudo apt install bolt), then do 'boltctl list,' 'boltctl authorize <UUID>,' and oldfred's fwupdmgr commands. And before you start go into the BIOS and turn off security for Thunderbolt 3.

---

