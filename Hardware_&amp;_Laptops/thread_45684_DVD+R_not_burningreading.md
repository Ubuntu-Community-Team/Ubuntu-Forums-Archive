---
title: "DVD+R not burning/reading"
date: 2005-07-01
forum: Hardware &amp; Laptops
---

### Post by robbie1 on 2005-07-01
I have been useing Gnomebaker/growisofs/Graveman to burn DVD+Rs which seems to burn correctly (visible on the dvd) but when trying to mount one I just burnt I get the following error:

Quote:
Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.

mount: wrong fs type, bad option, bad superbloack on /dev/hdc missing codepage or other error


When using growisofs I get:

/dev/hdc: "Current Write Speed" is 8.2x1385KBps.
the LUN appears to be stuck writing LBA=310h, retry in 70ms
the LUN appears to be stuck writing LBA=310h, retry in 70ms

And the dvd is unreadable.

Is there anything I have to do to enable DVD burning? Device manager lists the device as "PIONEER DVD-RW DVR-109" and it is +/- compatible. I have installed NeroLinux which burns readable DVD+Rs successfully, but I want to get this working using GPLed/free tools.

Cheers,

rob

Below is a tail of my dmesg:

UDF-fs: No VRS found
ISO 9660 Extensions: Microsoft Joliet Level 3
ISO 9660 Extensions: RRIP_1991A
UDF-fs: No VRS found
ISO 9660 Extensions: Microsoft Joliet Level 3
ISO 9660 Extensions: RRIP_1991A
UDF-fs: No VRS found
ISO 9660 Extensions: Microsoft Joliet Level 3
ISO 9660 Extensions: RRIP_1991A
eth0: no IPv6 routers present
eth0: no IPv6 routers present
agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
UDF-fs: No VRS found
ISO 9660 Extensions: Microsoft Joliet Level 3
ISO 9660 Extensions: RRIP_1991A
cdrom: This disc doesn't have any tracks I recognize!
cdrom: This disc doesn't have any tracks I recognize!
attempt to access beyond end of device
hdc: rw=0, want=68, limit=4
attempt to access beyond end of device
hdc: rw=0, want=8294400, limit=4
attempt to access beyond end of device
hdc: rw=0, want=8293376, limit=4
attempt to access beyond end of device
hdc: rw=0, want=8293152, limit=4
attempt to access beyond end of device
hdc: rw=0, want=8294392, limit=4
attempt to access beyond end of device
hdc: rw=0, want=8293368, limit=4
attempt to access beyond end of device
hdc: rw=0, want=8293144, limit=4
attempt to access beyond end of device
hdc: rw=0, want=8293800, limit=4
attempt to access beyond end of device
hdc: rw=0, want=8292776, limit=4
attempt to access beyond end of device
hdc: rw=0, want=8292552, limit=4
attempt to access beyond end of device
hdc: rw=0, want=8293792, limit=4
attempt to access beyond end of device
hdc: rw=0, want=8292768, limit=4
attempt to access beyond end of device
hdc: rw=0, want=8292544, limit=4
attempt to access beyond end of device
hdc: rw=0, want=6805668, limit=4
attempt to access beyond end of device
hdc: rw=0, want=6804644, limit=4
attempt to access beyond end of device
hdc: rw=0, want=6804420, limit=4
attempt to access beyond end of device
hdc: rw=0, want=6805660, limit=4
attempt to access beyond end of device
hdc: rw=0, want=6804636, limit=4
attempt to access beyond end of device
hdc: rw=0, want=6804412, limit=4
attempt to access beyond end of device
hdc: rw=0, want=6805068, limit=4
attempt to access beyond end of device
hdc: rw=0, want=6804044, limit=4
attempt to access beyond end of device
hdc: rw=0, want=6803820, limit=4
attempt to access beyond end of device
hdc: rw=0, want=6805060, limit=4
attempt to access beyond end of device
hdc: rw=0, want=6804036, limit=4
attempt to access beyond end of device
hdc: rw=0, want=6803812, limit=4
attempt to access beyond end of device
hdc: rw=0, want=1252, limit=4
attempt to access beyond end of device
hdc: rw=0, want=1028, limit=4
UDF-fs: No partition found (1)
attempt to access beyond end of device
hdc: rw=0, want=68, limit=4
isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
cdrom: This disc doesn't have any tracks I recognize!

---

### Post by kassetra on 2005-09-01
Ok.  This particular drive is a great drive - however, there are some firmware issues with it in linux.

** First - some bad news:**
Any firmware revision before 1.58 prevents the drive from burning any dvd under growisofs (what gnomebaker and many other burning applications use.) - ESPECIALLY DVD+R media.

Reading a DVD+R disc requires a minimum firmware version of 1.40 -- and the correct "lead-in" information (which can change per dvd drive manufacturer.)

The firmware upgrades are given in either windows only or floppy-disk required formats.

The growisofs command that gnomebaker uses is incompatible with this drive.

** Now, some good news:**
You can upgrade the firmware using linux.
You can burn DVD+R media with the upgraded firmware, using the growisofs command in a terminal (it's fairly straightforward and mostly easy to understand.) -- one caveat to this is that the DVD+R that you burn may not work in older drives (say, a non-firmware-updated drive that's a year old.)

** Ok, now that you've read the good and the bad - here comes the ugly:**
How to flash the firmware of your DVR-109 drive (***NOT FOR THE NEW LINUX USER!!***)
1. You need this utility: [DVRFlash]("http://lasvegas.rpc1.org/DVRFlash_v2.1.zip")
2. You need to determine your EXACT DVR-109 model & firmware version by typing this in a terminal:
 ```
cdrecord dev=ATAPI -scanbus
``` 
Here is what mine looks like (now, after I flashed the drive.)
```
scsibus0:
	    0,0,0	 0) 'PIONEER ' 'DVD-RW  DVR-109 ' '1.58' Removable CD-ROM
```
My drive is a basic DVR-109 (BK, because mine is a black drive.)
My firmware version is '1.58'  (It was 1.40 before I upgraded.)

3. Now, you need to get the right firmware upgrade from [Pioneer]("http://wwwbsc.pioneer.co.jp/product-e/ibs/device_e/dev00001r_e.html") - in the first [color=MediumTurquoise]**CYAN colored box**[/color] it says ATAPI and then Drive right under it (in a light blue). Under "Drive" are two options - mine is a plain DVR-109 (BK) - the beige color would be DVR-109. If you have a european version or a "name-branded" version that came with your computer, most likely you do not want the DVR-109 firmware (match the drive model that you just found out with the cdrecord command). 

Over just to the right of the Drive list is the area to download the firmware. Click the DOWNLOAD button on the correct row to get your firmware. 
***(NOTICE! This is an EXE file - which means you'll need access to wine, vmware, cedega, crossover, or a real winxp box in order to uncompress the firmware files out of it.)***

Ok, with the firmware EXE and the DVRFlash utility, we can go on to the next steps - but first, some warnings - because this is NOT something to do without a lot of thought.
 

[b][color=Red]DO NOT flash your drive during a storm or during any time when the power could go out even for a nanosecond, YOU WILL DESTROY YOUR DRIVE.

[/color][/b][b][color=Red]IF THE DRIVE LOSES POWER WHILE FLASHING - IT WILL NEVER WORK AGAIN. Make sure your drive is on a good power supply and securely plugged in.

[/color][/b][b][color=Red] DO NOT DO ANYTHING on your computer, don't even move the mouse during the actual flashing process. YOU COULD DESTROY YOUR DRIVE.

[/color][/b][b][color=Red] DO NOT CAUSE ANY VIBRATIONS while flashing your drive.  YOU WILL MOST LIKELY DESTROY YOUR DRIVE.

[/color][/b]**[color=Red] DO NOT have ANYTHING IN THE DRIVE while you flash - YOU WILL DESTROY YOUR DRIVE.[/color]**
 
[b][color=Red] ANY GLITCH WHATSOEVER COULD EASILY CAUSE YOUR DRIVE TO NEVER WORK AGAIN, AT ALL, PERIOD.

EVEN USING THE UPGRADE FILES FROM PIONEER DIRECTLY IS NOT A GUARANTEE THAT YOUR DRIVE WON'T BE DESTROYED AFTER UPGRADING.

EVEN IF EVERYTHING GOES "CORRECTLY" YOUR DRIVE *STILL* COULD BE DESTROYED (but that's a bit smaller chance.)


[/color][/b] Hopefully you understand that flashing the firmware on your drive is not the time to have a party and be dancing around.  

Ok, with the obligatory warnings out of the way, let's flash your drive.

1. Unpack the EXE file by running it in some kind of windows xp or fake windows environment. When it asks you for a directory to unpack, locate your desktop. After it extracts three files it will ask if you want to flash your drive - JUST SAY NO! Ok, actually, just cancel the flashing utility. We just needed the files. (IF YOU DO TRY TO FLASH YOUR DRIVE THIS WAY - YOU WILL MOST LIKELY DESTROY YOUR DRIVE COMPLETELY.)
 
You should have one UPGR109.EXE file and two files with a . and then a revision number ( as of this writing, it was .158 ) - you can safely remove the extracted UPGR109.EXE file. TAKE NOTE of the two remaining file names - one should have four zeros in the middle of the name, and the other will not. You will need to have them in the correct order later!

2. Open the DVRFlash zip file, and navigate to the linux version (as of this writing, it's /DVRFash_v2.1/linux-x86/)

3. Extract the DVRFlash utility to your desktop.

4. Ok, remove ANY media that's in your drive.

5. Open a terminal, change to your desktop directory.  (Usually, cd /home/YOUR_NAME/Desktop)

6. All right.  BREATHE VERY DEEPLY.  The command to flash your drive works like this:
 ```
sudo ./DVRFlash -vf /dev/YOUR_DEVICE_HERE R##0000#.### R##00#0#.###
``` 
Notice that the file with four zeros goes FIRST.  If you didn't know your device, you could look in /etc/fstab.
Ok, so as of this writing, the two files I used were R9100009.158 and R9100109.158 - and you've stated that your device is /dev/hdc - so your command would look like this:
 ```
sudo ./DVRFlash -vf /dev/hdc R9100009.158 R9100109.158
``` 
You will be required to answer "y" to a couple of questions as it starts to flash the drive. BE VERY CALM - IT CAN TAKE UP TO FIVE WHOLE MINUTES to finish flashing your drive.

If EVERYTHING WENT FINE - it will tell you that the firmware upgrade was successful. If not... you most likely have a dead drive. You can check your drive AFTER the flashing procedure is over by typing:
 ```
cdrecord dev=ATAPI -scanbus
``` 
it SHOULD report the drive back to you WITH AN UPGRADED FIRMWARE VERSION.

Now that you've upgraded your firmware, you can write DVD+R data files from the terminal with this command (can also be used to write non-data dvds):
```
sudo growisofs -use-the-force-luke=dao -speed=2 -dvd-compat -Z /dev/hdc=filename.iso
``` OR this command (this command will ONLY write a data dvd):
```
sudo growisofs -use-the-force-luke=dao -speed=2 -dvd-compat -Z /dev/hdc /path/to/a/directory/conaining/files/you/want/to/write
```

-- 
The firmware upgrade will fix reading of MOST dvd+r media, as well as burning from the command line. Using a nice gui to burn your dvd+r media may not work, however, because the 1.58 firmware [STILL HAS AN INCOMPATIBILITY]("http://lists.debian.org/cdwrite/2005/04/msg00016.html") with the growisofs command (essentially, burning anything greater than ROUGHLY 1000 Mb stalls the drive burning indefinitely, which never "finishes" the dvd.)

I hope this helps you.  (Even though it's most likely NOT the answer you wanted to hear.)

---

### Post by Agio on 2006-08-26
Hi, when I write (C&P) the comand "cdrecord dev=ATAPI -scanbus" I get the output for two drives, a cd-rw and dvd ro drive, but not for the DVD-RW. The DVD-RW is with the HDD on another IDE as slave.
0,0,0     0) 'SONY    ' 'CD-RW  CRX175A1 ' '5YS2' Removable CD-ROM
        0,1,0     1) 'PLEXTOR ' 'DVD-ROM PX-116A2' '1.00' Removable CD-ROM
        0,2,0     2) *

Any help is very apreciated, I'm having trouble with this drive.
P.S.: Sorry for "undigging" an old post =\

---

