---
title: "ASUS EB1037 - nvidia 820m - VBios issue - optimus"
date: 2014-07-14
forum: Hardware
---

### Post by anthonythomas on 2014-07-14
Hello,

I've bought an ASUS EeeBox EB1037 thinking it would make a great HTPC.

After trying to install ubuntu I've discovered it is an nvidia optimus based system.

I've tried loads of different ways to get things working but I think the main issue comes down to ubuntu not being able to access the VBios.

When trying to boot from a LiveCD I have to add "nouveau.modeset=0" to the Linux grub command. That then boots fine. If I don't do that and remove the quiet splash part it hangs at the VBios section.

To be able to boot all the time nouveau has to be blacklisted.

[The hang looks like this with the Bios error:]("https://dl.dropboxusercontent.com/u/14641356/ubuntu/eb1037-vbios.jpg")

This is also true when using bumblebee

I get the following error with bumblebee.

```
[COLOR=#000000][FONT=monospace]kernel: [ 2103.239018] vgaarb: this pci device is not a vga device[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]kernel: [ 2103.240424] nvidia 0000:01:00.0: irq 113 for MSI/MSI-X[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]kernel: [ 2103.247963] NVRM: failed to copy vbios to system memory.[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]kernel: [ 2103.249699] NVRM: RmInitAdapter failed! (0x30:0xffffffff:714)[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]kernel: [ 2103.249714] NVRM: rm_init_adapter failed for device bearing minor number 0[/FONT][/COLOR]
```

Any ideas how to get past this step so I can somehow try and get the nvidia graphics working?

Edit: I should add that I am using ubuntu 14.04. The things I had tried were various nvidia drivers (319, 331, 337) with and without bumblebee. prime-switch and bbswitch fail and the issues all seem to be around the vbios problem.

---

### Post by karimakela on 2014-07-14
I am trying the same - but can't help much.

I tried 14.04 64 bit server, and 14.04 64 bit desktop. Both did hang in early phase of USB boot, just gray screen and nothing else. Then I noticed that in BIOS (or exactly speaking, not in BIOS but UEFI) has options to define which operating system is used, and ACPI options. I changed operating system to Android (instead of Win7 or Win8), and changed the ACPI to "PCI" if I recall right, without understanding what I did. After that I tried to install old version, 12.04.3 32 bit desktop, and it seems to be OK, just done and boots and looks normal (except that initially it shows ugly black-white striped display)

But I do not like the idea of starting with something old, and it also does not recognize the WLAN chip.

Did you have to modify the UEFI options, or did you get it up with just that GRUB parameter?

I did not yet have time to try 14.04 after the two ACPI modifications were done, will try tomorrow.

---

### Post by anthonythomas on 2014-07-14
I can get ubuntu 14.04 to install fine in EFI mode.

You need to add "nouveau.modeset=0" to the grub linux command for the LiveCD and then also on first boot or it will hang. If you remove "quiet splash" you'll see exactly where it hangs. That should get you to the desktop. Once you're there add "blacklist nouveau" to /etc/modprobe.d/blacklist.conf and ubuntu should boot fine.

Then you can try to install nvidia drivers....!

I've read around that there's some patches for similar issues where the vbios isn't copied which is down to an ACPI/EFI/CSM issue.

I also changed a few things to PCI mode and back. Tried various combinations in various menus in the EFI to set it to Win7, Win8, Android, Other OS. Can't seem to find the right settings to get the vbios to copy.

---

### Post by karimakela on 2014-07-15
OK, and thanks for the advice. Now I am in the same situation. I resetted all UEFI settings to default (except temp boot device), and got the same hang if I did not disable nouveau, and got it up by disabling it.

This is partially good for me, because I was planning to buy one more of these boxes, so that the first one will be used only as a web server and SSH hopper (no windows, just text), and the other then with graphical interface. Thus, this would be OK for the server. It is small, very silent and does not get  warm at all.

And it might even be OK for the other use without the nvidia, because the other one is a "kitchen laptop" used by all the family for simple and mundane things like checking public transportation timetables, reading news(papers), weather, recipes, and all such stuff which seems to work OK also without nvidia - even if it is a bit stupid.

---

### Post by anthonythomas on 2014-07-16
I've given up for the time being and stuck OpenElec on and I'll just use the Intel graphics until I get the nvidia working.

Pretty sure it's an nvidia driver issue but my post on the nvidia forum is coming up as "hidden" which is irritating.

---

### Post by jicha on 2014-10-14
Hi, I am thinking about getting this PC. I want to have a HTPC with Ubuntu/XBMC attached to my TV. This one looks very good and is cheap. Have you found any solution for the nVidia graphics card problems? If I don't plan to use it to play 3D games, can I live with the integrated graphics?

I found this article, which might be useful: [http://xmodulo.com/install-configure-nvidia-optimus-driver-ubuntu.html](http://xmodulo.com/install-configure-nvidia-optimus-driver-ubuntu.html)

Or would you suggest a different HTPC? If it had a DVD drive, it would be ideal. But it must be slim (less then 3").

---

### Post by ekx27 on 2014-10-27
Have anyone tried to modify some options into the BIOS ?

There is a 0606 version available here : [http://www.asus.com/EeeBox_PCs/EB1037/HelpDesk_Download/]("http://www.asus.com/EeeBox_PCs/EB1037/HelpDesk_Download/")

I an not very familiar with those CSM settings in the BIOS, anyone does ?

---

### Post by ekx27 on 2014-10-28
On this webpage [http://us.download.nvidia.com/XFree86/Linux-x86/304.43/README/commonproblems.html]("http://us.download.nvidia.com/XFree86/Linux-x86/304.43/README/commonproblems.html") I get the following details:

> 
Why does the VBIOS fail to load on my Optimus system?
	

On some notebooks with Optimus graphics, the NVIDIA driver may not be able to retrieve the Video BIOS due to interactions between the System BIOS and the Linux kernel's ACPI subsystem. On affected notebooks, applications that require the GPU will fail, and messages like the following may appear in the system log:

NVRM: failed to copy vbios to system memory.
NVRM: RmInitAdapter failed! (0x30:0xffffffff:858)
NVRM: rm_init_adapter(0) failed

Such problems are typically beyond the control of the NVIDIA driver, which relies on proper cooperation of ACPI and the System BIOS to retrieve important information about the GPU, including the Video BIOS.

The issue seems to be the ACPI, does anyone knows any settings to change into the BIOS ?

---

### Post by josef7 on 2014-11-05
Hi I'm also a proud owner of a EB1037. 


I current running with the nvida disabled only using the intel grapichs.

Still i have issues with the system freezing from time to time.
I runned dmesg and could see that there is alot of error messages related to ACPI. So I have set the acpi=off in grub and now my system seems to be stable. 

Seems to be a way to move forward for this issue, following this steps 
[https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI) 

I have not got further than the apci=off step, i will keep it for a while to be 100% sure.

Is there anyone that is ahead of me tracking this down?

---

### Post by ekx27 on 2014-11-05
Which version of Ubuntu do you use ?

On Xubuntu 14.10 I have no ACPI issues, even for running the LiveCD...

---

### Post by josef7 on 2014-11-09
I'm current running on Ubuntu 14.04. Perhaps I should dare to upgrade to 14.10 then.
 Is your system stable no other issues than the nvidia Graphics?

---

### Post by josef7 on 2014-11-10
Upgraded to Ubuntu 14.10 and enabled acpi, still get some ACPI Errors during boot.
Don't know if it is related to nvidia issue. Don't know if system is stable yet (need to run it for a while). 

[   19.101968] asus_wmi: ASUS WMI generic driver loaded
[   19.119122] asus_wmi: Initialization: 0x0
[   19.119183] asus_wmi: BIOS WMI version: 0.9
[   19.119296] asus_wmi: SFUN value: 0x0
[   19.120867] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input7
[   19.124737] ACPI Error: No handler for Region [ECRM] (ffff88015b0262d0) [EmbeddedControl] (20140424/evregion-163)
[   19.124747] ACPI Error: Region EmbeddedControl (ID=3) has no handler (20140424/exfldio-299)
[   19.124755] ACPI Error: Method parse/execution failed [\OWLS] (Node ffff88015b02a348), AE_NOT_EXIST (20140424/psparse-536)
[   19.124765] ACPI Error: Method parse/execution failed [\AMW0.DEVS] (Node ffff88015b029d70), AE_NOT_EXIST (20140424/psparse-536)
[   19.124776] ACPI Error: Method parse/execution failed [\AMW0.WMBC] (Node ffff88015b029af0), AE_NOT_EXIST (20140424/psparse-536)
[   19.125590] ACPI Error: No handler for Region [ECRM] (ffff88015b0262d0) [EmbeddedControl] (20140424/evregion-163)
[   19.125601] ACPI Error: Region EmbeddedControl (ID=3) has no handler (20140424/exfldio-299)
[   19.125608] ACPI Error: Method parse/execution failed [\OBTS] (Node ffff88015b02a398), AE_NOT_EXIST (20140424/psparse-536)
[   19.125619] ACPI Error: Method parse/execution failed [\AMW0.DEVS] (Node ffff88015b029d70), AE_NOT_EXIST (20140424/psparse-536)
[   19.125630] ACPI Error: Method parse/execution failed [\AMW0.WMBC] (Node ffff88015b029af0), AE_NOT_EXIST (20140424/psparse-536)
[   19.126574] asus_wmi: Backlight controlled by ACPI video driver
[   19.369041] cfg80211: World regulatory domain updated:
[   19.369048] cfg80211:  DFS Master region: unset

---

### Post by ekx27 on 2014-11-12
Don't know ether, all I know is that everything works fine except the Nvidia card on version 14.10...

---

### Post by ekx27 on 2014-12-30
My Asus EB1037 with Ubuntu 14.10 is now crashing from time to time...

The problem comes from xorg but the whole system is crashing, I have to remove the power cord to shutdown the computer...
According to dmesg it seems to come from ACPI...

The BIOS version is 0606, the latest : [http://www.asus.com/Commercial_Desktops/EB1037/HelpDesk_Download/]("http://www.asus.com/Commercial_Desktops/EB1037/HelpDesk_Download/")

By the way, did anyone tried to install Ubuntu in secure mode (UEFI)?

---

### Post by josef7 on 2015-01-16
Hi,

I also got crashes after upgrading kernel for 14.10 about 3-4 week ago.  
I disabled acpi (acpi=off) in grub and then system was stable again.

I saw that there is a new bios from Asus 0601 don't really understand their version strategy since the last before was 0606. But perhaps i would be interesting to test it out.

Have not tested secure mode.

---

### Post by ekx27 on 2015-01-16
Hi,

Thank you for the BIOS update, I will test it tomorrow, hope this change something about the NVidia issue...

---

### Post by ekx27 on 2015-03-02
I found an solution about crash on EB1037, it is related to CPU Power Technology : disable it into the BIOS.

After that there is no need to disable ACPI anymore... :)

[IMG]http://reho.st/self/7d850bcabcfa5fc3d42dd73c094396136a2c29a2.png[/IMG]

---

### Post by ekx27 on 2015-06-01
New BIOS Update from Asus : version 1103

[http://dlcdnet.asus.com/pub/ASUS/DigitalHome/DAV/EB1037/EB1037-ASUS-1103.zip]("http://dlcdnet.asus.com/pub/ASUS/DigitalHome/DAV/EB1037/EB1037-ASUS-1103.zip")

---

### Post by ekx27 on 2016-03-28
The only way to get stability with Ubuntu and this crap of ASUS EB1037 was to add the following options in the grub :

acpi=off pnpbios=off

---

