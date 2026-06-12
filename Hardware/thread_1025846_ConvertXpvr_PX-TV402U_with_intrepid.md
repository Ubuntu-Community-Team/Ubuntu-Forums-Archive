---
title: "ConvertXpvr PX-TV402U with intrepid"
date: 2008-12-30
forum: Hardware
---

### Post by Warll on 2008-12-30
Hello this is my first post and as such I hope I got this into the right section. I am trying to set up a server for my church, we've had some nasty cases of vandalism and as such set up some security cameras. The server was originally set up with Gentoo and a PX-TV402U, the password was lost sadly and now I'm trying to redo it with Ubuntu. So far I have gotten just about everything I want set up, VNC, the network share, except the all important PVR. I have not had much success, any guides I have found are too old to include help for Intrepid. 
The best guide I have tried so far would likely have to be this one: [http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver#Ubuntu_usbfs_fix](http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver#Ubuntu_usbfs_fix) 
I seam to be stuck with usbfs fix, when I run the fix command I get: "sudo: patch: command not found"
I have also tried to just install MythTv in the hopes that would do everything, although I really would like to run a smaller program if possible. I had installed the "MythTV frontend" from the repository, when I run it though it asks for some MySQL configuration. 
Anyway I hope I'v given enough information for some kind soul to help me, if anymore information is needed please tell me, I really would like to use linux for this although if push comes to shove I may jut have to use Windows 2003.

---

### Post by Rohan Kapoor on 2008-12-30
> **Warll said:**
> Hello this is my first post and as such I hope I got this into the right section. I am trying to set up a server for my church, we've had some nasty cases of vandalism and as such set up some security cameras. The server was originally set up with Gentoo and a PX-TV402U, the password was lost sadly and now I'm trying to redo it with Ubuntu. So far I have gotten just about everything I want set up, VNC, the network share, except the all important PVR. I have not had much success, any guides I have found are too old to include help for Intrepid. 
The best guide I have tried so far would likely have to be this one: [http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver#Ubuntu_usbfs_fix](http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver#Ubuntu_usbfs_fix) 
I seam to be stuck with usbfs fix, when I run the fix command I get: "sudo: patch: command not found"
I have also tried to just install MythTv in the hopes that would do everything, although I really would like to run a smaller program if possible. I had installed the "MythTV frontend" from the repository, when I run it though it asks for some MySQL configuration. 
Anyway I hope I'v given enough information for some kind soul to help me, if anymore information is needed please tell me, I really would like to use linux for this although if push comes to shove I may jut have to use Windows 2003.
If you're trying to install something to interface with your cameras try this amazing software called zoneminder: [www.zoneminder.com](www.zoneminder.com)

---

### Post by Warll on 2008-12-30
Thank you for your reply I will look into using it, I will need to check what type of cameras we have though. All I know is that the camera's feeds came into the electrical room over coxal.

---

### Post by Rohan Kapoor on 2008-12-30
> **Warll said:**
> Thank you for your reply I will look into using it, I will need to check what type of cameras we have though. All I know is that the camera's feeds came into the electrical room over coxal.
Ok, so your cameras are coming in using a coaxial video input. If I'm understanding you correctly, what you want to do is set up MythTv so that it records all of the channels coming in over the Coaxial input. Am I correct so far?

Your problem with MythTV is that you need a backend to record the inputs.

Try this guide (for 8.04, should work fine with 8.10)

[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

---

### Post by Warll on 2008-12-30
Alright this does look like a promsing path of pursuit. Found this page* which says that it should work, i'll try the guide to install MythTV now. 

*:[http://www.mythtv.org/wiki/index.php/Plextor_PX-TV402U](http://www.mythtv.org/wiki/index.php/Plextor_PX-TV402U)

---

### Post by Rohan Kapoor on 2008-12-30
> **Warll said:**
> Alright this does look like a promsing path of pursuit. Found this page* which says that it should work, i'll try the guide to install MythTV now. 

*:[http://www.mythtv.org/wiki/index.php/Plextor_PX-TV402U](http://www.mythtv.org/wiki/index.php/Plextor_PX-TV402U)
Allright, let us know how it goes!

---

### Post by Warll on 2009-01-01
Ok so I have been trying to get MythTv, not going all that well. First thing I had done was install useing the "MythTV frontend" from the repository, when it first asked me to set up the MythTV user I had spezified a password, then once it tried to configure the DB it comes up with "cannot login to database". After some quite diging it apears as if this had to do with my setting a password. I've taken the steps outlined in this* post just when I try to sudo rm ~/.mythtv -rf && rm /home/mythtv/.mythtv -rf I get an "permision denied. When I try the first command of the second step, sudo dpkg-reconfigure mythtv-database, I get: ```
user@lcotgs-ubuntu-server:~$ sudo dpkg-reconfigure mythtv-database
 * Starting MySQL database server mysqld                                    [ OK ] 
Failed to connect to database: Access denied for user 'root'@'localhost' (using password: NO) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
It's also possible that mysql-server wasn't running.  After install
is completed, you will need to make sure mysql-server is running
and that you supplied correct information. Try:
sudo dpkg-reconfigure mythtv-database
user@lcotgs-ubuntu-server:~$
```
When I try the second command, sudo dpkg-reconfigure mythtv-common, I get this: ```
user@lcotgs-ubuntu-server:~$ sudo dpkg-reconfigure mythtv-common
[sudo] password for user: 
mv: cannot move `/tmp/mysql.txt-Ng6480' to `/etc/mythtv/mysql.txt': No such file or directory
user@lcotgs-ubuntu-server:~$ 

```
The MythTV set up still fails.

---

### Post by Rohan Kapoor on 2009-01-01
> **Warll said:**
> Ok so I have been trying to get MythTv, not going all that well. First thing I had done was install useing the "MythTV frontend" from the repository, when it first asked me to set up the MythTV user I had spezified a password, then once it tried to configure the DB it comes up with "cannot login to database". After some quite diging it apears as if this had to do with my setting a password. I've taken the steps outlined in this* post just when I try to sudo rm ~/.mythtv -rf && rm /home/mythtv/.mythtv -rf I get an "permision denied. When I try the first command of the second step, sudo dpkg-reconfigure mythtv-database, I get: ```
user@lcotgs-ubuntu-server:~$ sudo dpkg-reconfigure mythtv-database
 * Starting MySQL database server mysqld                                    [ OK ] 
Failed to connect to database: Access denied for user 'root'@'localhost' (using password: NO) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
It's also possible that mysql-server wasn't running.  After install
is completed, you will need to make sure mysql-server is running
and that you supplied correct information. Try:
sudo dpkg-reconfigure mythtv-database
user@lcotgs-ubuntu-server:~$
```
When I try the second command, sudo dpkg-reconfigure mythtv-common, I get this: ```
user@lcotgs-ubuntu-server:~$ sudo dpkg-reconfigure mythtv-common
[sudo] password for user: 
mv: cannot move `/tmp/mysql.txt-Ng6480' to `/etc/mythtv/mysql.txt': No such file or directory
user@lcotgs-ubuntu-server:~$ 

```
The MythTV set up still fails.
Right, I'm no expert with MythTV, not currently running it at all. However what I have to tell you is that before you install the frontend.......

You have to install a backend. That can be on another computer or this one.


Let me try to explain the differences between a frontend and backend:

Frontend: Located where the user would watch stuff, eg. TV. It only connects to the backend and allows you to watch stuff streaming to the backend (camera feeds).

Backend: Located anywhere, potentially even same computer as the frontend. It digitizes the camera feeds (coaxial) and sends them to any frontend watching!

Honestly because I'm not running Myth right now, that's the best I can offer you! I'm still monitoring the thread and will pop in as I can. Sorry!

---

### Post by Rohan Kapoor on 2009-01-01
> **Warll said:**
> Ok so I have been trying to get MythTv, not going all that well. First thing I had done was install useing the "MythTV frontend" from the repository, when it first asked me to set up the MythTV user I had spezified a password, then once it tried to configure the DB it comes up with "cannot login to database". After some quite diging it apears as if this had to do with my setting a password. I've taken the steps outlined in this* post just when I try to sudo rm ~/.mythtv -rf && rm /home/mythtv/.mythtv -rf I get an "permision denied. When I try the first command of the second step, sudo dpkg-reconfigure mythtv-database, I get: ```
user@lcotgs-ubuntu-server:~$ sudo dpkg-reconfigure mythtv-database
 * Starting MySQL database server mysqld                                    [ OK ] 
Failed to connect to database: Access denied for user 'root'@'localhost' (using password: NO) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
It's also possible that mysql-server wasn't running.  After install
is completed, you will need to make sure mysql-server is running
and that you supplied correct information. Try:
sudo dpkg-reconfigure mythtv-database
user@lcotgs-ubuntu-server:~$
```
When I try the second command, sudo dpkg-reconfigure mythtv-common, I get this: ```
user@lcotgs-ubuntu-server:~$ sudo dpkg-reconfigure mythtv-common
[sudo] password for user: 
mv: cannot move `/tmp/mysql.txt-Ng6480' to `/etc/mythtv/mysql.txt': No such file or directory
user@lcotgs-ubuntu-server:~$ 

```
The MythTV set up still fails.
Right, I'm no expert with MythTV, not currently running it at all. However what I have to tell you is that before you install the frontend.......

You have to install a backend. That can be on another computer or this one.


Let me try to explain the differences between a frontend and backend:

Frontend: Located where the user would watch stuff, eg. TV. It only connects to the backend and allows you to watch stuff streaming to the backend (camera feeds).

Backend: Located anywhere, potentially even same computer as the frontend. It digitizes the camera feeds (coaxial) and sends them to any frontend watching!

Honestly because I'm not running Myth right now, that's the best I can offer you! I'm still monitoring the thread and will pop in as I can. Sorry!

---

### Post by Warll on 2009-01-03
Alright just a quick update, I had given up on interpid and mythtv. When I saw about using a clean Mythbuntu install I first tried it out with the livecd, even with the live cdit had the "cannot connect to DB" error. So think it to be the easy way out I just installed Windows 2003, the thing didn't even have drivers for the ethernet, so insed of fighting to get drivers for some unknown device I'm going to see about using gentoo with the px-tv402u. Or maybe I will take mythbuntu for a spin.
Edit: Ok installed Mythbuntu looks like its going to be all ok. Need to sleep now.

---

### Post by Rohan Kapoor on 2009-01-03
> **Warll said:**
> Alright just a quick update, I had given up on interpid and mythtv. When I saw about using a clean Mythbuntu install I first tried it out with the livecd, even with the live cdit had the "cannot connect to DB" error. So think it to be the easy way out I just installed Windows 2003, the thing didn't even have drivers for the ethernet, so insed of fighting to get drivers for some unknown device I'm going to see about using gentoo with the px-tv402u. Or maybe I will take mythbuntu for a spin.
Edit: Ok installed Mythbuntu looks like its going to be all ok. Need to sleep now.
OK, glad to see that you got Mythbuntu working. Sleeping is a good idea!

---

### Post by Warll on 2009-01-03
Alright so mythbuntu wasn't the easy way, tried Fedora 9, got a headache tring ot set up vnc. Installed Ubuntu 8.04 and I am a lot closer I have the drivers compiled, I think, the only problem now is that it won't detect the device. I seem to have found when its going wrong heres the dmesg, notice the tainted kernel part.
```
[  549.109449] usb 5-1: USB disconnect, address 2
[  550.859987] usb 5-1: new high speed USB device using ehci_hcd and address 4
[  550.992467] usb 5-1: configuration #1 chosen from 1 choice
[  551.156883] snd_go7007: no version for "snd_pcm_new" found: kernel tainted.
[  551.195254] Linux video capture interface: v2.00
[  551.231256] go7007-usb: probing new GO7007 USB board
[  551.493421] go7007: registering new Plextor PX-TV402U-NA
[  551.512419] wis-saa7115: initializing SAA7115 at address 32 on WIS GO7007SB EZ-USB
[  551.592501] wis-uda1342: initializing UDA1342 at address 26 on WIS GO7007SB EZ-USB
[  551.611878] wis-sony-tuner: initializing tuner at address 96 on WIS GO7007SB EZ-USB
[  551.611904] wis-sony-tuner: type set to 202 (Sony NTSC (BTF-PB463Z))
[  551.611947] BUG: unable to handle kernel NULL pointer dereference at virtual address 0000006d
[  551.611953] printing eip: e0a3f810 *pde = 00000000 
[  551.611959] Oops: 0002 [#1] SMP 
[  551.611962] Modules linked in: wis_sony_tuner wis_uda1342 wis_saa7115 go7007_usb go7007 videodev v4l2_common v4l1_compat snd_go7007(F) i2c_core ipv6 af_packet radeon drm rfcomm l2cap bluetooth ppdev speedstep_lib cpufreq_powersave cpufreq_userspace cpufreq_ondemand cpufreq_stats freq_table cpufreq_conservative video output container sbs sbshc dock battery iptable_filter ip_tables x_tables ac lp snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss parport_pc parport snd_pcm snd_seq_dummy snd_seq_oss pcspkr snd_seq_midi evdev snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore snd_page_alloc iTCO_wdt iTCO_vendor_support button shpchp intel_agp agpgart pci_hotplug usbhid hid ext3 jbd mbcache sg sd_mod sr_mod cdrom ata_piix ata_generic floppy pata_acpi skge libata scsi_mod ehci_hcd uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  551.612019] 
[  551.612022] Pid: 5774, comm: modprobe Tainted: GF       (2.6.24-16-generic #1)
[  551.612025] EIP: 0060:[<e0a3f810>] EFLAGS: 00010202 CPU: 0
[  551.612039] EIP is at snd_pcm_set_ops+0x10/0x20 [snd_pcm]
[  551.612042] EAX: 00000001 EBX: dea66b20 ECX: e0b4e7e0 EDX: 00000034
[  551.612044] ESI: 00000000 EDI: def40000 EBP: 00000003 ESP: de611d38
[  551.612046]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
[  551.612049] Process modprobe (pid: 5774, ti=de610000 task=de220000 task.ti=de610000)
[  551.612051] Stack: e0b4d411 00000000 00000001 dea66b24 e0fce04d 0000f0f2 def40000 e0fc70ce 
[  551.612057]        e0fce04d def40014 def40868 00000060 000000ff 000000ca 00000004 00000000 
[  551.612064]        00000000 def40868 e0b98544 def40a2c def40000 e0b95d06 00000000 00000000 
[  551.612070] Call Trace:
[  551.612072]  [<e0b4d411>] go7007_snd_init+0x141/0x1b0 [snd_go7007]
[  551.612092]  [<e0fc70ce>] go7007_register_encoder+0x17e/0x200 [go7007]
[  551.612127]  [<e0b95d06>] go7007_usb_probe+0x206/0x720 [go7007_usb]
[  551.612162]  [<c0316518>] mutex_lock+0x8/0x20
[  551.612174]  [<e089e82b>] usb_autopm_do_device+0x7b/0x100 [usbcore]
[  551.612200]  [<e089e397>] usb_match_one_id+0x27/0xb0 [usbcore]
[  551.612230]  [<e089f5d9>] usb_probe_interface+0xb9/0x140 [usbcore]
[  551.612262]  [<c027d988>] driver_probe_device+0x88/0x190
[  551.612268]  [<c02113f0>] kobject_uevent_env+0xf0/0x3d0
[  551.612288]  [<c027dbfe>] __driver_attach+0x9e/0xa0
[  551.612298]  [<c027cdbb>] bus_for_each_dev+0x3b/0x60
[  551.612316]  [<c027d806>] driver_attach+0x16/0x20
[  551.612320]  [<c027db60>] __driver_attach+0x0/0xa0
[  551.612323]  [<c027d13a>] bus_add_driver+0x8a/0x1e0
[  551.612345]  [<e089f11e>] usb_register_driver+0x8e/0x110 [usbcore]
[  551.612377]  [<c01506b6>] sys_init_module+0x126/0x19c0
[  551.612510]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[  551.612552]  =======================
[  551.612553] Code: 89 d1 89 d8 89 34 24 8b 17 e8 6d fb ff ff 89 c1 eb dc 90 90 90 90 90 90 90 90 90 6b d2 34 8b 84 10 b8 00 00 00 85 c0 74 0f 66 90 <89> 48 6c 8b 80 80 00 00 00 85 c0 75 f3 f3 c3 90 8b 50 70 8b 00 
[  551.612587] EIP: [<e0a3f810>] snd_pcm_set_ops+0x10/0x20 [snd_pcm] SS:ESP 0068:de611d38
[  551.612599] ---[ end trace b000d5c89156ef1a ]---
[  591.567632] usb 5-1: USB disconnect, address 4
user@lcotgs-server:~$ 


```

---

### Post by Rohan Kapoor on 2009-01-04
> **Warll said:**
> Alright so mythbuntu wasn't the easy way, tried Fedora 9, got a headache tring ot set up vnc. Installed Ubuntu 8.04 and I am a lot closer I have the drivers compiled, I think, the only problem now is that it won't detect the device. I seem to have found when its going wrong heres the dmesg, notice the tainted kernel part.
```
[  549.109449] usb 5-1: USB disconnect, address 2
[  550.859987] usb 5-1: new high speed USB device using ehci_hcd and address 4
[  550.992467] usb 5-1: configuration #1 chosen from 1 choice
[  551.156883] snd_go7007: no version for "snd_pcm_new" found: kernel tainted.
[  551.195254] Linux video capture interface: v2.00
[  551.231256] go7007-usb: probing new GO7007 USB board
[  551.493421] go7007: registering new Plextor PX-TV402U-NA
[  551.512419] wis-saa7115: initializing SAA7115 at address 32 on WIS GO7007SB EZ-USB
[  551.592501] wis-uda1342: initializing UDA1342 at address 26 on WIS GO7007SB EZ-USB
[  551.611878] wis-sony-tuner: initializing tuner at address 96 on WIS GO7007SB EZ-USB
[  551.611904] wis-sony-tuner: type set to 202 (Sony NTSC (BTF-PB463Z))
[  551.611947] BUG: unable to handle kernel NULL pointer dereference at virtual address 0000006d
[  551.611953] printing eip: e0a3f810 *pde = 00000000 
[  551.611959] Oops: 0002 [#1] SMP 
[  551.611962] Modules linked in: wis_sony_tuner wis_uda1342 wis_saa7115 go7007_usb go7007 videodev v4l2_common v4l1_compat snd_go7007(F) i2c_core ipv6 af_packet radeon drm rfcomm l2cap bluetooth ppdev speedstep_lib cpufreq_powersave cpufreq_userspace cpufreq_ondemand cpufreq_stats freq_table cpufreq_conservative video output container sbs sbshc dock battery iptable_filter ip_tables x_tables ac lp snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss parport_pc parport snd_pcm snd_seq_dummy snd_seq_oss pcspkr snd_seq_midi evdev snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore snd_page_alloc iTCO_wdt iTCO_vendor_support button shpchp intel_agp agpgart pci_hotplug usbhid hid ext3 jbd mbcache sg sd_mod sr_mod cdrom ata_piix ata_generic floppy pata_acpi skge libata scsi_mod ehci_hcd uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  551.612019] 
[  551.612022] Pid: 5774, comm: modprobe Tainted: GF       (2.6.24-16-generic #1)
[  551.612025] EIP: 0060:[<e0a3f810>] EFLAGS: 00010202 CPU: 0
[  551.612039] EIP is at snd_pcm_set_ops+0x10/0x20 [snd_pcm]
[  551.612042] EAX: 00000001 EBX: dea66b20 ECX: e0b4e7e0 EDX: 00000034
[  551.612044] ESI: 00000000 EDI: def40000 EBP: 00000003 ESP: de611d38
[  551.612046]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
[  551.612049] Process modprobe (pid: 5774, ti=de610000 task=de220000 task.ti=de610000)
[  551.612051] Stack: e0b4d411 00000000 00000001 dea66b24 e0fce04d 0000f0f2 def40000 e0fc70ce 
[  551.612057]        e0fce04d def40014 def40868 00000060 000000ff 000000ca 00000004 00000000 
[  551.612064]        00000000 def40868 e0b98544 def40a2c def40000 e0b95d06 00000000 00000000 
[  551.612070] Call Trace:
[  551.612072]  [<e0b4d411>] go7007_snd_init+0x141/0x1b0 [snd_go7007]
[  551.612092]  [<e0fc70ce>] go7007_register_encoder+0x17e/0x200 [go7007]
[  551.612127]  [<e0b95d06>] go7007_usb_probe+0x206/0x720 [go7007_usb]
[  551.612162]  [<c0316518>] mutex_lock+0x8/0x20
[  551.612174]  [<e089e82b>] usb_autopm_do_device+0x7b/0x100 [usbcore]
[  551.612200]  [<e089e397>] usb_match_one_id+0x27/0xb0 [usbcore]
[  551.612230]  [<e089f5d9>] usb_probe_interface+0xb9/0x140 [usbcore]
[  551.612262]  [<c027d988>] driver_probe_device+0x88/0x190
[  551.612268]  [<c02113f0>] kobject_uevent_env+0xf0/0x3d0
[  551.612288]  [<c027dbfe>] __driver_attach+0x9e/0xa0
[  551.612298]  [<c027cdbb>] bus_for_each_dev+0x3b/0x60
[  551.612316]  [<c027d806>] driver_attach+0x16/0x20
[  551.612320]  [<c027db60>] __driver_attach+0x0/0xa0
[  551.612323]  [<c027d13a>] bus_add_driver+0x8a/0x1e0
[  551.612345]  [<e089f11e>] usb_register_driver+0x8e/0x110 [usbcore]
[  551.612377]  [<c01506b6>] sys_init_module+0x126/0x19c0
[  551.612510]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[  551.612552]  =======================
[  551.612553] Code: 89 d1 89 d8 89 34 24 8b 17 e8 6d fb ff ff 89 c1 eb dc 90 90 90 90 90 90 90 90 90 6b d2 34 8b 84 10 b8 00 00 00 85 c0 74 0f 66 90 <89> 48 6c 8b 80 80 00 00 00 85 c0 75 f3 f3 c3 90 8b 50 70 8b 00 
[  551.612587] EIP: [<e0a3f810>] snd_pcm_set_ops+0x10/0x20 [snd_pcm] SS:ESP 0068:de611d38
[  551.612599] ---[ end trace b000d5c89156ef1a ]---
[  591.567632] usb 5-1: USB disconnect, address 4
user@lcotgs-server:~$ 


```
It looks like your kernel is tainted. I believe you may need to complie your own kernel which will be a helluva lot of fun!

---

### Post by Warll on 2009-01-04
I don't think its that bad. What I think did it was my "following" the steps outlined here: [http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver#Ubuntu_Hardy_with_kernel_.3C.3D_2.6.46-17](http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver#Ubuntu_Hardy_with_kernel_.3C.3D_2.6.46-17) The thing is I don't have a linux-headers-2.6.24-19-generic. So instead I renamed the sound link in the linux-headers-2.6.24-**22**-generic folder and used linux-headers-2.6.24-**22**-generic instead of linux-headers-2.6.24-**19**-generic wherever it was referenced. My guess is that I really need to use linux-headers-2.6.24-16-generic, in fact it said something about linux-headers-2.6.24-16-generic when it was compiling the driver. The list of kernel folders I have: 
```
user@lcotgs-server:/usr/src$ ls
linux-headers-2.6.24-16          linux-headers-2.6.24-22
linux-headers-2.6.24-16-generic  linux-headers-2.6.24-22-generic

``` How do I know which one my computer uses? Do I even need to know?

Edit:
Alright so a rebuild of the kernel using the "correct" linux-header did not fix it. I take it I'll have to reinstall?
Edit2: 
Ok after rereading the issue I think I stumbled on I think its best I use 7.10. Reinstall ahead! but not before bed!

---

### Post by Rohan Kapoor on 2009-01-04
> **Warll said:**
> I don't think its that bad. What I think did it was my "following" the steps outlined here: [http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver#Ubuntu_Hardy_with_kernel_.3C.3D_2.6.46-17](http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver#Ubuntu_Hardy_with_kernel_.3C.3D_2.6.46-17) The thing is I don't have a linux-headers-2.6.24-19-generic. So instead I renamed the sound link in the linux-headers-2.6.24-**22**-generic folder and used linux-headers-2.6.24-**22**-generic instead of linux-headers-2.6.24-**19**-generic wherever it was referenced. My guess is that I really need to use linux-headers-2.6.24-16-generic, in fact it said something about linux-headers-2.6.24-16-generic when it was compiling the driver. The list of kernel folders I have: 
```
user@lcotgs-server:/usr/src$ ls
linux-headers-2.6.24-16          linux-headers-2.6.24-22
linux-headers-2.6.24-16-generic  linux-headers-2.6.24-22-generic

``` How do I know which one my computer uses? Do I even need to know?

Edit:
Alright so a rebuild of the kernel using the "correct" linux-header did not fix it. I take it I'll have to reinstall?
Edit2: 
Ok after rereading the issue I think I stumbled on I think its best I use 7.10. Reinstall ahead! but not before bed!
Allrighty then, yes from your link 7.10 looks like a better idea. However when you update kernels and have two, you should be able to delete one!

---

### Post by Warll on 2009-01-04
I never ran a kernel update though, thats how it was out of the box.

---

### Post by Rohan Kapoor on 2009-01-04
> **Warll said:**
> I never ran a kernel update though, thats how it was out of the box.
You should still be able to delete one of the kernels:

[http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/](http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/)

---

### Post by Warll on 2009-01-10
Alright I have everything working, the network share, VNC and most importantly the PX-TV402U. In the end I had to use 7.10. I did get a scare though since while I had the PX-TV402U working at first, later after I got the VNC and share working the PX-TV402U had just stopped working. In the end I had to set GRUB to boot with the older kernel, guess one of the updates had changed the kernel.

---

### Post by Rohan Kapoor on 2009-01-11
> **Warll said:**
> Alright I have everything working, the network share, VNC and most importantly the PX-TV402U. In the end I had to use 7.10. I did get a scare though since while I had the PX-TV402U working at first, later after I got the VNC and share working the PX-TV402U had just stopped working. In the end I had to set GRUB to boot with the older kernel, guess one of the updates had changed the kernel.
I'm glas to hear you could do it. Hope to see you around!

---

