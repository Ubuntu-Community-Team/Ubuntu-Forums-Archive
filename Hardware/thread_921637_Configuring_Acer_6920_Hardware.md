---
title: "Configuring Acer 6920 Hardware"
date: 2008-09-16
forum: Hardware
---

### Post by CJay554 on 2008-09-16
[NOTE] As of Ubuntu 9.10 everything works out of the box except two things: fingerprint scanner, Video card. The video card works nice, it just feels like the driver itself isn't fully completed. Using Gnome Shell during the "activity" screen many little holes exist in the screen (unclickable area) because of this driver issue.




I've fallen in love with this Acer 6920 that i configured to ALMOST work flawlessly with Ubuntu, here's what i found that works:


**Works out of the box:**
-Brightness fn key adjuster with a few other "fn" keys
-Graphics seem to be fine and smooth 
-Wireless works Perfectly
-Shortcut keys _(such as the "e" button, wireless on/off button, internet/email/bluetooth)_
-Locking the CineDash is functional _(its already configured at the hardware level)_ *:: If kept locked at login will not let volume up/down work.*
-Play, Pause, Stop, Next song, Previous song work flawlessly, the shortcuts can be set in the keyboard shortcuts _(For gnome its preset to work with rhythmbox)_.
-USB's
-VGA adapter _(just restart xserver while connected to monitor/overhead to clone output, sometimes restart the whole computer, if that doesn't work just configure in system>pref>screen resolution  make sure "clone screens" is checked.)_
-CD/DVD Reader/Burner is flawless.
-And yes, the pretty blue lights on each side of the screen joints work just fine =] as well as the power button light and the CineDash light.



**Will work with a bit of configuration:**
-Camera _(Conflicts with Ubuntu 8.10 AFTER online package updates)_.
-Sound
-CineDash Pad (Vol+, Vol-, Mute)  _***(ALSA: Volume controls on CineDash work but make sure on login you DO NOT have the controls on "Hold" or else ubuntu will not detect the hardware, if you logging with it on hold just log out and log back in this time with the Hold off!)***_
-Ethernet _(WORKS OUT OF BOX IN INTREPID 8.10)_

(be prepared to spend some time configuring them all, or you can configure them individually by finding its section in this tutorial)



**What i have found that doesn't work:**

-The 2 buttons on CineDash _(one with the little man spreading his arms and the backwards arrow)_
-Mic
-Fingerprint scanner [U](Who uses this anyway?)
[/U]

***Resolved:***

-SD Card Reader If booting up with an SD card already inserted Ubuntu can detect the hardware that way and recognize the SD card. _(May work on login)_
-Volume up/down CineDash *:: Works with ALSA 1.18 when you login, MAKE SURE THE HOLD BUTTON IS NOT ON, otherwise ubuntu will not detect the hardware.*



Unknown Issues:
WebCam seems to act weird when updating to latest software versions, I'm not sure which package ruins this but the kernel update seems to not bother the webcam, i refuse to upate until this is resolved [I]:: After package updates Webcam only displays on lowest resolution, will not do 800x600 or others.
[/I]
Mic is not supported with the alsa driver *yet*




**_Installing your hardware drivers!_**

**Camera**

First check if your camera is already supported.
install Cheese (it depends on ubuntu version, to my knowledge 8.04 supports my camera):

```
sudo apt-get install cheese
```

After you install it run it through Applications > Graphics > Cheese
If you see an image feed your good!

If not...

Directions: [https://help.ubuntu.com/community/EasyCam]("https://help.ubuntu.com/community/EasyCam")

  Very simple. add two repositories through your:


  System > Administration > Software Sources

  "Third-Party Resources" Tab

  click "+ Add"

  copy paste these two lines individually into the text field.

  ```
deb http://blognux.free.fr/ubuntu hardy main
  deb-src http://blognux.free.fr/ubuntu hardy main
```
 
  then open a terminal and do
 
  ```
sudo apt-get update
```

  Now, if you se Gnome (gtk -- Regular Ubuntu) use this to install 
  Easycam:
 
  ```
sudo apt-get install easycam2-gtk
```
  
  If you use KDE (qt -- Kubuntu <-- KDE version of Ubuntu) use this:
  
  ```
sudo apt-get install easycam2-qt
```

  Run the EasyCam through Applications > Accessories the interface might 
  be i a different language but its as simple and clicking next and then
  clicking the middle to scan for the camera and find suitable drivers.

  After that try using Cheese to see if you get an image feed, you  
  should, if not post your problems!
 





=====================================================================





Sound and CineDash are a bit tricky..

PICK ONE OF THE FOLLOWING: EITHER ALSA OR OSS4!
**Sound**
**---------------------------ALSA 1.0.18a Driver---------------------------**

**NOTICE!!!!! IF YOU HAVE TRIED TO INSTALL WITH THIS SCRIPT BEFORE AND DID NOT HAVE ANY LUCK TRY DOING " sudo rm /usr/src/alsa/* " TO REMOVE OLD INSTALLATION FILES THAT WILL RENDER THE SCRIPT CONFUSED!!!**

This will install the newest ALSA driver which will have 80% functionality of your sound quality (surround sound not supported completely) 




To start the installation simply download this script to your home folder:
[http://www.box.net/shared/454ic17as0](http://www.box.net/shared/454ic17as0)

THIS SCRIPT WILL TURN OFF THE COMPUTER WHEN DONE MAKE SURE YOU SAVE ALL DATA PRIOR TO RUNNING THIS SCRIPT!

Fire up a Terminal and enter the following (use as separate lines):
```

sudo chmod +x alsa_setup_1.0.18.sh
sudo ./alsa_setup_1.0.18.sh

```

The script will download the ALSA 1.0.18a drivers from the ALSA-PROJECT website and install them automatically, will take approx 10-20 mins depending on connection.

After restart come back and continue...



After restart add the sound control app on to your panel if u have not already.

right click on the app and go to preferences:

For the device select HDA Intel (Alsa mixer)
now for every entry underneith (Master, Headphone, PCM, etc...)
left click to open sound control on the panel app. select each entry and unmute it from its position, the new driver mutes every entry as a precaution i guess.

And that should be it!




**HDA VERB HIGH DEFINITION AUDIO SET UP**
This installs the HDA VERB in an attempt to use the full potential of our speakers, its not too shabby.

```

wget ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.3.tar.gz
tar -xvmf hda-verb-0.3.tar.gz
cd hda-verb-0.3
make
sudo cp hda-verb /usr/local/bin  
sudo gedit /etc/rc.local 

```

now add this string:
```

/usr/local/bin/hda-verb /dev/snd/hwC0D0 0×15 SET_EAPD_BTLENABLE 2

```

save and exit, now just restart and hda verb shall be installed!
before the exit 0
**--------------------------OSS4--------------------------------**
This method installs the OSS4 driver which then u can program the cinedash to use as a volume up/down but since it is not a native driver to ubuntu it may cause some trouble. One is a lower volume expected than regular.

  You can follow this guide: [https://help.ubuntu.com/community/OpenSound]("https://help.ubuntu.com/community/OpenSound")

Download my easy to install script from to you home folder:
[http://www.box.net/shared/3o33r9guai](http://www.box.net/shared/3o33r9guai)

Download the libflashsupport.so.gz to you home folder: 
[https://help.ubuntu.com/community/OpenSound?action=AttachFile&do=view&target=libflashsupport.so.gz](https://help.ubuntu.com/community/OpenSound?action=AttachFile&do=view&target=libflashsupport.so.gz)


now fire up a terminal and put in:
chmod +x oss4_install.sh
sudo ./oss4_install.sh

This will download and install the OSS4 driver follow instructions from the terminal, make sure u set the default driver as OSS rather than the default ALSA.


Now to be able to manipulate sound you will need to use the ossxmix program that comes with the OSS4, u could also likewise use ossmix, but ossxmix has a gui. 

1. Go to your System > Preferences > Sessions
2. Click "+ Add"
3. Type in the name of the program: OSS X Mix
4. The command will be ossxmix
5. Then enter the description "Volume Control For OSS4



      Reboot and your sound should work!

You will see a new item in the sys tray, it a black square with a neon blue writing on it, thats ossxmix. Clicking that will open a full screen sound manipulation... which kinda sucks... but its good for what  need it for. 











=====================================================================






CineDash: WORKS WITH OSS4 (with this configuration)::: WORKS FINE WITH THE ALSA DRIVER (Tho it stops working randomly...)

Theres two procedures, a patch for GStreamer [Patch]("http://ubuntuforums.org/showpost.php?p=4874981&postcount=2")

Which turned out a bit buggy for my rhythmbox with very very fuzzy sound (but made my cinedash work fine). You'll have to switch to amarok in order to fix the fuzz, and even then your shortcut keys for play/pause won't work. (at least to my attempt)

If you want to stay in Rhythmbox here we go:


**Configure CineDash**

   First unhide the configuration editor in the Applications > System Tools menu by going to System > Preferences > Main Menu

   On that window click on the "System Tools" on the left folder tree
   Configuration Editor should be on the very top, check the box and click close.

   Now we'll need to create some scripts
   Create new folder in home folder and go into it:
   
   ```

   mkdir ~/.volumeControl
   cd ~/.volumeControl
   
```

   create first script to lower the volume:

   ```
pico lowerVol.sh
```

   Now just copy and paste the following into the terminal text editor pico that you just started:

   ```
 #!/bin/bash 

VOL=$(ossmix | grep misc.mix21 | awk '{print $4}' | awk -F : '{print $1}')
 VOL=$(echo $VOL-8 | bc)
 ossmix misc.mix21 $VOL:$VOL

```

   now press Ctrl + x
   It will ask you if you want to save, press y then enter

   now to make a script for volume up!

   ```
pico raiseVol.sh
```
   
   then copy the next code in the term...
  
   ```
 VOL=$(ossmix | grep misc.mix21 | awk '{print $4}' | awk -F : '{print $1}')
 VOL=$(echo $VOL+8 | bc)
 ossmix misc.mix21 $VOL:$VOL

```

   again 'Ctrl + x' then 'y' then 'enter'.

   and one more script:

   ```
pico mute.sh
```

   then the next code copy to term..

   ```
 #!/bin/bash

 VOLUME=$(cat $HOME/.volume)
 if [ -z "$VOLUME" ]; then
       VOLUME=$(ossmix | grep misc.mix21 | awk '{print $4}' | awk -F : '{print $1}')
       ossmix misc.mix21 0:0
       echo $VOLUME > $HOME/.volume
 else
       VOLUME=$(echo $VOLUME + 1 | bc)
       ossmix misc.mix21 $VOLUME:$VOLUME
       > $HOME/.volume
 fi


```

   Againt with the 'ctrl+x' 'y' 'enter'
  
   no more scripts! just one more file.

   ```
pico mute.txt
```

   then just type in "0:0"  (without quotes)
   and press 'ctrl + x' 'y' 'enter'

   The mute.txt file will keep track of whether the system is muted or not so it knows to mute or unmute.

   Now we'll have to make each of these scripts executable by running
  
   ```
chmod +x mute.sh
```

   Just do this for the other two scripts and ur done with this part..

   Good! Now we have to bind these scripts to our CineDash
   The CineDash uses regular keyboard interrupt requests (signals) so we just need to find what those signals are!

   open your regular keyboard shortcut editor
   and now open your config editor Applications > System > Configuration Editor

in the configuration editor navigate to metacity   apps > metacity

 in here you set shortcuts to many things, and edit anything to do with metacity (your window manager)

go to 'global keybindings'

in here you'll see keystrokes that will do certain things we're looking to make our own shortcuts so go under run_command_1 next to it you'll see "disabled" click on the disabled and it'll ask for some text. this is where we need to know which signal codes our keys give so we can bind that code with a command. So go to ur Keyboard Shortcuts window and analyze mute, volume down, and volume up. Right next to each is a set of text
something in the lines of 0x0a 

you want that text, thats the keyboard code for that key. so go to your config editor and under run_command_1 put in the text u see under "Mute" on the keyboard shortcut window. and do the same for volume up with run_command 2 and volume down with run_command_3

So now we have them binded! But the metacity doesn't know what to do when you press those keys, it knows its there, but doesn't know what to do in particular.

now on the config editor go to "keybindings_command" 

its in the left file tree in the same directory as "global_keybindings" in the metacity directory.

and in this folder we'll see "command_1" and so forth. This is where we tell metacity what to do when we press mute, volume up, and volume down. We already identified what the keys were when we set the '0x0a'-etc. and other text in the 'run_command_1'

Now we just have to bind those scripts we made to those keys
we made run_command_1 bind with mute
run_command_2 bind with volume up
run_command_3 bind with volume down
  
so all we have to do is go to command_1 click on the right under "value" (its probably blank) then type in the directory of our scripts including the script.

/home/<your user id>/.volumeControl/mute.sh

and the same for volume up (command_2) and volume down (command_3)

after your done with that.. .your done! restart the x server with ctrl + alt + del and now your volume control should work!  The mute will be a little fussy because on the CineDash when you activate the mute it stops control of volume, Ubuntu doesn't have a driver for CineDash to recognize if CineDash itself is muted. So when you mute you might lock the CineDash, but Ubuntu will Un-mute, so just use the fn-f8 key to balance the mute on ubuntu with the lock on cinedash... small bug.









=======================================================================



Ethernet is actually rather simple


**Ethernet**

download the driver into your home directory:
[http://ubuntuforums.org/attachment.php?attachmentid=81153&d=1218480703]("http://ubuntuforums.org/attachment.php?attachmentid=81153&d=1218480703")

go into your terminal 
and run these:

```
cd ~
mkdir l1e-linux-v1.0.1.0
cd l1e-linux-v1.0.1.0
cp ../l1e-linux-v1.0.1.0.tar.gz .
tar xzf l1e-linux-v1.0.1.0.tar.gz
cd src
sudo KBUILD_NOPEDANTIC=1 make
sudo KBUILD_NOPEDANTIC=1 make install
cd /lib/modules/2.6.24-16-generic/kernel/drivers/net/atl1e/
sudo insmod ./atl1e.ko

```
and thats it! you got your network card working with ethernet :guitar:











Thats all that i could find that works with the Acer 6920. The rest i have not found yet... I know the mic support will have to do with the sound driver OSS4, and i've seen that an updated ALSA and Verbose makes the sound work fine, but will crash when trying to use multiple apps with sound, the ALSA might also support the mic... 

Kopete seems to work, but sometimes me and the recipient can only see a black box...
[[Kopete will work fine with camera if you install the Jasper from the ubuntu repositories, use synaptic to search. If you compile from source u may be broadcasting a black box... dont know how that works.]]

The SD card is what i really want to get working, after that i really don't need anything else (but i would like everything to work flawlessy :P)

Hope this tutorial helped configure your Acer 6920 to function for you =]

If anyone has any hints to kopete or mic (sound driver) or SD card, PLEAAASSE respond =]


Reports:

ALSA 1.0.18a:
Also works on a Intel HDA 8280I (ICH9) sound with a Dell Inspiron 1440.

---

### Post by Djustin on 2008-09-16
Hello,
I have got mine laptop for 2months and had been wondering when something like this would come up
i gave up within days when i figured i couldnt fix it ^^
(sound,graphics,...)
im gonna test it now in Kubuntu KDE4 ill let you know if something doesnt work^

Another THANK YOU
(also could you describe how you installed the 9500m GS Vidcard)

---

### Post by aralbald on 2008-09-16
Hey! Very nice collection, thank you! The volumeContol stuff is new for me, will try that in a while :)

Does your brightness function keys work (fn+left or right arrow)?

Oh and Djustin, the 9500GS is configured the same way as any other nvidia card - From the restricted drivers manager

---

### Post by Djustin on 2008-09-17
i dont see that button on the KDE4 -.-"
well the ethernet connection works
but only my wireless is there, but cannot connect to my network
the router is setup not to broadcast,n-only,WPA2-personal
any suggestions?

---

### Post by CJay554 on 2008-09-23
Because your router is not broadcasting your going to have to manually set up the connection:

either by leaving roaming mode or by clicking on ur icon for the wireless in your systray, then "Connect to other wireless networks..." 

Put in your ESSID (name of your wireless) then the encryption type/key and that should let you communicate with the router.

I never configured my graphics card, was never in my proprietary drivers. Seemed to work fine out of the box? Keep in mind theres the 6920, 6980, and im sure other models with different functions, but the basics are the same.

I really want the SD card to work =[

Oh, and with Kopete, install the jasper from repositories, search in synaptic, when i installed from source on jasper host site, it gave me a black box when broadcasting camera, but when i installed from repo's it worked perfectly! although yahoo cam on kopete lags a little more than vista, small price for good functionality ;]

Brightness buttons worked for me out of the box.

---

### Post by Freaky_Llama on 2008-09-26
Thank you for this post. after having linux absent from this laptop for months, I decided to search and try again.

I have sound, however, I cannot control the level from both the pad or a mixer. I have followed this guide to the T, and done searches around for fixes. Are there any recommendations?


DERRRRRR 

People, check to make sure whether you're running 32bit or 64bit. 
My mistake was since I installed Ubuntu via Wubi, I had no idea it was 64bit. Once I copied the right file over and restarted the volume control, it started working. The control pad works now too!

---

### Post by frac on 2008-10-14
Heya. thanks for the tutorial

I tryed to make it to work with alsa using the alsa update to version 1.08.rc3

first using using this [http://ubuntuforums.org/showthread.php?t=820959]("http://ubuntuforums.org/showthread.php?t=820959")

but when I rebooted could not load the snd modules after running around in circles for a while I found this [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/200491]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/200491") 

the problem was oss that I installed removing the dir /lib/modules/`uname -a`/kernel/sound  and removing the soundcore.ko that was inside.

so I removed the oss from /usr/lib/oss (the one from mercurial)

reinstalled the kernel with

sudo apt-get install --reinstall linux-image-2.6.24-21-generic

and everything was dandy..

alsa and all the only problem left is the headphones.. when you plug it it doesn't stop the playback on the main speakers

and on reinstaling the

---

### Post by no0ne on 2008-10-15
Those looking to get the alc889 sound chip (ships on both acer aspire 8920 and 6920) working should take a look at [this]("http://ubuntuforums.org/showpost.php?p=5917661&postcount=4").

The integrated speakers can be muted (ironically) by muting your headphone. Found this out just by trial and error. (That would be with alsa 1.0.17 on hardy 32-bit.) :D

The ethernet fix above is missing a little bit, since after driver version 1.0.0.4 the insmod line hasn't been enough to make the module load by default (anymore), so you should add "atl1e" without the quotes to /etc/modules. Complete instructions [here]("http://jan.ucc.nau.edu/wal2/atheros_attansic.html").

Working on the mic now, though I think the problem will be resolved with the next release of alsa since they've released [a patch]("http://kerneltrap.org/mailarchive/git-commits-head/2008/2/1/670014") (patch_realtek.c) for alsa to add support for the three realtek chips. So far I've been unable to compile alsa (1.0.17 and 1.0.18 rc's) succesfully with the patch though, so I am very excited to see the next stable release.

After some research about the TV chip it became clear that this is a basic device and even though the version of the chip in Aspire 6920 ships with vista drivers there is [no single driver available]("http://www.avermedia.com/avertv/Product/ProductDetail.aspx?Id=370") for download, so if you want to have a working tv chip you might want to consider buying a supported pcmcia or usb device instead.

---

### Post by glethro on 2008-10-20
wow great tutorial it actually made sense :D
haha
but i still have problems with the sound.. or lack of :P

when i go to system> preferences> sound
and click "Test"
i get this weird error
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

i flicked through the different options (ALSA,ESD,OSS,PulseAudio) but it changed nothing

i thought it might be because i tried getting pulse audio to work before i found your tutorial.. but i have no idea...
any ideas?

---

### Post by rab4567 on 2008-10-20
Same here.

---

### Post by CJay554 on 2008-10-21
Im sorry i can't quite understand the error, you followed the instructions completely? i found it easy to make a bash script to install everything for me, just by copying all the lines of code i listen in a file and adding #!/bin/sh in the first line.
running chmod +x <file.sh> 
and running ./file.sh

just pay attention when it prompts for any information. This sound tut works perfectly for the Acer 6920 on Hardy Heron, i haven't tried other. make sure ur statistics are the same

---

### Post by khurtsiya on 2008-10-22
> **rab4567 said:**
> Same here.
Hi, CJay554!

Many thanks for this guide.

I still can't configure my display. My max screen resolution is 800x600.

Any tips will be appreciated.

TIA

Michael

---

### Post by glethro on 2008-10-22
for the video adapter:
all i had to do was enable the restricted drivers. 
i think u do it by
System> admin>hardware drivers

than enable the restricted nividia drivers

---

### Post by eTiMaGo on 2008-10-23
Thank you so much for this, I have one of these laptops too (they rock!) and I'm a very much a Linux n00b...

I have the version with 4GB RAM, which causes some incompatibility with the kernel and the video memory addressing, somehow got that to work, but I still have several minor issues (no sound!)

So, I think, once Improbable Iraqi is released, it's time for a fresh start!

---

### Post by khurtsiya on 2008-10-26
Sound is warking good, but it is to quiet... What can I do to make it louder?

TIA

Michael

---

### Post by glethro on 2008-10-26
guess ill just reinstall ubuntu.. what a pain :P
now i actually have to logon to vista :( ... tht os.. makes me soo mad..

---

### Post by khurtsiya on 2008-11-01
> **khurtsiya said:**
> Sound is warking good, but it is to quiet... What can I do to make it louder?

TIA

Michael

Any tips? ](*,)

---

### Post by aralbald on 2008-11-02
Nope... The sound is quiet and flat :)

---

### Post by costre on 2008-11-03
Just had to say thanks for the tutorial, I just bought my own acer laptop, the Acer AS8920G. I like this series, thanks to the bluray player, the 16:9 display and the hardwares capability of displaying HD movies.

Hopefully I'll get everything to work :)

---

### Post by CJay554 on 2008-11-04
Compared to how the drivers work in Vista with the Audio, the Ubuntu hardy drivers aren't as loud (no surround sound as promised with acer) so you'll be stuck with regular sound..

Ubuntu 8.10 has come out and im excited to see what will be done to address this! so far i don't see a difference other than the Ethernet is recognized.
The sound is still void, unless im missing something...

---

### Post by supern00b on 2008-11-08
thank you so much for this guide, i followed the steps from this site
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
and now i have sounds o my acer 6920 again!
the only problem is that it is much quieter than i was expecting, is this normal for linux? my only other problem is that the volume control next to the time and date on the "start bar" does work, when i click it i get this message - "No volume control GStreamer plugins and/or devices found." is this normal? do i need to get a new app to fix this? i am very new to this OS so the simpler the solution the better.

thanks

---

### Post by CJay554 on 2008-11-16
Oh im sorry i totally forgot about the volume control, for that you will have to use ossxmix

go into your system > preferences > session  in there add the program "ossxmix" you can name it whatever, this will let ossmix start with login. You can either way start it by going to the terminal and typing "ossxmix &" and enter  (the & lets the computer know to run that command in the background so it doesn't keep the terminal busy)

---

### Post by CJay554 on 2008-12-07
Great News!!! and one not so great... 

ALSA has a new updated driver that works nicely with Ubuntu and our beloved acer 6920's!!

Bad News... Ubuntu 8.10 still encorporates a lower version of the driver, so you would have to manually install the alsa driver...

heres the guide:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
the newest one so far i believe is 1.0.18 (the one i installed)

Mic still doesn't work tho..
After install make sure to unmute all of your sounds (PCM, front, mic, master, etc)
i had some odd problems with it but it turned out everything was mute after the install

Also, when editing the "options snd-hda-intel model=MODEL"   for MODEL put in "auto" without the quotes.  

Don't expect the CineDash to work however.. for some reason it looses its functionality after the driver update... but at least now you HAVE sound o.o

I'll incorporate this into the full guide once everyone is able to settle this and confirm that it works. 



Cheers!

---

### Post by khurtsiya on 2008-12-08
Great news CJay!

I am lame, so I will wait for guide. Also I have installed ossxmix, so for me it will be harder, cuz I must uninstall it first I guess(

---

### Post by khurtsiya on 2008-12-08
edit double

---

### Post by CJay554 on 2008-12-08
I edited a script to encorporate 1.0.18 (latest driver) to install on your system:  
(note you need ALSA to be installed, if u already installed OSS4 follow the link at the end of this post to reinstall ALSA)

just download this to your home folder:

[http://www.box.net/shared/454ic17as0](http://www.box.net/shared/454ic17as0)

then go to your terminal and do these commands:

```
 
sudo chmod +x alsa_setup_1.0.18.sh
sudo ./alsa_setup_1.0.18.sh

```

each line seperately.

It will download the 1.0.18a drivers from the alsa-project site and automatically install it on your system. It will also automatically restart your computer when its done, so make sure your not working on anything and save everything you are working on. Will take ~10 mins

After restart come back to ubuntu and report if your sound works so i can update my guide.

Cheers!


[ADD]

If you have already installed OSS4 and want to go back to ALSA and then try the script above, follow the first post here (#331): [http://ubuntuforums.org/showthread.php?p=5539687](http://ubuntuforums.org/showthread.php?p=5539687)

---

### Post by rab4567 on 2008-12-09
No luck for me.

---

### Post by rab4567 on 2008-12-09
Don't get get me wrong cjay you've been a great help to us all I just want to thank you for your hard work. I'm still a noob at this stuff and until linux sinks down into my head will I understand how its works. Meanwhile can you give me a command to review the new alsa i just downloaded thanks.

---

### Post by CJay554 on 2008-12-09
I just wanted to see if the installation will work as is with the commands to install, now do this:

```

sudo nano /etc/modprobe.d/alsa-base

```

then add this to the end of the file:
```

options snd-hda-intel model=auto

```

press ctrl+x then press Y to save changes and then enter to save.

then restart your system: The model=auto will tell the alsa to look at the bios for your sound card version/etc, and because this is a laptop the bios will have all hardware information.

now as you log in see if you hear the logging in sounds. If not, go into System>Preferences>sound  and set all to "ALSA -Advanced Linux Sound Architecture"

then add the volume control to your panel if you haven't already: and right click on the volume control and click preferences:
changed the device to "HDA Intel (Alsa mixer)

and underneith there will be a bunch of options "Master" , "Headphone", etc. 

Highlight each one and and use the volume control on the panel to unmute all of the entries.

After that try playing some music or something. 

This is the exact way i configured my soundcard to work on my 6920. Report back plz. thanks!

Oh and rab don't worry, this is a trial and error thing, it'll work soon! hopefully with these modifications. The card is already read by 8.10 we just need to configure it a little! thats it =] 
I'll add the commands and their correspoding functions when we get this settled, so lets get this over with :P

---

### Post by rab4567 on 2008-12-09
Yippeeeeee that worked I've waiting for months and you came in for me, if only I could do a cartwheel. There are a few issues the mike and cheese no longer works as well as the cinadash except for volume control you must tap it to go full throttle weird but thats minor. Thank you, thank you, thank you!

---

### Post by CJay554 on 2008-12-09
I guess that's why they might have not added the new ALSA to the ubuntu...
If i had a guess i would say that this might be a hardware conflict.. soundcard and camera, maybe an IRQ request?...
Grr.. not cool...

My CineDash doesn't work at all either... But i made shortcut keys ctrl+up for volume up and ctrl+down for volume down...

Well we got some good functionality out of this... but lost others... I'll start another thread on those problems. I'll add this to the manual soon!

In the meanwhile keep posting updates! 
Tell me any other issues there might be with the system so i can add a "disability" to the driver update..

---

### Post by CJay554 on 2008-12-09
@rab4567    Did you have to unmute all the sounds? just curiousity, or did it work after restart?

[ADD] OH! and camera DOES work, but it works only under 160 x 120 resolution (very pixily...)

---

### Post by rab4567 on 2008-12-10
> **CJay554 said:**
> @rab4567    Did you have to unmute all the sounds? just curiousity, or did it work after restart?

[ADD] OH! and camera DOES work, but it works only under 160 x 120 resolution (very pixily...)

The sound came on as soon as I rebooted, however the unmute key F8 does not work. I'm to going mess around with the alsa mixer and try to get the mike  working, and oh yeah the headphones work perfectly.

---

### Post by CJay554 on 2008-12-10
Another fault, for some reason when i leave my laptop running over night in the morning its crashed. the caps lock button and the wireless blinking button blink continually but idunno what happened, i have to hard shutdown and put it back up..
Has not happened before ALSA was installed.

---

### Post by rab4567 on 2008-12-11
> **CJay554 said:**
> Another fault, for some reason when i leave my laptop running over night in the morning its crashed. the caps lock button and the wireless blinking button blink continually but idunno what happened, i have to hard shutdown and put it back up..
Has not happened before ALSA was installed.

I've leave my laptop on all week long no problems the only lock up or crash occurred was when I turned on the screen saver. Sometimes the cinedash does work during the day I guess there is some conflict, but I'm still having trouble getting the mike to work, but no matter I have sound.

---

### Post by CJay554 on 2008-12-12
Yeah it only freezes for me on some occasion.. really weird...

Anyway, i updated my guide to install the ALSA driver, as well as modified my OSS4 installation with a simple to execute script that will install everything for you, just make sure you download the right things to you home directory!

Cheers! :popcorn:

---

### Post by aralbald on 2008-12-13
Just a little tip for the volume control:

Run gconf-editor, go to /apps/gnome_settings_daemon/ and change volume_step to 13.

Now the indicator on the cinedash panel shows the real volume :)

---

### Post by Sultan-mrm on 2008-12-13
hi all

I have acer 6935g and every things working good
except SD card I didn,t find the driver

but when insert my data sd card and restart the laptop 
 I saying WOW it,s work :guitar:

I can not believe that 

all of you just do that and see.

):P

Regret bad language.

---

### Post by Sigsaucer647 on 2008-12-14
ugh!!! i did exactly wat you said, and it all installed fine
but, when i trie a different way from someone before, it messed up the sound, so when ever i try to unmute it, i get "no volume control GStreamer plugins and/or devices found"

why wont it work!?!?

---

### Post by Shinger on 2008-12-14
I have the 6920G .. and im using Ubuntu 8.10 with the "old" ALSA drivers. But my question was.. does anybody have a problem with the sound speakers. My problem with my laptop is that only the right speaker works and sometimes the left one works but just for 10-20 seconds.

I dont know if its because of the drivers or maybe i just have blown it up.. I dont have Winxp or Vista on it. Because vista needs to be installed first -_-!.. and winxp needs satacontroller drivers -_-!.. 

MS a company with alot of money but the work they spent on their products its just POOORR!!

---

### Post by rab4567 on 2008-12-16
> **Sigsaucer647 said:**
> ugh!!! i did exactly wat you said, and it all installed fine
but, when i trie a different way from someone before, it messed up the sound, so when ever i try to unmute it, i get "no volume control GStreamer plugins and/or devices found"

why wont it work!?!?

I'm sorry to have say this, but you may have to reinstall 8.10 to it get back to the normal settings then try again it does work.

---

### Post by Sigsaucer647 on 2008-12-16
> **rab4567 said:**
> I'm sorry to have say this, but you may have to reinstall 8.10 to it get back to the normal settings then try again it does work.
how do i do that?
i have an install disk...
do i have to delete everything? or do i just put the disk in again?
sorry if im a pain, im new to this stuffs =d

---

### Post by rab4567 on 2008-12-16
> **Sigsaucer647 said:**
> how do i do that?
i have an install disk...
do i have to delete everything? or do i just put the disk in again?
sorry if im a pain, im new to this stuffs =d

YOU ARE NOT A PAIN! First tell me what set up you have on your acer is it a dual boot or anything?

---

### Post by Sigsaucer647 on 2008-12-16
im dual booting vista which came preinstalled and ubuntu 8.10

---

### Post by CJay554 on 2008-12-16
> 
but, when i trie a different way from someone before, it messed up the sound, so when ever i try to unmute it, i get "no volume control GStreamer plugins and/or devices found"


What did you install then? OSS4? if you did follow my reply on page 4 on how to uninstall the OSS4 and go back to alsa, you dont have to reinstall the ubuntu system completely... but if you want you can, its nice to clean up sometimes. I do recomend you split ubuntu into a root drive "/" and a home drive "/home"  heres an idea how:
[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

usually when you install ubnutu you just simply make a / partition in the form of ext3... and you mount it on /

but to make a /home a well, you simply do:
/  ext3        10 gb
/home ext3     <as big as you want>gb
swap linux-swap <depends on RAM>gb

so when you re-install ubuntu all you have to do is format the / partition, and ONLY MOUNT the /home partition and you will still have the files that you usually had (music/pics/documents) but the programs will be erased sinse they install on the / partition. DO NOT FORMAT THE /home partition.
...
Just an idea, it saves me alot of time especially when i want to install a new ubuntu rather than update cuz sometimes updates can go horribly wrong no matter what the system...

---

### Post by rab4567 on 2008-12-16
> **Sigsaucer647 said:**
> im dual booting vista which came preinstalled and ubuntu 8.10

You need to back up your files burn to dvd.

---

### Post by Sigsaucer647 on 2008-12-16
thanks guys, you've been a lotta help, i have to take midterms, so ill try reinstalling on friday

---

### Post by CJay554 on 2008-12-26
> **rab4567 said:**
> You need to back up your files burn to dvd.

uhhh, 170 gb's of stuff isn't easy to backup on DVD's ;)

I still get a bunch of random freezes though i can't pinpoint what it is... all i know is my Caps Lock key goes haywire...
anyway. Nothing on the other modules yet (mic, camera fix) I hope this gets easier to fix...

I would like feedback if anyone has installed this and it worked for them! Whether it be the Acer 6920 or any other model!
Feedback is what grows this community!

Much Appreciated [=

-ADD

The freezing problem seems to be happening after the Intrepid Update for me... and another user with a 6920

If your running Intrepid and on a 6920 check here:
[http://ubuntuforums.org/showthread.php?t=976287](http://ubuntuforums.org/showthread.php?t=976287)

It might be safe to go back to 8.04 since i or others didnt have this problem at that time.

---

### Post by khurtsiya on 2008-12-28
Sound works now! Thanks!

---

### Post by CJay554 on 2009-01-06
The misfunctional CineDash pad after the update is definitely a gnome issue. As i recently decided to try out Kubuntu (looks very shiny =] ) and i updated my driver as so in the guide, and my cinedash worked fine! Weird... but the pause/play button is a bit weird... it pauses Amarok.. then it plays it again, both actions with one press...

So many tiny bugs that prevent everyone from having a good time =[
Luckily i love fixing bugs :P

---

### Post by monitorman on 2009-01-15
Thanks!

I'd been spending more time on the Vista partition of my HD, and was missing Ubuntu.
I've got sound, and have everything set up the way I like.

Thanks for this fix!

Acer AS8920-6432

---

### Post by alpho2k on 2009-01-15
Thanks for this topic, my sound work fine now!

Does anyone successfully configured the mic on the acer 6920?

---

### Post by CJay554 on 2009-01-18
{{UPDATE}}

Alright, i found a slight problem that effects the camera + volume control: The 2.6.27-9 kernel. 

I re-installed my ubuntu system trying to fix my random freezes (which is caused by something else btw) and reverting back to 27-7 i decided to test an see whether the alsa 1.18 driver would effect my system as it did before, it didn't. Im currently running ubuntu 8.10 (note, alsa 1.18 does not seem to fix the problem in ubuntu 8.04 since it uses kernel 2.6.24).

Running 8.10 with kernel 2.6.27-7 with instaled alsa 1.18, my camera works perfectly as it did before, my volume control works flawlessly as well!

One issue, the broadcom driver for our wireless (what it automatically comes installed with on ubuntu as the driver) has a few buggy issues revolving data transfer, the higher the load the higher the chance of a kernel panic and freeze, or if you attempt to connect to a n secure wireless network it will also kernel panic, i haven't actually found a fix for this yet, not sure if there is one, but it should be fixed as reports are flowing in about this problem on launchpad.

[COLOR="Red"]**[B]Volume control still seems to be unworkable.**[/B][/COLOR]
ADD: Volume control DOES work, but when logging in you have to make sure you DO NOT have the CineDash on "Hold", if you log in with it on hold (pretty much turning off the whole pad) ubuntu has no driver to probe the driver to see if its working or not, but if its off of hold ubuntu can detect the controls! =]

I will be making a PDF file documentation with a more organized look and feel of this guide and in due time, are there any suggestion as to what else (appart from my guide) should be in there? If so point to the corresponding forum and I will look it over to see if it has not been solved yet here. 
CHeeRs~!

---

### Post by alpho2k on 2009-01-19
I just installed the new version of alsa (1.0.19) and the mic still doesn't work,

I really really want to make it work. Anyone has an idea? This is the only reason I am always rebooting on vista.

I know the mic will work with oss4 but if I install oss4, a lot of others thing will not work (amarok2, dragon player,etc).

---

### Post by alpho2k on 2009-01-27
Anyone got also this problem with the mic?

---

### Post by khurtsiya on 2009-01-27
> **alpho2k said:**
> Anyone got also this problem with the mic?

I think everybody))

---

### Post by weirdfox on 2009-01-30
> **CJay554 said:**
> 
[COLOR="Red"]**[B]Volume control still seems to be unworkable.**[/B][/COLOR]
ADD: Volume control DOES work, but when logging in you have to make sure you DO NOT have the CineDash on "Hold", if you log in with it on hold (pretty much turning off the whole pad) ubuntu has no driver to probe the driver to see if its working or not, but if its off of hold ubuntu can detect the controls! =]


That's strange, I have a Aspire 6920 and the cinedash works flawlessly  even when on hold at login time (except the volume level indicator, but it does not work on windows either, so I don't realy care) and it does not need any configuration for any of it's keys...  
Am I the only lucky one ?

But I have another problem, the sond works well when upgrading Alsa (I'm now using alsa 1.0.19, with [AlsaUpgrade]("http://ubuntuforums.org/showthread.php?p=6589810") ) but, when resuming from sleep mode there is no more sound and nothing get it back ecxept a reboot (even unloading all the alsa drivers and loading them back)...

---

### Post by matmat07 on 2009-01-30
Taken from another thread, it fitsmore here:

In the firsts boot of kubuntu, I had no sound. The aplay -l command worked. I tried to seek solutions which got things worst. One of them was the attached script. I tried to remove some of the things it did, but I'm a new users and I don't understand every command. Anyway, now the aplay -l command doesn't show the devices. I must do the following command to make the sound work:
```
sudo modprobe snd-hda-intel
sudo /usr/local/bin/hda-verb /dev/snd/hwC0D0 0x15 SET_EAPD_BTLENABLE 2

```
But I must do them at each boot for an unknown reason. After booting kubuntu, the sound doesn't work again. Here's the output of the command when it works:
```
**** List of PLAYBACK Hardware Devices ****       
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Ps: I'm on vista right now, so I cannot upload the fle again, it's there : [http://ubuntuforums.org/showthread.php?t=1053575&highlight=6920g+sound]("http://ubuntuforums.org/showthread.php?t=1053575&highlight=6920g+sound")

---

### Post by alpho2k on 2009-01-30
Hi,

to make the sound work, just add this line at the end of this file : /etc/modprobe.d/alsa-base and reboot after

```
options snd-hda-intel model=auto
```

it worked for me!

If it doesnt work, wich version of alsa do you have?

---

### Post by CJay554 on 2009-01-30
i incorporated that line to be added inside the script so it SHOULD work, i just did it not too long ago so try the script again and see if it works, this is for the acer aspire 6920 so please post which machine you use if you use other

---

### Post by alpho2k on 2009-01-30
The script of CJay554 is at page 3 by the way.

His script works very well!

If you want alsa v1.0.19, just change in the script the 3 line containing 1.0.18a by 1.0.19.

If you want to know your version of alsa, use this command :


cat /proc/asound/version

---

### Post by matmat07 on 2009-01-31
I uninstalled oss4 using the post on page 3 and reinstalled ALSA with is script. Now aplay -l works at boot, but there's still no sound and I can't make it work anymore with the hda-verb command.

---

### Post by alpho2k on 2009-01-31
What is the result of this command?

```
cat /proc/asound/version
```

---

### Post by matmat07 on 2009-02-01
Advanced Linux Sound Architecture Driver Version 1.0.17.

Should I upgrade to 1.0.18 or 1.0.19?

---

### Post by alpho2k on 2009-02-01
> **alpho2k said:**
> The script of CJay554 is at page 3 by the way.

His script works very well!

If you want alsa v1.0.19, just change in the script the 3 line containing 1.0.18a by 1.0.19.

If you want to know your version of alsa, use this command :


cat /proc/asound/version

Do as I said here :)

---

### Post by matmat07 on 2009-02-01
Thanks, it finally works. I didn't had the time to look, but the script couldn't compile correctly the files and rebooted before I could see there was an error. I delete the file in usr/src/alsa redone the script and it worked. There's just one thing I'm wondering: is there supposed to be a boot sound, like in windows?

---

### Post by alpho2k on 2009-02-01
Great!

For gnome and kde there is one at the startup. Wich distribution do yo have? Did you check your alsamixer?

---

### Post by matmat07 on 2009-02-01
I have kubuntu. What should I check? This time, just played a song in Amarok without doing something else and it worked.

---

### Post by alpho2k on 2009-02-01
I was wondering if maybe there was a muted sound in alsamiser or something like that...

---

### Post by matmat07 on 2009-02-01
I unmuted everything, rebooted, and still no boot sound. I don't understand everything, but could it be the hda-verb thing loading after the boot sound and enabling the sound?

Also, one day I stumbled upon some command to change the cinedash volume step when pressing + or - . Do you know where I could find it.

---

### Post by alpho2k on 2009-02-01
Soory, I really dont know!

---

### Post by CJay554 on 2009-02-12
I Updated my script to include a version variable wherein you can change which version you would like to download by editing the script variable.

I found a problem. If you have tried to update alsa multiple times and u happen to have not had any luck try doing sudo rm /usr/src/alsa/* to remove old installation files as that will cause the script confusion, i will figure out a way to do this in the script with due time. the new download is in the same link: [http://www.box.net/shared/454ic17as0](http://www.box.net/shared/454ic17as0)

By default this script will install the newest version: 1.0.19

CHeeRz!:popcorn:

---

### Post by atarifreak on 2009-02-13
hi!

im using 8.10 and the only thing i need to do is
```
model=auto
```

any solution for 5.1 surround sound?

---

### Post by alpho2k on 2009-02-13
I just created a blog in wich I will list all the problems I have with ubuntu on an acer aspire 6920.

[http://monespaceperso.org/blog-en](http://monespaceperso.org/blog-en)
	
Thank you to make a short visit :)

---

### Post by CJay554 on 2009-02-14
BUG ADD:
I would recomend sticking with the 1.0.18 driver, i have taken the .19 driver for a test spin but it seems that after i shut down my firefox browser after watching a youtube video (or other website that uses sound). After i shut it down and open rhythmbox, it would not start playing music. (There has been an issue with ALSA playing more than one sound at a time). While in .18 you just have to close down one of the applications for the other to work, for the .19 i have to do restart my login in order to reset whichever node that tells the alsa driver its free to be used again, just simply turning off one or the other doesn't seem to work as well as the .18. I have reconfigured the script to install .18 by default as it is much more stable.

---

### Post by atarifreak on 2009-02-14
THE SOLUTION: [http://ubuntuforums.org/showthread.php?t=1013750](http://ubuntuforums.org/showthread.php?t=1013750)

---

### Post by CJay554 on 2009-02-17
HDA-VERB isn't as stable yet so I'll pass on adding it to the guide for now, if anyone would like to report how it does compared with without it, and if its good enough i'll add it to the guide

---

### Post by atarifreak on 2009-02-21
its nice. but i need to run your alsa-setup script again after some updates.

Any other solution to get real good sound? oss4 ? i'm not shure i want to try it...

---

### Post by alpho2k on 2009-02-21
Dont use oss4.... Its old and you have to reconfigure each application to use it. Also, Amarok2 wasn't working when I had oss4.

---

### Post by CJay554 on 2009-02-25
yeah, so far the best choice is alsa 1.18, but i mean, it works really good, apart from the windows counterpart with the fake bass attempt, it all works nicely

---

### Post by pm608 on 2009-03-10
So, I got my sound working (:D) but the mic is still dead... Any solutions for that?

---

### Post by CraigBray on 2009-03-25
I have the ALC889 sound driver, but as i posted [here]("http://ubuntuforums.org/showpost.php?p=6749447&postcount=14") in [this]("http://ubuntuforums.org/showthread.php?t=1013750") thread.
As you can see rev04. if any of you have this very same revision, please pm me or something to tell me anything you did, or what thread/tutorial helped you. Vista x64 pisses me off so much lol.:confused:

---

### Post by CraigBray on 2009-03-28
I seem to have found a sensible fix. You need to bail on Alsa, and instal OSS4. Here is the guide.[https://help.ubuntu.com/community/OpenSound]("https://help.ubuntu.com/community/OpenSound")

This seems to have worked. Is it just me? or does the keyboard have a weird lag as well?

---

### Post by Changturkey on 2009-03-29
Does it work any better in 9.04?

---

### Post by CraigBray on 2009-03-29
I wish i could say, i haven't had time to get 9.04 installed, but i would imagine that OSS4 should work. I have read it works in Intrepid too.

---

### Post by atarifreak on 2009-04-06
i tried 9.04 since alpha 2 but sound doesnt work out of box.
not jet tried any alsaupdate nor oss

---

### Post by wicky_ts on 2009-04-09
is things work better with 9.04 than the 8.04.

---

### Post by Changturkey on 2009-04-10
Gonna try Kubuntu 9.04. If things don't work out, I am gonna try Mandriva.

---

### Post by MichaelRX8 on 2009-04-17
I just did Clay's script in Jaunty and now have 100% sound for the first time! Thanks Clay554!

---

### Post by CJay554 on 2009-04-26
In ubuntu 9.04 its a simple as just running this in your terminal:
```
sudo echo "options snd-hda-intel model=auto" >> /etc/modprobe.d/alsa-base
```

then just do a restart and tada =]

this code is part of the install script i made, tho its the only thing you need to get sound working, just tells the bios configuration to automatically search for the sound device rather than specifying a model

---

### Post by omegavirus on 2009-04-26
Hi, I have the aspire 6920, working fine thanks to you all! But what about the infrared remote receiver? I have not manage it to work whit a gateway remote control.

I have used the bluetooth whit my cellphone (sony ericsson) and manage to use it as a control remote.

I'm using the infrared remote control program and mythbuntu.

Thanks in advance... 

[HBR]("http://elgranpez-hbr.blogspot.com/")

PD: does any one has try to install OpemFoam 1.5 under ubuntu 8.10? I cant make it work...

---

### Post by applefreakpeeps on 2009-05-07
Anyone got the internal mic working??

---

### Post by khurtsiya on 2009-05-16
Installed Ubuntu 9.04. No sound =(

---

### Post by alpho2k on 2009-05-16
> **CJay554 said:**
> In ubuntu 9.04 its a simple as just running this in your terminal:
```
sudo echo "options snd-hda-intel model=auto" >> /etc/modprobe.d/alsa-base
```

then just do a restart and tada =]


Just do this :)

---

### Post by khurtsiya on 2009-05-16
Something wrong with this

> khurtsiya@khurtsiya-laptop:~$ sudo echo "options snd-hda-intel model=auto" >> /etc/modprobe.d/alsa-base
bash: /etc/modprobe.d/alsa-base: Permission denied


---

### Post by alpho2k on 2009-05-16
Ok, do it like that :

sudo gedit /etc/modprobe.d/alsa-base

The file should open in a new windows. Write the lines "options snd-hda-intel model=auto" without the quotes at the end of the file and restart your computer.

Also, I described this method on my blog : [http://monespaceperso.org/blog-en/2009/04/29/acer-aspire-6920-no-sound-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/04/29/acer-aspire-6920-no-sound-on-ubuntu-jaunty-904/)

---

### Post by khurtsiya on 2009-05-17
I already have 2 such lines there =) May be they appeared because I used manual from first post.

I have sound now, but it to quiet.

In 8.04 it was quiet until some updates - then it was good and loud.

Now again.

How can I increase volume?

---

### Post by alpho2k on 2009-05-18
For me, with Ubuntu 9.04, the sound is a lot better since I upgraded Alsa to 1.0.20.

---

### Post by khurtsiya on 2009-05-18
How did you do that?

> khurtsiya@khurtsiya-laptop:~$ sudo apt-get upgrade alsa
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


---

### Post by alpho2k on 2009-05-18
It's like the script of CJay : [http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/)

---

### Post by ffffrank on 2009-05-18
Yes, I also upgraded to Alsa to 1.0.20 and the sound was much better.

---

### Post by khurtsiya on 2009-05-18
Same here. 

Thanks!

---

### Post by zenmester on 2009-05-24
thaks for your tread 

Does anybody else have no sound after upgrading to 9.04
I've lost sound. and Nvidia drivers 
and nothing I've tried works

can anyone point me in the right direction

---

### Post by mc6415 on 2009-05-27
Just a quick question to see if anyone here can help me out, does anyone here know how to get sound working on one of these in Mandriva 2009?

---

### Post by autooffspring007 on 2009-05-31
If anybody is having problems with cinepad or function keys "not responding" , you can use [FONT="Courier New"]xmodmap -pke[/FONT], [FONT="Courier New"]setkeycodes[/FONT], and [FONT="Courier New"]dmesg[/FONT] to tell the keys what to do. 

for example, i have set the cinepad key that looks like an arrow looping back around to be eject.  This key did not do anything by default.  Push the key, then go to terminal and do [FONT="Courier New"]dmesg[/FONT].  It will give you something like the following

[FONT="Courier New"]delta kernel: [ 1512.573661] atkbd.c: Unknown key released (translated set 2, code 0x83 on isa0060/serio0).
delta kernel: [ 1512.573667] atkbd.c: Use 'setkeycodes e003 <keycode>' to make it known.[/FONT]

As this says you will use [FONT="Courier New"]setkeycodes e003 <keycode>[/FONT], where e003 is the code returned by dmesg (use the code that is returned to you) and <keycode> is the keycode for the function that you want the key to do.  To find the keycode you want to map, enter [FONT="Courier New"]xmodmap -pke[/FONT] into terminal.  Read through the list until you find the keycode you need, in this case the keycode for eject is 170.  Note that you will have to subtract 8 from the keycode in order for it to map properly (because the codes 0 to 7 are not in the [FONT="Courier New"]xmodmap -pke[/FONT] list.  So the command will be

[FONT="Courier New"]sudo setkeycodes e003 162[/FONT]

Finally, open system -> preferences -> keyboard shortcuts and make sure that the "Eject" is set to XF86Eject (or whatever function you are trying to set)

---

### Post by autooffspring007 on 2009-05-31
Forgot to mention,  for those of you using compiz there is a better way to turn it on.  Most people add [FONT="Courier New"]compiz --replace[/FONT] or [FONT="Courier New"]fusion-icon[/FONT] to System->Preferences->Startup Applications (or session depending on what version you are using, I am on 9.04).  When you login this way, metacity begins, and is replaced by compiz as your session loads, causing panels and wallpapers to be drawn twice, giving your screen a flickering effect.  To correct this, you have to set compiz to be the default window manager so that it begins at startup.  

The proper way to load compiz is to create or edit the text-file ~/.gnomerc so it says "export WINDOW_MANAGER=/usr/bin/compiz".  Restart X.

If this doesn't work (it didn't for me), there is an alternative.  

     [I]Edit the file /usr/share/gnome/wm-properties/compiz.desktop
     and add the following keys:

     Type=Application
     X-GNOME-Autostart-Phase=WindowManager
     X-GNOME-Provides=windowmanager

     Change the Exec key to
     Exec=gnome-wm

     Then change "metacity" to "compiz" in the following gconf keys:
     /desktop/gnome/session/default-session
     /desktop/gnome/session/required-components/windowmanager [/I]
[URL="http://www.nabble.com/-Cooker--Gnome-2.23-and-compiz-fusion-td18330823.html"]
[COLOR="Blue"]http://www.nabble.com/-Cooker--Gnome-2.23-and-compiz-fusion-td18330823.html[/COLOR][/URL]

Now you must remove any compiz startup you have created for your session, or it will load twice anyways.  If you use fusion-icon, switching to metacity may cause a crash (you can still use it for everything else however) so you will need to do two things:

1:  Add [FONT="Courier New"]fusion-icon -n[/FONT] to your startup (this will load fusion-icon without replacing the window manager)
2:  Open Compiz settings manager, enable crash handler plugin, and in this plugins options add [FONT="Courier New"]metacity --replace[/FONT] underneath "Start other window manager"

---

### Post by CJay554 on 2009-10-01
Sorry i havent been on lately guys been a bit preoccupied.

Anyway, if you've upgraded to 9.04 getting sound is as simple as running this command:

```

sudo echo "options snd-hda-intel model=auto" >> /etc/modprobe.d/alsa-base

```

And after you enter it just restart your computer

I already stated this 2 pages back, so please make sure you read the whole thread before you ask any questions.

---

### Post by hijibijbij on 2009-10-26
This post saved my life in more than one way! Just want other readers to note that running the alsa 1.0.18a setup solved my problems with Intel HDA 8280I (ICH9) sound with a Dell Inspiron 1440.

---

### Post by JBAlaska on 2009-11-01
Update to this great thread for the Acer 6920. I installed Karmic and EVERYTHING but the fingerprint reader works outta the box. I installed cheese from synaptic and my camera works perfect, sound and mic works just fine as well, wireless working better that Vista.

Karmic 9.10 is a GREAT release for the superb Acer 6920!

---

### Post by aralbald on 2009-11-02
Yeah, everything is working nicely. The only thing that bugs me is the nvidia/compiz issues, like some buttons not working in flash, java crashes, tearing in compiz animations and etc.

Someone experiencing the same issues?

---

### Post by JBAlaska on 2009-11-02
Not a bit, What Nvidia driver are you using?

---

### Post by aralbald on 2009-11-02
Hmm, that is strange. I'm using the default one - 185.18.36, will try 190.xx later.

Have you changed any settings in the nvidia control panel or the compiz one?

---

### Post by aralbald on 2009-11-02
Ok, so the flash/click issue is all over launchpad, e.g [https://bugs.launchpad.net/compiz/+bug/410407](https://bugs.launchpad.net/compiz/+bug/410407) (there is a temporally fix at comment #143)

For the compiz tearing (actually it is not 'that' bad, it's more like - 'the animations are sometimes slow and jerky') i use the ugly fix for powemizer, forcing it in high performance mode. That way everything is smoooth ;)

Haven't tried 190.xx though.

---

### Post by Shinger on 2009-11-05
Ive just installed 9.10 on the Acer Aspire 6920G. 

WORKS OUT OF THE BOX:

- Graphics
- Sound + internal Mic (you have to set it on mic 2 not 1 to get it to work)
- Wlan + LAN
- Bluetooth Sending - Receiving didnt but i think it was the phones fault.
- 2 other buttons between bluetooth and wlan only one works because the second tries to open emailclient but dont have any emailclients on it.
- cinedash
- USB
- Internal webcam

DID NOT WORK:

- SDCard Reader
- FingerPrint Reader

DID NOT TEST:

- Infra Remote Control
- Express Card
- DVB (although hardware drivers for proprietary drivers did gave me a driver to install)

I dont know if somebody managed to get to last 5 things to work if so could you please reply about how you managed to get it to work.

---

### Post by CJay554 on 2010-01-02
The SD card works if you boot up with a SD card inserted, i assume this is a driver that is loaded when it detects the hardware (when the sd card is inserted)  

fingerprint reader: not sure what is up with this, there really are no programs in the ubuntu software repository to use this device, though some do exist, anyone set this up?

By default infra remote should be supported with new Koala release.
Express card has always worked
DVB should be functional out of the box (not as good as windows but close)

---

### Post by CJay554 on 2010-01-31
Notice: 
When playing around with another distro, Sabayan, i noticed that the graphics card worked ALOT nicer! including games such as nexus and open arena, it worked very well whilst in ubuntu the graphics did not even load correctly (ie, floors and walls, characters didnt render well or render at all) im taken to believe ubuntu isn't using the best driver suitable for our graphics cards!

i found this:

[http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html)

though im not quite sure where to start...

[EDIT] Turns out Ubuntu has the same drivers, its just that you have to configure game settings to get good quality gameplay, its nothing to do with the drivers. You have to go into the game of your choice and go into video and tinker with the settings until you have it good.

---

### Post by Bakon Jarser on 2010-02-25
> **aralbald said:**
> Ok, so the flash/click issue is all over launchpad, e.g [https://bugs.launchpad.net/compiz/+bug/410407](https://bugs.launchpad.net/compiz/+bug/410407) (there is a temporally fix at comment #143)

For the compiz tearing (actually it is not 'that' bad, it's more like - 'the animations are sometimes slow and jerky') i use the ugly fix for powemizer, forcing it in high performance mode. That way everything is smoooth ;)

Haven't tried 190.xx though.

For video tearing:  [http://ubuntuforums.org/showthread.php?t=1390284&highlight=nvidia+tearing](http://ubuntuforums.org/showthread.php?t=1390284&highlight=nvidia+tearing)

except in the third step change nvidia-settings --load-config-only to

nvidia-settings -l

I can still notice tearing just a little bit once in a while but it's a huge improvement.

---

### Post by RussianNeuroMancer on 2010-04-16
In Ubuntu 10.04 ALL CineDash buttons work out of the box?
Porblem not detecting CineDash hardware if controlls on HOLD is still here?

---

### Post by Shinger on 2010-06-09
For the people who installed Ubuntu 10.04 on this laptop. Could you post what hardware works and what not...

---

