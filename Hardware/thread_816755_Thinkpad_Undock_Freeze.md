---
title: "Thinkpad Undock Freeze"
date: 2008-06-03
forum: Hardware
---

### Post by MikeKnoop on 2008-06-03
Hey all,

I had this problem a few weeks back: Whenever my IBM x60s would undock in the new Hardy Heron (8.04), *and* the machine was booted up WHILE docked, the machine would completely freeze up when I attempted to undock it.

I wrote a script that I execute just before undocking. It identifies which scsi_device is assigned to the CD-ROM drive and removes it. In addition, the script also will re-add the device when run a second time.

Caution with the scripts... I am new to BASH scripting and I had some permission issues removing and adding the scsi_device. I beleive my two script system will work (it works on my system when run through the GUI [nautilus] and selecting "Run in terminal"), however I am sure there is a more optimized way to do this. If you have suggestions please post a reply.

The script works by running through the first 20 (modifiable) possible scsi_device folders and if it exists, checks the vendor file to match it up with the CD-ROM vendor. The vendor ID on my x60s Ultrabay x6 is listed as "HL-DT-ST". I suspect this may vary from docking station to docking station. When it finds the device, it stores the device number in a variable file in the same path as the script file, then removes the appropriate scsi_device. Executing the script a 2nd time uses the variable file to rescan the host on the correct device and re-add it.

**toggle_cd.sh**
```
#!/bin/bash

script_path=`dirname $0`

sudo $script_path/toggle_cd_cmd.sh
```


**toggle_cd_cmd.sh**
```
#!/bin/bash

script_path=`dirname $0`
counter=0
if [ -e $script_path/toggle_cd_var ]; then
	echo 0 0 0 > /sys/class/scsi_host/host`cat $script_path/toggle_cd_var`/scan
	echo "Mounted CD-ROM drive on device `cat $script_path/toggle_cd_var`:0:0:0"
	rm $script_path/toggle_cd_var
else
	while [ $counter -lt 20 ]; do
			directory="/sys/class/scsi_device/$counter:0:0:0/"
		if [ -d $directory ]; then
			if [ "`cat /sys/class/scsi_device/$counter:0:0:0/device/vendor`" = "HL-DT-ST" ]; then
				echo 1 > /sys/class/scsi_device/$counter:0:0:0/device/delete
				echo "Unmounted CD-ROM drive on device $counter:0:0:0"
				echo "$counter" > $script_path/toggle_cd_var
			fi
		fi
		let counter=counter+1
	done
fi
```


The correct sequence of events would be to run the "toggle_cd.sh" file in the terminal, then undock your machine. Later when you re-dock, run the "toggle_cd.sh" file again and your CD-ROM will be re-added.


Thanks,
-Mike

---

### Post by roffik on 2008-07-08
Your script doesn't work, but it helped me, thanks!
I have Thinkpad T40, and Ubuntu 8.04. It freezes when I pull my UltraBay device. I need to log in as a root and execute this command:
```
echo 1 > /sys/class/scsi_device/1:0:0:0/device/delete
```
Now I'm able to pull it out without effort. When I plug it again, it works fine. So the only problem is, how to automatize executing that command. Any ideas?

---

### Post by mini_g on 2008-07-24
[This might be able to help you]("http://www.thinkwiki.org/wiki/How_to_hotswap_the_UltraBase") Mike. The only downside to this is that it seems that the kernel will need to be recompiled.

---

### Post by roffik on 2008-11-02
Oh yeah! Works like a charm in Intrepid! No configuration needed nor command from my previous post.

---

