---
title: "Asus R2E UMPC How To"
date: 2009-03-24
forum: Hardware
---

### Post by sandlidl on 2009-03-24
The Asus R2E Guide:
(Some of this guide may be useful for Asus R2H users).

The Flavors:

Ubuntu-UMPC – [http://cdimage.ubuntu.com/releases/intrepid/release/ubuntu-8.10-umpc-i386.img](http://cdimage.ubuntu.com/releases/intrepid/release/ubuntu-8.10-umpc-i386.img)
Xubuntu – [http://www.xubuntu.com/get](http://www.xubuntu.com/get)

What works:

OTB--
Touchscreen
Most buttons
Sound
Wireless and HSDPA
Fingerprint reader
GPS

Not OTB--
No Standby
Webcam
In Jaunty, there are some small problems with the touchscreen. (Hopefully it will be ironed out before the full release).

The bugs:
GPS sometimes takes a few minutes before it starts tracking your position.

Webcam shows a flipped image. Webcam doesn't work well in skype.

Gksudo doesn't display a prompt when it requires your fingerprint.

The steps:
INTRO: (You can skip this if you know what you're doing.)

Get your favorite distro. This guide is based on Ubuntu-UMPC. Get it here:

Ubuntu-UMPC – [http://cdimage.ubuntu.com/releases/intrepid/release/ubuntu-8.10-umpc-i386.img](http://cdimage.ubuntu.com/releases/intrepid/release/ubuntu-8.10-umpc-i386.img)

After you download the .img file, plug in your usb drive and open a terminal. To find out where it is mounted you could type:
```
dmesg
```

and you'll see something like sdb or sdc. Change to the directory you downloaded the .img file to and type this command: (But be very sure the device you are selecting is your USB disk, or you might lose something you don't want to lose).

```
sudo dd if=ubuntu-8.10-umpc-i386.img of=/dev/sdb(or maybe sdc).
```

Wait.

After it's finished plug it into your Asus and start it up. Install to your preference. I suggest using the TAB button to move around the install dialogs. When you've installed and updated you're ready for the real work.

#A couple things I recommend in Ubuntu-UMPC. Make the top menu bar “autohide”, and delete the side bar and add the “window list” to the top menu bar. It makes a few things easier to do and saves on precious screen-space.

PART ONE
--Calibrate the touch screen:

menu-->system-->administration-->calibrate touchscreen

follow the directions, then log out and back in so it takes effect.

--Fingerprint reader:
Install these packages:

fprint-demo
libpam-fprint
libfprint0

```
sudo apt-get install fprint-demo libpam-fprint libfprint0
```

After this, you can run the program fprint-demo to enroll your fingerprints. Don't worry if it says it cannot open your fingerprint device; all you need to do is log out and back in, or reboot and it should work fine.

#One thing that will make it easier for you is that when you enroll your finger, the window will grow and you won't see the accept or deny buttons. So if you are satisfied with the scan, hit the TAB key twice and hit spacebar. If you didn't like it, hit the TAB button once and then spacebar.

#At one time there was a bug that you could only enroll one finger and expect it to work, so be aware that if it isn't working, you may need to delete the other fingerprints and just go with one. I haven't seemed to have trouble with it though.

#One more thing to realize is that there IS a bug that interferes with gksudo (or something like that) so that a dialog DOES NOT appear, prompting you for you to scan. So just be aware that if you open something that normally requires a password (like a package manager) and you don't see anything happening, it means you need to swipe your finger. Voila! The program will begin or ask you for a password.

Enough of that. Enroll your finger(s). You can also verify them using fprint-demo. Now you're ready for the final step.

Edit this file /etc/pam.d/common-auth

```
sudo gedit /etc/pam.d/common-auth
```

add this line after the big block of comments:

```
auth	sufficient	pam_fprint.so
```

This will fallback to a password if the scan is unsuccessful. There is a way to totally commit to the fingerprint reader, but it is not suggested because it is still an “alpha” program. To be thorough, I will include the code here. Instead of the previous code, you insert this line:

```
auth	required	pam_fprint.so
```

Use it at your own risk.

After this, when you reboot, you will be prompted to scan your finger. If it was too slow, then it will revert to a password. Feel free to look up more ways to configure it, because I'm sure there's a lot more things you can do to customize how the fingerprint reader works in Ubuntu.

Gps:

There are a lot of programs to use for your Gps. Viking, Gps Drive, etc. But I highly recommend Tango GPS. It's not 1.0 yet, but it doesn't require setting up, it has a very simple and effective interface, and it looks good on a UMPC.

[http://www.tangogps.org/downloads/tangogps_0.9.6_i386.deb](http://www.tangogps.org/downloads/tangogps_0.9.6_i386.deb)

You also need to install gpsd and it's dependencies.

```
sudo apt-get install gpsd
```

Once that is finished, you need to start the gps daemon. This can be done in a number of ways. I put it as a startup item: menu-->system-->Preferences-->sessions. Or you could create a script.

The command you need to use, in either case, is:

```
gpsd /dev/ttyS0
```

This tells gpsd where the device is. There is much more to gpsd than I know, and I recommend looking into it further. But this will work. Remember, it may take a little bit of time to find you and start tracking you. I haven't noticed it being exceptionally quick on that part.

PART TWO
The WEBCAM....!

#You should note that the module is now integrated in the 2.6.28 kernel, which is what Jaunty is based on. Therefore, the Webcam should work out of the box. However, I still needed to do the vertical flip.

I cannot take credit for this part of the tutorial because it comes from here:

[http://m560x-driver.wiki.sourceforge.net/howto_install](http://m560x-driver.wiki.sourceforge.net/howto_install)

It's very easy to do, but the best part is the v4lctrl. We will use this to flip our picture image upright.

Download: [http://www.karry.wz.cz/download/v4lctrl-0.2.3.tar.gz](http://www.karry.wz.cz/download/v4lctrl-0.2.3.tar.gz)

Extract it and cd into it. Then:
```
./configure
make
sudo make install
```

The commands are simple: 
First, list your device.

```
v4lctrl -d
```

Find the one that has the name “vertical flip”. Copy the number from the ID. Now we use that number like this to change the boolean value from 0 (off) to 1 (on)

```
v4lctrl -s ######### -v 1
```

And you can use this command to change other things like horizontal flip, gain, auto exposure, etc. If the only problem you notice with the webcam is the vertical flip, then I recommend adding it as a startup script just like the gps because your settings will be lost after you shutdown.

CONCLUSION

Thanks to all the people who put their knowledge out there for the rest of us. It's cool to know that in time, these problems will probably disappear and everything will just work.:D

---

### Post by Sukhinov on 2009-06-24
Ubuntu on R2E sometimese freezes when connecting to a wireless network. The only thing I can do after that is power down. Please help!

---

