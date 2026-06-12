---
title: "Gateway FX Success Story"
date: 2009-05-23
forum: Hardware
---

### Post by asdel on 2009-05-23
I have a Gateway-7805u and this is my list of notes. I've installed the AMD/64-bit Ubuntu  9.04 and this is the catalogue of my successes and issues.

Installation went cleanly. I used a Qparted rescue cd to scrink the Windows Vista partition to ~100GB. Please note, partition /dev/sda1 is a windows re-install/rescue partition and /dev/sda2 is the windows partition.

After installation I had the following problems:

1) Would not awake from suspend/hiberate 
2) Very spoty/unreliable Wireless
3) No 3-D, and no option System-->Administration to install a restricted driver for the NVidia chip
4) Brightness button brightens/dims the screen in two increments, rather than one.
5) partial functionality of media keys.


FIRST, GETTING NVIDIA 3D TO WORK.
I had to explicitly install the NVidia restricted drivers as follows:

sudo apt-get install nvidia-glx-180

And reboot.


SPOTTY WIRELESS

I would loose wireless connectivity for up to 30 seconds every minute or two. Maddening! The problem has to the with the drivers, so installing the juanty backport drivers did the trick. Perfect wireless after this:

sudo aptitude install linux-backports-modules-jaunty-generic


NO VIDEO AFTER SUSPEND

This was the most frustrating and difficult to solve. The problem is that the intel_agp kernel module is loaded, and it prevents the video card from coming on line after resuming. If I was at a command line (i.e. not in X) I can type 'find /' at the keyboard and see disk activity, but I could not see anything on the monitor.

See this solution:
[http://en.opensuse.org/NVidia_Suspend_HOWTO](http://en.opensuse.org/NVidia_Suspend_HOWTO)

It amounts to adding this line to /etc/modprobe.d/blacklist.conf
   blacklist intel_agp

And adding 
   Option "NVagp" "1"
to you /etc/X11/xorg.conf in the Driver section

Reboot, and perfect.

MEDIA KEYS
still working on this. Pause/play/stop/mute/next/previous/volume work. The Music and DVD keys do nothing

DOUBLE BRIGHTNESS
The Vidoe Brightness Up and Down seem to do two steps of brightness.



OTHER ELMENTS

The Web Camp - 

sudo aptitude install libpt-1.10.10-plugins-v4l2 luvcview

To test, run luvciew


The Wireless Button
Works fine. You can turn off wireless and turn it back on and NetworkManager handles this gracefully.

DVD and CRROM burner works.

MicroCard reader works

USB ports work

Wired Ethernet works like a champ. I have only an 100Mb switch, so I cannot tell you if 1Gb works.

I have not tried the eSATA, HDMI, VGA, or FireWire ports.

---

### Post by hotstepperk on 2010-01-07
i've just got the gateway p-7915u running on ubuntu 9.10 64 bit. trying to get the multimedia keys to work (music and dvd). any luck on your part?

---

### Post by asdel on 2010-01-07
> **hotstepperk said:**
> i've just got the gateway p-7915u running on ubuntu 9.10 64 bit. trying to get the multimedia keys to work (music and dvd). any luck on your part?


The Play/Pause, Stop, Next/Last Sound, Mute, and Volume worked well. The Music Player and DVD player buttons do nothing under 9.10 64-bit. What's more, I haven't found a way to map them to an application.

I am also glad to report that the wireless now works out of the box.

Thanks
Mike

---

### Post by hotstepperk on 2010-01-16
ok then. i'll keep working on it. i'll be sure to post my findings here.

---

