---
title: "Gigabyte T1005M Can't detect Touch Pad but Touch Screen works"
date: 2010-12-24
forum: Hardware
---

### Post by Captain_Glen on 2010-12-24
Hi,

I wanted to try out the new multitouch features of Ubuntu 10.10.  So I bought the Gigabyte T1005M.  I wasn't sure if it would work.  But I figured it was worth a shot.

Anyway long story short.  The touch screen works pretty much out of the box.  But the touchpad isn't even detected.

To get the touchscreen to work properly I had to go System -> Preferences -> Input Method Switcher and select Remove user choice to enable system choice.  Otherwise it worked but did not move the mouse to where you touched.  Instead you had to drag it to where you wanted and then click.  But now it works.

However Ubuntu can't even detect the touchpad?  Any ideas on how I can solve this?

Also I want to test out the multitouch gestures on the touch screen?  I have installed utouch and the multitouch gesture gtk packages from the app store.  But I don't have two finger scrolling or any of the other cool features shown in the demo video for ubuntu multitouch.  How do I turn them on?

Lastly the keyboard tends to misbehave too.  Sometimes it just repeats key presses when I press the same key a few times quickly.  Backspace is the worst!!

Thanks,
Glen.

---

### Post by Captain_Glen on 2010-12-24
So I've made some progress on getting the gestures working:

I followed this guide: [http://ubuntuforums.org/showthread.php?t=1252492&page=128]("http://ubuntuforums.org/showthread.php?t=1252492&page=128")

Any way if I run ginn in the terminal, then some gestures work.  But the four fingered ones don't.  :(

I also tried "gesturetest 0 0 0xfff" in the terminal.  This did an okay job of recognising 2 fingered gestures.  But reported 3 and 4 fingered gestures as only two fingers.  The screen on the T1005M is capacitive so I can't imagine that it is a hardware problem???

Any ideas?

Also I have not made an progress on the touch pad yet.

---

### Post by m_b_o on 2010-12-24
Hi,

to get the touchpad working you have to add a boot parameter.

In **/etc/default/grub** add **i8042.noloop=1** to **GRUB_CMDLINE_LINUX_DEFAULT**

After that it should look something like this

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.noloop=1"

Make **sudo update-grub **and reboot and the touchpad should work. :D

For the key repeat issue I've found no solution. The only thing that helped, was to disable the key-repeat feature in the keyboard settings. 

Gestures I haven't tried so far, is it worth?
Is your fan also running most of the time?

greets

---

### Post by Captain_Glen on 2010-12-24
Cheers mate.

Touch pad is working!!! :D

So is two< fingered scrolling.

My fan is running atm.  But it is not very loud.  I don't know if it has been running all day, if it was I did not notice.  I'll check it out tomorrow and post back.

Regarding gestures.  I reckon that is the coolest feature about the multitouch gestures.

---

### Post by m_b_o on 2010-12-24
And to get the suspend mode to work add the file **/etc/pm/sleep.d/20_custom-xhci_hcd**

[HTML]
#!/bin/sh
# File: "/etc/pm/sleep.d/20_custom-xhci_hcd".
TMPLIST=/tmp/xhci-dev-list

case "${1}" in
        hibernate|suspend)
    echo -n '' > $TMPLIST
          for i in `ls /sys/bus/pci/drivers/xhci_hcd/ | egrep '[0-9a-z]+\:[0-9a-z]+\:.*$'`; do
              # Unbind ehci_hcd for first device XXXX:XX:XX.X:
               echo -n "$i" | tee /sys/bus/pci/drivers/xhci_hcd/unbind
           echo "$i" >> $TMPLIST
          done
        ;;
        resume|thaw)
    for i in `cat $TMPLIST`; do
              # Bind ehci_hcd for first device XXXX:XX:XX.X:
              echo -n "$i" | tee /sys/bus/pci/drivers/xhci_hcd/bind
    done
    rm $TMPLIST
        ;;
esac[/HTML]After that do a [B]chmod 755 /etc/pm/sleep.d/20_custom-xhci_hcd

[/B]Described here: [http://ubuntuforums.org/showthread.php?t=1444822](http://ubuntuforums.org/showthread.php?t=1444822)

greets

---

### Post by Captain_Glen on 2010-12-24
Thanks again.  That trick about suspending works a treat.

Regarding the fan, it does appear to be on all the time.  Better on too much than too little, mind you I doubt it helps out with power usage.

The biggest problem though is that when I unplug the power cord the laptop goes into suspend mode.  It use to just crash on an error about power management.  But now that it can successfully suspend it does that instead.

Merry Christmas and thanks again for your help.

---

### Post by m_b_o on 2010-12-25
Your welcome!  ;)

Merry Christmas!

---

### Post by brukutu on 2010-12-27
Hi. Also got a t1005m.
Running jolicloud (based on ubuntu).
Got suspend working, touchpad working, touchscreen wrking.


Things still needed to sort out:
Touchscren calibration
cant find anyway to calibrate my screen (cando multitouch)
its 95% accurate so not such a biggie. any ideas?


Screen rotation
wrote a script to ratate it, works great..but touchscreen doesnt rotate...any ideas? found lots of guides, but not any for the cando....

Sidekey binding
trying acpi listen and x events...cant pick it up anywhere...any1 ideas?

---

### Post by Captain_Glen on 2010-12-27
Can you do the multitouch gestures shown in the demo video here: [http://blip.tv/file/4245457/]("http://blip.tv/file/4245457/")

Let me know if you make any progress with the to the other issues.

---

### Post by brukutu on 2010-12-27
> **Captain_Glen said:**
> Can you do the multitouch gestures shown in the demo video here: [http://blip.tv/file/4245457/]("http://blip.tv/file/4245457/")

Let me know if you make any progress with the to the other issues.

I wish. 
Forgot to mention that multi touch doesnt work.
i may have a solution thou.
I use linux on a daily basis (arch linux on desktop), but i am not very clued up when it comes to drivers apart from the usual modprobe.
Anyhow, this may put on of you in the right that, on the opensuze moblin remix, i think it goes by the name of goblin, multitouch works on the t1005m out of the box. If i remembered correctly, 2-finger touch drags. If any1 could look into it and maybe find out the solution?

After looking at that video, makes me wanna switch to UNR, any of you use it with the t1005m? When i tried, it recognized my touchscreen sort of like a touchpad....drag the pointer with it and tap to click, not like the normal touchscreen...that was/is really the only thing that is holding me back to go UNR. Jolicloud is nice, but somewhat to limited for my liking.

Any1 has any more information on this netbook on linux? seems to be a very limited amount of information on the forums and around the net.

One more problem, sometimes my keys "stick". not phisycally, but I press another key, they keep repeating....

---

### Post by brukutu on 2010-12-27
seen that you fix touchscreen touchpad issue on 1st post, i rate i am switching to UNR. :)

---

### Post by Captain_Glen on 2010-12-27
I am running ubuntu desktop version, as the netbook remix is too slow because they are using mutter instead of compiz.

Anyway I got the touchscreen working.  As mentioned in my original post:

To get the touchscreen to work properly I had to go System -> Preferences -> Input Method Switcher and select Remove user choice to enable system choice.

Also multitouch works with the two fingered gestures on the touchscreen.  Try pinch zoooming in eye of gnome and also rotating.  Install utouch and then run "ginn" from cmd line to test it.

However the 3 & 4 fingered gestures don't seam to work.  If you run "gesturetest 0 0 0xfff" from cmd line you can see that ubuntu thinks 3 & 4 fingered gestures are only two fingered.

Keep me posted on how you go.  Especially if you can fix the keyboard overflow problem.

Thanks,
Glen.

---

### Post by brukutu on 2010-12-27
so u rate its better to run desktop rather then UNR?

when i tried unr it seemed a little slow, also for you?

---

### Post by brukutu on 2010-12-27
> **Captain_Glen said:**
> I am running ubuntu desktop version, as the netbook remix is too slow because they are using mutter instead of compiz.

Anyway I got the touchscreen working.  As mentioned in my original post:

To get the touchscreen to work properly I had to go System -> Preferences -> Input Method Switcher and select Remove user choice to enable system choice.

Also multitouch works with the two fingered gestures on the touchscreen.  Try pinch zoooming in eye of gnome and also rotating.  Install utouch and then run "ginn" from cmd line to test it.

However the 3 & 4 fingered gestures don't seam to work.  If you run "gesturetest 0 0 0xfff" from cmd line you can see that ubuntu thinks 3 & 4 fingered gestures are only two fingered.

Keep me posted on how you go.  Especially if you can fix the keyboard overflow problem.

Thanks,
Glen.

Runing ubuntu desktop mavaerick now. Did your trick for the touch screen, no help...
What is yoru "system choice"?

my default is setting by the sysadmin.
what is urs?
i am afraid it is reseting to the wrong one.

---

### Post by brukutu on 2010-12-27
> **brukutu said:**
> Runing ubuntu desktop mavaerick now. Did your trick for the touch screen, no help...
What is yoru "system choice"?

my default is setting by the sysadmin.
what is urs?
i am afraid it is reseting to the wrong one.

touchscreen is now working!
had to patch evdev and comfile it from src

gestures not yet ....
cant get ginn to work...compile, install, run...then what? it says it loaded the gestures, but nothing.....also, what am i suppose to see from gesture test program? i see nothing :(

what drive u using for touchscreen
help plz, i want gestures..(thinking my driver only single touch)

---

### Post by Captain_Glen on 2010-12-28
Okay so:

> cant get ginn to work...compile, install, run...then what? it says it loaded the gestures, but nothing.....also, what am i suppose to see from gesture test program? i see nothing

```
sudo apt-get install ginn
ginn
```

That is all I did.  You should see output working in the terminal when you do a gesture.  Try pinch zooming in eye of gnome and                         make sure the terminal running ginn shows you did a pinch.

> touchscreen is now working!
had to patch evdev and comfile it from src

I did not have to do this.  Maybe that is why ginn does not work.  I just installed utouch and everything touch related in the software centre.

> so u rate its better to run desktop rather then UNR?

I tried UNR on my sisters aspire one.  It sucked so I did not even try it on my T1005M.  But I did install cairo dock from the software centre.  I rate it over UNR.

---

### Post by brukutu on 2010-12-29
> **Captain_Glen said:**
> Okay so:



```
sudo apt-get install ginn
ginn
```That is all I did.  You should see output working in the terminal when you do a gesture.  Try pinch zooming in eye of gnome and                         make sure the terminal running ginn shows you did a pinch.



I did not have to do this.  Maybe that is why ginn does not work.  I just installed utouch and everything touch related in the software centre.



I tried UNR on my sisters aspire one.  It sucked so I did not even try it on my T1005M.  But I did install cairo dock from the software centre.  I rate it over UNR.




bruk@bruk-tab:~$ sudo apt-get install ginn
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ginn

---

### Post by Captain_Glen on 2010-12-29
Did you add the utouch repository?

Try installing from the software centre it is probably easier.

Otherwise I think it is 

```
sudo add-apt-repository ppa:utouch-team/utouch
sudo apt-get update 
sudo apt-get install utouch ginn
```

---

### Post by brukutu on 2010-12-29
> **Captain_Glen said:**
> Did you add the utouch repository?

Try installing from the software centre it is probably easier.

Otherwise I think it is 

```
sudo add-apt-repository ppa:utouch-team/utouch
sudo apt-get update 
sudo apt-get install utouch ginn
```


nope installed from source.....
had to resintall laptop, tried ur method to make touch screen work, worked fine..ginn working. didnt play with it eought, but seems like its only doing 2 touche gestures?

ur side?

---

### Post by Captain_Glen on 2010-12-29
Same result here.  Only one and two fingered gestures work on the touch screen.

Also when I run gesturetest 0 0 0xfff it reports 3 and 4 fingered gestures as 2 fingered.

However the touch pad has multitouch with more fingers.  2 fingers to middle click and 3 fingers to right click.  I like it.

Does yours suspend when you unplug the power?

-Glen.

---

### Post by brukutu on 2010-12-29
> **Captain_Glen said:**
> Same result here.  Only one and two fingered gestures work on the touch screen.

Also when I run gesturetest 0 0 0xfff it reports 3 and 4 fingered gestures as 2 fingered.

However the touch pad has multitouch with more fingers.  2 fingers to middle click and 3 fingers to right click.  I like it.

Does yours suspend when you unplug the power?

-Glen.
It did once upon a time. 
That is something i can help you out with.

Not an ideal solution but much better then suspend on power on or off.

Go to power setting and change both the setiing on battery and ac power (when closing laptop lid) to blank screen.

It will then only blank the screen (rrestored by a simple touch or keypress) rather then suspending. 

hope that is better?


Any news on rotation?
I can rotate screen no probablem, but cant rotate screen calibration without restarting X.....(not accpeptable)...

Also on the gestures note, do you know applications names? on the wishes.xml file you can set specific gestures for spefic apps, and i am strugling to get specific gestures working only for firefoxx for example....i think i have the wrong "application name"

---

### Post by brukutu on 2010-12-29
got it!
FInally tablet rotation with touchscreen rotated! 

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1415915&page=35](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1415915&page=35)
post 349

Change device id in it and it works! 




do u have any idea how to get that side key on the t1005m to launch this script? cant pick up the key anywhere!

---

### Post by m_b_o on 2010-12-30
> **Captain_Glen said:**
> ```
sudo add-apt-repository ppa:utouch-team/utouch
sudo apt-get update 
sudo apt-get install utouch ginn
```

Followed this, copied /usr/share/ginn/wishes.xml  to /etc/wishes.xml and multitouch worked.
However, in Firefox I like the[ Grab and Drag Extension]("https://addons.mozilla.org/de/firefox/addon/1250/") much more.

---

### Post by brukutu on 2010-12-30
> **m_b_o said:**
> Followed this, copied /usr/share/ginn/wishes.xml  to /etc/wishes.xml and multitouch worked.
However, in Firefox I like the[ Grab and Drag Extension]("https://addons.mozilla.org/de/firefox/addon/1250/") much more.


THanks for the hint with the firefox add on. did you try the screen rotation? working well...

Any ideas how to  bind the button on the side to do anything? cant pick it up anywhere!

I got gestures working, but if you look inside that wishes.xml, you can make your own gestures for specific applications....that is what i am trying to get to.....

---

### Post by m_b_o on 2010-12-31
Screen rotation works, but I've no glue how to bind the hardware button to the script...

Following this guide [http://samiux.blogspot.com/2010/11/howto-ubuntu-1010-on-gigabyte-touchnote.html](http://samiux.blogspot.com/2010/11/howto-ubuntu-1010-on-gigabyte-touchnote.html) for screen calibration with*[FONT=Arial] xinput_calibrator [/FONT]*works fine. If you are on 64-bit, you have to compile it, but for 32-bit there is a .deb to download.

---

### Post by brukutu on 2011-01-02
> **m_b_o said:**
> Screen rotation works, but I've no glue how to bind the hardware button to the script...

Following this guide [http://samiux.blogspot.com/2010/11/howto-ubuntu-1010-on-gigabyte-touchnote.html](http://samiux.blogspot.com/2010/11/howto-ubuntu-1010-on-gigabyte-touchnote.html) for screen calibration with*[FONT=Arial] xinput_calibrator [/FONT]*works fine. If you are on 64-bit, you have to compile it, but for 32-bit there is a .deb to download.

Came right with just a script and x commands.

No news on hardware button?

---

