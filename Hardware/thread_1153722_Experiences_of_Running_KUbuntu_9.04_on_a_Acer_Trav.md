---
title: "Experiences of Running KUbuntu 9.04 on a Acer Travelmate C312XMi"
date: 2009-05-09
forum: Hardware
---

### Post by black_shadow on 2009-05-09
I am writing this help guide / tutorial as I have found it not easy to find the information to install KUbuntu on an Acer TravelMate C312XMi.

1) Getting the Touch Screen and Stylus fully working, after doing a standard install of KUbuntu the touch screen works but only the tip / eraser of the stylus works.

a) First we need to download the newest linux wacom release,

```
cd ./Desktop
wget http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.3-3.tar.bz2
```b) Next install the needed libraries, packages and updates using the following apt-get commands.

```
sudo apt-get update
sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev wacom-tools tcl8.4-dev libncurses5-dev
sudo apt-get upgrade
```c) 3) Now the kernel headers for your kernel are needed. To determine your kernel version:

```
uname -r
```If you have the generic kernel:

```
sudo apt-get install linux-headers-generic
```If you have the rt kernel:

```
sudo apt-get install linux-headers-rt
```(Remember if you update to a newer kernel, then the module won't work on restart because the module is compiled for a specific kernel. You will have to recompile the module for the newer kernel.)

d) Okay now unpack the source code tar and go into the unpacked source code directory.

```

tar xjvf linuxwacom-0.8.3-3.tar.bz2
cd linuxwacom-0.8.3-3
```e) Then we compile the module.

```
./configure --enable-wacom
make
```*****We DO NOT run "sudo make install" since we only want the module.*****

f) Next we copy the module to the appropriate directory:

```
sudo cp ./src/2.6.28/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```g) This is the fdi file I have used located in /usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi

```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
   <match key="input.originating_device" contains="if0">
      <match key="info.product" contains="Wacom">
    <merge key="input.x11_driver" type="string">wacom</merge>
    <merge key="input.x11_options.Type" type="string">stylus</merge>
        <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
        <append key="wacom.types" type="strlist">eraser</append>
        <append key="wacom.types" type="strlist">cursor</append>
        <append key="wacom.types" type="strlist">pad</append>
      </match>

      <match key="info.product" contains="WALTOP">
    <merge key="input.x11_driver" type="string">wacom</merge>
    <merge key="input.x11_options.Type" type="string">stylus</merge>
        <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
        <append key="wacom.types" type="strlist">eraser</append>
        <append key="wacom.types" type="strlist">cursor</append>
        <append key="wacom.types" type="strlist">pad</append>
      </match>
    </match>
    <match key="info.capabilities" contains="serial">
      <match key="@info.parent:pnp.id" contains_outof="WACf001;WACf002;WACf003;WACf004;WACf005;WACf006;WACf007;WACf008;WACf009;WACf00a;WACf00b;WACf00c;FUJ02e5">
        <append key="info.capabilities" type="strlist">input</append>
        <merge key="input.x11_driver" type="string">wacom</merge>
        <merge key="input.x11_options.Type" type="string">stylus</merge>
        <merge key="input.x11_options.ForceDevice" type="string">ISDV4</merge>
        <merge key="input.device" type="copy_property">serial.device</merge>
        <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
        <append key="wacom.types" type="strlist">eraser</append>
        <match key="@info.parent:pnp.id" contains_outof="WACf008;WACf009">
          <!-- Serial tablets with touch capabilities -->
          <append key="wacom.types" type="strlist">touch</append>
        </match>
      </match>
    </match>
    <!-- N-Trig Duosense Electromagnetic Digitizer -->
    <match key="info.product" contains="HID 1b96:0001">
      <match key="info.parent" contains="if0">
       <merge key="input.x11_driver" type="string">wacom</merge>
       <merge key="input.x11_options.Type" type="string">stylus</merge>
      </match>
    </match>
  </device>
  <!-- Match the Wacom Bluetooth A5 pen tablet -->
  <device>
    <match key="info.capabilities" contains="input.mouse">
      <match key="info.product" contains="WACOM">
        <match key="info.product" contains="Tablet">
          <merge key="input.x11_driver" type="string">wacom</merge>
          <merge key="input.x11_options.Type" type="string">stylus</merge>
          <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
          <append key="wacom.types" type="strlist">eraser</append>
          <append key="wacom.types" type="strlist">cursor</append>
        </match>
      </match>
    </match>
  </device>
</deviceinfo>
```h) The names that the FDI creates need to be translated to what wacamcp will read.

```
sudo nano /etc/init.d/wacom-names
```Copy and paste the following script into the empty file.  Save and close.  

```
# wacom-names script by Roger E. Critchlow, Jr. (4-12-09)
#   modified by gali98/Favux (4-14-09)
#
# Place the wacom-names script in  /etc/init.d/wacom-names and link it as
# /etc/rc{2,3,4,5}.d/S27wacom-names.
# Use "sudo update-rc.d wacom start 27 2 3 4 5 ." or "sudo update-rc.d wacom defaults 27".
# Using S27 starts the script after hal and before gdm.  This allows us to modify the hal
# properties before the xserver sees them for the first time.
#
# The script renames the input devices back to what wacomcpl and xsetwacom expect them to
# be, so rotation and interactive calibration work.  It also enables xorg.conf & .xinitrc
# style configuration of Wacom features like the stylus button(s) and calibration.
#
# The script needs to be executable.  chmod +x wacom-names

#! /bin/sh
## find any wacom devices
for udi in `hal-find-by-property --key input.x11_driver --string wacom`
do
type=`hal-get-property --udi $udi --key input.x11_options.Type`
## rewrite the names that the Xserver will use
hal-set-property --udi $udi --key info.product --string $type
#
## To add a xorg.conf or xsetwacom (.xinitrc) style configuration, say mapping a stylus
## button, you could add to the script:
#case $type in
#stylus|eraser)
## eg:  map stylus button 2 to mouse button 3 (right click)
#hal-set-property --udi $udi --key input.x11_options.Button2 --string 3
#
#;;
#esac
done
```To make the script executable:

```
sudo chmod +x /etc/init.d/wacom-names
```To link the script to the appropriate run-levels (2 3 4 5):

```
sudo update-rc.d wacom-names defaults 27
```h) Wacomcpl and settings

After you have rebooted, you should be able to run the command wacomcpl. This will bring up a dialog that will allow you to configure your tablet, calibrate it and change which buttons do what. After you exit wacomcpl, your settings are saved to a file in your home folder named .xinitrc.

2) To add the buttons on the screen to rotate the display and stylus. (To Be added in the next couple of days)

a) My Rotate scripts :-

script for general rotating of screen
```
if [ -f /home/mjruff/screen-rotation ] ; then
    ROTATION=`cat /home/mjruff/screen-rotation`
else
    echo normal > /home/mjruff/screen-rotation
    ROTATION=normal
fi

echo normal > /home/mjruff/screen-slate

case "$ROTATION" in
    normal)
        echo right > /home/mjruff/screen-rotation    
        xrandr -o right
        xsetwacom set "stylus" Rotate CW
        xsetwacom set "eraser" Rotate CW
        cellwriter
    ;;
    right)
        echo inverted > /home/mjruff/screen-rotation
        xrandr -o inverted
        xsetwacom set "stylus" Rotate half
        xsetwacom set "eraser" Rotate half
    ;;
    inverted)
        echo left > /home/mjruff/screen-rotation
        xrandr -o left
        xsetwacom set "stylus" Rotate CCW
        xsetwacom set "eraser" Rotate CCW
    ;;
    left)
        echo normal > /home/mjruff/screen-rotation
        xrandr -o normal
        xsetwacom set "stylus" Rotate NONE
        xsetwacom set "eraser" Rotate NONE
        killall cellwriter
    ;;

esac
```Script for inverting screen more work needed on it
```
if [ -f /home/mjruff/screen-slate ] ; then
    ROTATION=`cat /home/mjruff/screen-slate`
else
    echo normal > /home/mjruff/screen-slate
    ROTATION=normal
fi

echo normal > /home/mjruff/screen-rotation

case "$ROTATION" in
    normal)
        echo inverted > /home/mjruff/screen-slate    
        xrandr -o inverted
        xsetwacom set "stylus" Rotate half
        xsetwacom set "eraser" Rotate half
        cellwriter
    ;;
    inverted)
        echo normal > /home/mjruff/screen-slate
        xrandr -o normal
        xsetwacom set "stylus" Rotate none
        xsetwacom set "eraser" Rotate none
        killall cellwriter
    ;;
esac
```

---

