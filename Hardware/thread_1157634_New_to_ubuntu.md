---
title: "New to ubuntu"
date: 2009-05-12
forum: Hardware
---

### Post by LisaKayyyyyy on 2009-05-12
My friend ranted and raved about ubuntu for months. After extensive windows problems I just yesterday whiped out my hard drive and installed ubuntu.

I love it so far, issue is I need to figure out how to hook up my wireless. I have a broadcom internally but I cannot seem to get it to connect. I'm assuming i need some drivers but I have no idea where to begin to look. 

Anyone patient willing to help me :D

---

### Post by sir_nasty on 2009-05-12
hook us up with some info about your system.... wireless for starters... drop into terminal and run: dmesg | grep "broadcom" and let us see the results....

---

### Post by LisaKayyyyyy on 2009-05-12
i know how to get into the terminal but when i type in what you've wrote nothing happens :O

---

### Post by sir_nasty on 2009-05-12
in that case just drop into terminal and run dmesg, post the info related to your network adapter... should give us a clue about what's happening....

What kind of pc are you using? or is it a laptop?

---

### Post by sir_nasty on 2009-05-12
or try dmesg | grep broadcom

---

### Post by LisaKayyyyyy on 2009-05-12
17.096721] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   17.098283] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[   17.164223] pcmcia_socket pcmcia_socket1: pccard: PCMCIA card inserted into slot 1
[   17.164237] pcmcia_socket pcmcia_socket1: cs: memory probe 0xf6000000-0xfbffffff: excluding 0xf6000000-0xf65fffff 0xf6c00000-0xf71fffff 0xf7e00000-0xf83fffff 0xf9c00000-0xfa1fffff 0xfae00000-0xfb3fffff
[   17.177730] pcmcia 1.0: pcmcia: registering new device pcmcia1.0
[   17.179011] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: clean.
[   17.180055] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: clean.
[   17.180485] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
[   17.180541] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
[   17.181071] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[   17.181814] input: DualPoint Stick as /devices/platform/i8042/serio1/input/input7
[   17.215699] input: AlpsPS/2 ALPS DualPoint TouchPad as /devices/platform/i8042/serio1/input/input8
[   17.924041] intel8x0_measure_ac97_clock: measured 55226 usecs
[   17.924046] intel8x0: clocking to 48000
[   18.071548] lp0: using parport0 (interrupt-driven).
[   18.139655] Adding 1253028k swap on /dev/sda5.  Priority:-1 extents:1 across:1253028k
[   18.164769] EXT3 FS on sda1, internal journal
[   18.750398] type=1505 audit(1242183474.380:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1910
[   18.814551] type=1505 audit(1242183474.444:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1914
[   18.814706] type=1505 audit(1242183474.444:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1914
[   18.814763] type=1505 audit(1242183474.444:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1914
[   18.814815] type=1505 audit(1242183474.444:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1914
[   19.005677] type=1505 audit(1242183474.636:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1919
[   19.006047] type=1505 audit(1242183474.636:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1919
[   19.042783] type=1505 audit(1242183474.672:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1923
[   21.582684] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.582689] Bluetooth: BNEP filters: protocol multicast
[   21.600338] Bridge firewalling registered
[   22.818060] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   23.078465] [drm] Initialized drm 1.1.0 20060810
[   23.364929] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   23.758332] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   23.758353] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   23.758390] pci 0000:01:00.0: putting AGP V2 device into 4x mode
[   24.179840] [drm] Setting GART location based on new memory map
[   24.179850] [drm] Loading R200 Microcode
[   24.179905] [drm] writeback test succeeded in 2 usecs
[   27.671626] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.742506] input: b43-phy0 as /devices/virtual/input/input9
[   27.772489] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   27.901110] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   27.901117] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).
[   27.915367] input: b43-phy0 as /devices/virtual/input/input10
[   27.945812] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   27.947881] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   27.947887] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).
[   29.237279] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   29.237284] tg3: eth0: Flow control is off for TX and off for RX.
[   29.237561] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   39.736034] eth0: no IPv6 routers present

---

### Post by sir_nasty on 2009-05-12
Here's the offending part...

27.772489] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[ 27.901110] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[ 27.901117] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Dr...devicefirmware](http://linuxwireless.org/en/users/Dr...devicefirmware) and download the latest firmware (version 4).
[ 27.915367] input: b43-phy0 as /devices/virtual/input/input10
[ 27.945812] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[ 27.947881] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[ 27.947887] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Dr...devicefirmware](http://linuxwireless.org/en/users/Dr...devicefirmware) and download the latest firmware (version 4).

you need the drivers/firmware for a b43xx card... follow that link to linuxwireless and get the firmware and put it in /lib/firmware then just do a quick reboot....

I think the command we need is dmesg | grep b43

---

### Post by LisaKayyyyyy on 2009-05-12
i went to the link but i totally dont get it. broadcom has like 343048 drivers on their site. and idk which one i need. and i dont know how to extract the firmware from the file.

i'm like retarded at this :-/.

windows born and raised. lol.

---

### Post by sir_nasty on 2009-05-12
here's a link for some info:

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

However, based on what it's saying....  run uname -r and it should say what kernel version you are running, then follow that link above and download the drivers/firmware that correspond...

essentially you need to get this file: ucode5.fw into the /lib/firmware directory and it should fix it.

---

### Post by LisaKayyyyyy on 2009-05-12
wooo english!!! haha. alright i'm going to try this out :D wish me luck.

thanks a bunch for your help and patience!

---

### Post by sir_nasty on 2009-05-12
better yet!  a helpfull person found the firmware and posted a link (pain in the rear to find...)

[http://www.omattos.com/broadcom/](http://www.omattos.com/broadcom/)

download that file and put it in the right directory and reboot.

---

### Post by LisaKayyyyyy on 2009-05-12
ok i think i have the correct file. now when i try to drag it into to the lib/firmware folder it says that i do not have permission to do so...

---

### Post by LisaKayyyyyy on 2009-05-12
alright i downloaded the link you just sent, to be sure i had everything correct. now how exactly do i put it into the firmware folder. can i just drag both folders that extract from the zip directly into the firmware folder.

ahh i feel so dumb :-/

---

### Post by sir_nasty on 2009-05-12
yeah it's a permissions thing..... here's the "easy way"

since you're a windows guy like me I hope you understand directories....


open terminal and type: 
```

sudo mv /directorywherefileis/filename /lib/firmware/ucode5.fw

cd /lib/firmware
ls

```
you should see the ucode.fw file there

---

### Post by sir_nasty on 2009-05-12
now assuming you are going to run into the same issue I did at one point.... where the @#$@#! is the file at?  Open the folder in the 'file browser' click the little arrow that points left and it will expand to show you the path to the files

you only need to copy that one file, not the whole folder

---

### Post by LisaKayyyyyy on 2009-05-12
:( im clearly not as smart as you! i cant get that to work. i got the whole sudo thing, to prompt me for my password. i know the file location. 
but im still like.. lost :P

---

### Post by sir_nasty on 2009-05-12
did you get the sudo mv xxalksdf;a skdfsl/fiel command to work?  if so then do a reboot and run dmesg again and post the results.

if not then post the exact location of the firmware file.

FYI: ucode5.fw is the firmware file

---

### Post by LisaKayyyyyy on 2009-05-12
i didnt get anything to work correctly.


however i know that hte firmware file is in the following location

home/lisa/desktop/b43-all-fw/b43/ucode5.fw


im on a fkn time limit. im borrowing someones ethernet cable for the next 5 or so minutes and then i gotta wait til tomorrow :-/

---

### Post by sir_nasty on 2009-05-12
type this:

sudo mv home/lisa/desktop/b43-all-fw/b43/ucode5.fw /lib/firmware/ucode5.fw

then restart

dmesg 

post results

---

### Post by wabbalee on 2009-05-12
try this:

you would probably need to enable your wireless functionality.
check 'system' -> 'hardware drivers' with a network cable plugged in.
if nothing shows up there then update your system first and after reboot check there again with the network cable still plugged in. It will probably (after enabling) want to download/install drivers for your hardware.

---

### Post by sir_nasty on 2009-05-12
correction:

sudo mv /home/lisa/desktop/b43-all-fw/b43/ucode5.fw /lib/firmware/ucode5.fw

---

### Post by LisaKayyyyyy on 2009-05-12
ill do that and post the results tomorrow. im getting booted out of this bedroom. these folks want to sleep haha. ill have to resume tomorrow. thank you so much for your help!!! 

 as for the wireless functionality mumbojumbo yeah i tried that first. deemed it the easy route. didnt work. :(

---

### Post by sir_nasty on 2009-05-13
since you'll probably be here before me you could always drop into terminal, run gksudo nautilus or 

gksu "nautilus --no-desktop"

and try to drag/drop the file into the /lib/firmware directory

---

### Post by LisaKayyyyyy on 2009-05-13
i have the phsyical ucode5.fw file in the firmware folder now... but  i still cannot get my wireless router up and running.

---

### Post by sir_nasty on 2009-05-13
can you give me a quick output of dmesg so we can see that it's loading properly?

---

### Post by LisaKayyyyyy on 2009-05-13
i cant copy paste :-x im running on a windows computer right now wirelessly with ubuntu on my laptop in front of me.

---

### Post by sir_nasty on 2009-05-13
ok, then under the dmesg does it show the broadcom loading the firmware file?  before it said it couldn't find it please visit blah blah blah to download it... if that's all correct now then I'd go into network manager and see if it shows up

---

### Post by LisaKayyyyyy on 2009-05-13
sooo i couldnt get it to work finally i downgraded from 9.04 to 8.04. did the same things i was doing before and it worked! woooo hoooo :) thank you so much for your help. its greatly appreciated! :KS

---

### Post by sir_nasty on 2009-05-13
no problem glad it's working!

---

### Post by LisaKayyyyyy on 2009-05-13
more issues! a) my inboard microphone, and b) my usb devices...

when i dmesg it says my usbs are working and it says my webcam has been recognized but i do believe i need the drivers to get it to work. ahh help some more!?

---

### Post by LisaKayyyyyy on 2009-05-13
okay, my mic is working! woot.

but on to the usb issues.

nothing i connect will work. even tho its been recognized :-/

---

