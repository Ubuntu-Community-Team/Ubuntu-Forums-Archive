---
title: "Broken Intel/RadeonHD Hybrid Graphics &amp; overheating on Samsung Laptop"
date: 2013-03-18
forum: Hardware
---

### Post by rousseau09 on 2013-03-18
I have this laptop and every variant of Ubuntu had the same issue,

[LIST]
[*] General Overheating 
[*] AMD Catalyst not working (means Hybrid Gfx was failing)
[/LIST]
Tried every possible forum posts, advices and nothing solved it. Cant remember how many time I broke my installation and had to roll back everything. Finally solved it. Postng it in the hope that it will help someone else with similar problems. 

**Solution:**

[LIST=1]
[*] Installing Catalyst Manually (from AMD/ATI's site) See [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#GUI](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#GUI) for step by step solution if you want, I've only used the part that's relevant. 
[*] Install the prerequisite packages: 
```
 sudo apt-get install build-essential cdbs dh-make dkms execstack dh-modaliases fakeroot libqtgui4
```
and 
If you are using the x86_64 architecture (64 bit):
```
 sudo apt-get install lib32gcc1 
```
If your /etc/modprobe.d/blacklist-local.conf contains blacklist fglrx make sure you comment out this line by adding a # in front of it. 
[*] Download the latest Catalyst package. This package contains both the 32-bit and 64-bit driver.
```
wget [http://www2.ati.com/drivers/linux/amd-driver-installer-catalyst-12.10-x86.x86_64.zip](http://www2.ati.com/drivers/linux/amd-driver-installer-catalyst-12.10-x86.x86_64.zip)
unzip amd-driver-installer-catalyst-12.10-x86.x86_64.zip
chmod +x amd-driver-installer-catalyst-12.10-x86.x86_64.run

```
[*] Install packages.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.orig
./amd-driver-installer-catalyst-12.10-x86.x86_64.run
```
[*] For Intel/ATI Hybrids, follow GUI Installation and choose the basic one "ATI/AMD proprietary FGLRX graphics driver". Let the install finish and it will ask you to reboot. Do not REBOOT.
[*] Make a backup if you xorg.conf if you haven't done it already.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.orig
```
[*] Generate a new config:
```
sudo amdconfig --initial -f
```
[*] Force use of the new xorg.conf.
```
sudo amdconfig --input=/etc/X11/xorg.conf --tls=1
```
[*] Run the following commands to confim your new settings:
```
fglrxinfo
```
and
```
fgl_glxgears
```
[*] Once all done, Reboot.
[*] Relogin and try the following command to see your Graphics card status:
```
sudo lshw -C display
```
[*] Re-open "Additional Drivers" settings and you will see "ATI/AMD proprietary FGLRX graphics driver" status as "This driver is activated and currently in use". Open "AMD Catalyst Control Center" to see more options. Step 1-12 Solves Intel/ATI Hybrid Graphics issues. *_Go to step 13 ono if you have overheating issue, else Stop, you're done. _*
[*] Install Jupiter Applet. ([http://www.webupd8.org/2010/07/jupiter-ubuntu-ppa-hardware-and-power.html](http://www.webupd8.org/2010/07/jupiter-ubuntu-ppa-hardware-and-power.html)). To add the Jupiter PPA:
```
sudo add-apt-repository ppa:webupd8team/jupiter
sudo apt-get update
```
[*] Install Jupiter (The main Jupiter package)
```
sudo apt-get install jupiter
```
[*] Run Jupiter for the first time and it will configure your laptop as required. Next time you don't have to run this command anymore.
```
sudo jupiter &
```
[/LIST]

More comments, enhancements on this would be appreciated. 

I've tested on my Intel Gen 2/RadeonHD7550 gfx cards on a Samsumg NP530U4B-S01AU Laptop running 12.04LTS. This solved overheating and crashing of AMD Catalyst Control Center. Now my laptop is quieter and running cooler compared to stock Windows 7 it came with. Battery lasting 40% longer.

---

### Post by Yellow Pasque on 2013-03-18
Note that steps 3 and 4 use different versions of Catalyst...(contradicting filenames will make step4 fail).

---

### Post by Yellow Pasque on 2013-03-18
Also, it's unclear how this is different from simply apt-get install fglrx, and whether you've disabled the Intel IGP (normally, installing fglrx breaks the Intel 3D). Don't you have to switch back and forth with amdconfig? Can you run:
```
amdconfig --pxl
```

---

### Post by rousseau09 on 2013-03-18
> **Temüjin said:**
> Note that steps 3 and 4 use different versions of Catalyst...l Fixed. Thank you.

---

### Post by rousseau09 on 2013-03-18
> **Temüjin said:**
> Also, it's unclear how this is different from simply apt-get install fglrx, and whether you've disabled the Intel IGP (normally, installing fglrx breaks the Intel 3D). Don't you have to switch back and forth with amdconfig? Can you run:
```
amdconfig --pxl
```
I manually installed an older version cause new version for some reason didn't work for me. (overheat problem)
Good point, 
```
erased@UNITY:~$ amdconfig --pxl
PowerXpress: Discrete GPU is active (High-Performance mode).
```
My laptop is Muxless. As far I know most new laptops are similar. The discrete card is used solely for rendering, not display. I probably should run amdconfig --px-igpu to see how it behaves... 
```
amdconfig --px-dgpu (currently being used)
amdconfig --px-igpu (for Power-Saving)
```

---

