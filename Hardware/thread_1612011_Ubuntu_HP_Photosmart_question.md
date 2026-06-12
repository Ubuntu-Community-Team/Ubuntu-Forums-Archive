---
title: "Ubuntu HP Photosmart question"
date: 2010-11-02
forum: Hardware
---

### Post by benwiddowson on 2010-11-02
Hi guys

I'm a bit of an Linux noob having only made the switch from Windows a few weeks back. So far im happy with my choice but one issue is driving me nutts. I have a Hp Photosmart C4780 printer (wireless). Ive successfully installed the printer onto my ubuntu laptop and printed a few documents. After i rebooted everything changed. If i click print it will just sit in the queue for several minutes then click up an error. If i delete the printer and reinstall it all is fine with printing/scanning until i again reboot and were back at square one. The printer is connected by Wifi due to it being located upstairs. The printer itself isn't connected to my router via cable but via wifi again. I'm going to try to connect it via ethernet to the router to see if that changes anything.

In the meantime has anyone got any other ideas?

Ben

---

### Post by benwiddowson on 2010-11-02
i would if there was an Ethernet port on the printer

---

### Post by nemarona on 2010-11-29
I'm having the same problem with my HP Photosmart C4780. I've tried everything I could think of, without success:

1. Turning the printer off and on again.
2. Uninstalling and installing again.
3. Uninstalling and installing again via hp-setup.
4. Switching back to the old Linux kernel.

Every one of these solutions brings the printer back to normal for some time; it typically prints fine once or twice, or until the next reboot, and then it just dies.

Any ideas?

---

### Post by pricetech on 2010-11-29
Will your router let you reserve IP addresses for certain MACs ??  If so, reserve an IP for your printer and your laptop.

See if that helps.

---

### Post by nemarona on 2010-11-29
Thanks for the reply. I don't think my router lets me do what you suggest; I just checked [http://192.168.1.1/](http://192.168.1.1/) and the only things I can configure are the ESSID, the encryption type (WEP, WPA, etc.) and the password.

---

### Post by pricetech on 2010-11-30
Is the IP of the printer fixed or DHCP ??  A fixed IP might help.

---

### Post by Manyette on 2010-11-30
I also had immense troubles connecting an HP printer via WiFi. All the tech help from HP was to no avail.  I finally tried to make all the settings on the printer itself, instead of using the software to do it.  If you make the settings you need for wifi by using the built in tools on the printer menu, it seems to find things that the normal software does not cover.  On my J6480, from the font panel chose Tools, and then WiFi.  It worked for me, when all else failed.

---

### Post by nemarona on 2010-11-30
The printer IP is static, not DHCP.

What bothers me most about this is that the printer worked perfectly for a couple of weeks, until for no aparent reason (I'm guessing a Linux kernel update here) it started giving me trouble.

Just realized I also can't scan.

---

### Post by Manyette on 2010-11-30
Yes, I also assigned a static IP from my router.  I also assigned a WPA2 security key.  All done from the printer. I have assigned a static IP for all three machines and the printer in the linksys router. Again, this worked when nothing else I or HP could suggest would work.

---

### Post by deanjm1963 on 2010-11-30
The only way I could get a photosmart printer to print or scan via wireless was to add it's ip address to my router, then I had to install hplip-gui, connect the printer temporarily to my machine with a usb cable, run hplip-setup as root (gksudo hplip-setup), follow the instructions. It worked ok, but then I decided to give the whole wireless thing away, way too much hassle just to print and scan.

---

### Post by aeronutt on 2010-11-30
FYI, I use the hplip-gui to successfully (and via wireless) setup my HP 6480 officejet printer for the last few versions of Ubuntu. Print and scan work.

---

### Post by Hotwheelz79 on 2010-12-01
Hi, 

Anyone know if this printer works OTB in 10.10

[http://h10010.www1.hp.com/wwpc/au/en/ho/WF05a/18972-18972-238444-410635-410635-4073314.html#null](http://h10010.www1.hp.com/wwpc/au/en/ho/WF05a/18972-18972-238444-410635-410635-4073314.html#null)

Thanks.

:-)

---

### Post by 1childish1 on 2011-12-30
Hey,

I've been having the same issues with my C4780 printer too. The odd things is that I fixed it once and now I can't, but maybe it will help you. What I did was plugged my printer via USB and then in the terminal I put the following:

```
hp-setup -i 192.168.1.69
```with "192.168.1.69" as my printer's static IP in my router. It apparently detected it very quickly and didn't even ask me what kind of connection I wanted (USB or net), but now all it gives me is

```
error: Invalid device URI: 
error: No device selected/specified or that supports this functionality.
```I didn't even do anything to it, but just today it showed the same old communication error (5012) and it didn't let me use my wireless printing.

If anyone has an answer to this, would really appreciate it!! And I'm running 11.10 with Windows 7 dualboot (don't think that has anything to do with this problem).

---

### Post by 1childish1 on 2011-12-30
OK, I don't know what just happened, but I got it fixed (again). So, after many attempts, all I did was remove all the printers and run the command I had mentioned above but with root privilidges:
```

hp-setup -r
sudo hp-setup -i 192.168.1.69
``` (my printer's IP is still being the same) It did the exact same thing as the first time I fixed it (which was skip asking and go directly to installing). I then restarted my computer, the printer and the router all together (because it still gave me "Communication Error 5012") and viola! It works! Printing, and scanning!

Basically, the way I knew I fixed it was that after running the "-i" command, it SHOULD NOT ask to choose between USB and net, and just install directly. I'm just hoping this stays put and doesn't mess up later. And I also hope this helps anyone!

=P

---

