---
title: "Elantech touchpad not recognised at all in Kubuntu 15.10"
date: 2015-12-23
forum: Hardware
---

### Post by greg100 on 2015-12-23
Clean install of Kubuntu 15.10 on ASUS UX305CA laptop (uses the Elantech touchpad) and the touchpad will not work at all.  It does not recognize single tap, double tap, two finger scroll, or any clicking actions.  Basically, the touchpad doesn't even exist.

This is a dual-boot and the touchpad works fine on the Windows 10 side.

I installed updates and checked versions:  kernel is 4.2, plasma is 5.4.2, and QT is 5.5.2

I tried:

sudo apt-get install xserver-xorg-input-synaptics

and it tells me that my synaptics version is already the latest installed.  So then, I do a sudo apt-get update followed by a reboot and same thing.

I tried:

sudo add-apt-repository ppa:hanipouspilot/focaltech-dkms
sudo apt-get update
sudo apt-get install focaltech-dkms

followed by a reboot but still nothing.  (Later, I discover this method is obsolete anyway after kernel version 3.19)

I tried:

sudo modprobe -r psmouse
sudo modprobe psmouse proto=imps

Again, no beans.  I even purged the synaptics driver package and re-installed followed by apt-get update and a reboot and still nothing.

Finally, I keyboarded my over to system settings->input devices->touchpad and there is a red box with a message that says "Synaptics backend not found"

What I haven't tried is:  

cat /proc/bus/input/devices

because that is a little too technical for me to understand anyway.  Any ideas???  Thanks in advance.

---

### Post by greg100 on 2015-12-23
Just an update:

Did a clean install of Ubuntu 15.10 (Unity) and the same problem exists.

This must be either an issue with all Debian/Ubuntu based installs or this laptop is just simply too new to have support for Linux.  Leave it to ASUS to purposely get an edge on the open source community.  I used to think they were a good brand but recently through multiple experiences (drivers, support, etc) I have realized they are just money grubbing whores like Microsoft.  ASUS support said "we do not provide support for Linux."  I wouldn't be surprised if Microsoft paid them to make a proprietary configuration that only works with Windows.

I will try a non-Debian/Ubuntu distro to see if I can narrow down the problem...as of now, I think the problem is that "ASUS recommends Windows" or at least their checkbook does.

---

### Post by dubis on 2016-02-14
Hi,

I went to recieved an ASUS R556U (X555UF). I think I've the same problem than you.

If the problem still exist, could you give the result of the booth command :
        xinput --list
and 
         synclient -l

Here the're mines :
```
@X555UF:~$ synclient -l
Couldn't find synaptics properties. No synaptics driver loaded?
mdubois@X555UF:~$ xinput -list
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; ELAN1000:00 04F3:0401                     id=11   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=9    [slave  keyboard (3)]
    &#8627; USB2.0 VGA UVC WebCam                     id=10   [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                          id=12   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=13   [slave  keyboard (3)]


```
On my side my touchpad works with basic functon
Any solution are welcome

---

