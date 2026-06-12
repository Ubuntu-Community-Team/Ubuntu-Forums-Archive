---
title: "HOW TO: Play a DVD on a Dell 700m"
date: 2006-03-08
forum: Hardware &amp; Laptops
---

### Post by voidmain on 2006-03-08
I figured I'd log my last two hours of work to get the DVDs working on a Dell 700m so that it is searchable.

1. sudo apt-get install libdvdread3
2. sudo /usr/share/doc/libdvdread3/examples/install-css.sh
3. sudo apt-get install wget
4. cd /tmp; wget [ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb)
5. sudo dpkg -i  w32codecs_20050412-0.0_i386.deb
6. sudo apt-get install vlc
7. vlc /media/cdrom

Explanation:

1. You need to install the libdvdread3 library if it isn't already installed and that contains a script to install the libdvdcss, which is used for DVD decryption.
2. This command installs libdvdcss
3. This installs wget, which is a good command-line utility for grabbing stuff off the web
4. This downloads the win32 codecs that are used to help play DVDs and other non-free formats.
5. This installs the downloaded win32 codecs
6. This installs the vlc application that will be used to play the DVDs. This is important because totem DOESN'T WORK with a Dell 700m for whatever reason and crashes everytime no matter what you try. I think this is because it cannot handle some types of DVD audio streams (the more common type) and bails. It probably can play older DVDs but not newer ones.
7. This opens the media to be played in vlc. This is also really important because you must use the path name to the mounted location of the CDROM drive. Using dvd:// for a Dell 700m DOESN'T work and I have no idea why. I think it is because this MRL isn't correctly mapped, but I didn't want to spend the time to figure it out since using the path works fine. 

Good luck!

---

### Post by Jeremy'sCoding on 2006-03-08
Hello voidman,

I have been using Ubuntu only a few weeks, but I can provide a little info.  I had trouble using totem on my fairly new HP pavilion desktop.  I found out that in order to get totem to work you also need to install some music player apps.  I just went to the wikipedia app installation guide and installed every type of music and MP3 player I could find and then totem worked just fine.  

This was a fairly crude solution, no doubt, but it worked for me.

Best of Luck,

Jeremy

---

### Post by voidmain on 2006-03-09
[QUOTE=Jeremy'sCoding]
I have been using Ubuntu only a few weeks, but I can provide a little info.  I had trouble using totem on my fairly new HP pavilion desktop.  I found out that in order to get totem to work you also need to install some music player apps.  I just went to the wikipedia app installation guide and installed every type of music and MP3 player I could find and then totem worked just fine.  
[/QUOTE]

Sounds like a pain in the arse. I'd much rather the totem folks figure out their dependencies and put it in the deb or rpm package. It would also be nice if the linux world in general world stop tripping over this non-free issue we have and start providing complete installation packages for people. This is the only way the desktop linux is going to work. I think there should be a package like this:

dvds-in-gnome-1.0.deb

This would be a symbolic package that included css, dvdread, w3scodecs, etc and took the hardship out of getting things to work. Linux is still such a hackers OS that no non-programmer/non-techie will use it until it grows up a bit.

---

