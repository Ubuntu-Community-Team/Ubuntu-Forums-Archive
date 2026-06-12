---
title: "[r-pi v4] 3.5&quot; Touchscreen for Raspberry Pi 4B"
date: 2021-02-18
forum: Hardware
---

### Post by cyrus-panesri on 2021-02-18
I'm having some trouble getting my Pi 4B running 20.10 to recognise and display on a 3.5" Touchscreen. Any help would be appreciated. Apologies if this one runs a bit long...

The Hardware:
[LIST]
[*]Raspberry Pi 4B 8GB
[*][Joy-IT 3.5" Touchscreen]("https://joy-it.net/en/products/RB-TFT3.5")
[*]HP 2229h HDMI Monitor
[/LIST]

The Software:
[LIST]
[*]Ubuntu 20.10 Desktop (Imaged onto SD card with Raspberry Pi Imager for Linux).
[*]All software including the Pi's eeprom has been updated to the latest levels as of 18/02/2021.
[/LIST]

The Setup:
[LIST]
[*]The Pi 4 tries to boot off USB and then the SD card (i.e. 0xf14) - this is intentional.
[*]The 3.5" Touchscreen is connected using GPIO module (pins 1-26).
[*]The HP monitor is connected using HDMI0 and a micro to regular converter.
[/LIST]
 
The Dream:
[LIST]
[*]I would like to use the Pi with both the 3.5" Touchscreen as well as the HDMI monitor simultaneously.
[*]As the primary use case in this instance requires the Pi to be portable, I need to be able to boot into 20.10 on the 3.5" TouchScreen but then also 'hot-plug' the HDMI monitor when necessary.
[/LIST]

The Stepping Stones:
[LIST]
[*]Firstly, I tried using the instructions on the Manufacturer's [website]("https://joy-it.net/files/files/Produkte/RB-TFT3.5/RB-TFT-Manual_04082020.pdf"). Initially this didn't work out as the locations of the config.txt and cmdline.txt files as well as the Overlays folder for the .dtbo are different in 20.10 viz. /boot/firmware/.
[*]Even after adapting the instructions to match the correct locations and syntax for the Pi 4 (e.g. referencing HDMI with ':0'), when I booted up (as specified in the instructions, this would be the first time it requests a reboot) the Pi, it got past POST on the HP Monitor but after the spinning logo disappeared, it hung on the black screen with Ubuntu plastered across the bottom. The 3.5" Touchscreen remained blank white throughout this process.
[/LIST]


[LIST]
[*]Next, I contacted the Manufacturer and they directed me to use [these instructions from LCDwiki]("http://www.lcdwiki.com/3.5inch_RPi_Display"). Again this involved manually running through the commands detailed in the provided script and making modifications where necessary to match the correct paths for 20.10.
[*]The result was more or less the same again with the only difference being that the Pi got past POST and hung on a plain black screen before the logo appeared. Again, the 3.5" Touchscreen remained blank white throughout this process.
[/LIST]


[LIST]
[*]Finally, I tried an amalgamation of both the above methods, and as an added measure, continued on to install and configure fbcp and now the HP monitor seems to work fine but the Touchscreen is still in the same situation, remaining a blank white screen.
[/LIST]

I'm aware that there are similar 3.5" Touchscreens out there but has anyone actually managed to get one working with Ubuntu 20.10 desktop. All the results I get when searching pertain to Raspbian in some form or the other.

I'm attaching my config, cmdline, 99-calibration and 99-fbturbo files for reference.

config.txt
```

[pi4]max_framebuffers=2


[all]
arm_64bit=1
kernel=vmlinuz
cmdline=cmdline.txt
initramfs initrd.img followkernel


# Enable the audio output, I2C and SPI interfaces on the GPIO header
dtparam=audio=on
dtparam=i2c_arm=on
dtparam=spi=on


# Enable the FKMS ("Fake" KMS) graphics overlay, enable the camera firmware
# and allocate 128Mb to the GPU memory
#dtoverlay=vc4-fkms-v3d
gpu_mem=128
start_x=1


# Comment out the following line if the edges of the desktop appear outside
# the edges of your display
disable_overscan=1


# If you have issues with audio, you may try uncommenting the following line
# which forces the HDMI output into HDMI mode instead of DVI (which doesn't
# support audio output)
#hdmi_drive=2


# If you have a CM4, uncomment the following line to enable the USB2 outputs
# on the IO board (assuming your CM4 is plugged into such a board)
#dtoverlay=dwc2,dr_mode=host
hdmi_force_hotplug:0=1
enable_uart=1
dtoverlay=tft35a:rotate=270
max_usb_current=1
config_hdmi_boost=7
hdmi_drive:0=1
hdmi_ignore_edid:0=0xa5000080
hdmi_group:0=2
hdmi_mode:0=58

```

cmdline.txt
```

dwc_otg.lpm_enable=0 console=tty1 console=ttyAMA0,115200 root=LABEL=writable rootfstype=ext4 elevator=deadline rootwait fbcon=map:10 fbcon=font:ProFont6x11 fixrtc quiet splash 

```

99-calibration.conf
```

Section "InputClass"
    Identifier "calibration"
    MatchProduct "ADS7846 Touchscreen"
    Option "Calibration" "160 3723 3896 181"
    Option "SwapAxes" "0"
EndSection

```

99-fbturbo.conf
```

Section "Device"
        Identifier      "Allwinner A10/A13/A20 FBDEV"
        Driver          "fbturbo"
        Option          "fbdev" "/dev/fb0"


        Option          "SwapbuffersWait" "true"
EndSection

```

Any help would be appreciated - even if you're just going to point me in the right direction. Thanks for taking the time to slog through this...

---

