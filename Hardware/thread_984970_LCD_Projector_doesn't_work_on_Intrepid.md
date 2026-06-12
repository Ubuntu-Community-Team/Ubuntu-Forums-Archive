---
title: "LCD Projector doesn't work on Intrepid"
date: 2008-11-17
forum: Hardware
---

### Post by wersdaluv on 2008-11-17
LCD Projectors plugged on my laptop used to work while I was on Hardy. Now, on Intrepid, it doesn't. I have an Intel X3100 video card in this. Also, a friend of mine on Intrepid experiences the same problem. I don't know her video card, though. What's the deal with Intrepid?

Any idea on how to fix this? :)

---

### Post by wersdaluv on 2008-11-19
Bomptigabompbompbompbomp

---

### Post by Keyper7 on 2008-11-19
It would help if you give any more details than "doesn't work".

What happens, exactly? Is it not detected? Post what you tried, step-by-step.

---

### Post by wersdaluv on 2008-11-19
If I boot with the projector plugged, the usplash will appear. The GDM appears sometimes too but I never saw my GNOME desktop on the screen. I tried the screen resolutions dialog and it appears that it can detect the projector, though.

---

### Post by Keyper7 on 2008-11-19
If it's detected, what happens when you tweak the options in the resolutions utility?

PS: it might take an entire day to check your reply to this, but I will.

---

### Post by mariner09 on 2008-11-19
I had the same issue on my Lenovo T61.  In fact, I have the same issues on Intrepid and FC10.  It's forced me to resort to XP to do my job until I can figure things out.

Have you tried turning compiz off and using the projector?

I have an old projector at home that just won't show up to xrandr or the display resolution tool.  Windows can use it.

I went to a customer and could see the projector but had the same results as you, usplash and then nothing.

Most people where I work indicate success with Compiz turned off, but I have not tried it yet.  The old projector I have still doesn't work with Compiz off.

Any pointers would be helpful, I hate having to use XP...

---

### Post by wersdaluv on 2008-11-19
Thank you so much. Nothing happens. I pressed "detected displays," lowered my resolution, and ticked "mirror screens" but I got nothing.

---

### Post by wersdaluv on 2008-11-19
> **mariner09 said:**
> I had the same issue on my Lenovo T61.  In fact, I have the same issues on Intrepid and FC10.  It's forced me to resort to XP to do my job until I can figure things out.

Have you tried turning compiz off and using the projector?

I have an old projector at home that just won't show up to xrandr or the display resolution tool.  Windows can use it.

I went to a customer and could see the projector but had the same results as you, usplash and then nothing.

Most people where I work indicate success with Compiz turned off, but I have not tried it yet.  The old projector I have still doesn't work with Compiz off.

Any pointers would be helpful, I hate having to use XP...
I'll try it :)

---

### Post by mariner09 on 2008-11-20
I had the same results with using the display resolution tool.  The mirror setting never took.  I'm told that if it works with a CRT that it should work with a projector.  Might try that later today...

---

### Post by Keyper7 on 2008-11-20
Okay, let's forget the resolutions utility for a while.

Could you post the output of the command "xrandr" with the projector connected?

(just to be sure, reboot after connecting)

---

### Post by wersdaluv on 2008-11-20
> **Keyper7 said:**
> Okay, let's forget the resolutions utility for a while.

Could you post the output of the command "xrandr" with the projector connected?

(just to be sure, reboot after connecting)

I'm not in school now so I can't try the projector but I remembered that I have this [PC to TV Converter]("http://www.cdrking.com/local/products/index.php?action=mnu&temp=2&typeno=7034274-754362-258585024-9183538&prod=TV%20Tuner%20Devices&prodcode=8862340-236221-482106101-9429924") which I connect to my VGA port. It doesn't work anymore in Intrepid as well. It used to work in Hardy.

Here's xrandr while connected to the PC to TV converter ```
 xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1280 x 1280
VGA connected (normal left inverted right x axis y axis)
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 261mm x 163mm
   1280x800       59.8 +
   1024x768       60.0* 
   800x600        60.3  
   640x480        59.9  
TMDS-1 disconnected (normal left inverted right x axis y axis)
TV disconnected (normal left inverted right x axis y axis)

```

Whew. Even it doesn't work on Intrepid.

---

### Post by Keyper7 on 2008-11-21
Hm, so we can see that it *is* detected...

Okay, let's start with some basic experimenting. Try:

```
xrandr --output LVDS --mode 1280x800
```

(Or, if you're at school, try the equivalent for the projector. It might not be LVDS in this case.)

---

### Post by wersdaluv on 2008-11-21
> **Keyper7 said:**
> Hm, so we can see that it *is* detected...

Okay, let's start with some basic experimenting. Try:

```
xrandr --output LVDS --mode 1280x800
```

(Or, if you're at school, try the equivalent for the projector. It might not be LVDS in this case.)
Got no output. It didn't change anything

---

### Post by Keyper7 on 2008-11-22
Sorry, I'm a retard.

LVDS is your laptop screen, not the projector. VGA is the projector. Try:

```
xrandr --output VGA --mode 1152x864
```

You probably use your laptop screen at 1280x800, right? Then it makes sense that nothing happened with the previous command.

---

### Post by wersdaluv on 2008-11-22
> **Keyper7 said:**
> Sorry, I'm a retard.

LVDS is your laptop screen, not the projector. VGA is the projector. Try:

```
xrandr --output VGA --mode 1152x864
```

You probably use your laptop screen at 1280x800, right? Then it makes sense that nothing happened with the previous command.
Oh my, dude. You totally pwn. It worked. Where in the world do I get to learn those codes? Hehe.

How come I have to do this in Intrepid while it worked without tweaking on previous versions? Is there a GUI way to do this? :)

---

### Post by Arabiest on 2008-11-22
it works with me with no problems. Fujitsu Siemens T4210.

---

### Post by mariner09 on 2008-11-22
I can say that the projector I have does not show up when I type the xrandr -q command, but it can be used with a windows load.  When using under windows, the color is extremely red so what that tells me is that the cable might be bad enough not to allow xrandr to read it.  I may have a KVM cable I can try this with.

---

### Post by wersdaluv on 2008-11-23
> **Arabiest said:**
> it works with me with no problems. Fujitsu Siemens T4210.
On Intrepid? Mine is Fujitsu Esprimo U9200

---

### Post by Andy17MB on 2008-11-23
Bother..

Just when I Thought I had got to the bottom of my problem it doesn't work..  I have a slightly different setup.  I'm running Hardy on A sony vaio pgr-k115b.  Like Others I get everything upto the point of GDM starting on the external screen (I'm using a CRT monitor to test but will eventually hook up with a projector of the same resolution as the CRT).

Running xrandr -q with the CRT connected gives;
```
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1024 x 1024
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 267mm x 200mm
   1024x768       74.9*    75.1     70.1     60.0     43.5  
   832x624        74.6  
   800x600        84.9     85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     84.6     75.0     72.8     66.7     60.0  
   720x400        87.8     70.1  
DVI-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+   60.0  
   800x600        60.3  
   640x480        59.9  
S-video disconnected (normal left inverted right x axis y axis)

```

So something is seeing the external monitor (and it disappears if I disconnect it. Now if I follow the Instructions above and run:
```
xrandr --output VGA-0 --mode 1024x768
``` Nothing happens.

If I look at Gnome Screen resolutions nothing is detected (even if I press the detect displays button) and there is no option to mirror displays.  The Clone displays box is unticked.

Sorry to crash the query, but this seem so close to what I am struggling with it seemed to make more sense to post here than start a new thread

Any Suggestions appreciated

Andy

---

### Post by Keyper7 on 2008-11-23
wersdaluv, nice to see it worked. It's a little bit strange, though, because as far as I know the screen resolutions utility is nothing more than a GUI frontend to the xrandr command, so it should have worked...

There are other options available, such as Alberto Milone's UrandR ([http://albertomilone.com/urandr.html](http://albertomilone.com/urandr.html)) or the gnome-randr-applet (available in the repositories). Perhaps one of them will work for you as a temporary alternative GUI option. Meanwhile, it might be useful to file a bug explaining that the utility worked in Hardy but it does not in Intrepid (your board is quite common, though, so I'd guess that someone did it already)

Andy17MB, is your video board also an Intel?

---

### Post by Andy17MB on 2008-11-23
Keyper7

The video on the Sony is an ATI Radeon IGP345M

---

### Post by wersdaluv on 2008-11-23
> **Keyper7 said:**
> wersdaluv, nice to see it worked. It's a little bit strange, though, because as far as I know the screen resolutions utility is nothing more than a GUI frontend to the xrandr command, so it should have worked...

There are other options available, such as Alberto Milone's UrandR ([http://albertomilone.com/urandr.html](http://albertomilone.com/urandr.html)) or the gnome-randr-applet (available in the repositories). Perhaps one of them will work for you as a temporary alternative GUI option. Meanwhile, it might be useful to file a bug explaining that the utility worked in Hardy but it does not in Intrepid (your board is quite common, though, so I'd guess that someone did it already)

Andy17MB, is your video board also an Intel?
Amaaazing :D UrandR works and it has many options. Sweet! :D

---

### Post by Keyper7 on 2008-11-24
wersdaluv,

Milone's tools usually work very well, he's also the author of Envy.
Don't forget to thank him and send eventual bug reports. :)

Andy17MB,

Since I don't have an ATI card, everything I'll say should be taken with a grain of salt, as I have no means to test, but I'll try to help anyway. Are you using the proprietary ATI drivers? The proprietary drivers usually do not work very well with the usual Linux ways of doing things. Instead, they rely on their own proprietary tools.

If I remember correctly, the ATI tool is known as "Catalyst". Is it installed in your computer?

---

### Post by wersdaluv on 2008-11-24
Awww. I was supposed to use my laptop for our presentation in school earlier. The projector connected on my VGA out isn't detected by Ubuntu. Oh well. I'll see if other projectors in school work.

---

### Post by Keyper7 on 2008-11-25
DAMN!

I think I'm as disappointed as you are... :)

But not being detected is strange... is it detected by Windows?

---

### Post by wersdaluv on 2008-11-25
We used my classmates laptop running Windows. Didnt try my windows

---

### Post by Andy17MB on 2008-11-25
Keyper7,

I'm running the open source driver, I don't think the "official" ATI one supports my chipset

---

### Post by Keyper7 on 2008-11-26
Okay Andy, let's go back to xrandr.

Did you try all the resolutions available for VGA-0? None of them worked?

What about error messages when you try?

---

### Post by Andy17MB on 2008-11-28
Keyper7,

Tried all 5 reported resolutions:> 
sudo xrandr --output VGA-0 --mode 1024x768
xrandr -q
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1024 x 1024
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 267mm x 200mm
   1024x768       74.9*    75.1     70.1     60.0     43.5  
   832x624        74.6  
   800x600        84.9     85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     84.6     75.0     72.8     66.7     60.0  
   720x400        87.8     70.1  
DVI-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+   60.0  
   800x600        60.3  
   640x480        59.9  
S-video disconnected (normal left inverted right x axis y axis)
sudo xrandr --output VGA-0 --mode 832x624
sudo xrandr --output VGA-0 --mode 800x600
sudo xrandr --output VGA-0 --mode 640x480
sudo xrandr --output VGA-0 --mode 720x400

There are no error messages, but I can see that the LCD screen on the laptop refresh.  Nothing happens on the CRT monitor I am using to test, but as I mentioned previously when I boot up the laptop with the CRT connected I get the boot up text and Ubuntu splashscreen and then it blanks as soon as GDM kicks in.  Also tried xrandr without the Sudo, but no difference.

Andy

---

### Post by Keyper7 on 2008-11-28
It might be that your board does not fare well with xrandr itself.

Does it work to change the resolution in the laptop LCD through xrandr?

---

### Post by Andy17MB on 2008-11-28
Keyper7,

I can use Xrandr quite happily to swap resolution on the panel, so doesn't look like it's that..

I've been looking at the /var/log/Xorg.0.log and it clearly picks up the presence of the external VGA output on boot up, but then disconnects it:
> in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): Output LVDS connected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Output LVDS using initial mode 1024x768
after xf86InitialConfiguration

Not sure if that helps but that certainly seems to be where it is disabled

Andy

---

### Post by Keyper7 on 2008-11-30
(sorry, couldn't use the computer yesterday)

What really intrigues me is that xrandr does detect the other output and does not give any error message. Try using xrandr again, this time with the -v option to see if it says at least something.

I'm inclined to guess that some extra parameters in xrandr might solve this.

---

### Post by Andy17MB on 2008-11-30
Keyper7,

not to worry I was at a wedding and in no danger of making any sense anyway..  Thanks for looking at this again.

If I try ¨xrandr -v" it reports > Server reports RandR version 1.2

If I Try > xrandr -v --output LVDS --mode 800x600
it does as it&#347; told and there is no error message.  I  get the same result if I try and route the output to VGA-0

Deeply puzzled..
Andy

---

### Post by Keyper7 on 2008-12-01
Do you have any other output options to test? Like a svideo cable and a TV?

When I have some more time today I'll search for common xrandr problems and workarounds.

---

### Post by Andy17MB on 2008-12-01
Keyper7,

There is an s-video out on this Vaio, but I`m struggling to find a lead, so i`ll try and get one tomorrow and try then

Cheers again 

Andy

---

### Post by Keyper7 on 2008-12-02
By the way, Andy, did you test the projector with Windows?

---

### Post by Andy17MB on 2008-12-04
Keyper7,

Finally found a lead to link to the TV & surprise, surprise nothing works.  Xrandr shows an S-video out, but shows it as disconnected, even when I have a lead connected.  I don remember ever trying this out under windows, so don`t know whether this gets us any further.  If I run xrandr -q with the --verbose option it does recognise that there is an s-video interface and that it is sset to NTSC.  Even so if it put out an ntsc picture I should see something on a PAL TV.  

I`ve also seen the projector running with windows

thanks again 
Andy

---

### Post by Keyper7 on 2008-12-05
The only thing that's left for me to suggest is to manually tweak your /etc/X11/xorg.conf.

Have you ever did this before? Don't worry if you don't, just create a back up of it and you can mess with it as much as you like. Any problems, just revert to the backup.

It might be that you'll need to add a custom modeline. This guide here might help you to get started:

[http://www.mythtv.org/wiki/index.php/Working_with_Modelines](http://www.mythtv.org/wiki/index.php/Working_with_Modelines)

Please let me know if you have any problems. Meanwhile I'll search for easier alternatives.

---

### Post by Andy17MB on 2008-12-16
Keyper7,

Had my nose firmly pressed to the Grindstone, so not been able to try anything until today, But I think I am making some progress.  The modlines article was good, but I think the problem may be  abit more basic than that.  Here`s the relevant chunk of my xorg.conf file:
> Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

I am assuming I need a ¨monitor¨ section for the external monitor/projector (in which I can tweak modlines if needed) and a ¨screen¨ section to link the external monitor with the VGA-0 output of the graphics card.  It looks like something is storing the monitor data elsewhere, but i can not figure what or where.

I`ve also had a fish in /var/log/Xorg.0.log, and Xserver seems to pick up the external monitor (and provide all the data needed if modlines are required - takes a bit of hunting down, but it`s there)

I`m definitely on the edge of my comfort zone here, so before I start B*******g things up does this sound along the right lines?  Any suggestions?

CHeers again

Andy

---

### Post by Andy17MB on 2008-12-17
I think I'm onto the problem now... Just had a hitch with my Xorg.conf and got prompted to manually configure the display driver, and Guess what... Up comes the external display along with the main display, admitedly only at 800x600, but at least it worked.  Xrandr only showed one available screen, so the display driver wasn't quite right.  Reconfigured Xorg to autodetect the graphics card to try and sort this and to get 1024x768 back and surprise, surprise no external monitor.  I'll soldier on with experiments into the right driver and let you all know what I find..

Andy

---

