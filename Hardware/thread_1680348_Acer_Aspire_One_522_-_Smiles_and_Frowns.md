---
title: "Acer Aspire One 522 - Smiles and Frowns"
date: 2011-02-02
forum: Hardware
---

### Post by Rowan_ on 2011-02-02
[ Update - May 7, 2012:  12.04 LTS is working very well after a few days of install.  I did not install the proprietary graphics drivers and Unity works with only a slight delay. I also noticed when viewing video the screen dims slightly after about 20 seconds.  
There is no issue with wireless connections.
Battery reporting seems slightly inaccurate, but I haven't changed the power settings as of yet.  Perhaps im mistaken.]




Seeing as the Acer Aspire One 522 is quite new to the marketplace I thought I'd note my experiences with it. 

Ubuntu's Netbook interface,Unity, does not work.

Ubuntu Desktop, and Unity-2D do work; but not flawlessly.

I have noted the netbook's incompatibilities at [http://art.ubuntuforums.org/showthread.php?t=1543009&page=12]("http://art.ubuntuforums.org/showthread.php?t=1543009&page=12")  posts #118 & 119.

If anyone has any suggestions for the lack of wireless capability then I would deeply appreciate it.  Having a netbook is pointless without wireless online connectivity.
The interesting part is that I must use Fn + F3 at startup otherwise i experience random freeze/crashes.  If i plug in an Ethernet connection no crash occurs regardless of manually cycling off the wireless.

Other than the permanent watermark from the ATI Catalyst drivers and the wireless issues, the OS works marvelously quick and problem free. *[Edit:  Not so marvelous; random freezing/crashes became constant freezing] *
I found it usefull to install the recently available Unity 2D.  After initial boot - and then reboot - it works quite well, and looks nice.

However, no wireless means back to MS Windows for me.... sigh.

---

### Post by jerrylamos on 2011-02-02
Acer Aspire one D255E running Unity 3D on Natty Narwhal O.K., as functional as an Alpha 1 usually is.

I tried Ubuntu 10.10 netbook but didn't see the point, since regular Ubuntu 10.10 and Ubuntu 11.04 Natty working fine.

Now Natty 11.04 is in Alpha and not stable i.e. may crash however it does function on my D255E as good as or better than any of my test pc's.

Jerry

---

### Post by Rowan_ on 2011-02-02
Okay, well thanks for the reply.  However; it doesn't seem relevant.  Your acer is a different model with a different CPU and GPU.
The 522 has an AMD C-50 ‘Ontario’ APU, which is a 1GHz dual core processor and Radeon HD 6250 chip GPU.
As you see this differs greatly from your intel setup.

Thanks for help though.  If you have any insight into the wireless issue that would be great.

---

### Post by srstrt on 2011-02-03
Hey there, 

I'm having the same problem... The driver is there but when I try to activate it the activation process crashes... would love to have an answer...

Peace.

---

### Post by andrewthong on 2011-02-06
Try installing the latest Catalyst manually- no watermark there.

I had wifi working properly initially, but it didn't show up on 3rd-4th reinstall for some reason- had to go back to Windows to get it enabled again.

This is for Desktop 10.10

---

### Post by x86Daddy on 2011-02-07
What's everyone's successful method of booting Ubuntu on the 522?  

I've built thumbdrive installers with the recommended Pendrivelinux creator and UNetbootin, and I've tried 10.10 and an 11.04 nightly, with no luck.  I get a frozen mouse cursor on the Ubuntu load graphic at best, or it just freezes at the Syslinux loading line immediately, depending on which USB imager I used.

---

### Post by Rowan_ on 2011-02-08
> **x86Daddy said:**
> What's everyone's successful method of booting Ubuntu on the 522?  

I've built thumbdrive installers with the recommended Pendrivelinux creator and UNetbootin, and I've tried 10.10 and an 11.04 nightly, with no luck.  I get a frozen mouse cursor on the Ubuntu load graphic at best, or it just freezes at the Syslinux loading line immediately, depending on which USB imager I used.

Try booting with the livecd (usb) and use disk manager to Format the partitions.  For some reason ubuntu looks for a previous install and then f@(k$ up and freezes.  In particular i found that the swap partition is what was causing the problem.  
Worked for me several times with different computers.
Good luck.

---

### Post by Rowan_ on 2011-02-08
There is a freezing issue that really makes Ubuntu useless on the 522.  It seems to be related to the wireless trying to connect.  I'm back on windows.... blah.
Please provide feedback if anyone has a successful install with wireless working. 
Cheers!

---

### Post by dsummy on 2011-02-09
Hey, i just purchased an acer ao522 also and am having the same issue with the watermark. I installed windows 7 x64 for the time being and have been searching for a fix to the ubuntu driver issue. It seems amd has not yet released drivers to support the 6250 on linux yet. but i did find these drivers..don't know how to install them though :(
[http://www.phoronix.com/scan.php?pag...item&px=OTA3Nw](http://www.phoronix.com/scan.php?pag...item&px=OTA3Nw)

I also seem to be having an over heating issue..today while on the train I had the netbook in my bag, not turned off, just sleeping and when I woke it up and closed some applications and went to turn on a movie..it got EXTREMELY hot in the bottom left corner of the screen and under the power button, Also, in the middle of the screen right by the letter 'a' in acer there a little circle the size of a screw that looks to have melted the plastic of the screen :( going to talk to acer tomorrow.

---

### Post by Rowan_ on 2011-02-09
> **dsummy said:**
> Hey, i just purchased an acer ao522 also and am having the same issue with the watermark. I installed windows 7 x64 for the time being and have been searching for a fix to the ubuntu driver issue. It seems amd has not yet released drivers to support the 6250 on linux yet. but i did find these drivers..don't know how to install them though :(
[http://www.phoronix.com/scan.php?pag...item&px=OTA3Nw](http://www.phoronix.com/scan.php?pag...item&px=OTA3Nw)

I also seem to be having an over heating issue..today while on the train I had the netbook in my bag, not turned off, just sleeping and when I woke it up and closed some applications and went to turn on a movie..it got EXTREMELY hot in the bottom left corner of the screen and under the power button, Also, in the middle of the screen right by the letter 'a' in acer there a little circle the size of a screw that looks to have melted the plastic of the screen :( going to talk to acer tomorrow.

Yikes.

---

### Post by emerth on 2011-02-10
> **Rowan_ said:**
> Seeing as the Acer Aspire One 522 is quite new to the marketplace I thought I'd note my experiences with it. 

Ubuntu's Netbook interface,Unity, does not work.

Ubuntu Desktop, and Unity-2D do work; but not flawlessly.

I have noted the netbook's incompatibilities at [http://art.ubuntuforums.org/showthread.php?t=1543009&page=12](http://art.ubuntuforums.org/showthread.php?t=1543009&page=12)  posts #118 & 119.

If anyone has any suggestions for the lack of wireless capability then I would deeply appreciate it.  Having a netbook is pointless without wireless online connectivity.

...



Edit: it seems some 522's ship with Atheros wireless and some ship with Broadcom wireless. Below notes are for Broadcom!

This was on OpenSuSE 11.3. It should work on Ubuntu... mod the location of the wpa_supplicant conf file. You'll need GCC and kernel development debs installed.

Driver is at [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

~> make
~> make install
~> modprobe lib80211
~> modprobe wl
~> wpa_supplicant -B -Dwext -ieth1 -c /etc/wpa_supplicant/wpa_supplicant.conf
~> wpa_gui

Then scanned for APs to find my AP.

I put the modprobes and wpa_supplicant invocation in /etc/init.d/boot.local so that part is done at boot. I run wpa_gui manually.

Wifi infrastructure on Linux is not my strong suit... normally Gnome/KDE/XFCE would have wifi control panel installed: OpenSuSE did not install any of that for me I guess because it did not find a wifi card. So the wpa_gui method I am using is a bit manual, I have to run it from LXDE Start|Run - I do not have a nice system tray applet to control the 522 wireless thus am using wpa_gui SUID as a work around.

---

### Post by emerth on 2011-02-10
Other comments.

I've had two lock ups. Do not know why.

I installed AMD Catalyst 11.1 and AMD Stream SDK, built the examples. I have not run all the examples, only about half of them, but the ones I ran all worked.

On boot, watching the console, a large number of undefined symbol sort of errrors coming from the Catalyst code are printed but the machine works, OpenGL works, CAL & OpenCL Stream example programs work.

The OpenCL examples run several times faster on GPU than on CPU. 

Video playback using xine is very good, no tearing. 

Sound works, but not how I would like. I only have a master volume control, and!!! when I plug headphones in the PC speakers keep working, they are not muted.  This is really irritating. This evening maybe I will be investigating whether I have the correct sound driver, if there is a better driver.

There is a 522 thread at phoronix: [http://phoronix.com/forums/showthread.php?31961-Notes-on-Acer-Aspire-One-522](http://phoronix.com/forums/showthread.php?31961-Notes-on-Acer-Aspire-One-522)

Does anyone have advice on building a 2.6.38 rc4 kernel for this machine? I've given it a try but I keep getting massive screen corruption and incomplete boot.

OT, but running Win7/64, I installed Left 4 Dead, set video to 1280x720 (native resolution) and turned eye candy to minumum and sound to low quality. The game ran at between 6 and 30 FPS depending on how many monsters were on screen, and whether flames were being displayed. Which was kind of cool, I'm an L4D junkie. Funny thing I learned is that L4D is just as much fun at 6 FPS as at 70+++ that my dual 4890 gaming box manages, lol.

---

### Post by GenBattle on 2011-03-14
I've also just bought a new Acer Aspire One 522.

They only just hit New Zealand in the last few days, and we seem to have a slightly different hardware configuration to some of the posts by US/UK user's i've seen around so far. Mainly this is because our ethernet chip is an Atheros chip, and wlan is a Broadcom chip (as opposed to a Atheros chip in some other models).

My main sticking point has been a mix of wlan drivers and graphics drivers. I tried Ubuntu 10.10 and 11.04 Alpha 3, but there are various issues with both at the moment. 10.10 lacks graphics driver support and wlan/ethernet support. 11.04 may possibly support ethernet, but gdm and unity won't seem to start underr the xfree86 open radeon driver included with 11.04, and installing the AMD CCC 11.2 drivers causes the whole OS to become unbootable.

I actually had a fair bit of success with OpenSuse 11.4 (KDE, haven't tried gnome yet), which supported wlan, ethernet and graphics (to a certain degree). However it was impossible to get the AMD driver to install properly, and it just ended up corrupting the installation.

---

### Post by GenBattle on 2011-03-14
Just tested OpenSuse 11.4 GNOME with no issues.

I won't double-post what i've already said;

[http://ubuntuforums.org/showpost.php?p=10560508&postcount=12](http://ubuntuforums.org/showpost.php?p=10560508&postcount=12)

EDIT:
Not completely true, i'm now getting freezes after startup. This seems to have started when i set up a default wireless network to connect to on startup.

---

### Post by GenBattle on 2011-03-15
Posting this from my Aspire One 522 running Linux Mint 10. Both Linux Mint 10 and Ubuntu 10.10 do seem to work fine with the Atheros/Broadcom version of this netbook.

Start with a standard install, reboot (it will be running at 800x600). Then just install both the ATI and Broadcom restricted drivers from the restricted driver manager, restart. Install the latest AMD graphics driver (11.2).

It seems half the problem is because of a mix of the new kernel and the non-binary drivers for network cards and video cards.

---

### Post by jason.s on 2011-03-17
I am having the same issues.  I was able to get the video driver installed so it ran at the right resolution.  I ordered RAM which I heard would fix the hibernate problems.  But, I still had issues with the sound coming from the speakers when headphones were in, and, more importantly, it started freezing constantly.  

Has anybody fixed the freezing issues or does anybody know of any linux distros that work on the Acer Aspire One 522?

---

### Post by GenBattle on 2011-03-19
> **jason.s said:**
> I am having the same issues.  I was able to get the video driver installed so it ran at the right resolution.  I ordered RAM which I heard would fix the hibernate problems.  But, I still had issues with the sound coming from the speakers when headphones were in, and, more importantly, it started freezing constantly.  

Has anybody fixed the freezing issues or does anybody know of any linux distros that work on the Acer Aspire One 522?
OpenSuse 11.4 seems to have very few issues, and as i've said, i'm using Linux Mint 10.10 with few or no issues. It seems to also partly depend which network hardware you have as to how successful you are with compatibility.

---

### Post by jason.s on 2011-03-19
> **GenBattle said:**
> i'm using Linux Mint 10.10 with few or no issues.

I installed Mint 10.10 as you recommended.  It started out in 800x700, so I downloaded and installed the 11.2 catalyst driver to take advantage of the full resolution.

Then, to test everything out, I unplugged the cord to make it go onto battery.  Within a couple seconds, it froze.  This is the same thing I've been seeing on ubuntu.... are you seeing this?  If not, what did you do to get it to work at its full resolution? Did you use the same driver that I am (the one from [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)?]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx%29?")

The freezing has always seemed random to me, but it always seems to be connected to me being on battery.

Edit: Another 2 freezes since I posted this maybe 20 minutes ago.  One right after reboot.  So, I'm seeing the exact issues I saw on Ubuntu 10.10 when using Mint 10.10.

The only thing I have changed from the default install is running the catalyst driver install ([http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)).  that's the only way I know to get it to work at its real resolution, but I must be doing something fundamentally wrong. I'm a linux noob.

Update: The freezing has happened on power too, so it's not battery-only as I thought.

---

### Post by Onitake on 2011-03-25
Hi guys. I managed to get the headphone output working by manually installing ALSA 1.0.24 using the script from [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577) and then adding model=ideapad to snd-hda-intel module options. Well, in fact I modified alsa-driver so it would use model=ideapad for the Aspire One 522. Didn't try with module option yet, but it should have the same effect. Would be nice if someone could confirm that this works too.

Unfortunately, this hack totally disables the internal speaker. So only partial success so far...
*Edit:* After a reboot, switching between internal speaker and headphone output works just fine. No idea what was wrong before.

Bug report on the ALSA tracker: [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=5324](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=5324)

As for the freezes... I managed to avoid them if I turned off either network device. WiFi works ok if I unload atl1c, whereas Ethernet works if I switch off WLAN with Fn-F3. But I've had instances where Ethernet would stop receiving data - only a reboot or switching over to WiFi got me networked again.

---

### Post by DarkTide on 2011-03-26
I have the same problem :-s plz help me

Thanks:popcorn:

---

### Post by Onitake on 2011-03-26
> **DarkTide said:**
> I have the same problem :-s plz help me

Do you mean the sound or the freeze problem?
The freeze problem hasn't been fully solved, if my workaround doesn't help, you'll have to wait.

As for audio, you can try the following:

1. Open Terminal and enter:
```
gksudo gedit /etc/modprobe.d/options.conf
```
2. Insert this:
```
options snd-hda-intel model=ideapad
```
3. Save
4. Plug your headphones or speakers in
5. Reboot

With this procedure, the driver should detect during bootup that something is connected to the headphone jack and switch the output. Jack sensing doesn't seem to work, so the output state will stick until the next boot.

I have tested only with ALSA 1.0.24, but the relevant code is already contained in ALSA 1.0.23, so it should theoretically work too.

---

### Post by cubeist on 2011-04-01
My experiences:
First, this is an amazing little netbook.  The fusion platform (with upgraded ram) is a real work horse and I am very impressed.  This runs like a low-end laptop, not a netbook. 720p video is seamless with both open source and restricted ati, and cpu keeps up with all normal tasks.

[COLOR="Red"]Update:[/COLOR] HD video is laggy. GPU acceleration xvba is not available yet for this chip so cpu is doing 90% of the work, and cpu gets very hot. Using latest VLC with GPU acceleration checked (in the prefs) and the ati catalyst driver is your best bet at this point. I'm currently trying to install mplayer-vaapi and will post back with results.
I installed XBMC from svn and despite taking four hours to compile it works fantastically. I now have a mobile htpc.

I'm using Natty Narwhal 11.04 beta. It installed aok and is a wonderful OS.

--I've updated the BIOS twice, latest is 1.07--
What works:
Nearly everything
CPU: Yes (fan runs a lot, machine is always warm, but rarely hot)
Graphics: Yes (both opensource and ati catalyst)
touchpad: yes (vertical scroll on right enabled by default"
ethernet: yes (no system freezes using 2.6.38 and atl1c)
wifi: yes (restricted broadcom driver works but seems to cause freezes, haven't troubleshooted, but works for others)
suspend: yes with opensource graphics, no with catalyst
webcam: yes
function keys: most
hdmi out: yes!
audio through hdmi: YES! (install pulse audio volume control)
audio: speaker works, but headphone does not (tried onitake's solution, but nothing. conexant 5084 chip is not in alsa spec, but 5085 is, YMMV)
card reader: cards are detected, but they crash when trying to mount
Battery life: my battery doesn't charge to capacity, it might need cycling, but estimate about 5 hours. ([COLOR="red"]update:[/COLOR] I've cycled the battery and now get 4-7 hours depending on tasks).
screen: works but is too bright IMO. Turning brightness down doesn't help. It needs a way to turn the backlight down, which is way too strong, although some people may think this is a feature.  Also I have backlight bleed on the top edge. Cheap.

If I forgot anything, please ask.

---

### Post by tactus on 2011-04-02
That's good news cubeist, please keep us posted if you find way to deal with wifi, headphone jack or battery issues. Sounds to me these are the most prominent issues at the moment for casual usage.

I expect my 522 to arrive next week hopefully, Aptosid (Debian unstable) or Ubuntu 11.04 looks to be the most interesting Linux candidates for me as Linux kernel 2.6.38 seem to be the way to go for this netbook. :)

---

### Post by Onitake on 2011-04-02
Thank you cubeist!

The atl1c problems are driving me mad, good to hear they're fixed in 2.6.38. I'll wait for the final 11.04 before updating. About WLAN, I've got one of the Atheros models, hopefully newer ath9k versions fix the constant crashes I have. For some reason, they only happen when running on battery. On mains power, no issues at all. My suspicion is a power management issue in the driver and/or hardware.

As for sound: Raymond on the ALSA bug tracker suggested contacting the developer mailing list, as we might have a deeper issue here. I do hope it can be solved. Unless someone wants to jump ahead, I'll do that once 11.04 is out.

---

### Post by tactus on 2011-04-06
My Acer Aspire One 522 arrived two days ago. I couldn't get Ubuntu 11.04 alternate to boot from my USB stick, with Aptosid the screen got garbaged during booting up (even when booting to console). Fedora live cd was flaky. I had some success with Crunchbanglinux.

In the end I went with a vanilla / bare Debian, upgraded it to unstable and that is what I am running now. I also have the Atheros wireless and it works fine when it is used alone. The freezing stopped when I commented out ethernet in /etc/network/interfaces (I don't use networkmanager yet, just wpa_supplicant). Xorg runs with radeon driver (have not tested propriatary fglrx in Debian unstable) and I think the opensource driver have come a long way since last time I tested an ATI card. Sound does not work, but I have some volume controlls in alsamixer.

I think this machine is very close being ready for running Linux full time, I mainly just miss the sound to work. Hopefully when newer versions of Alsa gets added to unstable I will have sound with a simple apt-get dist-upgrade. :)

**Update:** Sound card is working, it's just confused with hdmi sound output or something. To get it working, correct sound card needs to be selected in asound.conf or .asoundrc.

```
$ cat /etc/asound.conf 
# Selects default card.
# How to find card:
# cat /proc/asound/cards
# See also http://alsa.opensrc.org/FAQ026

pcm.!default {
    type hw
    card SB
}
ctl.!default {
    type hw           
    card SB
}

```

The speaker (!) is not muted if jackplug is inserted, sound will play from both speaker and head phones. :P

---

### Post by letmeknow on 2011-05-02
The freezing issue comes for WiFi:

You can either boot Win7 before and do a reboot to Linux or do following:

add in /etc/modprobe.d/blacklist.conf this line

blacklist atl1c

and do in terminal:

sudo update-initramfs -u

---

Regarding Sound: Does someone gets Micro working (for skype?)

And the jack sensing? That's what I am struggling with...

---

### Post by md80hb-iuh on 2011-05-06
Since my last post I've installed Ubuntu 11. ATI catalyst does not work any more and I have poor video playback (regression)

I still have random freeze but this is only when I'm not plugged on A/C  power. If I go on battery it will freeze within the two minutes of use.  Passed 2 minutes  it will continue working regardless of wifi settings  (on or off). Checked and rechecked all the power management with no  luck.

On battery it will not freeze if I'm wired ethernet.

Still problems with audio jack, mic and card reader.

I have several environment installed on it (Ubuntu, Kbuntu, Netbook  remix) and they all behave the same way. Yes all updates have been run.

---

### Post by tactus on 2011-05-07
About jack sensing, you need to define correct model for Alsa. There might be variations in what chip are used but "options snd-hda-intel model=dell-vostro" worked for me. See:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) for details in Ubuntu.

Alsa 1.0.23 or 1.0.24 doesn't matter I believe, I have Alsa 1.0.23 and jack sensing works after defining model. (I don't have Ubuntu at the moment thought.)

Blacklisting atl1c worked for me as well, no stability issues but no Ethernet unless I load driver manually (when Ethernet cable is attached).

**Update: **It should be "options snd-hda-intel model=,dell-vostro", notice the comma. More details in [this bug rapport]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/775788").

---

### Post by pharnet on 2011-05-07
Hello,

I have a Canadian Aspire One 522 BZ499, AR8152 eth0/BCM4313 eth1, Updated BIOS 1.07, Ubuntu 11.04, open source ati driver (afraid to try fglrx if suspend not OK). I have upgraded it to 2GB.

Linux 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

Only weirdness I have noticed so far is that when I resume from suspend Unity Launcher stops auto hiding and system indicators seem to stop updating. They respond to clicks on them but no updating. Sound indicator looks like it is muted but it is not. Network indicator empty piece of pie but it is still connected. It is back to normal after the next reboot until suspend again.

Card reader seems to be working for me.
No joy with headphone jack.

Is it better to use the open source video driver or fglrx?

---

### Post by letmeknow on 2011-05-10
A bit OT I need your help.

I was updating my Acer 522 with 2Gb of RAM. Everything works fine so far. Than I thought it is a good idea to make a memtest - as you never now. So I downloaded memtest86+, which is one of the best RAM Test programms ([http://www.memtest.org/#downiso](http://www.memtest.org/#downiso)).
I was surprised to see, that all 3 RAMS I have (the original 1GB and the 2 2GB) show exactly the same 6 errors at exactly the same location. So from my point of view this can't be connected with wrong RAM but with either problems of Hardware (Motherboard, Processor) or some software issue (BIOS, memtest itself). That's way I would ask you to repeat this test, to find out whether just my hardware is defect or this is probably no problem but some issue for all Acer 522 as (speculation) some addresses are remapped in BIOS...
Although memtest can spend a lot of time for a complete test, this messages come quit fast after start, so you have to spend just 1 minute or 2.
Please let me know about you results.

Another mystery: With the Ubuntu included memtest (4.10) I don't get an error. But with the 4.10 version downloaded from the link above I get errors at one of the addresses.

Regards

---

### Post by ubuntumatic on 2011-06-22
Hi everyone,

Just wanted to share my experiences with this laptop.

First: I've managed to get the internal microphone to work by applying the solution in this thread: 
[http://ubuntuforums.org/showthread.php?p=10906814#post10906814](http://ubuntuforums.org/showthread.php?p=10906814#post10906814)

As for having proper stereo sound with the audio out jack / headphones, this configuration works for me: 

options snd-hda-intel model=laptop,dell-vostro position_fix=0,1

Still no luck for having mixed left+right audio channel through the internal mono speaker. 
Has anyone managed to get that working?

Other than that, I still have inconsistent results with suspend: the first time I use it, it works fine. But at times it closes the applications I am using, and other times it hangs. This is using the open source video driver. Any help with that would be helpful

---

### Post by Zaphrous on 2011-07-13
I got this new netbook, upgraded the ram to 4gigs, and since it was $210  i don't really want to upgrade windows for $80 just to get access to  the artificially restricted RAM from windows 7 starter. Not to mention  no disk to clean install without bloatware. Since i use a lot of open source software it made sense to try out linux, and ubuntu seemed like a good place to start. 

Things were running well before i upgraded the ram, so i though the ram was the problem - memtest shows no errors, and the system seems to freeze only when i try to configure network settings, or connect to wireless. So I appear to be currently getting the wireless freeze. There also appears to be a solution.

"
add in /etc/modprobe.d/blacklist.conf this line

blacklist atl1c

and do in terminal:

sudo update-initramfs -u
"
However i do not have write permissions and i cant get it to work either in terminal or by navigating to the file and opening it (it is read only). Nor can i log in as 'Root'. As a windows user i am not familiar with Linux commands. 
I presume there is some way to run the text editor as Root, some way to give myself write permission on the file from my user created during install, or some terminal shell command i can use to get root access to change the text file.

TLDR : How can i (a linux newb) modify a text file that requires root permissions?

Edit : wasn't using gksudo with gedit
gksudo gedit /etc/modprobe.d/blacklist.conf 
allowed me to edit it


Edit2: gotta write those down. could prove useful. And the machine seems to be back to working now. So there is peace in the universe once more.
Sorry, just realized this was wrong thread. It had relevant info though. I'm on 11.04 not netbook remix. Seemed to have same problem and solution though.

---

### Post by Dr-Zeuss on 2011-07-19
On a 522 with 1GB I can report Ubuntu 11.04 64bit will crawl and eventually freeze (fresh install all updates), go the 32bit option until you drop 2GB or 4GB into it.
11.04 has almost all bugs mentioned here (except jack detection) fixed as of this date.


 - Side note:
I got some crumbs under the keys, popped out two arrows keys (bottom right corner) to clean.

Now for the life of me i cant 'pop' them back in.
(cant find guide for key replacement on 522)
Anyone got experience getting a key back onto the keyboard?

---

### Post by Dr-Zeuss on 2011-08-12
....&#8593; anyone?

---

### Post by casainho on 2011-10-03
Can 522 and 722 users please share on Ubuntu wiki: [https://help.ubuntu.com/community/AspireOne522](https://help.ubuntu.com/community/AspireOne522)

I found already a few hacks and documented them there:

* Touchpad vertical and horizontal scroll
* GPU dynamic
* Undervoltage
* Fan control (almost there, I hope)

We need help for finding EC register to turn off/auto the fan!! Please help if you can!

[https://help.ubuntu.com/community/AspireOne522](https://help.ubuntu.com/community/AspireOne522)

---

### Post by arkeo on 2011-10-04
Just wanted to share my experiences with a brand-new 522 (aesthetically beautiful, and for just €240!). But...

I seem to be one of those few having problems booting and installing various distros.

Immediately after I unpacked it I installed Natty 64 (my AO522's the 2/320GB version), and let the installer wipe the Linpus installation and encrypt everything (after all, being so small, it seemed a safe precaution).

Everything went well for about two days (updates installed, other software I needed, the Catalyst drivers), then after a boot/reboot or wake-up (can't recall exactly which) something went terribly wrong and try as I might I always got:

1-triple drum roll but no login screen, trackpad and keyboard frozen

OR

2-login window, again with trackpad and keyboard frozen

After hours of trial and error, I managed to get from GRUB the recovery for the previous kernel, and even then it only worked if I told him to drop me to the root console. Then more miserable hours trying to figure out how to recover one single 15KB file from the encrypted partition I was working on (only user can do that), mount a USB stick (root needed here) and copy it there.
Sounds simple, it's been Hell for me... Well, at last I recovered the damn file and decided to re-install Natty. I'm in freezing hell ever since (meaning every installer at some point freezes).

I tried every major distro, current or in beta, via flash and USB CDROM. Either the installer fails (Debian stable and testing freeze trying to format the drive), or if trying a Live distro I never even get to the login screen (Ubuntu 04/10 sticks to the purple screen, Xubuntu to the black dog, Fedora looks about to load GNOME Shell, but I get stuck to a frozen waiting pointer).

I put a temporary Win7 on it and it installed ok (via flash stick), I updated the BIOS (just in case) and now I'm running a low level scan of the HD via Ultimate Boot CD after the quick scan revealed no errors.

I'm at a complete loss... :confused:

I'll try the UBCD Ram test next, but after that I don't know on which sharp corner bang my forehead (VERY apt expression)... ](*,)

Any help would be greatly appreciated...

---

### Post by casainho on 2011-10-05
> **arkeo said:**
> Just wanted to share my experiences with a brand-new 522 (aesthetically beautiful, and for just €240!). But...

I seem to be one of those few having problems booting and installing various distros.

Immediately after I unpacked it I installed Natty 64 (my AO522's the 2/320GB version), and let the installer wipe the Linpus installation and encrypt everything (after all, being so small, it seemed a safe precaution).

Everything went well for about two days (updates installed, other software I needed, the Catalyst drivers), then after a boot/reboot or wake-up (can't recall exactly which) something went terribly wrong and try as I might I always got:

1-triple drum roll but no login screen, trackpad and keyboard frozen

OR

2-login window, again with trackpad and keyboard frozen

After hours of trial and error, I managed to get from GRUB the recovery for the previous kernel, and even then it only worked if I told him to drop me to the root console. Then more miserable hours trying to figure out how to recover one single 15KB file from the encrypted partition I was working on (only user can do that), mount a USB stick (root needed here) and copy it there.
Sounds simple, it's been Hell for me... Well, at last I recovered the damn file and decided to re-install Natty. I'm in freezing hell ever since (meaning every installer at some point freezes).

I tried every major distro, current or in beta, via flash and USB CDROM. Either the installer fails (Debian stable and testing freeze trying to format the drive), or if trying a Live distro I never even get to the login screen (Ubuntu 04/10 sticks to the purple screen, Xubuntu to the black dog, Fedora looks about to load GNOME Shell, but I get stuck to a frozen waiting pointer).

I put a temporary Win7 on it and it installed ok (via flash stick), I updated the BIOS (just in case) and now I'm running a low level scan of the HD via Ultimate Boot CD after the quick scan revealed no errors.

I'm at a complete loss... :confused:

I'll try the UBCD Ram test next, but after that I don't know on which sharp corner bang my forehead (VERY apt expression)... ](*,)

Any help would be greatly appreciated...

Isn't that the hang due to Ethernet board? where you should enable on BIOS boot from Ethernet to avoid that problem of hanging?

---

### Post by arkeo on 2011-10-05
> **casainho said:**
> Isn't that the hang due to Ethernet board? where you should enable on BIOS boot from Ethernet to avoid that problem of hanging?

Why should I?

Enable Network Boot to boot actually from a USB-based device?

I'm completely in the dark about this... It's enabled per se, but it's lower on my bootchain than USB Flash or USB CD.

---

### Post by arkeo on 2011-10-05
> **casainho said:**
> Isn't that the hang due to Ethernet board? where you should enable on BIOS boot from Ethernet to avoid that problem of hanging?
Done.
 It skips Ethernet (check cable!) and then keeps on going down the boot sequence as defined in BIOS.

---

### Post by arkeo on 2011-10-05
> **arkeo said:**
> Done.
 It skips Ethernet (check cable!) and then keeps on going down the boot sequence as defined in BIOS.
Done, and I mean I'm done.

(tried some more Debian voodoo, managed to get a horrible stable and then go to testing, and now all I got is garbled pixels)

I'll wait until 11.10 final, then I'll see. For now, it's a bloody 250-quid brick.

Disgusting. Either this or the Windows tax??? I'm angry, very VERY angry. So much for Ontario, so much for a real nice netbook, so much for a great bargain finally MS-free...

---

### Post by casainho on 2011-10-05
There are a lot of users of AO522 and 722 using Ubuntu!! There is no reason for it not working for you!

When I got that hangs at login I searched on google and everyone mention this problem and solutions. I did enable Ethernet boot as first option on BIOS but my Ubuntu 11.04 boots from the HDD.

And please share your solutions here: [https://help.ubuntu.com/community/AspireOne522](https://help.ubuntu.com/community/AspireOne522)

---

### Post by arkeo on 2011-10-05
Pardon me, but I can search Google as well.

"There is no reason for it not working for you!" I busted my a$$ trying to make it work.

The page you linked to doesn't really seem to apply, does it?

Start from here:
I CAN'T BOOT.

Then you can see that (issues referred to on the linked page):
*Touchpad: IRRELEVANT, I can never get to use it.

*GPU Dynamic: it at least presumes an environment in which I can issue the suggested command.

*Undervoltage: I'd LOVE to have my 522 quieter and cooler, BUT, quoting "first download Undervoltage": see above, I CAN'T BOOT

*Embedded Controller: "You can read all register values by doing: sudo ./acer_ec.pl regs " I wish to God I could get a *user* console and then sudo from it

*Fan control: kinda like seems to fall in the same categories as mentioned before

Different production lines? Different components?
I'm all open to hear it, with comparisons between models if possible.

Otherwise I can't see a reason why my angry rant (admittedly) should be dismissed like this (after all I tried to offer all the info). I searched for all kinds of solutions or explanations, I used 4 different flash drives from 3 different manufacturers, and then I tried the only USB-DVD I have, with multiple ISOs burned to multiple physical CDs.

Please don't tell me I just didn't search for it on Google.

As far as I can see there are other people besides me with very similar boot/freeze issues. The page you linked to was one of the first hits, but in my (our?) case, it really doesn't address the point at all.

---

### Post by casainho on 2011-10-05
You wrote:

"Everything went well for about two days (updates installed, other software I needed, the Catalyst drivers), then after a boot/reboot or wake-up (can't recall exactly which) something went terribly wrong and try as I might I always got:

1-triple drum roll but no login screen, trackpad and keyboard frozen

OR

2-login window, again with trackpad and keyboard frozen"

I got situation 2 and the solution were to enable boot Ethernet on BIOS.

If your AO522 simply does boot from any media, maybe is broken.

---

### Post by arkeo on 2011-10-05
Please, can you explain to me why? Why Ethernet boot should in some way allow the regular boot from HDD?? And BTW, booting from Ethernet IS enabled, wherever I put it on the boot list, nothing changes... Something's not quite right here... :confused:

---

### Post by arkeo on 2011-10-05
> If your AO522 simply does boot from any media, maybe is broken.

Can you elaborate on this?

---

### Post by casainho on 2011-10-05
> **arkeo said:**
> Please, can you explain to me why? Why Ethernet boot should in some way allow the regular boot from HDD?? And BTW, booting from Ethernet IS enabled, wherever I put it on the boot list, nothing changes... Something's not quite right here... :confused:

I read on foruns that the hang at login is due to bad Ethernet controller initialization. Maybe there isn't working code on Ubuntu for it.
A way to avoid the hang is to enable Ethernet boot on BIOS since Ethernet controller will get correct initialized by BIOS on that way.

---

### Post by casainho on 2011-10-05
> **arkeo said:**
> Can you elaborate on this?

I mean that if your AO522 can't boot from HDD or USB flash drive, then may be broken and I should send it back to shop.

---

### Post by arkeo on 2011-10-06
> **casainho said:**
> I read on foruns that the hang at login is due to bad Ethernet controller initialization. Maybe there isn't working code on Ubuntu for it.
A way to avoid the hang is to enable Ethernet boot on BIOS since Ethernet controller will get correct initialized by BIOS on that way.

I'll be damned... Natty is installing right now...

I changed the boot order like this:

1-NetBoot
2-USB flash drive

Once installation is complete I'll simply put HDD as number 2, and see what happens...

=)

---

### Post by casainho on 2011-10-06
> **arkeo said:**
> I'll be damned... Natty is installing right now...

I changed the boot order like this:

1-NetBoot
2-USB flash drive

Once installation is complete I'll simply put HDD as number 2, and see what happens...

=)

Yes.

Please report later.

---

### Post by arkeo on 2011-10-06
> **casainho said:**
> Yes.

Please report later.

I will!

I'll also try to reproduce the bug (now I'm running software update, as last time when Ubuntu hanged was fully updated) by moving down NetBoot in the boot list leaving internal HDD as #1...

:guitar:

---

### Post by arkeo on 2011-10-06
Bug confirmed and reproducible:

**On the Acer Aspire One 522 NetBoot has to come first in the boot order as specified by the BIOS**, otherwise all kinds of crazy stuff starts to happen, frozen login screens mostly.

Otherwise everything seems to be alright, though the left speaker won't work (but this is known)... I'll check out the other issues mentioned on the linked AO522 page as well later.

---

### Post by casainho on 2011-10-06
> **arkeo said:**
> Bug confirmed and reproducible:

**On the Acer Aspire One 522 NetBoot has to come first in the boot order as specified by the BIOS**, otherwise all kinds of crazy stuff starts to happen, frozen login screens mostly.

Otherwise everything seems to be alright, though the left speaker won't work (but this is known)... I'll check out the other issues mentioned on the linked AO522 page as well later.

Good to know it worked for you ;-)

Right now, I verified that undervoltage get the AO522 about less 8ºC, which is a lot!!

Is your vertical and horizontal scroll on touchpad working?

---

### Post by arkeo on 2011-10-06
> **casainho said:**
> Good to know it worked for you ;-)

I have to admit that when I read your suggestions about the boot order I didn't believe for a minute it would work. I'm glad you proved me so resoundingly wrong! :-)

Right now I don't have time to check all the other things, but I assure you I will, either later in the day or the next couple of days...

Cheers!!

---

### Post by casainho on 2011-10-13
Yesterday I was able to flash the "hacked" BIOS file to unlock hidden BIOS menus -- I documented it on Ubuntu wiki:

[https://help.ubuntu.com/community/AspireOne522](https://help.ubuntu.com/community/AspireOne522)

---

### Post by ritalovely on 2011-10-16
Hi all, 
I've been experienceing a few issues with AO522 and I thought it would be nice to share them. 
I'm running a dual boot : W7 and Ubuntu (boot order: W7 last on the list)

Used to have the same problems as described by everyone regarding : 
audio jack : on Ubuntu 11.04, audio was working fine but when a jack was plugged, no sounds on the earphone and speakers would go go working / now working great with Ubuntu 11.10 : spearks working, jacks working - note : this is automatic configuration, I have done zero configuration on my own after upgrading from 11.04 to 11.10.
Mouse (touchpad): had issues on horizontal and vertical moves on 11.04 (horizontal never worked, vertical would work randomly); on 11.10, touchpad works flawlessly (again, no personnal configuration from me).
WIFI working properly, with automatic login on start up (used also to work on 11.04). 
Mike and camera not yet tested. 

Now, the only one thing (so far! still praying :)) not working properly is a start up when running on battery. Here is the thing:
When the energy cable is plugged: 
- freezing problems on Ubuntu login are random. I noticed something though, might be a coincidence, but well: startup on Ubuntu will only freeze when W7 has not finished on upgrading. Whenever all upgrades for W7 are done, login to Ubuntu work marvelously; but if not, I get blocked on the purple screen (ie. got to click on start my session; notice that I don't have a PSW, so don't know if the keyboard would be working or not; mouse works until I click start session but then everything freezes after that). Only thing to do then: power off with the button and boot on W7, wait for those updates to be finished. Rebooting after that on Ubuntu works  fine. But have to go through W7 or Ubuntu will keep on freezing on that point. 
When the energy cable is unplugged and battery (6-cell li-on) is 100% (say 99%, as W7 never tells me it is 100%):
- boots alright for W7.
- Never got it to boot on Ubuntu (either 11.04 or 11.10). I get to click on the start a session button and then nothing. Tried waiting 'till 10 min, but nothing (the light on HD gets turned off), mouse is freezed. Unlike other users, I have no message at all (ie. saw that some folks get connection messages problems). 
- The going first through W7 trick won't work. I positively have to plug the energy cable before I can boot on Ubuntu. Sometines I boot directly to Ubuntu, sometimes I have to do the W7 trick. 

Forgot to tell you that I'm using ZERO proprietary drivers. 
Also forgot to tell you that I'm a newbie to Ubuntu (1-year user :)) so if you need me to post anything, please describe what to do in the terminal. 

Voilà :) Thank you all in advance for any clue.

---

### Post by casainho on 2011-10-16
> **ritalovely said:**
> 
Mouse (touchpad): had issues on horizontal and vertical moves on 11.04 (horizontal never worked, vertical would work randomly); on 11.10, touchpad works flawlessly (again, no personnal configuration from me).


My touchpad is Alps brand and I got it working as I described here: [https://help.ubuntu.com/community/AspireOne522](https://help.ubuntu.com/community/AspireOne522)
Does it works for you or not?

You know that there are hardware differences over AO522...

About the updates of windows and not booting Ubuntu, I verified that there is something triggered on AO522 hardware when I hibernate on Ubuntu. If I hibernate, I can't access to BIOS or boot menu!!! I need to shutdown instead to access BIOS and boot menu.
Maybe windows updates are putting AO522 in a state that don't let Ubuntu boot.
I have no experience with Windows, since I only have Ubuntu (but Windows on virtual machine - virtualbox).

---

### Post by ritalovely on 2011-10-16
> **casainho said:**
> My touchpad is Alps brand and I got it working as I described here: [https://help.ubuntu.com/community/AspireOne522](https://help.ubuntu.com/community/AspireOne522)
Does it works for you or not?

It does work, without going through the procedure described. As I upgraded to 11.10, it just worked. The only thing not workin is the zooming with two fingers stuff. 
I will check the brand if you like. I have to boot on W7, dunno how to do it from Ubuntu ;)

> **casainho said:**
> You know that there are hardware differences over AO522...

I know and sorry I did not specify it since I assumed it was irrevelant since it is the same as yours (ie. [one of] your first post[s]). That's why I only specified the 6-cell battery since the problem I described might be connected - though instinticvely I dont think so. 

One question: was your system W7 free or did you have the loader before you installed Ubuntu? I'm asking coz I'm afraid that I couldn't boot safely with Ubuntu only. Can you boot on Ubuntu when running on batterty only?

---

### Post by arkeo on 2011-10-16
My touchpad scrolls vertically but not horizontally... How can I figure out which vendor is it from?

Regarding sound: only the left speaker works. And when I plug in earphones they work fine, but the speaker won't switch off.

(I'm hoping the next kernel release might fix these audio issues? :confused: )

Don't know about the microphone, but the camera seems to work ok.

I'm on Xubuntu 11.10 now.

Regarding video drivers: I have the proprietary drivers (Catalyst) installed from the release. In Additional Drivers now appears a newer ("post-release") driver, but it won't install--tried this on Ubuntu and Xubuntu, with the previous proprietary drivers installed and after a fresh install with no previous version installed. No luck so far...

It's a pity, because video performance (HD content) is *almost* there but not quite right (some skipping, some slow screen redraws)...I'd say 95%, so I was hoping this new driver would solve the remaining problems... :(

Only thing I haven't tried so far is to install the 11.9 drivers downloaded from AMD on a clean *buntu installation... But I'm not sure I want to try yet another install! :roll:

---

### Post by arkeo on 2011-10-16
> **ritalovely said:**
> One question: was your system W7 free or did you have the loader before you installed Ubuntu? I'm asking coz I'm afraid that I couldn't boot safely with Ubuntu only. Can you boot on Ubuntu when running on batterty only?

Mine was Windows-free; it came with Linpus, with not even a graphical environment installed or at least configured--"startx" wouldn't work! Wiped it out immediately... :mrgreen:

I can boot regularly either way, when the AO is connected or on battery... Have you tried the boot order change, with Netboot on top?

---

### Post by ritalovely on 2011-10-16
Arkeo, thank you for your message. 
Booting with Netbook on top did work :p (energy cable off, battery on 99% and starting up Ubuntu without going through W7). 
Is there a logical reason for that ? 

Regarding the sound now, I don't want to sound silly but, as for my AO522, I only have one speaker, located on the left... when I plug the jack it works perfectly (will have to try to listen to some mono recordings - Beatles fan - to see how it goes, but it does the stereo mix on his own since U11.10. 

Thank you again, but I'd still like to understand what is the logic in all that :D

---

### Post by arkeo on 2011-10-16
> **ritalovely said:**
> Is there a logical reason for that ?

There surely must be a logical reason, but it's well beyond my understanding! Why should a NetBoot attempt avoid a kernel freeze later, or in your case allow you to boot on battery, is beyond me...

Anyway, I'd hope that with the next *buntu 12.04 our problems should be solved (that would make it more than a year after the AO522's introduction!)... Acer's Linux support has declined steadily over the years, my last laptop and this netbook seem to be purposefully built with components that have little or no Linux support.

---

### Post by arkeo on 2011-10-16
> **arkeo said:**
> And when I plug in earphones they work fine, but the speaker won't switch off.

Correction: the speaker now goes mute when earphones are connected (on Xubuntu 11.10). Maybe the issue was present in 11.04 and is now fixed, or there are enough differences between Ubuntu and Xubuntu 11.10 that in the first distro it doesn't work properly, in the second it does...

---

### Post by casainho on 2011-10-16
> **arkeo said:**
> My touchpad scrolls vertically but not horizontally... How can I figure out which vendor is it from?

*sudo lsinput*

outputs this for me (relevant parts only):

[I]/dev/input/event7
   bustype : BUS_I8042
   vendor  : 0x2
   product : 0x8
   version : 0
   name    : "PS/2 Mouse"
   phys    : "isa0060/serio1/input1"
   bits ev : EV_SYN EV_KEY EV_REL

/dev/input/event8
   bustype : BUS_I8042
   vendor  : 0x2
   product : 0x8
   version : 29478
   name    : "AlpsPS/2 ALPS GlidePoint"
   phys    : "isa0060/serio1/input0"
   bits ev : EV_SYN EV_KEY EV_ABS
[/I]

About booting, I have none problems. Do you have latest BIOS version?

---

### Post by casainho on 2011-10-16
> **arkeo said:**
> My touchpad scrolls vertically but not horizontally... How can I figure out which vendor is it from?

I just documented the way to find, on wiki: [https://help.ubuntu.com/community/AspireOne522](https://help.ubuntu.com/community/AspireOne522)

There I also linked to pictures I took from my BIOS with unlocked menus :-)

---

### Post by arkeo on 2011-10-17
> **casainho said:**
> *sudo lsinput*

...

About booting, I have none problems. Do you have latest BIOS version?

Thanks...
Well, lsinput has this to say about my touchpad:

```

/dev/input/event8
   bustype : BUS_I8042
   vendor  : 0x2
   product : 0xe
   version : 0
   name    : "ETPS/2 Elantech Touchpad"
   phys    : "isa0060/serio1/input0"
   bits ev : EV_SYN EV_KEY EV_ABS

```

We have a new vendor! :D

About booting, yes I have version 1.12 installed. It's clear that there are many different versions of this little baby around. I guess that those who have a certain component (Ethernet controller?) by a specific manufacturer are having the "NetBoot-first or kernel panic" issue, others do not...

---

### Post by casainho on 2011-10-17
> **arkeo said:**
> Thanks...
Well, lsinput has this to say about my touchpad:

```

/dev/input/event8
   bustype : BUS_I8042
   vendor  : 0x2
   product : 0xe
   version : 0
   name    : "ETPS/2 Elantech Touchpad"
   phys    : "isa0060/serio1/input0"
   bits ev : EV_SYN EV_KEY EV_ABS

```

We have a new vendor! :D

So, if your touchpad scrolls vertically but not horizontally, maybe you could search for "ETPS/2 Elantech Touchpad" and see if there is better support for it on some other PC models.

Don't remember if you had windows, but if so, did horizontal scrolls worked?

If sure your touchpad should do horizontal scroll, you can fill an Ubuntu bug by running on terminal: ubuntu-bug

---

### Post by arkeo on 2011-10-17
> **casainho said:**
> So, if your touchpad scrolls vertically but not horizontally, maybe you could search for "ETPS/2 Elantech Touchpad" and see if there is better support for it on some other PC models.

Don't remember if you had windows, but if so, did horizontal scrolls worked?

If sure your touchpad should do horizontal scroll, you can fill an Ubuntu bug by running on terminal: ubuntu-bug

Well, no, I'm not sure... I just assumed it should since I see all of you talking about it! :D
Furthermore, I think this feature is strictly software--but I might be mistaken...

I only installed Windows briefly to update the BIOS, so I didn't install any drivers, and I don't know how the touchpad should work with it...

---

### Post by casainho on 2011-10-17
> **arkeo said:**
> I only installed Windows briefly to update the BIOS, so I didn't install any drivers, and I don't know how the touchpad should work with it...

Hmmm, I always used USB disk with FreeDOS for update BIOS. Using Unebootbin on Ubuntu we can created a bootable FreeDOS USB disk and put there the BIOS update files :-)

About your touchpad, search on google to discover more about it. I like a lot horizontal scroll... other Aspire One 110 I had also had horizontal scroll :-)

---

### Post by casainho on 2011-10-17
> **arkeo said:**
> 
I only installed Windows briefly to update the BIOS,

I just update wiki page with info on BIOS update using Linux and FreeDOS:

[https://help.ubuntu.com/community/AspireOne522](https://help.ubuntu.com/community/AspireOne522)

---

### Post by casainho on 2011-11-08
**One thing that still don't work for me and I would like to have it is the LCD backlight control** - right now I can use the FN + CTL left/right to control the backlight but it increases/decreases in double steps :-( -- but this happens only when using the Open Source video driver, which I need because I put the AO522 sleeping and hibernating every time. Backlight control works perfectly with AMD closed source video drivers but then ibernation and sleeping doesn't work.

Anyone have a solution?

[https://help.ubuntu.com/community/AspireOne522](https://help.ubuntu.com/community/AspireOne522)

---

### Post by arkeo on 2011-11-10
> **casainho said:**
> **One thing that still don't work for me and I would like to have it is the LCD backlight control** - right now I can use the FN + CTL left/right to control the backlight but it increases/decreases in double steps :-( -- but this happens only when using the Open Source video driver, which I need because I put the AO522 sleeping and hibernating every time. Backlight control works perfectly with AMD closed source video drivers but then ibernation and sleeping doesn't work.

Anyone have a solution?

[https://help.ubuntu.com/community/AspireOne522](https://help.ubuntu.com/community/AspireOne522)

Seems to be working fine for me, Fn+left/right...but right now I'm giving Fedora 16 a spin, so maybe it's a distro-related issue? I'm also using the open source radeon drivers, but since Catalyst 11.10 is out I'm planning to give it a try and see how it goes...

---

### Post by arkeo on 2011-11-10
> **arkeo said:**
> Seems to be working fine for me, Fn+left/right...but right now I'm giving Fedora 16 a spin, so maybe it's a distro-related issue? I'm also using the open source radeon drivers, but since Catalyst 11.10 is out I'm planning to give it a try and see how it goes...

This is just great...the installation went fine, then I tried to reboot. Wops! No reboot in Gnome-Shell! It forces you to log out instead, so invoking gdm again... But the newly installed Catalyst drivers didn't like this...so? System bricked!

Has anyone an idea on how to put Shutdown and Reboot back where they belong??? WHO THE FSCK IS DESIGNING THESE GUIs??? ](*,)

---

### Post by arkeo on 2011-11-10
Managed to uninstall the driver in recovery mode, rebooted, then tried to install it again from a root console (telinit 3), but I got the same results. And had to uninstall it again.

It would seem that the 11.10 ATI Catalyst drivers are 100% incompatible with F16.

Has anyone tried them on Ubuntu? If I have to install yet another distro just to see it not working I might actually go into a coma...

](*,)

**Does anyone at ATI test these things before releasing them?** :confused:

---

### Post by walterav on 2012-02-14
SD card reader:
Does anyone have success with the integrated SD card reader using SD-cards in the amd64 releases of 11.04/11.10/12.04?

I did have success with Sony memory sticks in the same reader but inserting SD-cards will just freeze the Harddisk led, and will not detect or sometimes detects a card but will not write it... The SD-card workes fine in a different machine.

---

### Post by arkeo on 2012-02-15
> **walterav said:**
> SD card reader:
Does anyone have success with the integrated SD card reader using SD-cards in the amd64 releases of 11.04/11.10/12.04?

I had no problem so far with that... :shock:

It would seem that there are many different machines out there, bearing the same name but built with VERY different components.

Which leads me to: a little off-topic, but HUGELY important in case you want to upgrade your RAM.

Despite what everything and everybody on the Net says, including the official Acer Tech Specs page, my 522 had a 1333 SO-DIMM, not a 1066 one. I blindly bought a 4GB @ 1066 and the system wouldn't even pass its own POST. ](*,)

**If you want to upgrade your RAM, check it physically yourself before buying it (and potentially wasting 20€ or so).**

12.04 looks promising, by the way. I just hope AMD will get its act together at some point and release a decent fglrx--I bought the 522 for the 720p display and I can't get fluid 720p video EVER? =D>

As time goes by I'm more and more tempted to shell out another 80€ or so and buy me a Win7 license and be done with it... :cry:

---

### Post by walterav on 2012-03-31
> **walterav said:**
> SD card reader:
... some SD-cards will just freeze the Harddisk led, and will not detect or sometimes detects a card but will not write it... The SD-card workes fine in a different machine.
Probably a problem related to the specific SD-card not the AAO522.

It has the same behavior under Windows 7 on the same system, also the same behavior on a similar AAO 522, both OS's. 

But external usb cardreaders are able to read/write the card succesfully. Maybe need to find some analyzing software for SD cards...

---

### Post by jaythecaesarean on 2012-05-19
i'm using acer 522 with Ubuntu 12.04
I can't enable nor disable the bluetooth's visibility. 
I need some help on this one. Thanks in advance.

---

### Post by bluedot34 on 2012-05-23
> **jaythecaesarean said:**
> i'm using acer 522 with Ubuntu 12.04
I can't enable nor disable the bluetooth's visibility. 
I need some help on this one. Thanks in advance.

First be sure that your unit has BT, as not all units are shipped with it. The box usually  contains a sticker with hardware specs. 

My unit lacks BT, yet IIRC the (unity) menubar showed a BT icon, with all options grayed out, quite similar to what you are experiencing.

---

### Post by c-m on 2012-07-03
I recently bought a AO522

I've installed the restricted ATI/AMD drivers but for some reason i'm still not getting hardware acceleration in flash (checked on youtube using video info), or when playing HD video in vlc.

Is HD hardware acceleration working for anyone else?

---

### Post by c-m on 2012-07-10
So how is everyone getting on?

I've installed the ATI propriety drivers and can watch HD720p video no problem, but resource monitor showing that CPU usage is at something stupid like 120-150%

The same video in windows uses about 60% cpu.

I played the video in XBMC in Linux, which is suppose to use hardware acceleration on ATI cards.

Any thoughts?

---

