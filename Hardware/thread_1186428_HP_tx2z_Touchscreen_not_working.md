---
title: "HP tx2z Touchscreen not working"
date: 2009-06-13
forum: Hardware
---

### Post by RageAge on 2009-06-13
Hey, i recently bought a pretty neat touchscreen laptop, HP touchsmart tx2z, and installed ubuntu on it. the pen works nicely, although the button on the stylus doesnt do anything.

i have the usual laptop functions working (sound, picture, keyboard, touchpad), but the actual touch screen does not. it recognises the pen and the cursor follows it nicely, but when i use my hand, it simply moves the cursor to the top left.

i've tried looking for quite a while to find an answer, and nothing works. can anyone give me a nice step by step tutorial of how to get this working? :D

---

### Post by Favux on 2009-06-13
Hi RageAge,

That may be the best you can do in Jaunty for right now.  Basically the Jaunty kernel doesn't provide enough support.  N-trig hasn't released linux drivers.  There are some patches available for the linuxwacom drivers that can get them to substitute for N-trig drivers.  The MPX project (multitouch) hasn't been integrated into Xorg's Xserver yet.  It looks like all that will change with Kharmic due out in October.

That said Attilla_fdd is trying to get things set up in Jaunty.  For more info. on all this start with post #146 here:  [http://ubuntuforums.org/showthread.php?t=1038898&page=15](http://ubuntuforums.org/showthread.php?t=1038898&page=15)

We may be able to get your button working through wacomcpl or adding a line to the .fdi.  Let's see what the output of this command in a terminal looks like:
```
xinput --list
```

---

### Post by RageAge on 2009-06-13
k, here's the output from the command:

```
"Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"AT Translated Set 2 keyboard"	id=2	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=3	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=4	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"SynPS/2 Synaptics TouchPad"	id=5	[XExtensionPointer]
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 1472
		Max_value is 5472
		Resolution is 1
	Axis 1 :
		Min_value is 1408
		Max_value is 4448
		Resolution is 1
"HID 1b96:0001"	id=6	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 9600
		Resolution is 10000
	Axis 1 :
		Min_value is 0
		Max_value is 7200
		Resolution is 10000
"HID 1b96:0001"	id=7	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 5
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 9600
		Resolution is 1016
	Axis 1 :
		Min_value is 0
		Max_value is 7200
		Resolution is 1016
	Axis 2 :
		Min_value is 0
		Max_value is 256
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1

```

---

### Post by RageAge on 2009-06-13
oh, and yea, the button on the stylus is supposed to be a right click. if that gets working i think i will be content, seeing as it can function as a tablet with just those.

and yea, i have it set up as a dual boot, so vista is still there. but its far too slow, and i greatly prefer ubuntu.

---

### Post by Favux on 2009-06-13
Hi RageAge,

If you looked at the thread I linked then we got what we expected, which is the wacom.fdi doesn't seem to recognize your N-trig.  To be certain you'd "lshal>lshal.txt" and in gedit you could use find to pull out your N-trig sections.  You'd search "HID 1b96:0001".

The sections for your N-trig seem to be:
"HID 1b96:0001"	id=6	[XExtensionPointer]
and/or
"HID 1b96:0001"	id=7	[XExtensionKeyboard]

To make the stylus button a right mouse click you could add to the "10-wacom.fdi" in "/usr/share/hal/fdi/policy/20thirdparty/" the following line:
```
       <merge key="input.x11_options.Button2" type="string">3</merge>
```
so that the N-trig subsection would look like:
```
    <!-- N-Trig Duosense Electromagnetic Digitizer -->
    <match key="info.product" contains="HID 1b96:0001">
      <match key="info.parent" contains="if0">
       <merge key="input.x11_driver" type="string">wacom</merge>
       <merge key="input.x11_options.Type" type="string">stylus</merge>
       <merge key="input.x11_options.Button2" type="string">3</merge>
      </match>
    </match>
```
You could check in Synaptics Package Manager and see if both Wacom packages (xserver-xorg-input-wacom and wacom-tools) are installed and add the line and reboot and see if it works.  My current understanding is that this won't work.  Another way is to use "wacomcpl" but that also depends on linuxwacom recognizing the N-trig digitizer.

Most likely you'd have to find the hypothetical .fdi that is presumably configuring the N-trig as a HID (Human Interface Device) and see if adding the line to it would work.  My guess is that it would be somewhere in the "/usr/share/hal/fdi/" directory.  That would likely require some ingenuity and persistence.

---

### Post by RageAge on 2009-06-13
k, i did sudo gedit, opened the .fdl you directed me to, added the line of code you gave me, and right clicking works. thank you, very much :D

with that i think i can survive till Kharmic is released. 

one last question: i found a script on the thread you gave me a link to that rotates the screen: the screen rotation works flawlessly, but the digitizer does not. so when the stylus is put to the top of the screen (where it says applications), it moves to the left. 

i'm pretty sure its this part of the code that needs to be changed:
```
   xsetwacom set stylus rotate  CW 
    xsetwacom set touch rotate CW 
    xsetwacom set eraser rotate CW 
```

i'm guessing it would be because xsetwacom is not in charge of the digitizer. any ideas?

---

### Post by Favux on 2009-06-13
Hi RageAge,

Wow, great work!  So the wacom.fdi is doing something.  If you can get rotation working you're ready to write a mini HOW TO for Jaunty.  There's a bunch of TX2z users who could use it.

Well assuming xsetwacom commands will work then lose the lines with eraser and touch.  Xinput tells us:
stylus = "HID 1b96:0001"

So replace stylus with it like so:
```
xsetwacom set "HID 1b96:0001" rotate  CW
```
I think with the quotes.  See if that works

---

### Post by RageAge on 2009-06-13
i think a how-to is a good idea. anyone else in my situation would probably benefit from it, and i have the time to write a nice easily understood one.

and ha, looks like the script to turn the screen was made by you. i didnt notice the name before, "Favux_.Compiz_off_Rotation.sh"

but anyways, renaming the stylus part worked flawlessly. a last part to get working would be linking the button on the side of the computer to the script. i have no idea how that would work though.

if that isnt possible, i think an application launcher would do. maybe put one up by the links to firefox and evolution.

edit: also, i think i have an idea for a revision to the code. might simply restarting compiz after the rotation takes place work? rather than switching to metacity? i think that would both speed up the script, and keep visual effects set up in compiz, provided it works.

what is the command the compiz-fusion icon uses for reload window manager? putting that in after the rotation should do it.

---

### Post by Favux on 2009-06-13
Hi RageAge,

Great!  So now you have rotation too.  If you look at the HOW TO in the first post first page of the thread you got the rotation script from it talks about key binding the script or using a launcher.

I don't know what command the compiz-fusion icon uses.  It wouldn't surprise me if the script can be improved though.

I wonder if rec's script would translate "HID 1b96:0001" to stylus?  Then you wouldn't have to rename the xsetwacom command and you could use wacomcpl.

If you're interested in checking it out the link to rec's script is in Jaunty Users 3a near the top here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  And then Section 3 shows you how to use wacomcpl.

Either way does the stylus work in say CellWriter and Xournal?  And do you get pressure in Gimp?  Towards the bottom of the Wacom wiki it talks about setting up Gimp:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

---

### Post by RageAge on 2009-06-13
i'll look at the other how-to's tomorrow about the key binding, but i already made a launcher for it and it works nicely. one thing i noticed is that occationally the cursor does not follow the stylus, sometimes it is slightly below where i hold it. this is purely cosmetic though. it still registers the cursor as being below the stylus, so opening menus and clicking things is true to the stylus, it just doesnt appear so.

and yes, all three of the programs you mentioned work very well. i already had cellwriter set up to start when i log in, but i had not heard of xournal, or that gimp has pressure sensitivity. xournal works quite nicely though. the button on the stylus acts as an eraser.

and in gimp the pressure sensitivity works. the button acts as right click still in gimp, but thats ok, because thats more useful than an eraser. i followed the directions given, and all i really had to do is change one setting from disabled to screen. the stylus is the second "HID 1b96:0001" in the list (both showed up in the gimp options). i wonder if the first one is the touch screen?

---

### Post by Favux on 2009-06-13
Hi RageAge,

Wow!  Real progress.  I'm not sure what the double entries mean.  My guess was that the [XExtensionKeyboard] one was the stylus, because that's how our wacom stuff shows up in xinput.

It may be it needs a little calibration.  We could do it through the .fdi (or wacomcpl).  Wacomcpl has a calibration routine where you touch the targets with your stylus and it generates the correct coordinates.

---

### Post by Vincent_Lin on 2009-06-16
Favux,

Inspired by the discussion of this thread, I did some experiments.

In the script for rotation, instead of using

xsetwacom stylus rotate CW

I use 

xsetwacom "stylus" rotate CW

And it works!! 

I have stock installation of 9.04 with fglrx, and I touched nothing on xorg.conf, expcept the long standing xorg.conf with stylus, eraser, etc..., that was mentioned in the other thread.  I could not have rotation on stylus working as expected. 

I did not touched fdi either. 

Now with the quotes around stylus, rotation works.

Vincent

---

### Post by Favux on 2009-06-16
Hi Vincent_Lin,

Wow!  Great inspiration/intuition!

I have no idea why that works.  I wonder if it works with the other linuxwacom names.  Like "eraser" etc.  You'd still have to rename things, but now the names would be descriptive.

I lost you on the xorg.conf.  Do you mean you put the entries for Intrepid on the TX2z thread into your Jaunty xorg.conf?  If so does it give you touch?

---

### Post by Vincent_Lin on 2009-06-17
Favux,

Yes I took the xorg.conf for 8.10 and used it as is.  And unfortunately, touch does not work.  But it responds to the touch of finger and the cursor moves to top-left corner when the finger touch is moved.  The cursor does not move when simply finger touches the screen.  The cursor only moves when finger moves when touching the screen.

Moreover, when I edited xorg.conf to remove all mentions of touch, the screen/cursor still behaves the same.

Vincent

---

### Post by RageAge on 2009-06-18
ooh, i found something interesting. in the same folder as the wacom .fdi, there's one called "50-touchkit.fdi". the contents look like this:

```
<!-- -*- SGML -*- -->
&#8722;
<deviceinfo version="0.2">
&#8722;
<device>
&#8722;
<match key="info.product" contains="Touchkit Touch">
&#8722;
<match key="info.capabilities" contains="input">
<merge key="input.x11_driver" type="string">evtouch</merge>
<merge key="input.x11_options.minx" type="string">130</merge>
<merge key="input.x11_options.miny" type="string">197</merge>
<merge key="input.x11_options.maxx" type="string">3945</merge>
<merge key="input.x11_options.maxy" type="string">3894</merge>
<merge key="input.x11_options.taptimer" type="string">30</merge>
<merge key="input.x11_options.longtouchtimer" type="string">750</merge>
<merge key="input.x11_options.longtouched_action" type="string">click</merge>
<merge key="input.x11_options.longtouched_button" type="string">3</merge>
<merge key="input.x11_options.oneandhalftap_button" type="string">2</merge>
<merge key="input.x11_options.movelimit" type="string">10</merge>
<merge key="input.x11_options.touched_drag" type="string">1</merge>
<merge key="input.x11_options.maybetapped_action" type="string">click</merge>
<merge key="input.x11_options.maybetapped_button" type="string">1</merge>
</match>
</match>
</device>
</deviceinfo>
```

also, i googled touchkit touch (the device) and that is definitely the touch screen. might editing this enable touch capabilities? or deleting and using xorg.conf?

---

### Post by elboy0712 on 2009-06-18
Hi everyone, I am new to the forums but this one is close to home. Im stoked by the progress you are all making. I have a TX2Z at home(cant bring it to work because of my job) running the latest mint. I dont know how much help I can be as I am very time constrained, but if you want anything tested on a second box just say so and ill let you all know if it is consistent with what you are all seeing or expect to see. Plus I dont mind slicking if necessary so I am not to scared of mistakes on this one.... Thanks again for the effort, let me know if I can help. Ill be watching...R

---

### Post by Favux on 2009-06-18
Hi Vincent_Lin, RageAge, and elboy0712,

Well when the cursor heads to the corner like that it usually means Xinput isn't getting any input.  That makes sense from what Rafi tells us.  The only way to get touch is to use the 2.6.29 kernel and Rafi's n-trig.patch like Attilla_fdd is doing on the "Re: HOWTO setting up ubuntu 8.10 intrepid on the HP tx2z tablet pc" starting with post #147.  Responding to my posts #145 & 146.

This is because no one has done the patches for linuxwacom drivers in Jaunty (much less a deb) like was done for linuxwacom in Intrepid.  Probably because of changes in linuxwacom and going to Xserver 1.6 made updating the patches non-trivial.

So now the stylus works with both the xorg.conf and the N-trig subsection in the 10-wacom.fdi.  I have no idea why.  My guess is that Timo Aaltonen did apply some N-trig patches to the custom 0.8.2-2 linuxwacom in Jaunty.  But when I look at the changelog.Debian.gz in "/usr/share/doc/xserver-xorg-input-wacom" I see no mention of this being done.  But how else is the N-trig subsection of the 10-wacom.fdi active and pressure available in Gimp?  Could the N-trig drivers in the kernel HID section do this?  Seems unlikely.  And why would Timo put the N-trig section in the .fdi if he didn't know the linuxwacom drivers would recognize it?  So color me confused.

Even if this is what's going on touch probably isn't possible in Jaunty (without a new kernel) otherwise wouldn't have Timo added it to the .fdi?  So RageAge is what you're asking is the duplicate entry '"HID 1b96:0001"	id=6	[XExtensionPointer]' the touch input?  And can you get it going with evtouch?  I wouldn't think so.  I don't think evtouch and linuxwacom can coexist.  But I've been wrong before.

Right now it looks like Timo setup things up so you could get your N-trig stylus working through linuxwacom and the 10-wacom.fdi.  Which means you can also get your stylus button working.

---

### Post by proverbs308 on 2009-06-18
I am wanting to take a slightly different approach.  Is it possible to completely eliminate the touch controls?  I would actually like to have only the pen or at least the ability to turn off touch so that when I am writing with the pen I don't moving anything with the touch.

I am a student and this last year I used Vista in order to not have my hand on the screen mess with the stylus input. Has anyone found a way doing this?

---

### Post by proverbs308 on 2009-06-19
I was just reading this morning about the kernal 2.6.30.  Acording to what I have read it has n-trig written into the kernal.  After I installed it to test it I had to add two sections to my xorg.conf file:

```
Section "InputDevice"                                    
        Driver "wacom"                                   
        Option "Mode" "Absolute"                         
        Identifier "touch"                               
        Option "Type" "touch"                            
        Option "ForceDevice" "ISDV4" # Tablet PC ONLY    
        Option "Device" "/dev/input/event3"              
        # Option "Device" "/dev/input/by-path/pci-0000:00:13.1-usb-0:2:1.0-event-mouse"
        Option "TopX" "0"                                                              
        Option "TopY" "0"                                                              
        Option "BottomX" "9600"                                                        
        Option "BottomY" "7200"                                                        
        Option "USB" "on"                                                              
EndSection                                                                             
                                                                                       
Section "InputDevice"                                                                  
        Driver "wacom"                                                                 
        Identifier "stylus"                                                            
        Option "Mode" "Absolute"                                                       
        # Option "Device" "/dev/input/event3"                                          
        Option "Device" "/dev/input/by-path/pci-0000:00:13.1-usb-0:2:1.0-event-mouse"  
        Option "Type" "stylus"                                                         
        Option "ForceDevice" "ISDV4" # Tablet PC ONLY
        Option "TopX" "0"
        Option "TopY" "0"
        Option "BottomX" "9600"
        Option "BottomY" "7200"
        Option "USB" "on"
        Option "Button1" "1"
        Option "Button2" "3"
        Option "Button3" "2"
EndSection

```

I know have the stylus working but the touch seems to work intermentanly.  Any ideas?

---

### Post by Favux on 2009-06-19
Hi proverbs308,

Did you use kernel 2.6.29 or 2.6.30?  If so which version?

I think you have to comment out the 13.1 by-paths (for Dell Latitude XT?) and substituted 14.5 in the by-paths for the TX2z.

Also I suspect the xorg.conf sections aren't functional and the kernel N-trig HID drivers are doing everything.  You probably still need to install the n-trig.patch on the latest linuxwacom and compile it.  I describe doing this in post #155 here:  [http://ubuntuforums.org/showthread.php?t=1038898&page=16](http://ubuntuforums.org/showthread.php?t=1038898&page=16)  And I have Rafi's xorg.conf wacom sections.

---

### Post by Favux on 2009-06-19
Hi proverbs308,

HOLD OFF doing anything more.  Ayuthia in post #409 here:  [http://ubuntuforums.org/showthread.php?p=7485847#post7485847](http://ubuntuforums.org/showthread.php?p=7485847#post7485847)  seems to be getting a handle on things.  He may have a breakthrough for N-trig on Jaunty in a little bit.

---

### Post by Ayuthia on 2009-06-19
> **proverbs308 said:**
> I was just reading this morning about the kernal 2.6.30.  Acording to what I have read it has n-trig written into the kernal.  After I installed it to test it I had to add two sections to my xorg.conf file:

```
Section "InputDevice"                                    
        Driver "wacom"                                   
        Option "Mode" "Absolute"                         
        Identifier "touch"                               
        Option "Type" "touch"                            
        Option "ForceDevice" "ISDV4" # Tablet PC ONLY    
        Option "Device" "/dev/input/event3"              
        # Option "Device" "/dev/input/by-path/pci-0000:00:13.1-usb-0:2:1.0-event-mouse"
        Option "TopX" "0"                                                              
        Option "TopY" "0"                                                              
        Option "BottomX" "9600"                                                        
        Option "BottomY" "7200"                                                        
        Option "USB" "on"                                                              
EndSection                                                                             
                                                                                       
Section "InputDevice"                                                                  
        Driver "wacom"                                                                 
        Identifier "stylus"                                                            
        Option "Mode" "Absolute"                                                       
        # Option "Device" "/dev/input/event3"                                          
        Option "Device" "/dev/input/by-path/pci-0000:00:13.1-usb-0:2:1.0-event-mouse"  
        Option "Type" "stylus"                                                         
        Option "ForceDevice" "ISDV4" # Tablet PC ONLY
        Option "TopX" "0"
        Option "TopY" "0"
        Option "BottomX" "9600"
        Option "BottomY" "7200"
        Option "USB" "on"
        Option "Button1" "1"
        Option "Button2" "3"
        Option "Button3" "2"
EndSection

```

I know have the stylus working but the touch seems to work intermentanly.  Any ideas?

Here is what I have for my touch in xorg.conf:
```
Section "InputDevice"

#       Option      "LongTouchTimer" "1"
#       Option      "MoveLimit" "1"
        Identifier  "touch"
        Driver      "wacom"
        Option      "Mode" "Absolute"
        Option      "Touch" "on"
        Option      "Type" "touch"
#       Option      "ForceDevice" "ISDV4"
        Option      "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
        Option      "USB" "on"
#       Option      "Suppress" "0"
        Option      "TopX" "0"
        Option      "TopY" "0"
        Option      "BottomX" "9600"
        Option      "BottomY" "7200"
        Option      "MaxX" "9600"
        Option      "MaxY" "7200"
        Option      "ResX" "1280"
        Option      "ResY" "800"
#       Option      "TapTimer" "0"
        Option      "Buttons" "5"
        Option      "DebugLevel" "8"
        Option      "Button1" "1"
        Option      "Button10" "1"
EndSection

```Mine seems to working fine in Gentoo using the 2.6.30 kernel and I am still testing my [changes]("http://ubuntuforums.org/showthread.php?t=1038898&page=16")(see posts 157 and 158) for the Ubuntu 2.6.28-13-generic kernel.

EDIT:
Another tidbit.  I have not been able to get the touch to stop working while I am writing in xournal even with the 2.6.30 changes.  If I remember correctly, if I had the touch and stylus defined in 10-wacom.fdi, the touch did not work.

EDIT2:  On Rafi Rubin's [webpage]("http://ofb.net/~rafi/latitude_xt.html"), he mentions how to disable the touch with the 2.6.30 kernel:
> One bit of advice, I suggest using an alias or something to wrap xournal if you want to run it with pen only. "xsetwacom set touch touch off; xournal; xsetwacom set touch touch on". I don't know how to make xournal act intelligently when the touch sensor is active. But it works very nicely with touch off. 

---

### Post by Favux on 2009-06-24
Hi proverbs308, Vincent_Lin, RageAge, and elboy0712,

Ayuthia has done it!  Stylus and touch in Jaunty.  You use a xorg.conf.  See his instructions and deb.s on posts #157 & 158 here:  [http://ubuntuforums.org/showthread.php?t=1038898&page=16](http://ubuntuforums.org/showthread.php?t=1038898&page=16)  I have attached what I think is a working TX2z xorg.conf for Jaunty to the bottom of the Rotation HOW TO here:  [http://ubuntuforums.org/showthread.php?p=6274392#post6274392](http://ubuntuforums.org/showthread.php?p=6274392#post6274392)

---

### Post by RageAge on 2009-07-27
sorry for not replying for so long, i've been visiting relatives for the past month or so and havent been able to get on the internet much. 

anyways, this worked perfectly! it took me a while, and i failed the first time (to the point of needing a re-install, but thats ok, i didnt lose anything important), but now touch works, and life is good.

thanks so much for the help :)


edit: ah, noticed a problem. it only responds to touch when i move after touching the screen. so simply poking it does nothing.

---

### Post by Favux on 2009-07-27
Hi RageAge,

Welcome back from the Wilderness(?)!

Did you use the new deb.s on post #186?

Ayuthia uses a two finger swipe to get touch back.  Synace says a two finger pinch works better for him.

---

### Post by RageAge on 2009-07-27
ha, thanks. and it wasnt so much wilderness as my relatives kept me incredibly busy.

the first time i didnt use the .deb's, which is why it didnt work. the second time i did, and this is where the no touch without movement comes into play.

if it makes a difference, i have a 64 bit processor, and used 64 bit deb files

---

### Post by Favux on 2009-07-27
Hi RageAge,

Did you comment out the n-trig subsection of the 10-wacom.fdi?

---

### Post by RageAge on 2009-08-07
ah, i discovered a problem. if you have compiz enabled, when using the xorg.conf for touch, boot does not get far enough to log in. so... how would i go about fixing this? is there some file i can edit to tell ubuntu to boot metacity rather than compiz?

---

### Post by Favux on 2009-08-07
Hi RageAge,

That's a new one.  I think people have problems rotating with Compiz active, not booting.  That may be something else.

The Compiz Fusion icon in Synaptic Package Manager let's you toggle between Compiz and Metacity.

You can also do it with Configuration Editor (gconf editor) by editing in desktop>gnome>session>required_components the value for windowmanager from compiz to metacity or vice versa.  I'm pretty sure anyway.

---

