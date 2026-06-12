---
title: "Touchpad not working (Jaunty)"
date: 2009-04-27
forum: Hardware
---

### Post by mungojerrie2 on 2009-04-27
hi all

I have just installed (from scratch) the new released ubuntu jaunty 9.04 and am happy with it, but I have a rather annoying problem, my touchpad is not working, so I must use external mouse.

I have read via google that previous kernels had this problem but it is said to be fixed with a kernel with lower number than jaunty's

Anyone experience the same?

---

### Post by reeko124 on 2009-04-27
I am having the same exact problem. Thats my only problem with it. It looks and runs real nice otherwise. I read one thread about changing something and I did but it didn't work.

---

### Post by python_king on 2009-04-28
I also in the similar case.

Here is the details of my case:
Hi folks,

I'm new to ubuntu (and linux) world. I bought a new laptop in mid of April 2009.

The laptop is Toshiba Satellite L310-P406. The laptop is only come with Free-DOS.

As I knew that the latest ubuntu (9.04 - Jaunty Jackalope) is going to release soon (at that time I bought the laptop),
so I did not install any OS into the laptop and waiting for the latest release of Jaunty.

Last weekend, I downloaded Jaunty and installed it into my laptop.
Then, I found out that the TOUCHPAD DOES NOT WORKING! I only can use usb mouse to move the cursor.
Is that any driver / configuration needed to active the touchpad? or that's my hardware problem?
Any folks can share your idea / solution? 
fyi, i does not have internet connection at home and i am not free to go starbucks online in this few days.

Thanks for your advise.

---

### Post by magicke on 2009-04-28
Same problem here using an Acer 4530 amd64.

I upgraded to Jaunty last weekend and lost touchpad functionality after restarting the laptop.

I tried reinstalling all the installed mouse-related drivers using the synaptic package manager, just in case something had gone wrong during the upgrade that I hadn't noticed, but no improvements occurred.

I hope someone from the community can help out.

---

### Post by zambiandreams on 2009-04-29
Another with the same problem. I am using a Sager NP6630, and had full touchpad capibilities with 8.10.

---

### Post by python_king on 2009-04-29
> **python_king said:**
> I also in the similar case.

Here is the details of my case:
Hi folks,

I'm new to ubuntu (and linux) world. I bought a new laptop in mid of April 2009.

The laptop is Toshiba Satellite L310-P406. The laptop is only come with Free-DOS.

As I knew that the latest ubuntu (9.04 - Jaunty Jackalope) is going to release soon (at that time I bought the laptop),
so I did not install any OS into the laptop and waiting for the latest release of Jaunty.

Last weekend, I downloaded Jaunty and installed it into my laptop.
Then, I found out that the TOUCHPAD DOES NOT WORKING! I only can use usb mouse to move the cursor.
Is that any driver / configuration needed to active the touchpad? or that's my hardware problem?
Any folks can share your idea / solution? 
fyi, i does not have internet connection at home and i am not free to go starbucks online in this few days.

Thanks for your advise.


**Problem Solved**
The stupid user does not on his laptop touchpad (FN + Fx key) :lolflag:

Besides, i think you can try "xinput list" to check is the touchpad being detected or not.

---

### Post by Matataki on 2009-04-29
I am having the same problem as everybody else it seems. My touchpad is being recognized by the system, as the buttons still work, but the touchpad itself accepts no response from the user.

I've tried messing with all of the settings in the mouse control panel, but that changes nothing for me. If I disable the touchpad in the settings the buttons cease working, but nothing seems to help me in making the trackpad work!

My system is an Averatec 3715, a few years old.

Following is the output of my 'xinput list'

```

kyle@craptop:~$ xinput list
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
"Macintosh mouse button emulation"	id=2	[XExtensionPointer]
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
"AT Translated Set 2 keyboard"	id=3	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"ETPS/2 Elantech Touchpad"	id=4	[XExtensionPointer]
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 32
		Max_value is 544
		Resolution is 1
	Axis 1 :
		Min_value is 32
		Max_value is 352
		Resolution is 1
"Video Bus"	id=5	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Logitech Optical USB Mouse"	id=6	[XExtensionPointer]
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

```

Any help would be much appreciated.

---

### Post by Matataki on 2009-04-30
I found a solution to my above problem, but as a result there are no longer any touchpad controls in the system panel. Although tap to click and the like can't be disabled with this method, it works as a last ditch method:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/315882/comments/33](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/315882/comments/33)

If anybody finds a better solution then that'd be pretty :guitar:.

---

### Post by shl_junk on 2009-04-30
Based on what Mataki said, I tried his solution.

The problem is when I type:

modprobe -r psmouse

I get this:

[COLOR=#000000][FONT=Tahoma]FATAL: Error removing psmouse (/lib/modules/2.6.28-11-generic/kernel/drivers/input/mouse/psmouse.ko): Operation not permitted

I don't know what else I can do ... I do know the buttons work, but touchpad not moving the cursor at all.

===========================

Oops, spoke too soon ... I figured it out with help of a friend.  Touchpad now works.
[/FONT][/COLOR]

---

### Post by mungojerrie2 on 2009-05-01
just follow this link
and add "sudo" to all commands
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/315882/comments/33](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/315882/comments/33)
that worked for me :-)

---

### Post by magicke on 2009-05-01
hmm...that didnt work for me. now the touchpad tab in the mouse config applet is gone and i dont know how to get it back 
:(

---

### Post by shl_junk on 2009-05-01
Thanks everyone.  I was able to make this work last night.  I woke up, booted up the laptop again and the touchpad doesn't move the cursor again.

So does that mean I will have to do this every time?  If so, I better copy and paste the instructions and put it on the desktop.

---

### Post by Matataki on 2009-05-02
If you do the

and add: options psmouse proto=imps
to: gedit /etc/modprobe.d/options

step in the posted solution it'll initialise on every bootup.

---

### Post by rharagon on 2009-05-02
You say you fixed it with the help of a friend.  Could you explain?  I'm having the same problem - getting the same FATAL etc. message.  What did you do to fix it?

---

### Post by shl_junk on 2009-05-03
I haven't tried Mataki's latest comment yet.  When I said I fixed it with a friend's help, I found out I wasn't typing "sudo" in front of what Mataki posted.  Once I figured that out, from the terminal, you would type:

sudo modprobe -r psmouse

Hit ENTER

Then, it will ask for your password.  You type it in and hit ENTER.

Then you type:

sudo modprobe psmouse proto=imps

Hit ENTER

At this point, I moved my cursor and it moved.  

===============

If Mataki is still reading this thread and if he's patient, can you please go through it step by step with the rest of your directions?  I'm really new with Ubuntu and Linux.

---

### Post by TheMusicGuy on 2009-05-03
Thank you, Matataki! :KS

I was having the same issue as everyone else with my toucpad being reported as "ETPS/2 Elantech Touchpad" by `xinput list` and not working, except for the buttons. Then I tried the following commands, adapted from Matataki's bug report:

```

sudo modprobe -r psmouse
sudo modprobe psmouse proto=imps

```

When I tried doing this from an X terminal emulator it made the X server freeze and I was unable to use ANY mouse or keyboard. But then I restarted my system and tried the commands again from the (non-X) tty terminal, and now the touchpad works just fine. Adding the option to /etc/modprobe.d/options worked as intended also, but I had to actually create the "options" file first.

Edit:

I've created a blog entry to summarize this issue and its solution at the following url: [http://tmg-vs-tech.blogspot.com/2009/05/curing-jauntys-fear-of-touchpads.html](http://tmg-vs-tech.blogspot.com/2009/05/curing-jauntys-fear-of-touchpads.html)

---

### Post by shiggs on 2009-05-04
> **TheMusicGuy said:**
> Thank you, Matataki! :KS

I was having the same issue as everyone else with my toucpad being reported as "ETPS/2 Elantech Touchpad" by `xinput list` and not working, except for the buttons. Then I tried the following commands, adapted from Matataki's bug report:

```

sudo modprobe -r psmouse
sudo modprobe psmouse proto=imps

```

When I tried doing this from an X terminal emulator it made the X server freeze and I was unable to use ANY mouse or keyboard. But then I restarted my system and tried the commands again from the (non-X) tty terminal, and now the touchpad works just fine. Adding the option to /etc/modprobe.d/options worked as intended also, but I had to actually create the "options" file first.

Edit:

I've created a blog entry to summarize this issue and its solution at the following url: [http://tmg-vs-tech.blogspot.com/2009/05/curing-jauntys-fear-of-touchpads.html](http://tmg-vs-tech.blogspot.com/2009/05/curing-jauntys-fear-of-touchpads.html)


this worked for me, but i have a synaptics touchpad, "xinput list" added the following 

```

"ImPS/2 Synaptics TouchPad"	id=6	[XExtensionPointer]
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

```

...which was lacking prior, not sure if it will persist on reboot. Will report back if not.

---

### Post by TheMusicGuy on 2009-05-06
It will not persist until you put the options into /etc/modprobe.d. To do that, run this line:

```
sudo echo "modprobe psmouse proto=imps" >> /etc/modprobe.d/touchpadfix.conf
```

Btw, my xinput list gives the following:
```
"ImPS/2 Generic Wheel Mouse"    id=5    [XExtensionPointer]
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
```

Although I sometimes have a wheel mouse attached, I didn't when I ran xinput list. Odd, but no harm done.

---

### Post by clandestino on 2009-05-10
Hello everybody

I have a eeepc 901 and I've been struggling with the elantech touchpad since I've upgraded to jaunty. I remember having some issues even with 8.10...
After the jaunty installation the touchpad worked fine, well with a little slow response but it worked. Then, without installing anything special, the touchpad stopped working from time to time: I mean sometimes I started the laptop and I had no touchpad. It was a very random behavior, but after a while it went away completely and I started working with a small usb mouse.
Today I've upgraded to the array.org kernel (2.6.28-12-netbook-eeepc) and decided to fix the touchpad issue. Well I found your post and tried  Matataki's solution.
Here is what I get:

xinput list
[INDENT]"Virtual core pointer"  id=0    [XPointer]
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
"Virtual core keyboard" id=1    [XKeyboard]
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
"Synaptics Touchpad"    id=2    [XExtensionPointer]
        Num_buttons is 12
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
"Asus EeePC extra buttons"      id=3    [XExtensionKeyboard]
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
"AT Translated Set 2 keyboard"  id=4    [XExtensionKeyboard]
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
"Video Bus"     id=5    [XExtensionKeyboard]
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
"USB Mouse"     id=6    [XExtensionPointer]
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
                Resolution is 1[/INDENT]


sudo modprobe psmouse proto=imps
[INDENT]FATAL: Error inserting psmouse (/lib/modules/2.6.28-12-netbook-eeepc/kernel/drivers/input/mouse/psmouse.ko): Unknown symbol in module, or unknown parameter (see dmesg)[/INDENT]

here is what dmesg gives:
[INDENT][ 1451.237133] psmouse: Unknown parameter `elantech'[/INDENT]

Strange enough I have no elantech.c file on my system and the 
/usr/src/linux-headers-2.6.28-12-netbook-eeepc/include/config/mouse/ps2/elantech.h file is empty

I hope somebody has an idea about what's going on ...

Thanks a lot

---

### Post by pato101 on 2009-05-13
I've experimented same issue: touchpad stopped working since I upgraded to array.org kernel (which boots quite faster, btw), in my eee901. I had 8.10 + array.org and I upgraded to 9.04 and then re-enabled array.org repos and installed array.org kernel.

I've seen that in /etc/modprobe.d/eeepc there is a line which says

options psmouse elantech=1

commenting it just does the trick for me! (after reboot). I'm not sure if I'm using all the touchpad features, but does the two-finger wheel effect and I don't have to popup touchpad properties window in order to enable that any more.

---

### Post by sakris on 2009-06-07
i had a similar issue with my laptop. Make sure you've not locked the touch pad using the function key (lock)!:D

---

### Post by koelimaya on 2009-06-28
> **mungojerrie2 said:**
> just follow this link
and add "sudo" to all commands
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/315882/comments/33](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/315882/comments/33)
that worked for me :-)

thanks.. it's work on my laptop / axioo centaur SL 726

---

### Post by gmoctav on 2009-07-18
it might be solved for you . but my touch-pad is still not working, after reinstalling ubuntu 9.10 . I've been using jaunty since the release , and the laptop worked flawlessly (except the fan ) . now I've got this problem...hmmm

---

### Post by vishal khialani on 2009-07-23
Hi,
Like many of the earlier users I am also facing a problem on my touchpad. I am new to linux.

I first tried to use the xinput list and the below result shows no touchpad :( 

Virtual core pointer"  id=0    [XPointer]
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
"Virtual core keyboard" id=1    [XKeyboard]
        Num_keys is 248                    
        Min_keycode is 8                   
        Max_keycode is 255                 
"AT Translated Set 2 keyboard"  id=2    [XExtensionKeyboard]
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
"Video Bus"     id=3    [XExtensionKeyboard]
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
"Macintosh mouse button emulation"      id=4    [XExtensionPointer]
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
"USB U+P Mouse" id=5    [XExtensionPointer]
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


I then tried the below command as suggested which also did not work.


modprobe -r psmouse
modprobe psmouse proto=imps
 

I am not sure what should I do I know I am having a Elantech touchpad on my laptop and it works fine under windows. I am using an axioo ml 058  and my os details are Linux vishal-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux


Hope someone can help me here :)



Cheers,
Vishal Khialani

---

### Post by neologix on 2009-08-19
i just tried this modprobe trick to fix my elantech touchpad and while it works for me, i want to restore the touchpad tab of the mouse control panel. how can i do this?

---

### Post by murchball on 2009-08-31
Adding the line

options psmouse proto=imps

to /etc/modprobe.d/options got my touchpad working on my Alienware Sentia. Thanks a bunch, I've had this issue for a while, but always just attached a usb mouse. Not very portable.

---

### Post by Bender2k14 on 2010-04-28
If your problem is the touchpad being recognized as a wheel mouse, then the following links my be helpful.

Bug report:
[http://ubuntuforums.org/showthread.php?p=9175201#post9175201](http://ubuntuforums.org/showthread.php?p=9175201#post9175201)

...and thread:
[http://ubuntuforums.org/showthread.php?p=9175201#post9175201](http://ubuntuforums.org/showthread.php?p=9175201#post9175201)

---

