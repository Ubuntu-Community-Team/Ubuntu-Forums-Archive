---
title: "ALSA1.5 Intel HD Audio no sound Gutsy Lenovo Y410"
date: 2007-11-12
forum: Hardware &amp; Laptops
---

### Post by sarath_it on 2007-11-12
I bought a new Lenovo 3000 Y410 from officedepot. I have been using Dell Inspiron 6000 and ubuntu from Drapper.

Buing this new laptop has dissappointed me about ubuntu. The laptop cannot do sound in Ubuntu. can in windows. I have always boasted to my friends about ubuntu.. and all of a sudden i find myself sneered at.

I am neither a noob nor a very techy guy. But here is what happened.

When i first installed, I got the volume control in the notification area with two devices, realtek HD and ACL262 (not exactly from my best memory). However, I never got sound from my speakers/headphones.

so ii decided, I will get help from 
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) (using alsa1.15)

few a times, i had problems compiling. finally i installed all dependencies ncurses etc, i got it to make install.

wat happens? I lost the whole sound card info.i get a volume control icon with an X and double clicking it gives a message (see attachment)

amixer gives this.
```
sarath@sarath-lenovo:~$ amixer
amixer: Mixer attach default error: No such device

```

lspci gives 
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
08:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
08:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

```

dmesg gave some errors about version number (see attachment)
like
```
[ 5176.452000] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[ 5176.452000] snd_hda_intel: Unknown symbol snd_ctl_add

```

If there is any angel who can help me, i will appreciate the help. Even if you give other options i could try i will.

Thanks,
Sarath.

---

### Post by sarath_it on 2007-11-13
no one is having issues with hda-intel? or no one is buying new laptops?

my friend got a new hp laptop too his comes with hda-intel. his system cannot do sound either (in live cd, i am not installing ubuntu in another system until this gets resolved.)

---

### Post by catastrophix on 2007-11-15
Also having the same troubles with my Y410...seemingly no clear solution as yet.

---

### Post by dberg on 2007-11-21
I've been thinking about buying this laptop but have been reading about everyone's issues with the sound not working. Has anyone been able to find a solution to this yet?

I've seen a howto that sound promising, anybody tried it and did it work?

[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/]("http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/")


Thanks

---

### Post by tlivingd on 2007-11-24
Just picked up this laptop,  however I do sound as a hobby for community theater and looking to take the plunge into a linux distro.  Hoping someone will find an answer.

-nate

---

### Post by jcsteele on 2007-11-24
[http://ww2.coastal.edu/jcsteele/gutsy-S4134.html](http://ww2.coastal.edu/jcsteele/gutsy-S4134.html) has my simple solution for fixing Intel HDA sound on my toshiba notebook...also can check at [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

//jcs

---

### Post by fung on 2007-11-25
> **jcsteele said:**
> [http://ww2.coastal.edu/jcsteele/gutsy-S4134.html](http://ww2.coastal.edu/jcsteele/gutsy-S4134.html) has my simple solution for fixing Intel HDA sound on my toshiba notebook...also can check at [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

//jcs

Just tried that but unfortunately doesn't work :mad: superior integrated graphics but poor sound support :( what a 

EDIT:
I did a quick google search and came up with this:

[http://www.linuxquestions.org/questions/linux-laptop-and-handheld-25/sound-card-problem-in-y410-wid-fc-7-598412/](http://www.linuxquestions.org/questions/linux-laptop-and-handheld-25/sound-card-problem-in-y410-wid-fc-7-598412/)

seems promising, I'll go through it and post the results

---

### Post by jcsteele on 2007-11-25
Try looking at [http://ubuntuforums.org/showpost.php?p=3768914&postcount=60](http://ubuntuforums.org/showpost.php?p=3768914&postcount=60) which may or may not help you...I can not verify much about OSSv4 as I do not use it, however it might be the key to your problem (until the alsa problems are figured out eventually)

//jcs

---

### Post by fung on 2007-11-25
I came across this article [http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/) seems to address this EXACT problem.. too bad I can't get it to work. Anyone else have any lluck?

EDIT
lol just ran across this [http://ubuntuforums.org/showthread.php?t=530374](http://ubuntuforums.org/showthread.php?t=530374) basically the mother-of-all-threads regarding the issue with Intel HD Audio not working :(

Ok I have spent 12 hours today trying to fix this problem but I'm too frustrated to continue (not to mention I have plenty of homework due tomorrow too). If someone does figure it out, please report your results, thanks.

---

### Post by fung on 2007-11-26
At the risk of sounding immature.. LOL WTF MY LAPTOP HAS SOUND! I haven't really done anything since my last edited post right above this one other than leaving the laptop on for 6 hours while i slept, then putting my laptop to sleep when I woke up at 5am, working on some homework on the laptop at around 9am, then putting it to sleep again at 2pm when I went to class. when I tried to wake it up, the keyboard didn't function so ctrl+alt+backspaced to reboot x and lo and behold, IT WORKS. so, it IS possible. if anyone wants me to post up settings and configs I'd be welcome to. good luck

EDIT guess what? it broke again. Then I changed one thing from /etc/modprobe.d/alsa-base . the last line should read something alone the lines of:
 options snd-hda-intel index=0 model=xxxxxxx where xxxxxx says something. replace it with fujitsu 
[http://ubuntuforums.org/showthread.php?p=3796486#post3796486](http://ubuntuforums.org/showthread.php?p=3796486#post3796486)
got the idea from that link. odd ain't it?

EDIT2
both fujitsu and benq work.. the catch is-no headphone support. kinda annoying but at least now I can watch movies with (typical laptop) sound.

---

### Post by tlivingd on 2007-11-28
> **fung said:**
> At the risk of sounding immature.. LOL WTF MY LAPTOP HAS SOUND! I haven't really done anything since my last edited post right above this one other than leaving the laptop on for 6 hours while i slept, then putting my laptop to sleep when I woke up at 5am, working on some homework on the laptop at around 9am, then putting it to sleep again at 2pm when I went to class. when I tried to wake it up, the keyboard didn't function so ctrl+alt+backspaced to reboot x and lo and behold, IT WORKS. so, it IS possible. if anyone wants me to post up settings and configs I'd be welcome to. good luck

EDIT guess what? it broke again. Then I changed one thing from /etc/modprobe.d/alsa-base . the last line should read something alone the lines of:
 options snd-hda-intel index=0 model=xxxxxxx where xxxxxx says something. replace it with fujitsu 
[http://ubuntuforums.org/showthread.php?p=3796486#post3796486](http://ubuntuforums.org/showthread.php?p=3796486#post3796486)
got the idea from that link. odd ain't it?

EDIT2
both fujitsu and benq work.. the catch is-no headphone support. kinda annoying but at least now I can watch movies with (typical laptop) sound.

Fung, other than adding that one line above.  What else did you do to the system?  
BTW i'm a newbie to the whole linux/ubuntu. so please take it easy on me,  I don't mind getting windows stuff to work although picking this up quicly today,  figured out how to edit a system file ugg.  it's a bit backwards,  added an icon for the gksudo nautilus command to allow admin access to file search so sys files arn't read only.  got the touch pad to correctly speed up and the sliders work now in the mouse settings,  got the wireless to connect after finding out that WEP dosen't work with this network card but WPA does!  and I think i got the proper codecs installed to play an mp3 file, but with no sound can't tell.  So things arn't going to bad for about 6 hrs of playing with it. 

Thanks!  oh and someone is reading your posts.
-nate

---

### Post by fung on 2007-11-28
I think the only things that mattered were upgrading alsa to 1.0.15 and then adding in that line. although I did screw around with tons of other stuff... try adding in the line and upgrading alsa first. if that doesn't work we can backtrack from there. Try following these instructions to install alsa. [http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel) I have a genetics exam in less than an hour so I'll be back later

---

### Post by tlivingd on 2007-11-28
uggg.... i get some goofy errors trying to follow the directions at the alsa project.  
i figured out how to browse to my own dir where i saved the driver file.  however I think i'm missing a few fundimental commands to do this correctly.  First it seems or was having trouble making files in other folders as I don't have the rights to do.  (tried sudo and may have allowed me to do it)   

was then getting another error about 

configure:2471: error: C compiler cannot create executables
See `config.log' for more details.

does this sound right,  I could wait till they update Synaptic but i'd like to get this working sooner and learn how to get it working.

thanks,
-nate

---

### Post by fung on 2007-11-28
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) there are some instructions here you can try.

---

### Post by tlivingd on 2007-11-29
woohoo!!! another lenovo y410 with functioning sound!!!!   basicly all it is is to load the .15 drivers,  and add that line mentioned above.  unfortunately i lost my volume control on the top of the keyboard (orange buttons)  the onscreen worked before  oh  also the sound is abnormally tinny sounding, however i think the lenovo has a digitally controlled "subwoofer" with a crossover to the main speakers. 

ok got it to stay on upon boot.  and it now allows all the volume controls to work  WOOT!

-nate

---

### Post by kitejumping on 2007-12-01
I have this same problem, Y410 laptop from office depot, (black friday) but with kubuntu... I installed the alsa driver and libs version .15rc3 and utils .15rc1, with no make or configure problems.

I tried the fujitsu and benq options with no luck... any ideas?

---

### Post by tlivingd on 2007-12-01
I too got the black friday y410 from office depot.  the store had 2,  one went in the orginal box out the door 1st thing in the morning and this one was the display model (just put out) but came with all it's packaging.  

Give the final release of 15 a try.  it looks like there are quite a few revisions to the HDA-intel driver looking at it's version numbers.  compared to rc3  I'm sorry I can't help a whole lot as i'm pretty new to this linux thing and think I got lucky getting it to work.  
but we'll see what we can do.
-nate

---

### Post by kitejumping on 2007-12-01
Where can I download the final release, and do I have to do anything special to uninstall the old one?

---

### Post by tlivingd on 2007-12-01
i followed the instructions above
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
there.  (also posted above.)  i followed it to about step 4. then followed the instructions of the link below.

but then i redid it like this  that has the link to the most recent alsa driver.
[http://ubuntuforums.org/showthread.php?p=3475485](http://ubuntuforums.org/showthread.php?p=3475485)

but where it says to add
options snd-hda-intel model=hp
change the HP to Fujitsu as mentioned by Fung above these are a couple of extra lines that i'm not sure are needed, but mine works.

and download final release 
[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

just came out on oct 16

---

### Post by kitejumping on 2007-12-02
I got it to work :) :) :) 
The problem was in the default /etc/modprobe.d/alsa-base config

find the line 
options snd-hda-intel model=3stack-dig

and comment it out so its
#options snd-hda-intel model=3stack-dig

then add this to the bottom
options snd-hda-intel index=0 model=fujitsu

Thanks for the help... :guitar:

---

### Post by hellmet on 2007-12-05
Ok.. so now the headphones work too?
I got sound to work, but headphones don't .. Ubuntu doesn't even sense a jack being plugged in. Any help on this?

---

### Post by harsha10 on 2007-12-06
Hi...
information abt...my alsa etc/modprobe.d/alsa-base....
```

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388


```
I am having problems with sound..in my laptop...and i tries what the member have done here...but i didnt get how to modify my alsa-base...can u please help mee...:confused:

---

### Post by tlivingd on 2007-12-18
For the lenovo y410,  what we've hashed here has be republished here in an easy to read instructional format.
[http://linuxondesktop.blogspot.com/2007/12/getting-sound-to-work-on-your-ubuntu.html](http://linuxondesktop.blogspot.com/2007/12/getting-sound-to-work-on-your-ubuntu.html)

after doing some more reading.  I wish i was more comfortable with Ubuntu, Because 
this Ubuntu Wiki has some soundcard things to say about the 3000 and I'm thinking may work on the y410  [https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100_0768](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100_0768)


I'm wondering if the 3000 has the optical-out thru the headphone jack like the y410.  I've never seen that before until this laptop.

---

### Post by wrishibothra on 2007-12-25
Hi ... I got the speaker output working using the new alsa drivers. My internal mic does not seem to work yet ... I used the gui based alsa mixer and unmuted all controls post which i used sound recorder to test the mike using all available options. However none worked.

Any clues ...

---

### Post by prsamy on 2007-12-31
I too have a Lenovo Y410 and the sound is "deafening" silence. Have tried everything I found on the internet re this and so far not a squeak in ubuntu from my laptop. Well, I will go back to windows again until somebody discovers a foolproof solution.

prs

What crap! Lo and behold right after I posted the above and rebooting my sound starts to work. What I did was to update alsa to 1.5 somthing and for alc262 used benq as compatible model.

prs

---

### Post by DJAltair on 2008-06-06
Has anyone managed to get the headphone jack working properly on their Y410?

---

### Post by jalanbuntu on 2008-07-01
I still can't make the jack output to work :( Does anyone can?

---

### Post by fung on 2008-07-24
For anyone still interested in the Y410 and its jack problem, I stumbled upon this thread:

[http://ubuntuforums.org/showthread.php?t=820959&highlight=y410](http://ubuntuforums.org/showthread.php?t=820959&highlight=y410)

Basically there's another version to try out, so I did. I noticed that there seems to be a new codec just for the Y410: model=lenovo-3000

I tried it, unfortunately no sound came out neither through the laptop speakers nor the headphones. However, I noticed the little red light that shines out of the headphones plug shined when it normally didn't! (I use model=fujitsu). Any ideas?

edit: After looking at the alsa website and seeing they already released 1.0.17, rc3 would be older than that right? or no? what's the command to check the version of alsa installed?

edit edit

EXTRA EXTRA Y410 IS NOW SUPPORTED! (hopefully headphones too)
======================
    - hda-codec - model for alc262 to support Lenovo 3000 
    This model is to support the Lenovo 3000 y410. 

Directly from the changelog at 

[http://www.alsa-project.org/main/index.php/Changes_v1.0.16_v1.0.17](http://www.alsa-project.org/main/index.php/Changes_v1.0.16_v1.0.17)

---

### Post by taylorg273 on 2008-07-24
I successfully upgraded to Alsa 1.0.17 thanks to that thread. I used the scripts from post #1 and the configuration instructions in post #19. I now have all of the audio hardware working except for the internal mic (external mic jack is OK). The headphone jack works and even cuts off the speakers when the headphone plug is inserted.

The scripts will download and install everything needed from Alsa. There is one missing step in the instructions in post #19. The 'alsa-driver' directory needs to be created in your *home* directory for the remainder of the steps to work. This new driver has a model option for 'lenovo-3000' which is what I am now using in my /etc/modprobe.d/alsa-base.

Also just got the webcam working in Skype - too bad I don't have the mic to go with it.

---

