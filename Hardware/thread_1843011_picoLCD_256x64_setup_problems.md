---
title: "picoLCD 256x64 setup problems"
date: 2011-09-12
forum: Hardware
---

### Post by jtupulis on 2011-09-12
Hi,

Trying to set up picoLCD 256x64, has ran into problems just can't figure out by myself. Any help appreciated.

First of all, seem that hw is not an issue: lcd lights at startup and is found by lsusb.

Then, tried an easy way - installing manufacturer provided drivers+sw: [http://www.picolcd.com/drivers/?ck=V26aH-55AcwZSZkP&vid=V26aH-55AesZSWMp&cktime=96661](http://www.picolcd.com/drivers/?ck=V26aH-55AcwZSZkP&vid=V26aH-55AesZSWMp&cktime=96661) Initially - most simple thing - installer. Doesn't work - software just doesn't fire up, nothing happen. Tried to run script in a terminal, got messages I wasn't able to google out:

```

jtupulis@STRAZDS:~/picolcd-256x64/picoLCDGraphic$ ./start-picolcd256x64.sh 
Installation path: /home/jtupulis/picolcd-256x64
Running gksu wrapper
/home/jtupulis/picolcd-256x64/picoLCDGraphic/gksu: error while loading shared libraries: libstartup-notification-1.so.0: wrong ELF class: ELFCLASS64
/home/jtupulis/picolcd-256x64/picoLCDGraphic/gksu: error while loading shared libraries: libstartup-notification-1.so.0: wrong ELF class: ELFCLASS64


```

Then decided to go harder way: installed lcd4linux from svn and to to be sure (?) compiled picoLCD driver from manufacturer source. But, trying to launch lcd4linux:

```

missing 'Display' entry in /etc/lcd4linux.conf!

```

But there is display entry in conf file:

```

# The display settings

Display picoLCD {
	Driver	'picoLCDGraphic'
	Size	'256x64'
	Contrast	230
	Backlight	1
	Inverted	1
	Icons	1
}


```

I was not able to google out next step in order to proceed, please help, maybe somebody has similar experience?

---

### Post by fineghal on 2011-09-20
Does your driver "picoLCD" or "picoLCDgraphic" exist?
I remember the svn had an issue about a missing driver for a while, not sure if it was ever fixed. 


Are there any other display entries in your lcd4linux.conf?
Don't remember if that matters but worth checking.

Final thought: Make sure your permissions on the lcd4linux.conf file are correct and readable by the user you're starting the program with. 

Also: Your lcd4linux.conf exists in /etc right? I fuzzily recall the default install path being something like /etc/lcd4linux.

I messed with this about a year ago and never got it working, maybe you'll have better luck.

Final thought: did you try compiling the manufacturer supplied source as well? Your initial error suggests you're running in a 64-bit environment. Or you're in 32 and the package was compiled in 64. Might try copying the libstartup-notification-*.so from your system into the lcd4linux folder as libstartup-notification-1.so

---

### Post by fineghal on 2012-01-01
I should have asked you to post the debug output form lcd4linux ala lcd4linux -Fvvq.

That being said: There is a known bug that will cause lcd4linux to hang  when requesting the lcd.

The bug exists within the hid_picolcd module.
Requesting a hid_release, or forcefully removing the module fails to make the picoLCD available to the OS.

In order for lcd4linux to acquire the device, you'll need to blacklist the hid_picolcd module.

This is done by editing the /etc/modprobe.d/blacklist.conf file and adding 
"blacklist hid_picolcd" without the quotes to the end of the file. 

Once this is done a reboot will make the lcd available to the OS.

---

