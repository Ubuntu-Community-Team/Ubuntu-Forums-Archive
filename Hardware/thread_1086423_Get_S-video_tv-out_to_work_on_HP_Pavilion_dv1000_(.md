---
title: "Get S-video tv-out to work on HP Pavilion dv1000 (dv1065us)"
date: 2009-03-04
forum: Hardware
---

### Post by eesh on 2009-03-04
Hi!

I got a used HP dv1065us and put Ubuntu 8.10 on it (On a USB drive, but I doubt that it matters). Almost everything seems to work out of the box, but I can't seen to get the tv-out to work. GNOME has no relevant settings in the GUI, and xorg.conf only has "Configured Video Device", "Configured Monitor" and "Default Screen", with no other settings.

[This post]("http://ubuntuforums.org/showthread.php?t=196128") seems to be relevant, but I'm afraid of touching my almost-empty xorg.conf.

What can I do?

Thank you!

_Edit_: Forgot to mention this is an Intel 945GM Express chipset.

---

### Post by jaminux on 2009-03-04
Hi, I have a HP Pavillion dv7 1020ea and the following is how I set up my VGA w/ an external screen. Might help you - assuming ofc you are using Nvidia like me.

1) Get the latest drivers and restart the computer. Go to System > Administration > Hardware Drivers. Oh and plug the monitor in before the system starts up again.

2) After reboot type gksudo nvidia-settings (entry in administration doesn't have correct permission i.e. the gksudo part).

3) Go to X-Server Display Configuration and enable your monitors as necessary. Rather than clicking apply click save to x config file. 

4) Restart X: Press control alt backspace

If you found your settings in no. 3 it should work fine.

*Substitute the the word monitor tv where necessary.

This might not work the same for a TV. However, NVidia settings deal with your gfx card; the gfx card will handle any TV out as well do setting it up might be similar.

Hope this helps.

---

### Post by eesh on 2009-03-04
Thanks! But I forgot to mention, I have an Intel Extreme Graphics 2 adapter. I'll edit the original post though. Is there a simialar utility for Intel?

(That's what you get for posting late at night after everything you tried has failed :) )

---

### Post by eesh on 2009-03-08
Hi,

Still struggling with this... I found a few references to setting this up with xorg.conf, but I don't want to use it unless I have to (Because from what I can gather, there's a new method).

[https://wiki.ubuntu.com/X/Config/SVideo](https://wiki.ubuntu.com/X/Config/SVideo)

Trying the suggested command gives me:
```
eesh@mylaptop:/etc/X11$ xrandr --output S-video --set load_detection 1
X Error of failed request:  173
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  15 ()
  Serial number of failed request:  16
  Current serial number in output stream:  16
```
I can't find any relevand FDL files in my system (I read that's the "replacement" for xorg.conf, so to speak).

I know it's cliche, but TV-Out is a showstopper for me - If I can't get this to work, it's Windows for that machine... And I don't want that. :)

Thank you!

---

### Post by Chibone on 2009-03-08
Did you try the third command on that page?

```
xrandr --addmode S-video 800x600
```

How did that work out?

---

### Post by eesh on 2009-03-08
> **Chibone said:**
> Did you try the third command on that page?

```
xrandr --addmode S-video 800x600
```

How did that work out?

```
eesh@mylaptop:~$ xrandr --addmode S-video 800x600
xrandr: cannot find output "S-video"
```
No luck...

If it were using xorg.conf, I'd need to add another monitor there, named "S-video", or "TV" (According to [FONT="Courier New"]man i810[/FONT]), but, well, you know. :)

Where is Xorg drawing its settings from now? What file can I edit to change them? Or GUI to use?

---

### Post by Chibone on 2009-03-08
maybe looking here will help?

[http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)

some things to try from glancing at this document and also stuff i thought of:

1) connect your s-video and go to System -> Preferences -> Screen Resolution and click the "Detect Displays" button

2) connect your s-video before booting the laptop and see if 
its autodetected

3) xrandr -auto

4) xrandr 
by itself; see what outputs are on

---

### Post by eesh on 2009-03-08
> **Chibone said:**
> maybe looking here will help?

[http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)

some things to try from glancing at this document and also stuff i thought of:

1) connect your s-video and go to System -> Preferences -> Screen Resolution and click the "Detect Displays" button

2) connect your s-video before booting the laptop and see if 
its autodetected

3) xrandr -auto

4) xrandr 
by itself; see what outputs are on

Hi,

I tried 1 and 2 already. No change. I just see "Laptop", and when I connect an external VGA, I see that too.

xrandr --auto gives no output, and it does nothing - the outputs I have both before and after it are the same:
```
eesh@mylaptop:~$ xrandr --verbose
Screen 0: minimum 320 x 200, current 1280 x 768, maximum 1280 x 1280
VGA disconnected (normal left inverted right x axis y axis)
	Identifier: 0x3b
	Timestamp:  32693
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
LVDS connected 1280x768+0+0 (0x3d) normal (normal left inverted right x axis y axis) 305mm x 183mm
	Identifier: 0x3c
	Timestamp:  32693
	Subpixel:   horizontal rgb
	Clones:    
	CRTC:       1
	CRTCs:      1
	EDID_DATA:
		00ffffffffffff0006af140e684a0000
		260e0103802114780a055097574f8f26
		21505400000001010101010101010101
		010101010101c61b00a0500037301070
		130031b710000018000000fe42313430
		45573031381f0a202020000000fe4231
		343045573031381f0a202020000000fc
		00436f6c6f72204c43440a2020200099
	BACKLIGHT_CONTROL: kernel
		supported: native       legacy       combination  kernel      
	BACKLIGHT: 5 (0x00000005) range:  (0,5)
  1280x768 (0x3d)   71.1MHz -HSync -VSync *current +preferred
        h: width  1280 start 1296 end 1408 total 1440 skew    0 clock   49.4KHz
        v: height  768 start  769 end  772 total  823           clock   60.0Hz
  1024x768 (0x41)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x46)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  640x480 (0x4b)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
```
According to the page you linked to, I should be seeing "TV" there.

I also checked the BIOS - There doesn't seem to be any related setting.

---

