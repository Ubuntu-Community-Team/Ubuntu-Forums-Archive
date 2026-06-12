---
title: "Matrox DualHead2Go (and possibly TripleHead2Go) + nVidia -&gt; The SECRET to make it wrk"
date: 2011-04-30
forum: Hardware
---

### Post by Cyclops_ on 2011-04-30
OK.... I have just spent several hours trying to get the Matrox DualHead2Go to work with Ubuntu.  I changed the xorg.conf settings, I used the nvidia-settings tool, I did some xrandr stuff....  But after several attempts, and a very very late night, I FINALLY got it.

Here's what I was coming up against:  no matter what I did, the correct mode would never show up in the options in Nvidia-settings.  Ugh!

So...  after search upon search, I came across something that sparked a chain of things.  Hopefully, this may help someone out there.

I found out that there was updated firmware for the DH2G.  Now, this by itself wasn't the fix, but I'll bet it helped.  The first thing I did was to reboot into Windows 7, download the firmware (and software) updates, installed them (after doing the recommended backup).

After that, I rebooted back into Ubuntu.  Still no luck, but another mode showed up that wasn't there previously.

Finally, in a last ditch effort, I went back into Windows, and ran the PowerDesk (is that the right word?) utility.  There was a gxm setup which I also ran.  The trick here was to A) get it working right in Windows and B) ensuring that the software had added the correct mode(s) to the device.  (in my case, 1920x1080, as I already had 1920x1200 working at home).  Apparently the Windows software acts as a sort of manager for the settings on the actual device - not just as Operating System settings manager.

Reboot into Linux, pull up nvidia-settings (with sudo), apply the correct mode and save settings.

Done.  Go to bed!

I really really hope this helps someone else.  I tore my hair out (well, OK, I'm already losing that naturally)...   over this one.

Good luck!

Oh, PS... I also updated the nvidia drivers by installing the nvidia drivers from the nvidia site.  YMMV here, and it was just a step along the way.  Don't know if it was a factor, but I think the Windows app setting bit was the real key here.

---

### Post by avilella on 2011-08-02
Hi Cyclops_,

This is definitely useful for me, since I am trying to do the same on my laptop. The problem is, I've got no Windows 7 on this laptop, but for what you tell, it's only a matter of configuring it as you would like it to be for the monitors, then using that configuration with the Ubuntu laptop.

In my case, I've got an nvidia (actually hybrid graphics) laptop with Ubuntu 11.04 and would like to have 2 x 1920x1200 monitors attached to the Matrox DualHead2Go.

How can I find out if the firmware is already up-to-date on the DH2G? Can I find out in Linux or do I need to borrow a Windows/Mac computer for that?

> **Cyclops_ said:**
> OK.... I have just spent several hours trying to get the Matrox DualHead2Go to work with Ubuntu.  I changed the xorg.conf settings, I used the nvidia-settings tool, I did some xrandr stuff....  But after several attempts, and a very very late night, I FINALLY got it.

Here's what I was coming up against:  no matter what I did, the correct mode would never show up in the options in Nvidia-settings.  Ugh!

So...  after search upon search, I came across something that sparked a chain of things.  Hopefully, this may help someone out there.

I found out that there was updated firmware for the DH2G.  Now, this by itself wasn't the fix, but I'll bet it helped.  The first thing I did was to reboot into Windows 7, download the firmware (and software) updates, installed them (after doing the recommended backup).

After that, I rebooted back into Ubuntu.  Still no luck, but another mode showed up that wasn't there previously.

Finally, in a last ditch effort, I went back into Windows, and ran the PowerDesk (is that the right word?) utility.  There was a gxm setup which I also ran.  The trick here was to A) get it working right in Windows and B) ensuring that the software had added the correct mode(s) to the device.  (in my case, 1920x1080, as I already had 1920x1200 working at home).  Apparently the Windows software acts as a sort of manager for the settings on the actual device - not just as Operating System settings manager.

Reboot into Linux, pull up nvidia-settings (with sudo), apply the correct mode and save settings.

Done.  Go to bed!

I really really hope this helps someone else.  I tore my hair out (well, OK, I'm already losing that naturally)...   over this one.

Good luck!

Oh, PS... I also updated the nvidia drivers by installing the nvidia drivers from the nvidia site.  YMMV here, and it was just a step along the way.  Don't know if it was a factor, but I think the Windows app setting bit was the real key here.

---

### Post by Cyclops_ on 2012-04-21
Oh my.  Sorry I'm so late to the party... but yes, you need to use a Windows computer to get the Matrox set up.  It has some kind of special firmware settings that need to be set within a Windows environment.

Hope that still helps.

---

### Post by Bashar &quot; on 2012-06-20
Hello,
if i dont have nvidia card would it work for split screens on the matrox dualhead2go ?

I have Lenovo S10 and i'm not exactly sure which vga card it has, but dmesg shows something like an OEM?
[    0.277865] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.277898] vgaarb: loaded
[    0.277904] vgaarb: bridge control possible 0000:00:02.0


[   13.017963] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   13.045733] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[   13.049712] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   13.477767] input: Ideapad extra buttons as /devices/platform/ideapad/input/input6
[   13.570928] type=1400 audit(1340193262.780:2): apparmor="STATUS" operation="profile_load" name="/sbin/d
hclient" pid=517 comm="apparmor_parser"
[   13.572646] type=1400 audit(1340193262.784:3): apparmor="STATUS" operation="profile_load" name="/usr/li
b/NetworkManager/nm-dhcp-client.action" pid=517 comm="apparmor_parser"
[   13.573535] type=1400 audit(1340193262.784:4): apparmor="STATUS" operation="profile_load" name="/usr/li
b/connman/scripts/dhclient-script" pid=517 comm="apparmor_parser"

---

### Post by Cyclops_ on 2012-06-20
> **Bashar " said:**
> Hello,
if i dont have nvidia card would it work for split screens on the matrox dualhead2go ?


Bashar, I'm not sure.  Sorry :(   My guess is just that you need something that will output the correct resolution and a software or method that will allow you to configure it.

Wish I could be of more help.

---

### Post by WebDawg on 2012-07-04
I have debian and an intel graphics card and I did the same things that OP was talking about.

I connected the device to a windows box.  I updated my firmware.  Checked the modes.  (I did not have to add one.)  Configured the device to be the resolution I wanted it to be on the nix box.  I did not have to add or del a mode.

The big thing that I had to make sure to do to get the device to work was to match the refresh rate on the nix box.  If I did not the dualhead did not work right.

So 2048x768 @ 60hz and not @ 80hz

Web...

---

### Post by chagam on 2012-12-09
Hi,

@WebDawg, please, can you give some more informations on how to set the frequency

Thanks

Chag

---

