---
title: "Acer 5315 Internal Microphone Jaunty"
date: 2009-10-03
forum: Hardware
---

### Post by moebuspcgold on 2009-10-03
I have been tearing my hair out for the last few weeks trying to get the internal mic working on my Acer. At first modifying the /etc/modprobe.d/alsa-base.conf file with various options but there were issues with noise and distortion.
Finally I installed the Realtek Alsa driver for the sound card.  Thanks to         alpho2k blog on ALSA in Ubuntu

Just to clarify:

PC Model: ACER 5313
Sound Card: ALC268 - HDA INTEL
Alsa Version: 1.0.18rc3
O/S: Ubuntu Jaunty 9.04
Issue: No internal Mic.

Go ahead and download the Linux driver from the Realtek download page. Look under high definition codecs.
[http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/)

Download the files to your home directory ~

Open the package and extract the following sub packages to your home directory:
alsa-driver-*
alsa-lib-*
alsa-utils-*


Stop Alsa :

```
 sudo /etc/init.d/alsa-utils stop 
```Install the necessary tools to compile along with the kernel headers:

```
sudo apt-get -y install build-essential ncurses-dev gettext xmlto
sudo apt-get -y install linux-headers-`uname -r`
```Move the three tar files we just extracted to the source code folder:

```
sudo rm -rf /usr/src/alsa
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/alsa* .
```Unpack the 3 tar files :

```
sudo tar xjf alsa-driver*
sudo tar xjf alsa-lib*
sudo tar xjf alsa-utils*
```Compile and install alsa-driver:

```
cd alsa-driver*
sudo ./configure
sudo make
sudo make install
```Compile and install alsa-lib:

```
cd ../alsa-lib*
sudo ./configure
sudo make
sudo make install
```Add some Symbolic links before completing the next stage:

```
sudo ln -s libpanelw.so.5 /usr/lib/libpanelw.so
sudo ln -s libformw.so.5 /usr/lib/libformw.so
sudo ln -s libmenuw.so.5 /usr/lib/libmenuw.so
sudo ln -s libncursesw.so.5 /lib/libncursesw.so
```Compile and install alsa-utils:

```
cd ../alsa-utils*
sudo ./configure
sudo make
sudo make install
```Clean up and remove the 3 tar files in the home folder that are not anymore necessary:

```
rm -f ~/alsa-driver*
rm -f ~/alsa-lib*
rm -f ~/alsa-utils*
```Add the following to the bottom of your alsa-base.conf:
*no need to add anything else at all.
```
sudo gedit /etc/modprobe.d/alsa-base.conf
``````
# ALSA portion
alias char-major-116 snd
alias snd-card-0 snd-xxxx
# OSS/Free portion
alas char-major-14 soundcore
alias sound-slot-0 snd-card-0
# card #1
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

```The final alsa-base.conf should look like this:
```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbi$
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-os$
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mi$
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-mi$
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist sn$
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist sn$
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist sn$

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-al$
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2

# ALSA portion
alias char-major-116 snd
alias snd-card-0 snd-xxxx
# OSS/Free portion
alas char-major-14 soundcore
alias sound-slot-0 snd-card-0
# card #1
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss

```Restart your PC and run the alsaconf sound card config program:

```
sudo alsaconf
```Go to System > Preferences > Sound and change settings to the following:

Everything but capture should be 'Alsa'.
Capture should be 'HDA Intel ALC268 analouge (ALSA)

Remember to run alsamixer and unmute and turn the volume up on everything including 'capture', 'internal mic' and input setting selected as 'mic'.

Now you can test the internal mic on Applications > Sound & Video > Sound Recorder.

Feel free to improve on the posting if you like.

---

### Post by dantakeoff on 2010-01-29
or, alternatively:update your kernal to the most recent, it should work fine. once you have updated, you should find your internal mic if you reboot, right-click the volume control on your panel,click on sound preferences,input,and then microphone 2...do not set your input volume too high, though, or it wont work. you can test it by speaking and watching the input level....mine works best when the input volume is about one third up the meter...
thanks to gunz for that solution....

---

