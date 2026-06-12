---
title: "Help configuring multi-touch input for hp tx2 1275 dx"
date: 2011-12-27
forum: Hardware
---

### Post by homer1234 on 2011-12-27
Hi there,

First of I would like to admit that I am a noob. I don't like being a noob, but everyone has to be there at some point. I look forward to learning more about this wonderful OS in order to no longer be a noob and therefore contribute to this community as much as I can.

That being said, I was wondering if I could get any advice on how to configure multi touch on my hp tx2 1275 dx. 

I am running ubuntu 11.10 
kernel is 
Linux TX2-tab 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

The touch screen on my computer is 

Bus 007 Device 003: ID 1b96:0001 N-Trig Duosense Transparent Electromagnetic Digitizer

I already have (out of the box) the ability to use my finger to control the cursor but only for one single touch point. My goal is to hopefully get it so that I can use as many fingers as my hardware supports.

Research already done:

I have looked at multiple threads and pages for any info on how to do this. All of the threads that I have found seem to be applicable to 11.04 or earlier. 
Furthermore, I have checked [http://lii-enac.fr/en/architecture/linux-input/multitouch-howto.html](http://lii-enac.fr/en/architecture/linux-input/multitouch-howto.html) and have verified that my n-trig screen is included on the list of supported devices. That being said, there appears to be no generic driver. According to ENAC, this means that

"if your kernel is more recent than the version number in the rightmost    cell, your panel should be supported automatically. However, it will only    have the single touch emulation and work with older multitouch demos (protocol    A). If you are using a Linux distro, you can proceed to    [How to test...]("http://lii-enac.fr/en/architecture/linux-input/multitouch-howto.html#test") below. If you are using an Android, refer to    our [Android howto]("http://lii-enac.fr/en/architecture/linux-input/multitouch-android-howto.html")."

This of course tells me only what I already know. 

The piece of tantalizing evidence that prompted me to do all of this research in the first place was originally this video
[http://www.youtube.com/watch?v=CH6kxNRYz20](http://www.youtube.com/watch?v=CH6kxNRYz20)

Which links to [http://ubuntuforums.org/showthread.php?t=1252492](http://ubuntuforums.org/showthread.php?t=1252492) as the how-to

Unfortunately, that page is definitely beyond me and appears to be referring to an older linux version than what I have running.

Any help on this would be greatly appreciated! As I said, I'm brand new to these forums so please excuse me if I've broken any forum etiquette such as posting in the wrong place or not doing enough research before posting. If I have done any of those things, let me know and I promise I will fix it to the best of my abilities and remember it for the future.

Thanks again!
Homer

---

### Post by Favux on 2011-12-27
Hi homer1234,

The reason I haven't updated the [N-trig HOW TO]("http://ubuntuforums.org/showthread.php?t=1252492") yet to include Oneiric is that no one has posted any feedback on using Oneiric.  I have been assuming that means that all of the information that applies to Natty regarding ginn for multi-touch is unchanged.  The reason the guy on the video's multi-touch is working is he is using ginn.

The main things are to determine your BIOS version and firmware version.  You should be able to get them in Windows.  Don't update them unless you know what you are doing.  Then from there figure out if you need a new hid-ntrig.ko.  With luck your current ones will all work for you and you won't have to do anything other than install ginn.  The HOW TO tells you how to do that, the format of the commands, and links you to samples of the commands.

Feel free to post on the HOW TO thread if you want.

---

### Post by homer1234 on 2011-12-27
> **Favux said:**
> Hi homer1234,

The reason I haven't updated the [N-trig HOW TO]("http://ubuntuforums.org/showthread.php?t=1252492") yet to include Oneiric is that no one has posted any feedback on using Oneiric.  I have been assuming that means that all of the information that applies to Natty regarding ginn for multi-touch is unchanged.  The reason the guy on the video's multi-touch is working is he is using ginn.

The main things are to determine your BIOS version and firmware version.  You should be able to get them in Windows.  Don't update them unless you know what you are doing.  Then from there figure out if you need a new hid-ntrig.ko.  With luck your current ones will all work for you and you won't have to do anything other than install ginn.  The HOW TO tells you how to do that, the format of the commands, and links you to samples of the commands.

Feel free to post on the HOW TO thread if you want.


Favux,

Thanks so much for your quick response!

So I'm not sure I understand though. I no longer have windows on this machine (it was given to me with windows vista loaded with viruses so I reformatted and installed linux). In any case, are you saying that downloading drivers on a windows partition will let me use them on an ubuntu partition?
In the how-to you mention :
**[COLOR=RoyalBlue]"Currently Ayuthia recommends the 2.239 software bundle, containing the 4.6.5.8.5 firmware[/COLOR]**.   This newest firmware version is available for the HP and the Dell's at  their sites.  [The 32-bit version is not available at the HP site,"

Though I'm not sure to what exactly you're referring to. Are you saying that I should reinstall windows on another partition, and go to HP's website and download the multitouch drivers from HP's driver website for windows 7?

Since I already have 11.10, I have GINN installed already (i have verified this through synaptics package manager) does that mean that since I already see one touch point, all I have to do is edit the code in GINN and my computer will detect the multiple points?

Thanks again!
Homer

---

### Post by Favux on 2011-12-27
> I no longer have windows on this machine (it was given to me with windows vista loaded with viruses so I reformatted and installed linux).
I feel your pain.  So far I've managed to keep my Vista install on my HP TX2000 clean - I think.  But darn, does it take forever to boot.  Drives me crazy.
> In any case, are you saying that downloading drivers on a windows partition will let me use them on an ubuntu partition?
No not drivers, but the BIOS and N-trig firmware.  As a practical matter you need a Windows install to be able to download and update those.  Trying to do it in linux ranges from difficult and risky to impossible.  But again don't get the latest unless you know what you are doing.  For example the A11 and A12 BIOS (I think) for the Dell XT or XT2 break the dell-wmi.ko so Magick Rotation and the bezel buttons don't work.  We're just getting a handle on what changes we need to make to the dell-wmi.c to fix things.

Also the Windows partition is the easiest way to figure out the version of the BIOS and firmware.  Miscellaneous Notes on the HOW TO links you to Rafi's linux firmware tool and some folks have reported the results.  But I don't think I have enough information to cross-correlate that with the Windows version to tell you where you're at.  Part of the problem is Rafi has been changing the hid-trig.ko to improve version reporting so it is a bit of a moving target.

Be aware that installing Windows will lose you access to your Oneiric partition.  This is because Windows will overwrite your Grub 2 in the MBR.  So you need to reinstall it from a live CD:  [https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files)
> Since I already have 11.10, I have GINN installed already (i have verified this through synaptics package manager) does that mean that since I already see one touch point, all I have to do is edit the code in GINN and my computer will detect the multiple points?
Not sure.  Ginn should have default scripts installed so if everything is working you should have some mult-touch.

What could be causing the problem is not having recent enough N-trig firmware or a recent enough hid-ntrig.ko.  I'm not sure what hid-ntrig.ko comes default with Oneiric's 3.0 kernel but I would think it would be good enough.  So my guess is the culprit is likely the N-trig firmware.  Without knowing the version we can get an idea by you posting the output of:
```
xinput list
```
in a terminal.  We'll see if I can remember enough to spot the older non-multitouch firmware from that output.

---

### Post by homer1234 on 2011-12-27
> **Favux said:**
> I feel your pain.  So far I've managed to keep my Vista install on my HP TX2000 clean - I think.  But darn, does it take forever to boot.  Drives me crazy.

No not drivers, but the BIOS and N-trig firmware.  As a practical matter you need a Windows install to be able to download and update those.  Trying to do it in linux ranges from difficult and risky to impossible.  But again don't get the latest unless you know what you are doing.  For example the A11 and A12 BIOS (I think) for the Dell XT or XT2 break the dell-wmi.ko so Magick Rotation and the bezel buttons don't work.  We're just getting a handle on what changes we need to make to the dell-wmi.c to fix things.

Also the Windows partition is the easiest way to figure out the version of the BIOS and firmware.  Miscellaneous Notes on the HOW TO links you to Rafi's linux firmware tool and some folks have reported the results.  But I don't think I have enough information to cross-correlate that with the Windows version to tell you where you're at.  Part of the problem is Rafi has been changing the hid-trig.ko to improve version reporting so it is a bit of a moving target.

Be aware that installing Windows will lose you access to your Oneiric partition.  This is because Windows will overwrite your Grub 2 in the MBR.  So you need to reinstall it from a live CD:  [https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files)

Not sure.  Ginn should have default scripts installed so if everything is working you should have some mult-touch.

What could be causing the problem is not having recent enough N-trig firmware or a recent enough hid-ntrig.ko.  I'm not sure what hid-ntrig.ko comes default with Oneiric's 3.0 kernel but I would think it would be good enough.  So my guess is the culprit is likely the N-trig firmware.  Without knowing the version we can get an idea by you posting the output of:
```
xinput list
```in a terminal.  We'll see if I can remember enough to spot the older non-multitouch firmware from that output.


Ok that kind of makes sense. I'm still a bit confused but lets go from there:

Here is the output you asked for:

```
xhomer@TX2-tab:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen stylus                           id=11    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Touchscreen                          id=12    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen stylus                           id=13    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Touchscreen                          id=14    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=16    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen eraser                           id=19    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen pad                              id=20    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen eraser                           id=21    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen pad                              id=22    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; HP Webcam                                   id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=15    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                              id=17    [slave  keyboard (3)]
    &#8627; ENE eHome Infrared Remote Receiver          id=18    [slave  keyboard (3)]

```Although I'm not sure how much that helps. 

Would you recommend that I install windows 7 or windows vista on this machine then and then pull up the BIOS and firmware for the n-trig? I don't mind doing that or loosing data on this computer if it will better help you help me :)

Thanks,
Homer

---

### Post by Favux on 2011-12-27
That helped.  In addition to "N-Trig Pen" and "N-Trig Touchscreen" you should be seeing "N-Trig MultiTouch".  Without the "N-Trig MultiTouch" you only have single finger touch (1FGT) available which is what the "N-Trig Touchscreen" is.  I think the bug for that is fixed and it should be working correctly in Oneiric.  So you've got that, 1FGT, at least.

The double entries for the N-trig input devices are also a give away.  I think that can also come from the hid-ntrig.ko but I think in your case both are due to old N-trig firmware.
> Would you recommend that I install windows 7 or windows vista on this machine then and then pull up the BIOS and firmware for the n-trig?
Yes because at this point I'm reasonably sure your firmware is too old to support multi-touch.  Unless you are happy with single finger touch you will need to.  Besides I don't know how long HP will maintain access to the BIOS and N-trig firmware for the TX2z on their site since it is a discontinued model.

I've been trying to recall if there is any problem with updating the HP BIOS and I can't remember one.  So when you determine your current BIOS version and it's date post it and the version and date of the one you are proposing to update to.  I suspect as long as the date is from a year or more ago it would probably be safe to update to it.

For the N-trig firmware see if you can update to the 2.239 software bundle, containing the 4.6.5.8.5 firmware that Ayuthia recommends.  I think the newer version is OK also but I can't remember for sure right now.  I seem to recall a minor problem but maybe that was with the Dells?


Edit:  Oh, and FYI the stylus in "N-Trig Pen stylus" was appended to "N-Trig Pen" by the Wacom X driver xf86-input-wacom.  The stylus uses the Wacom X driver while touch is on evdev.  If you want to stick with 1FGT touch then we should check out if it behaves better on the Wacom driver if there is a problem with it on evdev.

---

### Post by homer1234 on 2011-12-27
> **Favux said:**
> 
I've been trying to recall if there is any problem with updating the HP BIOS and I can't remember one. So when you determine your current BIOS version and it's date post it and the version and date of the one you are proposing to update to. I suspect as long as the date is from a year or more ago it would probably be safe to update to it.
 
For the N-trig firmware see if you can update to the 2.239 software bundle, containing the 4.6.5.8.5 firmware that Ayuthia recommends. I think the newer version is OK also but I can't remember for sure right now. I seem to recall a minor problem but maybe that was with the Dells?
 
 
Edit: Oh, and FYI the stylus in "N-Trig Pen stylus" was appended to "N-Trig Pen" by the Wacom X driver xf86-input-wacom. The stylus uses the Wacom X driver while touch is on evdev. If you want to stick with 1FGT touch then we should check out if it behaves better on the Wacom driver if there is a problem with it on evdev.
 
Hi,
 
I definitely would like more than one touch point. I don't really care about the stylus but I do want to make use of multi touch gestures.
 
Ok so I installed windows 7 now and after running msinfo32 it looks like I'm running BIOS F.12, 2/17/2009
 

The one available from HP's website is
BIOS f.25 11-20-2009
 
Older versions ARE available and doing some light research doesn't show any issues in updating to this but you're the expert :)
 
As for the N-trig I've downloaded and installed 2.239 and can confirm that I do have up to 4 touch points on windows 7. Should I now install Oneric on a second partition and expect multi-touch to be working? or Shall I update the BIOS first?
 
Thanks,
Homer

---

### Post by Favux on 2011-12-27
Given its date I would think updating BIOS F.12 2/17/2009 to BIOS f.25 11-20-2009 is safe and I would.  It may address issues you haven't discovered yet.  But see if there is anything about rolling back to a previous BIOS if needed.  I wouldn't spend too much time on that, just check around a bit.  I think I recall some issues about CPU temp. and the fan but I can't remember if that was just for the TX2500 or both the TX2500 and the TX2z.
> As for the N-trig I've downloaded and installed 2.239 and can confirm that I do have up to 4 touch points on windows 7.
After that I would go ahead and re-install Oneiric.  With 2.239 I would expect you should now see multi-touch behavior since ginn is installed by default.

---

### Post by homer1234 on 2011-12-28
Ok so I updated the BIOS and installed Oneiric on another partition (after many failed attempts which stemmed from a failing flash drive!) 
 
Now here's the thing; as soon as I boot into ubuntu to even install it, the cursor jumps around the screen constantly and all over the screen. 
I managed to quiet it enough to run through the installer by putting 4 fingers on the touch screen and using the mousepad to navigate through the menu.
Do you have any suggestions on this? I know Rafi had a calibration tool which is supposed to prevent false clicks. Do you feel that it would be applicable here or is this more likely a hardware issue that's ground related?
 
When I tested it on the windows side on paint, the cursor doesn't jump on it's own but when I touch the screen I can't draw a single straight line with my finger. It starts jumping as I drag it accross the screen... :/
 
Thanks,
Homer

---

### Post by Favux on 2011-12-28
Well definitely use Rafi's calibration tool and degauss the screen.  I'm sure that has never been done.  But like you I am wondering about a hardware issue because there is a problem in Windows too.  It can't be the firmware that came with the 2.239 software package.  Unless the firmware install was somehow defective.  And I find it hard to believe they would have left up a defective BIOS for over 2 years!

If you have a mouse or something plugged in, especially if it is on the same usb port as the "defective/failing" flash drive was on, unplug it.  I'd wonder if in fact the problem is the usb port.  Otherwise I'd wonder about a loose connection, just like you are.

At least the fact that putting four fingers on the screen does something is encouraging.  It sort of suggests multi-touch is recognized.

---

### Post by clevermacia on 2012-01-07
Hey I have the 1025 dx on Ubuntu 11.1 my output for xinput list is the following

```
tx2-Notebook-PC:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen stylus                       	id=11	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig MultiTouch                       	id=12	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig Touchscreen                      	id=13	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=15	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen eraser                       	id=18	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen pad                          	id=19	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; CNF8038                                 	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=14	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=16	[slave  keyboard (3)]
    &#8627; ENE eHome Infrared Remote Receiver      	id=17	[slave  keyboard (3)]

```

You can see the Ntrig Multitouch is recognized .. but I cant get the multitouch to work! Single touch works fine .. although I had to do some tweaking to get that working.

Also I have Ginn installed .. but I cant get the multi touch to work for some reason. Anybody know what Im doing wrong ?

Here is my output for ginn


```
tx2-Notebook-PC:~$ ginn
usage: ginn <configxml>
Using wishes file /etc/ginn/wishes.xml
using default configuration file /etc/ginn/wishes.xml ... 
ginn
 global
  wish
   action
    trigger
    key
  wish
   action
    trigger
    key
  wish
   action
    trigger
    key
  wish
   action
    trigger
    key
  wish
   action
    trigger
    key
  wish
   action
    trigger
    key
  wish
   action
    trigger
    key
  wish
   action
    trigger
    key
 applications
  application
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
  application
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
  application
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
  application
   wish
    action
     trigger
     button
   wish
    action
     trigger
     button
  application
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
  application
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
  application
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
   wish
    action
     trigger
     key
Button : 4 Button : 5 

```

---

### Post by Favux on 2012-01-07
Hi clevermacia,

It appears your wish list isn't populated with any wishes.  What are the contents?  See:  [https://wiki.ubuntu.com/Multitouch/Ginn](https://wiki.ubuntu.com/Multitouch/Ginn)  This shows some examples and the HOW TO has one of them:

Zoom out the virtual desktop (4-tap): 4-fingers-Tap -> Super+E. 
```

    <wish gesture="Tap" fingers="4">
      <action name="action1" when="update">
        <trigger prop="tap time" min="20" max="400"/>
        <key modifier1="Super_L">E</key>
      </action>
    </wish>

```
Bring up all windows (3-pinch): 3-fingers-Pinch -> Super+W 
```

      <wish gesture="Pinch" fingers="3">
        <action name="action4" when="update">
          <trigger prop="radius delta" min="-80" max="-50"/>
          <key modifier1="Super_L">W</key>
        </action>
      </wish>

```
The HOW to then links you to examples other Ntrig users have come up with.  floyd0815's posts have sample lists attached you can download.  His first post:  [http://ubuntuforums.org/showpost.php?p=10367869&postcount=1391](http://ubuntuforums.org/showpost.php?p=10367869&postcount=1391)

---

