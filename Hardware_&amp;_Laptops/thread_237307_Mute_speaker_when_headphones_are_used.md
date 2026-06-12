---
title: "Mute speaker when headphones are used"
date: 2006-08-15
forum: Hardware &amp; Laptops
---

### Post by bsaber on 2006-08-15
Hi everyone,

I'm almost ready to fully switch over from Windows to Ubuntu.  There is only two things thats really keeping me from making the move.  The first is I can't stream videos from a windows share but I can live without that.  

Second, is that when I have the headhphones plugged in the sound still comes out of the speakers.  I have a HP dv2040us laptop with the HDA Intel sound card.  I was wondering if anyone can help me with this problem because I use my laptop quite often in class and using the headphones to mute the speaker especially when the computer first starts up is a must.  I would be very grateful if anyone can help me with this matter.

Things I've tried already:

I've tried searching the forums for solutions but they all relate to either no sound at all from the headphones or headphone volume too low, etc. 

I've downloaded and installed the latest Alsa drivers.

Another thing is that the sound volume in Ubuntu is much lower than the volume in Windows even when everything is maxed out.  From what I've read in the forums there doesn't really seem to be anything that can fix this problem.  (I've tried almost all the "solutions" that I found while searching the forums for this particular problem.)  Thanks in advance for any guidance.

---

### Post by louis_nichols on 2006-08-16
What you're saying is very strange. Are you sure the same thing (speakers not mutted when headphones plugged) doesn't happen in Windows? This is because such things happen at hardware level, without intervention from the soundcard. Basically, it's just a switch in the female plug, which is disconnected when male is plugged.

Well, at least it should... I can't think of any reason why such a thing would be re-wired through the sound card...

---

### Post by bsaber on 2006-08-17
Hi,

Thank you for replying.  The thing is that it works perfectly fine in Windows.  Its just with Ubuntu.  I don't know why it would be like that.  Anymore suggestions?

Bsaber

---

### Post by Bakerconspiracy on 2006-08-17
You could try finding the driver for your sound card and installing it,
instead of using the generic one. TThose last couple steps away from windows
are always the hardest.

---

### Post by bsaber on 2006-08-17
Bakerconspiracy,

How would I go about doing that?  Any help or guidance would be greatly appreciated.

---

### Post by sweRascal on 2006-08-17
I had this problem as well but found an option on my HP nx8220 when i clicked on the speaker in the top right corner that said "Be aware of headphones connection" When I checked that it worked beautifully and mutet the speakers when I connected the headphones.
Just my 50 cents on the subject.

/André

---

### Post by bsaber on 2006-08-17
> **sweRascal said:**
> I had this problem as well but found an option on my HP nx8220 when i clicked on the speaker in the top right corner that said "Be aware of headphones connection" When I checked that it worked beautifully and mutet the speakers when I connected the headphones.
Just my 50 cents on the subject.

/André

I just tried that but I don't see an option for that.  Is this in  Dapper?

---

### Post by sweRascal on 2006-08-17
Yes in dapper,, I can check it out and give you more details when I get home.

---

### Post by franute on 2006-08-17
What's your soundcard model??

---

### Post by bsaber on 2006-08-17
> **franute said:**
> What's your soundcard model??

I'm not sure what model it is exactly but in Windows Device Manager is says its a Conexant High Definition Audio.  The driver from the HP website also says Conexant High Definition Audio but doesn't give an exact model number.  I can try and contact HP and see if they can give me an exact model number if that would help. 

sweRascal, thanks that would be appreciated.

Thanks again to everyone thats trying to help.

---

### Post by franute on 2006-08-18
I think it's based on the intel high definition audio, open a terminal and write:
"lsmod | grep snd"
if down appears the snd-hda-intel modules loaded, I'm right :D

look here:
[http://www.unixboard.de/vb3/archive/index.php/t-16689.html]("http://www.unixboard.de/vb3/archive/index.php/t-16689.html")
and look for your model (y suppose it's "hp"), so you must write in:
/etc/modules
[I]snd-hda-intel
options snd-hda-intel model=hp[/I]

and in:
/etc/modprobe.d/alsa-base
(i think you've got to do it here too)
*options snd-hda-intel model=hp*

I'm not very sure, you can always follow the [official how-to]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=ICH+southbridge+HD-audio+and+modem.&chip=ICH6%2C+ICH6M%2C+ICH7%2C+ESB2&module=hda-intel") and put the options in its place, sorry I can't explain better :neutral:

---

### Post by bsaber on 2006-08-18
franute,

I tried what you suggested and also followed the instructions from the links you provided but still nothing.  Thanks again for the help though.  Anymore suggestions?  If not I'll have no choice to but keep using Windows as my main desktop and just hope that the next release of Ubuntu will fix this sound problem.

---

### Post by Ugeek on 2006-08-19
I have compaq V3018 and aving exactly same promlem and its due to hardware. Still no improvement... Another thing I am sure its the problem with the driver... latest version of alsa also have it. Also other linux distributions (FC5,SLED)

---

### Post by bsaber on 2006-08-20
> **Ugeek said:**
> I have compaq V3018 and aving exactly same promlem and its due to hardware. Still no improvement... Another thing I am sure its the problem with the driver... latest version of alsa also have it. Also other linux distributions (FC5,SLED)

So I'm guessing we're out of luck.  The weird thing is that it works perfectly fine in Windows.  Maybe they'll have this problem solved in the next release of Ubuntu.

---

### Post by deunan on 2007-02-04
Hi all, I'm an idiot and didn't realize until..

I am using a HP Compaq nx6120 running 6.10 Edgy Eft

Same problem..  What I did was -

"Right Click" Volume Control Icon on the TaskBar
Click "Open Volume Control"
Click "Switches" Tab
Enable the "Headphone Jack Sense"

Voila and enjoy!   :lolflag: 


Sincere regards and thanks everyone!!

---

### Post by DonnieP on 2007-03-15
I have the same problem on Toshiba Satellite A135 running Edgy.  And my 'Open Volume Control' does not have a 'Switches' tab.  Only Playback and Capture.

---

### Post by dixon on 2007-03-20
Open volume control -> edit -> preferences -> check Headphone Jack sense -> ok

Switches tab will appear ;)

---

### Post by muhacir on 2007-03-22
Strange i use hp nx8220 and no problem. there are also microphone config in tabs

---

### Post by DonnieP on 2007-03-22
I tried the Edit Preferences and there's nothing about headphones.  Only Master, PCM and Capture.  The sound module is snd-hda-intel.  And alsa-mixer reports HDA Intel as well.

---

### Post by dixon on 2007-03-22
> **DonnieP said:**
> I tried the Edit Preferences and there's nothing about headphones.  Only Master, PCM and Capture.  The sound module is snd-hda-intel.  And alsa-mixer reports HDA Intel as well.

Have u tried [this]("https://help.ubuntu.com/community/HdaIntelSoundHowto")?

---

### Post by muhacir on 2007-03-23
> **DonnieP said:**
> I tried the Edit Preferences and there's nothing about headphones.  Only Master, PCM and Capture.  The sound module is snd-hda-intel.  And alsa-mixer reports HDA Intel as well.



[IMG]http://img65.imageshack.us/img65/2039/screenshotvolumecontrolpf7.png[/IMG]
got it:)

---

### Post by jonathanpiper on 2007-04-01
I've also got a Toshiba A135 with Intel HDA.  I'm having the same problem with the headphone output in Feisty, but in the volume control app there's only a "Headphone" switch instead of "Headphone Jack Sense."  I don't know if that *should* make any functional difference, but the switch only enables the headphones without muting the main speakers.  Is there any way I can get the Jack Sense switch, or is there another solution?

---

### Post by alegir on 2007-04-09
Hello All,

I have the same problem with a HP dv2000. My sound stopped working randomly and then I recompiled the latest alsa (development release) and it works now, not sure if it will when I reboot.

Anyway, I plugged in my headphones and got sound from PC speakers and headphones.

I also have no option under the switches tab for headphone jack sense.

Here is the interesting thing:

With sound coming out of speakers and headphones, if I hit the mute button twice (mute then unmute) the it switches to just the headphones. 

Then, if I unplug the headphones, no sound anywhere. If I mute and unmute it comes back to the PC speakers.

While this is not a *solution*, it at least makes it usable.

Is anyone else able to do this mute/unmute to get it to work?

---

### Post by fwallace99 on 2007-04-15
I have the same problem:

Toshiba Satellite A135-S2276
Ubuntu 6.06 LTS

It's an ATI Card. I can have sound on both speakers and headphones but not headphones only. Interestingly, the built in volume control works and adjusts both headphones and speakers.

Any suggestions?

---

### Post by x64Jimbo on 2007-05-03
Same problem with HP NX6325 - Feisty 32 bit. Problem was absent in Edgy.

---

### Post by n3azz on 2007-05-03
I have a Toshibe Sat Pro A120 and am in exactly the same situation as the original poster.

However, The streaming of movies problem was solved by using Totem and in the preferences settings select LAN connection. VIOLA.!.!

The volume issue is solved by increasing the PCM volume in your sound preferences.

The sound coming from Headphones and Speakers at the same time however, I have no F@*~ing clue. I am at a loss. It isn't hardware.

mine is an Intel sound card too.

Has anybody solved this on a Toshiba yet?

---

### Post by thekidrio on 2007-06-03
[URL="http://www.pixelmonkey.org/2007/03/18/dv2000-alsa-patches/#more-348"]http://www.pixelmonkey.org/2007/03/18/dv2000-alsa-patches/#more-348
[/URL]
is the source of the following:


```
1. Backup your current drivers

    tar -zcvf original-drivers.tgz /lib/modules/`uname -r`/kernel/sound

2. Next, get the latest release and bring it current.

    wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc3.tar.bz2

    wget http://members.dsl-only.net/~tdavis/alsa-patches/conexant-latest-rc3.patch

    tar -jxf alsa-driver-1.0.14rc3.tar.bz2

    cd alsa-driver-1.0.14rc3/alsa-kernel

    patch -p1 < ../../conexant-latest-rc3.patch

    cd ../../

3. Build the code.

    cd alsa-driver-1.0.14rc3

    ./configure --with-debug=detect --with-cards=hda-intel

    make

    sudo make install

    sudo depmod -a

    sudo dmesg -c >/dev/null

4. Stop all audio applications and remove all audio drivers

On my system, the following works:

    modprobe -r snd-usb-audio

    modprobe -r snd-hda-intel snd-hda-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-timer snd snd-page-alloc

5. Reload the new driver

Simply run modprobe snd-hda-intel, look at the dmesg output and test it out.

Using alsamixer will show you all available channels. In gnome-volume-control, you can also enable additional channels with Edit->Preferences. You&#8217;ll need at least Master, PCM, and PCM-2 enabled to get proper volume working on the headphones and speakers. You&#8217;ll need Capture enabled in the Capture tab to get mic input working.

If nothing works, or one function doesn&#8217;t work, try reloading the driver with &#8220;model=test&#8221; as a parameter. On Ubuntu, this can be done by doing sudo vim /etc/modprobe.d/alsa-base and adding a line to the end that says This should enable everything.

If you have issues, you can try to contact Tobin Davis or other hackers at the ALSA team. Or you could even post a comment here and I&#8217;ll pass it along. Please include the system make/model, the subsystem line from &#8220;lspci -s 0:1b -vn&#8221; (Ex: Subsystem: 103c:30b2), the dmesg output from above, and the output from &#8220;cat /proc/asound/card0/codec#0&#8243;.
```

++EDIT++

Might need to follow the following to get a complete install
```
sudo apt-get install build-essential
```

and
[URL="http://ubuntuforums.org/showthread.php?p=1695531"]
http://ubuntuforums.org/showthread.php?p=1695531[/URL]

---

### Post by crimsun on 2007-06-03
> **thekidrio said:**
> If you have issues, you can try to contact Tobin Davis or other hackers at the ALSA team. Or you could even post a comment here and I’ll pass it along. Please include the system make/model, the subsystem line from “lspci -s 0:1b -vn” (Ex: Subsystem: 103c:30b2), the dmesg output from above, and the output from “cat /proc/asound/card0/codec#0&#8243;.[/CODE]

Keep in mind that most of us hacking the drivers don't read this forum.  Please use the #alsa IRC channel, or preferably, file a bug report using Launchpad against the `linux-source-2.6.20' source package (if using feisty).

---

### Post by x64Jimbo on 2007-06-04
It's fixed now... must have been the kernel update

---

### Post by loathsome on 2007-06-04
> **x64Jimbo said:**
> It's fixed now... must have been the kernel update
Nope, nothing here.

---

### Post by x64Jimbo on 2007-06-06
Well, now it's broken again. Sure is weird.

---

### Post by loathsome on 2007-06-06
I've found a workaround, though.

When you've plugged your mighty headphones in, open up «alsamixer», and then mute «front» - works fine here.

---

### Post by x64Jimbo on 2007-06-07
Doesn't work when you don't have a "front" toggle in the first place.

---

### Post by Braveheart1980 on 2007-11-19
WoW

I am having this same prob with my hda-intel sound card on my laptop

Any ideas?

---

### Post by abhitux on 2007-11-19
> **loathsome said:**
> I've found a workaround, though.

When you've plugged your mighty headphones in, open up «alsamixer», and then mute «front» - works fine here.

This works for me as a rough work around unless something is implemented in the main distro itself. I am using Lenovo Y500 series (in India).

---

### Post by biodiesel-bri on 2007-11-24
Sound works fine but the main speakers do not shut off with headphones plugged in.  Sound buttons on the laptop work.

HP dv9610us with Conexant using snd_intel_hda driver.  Alsamixer gives me no "front speaker" option nor does Gnome Alsa Mixer.

---

### Post by biodiesel-bri on 2007-11-24
FIXED!

This post fixed my problem:
[http://ubuntuforums.org/showthread.php?p=3501600#post3501600](http://ubuntuforums.org/showthread.php?p=3501600#post3501600)

---

### Post by Spirotot on 2007-12-05
I'm using a Toshiba Satellite A135-S4527, with and HDA Intel card, and a Realtek ALC861-VD chip (whatever the second one means, I don't know... I got that from alsamixer, run from a Terminal). Anyway, when I plug in my headphones, the PC speakers don't automatically cut out, and no matter what I try (I've tried everything I can think of in alsamixer [run from a terminal], and and using the "Open Volume Control" thing [including checking and unchecking the Headphones thing. I don't have a Headphone jack sense, or whatever... Just "Headphones"]). For everything I've tried so far, the headphones just seem "attached" to the PC speakers - if they mute, so do the headphones, etc. Any ideas would be appreciated - Thanks!

---

### Post by prog101 on 2007-12-07
I'm using a Toshiba Satellite A135-S7404, similar problem , same as reported by Spirotot. Any help is appreciated!

---

### Post by nbv4 on 2008-01-20
I'm using a Toshiba A135-2266 and am having a similiar problem. When I plug in the headphones, the main speakers still work, but in my case, the headphones don't make any sound either. I know the port works, because they woek under linux. I'm using Kubuntu, btw.

---

### Post by 3dOptics on 2008-01-29
I was having the same problem with my sager np2090 in Ubuntu Gusty. I fixed it by going to System, Preferences, Sound, and under "Default mixer tracks" click PCM. (The reason to do this is so that PCM will control the volume for both front and headphones.) Then close the window. Now double click on the sound icon in the system tray, then from the edit menu, click on preferences, check "off-hook", then close. Now a tab labelled "switches" will be displayed, click it and check "off-hook". On the "playback" tab, max out the volume on headphones and front. Pressing the volume keys on your keyboard should slide up and down the PCM slider. Now if you plug in your headphones your system speakers will mute, unplug them and your system speakers will turn back on. Dont move the front slider up or down when you have headphones plugged in because it will turn on the system speakers while you are using your headphones. Only control volume with the PCM slider or the volume keys on your keyboard.

---

### Post by cdtech on 2008-01-29
I just posted on this subject about 15 minutes ago.

See [[COLOR="DarkRed"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=676917")

I have the Conexant on a Pavilion HP dv9608nr, this might help you.

Hope this helps......

---

### Post by ligelowbee on 2008-07-03
Hey I'm on a Toshiba satellite a200 ah1 and was having the same problem.
On the superwiser interweb I found the following solution.
I'm using the  snd_hda_intel module, first disable the module.

```
sudo modprobe -r snd_hda_intel
```

edit /etc/modprobe.d/sound as root and add the line:
```
options snd-hda-intel model=lenovo
```

then reload the module:
```
sudo modprobe snd_hda_intel
```

for some reason specifing the model as lenovo, even though it's not, makes the plug turn off the speakers.  Who knew.

---

