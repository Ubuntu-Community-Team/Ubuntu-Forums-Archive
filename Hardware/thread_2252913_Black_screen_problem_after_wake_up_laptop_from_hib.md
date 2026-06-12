---
title: "Black screen problem after wake up laptop from hibernation"
date: 2014-11-15
forum: Hardware
---

### Post by maruda on 2014-11-15
Hi all.
I'd like to ask you about help with strange problem. I've installed Xubuntu : Linux 3.13.0-39-generic #66-Ubuntu SMP Tue Nov 15 13:31:23 UTC 2014 i686 i686 i686 GNU/Linux. If I close the laptop lid it goes sleep. After I opening a lid and laptop wake up, login menu appear to unlock session . I write my login / password and after I press 'Enter' the screen goes black :mad:. I can see that laptop isn't hungs up but I can't get screen back from black and I have to shut down laptop.
Please let me know some clue what to do?

I've enclosed some additional information I hope to help to figure out solution:

1. laptiop: Dell XPS M 1330
2. graphic card: Nvidia Geforce 8400M GS 128 MB
3. driver loaded: 
```

a@tr:~$ sudo lshw -c video | grep 'configuration'
[sudo] password for a:
       configuration: driver=nouveau latency=0

```
Here is dump command: dmesg | grep video:
```

[  209.177227] systemd-hostnamed[2417]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
a@tr:~$ dmesg | grep video
[    0.252866] pci 0000:01:00.0: Boot video device
[   15.015941] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   15.511381] Linux video capture interface: v2.00
[   15.978947] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:7670)
[   15.980322] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[   16.017354] usbcore: registered new interface driver uvcvideo
a@tr:~$ 

```

When I check my system settings from Xwindows in section 'Additional drivers' I can see there is checked: 
> 
Server X od X.Org --driver Nouveau from xserver-xorg-video-nouveau (opensource)


Besides this one deiver above, I can see there a lot different Nvidia drivers (but I don't know how to unistall them).

In System settings in 'Start and session' section I've tuned off 'NVIDIA X Servers Settings (configure NVIDIA X Server Settings)' and it not starting automatically.

Please for help.

Best wishes.
-= maruda=-

---

### Post by Linus_Drumbler on 2014-11-18
This appears to be a well-known and common bug. It seems to have been fixed already, or so the developers claim...[https://bugs.launchpad.net/ubuntu/+source/xubuntu-default-settings/+bug/1303736](https://bugs.launchpad.net/ubuntu/+source/xubuntu-default-settings/+bug/1303736) [https://bugs.launchpad.net/ubuntu/+source/xubuntu-default-settings/+bug/1342065](https://bugs.launchpad.net/ubuntu/+source/xubuntu-default-settings/+bug/1342065)

I have this problem too. I have an Asus K751, and the standard fixes haven't worked for me.

---

