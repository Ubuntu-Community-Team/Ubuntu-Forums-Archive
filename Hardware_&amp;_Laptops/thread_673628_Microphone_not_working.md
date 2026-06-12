---
title: "Microphone not working"
date: 2008-01-20
forum: Hardware &amp; Laptops
---

### Post by mickthejew on 2008-01-20
Hi, I've just installed Gutsy on my BenQ Joybook S53 and everything is working a treat except for the microphone, which i really need as I make many calls using Skype.  The sound playback works fine on the speaker but I can't capture anything on my mic.

I have used ALSA Mixer and checked all boxes to use Alsa and made sure everything is unmuted.  I have checked Mic Boost.  I have started and restarted ALSA service and that didn't work either.

My audio chipset is Intel 82801 ICH6 (AC97) and it did work fine on Windows.  I've also tried plugging in an external microphone to the port in the front of the notebook but that had the same result too. 

So what can I do?  reinstall Alsa?  reinstall Gutsy?  Is there any other way??

Please help!!

PS I have seen and read all the other threads of people with similar problems but none of the fixes seem to work for my laptop.

Thanks

---

### Post by mickthejew on 2008-01-23
bump...anyone?  please???

---

### Post by quadrispro on 2008-01-23
Take a look here [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

---

### Post by alkat on 2008-01-23
Mic is not working on my machine either. My audio controller is not in the list at the page linked above.

```
root@ubuntolo:~# lspci -n | grep `lspci | grep -i audio | awk '{print $1}'`
00:1b.0 0403: 8086:27d8 (rev 02)
root@ubuntolo:~# lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
0a:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0a:06.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

```

---

### Post by quadrispro on 2008-01-23
your device

```

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

```

is present in the doc ;)

```

    *

      Precision M6300
          o

            00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
          o

            /proc/asound/card0/codec#0:Codec: SigmaTel STAC9205
          o

            /proc/asound/card0/codec#1:Codec: Conexant ID 2c06

```

---

### Post by alkat on 2008-01-23
Ooops... I didn't see it.
Gee, this here laptop is driving me mad! Too many things just don't work! :(

---

### Post by mickthejew on 2008-01-24
> **quadrispro said:**
> Take a look here [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

Thanks for the info, I'm not sure that is the problem though?

mick@mick-laptop:~$ lspci -n | grep `lspci | grep -i audio | awk '{print $1}'` 
00:1e.2 0401: 8086:266e (rev 04)

But that bug relates to PC's that have the Sound device PCI Id 8086:284b 

And when I checked the specific microphone fixes on that page it says:

> Microphone Fixes
Method A

    *

      does work: Dell Vostro 1500 (card: SigmaTel STAC9205)
    *

      does not work: Dell Latitude D630, Acer Aspire 4270

This workaround comes from this ALSA bug: [WWW] [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3495](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3495)

   1.

      Open Volume Control
   2.

      Go to Edit -> Preferences
   3.

      Make sure "Digital" and "Digital Input Source" is selected
   4.

      On the "Recording" tab, make sure the "Digital" slider is non-muted and turned up
   5.

      On the "Options" tab, make sure the "Digital Input Source" is set to "Digital Mic 1"

Method B

    *

      does work: Dell Latitude D830, Acer Aspire 4270
    *

      does not work:

   1.

      Open Volume Control
   2.

      Go to Edit -> Preferences
   3.

      Make sure "Digital" is selected
   4.

      On the "Recording" tab, make sure the "Digital" slider is non-muted and turned up
   5.

      On the "Options" tab, make sure the "Input Source" is set to "Mic"


However when I open volume control, there is no "Digital" tab available to be selected.

---

### Post by mickthejew on 2008-01-24
I've also installed Gnome Alsa Mixer as it had more options, but no "Digital" tab in there either.

---

### Post by alkat on 2008-01-24
Thanks to Mick's post, I thought about setting the volume from alsamixer and now I can see the mic is working: I can talk through the mic and hear my voice coming out of the speakers.
Too bad I still haven't figured out how to make it work with Audacity and Skype... :( Any hints, on that?
A.

---

### Post by mickthejew on 2008-01-24
Can't believe I actually helped someone, i'm such a n00b!

anyway try these couple of links with the skype problem, 

[http://jadmadi.net/blog/2007/12/27/ubuntu-gutsy-skype-microphone/](http://jadmadi.net/blog/2007/12/27/ubuntu-gutsy-skype-microphone/)

---

### Post by b0rka7a on 2008-01-24
Go to the Volume Control (gnome-volume-control) > Edit > Preferences > check the Capture box > Close. Next go to the Recording tab and set Capture to max (and unmute it if it's muted)
Tell me if this works ;)

---

### Post by mickthejew on 2008-01-24
nope didnt work, still nothing.

---

### Post by Najmudin on 2008-01-24
Try to do this  , go to volume control > Preferences > check the Digital source box
you will get a tab named option , try to play with the selected options , maybe one of them will work.
I'm not sure if that will help you , for me it solved the ( what you hear sound recording) not the microphone recording which was working well with Feisty Fawn , but gutsy i still can't use my microphone.
Good luck:)

---

### Post by Avalokiteshvara on 2008-01-24
Hi there,

My mic wasn't working either but I had to do two things to make it work, I don't know if you've tried this already but don't hurt to share.

First I did what b0rka7a suggested above. Then went to the mixer's Options tab and where it said Mic-In Mode I changed it to Mic-In. Had to do both those things, tried them separately and nada. 

Hope this helps.

---

### Post by Toadmund on 2008-01-24
I did what b0rka7a said, and it didn't work, but then I also unmuted microphone under playback, and now I can hear my dollar store microphone through my speakers.
:)
Now 'sound recorder' even works now!

This is great!

Thanks!

---

### Post by mickthejew on 2008-01-26
> **Avalokiteshvara said:**
> Hi there,

. Then went to the mixer's Options tab and where it said Mic-In Mode I changed it to Mic-In. Had to do both those things, tried them separately and nada. 

Hope this helps.

Hey, sorry I dont really understand what you mean by this, where can i find the mixers options tab?   What exactly do I have to change?

Thanks

---

### Post by mickthejew on 2008-01-26
> **Najmudin said:**
> Try to do this  , go to volume control > Preferences > check the Digital source box
you will get a tab named option , try to play with the selected options , maybe one of them will work.
I'm not sure if that will help you , for me it solved the ( what you hear sound recording) not the microphone recording which was working well with Feisty Fawn , but gutsy i still can't use my microphone.
Good luck:)

I dont have "Digital Source" Box in my preferences.. :confused:

---

### Post by Najmudin on 2008-01-26
> **mickthejew said:**
> I dont have "Digital Source" Box in my preferences.. :confused:

What sound device you are using now , double click on volume control > File > Change device
Did you find alsa mixer and oss mixer or just one of them.

---

### Post by mickthejew on 2008-01-26
I am currently using ALSA, but I also have the option to choose OSS.

---

### Post by Najmudin on 2008-01-27
> **mickthejew said:**
> I am currently using ALSA, but I also have the option to choose OSS.

I'm not sure about this but i think you are missing something , because there are two Preferences windows:
First one you can open it when you double click on the sound volume icon :

[[IMG]http://img184.imageshack.us/img184/1118/screenshotvolumecontroltu8.th.png[/IMG]]("[URL=http://img184.imageshack.us/my.php?image=screenshotvolumecontroltu8.png)"][[IMG]http://img184.imageshack.us/img184/1118/screenshotvolumecontroltu8.th.png[/IMG]](http://img184.imageshack.us/my.php?image=screenshotvolumecontroltu8.png)[/URL]

and the second one you can open it if you right clicked on the sound volume icon and select preferences from the list that will be shown to you.

[[IMG]http://img87.imageshack.us/img87/3885/screenshotvolumecontrollg6.th.png[/IMG]](http://img87.imageshack.us/my.php?image=screenshotvolumecontrollg6.png)

So which one you mean , in the first window there should be a Digital Source box in the preferences.
in the second one you will not find it ( in my case i don't see it , and not sure about most users ) .
I hope that will help and sorry for my English :)

---

### Post by mickthejew on 2008-01-27
yeah I just checked again and I don't have the Digital Source Option in my preferences.

I double clicked Volume Control -> Edit -> Preferences and it is not listed in there.  Its probably something to do with the type of sound card in my laptop (I'm guessing).

---

### Post by Najmudin on 2008-01-27
> **mickthejew said:**
> yeah I just checked again and I don't have the Digital Source Option in my preferences.

I double clicked Volume Control -> Edit -> Preferences and it is not listed in there.  Its probably something to do with the type of sound card in my laptop (I'm guessing).

Your guessing might be right , I'm sorry I tried my best but I couldn't help you :(
I hope some one else with more knowledge and experience in Ubuntu and Linux can help you.
Don't give up.

---

### Post by mickthejew on 2008-01-28
hey thanks for your help mate, I really appreciate it.  

Will keep on trying!

---

### Post by mickthejew on 2008-01-30
bump....

Anybody? Bueller??

---

### Post by cdtech on 2008-01-30
Use your alsamixer

Press f5 to bring up all controls and select IntMic using the arrow keys. Press the space key to select as the capture.

Should be good to go.....

---

### Post by mickthejew on 2008-01-30
> **cdtech said:**
> Use your alsamixer

Press f5 to bring up all controls and select IntMic using the arrow keys. Press the space key to select as the capture.

Should be good to go.....

Ok, thanks for that.  I did what you said but I don't have IntMic on my AlsaMixer?

I just have MIC (which is already set to capture) and Capture (which is also set to capture.  I also have Mic Boost.

---

### Post by cdtech on 2008-01-30
> **mickthejew said:**
> Ok, thanks for that.  I did what you said but I don't have IntMic on my AlsaMixer?

I just have MIC (which is already set to capture) and Capture (which is also set to capture.  I also have Mic Boost.

Yours doesn't look like this setup when you press f5?

[ATTACH]58083[/ATTACH]

You can't have a capture set to capture..

can you post a screen shot of that? that's strange.

---

### Post by mickthejew on 2008-01-30
Ok here are all of my ALSA mixer settings.  there are a few so i had to take 3 screenshots.

[[IMG]http://img518.imageshack.us/img518/7187/screenshotwi9.jpg[/IMG]](http://imageshack.us)
[[IMG]http://img518.imageshack.us/img518/7187/screenshotwi9.a0b9bd5256.jpg[/IMG]](http://g.imageshack.us/g.php?h=518&i=screenshotwi9.jpg)

[[IMG]http://img262.imageshack.us/img262/4779/screenshot1eu2.jpg[/IMG]](http://imageshack.us)

[[IMG]http://img262.imageshack.us/img262/2379/screenshot2uo9.jpg[/IMG]](http://imageshack.us)

And somehome I've managed to set CD as capture too, but can't uncheck it using the space bar.  Not that it really changed anything.

---

### Post by cdtech on 2008-01-30
Can't you change your line or aux to be capture using your space bar? Those would be the correct capture devices. Any one with dashes below it will be a capture device and you should select one of those. You select with the space bar. If you have one selected you can un-select it first to select the next, until you find the correct capture device.

Use :
```
amixer
```
This will show you what current playback and capture that you are using.

This is my setup, 

[ATTACH]58149[/ATTACH]

I'm also using the v1.0.15rc1 alsamixer. If your mixer is buggy, I would upgrade to the new version.

---

### Post by mickthejew on 2008-01-30
Thanks again for that, I tried all the capture devices and none of them worked.  The interesting thing I noted was that when i called into Skype testing service, the capture level would automatically drop by 50%.

I guess next step is to upgrade AlsaMixer, is there any easy way to do that?

---

### Post by cdtech on 2008-01-30
I found this somewhere on the web or in here, not really sure, so I can't take the credit for this. I used this method to upgrade mine.

**Install these packages:**

sudo apt-get install linux-headers-`uname -r` build-essential libncurses5-dev libncursesw5-dev ncurses-term alsa-tools-gui gettext po-debconf debhelper quilt alsa-base libc6-dev

**and uninstall these:**

sudo apt-get remove --purge alsa-base alsa-tools

**!!! be sure not to uninstall alsa-utils as it will uninstall your gdm too !!!**

**Back-up your current configuration:**

tar -zcvf original-drivers.tgz /lib/modules/`uname -r`/kernel/sound

**Make a directory for alsa packages:**

mkdir /usr/src/alsa-15rc
cd /usr/src/alsa-15rc

**Get alsa packages:**

```

wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc3.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15rc3.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15rc1.tar.bz2
wget ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.15rc1.tar.bz2

```

**Unpack archives:**

tar xvf alsa-driver-1.0.15rc3.tar.bz2
tar xvf alsa-lib-1.0.15rc3.tar.bz2
tar xvf alsa-utils-1.0.15rc1.tar.bz2
tar xvf alsa-firmware-1.0.15rc1.tar.bz2

**you wont need the tar's afterwards so remove them:**

sudo rm *.bz2

**Install driver:**

cd alsa-driver-1.0.15rc3
sudo make clean
sudo make mrproper
./configure --with-cards=hda-intel 
sudo make
sudo make install

**Install alsa-lib:**

cd ../alsa-lib-1.0.15rc3
sudo make clean
./configure
sudo make
sudo make install

**Install alsa-utils:**

cd ../alsa-utils-1.0.15rc1
./configure
sudo make clean
sudo make 
sudo make install

**Install alsa-firmware:**

cd ../alsa-firmware-1.0.15rc1
./configure
sudo make clean
sudo make 
sudo make install

double-click Volume control (the speaker next to the clock), then Edit->Preferences and check all the boxes (you should have 8 boxes : Master, PCM, LineIn, IEC958, Digital, Ext Mic, Int Mic, Int Mic (yes 2 times Int Mic). Close Preferences.

Go to Switches tab and check LineIn

Go to Recording tab and be sure both mic and speakers are not muted.

Go to Playback tab and be sure Master,PCM, and Ext Mic are not muted and BE SURE IntMic IS MUTED!

In a terminal, login as root and type:

 /etc/init.d/alsa-utils stop

Type the following command:

/usr/sbin/alsaconf

When it asks you, choose the 'hda-intel' card and then to save the changes to the files

Type:

 /etc/init.d/alsa-utils start

That should be it......

I did a reboot on mine and adjusted everything using alsamixer afterwards......

---

### Post by mickthejew on 2008-01-31
err, is there any simpler way to do it?

I'm a bit of a ubuntu noob, last time i tried to upgrade alsamixer I ended up deleting my GUI and had to reinstall ubuntu.  was very painful!

---

### Post by cdtech on 2008-01-31
Experts were once noobs too........:)

---

### Post by cthulhu666 on 2008-02-01
Much simpler approach:

wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc1.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc1.tar.bz2)
tar xvpjf alsa-driver-1.0.15rc1.tar.bz2
cd alsa-driver-1.0.15rc1
./configure --with-cards=hda-intel
make
sudo make install


Make sure you reboot after a successful "sudo make install". 

 - from [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

---

### Post by aonegodman on 2008-02-05
> **Najmudin said:**
> Try to do this  , go to volume control > Preferences > check the Digital source box
you will get a tab named option , try to play with the selected options , maybe one of them will work.
I'm not sure if that will help you , for me it solved the ( what you hear sound recording) not the microphone recording which was working well with Feisty Fawn , but gutsy i still can't use my microphone.
Good luck:)

Where are you guys getting this "Digital source box" thing at? I don't have that option.  :confused:

---

### Post by cdtech on 2008-02-05
That switch is located under preference:
[ATTACH]58779[/ATTACH]
other switches:
[ATTACH]58780[/ATTACH]

---

### Post by Najmudin on 2008-02-06
Yesterday and finally i get my microphone to work with my sound card :)
What was wrong with me is that i was using the mic slot in sound card which is in pink color
i decided to try the line in slot instead, so i plugged in the microphone cable , then i changed the setting in volume control>option tab>Digital Source > to " i2s in" (this is in my case, i dont' know about yours guys)
the Shared Mic/Line in will be "Mic In" ,it should look like this :

 [IMG]http://img519.imageshack.us/img519/1117/screenshotvolumecontrolfc3.png[/IMG]

then selecting the Recording Tab , unmute the "Line in" recording , rise the volume control to highest level , mute the "microphone" , should look like that:

[IMG]http://img100.imageshack.us/img100/1502/screenshotvolumecontrolbp7.png[/IMG]

That's how it works for me , i hope this can help you guy's.

---

### Post by aonegodman on 2008-02-06
> **cdtech said:**
> That switch is located under preference:
[ATTACH]58779[/ATTACH]
other switches:
[ATTACH]58780[/ATTACH]

Thanks, but I don't have that config in my sound control panel. Mine is an Ensoniq ALSApci.

As you will see there is no digital sound selection available.    :(

By the way - I'm using a USB Logitech headset.

---

### Post by mickthejew on 2008-02-06
> **cthulhu666 said:**
> Much simpler approach:

wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc1.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc1.tar.bz2)
tar xvpjf alsa-driver-1.0.15rc1.tar.bz2
cd alsa-driver-1.0.15rc1
./configure --with-cards=hda-intel
make
sudo make install


Make sure you reboot after a successful "sudo make install". 

 - from [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

thanks for that but I get the following error when trying the tar command:

> mick@mick-laptop:~/alsa-driver-1.0.15rc1$ ./configure --with-cards=hda-intel
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
mick@mick-laptop:~/alsa-driver-1.0.15rc1$ 
mick@mick-laptop:~/alsa-driver-1.0.15rc1$ ./configure --with-cards=hda-intel


Would you have any idea why I'm getting the error?

---

### Post by cdtech on 2008-02-06
See if you have the compiler installed:

**which cc gcc**

and see if its in your path:

**echo $PATH**

If not you may need the build-essentials: **sudo apt-get install build-essential**

---

### Post by mickthejew on 2008-02-07
> **cdtech said:**
> See if you have the compiler installed:

**which cc gcc**

and see if its in your path:

**echo $PATH**

If not you may need the build-essentials: **sudo apt-get install build-essential**

ok tried that, got the following errors:

> Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main libc6-dev 2.6.1-1ubuntu10 [3287kB]
Fetched 3940kB in 5m0s (13.1kB/s)                                              
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/pool/main/g/gcc-4.1/libstdc++6-4.1-dev_4.1.2-16ubuntu2_i386.deb  Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/pool/main/g/gcc-4.1/g++-4.1_4.1.2-16ubuntu2_i386.deb  Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/pool/main/g/gcc-defaults/g++_4.1.2-9ubuntu2_i386.deb  Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/pool/main/p/patch/patch_2.5.9-4_i386.deb  Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/pool/main/d/dpkg/dpkg-dev_1.14.5ubuntu16_all.deb  Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/pool/main/b/build-essential/build-essential_11.3ubuntu1_i386.deb  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


So I ran sudo apt-get update then got the following errors:

[quote]W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems[\quote]

Blocked at every corner!! :)

---

### Post by cthulhu666 on 2008-02-07
Did you insert the Ubuntu CD as instructed?

---

### Post by mickthejew on 2008-02-08
yes, still didn't work.

---

### Post by cthulhu666 on 2008-02-08
> **mickthejew said:**
> yes, still didn't work.
That's strange, I just worked for me. :confused:

If you happen to have more than one CD/DVD drive: did you insert the Ubuntu CD into the same drive as you used when installing Ubuntu?

---

### Post by mickthejew on 2008-02-08
> **cthulhu666 said:**
> That's strange, I just worked for me. :confused:

If you happen to have more than one CD/DVD drive: did you insert the Ubuntu CD into the same drive as you used when installing Ubuntu?

yeah i've only got 1 cd / dvd drive as its a laptop,

---

### Post by cthulhu666 on 2008-02-08
> **mickthejew said:**
> yeah i've only got 1 cd / dvd drive as its a laptop,
I have to admit that Ubuntu is not really my "home turf", as I'm more of a Gentoo person. So I bet there are more qualified ppl on this forum, that can help you getting **build-essentials** installed.

Have you tried mounting the CD manually? I'm not sure exactly where to mount it, though - /media/cdrom perhaps...

---

### Post by DamonChyld on 2008-02-14
I am on a Dell Vostro 1500 with a STAC 9205 and just got my mic working by using the ALSA mixer and going into applications> sound recorder and changing input to ACDMux. It changed back to InVol after a restart but seems to be stable now... hope this will help someone ;)

---

