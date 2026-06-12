---
title: "Iriver mp3 player, USB"
date: 2005-12-19
forum: Hardware &amp; Laptops
---

### Post by Nickoladze on 2005-12-19
Yeah im new to nix and im trying to get my mp3 player connected to usbto mount. i type lsusb and its there saying:
> Bus 004 Device 003: ID 4102:2101 iRiver, Ltd.


but im not sure where to go from there.
its not showing up on my desktop, /media, or /mnt

---

### Post by jliedeka on 2005-12-19
Your iRiver may not support the usb-storage protocol.  I have the iFP-799 and mine doesn't.  I use a utility called ifp to access.  There a couple of gui-based interfaces as well.  I have the Iriver Music Manager.

---

### Post by Nickoladze on 2005-12-19
i have an h10, and i can use it like that on windows, theres no iriver manager program for h10s

---

### Post by jliedeka on 2005-12-19
If you don't already have a mount point set up under /media or /mnt, create one with

sudo mkdir /media/usbdrive
 (or whatver you want it to be)

Then try:

sudo mount -t vfat -o rw,uid=1000,gid=1000,sync,noatime,nosuid /dev/sda1 /media/usbdrive

Your device may not be /dev/sda1 if you have more than one thing plugged into USB or if you have SCSI or SATA drives.

---

### Post by Nickoladze on 2005-12-19
> mount: special device /dev/sda1 does not exist


yeah theres no sda1 folder, but the list of folders in /dev are:
evms
fd
input
loop
mapper
net
pts
shm
snd


yeah im really new at this, but thanks for your help so far :D

---

### Post by jliedeka on 2005-12-19
I'm guessing the hotplug driver isn't loading the usp-storage driver when you connect the device.

Can you connect the device the post what you get in dmesg?

---

### Post by Nickoladze on 2005-12-19
```
aj@AJComputer:~$ dmesg
or detected.  Restarting.
[4303519.732000] ipw2200: Firmware error detected.  Restarting.
[4303522.099000] ipw2200: Firmware error detected.  Restarting.
[4303550.964000] ipw2200: Firmware error detected.  Restarting.
[4303559.879000] ipw2200: failed to send SSID command
[4303560.879000] ipw2200: failed to send ASSOCIATE command
[4303561.879000] ipw2200: failed to send SSID command
[4303673.789000] ipw2200: Firmware error detected.  Restarting.
[4303678.364000] ipw2200: Firmware error detected.  Restarting.
[4303681.850000] ipw2200: Firmware error detected.  Restarting.
[4303687.639000] ipw2200: Firmware error detected.  Restarting.
[4303689.077000] ipw2200: Firmware error detected.  Restarting.
[4303694.702000] ipw2200: Firmware error detected.  Restarting.
[4303696.716000] ipw2200: Firmware error detected.  Restarting.
[4303700.298000] ipw2200: Firmware error detected.  Restarting.
[4303712.489000] ipw2200: Firmware error detected.  Restarting.
[4303716.775000] ipw2200: Firmware error detected.  Restarting.
[4303725.190000] ipw2200: Firmware error detected.  Restarting.
[4303728.772000] ipw2200: Firmware error detected.  Restarting.
[4303730.971000] ipw2200: Firmware error detected.  Restarting.
[4303735.320000] ipw2200: Firmware error detected.  Restarting.
[4303737.687000] ipw2200: Firmware error detected.  Restarting.
[4303739.072000] ipw2200: Firmware error detected.  Restarting.
[4303743.710000] ipw2200: Firmware error detected.  Restarting.
[4303745.714000] ipw2200: Firmware error detected.  Restarting.
[4303758.354000] ipw2200: Firmware error detected.  Restarting.
[4303760.249000] ipw2200: Firmware error detected.  Restarting.
[4303786.985000] ipw2200: Firmware error detected.  Restarting.
[4303792.583000] ipw2200: Firmware error detected.  Restarting.
[4303826.743000] ipw2200: Firmware error detected.  Restarting.
[4303831.911000] ipw2200: Firmware error detected.  Restarting.
[4303837.221000] ipw2200: Firmware error detected.  Restarting.
[4303839.875000] ipw2200: Firmware error detected.  Restarting.
[4303844.836000] ipw2200: Firmware error detected.  Restarting.
[4303846.667000] ipw2200: Firmware error detected.  Restarting.
[4303850.738000] ipw2200: Firmware error detected.  Restarting.
[4303853.808000] ipw2200: Firmware error detected.  Restarting.
[4303870.704000] ipw2200: Firmware error detected.  Restarting.
[4303876.847000] ipw2200: Firmware error detected.  Restarting.
[4303880.141000] ipw2200: Firmware error detected.  Restarting.
[4303885.355000] ipw2200: Firmware error detected.  Restarting.
[4303887.401000] ipw2200: Firmware error detected.  Restarting.
[4303895.688000] ipw2200: Firmware error detected.  Restarting.
[4303913.321000] ipw2200: Firmware error detected.  Restarting.
[4303920.991000] ipw2200: Firmware error detected.  Restarting.
[4303948.449000] ipw2200: Firmware error detected.  Restarting.
[4303951.200000] ipw2200: Firmware error detected.  Restarting.
[4303955.102000] ipw2200: Firmware error detected.  Restarting.
[4303957.980000] ipw2200: Firmware error detected.  Restarting.
[4303960.290000] ipw2200: Firmware error detected.  Restarting.
[4303963.163000] ipw2200: Firmware error detected.  Restarting.
[4303969.529000] ipw2200: Firmware error detected.  Restarting.
[4303970.268000] ipw2200: Firmware error detected.  Restarting.
[4303974.522000] ipw2200: Firmware error detected.  Restarting.
[4304195.161000] ipw2200: Firmware error detected.  Restarting.
[4304405.111000] ipw2200: Firmware error detected.  Restarting.
[4304419.767000] ipw2200: Firmware error detected.  Restarting.
[4304422.486000] ipw2200: Firmware error detected.  Restarting.
[4304424.108000] ipw2200: Firmware error detected.  Restarting.
[4304427.754000] ipw2200: Firmware error detected.  Restarting.
[4304430.275000] ipw2200: Firmware error detected.  Restarting.
[4304433.111000] ipw2200: Firmware error detected.  Restarting.
[4304437.493000] ipw2200: Firmware error detected.  Restarting.
[4304439.771000] ipw2200: Firmware error detected.  Restarting.
[4304445.930000] ipw2200: Firmware error detected.  Restarting.
[4304448.232000] ipw2200: Firmware error detected.  Restarting.
[4304461.255000] ipw2200: Firmware error detected.  Restarting.
[4304469.441000] ipw2200: Firmware error detected.  Restarting.
[4304478.240000] ipw2200: Firmware error detected.  Restarting.
[4304480.478000] ipw2200: Firmware error detected.  Restarting.
[4304494.334000] ipw2200: Firmware error detected.  Restarting.
[4304498.672000] ipw2200: Firmware error detected.  Restarting.
[4304501.070000] ipw2200: Firmware error detected.  Restarting.
[4304586.334000] ipw2200: Firmware error detected.  Restarting.
[4304647.845000] ipw2200: Firmware error detected.  Restarting.
[4304682.248000] ipw2200: Firmware error detected.  Restarting.
[4305079.850000] ipw2200: Firmware error detected.  Restarting.
[4305128.741000] ipw2200: Firmware error detected.  Restarting.
[4305147.982000] ipw2200: Firmware error detected.  Restarting.
[4305166.063000] ipw2200: Firmware error detected.  Restarting.
[4305169.387000] ipw2200: Firmware error detected.  Restarting.
[4305180.618000] ipw2200: Firmware error detected.  Restarting.
[4305183.976000] ipw2200: Firmware error detected.  Restarting.
[4305225.452000] ipw2200: Firmware error detected.  Restarting.
[4305302.357000] cdrom: open failed.
[4305326.712000] ipw2200: Firmware error detected.  Restarting.
[4305354.976000] ipw2200: Firmware error detected.  Restarting.
[4305425.896000] ipw2200: Firmware error detected.  Restarting.
[4305441.256000] ipw2200: Firmware error detected.  Restarting.
[4305463.785000] ipw2200: Firmware error detected.  Restarting.
[4305473.512000] ipw2200: Firmware error detected.  Restarting.
[4305518.839000] ipw2200: Firmware error detected.  Restarting.
[4305549.613000] ipw2200: Firmware error detected.  Restarting.
[4305554.923000] ipw2200: Firmware error detected.  Restarting.
[4305568.010000] ipw2200: Firmware error detected.  Restarting.
[4305570.313000] ipw2200: Firmware error detected.  Restarting.
[4305590.064000] ipw2200: Firmware error detected.  Restarting.
[4305636.564000] ipw2200: Firmware error detected.  Restarting.
[4305639.850000] ipw2200: Firmware error detected.  Restarting.
[4305645.011000] ipw2200: Firmware error detected.  Restarting.
[4305651.472000] ipw2200: Firmware error detected.  Restarting.
[4305659.971000] ipw2200: Firmware error detected.  Restarting.
[4305661.953000] ipw2200: Firmware error detected.  Restarting.
[4305677.992000] ipw2200: Firmware error detected.  Restarting.
[4305687.368000] ipw2200: Firmware error detected.  Restarting.
[4305690.118000] ipw2200: Firmware error detected.  Restarting.
[4305703.275000] ipw2200: Firmware error detected.  Restarting.
[4305706.602000] ipw2200: Firmware error detected.  Restarting.
[4305722.794000] ipw2200: Firmware error detected.  Restarting.
[4305725.256000] ipw2200: Firmware error detected.  Restarting.
[4305729.158000] ipw2200: Firmware error detected.  Restarting.
[4305737.905000] ipw2200: Firmware error detected.  Restarting.
[4305747.280000] ipw2200: Firmware error detected.  Restarting.
[4305752.175000] ipw2200: Firmware error detected.  Restarting.
[4305758.487000] ipw2200: Firmware error detected.  Restarting.
[4305761.109000] ipw2200: Firmware error detected.  Restarting.
[4305826.333000] ipw2200: Firmware error detected.  Restarting.
[4305853.818000] ipw2200: Firmware error detected.  Restarting.
[4305873.563000] ipw2200: Firmware error detected.  Restarting.
[4305878.681000] ipw2200: Firmware error detected.  Restarting.
[4305881.016000] ipw2200: Firmware error detected.  Restarting.
[4305882.313000] ipw2200: Firmware error detected.  Restarting.
[4305891.560000] ipw2200: Firmware error detected.  Restarting.
[4305893.733000] ipw2200: Firmware error detected.  Restarting.
[4305927.595000] ipw2200: Firmware error detected.  Restarting.
[4305976.184000] ipw2200: Firmware error detected.  Restarting.
[4305987.803000] ipw2200: Firmware error detected.  Restarting.
[4306008.181000] ipw2200: Firmware error detected.  Restarting.
[4306049.913000] ipw2200: Firmware error detected.  Restarting.
[4306056.513000] ipw2200: Firmware error detected.  Restarting.
[4306060.863000] ipw2200: Firmware error detected.  Restarting.
[4306063.517000] ipw2200: Firmware error detected.  Restarting.
[4306066.716000] ipw2200: Firmware error detected.  Restarting.
[4306068.603000] ipw2200: Firmware error detected.  Restarting.
[4306071.743000] ipw2200: Firmware error detected.  Restarting.
[4306077.150000] ipw2200: Firmware error detected.  Restarting.
[4306081.124000] ipw2200: Firmware error detected.  Restarting.
[4306083.298000] ipw2200: Firmware error detected.  Restarting.
[4306086.429000] ipw2200: Firmware error detected.  Restarting.
[4306089.531000] ipw2200: Firmware error detected.  Restarting.
[4306097.674000] ipw2200: Firmware error detected.  Restarting.
[4306277.572000] ipw2200: Firmware error detected.  Restarting.
[4306386.450000] ipw2200: Firmware error detected.  Restarting.
[4306397.275000] ipw2200: Firmware error detected.  Restarting.
[4306408.154000] ipw2200: Firmware error detected.  Restarting.
[4306420.385000] ipw2200: Firmware error detected.  Restarting.
[4306430.003000] ipw2200: Firmware error detected.  Restarting.
[4306469.111000] ipw2200: Firmware error detected.  Restarting.
[4306524.509000] ipw2200: Firmware error detected.  Restarting.
[4306536.965000] ipw2200: Firmware error detected.  Restarting.
[4306755.556000] ipw2200: Firmware error detected.  Restarting.
[4306758.881000] ipw2200: Firmware error detected.  Restarting.
[4306761.695000] ipw2200: Firmware error detected.  Restarting.
[4306764.477000] ipw2200: Firmware error detected.  Restarting.
[4306777.789000] ipw2200: Firmware error detected.  Restarting.
[4306780.254000] ipw2200: Firmware error detected.  Restarting.
[4306787.101000] ipw2200: Firmware error detected.  Restarting.
[4306787.775000] ipw2200: Firmware error detected.  Restarting.
[4306792.829000] ipw2200: Firmware error detected.  Restarting.
[4306794.780000] ipw2200: Firmware error detected.  Restarting.
[4306807.299000] ipw2200: Firmware error detected.  Restarting.
[4306809.672000] ipw2200: Firmware error detected.  Restarting.
[4306812.582000] ipw2200: Firmware error detected.  Restarting.
[4306815.723000] ipw2200: Firmware error detected.  Restarting.
[4306825.802000] ipw2200: Firmware error detected.  Restarting.
[4306827.752000] ipw2200: Firmware error detected.  Restarting.
[4306843.433000] ipw2200: Firmware error detected.  Restarting.
[4306845.738000] ipw2200: Firmware error detected.  Restarting.
[4306849.521000] ipw2200: Firmware error detected.  Restarting.
[4306868.672000] ipw2200: Firmware error detected.  Restarting.
[4306891.873000] ipw2200: Firmware error detected.  Restarting.
[4306905.442000] ipw2200: Firmware error detected.  Restarting.
[4306913.413000] ipw2200: Firmware error detected.  Restarting.
[4306949.937000] ipw2200: Firmware error detected.  Restarting.
[4306988.389000] ipw2200: Firmware error detected.  Restarting.
[4306995.399000] ipw2200: Firmware error detected.  Restarting.
[4307018.193000] ipw2200: Firmware error detected.  Restarting.
[4307019.665000] ipw2200: Firmware error detected.  Restarting.
[4307024.079000] ipw2200: Firmware error detected.  Restarting.
[4307050.801000] ipw2200: Firmware error detected.  Restarting.
[4307055.824000] ipw2200: Firmware error detected.  Restarting.
[4307127.320000] ipw2200: Firmware error detected.  Restarting.
[4307135.169000] ipw2200: Firmware error detected.  Restarting.
[4307184.358000] ipw2200: Firmware error detected.  Restarting.
[4307187.428000] ipw2200: Firmware error detected.  Restarting.
[4307230.885000] ipw2200: Firmware error detected.  Restarting.
[4307235.587000] ipw2200: Firmware error detected.  Restarting.
[4307246.878000] ipw2200: Firmware error detected.  Restarting.
[4307279.768000] ipw2200: Firmware error detected.  Restarting.
[4307325.016000] ipw2200: Firmware error detected.  Restarting.
[4307348.537000] ipw2200: Firmware error detected.  Restarting.
[4307352.961000] ipw2200: Firmware error detected.  Restarting.
[4307439.371000] ipw2200: Firmware error detected.  Restarting.
[4307469.998000] ipw2200: Firmware error detected.  Restarting.
[4307474.561000] ipw2200: Firmware error detected.  Restarting.
[4307476.817000] ipw2200: Firmware error detected.  Restarting.
[4307480.766000] ipw2200: Firmware error detected.  Restarting.
[4307533.694000] ipw2200: Firmware error detected.  Restarting.
[4307559.716000] ipw2200: Firmware error detected.  Restarting.
[4307598.632000] ipw2200: Firmware error detected.  Restarting.
[4307605.114000] ipw2200: Firmware error detected.  Restarting.
[4307749.198000] ipw2200: Firmware error detected.  Restarting.
[4307751.063000] ipw2200: Firmware error detected.  Restarting.
[4307782.361000] ipw2200: Firmware error detected.  Restarting.
[4307785.239000] ipw2200: Firmware error detected.  Restarting.
[4307787.285000] ipw2200: Firmware error detected.  Restarting.
[4307834.906000] ipw2200: Firmware error detected.  Restarting.
[4307846.630000] ipw2200: Firmware error detected.  Restarting.
[4307964.825000] ipw2200: Firmware error detected.  Restarting.
[4307972.806000] ipw2200: Firmware error detected.  Restarting.
[4307986.650000] ipw2200: Firmware error detected.  Restarting.
[4308112.586000] ipw2200: Firmware error detected.  Restarting.
[4308124.137000] ipw2200: Firmware error detected.  Restarting.
[4308129.081000] ipw2200: Firmware error detected.  Restarting.
[4308151.423000] ipw2200: Firmware error detected.  Restarting.
[4308239.850000] ipw2200: Firmware error detected.  Restarting.
[4308832.703000] cdrom: open failed.
[4309281.542000] ipw2200: Firmware error detected.  Restarting.
[4311665.872000] ipw2200: Firmware error detected.  Restarting.
[4311680.395000] ipw2200: Firmware error detected.  Restarting.
[4313940.418000] ipw2200: Firmware error detected.  Restarting.
[4314455.982000] ipw2200: Firmware error detected.  Restarting.
[4314516.484000] ipw2200: Firmware error detected.  Restarting.
[4314669.593000] ipw2200: Firmware error detected.  Restarting.
[4314825.307000] ipw2200: Firmware error detected.  Restarting.
[4314923.080000] ipw2200: Firmware error detected.  Restarting.
[4314932.593000] ipw2200: Firmware error detected.  Restarting.
[4316598.797000] ipw2200: Firmware error detected.  Restarting.
[4317499.028000] ipw2200: Firmware error detected.  Restarting.
[4317888.003000] usb 4-1: new high speed USB device using ehci_hcd and address 4
[4318563.956000] ipw2200: Firmware error detected.  Restarting.
[4318757.947000] ipw2200: Firmware error detected.  Restarting.
[4318997.837000] usb 4-1: USB disconnect, address 4
[4319059.238000] ipw2200: Firmware error detected.  Restarting.
[4319119.245000] ipw2200: Firmware error detected.  Restarting.
[4320709.342000] ipw2200: Firmware error detected.  Restarting.
[4321147.998000] ipw2200: Firmware error detected.  Restarting.
[4321159.582000] ipw2200: Firmware error detected.  Restarting.
[4321939.123000] ipw2200: Firmware error detected.  Restarting.
[4322095.164000] ipw2200: Firmware error detected.  Restarting.
[4322097.274000] ipw2200: Firmware error detected.  Restarting.
[4322227.147000] ipw2200: Firmware error detected.  Restarting.
[4323617.226000] ipw2200: Firmware error detected.  Restarting.
[4323761.651000] ipw2200: Firmware error detected.  Restarting.
[4323793.909000] ipw2200: Firmware error detected.  Restarting.
[4324268.268000] usb 4-1: new high speed USB device using ehci_hcd and address 5

```

so yeah i guess theres a firmware error, lol

---

### Post by jliedeka on 2005-12-20
Your wireless errors are another issue.  You could have omitted those.  The dmesg entry was most unhelpful.  It's fairly obvious the mass storage driver isn't being loaded.  2 suggestions.

1.  Try to sudo modprobe usb-storage with the device connected and see if a new sdX device shows up in /dev.

2.  If that fails, try installing ipf and see if it can establish communication with your device.  If 1 works, let me know and I'll try to figure out what you need to do with your hotplug setup to make it work automagically.

---

### Post by Nickoladze on 2005-12-20
first doesnt work and ifp installs but wont run (on wine)

well this probably wont work, and im planning on making a windows partition soon.

so i have a question, if i boot into windows and move my music onto my computer, can i access those files from the linux partition?

---

### Post by bk452 on 2005-12-20
> so i have a question, if i boot into windows and move my music onto my computer, can i access those files from the linux partition?

I'm pretty sure you can.  I could with SuSE.  I don't know how to do it with Ubuntu.

---

### Post by jliedeka on 2005-12-21
Ipf is a linux program.  I'm not sure what that has to do with wine.

---

### Post by Nickoladze on 2005-12-21
oh for some reason i was thinking of the iriver manager.

so i installed all he ifp stuff now and when running get:
```
err:  [ifp_os_control_send] err=-1. error sending ifp control code the command 2 (0, 3). ctl[8]  Returned -1.
err:  [ifp_control_send] err=-1. error sending control value
err:  [ifp_firmware_version] err=-1. error reading device model string
err:  [ifp_selftest] err=-1. couldn't get firmware version.
err:  [ifp_init] err=-1. self test failed.
Segmentation fault

```

---

### Post by 3rdalbum on 2005-12-21
The memory-based iRiver players can be loaded through normal UMS. Apparantly, some of the hard-disk players can too, but only those purchased in certain countries. If you live in the US, you may be out of luck.

---

### Post by jliedeka on 2005-12-22
You may want to check out [this]("http://www.leenooks.com/229") page.  I googled "iriver h10 linux".

---

### Post by Nickoladze on 2005-12-28
HEY THAT WORKED!!!!

mounted and everything, thanks for that link :D

---

### Post by nuclearwasted on 2006-01-09
On google I also found instructions on changing the H10's firmware and bootloader so that it always connects in UMS mode.

(sorry I don't have a link)

---

### Post by macca87 on 2006-07-27
OK, now a slightly new iRiver problem (not sure if its iRiver or ubs disks in general.. but anyways) i have a iRiver model T10 512mb, and i could plug it into fedora with no worries, however i am having a very wierd problem with ubuntu 6.06.

The device is recognised as a usb disk and mounted and i get a nice little launcher on the desktop and all, however i start copying files and all of a sudden there is no more disk space.... so i delete 3 albums and then try to copy the other album back on (Karnivool - Themata...check em out!!) anyways it still says not enough space.:-( 

so i looked in nautilus properties and it said size: 97Mb, and wont let me add any more.... whats the deal anyone know?

Here is the output of my df -h
/dev/sda              497M  497M     0 100% /media/usbdisk

497!! so i tried copying the files without nautilus by the terminal and it still said not enough space.. very confused

[EDIT] : Hey, just found a wierd thing, if i delete all files off the disk (sda) and do a 'df -h | grep sda' it still says 100% used.....
thanks

---

### Post by macca87 on 2006-07-27
Hey,
i noticed why... i feel dumb ahaha. If anyone wants to know..
every file i deleted off the disk was put into a hidden folder called .trash-[USERNAME], not seen to nautilus but in the term you can see with a ls -a.

Wow.. so does this mean any filesystem i mount and then delete files off contains this folder wasting my valuable space?

---

### Post by sinaen on 2006-08-15
> **Nickoladze said:**
> ```
aj@AJComputer:~$ dmesg
or detected.  Restarting.
[4303519.732000] ipw2200: Firmware error detected.  Restarting.
[4303522.099000] ipw2200: Firmware error detected.  Restarting.
[4303550.964000] ipw2200: Firmware error detected.  Restarting.
[4303559.879000] ipw2200: failed to send SSID command
[4303560.879000] ipw2200: failed to send ASSOCIATE command
[4303561.879000] ipw2200: failed to send SSID command
[4303673.789000] ipw2200: Firmware error detected.  Restarting.
[4303678.364000] ipw2200: Firmware error detected.  Restarting.
[4303681.850000] ipw2200: Firmware error detected.  Restarting.
[4303687.639000] ipw2200: Firmware error detected.  Restarting.
[4303689.077000] ipw2200: Firmware error detected.  Restarting.
[4303694.702000] ipw2200: Firmware error detected.  Restarting.
[4303696.716000] ipw2200: Firmware error detected.  Restarting.
[4303700.298000] ipw2200: Firmware error detected.  Restarting.
[4303712.489000] ipw2200: Firmware error detected.  Restarting.
[4303716.775000] ipw2200: Firmware error detected.  Restarting.
[4303725.190000] ipw2200: Firmware error detected.  Restarting.
[4303728.772000] ipw2200: Firmware error detected.  Restarting.
[4303730.971000] ipw2200: Firmware error detected.  Restarting.
[4303735.320000] ipw2200: Firmware error detected.  Restarting.
[4303737.687000] ipw2200: Firmware error detected.  Restarting.
[4303739.072000] ipw2200: Firmware error detected.  Restarting.
[4303743.710000] ipw2200: Firmware error detected.  Restarting.
[4303745.714000] ipw2200: Firmware error detected.  Restarting.
[4303758.354000] ipw2200: Firmware error detected.  Restarting.
[4303760.249000] ipw2200: Firmware error detected.  Restarting.
[4303786.985000] ipw2200: Firmware error detected.  Restarting.
[4303792.583000] ipw2200: Firmware error detected.  Restarting.
[4303826.743000] ipw2200: Firmware error detected.  Restarting.
[4303831.911000] ipw2200: Firmware error detected.  Restarting.
[4303837.221000] ipw2200: Firmware error detected.  Restarting.
[4303839.875000] ipw2200: Firmware error detected.  Restarting.
[4303844.836000] ipw2200: Firmware error detected.  Restarting.
[4303846.667000] ipw2200: Firmware error detected.  Restarting.
[4303850.738000] ipw2200: Firmware error detected.  Restarting.
[4303853.808000] ipw2200: Firmware error detected.  Restarting.
[4303870.704000] ipw2200: Firmware error detected.  Restarting.
[4303876.847000] ipw2200: Firmware error detected.  Restarting.
[4303880.141000] ipw2200: Firmware error detected.  Restarting.
[4303885.355000] ipw2200: Firmware error detected.  Restarting.
[4303887.401000] ipw2200: Firmware error detected.  Restarting.
[4303895.688000] ipw2200: Firmware error detected.  Restarting.
[4303913.321000] ipw2200: Firmware error detected.  Restarting.
[4303920.991000] ipw2200: Firmware error detected.  Restarting.
[4303948.449000] ipw2200: Firmware error detected.  Restarting.
[4303951.200000] ipw2200: Firmware error detected.  Restarting.
[4303955.102000] ipw2200: Firmware error detected.  Restarting.
[4303957.980000] ipw2200: Firmware error detected.  Restarting.
[4303960.290000] ipw2200: Firmware error detected.  Restarting.
[4303963.163000] ipw2200: Firmware error detected.  Restarting.
[4303969.529000] ipw2200: Firmware error detected.  Restarting.
[4303970.268000] ipw2200: Firmware error detected.  Restarting.
[4303974.522000] ipw2200: Firmware error detected.  Restarting.
[4304195.161000] ipw2200: Firmware error detected.  Restarting.
[4304405.111000] ipw2200: Firmware error detected.  Restarting.
[4304419.767000] ipw2200: Firmware error detected.  Restarting.
[4304422.486000] ipw2200: Firmware error detected.  Restarting.
[4304424.108000] ipw2200: Firmware error detected.  Restarting.
[4304427.754000] ipw2200: Firmware error detected.  Restarting.
[4304430.275000] ipw2200: Firmware error detected.  Restarting.
[4304433.111000] ipw2200: Firmware error detected.  Restarting.
[4304437.493000] ipw2200: Firmware error detected.  Restarting.
[4304439.771000] ipw2200: Firmware error detected.  Restarting.
[4304445.930000] ipw2200: Firmware error detected.  Restarting.
[4304448.232000] ipw2200: Firmware error detected.  Restarting.
[4304461.255000] ipw2200: Firmware error detected.  Restarting.
[4304469.441000] ipw2200: Firmware error detected.  Restarting.
[4304478.240000] ipw2200: Firmware error detected.  Restarting.
[4304480.478000] ipw2200: Firmware error detected.  Restarting.
[4304494.334000] ipw2200: Firmware error detected.  Restarting.
[4304498.672000] ipw2200: Firmware error detected.  Restarting.
[4304501.070000] ipw2200: Firmware error detected.  Restarting.
[4304586.334000] ipw2200: Firmware error detected.  Restarting.
[4304647.845000] ipw2200: Firmware error detected.  Restarting.
[4304682.248000] ipw2200: Firmware error detected.  Restarting.
[4305079.850000] ipw2200: Firmware error detected.  Restarting.
[4305128.741000] ipw2200: Firmware error detected.  Restarting.
[4305147.982000] ipw2200: Firmware error detected.  Restarting.
[4305166.063000] ipw2200: Firmware error detected.  Restarting.
[4305169.387000] ipw2200: Firmware error detected.  Restarting.
[4305180.618000] ipw2200: Firmware error detected.  Restarting.
[4305183.976000] ipw2200: Firmware error detected.  Restarting.
[4305225.452000] ipw2200: Firmware error detected.  Restarting.
[4305302.357000] cdrom: open failed.
[4305326.712000] ipw2200: Firmware error detected.  Restarting.
[4305354.976000] ipw2200: Firmware error detected.  Restarting.
[4305425.896000] ipw2200: Firmware error detected.  Restarting.
[4305441.256000] ipw2200: Firmware error detected.  Restarting.
[4305463.785000] ipw2200: Firmware error detected.  Restarting.
[4305473.512000] ipw2200: Firmware error detected.  Restarting.
[4305518.839000] ipw2200: Firmware error detected.  Restarting.
[4305549.613000] ipw2200: Firmware error detected.  Restarting.
[4305554.923000] ipw2200: Firmware error detected.  Restarting.
[4305568.010000] ipw2200: Firmware error detected.  Restarting.
[4305570.313000] ipw2200: Firmware error detected.  Restarting.
[4305590.064000] ipw2200: Firmware error detected.  Restarting.
[4305636.564000] ipw2200: Firmware error detected.  Restarting.
[4305639.850000] ipw2200: Firmware error detected.  Restarting.
[4305645.011000] ipw2200: Firmware error detected.  Restarting.
[4305651.472000] ipw2200: Firmware error detected.  Restarting.
[4305659.971000] ipw2200: Firmware error detected.  Restarting.
[4305661.953000] ipw2200: Firmware error detected.  Restarting.
[4305677.992000] ipw2200: Firmware error detected.  Restarting.
[4305687.368000] ipw2200: Firmware error detected.  Restarting.
[4305690.118000] ipw2200: Firmware error detected.  Restarting.
[4305703.275000] ipw2200: Firmware error detected.  Restarting.
[4305706.602000] ipw2200: Firmware error detected.  Restarting.
[4305722.794000] ipw2200: Firmware error detected.  Restarting.
[4305725.256000] ipw2200: Firmware error detected.  Restarting.
[4305729.158000] ipw2200: Firmware error detected.  Restarting.
[4305737.905000] ipw2200: Firmware error detected.  Restarting.
[4305747.280000] ipw2200: Firmware error detected.  Restarting.
[4305752.175000] ipw2200: Firmware error detected.  Restarting.
[4305758.487000] ipw2200: Firmware error detected.  Restarting.
[4305761.109000] ipw2200: Firmware error detected.  Restarting.
[4305826.333000] ipw2200: Firmware error detected.  Restarting.
[4305853.818000] ipw2200: Firmware error detected.  Restarting.
[4305873.563000] ipw2200: Firmware error detected.  Restarting.
[4305878.681000] ipw2200: Firmware error detected.  Restarting.
[4305881.016000] ipw2200: Firmware error detected.  Restarting.
[4305882.313000] ipw2200: Firmware error detected.  Restarting.
[4305891.560000] ipw2200: Firmware error detected.  Restarting.
[4305893.733000] ipw2200: Firmware error detected.  Restarting.
[4305927.595000] ipw2200: Firmware error detected.  Restarting.
[4305976.184000] ipw2200: Firmware error detected.  Restarting.
[4305987.803000] ipw2200: Firmware error detected.  Restarting.
[4306008.181000] ipw2200: Firmware error detected.  Restarting.
[4306049.913000] ipw2200: Firmware error detected.  Restarting.
[4306056.513000] ipw2200: Firmware error detected.  Restarting.
[4306060.863000] ipw2200: Firmware error detected.  Restarting.
[4306063.517000] ipw2200: Firmware error detected.  Restarting.
[4306066.716000] ipw2200: Firmware error detected.  Restarting.
[4306068.603000] ipw2200: Firmware error detected.  Restarting.
[4306071.743000] ipw2200: Firmware error detected.  Restarting.
[4306077.150000] ipw2200: Firmware error detected.  Restarting.
[4306081.124000] ipw2200: Firmware error detected.  Restarting.
[4306083.298000] ipw2200: Firmware error detected.  Restarting.
[4306086.429000] ipw2200: Firmware error detected.  Restarting.
[4306089.531000] ipw2200: Firmware error detected.  Restarting.
[4306097.674000] ipw2200: Firmware error detected.  Restarting.
[4306277.572000] ipw2200: Firmware error detected.  Restarting.
[4306386.450000] ipw2200: Firmware error detected.  Restarting.
[4306397.275000] ipw2200: Firmware error detected.  Restarting.
[4306408.154000] ipw2200: Firmware error detected.  Restarting.
[4306420.385000] ipw2200: Firmware error detected.  Restarting.
[4306430.003000] ipw2200: Firmware error detected.  Restarting.
[4306469.111000] ipw2200: Firmware error detected.  Restarting.
[4306524.509000] ipw2200: Firmware error detected.  Restarting.
[4306536.965000] ipw2200: Firmware error detected.  Restarting.
[4306755.556000] ipw2200: Firmware error detected.  Restarting.
[4306758.881000] ipw2200: Firmware error detected.  Restarting.
[4306761.695000] ipw2200: Firmware error detected.  Restarting.
[4306764.477000] ipw2200: Firmware error detected.  Restarting.
[4306777.789000] ipw2200: Firmware error detected.  Restarting.
[4306780.254000] ipw2200: Firmware error detected.  Restarting.
[4306787.101000] ipw2200: Firmware error detected.  Restarting.
[4306787.775000] ipw2200: Firmware error detected.  Restarting.
[4306792.829000] ipw2200: Firmware error detected.  Restarting.
[4306794.780000] ipw2200: Firmware error detected.  Restarting.
[4306807.299000] ipw2200: Firmware error detected.  Restarting.
[4306809.672000] ipw2200: Firmware error detected.  Restarting.
[4306812.582000] ipw2200: Firmware error detected.  Restarting.
[4306815.723000] ipw2200: Firmware error detected.  Restarting.
[4306825.802000] ipw2200: Firmware error detected.  Restarting.
[4306827.752000] ipw2200: Firmware error detected.  Restarting.
[4306843.433000] ipw2200: Firmware error detected.  Restarting.
[4306845.738000] ipw2200: Firmware error detected.  Restarting.
[4306849.521000] ipw2200: Firmware error detected.  Restarting.
[4306868.672000] ipw2200: Firmware error detected.  Restarting.
[4306891.873000] ipw2200: Firmware error detected.  Restarting.
[4306905.442000] ipw2200: Firmware error detected.  Restarting.
[4306913.413000] ipw2200: Firmware error detected.  Restarting.
[4306949.937000] ipw2200: Firmware error detected.  Restarting.
[4306988.389000] ipw2200: Firmware error detected.  Restarting.
[4306995.399000] ipw2200: Firmware error detected.  Restarting.
[4307018.193000] ipw2200: Firmware error detected.  Restarting.
[4307019.665000] ipw2200: Firmware error detected.  Restarting.
[4307024.079000] ipw2200: Firmware error detected.  Restarting.
[4307050.801000] ipw2200: Firmware error detected.  Restarting.
[4307055.824000] ipw2200: Firmware error detected.  Restarting.
[4307127.320000] ipw2200: Firmware error detected.  Restarting.
[4307135.169000] ipw2200: Firmware error detected.  Restarting.
[4307184.358000] ipw2200: Firmware error detected.  Restarting.
[4307187.428000] ipw2200: Firmware error detected.  Restarting.
[4307230.885000] ipw2200: Firmware error detected.  Restarting.
[4307235.587000] ipw2200: Firmware error detected.  Restarting.
[4307246.878000] ipw2200: Firmware error detected.  Restarting.
[4307279.768000] ipw2200: Firmware error detected.  Restarting.
[4307325.016000] ipw2200: Firmware error detected.  Restarting.
[4307348.537000] ipw2200: Firmware error detected.  Restarting.
[4307352.961000] ipw2200: Firmware error detected.  Restarting.
[4307439.371000] ipw2200: Firmware error detected.  Restarting.
[4307469.998000] ipw2200: Firmware error detected.  Restarting.
[4307474.561000] ipw2200: Firmware error detected.  Restarting.
[4307476.817000] ipw2200: Firmware error detected.  Restarting.
[4307480.766000] ipw2200: Firmware error detected.  Restarting.
[4307533.694000] ipw2200: Firmware error detected.  Restarting.
[4307559.716000] ipw2200: Firmware error detected.  Restarting.
[4307598.632000] ipw2200: Firmware error detected.  Restarting.
[4307605.114000] ipw2200: Firmware error detected.  Restarting.
[4307749.198000] ipw2200: Firmware error detected.  Restarting.
[4307751.063000] ipw2200: Firmware error detected.  Restarting.
[4307782.361000] ipw2200: Firmware error detected.  Restarting.
[4307785.239000] ipw2200: Firmware error detected.  Restarting.
[4307787.285000] ipw2200: Firmware error detected.  Restarting.
[4307834.906000] ipw2200: Firmware error detected.  Restarting.
[4307846.630000] ipw2200: Firmware error detected.  Restarting.
[4307964.825000] ipw2200: Firmware error detected.  Restarting.
[4307972.806000] ipw2200: Firmware error detected.  Restarting.
[4307986.650000] ipw2200: Firmware error detected.  Restarting.
[4308112.586000] ipw2200: Firmware error detected.  Restarting.
[4308124.137000] ipw2200: Firmware error detected.  Restarting.
[4308129.081000] ipw2200: Firmware error detected.  Restarting.
[4308151.423000] ipw2200: Firmware error detected.  Restarting.
[4308239.850000] ipw2200: Firmware error detected.  Restarting.
[4308832.703000] cdrom: open failed.
[4309281.542000] ipw2200: Firmware error detected.  Restarting.
[4311665.872000] ipw2200: Firmware error detected.  Restarting.
[4311680.395000] ipw2200: Firmware error detected.  Restarting.
[4313940.418000] ipw2200: Firmware error detected.  Restarting.
[4314455.982000] ipw2200: Firmware error detected.  Restarting.
[4314516.484000] ipw2200: Firmware error detected.  Restarting.
[4314669.593000] ipw2200: Firmware error detected.  Restarting.
[4314825.307000] ipw2200: Firmware error detected.  Restarting.
[4314923.080000] ipw2200: Firmware error detected.  Restarting.
[4314932.593000] ipw2200: Firmware error detected.  Restarting.
[4316598.797000] ipw2200: Firmware error detected.  Restarting.
[4317499.028000] ipw2200: Firmware error detected.  Restarting.
[4317888.003000] usb 4-1: new high speed USB device using ehci_hcd and address 4
[4318563.956000] ipw2200: Firmware error detected.  Restarting.
[4318757.947000] ipw2200: Firmware error detected.  Restarting.
[4318997.837000] usb 4-1: USB disconnect, address 4
[4319059.238000] ipw2200: Firmware error detected.  Restarting.
[4319119.245000] ipw2200: Firmware error detected.  Restarting.
[4320709.342000] ipw2200: Firmware error detected.  Restarting.
[4321147.998000] ipw2200: Firmware error detected.  Restarting.
[4321159.582000] ipw2200: Firmware error detected.  Restarting.
[4321939.123000] ipw2200: Firmware error detected.  Restarting.
[4322095.164000] ipw2200: Firmware error detected.  Restarting.
[4322097.274000] ipw2200: Firmware error detected.  Restarting.
[4322227.147000] ipw2200: Firmware error detected.  Restarting.
[4323617.226000] ipw2200: Firmware error detected.  Restarting.
[4323761.651000] ipw2200: Firmware error detected.  Restarting.
[4323793.909000] ipw2200: Firmware error detected.  Restarting.
[4324268.268000] usb 4-1: new high speed USB device using ehci_hcd and address 5

```

so yeah i guess theres a firmware error, lol

Ubuntu dapper does have support for iw2200 i have it in my computer and it was a bit of a hassle before. but now it's supported completely :) its a wireless network driver

---

### Post by sinaen on 2006-08-15
> **macca87 said:**
> Hey,
i noticed why... i feel dumb ahaha. If anyone wants to know..
every file i deleted off the disk was put into a hidden folder called .trash-[USERNAME], not seen to nautilus but in the term you can see with a ls -a.

Wow.. so does this mean any filesystem i mount and then delete files off contains this folder wasting my valuable space?

not those you remove in the console. :) olny if you use a graphical file-manager. to get rid of the files, they should pop up in the trashcan :)or try to remove them while marking them and ctrl+delete, think it would work to. then it doesnt move the files to the trashcan. 
wierd system according to me. hope the gui file manager would/could in the future separate removable devices like diskettes where

---

### Post by mattbatt on 2006-08-15
It's the lame copy protection I have a T30 and had the same problem.  If the device was a "plays for sure" device that means that it only works with Explorer and the microsoft media player.  check over at the [http://www.misticriver.net/](http://www.misticriver.net/) forums and see if there is a hack for your player.  There is one for my T30.
If not I think I remember someone saying that they could access their player through a linux program used to pull pictures off of a digital camera. I can't remember for sure though.
Good Luck.

---

### Post by sinaen on 2006-08-29
doess anyone know how to do with an iriver ifp-799 that has ums-firmware and needs to reformat whenever i plug it in to make the device
not to be hidden?
it runs on fat16 filesystem

---

### Post by mattbatt on 2006-09-04
Check on the [www.MisticRiver.net](www.MisticRiver.net) page it's more of a iRiver hack than a ubuntu thing.  You could also try opening it up as a camera I know that works for some devices.  I remember reading that at Mistic River too.  Good Luck.
BTW the T30 uses FAT32 so I don't think that matters much.

---

### Post by sinaen on 2006-10-02
the ifp-799 runs fat-16 so every time i plug it in it turned its system to fat-16 hidden :/ hope i have better luck in gnome,than i did in kde :D

---

### Post by nekr0z on 2006-12-23
Hello, guys! I have bought myself a T10 today, it's UMS and everything works just good, but one question remains:

how do I make the player always mount to a separate specified directory, not "usbdisk" like a flasdrive?

---

