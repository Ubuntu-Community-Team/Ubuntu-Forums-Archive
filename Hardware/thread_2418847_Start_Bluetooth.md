---
title: "Start Bluetooth"
date: 2019-05-12
forum: Hardware
---

### Post by capemayal on 2019-05-12
I have upgraded to 19.04 with a fresh install.

Why can't the bluetooth problem be solved?

The last time it worked consistently was in 16.04 with 4.15 kernel.

Al

---

### Post by #&amp;thj^% on 2019-05-14
Spent many years trying to help others with this problem, as you are already aware ;)
When things went south I used the below:
```
sudo service bluetooth restart
```
Then I use:
```
 sudo -i (Optional)
# bluetoothctl (Needed)
[bluetooth]# power off
[bluetooth]# power on
[bluetooth]# scan on
[bluetooth]# connect XX:XX:XX:XX:XX:XX (your bluetooth address)
[Arc Touch Mouse SE]# trust
[Arc Touch Mouse SE]# pair
[Arc Touch Mouse SE]# unblock
[Arc Touch Mouse SE]# power off
[bluetooth]# power on
```
The mouse is just part of my note's kept so you can disregard that part.

Another common situation was that to make the device work I had to remove the bluetooth device and pair it again. After some research, I found out that one of the root causes was a bug inside the 4.48 version of bluez (the one shipped by default with Ubuntu 18.04). This problem causes unstable behavior during common actions (connect, disconnect, pair) and the situation we are trying to solve. 

I had forgotten to mention that I'm on Arch Linux so my version is:
```
pacman -Q bluez
bluez 5.50-6

```
So I'm just going to run through how I set it up on Ubuntu:
```
sudo apt install pulseaudio pulseaudio-utils pavucontrol pulseaudio-module-bluetooth
```
Then I edit this:
```
sudoedit /etc/bluetooth/audio.conf
```
Add the following lines:
```

# This section contains general options
    [General]
    Enable=Source,Sink,Media,Socket
```
Save and exit.
Now another thing I did was to insure a quality sound I edited my .bashrc:
I need to set A2DP as output:
```

nano .bashrc

####Then add the following line at the end:
alias soundon = 'pacmd set-card-profile device_name a2dp_sink'
```
My friend I wish you all the luck with this, as I know first hand how frustrating this is, or can be>:)

---

