---
title: "GUIDE TO RUN UBUNTU 12.04 ON AN HP DV6T (up-to-date as of August 12, 2012)"
date: 2012-08-12
forum: Hardware
---

### Post by Dans564 on 2012-08-12
[IMG]http://2.bp.blogspot.com/-b-60R45Qh2c/TX363Hjq0zI/AAAAAAAAC6I/c9ijjipIroQ/s1600/hp-pavilion-dv6.gif[/IMG]

**Things that don't work out of the box:**

1) Wifi after suspend

2) Switchable graphics

3) Screen brightness control

4) Full Beats&#8482; audio experience

**How to fix them:**[INDENT]**1) to make the wifi work:**[INDENT]```
sudo nano /etc/modprobe.d/iwlwifi.conf
```and paste  this 
```
options iwlwifi bt_coex_active=N
```save, close, and  reboot.  Wifi now works after suspend![/INDENT]**2) to make switchable graphics work:**[INDENT]Install the prerequisite packages: 
```
sudo apt-get install build-essential cdbs dh-make dkms execstack dh-modaliases fakeroot libqtgui4
```*If you are using the x86_64 architecture (64 bit)*: 

```

sudo apt-get install ia32-libs-multiarch:i386 lib32gcc1 libc6-i386 
sudo apt-get install ia32-libs 
cd /usr ; sudo ln -svT lib /usr/lib64 
```Download the latest Catalyst package (includes 32-bit and 64-bit)
```
cd ~/; mkdir catalyst[12.6]("http://wiki.cchtml.com/index.php/12.6"); cd catalyst[12.6]("http://wiki.cchtml.com/index.php/12.6")/ 
wget [http://www2.ati.com/drivers/linux/amd-driver-installer-](http://www2.ati.com/drivers/linux/amd-driver-installer-)[12-6]("http://wiki.cchtml.com/index.php/12-6")-x86.x86_64.run 
chmod +x amd-driver-installer-[12-6]("http://wiki.cchtml.com/index.php/12-6")-x86.x86_64.run
```Create and install the .deb packages
```
sudo sh ./amd-driver-installer-[12-6]("http://wiki.cchtml.com/index.php/12-6")-x86.x86_64.run --buildpkg Ubuntu/precise 
sudo dpkg -i fglrx*.deb
```Generate a generic xorg.conf
```
sudo amdconfig --initial -f 
```[FONT=Arial][SIZE=2]Open the /etc/X11/Xsession.d/10fglrx file with root rights :
```
gksu gedit /etc/X11/Xsession.d/10fglrx
```If you're using a 32bits system add at the end of 4th line this text : *"/usr/lib32/dri/*" without the quotes. The file should now look like this :
```
 LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri 
if [ `uname -m` = 'x86_64' ]; then 
if [ -d /usr/lib32/fglrx/dri ]; then 
LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri:/usr/lib32/dri
if [ ! -z $LD_LIBRARY_PATH ]; then 
LD_LIBRARY_PATH=$LD_LIBRARY_PATH: 
fi 
LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib32 
export LD_LIBRARY_PATH 
fi 
fi 
export LIBGL_DRIVERS_PATH
```If you're using a 64bits system add at the end of 4th line this text : *"/usr/lib/x86_64-linux-gnu/dri/*" without the quotes. The file should now look like this :
```
 LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri 
if [ `uname -m` = 'x86_64' ]; then 
if [ -d /usr/lib32/fglrx/dri ]; then 
LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri:/usr/lib/x86_64-linux-gnu/dri
if [ ! -z $LD_LIBRARY_PATH ]; then 
LD_LIBRARY_PATH=$LD_LIBRARY_PATH: 
fi 
LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib32
export LD_LIBRARY_PATH 
fi 
fi 
export LIBGL_DRIVERS_PATH
```Now save the file[/SIZE][/FONT]
**DO NOT LET UPDATE MANAGER UPDATE YOUR FLGRX DRIVER.**    You can  elect to "lock" the packages using the synaptic package manager  (available in the Software Center) to prevent them from showing up in  updates.[/INDENT]**3) How to gain control of screen brightness**
[/INDENT][INDENT][INDENT]1) Edit the GRUB2 boot parameters in /etc/default/grub to 

add acpi_vendor=backlight , as follows:

```
GRUB_CMDLINE_LINUX_DEFAULT="splash acpi_backlight=vendor"
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```2) Update GRUB configuration:
```
sudo update-grub
```3) reboot

[/INDENT]**4) How to gain a full Beats&#8482; audio experience**[INDENT]```
[COLOR=black]gksu gedit /etc/[/COLOR][COLOR=black][FONT=Arial]modprobe.d/alsa-base.conf[/FONT][/COLOR]
```and add the following line to the bottom
```
[COLOR=Black][FONT=Arial]options snd-hda-intel model=ref[/FONT][/COLOR]
```[/INDENT][/INDENT]Hope this short tutorial helps some fellow dv6t owners enjoy 12.04!

---

### Post by Dy1anW on 2012-08-13
Thanks for this. I have a brand new dv7 and 'suffer' similar problems, with the exception that I'm using nvidia rather than ati. Will try these out when I get back.

Edit:
Oh, btw, you wouldn't happen to know how to get the gesturepad to recognise gestures?

---

### Post by vasanth on 2012-09-03
Hi,

Fingerprint reader and Webcam are working for you out of the box?

---

### Post by Dans564 on 2012-09-03
webcam yes.  Finger Print reader no, the manufacturer never released a linux driver.

---

### Post by kapad on 2012-09-26
Hi, 

Thanks for the post. I am using an HP ENVY ultrabook 4-1002TX. 

The only thing that I haven't been able to get working is the sound. I tried using your method and added the line in alsa_base.conf. 

The sound started, but it was so soft that I am sure it not playing from the beats audio speakers (its much louder on windows). And maybe using some internal speaker that plays the bios beeps. Or just some other problem all together. 

Any suggestions?

output from ```
lspci | grep Audio
``` is

> 00:1b.0 Audio device: Inter Corporation Panther Point High Definition Audio Controller (rev 04)

---

### Post by LeapingLlama on 2012-09-27
Thanks for this awesome post! I especially appreciate being able to control my brightness.

I have encountered one issue, however. I installed the fglrx drivers quite successfully, as per your instructions (but using driver 12.8 instead of 12.6), but every time I use the Catalyst Control Center to switch to integrated graphics, after my next reboot, Unity fails to start. When I login, I can still see my desktop wallpaper and a movable mouse, but am unable to open a terminal using Ctrl+Alt+T or Alt+F2. Fortunately I was able to use [FONT="Courier New"]sudo aticonfig --px-dgpu[/FONT] to switch back to my discrete card, and after a reboot, everything is fine again. So my question/problem is, how do I switch to the integrated graphics without any problems?

Thanks again for your awesome guide!

---

### Post by Dgordon8765 on 2012-11-13
I have every step for #2 (at least I think I have). However, when I go to the catalyst control center to turn on the better graphics card, it says to restart the computer. I do, and the change is never made. It seems I can't get the switchable graphics to work. I also cannot get an external monitor to work.

I had already run some of these commands and installed catalyst (same version) before I saw this thread. 

Does it matter if I do the same commands more than once?

---

