---
title: "Acer Timeline 3810T"
date: 2009-05-20
forum: Hardware
---

### Post by tokyoahead on 2009-05-20
Hi guys, 

I just got my Acer 3810T and trying to install linux on it. I want to document here what I am doing to get it run and hope you will contribute your own experiences here to create a central resource.

The following things do not work out of the box (list to be extended)

1. SATA: the boot takes forever, with error messages. Actually it crashes without interaction. I have to press CTRL-ALT-F1 as soon as the ubuntu-screen with the progressbar pops up, and wait until the messages stop. then press enter, and I see {initramfs} Then I enter 'exit', which bring up the messages (see below) again but eventually it will show the login screen. submitted bug [https://bugs.launchpad.net/ubuntu/+bug/379831](https://bugs.launchpad.net/ubuntu/+bug/379831) 
Workarounds: 
- If you go into BIOS and switch the SATA mode to IDE (from AHCI), it will work, but this will disable any Vista that is installed.
- Further, you can workaround the issue by adding "libata.noacpi=1" to your kernel boot command line

2. The LAN Card
On this page here: [http://partner.atheros.com/Drivers.aspx]("http://partner.atheros.com/Drivers.aspx") you can find the AR813X-linux-v1.0.0.8.tar.gz driver. The README in the file pretty much explains the installation. The MAKE INSTALL failed for me on the installation of the man-file but that does not seem to have mattered. Now the card is deteced.

Here is a mode detailed description:
$ gunzip AR813X-linux-v1.0.0.8.tar.gz
$ tar xvf AR813X-linux-v1.0.0.8.tar.gz
$ cd src/
$ make
$ sudo make install
restart

3. Camera: works fine also after installing the proper driver:
- type in: sudo modprobe uvcvideo
- type in: sudo apt-get install cheese
- type in: cheese
- set the resolution in the preferences to 640x480 to get rid of the distortion
- done!

The following version DO work out of the box, as far as I could test it:
1. The graphics. They start up directly in the right resolution.
2. The SD-Card reader. Inserted cards are opened and read fine.
3. The Wireless network. The reception is strong and connections work good
4. The soundcard. Speakers work fine, even though the volume of the internal speakers is low (same as in Vista)
5. Bluetooth. I was able to discover and pair with my cellphone
6. The FN-linked button for sound, screen brightness, bluetooth off/on etc


**Attaching an external Screen**

I have a Samsung 970p here and wanted to attach it with a resolution of 1280x1024 and had some trouble doing it. So here is the solution in case you also have issues getting the proper resolution.

First, know the resolution and the frequency. 60Hz is working fine here.
You have to find out a modeline for the screen you are using. For this go into a shell and type:

```
# gtf 1280 1024 60.0
```
which gives you the modeline for 1280 x 1024 at 60Hz:
```
  # 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
  Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync1024 1025 1028 1060  -HSync +Vsync
```

Then you edit your /etc/X11/xorg.conf to look like this:
```

Section "Monitor"
        Identifier      "Acer Monitor"
EndSection

Section "Monitor"
        Identifier      "External Monitor"
        Modeline        "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
EndSection

Section "Screen"
        Identifier      "Internal Screen"
        Monitor         "Acer Monitor"
        Device          "Video Card (Primary)"
        SubSection "Display"
                Virtual         1900 1200
                Modes           "1900x1200" "1366x768" "1280x1024"
        EndSubSection
EndSection

Section "Device"
        Identifier      "Video Card (Primary)"
        Option          "Monitor-VGA" "External Monitor"
EndSection

```

Note where I inserted my modeline to make it work. If you then log out and log in again, the menu SYSTEM - PREFERENCES - DISPLAY should show the 1280x1024 resolution in the dropdown. This is the general direction. If this does NOT work for you for whatever reason, please take a look at this here: [http://wiki.ubuntu.com/X/Config/Resolution]("http://wiki.ubuntu.com/X/Config/Resolution")

---

### Post by djolk on 2009-05-21
I am considering, a lot, buying one of these laptops.  Once I can convince my fiancee to go 'halfies' with me.  I probably won't be installing ubuntu but I probably will be, if I need to, watching ubuntu threads for problems/help.

I'd be interested in hearing your opinion on the system in general and any other install issues.

Thanks

---

### Post by codedash on 2009-05-22
Any luck? All the above with jaunty install i guess?

---

### Post by tokyoahead on 2009-05-22
> **djolk said:**
> I am considering, a lot, buying one of these laptops.  Once I can convince my fiancee to go 'halfies' with me.  I probably won't be installing ubuntu but I probably will be, if I need to, watching ubuntu threads for problems/help.

I'd be interested in hearing your opinion on the system in general and any other install issues.

Thanks

its a nice system. I had a heavier Toshiba Portege M500 before. This sytem is much less hot, the resolution gives a lot more than the 1280, and the battery is actually 8 hours w/o problems. The keyboard is also good, but if you are used to a 12'' laptop it takes a bit getting used to the larger keyboard.

the built-in camer is super-clear, and the wlan reception is VERY strong.

---

### Post by tokyoahead on 2009-05-22
> **codedash said:**
> Any luck? All the above with jaunty install i guess?

Yeah its all 9.4

Did not have time to go further into it. will try this weekend egain. so far I do not even know what the actual problem is coming from.

---

### Post by danielviolin on 2009-05-24
After turning the hard disk mode in BIOS form AHCI to IDE, I can boot ubuntu without problems.

---

### Post by codedash on 2009-05-25
> **danielviolin said:**
> After turning the hard disk mode in BIOS form AHCI to IDE, I can boot ubuntu without problems.

Thanks a lot for the info. And recognizes everything? graphics, sound etc? Because i plan to buy the 4810T so if yours work with jaunty that one will also.

---

### Post by tokyoahead on 2009-05-25
> **codedash said:**
> And recognizes everything? graphics, sound etc?

I would not rely on this since there are different configurations for Graphics and maybe also for sound.

From my experience the intel graphics card is recognized w/o any problems with the right resolutions right away. I have not checked the sound yet.

---

### Post by codedash on 2009-05-25
Please give it a try some day. I plan buying it at the end of june so your review would be very helpfull. Thanks

---

### Post by tokyoahead on 2009-05-25
Ok I can confirm now that switching the SATA mode from AHCI to IDE enables 9.04 to be installed. However, a dualboot into a previously installed Vista will not work anymore.  I assume that reinstalling vista will be working if you re-install it after you switched to AHCI.

One more remark: I have read on some places that the support for AHCI is improved in the upcoming kernel. I tried to start 9.04 from a USB stick which gave the same problems as from the harddisk. However stating the pre-release of the latest fedora-version did not have this issue. I assume that the later kernels are more able to work with AHCI. 

Also, I tried out the SD-Card reader now which works fine. No time yet for other functionality.

---

### Post by luggio on 2009-05-25
i found a workaround for the ata error.
boot with "libata.noacpi=1" in the kernel line
it seems to be a bug in the acpi.

Unfortunately i have formatted all the drive losing the service partition.
I made a image but it's not booting. 
if any of you is able to access the pqservice partition please pm me

---

### Post by tokyoahead on 2009-05-25
ok guys check out the original article please. I have edited the text to update the latest findings:

- bluetooth works
- camera works
- AHCI/ACPI issues hav a workaround

---

### Post by federa on 2009-05-27
hi guys!!
i've got acer timeline 3810t too..it's cool!
everything work..almost everything: when i use suspend function after it the resume doesn't work: instead of resuming i've got power off...anyone got the same problem?

---

### Post by Rocks and Water on 2009-05-28
I'm curious, has anyone purchased the Timeline with a SSD? I've heard that it's available. Was installing Ubuntu any different? And did you get noticeably better battery life?

---

### Post by tokyoahead on 2009-05-28
> **federa said:**
> hi guys!!
when i use suspend function after it the resume doesn't work: instead of resuming i've got power off...anyone got the same problem?

if you had to switch off the ACPI to get it to boot I would assume thats normal... AFAIK the ACPI is controlling how the standby works.

UPDATE: Please note that, as reported in a post later someone correctly mentioned that A) you have to switch of AHCI in bios, not ACPI to make it work and AHCI has nothing to do with the powersaving and should not influence the standby mode.

---

### Post by Ususbuntung on 2009-06-05
Hi all,

I have this machine with me and I have installed Ubuntu 9.04 almost without any problem. I partitioned the harddisk into 2 ntfs partition for original Vista, and 5 ext3 (+swap) for Linux. This process of partitioning took looong, but luckily everything went smooth.

The problem came when I use compiz, while it works (I use avant windows manager) but display in any window, be it applications, dialogue or the related menu sometime disappears. I have to minimise and restore to get the display reappears. Using metacity there is no problem everything just works!

In short it is good laptop, the machine is comfortable to use.

---

### Post by Giovy on 2009-06-05
Hi all!
I bought this laptop two days ago (is fantastic!), installed Ubuntu 9.04 two hours ago (using the libata.noacpi workaround) but... I've no audio... :(
Somebody experienced the same problem?

Thanks!

---

### Post by miegiel on 2009-06-05
> **Giovy said:**
> ... I've no audio... :(

Check if all you volume levers are set to the max (btw they might be hidden).

If that's not it, search the forums there are loads of sound threads. If that doesn't help solving your problem, it will at least give you an idea of what kind of info people need to help you. ;)

---

### Post by Rocks and Water on 2009-06-05
> **tokyoahead said:**
> Hi guys, 
- If you go into BIOS and switch the SATA mode to IDE (from AHCI), it will work, but this will disable any Vista that is installed.
- Further, you can workaround the issue by adding "libata.noacpi=1" to your kernel boot command line
 off/on etc

Forgive me for my lack of knowledge on the subject, but what exactly is happening when you switch from AHCI to IDE? Is there any functionality that you're losing as a result?

---

### Post by Giovy on 2009-06-06
> **miegiel said:**
> Check if all you volume levers are set to the max (btw they might be hidden).

If that's not it, search the forums there are loads of sound threads. If that doesn't help solving your problem, it will at least give you an idea of what kind of info people need to help you. ;)

I checked all the volume levels, I've tried different audio source but still no audio.
In the first post of this thread I can read that the audio should work out of the box... :(

---

### Post by miegiel on 2009-06-06
> **Giovy said:**
> I checked all the volume levels, I've tried different audio source but still no audio.
In the first post of this thread I can read that the audio should work out of the box... :(

That's why I'm thinking it's not related to the 3810T but a general sound problem (and that you should look for help in a general sound thread). In any case, you need to figure out what the problem is. Here are 2 links to get you on your way.

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)

---

### Post by BooToo on 2009-06-08
Hi, 
Thanks a lot for documenting all the tricks to get Ubuntu installed on the Timeline.

I have placed my order today and cannot wait to install Kunbuntu on it.

I have 2 questions for the ones who already installed it:
- Is the 64bits distro ok as well? (especially for the Lan driver..)
- What about battery life? (I have read that the 8 hours were only possible due to some serious Acer optimization software installed in Windows and I will assume there isn't a Linux version yet ;-)

Personnaly, I only need around 6 hours with Wifi enabled but was wondering what you guys have experienced so far and if you have any tips...

Many thanks for this thread. ):P
BooToo

---

### Post by tokyoahead on 2009-06-08
> **Rocks and Water said:**
> Forgive me for my lack of knowledge on the subject, but what exactly is happening when you switch from AHCI to IDE? Is there any functionality that you're losing as a result?

I would assume that any powermanagement of the harddisk ist not working anymore. This might be the casue why it is currently not possible to resume from standby for at least some if not all users.

**UPDATE:** What I wrote here was wrong since I confused ACPI with AHCI. Read the next post from soleblaze for a clarification.

---

### Post by soleblaze on 2009-06-08
AHCI controls advanced SATA II features, such as native command queuing and hot swapping.  It has nothing to do with power management.  However, ACPI does.  

If you're turning off ACPI instead of AHCI then you will lose the ability to put your laptop to sleep/hibernate.  You should also lose the ability to do cpu scaling and some misc monitoring features.

Does the laptop work fine disabling AHCI or ACPI, or do you need to disable both?  Also how much battery life are y'all getting?  I'm thinking about getting one, but if I have to disable ACPI then I'll have to wait until that's fixed.  (AHCI isn't an issue for me, I use a SSD that doesn't support AHCI)

---

### Post by tokyoahead on 2009-06-08
> **soleblaze said:**
> 
Does the laptop work fine disabling AHCI or ACPI, or do you need to disable both?  

thanks for clearing up my confusion. the laptop works with disabling AHCI.

---

### Post by badte on 2009-06-10
hello everyone.

everything works fine except bluetooth. when i type "hcitool dev" i will get no devices.
what should i do, to get bluetooth to work?

---

### Post by Neo5588 on 2009-06-11
> **BooToo said:**
> Hi, 
Thanks a lot for documenting all the tricks to get Ubuntu installed on the Timeline.

I have placed my order today and cannot wait to install Kunbuntu on it.

I have 2 questions for the ones who already installed it:
- Is the 64bits distro ok as well? (especially for the Lan driver..)
- What about battery life? (I have read that the 8 hours were only possible due to some serious Acer optimization software installed in Windows and I will assume there isn't a Linux version yet ;-)

Personnaly, I only need around 6 hours with Wifi enabled but was wondering what you guys have experienced so far and if you have any tips...

Many thanks for this thread. ):P
BooToo

You are correct, the timer for the battery life never says more than 4 hours but I believe this to be a loose approximation because it also say that the battery life is unknown as well. I have not actually tried to run out the battery in Linux and time it. You might be able to change the brightness of the screen to save some more.

---

### Post by Neo5588 on 2009-06-11
I can't say this will work for everyone but it worked great for me. I have the 4801TZ version and what I did is I actually installed 8.04 first which loaded fine without the need to change any of the settings, be it that it didn't have many of the drivers. So I read this forum and thought why not give Jaunty a try and I reinstalled over the previous version I had first put on without formatting it and it worked perfectly without having any problems. I have re-installed Linux many times and noticed that many times it kept settings and other features after re-installing. I am not entirely sure how it worked but I am just happy it worked.

---

### Post by yuki86 on 2009-06-11
for those who struggle with lan like me: 
- get the driver  on this page here: [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx) you can find the AR813X-linux-v1.0.0.8.tar.gz drive 

$ gunzip tar.gz file
$ tar xvf tar.gz file
$ cd src/
$ make
$ sudo make install

restart - whoala lan is working

ps maybe you need linux-ports-source or linux-source-2.6.28 and than restart if not tell me..
dont forget to say thanks:)


anyone dont you know how to fix gma sync to vblank issue? In the motion its not worst. try to move with window have you desynchronization like me? 
[[IMG]http://img31.imageshack.us/img31/6264/snmekobrazovky.th.png[/IMG]](http://img31.imageshack.us/i/snmekobrazovky.png/)

---

### Post by PatrickVogeli on 2009-06-12
for the graphics, try this thread: [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

### Post by dhlacik on 2009-06-12
Hi guys,

I have acer timeline 5810T, 2 thinks are not working to me

-> changing brightness in gnome (can be workaround-ed by changing using xrandr to native mode)

It is even mentioned in logs :
un 12 20:58:14 david kernel: [   27.320635] acer-wmi: Acer Laptop ACPI-WMI Extras
Jun 12 20:58:14 david kernel: [   27.378719] acer-wmi: Brightness must be controlled by generic video driver
Jun 12 20:58:14 david kernel: [   27.378856] acer-wmi: software RFKILL enabled
It must be bug of gnome-power-settings


-> shut down / or reboot. I have AHCI enabled in bios
The strange is that I could not found something relevant in logs.
During restart / reboot it hangs on blicking pointer . When pressed ctrl+alt+del I will recieve an info about shuttind down all md0 raids or something related and it finally restarts.

---

### Post by yuki86 on 2009-06-13
hi just do this: it works and system is quick as usual

"Further, you can workaround the issue by adding "libata.noacpi=1" to your kernel boot command line"

---

### Post by realitygaps on 2009-06-14
Just got the 3810T, thanks for all the informative posts in this thread - definitely helped with the decision. 

Is there any way to get the suspend/resume working? Does it make a difference to ACPI whether im running in ahci or ide mode?

Thanks

---

### Post by miegiel on 2009-06-14
> **realitygaps said:**
> Just got the 3810T, thanks for all the informative posts in this thread - definitely helped with the decision. 

Is there any way to get the suspend/resume working? Does it make a difference to ACPI whether im running in ahci or ide mode?

Thanks

ACPI and AHCI are 2 different things.

Wikipedia is your friend :D
[http://en.wikipedia.org/wiki/ACPI](http://en.wikipedia.org/wiki/ACPI)
> 
Advanced Configuration and Power Interface (ACPI) specification is an open standard for unified operating system-centric device configuration and power management.

[http://en.wikipedia.org/wiki/AHCI](http://en.wikipedia.org/wiki/AHCI)
> 
Advanced Host Controller Interface (AHCI) is a programming-specification which defines the operation of Serial ATA host-controllers


---

### Post by realitygaps on 2009-06-14
Thanks for the tips, although I did actually realise that difference. Just thought perhaps the settings might affect something in ACPI.

Any idea how to get suspend/resume working?

Thanks

---

### Post by dhlacik on 2009-06-16
> **realitygaps said:**
> Thanks for the tips, although I did actually realise that difference. Just thought perhaps the settings might affect something in ACPI.

Any idea how to get suspend/resume working?

Thanks

Hi, It works for me. You may want to go to acer website and update to latest BIOS for your Acer Timeline.

---

### Post by tokyoahead on 2009-06-16
nope, cannot confirm that. resuming after suspend does not work, even with the 1.04 bios from the acer website.

---

### Post by realitygaps on 2009-06-16
I have the same experience as tokyohead, upgraded the bios and resuming from suspend still powers off... any ideas?

---

### Post by dhlacik on 2009-06-19
> **realitygaps said:**
> I have the same experience as tokyohead, upgraded the bios and resuming from suspend still powers off... any ideas?

Hi , i have workarounded a lot of issues (mainly problem with brightness and reset/power-off) by installing a 2.6.30 kernel to my jaunty.

1. Download & install the 2.6.30 kernel according to your architecture:

i386 users:
Code:
```

$ wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630_2.6.30-020630_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb
$ sudo dpkg -i linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb linux-headers-2.6.30-020630_2.6.30-020630_all.deb linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb

```
amd64 users:
Code:
```

$ wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630-generic_2.6.30-020630_amd64.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630_2.6.30-020630_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-image-2.6.30-020630-generic_2.6.30-020630_amd64.deb
$ sudo dpkg -i linux-headers-2.6.30-020630-generic_2.6.30-020630_amd64.deb linux-headers-2.6.30-020630_2.6.30-020630_all.deb linux-image-2.6.30-020630-generic_2.6.30-020630_amd64.deb

```

Restart and boot to new kernel.

---

### Post by federa on 2009-06-20
hey..
the 2.6.30 kernel you've installed checks the right amount of RAM you have??
the 2.6.28 kernel does not recognize the right size: 2.9 GB instead of 3.9!
other question: resume after suspend work after upgraded kernel??

thanks very much!!

---

### Post by muckst3r on 2009-06-21
Hello All,

I've just gotten started with Ubuntu and a new 3810t this weekend and feel I haven't had nearly as much as success as everyone here. In particular, things run brilliantly for hours but then I inevitably get file system corruption on EXT3 as well as some random segfaults. It's quite bad actually - I generally have to reinstall afterward as fsck.ext3 can't repair the file system adequately. No, I haven't yet ruled out some hardware problems (although memtest86 tests fine). And yes, I've put the HD in IDE mode.

My first question: are you using the 64-bit version of Jaunty / 9.04 or are you sticking with the 32-bit version? Perhaps I've just tried to be too bleeding-edge.

regards,

/m

---

### Post by serxxx on 2009-06-22
(Reposted from the Launchpad group)

Here's another 4810 experience:

I replaced the internal harddrive with a 30GB OCZ SSD that I had
already formatted via USB on another Linux box, to ensure that the
block sizes were "optimal"
([http://thunk.org/tytso/blog/2009/02/20/aligning-filesystems-to-an-ssds-erase-block-size/](http://thunk.org/tytso/blog/2009/02/20/aligning-filesystems-to-an-ssds-erase-block-size/)).

I installed from a Kubuntu 8.10 CD and did a dist upgrade to 9.04.
Everything went fine, except upon reboot the BIOS hung (didn't even
get to GRUB) and then rebooted; when it came up, I went into the BIOS
and changed the interface from AHCI (or whatever it was) to IDE; that
fixed it.  It booted without problems directly into KDM.

   1. The driver was correctly identified, and the screen resolution
      was correctly set.  Compiz was enabled by default, and the eye
      candy worked (mostly) fine.  There were some artifacts
      (background windows obscured by pop-up alerts were often not
      refreshed correctly when the alerts were dismissed).
      Considering how insanely buggy KDE 4.2 is, I'm inclined to blame
      KDE.
   2. Wireless networking started out beautifully, but at least once
      the connection would drop and KDE would refuse to reconnect.
      Again, at the moment I'm blaming KDE (see below).
   3. I haven't tried bluetooth yet.
   4. USB is ***mostly*** fine; an RF mouse with dongle worked as expected.
   5. KDE wouldn't recognize a USB memory stick (again, definitely a
      KDE bug -- see below)
   6. Within a couple of hours, the KDE panel crashed.  Not a laptop
      issue.
   7. Suspend/resume worked with no problems.  In fact, it's got the
      ***fastest*** resume of any laptop I've seen -- it is incredible.
   8. Haven't tried hibernate yet.
   9. The "toggle the touchpad button" works, but it is a one-way
      trip.  Once you turn it on, it won't turn off.  However, I've
      discovered that turning it off, suspending, and resuming causes
      it to come back on again.  In fact, turning the touchpad off,
      suspend, and resuming causes it to come back on again -- even if
      the button is lit, saying that the touchpad is off.  I think
      this is a Ubuntu problem.
  10. The SD/MMC/etc. slot works perfectly.
  11. I was pleasantly surprised by the performance of the machine.
      The screen is beautiful, and bright.  The battery life seems
      about on par with the advertised time (haven't done any
      strenuous testing, but my wife had it on battery for most of the
      day, so 8 hours wouldn't have been far off the mark).
  12. The sleep button doesn't seem to be recognized by the default
      Ubuntu set-up.
  13. The brightness keys are recognized, but don't seem to have any
      actual effect.
  14. The audio keys are also recognized, but I haven't tested them yet
  15. The "blank screen" function works beautifully -- why don't all
      laptops have this??

KDE was so twitchy that I installed ubuntu-destop and re-logged in to
Gnome.

   1. I haven't seen any artifacts related to alerts, so #1 seems
      fixed by this.  Hence, it seems to be a KDE problem.
   2. I haven't had any problems with wireless, so #2 seems to be a
      KDE problem, too.
   3. Gnome correctly recognized the USB stick, and would let me mount
      it; #5 is definitely a KDE problem.
   4. The battery life ***seems*** a little less robust under Gnome, but
      I'll do some timings next week-end.

So, though I hate Gnome because of it's insistence on moving the order
of "Ok/Cancel" buttons, it is definitely less buggy than KDE 4.2, and
the laptop works much better under it.  <rant>The button swap was a
horrible user-interface decision.  Many people are forced to use
Windows at work, and the order of Ok/Cancel buttons has been a
de-facto standard in UIs for years.  The decision to change this order
causes confusion for people having to use multiple desktop
environments, and was entirely arbitrary, or based on vague,
poorly-supported guesses on usability benefits.  It should rank as one
of history's worst UI decisions.</rant>

In summary, the laptop works well under Linux.  The "disable touchpad"
button is a god-send under Windows, and if anybody figures out how to
get it working correctly under Linux, please post about it.  This
touchpad is extremely sensitive, and being able to disable it is
critically important -- and while that part works, being unable to
re-enable it (easily) means that an external mouse is really a
requirement for this laptop under Linux.

---

### Post by klawlf on 2009-06-22
hi serxxx, reactivating the touchpad works fine out of the box here with Mandriva 2009.1

---

### Post by muckst3r on 2009-06-22
> **klawlf said:**
> hi serxxx, reactivating the touchpad works fine out of the box here with Mandriva 2009.1

That feature works flawlessly here too, straight out of the box.

--
Acer 3810t
u9400
64-bit Ubuntu 9.04

---

### Post by BooToo on 2009-06-23
Can you please confirm if the Ethernet driver also works with the 64 bits 9.4 Ubuntu version?
Many thanks,
BooToo

---

### Post by muckst3r on 2009-06-23
> **BooToo said:**
> Can you please confirm if the Ethernet driver also works with the 64 bits 9.4 Ubuntu version?
Many thanks,
BooToo

I don't know - it's a struggle for me to find a wired network much anymore! I'll give it a go at work tomorrow and see how it goes.

---

### Post by bududu on 2009-06-24
> **Neo5588 said:**
> You are correct, the timer for the battery life never says more than 4 hours but I believe this to be a loose approximation because it also say that the battery life is unknown as well. I have not actually tried to run out the battery in Linux and time it. You might be able to change the brightness of the screen to save some more.

Have anybody tried to run out battery and measure real battery life of 3810T with Ubuntu?
Battery life is one of the most important points for me..

---

### Post by bududu on 2009-06-24
And what about multitouch touchpad? Does it work well under Ubuntu?

Thanks!

---

### Post by avilella on 2009-06-25
Hi bududu,

I think the multitouch options can be turned on by editing the xorg.conf file. For example, adding options like this:

Option "VertTwoFingerScroll" "1"
Option "HorizTwoFingerScroll" "1"
Option "EmulateTwoFingerMinZ" "120"#  Option          "AlwaysCore"


> **bududu said:**
> And what about multitouch touchpad? Does it work well under Ubuntu?

Thanks!

---

### Post by realitygaps on 2009-06-26
Hi guys, thanks again for all the info on this thread

Suspend/resume still isnt working for me, with bios 1.04 and kernels 2.6.28 and 2.6.30 on both jaunty and karmic (32bit and 64bit). Suspending works fine but resuming powers off the computer.

Is anyone else still having suspend/resume problems or is it just me?

anyone have any ideas?

Thanks

---

### Post by Incompetnce on 2009-06-26
I want to put ubuntu on my 4810T, but if it significantly reduces my battery life I'm not sure... Also, if it involves significant work to get going, I don't know... I'll try a LiveCD first, I guess...

---

### Post by muckst3r on 2009-06-26
> **realitygaps said:**
> 
Suspend/resume still isnt working for me, with bios 1.04 and kernels 2.6.28 and 2.6.30 on both jaunty and karmic (32bit and 64bit). Suspending works fine but resuming powers off the computer.

Is anyone else still having suspend/resume problems or is it just me?


I've got the Core 2 Duo processor in a 3810t, I've tried both these kernels in 32 and 64-bit Jaunty and this is precisely what happens when I suspend to RAM as well. I'm out of ideas for the moment frankly.

---

### Post by Tocharius on 2009-06-27
I have a problem with the audio on my 3810T as well. It used to work out of the box with a fresh Ubuntu 9.04, but it doesn't work anymore after installing the latest updates.

Is there a way to reset alsa, or what else should I try?

---

### Post by Incompetnce on 2009-06-27
I just put a Live CD into my 4810 and it's worked like a dream: sound, wifi without a problem. I've now just got to get it to install without upsetting windows and everything will be fine and dandy.

Anyone who could link me to information regarding installing ubuntu (9.04) without upsetting my windows installation, that would be much appreciated. My plan is to have 3 partitions: Vista, Jaunty and a Data partition that both ubuntu and windows can read...

Incidentally, I can upgrade to Windows 7 today, acording to information that came with my timeline... I might give it a try.
["Turn off touchpad" button works, but you can't turn touchpad back on...]

---

### Post by Tocharius on 2009-06-28
Ok, I reinstalled jaunty, installed only the important security updates, and the sound still works.

---

### Post by Ususbuntung on 2009-06-29
Hi all,
I'd like to share my experience with my 3810T, Core2 Solo:
- with Jaunty, 4 GB mem shows only 2.9, using free
- BIOS v1.01, recovery after suspend works, hibernate is still problem
- a bit problem using compositing with Compiz, good with Metacity.

Recently I install Ultimate Edition, it works very well, where Compiz shows no problem with Compiz, but suspend and hibernate do not work at all.

Regards

---

### Post by bududu on 2009-06-29
Here is my experience with Acer 3810T (solo) and Xubuntu 9.04.

Almost everything works by default. Except:
1. Skype doesn't work with microphone. (Microphone works, but skype can't get sound from it).
2. Suspend to ram doesn't work
3. <s>Multitouch touchpad doesn't work.</s> synclient -m 100 doesn't show more than "1 finger".
I've tried to make it working with these guide:
[http://ubuntu-snippets.blogspot.com/2009/03/multi-touch-for-anyall-synaptics.html](http://ubuntu-snippets.blogspot.com/2009/03/multi-touch-for-anyall-synaptics.html)

Do anybody use skype under xubuntu/ubuntu with these laptop? Have you any issues with mic?

<s>And what about multitouch touchpad, is it working for anybody?</s>

It is working me :) Sorry for confusing you guys.

It really doesn't show multi-touch support in synclient -m 100 output, however it works with following hal code (see link above for details):

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <!-- Arbitrary options can be passed to the driver using
             the input.x11_options property since xorg-server-1.5. -->
        <!-- EXAMPLE:
        <merge key="input.x11_options.LeftEdge" type="string">120</merge>
        -->
	<merge key="input.x11_options.SHMConfig" type="string">On</merge>
        <merge key="input.x11_options.EmulateTwoFingerMinZ" type="string">80</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.TapButton1" type="string">1</merge>
        <merge key="input.x11_options.TapButton2" type="string">2</merge>
        <merge key="input.x11_options.TapButton3" type="string">3</merge>

    </match>
  </device>
</deviceinfo>
```

The most confusing part is TapButton 2 and 3. According to these code "two fingers click" should emulate second (right button), but in my case with this hal code - two fingers click emulates 3-rd button.

---

### Post by bududu on 2009-06-29
Ah.. actually, it is not real multi-touch support. It is just emulation of multi-touch. So, Ubuntu can't recognize multi-touch capabilities of our touchpad. Isn't it?

---

### Post by Jimcanoa on 2009-06-29
Just a few words to thank all of you for your contribution to the linux community... I just got my 3810T and found this thread and I found the solution to *everything* here!

Simply put, today I'm really proud of being a linux user!

---

### Post by Incompetnce on 2009-06-29
BAM, just installed ubuntu on my 4810 with no problems. I've not yet checked multitouch or webcam, but I'm not all that fussed about either.

But I will try and get the battery life back to 8 hours if possible. Any help in that respect is appreciated.

---

### Post by muckst3r on 2009-06-30
> **Ususbuntung said:**
> Hi all,
- with Jaunty, 4 GB mem shows only 2.9, using free
Regards

Could it be you're not using the 64-bit version of Jaunty? 32-bit operating systems can address a maxium of 3GB of RAM.

---

### Post by gnawol on 2009-06-30
> **Tocharius said:**
> I have a problem with the audio on my 3810T as well. It used to work out of the box with a fresh Ubuntu 9.04, but it doesn't work anymore after installing the latest updates.
Is there a way to reset alsa, or what else should I try?


I have an Acer Aspire 3935 and had the same problem after updating the kernel. I found a solution to fix it ( its the same as the Acer Aspire one microphone fix taken from [https://help.ubuntu.com/community/AA1/Fixes](https://help.ubuntu.com/community/AA1/Fixes) )

Download [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2) 
Extract it somewhere then open the terminal and enter the folder
then type the following; 

```
sudo apt-get install build-essential linux-headers-$(uname -r)
./configure --with-cards=all
make
sudo make install
```

Reboot and set your audio levels and make sure everything is unmuted.

That's it.

Hope it helps

---

### Post by avilella on 2009-06-30
Hi,

Is this the model with integrated Intel graphics card or with discrete ATI graphics card?

> **Incompetnce said:**
> I just put a Live CD into my 4810 and it's worked like a dream: sound, wifi without a problem. I've now just got to get it to install without upsetting windows and everything will be fine and dandy.

Anyone who could link me to information regarding installing ubuntu (9.04) without upsetting my windows installation, that would be much appreciated. My plan is to have 3 partitions: Vista, Jaunty and a Data partition that both ubuntu and windows can read...

Incidentally, I can upgrade to Windows 7 today, acording to information that came with my timeline... I might give it a try.
["Turn off touchpad" button works, but you can't turn touchpad back on...]

---

### Post by cucisan on 2009-07-01
hi guys!

im planning on getting a acer timeline 3810T.. but i dunno if i should get the core2duo version which kosts 120-220eur more than the core solo version..

i dont want the ati card.. i hate fglrx so much after years of using it ;)

please please please!

tell me your experiences with both versions.. how is the performance (perhaps in comparison to other pcs you have owned & used like netbooks, other notebooks with better hardware).. is the solo really that damn slow? i read about some user comments whining 'bout its so slow .. but hey they ran vista..

even my core2duo P8600 with 4GB ram is sometimes a real pain with vista compared to ubuntu which feels muchmuch faster.


then next, PLEASE anyone.. time your battery life! really.. its so important for so many people including me (and the main point in getting this laptop)

a reallife example would be 30-40% display brightness and wlan on.. doing some easy stuff.. like surfing etc..

i think that would be the most important measurement for batterylife.. 

sorry for being a littlebit offtopic.. ;)

and thanks to everybody giving me answers :)

---

### Post by Incompetnce on 2009-07-02
> **avilella said:**
> Hi,

Is this the model with integrated Intel graphics card or with discrete ATI graphics card?

Integrated graphics version, I think...

---

### Post by miegiel on 2009-07-02
> **cucisan said:**
> hi guys!

im planning on getting a acer timeline 3810T.. but i dunno if i should get the core2duo version which kosts 120-220eur more than the core solo version..

i dont want the ati card.. i hate fglrx so much after years of using it ;)

please please please!

tell me your experiences with both versions.. how is the performance (perhaps in comparison to other pcs you have owned & used like netbooks, other notebooks with better hardware).. is the solo really that damn slow? i read about some user comments whining 'bout its so slow .. but hey they ran vista..

even my core2duo P8600 with 4GB ram is sometimes a real pain with vista compared to ubuntu which feels muchmuch faster.


then next, PLEASE anyone.. time your battery life! really.. its so important for so many people including me (and the main point in getting this laptop)

a reallife example would be 30-40% display brightness and wlan on.. doing some easy stuff.. like surfing etc..

i think that would be the most important measurement for batterylife.. 

sorry for being a littlebit offtopic.. ;)

and thanks to everybody giving me answers :)

Personally I think the mobile core solo is a pointless CPU. If I wouldn't need the performance of a core duo I'd get a laptop with an Atom. The Atom is a single core too, but at least it's got hyper threading. ASUS and Acer both have Atom laptops with great battery live and 11.6" LED back lit 1366x768 screens.

Here are some links to compare the CPU's :
[_Intel Core2 Solo SU3500_]("http://ark.intel.com/Product.aspx?id=37133")
[_Intel Core2 Duo SU9400_]("http://ark.intel.com/Product.aspx?id=36697")
[_Intel Atom Z520_]("http://ark.intel.com/Product.aspx?id=35466")

As for battery life I've read from several users and review sites that it lasts 8½ to over 10 hours if the laptop is on and _doing nothing_. If you ramp up the power you use to the max it lasts about 2½ to 3 hours (full brightness, wireless on, cpu @ 100%, disk continuously reading/writing, etc.).

---

### Post by Incompetnce on 2009-07-02
> **miegiel said:**
> As for battery life I've read from several users and review sites that it lasts 8½ to over 10 hours if the laptop is on and _doing nothing_. If you ramp up the power you use to the max it lasts about 2½ to 3 hours (full brightness, wireless on, cpu @ 100%, disk continuously reading/writing, etc.).

Were those websites and users using windows or linux? I doubt I've got anywhere near 8 hours with ubuntu yet. (I haven't tried to get into optimising battery performance yet, so I'm not saying it isn't possible...)

---

### Post by miegiel on 2009-07-02
> **Incompetnce said:**
> Were those websites and users using windows or linux? I doubt I've got anywhere near 8 hours with ubuntu yet. (I haven't tried to get into optimising battery performance yet, so I'm not saying it isn't possible...)

Windows, but as I said it's when the laptop is doing nothing, just sitting there waiting for the battery to run out. I don't think windows users will get to 8 hours either. Even if you're only reading web pages there are always flash adds and
:lolflag:
 animations sucking juice from the battery. It's almost impossible to say how long a battery lasts for someone. But if you know what the max and min battery life is, you can figure out how long it will last you for your usage.

---

### Post by Incompetnce on 2009-07-02
My point was that the default power management options on the pre-installed Vista are more sophisticated than for Ubuntu. So out of the box you'll get better battery life on windows. If anyone knows any more about this please do share.

---

### Post by cucisan on 2009-07-02
> **miegiel said:**
> Personally I think the mobile core solo is a pointless CPU. If I wouldn't need the performance of a core duo I'd get a laptop with an Atom. The Atom is a single core too, but at least it's got hyper threading. ASUS and Acer both have Atom laptops with great battery live and 11.6" LED back lit 1366x768 screens.



well .. i think the core solo MAY be a good choice.. because its cheap and seems to be a nice alternative to those atoms brrr
but i never had the chance to test a system with that cpu
so i hoped for some answers here... 

the acers with 11.6" -> intel gma500 (wtf?)... gl hf.. search for adamw.. he said everything that has to be said ;)
it costs only 100eur less then the acer with coresolo.. but i get much more from the timeline (specs + doubled warranty!) 
i like asus but not their netbooks.. design horrible mixed with good batterylifetime or vice versa.. no thanks
i tried netbooks -alot.. they suck so much for how much they cost and the screens are too small for my eyes

nevertheless thanks for the links :)

---

### Post by PatrickVogeli on 2009-07-02
for powersaving, look into this thread: [http://ubuntuforums.org/showthread.php?t=847773](http://ubuntuforums.org/showthread.php?t=847773)

it's meant for the xps m1330, but it should be a good starting point, since most of it should be the same for the timeline, as both have intel chipsets

---

### Post by ghosthead123 on 2009-07-04
> **tokyoahead said:**
> Hi guys, 

2. The LAN Card
On this page here: [http://partner.atheros.com/Drivers.aspx]("http://partner.atheros.com/Drivers.aspx") you can find the AR813X-linux-v1.0.0.8.tar.gz driver. The README in the file pretty much explains the installation. The MAKE INSTALL failed for me on the installation of the man-file but that does not seem to have mattered. Now the card is deteced.

Here is a mode detailed description:
$ gunzip AR813X-linux-v1.0.0.8.tar.gz
$ tar xvf AR813X-linux-v1.0.0.8.tar.gz
$ cd src/
$ make
$ sudo make install
restart
[/URL]

I just buy my acer 3810t and install ubuntu 9.04 but the only thing thast not work is the lan card. I cant find anywhere AR813X-linux-v1.0.0.8.tar.gz only [459]AR813X-linux-v1.0.0.9.tar.gz which did not work with my pc. When i try to "sudo make install" there is an error:

=====================================================
ivan@ivan-laptop:~/Desktop/[459]AR813X-linux-v1.0.0.9/src$ make
make -C /lib/modules/2.6.28-13-generic/build SUBDIRS=/home/ivan/Desktop/[459]AR813X-linux-v1.0.0.9/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
ivan@ivan-laptop:~/Desktop/[459]AR813X-linux-v1.0.0.9/src$ sudo make install
[sudo] password for ivan: 
make -C /lib/modules/2.6.28-13-generic/build SUBDIRS=/home/ivan/Desktop/[459]AR813X-linux-v1.0.0.9/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
# remove all old versions of the driver
find /lib/modules/2.6.28-13-generic -name atl1e.ko -exec rm -f {} \; || true
find /lib/modules/2.6.28-13-generic -name atl1e.ko.gz -exec rm -f {} \; || true
install -D -m 644 atl1e.ko /lib/modules/2.6.28-13-generic/kernel/drivers/net/atl1e/atl1e.ko
install: cannot stat `atl1e.ko': No such file or directory
make: *** [install] Error 1
=======================================================
Please someone help!

---

### Post by miegiel on 2009-07-04
> **ghosthead123 said:**
> install: cannot stat `atl1e.ko': No such file or directory
make: *** [install] Error 1

Check if atle.ko does exist you might have the typo bug mentioned [_here_]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/292411").

---

### Post by Step by Step on 2009-07-04
Hi everyone and thank you for the very useful info I found here. I have a 4810T and used Ubuntu without any problems for some weeks. Actually the laptop used to get hot in the hard disk place but I didn't pay great attention to that... Till the other day: after doing too many experiments I decided to re-install Ubuntu. Partition Editor told me that in the Vista partition some clusters were corrupted. I ignored it and tried to proceed anyway, but the process stopped with a disk error and then even grub was lost. Anyway after waiting some hours I was able to launch the installation again and now have both the systems working...

The problem is that now I'm too scared to go back to Ubuntu even if I'm already missing it :P
Have you experienced overheating problems too? Can you please help me finding a solution?

---

### Post by avilella on 2009-07-04
I would suggest you recover the original partitioning from the Windows recovery disk and then do a clean Ubuntu install.
With the new Ubuntu, can you report this problem in a new launchpad bug?
[http://bugs.launchpad.net](http://bugs.launchpad.net)

Attaching at least this info:

cat /proc/version > proc.version.txt
sudo lspci -vvnn > lspci.vvnn.txt
uname -a > uname.txt
lsmod > lsmod.txt
sudo dmidecode > dmidecode.txt
/var/log/syslog
/var/log/kern.log.0
/var/log/kern.log


> **Step by Step said:**
> Hi everyone and thank you for the very useful info I found here. I have a 4810T and used Ubuntu without any problems for some weeks. Actually the laptop used to get hot in the hard disk place but I didn't pay great attention to that... Till the other day: after doing too many experiments I decided to re-install Ubuntu. Partition Editor told me that in the Vista partition some clusters were corrupted. I ignored it and tried to proceed anyway, but the process stopped with a disk error and then even grub was lost. Anyway after waiting some hours I was able to launch the installation again and now have both the systems working...

The problem is that now I'm too scared to go back to Ubuntu even if I'm already missing it :P
Have you experienced overheating problems too? Can you please help me finding a solution?

---

### Post by alvinator@ on 2009-07-06
Just got an Acer Timeline 4810T yesterday (Thanks to this forum btw). Anyone care to explain or provide me a link how to work around the brightness settings? The brightness controls seems to work but does not actually change the screen brightness.

---

### Post by The Tronyx on 2009-07-07
I see some people on this thread saying that they have had no issues and some people staying that they have had a few issues.  For the people that are saying this thread helped them fix everything or that everything is working for them 100%, are you able to suspend the laptop or is that mostly the sticking point right now?

---

### Post by federa on 2009-07-08
Is there someone out there that is able to recompile kernel?
i'm not very good in doing that stuff..but if all the people with acer timeline could have a compiled kernel that allow them to use the suspend function, hi saving batteries, remove all the useless modules (es PCMCIA, IRDA ecc ecc..), allow ubuntu to see 4 gb of RAM ecc ecc..with all these stuff i think that acer timeline+ubuntu will be better than apple..and many many people interesse! Canonical instead should do this! :)

---

### Post by The Tronyx on 2009-07-08
> **federa said:**
> Is there someone out there that is able to recompile kernel?
i'm not very good in doing that stuff..but if all the people with acer timeline could have a compiled kernel that allow them to use the suspend function, hi saving batteries, remove all the useless modules (es PCMCIA, IRDA ecc ecc..), allow ubuntu to see 4 gb of RAM ecc ecc..with all these stuff i think that acer timeline+ubuntu will be better than apple..and many many people interesse! Canonical instead should do this! :)

Hi,

There's a post a few pages back that talks about using a .deb and dpkg to install an updated kernel which will supposedly work with suspend and other stuff.  Might want to give it a try and let us know how it works out for you.

My timeline is still in the mail.  I'll report back once it arrives :)

---

### Post by federa on 2009-07-08
> **2point0 said:**
> Hi,

There's a post a few pages back that talks about using a .deb and dpkg to install an updated kernel which will supposedly work with suspend and other stuff.  Might want to give it a try and let us know how it works out for you.

My timeline is still in the mail.  I'll report back once it arrives :)

i'm using the kernel 2.6.30...problems are not solved: resuming after suspend still doesn't work, battery life is not so much long as you use windows..ram is 3gb instead of 4gb...BUT: backlight works much better  :D

nothing more nothing else..

---

### Post by mrwiggum on 2009-07-08
People who are still having problems should post:
1. The full model of laptop they are using. (including info on what processor, graphics etc.)
2. The Ubuntu release. (including if it's the x86 or x86_64 build etc.)
3. Any modifications they have already made. (i.e. new kernel, alsa, bios changes, or boot params.)
4. The problems they are having.
5. Applicable error messages.

That way we may be able to isolate problems to certian os versions or hardware revisions.

---

### Post by federa on 2009-07-08
> **mrwiggum said:**
> People who are still having problems should post:
1. The model of laptop they are using.
2. The Ubuntu release. (including if it's the x86 or x86_64 build etc.)
3. Any modifications they have already made. (i.e. new kernel, alsa, bios changes, or boot params).
4. The problems they are having.
5. Applicable error messages.

That way we may be able to isolate problems to certian os versions or hardware revisions.

hi...i'm federico from modena, italy:
1. acer aspire timeline 3810t (core due duo processor)
2. ubuntu jaunty jackalope 32 bit (the 64 bit distro, doesn't work on my pc!)
3. Installed new kernel: 2.6.30, modified boot parameters to workarounds of HD (libata.noacpi=1)
4. resuming after suspend never worked; battery life: 7 hours..with powertop; laptop mode doesn't start auto when desconnected from AC
5. no error messages in log...

---

### Post by The Tronyx on 2009-07-08
> **federa said:**
> hi...i'm federico from modena, italy:
1. acer aspire timeline 3810t (core due duo processor)
2. ubuntu jaunty jackalope 32 bit (the 64 bit distro, doesn't work on my pc!)
3. Installed new kernel: 2.6.30, modified boot parameters to workarounds of HD (libata.noacpi=1)
4. resuming after suspend never worked; battery life: 7 hours..with powertop; laptop mode doesn't start auto when desconnected from AC
5. no error messages in log...

Hello Federa,  

Even after the kernel upgrade suspend still isn't working?

---

### Post by mrwiggum on 2009-07-08
Have you tried deactivating ncq instead of acpi for the boot work around?

---

### Post by The Tronyx on 2009-07-08
Small update, as noted, I don't have my timeline yet but I will shortly.  In the mean time, you may wish to create a custom DSDT to see if that takes care of suspend.

[http://gaugusch.at/kernel.shtml](http://gaugusch.at/kernel.shtml)
[http://ubuntuforums.org/showthread.php?t=426684](http://ubuntuforums.org/showthread.php?t=426684)

---

### Post by alvinator@ on 2009-07-08
Ok, I finally had time to fix more issues on my Timeline 4810T SU3500. For people having issues with Suspend, Hibernate, Brightness, and ACPI. The solution has already been posted here before so I'll just echo this back:

First download the 2.6.30 kernel packages from the kernel PPA:
```

#$ wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630_2.6.30-020630_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb

``````

#$ sudo dpkg -i linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb linux-headers-2.6.30-020630_2.6.30-020630_all.deb linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb

```Reboot and you might notice that you lost your sound. To fix it, we have to build the ALSA module for our newly installed kernel:
```

#$ sudo apt-get install build-essential linux-headers-$(uname -r)

```Download and Extract [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2)
```

#$ cd alsa-driver-1.0.20/
#$ ./configure --with-cards=all
#$ make
#$ sudo make install

```Reboot and you'll find that the sound is either muted or in a very low volume (same case with mic). To fix this tinker your settings using "alsamixer":
```

#$ alsamixer

```After that you will have a fully working Ubuntu on your Acer Timeline. ACPI works properly and you'll immediately notice a performance increase on video (try setting the Visual Effects to Extra). AHCI mode also works! Keep in mind that you might have to recompile and install ALSA again when you upgrade to a new kernel (Unless Ubuntu releases their own 2.6.30 generic kernel in the repositories). Also there's a quick way to check if your webcam is working:

```

#$ gst-launch-0.10 v4l2src ! xvimagesink

```Cheers!

EDIT: For those who experienced some network disconnection issues with kernel 2.6.28 (when copying large files within a local network), 2.6.30 seems to resolve the problem. :)

---

### Post by The Tronyx on 2009-07-08
> **alvinator@ said:**
> Ok, I finally had time to fix more issues on my Timeline 4810T SU3500. For people having issues with Suspend, Hibernate, Brightness, and ACPI. The solution has already been posted here before so I'll just echo this back:
...


Very nice alvinator@.  Thanks for the input on how to get it going 100%.  Really happy to know that the kernel update takes care of suspend.

---

### Post by mrwiggum on 2009-07-08
alvinator@ what problems did you have/fixed did you apply previously?

---

### Post by alvinator@ on 2009-07-08
> **mrwiggum said:**
> alvinator@ what problems did you have/fixed did you apply previously?

Sorry can you rephrase your question?

I was using a vanilla Ubuntu 9.04 on it and updated to kernel 2.6.28-generic. I got this laptop as my emergency replacement for my work PC so I had little time to fix some issues. 

First thing I noticed when I was using the Ubuntu built 2.6.28 kernel is that my laptop seems to get disconnected when copying large files over the network (using LAN or WLAN). I tried to alleviate the problem by increasing the MTU to 1500 in /proc/network/interfaces but the problem persisted.

Doing the steps I mentioned before should fix all the problems. I have to give kudos to the guys who posted the kernel 2.6.30 PPA links.

---

### Post by The Tronyx on 2009-07-08
> **federa said:**
> i'm using the kernel 2.6.30...problems are not solved: resuming after suspend still doesn't work, battery life is not so much long as you use windows..ram is 3gb instead of 4gb...BUT: backlight works much better  :D

nothing more nothing else..

Federa, could you please provide us with the output of uname -a?  Thanks.

---

### Post by csipuka on 2009-07-10
I have a 4810, and during boot it is strange for me after grub started and I can see the loading... screen, but I need to wait about 10 seconds to get the splash screen of boot. 
Does anybody have an idea what happens in the background or how to check it? On my desktop I almost get immediatelly the splash screen after grub.

Anyway my laptop is a dualcore (SU9400) with an ATI card.
If I uses the integrated card, then the laptop is quite warm, and estimated 3 hours in battery mode. 
I changed to use ATI in powersave mode, and with some powermod suggestion currently about 6 hours is the estimated time.
The powertop says about 12W.
I tried to upgrade to kernel 2.6.30, but in tht case I cannot uses the ATI card, and I do not want to install it manually.
The brightness control works, but do not display the popup during when I change the brightness.
Audio is ok, but I still have problem with microphone, skype does not like it.
The built in webcam and wifi work out of the box.

---

### Post by alvinator@ on 2009-07-10
> **csipuka said:**
> I have a 4810, and during boot it is strange for me after grub started and I can see the loading... screen, but I need to wait about 10 seconds to get 


I have the same issue too, I'll find it out when I have time. 

One more useful advice: 
Be sure to add the CPU Frequency Scaling monitor applet. It works on 2.6.30. You will be able to set your CPU Frequency from 1.4ghz, 1.2ghz, and 800mhz or on-demand. Good stuff! :)

---

### Post by The Tronyx on 2009-07-10
> **alvinator@ said:**
> I have the same issue too, I'll find it out when I have time. 

One more useful advice: 
Be sure to add the CPU Frequency Scaling monitor applet. It works on 2.6.30. You will be able to set your CPU Frequency from 1.4ghz, 1.2ghz, and 800mhz or on-demand. Good stuff! :)

Hi.  You may want to install bootchart which will show you how long each "thing" is taking during the boot stage.  If you would lik, to see what is happening as it's happening, edit /boot/grub/menu.lst and add change the boot line from 'splash' to 'nosplash' and restart.

Cheers.

---

### Post by soyEdulix on 2009-07-10
I'm getting random segfaults and I can't live with that. It's probably related to the kernel driver but I can't really live with something like that so I'm going to return my laptop, it's an Acer Timeline 3810T, testing Ubuntu 9.04 64 bits. Otherwise the laptop is cool, but I with kwin compositing some things work quite good (kwin animations) and others are a bit laggy (ktabwidget switching). Also, the Core 2 solo is not very fast specially if you plan to do compiling on it.

---

### Post by The Tronyx on 2009-07-10
> **soyEdulix said:**
> I'm getting random segfaults and I can't live with that. It's probably related to the kernel driver but I can't really live with something like that so I'm going to return my laptop, it's an Acer Timeline 3810T, testing Ubuntu 9.04 64 bits. Otherwise the laptop is cool, but I with kwin compositing some things work quite good (kwin animations) and others are a bit laggy (ktabwidget switching). Also, the Core 2 solo is not very fast specially if you plan to do compiling on it.

When I see random segfaults the first thing that comes to mind is that it might be RAM.  Not that you should just buy new RAM for a brand new machine, just saying...

---

### Post by gotosk on 2009-07-11
hi, I'm a chinese guy using 4810T with ubuntu 9.04 for several days.
About brightness, I tried the ways  of editing /etc/default/acpi-support, /etc/laptop-mode/laptop-mode.conf files for LCD brightness control, but it doesn't work.

After doing some seaches on google, I got this method now well working for me:)

first :

```
$ xrandr --output LVDS --set BACKLIGHT_CONTROL native
```

if you don't have xbacklight, just:

```
sudo apt-get install xbacklight
```

then

```
xbacklight -set 60
```

now change the value you want, and enjoy!
Can define some hot-key in Compiz and bind them with custom sh files in ~/bin.

I have my quetions about multi-touch and power_saving, If you have any good suggestion on them, please tell me.

---

### Post by alvinator@ on 2009-07-12
> **gotosk said:**
> hi, I'm a chinese guy using 4810T with ubuntu 9.04 for several days.
About brightness, I tried the ways  of editing /etc/default/acpi-support, /etc/laptop-mode/laptop-mode.conf files for LCD brightness control, but it doesn't work.

After doing some seaches on google, I got this method now well working for me:)

first :

```
$ xrandr --output LVDS --set BACKLIGHT_CONTROL native
```if you don't have xbacklight, just:

```
sudo apt-get install xbacklight
```then

```
xbacklight -set 60
```now change the value you want, and enjoy!
Can define some hot-key in Compiz and bind them with custom sh files in ~/bin.

I have my quetions about multi-touch and power_saving, If you have any good suggestion on them, please tell me.

Updating your kernel to 2.6.30 will solve most of the problems. Read about it on the last page. You can further enhance your battery life by using the CPU scaling applet. I operate mine most of the time @ 800mhz.

I upgraded my BIOS to 1.20. I recently experienced my CPU uncontrollably running 100% after I woke it up while downloading some stuff overnight. I'm not sure yet but it seems that 4810T BIOS 1.20 solved the problem.

---

### Post by gotosk on 2009-07-12
> **alvinator@ said:**
> Updating your kernel to 2.6.30 will solve most of the problems. Read about it on the last page. You can further enhance your battery life by using the CPU scaling applet. I operate mine most of the time @ 800mhz.

I upgraded my BIOS to 1.20. I recently experienced my CPU uncontrollably running 100% after I woke it up while downloading some stuff overnight. I'm not sure yet but it seems that 4810T BIOS 1.20 solved the problem.

Thank you for your advice. I just took linux distro as my desktop recently, and Ubuntu is the second linux distro that I tried, the first is Fedora.

How can I update my BIOS under Ubuntu? BIOS file on Acer website are executable file for Windows. For updating, I think I should run into DOS first, and use a usb stick, run flash.bat. Oops,It's a lot work to do... -_-

I never update kernel before. It's the last choice for me to solve problems. Maybe someday ubuntu do kernel updating, I can wait. :)

Choose "powersave" mode in CPU scaling applet, now CPU works at 800MHz.

---

### Post by muadnu on 2009-07-12
I'm considering buying a 3810T, and there's one thing I'm not sure about from all the posts (maybe it's there and I missed it). How does the touchpad work? Do the multitouch functions work? In particular, is there any way to get vertical scrolling working?

---

### Post by The Tronyx on 2009-07-12
My Setup experiences with the Timeline AS4810TZ-4696 SU2700.

**If you see a reference to overview, please refer to the relevant section(s) at [http://ubuntuforums.org/showpost.php?p=7582206&postcount=86**](http://ubuntuforums.org/showpost.php?p=7582206&postcount=86**)

**The installation**
_Ubuntu 9.04 Jaunty_
The installation took a bit to get right.  Others have reported that the install went fine.  The below is based on my attempts, ymmv.

_GUI installer_
When I used the GUI installer(not from the LiveCD environment) the CD-ROM continually came umounted during the install making it rather difficult.  Despite multiple attempts, the GUI installer would fail miserably and never fully complete.  Also had lots of I/O errors on sr0 not related to the disk, possible to the unmounting.  When I actually did manage to make it to the formatting part, it would eventually fail with lots of squashfs errors.

_Alternate isntallation media_
This worked fairly well but for some reason left the pointer/touchpad very unfunctional resulting in the pointer jumping around like complete madness - no workaround, required a reinstall

_LiveCD environment_
Worked perfectly.  Boot into the live environment then click the desktop icon to install to disk.  This corrected the touchpad issues and I have had no problems with erratic pointer behavior since.

**Components**
Wireless - works out of the box
Web cam  - works out of the box
Sound    - works out of the box
Suspend  - does not work, see kernel upgrade at overview (you will need to rebuild alsa after this, also covered in the overview.
NIC      - does not work out of the box, see overview

Despite some hiccups in getting started, the thing now works perfectly fine, sound keys, function keys, screen brightness changes, etc.

Not much else to say, it's up and working 100%, I love this little machine for the price and if anyone finds this thread and is wondering if they should buy one, I would say absolutely!

---

### Post by alvinator@ on 2009-07-12
> **muadnu said:**
> I'm considering buying a 3810T, and there's one thing I'm not sure about from all the posts (maybe it's there and I missed it). How does the touchpad work? Do the multitouch functions work? In particular, is there any way to get vertical scrolling working?

Vertical Scroll works out of the box. It can be done by dragging your finger on the right hand side (I originally assumed that it doesn't have one since there's no markings). Touchpad works fine and I don't see myself using the multi-touch functions (There's a way to enable this on X.org). There's a little annoyance though, the button for enabling/disabling the touchpad doesn't work yet on 2.6.30. My USB mouse and touchpad is enabled at the same time but it doesn't hinder my user experience though.

As for the BIOS, I dual-booted mine with Windows 7 RC to play some old school games. Flashing BIOS in windows was a breeze.

---

### Post by mopay on 2009-07-13
I already wrote about this in another post, but I think this is the right place.

I bought the acer Timeline 4810T and not work the CD/DVD recorder.

Recognized but when I insert a cd or dvd says there is no media.
This is the dmesg output

[ 20.210145] sd 1:0:0:0: [sda] Attached SCSI disk
[ 20.210190] sd 1:0:0:0: Attached scsi generic sg0 type 0
[ 20.212379] scsi 4:0:0:0: CD-ROM TSSTcorp CDDVDW TS-U633A AC01 PQ: 0 ANSI: 5
[ 20.217927] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[ 20.217931] Uniform CD-ROM driver Revision: 3.20
[ 20.218017] sr 4:0:0:0: Attached scsi CD-ROM sr0
[ 20.218057] sr 4:0:0:0: Attached scsi generic sg1 type 5
[ 20.218702] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[ 20.218721] ehci_hcd 0000:00:1a.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[ 20.218736] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[ 20.218740] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[ 20.218801] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1

When I insert a cd / dvd does not recognize that there is one in the recorder.
 
and this when I trying to mount it manually

me@me-laptop:~$ sudo mount -t iso9660 /dev/sr0 /media/cdrom0
[sudo] password for me:
montar: no se encontro medio en /dev/sr0
me@me-laptop:~$ sudo mount -t iso9660 /dev/scd0 /media/cdrom0
montar: no se encontro medio en /dev/sr0 [no media found]
	
Windows works properly, it recognizes the disk and reads and writes well.  

Sorry for my horrible English.

---

### Post by pmaciver on 2009-07-13
Okay, I need some help.

I Bought this laptop a few days ago and with the help of this thread I have got pretty much everything I want working. Not suspend and resume but that can wait for now. 

My specs are 

Acer Timeline 3810T core 2 solo
Ubuntu 9.0.4
Result of uname -a "Linux linuxbox 2.6.28-13-server #45-Ubuntu SMP Tue Jun 30 20:51:10 UTC 2009 i686 GNU/Linux"

My problem is that whenever I use a video media player, say for instance mplayer or vlc, they are fine playing at the default resolution for that video, as soon as I maximise or move the original video around the screen with any sort of pace, my gnome session shows a few crazy colors (like the number of colors has gone down) and then blows up and restarts at the login. 

I have tried various things. Using Gnome, xfce, fluxbox, but still the same result.

I renamed my home directory and created a fresh one just to see if that had anything to do with it same result.

I can't even ctrl-alt-f[1-8] to a console because it does this freezing thing until I come back to the f7 console.

It has only happened when I use video, I have gone crazy with compiz doing the effect where you zoom in and out to show all desktops and all sorts of things that will put the processor under stress but that didn't cause the problem to happen.

So, before I drive myself crazy does anyone know why this might be happening? Maybe the server Kernel perhaps? Not sure. I am going to give the generic kernel a try and see if that changes anything, although I won't have my 4 GB of RAM available to me. 

Anyway, like I said, anyone can shed some light on this I would love to hear it. In the mean time I will try the generic kernel and see what that does.

Thanks

---

### Post by pmaciver on 2009-07-13
So quick update/answer to my own post, using generic kernel did fix things.

Now does anyone know how I can get my 4GB of ram back?

Also does anyone know why the server kernel did that? It would be good to know.

> **pmaciver said:**
> Okay, I need some help.

I Bought this laptop a few days ago and with the help of this thread I have got pretty much everything I want working. Not suspend and resume but that can wait for now. 

My specs are 

Acer Timeline 3810T core 2 solo
Ubuntu 9.0.4
Result of uname -a "Linux linuxbox 2.6.28-13-server #45-Ubuntu SMP Tue Jun 30 20:51:10 UTC 2009 i686 GNU/Linux"

My problem is that whenever I use a video media player, say for instance mplayer or vlc, they are fine playing at the default resolution for that video, as soon as I maximise or move the original video around the screen with any sort of pace, my gnome session shows a few crazy colors (like the number of colors has gone down) and then blows up and restarts at the login. 

I have tried various things. Using Gnome, xfce, fluxbox, but still the same result.

I renamed my home directory and created a fresh one just to see if that had anything to do with it same result.

I can't even ctrl-alt-f[1-8] to a console because it does this freezing thing until I come back to the f7 console.

It has only happened when I use video, I have gone crazy with compiz doing the effect where you zoom in and out to show all desktops and all sorts of things that will put the processor under stress but that didn't cause the problem to happen.

So, before I drive myself crazy does anyone know why this might be happening? Maybe the server Kernel perhaps? Not sure. I am going to give the generic kernel a try and see if that changes anything, although I won't have my 4 GB of RAM available to me. 

Anyway, like I said, anyone can shed some light on this I would love to hear it. In the mean time I will try the generic kernel and see what that does.

Thanks

---

### Post by The Tronyx on 2009-07-13
Hello Pmaciver,

The first thing to do would be to boot into the right kernel if you want suspend.  If you do not care about suspend...Well I am not sure to be honest.  You can install a 64 bit OS which will recognize the 4G of RAM or you can try and enable PAE in the kernel.  Ideally, we would be able to get you into the 2.6.30 kernel (Suspend works in this kernel) as well as having the OS recognize the 4G of RAM.  Unfortunately I have never dealt with PAE or 4G of RAM on Ubuntu so I cannot really advise on that one =/

If you were to go with the 64 bit Ubuntu install, you can get the 4G of RAM as well as suspend functionality you would want the below.

```

$ wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630-generic_2.6.30-020630_amd64.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630_2.6.30-020630_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-image-2.6.30-020630-generic_2.6.30-020630_amd64.deb
$ sudo dpkg -i linux-headers-2.6.30-020630-generic_2.6.30-020630_amd64.deb linux-headers-2.6.30-020630_2.6.30-020630_all.deb linux-image-2.6.30-020630-generic_2.6.30-020630_amd64.deb

```

---

### Post by pmaciver on 2009-07-13
Thanks.

I may give this a go tomorrow, if I can remember what turned me away from 64 bit kernels in the first place and if the reason is still valid.

Thanks again.

> **2point0 said:**
> Hello Pmaciver,

The first thing to do would be to boot into the right kernel if you want suspend.  If you do not care about suspend...Well I am not sure to be honest.  You can install a 64 bit OS which will recognize the 4G of RAM or you can try and enable PAE in the kernel.  Ideally, we would be able to get you into the 2.6.30 kernel (Suspend works in this kernel) as well as having the OS recognize the 4G of RAM.  Unfortunately I have never dealt with PAE or 4G of RAM on Ubuntu so I cannot really advise on that one =/

If you were to go with the 64 bit Ubuntu install, you can get the 4G of RAM as well as suspend functionality you would want the below.

```

$ wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630-generic_2.6.30-020630_amd64.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630_2.6.30-020630_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-image-2.6.30-020630-generic_2.6.30-020630_amd64.deb
$ sudo dpkg -i linux-headers-2.6.30-020630-generic_2.6.30-020630_amd64.deb linux-headers-2.6.30-020630_2.6.30-020630_all.deb linux-image-2.6.30-020630-generic_2.6.30-020630_amd64.deb

```

---

### Post by cyberfish on 2009-07-14
I just installed 9.10 alpha 2 on my 3810t (Intel SSD version), and almost everything I tested worked out of the box - SATA (AHCI mode), LAN, WLAN, sound, FN (only brightness tested), video (INCLUDING external display - just connect and go System -> Pref -> Display, automatically detected and works amazingly), enabling and disabling touchpad (yes, I can disable it and re-enable it and disable it... all I want). 

I installed it alongside Vista (12GB vista recovery, ~30GB vista, ~35GB 9.10). Had to do "sudo apt-get update; sudo apt-get install ubiquity ubiquity-frontend-gtk ubiquity-ubuntu-artwork" inside the Live CD environment as per the instructions here - [https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/385995](https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/385995) to install GRUB 2. After that the installation worked smoothly.

My only problem right now is resuming from suspend. It powers off instead. I've tried both the 2.6.30 and 2.6.31 kernels in the 9.10 repository, and both 1.04 and 1.08 BIOSes.

Any ideas?

Battery is also a little short compared to Vista (Ubuntu says 6:30 on full charge), but I think I wasn't comparing at equal screen brightness, and I have no idea if Ubuntu's estimation is accurate (didn't actually time it). But that's of a bit lesser concern for me.

At least it's good to know that our laptops will work (at least almost) out of the box when October comes around :).

EDIT: btw, I installed using my USB drive (unetbootin).

---

### Post by norkakn on 2009-07-14
> **gotosk said:**
> 
How can I update my BIOS under Ubuntu? BIOS file on Acer website are executable file for Windows. For updating, I think I should run into DOS first, and use a usb stick, run flash.bat. Oops,It's a lot work to do... -_-


[http://www.netbooktech.com/tag/acer-aspire-one-bios-update-instructions/](http://www.netbooktech.com/tag/acer-aspire-one-bios-update-instructions/)

Except use the proper BIOS update.  Make sure to select "Live CD Only"

---

### Post by cyberfish on 2009-07-17
I have being trying to get resume from suspend work for the last few days (unloading various modules) without success. There's no any mentioning of the failed resumes either in /var/log/kern.log.

I don't really want to switch to 9.04, though. Since everything else just works so perfectly with 9.10, and I don't even know if the resume issue is fixed in 9.04.

---

### Post by KariV on 2009-07-17
I am running Ubuntu 9.04 64bit version (dual-boot with Vista) on 3810t Core 2 Solo with BIOS 1.08 and the main problem remaining is the shutdown when trying to resume from suspend (hibernation works). I had to use the kernel option libata.force=noncq to be able to boot to the Linux. KVM also complains during the boot that support for it is disable from BIOS. Battery life in Ubuntu under light load with everything in powersave mode was ~6.5 hours and in Vista 32bit >8 hours. I got everything else working in Jaunty with a little tweaking and in Vista everything works out of the box.

The resume from suspend not working is very annoying because the wakeup from hibernation takes much longer. Hopefully we can find the solution to it soon. Apart from that I am a happy owner.

Kari

---

### Post by cyberfish on 2009-07-17
> **KariV said:**
> I am running Ubuntu 9.04 64bit version (dual-boot with Vista) on 3810t Core 2 Solo with BIOS 1.08 and the main problem remaining is the shutdown when trying to resume from suspend (hibernation works). I had to use the kernel option libata.force=noncq to be able to boot to the Linux. KVM also complains during the boot that support for it is disable from BIOS. Battery life in Ubuntu under light load with everything in powersave mode was ~6.5 hours and in Vista 32bit >8 hours. I got everything else working in Jaunty with a little tweaking and in Vista everything works out of the box.

The resume from suspend not working is very annoying because the wakeup from hibernation takes much longer. Hopefully we can find the solution to it soon. Apart from that I am a happy owner.

Kari

Using 9.10 (32-bit) I don't need to add any special boot parameters (and AHCI works out of box, for both installation and running)

As for battery life, have you tried powertop? It tells you your current power consumption. I was able to get it down to about 9W, with wifi on and LCD at 30% brightness. Powertop estimates a battery life of 7.5 hours. wifi power saving mode matters (saves about 2W) - ```
sudo iwconfig wlan0 power on
```

I haven't tried hibernation... but it could be a possible solution for me, since I have the Intel SSD version, and resume from hibernation should be fast (2GB/250MB/s = 8 seconds). That will have to do until a solution for resume from suspend is found. Hopefully a solution will be found by September, when I will be bringing this laptop to school...

---

### Post by KariV on 2009-07-17
> **cyberfish said:**
> 
As for battery life, have you tried powertop? It tells you your current power consumption. I was able to get it down to about 9W, with wifi on and LCD at 30% brightness. 


Yep, I used powertop to enable the powersave mode for different components. I was able to get the power consumption down to <8W when I turned bluetooth off (Fn+F3) with wifi on. Screen brightness doesn't seem to affect the powertop number very much when using the dimmer modes. However, the power consumption goes up couple of Watts during normal web browsing. 

Btw, is there a physical kill switch for wifi similar to bluetooth Fn+F3? Currently I have to use the network applet to switch it off.

Kari

---

### Post by cyberfish on 2009-07-17
> **KariV said:**
> Yep, I used powertop to enable the powersave mode for different components. I was able to get the power consumption down to <8W when I turned bluetooth off (Fn+F3) with wifi on. Screen brightness doesn't seem to affect the powertop number very much when using the dimmer modes. However, the power consumption goes up couple of Watts during normal web browsing. 

Btw, is there a physical kill switch for wifi similar to bluetooth Fn+F3? Currently I have to use the network applet to switch it off.

Kari

Yes, the wifi indicator light is also a "touch switch". Took me quite a while to figure out (so is the battery leaf thing, for power saving mode, but it doesn't seem to affect Linux, so probably software based). I find changing screen brightness from 100% to 0% saves about 2.5W (but the backlight wobbles at 0%, and slightly at 20%).

I just tried out hibernation on my machine. Hibernate takes about 16 seconds, and wakeup about 8.

BTW, disabling compiz seems to help ever so slightly, too (~0.5W). EDIT: NOPE, not true, seems like the power consumption drops slightly when the system is left idle for a while. I was seeing that. Same power consumption with compiz on.

---

### Post by federa on 2009-07-17
hi!
here's my uname -a

Linux federacchia-mobile 2.6.30-020630-generic #020630 SMP Wed Jun 10 09:45:40 UTC 2009 i686 GNU/Linux

anyway: other "problems"...it seems that HDD spin too much...they goes warm after very little time!
also with kernel 2.6.30 suspend doesn't work. I could not install new bios..i've completely removed windows from my hd!!
nobody could develop a brand new kernel for this acer?? (my acer is 3810t with core 2 duo processor, but, in my opinion, the 4810t wouldn't be so different!)

question: is it possible to regulate with hdparm the rotation speed of HDD?? anyone knows?

thanks guys!!

---

### Post by cyberfish on 2009-07-17
Updating BIOS doesn't help with suspend. I have tried all their BIOSes. We don't even know what the problem is now.

As for HD, you can try to get it to spin down (try Google). It introduces a noticeable lag for spinning up, though. There's no way to set rotational speed.

---

### Post by Bateluer on 2009-07-17
Whats the verdict on the Timeline series for Linux compatibility? This long thread makes it seem like a crapshoot.

I'm interested in the upcoming 1810T, or possibly the 3810T if I find it for a good price, but I would like to use Ubuntu or Mint on it.

---

### Post by cyberfish on 2009-07-17
With 9.10 alpha 2, everything I have tested worked out of the box, except for waking up from suspend. It shuts down instead. There's no known fix for that at the moment.

For 9.04, you need to install the LAN driver manually, and some say the touchpad enable/disable button only work the first time (I can confirm it to be fixed in 9.10).

Also, battery life seems to be slightly less under Linux. ~8 hrs vs ~10 hrs, as reported by the OS anyways.

---

### Post by cyberfish on 2009-07-18
In single user (recovery) mode, I've tried unloading just about all modules (the sound modules can't be unloaded for some reason), and then suspend. Still doesn't work. I am out of things to try now.

---

### Post by federa on 2009-07-18
@Bateluer: i've installed ubuntu 9.04 32 bit and everything was perfect. the only one things that don't work is the resume after suspend.

with ubuntu 9.04 64 bit something did not work correctly, after few minute after installation the system crashed! (i've tried to reinstall the OS many times before install the 32 bit version).

---

### Post by Bateluer on 2009-07-18
> **federa said:**
> @Bateluer: i've installed ubuntu 9.04 32 bit and everything was perfect. the only one things that don't work is the resume after suspend.


Which usually never works under Windows either. Thanks for ther response.

---

### Post by raduvaleriu on 2009-07-22
Hello

I have an Acer Timeline 3810T laptop (Intel Core 2 Solo, Intel GMaA 4500MHD, 4GB DDR3, 500GB HDD) and I installed Ubuntu 9.04.

Everything works ok. The only thing is that it gets a lot hotter than when running Windows on it, and the coolers work almost all the time. I think this is because it runs at full power all the time.

Is there something in Gnome like the Power Plan selector from Windows? That would allow me to select profiles like "power saver", "balanced" etc? Profiles that would make changes to the CPU Frequency, HDD park etc not only to screen brightness or sleep interval. I think that KDE has something like Power Profile or something like that).

Thank you
I am a beginner in Linux so please bare with me.
Thank you

---

### Post by avilella on 2009-07-23
This looks like an issue with the cpu frequency. Some people suggested updating the BIOS as a solution...

> **raduvaleriu said:**
> Hello

I have an Acer Timeline 3810T laptop (Intel Core 2 Solo, Intel GMaA 4500MHD, 4GB DDR3, 500GB HDD) and I installed Ubuntu 9.04.

Everything works ok. The only thing is that it gets a lot hotter than when running Windows on it, and the coolers work almost all the time. I think this is because it runs at full power all the time.

Is there something in Gnome like the Power Plan selector from Windows? That would allow me to select profiles like "power saver", "balanced" etc? Profiles that would make changes to the CPU Frequency, HDD park etc not only to screen brightness or sleep interval. I think that KDE has something like Power Profile or something like that).

Thank you
I am a beginner in Linux so please bare with me.
Thank you

---

### Post by cyberfish on 2009-07-23
> **raduvaleriu said:**
> Hello

I have an Acer Timeline 3810T laptop (Intel Core 2 Solo, Intel GMaA 4500MHD, 4GB DDR3, 500GB HDD) and I installed Ubuntu 9.04.

Everything works ok. The only thing is that it gets a lot hotter than when running Windows on it, and the coolers work almost all the time. I think this is because it runs at full power all the time.

Is there something in Gnome like the Power Plan selector from Windows? That would allow me to select profiles like "power saver", "balanced" etc? Profiles that would make changes to the CPU Frequency, HDD park etc not only to screen brightness or sleep interval. I think that KDE has something like Power Profile or something like that).

Thank you
I am a beginner in Linux so please bare with me.
Thank you

Install the CPU Frequency Governor (or something to that effect) taskbar applet. You'll get a few options to choose from (powersave, performance, conservative, ondemand) for CPU dynamic clock changing.

---

### Post by almozavr on 2009-07-23
Installed 9.10 Netbook Remix with linux kernel 2.6.31 BUT still can't load with AHCI hdd mode.

So, does anyone know issue? Suggestion with new kernel installation isn't working as you see...

---

### Post by cyberfish on 2009-07-23
Has anyone tried a different harddrive to eliminate the problem?

I can confirm that the Intel SSD version does NOT have this problem (I can use AHCI without any kernel parameters).

---

### Post by almozavr on 2009-07-23
Using another type of hdd is NOT the solution!

So WHAT is the solution for AHCI problem?

---

### Post by cyberfish on 2009-07-23
It's not the solution, but can aid us in coming up with a solution. The first step of coming up with a solution is to find where the problem is.

If you are too lazy to find (or helping to find) a solution and just want other people to do it for you, the answer is THERE IS NO SOLUTION RIGHT NOW.

---

### Post by miegiel on 2009-07-23
> **almozavr said:**
> Installed 9.10 Netbook Remix with linux kernel 2.6.31 BUT still can't load with AHCI hdd mode.

So, does anyone know issue? Suggestion with new kernel installation isn't working as you see...

> **almozavr said:**
> Using another type of hdd is NOT the solution!

So WHAT is the solution for AHCI problem?

Try kernel 2.6.30 instead of kernel 2.6.31, some people said their AHCI issues went away using that kernel.

Can you list the brand, model and size of the disks you tried, different timelines have different disks you know ;) and it's impossible to know what other disk(s) you tried.

---

### Post by almozavr on 2009-07-23
Surely, I'll try 2.6.30! Hope this would help. :cool:

My 3810T uses Hitachi hdd, works fine. But, are you sure that AHCI is hdd function? I thought it's from chipset...

Anyway thanks for help, now it's time to try :D

---

### Post by miegiel on 2009-07-23
> **almozavr said:**
> Surely, I'll try 2.6.30! Hope this would help. :cool:

My 3810T uses Hitachi hdd, works fine. But, are you sure that AHCI is hdd function? I thought it's from chipset...

Anyway thanks for help, now it's time to try :D

Sure, it's on the chipset too. Like sata is on the chipset and the hdd ;)

---

### Post by almozavr on 2009-07-23
Still no luck with AHCI! :(
Installing 2.6.30 Kernel or adding libata.noacpi=1 didn't helped at all...

I'm still wondering what to do...

---

### Post by miegiel on 2009-07-23
> **almozavr said:**
> Still no luck with AHCI! :(
Installing 2.6.30 Kernel or adding libata.noacpi=1 didn't helped at all...

I'm still wondering what to do...

A common mistake, [_AHCI_]("http://en.wikipedia.org/wiki/AHCI") is not [_ACPI_]("http://en.wikipedia.org/wiki/ACPI").

If you want to turn off AHCI you can do that in the BIOS (set to IDE mode). Running in IDE mode will decrease disk performance a bit, but at least you have a functional laptop till the AHCI issue is sorted.

Oh, you might want to check what version your BIOS is. Acer released a new BIOSes for the timelines that fix some bugs (though I think they had to do with power management, read ACPI :twisted:)

I was reading a bit to prepare installing ubuntu on my 3810T 944G32N (I hope it arrives tomorrow, but it will probably be monday or tuesday) and I found these 2 pages which link back to the (more) relevant posts in this thread.

[https://launchpad.net/~acertimeline](https://launchpad.net/~acertimeline)
[http://linux-macbook-air-killers.blogspot.com/2009/05/new-linux-and-acer-aspire-timeline.html](http://linux-macbook-air-killers.blogspot.com/2009/05/new-linux-and-acer-aspire-timeline.html)

---

### Post by almozavr on 2009-07-24
Ok, now we've got a working issue with AHCI problem!!! :D

The solution is adding to kernel string "libata.force=noncq" (could be done by editing /boot/grub/menu.lst file). This disables NCQ hdd mode but working fine on my 3810T in AHCI mode. 
Besides, some guys advised to install 2.6.30 kernel but it didn't worked for me (no matter what: 2.6.28, 2.6.30 or 2.6.31). Also there was a solution by editing initramfs, but it had no results for me too ((

So, just add libata.force=noncq to kernel string!

This solution was tested on Jaunty and Netbook Remix, so enjoy! :)

---

### Post by antikristian on 2009-07-24
I've made a page on the Ubuntu Community Wiki:

Still a WIP, but it might make it easier for people to find out how to setup a Timeline computer. Feel free to contribute :-)

[http://help.ubuntu.com/community/AspireTimeline]("http://help.ubuntu.com/community/AspireTimeline")

---

### Post by antikristian on 2009-07-24
> **cyberfish said:**
> With 9.10 alpha 2, everything I have tested worked out of the box, except for waking up from suspend. It shuts down instead. There's no known fix for that at the moment.

Has anyone filed a bug about this?

---

### Post by avilella on 2009-07-26
Here is a report from cyberfish for Ubuntu Karmic Alpha 3:

> I just installed alpha 3 (since my alpha 2 died when my computer crashed in the middle of a apt-get upgrade), and there are still a few problems.

- with 2.6.31-3-generic, hibernate still works, and suspend still doesn't work. Still haven't found any clue as to why.
- "sudo update-grub2" is needed after installation to find the Vista partition and add it to GRUB. This is a known bug. [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/402795](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/402795)
- Intel Wireless doesn't work out of the box anymore. The problem seems to be related to RFKILL framework change in 2.6.31 ([http://www.h-online.com/open/Kernel-Log-Coming-in-2-6-31-Part-1-New-Wi-Fi-drivers-and-other-network-related-changes--/news/113670](http://www.h-online.com/open/Kernel-Log-Coming-in-2-6-31-Part-1-New-Wi-Fi-drivers-and-other-network-related-changes--/news/113670)). The RFKILL status seems to default to on (wireless disabled) on boot every time (btw, for those that don't know already, to toggle wireless, touch the wireless indication light). I have tried using the RFKILL utility found here - [http://wireless.kernel.org/en/users/Documentation/rfkill](http://wireless.kernel.org/en/users/Documentation/rfkill), to no avail. The wifi device is "hard blocked". It seems like at least HP and Asus people are having problems with their laptops, too, but I didn't investigate into that further. The problem COULD be related to the acer_wmi module.

I didn't and still don't need any special kernel parameter since I have the SSD version, so I can't say if that's "fixed".

Everything else seems to work just like in alpha 2.

[https://lists.launchpad.net/acertimeline/msg00085.html](https://lists.launchpad.net/acertimeline/msg00085.html)

---

### Post by MaXX99 on 2009-07-26
Hello All,

I installed Jaunty on my 3810T with dual core CPU and updated the kernel to 2.6.30 and the BIOS to 1.08
Almost all works well, except for the Suspend issue and I also seem to have a problem with the Cpu Frequency Scaling. Some of you reported running their systems at 800 Mhz, But unfortunately I seem to be unable to get below 1.2 Ghz; neither does it show up in the applet (yes I did try on-demand and it did not pop up).

> 
xxx@yyy:~$ sudo cpufreq-info
cpufrequtils 004: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [EMAIL="cpufreq@lists.linux.org.uk"]cpufreq@lists.linux.org.uk[/EMAIL], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 1.20 GHz - 1.40 GHz
  available frequency steps: 1.40 GHz, 1.40 GHz, 1.20 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 1.20 GHz and 1.40 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.20 GHz (asserted by call to hardware).
  cpufreq stats: 1.40 GHz:0.00%, 1.40 GHz:0.00%, 1.20 GHz:0.00%  (417)
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 1
  hardware limits: 1.20 GHz - 1.40 GHz
  available frequency steps: 1.40 GHz, 1.40 GHz, 1.20 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 1.20 GHz and 1.40 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.20 GHz (asserted by call to hardware).
  cpufreq stats: 1.40 GHz:0.00%, 1.40 GHz:0.00%, 1.20 GHz:0.00%  (448)
and

> 
xxx@yyy:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_available_frequencies
1401000 1400000 1200000 
1401000 1400000 1200000
Strange enough I seem to have a 1.401 Ghz CPU state, but no 800 mhz state ???

Does someone have a similar issue, or even better .... a solution ? :KS

Cheers ! :popcorn:

---

### Post by miegiel on 2009-07-26
> **MaXX99 said:**
> Hello All,

I installed Jaunty on my 3810T with dual core CPU and updated the kernel to 2.6.30 and the BIOS to 1.08
Almost all works well, except for the Suspend issue and I also seem to have a problem with the Cpu Frequency Scaling. Some of you reported running their systems at 800 Mhz, But unfortunately I seem to be unable to get below 1.2 Ghz; neither does it show up in the applet (yes I did try on-demand and it did not pop up).

and

Strange enough I seem to have a 1.401 Ghz CPU state, but no 800 mhz state ???

Does someone have a similar issue, or even better .... a solution ? :KS

Cheers ! :popcorn:

If you're bold enough you could try editing the */sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies* and */sys/devices/system/cpu/cpu1/cpufreq/scaling_available_frequencies* files to
```
1400000 1200000 1000000 800000
```
or
```
1400000 1200000 800000
```
On the other hand, the trick might be editing */sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq* and */sys/devices/system/cpu/cpu1/cpufreq/scaling_min_freq*.

Or, who knows, you might need to edit all 4 files.

At the moment I can't test it yet, my 3810 (with SU9400 also) should arrive tomorrow \\:D/

---

### Post by cyberfish on 2009-07-26
[quote=antikristian]
I've made a page on the Ubuntu Community Wiki:

Still a WIP, but it might make it easier for people to find out how to setup a Timeline computer. Feel free to contribute

[http://help.ubuntu.com/community/AspireTimeline](http://help.ubuntu.com/community/AspireTimeline)
[/quote]
That would be great! I'll be adding all I know.

> Has anyone filed a bug about this?
Not that I am aware of. I would do it myself... but I'm not familiar with the bug reporting system. We don't even know which package is responsible for this (probably the kernel, though).

---

### Post by cyberfish on 2009-07-26
> **miegiel said:**
> If you're bold enough you could try editing the */sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies* and */sys/devices/system/cpu/cpu1/cpufreq/scaling_available_frequencies* files to
```
1400000 1200000 1000000 800000
```
or
```
1400000 1200000 800000
```
On the other hand, the trick might be editing */sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq* and */sys/devices/system/cpu/cpu1/cpufreq/scaling_min_freq*.

Or, who knows, you might need to edit all 4 files.

At the moment I can't test it yet, my 3810 (with SU9400 also) should arrive tomorrow \\:D/

Are you sure that would be a good idea?

Both the SU3500 (which I have) and the SU9400 run on 200mhz FSB (quad-pumped to 800mhz), with a max multiplier of 7 (200x7 = 1.4ghz). As far as I have seen, the lowest multiplier any Intel CPU can do is 6, which makes 1.2ghz (200x6). To achieve anything lower than 1.2ghz, one would have to lower the FSB, which gets problematic (it's not just the CPU anymore, but also the motherboard, memory sub-system, and potentially PCI, PCI-E, since they all run on a ratio to FSB).

---

### Post by cyberfish on 2009-07-26
Suspend (resume) bug reported
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405120](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405120)

---

### Post by cyberfish on 2009-07-27
Two wifi regressions are also reported.

RFKILL switch "bug" -
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405152](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405152)

Power management not supported regression -
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405158](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405158)

---

### Post by miegiel on 2009-07-27
> **cyberfish said:**
> Are you sure that would be a good idea?
No :) hence I said: "If you are bold enough ..."

> Both the SU3500 (which I have) and the SU9400 run on 200mhz FSB (quad-pumped to 800mhz), with a max multiplier of 7 (200x7 = 1.4ghz). As far as I have seen, the lowest multiplier any Intel CPU can do is 6, which makes 1.2ghz (200x6). To achieve anything lower than 1.2ghz, one would have to lower the FSB, which gets problematic (it's not just the CPU anymore, but also the motherboard, memory sub-system, and potentially PCI, PCI-E, since they all run on a ratio to FSB).

The [_SU3500 is a single core_]("http://ark.intel.com/Product.aspx?id=37133"), you said you had a dual core !?

Anyway, I can't remember the source, but I read somewhere that the SU9400 (and I assume the SU3500 too) should clock down to 800Mhz when idle. I'll dig my way through the [_data sheet for the SU9400 and SU3500_]("http://download.intel.com/design/mobile/datashts/32012001.pdf") (and other mobile CPUs) when I have time later.

---

### Post by cyberfish on 2009-07-27
> 
The SU3500 is a single core

Yeah, the only difference between them is that one is single one is dual, and power consumption (10W TDP vs 5.5W)

> 
you said you had a dual core !?

I did?! I don't recall, but sorry about that. I have the single core.

As for clocking down to 800MHz, it would have to be either 133x6 or or 200x4. 200x4 I really don't think is possible. 133x6 COULD be potentially possible (and is possible on some desktop machines with NVIDIA chipset), but I'm not aware of any Intel powersaving technology that downclocks the FSB. SpeedStep and C1E both work on multiplier and core voltage. Would love to be proven wrong.

---

### Post by miegiel on 2009-07-27
> **cyberfish said:**
> [QUOTE=miegiel;7685429]The [_SU3500 is a single core_]("http://ark.intel.com/Product.aspx?id=37133"), you said you had a dual core !?


I did?! I don't recall, but sorry about that. I have the single core.[/QUOTE]

Sorry that was MaXX99 :rolleyes:

---

### Post by federa on 2009-07-27
@miegiel:
i've got your same "problem": no 800MHz available in cpu freq choose!!

generic question: Is it so important to update BIOS version?? waddafuck, i've completely removed windows form my box...flashbios doesn't work.. :D but everything works fine (of course, not the resuming after suspend).
almost everyone tryed to install 64 bit ubuntu version??
in my computer something goes wrong about 20 min after installation..character goes to square box and rebooting give me root (or something similar) not found.

---

### Post by PatrickVogeli on 2009-07-27
I think it's possible to get the 800MHz option. I believe reading somether some intel procs where able to lower its FSB to lower power consumption. My girlfriend has T7250 and it will scale down to 800MHz. I have a T5450 and I'm not able to go below 1GHz. No timelines, of course.

---

### Post by MaXX99 on 2009-07-27
> **miegiel said:**
> Sorry that was MaXX99 :rolleyes:

Hello Miegiel, yes I have a dualcore .... I already had a quick look through the datasheet, but could not find immediately what I was looking for and gave up (I am in the south of France on holiday and have better things on my mind right now :p)
But some extra battery life is always welcome for those long roadtrips :)

---

### Post by hefistion on 2009-07-27
Hello, first, sorry for my bad English. I have an acer 5810T timeline and everything works well in kubuntu 9.04 but two things. 
 - Controlling the screen brightness does not work with the fn key 
 - Only recognizes 3 gb of memory (I think a kernel server is fixed) 

 Tell someone how to fix the screen brightness 

 Thank you very much

---

### Post by cyberfish on 2009-07-28
Acer released BIOS v1.10 for the 3810t! (released yesterday)

But there's only a DOS version, and it doesn't seem to work under Vista. I am looking for ways around that.

---

### Post by cyberfish on 2009-07-28
Okay I flashed it using unetbootin (choose FreeDOS for distribution, boot with the vanilla option - you'll see what I mean when you boot it) on my USB drive.

Suspend still doesn't work. I haven't noticed anything different than before.

---

### Post by arvin0416 on 2009-07-28
Thanks a lot... i had a problem with my Atheros Network card driver in Ubuntu 9.04 installed in my Acer 4810t, i just follow the instructions posted by "tokyoahead" and it works... thanks so much...

---

### Post by cyberfish on 2009-07-28
Yours has an Atheros card?... how come all ours have Intel cards?

EDIT: Ah, sorry. I thought you meant wireless :).

---

### Post by miegiel on 2009-07-29
In response to [https://help.ubuntu.com/community/AspireTimeline/Fixes](https://help.ubuntu.com/community/AspireTimeline/Fixes)
> Switch SATA mode from AHCI to IDE

Enter the BIOS and change the SATA mode from AHCI to IDE. (Feel free to write this process down in more detail if you like)

Issues

    * Changing mode to IDE will prevent you from dual booting into Vista
    * NCQ is disabled (does the disk have NCQ?) 

The [_320GB Hitachi Travelstar 5K500.B_]("http://www.hitachigst.com/portal/site/en/products/travelstar/5K500.B/") (that came in my timeline) doesn't support NCQ. Hitachi's data sheet doesn't mention NCQ at all (marketing rule 27.2 : Don't mention anything the product doesn't support) and [_this web shop_]("http://www.scan.co.uk/Products/320GB-Hitachi-HTS545032B9A300-Travelstar-5K500B-25-SATA-3Gb-s-5400rpm-8MB-Cache-12-ms") (click *Technical Specs*) puts a pretty [color=red]**X**[/color] behind NCQ.

Besides NCQ, AHCI also supports hotswapping hard disks, but that's pretty useless in a laptop. It seems to me that disabling AHCI has no real disadvantage in these acers, till you upgrade your disk anyway ;)

Oh, almost forgot, some of the timelines have westerndigital HDD's. I didn't research those since I don't know the exact model :twisted:

If anyone has any thoughts on this or can post her/his WD disks NCQ abillities (or lack there off) please do.

**ps** win7 gave a BSOD with AHCI enabled.

---

### Post by teeepeli on 2009-07-29
I bought Acer Travelmate 8371, it's kind of a business version of the 3810t with matte screen and fingerprint reader.
HDD in this one is 250GB Toshiba MK2555GSX and it supports NCQ and Karmic is running fine in this with AHCI enabled.

So far only problems i have are that the wireless power saving can't be enabled and suspend doesn't work (i have even upgraded bios to 1.10).

Fingerprint reader is made by Egistec and model is probably [SS801U]("http://www.egistec.com/sensors/fingerprint-ss801u.html") which should be supported by [Egistecs BioExcess Linux]("http://www.egistec.com/products/bioexcess-linux.html") software.

> The biometric software needs to be used with specific branded sensor. Therefore, our company provides BioExcess mainly to OEM companies, who then incorporates it into their products. And currently, the BioExcess Linux Edition is still not available for download on our website. 

---

### Post by cyberfish on 2009-07-29
> **teeepeli said:**
> I bought Acer Travelmate 8371, it's kind of a business version of the 3810t with matte screen and fingerprint reader.
HDD in this one is 250GB Toshiba MK2555GSX and it supports NCQ and Karmic is running fine in this with AHCI enabled.

So far only problems i have are that the wireless power saving can't be enabled and suspend doesn't work (i have even upgraded bios to 1.10).

Fingerprint reader is made by Egistec and model is probably [SS801U]("http://www.egistec.com/sensors/fingerprint-ss801u.html") which should be supported by [Egistecs BioExcess Linux]("http://www.egistec.com/products/bioexcess-linux.html") software.

Both problems are known (but no known fix). If you really need the extra battery life now, I suggest downgrading to 2.6.30 (which, IIRC, does support power saving). 

As for fingerprint reader, have you looked at the fprint project? It seems to support quite a few fingerprint readers last time I checked. The program (and biometric authentication in general with Linux) is far from mature, yet, though. My last laptop (HP tx2000) had a fingerprint reader, and I got it to work with fprint, but I ended up using plain old password login anyways. It's too unreliable. Fingerprint authentication doesn't offer any more security than plain old password authentication anyways. It's just a convenience thing. The machine itself is full of your fingerprints :).

---

### Post by miegiel on 2009-07-29
> **teeepeli said:**
> I bought Acer Travelmate 8371, it's kind of a business version of the 3810t with matte screen and fingerprint reader.
HDD in this one is 250GB Toshiba MK2555GSX and it supports NCQ and Karmic is running fine in this with AHCI enabled.

...

That seems to confirm my suspicion that the AHCI issue is caused by the lack off NCQ support on the hard disks. Since **cyberfish** already reported :

> **cyberfish said:**
> Has anyone tried a different harddrive to eliminate the problem?

I can confirm that the Intel SSD version does NOT have this problem (I can use AHCI without any kernel parameters).

Despite lacking a spinning disk intel's SSD's do support NCQ :D

---

### Post by cyberfish on 2009-07-29
Ah, so it's problem with the SATA driver, since it can't correctly detect the lack of NCQ through negotiating with the device.

Anyone care to file a bug report? (I don't have the problem myself, so not me this time :))

It's probably not 3810t-specific, though. Tons of laptops use this chipset. But I'm surprised the problem has not been fixed yet (the chipset has been out for a year already, and Intel is usually pretty good at making good Linux drivers).

EDIT: Actually, on a second thought, it could be the Hitachi harddrive that's falsely claiming support for NCQ. We'll need another drive that DOESN'T support NCQ to be sure.

---

### Post by miegiel on 2009-07-29
> **cyberfish said:**
> EDIT: Actually, on a second thought, it could be the Hitachi harddrive that's falsely claiming support for NCQ. We'll need another drive that DOESN'T support NCQ to be sure.

Win7 also treats you on a BSOD during boot up if AHCI is enabled in the BIOS. Though vista didn't have any issues, I wouldn't put it past acer to mod NCQ or AHCI out of their version of vista. At the moment I'm inclined to blame the disk, after all, it's a hitachi :twisted:

---

### Post by xir_ on 2009-07-29
anyone know why the 4810t has a BIOS revision number 1.20 and the 3810t has a revision of 1.10.

anyone know if is there any key difference between the two?

---

### Post by muadnu on 2009-07-29
Sorry if this was already answered in the thread, but I couldn't find it.

I have a 3810T and cannot get the ethernet to work. With  the 2.28 kernel I tried the trick suggested in the first post, but didn't work. After installing the generic 2.30 kernel, I tried again, but now I can't even build the driver:
```
$ make
make -C /lib/modules/2.6.30-020630-generic/build SUBDIRS=/home/dani/Download/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.30-020630-generic'
  CC [M]  /home/dani/Download/src/at_common_main.o
  CC [M]  /home/dani/Download/src/atl1e_main.o
/home/dani/Download/src/atl1e_main.c: In function ‘atl1e_request_irq’:
/home/dani/Download/src/atl1e_main.c:156: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
  CC [M]  /home/dani/Download/src/atl1c_main.o
/home/dani/Download/src/atl1c_main.c: In function ‘atl1c_intr’:
/home/dani/Download/src/atl1c_main.c:1640: error: expected expression before ‘;’ token
/home/dani/Download/src/atl1c_main.c:1654: error: expected expression before ‘;’ token
/home/dani/Download/src/atl1c_main.c:1678: error: expected expression before ‘;’ token
/home/dani/Download/src/atl1c_main.c:1708: warning: ‘return’ with a value, in function returning void
/home/dani/Download/src/atl1c_main.c: In function ‘atl1c_request_irq’:
/home/dani/Download/src/atl1c_main.c:2350: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
make[2]: *** [/home/dani/Download/src/atl1c_main.o] Error 1
make[1]: *** [_module_/home/dani/Download/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.30-020630-generic'
make: *** [default] Error 2

```

I'm not really sure what's going on...

---

### Post by cyberfish on 2009-07-29
With 2.6.30, you shouldn't need to build your own driver. The kernel includes it.

---

### Post by muadnu on 2009-07-29
> **cyberfish said:**
> With 2.6.30, you shouldn't need to build your own driver. The kernel includes it.

That's what I thought. but it didn't work... Maybe I need to remove the driver I built with 2.6.28? In which case, how should I do that?

---

### Post by serinox on 2009-07-29
All-righty people I read the whole thread and didn't see answers to these questions so if someone could point me in the right direction I'd very much appreciate it. 

[LIST=1]
[*]The microphone doesn't pick up sound. I've tried both 2.6.28 and 2.6.30 and made sure everything was turned up in alsamixer and the gnome mixer (on all reported devices, theres a couple in the drop-down list). is there something else i can check?
[*]the ethernet does not seem to work in 2.6.30 x86_64. and I could not build the driver from source against that version. I could however build it for the 2.6.28 kernel.
[*]The reported amount of ram in the System Monitor applet is 3.7 gigs. which is somewhat sort of the 4 gigs I have installed.
[*]And the last thing which kinda comes and goes is that the gnome battery panel app thingy and powertop both seem to be unable to read the battery state until I unplug the power cord. this seems to "enable" it for the lack of a better description.
[/LIST]

The full model name is 3810t-6415

And here's my uname -a in case its useful
```
Linux Ygdrasil 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 01:19:55 UTC 2009 x86_64 GNU/Linux
```

---

### Post by miegiel on 2009-07-29
> **serinox said:**
> All-righty people I read the whole thread and didn't see answers to these questions so if someone could point me in the right direction I'd very much appreciate it. 

[LIST=1]
[*]The microphone doesn't pick up sound. I've tried both 2.6.28 and 2.6.30 and made sure everything was turned up in alsamixer and the gnome mixer (on all reported devices, theres a couple in the drop-down list). is there something else i can check?
[*]the ethernet does not seem to work in 2.6.30 x86_64. and I could not build the driver from source against that version. I could however build it for the 2.6.28 kernel.
[*]The reported amount of ram in the System Monitor applet is 3.7 gigs. which is somewhat sort of the 4 gigs I have installed.
[*]And the last thing which kinda comes and goes is that the gnome battery panel app thingy and powertop both seem to be unable to read the battery state until I unplug the power cord. this seems to "enable" it for the lack of a better description.
[/LIST]

[LIST=1]
[*]Check the volume control and make sure the right mic is selected (you have 2 mic inputs, 1 above the screen and a 2nd you can plug in).
[*]I didn't bother with jaunty and went straight for karmic :) LAN works fine there.
[*]Your onboard intel graphics is stealing some of your system memory because it's got no memory of it's own.
[*]Seems to have issues in keramic too, but I didn't give it much attention yet. The icon says 0.0%, but if I click it I get the correct charge in the info window.
[/LIST]
Regarding the battery tray icon: It seems dysfunctional when I boot up with the power connected. When I boot on battery power it seems to work as it should.

---

### Post by miegiel on 2009-07-29
> **xir_ said:**
> anyone know why the 4810t has a BIOS revision number 1.20 and the 3810t has a revision of 1.10.

anyone know if is there any key difference between the two?

Maybe you can find some inspiration in the BIOS release notes.

---

### Post by serinox on 2009-07-29
> **miegiel said:**
> [LIST=1]
[*]Check the volume control and make sure the right mic is selected (you have 2 mic inputs, 1 above the screen and a 2nd you can plug in).
[*]I didn't bother with jaunty and went straight for karmic :) LAN works fine there.
[*]Your onboard intel graphics is stealing some of your system memory because it's got no memory of it's own.
[*]Seems to have issues in keramic too, but I didn't give it much atention yet. The icon says 0.0%, but if I klick it I get the correct charge in the info window.
[/LIST]

I'm testing it in audacity, I have all the microphones as high as they'll go in the gnome monitor and I still get nothing in audacity no matter what I set the input source to be.

I just installed 2.6.30 on jaunty. where can I can the karmic alpha/beta?

300-400 mb seems like a heck of a lot of ram for an on-board card to be using. any place to see how much memory its keeping for itself. 

and the battery icon thing seems to be more complicated than I though. if i run the battery down a bit the battery app works *UNTIL* the battery is fully charged then the light on the from turns blue and at that moment it stops being able to talk to the batter. maybe its some sorta hardware function to prevent overcharging the battery?

EDIT: I've watched it do this "light turns blue/applet stops working" thing several times now and it happens every time so far.

---

### Post by miegiel on 2009-07-29
> **serinox said:**
> ...

I just installed 2.6.30 on jaunty. where can I can the karmic alpha/beta?

...

About 9.10
[http://www.ubuntu.com/testing/karmic/alpha3](http://www.ubuntu.com/testing/karmic/alpha3)

get 9.10
[http://cdimage.ubuntu.com/releases/karmic/alpha-3/](http://cdimage.ubuntu.com/releases/karmic/alpha-3/)

KarmicReleaseSchedule
[https://wiki.ubuntu.com/KarmicReleaseSchedule](https://wiki.ubuntu.com/KarmicReleaseSchedule)

**ps** Karmic still has bugs that might put you off more then the issues you have with jaunty and the new grub can kill your older ubuntu if you decide to dual boot. I suggest you read the "about" info and the karmic threads before you try it :twisted:

---

### Post by serinox on 2009-07-29
> **miegiel said:**
> About 9.10
[http://www.ubuntu.com/testing/karmic/alpha3](http://www.ubuntu.com/testing/karmic/alpha3)

get 9.10
[http://cdimage.ubuntu.com/releases/karmic/alpha-3/](http://cdimage.ubuntu.com/releases/karmic/alpha-3/)

KarmicReleaseSchedule
[https://wiki.ubuntu.com/KarmicReleaseSchedule](https://wiki.ubuntu.com/KarmicReleaseSchedule)

**ps** Karmic still has bugs that might put you off more then the issues you have with jaunty and the new grub can kill your older ubuntu if you decide to dual boot. I suggest you read the "about" info and the karmic threads before you try it :twisted:


Thanks for the warnings. From a first glance it looks like karmic is a no go due to dual booting issues with vista ( i need vista for school :( )

---

### Post by cyberfish on 2009-07-30
Just do a "sudo update-grub2" after installation. It will make your Vista appear again.

---

### Post by cyberfish on 2009-07-30
For the suspend problem, I tried removing all modules again, and documented it this time. Still doesn't work, though.

I used these commands (after booting into single user mode) -
modprobe -r atl1c uvcvideo serio_raw pcspkr psmouse acer_wmi iwlagn snd_seq_midi snd_seq_oss snd_seq_dummy
modprobe -r joydev lp parport arc4 ecb snd_hda_intel snd_pcm_oss
modprobe -r snd_hda_codec_intelhdmi snd_hda_codec_realtek

to remove all the modules that aren't depended on.

And here's the list of modules left -
Module                  Size  Used by
fbcon                  36512  70 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5308  1 fbcon
softcursor              1756  1 bitblit
i915                  211496  1 
drm                   159136  1 i915
i2c_algo_bit            5760  1 i915
video                  19092  1 i915
output                  2780  1 video
intel_agp              26556  1 
agpgart                34988  2 drm,intel_agp

This suggests that the problem is in either these modules, or the kernel itself.

---

### Post by alvinator@ on 2009-07-30
Hello Cyberfish, I received your Personal Message. My post in #86 solves most of the problem and I have been using ubuntu ever since I got it. Here's the complete specs of my Timeline: 

Model: Acer TImeline 4810T-352G25Mn 
CPU: 1.4Ghz Intel Core 2 Solo SU3500
Memory: 2GB DDR3 RAM
Video: Intel GMA 4500MHD
Sound: Intel HDA ALC269
HDD: WDC WDC2500BEVT-22ZCT0 250GB 
WLAN: Intel Wifi Link 5100 AGN 
LAN: Atheros AR8131 PCI-E Gigabit Ethernet 
 
Mine came with BIOS 1.10 and I experienced the 100% CPU problem even in linux. Flashing it to 1.20 fixed the problem. I bought this one in Philippines so I think it is similar to the ones available in Singapore. I believe Acer have been releasing Acer Timelines with different parts manufacturers. 

My Kernel:
> Linux timeline 2.6.30-020630-generic #020630 SMP Wed Jun 10 09:45:40 UTC 2009 i686 GNU/LinuxCheers!

---

### Post by cyberfish on 2009-07-30
Many thanks for your help!

The only thing that are different seem to be the Western Digital harddrive (many other people have Hitachi), but I have the Intel SSD and have the problem, too...

Just to confirm, suspend (to RAM, power button blinking) and resuming works for you?

---

### Post by alvinator@ on 2009-07-30
Yes, I just did a Suspend to RAM. Hibernate works fine also. I don't have any special packages on my Ubuntu Jaunty but I do have my BIOS HDD setting of IDE instead of AHCI. Updating to PPA kernel solves the AHCI problem and I can boot to ubuntu with AHCI on but my Windows 7 RC won't and it gives me a blue screen (probably because I installed Win7 when it was set to IDE mode).

---

### Post by csipuka on 2009-07-30
> **serinox said:**
> All-righty people I read the whole thread and didn't see answers to these questions so if someone could point me in the right direction I'd very much appreciate it. 

The microphone doesn't pick up sound. I've tried both 2.6.28 and 2.6.30 and made sure everything was turned up in alsamixer and the gnome mixer (on all reported devices, theres a couple in the drop-down list). is there something else i can check?

My microphone also not worked out of box, so I have upgraded alsa (did not help), and I have found somewhere an article, that there is a connection between mircophone and another device.
In the mixer, makes visible all device, and unmute the "new" devices. The name of it was strange and I cannot remember, something like EA2323. Originally it is not provided to adjust.
I do not know whether only this swith on makes my microphone live with the new alsa, or it would work on the original alsa.
Currently I have a useable microphone, and I can use it in skype.
I hope it help.
Csipu

---

### Post by muadnu on 2009-07-30
> **cyberfish said:**
> With 2.6.30, you shouldn't need to build your own driver. The kernel includes it.
I removed the driver I had built but still no lan (I'm running 2.6.30). I'm not sure what to do next.

And on a different matter, I cannot get dual monitors to work. When I configure it through system->preferences->display, I get a working configuration but desktop effects cannot be enabled. And furthermore, I need to be able to restart with or without my external monitor attached and have Ubuntu recognize this automatically. I just switched from a laptop with an Nvidia card, which did this automatically, but I'm not sure how to do it without nvidia-settings.

I tried tokyoahead's suggestion on the first post, but I get mirrored screens and moreover my laptop screen appears very dark.

---

### Post by cyberfish on 2009-07-31
> 
Yes, I just did a Suspend to RAM. Hibernate works fine also. I don't have any special packages on my Ubuntu Jaunty but I do have my BIOS HDD setting of IDE instead of AHCI. Updating to PPA kernel solves the AHCI problem and I can boot to ubuntu with AHCI on but my Windows 7 RC won't and it gives me a blue screen (probably because I installed Win7 when it was set to IDE mode).

Thanks for the help. Still not working, though :(. The only thing different between our setups now seems to be the BIOS. There's a remote chance that flashing a 3810t with a 4810t BIOS will fix it, since they have very similar hardware... but I am pretty sure I don't want to do that (AND I'M NOT SUGGESTING ANYONE TO TRY IT, AS IT WILL PROBABLY BRICK THE MACHINE). 

So I guess we just have to wait now, for 1) Acer to release a new BIOS or 2) anything to happen on the bug reports.

I have already contacted the author of acer_wmi, and he said it (the suspend problem) has nothing to do with the module, and suggests we contact the kernel ACPI people instead.

---

### Post by Dave_N on 2009-08-01
Hi. 

I am seriously considering the purchase of a 13.3 Acer Timeline. I have read the wiki and this whole thread. Could someone confirm my understanding of the "best" way to install Linux on this machine 

1.) Acquire laptop.
2) Flash latest bios from Acer and burn LiveCD of Ubuntu; jaunty 64 bit or karmic 64 bit alpha 2/3 correct?
3) Install from live CD. Do most people reformat or leave windows install for future bios?
4) Install the fixes from the wiki especially the 2.6.30 kernel.
5.) Enjoy

Now I have a question about virtualization:
Has anyone tried to get a virtualization solution going? I have a couple of apps that I need for work and I also run quicken. Ideally, I would like to run linux as the primary os and a virtual machine for quicken and the work apps. Is this asking too much of the core 2 solo or core 2 duo? Has anyone tried it yet? What would be the virtualization technology? KVM? VMWare workstation? Is it ridiculous to suggest that Xen might work on this platform? 

Thanks in advance.

Dave

---

### Post by marcw on 2009-08-02
> **muadnu said:**
> Sorry if this was already answered in the thread, but I couldn't find it.

I have a 3810T and cannot get the ethernet to work. With  the 2.28 kernel I tried the trick suggested in the first post, but didn't work. After installing the generic 2.30 kernel, I tried again, but now I can't even build the driver:

It's possible you have the same problem I had.  I couldn't get the recommended solution (installing l1e atheros module) to work either.  Then I discovered that my Atheros chip isn't an l1e - it's an l1c.  If you do an lspci command and see that your ethernet controller is an Attansic device 1063, you've got an l1c chip also.  I found the solution for this chip in a Radhat forum:  [https://bugzilla.redhat.com/show_bug.cgi?id=514069](https://bugzilla.redhat.com/show_bug.cgi?id=514069) .  Comments #3 and #4 provide a link for the correct module source for my l1c chip.  It compiles and works great!

My machine is is 3810t-6415.  Just running 9.04 for now.  Hope this helps someone else.  Now if I could get the suspend/resume thing to work...

---

### Post by miegiel on 2009-08-02
> **Dave_N said:**
> Hi. 

I am seriously considering the purchase of a 13.3 Acer Timeline. I have read the wiki and this whole thread. Could someone confirm my understanding of the "best" way to install Linux on this machine 

1.) Acquire laptop.
2) Flash latest bios from Acer and burn LiveCD of Ubuntu; jaunty 64 bit or karmic 64 bit alpha 2/3 correct?
3) Install from live CD. Do most people reformat or leave windows install for future bios?
4) Install the fixes from the wiki especially the 2.6.30 kernel.
5.) Enjoy

Now I have a question about virtualization:
Has anyone tried to get a virtualization solution going? I have a couple of apps that I need for work and I also run quicken. Ideally, I would like to run linux as the primary os and a virtual machine for quicken and the work apps. Is this asking too much of the core 2 solo or core 2 duo? Has anyone tried it yet? What would be the virtualization technology? KVM? VMWare workstation? Is it ridiculous to suggest that Xen might work on this platform? 

Thanks in advance.

Dave
Make that :
[LIST=1]
[*]Acquire laptop.
[*]Do the automated vista installation
[*]**Make the (vista) restore CD**
[*]Flash latest bios from Acer and burn LiveCD of Ubuntu; jaunty 64 bit or karmic 64 bit alpha 2/3 correct?
[*]Install from live CD. Do most people reformat or leave windows install for future bios?
[*]Install the fixes from the wiki especially the 2.6.30 kernel.
[*]Enjoy
[/LIST]
I managed to mess up the vista partition when making partitions for ubuntu and once you loose vista you can't make the restore CD and you can't flash the BIOS. Though if you have a vista installation CD you're probably still OK. Of course you can't flash BIOSes form linux :( (or can you?). I installed win7 (because I still want to have windows as a fall back) but you can't flash BIOSes from win7 either, yet. Maybe XP is an option, but I didn't try that. Luckily I flashed my BIOS before destroying vista.

As for the laptop itself. It's a great piece of plastic crap. I mean it's great, but it's plastic crap at the same time. I seriously considered returning it the 1st few hours I had the laptop. When I picked it up I noticed the keyboard had come loose during transport. I clicked the corner that came loose back, but every time I picked the laptop up with 1 hand at the front right corner, the keyboard would come loose in the top left corner again. In the end I decided to keep the laptop and solve the issue by sticking a few strips of carton along the bottom edge of the keyboard to keep it firmly in place. The carton came with the laptop :twisted: Another issue I have are the led switches above the keyboard (wifi, energy save mode and the useless backup buttons), they're pretty hard to press. To finish my rant, the timeline comes with disks that don't support NCQ, I thought that would be standard on disks by now, I guess that was to much to expect. I'll upgrade the disk later anyway and stick this one in an external case.

So I decided to keep the laptop regardless. :D The main reason was that I just didn't want to spend more money on it. Other laptops with the ultra-low-voltage core duo's would cost me an extra 500 euros at least and they had less memory (not that important to me), tiny 120GB disks or a significantly shorter battery life.

Oh, and a thumbs up for the keyboard when it comes to typing. Not that I've used that many laptops (this is the 1st I can really call my own) but I like it a lot more than the keyboards of other laptops I've used.

Regarding virtualliation, I haven't tried it (yet), but having 2 cores should make a big difference.

---

### Post by dsz on 2009-08-03
I have a 3810T core2 solo. I have installed ubuntu 9.04 + kernel 2.6.30
 
I installed the LAN driver as well, as mentioned in this thread.
 
When I copy big files, the LAN speed slows down to ~100-200 kbyte/sec after 0,5-1GB of data transferred.
 
any IDEA?
 
thanks
 
dsz

---

### Post by alvinator@ on 2009-08-03
It runs Windows XP pretty well using VirtualBox and it doesn't render your laptop unusable. I have the Single Core SU3500 timeline btw.

---

### Post by chookie on 2009-08-03
I have a problem with my 3810t that I have not seen in this thread before: mine won't restart or shut down, it hangs on "mount: / is busy".

I am running 9.04, 64 bit, with a normal 2.6.28 kernel. I have not changed the bios option, since it never had any problems starting up.

Edit: never mind, solved with the 2.6.30 kernel.

---

### Post by dsz on 2009-08-04
> **marcw said:**
> It's possible you have the same problem I had.  I couldn't get the recommended solution (installing l1e atheros module) to work either.  Then I discovered that my Atheros chip isn't an l1e - it's an l1c.  If you do an lspci command and see that your ethernet controller is an Attansic device 1063, you've got an l1c chip also.  I found the solution for this chip in a Radhat forum:  [https://bugzilla.redhat.com/show_bug.cgi?id=514069](https://bugzilla.redhat.com/show_bug.cgi?id=514069) .  Comments #3 and #4 provide a link for the correct module source for my l1c chip.  It compiles and works great!

My machine is is 3810t-6415.  Just running 9.04 for now.  Hope this helps someone else.  Now if I could get the suspend/resume thing to work...

Thanks!!!

the LAN slow down problem solved with this solution!!!!

thank you again! :D

dsz

---

### Post by muadnu on 2009-08-04
Any luck with the suspend issue?

---

### Post by cyberfish on 2009-08-05
> **muadnu said:**
> Any luck with the suspend issue?

The suspend issue is tracked here -
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405120](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405120)

---

### Post by amitz on 2009-08-10
Does the intel 5100AGN of Acer Timeline support master mode? Thanks in advance.

---

### Post by miegiel on 2009-08-10
> **amitz said:**
> Does the intel 5100AGN of Acer Timeline support master mode? Thanks in advance.

I guess so, but I haven't used wifi much yet. Check the flexibility section on [_this page_]("http://www.intel.com/network/connectivity/products/wireless/adapters/5000/index.htm").

---

### Post by muadnu on 2009-08-11
I've been trying to upgrade my BIOS to 1.10 but haven't been able to. I downloaded the new BIOS from the Acer website, but cannot run it in Vista since it is 64 bit (and, as it seems, the BIOS file only works in 32 bit).

I tried next flashing it booting in FreeDOS, as suggested by cyberfish in [this post]("http://ubuntuforums.org/showpost.php?p=7690770&postcount=151"). But when I run the executable I get an error (something like "DOS/4GW Professional error (2001): exception... (page fault)", which I'm not sure how to interpret). Luckily nothing bad happened to my motherboard. Maybe I didn't know how to interpret the "boot with the vanilla option" part of cyberfish's post, I don't know if booting with the wrong option makes a difference, but I'd like to know better before trying again.

---

### Post by miegiel on 2009-08-11
> **muadnu said:**
> I've been trying to upgrade my BIOS to 1.10 but haven't been able to. I downloaded the new BIOS from the Acer website, but cannot run it in Vista since it is 64 bit (and, as it seems, the BIOS file only works in 32 bit).

I tried next flashing it booting in FreeDOS, as suggested by cyberfish in [this post]("http://ubuntuforums.org/showpost.php?p=7690770&postcount=151"). But when I run the executable I get an error (something like "DOS/4GW Professional error (2001): exception... (page fault)", which I'm not sure how to interpret). Luckily nothing bad happened to my motherboard. Maybe I didn't know how to interpret the "boot with the vanilla option" part of cyberfish's post, I don't know if booting with the wrong option makes a difference, but I'd like to know better before trying again.

There is also [flashrom]("http://www.coreboot.org/Flashrom") to flash from linux (it's in the ubuntu repos), but it doesn't recognise the eeprom in my 3810t ... yet.

```
:~$ sudo flashrom
flashrom v0.9.0-r631
No coreboot table found.
Found chipset "Intel ICH9M-E", enabling flash write... OK.
Calibrating delay loop... OK.
[color=red]No EEPROM/flash device found.[/color]
If you know which flash chip you have, and if this version of flashrom
supports a similar flash chip, you can try to force read your chip. Run:
flashrom -f -r -c similar_supported_flash_chip filename

Note: flashrom can never write when the flash chip isn't found automatically.
```

---

### Post by cyberfish on 2009-08-11
> **muadnu said:**
> I've been trying to upgrade my BIOS to 1.10 but haven't been able to. I downloaded the new BIOS from the Acer website, but cannot run it in Vista since it is 64 bit (and, as it seems, the BIOS file only works in 32 bit).

It only works under DOS/FreeDOS. I tried it under 32-bit Vista and it didn't work either.

> **muadnu said:**
> 
I tried next flashing it booting in FreeDOS, as suggested by cyberfish in [this post]("http://ubuntuforums.org/showpost.php?p=7690770&postcount=151"). But when I run the executable I get an error (something like "DOS/4GW Professional error (2001): exception... (page fault)", which I'm not sure how to interpret). Luckily nothing bad happened to my motherboard. Maybe I didn't know how to interpret the "boot with the vanilla option" part of cyberfish's post, I don't know if booting with the wrong option makes a difference, but I'd like to know better before trying again.
Hmm I didn't get the error so I don't know...
The "vanilla option" I referred to is the one without HIMEM and EMM386. I think it was the last or the second last option in the unetbootin boot menu.

---

### Post by muadnu on 2009-08-12
> **cyberfish said:**
> It only works under DOS/FreeDOS. I tried it under 32-bit Vista and it didn't work either.


Hmm I didn't get the error so I don't know...
The "vanilla option" I referred to is the one without HIMEM and EMM386. I think it was the last or the second last option in the unetbootin boot menu.
Ok, my bad. I probably picked the wrong one when I tried last time. Now it worked perfectly. Thanks, cyberfish!

---

### Post by miegiel on 2009-08-13
Yay \\:D/ I've got two-finger scrolling.

All thanks to [_this post_]("http://ubuntuforums.org/showthread.php?p=7253159#post7253159") (just needed to share my happiness :D)

---

### Post by pound_forthesound on 2009-08-14
Hi everyone,

I've just installed Jaunty on my 3810t, but I'm having some problems.  The live USB loaded okay, and everything seemed to work fine, and the install went fine.  But when I restart and try to run Ubuntu, the laptop just goes to a blank screen partway through booting.  Any ideas what I've done wrong?

Thanks, Harry

Update: found this page: [https://help.ubuntu.com/community/AspireTimeline/Fixes](https://help.ubuntu.com/community/AspireTimeline/Fixes)

I couldn't get the "Set boot option in GRUB" instruction to work, but then I installed Karmic Alpha 4, and tried that instruction again, and all seems well now :)

---

### Post by yuki86 on 2009-08-16
tell me how, you can set ubuntu to save battery more? my battery time is just 5 hours, thank you...

---

### Post by miegiel on 2009-08-16
> **yuki86 said:**
> tell me how, you can set ubuntu to save battery more? my battery time is just 5 hours, thank you...

1st of all, 5 hours isn't that bad :) I get something like 6 hours.

That said, what you can do is:
[LIST]
[*]Set screen brightness to a (workable) minimum.
[*]Disable wifi and bluetooth if you don't use it.
[*]Disable the onboard ATI card (if you have that model) in the BIOS.
[*]Add the *CPU frequency scaling monitor* to your panel (both cores) so you can set your cores to *power save* easy.
[*]Don't use compiz or any 3D eye candy.
[*]Don't run conky or other stuff that keeps you laptop bussy.
[*]Don't play music (keeps your disk in a active state).
[*]Don't watch vids, especially HD vids suck the life out of your laptop.
[*]Close your browser when you're not surfing.
[*]Avoid ubuntu forums, those animated smilies are a waste of battery life
:lolflag:
[/LIST]

I get something like 8 hours battery life if I don't use my laptop, But I rather have the music and eye candy.

---

### Post by cyberfish on 2009-08-16
The most important thing is to enable wifi power saving mode. Read the wiki for how to do that.

---

### Post by anandharaj on 2009-08-18
Guys,

I having some issue with my Acer Timeline 4810 ATI driver card. Please refer my post here: [http://ubuntuforums.org/showthread.php?p=7800701](http://ubuntuforums.org/showthread.php?p=7800701)

Please help to solve this issue.

---

### Post by pound_forthesound on 2009-08-18
Has anyone else had difficulty connecting to wireless networks with this laptop?  I mean both under Windows and Ubuntu... I can sometimes connect, but the laptop decides to disconnect regularly and then not connect again for long periods.  To me it seems like a hardware issue

---

### Post by muadnu on 2009-08-18
> **pound_forthesound said:**
> Has anyone else had difficulty connecting to wireless networks with this laptop?  I mean both under Windows and Ubuntu... I can sometimes connect, but the laptop decides to disconnect regularly and then not connect again for long periods.  To me it seems like a hardware issue

This used to happen to me regularly, though mostly when using wireless for a long time. It hasn't happened in a while, though when I use the laptop for a long time I usually use the ethernet. I don't know about Windows, and I'm actually running Fedora 11.

---

### Post by csipuka on 2009-08-18
> **pound_forthesound said:**
> Has anyone else had difficulty connecting to wireless networks with this laptop?  I mean both under Windows and Ubuntu... I can sometimes connect, but the laptop decides to disconnect regularly and then not connect again for long periods.  To me it seems like a hardware issue
I had only connection issue to open network, but I have changed to wicd as network manager, and now the connection is ok.
I have no stability issue.

---

### Post by pound_forthesound on 2009-08-18
Thanks muadnu and csipuka, this is getting really frustrating so I think I'm going to try sending it back to Amazon for a replacement.

---

### Post by cyberfish on 2009-08-18
No problem at all here. I have been connected for about a week already.

---

### Post by lemurian on 2009-08-18
> **miegiel said:**
> 
[LIST]
[*]Add the *CPU frequency scaling monitor* to your panel (both cores) so you can set your cores to *power save* easy.
[/LIST]


Actually the developer of the frequency scaling monitor recommends using ondemand.  There are some cases in which powersave can be a better choice (e.g. old CPUs which do not have an idle state).  However, on modern laptops you want to get your processor to run in the idle state as much as possible.  If you force a low frequency (like powersave does), the CPU takes longer to accomplish the work you want it to accomplish to it takes longer to reach the idle state.

Here's a post from Arjan van de Ven discussing the problem:

[http://lkml.indiana.edu/hypermail/linux/kernel/0707.2/3763.html](http://lkml.indiana.edu/hypermail/linux/kernel/0707.2/3763.html)

---

### Post by quail-linux on 2009-08-19
> **muadnu said:**
> Any luck with the suspend issue?

To get the laptop to suspend and hibernate correctly I have to add ```
pci=biosirq
``` to the kernel boot string. This works on the 4810T, but not sure about the 3810T.

NOTE:
You can do this on the fly for testing purposes as you boot up by pressing 'e' at the kernel selection and then pressing 'e' again on the Kernel line, and at the end of the line add ```
pci=biosirq
```

I have done a bit of a write up about the 4810T laptop [here]("http://quail.southernvaleslug.org/debian_acer_aspire_timeline_4810t.html")

---

### Post by lemurian on 2009-08-19
> **quail-linux said:**
> To get the laptop to suspend and hibernate correctly I have to add ```
pci=biosirq
``` to the kernel boot string. This works on the 4810T, but not sure about the 3810T.


Are you running a 32 bit kernel?  I checked the kernel doc and found that biosirq is listed as a [X86-32] parameter.

I have a 3810T but I can't reboot right now because I'm in the middle of installing TeXLive 2009 (the pre-release version).

---

### Post by quail-linux on 2009-08-19
> **lemurian said:**
> Are you running a 32 bit kernel?  I checked the kernel doc and found that biosirq is listed as a [X86-32] parameter.

I have a 3810T but I can't reboot right now because I'm in the middle of installing TeXLive 2009 (the pre-release version).

I am using X86_64 (2.6.30-1-amd64 #1 SMP Mon Aug 3 12:28:22 UTC 2009 x86_64 GNU/Linux)

---

### Post by miegiel on 2009-08-19
> **quail-linux said:**
> To get the laptop to suspend and hibernate correctly I have to add ```
pci=biosirq
``` to the kernel boot string. This works on the 4810T, but not sure about the 3810T.

NOTE:
You can do this on the fly for testing purposes as you boot up by pressing 'e' at the kernel selection and then pressing 'e' again on the Kernel line, and at the end of the line add ```
pci=biosirq
```

I have done a bit of a write up about the 4810T laptop [here]("http://quail.southernvaleslug.org/debian_acer_aspire_timeline_4810t.html")

I tried that in 32bit karmic (2.6.31-6 kernel and grub2 on a 3810T), but suspend still crashes a few seconds after waking up. Hibernate works fine though, regardless of the kernel parameter. Running in 32bit also speeds up hibernation by 25% :D don't use that extra 1GiB anyway.

---

### Post by lemurian on 2009-08-19
Well, I tried pci=biosirq but my kernel complained that it was an unrecognized parameter.

---

### Post by quail-linux on 2009-08-19
For people that are interested here is a log of my suspend to ram and resume from it.

tail -f /var/log/messages
```

Message from syslogd@quails-laptop at Aug 20 10:45:59 ...
 kernel:[23317.939343] Disabling IRQ #16
Aug 20 10:45:59 quails-laptop kernel: [23317.939230] Pid: 7669, comm: pm-suspend Tainted: G        W  2.6.30-1-amd64 #1
Aug 20 10:45:59 quails-laptop kernel: [23317.939233] Call Trace:
Aug 20 10:45:59 quails-laptop kernel: [23317.939236]  <IRQ>  [<ffffffff8027fe1f>] ? __report_bad_irq+0x30/0x7d
Aug 20 10:45:59 quails-laptop kernel: [23317.939249]  [<ffffffff8027ff71>] ? note_interrupt+0x105/0x170
Aug 20 10:45:59 quails-laptop kernel: [23317.939254]  [<ffffffff80280563>] ? handle_fasteoi_irq+0x93/0xb5
Aug 20 10:45:59 quails-laptop kernel: [23317.939260]  [<ffffffff80212655>] ? handle_irq+0x17/0x1d
Aug 20 10:45:59 quails-laptop kernel: [23317.939264]  [<ffffffff80211e7c>] ? do_IRQ+0x57/0xbf
Aug 20 10:45:59 quails-laptop kernel: [23317.939268]  [<ffffffff80210453>] ? ret_from_intr+0x0/0x11
Aug 20 10:45:59 quails-laptop kernel: [23317.939270]  <EOI>  [<ffffffff802a9813>] ? remove_vma+0x0/0x6a
Aug 20 10:45:59 quails-laptop kernel: [23317.939278]  [<ffffffff802a99a6>] ? exit_mmap+0x129/0x148
Aug 20 10:45:59 quails-laptop kernel: [23317.939284]  [<ffffffff802401b8>] ? mmput+0x23/0xa5
Aug 20 10:45:59 quails-laptop kernel: [23317.939288]  [<ffffffff802c5829>] ? flush_old_exec+0x413/0x709
Aug 20 10:45:59 quails-laptop kernel: [23317.939295]  [<ffffffff802f4c3b>] ? load_elf_binary+0x364/0x18b9
Aug 20 10:45:59 quails-laptop kernel: [23317.939299]  [<ffffffff802a6896>] ? __get_user_pages+0x394/0x427
Aug 20 10:45:59 quails-laptop kernel: [23317.939304]  [<ffffffff802c4ca1>] ? get_arg_page+0x46/0xa5
Aug 20 10:45:59 quails-laptop kernel: [23317.939309]  [<ffffffff802c50bc>] ? search_binary_handler+0xca/0x254
Aug 20 10:45:59 quails-laptop kernel: [23317.939313]  [<ffffffff802c63f5>] ? do_execve+0x272/0x399
Aug 20 10:45:59 quails-laptop kernel: [23317.939319]  [<ffffffff8020e4e4>] ? sys_execve+0x35/0x4c
Aug 20 10:45:59 quails-laptop kernel: [23317.939323]  [<ffffffff8020ff1a>] ? stub_execve+0x6a/0xc0
Aug 20 10:46:28 quails-laptop kernel: [23317.961974] PM: Syncing filesystems ... done.
Aug 20 10:46:28 quails-laptop kernel: [23317.966058] Freezing user space processes ... (elapsed 0.00 seconds) done.
Aug 20 10:46:28 quails-laptop kernel: [23317.966744] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Aug 20 10:46:28 quails-laptop kernel: [23317.966789] Suspending console(s) (use no_console_suspend to debug)
Aug 20 10:46:28 quails-laptop kernel: [23318.268065] sd 1:0:0:0: [sda] Synchronizing SCSI cache
Aug 20 10:46:28 quails-laptop kernel: [23318.268249] sd 1:0:0:0: [sda] Stopping disk
Aug 20 10:46:28 quails-laptop kernel: [23319.228305] atheros_eth 0000:01:00.0: PME# disabled
Aug 20 10:46:28 quails-laptop kernel: [23319.228312] atheros_eth 0000:01:00.0: PCI INT A disabled
Aug 20 10:46:28 quails-laptop kernel: [23319.244147] ata_piix 0000:00:1f.5: PCI INT B disabled
Aug 20 10:46:28 quails-laptop kernel: [23319.260166] ata_piix 0000:00:1f.2: PCI INT B disabled
Aug 20 10:46:28 quails-laptop kernel: [23319.276054] ehci_hcd 0000:00:1d.7: PCI INT A disabled
Aug 20 10:46:28 quails-laptop kernel: [23319.276110] ehci_hcd 0000:00:1d.7: PME# disabled
Aug 20 10:46:28 quails-laptop kernel: [23319.292052] uhci_hcd 0000:00:1d.3: PCI INT C disabled
Aug 20 10:46:28 quails-laptop kernel: [23319.292103] uhci_hcd 0000:00:1d.2: PCI INT D disabled
Aug 20 10:46:28 quails-laptop kernel: [23319.292152] uhci_hcd 0000:00:1d.1: PCI INT B disabled
Aug 20 10:46:28 quails-laptop kernel: [23319.292202] uhci_hcd 0000:00:1d.0: PCI INT A disabled
Aug 20 10:46:28 quails-laptop kernel: [23319.324115] HDA Intel 0000:00:1b.0: PCI INT A disabled
Aug 20 10:46:28 quails-laptop kernel: [23319.340098] ehci_hcd 0000:00:1a.7: PCI INT D disabled
Aug 20 10:46:28 quails-laptop kernel: [23319.340161] ehci_hcd 0000:00:1a.7: PME# disabled
Aug 20 10:46:28 quails-laptop kernel: [23319.356103] uhci_hcd 0000:00:1a.1: PCI INT B disabled
Aug 20 10:46:28 quails-laptop kernel: [23319.356160] uhci_hcd 0000:00:1a.0: PCI INT A disabled
Aug 20 10:46:28 quails-laptop kernel: [23319.476116] ACPI: Preparing to enter system sleep state S3
Aug 20 10:46:28 quails-laptop kernel: [23320.284281] Disabling non-boot CPUs ...
Aug 20 10:46:28 quails-laptop kernel: [23320.284296] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Aug 20 10:46:28 quails-laptop kernel: [23320.284296] ACPI: Waking up from system sleep state S3
Aug 20 10:46:28 quails-laptop kernel: [23322.903308] pci 0000:00:02.0: PME# disabled
Aug 20 10:46:28 quails-laptop kernel: [23322.903314] pci 0000:00:02.1: PME# disabled
Aug 20 10:46:28 quails-laptop kernel: [23322.903363] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 20 10:46:28 quails-laptop kernel: [23322.903399] usb usb1: root hub lost power or was reset
Aug 20 10:46:28 quails-laptop kernel: [23322.903458] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Aug 20 10:46:28 quails-laptop kernel: [23322.903492] usb usb2: root hub lost power or was reset
Aug 20 10:46:28 quails-laptop kernel: [23322.903562] ehci_hcd 0000:00:1a.7: PME# disabled
Aug 20 10:46:28 quails-laptop kernel: [23322.903568] ehci_hcd 0000:00:1a.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Aug 20 10:46:28 quails-laptop kernel: [23322.903583] ehci_hcd 0000:00:1a.7: PME# disabled
Aug 20 10:46:28 quails-laptop kernel: [23322.903660] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Aug 20 10:46:28 quails-laptop kernel: [23323.006361] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Aug 20 10:46:28 quails-laptop kernel: [23323.006398] usb usb3: root hub lost power or was reset
Aug 20 10:46:28 quails-laptop kernel: [23323.006464] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Aug 20 10:46:28 quails-laptop kernel: [23323.006497] usb usb4: root hub lost power or was reset
Aug 20 10:46:28 quails-laptop kernel: [23323.006560] uhci_hcd 0000:00:1d.2: PCI INT D -> GSI 16 (level, low) -> IRQ 16
Aug 20 10:46:28 quails-laptop kernel: [23323.006596] usb usb5: root hub lost power or was reset
Aug 20 10:46:28 quails-laptop kernel: [23323.006663] uhci_hcd 0000:00:1d.3: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Aug 20 10:46:28 quails-laptop kernel: [23323.006700] usb usb6: root hub lost power or was reset
Aug 20 10:46:28 quails-laptop kernel: [23323.006770] ehci_hcd 0000:00:1d.7: PME# disabled
Aug 20 10:46:28 quails-laptop kernel: [23323.006775] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Aug 20 10:46:28 quails-laptop kernel: [23323.006790] ehci_hcd 0000:00:1d.7: PME# disabled
Aug 20 10:46:28 quails-laptop kernel: [23323.006870] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Aug 20 10:46:28 quails-laptop kernel: [23323.006963] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Aug 20 10:46:28 quails-laptop kernel: [23323.006981] pci 0000:00:1f.6: PME# disabled
Aug 20 10:46:28 quails-laptop kernel: [23323.007074] atheros_eth 0000:01:00.0: PME# disabled
Aug 20 10:46:28 quails-laptop kernel: [23323.007081] atheros_eth 0000:01:00.0: PME# disabled
Aug 20 10:46:28 quails-laptop kernel: [23323.331312] ata1: SATA link down (SStatus 4 SControl 300)
Aug 20 10:46:28 quails-laptop kernel: [23323.342536] ata4: SATA link down (SStatus 4 SControl 300)
Aug 20 10:46:28 quails-laptop kernel: [23323.496154] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug 20 10:46:28 quails-laptop kernel: [23323.496341] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Aug 20 10:46:28 quails-laptop kernel: [23323.504406] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
Aug 20 10:46:28 quails-laptop kernel: [23323.504410] ata2.00: ACPI cmd ef/03:41:00:00:00:a0 filtered out
Aug 20 10:46:28 quails-laptop kernel: [23323.520688] ata2.00: configured for UDMA/133
Aug 20 10:46:28 quails-laptop kernel: [23323.768349] ata3.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
Aug 20 10:46:28 quails-laptop kernel: [23323.768354] ata3.00: ACPI cmd ef/03:41:00:00:00:a0 filtered out
Aug 20 10:46:28 quails-laptop kernel: [23323.824384] ata3.00: configured for UDMA/100
Aug 20 10:46:28 quails-laptop kernel: [23323.992107] usb 8-5: reset high speed USB device using ehci_hcd and address 2
Aug 20 10:46:28 quails-laptop kernel: [23324.216425] sd 1:0:0:0: [sda] Starting disk
Aug 20 10:46:28 quails-laptop kernel: [23324.412101] usb 1-2: reset full speed USB device using uhci_hcd and address 3
Aug 20 10:46:28 quails-laptop kernel: [23325.140059] btusb 1-2:1.0: no reset_resume for driver btusb?
Aug 20 10:46:28 quails-laptop kernel: [23325.140062] btusb 1-2:1.1: no reset_resume for driver btusb?
Aug 20 10:46:28 quails-laptop kernel: [23325.392354] Restarting tasks ... done.
Aug 20 10:46:28 quails-laptop gnome-power-manager: (quail) Resuming computer
Aug 20 10:46:30 quails-laptop kernel: [23326.586311] Registered led device: iwl-phy0::radio
Aug 20 10:46:30 quails-laptop kernel: [23326.586332] Registered led device: iwl-phy0::assoc
Aug 20 10:46:30 quails-laptop kernel: [23326.586351] Registered led device: iwl-phy0::RX
Aug 20 10:46:30 quails-laptop kernel: [23326.586370] Registered led device: iwl-phy0::TX
Aug 20 10:46:30 quails-laptop kernel: [23326.756912] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 20 10:46:30 quails-laptop kernel: [23326.956095] atheros_eth 0000:01:00.0: stop mac failed
Aug 20 10:46:30 quails-laptop kernel: [23326.957053] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 20 10:47:00 quails-laptop kernel: [23356.802753] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Aug 20 10:47:06 quails-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name
Aug 20 10:47:06 quails-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.domain_search
Aug 20 10:47:06 quails-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Aug 20 10:47:06 quails-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Aug 20 10:47:06 quails-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.interface_mtu

```
Hopefully this is some help

---

### Post by cyberfish on 2009-08-19
Adding "pci=biosirq" doesn't help on my 3810t (alpha 4). Hibernate has always worked.

---

### Post by quail-linux on 2009-08-19
After some further testing I have found out the pci=biosirq does nothing. Reason I added it to my bootup parameters is cause my laptop never came out of suspend properly and the screen used to stay blank. It turns out that my suspend and hibernate are working correctly anyways.

I am now wondering if it cause my backlight control keys don't work to control and I had to install xbacklight and set this ```
xrandr --output LVDS --set BACKLIGHT_CONTROL native
``` so I could use xbacklight to control my backlight instead of the kernel.

---

### Post by cyberfish on 2009-08-19
BTW, does anyone have a 3810t with suspend working? All working reports seem to be from 4810t's.

---

### Post by lemurian on 2009-08-20
> **quail-linux said:**
> 
I am now wondering if it cause my backlight control keys don't work to control and I had to install xbacklight and set this ```
xrandr --output LVDS --set BACKLIGHT_CONTROL native
``` so I could use xbacklight to control my backlight instead of the kernel.

I don't use pci=biosirq but I do have an issue with brightness.  I used your xrandr command and was able to restore control.  (Thanks.)  But I don't need to use xbacklight.  I can just use Fn-LeftArrow/Fn-RightArrow and it works.  The steps from one brightness level to the other are very small though.

Hmm... one thing though.  I definitely did a test just after installing Ubuntu and I remember brightness working right.  I don't know if a kernel upgrade screwed it up or whether the bios upgrade from 1.04 to 1.08 screwed it up.  (I was on 1.04 initially.)

---

### Post by miegiel on 2009-08-20
> **lemurian said:**
> I don't use pci=biosirq but I do have an issue with brightness.  I used your xrandr command and was able to restore control.  (Thanks.)  But I don't need to use xbacklight.  I can just use Fn-LeftArrow/Fn-RightArrow and it works.  The steps from one brightness level to the other are very small though.

Hmm... one thing though.  I definitely did a test just after installing Ubuntu and I remember brightness working right.  I don't know if a kernel upgrade screwed it up or whether the bios upgrade from 1.04 to 1.08 screwed it up.  (I was on 1.04 initially.)

I read a lot of people are having issues with their brightness, but I'm not having any. Not now (32bit karmic alpha4 9.10 2.6.31-6 kernel), nor on my brief excursion to 64bit hardy (I thought it was a jaunty CD :D), nor with the 64bit karmic I've been using mostly since alpha5.

What kind of issues are people having anyway, "brightness issues" is a bit vague.

---

### Post by lemurian on 2009-08-20
> **miegiel said:**
> 
What kind of issues are people having anyway, "brightness issues" is a bit vague.

Correct, it is vague.

1. Using the Fn keys to change brightness does not work.
2. When going from battery to AC or AC to battery, Gnome will show a notification that it is changing the brightness but the brightness does not change.

Basically, it seems that any brightness changes issued from software (whether kernel or userland) are ineffective.

Using the xrandr command shown above fixes both problems.  As far as I can tell, it tells xrandr to send brightness changes directly to the hardware instead of letting the kernel handle it.

---

### Post by quail-linux on 2009-08-20
> **lemurian said:**
> Correct, it is vague.

1. Using the Fn keys to change brightness does not work.
2. When going from battery to AC or AC to battery, Gnome will show a notification that it is changing the brightness but the brightness does not change.

Basically, it seems that any brightness changes issued from software (whether kernel or userland) are ineffective.

Using the xrandr command shown above fixes both problems.  As far as I can tell, it tells xrandr to send brightness changes directly to the hardware instead of letting the kernel handle it.

I have the same above problems too.

I have tried to setup laptop-mode to control the brightness, but that does not work as laptop-mode does not notice the change between battery and AC.

Example of my /etc/laptop-mode/conf.d/lcd-brightness.conf
```

.....
#
# Should laptop mode tools control LCD brightness?
#
CONTROL_BRIGHTNESS=1


#
# Commands to execute to set the brightness on your LCD
#
#BATT_BRIGHTNESS_COMMAND="echo [value]"
#LM_AC_BRIGHTNESS_COMMAND="echo [value]"
#NOLM_AC_BRIGHTNESS_COMMAND="echo [value]"
#BRIGHTNESS_OUTPUT="/proc/acpi/video/VID/LCD/brightness"

BATT_BRIGHTNESS_COMMAND="xbacklight -time 0 -set 20"
LM_AC_BRIGHTNESS_COMMAND="xbacklight -time 0 -set 100"
NOLM_AC_BRIGHTNESS_COMMAND="xbacklight -time 0 -set 100"
BRIGHTNESS_OUTPUT="/dev/null"

```

and then I have to run:
```
/etc/init.d/laptop-mode restart
```
and then the above conf kicks in.

The closest kernel bug I have found related to this matter is [here]("http://bugzilla.kernel.org/show_bug.cgi?id=12174")

---

### Post by miegiel on 2009-08-20
Heh :) I find it a bit annoying that my brightness changes every time I (un)plug the charger, since I set my brightness depending on ambient light and not whether the charger is plugged in or not. I can imagine not being able to set your brightness with the FN + arrow keys is a major pain. 

I don't know if it's any help, but in my */etc/laptop-mode/conf.d/lcd-brightness.conf* it says *CONTROL_BRIGHTNESS=0* and not *CONTROL_BRIGHTNESS=1*. Also ther are a lot more notes in it.

Here's the whole file :
```
#
# Configuration file for Laptop Mode Tools module lcd-brightness.
#
# For more information, consult the laptop-mode.conf(8) manual page.
#


###############################################################################
# LCD brightness settings
# -----------------------
#
# Using these settings, you can make laptop mode tools automatically adjust
# your LCD's brightness settings. The settings are extremely simple -- they
# only allow for the execution of a command, nothing more. The reason for this
# is that LCD brightness settings are very different between laptop vendors.
#
# Suggestions for commands:
#
#  * If your system has the file "/proc/acpi/video/VID/LCD/brightness" (VID may
#    be VID1 or similar), use this file as BRIGHTNESS_OUTPUT, and use
#    the command "echo <value>". The possible values can be listed using the
#    command:
#
#       cat /proc/acpi/video/VID/LCD/brightness
#
#  * If you have a file /sys/class/backlight/.../brightness, then you can use
#    that file as BRIGHTNESS_OUTPUT, and the command "echo <value>".
#
#    As far as I understand it the values are between 0 and
#    the value contained in the file /sys/class/backlight/.../max_brightness.
#
#  * For Toshiba laptops, use the command "toshset" with the -lcd or -inten
#    command. Read the toshset(1) manual page for more information on the
#    parameters for this command. If you use this command, set
#    BRIGHTNESS_OUTPUT to "/dev/null".
#
###############################################################################

###############################################################################
#
# IMPORTANT: In versions 1.36 and earlier, these settings were included in the
# main laptop-mode.conf configuration file. If they are still present, they
# overrule the settings in this file. To fix this, simply delete the settings
# from the main config file.
#
###############################################################################


#
# Should laptop mode tools control LCD brightness?
#
CONTROL_BRIGHTNESS=0


#
# Commands to execute to set the brightness on your LCD
#
BATT_BRIGHTNESS_COMMAND="echo [value]"
LM_AC_BRIGHTNESS_COMMAND="echo [value]"
NOLM_AC_BRIGHTNESS_COMMAND="echo [value]"
BRIGHTNESS_OUTPUT="/proc/acpi/video/VID/LCD/brightness"
```

---

### Post by yuki86 on 2009-08-20
> **bududu said:**
> Here is my experience with Acer 3810T (solo) and Xubuntu 9.04.

Almost everything works by default. Except:
1. Skype doesn't work with microphone. (Microphone works, but skype can't 


hey i found solution in skype set this:

sound in - HDA Intel (hw:intel,o)
sound out - HDA Intel (hw:intel,o)
ringing - HDA Intel (hw:intel,o)

and then 
# alsamixer 
press tab than use arrows to switch mic from Front to Int
and prey..

---

### Post by lemurian on 2009-08-20
> **miegiel said:**
> 
I don't know if it's any help, but in my */etc/laptop-mode/conf.d/lcd-brightness.conf* it says *CONTROL_BRIGHTNESS=0* and not *CONTROL_BRIGHTNESS=1*. Also ther are a lot more notes in it.


Well, it's a good reminder. :)

I've actually tried this before but I retried after reading what you quoted just to make sure I really covered all my bases.  So I tried manipulating both of these directly and it had no effect:

/proc/acpi/video/OVGA/DD03/brightness
/sys/class/backlight/acpi_video0/brightness

I think the reason is that both are ways to get the *kernel* to change brightness.

There's a bunch of other devices than DD03 under OVGA but none of them support brightness changes.

---

### Post by quail-linux on 2009-08-20
> **miegiel said:**
> I don't know if it's any help, but in my */etc/laptop-mode/conf.d/lcd-brightness.conf* it says *CONTROL_BRIGHTNESS=0* and not *CONTROL_BRIGHTNESS=1*. Also ther are a lot more notes in it.

I know there was more to the file, if you look at my post in the code box at the start I put '....' mean there was more above and I only copied what was needed.

About the *CONTROL_BRIGHTNESS=0* and *CONTROL_BRIGHTNESS=1*, the 0 and 1 represents Off and On ie:

0 = Off
1 = On

---

### Post by joseph_d on 2009-08-22
Hey All,

I'm sorry for posting this here, but you'll understand my logic by the end.

I have installed a Ubuntu distro on my 3810T, got most working except for suspend. No biggie. During the partition process, I left the Vista restore partition and nothing else. I really didn't want to use Vista, but I kept the restore partition just in case. It's an option in Grub and I have booted into it already, so I know it's there.

However, when I go to perform a complete restore of my computer back to Vista (I'm giving the PC to my sister who doesn't know anything about Linux), I get the following error:

one of the services diskpart uses returned a failure.
ErrorCode=0, The operation completed successfully

Then the laptop reboots and it's back to Grub. Nothing is restored. This has something to do with the MBR, I'm pretty sure of it, but I don't know enough about Vista to fix it.

The reason I'm asking here, although this is a Ubuntu forum, you all (and myself included, with the exception of this issue) probably know more regarding MBRs, linux and Vista then the Vista only forums. 

I have a USB stick and no external CD/DVD drive, so if anyone has any ideas, please bear in mind I'll be using USB Stick only.

Again, booting to the Vista restore partition works, and I can mount it within Linux if you think I have to change any cfg files but it's not seeing the drive/MBR as the linux stuff is probably causing a conflict.

Also, just FYi, it's a full days work, ~7 hours, in Ubuntu with the Pentium (su2700) chip and brightness at 75%.

Thank you all!!!

---

### Post by miegiel on 2009-08-22
> **joseph_d said:**
> ...

one of the services diskpart uses returned a failure.
ErrorCode=0, The [COLOR="Red"]operation completed successfully[/COLOR]

Then the laptop reboots and it's back to Grub. Nothing is restored. This has something to do with the MBR, I'm pretty sure of it, but I don't know enough about Vista to fix it.

...

I love errors like that :D

Could be the MBR, but my 1st thought was "Is there free room for the "restore thing" to make a new partition?"
> 
...

I have a USB stick and no external CD/DVD drive, so if anyone has any ideas, please bear in mind I'll be using USB Stick only.

...

With *System > Administration > USB Startup Disk Creator* it's really easy to make USB boot disks from CDs, all you need is the CD .iso (for example the ubuntu-9.04-desktop-i386.iso you probably downloaded already or the [_gparted-live-0.4.5-2.iso_]("http://gparted.sourceforge.net/") to edit your partitions from a bootable CD/USB)

**ps** You might need to install it with :```
sudo apt-get install usb-creator
```

---

### Post by joseph_d on 2009-08-22
Thank you very much for the assistance. It definitely opened my eyes to some stuff I was overlooking, but I haven't had any luck.

I removed and reinstalled Ubuntu with a 10gig partition, leaving another partition for NTFS, which I created. Then I tried to restore again. I did notice, and forgot to mention before, that the restore utility does find my hard drive, but doesn't list anything for partition...so it's not finding the NTFS I made.

I truly can't believe I've screwed it up this much. I have no way of reinstalling Vista, as it didn't come with a CD/DVD nor do I have a drive (which reminds me, I filled out for a free Win7 upgrade...I wonder on what format they're going to send that to me)

I have the Vista license along the bottom of the laptop, perhaps I can find an ISO some where and go from there (it's not quite piracy, right?? :P )

Thank you for any other advice...

---

### Post by miegiel on 2009-08-22
> **joseph_d said:**
> ...

I removed and reinstalled Ubuntu with a 10gig partition, leaving another partition for NTFS, which I created. Then I tried to restore again. I did notice, and forgot to mention before, that the restore utility does find my hard drive, but doesn't list anything for partition...so it's not finding the NTFS I made.

Try deleting the NTFS partition. It might work only if there is empty space for a new partition. Yet you might be right with thinking the problem is with the MBR.

> ... 

I have the Vista license along the bottom of the laptop, perhaps I can find an ISO some where and go from there (it's not quite piracy, right?? :P )

I'm no lawyer It's more convenient then sending your laptop back to acer and let them fix it. But get a copy from a friend, the ISOs on the internet are often infected.

---

### Post by quail-linux on 2009-08-23
> **miegiel said:**
> Try deleting the NTFS partition. It might work only if there is empty space for a new partition. Yet you might be right with thinking the problem is with the MBR.

I'm no lawyer It's more convenient then sending your laptop back to acer and let them fix it. But get a copy from a friend, the ISOs on the internet are often infected.

When I backed up my recover partition on my 4810T it turned out to be 2 DVDs for Vista Home Premium and 1 DVD for Drivers and Apps.  After the backup I put in a Debian Lenny DVD and just repartitioned the whole 320GB HDD for Linux and and got rid of the recovery and Vista.

Remember to have your laptop on AC as the backup of the recovery partition to DVD does take awhile.

---

### Post by PatrickVogeli on 2009-08-23
for the brightness, I believe you could look into some file, I believe it could be /etc/acpi/events/video_brightnessdown and /etc/acpi/events/video_brightnessup, and there map some command to increase / decrease the backlight using xbacklight. I think people using some vaios with nvida 8400 gt cards did something similar, maybe you could search and do something similar.

---

### Post by sportjunkie on 2009-08-24
Hi there,

just joined the Timeline club :) and installed Karmic Koala Alpha 4 on my 4810T-8480. I do have some issues that are already mentioned here (mousepad lock doesn't unlock, no brightness change through fn buttons, power on command doesn't work for wlan driver), therefore I'm not going to bash about them.

But looking for advice about my mic, guess what - it doesn't work! Tried to use my VoIP client today and it could not pick up a sound from the build in mic or the external. Here what I tried so far:

- changed the input source in alsamixer from 'Front Mic' to 'Int Mic',
- set the mic booster to 0 (above 66% I get rustle),
- set the 'Front mic' value to 74 and 100,
- purged pulseaudio and reinstalled it,
- commented out pulse audio in /usr/share/alsa/alsa.conf,

All this had no effect. Any hints which nut I may have to twist?

Oh and has anyone reported the bugs I mentioned above and may has a link that I can track them?

Cheers
sportjunkie

---

### Post by miegiel on 2009-08-25
> **sportjunkie said:**
> Hi there,

just joined the Timeline club :) and installed Karmic Koala Alpha 4 on my 4810T-8480. I do have some issues that are already mentioned here (mousepad lock doesn't unlock, no brightness change through fn buttons, power on command doesn't work for wlan driver), therefore I'm not going to bash about them.

...

That's odd, all that stuff works for me (3810T, core duo, no ati). I don't know what power command you use for wlan, but I just turn it off (and on) with the icon in the notification area.

Regarding the mic. I'm having trouble there too. But karmic is not ready yet and the sound stuff (pulse, etc.) is still being worked on. [_Here_]("https://bugs.edge.launchpad.net/ubuntu/+bug/409819")'s the bug report. The external mic should work though.

---

### Post by sportjunkie on 2009-08-26
> That's odd, all that stuff works for me (3810T, core duo, no ati). I don't know what power command you use for wlan, but I just turn it off (and on) with the icon in the notification area.

Looks like a small misunderstanding. I was revering to the power managemand mode not turning the whole wlan on/off. The command I was refering to is
```

iwconfig wlan0 power on

Error for wireless request "Set Power Management" (8B2C) :
SET failed on device wlan0 ; Operation not supported.
```
I think cyberfish reported the same problem.

> Regarding the mic. I'm having trouble there too. But karmic is not ready yet and the sound stuff (pulse, etc.) is still being worked on. Here's the bug report. The external mic should work though.

I'm aware that karmic is still under heavy development and don't have a problem with testing bleeding edge software. Just wanted to know if anyone else had problems with his mic and may found out a workaround. External mic doesn't work either for me though.
Thanks for the link to the bug report.

---

### Post by -RAX- on 2009-08-27
After a partial upgrade of karmic alpha 3 I re-have the reboot/shutdown issue.

Everytime I try to turn the laptop off the cursor appears and starts blinking. The only way to stop it is an hardware power off.

I am using a 64 bit version with the latest kernel. I boot with libata.force=noncd in AHCI mode.


Any suggestion?

---

### Post by xir_ on 2009-08-27
> **-RAX- said:**
> After a partial upgrade of karmic alpha 3 I re-have the reboot/shutdown issue.

Everytime I try to turn the laptop off the cursor appears and starts blinking. The only way to stop it is an hardware power off.

I am using a 64 bit version with the latest kernel. I boot with libata.force=noncd in AHCI mode.


Any suggestion?

i solved this by using 2.6.30.5 compiled through kernelcheck (a really cool program). the blinking cursor has now gone away on shtdown.

---

### Post by -RAX- on 2009-08-27
> **xir_ said:**
> i solved this by using 2.6.30.5 compiled through kernelcheck (a really cool program). the blinking cursor has now gone away on shtdown.

Thanks for the tip, I am downloading it right now.
Did you use any specific settings or you just run it automatically?

I will let you know as soon as I try.

---

### Post by -RAX- on 2009-08-27
No it didn't work.. maybe i didn't configure it right. Should I have disabled ata support?


I do not have the issue with kernel 2.6.31-6, so I will use that for now. Hopefully they will fix the bug in the 31-8

---

### Post by quail-linux on 2009-08-28
In this post[1] Salixman made reference to that the 2.6.30 kernel fixes the problems with backlight (brightness controls) and some networking probs on the 4810T.  I am using the 2.6.30 Debian Kernel and I still have broken backlight controls and have to compile Ethernet drivers still.

I think they referring to the latest 2.6.31-rcX[2] kernels that fix the problems.

[1] [http://ubuntuforums.org/showpost.php?p=7856969&postcount=29](http://ubuntuforums.org/showpost.php?p=7856969&postcount=29)
[2] [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc7/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc7/)

---

### Post by redsunlee on 2009-08-28
Interesting thought, i completely agree with your perspective

[[color=#FFFFFF]_taux demande pret personnel en ligne credit simulation_](http://pretpersonnelenligne.org)[/color][color=#FFFFFF] Faire un pret immobilier en ligne avec un bon credit[/color][[color=#FFFFFF]_taux demande pret personnel en ligne credit simulation_](http://pretpersonnelenligne.org)[/color]

---

### Post by miegiel on 2009-08-28
> **-RAX- said:**
> After a partial upgrade of karmic alpha 3 I re-have the reboot/shutdown issue.

Everytime I try to turn the laptop off the cursor appears and starts blinking. The only way to stop it is an hardware power off.

I am using a 64 bit version with the latest kernel. I boot with libata.force=noncd in AHCI mode.


Any suggestion?

The shutdown/restart bug has been fixed in kernel 2.6.31-8.

If you're using karmic keep an eye on the [_Karmic Koala Testing and Discussion_]("http://ubuntuforums.org/forumdisplay.php?f=359") sub-forum, many problems with karmic aren't acer timeline related ;)

---

### Post by xir_ on 2009-08-28
> **-RAX- said:**
> Thanks for the tip, I am downloading it right now.
Did you use any specific settings or you just run it automatically?

I will let you know as soon as I try.

I just compiled to my cpu spec (might as well get a tiny bit of extra performance), core 2, disabled all the multi core options, and set the kernel frequency to 1000hz.

Silly question but are you sure that it booted you into the new kernel, on one laptop it didnt become the default kernel.

---

### Post by hammeraxe on 2009-08-28
My new 3810T laptop works great with 64bit Jaunty, yet I have a couple of questions.

How to map a function key? Fn+F2 does not do anything (unlike the other Fn combintions). xev does not see Fn keypress and neither does xbindkeys.

What do the "backup" and "powersave" keys do under Ubuntu? They do light up when touched, but I cant really understand their functions. "Backup" seems to do nothing, while "powersave" seems to prevent suspend if off while on battery power. It cannot be enabled while on AC.

Another thing is that the screen backlight seems to flicker slightly when set to minimum brightness. This is extremely annoying and hurts my eyes (as do higher brightness settings :D). Is there any way to fix this?

---

### Post by CptMath on 2009-08-31
I got a 5810T a few days ago, and this thread has been really helpful so far.  I upgraded to Karmic shortly after getting Ubuntu installed.  So far, I've experienced a few rather major issues

1) Screen tearing issue during video.  Karmic fixed this.
2) Cannot change brightness.  Like many others, it seems, I cannot adjust the backlight brightness.  I haven't been able to get any of the suggested fixes that I've seen to work.  The Fn+arrow keys cause Gnome's slider to change, but the actual brightness doesn't.  When I try xrandr, I get

```
 >  xrandr --output LVDS --set BACKLIGHT_CONTROL native
X Error of failed request:  BadRROutput (invalid Output parameter)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  15 (RRGetOutputProperty)
  Serial number of failed request:  30
  Current serial number in output stream:  30

```I did a bit of searching, and it seems that LVDS is really the only output option that'd make sense for a laptop, so I'm not sure what's going on there.  I'm not familiar enough with X or how the screen works in linux to know what to do from there.

3) Resuming from suspend is fairly broken.  I can get logged back in after I suspend, but the video is somewhat garbled.  The top bar on every menu (the one with minimize, maximize, etc.) is missing, and some of Gnome's menus are covered in lines.  Also, any new window I attempt to open isn't visible.  Logging out/in seems to fix this issue.  I have a sneaking suspicion that the laptop's lack of dedicated video memory and the way that suspend is restoring memory has something to do with this, but I don't know enough to go from there.

All in all, it's decent enough so far, but I am eagerly awaiting the release version of karmic, which will hopefully stabilize the experience.  If I can get the brightness and suspend issues fixed, I'll be quite a bit happier.

If anyone has any ideas how to correct my two outstanding issues, let me know.  Thanks :)

edit: I forget to include a couple of other minor bugs I've seen.  I've noticed others have mentioned these, as well.  The touchpad enable/disable button will disable the touchpad, but when I try to re-enable it, nothing happens.  The same goes for the wifi enable/disable button.

---

### Post by quail-linux on 2009-08-31
> **CptMath said:**
> 
2) Cannot change brightness.  Like many others, it seems, I cannot adjust the backlight brightness.  I haven't been able to get any of the suggested fixes that I've seen to work.  The Fn+arrow keys cause Gnome's slider to change, but the actual brightness doesn't.  When I try xrandr, I get

```
 >  xrandr --output LVDS --set BACKLIGHT_CONTROL native
X Error of failed request:  BadRROutput (invalid Output parameter)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  15 (RRGetOutputProperty)
  Serial number of failed request:  30
  Current serial number in output stream:  30

```I did a bit of searching, and it seems that LVDS is really the only output option that'd make sense for a laptop, so I'm not sure what's going on there.  I'm not familiar enough with X or how the screen works in linux to know what to do from there.


what does running this give you?
```
xrandr --prop
```

You should get an output similar to this:
```
$ xrandr --prop
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 1366 x 1366
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1366x768+0+0 (normal left inverted right x axis y axis) 310mm x 174mm
	EDID_DATA:
		00ffffffffffff0030e4010200000000
		00130103801f11780a8845955a568d28
		23505400000001010101010101010101
		010101010101561d56c6500020303020
		350036ae100000190000000000000000
		00000000000000000000000000fe004c
		4720446973706c61790a2020000000fc
		004c503134305748322d544c41310039
	PANEL_FITTING: full
		supported: center       full_aspect  full        
	BACKLIGHT_CONTROL: native
		supported: **native       legacy       combination  kernel**      
	BACKLIGHT: 2078 (0x0000081e) range:  (0,2078)
   1366x768       60.0*+
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right x axis y axis)
	BOTTOM: 37 (0x00000025) range:  (0,100)
	RIGHT: 46 (0x0000002e) range:  (0,100)
	TOP: 36 (0x00000024) range:  (0,100)
	LEFT: 54 (0x00000036) range:  (0,100)
	TV_FORMAT: NTSC-M
		supported: NTSC-M       NTSC-443     NTSC-J       PAL-M       
		           PAL-N        PAL         

```
The line in **bold** is support backlight controls.

---

### Post by miegiel on 2009-08-31
@**CptMath** try a clean karmic install instead of an upgrade from jaunty. I never had any issues with the brightness Fn keys or the touchpad switch in karmic, they just worked. I think some old jaunty stuff is messing things up for you, for example I don't even have a xorg.conf file any more.

---

### Post by tty on 2009-09-05
Currently, xrandr under Ubuntu does not support the XGA resolution for the 3810T.  This 1024x768 resolution is very useful for beamer presentations - there you would like to run beamer and laptop in mirror mode.  So far I have succeeded as follows:

cvt 1024 768

  to get the modeline

xrandr --newmode  "1024x768"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
xrandr --addmode LVDS1 1024x768
xrandr --output LVDS1 --set "scaling mode" "No scale"

What I do no understand here:

Is there a way to configure the No scale preference differently? I.e.,
I would like to put these lines into a startup script, but it seems I
have to switch to that mode to enable noscaling.

Where should I put all these lines into? /etc/gdm/Init/Default is probably the best place.

---

### Post by fictivetoast on 2009-09-06
> **cyberfish said:**
> BTW, does anyone have a 3810t with suspend working? All working reports seem to be from 4810t's.

I'm curious as well - have been running karmic on a new 3810t-6415 (dual core SU9400, intel graphics) and haven't had any luck with suspend on the 2.6.31.9.20 kernel with the latest bios (v.10).  Frustrating!  Does anyone with a 3810t have suspend working on x64?

Hibernate seems to take a *long* time to wake from too, and is generally not very responsive after waking.

Got wireless powersaving mode to work by installing the backports module as described here : [https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.31/+bug/405158](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.31/+bug/405158)

---

### Post by Ashrael on 2009-09-08
Hi all!

I bought a timeline 4810TG yesterday, today (after finally finishing the initial Vista setup) I decided to put on Jaunty....So I have the same issues with touchpad dis/enable button, suspend does not work... But more strange: I seem to have something going on that I have heard no-one talking about: my cd/dvd does not work properly..

dmesg | tail:

```
[ 2304.684320] ata5: link online but device misclassified, retrying
[ 2304.684325] ata5: hard resetting link
[ 2311.272040] ata5: failed to reset engine (errno=-5)
[ 2316.476259] ata5: link is slow to respond, please be patient (ready=0)
[ 2339.716277] ata5: softreset failed (device not ready)
[ 2339.716310] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 2339.716317] ata5: link online but device misclassified, retrying
[ 2339.716323] ata5: limiting SATA link speed to 1.5 Gbps
[ 2339.716327] ata5: hard resetting link
[ 2345.224120] ata5: failed to reset engine (errno=-5)
```


This could this be a hardware problem, but I am not sure.

uname -r:
```
2.6.28-15-generic

```

lshw:

```
ubuntu-timeline-h
    description: Computer
    product: Aspire 4810T
    vendor: Acer
    version: V1.20
    serial: LXPE10X2189252EB******
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6
    configuration: boot=normal uuid=914C72C0-6162-11DE-B1DD-C61EFAC9111B
  *-core
       description: Motherboard
       product: Aspire 4810T
       vendor: Acer
       physical id: 0
       version: Base Board Version
       serial: LXPE10X2189252EB******
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: INSYDE
          physical id: 0
          version: V1.20 (06/15/2009)
          size: 1MiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-memory
          description: System Memory
          physical id: 16
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM Synchronous 800 MHz (1.2 ns)
             product: M471B5673EH1-CF8
             vendor: 80CE
             physical id: 0
             serial: 84C11770
             slot: DIMM0
             size: 2GiB
             clock: 800MHz (1.2ns)
        *-bank:1
             description: SODIMM Synchronous 800 MHz (1.2 ns)
             product: M471B5673EH1-CF8
             vendor: 80CE
             physical id: 1
             serial: 84C11755
             slot: DIMM2
             size: 2GiB
             clock: 800MHz (1.2ns)
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Solo CPU    U3500  @ 1.40GHz
          vendor: Intel Corp.
          physical id: 1e
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          slot: CPU
          size: 1400MHz
          capacity: 1400MHz
          width: 64 bits
          clock: 800MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx x86-64 constant_tsc up arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority cpufreq
        *-cache:0
             description: L2 cache
             physical id: 1f
             slot: Unknown
             size: 3MiB
             capacity: 3MiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 21
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back data
     *-cache
          description: L1 cache
          physical id: 20
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-back instruction
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: Mobile 4 Series Chipset PCI Express Graphics Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
           *-display UNCLAIMED
                description: VGA compatible controller
                product: M92 LP [Mobility Radeon HD 4300 Series]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi cap_list
                configuration: latency=0
           *-multimedia
                description: Audio device
                product: R700 Audio Device [Radeon HD 4000 Series]
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-display UNCLAIMED
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network UNCLAIMED
                description: Ethernet controller
                product: Attansic Technology Corp.
                vendor: Attansic Technology Corp.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: c0
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list
                configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: Wireless WiFi Link 5100
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wmaster0
                version: 00
                serial: 00:22:fb:52:**:**
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn ip=10.0.0.191 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:7
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: ICH9M-E LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: ICH9M/M-E SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi1
             logical name: scsi4
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0 module=ahci
           *-disk
                description: ATA Disk
                product: WDC WD3200BEVT-2
                vendor: Western Digital
                physical id: 0
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: 11.0
                serial: WD-WX50A599****
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=463530c0
              *-volume:0
                   description: Windows FAT volume
                   vendor: MSDOS5.0
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   version: FAT32
                   serial: eaee-eb49
                   size: 9998MiB
                   capacity: 10000MiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 82f283a7-3316-3042-ab72-ad0c557647f4
                   size: 190GiB
                   capacity: 190GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-09-08 16:17:54 filesystem=ntfs label=ACER state=clean
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@1:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /
                   version: 1.0
                   serial: ded43a6f-50dc-41e5-adce-5820a71305ee
                   size: 19GiB
                   capacity: 19GiB
                   capabilities: primary journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2009-09-08 15:57:07 filesystem=ext3 modified=2009-09-08 14:35:02 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-09-08 14:35:02 state=mounted
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@1:0.0.0,4
                   logical name: /dev/sda4
                   size: 78GiB
                   capacity: 78GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 4094MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /home
                      capacity: 74GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=ordered state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM UJ862AS
                vendor: MATSHITA
                physical id: 1
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
        *-generic UNCLAIMED
             description: Signal processing controller
             product: 82801I (ICH9 Family) Thermal Subsystem
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 92:ee:98:3d:3e:d0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

Anyone have an idea?

TIA!

---

### Post by Ashrael on 2009-09-08
well... I solved it already.. I found this link:
[http://forum.ubuntu-fr.org/viewtopic.php?pid=2900788](http://forum.ubuntu-fr.org/viewtopic.php?pid=2900788)
And that set me on the path of fstab...

/dev/scd0    /media/cdrom0   udf,iso9660 ro,user,noauto              0    0

changed this to:

/dev/scd1    /media/cdrom0   udf,iso9660 ro,user,noauto              0    0

and: Oh JOY! it works... It seems that the jaunty installer made a mistake somehow...

SOLVED!

UPDATE: It seems that not all is solved...It worked for two cd's the third gave me the same dmesg output as before....

---

### Post by quail-linux on 2009-09-09
@**Ashrael** I noticed that you bios version is abit old, when I bought my 4810T it came with 1.26 version bios. You can download current bios from acer[1] and the current bios version looks to be 1.28. I know 1.26 Bios works fine, not sure of 1.28 not tested it. 

I have just heard of people having problems with older versions of bios especially in the 3810s iirc

Upgrading your bios when not got Windows install can still be done, refer to this page[2].

[1] [http://support.acer-euro.com/drivers/downloads_gd.html](http://support.acer-euro.com/drivers/downloads_gd.html)
[2] [http://www.netbooktech.com/tag/acer-aspire-one-bios-update-instructions/](http://www.netbooktech.com/tag/acer-aspire-one-bios-update-instructions/)

---

### Post by jacktow on 2009-09-09
I just purchased an Acer Timeline 8371 with discrete ATI graphics and I'm not quite liking it.

Before I start ranting, very nice thread, once I get my head around the graphics stuff, I shall start worrying about the touchpad, etc. ;-)

I was under the impression that one could choose which graphics card to use by changing a BIOS option. Turns out I was wrong. The switchable graphics option seems to keep both cards on and thus my machine runs hot and my battery, based on my estimate, would not even last 2 hours!

I'm currently using Karmic alpha 6 and by default, it loads both i915 and radeon drivers. I blacklisted radeon driver and further did the following which I thought would turn off the bus on which ATI sits:

```
echo 1 > /sys/bus/pci/devices/0000:01:00.0/remove
```

NOTE: I got the device id by looking at the output of "lspci"

Doing that caused the ATI card to no longer show up on lspci and its traces vanished everywhere, and YET, no changes in the temperature nor the pathetic battery life.

I didn't keep the vista long enough to see how it worked there, but it seems like a stupid design to enable both cards at startup and let the OS decide which to shut down!

Any ideas? or else I might end up exchanging this unit with the non-discrete version (which would be very difficult, considering I've unpacked everything and pulled out all the stickers, etc. :) )

NOTE: I've attached the output of "lshw" and "lspci" for those who can make use of it

---

### Post by Ashrael on 2009-09-09
@quail-linux: I've upgraded the bios to 1.28, now the dmesg output has changed a bit:
```

[  129.725023] ata5.00: cmd a0/00:00:00:02:00/00:00:00:00:00/a0 tag 0 pio 16388 in
[  129.725025]          cdb 43 02 05 00 00 00 00 00  02 00 00 00 00 00 00 00
[  129.725026]          res 50/00:03:00:04:00/00:00:00:00:00/a0 Emask 0x12 (ATA bus error)
[  129.725030] ata5.00: status: { DRDY }
[  129.725035] ata5: hard resetting link
[  130.208306] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  130.212524] ata5.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[  130.220136] ata5.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[  130.220200] ata5.00: configured for UDMA/33
[  130.226640] ata5: EH complete

```


I have started vista, and it does not seem to have a problem with the dvd drive, so I guess it must be a problem with software... I have had an error like this before on my pc, there the fault was the sata cable, but since this is a laptop I guess this time it can't be that (or can it?)


TIA!

---

### Post by Ashrael on 2009-09-09
This is the dmesg output that keeps repeating (with no disc in drive)


[  455.284148] ata5: failed to reset engine (errno=-5)
[  459.032231] ata5: softreset failed (device not ready)
[  459.032270] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  459.032278] ata5: link online but device misclassified, retrying
[  459.032283] ata5: hard resetting link
[  465.308324] ata5: failed to reset engine (errno=-5)
[  469.076284] ata5: softreset failed (device not ready)
[  469.076320] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  469.076328] ata5: link online but device misclassified, retrying
[  469.076333] ata5: hard resetting link

Is it just me that has this problem? If so, it might be hardware after all.

About the touchpad button: It does switch the tp off, but not on, could this be worked around by a script or making a module persistent or something like that? Has anyone installed the acerhk package from repo's, and with what result?

---

### Post by fictivetoast on 2009-09-09
> **Ashrael said:**
> About the touchpad button: It does switch the tp off, but not on, could this be worked around by a script or making a module persistent or something like that? Has anyone installed the acerhk package from repo's, and with what result?

Have you tried ```
sudo modprobe -r psmouse && sudo modprobe psmouse
``` as suggested here : [https://help.ubuntu.com/community/AspireTimeline/Fixes](https://help.ubuntu.com/community/AspireTimeline/Fixes) ?

---

### Post by trendzetter on 2009-09-09
> **quail-linux said:**
> what does running this give you?
```
xrandr --prop
```

You should get an output similar to this:
```
$ xrandr --prop
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 1366 x 1366
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1366x768+0+0 (normal left inverted right x axis y axis) 310mm x 174mm
	EDID_DATA:
		00ffffffffffff0030e4010200000000
		00130103801f11780a8845955a568d28
		23505400000001010101010101010101
		010101010101561d56c6500020303020
		350036ae100000190000000000000000
		00000000000000000000000000fe004c
		4720446973706c61790a2020000000fc
		004c503134305748322d544c41310039
	PANEL_FITTING: full
		supported: center       full_aspect  full        
	BACKLIGHT_CONTROL: native
		supported: **native       legacy       combination  kernel**      
	BACKLIGHT: 2078 (0x0000081e) range:  (0,2078)
   1366x768       60.0*+
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right x axis y axis)
	BOTTOM: 37 (0x00000025) range:  (0,100)
	RIGHT: 46 (0x0000002e) range:  (0,100)
	TOP: 36 (0x00000024) range:  (0,100)
	LEFT: 54 (0x00000036) range:  (0,100)
	TV_FORMAT: NTSC-M
		supported: NTSC-M       NTSC-443     NTSC-J       PAL-M       
		           PAL-N        PAL         

```
The line in **bold** is support backlight controls.

```

$ xrandr --prop
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 345mm x 194mm
	EDID_DATA:
		00ffffffffffff0030e4020200000000
		00130103802313780a28659759548e27
		1e505400000001010101010101010101
		010101010101561d56c6500020303020
		350059c2100000190000000000000000
		00000000000000000000000000fe004c
		4720446973706c61790a2020000000fc
		004c503135365748332d544c41310039
	scaling mode:	Fullscreen
		supported: Non-GPU      Fullscreen   No scale     Aspect      
   1366x768       60.0*+
   1360x768       59.8  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
DVI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)

```

Seems that I have no backlight control in xrandr. I've been googling but I didn't find a working solution.

---

### Post by quail-linux on 2009-09-09
> **Ashrael said:**
> 
.....
Has anyone installed the acerhk package from repo's, and with what result?

There is no need for *acerhk* as far as I understand is that *acer_wmi* is the successor of *acerhk*

---

### Post by Ashrael on 2009-09-10
@fictivetoast:

> Have you tried
Code:

sudo modprobe -r psmouse && sudo modprobe psmouse

as suggested here : [https://help.ubuntu.com/community/AspireTimeline/Fixes](https://help.ubuntu.com/community/AspireTimeline/Fixes) ?

Yes, I knew that one. But, I was thinking about linking this key to a script or something. I can get the keycode with xev, so It must be possible to link this key to a script that re-enables the touchpad.

XEV output: KeyPress event, serial 34, synthetic NO, window 0x4000001,
    root 0x7a, subw 0x0, time 671387, (-417,392), root:(257,443),
    state 0x0, keycode 200 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

@quail-linux: thanks! I was just wondering about that acerhk package.
@quail-linux: I have installed 8.10 yesterday and with the kernel on the livecd (2.6.27-7-generic) and this gives the following output:

$ dmesg | tail
[  233.511223] UDF-fs: No VRS found
[  233.595665] ISO 9660 Extensions: Microsoft Joliet Level 3
[  233.702364] ISO 9660 Extensions: RRIP_1991A
[  268.412516] end_request: I/O error, dev sr0, sector 0
[  268.412528] Buffer I/O error on device sr0, logical block 0
[  268.412536] Buffer I/O error on device sr0, logical block 1
[  268.412540] Buffer I/O error on device sr0, logical block 2
[  268.412543] Buffer I/O error on device sr0, logical block 3
[  268.421637] end_request: I/O error, dev sr0, sector 0
[  268.421655] Buffer I/O error on device sr0, logical block 0

BUT, it does work with this kernel. Then I updated all packages, and this gives the following result (2.6.27-14-generic):


[  166.752315] ata5.00: status: { DRDY }
[  166.752325] ata5: hard resetting link
[  168.584065] ata5: failed to reset engine (errno=-5)
[  176.784266] ata5: softreset failed (device not ready)
[  176.784306] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  176.784323] ata5.00: failed to IDENTIFY (I/O error, err_mask=0x40)
[  176.784328] ata5.00: revalidation failed (errno=-5)

So this is the same result I get with jaunty as mentioned in my previous posts.

If things are like that for much longer, I will have to revert to windows again (HELP!) I bought this laptop to be used with ubuntu....

TIA!

---

### Post by Dan48p on 2009-09-10
Hello, I have been looking around these forums briefly for a little while now and have a question about my acer.  I bought a 3810tz and installed an amd64 version of ubuntu 9.04 and was able to boot directly into ubuntu without changing from AHCI to IDE mode.

About a day after I had been using this setup part of the screen went dark and I got a replacement in the mail from amazon.  I followed the exact same procedure that I had before (shrinking the vista partition to about 140gb and installing ubuntu on the rest) but this time I had to switch into IDE mode.

Looking through the bios the only noticeable difference I could find was that the new laptop has "Hitachi" in the hard drive 0 space, followed by a series of numbers, and the old laptop just has a series of numbers in the same place.

I saw that other people were switching to IDE mode and thought I would try it out, though I'm fairly dissapointed that I have must switch modes in order to boot a particular OS.

I posted for a couple reasons, one, maybe narrow down why some of these laptops have to be in IDE mode and others don't.  Also, is there any way to get the my new machine to function like my other one does?  I will still have both of these laptops for a few days until I send the old one back, so if there are any settings I should look at on the two or anything please let me know.

Thanks,
dan

---

### Post by lemurian on 2009-09-10
> **Dan48p said:**
> Hello, I have been looking around these forums briefly for a little while now and have a question about my acer.  I bought a 3810tz and installed an amd64 version of ubuntu 9.04 and was able to boot directly into ubuntu without changing from AHCI to IDE mode.


Same here on my 3810T.  No need to switch from AHCI to IDE mode.  There are other pieces of advice I saw in this thread which did not apply to my machine.

In other news:

The backlight problem does not occur for me on kernel 2.6.31-6.  This is a karmic kernel which I installed from the PPA mentioned in this thread:

[http://ubuntuforums.org/showthread.php?t=1246398](http://ubuntuforums.org/showthread.php?t=1246398)

Don't upgrade to this kernel unless you know Ubuntu pretty well.  After the upgrade my machine would not boot and I had to boot in rescue mode and edit some files to get it to boot.  Also, 2.6.31-9 from that PPA hangs after mounting the encrypted fs.  I don't know why and have not investigated.

---

### Post by trendzetter on 2009-09-10
- I found a way to set the brightness using [this suggestion]("https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/397617/comments/2"):
> the only solution to increase or decrease the brightness (in fact i need to decrease it, because it is at 100% all the time) was with these commands:

first : find the device address (here 00:02.0)
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)

second :
setpci -s 00:02.0 F4.B=66 (a value between 00 and FF, where FF is 100%)

Not very userfriendly but working for now.

---

### Post by Dan48p on 2009-09-10
I suppose my last post should have been a little more clear.  The backlight problem that my machine had was that the bottom right hand corner of the screen would flicker and go out completely.  This happened in Ubuntu, Windows and even in the bios.  I have not noticed any problems with my brightness so far with this computer though I have really only used windows long enough to shrink it's partition so I don't really have much to compare it with.

I wonder if Amazon would notice if I swapped out the hard drives on these computers before I send the bad one back... It would be nice to have the option of booting windows without first changing my bios settings.

---

### Post by jacktow on 2009-09-11
For those with dedicated ATI graphics card models (eg 8371G), check out this post:
[http://ubuntuforums.org/showthread.php?p=7933876#post7933876](http://ubuntuforums.org/showthread.php?p=7933876#post7933876)

This should help you save some power

---

### Post by Ashrael on 2009-09-12
@quail-linux: 

well, I've decided to take this one (acer timeline 4810TG) back to the store. Since there seem to be only two people in the world with the same problem I had, I assume it must be the sata connection that is dodgy.
Will come back when I have had some hands-on time with the new one...

Thanks!

---

### Post by jacktow on 2009-09-12
Could everyone please post how much their laptop is drawing power and the battery life estimate. I used Intel's powertop tool (which is in the repository). Please use the same tool so we can compare.
Run the following in the shell to get powertop running:

```
sudo aptitude install powertop
sudo powertop
```

*NOTE: you need to run powertop as root, otherwise it won't show you half the stuff.*

Once powertop is running, look at the line that starts with "Power Usage (ACPI estimate)" and tell us what yours is. Here's mine with WiFi and Bluetooth on and LCD brightness at ~50%:

**Power Usage (ACPI estimate): 12.8W (5.0 hours)**

---

### Post by quail-linux on 2009-09-12
> **Ashrael said:**
> @quail-linux: 

well, I've decided to take this one (acer timeline 4810TG) back to the store. Since there seem to be only two people in the world with the same problem I had, I assume it must be the sata connection that is dodgy.
Will come back when I have had some hands-on time with the new one...

Thanks!

You are welcome, I sorry I not biggest of help.

People on the list I am running Debian on my 4810T, so I am more than help with my experiences.

Peace :-)

---

### Post by fictivetoast on 2009-09-12
> **jacktow said:**
> Once powertop is running, look at the line that starts with "Power Usage (ACPI estimate)" and tell us what yours is. Here's mine with WiFi and Bluetooth on and LCD brightness at ~50%:

**Power Usage (ACPI estimate): 12.8W (5.0 hours)**

Mine with Wifi and Bluetooth and LCD at ~50% : 
**Consommation électrique (estimation ACPI) : 9,0W (5,5 heures)**
(I've already been on battery for 2 hours, so I can confidently extrapolate that to mean 7,5 hours)

Running ```
sudo /sbin/iwconfig wlan0 power on
``` makes a huge difference, easily saves at least 3W.  Powertop regularly estimates 7 to 8,5 hours for me if the battery's fully charged. In idle, it'll dip to 8,7W ; with general usage (openoffice, firefox, gnome-do, empathy) it usually hovers at 9W and rarely exceeds 10.5W  I'm on Karmic, which may be helping a bit too.

---

### Post by rogerw05465 on 2009-09-12
> **marcw said:**
> It's possible you have the same problem I had.  I couldn't get the recommended solution (installing l1e atheros module) to work either.  Then I discovered that my Atheros chip isn't an l1e - it's an l1c.  If you do an lspci command and see that your ethernet controller is an Attansic device 1063, you've got an l1c chip also.  I found the solution for this chip in a Radhat forum:  [https://bugzilla.redhat.com/show_bug.cgi?id=514069](https://bugzilla.redhat.com/show_bug.cgi?id=514069) .  Comments #3 and #4 provide a link for the correct module source for my l1c chip.  It compiles and works great!

My machine is is 3810t-6415.  Just running 9.04 for now.  Hope this helps someone else.  Now if I could get the suspend/resume thing to work...
Marcw, I have the same atl1c issue with an Acer 4810T, Attansic 1063. I got the new alt1c off the Redhat posting you noted, and thank you for that lead. 

Now, being not a total duffer but something of a noob to the deep stuff, I am not sure of the proper steps to: 1) backup what I have so I don't shoot my foot off, and 2) get this new driver in place for trial. Could you spell it out a bit? Thanks much.

---

### Post by marcw on 2009-09-12
> **rogerw05465 said:**
> Now, being not a total duffer but something of a noob to the deep stuff, I am not sure of the proper steps to: 1) backup what I have so I don't shoot my foot off, and 2) get this new driver in place for trial. Could you spell it out a bit? Thanks much.

Actually, that laptop is now a couple hundred miles away from me sitting in my son's dorm room so I can't tell you exactly what I did.  But iirc, I simply followed the included instructions (or readme?).  It seems to me that it creates a kernel module that probably got installed with a 'make install' command.  Or something like that.

As far as backing up, I'm not sure I follow you.  This module will simply get your ethernet working.  I'm not sure what would need backing up.  Your ethernet doesn't work now, correct?  What's the worst that could happen if you really botched something. It still wouldn't work.  Then you would uninstall the module.

---

### Post by Ashrael on 2009-09-13
So.... I took the 4810TG back and got a brand new one....
SAME PROBLEM!!?? 
How come I can only find ONE other person with the same error? What are the chances I got two identical faulty machines? I am currently downloading the newest iso from ubuntu site to check if it might be a faulty cd. I do not really believe that this is the case, i tried 8.10, 9.04 and 9.10 cd's. OIt might be the type of cdrom (not recognized) otherwise I think it must be a software problem.

LSHW (extract): 
*-cdrom UNCLAIMED
                description: SCSI CD-ROM
                product: DVD-RAM UJ862AS
                vendor: MATSHITA
                physical id: 1
                bus info: scsi@4:0.0.0
                version: 1.00
                capabilities: removable
                configuration: ansiversion=5

Is it different from yours? Please tell..

Oh, I saw a message in Vista that said that it had disconnected the cdrom drive from power to save energy, might this be the problem? Because when I power up the machine, the FIRST cd always works, after that it starts spewing errors.

Also: does anyone know if there is bluetooth module in the 4810TG that is not connected/functional? I heard that it is installed by default. One of the tricks Acer supposedly does is changing the hardware vendor id (VID) and device id in the bluetooth module... I think this might be true, because I saw, upon installing Vista on an Acer, that the module came online and was ready to connect (it said so), but after the Acer software was installed I could not find the device anymore.

Any suggestions are welcome...

AARGH! I bought this timeline to be used with Ubuntu, not Vista...:(

---

### Post by PatrickVogeli on 2009-09-13
My girlfriend has bought a Packard Bell Dot M/U Sp 002, with 2gb ram, 250gb HDD, Intel Core 2 Solo U3500, the Attansic Lan and Intel 5100 wifi. This one is a 11.6" laptop, and seems to be a cheap version of the Timeline 1810T, and I'm pretty it shares a lot of things with the 3810.

What I've done: I've compiled a 2.6.30.5 kernel with PHC (processor undervolting) and Tux On Ice (faster and better hibernating) support, and all is just working fine. With the stock kernel, I had the issue that, after hibernating, on resume the system would power off, but I tried the 2.6.31-rc9 from the mainline PPA and that was solved. After that, I compiled the .31 kernel with the mentioned patches, and everything seems to be working fine.

The only issue now is the touchpad: locking works fine, but unlocking "won't". After playing a bit, I realized that pressing the FN button 2 or 3 times and then unlock or keeping the Fn button pressed for a few seconds and then also press the unlock one would work. So, the issue seems to be with the FN button. But it works, so I guess it's fine.

Powersaving and so on is fine too, since powertop reports an average of 9W doing normal stuff.

By the way, there was a Store here (similar to Walmart in the US, more les) which used to have the 3810T and, the stickers on the laptop, used to show 8+ hours of battery live. After sometime without having one (2 weeks maybe) yesterday we saw they had it again, but the sticker was different: 6+ hours "only".

---

### Post by quail-linux on 2009-09-13
@**Ashrael** I not sure what is going on with your cdrom / dvdrom, but here is what my cdrom is.
```

           *-cdrom
                description: DVD-RAM writer
                product: CDDVDW TS-U633A
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: AC01
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc

```

---

### Post by Ashrael on 2009-09-13
@quail-linux: 

I found a lot of posts about matSHITa drives and the UN-availability of newer/better firmware....so.
I decided to go and ask acer for a tsscorp replacement I guess, no way of knowing yet what they will say....
Or: linux/ubuntu learns how to use this drive properly: It works very well in Vista....
In the mean time I will not use this machine for ubuntu...sad.
I will keep on tweaking it for battery performance though, also goes for touchpad disable/enable button and brightness of screen....

thanks again for posting!

---

### Post by quail-linux on 2009-09-13
@ **Ashrael**

I had a MATSHITA cdrom in my old Acer laptop and it worked fine np under Ubuntu and Debian for 3 years.  I can't test the details of the cdrom on that laptop as I sold it to help pay for this laptop.

---

### Post by quail-linux on 2009-09-13
> **Ashrael said:**
> 
<snip ...>

Also: does anyone know if there is bluetooth module in the 4810TG that is not connected/functional? I heard that it is installed by default. One of the tricks Acer supposedly does is changing the hardware vendor id (VID) and device id in the bluetooth module... I think this might be true, because I saw, upon installing Vista on an Acer, that the module came online and was ready to connect (it said so), but after the Acer software was installed I could not find the device anymore.

Any suggestions are welcome...

AARGH! I bought this timeline to be used with Ubuntu, not Vista...:(

Have you tried using Fn + F3 (this the key combo on my 4810T) to see if you can turn the bluetooth on or off and see if you get the bluetooth icon on the gnome panel

Also can you run this command to see if the bluetooth is about:
```
lsusb -v | grep -E '\<(Bus|iProduct|bDeviceClass|bDeviceProtocol)' 2>/dev/null
```
Here the output for mine:
```

Bus 001 Device 002: ID 0a5c:2151 Broadcom Corp. 
  bDeviceClass          224 Wireless
  bDeviceProtocol         1 Bluetooth
  iProduct                2 BCM2046 Bluetooth Device

```

---

### Post by Nixblicker on 2009-09-14
Hello guys,

i also bought one of the 3810T (Duo core SU9600 version) last week and i haven't been able to install a running Ubuntu system so far, although i tried it two times already.

Both times i sticked to the suggestions that had been made around page 15-18, the step by step guide of how to install Ubuntu on this machine.
One problem occured, or at least i think so, flashing the Bios to version 1.10. I started the process after downloading the tool from the official website, went away for a moment while it proceeded and found my system hanging with black screen when i came back. I thought i bricked it already, but after a hard reset (i also had to remove the battery to make it restart again) i found that my worst expectations haven't had become reality - the bios claimed to be at v1.10 and my system booted up again. 
So, after reinstalling Vista via the recovery DVDs, cause PartedMAgic (or me) had screwed up to remove the recovery partition and then moving the vista partition over to the newly freed space i tried to proceed with the Jaunty 64bit installation as suggested in this thread.
And because people who had obviously been successful installing the system weren't very clear about the point, if the IDE or AHCI settings was active during the installation process, i tried either way but in both ways ended up with highly corrupted filesystems after a couple of restarts. For example, after a while ext2fsck kicked in and "corrected" my root filesystem the way it was completely useless afterwards, making /var a datafile with the same name to name just one of the observed oddities.
Before this happened, i tried to apply the grub settings suggested by one user "libata.force=noncq", but this didn'nt seem to have any effect as the bootup process was still incredibly slow and a lots of ata2.0 warnings mentioning ncq were produced.

Well, i don't wanna bore you with my experiences, but would like to ask all of you who successfully installed a running _64bit_ system, either karmic or jaunty on the _3810T_ with the Hitachi disk drive HTS545032B9A300 (320GB) of how they did it, which bios settings they used _during_ and _after_ installation concerning the Ahci/IDE switch and what they possibly did to avoid the ata problems.

Thank you very much for reading this and for probable solution hints,

Cheers Nix

Edt.:

Meanwhile i tried to use the alternate karmic 64bit CD via unetbootin in the hope to somehow circumvent the above ata errors and still determine the partitioning myself, like e.g. have /home on a different partition than root. but obviously i can't continue the installation from the usb drive without a running internet connection that i cannot set up, because neither the lan nor the wifi card is recognized. Is that a new feature? Does one of you know a way to circumvent this behaviour?

---

### Post by Migou67 on 2009-09-14
--

---

### Post by JaimeJB on 2009-09-14
Hi all.
I have an ACER 3810t, with an Intel Core Solo CPU 1.4Ghz and 320 GB of HD (ATA Hitachi HTS545032B9A300)

I installed Ubuntu along with the vista partition and the recovery partition that came with the laptop, then I did a backup image of the windows partition following this: [http://kuparinen.org/martti/comp/windows/backup.html](http://kuparinen.org/martti/comp/windows/backup.html)
That backup partition worked fine.

Later on I tried to format the laptop to keep just Ubuntu on it (BIG mistake ](*,) ). I also copied the backup image I had of vista on another partition, but I couldn´t load it from the grub.

The result is that now I do not have any OS on the laptop, since I can not load the Vista partition and Ubuntu doesn´t work either.

I have tried installing Windows XP and several Unix flavors (ubuntu, debian, linux mint, free bsd). Regarding just Ubuntu I have tried with the 9.04 and 9.10 Alpha 5 and none worked. I tried also switching to IDE mode, it didn't work either. 

The only thing that works is the live cd from the usb.

Does anyone with the very same laptop as mine managed to install **anything whatsoever **on the laptop? Could that someone please help me out? [-o<

Thank you very much.

---

### Post by Migou67 on 2009-09-14
Jaime,

Can you explain which error you have ?

Do you have the boot loader GRUB working ?

Did you get an error message when loading the kernel ?

Did you try to start the installation from your USB stick live CD ?

You have to describe when the problem appear and what append 
with more details ...

Regards,
Pat.

---

### Post by Migou67 on 2009-09-14
Hello Nixblicker,

I have the same disk as you in my 4810T !

# hdparm -I /dev/sda
/dev/sda:
ATA device, with non-removable media
    Model Number:       Hitachi HTS545032B9A300                 
    Serial Number:      090604PB5306Q6C09TEG
    Firmware Revision:  PB3OC60F

I have no problem with a 32 bits 9.10 Alpha 5. I have only 2 partitions / and SWAP.

If the raison of using a 64 bits version is for the 4 gigas memory , you can install trough
the synaptic the 32 bits kernel server which include the extended memory management.

Hope this help.

Regards.
Pat.

---

### Post by JaimeJB on 2009-09-14
1.- Grub loads fine, then I do CTR + ALT + F1 and wait until I get initramfs (cause it can not find the root device), I type exit and I get:
Kernel panic - not syncing: Attempted to kill init
drm:intelfb_panic ERROR panic ocurred, switching back to text console.

2.- With IDE mode I get:
PXE_M0F: Exiting Intel PXE ROM
No bootable device -- insert boot disk and press any key.

3.- From the USB (done using Unetbootbin) it works fine.

In the case of the Vista partition that I tried to recover, I copied byte to byte and then added it to the grub menu, but I just get a blinking "_" when I select it in grub.

Also, I would appreciate to read a comprehensive explanation of the steps taken to install Ubuntu by someone with the same laptop as mine.

Thanks for the help again.

---

### Post by Nixblicker on 2009-09-15
> **Migou67 said:**
> 
I have no problem with a 32 bits 9.10 Alpha 5. I have only 2 partitions / and SWAP.

If the raison of using a 64 bits version is for the 4 gigas memory , you can install trough
the synaptic the 32 bits kernel server which include the extended memory management.

Thank you very much for your suggestion, Pat.

Did you use the Alternate or the Desktop CD to install this?
What setting did you use in the Bios concerning ata - IDE or AHCI?

I try to install the 64 bit system because i think it makes some better use of the 2 Cores i have and of the 4 Gig too. I read somewhere that the core solo version should better be used with 32bit, but 64bit would be better for the core duo variants. 
Furthermore, i have problems to believe that the ata errors are related to the 32/64 bit issue but more to the correct controller driver and/or right specifications of the hard drive.
I think our Hitachi disk has an issue with the NCQ, and hasn't been listed to the blacklist of the controller driver.
But in order to settle this problem, i believe i must somehow install a working system (Bios setting IDE/AHCI?) and then use the workarounds mentioned earlier in this thread, like "libata.force=noncq" or add my drive to the blacklist somehow.

Any suggestions are still very appreciated,
Thank you!

Nix

---

### Post by Migou67 on 2009-09-15
Hello Nixblicker,

As I wrote in the 4810T thread:
I started the windows installation just to flash the laptop to the latest 1.28 bios
and checked the hardware. (You can do that also without windows)

Downloaded the Ubuntu 9.10 Alpha 5 32 Bits and created a USB startup disk with the ISO. (The Desktop CD)

Removed everything on the disk and installed Ubuntu with default partition's.

A full update of the Ubuntu as been done after.

_I don't have changed the BIOS parameter_ for the disk to IDE, as by default is AHCI
and I have no problem whit that on my Hitachi 320 Gigas.

Working out of the box :
Wifi, Bluetooth, Video card, Sound, Touch pad, sensor key's and FN, Gnome Power save (CPU scaling),DVD, Batterie indicator, Lan Gigabit, USB, WEB CAM.

Not tested :
Card reader.

Not working for the moment for me :
-Microphone recording.
-FN key for brightness , it work but Ubuntu stop responding !
I put my preferred setup in /etc/rc.local -> setpci -s 00:02.0 F4.B=**50**
-Suspend some time work another time not.
-Button for disabling the touch pad work but you never get it back :smile:

About the performance of dual core , its the same , I have a 17'' Toshiba with dual core
and 4 gigas RAM, the 32 bits version run very smooth with the kernel server and I see all memory. 64 bits is for large adressing not for speed , in many case if you don't have strong algorithm you will decrease your performances because you have more data to manipulate. And nothing to do with multitasking or multithread, no impact at all !

Sorry,I try just now and _this pacakges are note available_ in DesktopPC 9.10 Alpha 5, may be later in final release ?
[I]"just go to the synaptic and search (not quick search) for server, in the list scrool to  linux  and select:
linux-server
linux-image-2.6.xxx-server
linux-headers-2.6.xxx-server
Or by command line (easy way):
$ sudo apt-get update
$ sudo apt-get install linux-headers-server linux-image-server linux-server
$ sudo reboot[/I] "

Regards.
Pat.

---

### Post by Migou67 on 2009-09-15
Hello Jaime,

I think something is wrong  with the BIOS.

Have you updated to the latest bios your Timeline ? (you must do that)

If you have already done the update, can you try a factory default reset 
of your bios and try again?

*PXE* is the network device, check the bios boot order as it looks as if it ...

Try a full format of your disk with the live CD and install with default partitions or do a "fsck /dev/sda".

I hope you find a solution or maybe you have to wait for a new bios or Unbuntu release !

Regards.
Pat.

---

### Post by Nixblicker on 2009-09-15
@ Pat

Wow, thank you very much for that detailed report.
Although the different bios versions might still be a issue and possible sources of dissimilarities of our systems, this is exactly what i asked for.
I will give the 32bit version a try on the weekend, as i'm away on a summerschool in the moment and can't risk running into any unbootable system situation again.

Again, thanks a lot for your efforts - i'll report back when its done!

Bye, Nix

---

### Post by Migou67 on 2009-09-15
Nixblicker,

I think you right , it's possibly a bios or controller version  issue, may be the disk firmware too ...

A new bios or Ubuntu release can solve this issue.

Regards.
Pat.

---

### Post by JaimeJB on 2009-09-15
Hi, 
thanks for the help Pat. I am afraid I haven´t updated to the latest BIOS, I understand that the file is "BIOS_Acer_1.10_A_AS3410 AS3810.zip" on the ACER website. Is it possible to update from the LiveUSB? how would the process be? (I am gonna check in  [http://www.netbooktech.com/tag/acer-aspire-one-bios-update-instructions/](http://www.netbooktech.com/tag/acer-aspire-one-bios-update-instructions/))

Right after that I will try to install Ubuntu using Unetbootbin.

Thanks a lot!

---

### Post by Migou67 on 2009-09-15
Hi Jaime,

Your bios file BIOS_Acer_1.10_A_AS3410 AS3810.zip look's good for a 3810T,
and yes you can update from a live USB, you have the response from [norkakn]("http://ohioloco.ubuntuforums.org/member.php?u=697574") here
[http://ubuntuforums.org/showthread.php?t=1165087&page=11]("http://ohioloco.ubuntuforums.org/showthread.php?t=1165087&page=11")
     
Quote:
                                                                      [SIZE=1]Originally Posted by **gotosk**                     [[IMG]http://ohioloco.ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ohioloco.ubuntuforums.org/showthread.php?p=7603365#post7603365")[/SIZE]                 
                 *[SIZE=1]How can I update my BIOS under Ubuntu? BIOS file on Acer website are executable file for Windows. For updating, I think I should run into DOS first, and use a usb stick, run flash.bat. Oops,It's a lot work to do... [/SIZE]-_-*
                                 
[http://www.netbooktech.com/tag/acer-...-instructions/]("http://www.netbooktech.com/tag/acer-aspire-one-bios-update-instructions/")

Except use the proper BIOS update.  Make sure to select "Live CD Only"

---

### Post by idreamer on 2009-09-16
Hi, I isn't a ubuntu user but achlinux user and don't write in eglish very well. This post is the best post on 3810T but is very big. I'm lost!
it's possible make a summery?
3810t suspend?
intel glxgear fps lower?
audio boost?
thanks
Ale

---

### Post by JaimeJB on 2009-09-19
Alright, now I am writing from the Ubuntu 9.10 in the 3810t.

The steps taken are:
1.) Make a backup of the Vista partitions (in case everything works fine in the future).
2.) Install last acer BIOS.
3.) Install Ubuntu 9.10 Alpha 5 from Usb using Unetbootbin
4.) Change to IDE mode on the BIOS. (otherwise it takes ages to boot, IF it boots at all)


Even though, I still have some unresolved problems:
No audio.
No right click on touch pad.
Problems with Suspend.
No extensions on firefox (Ubuntu 9.10 issue).


Still, thanks for the help, since at least now I have something running on the laptop :)

---

### Post by Sashin on 2009-09-19
Anyone got any multitouch features to work, like two finger scrolling and right click? Or three finger middle click?

---

### Post by robson9776 on 2009-09-19
Hi,

I also just got this laptop last week... just because I can't wait to 9.10, I installed 9.04 and do this following instructions :

[https://help.ubuntu.com/community/AspireTimeline/Fixes](https://help.ubuntu.com/community/AspireTimeline/Fixes)

to solve wired LAN issue and it works like a charm.
but, when I boot 2.6.30 kernel to solve reboot and shut down issue, the wired LAN isn't detected. 

and when I tried to re-install the LAN driver, I got this error :

[I]robson@robson-laptop:~/Desktop/src$ make
make -C /lib/modules/2.6.30-020630-generic/build SUBDIRS=/home/robson/Desktop/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.30-020630-generic'
  CC [M]  /home/robson/Desktop/src/atl1c_main.o
/home/robson/Desktop/src/atl1c_main.c: In function ‘atl1c_intr’:
/home/robson/Desktop/src/atl1c_main.c:1635: error: expected expression before ‘;’ token
/home/robson/Desktop/src/atl1c_main.c:1649: error: expected expression before ‘;’ token
/home/robson/Desktop/src/atl1c_main.c:1673: error: expected expression before ‘;’ token
/home/robson/Desktop/src/atl1c_main.c:1703: warning: ‘return’ with a value, in function returning void
/home/robson/Desktop/src/atl1c_main.c: In function ‘atl1c_request_irq’:
/home/robson/Desktop/src/atl1c_main.c:2345: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
make[2]: *** [/home/robson/Desktop/src/atl1c_main.o] Error 1
make[1]: *** [_module_/home/robson/Desktop/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.30-020630-generic'
make: *** [default] Error 2[/I]

and this...

[I]robson@robson-laptop:~/Desktop/src$ sudo make install
[sudo] password for robson: 
make -C /lib/modules/2.6.30-020630-generic/build SUBDIRS=/home/robson/Desktop/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.30-020630-generic'
  CC [M]  /home/robson/Desktop/src/atl1c_main.o
/home/robson/Desktop/src/atl1c_main.c: In function ‘atl1c_intr’:
/home/robson/Desktop/src/atl1c_main.c:1635: error: expected expression before ‘;’ token
/home/robson/Desktop/src/atl1c_main.c:1649: error: expected expression before ‘;’ token
/home/robson/Desktop/src/atl1c_main.c:1673: error: expected expression before ‘;’ token
/home/robson/Desktop/src/atl1c_main.c:1703: warning: ‘return’ with a value, in function returning void
/home/robson/Desktop/src/atl1c_main.c: In function ‘atl1c_request_irq’:
/home/robson/Desktop/src/atl1c_main.c:2345: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
make[2]: *** [/home/robson/Desktop/src/atl1c_main.o] Error 1
make[1]: *** [_module_/home/robson/Desktop/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.30-020630-generic'
make: *** [default] Error 2
[/I]
what's wrong? can't I re-install the driver?

---

### Post by JaimeJB on 2009-09-19
Hi,
I am wondering if anyone has managed to call with SKYPE.
The audio works fine, but the laptop's microphone doesn't. (I have a 3810t)
I have been playing a bit with "pavumeter" and "pavucontrol" but no success.

Thanks again for the help.

---

### Post by odLott on 2009-09-19
Just got a 3810T-6415 and used a usb stick to try Ubuntu 9.04 i386 with the live CD. I was surprised by how well it worked. The wlan driver was detected correctly as was my resolution. I did notice a problem with Suspend/Resume. It suspends fine, but upon resuming, it shuts down straight away.

Don't really have time to install it yet, but will keep an eye on this thread and see how people get it to work.

---

### Post by quail-linux on 2009-09-20
> **robson9776 said:**
> Hi,

I also just got this laptop last week... just because I can't wait to 9.10, I installed 9.04 and do this following instructions :

[https://help.ubuntu.com/community/AspireTimeline/Fixes](https://help.ubuntu.com/community/AspireTimeline/Fixes)

to solve wired LAN issue and it works like a charm.
but, when I boot 2.6.30 kernel to solve reboot and shut down issue, the wired LAN isn't detected. 

and when I tried to re-install the LAN driver, I got this error :

[I]robson@robson-laptop:~/Desktop/src$ make
make -C /lib/modules/2.6.30-020630-generic/build SUBDIRS=/home/robson/Desktop/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.30-020630-generic'
  CC [M]  /home/robson/Desktop/src/atl1c_main.o
/home/robson/Desktop/src/atl1c_main.c: In function ‘atl1c_intr’:
/home/robson/Desktop/src/atl1c_main.c:1635: error: expected expression before ‘;’ token
/home/robson/Desktop/src/atl1c_main.c:1649: error: expected expression before ‘;’ token
/home/robson/Desktop/src/atl1c_main.c:1673: error: expected expression before ‘;’ token
/home/robson/Desktop/src/atl1c_main.c:1703: warning: ‘return’ with a value, in function returning void
/home/robson/Desktop/src/atl1c_main.c: In function ‘atl1c_request_irq’:
/home/robson/Desktop/src/atl1c_main.c:2345: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
make[2]: *** [/home/robson/Desktop/src/atl1c_main.o] Error 1
make[1]: *** [_module_/home/robson/Desktop/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.30-020630-generic'
make: *** [default] Error 2[/I]

and this...

[I]robson@robson-laptop:~/Desktop/src$ sudo make install
[sudo] password for robson: 
make -C /lib/modules/2.6.30-020630-generic/build SUBDIRS=/home/robson/Desktop/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.30-020630-generic'
  CC [M]  /home/robson/Desktop/src/atl1c_main.o
/home/robson/Desktop/src/atl1c_main.c: In function ‘atl1c_intr’:
/home/robson/Desktop/src/atl1c_main.c:1635: error: expected expression before ‘;’ token
/home/robson/Desktop/src/atl1c_main.c:1649: error: expected expression before ‘;’ token
/home/robson/Desktop/src/atl1c_main.c:1673: error: expected expression before ‘;’ token
/home/robson/Desktop/src/atl1c_main.c:1703: warning: ‘return’ with a value, in function returning void
/home/robson/Desktop/src/atl1c_main.c: In function ‘atl1c_request_irq’:
/home/robson/Desktop/src/atl1c_main.c:2345: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
make[2]: *** [/home/robson/Desktop/src/atl1c_main.o] Error 1
make[1]: *** [_module_/home/robson/Desktop/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.30-020630-generic'
make: *** [default] Error 2
[/I]
what's wrong? can't I re-install the driver?

Hi,

Have a read here to correctly compiling the atl1e driver[1], with the 2.6.30 kernel and above you have to alter one of the files called 'kcompat.h' in the src directory.

[1] [http://quail.southernvaleslug.org/webblog/archives/105](http://quail.southernvaleslug.org/webblog/archives/105)

---

### Post by quail-linux on 2009-09-20
> **JaimeJB said:**
> Hi,
I am wondering if anyone has managed to call with SKYPE.
The audio works fine, but the laptop's microphone doesn't. (I have a 3810t)
I have been playing a bit with "pavumeter" and "pavucontrol" but no success.

Thanks again for the help.

Hi,

I have Skype working under Debian 5.0.3, but I don't have Pulse Audio installed. The thing I had to alter under 'Options => Sound Devices' is the 'Sound In' to 'HDA Intel (hw:Intel,0)'

---

### Post by miegiel on 2009-09-20
> **Sashin said:**
> Anyone got any multitouch features to work, like two finger scrolling and right click? Or three finger middle click?

Yes, though the touchpad firmware doesn't suport *two-finger-scrolling* it does support *pinching*. If you run ```
synclient -m 10
``` in a terminal you can see the touchpad output. The **f** column is the number of fingers and the **w** column is the distance between your 2 fingers.

To use the width to simulate 2 fingers you need to install the latest [_Synaptics TouchPad driver_]("http://packages.debian.org/sid/xserver-xorg-input-synaptics") from debian-sid (is already included in karmic) and add some lines to */etc/hal/fdi/policy/preferences.fdi*

```
sudo nano /etc/hal/fdi/policy/preferences.fdi
```
Add the black lines, if you don't have a *preferences.fdi* file just make one including the red lines.
```
[COLOR="Red"]<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<!--
  Some examples how to use hal fdi files for system preferences
  You can either uncomment the examples here or put them in a seperate .fdi
  file.
-->
<deviceinfo version="0.2">
<!--
  The following shows how to hint gnome-volume-manager and other programs
  that honor the storage.automount_enabled_hint to not mount non-removable
  media.
-->
<!--
  <device>
    <match key="storage.hotpluggable" bool="false">
      <match key="storage.removable" bool="false">
        <merge key="storage.automount_enabled_hint" type="bool">false</merge>
      </match>
    </match>
  </device>
-->[/COLOR]
  <device>
    <match key="info.capabilities" contains="input.touchpad">
      <merge key="input.x11_options.SHMConfig" type="string">On</merge>
      <merge key="input.x11_options.EmulateTwoFingerMinZ" type="string">4</merge>
      <merge key="input.x11_options.EmulateTwoFingerMinW" type="string">7</merge>
      <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
      <merge key="input.x11_options.VertEdgeScroll" type="string">0</merge>
    </match>
  </device>
[COLOR="Red"]</deviceinfo>[/COLOR]
```

You might want to try different *MinZ* and *MinW* values from the ones I use. *synclient -m 10* should help with finding the right values for you. (you need to reboot after changing *preferences.fdi*)

It will never work as well as real multitouch, you get scroll jumps when the 2nd finger touches the pad. but it's better than single touch :)

A thread on this topic with more (in depth) info : [http://ubuntuforums.org/showthread.php?p=7253159#post7253159](http://ubuntuforums.org/showthread.php?p=7253159#post7253159)

---

### Post by miegiel on 2009-09-20
Here are some pics of the timeline 3810T's guts :twisted:

There's an extra SATA connection for a really small disk between the card-reader and the USB ports. And a free slot for a PCIe card that you can reach after removing the keyboard.

The last picture is of a card slot I found on the motherboard. You can reach it from the outside behind the battery, right next to the battery connector. I've got no idea what it's for. It's got to many contacts and they are to far apart for a sim card.

---

### Post by quail-linux on 2009-09-20
@**miegiel** nice pics, thanks for the them, as for the last pic the 2x4 connector slot I am at a lose to what it is.  When I get a chance to pull my 4810T apart I will post pics of it.

---

### Post by Nordfjord on 2009-09-20
@miegiel: That's excellent!

Any idea how I'd be able to enable tap-to-click? It's enabled in the options (the mouse config Gui), but not working in practice.

---

### Post by cyberfish on 2009-09-20
> **Nordfjord said:**
> @miegiel: That's excellent!

Any idea how I'd be able to enable tap-to-click? It's enabled in the options (the mouse config Gui), but not working in practice.

For 9.04, you need to issue a synclient command (forgot exactly what, google it up).

For 9.10, the gnome option works as it should.

---

### Post by miegiel on 2009-09-20
> **Nordfjord said:**
> @miegiel: That's excellent!

Any idea how I'd be able to enable tap-to-click? It's enabled in the options (the mouse config Gui), but not working in practice.

Try adding the blue lines, I discovered I didn't need them (in karmic). Inspred by what **cyberfish** posted, I guess you do need them in jaunty.

And to all who mis their easy select and paste 3rd mouse button. The green lines make a 3rd mouse button of all the corners of your touchpad. But you don't need to use all 4 corners of course :twisted:

```
[COLOR="Red"]<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<!-- 
  Some examples how to use hal fdi files for system preferences 
  You can either uncomment the examples here or put them in a seperate .fdi
  file.
-->
<deviceinfo version="0.2">
<!-- 
  The following shows how to hint gnome-volume-manager and other programs 
  that honor the storage.automount_enabled_hint to not mount non-removable
  media.
-->
<!--
  <device>
    <match key="storage.hotpluggable" bool="false">
      <match key="storage.removable" bool="false">
        <merge key="storage.automount_enabled_hint" type="bool">false</merge>
      </match>
    </match>
  </device>
-->[/COLOR]
  <device>
    <match key="info.capabilities" contains="input.touchpad">
      <merge key="input.x11_options.SHMConfig" type="string">On</merge>
[COLOR="Blue"]      <merge key="input.x11_options.TapButton1" type="string">1</merge>
      <merge key="input.x11_options.TapButton2" type="string">2</merge>[/COLOR]
      <merge key="input.x11_options.EmulateTwoFingerMinZ" type="string">4</merge>
      <merge key="input.x11_options.EmulateTwoFingerMinW" type="string">7</merge>
      <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
      <merge key="input.x11_options.VertEdgeScroll" type="string">0</merge>
[COLOR="Lime"]      <merge key="input.x11_options.LTCornerButton" type="string">2</merge>
      <merge key="input.x11_options.RTCornerButton" type="string">2</merge>
      <merge key="input.x11_options.LBCornerButton" type="string">2</merge>
      <merge key="input.x11_options.RBCornerButton" type="string">2</merge>[/COLOR]
    </match>
  </device>
[COLOR="Red"]</deviceinfo>[/COLOR]
```

---

### Post by cyberfish on 2009-09-21
Found another power saving tip here -
[http://ubuntuforums.org/showthread.php?t=999646](http://ubuntuforums.org/showthread.php?t=999646)

> ```

for i in {0..5}; do echo host$i result:; sudo sh -c "echo 'min_power' > /sys/class/scsi_host/host$i/link_power_management_policy"; cat /sys/class/scsi_host/host$i/link_power_management_policy; done

```

For me, the result is
> 
host0 result:
max_performance
host1 result:
min_power
host2 result:
min_power
host3 result:
min_power
host4 result:
max_performance
host5 result:
max_performance

Saves ~1-1.5W.

---

### Post by Nixblicker on 2009-09-21
Hi all,

it's me again. I don't know what i am doing wrong. 
Also my third attempt to get a Ubuntu to work on my 3810T Core Duo failed with the typical ata2.0 errors i also got in the previous ones. 
This time it was a Karmic 32bit daily build installed from USB via Unetbootin. The Live System worked flawlessly, so i tried installing it from there and ended up with an unbootable system again. First the system complains about various ata2.0 ncq issues and after more than 5 min just stops working while trying to load some services.
I really must have missed something important in the procedure - i don't understand, why i seem to be the only one who has this continuous problems with the hard drive and the ata controller. 
I wonder first, why this ata2 issue seems to be resolved for all who used karmic builds in this thread except me and if those used the suggestions to use libata.force=ncq as grub start option made by one user earlier.
In my previous attempts with Jaunty this didnt't seem to have a effect at all, but at least i could try this from a running system before it got wacked by ext2fsck.

Please help me guys, i don't want to bother with this ill MS Vista sh.. any more.:( 

May i ask you for the following confirmations:
[LIST]
[*]All of you with a running Ubuntu on a 3810T do not have ata2.0 error messages during bootup,
[*]... and you didn't care about any Bios setting concerning Ahci/IDE before and after the installation,
[*]...and you don't start your system with any extra grub boot options like noacpi or noncq,
[*]and you installed it via USB and not via a Mobile CDRom drive?
[/LIST]

I have no idea to proceed from here, please point me in the right direction.
If you need further information, just let me know!

Thank you and have a good night,

Nix

---

### Post by marcw on 2009-09-21
> **Nixblicker said:**
> 
May i ask you for the following confirmations:
[LIST]
[*]All of you with a running Ubuntu on a 3810T do not have ata2.0 error messages during bootup,
[*]... and you didn't care about any Bios setting concerning Ahci/IDE before and after the installation,
[*]...and you don't start your system with any extra grub boot options like noacpi or noncq,
[*]and you installed it via USB and not via a Mobile CDRom drive?
[/LIST]


I too have a 3810t (6415) and installed my 64bit 9.04 from a mobile CD player.  I changed nothing in the bios nor did I add anything to grub.  Everything works fine except for resume from S3.

---

### Post by cyberfish on 2009-09-21
> **Nixblicker said:**
> Hi all,

it's me again. I don't know what i am doing wrong. 
Also my third attempt to get a Ubuntu to work on my 3810T Core Duo failed with the typical ata2.0 errors i also got in the previous ones. 
This time it was a Karmic 32bit daily build installed from USB via Unetbootin. The Live System worked flawlessly, so i tried installing it from there and ended up with an unbootable system again. First the system complains about various ata2.0 ncq issues and after more than 5 min just stops working while trying to load some services.
I really must have missed something important in the procedure - i don't understand, why i seem to be the only one who has this continuous problems with the hard drive and the ata controller. 
I wonder first, why this ata2 issue seems to be resolved for all who used karmic builds in this thread except me and if those used the suggestions to use libata.force=ncq as grub start option made by one user earlier.
In my previous attempts with Jaunty this didnt't seem to have a effect at all, but at least i could try this from a running system before it got wacked by ext2fsck.

Please help me guys, i don't want to bother with this ill MS Vista sh.. any more.:( 

May i ask you for the following confirmations:
[LIST]
[*]All of you with a running Ubuntu on a 3810T do not have ata2.0 error messages during bootup,
[*]... and you didn't care about any Bios setting concerning Ahci/IDE before and after the installation,
[*]...and you don't start your system with any extra grub boot options like noacpi or noncq,
[*]and you installed it via USB and not via a Mobile CDRom drive?
[/LIST]

I have no idea to proceed from here, please point me in the right direction.
If you need further information, just let me know!

Thank you and have a good night,

Nix

Did you have a look at the wiki?
[https://help.ubuntu.com/community/AspireTimeline/Fixes](https://help.ubuntu.com/community/AspireTimeline/Fixes)

It seems like you need to either change AHCI to IDE, or use noncq.

I don't have the problem myself (I have the SSD version), so no first-hand experience.

There shouldn't be a difference installing from USB or CD. I used unetbootin.

---

### Post by Sashin on 2009-09-22
Hey, the multitouch scrolling script works fine, but does anyone know if it can be applied to right and middle clicks as well as scrolling.

---

### Post by Nordfjord on 2009-09-22
Anyone played with 9.10 alpha 6 yet? I was having some serious problems with it -- booted the first time pretty fine, a little rough around the edges (CUPS gave me an error) but not bad. Second time I tried to boot, got a black screen and nothing. So I downgraded back to 9.04 (aka, chickened out).

Someone out there's gotta be having better luck, huh?

---

### Post by miegiel on 2009-09-22
> **Nordfjord said:**
> Anyone played with 9.10 alpha 6 yet? I was having some serious problems with it -- booted the first time pretty fine, a little rough around the edges (CUPS gave me an error) but not bad. Second time I tried to boot, got a black screen and nothing. So I downgraded back to 9.04 (aka, chickened out).

Someone out there's gotta be having better luck, huh?

I've used karmic since alpha 3 or 4. It's a bumpy road sometimes :twisted: If you've got problems with karmic [_go to this sub-forum_]("http://ubuntuforums.org/forumdisplay.php?f=359"), often it's a bug more people are struggling with (and not really timeline related).

> **Sashin said:**
> Hey, the multitouch scrolling script works fine, but does anyone know if it can be applied to right and middle clicks as well as scrolling.

Heh, I turned them off. The lines below from the *.fdi* file set what the tap clicks should do (0=disable 1=left 2=middle 3=right). What I've done is set the "normal" 1 finger tap too my middle buton and then swap those buttons, making the left button below the pad my middle button and tap click my "normal" mouse click.

Stuff between <!-- stuff --> are notes.
```
      <merge key="input.x11_options.TapButton1" type="string">2</merge>           <!-- set tap-click to middle moue button, run 'xinput set-button-map "SynPS/2 Synaptics TouchPad" 2 1 3' to swap buttons 1 and 2 -->
      <merge key="input.x11_options.TapButton2" type="string">0</merge>           <!-- disable tap-click 2nd button, defalt=2=middle -->
      <merge key="input.x11_options.TapButton3" type="string">0</merge>           <!-- disable tap-click 3rd button, defalt=3=menu -->
```

---

### Post by Nixblicker on 2009-09-22
@ marcw 

> **marcw said:**
> I too have a 3810t (6415) and installed my 64bit 9.04 from a mobile CD player.  I changed nothing in the bios nor did I add anything to grub.  Everything works fine except for resume from S3.

Thank you for your comment. 
I don't know what is special on my system what causes this permanent problems. Do you also have the Hitachi disk drive HTS545032B9A300 (320GB) installed (see Bios or dmesg)?
@ cyberfish
> **cyberfish said:**
> 
Did you have a look at the wiki?
[https://help.ubuntu.com/community/AspireTimeline/Fixes](https://help.ubuntu.com/community/AspireTimeline/Fixes)
It seems like you need to either change AHCI to IDE, or use noncq.
I don't have the problem myself (I have the SSD version), so no first-hand experience.
There shouldn't be a difference installing from USB or CD. I used unetbootin.

Also thank you for commenting!
Yes, i had a look there and tried this options when i was booting my system, but the IDE setting was no real option for me, because this rendered Vista to be unusable and hence made researching this issue impossible, and the noncq grub setting didn't seem to have any effect at all on the boot process.
But thanks anyways!

@ all

Anyone else has an idea what i might try?
Did you all have the same Install-and-done experience like marcw has?

---

### Post by miegiel on 2009-09-22
> **cyberfish said:**
> Found another power saving tip here -
[http://ubuntuforums.org/showthread.php?t=999646](http://ubuntuforums.org/showthread.php?t=999646)



For me, the result is

Saves ~1-1.5W.

Finally running on battery with internet, time to try this. I must be doing something wrong. I guess I'll need to dig a bit deeper and put a bit more effort in it then a simple coppy and paste :roll:

```
usec@machine:~$ for i in {0..5}; do echo host$i result:; sudo sh -c "echo 'min_power' > /sys/class/scsi_host/host$i/link_power_management_policy"; cat /sys/class/scsi_host/host$i/link_power_management_policy; done
host0 result:
sh: cannot create /sys/class/scsi_host/host0/link_power_management_policy: Directory nonexistent
cat: /sys/class/scsi_host/host0/link_power_management_policy: No such file or directory
host1 result:
sh: cannot create /sys/class/scsi_host/host1/link_power_management_policy: Directory nonexistent
cat: /sys/class/scsi_host/host1/link_power_management_policy: No such file or directory
host2 result:
sh: cannot create /sys/class/scsi_host/host2/link_power_management_policy: Directory nonexistent
cat: /sys/class/scsi_host/host2/link_power_management_policy: No such file or directory
host3 result:
sh: cannot create /sys/class/scsi_host/host3/link_power_management_policy: Directory nonexistent
cat: /sys/class/scsi_host/host3/link_power_management_policy: No such file or directory
host4 result:
sh: cannot create /sys/class/scsi_host/host4/link_power_management_policy: Directory nonexistent
cat: /sys/class/scsi_host/host4/link_power_management_policy: No such file or directory
host5 result:
sh: cannot create /sys/class/scsi_host/host5/link_power_management_policy: Directory nonexistent
cat: /sys/class/scsi_host/host5/link_power_management_policy: No such file or directory
```

---

### Post by Sashin on 2009-09-22
I'm still confused, how do I set the width I want for right & middle click.

---

### Post by miegiel on 2009-09-22
> **Sashin said:**
> I'm still confused, how do I set the width I want for right & middle click.

It's this line :
```
      <merge key="input.x11_options.EmulateTwoFingerMinW" type="string">7</merge> <!-- set 2 finger emulation pinch width -->
```
To be more accurate. You don't set the width of the clicks, but the width of a touch that should trigger the 2 finger emulation.

I used
```
synclient -m 10
```
to measure the minimal width of 2 fingers next to each other (this minimizes scroll jumps when the 2nd finger is registered by the pad) and the maximum width of 1 finger. With my fingers that that gave me 8 and 6 so I set it to 7. I can also scroll with the side of my thumb :cool:

---

### Post by Nordfjord on 2009-09-22
How about this, miegiel? In Windows I was able to configure it so that a tap in the top-right corner of the trackpad acts as a right-click, a tap anywhere else acts as a left-click. Any ideas on how to do that? Or -- where are you getting your info about the synaptic driver from, so I can check it out (and save you the bother)?

Good work btw. :D

---

### Post by kwaanens on 2009-09-22
I'm thinking of getting this computer, but I'm wondering how it will feel compared to my existing notebook. My existing one is an MSI s262 12,1", 2 gb ram, 2 ghz core2duo cpu (T7200). ~ 2.5 years old

Any thoughts on this? I know the processor is slower, but there's twice as much memory, so maybe it will even itself out a little?
I have seen some talk about there being an SSD equipped version of this computer, but that will likely be too steep for me.

Use is mostly OO.o, using the web, accessing my private file server over LAN. I'm not compiling on a daily basis. I would like to continue using Compiz without *all* the bells and whistles, but would ideally like have the same or better experience with day to day use.

Any thoughts?

---

### Post by Nordfjord on 2009-09-22
The SU9400 is surprisingly quick, and the 4gb of ram will help. So IF your old laptop already doesn't have discrete graphics, you probably won't see a lot of change. If your lappy HAS discrete graphics, then it'll be a step down. But the 13" isn't going to be any more portable than a 12", even though it's thin. Right now I'm pretty sure that nobody's got anything above 4~5hr battery life with Ubuntu (to my knowledge), so don't expect an improvement there....

Unless you old laptop is BROKEN, I'd say stick with it. There's still a few kinks in Ubuntu on the Timeline, and by the sound of it you've got linux running on your old laptop. I'd like to push the Timeline, since I'm a fan, but in your case I can't really justify.... it's about the same portability, about the same speed, etc...

Edit: Oh, and in the US, the 80gb SSD version costs the same as the 500gb HDD version -- $800 (from Amazon).

---

### Post by kwaanens on 2009-09-22
Thanks for your reply!

My present computer has served me well, but is having its downsides:

- The speakers broke a year ago (nice one MSI, to have speaker cables pulled through the hinges on the laptop. Don't you realize those hinges are used more than a little?)
> The Timeline has its speakers where they should be, although I hear the hardware has reduced sound output

- The screen has more dead pixels than I'd like, and is not an LED
> The Timeline has a better screen, and it's not a bad idea to increase by an inch

- The HDD is 100 GB
> The Timeline has 5 times that

- Karmic tells me my battery may be broken. This might be a bug, but I'm suspecting I need to fork out NOK 700 (~ $100) to get a new battery. Also the battery has never given me more than 2 hours anyway
> No matter the kinks, the Timeline battery capacity will wipe the floor with my MSI


The portability is not much of an issue. I can live with an inch more, because having just measured it: Although the Timeline is 2 cm wider, it's almost 2 cm less deep. The MSI is 4 cm thick, while the Timeline is 2.9. The size of the MSI is due to the large battery sticking out in the back.
I'm pretty sure the Timeline is lighter too.

My main concern is that of CPU. I have read up on RAM and basically, with GNU/Linux, unless I keep a gazillion windows open at the same time, more RAM will just amount to more unused RAM.

How is the HDD speed on the 500 GB option? That might actually mean anything with regards to perceived speed. If there are several variants, how do they measure up with each other?

---

### Post by miegiel on 2009-09-22
> **Nordfjord said:**
> How about this, miegiel? In Windows I was able to configure it so that a tap in the top-right corner of the trackpad acts as a right-click, a tap anywhere else acts as a left-click. Any ideas on how to do that? Or -- where are you getting your info about the synaptic driver from, so I can check it out (and save you the bother)?

Good work btw. :D

The green lines in [_this post_]("http://ubuntuforums.org/showthread.php?p=7981583#post7981583") set the corner buttons to the middle mouse botton. Just change the 2 to what button you want the corner to be. 1=left click, 2=middle click, 3=right click, etc., 0=disable.

---

### Post by Nordfjord on 2009-09-22
@miegiel: Whoops, that was oblivious on my part. Thanks :D

---

### Post by marcw on 2009-09-22
> **Nixblicker said:**
> I don't know what is special on my system what causes this permanent problems. Do you also have the Hitachi disk drive HTS545032B9A300 (320GB) installed (see Bios or dmesg)?

It's 500GB.  I have no way to check the model since the laptop now lives in my son's dorm room a couple hundred miles from here.

---

### Post by tobik999 on 2009-09-23
@ [kwaanens]("http://ubuntuforums.org/member.php?u=22269"):
the SSD reads about 3 to 4 times faster than normale HDDs, writing is almost the same.

I guess the su9400 is faster than the old core duos, because ity is using the technology of the core2 duo, but i am not sure.

---

### Post by cyberfish on 2009-09-23
> **kwaanens said:**
> I'm thinking of getting this computer, but I'm wondering how it will feel compared to my existing notebook. My existing one is an MSI s262 12,1", 2 gb ram, 2 ghz core2duo cpu (T7200). ~ 2.5 years old

Any thoughts on this? I know the processor is slower, but there's twice as much memory, so maybe it will even itself out a little?
I have seen some talk about there being an SSD equipped version of this computer, but that will likely be too steep for me.

Use is mostly OO.o, using the web, accessing my private file server over LAN. I'm not compiling on a daily basis. I would like to continue using Compiz without *all* the bells and whistles, but would ideally like have the same or better experience with day to day use.

Any thoughts?

I have the Core 2 Solo version, and while Vista does feel a little sluggish, Ubuntu feels just the same as it does on my desktop (C2D @ 3ghz). Compiz runs flawlessly on the Intel integrated graphics. Clock for clock, I think the Core 2 Duo is about 10% faster than Core Duo (so a 1.8ghz C2D would be roughly as fast as a 2ghz CD). 

I have the SSD version, and surprisingly, it was not much more expensive than a HD one (about $50 more, when the X25-M retails for ~$250 even now, and was >$300 back then when I bought it). I thought it was a really good deal. It's about the best consumer SSD money can buy right now (the OCZ Vertex has higher sequential write, but lower random read/write, which is more important in real world usage). 

> Right now I'm pretty sure that nobody's got anything above 4~5hr battery life with Ubuntu (to my knowledge), so don't expect an improvement there....
I get ~8 hrs with wifi on. Could be a little shorter for HD version.

I find the high read speed of the SSD really useful, since suspend doesn't work, and I have to use hibernate. With the SSD, resume from hibernate takes <10 seconds. Would be almost a minute with a HD. It never heats the palm-rest up, too, and that's a nice bonus. And then it consumes less power. Also, when entering hibernation, you can just initiate the process, and close the laptop and take it with you (hence the slower writing speed doesn't really matter). You can't do that with a harddrive because they don't like being moved around while the head is busy writing stuff onto the disk. 

What are your main requirements, though? The 2 main strong points of this laptop are portability and battery life. If those aren't your main concerns, I think you are looking at the wrong place. You can get a much faster laptop at this price if you sacrifice the portability and battery life.

---

### Post by kwaanens on 2009-09-23
> **cyberfish said:**
> What are your main requirements, though? The 2 main strong points of this laptop are portability and battery life. If those aren't your main concerns, I think you are looking at the wrong place. You can get a much faster laptop at this price if you sacrifice the portability and battery life.

Thanks for your well put insights into this!
My preferred form factor atm is a relatively light notebook, at less than the 14-15" size. My 12,1" is a good compromise between size and portability, and size wise, the Timeline will match that (and even have a larger screen). Battery life is an important factor, but I'm not totally dependant on the extremes (like the Timeline capacity).
I've looked at the specs for the Lenovo Thinkpad SL300 today, which has less RAM, but a better CPU. (From what I understand of the RAM/CPU relationship, it might be better equipped for Linux, since Linux generally is not eating memory as much as, say, Vista) It lacks the battery capacity of the Timeline, but it's definitely bearable. It will cost a little more, but the increase is less than $100.
Need to think this over a bit, if SSD was an option (can't find that with my national keyboard layout, which is pretty important) it would probably push the Timeline over the finish line :)

---

### Post by cyberfish on 2009-09-23
Nowadays not many things are bottlenecked by the CPU anymore. Booting/programs starting are bottlenecked by the harddrive, gaming by the GPU, downloading/browsing by the network speed... Almost everything else is bottlenecked by the human.

CPU is only a bottleneck in, for example, compiling (though I am a programmer and compile quite a bit, I don't really notice any difference between my 3ghz C2D and this C2S, except you can obviously run 2 compiling processes on a dual core), encoding, and compression/decompression. 

I don't think memory size is that important, either. I have 2GB and very rarely use more than 512MB, and have never seen >1GB. Unused RAM is just unused RAM. Linux uses spare RAM for disk caching, but there is a point after which there won't be noticeable difference anymore. Upgrading from 128MB to 256MB will certainly make a huge difference. From my experience, 256-512 will make a differenece. 512-1GB will only make a difference if you are using A LOT of memory. 1GB-2GB... you would have to rely on placebo effect.

---

### Post by haywire.dk on 2009-09-23
I've been comparing the "minimum power usage footprint" of my AS3810T-354G50n under Ubuntu Karmic and Windows Vista, trying to figure out why Linux uses an extra 2.4 Watt. I even went as far as physically disconnecting bluetooth, wlan and camera to measure the impact on power usage.

I used powertop with all it's recommended settings plus "iwconfig wlan0 power on" under Linux, and RMClock under Windows. I used the lowest backlight setting under both Linux and Windows.

I didn't find the culprit of the extra 2.4 Watt, but I've at least I can say where it isn't:

**_[COLOR=Black]CPU power: 1.5 Watt[/COLOR]_**
At rest linux use 7.3 Watt, and Windows 4.9 Watt. At 100% CPU load linux used 11.3 Watt and Windows used 8.9 Watt. Since the processor has a TDP of 5.5 watt I tentatively conclude that it is using 1.5 Watt in idle mode (on both Linux and Windows)

_**LED Backlight: 1.2 Watt**_
Power consumption dropped 1.2 Watt when blanking screen, bringing Vista down to an impressive 3.7 Watt total, and Linux to a less impressive 6.1 Watt.

_**Bluetooth: < 0.1 Watt**_
I tried opening the laptop and physically disconnect the bluetooth hardware. Running Linux without Bluetooth connected didn't change power consumption.

_**Camera: < 0.1 Watt**_
I tried opening the laptop and physically disconnect the camera hardware. Running Linux without camera connected didn't change power consumption.

_**Wifi: 0.2 Watt**_
I tried opening the laptop and physically disconnect the wifi  hardware. Running Linux without wifi lowered power concumption about 0.2 Watt, down to 7.1 Watt total.


That leaves Audio, USB, SD-Card Reader, Video controller, RAM-controller, SATA controller, Harddisk and Chipset to search for excessive power usage.
I'd really like to save the extra 2.4 Watt that Vista shows is possible, but I'm currently out of ideas.

Any suggestions?

---

### Post by cyberfish on 2009-09-23
My guess is the northbridge (video and RAM controller) probably doesn't matter, and it's in the southbridge (USB/SATA). Unfortunately, there's nothing we can do about that, except trying to get Intel to release better chipset drivers for Linux. 

I'm pretty sure it's not the harddrive. I have the SSD and it's about the same (SSD consumes about 0 power on idle).

I'm not as concerned about power, though. 8 hr is enough for me :D (Vista can do about 10). I don't usually let the battery go below ~50%.

*edit* If you really want to test the harddrive, you can take it out and boot from USB (and do apt-get install powertop to install powertop to RAM)

---

### Post by bududu on 2009-09-24
> **yuki86 said:**
> hey i found solution in skype set this:

sound in - HDA Intel (hw:intel,o)
sound out - HDA Intel (hw:intel,o)
ringing - HDA Intel (hw:intel,o)

and then 
# alsamixer 
press tab than use arrows to switch mic from Front to Int
and prey..

Cool! That works for me. Thank you very much.

P.S. Updated to 1.14 BIOS today. Still no restore from suspend.

---

### Post by haywire.dk on 2009-09-24
_**BIOS v1.14 for Acer Timeline 3810T**_

I tried the new BIOS 1.14 today.
On battery power the fan now starts at 45°C and stops again at 42°C. With BIOS v1.10 the fan started at 55°C and stopped at 52°C.
The result being that with the current Ubuntu Karmic power usage the fan starts and stop all the time on battery, instead of just keeping quiet.

Luckily it is possible to revert back to BIOS v1.10...

---

### Post by Friqenstein on 2009-09-25
Hello all,

I finally got my Acer. It's the 4810T model, and I was able to get a unit that came with XP instead of Vista!  (yay me)
However, after about an hour of fishing through windows software and installing certain apps, I realized I really didn't need windows at all on this machine, so I wiped the entire HD and installed Jaunty Jackalope 9.04?
Everything seems to be working perfectly as far as I can tell. So far everything worked right out of the box, well everything that means something.

So now on to the questions:
I know I have a 4810 not a 3810 but I know there are others posting and reading this thread that also have a 4810.
1) How come the Fn keys don't seem to work? I cannot control my sound and a few of the other Fn keys don't seem to do jack.
2) How do I get the laptop to output via the HDMI port to a TV with HDMI input? I tried the Fn keys to switch vid modes, but again it's one of those Fn keys that don't seem to do jack.
3) Anybody figure out how to get the on/off working for the touchpad button?

Thanks

---

### Post by miegiel on 2009-09-25
> **Friqenstein said:**
> Hello all,

I finally got my Acer. It's the 4810T model, and I was able to get a unit that came with XP instead of Vista!  (yay me)
However, after about an hour of fishing through windows software and installing certain apps, I realized I really didn't need windows at all on this machine, so I wiped the entire HD and installed Jaunty Jackalope 9.04?
Everything seems to be working perfectly as far as I can tell. So far everything worked right out of the box, well everything that means something.

So now on to the questions:
I know I have a 4810 not a 3810 but I know there are others posting and reading this thread that also have a 4810.
1) How come the Fn keys don't seem to work? I cannot control my sound and a few of the other Fn keys don't seem to do jack.
2) How do I get the laptop to output via the HDMI port to a TV with HDMI input? I tried the Fn keys to switch vid modes, but again it's one of those Fn keys that don't seem to do jack.
3) Anybody figure out how to get the on/off working for the touchpad button?

Thanks

Others might disagree with me, but as far as I'm concerned this has become a general timeline thread :D

On question 1 and 3, that stuff works in karmic, it will be released in a month (9.10 beta is released next wensday).

---

### Post by Friqenstein on 2009-09-26
Thanks for the reply Miegel.

Anybody know anything about the HDMI output?
Also, I'm not getting anywhere near 8hours of battery life. I get about 4hours tops and that's even when I'm not running anything... as in just letting the laptop sit there idle. Any ideas on what I might be missing for proper power reserve?
I've not changed anything regarding the settings. All was from initial install.

Tnx.

---

### Post by cyberfish on 2009-09-26
> **Friqenstein said:**
> Thanks for the reply Miegel.

Anybody know anything about the HDMI output?
Also, I'm not getting anywhere near 8hours of battery life. I get about 4hours tops and that's even when I'm not running anything... as in just letting the laptop sit there idle. Any ideas on what I might be missing for proper power reserve?
I've not changed anything regarding the settings. All was from initial install.

Tnx.

Try powertop. What does it say for power consumption? (you need to run it on battery)

Post a screenshot.

---

### Post by Sashin on 2009-09-26
On the 4810T model touchpad does NOT work with karmic. Neither does the "two finger scrolling" tick.

---

### Post by Sashin on 2009-09-26
Neither does brightness, I get the same problem with jaunty prior to upgrading.

---

### Post by cyberfish on 2009-09-26
Did you upgrade or do a fresh install?

It's possible that some configuration files got left over.

Both of those problems are fixed for everyone else in Karmic.

---

### Post by megaexception on 2009-09-27
my status report, using 32bit ubuntu karmic.

what is working:

[LIST]
[*]4Gb RAM - using pae kernel
[*]sata controller - using 'libata.force=noncq' kernel cmd
[*]intel GMA videocard (framebuffer, X, composite - everything is ok)
[*]disabling ati video (lenovo-acpi.ko)
[*]lcd backlight using fn+arrows (worked out of box in karmic)
[*]hibernate/resume (out of box)
[*]sound output on builtin speakers and on headphone out (still sound volume is low)
[*]gigabit ethernet card (attansic 1063 driver in 2.6.31 kernel)
[*]wifi works perfect out of box
[*]touchpad works perfect out of box (scroll, multifinger tap, disable/enable button)
[*]card-reader works out of box
[*]bluetooth works out of box, bluetooth switch button fn-f3 works out of box
[*]camera works out of box
[*]fn-buttons working: brightness, sound volume, display switch, blank screen, media buttons
[/LIST]

what doesn't work:

[LIST]
[*]internal mic. i've tried every option in snd_hda_intel driver, still no luck getting mic working - with any catpure devices settings soundcard is listening only to external mic (even with setting input source to int) - will be hopefuly waiting for alsa drivers update
[*]with alsa-1.0.20 i am getting a lot of messages 'hda-intel: spurious responce 0x0:0x0' when probing codecs, probe masking and msi doesn't help
[*]suspend/resume, or actualy resume portion - device doing cold boot instean waking up
[*]switchable video - i haven't found a way to switch graphic output to ati and back to intel, and to disable unused card
[/LIST]

the most annoying problem for now is mic. have anybody found a fix?

---

### Post by Sashin on 2009-09-27
Then the 14 inch has something wrong with it, 'cause the brightness problem is here.

---

### Post by doktoreas on 2009-09-27
I am going out to buy a 3810T..so do you it's better to install Karmic ?
Right now my priority is to use it with an external monitor.

Thank you very much

Ciao
Luca

---

### Post by bududu on 2009-09-28
> **doktoreas said:**
> I am going out to buy a 3810T..so do you it's better to install Karmic ?
Right now my priority is to use it with an external monitor.


I use 9.04 xubuntu on 3810T with external monitor right now. I've used VGA first and now I'm using HDMI output.
Everything works well (except resuming from suspend, for sure :(

However, I'd suggest you to install karmic as there are some features (like grub2 or ext4) that are better to install from the fresh distro.

---

### Post by jacktow on 2009-09-28
> **megaexception said:**
> 
[LIST]
[*]switchable video - i haven't found a way to switch graphic output to ati and back to intel, and to disable unused card
[/LIST]


[See this]("http://ubuntuforums.org/showpost.php?p=7933876&postcount=11").

---

### Post by megaexception on 2009-09-28
> **jacktow said:**
> [See this]("http://ubuntuforums.org/showpost.php?p=7933876&postcount=11").

yes, i do use lenovo-acpi module to disable ati card. 
but i cannot make use of ati videocard - no difference what i put in xorg.conf, X always use Intel GS45 integrated graphics.

---

### Post by JaimeJB on 2009-09-28
Hi sorry, but when using skype I don't get any other option apart from pulseaudio server (local) on skype->sound devices.
Any ideas?

thanks again.

---

### Post by miegiel on 2009-09-28
> **JaimeJB said:**
> Hi sorry, but when using skype I don't get any other option apart from pulseaudio server (local) on skype->sound devices.
Any ideas?

thanks again.

Aren't there skype threads for that? :)

---

### Post by Frosty6677 on 2009-09-28
Thanks for this. I have an Acer Travelmate 5625WSMi. Your thread would be very helpful in solving some of my issues.

---

### Post by Frosty6677 on 2009-09-28
I believe there wouldn't be too much of a problem installing Ubuntu 9.0.4 with an Acer Tavelmate 5625WSMi right?
 
:confused:

---

### Post by Arlanthir on 2009-09-29
The xrandr fix for backlight issues doesn't seem to work for me.
I have a LVDS1 output instead of LVDS and xbacklight says no outputs support backlight property, confirming the xrandr output:

```

X Error of failed request: BadName (named color or font does not exist)
  Major opcode of failed request: 149 (RANDR)
  Minor opcode of failed request: 11 (RRQueryOutputProperty)
  Serial number of failed request: 31
  Current serial number in output stream: 31

```

Edit: this is on a 4810t by the way

---

### Post by JaimeJB on 2009-09-29
> **miegiel said:**
> Aren't there skype threads for that? :)

Well, I think the problem is related with the mic hardware, rather than with the skype software. After all, the mic does not work at all.

Thanks for the time.

---

### Post by Friqenstein on 2009-09-30
> **bududu said:**
> I use 9.04 xubuntu on 3810T with external monitor right now. I've used VGA first **and now I'm using HDMI output**...Ok, so I have to ask, b'cuz I've asked before and cannot seem to get mine to work.
How do you get the HDMI output to work?
I've got a brand new HDMI cable and a TV that has HDMI input port. I connected it and tried the fn key to switch displays, and saw a 'slight' glitch on the TV but nothing showing my laptops desktop screen.

When I say 'slight' glitch, what I mean is this: when you swith the TV to HDMI input source and there is no cable attached it will say NO SIGNAL on the TV screen. As soon as you connect the HDMI cable to the laptop and hit the fn key the NO SIGNAL goes away for a moment but nothing else happens. Am I missing something? Perhaps I didn't install something in the initial install that allows for the HDMI output to function properly?

Any help is greatly appreciated.
Tnx

---

### Post by miegiel on 2009-09-30
> **JaimeJB said:**
> Well, I think the problem is related with the mic hardware, rather than with the skype software. After all, the mic does not work at all.

Thanks for the time.

Fair enough. It sounded more like a skype issue then a timeline issue to me. My internal mic isn't working either, but that's in karmic and it's a pulse issue effecting some other laptops too. External microphones work fine though. To rule out broken hardware you could test your mic in windows if you still have it on your laptop.

---

### Post by coolvibe on 2009-09-30
> **Arlanthir said:**
> The xrandr fix for backlight issues doesn't seem to work for me.
I have a LVDS1 output instead of LVDS and xbacklight says no outputs support backlight property, confirming the xrandr output:

```

X Error of failed request: BadName (named color or font does not exist)
  Major opcode of failed request: 149 (RANDR)
  Minor opcode of failed request: 11 (RRQueryOutputProperty)
  Serial number of failed request: 31
  Current serial number in output stream: 31

```

Edit: this is on a 4810t by the way

Check the 4810T thread, I have found a workaround which I posted there: [http://ubuntuforums.org/showthread.php?p=8030550&highlight=5810t#post8030550](http://ubuntuforums.org/showthread.php?p=8030550&highlight=5810t#post8030550)

---

### Post by iiinycboi on 2009-09-30
Hi everyone, I am trying to install the mini.iso / minimal installation of ubuntu onto my acer timeline 3810. The network card is not listed in the detect network section. How would i be able to get the driver and install this, so i can install the "barebone" installation. Thank you!

---

### Post by miegiel on 2009-09-30
> **iiinycboi said:**
> Hi everyone, I am trying to install the mini.iso / minimal installation of ubuntu onto my acer timeline 3810. The network card is not listed in the detect network section. How would i be able to get the driver and install this, so i can install the "barebone" installation. Thank you!

**[COLOR="Red"]Search:[/COLOR]**   Keyword(s): **_atheros_**

---

### Post by miegiel on 2009-10-02
Has anyone used the HDD password security option in the BIOS yet?

I'm having some trouble getting it to work. At the moment I suspect it might only work if the BIOS is set to AHCI (will test that this weekend).

*edit:*
It was the IDE option in the BIOS, after turning AHCI on again and adding the *libata.force=noncq* option in grub HDD security works.

---

### Post by bududu on 2009-10-05
> **Friqenstein said:**
> 
How do you get the HDMI output to work?


I didn't do anything special to make it work. Just plugged HDMI<->DVI cable to my laptop and 22" Samsung monitor. Then used "Display" menu in "Settings", detect monitors, and here we are.
Just the same as is did with d-sub (vga) cable.
Everything is working out of the box for me.

---

### Post by X1R1 on 2009-10-05
thank you a LOT for the command to fix the brightness, have being looking for this for a loong time!!!!

---

### Post by Friqenstein on 2009-10-06
> **Friqenstein said:**
> Ok, so I have to ask, b'cuz I've asked before and cannot seem to get mine to work.
How do you get the HDMI output to work?
I've got a brand new HDMI cable and a TV that has HDMI input port. I connected it and tried the fn key to switch displays, and saw a 'slight' glitch on the TV but nothing showing my laptops desktop screen.

When I say 'slight' glitch, what I mean is this: when you swith the TV to HDMI input source and there is no cable attached it will say NO SIGNAL on the TV screen. As soon as you connect the HDMI cable to the laptop and hit the fn key the NO SIGNAL goes away for a moment but nothing else happens. Am I missing something? Perhaps I didn't install something in the initial install that allows for the HDMI output to function properly?

Any help is greatly appreciated.
TnxAnything yet? I've checked several other places an either people are not using the HDMI port (which I find hard to believe) or the question is just being overlooked easily. So I'm asking yet again.

Also, anybody having issues with bootup? Occationally, when I turn on the laptop, it will go all the way to the login screen on the desktop but and when I type in my name & pw it will just sit there as though it has forgotten how to be a computer. Cannot explain it any better than that.
The mouse cursor still moves, and you can click on the Restart or Shutdown menus but it won't restart nor shutdown w/out a hard power-off with the power button.
Curious if anybody else has had this issue. It has happened to me several times now but not enough to warrant really worrying me. It's just quite annoying. Also, when it's 'stuck' in that forgetful mode, I cannot change to any other terms (CTRL ALT F1) either.

T.I.A.

---

### Post by iiinycboi on 2009-10-06
I got a couple question, hopefully this thread is not dead.

Does anyone know if the acer timeline comes with an automatic battery killswitch when being plugged in? I noticed that when the laptop is charging it has an amber light, then when its full its blue. After being blue it shuts off completely? Does that mean that its not "topping off" the battery every min or so? 

I am trying to preserve the battery life so when ever im not in class i take the battery out, and this is probably the most tedious and annoying thing to do. What i notice, when the battery is taking out and placed back in the laptop doesnt sense the battery till i unplug it and plug it back in.

Does this mean its probably safe to say that when the battery is full the acer timeline switch off the battery and just uses external power and doesnt top off the battery?


Thanks!

---

### Post by miegiel on 2009-10-06
> **iiinycboi said:**
> I got a couple question, hopefully this thread is not dead.

Does anyone know if the acer timeline comes with an automatic battery killswitch when being plugged in? I noticed that when the laptop is charging it has an amber light, then when its full its blue. After being blue it shuts off completely? Does that mean that its not "topping off" the battery every min or so? 

I am trying to preserve the battery life so when ever im not in class i take the battery out, and this is probably the most tedious and annoying thing to do. What i notice, when the battery is taking out and placed back in the laptop doesnt sense the battery till i unplug it and plug it back in.

Does this mean its probably safe to say that when the battery is full the acer timeline switch off the battery and just uses external power and doesnt top off the battery?


Thanks!

IIRC
```
cat /proc/acpi/battery/BAT0/state
```
Says the battery is disconnected when the blue light is on.

---

### Post by miegiel on 2009-10-06
> **Friqenstein said:**
> Anything yet? I've checked several other places an either people are not using the HDMI port (which I find hard to believe) or the question is just being overlooked easily. So I'm asking yet again.

Also, anybody having issues with bootup? Occationally, when I turn on the laptop, it will go all the way to the login screen on the desktop but and when I type in my name & pw it will just sit there as though it has forgotten how to be a computer. Cannot explain it any better than that.
The mouse cursor still moves, and you can click on the Restart or Shutdown menus but it won't restart nor shutdown w/out a hard power-off with the power button.
Curious if anybody else has had this issue. It has happened to me several times now but not enough to warrant really worrying me. It's just quite annoying. Also, when it's 'stuck' in that forgetful mode, I cannot change to any other terms (CTRL ALT F1) either.

T.I.A.

Hard to believe I never used HDMI? I don't even have a TV!

Anyway, it seems answers are overlooked easy too ;)

> **bududu said:**
> I didn't do anything special to make it work. Just plugged HDMI<->DVI cable to my laptop and 22" Samsung monitor. Then used "Display" menu in "Settings", detect monitors, and here we are.
Just the same as is did with d-sub (vga) cable.
Everything is working out of the box for me.

I Don't have any boot problems, but check the forums. Often someone (including people who don't have an acer timeline) had the same problem at some point.

---

### Post by cyberfish on 2009-10-06
> **iiinycboi said:**
> I got a couple question, hopefully this thread is not dead.

Does anyone know if the acer timeline comes with an automatic battery killswitch when being plugged in? I noticed that when the laptop is charging it has an amber light, then when its full its blue. After being blue it shuts off completely? Does that mean that its not "topping off" the battery every min or so? 

I am trying to preserve the battery life so when ever im not in class i take the battery out, and this is probably the most tedious and annoying thing to do. What i notice, when the battery is taking out and placed back in the laptop doesnt sense the battery till i unplug it and plug it back in.

Does this mean its probably safe to say that when the battery is full the acer timeline switch off the battery and just uses external power and doesnt top off the battery?


Thanks!

They cut off the charger when the battery is full, which is a very good thing to do. Lithium ion batteries don't like overcharging at all. They will heat up and explode.

The "top off" you are describing is called trickle charging (applying a very small current after the battery is full to offset the shelf discharge). It's not necessary with lithium ion batteries because they discharge very slowly, and don't like being overcharged.

I would just leave the battery in there. The charging circuit knows what's best for the battery.

---

### Post by woonghee on 2009-10-06
I installed ubuntu 9.10 karmic koala beta and i am having some troubles.

First, wireless disconnects with AP after using 20~30 mins. It tries to connect to AP forever after it disconnects. But only solution is rebooting the system.

Second, an internal microphone never works. I tried every settings with volume-manager and alsamixer, but they were in vain.

Third, cairo-dock limits maximized window sizes. Windows' border can't reach bottom of screen. It always reaches bottom of cairo-dock.

Fourth, Google-Gadgets never works. Whenever I executes, it fails saying "Failed to load js-script-runtime". After installing xulrunner-1.9-dev, I can see "No permission to read file, No permission to access device status, X Window System error, Segmentation fault...)

It seems that a battery lasts longer than with Ubuntu 9.04 but still some problems occur.

---

### Post by BoneZZZ on 2009-10-07
> **megaexception said:**
> yes, i do use lenovo-acpi module to disable ati card. 
but i cannot make use of ati videocard - no difference what i put in xorg.conf, X always use Intel GS45 integrated graphics.

If you want to use ATI card, go to BIOS and select 'Discrete' in video mode. This switches off Intel video card. Install latest ATI drivers from amd.com and enjoy ... but battery will drop quicker and Compiz has delays under X.org 1.6, so ...

If you want to use Intel card, go to BIOS an select 'Switchable' in video mode. This will turn on BOTH cards, so you may have a messy video. Presently, X don't support switchable cards ... so the best option is use lenovo patch and switch off ATI card. You will have full 3D with intel drivers and small battery usage. But performance will be a little worse that in ATI.

PS: you may have to upgrade BIOS. I use v1.23

---

### Post by eScenCe on 2009-10-07
I'm sorry for bumb in like this, I hope noone gets mad on me because I'm not in the mood to read through nearly 400 posts just to get 5 informations answered / corrected / confirmed.


1) Does Ubuntu works out of the Box? 
As far as I can tell from flipping through here: Yes.
WLAN & LAN Works, ATI & Onboard is detected HDDs works also if AHCI is set to IDE.

2) Does the FN Buttons do _all_ work right out of the box?
I'm pretty sure I found the answer already: Yes.

3) Is the ATI 4330 & OnBoard GPU switchable like it is under Windows?
It should be aswell, right?

4) I've found some issues here concerning GNOME, KDE & such stuff.
Which one is the "best" at the moment - I really dislike graphically "bugs" and "issues".
Any one is already stable and performing great?

5) Last, the Battery lifetime...
Some reported 3 hours, some up to 8, another 6 ...

Let me be more specific: WLAN on everytime, ATI off, BlueTooth off , Display Brightness acceptable for closed rooms i.e. university (should be 2-3 I guess), Chatting, Surfing, PDF reading and from time to time some youtube clips.

Can I reach the 6 hours like under Vista/7 with that? Or does Ubuntu "eats" a lot more power than Windows? That would make Ubuntu very unattractive to me :(


Btw, if it's important, Model is 3810TG with SU9400, 500GB HDD and ATI 4330.

Sorry for my bad english, I'm from Germany.

---

### Post by BoneZZZ on 2009-10-07
> **Ashrael said:**
> @quail-linux: 

I found a lot of posts about matSHITa drives and the UN-availability of newer/better firmware....so.
I decided to go and ask acer for a tsscorp replacement I guess, no way of knowing yet what they will say....
Or: linux/ubuntu learns how to use this drive properly: It works very well in Vista....
In the mean time I will not use this machine for ubuntu...sad.
I will keep on tweaking it for battery performance though, also goes for touchpad disable/enable button and brightness of screen....

thanks again for posting!

I had a lot of issues with DVD drive at the beginning. All disappeared when I switched from AHCI to IDE in the BIOS settings. Also dmesg log is absolutely clean after this change. Using BIOS v1.23 and UB9.04 with kernel 2.6.30.6 (also worked with 2.6.28...)

---

### Post by deconstructingme on 2009-10-07
I just got a 3810T with SU9400 processor. I have Karmic Beta installed and everything is working fine except the two known problems with the internal mic and the suspend/resume.

I think there has been some change in the suspend resume behaviour with the last updates as it used to power down when I suspended, but now it sits and waits until I try to resume before powering down.

I notice on [https://help.ubuntu.com/community/AspireTimeline](https://help.ubuntu.com/community/AspireTimeline) that someone has posted a note that suspend seems to work with the beta. Are there any more details? 

I checked and I have Bios 1.04

---

### Post by TwiceOver on 2009-10-07
Since this has become the defacto "Acer Timeline" thread...

I have a 4810tz bios 1.28 Ubuntu 9.10 Beta. The brightness keys work however they cause all other keys, buttons, and mouse to stop responding.

When I press the fn + left/right arrow the brightness adjusts, however I cannot do anything else after that except continue adjusting brightness up and down.

EDIT:  This is completely locked up.  I can't switch into a different terminal and I can turn the wireless of with the button but Ubuntu doesn't register that it is down.

I thought I read a few pages back of similar issues.  Anyone have a fix for this?

EDIT:  I went through the Wiki and found the comment to add nomodeset acpi_backlight=vendor.  This actually allows me to use the brightness control in the power applet, but the fn keys still lock up the system.

---

### Post by Arlanthir on 2009-10-07
> **TwiceOver said:**
> Since this has become the defacto "Acer Timeline" thread...

I have a 4810tz bios 1.28 Ubuntu 9.10 Beta. The brightness keys work however they cause all other keys, buttons, and mouse to stop responding.

When I press the fn + left/right arrow the brightness adjusts, however I cannot do anything else after that except continue adjusting brightness up and down.

I thought I read a few pages back of similar issues.  Anyone have a fix for this?

I had the same issue with the 1.28 BIOS.
Had to downgrade it but it bricked the computer and so I had to trade it in :S

Not really sure what to advise you to do, just sharing my experience.

---

### Post by TwiceOver on 2009-10-07
> **Arlanthir said:**
> I had the same issue with the 1.28 BIOS.
Had to downgrade it but it bricked the computer and so I had to trade it in :S

Not really sure what to advise you to do, just sharing my experience.

Yeah, the bios was originally 1.10 but I read a couple posts about 1.28 helping out a bit, like my cdrom button working properly.

I guess I'll just have to use the power manager applet.

---

### Post by citizenofnowhere on 2009-10-08
Calling 4810 users!

I'm working on fixing suspend on the 3810 by modifying the DSDT. I think this has a shot at working because I've already managed to fix the command line system beep using this method (woo!).

The trouble is, I don't have a working suspend to compare my modifications to.

If **anyone with a 4810 who has suspend working now has some time and is willing to assist us 3810 folks, please PM me** file that is the output of this command from the terminal

```
sudo cp /proc/acpi/dsdt ~/DSDT.dump
```

This will simply make a binary copy of your working bios config in your home directory. I will try to do the rest by comparing my 3810 file and the 4810 one, and post back here as soon as I have made any progress.

---

### Post by quail-linux on 2009-10-08
> **citizenofnowhere said:**
> Calling 4810 users!

I'm working on fixing suspend on the 3810 by modifying the DSDT. I think this has a shot at working because I've already managed to fix the command line system beep using this method (woo!).

The trouble is, I don't have a working suspend to compare my modifications to.

If **anyone with a 4810 who has suspend working now has some time and is willing to assist us 3810 folks, please PM me** file that is the output of this command from the terminal

```
sudo cp /proc/acpi/dsdt ~/DSDT.dump
```

This will simply make a binary copy of your working bios config in your home directory. I will try to do the rest by comparing my 3810 file and the 4810 one, and post back here as soon as I have made any progress.

Here is my dsdt output attached
```
# cat /sys/firmware/acpi/tables/DSDT > acer-aspire-timeline-4810T_dsdt
```and archived as a gz. My bios version is 1.26

hope it helps out and good luck :-)

---

### Post by citizenofnowhere on 2009-10-08
That was quick! Thanks man, you rock! Can't wait to get cracking  :)

---

### Post by quail-linux on 2009-10-08
> **citizenofnowhere said:**
> That was quick! Thanks man, you rock! Can't wait to get cracking  :)

np, your welcome. Maybe you can work out the different between the 3810 and the 4810 with the backlight keys, as there has been chatter on the backlight keys work under different BIOS's than others.

I not long upgraded to the 1.26 BIOS and it seems to have fixed an intermittent problem I had with the Ethernet interface going spaz randomly when not being used.

Regards

---

### Post by citizenofnowhere on 2009-10-08
> Maybe you can work out the different between the 3810 and the 4810 with the backlight keys, as there has been chatter on the backlight keys work under different BIOS's than others. 

I will make sure to look out for that!

---

### Post by eScenCe on 2009-10-08
[Noone](http://ubuntuforums.org/showpost.php?p=8066052&postcount=359) ?
I'm planing to buy it tomorrow and I need to be sure everything is going to be fine.

---

### Post by miegiel on 2009-10-08
> **eScenCe said:**
> [Noone](http://ubuntuforums.org/showpost.php?p=8066052&postcount=359) ?
I'm planing to buy it tomorrow and I need to be sure everything is going to be fine.
All the questions you asked are already answered in the thread.

In karmic (ubuntu 9.10, to be released in 3 weeks) almost everything should work out of the box if you turn off AHCI in the BIOS or turn off NCQ in grub (add kernel parameter *libata.force=noncq*). The 2 things that don't work at all (yet) are the internal microphone and suspend to RAM.

I haven't really tried jaunty, but I know the wired network doesn't work out of the box.
 
Check [https://help.ubuntu.com/community/AspireTimeline](https://help.ubuntu.com/community/AspireTimeline) for more info.

Also, I heard a rumor that Acer is coming with new timeline models when win7 is released (in 2 weeks), so you might want to postpone your purchase for a few weeks.

---

### Post by citizenofnowhere on 2009-10-08
eScenCe:

As you may have already noticed, suspend doesn't work yet on the 3810. Doesn't look like it is going to be fixed over the next couple of days.

Other than that, running Karmic latest Beta most things work for me on kde4 (which is pretty and stable).

Battery life is easily 6 hours with light surfing, no bluetooth etc.

Card reader works for me, but my KDE doesn't see it - I have to mount from command line - small thing.

Also didn't look into getting HDMI to work so can't comment on that. 

Backlight works flawlessly for me on an Intel card (shortcuts, as well as onbattery and on AC)

I didn't even need turn off AHCI in the bios for Karmic Beta to boot after install.

Hope that answers your question.

---

### Post by miegiel on 2009-10-08
> **citizenofnowhere said:**
> ...

I didn't even need turn off AHCI in the bios for Karmic Beta to boot after install.

...

Great, I was wondering about that. I replaced the disk with a WD3200BJKT and undid the AHCI/NCQ fixes, but I forgot to test it on the old disk before wiping it clean. So in the end I didn't know if it was the new disk or updates to karmic that fixed it.

---

### Post by TwiceOver on 2009-10-08
> **TwiceOver said:**
> Since this has become the defacto "Acer Timeline" thread...

I have a 4810tz bios 1.28 Ubuntu 9.10 Beta. The brightness keys work however they cause all other keys, buttons, and mouse to stop responding.

When I press the fn + left/right arrow the brightness adjusts, however I cannot do anything else after that except continue adjusting brightness up and down.

EDIT:  This is completely locked up.  I can't switch into a different terminal and I can turn the wireless of with the button but Ubuntu doesn't register that it is down.

I thought I read a few pages back of similar issues.  Anyone have a fix for this?

EDIT:  I went through the Wiki and found the comment to add nomodeset acpi_backlight=vendor.  This actually allows me to use the brightness control in the power applet, but the fn keys still lock up the system.

Hrmmm... A little more to this...

I disabled compiz via Appearance -> Visual Effects -> None and my system doesn't freeze with the brighness adjust anymore.  Must be a problem with Compiz then.  Guess I'll go through each Compiz setting and see which one is causing it.

EDIT: "Normal" and "Advanced" cause my system to freeze when adjusting brighness.
EDIT: I disabled all of the Compiz plugins and still freeze. :( 
EDIT: Also noticed with Appearance settings to "none" the brighness notification comes up now.  It had not done that in the past.

---

### Post by eScenCe on 2009-10-08
@miegiel & citizenofnowhere

Thanks for the feedback.

I'm just curious, as you asnwered me any question than one:
Switching / disabling HD4330 and Onboard is possible?

---

### Post by miegiel on 2009-10-08
> **eScenCe said:**
> @miegiel & citizenofnowhere

Thanks for the feedback.

I'm just curious, as you asnwered me any question than one:
Switching / disabling HD4330 and Onboard is possible?

Can't say, I've got the timeline without ATI graphics. But you should be able to turn it on and off in the BIOS.

---

### Post by Sashin on 2009-10-09
What does disabling AHCI mean?

---

### Post by miegiel on 2009-10-09
> **Sashin said:**
> What does disabling AHCI mean?

It's an extension to IDE and your PC uses it to "talk" to the hard drive. It basically adds NCQ and hot-swapping to IDE, but it's also used to unlock your drive if you use the "secure your hard drive with a password" option in the BIOS.

Most laptop disks don't have NCQ yet and hot-swapping is pretty useless in a laptop. So, unless you want to secure your disk with a password, it is safe to turn it off (in the BIOS).

If you want to know more, wikipedia and google are your friend. ;)

---

### Post by iceman on 2009-10-09
Can't believe in october 2009, a notebook in Ubuntu won't suspend...
I have 3810T from 3-4 days and i am really happy of it... unfortunately, S3 Suspend for me it's too important and as far as i read, noone has it working.
Compiling latest kernel from kernel.org might help?

Really sad because everything works perfect (and i have Core2Solo!)

---

### Post by quail-linux on 2009-10-09
I just noticed that there is a 2.30 bios available as of the 2009/10/09 for the 4810T/TG/TZ models.

[http://support.acer-euro.com/drivers/downloads_gd.html](http://support.acer-euro.com/drivers/downloads_gd.html)

---

### Post by citizenofnowhere on 2009-10-09
Wow another firmware update for the 4810 folks? I was starting to feel left out with my 3810 until I saw this on the acer website today:

> 
	VOLUNTARY SAFETY RECALL
Dear valued Acer Customer,
It has come to our attention that certain Acer Aspire Notebooks may overheat under specific conditions. Acer is therefore voluntarily instituting a safety recall for these products.

The affected units are Acer Aspire models AS3410, AS3810T, AS3810TG, AS3810TZ and AS3810TZG manufactured prior to September 15, 2009. In the affected units the microphone cable may overheat when extreme pressure is applied repeatedly to the left palm rest. As a result, the unit&#1203; case may become deformed and the system may malfunction.

Acer has voluntarily instituted a safety recall program to proactively replace the microphone cable in the affected units to eliminate any risk of overheating.

[http://customercare.acer-euro.com/customercare/AcerUpdate.aspx?CID=SG&LID=ENG&IType=JM31](http://customercare.acer-euro.com/customercare/AcerUpdate.aspx?CID=SG&LID=ENG&IType=JM31)

---

### Post by quail-linux on 2009-10-10
I have GREAT news for the 4810T owners the 2.30 BIOS[1] is rockin we now have backlight control keys working :-D

There is a catch tho you have to change from
```
xrandr --output LVDS --set BACKLIGHT_CONTROL native
```
to
```
xrandr --output LVDS --set BACKLIGHT_CONTROL kernel
```
or you will get a freeze type effect on the desktop. Also I noticed that my wifi went funny to and I could not ping anything even tho NM was say I was connected to AP. 

**So [COLOR="Red"]DON'T[/COLOR] play with backlight key till done the above changes.**

[1] [http://support.acer-euro.com/drivers/downloads_gd.html](http://support.acer-euro.com/drivers/downloads_gd.html)

Edit: I have noticed this works correctly in 'combination' too
```
xrandr --output LVDS --set BACKLIGHT_CONTROL combination
```

---

### Post by TwiceOver on 2009-10-10
> **quail-linux said:**
> I have GREAT news for the 4810T owners the 2.30 BIOS[1] is rockin we now have backlight control keys working :-D

There is a catch tho you have to change from
```
xrandr --output LVDS --set BACKLIGHT_CONTROL native
```
to
```
xrandr --output LVDS --set BACKLIGHT_CONTROL kernel
```
or you will get a freeze type effect on the desktop. Also I noticed that my wifi went funny to and I could not ping anything even tho NM was say I was connected to AP. 

**So [COLOR="Red"]DON'T[/COLOR] play with backlight key till done the above changes.**

[1] [http://support.acer-euro.com/drivers/downloads_gd.html](http://support.acer-euro.com/drivers/downloads_gd.html)

Edit: I have noticed this works correctly in 'combination' too
```
xrandr --output LVDS --set BACKLIGHT_CONTROL combination
```

What version of Ubuntu?  I tried the xrandr change in 9.10 and it failed with incorrect parameter (or something like that) xrandr --prop shows no BACKLIGHT_CONTROL options.

---

### Post by quail-linux on 2009-10-10
> **TwiceOver said:**
> What version of Ubuntu?  I tried the xrandr change in 9.10 and it failed with incorrect parameter (or something like that) xrandr --prop shows no BACKLIGHT_CONTROL options.

I don't use Ubuntu, I run Debian. So in theory there should not be a lot of difference.

---

### Post by xir_ on 2009-10-10
> **citizenofnowhere said:**
> Wow another firmware update for the 4810 folks? I was starting to feel left out with my 3810 until I saw this on the acer website today:



[http://customercare.acer-euro.com/customercare/AcerUpdate.aspx?CID=SG&LID=ENG&IType=JM31](http://customercare.acer-euro.com/customercare/AcerUpdate.aspx?CID=SG&LID=ENG&IType=JM31)


Damn it im part of that group so i have to return mine!

thanks for the headsup

---

### Post by fictivetoast on 2009-10-10
> **xir_ said:**
> Damn it im part of that group so i have to return mine!

thanks for the headsup

Me as well - my hard drive seems to be a lemon too though (constant write errors, commits timestamps in the future, occasionally won't even show up in bios).  Has been complicated to figure out how to get a replacement since my warranty only covers service in the states (where the laptop was purchased) and I've since moved to France.  I'm hoping the recall will allow me to service both in one shot...

---

### Post by xir_ on 2009-10-10
> **fictivetoast said:**
> Me as well - my hard drive seems to be a lemon too though (constant write errors, commits timestamps in the future, occasionally won't even show up in bios).  Has been complicated to figure out how to get a replacement since my warranty only covers service in the states (where the laptop was purchased) and I've since moved to France.  I'm hoping the recall will allow me to service both in one shot...

if they are paying for the shipping ill ask for the windows refund whilst they are at it.

---

### Post by idreamer on 2009-10-10
news for resume?

---

### Post by Sashin on 2009-10-10
What's the difference between "kernel" and "combination"?

---

### Post by Sashin on 2009-10-10
Also how do you upgrade, these instructions don't seem to work.
  [http://www.netbooktech.com/tag/acer-aspire-one-bios-update-instructions/](http://www.netbooktech.com/tag/acer-aspire-one-bios-update-instructions/)

---

### Post by TexLogic on 2009-10-10
> **TwiceOver said:**
> Hrmmm... A little more to this...

I disabled compiz via Appearance -> Visual Effects -> None and my system doesn't freeze with the brighness adjust anymore.  Must be a problem with Compiz then.  Guess I'll go through each Compiz setting and see which one is causing it.

EDIT: "Normal" and "Advanced" cause my system to freeze when adjusting brighness.
EDIT: I disabled all of the Compiz plugins and still freeze. :( 
EDIT: Also noticed with Appearance settings to "none" the brighness notification comes up now.  It had not done that in the past.

Thanks for this.  I was experiencing exactly the same problem -- using the brightness hotkey would indeed dim the screen but would lock up the window mgr.  Turning off Visual Effects also solves the problem for me.  I dig the effects, but they're total eye candy so I can certainly live with that til they fix it.

TexLogic

---

### Post by TexLogic on 2009-10-10
Irrelevant post...original content deleted.

---

### Post by miegiel on 2009-10-10
> **Sashin said:**
> Also how do you upgrade, these instructions don't seem to work.
  [http://www.netbooktech.com/tag/acer-aspire-one-bios-update-instructions/](http://www.netbooktech.com/tag/acer-aspire-one-bios-update-instructions/)

I used unetbootin when I flashed my BIOS. I remeber the instructions I followed didn't work either. Can't remember exactly what I did, but it boils down too following the idea behind the instruction (make a dos USB boot disk with unetbootin and use that to flash the BIOS) instead of following the instructions to the letter.

---

### Post by Sashin on 2009-10-10
Well I've made the usb bootable with the necessary files, but when it gets to the terminal I don't know what to press, it says c in the guide but it doesn't work, neither does anything after that in the guide

---

### Post by miegiel on 2009-10-10
> **Sashin said:**
> Well I've made the usb bootable with the necessary files, but when it gets to the terminal I don't know what to press, it says c in the guide but it doesn't work, neither does anything after that in the guide

C: not C :roll:

oh ... and if you're lost in dos try *dir*, it's *ls* for dos

---

### Post by woonghee on 2009-10-10
My wireless on 3810TZ with Karmic Koala beta always hangs after using sometime. And wireless LED stay lighting not blinking. Network manager continuously tries to connect but it never connects.

This is the messages:

Oct 10 22:21:21 whlee-timeline pulseaudio[1601]: ratelimit.c: 3 events suppressed
Oct 10 22:21:22 whlee-timeline kernel: [  250.554184] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct 10 22:21:22 whlee-timeline kernel: [  689.175315] *pde = 00000000
Oct 10 22:21:22 whlee-timeline kernel: [  689.175329] Modules linked in: ppdev snd_hda_codec_intelhdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss arc4 snd_seq_midi ecb iptable_filter snd_rawmidi ip_tables snd_seq_midi_event snd_seq x_tables ath9k snd_timer uvcvideo joydev snd_seq_device mac80211 videodev snd acer_wmi v4l1_compat ath soundcore psmouse cfg80211 led_class serio_raw snd_page_alloc atl1c lp parport binfmt_misc fbcon tileblit font bitblit softcursor i915 drm i2c_algo_bit usbhid intel_agp agpgart video output
Oct 10 22:21:22 whlee-timeline kernel: [  689.175378]
Oct 10 22:21:22 whlee-timeline kernel: [  689.175383] Pid: 742, comm: phy0 Not tainted (2.6.31-13-generic #44-Ubuntu) Aspire 3810TZ
Oct 10 22:21:22 whlee-timeline kernel: [  689.175387] EIP: 0060:[<c048e7f2>] EFLAGS: 00010206 CPU: 0
Oct 10 22:21:22 whlee-timeline kernel: [  689.175391] EIP is at skb_release_data+0x52/0xa0
Oct 10 22:21:22 whlee-timeline kernel: [  689.175394] EAX: 3bc477be EBX: f5f9df00 ECX: f5f9df00 EDX: f5b10940
Oct 10 22:21:22 whlee-timeline kernel: [  689.175398] ESI: f5f9df00 EDI: f5f9df00 EBP: f6791d94 ESP: f6791d8c
Oct 10 22:21:22 whlee-timeline kernel: [  689.175401]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Oct 10 22:21:22 whlee-timeline kernel: [  689.175410]  f5f9df00 00000009 f6791da0 c048e362 f66661a0 f6791da8 c048e3fc f6791de4
Oct 10 22:21:22 whlee-timeline kernel: [  689.175418] <0> f94e9eaf 00000000 00000000 00000000 00000000 f6667148 00000000 f5b108c0
Oct 10 22:21:22 whlee-timeline kernel: [  689.175426] <0> f5b108bc f5f9df20 f5f9df00 f5f9df00 f66669f4 00000000 f6791e1c f95d9b24
Oct 10 22:21:22 whlee-timeline kernel: [  689.175440]  [<c048e362>] ? __kfree_skb+0x12/0x90
Oct 10 22:21:22 whlee-timeline kernel: [  689.175445]  [<c048e3fc>] ? consume_skb+0x1c/0x40
Oct 10 22:21:22 whlee-timeline kernel: [  689.175463]  [<f94e9eaf>] ? ieee80211_tx_status+0x43f/0x470 [mac80211]
Oct 10 22:21:22 whlee-timeline kernel: [  689.175480]  [<f95d9b24>] ? ath_tx_complete+0x124/0x150 [ath9k]
Oct 10 22:21:22 whlee-timeline kernel: [  689.175495]  [<f95cfdf7>] ? ath9k_hw_setup_calibration+0x97/0x140 [ath9k]
Oct 10 22:21:22 whlee-timeline kernel: [  689.175508]  [<f95d9bc1>] ? ath_tx_complete_buf+0x71/0xc0 [ath9k]
Oct 10 22:21:22 whlee-timeline kernel: [  689.175515]  [<c0146af5>] ? __do_softirq+0xe5/0x1a0
Oct 10 22:21:22 whlee-timeline kernel: [  689.175528]  [<f95daf94>] ? ath_draintxq+0x134/0x280 [ath9k]
Oct 10 22:21:22 whlee-timeline kernel: [  689.175543]  [<f95dc1ee>] ? ath_drain_all_txq+0xce/0x140 [ath9k]
Oct 10 22:21:22 whlee-timeline kernel: [  689.175557]  [<f95d80e2>] ? ath_set_channel+0x82/0x200 [ath9k]
Oct 10 22:21:22 whlee-timeline kernel: [  689.175570]  [<f95d4aae>] ? ath_update_chainmask+0x7e/0x90 [ath9k]
Oct 10 22:21:22 whlee-timeline kernel: [  689.175583]  [<f95d8407>] ? ath9k_config+0x1a7/0x200 [ath9k]
Oct 10 22:21:22 whlee-timeline kernel: [  689.175600]  [<f94e9972>] ? ieee80211_hw_config+0x72/0xb0 [mac80211]
Oct 10 22:21:22 whlee-timeline kernel: [  689.175618]  [<f94ee146>] ? ieee80211_scan_work+0xb6/0x220 [mac80211]
Oct 10 22:21:22 whlee-timeline kernel: [  689.175625]  [<c056962c>] ? schedule+0x40c/0x730
Oct 10 22:21:22 whlee-timeline kernel: [  689.175636]  [<c015316e>] ? run_workqueue+0x6e/0x140
Oct 10 22:21:22 whlee-timeline kernel: [  689.175652]  [<f94ee090>] ? ieee80211_scan_work+0x0/0x220 [mac80211]
Oct 10 22:21:22 whlee-timeline kernel: [  689.175660]  [<c01532c8>] ? worker_thread+0x88/0xe0
Oct 10 22:21:22 whlee-timeline kernel: [  689.175666]  [<c0157970>] ? autoremove_wake_function+0x0/0x40
Oct 10 22:21:22 whlee-timeline kernel: [  689.175671]  [<c0153240>] ? worker_thread+0x0/0xe0
Oct 10 22:21:22 whlee-timeline kernel: [  689.175675]  [<c015767c>] ? kthread+0x7c/0x90
Oct 10 22:21:22 whlee-timeline kernel: [  689.175680]  [<c0157600>] ? kthread+0x0/0x90
Oct 10 22:21:22 whlee-timeline kernel: [  689.175685]  [<c0103f17>] ? kernel_thread_helper+0x7/0x10
Oct 10 22:22:02 whlee-timeline kernel: Kernel logging (proc) stopped.

---

### Post by TwiceOver on 2009-10-11
> **TexLogic said:**
> Thanks for this.  I was experiencing exactly the same problem -- using the brightness hotkey would indeed dim the screen but would lock up the window mgr.  Turning off Visual Effects also solves the problem for me.  I dig the effects, but they're total eye candy so I can certainly live with that til they fix it.

TexLogic

Be sure to add yourself to the bug here:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/446717](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/446717)

---

### Post by netimen on 2009-10-12
> **quail-linux said:**
> I have GREAT news for the 4810T owners the 2.30 BIOS[1] is rockin we now have backlight control keys working :-D

There is a catch tho you have to change from
```
xrandr --output LVDS --set BACKLIGHT_CONTROL native
```
to
```
xrandr --output LVDS --set BACKLIGHT_CONTROL kernel
```
or you will get a freeze type effect on the desktop. Also I noticed that my wifi went funny to and I could not ping anything even tho NM was say I was connected to AP. 

**So [COLOR="Red"]DON'T[/COLOR] play with backlight key till done the above changes.**

[1] [http://support.acer-euro.com/drivers/downloads_gd.html](http://support.acer-euro.com/drivers/downloads_gd.html)

Edit: I have noticed this works correctly in 'combination' too
```
xrandr --output LVDS --set BACKLIGHT_CONTROL combination
```

I tried this fix but it didn't work for me: when I used the brightness keys on the keyboard the system became unstable

---

### Post by iceman on 2009-10-12
Is anyone be able to suspend to ram/S3 Acer 3810t with recent kernels?
Is there some trick?
I can't believe there is no way to suspend after a lots of months this notebook is out... and after so many persons ask to solve or understand why it does not works.

P.s. It's not polemic... I am really tired to powerup/shutdown everytime i need notebook for 3-4 minutes... We are in 2009 and i think this shold be normal! Why there is no news about this issue?

---

### Post by miegiel on 2009-10-12
> **iceman said:**
> Is anyone be able to suspend to ram/S3 Acer 3810t with recent kernels?
Is there some trick?
I can't believe there is no way to suspend after a lots of months this notebook is out... and after so many persons ask to solve or understand why it does not works.

P.s. Please, don't remove this post... It's not polemic... I am really tired to powerup/shutdown everytime i need notebook for 3-4 minutes... We are in 2009 and i think this shold be normal! Why there is no news about this issue?

I'm blaming Acer, this BIOS (1.10 3810T) doesn't support virtualization either. And (correct me if I'm wrong) the AHCI problem isn't fixed, but patched in the kernel. I bet they messed up the suspend/resume code in the BIOS too.

Hibernate is your best option for now.


*edit:*
btw the bug report is here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405120](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405120)

---

### Post by Nixblicker on 2009-10-13
Hello everybody,

should someone have the internal mic problem for example to use it with skype under jaunty 64bit on a 3810T (don't know if it is a widespread timeline problem), i found the solution [here]("https://lists.launchpad.net/acertimeline/msg00039.html") how to fix it.
In short, go to gnome sound settings and activate "Master, PCM, Front, Front Mic, Front Mic Boost, Capture, Headphone" and most important "Input source".
This let you choose "int. mic" in the gnome sound settings "Options" for "HDA Intel (Alsa mixer)".
Now select "HDA intel (hw:intel,0)" as mic in Skype audio settings and you are done.

Hope that helps anyone...
Thx. go out to Rod (original post above)

Cheers,
Nix

---

### Post by Arlanthir on 2009-10-13
> **Nixblicker said:**
> Hello everybody,

should someone have the internal mic problem for example to use it with skype under jaunty 64bit on a 3810T (don't know if it is a widespread timeline problem), i found the solution [here]("https://lists.launchpad.net/acertimeline/msg00039.html") how to fix it.
In short, go to gnome sound settings and activate "Master, PCM, Front, Front Mic, Front Mic Boost, Capture, Headphone" and most important "Input source".
This let you choose "int. mic" in the gnome sound settings "Options" for "HDA Intel (Alsa mixer)".
Now select "HDA intel (hw:intel,0)" as mic in Skype audio settings and you are done.

Hope that helps anyone...
Thx. go out to Rod (original post above)

Cheers,
Nix

I don't think I have those options on karmic :S

---

### Post by Marat89 on 2009-10-14
Hi
I do not know if the question was aked before.
I have problems with my Bluetooth, has anybody a hint to activate the Bluetooth of Acer Aspire 3810T?
Fn-Key does not work.
Gnome-Bluetooth says, I have no bluetooth-device.

Thx

---

### Post by sotomajor on 2009-10-14
> **Arlanthir said:**
> I don't think I have those options on karmic :S
So, does anybody know how to get working microphone in Karmic? Seems, I've tried all possible combinations of alsa and pulseaudio settings and no effect.
External microphone doesn't work also. The only thing - when enabling "Input source : front mic" and setting up high level of "Front Mic Boost" - I hear some noise, but it doesn't seems to be noise from microphone because nothing being recorded. :confused:

Btw, I can select nothing except 'Pulseaudio' as device in Skype...

---

### Post by miegiel on 2009-10-14
> **sotomajor said:**
> So, does anybody know how to get working microphone in Karmic? Seems, I've tried all possible combinations of alsa and pulseaudio settings and no effect.
External microphone doesn't work also. The only thing - when enabling "Input source : front mic" and setting up high level of "Front Mic Boost" - I hear some noise, but it doesn't seems to be noise from microphone because nothing being recorded. :confused:

Btw, I can select nothing except 'Pulseaudio' as device in Skype...

Though the timeline has ICH9 Family sound I think it's this bug:
[https://bugs.edge.launchpad.net/ubuntu/+bug/409819](https://bugs.edge.launchpad.net/ubuntu/+bug/409819)

---

### Post by quail-linux on 2009-10-14
Anyone with the TSSTcorp DVD+-RW TS-U633A optical drive tried updating there firmware?

The only place I have found the firmware[1]. And they don't have instructions on how to do it. :confused:  By what I can gather is the version is *Official DW10* for download.

How do I find out what the version of firmware my TSSTcorp DVD+-RW TS-U633A is using?

[1] [http://files.rpc1.org/index.php?act=category&id=1816](http://files.rpc1.org/index.php?act=category&id=1816)

---

### Post by quail-linux on 2009-10-14
> **quail-linux said:**
> How do I find out what the version of firmware my TSSTcorp DVD+-RW TS-U633A is using?

I was having a brain fart moment before, I got my answer.
```
# hdparm -I /dev/dvd

/dev/dvd:

ATAPI CD-ROM, with removable media
	Model Number:       TSSTcorp CDDVDW TS-U633A                
	Serial Number:      
	Firmware Revision:  AC01    
	Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5
Standards:
	Supported: CD-ROM ATAPI-3 -4 -5 -6 -7 
Configuration:
	DRQ response: 50us.
	Packet size: 12 bytes
Capabilities:
	LBA, IORDY(can be disabled)
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SATA-I signaling speed (1.5Gb/s)
	   *	Host-initiated interface power management
	   *	Phy event counters
	    	Device-initiated interface power management
	    	Asynchronous notification (eg. media change)
	   *	Software settings preservation
```

---

### Post by megaexception on 2009-10-15
with kernel 2.6.31-11-generic-pae i can achieve 6+ hours on batteries (without wifi i get max 6.5 hours of web+ssh+console via wired network)
with kernel 2.6.31-12 or newer, i can only get max 3 hours (with dark screen and no activity).
powertop says 10watts consumption on 2.6.31-11 and 20watts on newer kernels, but i cannot figure out the reason.

can someone tell me what can cause such degradation?

---

### Post by quail-linux on 2009-10-15
> **megaexception said:**
> with kernel 2.6.31-11-generic-pae i can achieve 6+ hours on batteries (without wifi i get max 6.5 hours of web+ssh+console via wired network)
with kernel 2.6.31-12 or newer, i can only get max 3 hours (with dark screen and no activity).
powertop says 10watts consumption on 2.6.31-11 and 20watts on newer kernels, but i cannot figure out the reason.

can someone tell me what can cause such degradation?

This might start some debate that I not really want to start, but for your question it hard to say.  I not sure if it still the case but as far as I know and still understand is that odd numbered kernels are in theory unstable as the kernel branching works.

With the 2.6.31 kernel my laptop just goes to crap with cd/dvd drive problems etc.  Best I can recommend is to drop back to 2.6.30 kernel and wait for 2.6.32.

---

### Post by Sashin on 2009-10-15
How long will it be 'til that?

---

### Post by quail-linux on 2009-10-15
> **Sashin said:**
> How long will it be 'til that?

iirc the kernel.org term work on a ~3 month release bases, so you be looking at a couple months.

---

### Post by megaexception on 2009-10-15
afaik, odd numbered kernels are not considered unstable anymore. so, problems can be fixed later in 2.6.31.x series, or not be fixed even in 2.6.32.

and another one problem - ubuntu's pae kernel is not tickless. with tickless kernel 6+ hours result can be improved.

---

### Post by Marat89 on 2009-10-16
HI
I have following problems with my 3810T and Karmic:
Under the Laptop, it is very warm.
and the fan runs almost constantly.
Anybody have this problems too?
Could a BIOS upgrade fix the probs?
Thanks
EDIT: 27°C (ACPI)
When on the laps, its quite annoying.

---

### Post by fowie on 2009-10-16
I know suspend doesn't work right now, but I don't think I have hibernate working on my 3810T under Karmic either.  How can I tell if hibernate is working, and how could I force it to go into hibernation (maybe a command line instead of clicking some button?)

---

### Post by deconstructingme on 2009-10-16
> **fowie said:**
> I know suspend doesn't work right now, but I don't think I have hibernate working on my 3810T under Karmic either.  How can I tell if hibernate is working, and how could I force it to go into hibernation (maybe a command line instead of clicking some button?)

Hibernate works perfectly on my 3810T. All I do is choose hibernate off the top right Gnome menu where the Empathy status/suspend/hibernate/etc... options are located. The machine hibernates and wakes up every time without fail.

---

### Post by fowie on 2009-10-16
Thanks, but I need to know how I can tell if it's really happening.  I'm assuming it's not because when I close the lid, the screen goes black, but when I open the lid it just turns the screen back on.  Closing the lid doesn't seem to really put it into hibernate for me (note, I have the SSD model)

---

### Post by nortexoid on 2009-10-16
> **tokyoahead said:**
> ...the battery is actually 8 hours w/o problems.

I'm not sure that would be true running Ubuntu, unfortunately. Vista (and Windows 7) has much better power management. See [http://www.anandtech.com/mobile/showdoc.aspx?i=3642&cp=2](http://www.anandtech.com/mobile/showdoc.aspx?i=3642&cp=2), for example.

---

### Post by deconstructingme on 2009-10-16
> **fowie said:**
> Thanks, but I need to know how I can tell if it's really happening.  I'm assuming it's not because when I close the lid, the screen goes black, but when I open the lid it just turns the screen back on.  Closing the lid doesn't seem to really put it into hibernate for me (note, I have the SSD model)

You may not have the power management settings set to hibernate when the lid closes. That's why I suggested using the menu on the top right, because you don't close the screen, you just select hibernate and watch it go to sleep. When you press the power button to wake up your laptop, you will see the GRUB menu, then it will wake up and ask for your password to unlock the screen saver.

Check your power management settings to see what your laptop is set to do when the lid closes.

---

### Post by fowie on 2009-10-16
[SOLVED] Thanks, my problem was that due to my copious amounts of memory I had decided not to have a swap partition, and that makes it quite difficult to swap memory for a hibernate...oops.  Remember kids, if you want to hibernate, you need a swap partition.

---

### Post by DevinD on 2009-10-21
I've also been having problems with the brightness control - running 9.10 beta (with latest upgrades) on an Acer Timeline 4810t. I tried the 
xrandr --output LVDS --set BACKLIGHT_CONTROL native
as was suggested, but it tells me

X Error of failed request:  BadRROutput (invalid Output parameter)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  15 (RRGetOutputProperty)
  Serial number of failed request:  30
  Current serial number in output stream:  30

When I first got my laptop a few months back I was running 9.04 and on upgrading the kernel this problem was fixed, but when I installed 9.10 the problem returned. Is there any reason why this command won't work for me?

---

### Post by miegiel on 2009-10-21
> **DevinD said:**
> I've also been having problems with the brightness control - running 9.10 beta (with latest upgrades) on an Acer Timeline 4810t. I tried the 
xrandr --output LVDS --set BACKLIGHT_CONTROL native
as was suggested, but it tells me

X Error of failed request:  BadRROutput (invalid Output parameter)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  15 (RRGetOutputProperty)
  Serial number of failed request:  30
  Current serial number in output stream:  30

When I first got my laptop a few months back I was running 9.04 and on upgrading the kernel this problem was fixed, but when I installed 9.10 the problem returned. Is there any reason why this command won't work for me?

Did you upgrade from jaunty or do a new install? It's possible that some configuration files from jaunty are messing things up.

In any case;
[LIST]
[*]Is [_this thread_]("http://ubuntuforums.org/showthread.php?t=1253179") useful?
[*]Do a search for *"brightness"* in the [_karmic subforum_]("http://ubuntuforums.org/forumdisplay.php?f=359"). Karmic has less and less bugs, but it's not bug free yet (also the proper forum for karmic problems ;)).
[*]Check if you have a file called */etc/X11/xorg.conf* If you do, see if there's anything mentioned about brightness in the file.
[/LIST]

The only problem I've had (3810T) with brightness in karmic,is that for a while when it was still alpha, the OSD didn't show the brightness indicator. But the keys always worked. And I've never needed to use
```
xrandr --output LVDS --set BACKLIGHT_CONTROL native
```

---

### Post by Nordfjord on 2009-10-24
Hi all. So I was having the same [problems]("http://ubuntuforums.org/showpost.php?p=7828339&postcount=222") as joseph_d had a while ago, and I followed someone's advice to used lilo to reinstall the mbr. Unfortunately, that didn't work, and left me unable to boot into any OS.

But I'm also having another problem. I'm unable to boot off of any external media except for the Acer-supplied Windows Vista disc. I don't know why, but I've tried dozens of CDs, DVDs and USB sticks, and the only thing it'll boot from is the Acer Vista disc -- it won't even boot from HP or Dell Windows discs. Unfortunately, the Vista disc gives me the same error as joseph_d was receiving from the recovery partition. So I 1. don't have a working OS, and 2. can't boot off of OS installation media. It's a pickle.

So is there some option in the BIOS (1.07) or anything else that might make me unable to boot off of anything non-Acer? I've been talking to their tech support, but they're totally useless, and I thought you guys would probably know a lot more....

---

### Post by miegiel on 2009-10-24
> **Nordfjord said:**
> Hi all. So I was having the same [problems]("http://ubuntuforums.org/showpost.php?p=7828339&postcount=222") as joseph_d had a while ago, and I followed someone's advice to used lilo to reinstall the mbr. Unfortunately, that didn't work, and left me unable to boot into any OS.

Define *"not being able to boot"*, sorry it's really to vague. Try to describe as well as you can at what point in the boot process the boot doesn't continue and what is the last successful step in the boot process (include any errors and/or unexpected behavior).

> But I'm also having another problem. I'm unable to boot off of any external media except for the Acer-supplied Windows Vista disc. I don't know why, but I've tried dozens of CDs, DVDs and USB sticks, and the only thing it'll boot from is the Acer Vista disc -- it won't even boot from HP or Dell Windows discs. Unfortunately, the Vista disc gives me the same error as joseph_d was receiving from the recovery partition. So I 1. don't have a working OS, and 2. can't boot off of OS installation media. It's a pickle.

As above, but also test the CDs and USB sticks (especially the ones you made yourself) in another machine to verify they really are bootable.

> So is there some option in the BIOS (1.07) or anything else that might make me unable to boot off of anything non-Acer?

No, that would be illegal in most countries. But do check the boot options in your BIOS and make sure the removable media are listed before you harddisk.

>  I've been talking to their tech support, but they're totally useless, and I thought you guys would probably know a lot more....

I don't care much for support (other than the community base kind) so I bought an acer regardless of the quality of their support. I tell all my friends not to buy acer :twisted:

Almost forgot ... what version of ubuntu are you using (to avoid confusion) and which timeline do you have ?

---

### Post by Marat89 on 2009-10-24
Timeline 3810T - Have you problems with your fan?
The fan here starts too often, so the laptop is very warm.
Anybody have a working Bluetooth?

---

### Post by miegiel on 2009-10-24
> **Marat89 said:**
> Timeline 3810T - Have you problems with your fan?
No
> The fan here starts too often, so the laptop is very warm.
The fan spins up when the CPU is above 46C
> Anybody have a working Bluetooth?
Yes, but I only tested it with my sisters phone (I don't own ant bluetooth devices)

Xubuntu karmic on 3810T BIOS 1.10

---

### Post by Marat89 on 2009-10-24
But I have a question.
I used the laptop with Vista a couple hrs and the fan runs barely. The device is cool.

Whats the problem now in Karmic? What can I change? Is there any control applet (gui)available?
Thanks

---

### Post by miegiel on 2009-10-24
> **Marat89 said:**
> But I have a question.
I used the laptop with Vista a couple hrs and the fan runs barely. The device is cool.

Whats the problem now in Karmic? What can I change? Is there any control applet (gui)available?
Thanks

Linuxes let the BIOS control the fan, unless you install software that takes fan control over from the BIOS (I read in the *lm-sensors* thread you can use *pwmconfig* to change fan speeds, but never tried it).

In windows the BIOS fan settings are generally ignored by the OS and speeds are controlled by the OS, drivers or 3rd party apps.

---

### Post by Marat89 on 2009-10-24
Cool Thx for the info ;-)
I tried to disable Compiz-- and now its perfect. No fan noise at all.. cool device.
to BT:
How did you make Bluetooth run?

---

### Post by miegiel on 2009-10-24
> **Marat89 said:**
> Cool Thx for the info ;-)
I tried to disable Compiz-- and now its perfect. No fan noise at all.. cool device.
to BT:
How did you make Bluetooth run?

[LIST=1]
[*]Turned on bluetooth (icon in notification area or Fn+F3)
[*]Turned on bluetooth on the phone
[*]"Discovered" the phone from my laptop (*bluetooth preferences*, via the menu of the bluetooth icon in notification area)
[*]Copied one of my favorite mp3 's to the phone
[/LIST]

---

### Post by Marat89 on 2009-10-24
> **miegiel said:**
> [LIST=1]
[*]Turned on bluetooth (icon in notification area or Fn+F3)

[/LIST]

But I have no icon in the notifications area?!
Fn+F3 does nothing, I get no visual feedback weather bt is on/off

Thanks

---

### Post by miegiel on 2009-10-24
> **Marat89 said:**
> But I have no icon in the notifications area?!
Fn+F3 does nothing, I get no visual feedback weather bt is on/off

Thanks
To start the same thing from a terminal run :
```
bluetooth-properties
```
Maybe you don't have the bluetooth packages installed (in jaunty I assume, I'm using karmic already). Run the following to verify :
```
apt-cache policy bluetooth
apt-cache policy bluez
```
I'm not sure which package it's in :D I have both installed. To install them :
```
sudo apt-get install bluetooth
```
and/or
```
sudo apt-get install bluez
```
You might want to investigate the packages before installing them.

---

### Post by Sashin on 2009-10-24
Anyone have any magical fixes for touchpad one/off and brightness on the 4810T.

---

### Post by Marat89 on 2009-10-25
> **miegiel said:**
> To start the same thing from a terminal run :
```
bluetooth-properties
```
Maybe you don't have the bluetooth packages installed (in jaunty I assume, I'm using karmic already). Run the following to verify :
```
apt-cache policy bluetooth
apt-cache policy bluez
```
I'm not sure which package it's in :D I have both installed. To install them :
```
sudo apt-get install bluetooth
```
and/or
```
sudo apt-get install bluez
```
You might want to investigate the packages before installing them.

Thank you for the instructions.
I have Karmic here and both packages are installed.
But no icon in the not. area...
I have no idea whats the problem.

---

### Post by PatrickVogeli on 2009-10-25
Hi there,

finally I've got an Acer 1810TZ, with the dual core Intel SU4100. I believe this laptop is very similar to the 3810T.

I have installed Karmic and the internal microphone doesn't work, and I think I've read this problem in this thread. Can someone confirm that?

My girlfriend, with a Packard Bell machine (similar to the Acer 1410) has Jaunty installed and the internal microphone is working.

Those laptops have the ALC269 codec, same as the 3810T?

---

### Post by miegiel on 2009-10-25
> **Marat89 said:**
> Thank you for the instructions.
I have Karmic here and both packages are installed.
But no icon in the not. area...
I have no idea whats the problem.

The last possibility I can think of is that you're missing the icons. Try :
```
sudo apt-get install humanity-icon-theme
```
If that still doesn't fix it and you can launch the *bluetooth preferences* with ```
bluetooth-properties
``` from a terminal, you could add a custom launcher to you panel. But *bluetooth* should also be listed in the settings menu.

For a while I didn't have the bluetooth icon in the notification area in karmic either, but it was still alpha 4 or 5 then. After that the icon would only show when bluetooth was on. Now it always shows (the icon is darker when it's off) in both ubuntu and xubuntu karmic.

> **PatrickVogeli said:**
> Hi there,

finally I've got an Acer 1810TZ, with the dual core Intel SU4100. I believe this laptop is very similar to the 3810T.

I have installed Karmic and the internal microphone doesn't work, and I think I've read this problem in this thread. Can someone confirm that?
Confirmed (happy owner of 3 external microphones) :roll:
> My girlfriend, with a Packard Bell machine (similar to the Acer 1410) has Jaunty installed and the internal microphone is working.

Those laptops have the ALC269 codec, same as the 3810T?

```
aplay -l
```
should tell you that, for example on my 3810T :
```
user@machine:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: **ALC269** Analog [ALC269 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: **ALC269** Digital [ALC269 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by PatrickVogeli on 2009-10-25
Yeah, my aplay -l output is the same as yours. Maybe it's time to open a bug report?

---

### Post by miegiel on 2009-10-25
> **PatrickVogeli said:**
> Yeah, my aplay -l output is the same as yours. Maybe it's time to open a bug report?

There is a [_bug report_]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/409819"), the problem is it is very polluted by people who didn't check their *alsamixer* settings before confirming they had this bug. So a lot of people who think they have this bug are posting that it can be fixed by changing the selected microphone and/or in/out-put volumes in *alsamixer*. As a result the bug is going nowhere.

The bug report clearly states :
> I played with Sound preferences, made sure "mute" was unchecked and I also tried in alsamixer to increase the mic boost and I tried out both "Internal" and "Mic" options.
Sadly the majority of the people didn't read the 2nd sentence in the report :(

Besides the acer timeline, the bug affects several (but not all) laptops with ICH8 and ICH9 Family sound.

---

### Post by PatrickVogeli on 2009-10-26
Ok, I got it working!

I assume you already tried the backport-modules packages, right?

I can't really say what fixed it, since I use a custom compiled kernel (por PHC undervolting). You could try installing alsa-drivers 1.0.21, which guess is what did the trick for me.

---

### Post by miegiel on 2009-10-26
> **PatrickVogeli said:**
> Ok, I got it working!
cool
> I assume you already tried the backport-modules packages, right?
yes
> I can't really say what fixed it, since I use a custom compiled kernel (por PHC undervolting). You could try installing alsa-drivers 1.0.21, which guess is what did the trick for me.
I'm guessing it's the alsa-drivers you installed. If it's not to much trouble tell us where you got them and how you installed it ;)

---

### Post by PatrickVogeli on 2009-10-27
Hi, sure, I'll try to help:

Download the alsa-drivers 1.0.21 from here: [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.21.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.21.tar.bz2)

Extract them, and to build and install:
```

cd path/to/extracted/folder
./configure --with-cards=hda-intel
make
sudo make install

```

Reboot and you should be fine. You may have to install some development tools, like build-essential and so on. If you need further assistance jus tell me, and I'll try to explain a bit better.

---

### Post by miegiel on 2009-10-28
> **PatrickVogeli said:**
> Hi, sure, I'll try to help:

Download the alsa-drivers 1.0.21 from here: [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.21.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.21.tar.bz2)

Extract them, and to build and install:
```

cd path/to/extracted/folder
./configure --with-cards=hda-intel
make
sudo make install

```

Reboot and you should be fine. You may have to install some development tools, like build-essential and so on. If you need further assistance jus tell me, and I'll try to explain a bit better.
Didn't work on my 3810T :(

---

### Post by jimmy the saint on 2009-10-29
I just wanted to chime in with my 2cents

I downloaded the release candidate a few days ago and have been using it as a live USB since then.  I have an 8310 with the SU 9400.  It is pretty snappy with Ubuntu's default settings.  I like much better than Hardy on my Thinkpad T61.  

There is a deal breaker for me, however.  The battery life is abysmal.  There is a 4 hour difference between the Vista install and Karmic.  I got more than 7 hours running Vista at school, working online and browsing the intertubes.  I was shocked to see the estimated battery life in Karmic at a little over 3.5 hours.  I was more shocked to see that it was actually a little under 3.5 hours doing similar tasks.

I saw a post about this issue a few pages back, and I am aware that there is usually a slight sacrifice, but it has never been like that.  Even the Asus 1000HE, with special windows-centric hacks to improve battery life only gave up 2 of the 7 hours.  This will not work at all.  I have no idea what the deal is, and I will do a little digging, but this has to change before I will even consider Karmic.  I spent a lot of money on a laptop specifically for the balance between performance and battery life.  I think this needs some attention, so I posted here.  I know a lot of people smarter than me are watching this thread, hopefully we can come up with something.

Edit: I forgot to mention the mousepad sensitivity.  For me, I have to flip the bird in order to use it.  If another finger gets within an inch of the touchpad, the thing goes nuts.  

Thanks for listening/reading!

JTS

---

### Post by iceman on 2009-10-30
Jimmy, i'm agree with you in everything. Those Are the same considerations i Made...
It's not acceptable in 2009 to have not battery life and S3...

---

### Post by schonni on 2009-10-30
> **miegiel said:**
> Didn't work on my 3810T :(
didn't work for me, too. to the contrary: the possibility to change the input source in alsamixer has gone now. is it possible to change it back?

---

### Post by miegiel on 2009-10-30
> **schonni said:**
> didn't work for me, too. to the contrary: the possibility to change the input source in alsamixer has gone now. is it possible to change it back?

I just installed the released karmic. It was time to cleanup my installation anyway. I tried removing it, but it wanted to uninstall (x)ubuntu-desktop too, though you could reinstall the desktop again.

---

### Post by avilella on 2009-10-31
Any particular improvements with the latest version? Anything you had to manually fix?

> **miegiel said:**
> I just installed the released karmic. It was time to cleanup my installation anyway. I tried removing it, but it wanted to uninstall (x)ubuntu-desktop too, though you could reinstall the desktop again.

---

### Post by miegiel on 2009-10-31
> **avilella said:**
> Any particular improvements with the latest version? Anything you had to manually fix?

Now I also [_don't have bluetooth_]("http://ubuntuforums.org/showthread.php?p=8158944#post8158944") in my notification area or settings menu (haven't tried to fix it yet). Sound isn't muted after reboot anymore, but that only bugged me in xubuntu. I haven't used the new installation much yet, so I can't say anything about battery life. If you haven't somehow wrecked your karmic (from alpha, beta or rc) there's no reason to reinstall, not that I noticed anyway.

---

### Post by avilella on 2009-10-31
Can you run powertop on batteries and see what is the power consumption in Watts?

> **miegiel said:**
> Now I also [_don't have bluetooth_]("http://ubuntuforums.org/showthread.php?p=8158944#post8158944") in my notification area or settings menu (haven't tried to fix it yet). Sound isn't muted after reboot anymore, but that only bugged me in xubuntu. I haven't used the new installation much yet, so I can't say anything about battery life. If you haven't somehow wrecked your karmic (from alpha, beta or rc) there's no reason to reinstall, not that I noticed anyway.

---

### Post by miegiel on 2009-10-31
> **avilella said:**
> Can you run powertop on batteries and see what is the power consumption in Watts?

I never really used *powertop*, didn't make a significant difference for me. Power use is the same as in the alphas and beta (judging by the mA I'm sucking out of the battery).

---

### Post by Dan48p on 2009-10-31
Hey guys, i just installed 9.10 upgrade option on my laptop.  I wanted to note here that all of my external displays are working perfectly.

With both 9.04 and win7 i was unable to get these displays 1440x900 and 1680x1050 to function at native resolution.  I used these displays one at a time not all at the same time.

9.10 immediately recognizes the displays and lets me add them in the "displays" option.

This is on a 3810tz (su2700, with intel graphics I believe).

Additionally, the excessive flickering at boot seem to have gone away, though I have only booted up this machine a few times.


dan

---

### Post by almozavr on 2009-11-03
MIC problem is SOLVED

Yes, new alsa supports Acer 3810T audio system (Intel 45 mobile chipset). But I didn't succeeded in manual installation. So I used great script for Auto Update (it also installed ~260 MB of dependencies, be patient).

----------------------------------------------------

You can find ALSA Upgrade Script [here]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810") ;)

---

### Post by pfem on 2009-11-03
> **almozavr said:**
> MIC problem is SOLVED

Yes, new alsa supports Acer 3810T audio system (Intel 45 mobile chipset). But I didn't succeeded in manual installation. So I used great script for Auto Update (it also installed ~260 MB of dependencies, be patient).

----------------------------------------------------

You can find ALSA Upgrade Script [here]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810") ;)

Not working for me.

---

### Post by almozavr on 2009-11-03
> **pfem said:**
> Not working for me.

After you checked that script SUCCESSFULLY installed latest drivers (alsactl -v command should give you 1.0.21) you should install Multimedia System Selector where choose ALSA for Audio->Default Input->Plugin and install Alsa Mixer where increase slider Capture and check button Rec.

Works just fine, you should try again ;)

---

### Post by miegiel on 2009-11-03
> **almozavr said:**
> ... you should install Multimedia System Selector where choose ALSA for Audio->Default Input->Plugin ...

Can you be a bit more precise? I can't find that *Multimedia System Selector*
[http://packages.ubuntu.com/search?suite=karmic&section=all&arch=any&searchon=all&keywords=Multimedia+System+Selector](http://packages.ubuntu.com/search?suite=karmic&section=all&arch=any&searchon=all&keywords=Multimedia+System+Selector)

Never mind, I found it :
```
sudo apt-get install gnome-media
```
and then
```
gstreamer-properties
```
Still doesn't work though, regardless of the *alsamixer* settings. Now even my external mic is dead (the same as with installing *linux-backports-modules-alsa-karmic-generic*).

---

### Post by almozavr on 2009-11-03
> **miegiel said:**
> Can you be a bit more precise? I can't find that *Multimedia System Selector*
[http://packages.ubuntu.com/search?suite=karmic&section=all&arch=any&searchon=all&keywords=Multimedia+System+Selector](http://packages.ubuntu.com/search?suite=karmic&section=all&arch=any&searchon=all&keywords=Multimedia+System+Selector)

I'm sorry. ***The Multimedia System Selector*** is the second name of *gnome-media* package (you can find it in synaptic or software center as pre-installed). 

So, you can make it visible in Gnome Menu Properties or just *Alt+F2 *and type *gstreamer-properties*

The next step is to set ***ALSA mixer*** (*gnome-alsamixer* package). Enable all devices and increase Capture (with Rec. checked) and Digital values to make it work 

Good Luck ;)

---

### Post by miegiel on 2009-11-03
Ok, I'll make sure not to ignore the digital settings.

*edit:*
I've kind of got it working now. My comments are in [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/459982/comments/10](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/459982/comments/10)
thanks for the help **almozavr**

---

### Post by pfem on 2009-11-04
> **miegiel said:**
> Ok, I'll make sure not to ignore the digital settings.

*edit:*
I've kind of got it working now. My comments are in [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/459982/comments/10](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/459982/comments/10)
thanks for the help **almozavr**

What you're saying on that link is that you uninstalled alsa 1.0.21 ?

---

### Post by almozavr on 2009-11-04
> **pfem said:**
> What you're saying on that link is that you uninstalled alsa 1.0.21 ?

WTF? Link leads to Alsa Update Script forum page!!! Read carefully

---

### Post by pfem on 2009-11-04
> **almozavr said:**
> WTF? Link leads to Alsa Update Script forum page!!! Read carefully

I'm not an expert in these matters. If somehow my question offended you, it wasn't meant to. I asked a question because I'm confused about what to do.

If someone could help, I'd be thankful.

On a side note, I hope that when you need help, no one replies with "WTF".

---

### Post by almozavr on 2009-11-04
> **almozavr said:**
> MIC problem is SOLVED

Yes, new alsa supports Acer 3810T audio system (Intel 45 mobile chipset). But I didn't succeeded in manual installation. So I used great script for **Auto Update** (it also installed ~260 MB of dependencies, be patient).

----------------------------------------------------

You can find **ALSA Update Script** [here]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810") ;)

I'm not an expert too. 
But what do you expect from link when it's description says AUTO UPDATE. Not an Uninstall. But  UPDATE. Maybe you should go by link and try to find out what it's all about before asking about unistalling.

It's simple, READ carefully.

---

### Post by almozavr on 2009-11-05
FINALLY!

There is **no** need to add **libata.force=noncq** to kernel command line for normal booting with **AHCI mode**!

It seems to be the **latest linux 2.6.32-rc6** kernel supports NCQ mode for Acer 3810T (it's all about Hitachi HDD)! 
Also my booting speed is 32 second now after 40 seconds on 2.6.31 kernel.

I also hope that enabling NCQ feature now will increase battery life on 3810T (now it's only 4,5 hours for me versus 7(!) on Windows 7)

P.S. you can find .deb packages of the latest kernel [here]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32-rc6/")

Good luck ;)

---

### Post by deconstructingme on 2009-11-05
I bought my 3810T just when Karmic Beta was released and never needed to add **libata.force=noncq**. It's always booted just fine with AHCI.

The only problems I've encountered have been the mic problem which was solved and the suspend/resume issue. I'm looking forward to that one getting fixed.

> **almozavr said:**
> FINALLY!

There is **no** need to add **libata.force=noncq** to kernel command line for normal booting with **AHCI mode**!

It seems to be the **latest linux 2.6.32-rc6** kernel supports NCQ mode for Acer 3810T (it's all about Hitachi HDD)! 
Also my booting speed is 32 second now after 40 seconds on 2.6.31 kernel.

I also hope that enabling NCQ feature now will increase battery life on 3810T (now it's only 4,5 hours for me versus 7(!) on Windows 7)

P.S. you can find .deb packages of the latest kernel [here]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32-rc6/")

Good luck ;)

---

### Post by pfem on 2009-11-05
> **almozavr said:**
> WTF? Link leads to Alsa Update Script forum page!!! Read carefully

Now that i see, i replied to miegel's post, not your post.

SO, since I'm unable to put my mic to work, go write a decent tutorial or GTFO of my face.

---

### Post by jimmy the saint on 2009-11-05
My touchpad goes absolutely bonkers all the time.  I have to be extremely careful because if a second finger gets within a quarter inch of the touchpad, the cursor jumps all over the screen clicking everywhere, highlighting text, selecting items and causing general havoc.  

Has anyone else experienced this and is there a fix?  

Thanks

JTS

---

### Post by almozavr on 2009-11-06
> **jimmy the saint said:**
> My touchpad goes absolutely bonkers all the time.

Yeah, the same for me...

---

### Post by Sashin on 2009-11-06
Anyone know how to get brightness working on 4810T with Karmic?

---

### Post by lemurian on 2009-11-06
> **deconstructingme said:**
> I bought my 3810T just when Karmic Beta was released and never needed to add **libata.force=noncq**. It's always booted just fine with AHCI.


And I bought my 3810T before Karmic Beta.  I've run Jaunty on it for months and never had to do anything about AHCI.  It just booted fine on the first try and every time thereafter.

---

### Post by citizenofnowhere on 2009-11-06
> **jimmy the saint said:**
> My touchpad goes absolutely bonkers all the time.  I have to be extremely careful because if a second finger gets within a quarter inch of the touchpad, the cursor jumps all over the screen clicking everywhere, highlighting text, selecting items and causing general havoc.  

Has anyone else experienced this and is there a fix?  

There's a few things that might be going on here. Firstly, are you running 9.10 or 9.04? 9.10 has a much newer touchpad driver.

Secondly, there is now in Karmic a touchpad tweak you can try that is supposed to prevent cursor jumpiness. It's called JumpyCursorThreshold (there's a lot of howtos out there on getting this to work).

All that being said, this is my personal experience: I had a beautifully working touchpad until my 3810 went to the service centre for the recall. WHen it came back they had swapped some touchpad cable that caused it to start jumping around like mad and it was almost unuseable. 

NOTE: I was however able to reproduce the same behavior on Vista which convinced them to swap it again and now it's working fine.

Conclusion: if you don't have issues on Vista, try some workarounds like the Synaptics option I posted above. If you get stuck I can of course give you a copy of my options file I just don't have it on hand. If you do have issues on Vista as well - get them to swap it for you!

Mine was crazy around the edges particularly, that's a good place to test.

---

### Post by muadnu on 2009-11-06
> **citizenofnowhere said:**
> ...

All that being said, this is my personal experience: I had a beautifully working touchpad until my 3810 went to the service centre for the recall. WHen it came back they had swapped some touchpad cable that caused it to start jumping around like mad and it was almost unuseable.

...

About the recall, I'm wondering what people's experience has been. I was about to try to contact Acer to get mine fixed, but (apart from the fact that their webpage didn't let me request it) I read about people having huge issues with the Acer support (not really surprising), with their laptops taking a long time to come back, a coming back with scratches and things not working.

On the other hand, I just don't know if it's worth it. Is it really a big issue? Would you recommend getting this mysterious mic cable fixed?

---

### Post by citizenofnowhere on 2009-11-06
> **muadnu said:**
> 
On the other hand, I just don't know if it's worth it. Is it really a big issue? Would you recommend getting this mysterious mic cable fixed?

Hi muadnu!

I think experiences vary country by country. I know on some countries Acer outsorces their service centers, so I would expect that to be less than an ideal situation. In Singapore where I got my 3810 though, Acer's been pretty great. They picked it up from me, and had it back within 3 working days (granted I think I was one of the first to send it in). They've also do some on the spot repairs here (fixed my touchpad cable in like 3 hours) and have done a motherboard replacement within 3 working days before too.

Mileage may vary though :)

---

### Post by jimmy the saint on 2009-11-06
About the recall.  I had some trouble with the customer service people regarding it.  I am a student and need this laptop so I was concerned about how long it would take.  After a couple weeks of getting nowhere with the indian "support" staff, I called the corporate headquarters in California.  I ended up talking with one of the people at the repair center about this recall.  Apparently the insulation on the microphone wire gets worn through, causing the microphone to stop working.  If you look at the images in this thread of the 3810t taken apart, you can see the issue is likely that the microphone cable is draped over the sharp edges of the HD enclosure.  I can't say with 100% certainty because I haven't had it replaced yet, but my guess is that they move the wire so that it is not on that sharp edge.  I wish they would just send me the dang wire so i can do it myself.

---

### Post by muadnu on 2009-11-06
> **jimmy the saint said:**
> About the recall.  I had some trouble with the customer service people regarding it.  I am a student and need this laptop so I was concerned about how long it would take.  After a couple weeks of getting nowhere with the indian "support" staff, I called the corporate headquarters in California.  I ended up talking with one of the people at the repair center about this recall.  Apparently the insulation on the microphone wire gets worn through, causing the microphone to stop working.  If you look at the images in this thread of the 3810t taken apart, you can see the issue is likely that the microphone cable is draped over the sharp edges of the HD enclosure.  I can't say with 100% certainty because I haven't had it replaced yet, but my guess is that they move the wire so that it is not on that sharp edge.  I wish they would just send me the dang wire so i can do it myself.

Thanks for the answer. Now, how bad do you (or anybody else) think this issue is? Seemingly you haven't yet sent it because you really need your laptop, and I'm in the same situation. I just wonder how bad this really is. Since I don't intend to "apply extreme pressure to the lower left palmrest" or whatever the recall said, I wonder how big a risk I'm taking by not sending it back...

---

### Post by jimmy the saint on 2009-11-06
They said it is optional.  I think losing the microphone is the worst that is likely to happen, though I don't like the idea of freyed wires in my system causing havoc.  I am going to send it in for repair in December between semesters.

---

### Post by citizenofnowhere on 2009-11-08
About the jumpy touchpad issue on an earlier page:

do those who experience the jumpy cursor still have their Recovery partitions on their drives?

The reason I ask is when I removed mine last night (after a successful win7 install I figured I don't need it anymore now that I have CDs!) my cursor went all funny on Ubuntu. As well as on every live CD I tried. The moment I used Gparted to copy the partition back and rebooted, it started to work again.

Recommend to all to make backup of said partition before deleting - best was is to use the copy function in Gparted

EDIT: those having trouble with their jumpy cursors, please PM me your e-mail addresses. I don't want to further dilute this thread, but I have managed to fix a broken PQSERVICE earlier so I think I know how to fix the touchpad even if the partition had been deleted. I need someone to go through the instructions with me though so that I'm sure it works before I can post a definitive howto.

---

### Post by cnkk on 2009-11-08
damn its very disappointing that i cannot change my backlight ): i almost tried everything..but still its not changing. my fn keys work i see the display but theres no effect to my brightness. even if i change it manually by typing the value into the brightness file theres still no effect. I've got timeline 4810TG. used the lenovo hack to disable my ati graphix. using karmic full release 64bit (tried 32bit before but same problems). BIOS version 1.23
and theres another problem. my fan is workin almost the whole time. not at full power but i can hear it and its bothersome. typing "sensors" tells me a temperature of about 40°C.

---

### Post by miegiel on 2009-11-08
> **cnkk said:**
> damn its very disappointing that i cannot change my backlight ): i almost tried everything..but still its not changing. my fn keys work i see the display but theres no effect to my brightness. even if i change it manually by typing the value into the brightness file theres still no effect. I've got timeline 4810TG. used the lenovo hack to disable my ati graphix. using karmic full release 64bit (tried 32bit before but same problems). BIOS version 1.23
and theres another problem. my fan is workin almost the whole time. not at full power but i can hear it and its bothersome. typing "sensors" tells me a temperature of about 40°C.

I'd ask if there are any options to change it for a different model or if you can get a refund. The 4810TG seems most bugged of all the timelines (in ubuntu/linux at least). If you can change it for a different model, consider getting one without the ATI graphics.

> **citizenofnowhere said:**
> About the jumpy touchpad issue on an earlier page:

do those who experience the jumpy cursor still have their Recovery partitions on their drives?

The reason I ask is when I removed mine last night (after a successful win7 install I figured I don't need it anymore now that I have CDs!) my cursor went all funny on Ubuntu. As well as on every live CD I tried. The moment I used Gparted to copy the partition back and rebooted, it started to work again.

Recommend to all to make backup of said partition before deleting - best was is to use the copy function in Gparted

EDIT: those having trouble with their jumpy cursors, please PM me your e-mail addresses. I don't want to further dilute this thread, but I have managed to fix a broken PQSERVICE earlier so I think I know how to fix the touchpad even if the partition had been deleted. I need someone to go through the instructions with me though so that I'm sure it works before I can post a definitive howto.

I wrecked the restore partition the 3rd day I had my 3810T :lolflag:
I don't understand how a partition you don't use can influence your tochpad. Regardless, I use the red lines in my */etc/hal/fdi/policy/11-x11-synaptics.fdi* file below to stabilize my touchpad.

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
[COLOR="Blue"]<!-- external mouse
  <device>
    <match key="info.capabilities" contains="input.mouse">
       <merge key="input.x11_driver" type="string">mouse</merge>
      <match key="/org/freedesktop/Hal/devices/computer:system.kernel.name" string="Linux">
        <merge key="input.x11_driver" type="string">evdev</merge>
        <merge key="input.x11_options.Emulate3Buttons" type="string">false</merge>
        <merge key="input.x11_options.ButtonMapping" type="string">2 1 3</merge>
      </match>
    </match>
  </device>
-->[/COLOR]
  <device>
    [COLOR="SeaGreen"]<match key="info.capabilities" contains="input.touchpad">[/COLOR]
      <merge key="input.x11_driver" type="string">synaptics</merge>
[COLOR="Blue"]<!-- 
  DON'T USE SHMConfig (unless you must, for example to run 'synclient -m 10'), obsolete (karmic and later at least) and a security risk
      <merge key="input.x11_options.SHMConfig" type="string">On</merge> -->
<!-- 
  The following is an example of swapping buttons on the Synaptics TouchPad
  that DOESN'T WORK anymore. See the end of 'man synaptics'
      <merge key="input.x11_options.Buttons" type="string">3</merge>
      <merge key="input.x11_options.ButtonMapping" type="string">2 1 3</merge>
-->[/COLOR]
      <merge key="input.x11_options.TapButton1" type="string">2</merge>              [COLOR="Blue"]<!-- set tap-click to middle mouse button, run 'xinput set-button-map "SynPS/2 Synaptics TouchPad" 2 1 3' to swap buttons 1 and 2. This gives you middle click on the left button and left click on tap. -->[/COLOR]
      <merge key="input.x11_options.TapButton2" type="string">0</merge>              [COLOR="Blue"]<!-- disable 2 finger tap-click, 2 finger tap-click to menu = 3 -->[/COLOR]
      <merge key="input.x11_options.TapButton3" type="string">0</merge>              [COLOR="Blue"]<!-- disable 3 finger tap-click -->[/COLOR]
      <merge key="input.x11_options.RBCornerButton" type="string">0</merge>          [COLOR="Blue"]<!-- disable tap-right-bottom-corner button (is on by default on my machine) -->[/COLOR]
      <merge key="input.x11_options.VertEdgeScroll" type="string">0</merge>          [COLOR="Blue"]<!-- disable edge scrolling -->[/COLOR]
      <merge key="input.x11_options.EmulateMidButtonTime" type="string">0</merge>    [COLOR="Blue"]<!-- effectivelly disable middle button emmulation -->[/COLOR]
      <merge key="input.x11_options.EmulateTwoFingerMinZ" type="string">4</merge>    [COLOR="Blue"]<!-- set 2 finger emulation presure -->[/COLOR]
      <merge key="input.x11_options.EmulateTwoFingerMinW" type="string">7</merge>    [COLOR="Blue"]<!-- set 2 finger emulation pinch width -->[/COLOR]
      <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>     [COLOR="Blue"]<!-- enable 2 finger scrolling -->[/COLOR]
      [COLOR="Red"]<merge key="input.x11_options.JumpyCursorThreshold" type="string">150</merge>[/COLOR]  [COLOR="Blue"]<!-- stabilize 2 finger tapping and 2 finger scrolling -->[/COLOR]
      [COLOR="Red"]<merge key="input.x11_options.MaxDoubleTapTime" type="string">50</merge>[/COLOR]
    </match>
  </device>
</deviceinfo>
```
Some notes:
[LIST]
[*] Merges are only applied for the devices where the [COLOR="SeaGreen"]green line[/COLOR] is true.
[*]Stuff between [COLOR="Blue"]<!--[/COLOR] and [COLOR="Blue"]-->[/COLOR] are notes (like after a # in other types of files).
[*]*/etc/hal/fdi/policy/preferences.fdi* or */etc/hal/fdi/policy/any.other.name.fdi* will all work. All the *.fdi* files are run regardless of their name. You can merge all the *.fdi* files into 1 or split them for different devices.
[*]I don't have or use */etc/X11/xorg.conf* anymore.
[/LIST]

---

### Post by cnkk on 2009-11-08
> **miegiel said:**
> I'd ask if there are any options to change it for a different model or if you can get a refund. The 4810TG seems most bugged of all the timelines (in ubuntu/linux at least). If you can change it for a different model, consider getting one without the ATI graphics.


no :/
my old asus' motherboard burned up and as a refund they gave me 600euro to buy a new in the same store..well i put some money to it and i bought the timeline..it was the best choice there. but i didn know that theres so less compability with ubuntu :/ so I've to deal with that or try to solve the problems somehow..
in windows i can reach a batterie life of bout 7h..in ubuntu i reach with disabled ati card (lenovo hack) and powertop mode bout 5h.. but it would be nice if i could adjust my brightness to the lowest level :/
sure that nobody can help me out of that pity?

---

### Post by Arlanthir on 2009-11-08
> **cnkk said:**
> no :/
my old asus' motherboard burned up and as a refund they gave me 600euro to buy a new in the same store..well i put some money to it and i bought the timeline..it was the best choice there. but i didn know that theres so less compability with ubuntu :/ so I've to deal with that or try to solve the problems somehow..
in windows i can reach a batterie life of bout 7h..in ubuntu i reach with disabled ati card (lenovo hack) and powertop mode bout 5h.. but it would be nice if i could adjust my brightness to the lowest level :/
sure that nobody can help me out of that pity?

What exactly have you tried so far?

---

### Post by cnkk on 2009-11-09
smartdimmer..
xbacklight -set ..
[http://ubuntuforums.org/showthread.php?t=767374](http://ubuntuforums.org/showthread.php?t=767374)    (this i tried)
editing the brightness file in /proc/acpi/video/VGA/LCD/brightness (i cannot change it manually. it doesnt accept the change) but i noticed that i can change this value by using the fn keys.. (which has no effect to my brightness)
well and some more but forget the commands :S

I also cannot use my cdrom :/ i wrote the following in my fstab but its still not working..:
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd2       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd3       /media/cdrom3   udf,iso9660 user,noauto,exec,utf8 0       0

no mounting point of the above ones exists :/ what am i doin wrong?

---

### Post by Burkhard on 2009-11-09
Did you make any progress regarding the fan noise? I got a 3810TG and the fan is running all of the time and it's driving me mad. It's much more quiet, acceptable quiet, when running on batteries, but with the AC plugged in it's unbearably noisy. This is with a 1.14 BIOS and ATI proprietary drivers. But at least on Windows whether ATI or Intel card doesn't matter for the fan at all. The cpu termperature is always below 40 degrees celcius, the power consumption is between 12 and 15 Watts.

---

### Post by Arlanthir on 2009-11-09
> **cnkk said:**
> smartdimmer..
xbacklight -set ..
[http://ubuntuforums.org/showthread.php?t=767374](http://ubuntuforums.org/showthread.php?t=767374)    (this i tried)
editing the brightness file in /proc/acpi/video/VGA/LCD/brightness (i cannot change it manually. it doesnt accept the change) but i noticed that i can change this value by using the fn keys.. (which has no effect to my brightness)
well and some more but forget the commands :S

I also cannot use my cdrom :/ i wrote the following in my fstab but its still not working..:
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd2       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd3       /media/cdrom3   udf,iso9660 user,noauto,exec,utf8 0       0

no mounting point of the above ones exists :/ what am i doin wrong?

Add the following to the GRUB_CMD_LINUX_DEFAULT entry in /etc/default/grub: 
nomodeset acpi_backlight=vendor

Example:```
(...)
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_backlight=vendor"
GRUB_CMDLINE_LINUX=""
(...)
```

and then run ```
sudo update-grub
``` on the terminal.

This works for me, and nothing did before it too ;)

For the cdrom, each time you want to open the tray run this (alt+f2 or in the terminal) instead: ```
eject cdrom
```
Make sure you haven't pressed the eject key since you rebooted before attempting this, otherwise it won't do anything.

---

### Post by miegiel on 2009-11-09
> **Burkhard said:**
> Did you make any progress regarding the fan noise? I got a 3810TG and the fan is running all of the time and it's driving me mad. It's much more quiet, acceptable quiet, when running on batteries, but with the AC plugged in it's unbearably noisy. This is with a 1.14 BIOS and ATI proprietary drivers. But at least on Windows whether ATI or Intel card doesn't matter for the fan at all. The cpu termperature is always below 40 degrees celcius, the power consumption is between 12 and 15 Watts.

Did you check the CPU temperature?

---

### Post by jimmy the saint on 2009-11-09
Just wanted to update on the issues I was having with the jumpy mouse and battery life.

After running an actual installation (Rather than the usb installation created with the USB creator tool) the mouse fixed itself after the first round of updates.  Not sure what did it, but I'm not complaining.  Now it is great and I just need to tweak it to enable multitouch emulation.

Still haven't got the mic to work, and not really worth troubleshooting for me.  I can live without it.

Suspend is still broken, but it seems to be a BIOS issue, so I will harass Acer rather than the Ubuntu team.

Battery life is much better than it was running from the USB stick for some reaason as well.

All in all, I think that Karmic is a good release, though not one of the best. It feels like there was a bunch of new technologies thrown in and some bugs need to be ironed out for the next LTS.

---

### Post by h0bbe on 2009-11-10
> **Dan48p said:**
> Hey guys, i just installed 9.10 upgrade option on my laptop.  I wanted to note here that all of my external displays are working perfectly.

With both 9.04 and win7 i was unable to get these displays 1440x900 and 1680x1050 to function at native resolution.  I used these displays one at a time not all at the same time.

9.10 immediately recognizes the displays and lets me add them in the "displays" option.
I wish I was as lucky as you... On my 1810TZ I can't get mirroring working. Sorry for [double posting]("http://ubuntuforums.org/showpost.php?p=8279710&postcount=2") but maybe one of you in this thread been through the same problem:> Why isn't it possible to mirror two screens (in my case the one on my Acer Aspire Timeline 1810TZ and my external 24" BenQ widescreen) with two individual resolutions? Please help!

---

### Post by cnkk on 2009-11-10
> **Arlanthir said:**
> Add the following to the GRUB_CMD_LINUX_DEFAULT entry in /etc/default/grub: 
nomodeset acpi_backlight=vendor

Example:```
(...)
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=&quot;10&quot;
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=&quot;quiet splash nomodeset acpi_backlight=vendor&quot;
GRUB_CMDLINE_LINUX=&quot;&quot;
(...)
```and then run ```
sudo update-grub
``` on the terminal.

This works for me, and nothing did before it too ;)

For the cdrom, each time you want to open the tray run this (alt+f2 or in the terminal) instead: ```
eject cdrom
```Make sure you haven't pressed the eject key since you rebooted before attempting this, otherwise it won't do anything.

 yayyyy thanks alot.. nomodeset acpi_backlight=vendor worked for me i can change my backlight now :D i either can turn it fully off damn im so happy right now :D thanks alot could you mayb explain what exactly the commands do? would be very nice.  and about the cdrom.. well my eject button on the hardware also opens the cdrom but the problem is it doesnt mount the cd/dvd

---

### Post by Arlanthir on 2009-11-10
> **cnkk said:**
> yayyyy thanks alot.. nomodeset acpi_backlight=vendor worked for me i can change my backlight now :D i either can turn it fully off damn im so happy right now :D thanks alot could you mayb explain what exactly the commands do? would be very nice.  and about the cdrom.. well my eject button on the hardware also opens the cdrom but the problem is it doesnt mount the cd/dvd

From looking around:

```
acpi_backlight=	[HW,ACPI]
		acpi_backlight=vendor
		acpi_backlight=video
		If set to vendor, prefer vendor specific driver
		(e.g. thinkpad_acpi, sony_acpi, etc.) instead
		of the ACPI video.ko driver.
```

This is needed to set the backlight driver to the vendor's one, as the default doesn't work correctly. Nomodeset turns off KMS for the driver to work, because it doesn't seem to do anything otherwise :S In practice you lose a bit of the WOW during boot.

I understand the eject button opens the tray, but it also wrongly tells Ubuntu that the cdrom drive has been unplugged (or so I think), because mounting never works after that. Instead, if you just use the command 'eject cdrom', it will mount the CD automatically when you close the tray :)

Sorry if I can't be more specific, I just found those commands here in the forums too ;)

---

### Post by cnkk on 2009-11-10
you were specific enough believe me I'm so glad that you did a post. finally i can change my backlight and youre right! when i type eject cdrom and put a cdrom into and close it, it mounts the cdrom! and again you did help me :D thats perfect..theres only the question if i could bind "eject cdrom" command to the eject key from the hardware.. (:

---

### Post by Arlanthir on 2009-11-10
> **cnkk said:**
> you were specific enough believe me I'm so glad that you did a post. finally i can change my backlight and youre right! when i type eject cdrom and put a cdrom into and close it, it mounts the cdrom! and again you did help me :D thats perfect..theres only the question if i could bind "eject cdrom" command to the eject key from the hardware.. (:

That would be nice but I don't know how to do it :P
Glad I could help :)

---

### Post by miegiel on 2009-11-10
> **cnkk said:**
> you were specific enough believe me I'm so glad that you did a post. finally i can change my backlight and youre right! when i type eject cdrom and put a cdrom into and close it, it mounts the cdrom! and again you did help me :D thats perfect..theres only the question if i could bind "eject cdrom" command to the eject key from the hardware.. (:

A keyboard shortcut like *Crtl+Alt+E* should be a lot easier.

---

### Post by cnkk on 2009-11-10
i assigned under system->keycombinations ctrl+alt+A to eject. if i use this shortcut i see the eject display above but theres no reaction to my cdrom :S

---

### Post by cnkk on 2009-11-11
ok i did a reboot and it works now for me (:

---

### Post by james rose on 2009-11-15
Hey, I need the atheros driver but the site is down, I don't suppose anyone could send it to me please?

---

### Post by miegiel on 2009-11-15
> **james rose said:**
> Hey, I need the atheros driver but the site is down, I don't suppose anyone could send it to me please?

No, sorry (in karmic you don't need to get the driver from atheros anymore).

---

### Post by miegiel on 2009-11-18
New BIOS (v1.15) available for 3810T and other models. No release notes :( Haven't tried it yet, just thought people might like to know.

---

### Post by cyberfish on 2009-11-18
> **miegiel said:**
> New BIOS (v1.15) available for 3810T and other models. No release notes :( Haven't tried it yet, just thought people might like to know.

Thanks! will try it tonight and report back, if no one beats me to it.

---

### Post by cyberfish on 2009-11-18
Gah, won't let me flash when running on battery, even though I have 6 hrs of battery left. Guess I have to really wait till tonight, then.

---

### Post by doktoreas on 2009-11-18
> **cyberfish said:**
> Gah, won't let me flash when running on battery, even though I have 6 hrs of battery left. Guess I have to really wait till tonight, then.

Sorry mate, how long does the battery last (using wifi and surfing on the net)?

Thank you
Luca

---

### Post by cyberfish on 2009-11-18
~8 hrs under Linux, 10 hrs under Windows.

I have the SSD version of 3810t, which appears to last a little bit longer.

---

### Post by almozavr on 2009-11-18
Installed new BIOS v 1.15 but still can't resume after suspend :(

I want to see list of changes!

---

### Post by cyberfish on 2009-11-19
ah, that's no good :(.

---

### Post by cyberfish on 2009-11-19
Tried 1.15, computer froze twice already. Flashed back to 1.10.

Not sure if it's directly related to the new BIOS, but think twice before flashing if your machine is important.

---

### Post by mr bob on 2009-11-19
To be more accurate it is a Linux-bios combination problem, since suspend-resume works fine in Windows, with the current bios.

Just out of interest, are there any kernel experts here that could say if the problem is either:

1) It is impossible to get the Linux kernel working with the current 3810T bios (1.10) because suspend-resume works fundamentally differently to how it works in Windows.

or

2) It is in theory possible to get suspend-resume working with the current bios but without access to the proprietary Windows suspend-resume code it is like looking for a needle in a haystack.

cheers. :)

---

### Post by miegiel on 2009-11-19
> **cyberfish said:**
> Tried 1.15, computer froze twice already. Flashed back to 1.10.

Not sure if it's directly related to the new BIOS, but think twice before flashing if your machine is important.
Thanks for the warning.

---

### Post by deconstructingme on 2009-11-20
I see that Acer has posted version 1.17 of the 3810 BIOS. Has anyone tested it? Does it solve any problems?

---

### Post by megaexception on 2009-11-20
can someone check if virtualization support was added in bios 1.15 or 1.17?
or may be some of acpi problems (suspend) fixed?

---

### Post by mr bob on 2009-11-20
Flashed v1.17 on my 3410 this evening and it doesn't fix suspend on my laptop unfortunately.

Sorry I don't know how to check for virtualization but the F2 BIOS screen looks the same.

---

### Post by miegiel on 2009-11-20
> **mr bob said:**
> Sorry I don't know how to check for virtualization but the F2 BIOS screen looks the same.

[S]While booting I get a warning (3810T BIOS 1.10) that the KVM module can't be loaded because it's disabled by the BIOS (or something like that). KVM stands for Kernel Virtual Machine. But you only get the warning if you disable the boot splash.[/S]

**note:** [COLOR="Red"]I haven't had the boot splash disabled for some time,[/COLOR][S] so I'm as[/S][COLOR="Red"]sum[/COLOR][S]ing no[/S][COLOR="Red"]thing has changed : )[/COLOR]

[COLOR="Silver"]**edit:** To disable the boot splash change the *GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"* line in */etc/default/grub* to *GRUB_CMDLINE_LINUX_DEFAULT=""* and run *update-grub* to commit the change (for grub2 in karmic).[/COLOR]

---

### Post by mr bob on 2009-11-20
I disabled the splash and I didn't notice any warnings about KVM.

I also tried sudo modprobe kvm and there were no warnings. So I hope that helps.

---

### Post by miegiel on 2009-11-20
> **mr bob said:**
> I disabled the splash and I didn't notice any warnings about KVM.

I also tried sudo modprobe kvm and there were no warnings. So I hope that helps.

No :D just booted with the 1.10 BIOS and splash disabled and I don't get the warnings either anymore.

---

### Post by lemurian on 2009-11-21
I've been thinking for a while that the solution to this problem is not to try to hack the kernel or the BIOS but to complain loudly.  The fact of the matter for me right now is this:

1. The 3810T is *great* except for the stupid suspend issue.

2. I can understand that there may be a *little* lag between the release of a machine and having full functionality in Linux.

3. However, complete disregard of the Linux market is simply unacceptable.  There are no excuses.

Hence the 3810T will be both the first and the last Acer I ever buy.  I've bought Dells and Sagers in the past and except for a temporary (and short) lack of full functionality initially (see point 2 above), the Dells and the Sagers quickly became fully operational in under Linux, either because the manufacturers cooperated or because they followed standards.

Regarding point 3 above, I'm ready to bet that there is an manager at Acer who made the calculation that ignoring the Linux market is financially better for Acer because they save on support but still sell machines.  They are hoping that Linux users will just accept it.  That person has to learn that ignoring the Linux market means lost sales.

---

### Post by pfem on 2009-11-21
If anyone has the time, knowledge and patience to write a letter to ACER I'll be happy to send it too.

---

### Post by lemurian on 2009-11-21
I've complained to Acer USA support today.  I'm expecting that the answer I get will be unsatisfactory.  At least, I'll be able to say I've been through normal channels before trying to get the attention of somebody at a higher level.

A couple years ago, I had a problem with eBags.  Their customer service representatives were refusing me a discount on the basis of an illogical argument.  (This is what happens when the people on the front line are trained to read from a script: they don't realize or don't care that their replies make no logical sense.)  I contacted the CEO directly by email and he replied very quickly and very apologetically.  I got a phone call from their VP of marketing the day after.  I stated my facts clearly and politely.  It worked.

---

### Post by molder on 2009-11-22
I have the Acer Timeline 3810TZ.  Suspend and Hibernate don't work, but that is not a big deal for me.  What really bugs me is the inability of the wireless to stay connected to my AP.  Slow transfer speeds and what not.  I saw someone made a post about this issue but didn't see any follow up.  

Karmic Using 2.6.31-14-generic-pae kernel.

What Works:
lan
sound
GM4500M
Battery life good
Touchpad on/off

Busted:
Wireless

---

### Post by muadnu on 2009-11-22
> **almozavr said:**
> MIC problem is SOLVED

Yes, new alsa supports Acer 3810T audio system (Intel 45 mobile chipset). But I didn't succeeded in manual installation. So I used great script for Auto Update (it also installed ~260 MB of dependencies, be patient).

----------------------------------------------------

You can find ALSA Upgrade Script [here]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810") ;)

This worked for me, at least I can now record using gnome-sound-recorder. But skype isn't working, I get no input at all... Has anyone got it to work? Maybe I'm missing something.

---

### Post by Arlanthir on 2009-11-22
> **molder said:**
> I have the Acer Timeline 3810TZ.  Suspend and Hibernate don't work, but that is not a big deal for me.  What really bugs me is the inability of the wireless to stay connected to my AP.  Slow transfer speeds and what not.  I saw someone made a post about this issue but didn't see any follow up.  

Karmic Using 2.6.31-14-generic-pae kernel.

What Works:
lan
sound
GM4500M
Battery life good
Touchpad on/off

Busted:
Wireless

Have you tried installing linux-backports-modules-karmic-generic ?
It fixes the wlan power managing, might fix your problems too.

---

### Post by citizenofnowhere on 2009-11-22
> **molder said:**
> What really bugs me is the inability of the wireless to stay connected to my AP.  Slow transfer speeds and what not.  ...
Busted:
Wireless

molder: are you using Ubuntu or Kubuntu, some other derivative? I have run across that issue before with the GNOME network manager but never with WICD on my KDE. I suggest you give WICD a try, as at least in my case it wasn't hardware related rather the inability of the Gnome network manager to reconnect after my wireless went into power saving mode.

---

### Post by Friqenstein on 2009-11-25
Hello again all,

Well, I've not been to this thread in a few weeks now because I've been overtly occupied doing other shtuff... I come back to find it already up to page 52. Wow. Nice to know that ACER doesn't really care about their products.

I personally think it's high time that we setup a petition and send it to ACER to show them just exactly what is wrong with their "technology" and how large the community is that uses this particular machine with an OS other than the Slave grinders try to force you to use (MS).

Anybody up for a petition?

I can say this, as someone else posted a few posts above, I'll never buy another ACER EVER again. I usually replace my laptop once every 1 to 1.5 years and I'll be damned if I'm going to ever buy a unit from ACER ever again.

It's really sad that our community is more proactive in solving issues that ACER will ever be. Typical. Too bad ACER didn't go by way of GM!

Petition!

---

### Post by almozavr on 2009-11-25
> **muadnu said:**
> This worked for me, at least I can now record using gnome-sound-recorder. But skype isn't working, I get no input at all... Has anyone got it to work? Maybe I'm missing something.

The problem is Skype uses Pulseaudio instead of ALSA system if at the time of Skype start Pulseaudio is working. Here is some [explanations]("http://share.skype.com/sites/linux/2009/09/some_explanations.html")

So, you should kill Pulseaudio process each time you start Skype and Skype will use ALSA. This worked for me.

I'd rather remove Pulseaudio system but honestly I don't know how - Dependencies...

---

### Post by muadnu on 2009-11-25
Thanks, I'll try killing pulseaudio...

On a different matter, does anyone have a copy of the atheros driver? The link doesn't work anymore, and I need it (I know I don't in karmic, but I wan't to try something in jaunty).

---

### Post by almozavr on 2009-11-25
New BIOS v 1.17 is out!!! Let's try it ;)

---

### Post by JimHQ on 2009-11-25
I seem to be having the same issue as Molder - wireless becomes slow then drops out and will not reconnect. Rebooting gets it going again. 
dmesg shows a few of the following
[  406.804924] wlan0: deauthenticated from 00:18:39:a8:af:33 (Reason: 6)
[  408.587525] wlan0: deauthenticating from 00:18:39:a8:af:33 by local choice (reason=3)

Any idea what is going on? 

Jim.

---

### Post by tomfool on 2009-11-25
Hi to everyone!
Well,i activeted the wifi power-saving mode and i was wonndering if it needs to be activeted every time i re-start my system or just onece?
I bag your pardon for my english,i'm italian!;)

---

### Post by csipuka on 2009-11-25
> **muadnu said:**
> This worked for me, at least I can now record using gnome-sound-recorder. But skype isn't working, I get no input at all... Has anyone got it to work? Maybe I'm missing something.
Hi,

I have found a solution here:
[http://ubuntuforums.org/showthread.php?t=1308090&page=2](http://ubuntuforums.org/showthread.php?t=1308090&page=2)
[I]Open alsamixer and change the mic volume (CAPTURE). The left side to 0 and the right to 100.
Open alsamixer, push F6 to choose the Audio card. Push F5 (All). Move with arrow keys on CAPTURE.
Push Z to decrease the left column and E to raise the right one.
Now start skype and it should work. I think it should work also in the D250.[/I]

It works on my 4810TG. I do not understand why, but works :)
Csipu

---

### Post by iceman on 2009-11-26
Amazing! I don't know why, but it works on 3810T too (Mint 8 aka Ubuntu 9.10 with latest linux-backports-modules-alsa-karmic-generic)
Kind regards.

P.s. I updated bios to 1.17 and suspend does not still works

---

### Post by jpgv on 2009-11-26
Can also confirm this works to solve the skype mic issue. No idea why, but it does work, no need to kill pulseaudio.

---

### Post by csipuka on 2009-11-26
> **iceman said:**
> Amazing! I don't know why, but it works on 3810T too (Mint 8 aka Ubuntu 9.10 with latest linux-backports-modules-alsa-karmic-generic)
Kind regards.

P.s. I updated bios to 1.17 and suspend does not still works

I am glad to hear it.
Back to the suspend. Mine fixed when the swap switched on.
Currently I have only 1 issue, I cannot write any CD. :(

---

### Post by iceman on 2009-11-26
I suppose you are not talking about suspend to ram... you are talking about suspend to disk (hibernate)
It's not the same thing, believe me...

---

### Post by csipuka on 2009-11-26
> **iceman said:**
> I suppose you are not talking about suspend to ram... you are talking about suspend to disk (hibernate)
It's not the same thing, believe me...

Well, mainly correct :)
I had problem with the hibernate. True.
The swap fixed the hibernate, and now I have tried the suspend. 
It works perfectly, but I do not know whether the swap is the solution or not.

---

### Post by iceman on 2009-11-26
I can't believe the problem (and the solution!) is the swap partition...

Anyway, how many time spend to resume from suspend to ram?

---

### Post by csipuka on 2009-11-27
> **iceman said:**
> I can't believe the problem (and the solution!) is the swap partition...

Anyway, how many time spend to resume from suspend to ram?

Just 2-3sec. If you can see the cursor of the mouse on the blank screen, the system is ready. Memory consumption ~300mb.
I have left the my laptop in suspend for 6hours, and it decreased the battery from 97%->91%. 1hour takes ~1%. Nice.
Probably I will use it more frequently...

---

### Post by iceman on 2009-11-27
Can you confirm you have exactly 3810T?
Please, post:

- Ubuntu version
- Bios version
- Kernel version
- Swap partition size

Thank you

---

### Post by iceman on 2009-11-27
Anyway, i did my test: with the latest 1.17 bios and Mint 8 (Ubuntu Karmic), with kernel 2.6.32-020632rc8-generic (latest) or 2.6.31-15-generic (karmic default) and 8gb swap partition, i still can't suspend S3.

The strange thing is why the entire 3810T community can't sleep S3 but you are able to?
I don't want to tell you, i don't believe you, but please explain how do you get the solution...

---

### Post by iceman on 2009-11-27
And i add: S4 is working properly... Hibernation has no problem in 3810T (with phisical swap partition enabled)

No way to get S3 to work. Harddisk just click on resume e suddenly shutdown laptop (even in AHCI/IDE mode and both kernel mixed configuration)

---

### Post by jimmy the saint on 2009-11-27
> **iceman said:**
> Can you confirm you have exactly 3810T?
Please, post:

- Ubuntu version
- Bios version
- Kernel version
- Swap partition size

Thank you

He already indicated that he has a 4810, not a 3810 when he detailed the fix for the skype/mic issue.

---

### Post by iceman on 2009-11-27
Ops... I started reading him, after his first reply to my post... :D

OK, nothing changes... we are in deep fog again... :(

---

### Post by csipuka on 2009-11-28
> **iceman said:**
> Ops... I started reading him, after his first reply to my post... :D

OK, nothing changes... we are in deep fog again... :(

I have a 4810 with the latest official kernel: 2.6.31-15.
I do not know the swapsize by heart (I do not use my laptop on daily basis), but usually I set it a bit larger than the physical memory.

---

### Post by caelestis2 on 2009-11-29
I ordered a 3810tz and will be joining the community as soon as I receive it. Just a few questions:

[LIST=1]
[*]How fast does it hibernate, and return from it?
[*]Supposedly, the machine doesn't come with recovery or windows cd's so you have to make them yourself, but there isn't an optical drive on this, do I have to use a network drive or external? Maybe burn them to an iso?
[*]How would you set up the partitions? Windows 7 would take up two partitions, and Windows 7 wants to be at the beginning of the drive usually, and for linux, I would need two partitions, one for the filesystem, and one for swap. So where does that leave the recovery partition if the drive has the max of four partitions? I don't really want to keep the recovery partition anyway though, is it necessary?
[*]Is battery life better when using 'g' instead of 'n' wireless?
[*]Why does linux consume more Watts on the processor than Windows? That seems rather absurd.
[*]Should I update to the latest BIOS? I'm worried that someone said there are a few problems with it.
[/LIST]

I'm doubting whether I should install linux as I bought the machine for it's battery life. To see people saying that there is a battery life difference between windows and linux is a bit disappointing, but I will give it a nice long shot before I give up.

Edit: Oh, and I would like to share this link if you haven't seen it yet: [http://forum.notebookreview.com/showthread.php?t=427347](http://forum.notebookreview.com/showthread.php?t=427347)

---

### Post by Arlanthir on 2009-11-30
> **caelestis2 said:**
> I ordered a 3810tz and will be joining the community as soon as I receive it. Just a few questions:

[LIST=1]
[*]How fast does it hibernate, and return from it?
[*]Supposedly, the machine doesn't come with recovery or windows cd's so you have to make them yourself, but there isn't an optical drive on this, do I have to use a network drive or external? Maybe burn them to an iso?
[*]How would you set up the partitions? Windows 7 would take up two partitions, and Windows 7 wants to be at the beginning of the drive usually, and for linux, I would need two partitions, one for the filesystem, and one for swap. So where does that leave the recovery partition if the drive has the max of four partitions? I don't really want to keep the recovery partition anyway though, is it necessary?
[*]Is battery life better when using 'g' instead of 'n' wireless?
[*]Why does linux consume more Watts on the processor than Windows? That seems rather absurd.
[*]Should I update to the latest BIOS? I'm worried that someone said there are a few problems with it.
[/LIST]

I'm doubting whether I should install linux as I bought the machine for it's battery life. To see people saying that there is a battery life difference between windows and linux is a bit disappointing, but I will give it a nice long shot before I give up.

Edit: Oh, and I would like to share this link if you haven't seen it yet: [http://forum.notebookreview.com/showthread.php?t=427347](http://forum.notebookreview.com/showthread.php?t=427347)

I have the 4810T and I can assure you battery life is pretty good on Ubuntu (around 5-6 hours with everything on, wireless, bluetooth, desktop effects, etc). Instead of turning features off, I run a small script to enter powersave mode where applicable (wlan, SATA management policy, screen brightness, CPU frequency, everything powertop says). The 3810T should be similar.

I had trouble with the BIOS on my previous 4810T, I bricked it downgrading on Windows, so be careful. People generally suggest making a DOS bootable usb thumbdrive (I didn't know that).

I kept the recovery partition so I have Windows 7, Ubuntu+Swap, Recovery. That's 4, and the limit, but you can always configure extended Partitions, I think Ubuntu does that automatically with Swap.

---

### Post by iceman on 2009-11-30
1° 15 seconds to hibernate, 45 seconds to resume
2° I made it by alchool 100%. Anyway, i had an external dvd-r which i used to make 2 dvds.
3° Windows 7 does not need 2 partitions. I installed on first partition Win7 (after backup Vista), on second Snow Leopard 10.6.2 and in the third (250gb) Linux Mint 8 (i have a fourth with 8gb swap, that from today is a new Moblin Intel Linux distro.. try it.. it's amazing!!).
4° n? I don't know it was an n!! :D Anyway, i used the second mini pci-e and put a Broadcom 4311 "g" because i needed "airport" wireless on Snow Leopard
5° On Ubuntu 9.10 things are little better. I don't know exactly why is so resource-hungry
6° I updated bios to the latest. For me, there was no differences from 1.10 to the latest 1.17

---

### Post by Arlanthir on 2009-11-30
> **iceman said:**
> 1° 15 seconds to hibernate, 45 seconds to resume
2° I made it by alchool 100%. Anyway, i had an external dvd-r which i used to make 2 dvds.
3° Windows 7 does not need 2 partitions. I installed on first partition Win7 (after backup Vista), on second Snow Leopard 10.6.2 and in the third (250gb) Linux Mint 8 (i have a fourth with 8gb swap, that from today is a new Moblin Intel Linux distro.. try it.. it's amazing!!).
4° n? I don't know it was an n!! :D Anyway, i used the second mini pci-e and put a Broadcom 4311 "g" because i needed "airport" wireless on Snow Leopard
5° On Ubuntu 9.10 things are little better. I don't know exactly why is so resource-hungry
6° I updated bios to the latest. For me, there was no differences from 1.10 to the latest 1.17

A little bit offtopic but just out of curiosity, how would I install MacOSX on this baby? :P
Does everything work?

---

### Post by caelestis2 on 2009-11-30
> **iceman said:**
> 1° 15 seconds to hibernate, 45 seconds to resume
2° I made it by alchool 100%. Anyway, i had an external dvd-r which i used to make 2 dvds.
3° Windows 7 does not need 2 partitions. I installed on first partition Win7 (after backup Vista), on second Snow Leopard 10.6.2 and in the third (250gb) Linux Mint 8 (i have a fourth with 8gb swap, that from today is a new Moblin Intel Linux distro.. try it.. it's amazing!!).


I found out that ultimate wants two partitions: ```
http://www.mydigitallife.info/2009/08/20/hack-to-remove-100-mb-system-reserved-partition-when-installing-windows-7/
```
Doesn't matter since I won't be using RC anymore.

45 second resume sucks, seems I will be just shutting it on and off. Hope suspend to ram gets fixed soon.

Can anyone else comment on battery life of linux vs windows 7/vista if you have both OS's on similar settings?

---

### Post by iceman on 2009-11-30
Works everything about QE/CI acceleration (resolution 1366x768 OK) and wireless (this is why i put broadcom 4311).
How did i install it? Original Snow Leopard DVD and iDeneb 1.5.6 from external usb drive. In iDeneb i started OSInstall.mpkg (MBR patched version) of a restored SL DVD on a partition. Install everything in target partition on local disk on 3810T. After that, i installed Chameleon 2. Reboot and played with kext (IOATAFamily, CPUPowerManager etc...)
Go to insanelymac forums and "search me" on italian forum (where i made a small italian guide you can translate by google ;-) )

---

### Post by iceman on 2009-11-30
> **caelestis2 said:**
> I found out that ultimate wants two partitions: ```
http://www.mydigitallife.info/2009/08/20/hack-to-remove-100-mb-system-reserved-partition-when-installing-windows-7/
```
Doesn't matter since I won't be using RC anymore.

45 second resume sucks, seems I will be just shutting it on and off. Hope suspend to ram gets fixed soon.

Can anyone else comment on battery life of linux vs windows 7/vista if you have both OS's on similar settings?
Obsolutely not. I installed Win7 Ultimate 64bit in only one partition.

---

### Post by Literati on 2009-12-01
Hi guys, I can't even seem to get my Timeline 3810TZ to boot from the USB image.

I copied the image to my usb using dd if=/path/ of=/dev/sde bs=4096

But it just hangs at the BIOS screen, flashing my USB activity light for hours on end (I left it on for well over an hour to see if it'd do something). 

Has anyone else had this issue? How did you fix it?

I tried Moblin too, and I can't boot that. Nor OpenSUSE... :(

---

### Post by iceman on 2009-12-01
I tried Moblin and it works very well on 3810T (you can see an italian guide on [my site](http://www.htpcpoint.it). In the same guide, i explain how to boot in vmware too).
i had the same problem on usb boot... but at the end i found the problem was my usb pen (or the dd to /dev/sdX that for some reason does not works well...)
I copied LiveOS and isolinux folders to another usb pen i have and edited grub to boot Moblin. It worked perfect.

---

### Post by Literati on 2009-12-01
Really? I bought this USB Stick specifically for the purpose, it'd suck if it didn't work since I don't have another lying around... :( 

I guess I'll try a few more things. I'm reading about syslinux and making my USB Stick bootable and such, but no luck so far. :(

---

### Post by iceman on 2009-12-01
Try with grub first... extract content to USB Root and install grub.

---

### Post by Literati on 2009-12-01
> **iceman said:**
> Try with grub first... extract content to USB Root and install grub.

I don't understand. Let's say I'm starting with a clean USB Stick. What should I do?

My Timeline doesn't seem to like booting iso9667 formatted USB Sticks. This is where it always hangs on the BIOS Screen.

---

### Post by dafeder on 2009-12-02
Has anyone received a response from Acer on the suspend issue?

---

### Post by lemurian on 2009-12-02
> **dafeder said:**
> Has anyone received a response from Acer on the suspend issue?

I contacted customer support a while back, I did not even get a response.  I've been busy with other things so I have not yet brought this up to the next level.  The next step as I see it is to find the contact information of someone higher up and explain plainly and politely to them that this situation is unacceptable and will result in them losing sales.  As it stands right now, I cannot in good conscience recommend Acer to anyone.  I can only recommend on the basis of my experience and my experience with Acer right now is not good.

---

### Post by acermobile on 2009-12-02
Hi everyone.

I have managed to get almost everything working on Karmic 9.10. For various reasons I stick to the discrete graphics card. However, this hinders hibernate (at least for me and I wasted DAYS trying to get it working). But since the bootup time is ridiculously short (something around 20 sec.) I don't really care.

One thing is, however, really freaking me out. Does the Intel SU4100 (2x 1.3 GHZ) cpu really only provide the two acpi modes listed (1200 and 1300 Mhz)? After googling for a while and browsing the mediocre intel website I found no additional information about the cpu and the available frequencies. To be honest I cannot imagine that 1200 is the lowest available frequency and I do suppose that a reduction to, e.g., 600 will result in massive increase in the battery power.

Any thoughts?

Felix


BTW: I can't wait the suspend issue to get solved...

---

### Post by iceman on 2009-12-02
Let's suppose your pendrive is /dev/sdb

Create a single partition on it (with gparted/fdisk/cfdisk... anything you want)
Format it (mkfs.ext3 /dev/sdb1)
Mount moblin image to a temporary folder (mkdir moblin; sudo mount -o loop moblin-2.1-final-20091103-002.img moblin/)
Mount partition to a temporary folder (mkdir pendrive; sudo mount /dev/sdb1 pendrive/)
Copy content of moblin into pendrive (sudo cp -rp moblin/* pendrive/)
If you are using Ubuntu like distro, copy your /boot folder into pendrive (sudo cp -rp /boot pendrive/)
Delete and recreate menu.lst (sudo rm pendrive/boot/grub/menu.lst; sudo touch pendrive/boot/grub/menu.lst)
Edit this file and put this:

> default 0
timeout 15


title Moblin 2.1
	kernel /isolinux/vmlinuz0 initrd=/isolinux/initrd0.img root=/dev/sda1 ro liveimg
	initrd /isolinux/initrd0.img

title Moblin 2.1 Installation
	kernel /isolinux/vmlinuz0 initrd=/isolinux/initrd0.img root=/dev/sda1 ro liveimgliveinst nosplash 4
	initrd /isolinux/initrd0.img


You can do it by "sudo nano pendrive/boot/grub/menu.lst" or "sudo vi pendrive/boot/grub/menu.lst". Choose what you prefer (nano is easier)

Unmount temporary folders (sudo umount pendrive/ moblin/)
Now, the most important thing: install grub.
Launch "grub"
After that, type:

root (hd1,0)
setup (hd1,0)
setup (hd1)
quit (or exit... i don't remember! :D)

In this way you will install bootloader in MBR and in the partition (just to be sure)
I wrote hd1 because i suppose your pendrive is /dev/sdb. If your pendrive is /dev/sda you have to change all occurences (of this guide) of sdb to sda  and hd1 to hd0 (all but menu.lst that should be left as i wrote).

Reboot your computer, enter F12 just to choose where to boot and choose your pendrive.

I hope this help you.

P.s. I contacted "Italian Acer", and they told me that the installed operating system is the only guaranteed to work right by them. Each other OS will no have any official support. Argh...

---

### Post by lemurian on 2009-12-02
> **iceman said:**
> P.s. I contacted "Italian Acer", and they told me that the installed operating system is the only guaranteed to work right by them. Each other OS will no have any official support. Argh...

Yep, Acer USA did not reply to me but if they had, I would have gotten the same answer.  That's what the people on the front line of customer service are trained to say.  And that's why what is needed is to grab the attention of someone higher up.  There's no guarantee of success but only people higher in the organization have the power to change anything.

---

### Post by Bios2000 on 2009-12-03
Hi,

does anyone try the 2.6.32 Kernel? Perhaps it will solve the suspend problem. :)

---

### Post by acermobile on 2009-12-03
I have 2.6.32rc6 running and it does in no was solve the suspend problem.

Someone has to fix the DSDT properly I suppose...

---

### Post by Literati on 2009-12-03
Thanks for the detailed response iceman! I'll give that a shot when I have a bit more time. For now I'm running Kubuntu and it's going okay. :) 

I wanted to mention how I love how it's faster for me to turn off and just cold boot my PC than it is for me to resume from a Hibernate. Maybe when the Suspend is fixed that'll change, but for right now, it's not too big of a deal, cause KDE remembers your sessions anyway. :D

I was also wondering, has anyone popped an SSD in this thing yet? How much faster does it get on boot / in general use? And how does it affect the battery life? I'm considering buying a 64GB SSD or so, but I won't bother if it won't make much difference. 

Thanks!

---

### Post by caelestis2 on 2009-12-04
My laptop arrived.

How did you guys install ubuntu? I opened up GParted, and not to my surprise, I was correct, I have 3 ntfs partitions, the 100mb one used by Windows 7 as I said earlier, the 12 gb recovery, and the rest was Windows 7.

I am trying to resize the Windows 7 partition to 85 GB and so far the bar is just bouncing back and forth, hope it's actually doing something. Had to put the ext-4 and swap into an extended partition.

Oh, and the audio isn't working running off of the live usb. Everyone else says that audio works fine by default so what's wrong?

Edit: Okay, GParted finished beautifully, and windows wanted to run CHKDSK and didn't find anything wrong. Going to try to install linux now =) Battery life in linux reported to be 5h 30 min doing nothing vs. windows 7 doing nothing...

---

### Post by caelestis2 on 2009-12-04
Okay, I've installed everything. Audio seems fine now, only things not working are resume from suspend, enabling wireless with the button after you press it once, and battery life still sucks (4-5h without wifi).

Anyone have a solution for the last two?

---

### Post by tomfool on 2009-12-05
Sure!
I'm gettin' 7hrs using wifi so i guess you could do the same!
That's what i did:
Install powertop
Enable Laptop_mode
when i'm on battery i run powertop and do what it sugests to me 
Enable wifi power_saving.
7hrs of autonomy!
Easy!

---

### Post by jimmy the saint on 2009-12-05
I have written a letter to Acer.  Clearly the customer service channels are proving ineffective for trying to get this bug fixed.  I am posting the letter below along with the address to the corporate headquarters in San Jose CA.  Snail mail, in this case, may serve us better than email, as any email regarding this issue is being either ignored, or auto-responded with a "we don't support linux so go away" response.  Please print out this letter, sign it and mail it to the address I provide.  Thank You.
> 
Acer Management,

I recently purchased an Acer Aspire 3810T.  It has thus far proved to be a wonderful little machine that is both light weight and has a great battery life.  There is, however, one major issue that has yet to be resolved.

There appears to be a bug in the BIOS that prevents the machine from being able to suspend RAM under Linux.  The same issue was present in the 4810T, but was fixed with a BIOS update.  Several Acer customers have contacted Acer and have either received no response, or a simple insistence that Acer does not support Linux.  While this may be true, the issue was clearly identified in the 4810T BIOS, and applying it to the 3810T BIOS should be a simple matter.

It is certainly your prerogative to support, or not, whichever operating systems you choose.  In this case, however, the fix is likely the same BIOS tweak that was applied to the 4810T.  Failing to release a simple fix to stand your ground that Linux will not be supported makes no sense.  You wind up alienating many customers in order to save a negligible amount of effort, or to prove a point.  Either way, it is bad business in my view.

I write this letter in the hope that you can send word down to your engineers that this fix should be applied to the 3810T BIOS.  Normal customer service channels have proved unwilling to do this.  Should you decide to do so, you will have the gratitude of many customers, including me.

More information on this issue can be found at the following websites.

Bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405120](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405120)

Acer timeline group:
[https://launchpad.net/~acertimeline](https://launchpad.net/~acertimeline)

Ubuntu Acer Timeline Forum Thread:
[http://ubuntuforums.org/showthread.php?t=1165087](http://ubuntuforums.org/showthread.php?t=1165087)



Sincerely,

The address is:

Acer America Corp.
333 W. San Carlos Street, Suite 1500
San Jose, CA 95110, USA

---

### Post by mr bob on 2009-12-05
> **tomfool said:**
> Sure!
I'm gettin' 7hrs using wifi so i guess you could do the same!
That's what i did:
Install powertop
Enable Laptop_mode
when i'm on battery i run powertop and do what it sugests to me 
Enable wifi power_saving.
7hrs of autonomy!
Easy!

I've found out to enable laptop mode it needs these instructions:
```

sudo laptop_mode start
sudo hdparm -S 4 /dev/sda

```

Where would I stick these to ensure this always enables on startup?

I can't find the commands to enable wifi power saving, can you tell me what they are?

thanks for any help.

---

### Post by tomfool on 2009-12-06
sudo gedit /etc/default/acpi-support  

Scroll until you find Enable_laptop_mode and set it to true.

For wifi use this command:sudo iwconfig wlan0 power on^C (Actually i don't know if you need to do it everytime you go on battery)
For using wifi powersaving you need to turn on the backports.

Use powertop!it can help you very much!

---

### Post by acermobile on 2009-12-06
Dispatched an e-mail toi Acer Germany yesterday adressing the technical issues (DSDT mainly) and, in addition, the customer service problem (no/unsatisfactory replies).

Let's see what the reply (if any...) says.

---

### Post by Literati on 2009-12-07
I too sent out an email to customer service. I figure if we all make our voices heard, we might have a better shot. :) At least, it couldn't hurt right? :)

UPDATE: They answered by just plugging their Telephone Service (Which is a complete ripoff haha.) and avoiding my point / questions all together. I've sent a follow-up email, and will keep you all updated.

---

### Post by jimmy the saint on 2009-12-07
> **acermobile said:**
> Dispatched an e-mail toi Acer Germany yesterday adressing the technical issues (DSDT mainly) and, in addition, the customer service problem (no/unsatisfactory replies).

Let's see what the reply (if any...) says.


> I too sent out an email to customer service. I figure if we all make our voices heard, we might have a better shot.  At least, it couldn't hurt right? 



Please consider snail mailing the letter, or a similar one, to the corporate headquarters.  The customer service arm is serving as a firewall and not sending on our feature requests.  I am hoping that by targeting management, we may be able to get through.  When I had issues with the recall I contacted the headquarters and got an American at the recall center rather than an Indian customer service rep reading from a card.  They were actually quite helpful once you got ahold of them.

Edit:  I also got ahold of the corporate customer service line and explained the issue.  He said he would try to get word down, since we have thus far been unable to get word up from the bottome

---

### Post by Literati on 2009-12-07
Not a big fan of Snail Mail. Never really know who reads it (Also, quite a hassle. :P)

Anyway, I just got off the phone with "kevin" at Acer Support, who after much time passed me to "Victor", his Supervisor. He gave me the usual line of we don't support other OS etc. Until it was clearly explained that 

1. 4810T had Suspend To RAM Issue under Linux.
2. Acer fixed this issue.
3. 3810T has same problem.
4. Acer has not fixed this problem.

Then he got what I was saying, typed up a whole bunch of stuff, and will pass it to his higher ups. I don't actually know if we'll see anything come of this, but again, steps in the right direction. Enough complaints (Hell, even a good Digg article or Consumerist) and we're golden. :)

---

### Post by caelestis2 on 2009-12-08
Does the 4810 and 3810 have different BIOS's?

---

### Post by miegiel on 2009-12-09
> **caelestis2 said:**
> Does the 4810 and 3810 have different BIOS's?

The x810T and x810TG series must have different BIOSes (I assume) because of the TG series needs to be able to switch graphics cards in the BIOS. I don't know of any differences in the 3810T, 4810T and 5810T motherboards and if they're identical, the BIOSes should be interchangeable, if the BIOSes are not identical already.

The problem is that if you try it you'll be in deep faeces if you brick your laptop. The only safe thing you can do is download the BIOSes and compare the files (don't ask me how to do that, I'll need to look it up). If 2 BIOSes of the same version for different timeline models are identical, the other BIOSes are probably interchangeable too.

But even if the BIOS files are not identical it doesn't exclude the possibility that they are interchangeable. It would surprise me if the motherboards in the laptops are not exactly the same electronically.

***edit:***
4810T and 5810T have the same motherboard. 3810T's motherboard is different. See **citizenofnowhere**'s [post]("http://ubuntuforums.org/showthread.php?p=8477484#post8477484")

---

### Post by jimmy the saint on 2009-12-09
I doubt they are the same.  If they were, it seems like they would release the BIOS updates at the same time and have the same version.  The 4810 has had far more BIOS releases and is in 2XX series, while the 3810T is still at 1.17.

---

### Post by miegiel on 2009-12-09
> **jimmy the saint said:**
> I doubt they are the same.  If they were, it seems like they would release the BIOS updates at the same time and have the same version.  The 4810 has had far more BIOS releases and is in 2XX series, while the 3810T is still at 1.17.

True, but I can see no sane reason for acer to use a different motherboard in the 4810T. After all, disregarding the screen size and the DVD player, the specs are exactly the same. Maybe someone with a 4810T can compare the motherboard with the [pics of the 3810T motherboard I posted here]("http://ubuntuforums.org/showthread.php?p=7979000#post7979000").

If someone knows a good way to compare 2 BIOS files (opening the BIOS file in *gedit* gives no joy) I wouldn't mind wasting some time on it. It could very well be that the older BIOSes are (almost) identical.

***edit:***
4810T and 5810T have the same motherboard. 3810T's motherboard is different. See **citizenofnowhere**'s [post]("http://ubuntuforums.org/showthread.php?p=8477484#post8477484")

---

### Post by citizenofnowhere on 2009-12-10
> Quote:
Originally Posted by jimmy the saint  
I doubt they are the same. If they were, it seems like they would release the BIOS updates at the same time and have the same version. The 4810 has had far more BIOS releases and is in 2XX series, while the 3810T is still at 1.17.


True, but I can see no sane reason for acer to use a different motherboard in the 4810T. After all, disregarding the screen size and the DVD player, the specs are exactly the same. Maybe someone with a 4810T can compare the motherboard with the pics of the 3810T motherboard I posted here.

If someone knows a good way to compare 2 BIOS files (opening the BIOS file in gedit gives no joy) I wouldn't mind wasting some time on it. It could very well be that the older BIOSes are (almost) identical.

I've asked myself this question a few weeks back. I found out they are NOT the same by many stretches.

1. Do NOT attempt to use a 4810 bios from any model on the 3810. It will allow you to flash it, which is the scary part because after that the laptop is totally bricked. If you're lucky you may be able to talk your way into a new motherboard. 

2. Comparing DSDT files alone I noticed that the hardware addresses are all completely different, as are all the port arrangements. Makes me think it's a very different mobo and very different code.

3. This was somewhat confirmed when I contacted Acer Singapore about the suspend issue. The only useful information they gave me is that the 4810 and 5810 series share the same mobo, but the 3810 doesn't.

That said, it shouldn't be too hard to fix,  because if both laptops had the same problem that points to a problem in the logic of the BIOS code - how hard can that be? :-\"

---

### Post by smb96 on 2009-12-12
Is there nobody with a version witch was shipped with linpus linux? maybe than we could figure something out.

---

### Post by Bios2000 on 2009-12-13
i have an Travelmate 8571 Timline. Got the same problems as the 3810t Suspend internal mic and bios is also the ame i think 1.17. it was shipped with linups...after i opened the box a paper was lying in it who tells me that suspend is not working with linups :( 

is this nice?

---

### Post by miegiel on 2009-12-13
> **Bios2000 said:**
> i have an Travelmate 8571 Timline. Got the same problems as the 3810t Suspend internal mic and bios is also the ame i think 1.17. it was shipped with linups...after i opened the box a paper was lying in it who tells me that suspend is not working with linups :( 

is this nice?

Not nice at all of acer ... at least it proves someone at acer knows suspend doesn't work.

---

### Post by mr bob on 2009-12-13
Do you mean linpus?

If they are shipping a model with the same bios with a distro of Linux preinstalled and the suspend doesn't work, then that is even more of a reason to fix it. There is absolutely no excuse at all!

If I was you I would contact them telling them that a model shipped without suspend not working is unacceptable.

---

### Post by smb96 on 2009-12-13
That doesn't sound good. If you ask me that means they know the problem, but dont want to change anything...
I would love to buy a 3810t or a 8371, but i learnd my lesson with other hardware before. I think i will go for an Asus UL30a or Samsung X360 now

---

### Post by caelestis2 on 2009-12-13
I have been using my 3810t with Windows 7 for a while now because I can set the laptop lid to suspend when closed, and it works fantastically. Wish acer could fix this issue with linux, because all the software I would like to use is on that OS.

Had some 1080p HD video playing on my laptop the other day that couldn't play on other people's laptop with better specs. Is this because of hardware acceleration? I try to use VLC on windows 7 and ubuntu but they both are not that good at it.

---

### Post by caelestis2 on 2009-12-13
Does anyone else have this problem? When I used the live cd, I could use two fingers just fine, but when I installed ubuntu, when I put two fingers down, the mouse pointer goes wild and erratic. If I lay my index finger flat to increase the surface area, it still works, only two fingers behaves like this. Anyone know why?

Edit: Nvm, I reinstalled ubuntu and it works fine again. *sigh*

---

### Post by miegiel on 2009-12-14
> **caelestis2 said:**
> ...

Had some 1080p HD video playing on my laptop the other day that couldn't play on other people's laptop with better specs. Is this because of hardware acceleration? I try to use VLC on windows 7 and ubuntu but they both are not that good at it.

Both in windows and linux VLC isn't a "good" player when you're playing vids that are at the end of what your machine can handle with it's resources. Of course VLC is magical when you need to crop, set the aspect ratio or sync the audio to the video and lots more (I use it for all vids 720p and less). 

For 1080p I use windows :roll: and XBMC (on my 3180T anyway). It's pretty easy to make 1080p not run smooth in ubuntu and windows, even on faster laptops. A messy windows installation should do the trick already. 1080p HD is a lot of ones and zeroes to process every second and near the edge of what the timeline can do.

---

### Post by originalmike on 2009-12-15
Hi, I've a 4810TG and I'd like to know your battery consumption. I stay between 12 and 14 W. I activated the laptop mode in "/etc/default/acpi-support" and this is my /etc/rc.local:
```
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/sbin/iwconfig wlan0 power on
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs 
hal-disable-polling --device /dev/cdrom

exit 0

```
With this configuration on karmic i can achieve 4 hours of battery life. Do you think i could better my configuration? Please tell me  if these solutions are corrected or not and if you know other tips. 
Thank you

---

### Post by mr bob on 2009-12-15
> **originalmike said:**
> Hi, I've a 4810TG and I'd like to know your battery consumption. I stay between 12 and 14 W. I activated the laptop mode in "/etc/default/acpi-support" and this is my /etc/rc.local:
```
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/sbin/iwconfig wlan0 power on
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs 
hal-disable-polling --device /dev/cdrom

exit 0

```
With this configuration on karmic i can achieve 4 hours of battery life. Do you think i could better my configuration? Please tell me  if these solutions are corrected or not and if you know other tips. 
Thank you

Have you the original bios? Updating the bios can make a huge difference.

---

### Post by originalmike on 2009-12-15
Do you think I have to install a specific bios or i can choose just the last one? And can you tell me also how to update bios from ubuntu? I have no windows installed on my laptop...

---

### Post by mr bob on 2009-12-15
Usually it is best to install the latest BIOS but it is probably best to ask guys with a 4810TG.

I think the 3810 has a different bios to the 4810.

It is best to install the bios from DOS or FreeDOS. 

I do this by having SysRescueCD installed onto a flash disk. SysRescueCD is a useful live linux distro for troubleshooting and archiving. One of its options is to boot up FreeDos and you can install the BIOS from there. 

If you search the forum I am sure there will be more detailed instructions of installing a bios from FreeDOS if you need them.

---

### Post by originalmike on 2009-12-15
Thank you so much for your help. Just another thing: with 12-14 W I'm around the average?

---

### Post by miegiel on 2009-12-15
> **originalmike said:**
> Thank you so much for your help. Just another thing: with 12-14 W I'm around the average?

I'm at 10-15W (3810T) depends on what I'm doing, can crank it up too 20W.

---

### Post by mr bob on 2009-12-16
Does anybody know how much resource the acer crystaleye (Suyin) webcam is using? I never use it. Is it possible to disable it? What modules can I turn off? I've searched the web and can't find any information.

Now that I've ensured all the other stuff isn't eating up the battery, Powertop is saying the webcam causes many of the wakeups and the top offenders do seem to be a USB device (I have no external device plugged in - so it much be an internal usb device).

I don't know if disabling it would save much but I would be interested to know, none the less.

Thanks for any help.

---

### Post by csipuka on 2009-12-16
> **originalmike said:**
> Thank you so much for your help. Just another thing: with 12-14 W I'm around the average?

I have the same configuration, and in idle mode my power consumption below 10W. WIFI on, BT off, backlight minimal, etc.
If I am just use browser (adblock, other ad removers active! flash ads eat too much), the estimated battery life around ~6.5hours.
One of the biggest improvement was to enable the power save for wifi. I got more than 1 hour extra time.
I use my ATI card in powersave mode always, and the compiz active. Nice.
One more thing. I use the BIOS 1.20.
Actually I have no problem, a no reason to update. Unfortunately I have not seen any brief/detailed change log for BIOS. :(

---

### Post by originalmike on 2009-12-17
Which laptop have you? 4810 or 3810? And can you explain me how to check if powersave for wifi is enabled? thank you

---

### Post by csipuka on 2009-12-17
> **originalmike said:**
> Which laptop have you? 4810 or 3810? And can you explain me how to check if powersave for wifi is enabled? thank you
4810. I am not sure about the last 2 letters (TG?), but I have an ATI4330.
If I remember well you have to use iwconfig, and on the result you can see the powersaving status.
More info:
[https://help.ubuntu.com/community/AspireTimeline/Using](https://help.ubuntu.com/community/AspireTimeline/Using)

---

### Post by originalmike on 2009-12-17
Thank you. So do you think the 1.20 BIOS is better than the last one?

---

### Post by csipuka on 2009-12-17
> **originalmike said:**
> Thank you. So do you think the 1.20 BIOS is better than the last one?
I never said that.
I just have no problem with the laptop, why should I upgrade?
Sorry, I have one issue. I cannot write CD, but I have the same issue on my desktop, so it is not BIOS relevant :)

---

### Post by originalmike on 2009-12-17
Thank you for the reply. Now I ask to the users who have my same laptop and tried different BIOS: which is the best one?

---

### Post by miegiel on 2009-12-17
> **originalmike said:**
> Thank you for the reply. Now I ask to the users who have my same laptop and tried different BIOS: which is the best one?

No one knows really and there are no release notes for the BIOSes either. Maybe acer's call wall (center) knows. Certain BIOSes fix certain bugs presumably. :twisted:

---

### Post by acermobile on 2009-12-21
Hi everyone. I just got the following reply from ACER Germany. It looks like they are at least willing to pass it on to the respective department. We'll see what they can or will do about it.

Best, felix

BTW: 3 weeks is a pretty long time to answer a service request. Anyway I am pleased with the result (if any).

[/snip]
Die Fehleranalyse ist abgeschlossen und Sie erhalten dazu folgende
Mitteilung: 
Wir werden Ihre Anfrage an unser Team zur Softwareentwicklung und
Programmierung BIOS geben. Leider kann zum jetzigen Zeitpunkt noch nicht
angegeben werden, ob und wann entsprechende Lösungsvorschläge oder
Rückmeldungen erfolgen. Daher möchte ich Sie um etwas Geduld bitten. 

Das Antworten auf diese E-Mail ist aus technischen Gründen nicht
möglich. 

PS: Stellen sie bitte vor allen weiteren Fehleranalyse-Maßnahmen sicher,
dass die neueste Biosversion für dieses Gerät installiert wurde (zu
finden auf support.acer-euro.com). 
[/snip]

---

### Post by avilella on 2009-12-21
Good news. There are already 130 or more linux users affected by this issue!

[http://launchpad.net/~acertimeline](http://launchpad.net/~acertimeline)

> **acermobile said:**
> Hi everyone. I just got the following reply from ACER Germany. It looks like they are at least willing to pass it on to the respective department. We'll see what they can or will do about it.

Best, felix

BTW: 3 weeks is a pretty long time to answer a service request. Anyway I am pleased with the result (if any).

[/snip]
Die Fehleranalyse ist abgeschlossen und Sie erhalten dazu folgende
Mitteilung: 
Wir werden Ihre Anfrage an unser Team zur Softwareentwicklung und
Programmierung BIOS geben. Leider kann zum jetzigen Zeitpunkt noch nicht
angegeben werden, ob und wann entsprechende Lösungsvorschläge oder
Rückmeldungen erfolgen. Daher möchte ich Sie um etwas Geduld bitten. 

Das Antworten auf diese E-Mail ist aus technischen Gründen nicht
möglich. 

PS: Stellen sie bitte vor allen weiteren Fehleranalyse-Maßnahmen sicher,
dass die neueste Biosversion für dieses Gerät installiert wurde (zu
finden auf support.acer-euro.com). 
[/snip]

---

### Post by jimmy the saint on 2009-12-21
An English Tranlation via Google Translate for us non Germans
> 
The error analysis is complete and automatically receive the following
Message:
We will process your request to our team for software development and
Programming the BIOS type. Unfortunately, at this stage not
specify if and when appropriate solutions or
Feedback takes. Therefore I would ask you to be patient.

The answers to these e-mail is not for technical reasons
possible.

PS: Make sure you ask before any other troubleshooting measures,
that the latest bios version is installed for this device (at
See support.acer-euro.com).

---

### Post by caelestis2 on 2009-12-21
Hey, I'm having a trouble trying to get my machine to boot from an SD card. I've tried two different types and they are not working. I think it stopped working when I updated my BIOS to 1.17. Is it safe to downgrade to 1.15?

---

### Post by miegiel on 2009-12-21
> **caelestis2 said:**
> Hey, I'm having a trouble trying to get my machine to boot from an SD card. I've tried two different types and they are not working. I think it stopped working when I updated my BIOS to 1.17. Is it safe to downgrade to 1.15?

I don't think so. 1.15 was only on the acer site for a short period and replaced with 1.17 in only 2 or 3 days. I think it's safer to downgrade to BIOS 1.10.

Hmm ... just checked. 1.15 is listed with the other BIOSes again. I'd swear they had removed it.

---

### Post by caelestis2 on 2009-12-21
So is it safe to downgrade?
The BIOS options in 1.17 look different than 1.15 too.

Edit: Hmm, it seems the bios updating utility won't let me downgrade. Now what am I supposed to do for linux?

---

### Post by caelestis2 on 2009-12-21
I tried a whole bunch of buttons to bring up the boot from device menu but I don't think 1.17 has it. I tried all the function keys and the del, esc key, they just dont work.

This is quite annoying.

Edit: Okay, I found that you have to enable the F12 boot menu in the BIOS settings. I opened the boot menu, and the SD card doesn't show up. I think 1.17 disabled the ability to boot from an SD card.

---

### Post by miegiel on 2009-12-21
> **caelestis2 said:**
> So is it safe to downgrade?
The BIOS options in 1.17 look different than 1.15 too.
I guess, else acer should have removed it.
> Edit: Hmm, it seems the bios updating utility won't let me downgrade. Now what am I supposed to do for linux?
Are you trying to flash it from windows? If so you could try flashing from something DOS-like (I used UBCD to flash to 1.10 IIRC).
> I tried a whole bunch of buttons to bring up the boot from device menu but I don't think 1.17 has it. I tried all the function keys and the del, esc key, they just dont work.
F12 should list the boot devices, hold it for a sec at the same time you would press F2 if you would want to enter the BIOS.

I just checked it on my machine (3810T BIOS 1.10) and you need to have the F12 boot menu option enabled in the BIOS (think it was in the *main* menu page)

---

### Post by caelestis2 on 2009-12-21
I borrowed someone's USB stick and it could boot off that. I hate that they changed booting from SD card.

I am trying to get the ethernet to work but [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx) doesn't work anymore. Can anyone share the driver?

---

### Post by miegiel on 2009-12-21
> **caelestis2 said:**
> I borrowed someone's USB stick and it could boot off that. I hate that they changed booting from SD card.

I am trying to get the ethernet to work but [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx) doesn't work anymore. Can anyone share the driver?

Are you still using jaunty? If so it might be less trouble upgrading to karmic (in karmic you don't need to install the driver manually)

---

### Post by caelestis2 on 2009-12-21
This BIOS is giving me a whole bunch of woes. How do you use UBCD to flash the BIOS?

---

### Post by miegiel on 2009-12-21
> **caelestis2 said:**
> This BIOS is giving me a whole bunch of woes. How do you use UBCD to flash the BIOS?

In short, what I remember I did was :
[LIST]
[*]Make a tiny FAT32 partition at the far end my hard disk (use gParted if the command line is to complicated) and put the BIOS there.
[*]Boot the UBCD (I used a USB DVD player, but if you put it on a USB stick it should work too).
[*]In the boot menu select the DOS to boot DOS (though IIRC it wasn't called DOS, check the FAQ/manual/readme on the UBCD site)
[*]Go to my hard disk (probably C: ) cd (change directory) my way to where I put the BIOS
[*]Flash it and reboot.
[/LIST]
UBCD always gives me a bit of a headache. Probably because I only use it once a year and never really get to know it. There's so much other stuff you can do with it that I always have trouble finding the DOS boot option. :D But the UBCD site should help you wade through the muddy parts.

**NB** it's recommended to reset the BIOS to it's default settings before and after flashing and boot past loading the BIOS once before setting up the BIOS the way you want it. Sometimes stuff gets messed up if you don't.

---

### Post by csipuka on 2009-12-22
> **caelestis2 said:**
> This BIOS is giving me a whole bunch of woes. How do you use UBCD to flash the BIOS?
At the bottom of the following page, there is a link, how to upgrade the BIOS.
[https://help.ubuntu.com/community/AspireTimeline/Using](https://help.ubuntu.com/community/AspireTimeline/Using)

---

### Post by avilella on 2009-12-24
Hi caelestis2,

Since your 3810t is suspending correctly under Windows 7, would you mind submitting your DSDT.dsl table so that it can be inspected to have it working with Linux?

Please attach your DSDT information to this Launchpad bug report specifying your laptop model:

[https://bugs.launchpad.net/bugs/312756](https://bugs.launchpad.net/bugs/312756)

To compile your DSDT information, install if you haven't already the acpidump and iasl tools:
sudo apt-get install acpidump iasl           # on Debian-based systems

Then run the following commands:

sudo acpidump > acpidump.txt
sudo acpixtract acpidump.txt
iasl -d DSDT.dat

This will create a DSDT.dsl file that you can attach to the bug report.

Thanks!

> **caelestis2 said:**
> I have been using my 3810t with Windows 7 for a while now because I can set the laptop lid to suspend when closed, and it works fantastically. Wish acer could fix this issue with linux, because all the software I would like to use is on that OS.

Had some 1080p HD video playing on my laptop the other day that couldn't play on other people's laptop with better specs. Is this because of hardware acceleration? I try to use VLC on windows 7 and ubuntu but they both are not that good at it.

---

### Post by jimmy the saint on 2009-12-24
Avilella,

You can find the files you want on the suspend issue bug report.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405120](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405120)

---

### Post by qnano on 2009-12-27
Does anyone know how to solve the fan problem (always running) on the 3810t under Karmic? After a while it becomes unbearable. The fan operates almost all the time (and the result is that the Core0 temperature never goes higher than 42 C). 

This temperature is not high enough for the fan to kick in...

I'm running BIOS version 1.17 on an Aspire 3810t laptop.

Thanks!

---

### Post by tomfool on 2009-12-28
qnano is the latest bios,try to downgrade at one before and i think you solve the problem!I guess  doing the same cuse it's so noising...

---

### Post by aioan on 2009-12-28
> **quail-linux said:**
> I have GREAT news for the 4810T owners the 2.30 BIOS[1] is rockin we now have backlight control keys working :-D

There is a catch tho you have to change from
```
xrandr --output LVDS --set BACKLIGHT_CONTROL native
```
to
```
xrandr --output LVDS --set BACKLIGHT_CONTROL kernel
```
or you will get a freeze type effect on the desktop. Also I noticed that my wifi went funny to and I could not ping anything even tho NM was say I was connected to AP. 

**So [COLOR="Red"]DON'T[/COLOR] play with backlight key till done the above changes.**

[1] [http://support.acer-euro.com/drivers/downloads_gd.html](http://support.acer-euro.com/drivers/downloads_gd.html)

Edit: I have noticed this works correctly in 'combination' too
```
xrandr --output LVDS --set BACKLIGHT_CONTROL combination
```

Same problem with system becoming unresponsive when using the brightness keys.

BIOS v1.31 => the above solution does not work for me...

any help appreciated,

Regards.

---

### Post by qnano on 2009-12-28
> **tomfool said:**
> qnano is the latest bios,try to downgrade at one before and i think you solve the problem!I guess  doing the same cuse it's so noising...

I am somewhat cautious with flashing the BIOS without good reason.. What makes you think that the fan speed will be normal if I downgrade to a previous BIOS version?

---

### Post by tomfool on 2009-12-29
> **qnano said:**
> I am somewhat cautious with flashing the BIOS without good reason.. What makes you think that the fan speed will be normal if I downgrade to a previous BIOS version?

Because i had the old bios and it didn't do it

---

### Post by mr bob on 2009-12-29
> **Arlanthir said:**
> Have you tried installing linux-backports-modules-karmic-generic ?
It fixes the wlan power managing, might fix your problems too.

I recently installed Linux Mint 8, based on Ubuntu 9.10 on my Acer Aspire Timeline 3410 (very similar to 3810t) and my wireless became very unreliable, often just switching off.

I've just installed the backports as suggested, having also read this thread:
[URL="http://ubuntuforums.org/showthread.php?t=1333994&page=2"]
http://ubuntuforums.org/showthread.php?t=1333994&page=2[/URL]

And the strength of the signal has increased from less than 50% to 97%!!!
Now the wireless is working perfectly.

---

### Post by qnano on 2009-12-29
> **tomfool said:**
> Because i had the old bios and it didn't do it

Was that also under Karmic? And is it possible to downgrade the BIOS? I have only updated versions this far. Thanks.

---

### Post by caelestis2 on 2009-12-29
> **qnano said:**
> Was that also under Karmic? And is it possible to downgrade the BIOS? I have only updated versions this far. Thanks.

Read back a couple of posts.

---

### Post by tomfool on 2009-12-31
Qnano have you donwngraded?

---

### Post by cyberfish on 2010-01-01
Flashed 1.20 (3810t). Still no suspend.

---

### Post by caelestis2 on 2010-01-01
> **cyberfish said:**
> Flashed 1.20 (3810t). Still no suspend.

Suspend not fixed in kernel 2.6.2 either

---

### Post by mr bob on 2010-01-08
> **cyberfish said:**
> Flashed 1.20 (3810t). Still no suspend.

Does Bios 1.20 offer any other improvements that anybody is aware of? 

It is really poor that Acer don't provide a list of new features with each version.

---

### Post by tomfool on 2010-01-09
Fan fixed,wokrs better.

---

### Post by idreamer on 2010-01-10
> **tomfool said:**
> Fan fixed,wokrs better.

how to?

---

### Post by tomfool on 2010-01-10
It's less noisy,even when you are on AC.I think nothing else.

---

### Post by acermobile on 2010-01-10
BIOS 1.20: Still no suspend,
Kernel 2.6.33-rc3: Still no suspend, even with the new "acpi_sleep=sci_force_enable" option; I was unable to compile to proprietary ATI driver (some naming errors, unable to replicate right now (running 2.6.32 now))

What keeps me smiling is the battery lifetime - no suspend needed at all...

---

### Post by mr bob on 2010-01-11
> **acermobile said:**
> BIOS 1.20: Still no suspend,
Kernel 2.6.33-rc3: Still no suspend, even with the new "acpi_sleep=sci_force_enable" option; I was unable to compile to proprietary ATI driver (some naming errors, unable to replicate right now (running 2.6.32 now))

What keeps me smiling is the battery lifetime - no suspend needed at all...

Just to be clear, are there any changes in BIOS 1.2 that further improve the battery life?

---

### Post by qnano on 2010-01-11
> **tomfool said:**
> It's less noisy,even when you are on AC.I think nothing else.

I have to disagree. In my case flashing 1.20 has had the effect that the fan starts spinning when the internal temperature reaches 34 C. With BIOS 1.17 the temperature where the fans kicked in was 42 C (and as far as I know with BIOS 1.10 it was around 54 C). It seems that in every BIOS upgrade the fan is made to kick in at lower temperatures. 

With regards to battery life increase, you can imagine the effect on battery life with the fan spinning all the time when on AC. 34 degrees is lower than body temperature..

In my view we are wasting our time with waiting for future BIOS releases to fix fan spinning and perhaps suspend and other issues. Ubuntu users are only a small (but important!) minority of people using this laptop, and frankly I now doubt whether the manufacturer would issue a new BIOS just for helping out Ubuntu users when it appears that under the more mainstream OSes these problems don't exist.

---

### Post by acermobile on 2010-01-12
I can confirm that the fan is now running much more often when on AC, than it was before :( No other changes noted so far.

---

### Post by jimmy the saint on 2010-01-12
This is likely do to the fact that they just announced the microphone cable recall in the US and it has been associated with fires according to engadget or wired or one of those online tech mags.

---

### Post by tomfool on 2010-01-12
Well guys,in my case i had the 1.17 bios and the fan was very noisy while now by the 1.20 it always runs but at less rpm and so i find it less noisy,for battery life it's almost the same in both bios,6.30 h with wifi on.

---

### Post by avilella on 2010-01-12
Maybe you have a different hardware than the other reports. Can you run this command in a terminal?

lspci -vnnn | perl -lne 'print if /^\d+\:.+(\[\S+\:\S+\])/'

> **tomfool said:**
> Well guys,in my case i had the 1.17 bios and the fan was very noisy while now by the 1.20 it always runs but at less rpm and so i find it less noisy,for battery life it's almost the same in both bios,6.30 h with wifi on.

---

### Post by idreamer on 2010-01-12
my acpi temperature is blocked on 26.8. every time, every firmware. how to fix it?

[idreamer@Marvin ~]$ acpi -t
Thermal 0: ok, 26.8 degrees C

---

### Post by tomfool on 2010-01-12
Here we are:

00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03) (prog-if 20)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03) (prog-if 20)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93) (prog-if 01)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M-E LPC Interface Controller [8086:2917] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03) (prog-if 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
00:1f.6 Signal processing controller [1180]: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem [8086:2932] (rev 03)
01:00.0 Network controller [0280]: Intel Corporation Wireless WiFi Link 5100 [8086:4232]
02:00.0 Ethernet controller [0200]: Attansic Technology Corp. Device [1969:1063] (rev c0)

---

### Post by qnano on 2010-01-12
> **jimmy the saint said:**
> This is likely do to the fact that they just announced the microphone cable recall in the US and it has been associated with fires according to engadget or wired or one of those online tech mags.

yeah, i've also thought about that regarding fan operation and temperature..

A suggestion: 

There is a module called "acerhdf" by some programmer that was initially made for the Aspire One netbook, but which has been successfully ported on the Acer 1810 to reduce fan speed under Ubuntu. The Acer 1810 is almost exactly the same as 3810 in terms of hardware - only smaller screen size and BIOS versions seem to be numbered differently. 

Does anyone have the technical skills to inform us how to use this module to control fan speed on the 3810? If it works on the very similar 1810 it might not prove to be too difficult to make it work under 3810.

---

### Post by erchewy on 2010-01-13
Acer 3810TGZ - Ubuntu karmik 64 bits.
Does lm-sensors works? It only detects one sensor for me, and is always at 26.8ºC . 
Thanks in advance.
Regards.

---

### Post by miegiel on 2010-01-13
> **erchewy said:**
> Acer 3810TGZ - Ubuntu karmik 64 bits.
Does lm-sensors works? It only detects one sensor for me, and is always at 26.8ºC . 
Thanks in advance.
Regards.

I think you forgot to run :
```
sudo sensors-detect
```

My *sensors* output (32bit karmic):
```
user@machine:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +26.8°C  (crit = +127.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +45.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +44.0°C  (high = +100.0°C, crit = +100.0°C)  

```
who knows : acpitz-virtual-0 :-k
core 1 : coretemp-isa-0000
core 2 : coretemp-isa-0001

---

### Post by pfem on 2010-01-14
> **erchewy said:**
> Acer 3810TGZ - Ubuntu karmik 64 bits.
Does lm-sensors works? It only detects one sensor for me, and is always at 26.8ºC . 
Thanks in advance.
Regards.

How does it work the ubuntu 64-bit for you, on 3810t ? I want to install it because 32-bit only supports 3Gb of ram.

---

### Post by jaleel on 2010-01-17
Hello guys, I have 3810tg with su9400
I killed ati graphic, made laptop-mode and have 10-14w
Is it normal?

---

### Post by miegiel on 2010-01-17
> **jaleel said:**
> Hello guys, I have 3810tg with su9400
I killed ati graphic, made laptop-mode and have 10-14w
Is it normal?

Yes, my 3810T (SU9400) uses 10W when it's idle. It goes up to 20W or so when I make it sweat.

---

### Post by jaleel on 2010-01-17
I'll try to install Arch next week, maybe it use less power...

---

### Post by acermobile on 2010-01-17
I am using Karmic with fglrx and laptop mode. The total power consumption is slightly smaller than 10 W with wireless enabled and bluetooth disabled. When shutting down wireless and stopping some rarely needed apps I can get close to 8 W and a total battery life of 7-8 h is possible, when being moderate. I can confirm that disabling the discrete graphics and enabling the intel does not give much longer battery life, although (I think) it should...

---

### Post by eScenCe on 2010-01-19
I was following development of Ubuntu and Acer Timeline patches latley and again I wanted to ask two important things:

a. Is there finally a solution under linux to **disable** the HD4330 and running battery power only from the **onboard** graphic card?

b. If things above are finaly fixed, how long do the Acer runs from battery power?
Last time I tried it, battery was empty after ~5 hours because of the gc issue - losing nearly 3 hours isn't simply acceptable. Is it possible to reach ~6 hours now?

I would be really thankful for replies.

---

### Post by pimseb on 2010-01-21
Hello,

Today I've received my Acer Aspire timeline 3810 TZG.
I've read a bit this forum but I feel I don't have the best power management.
I've installed Powertop. The lowest power consumption I've seen was 19 W. Usually it's around 20-22 W. I'm only surfing on firefox with the brightness low and wifi on.
What can I do to make the consumption lower ?
I've installed linux-backports-modules-karmic-generic. Some posts here are about wifi power management. How do I turn that on ?
The fan of the computer is always spinning. Is there a way to stop it ?
And last question like the post above : can we **disable** the HD4330 ?
I'm quite new to ubuntu, switched from windows some weeks ago and I don't really want to turn back to microsoft. But if W7 gives me 8 hours battery instead of 4, I could think about it :s
I'm using karmic 9.10. My kernel is 2.6.31 and bios of my motherboard is the latest (1.20) 
Thank you for your help !

---

### Post by miegiel on 2010-01-23
You can disable the HD4330 in the BIOS at least. It's a bit of a drag, but unless you're going to play a 3D game you won't need the HD4330 anyway and might as well leave it turned off.

---

### Post by eScenCe on 2010-01-23
> **miegiel said:**
> You can disable the HD4330 in the BIOS at least. It's a bit of a drag, but unless you're going to play a 3D game you won't need the HD4330 anyway and might as well leave it turned off.

That would be really big.
I don't use it anyway, sometimes on Win7 for World of Warcraft but I wouldn't mind to use the 3810 as a Office Notebook "full-time".

How long does the 3810 runs without HD4330 compared to switched on Graphic Card?
You tested that already?

btw: I'm running bios rev 1.17 ; and I can only switch between "Switchable" and "Discrete" - with discrete meaning only the 4330 is running, or?
Where can I disable it?

---

### Post by miegiel on 2010-01-23
> **eScenCe said:**
> ...

How long does the 3810 runs without HD4330 compared to switched on Graphic Card?
You tested that already?

Yes :twisted: I decided to turn off the HD4330 in my wallet and buy the 3810T. I haven't played wow on this laptop, but I have played [freeciv]("http://packages.ubuntu.com/karmic/freeciv-client-gtk") (doesn't really count I guess). Honestly, I never missed not having the HD4330.

Oh, and my battery times are crap. The battery got decalibrated and I can't get it to recalibrate. I get about 4 hours on _my workload_, it used to be something between 5 and 6 hours.

> **eScenCe said:**
> btw: I'm running bios rev 1.17 ; and I can only switch between "Switchable" and "Discrete" - with discrete meaning only the 4330 is running, or?
Where can I disable it?

There's a 4810TG thread if you can't find it in this thread, you might need a certain BIOS.

---

### Post by acermobile on 2010-01-24
Hi.

Battery life on Intel graphics only compared to ATI only is approximately the same for me. However, some applications REQUIRE hardware open gl to simply launch. Honestly I can't think of any reason to turn of the ATI consindering the described situation.

Here is a small script I wrote for enabling laptop mode. It enlarges bat. life by more than one hour for me, so it may be worth trying:

#!/bin/sh

sudo su -c "echo 5 >  /proc/sys/vm/laptop_mode"
sudo su -c "echo min_power > /sys/class/scsi_host/host0/link_power_management_policy"
sudo su -c "echo min_power > /sys/class/scsi_host/host1/link_power_management_policy"
sudo su -c "echo min_power > /sys/class/scsi_host/host2/link_power_management_policy"
sudo su -c "echo min_power > /sys/class/scsi_host/host3/link_power_management_policy"
sudo su -c "echo min_power > /sys/class/scsi_host/host4/link_power_management_policy"
sudo su -c "echo min_power > /sys/class/scsi_host/host5/link_power_management_policy"
sudo su -c "echo 500 > /proc/sys/vm/dirty_writeback_centisecs"
sudo laptop_mode start
# sudo hdparm -S 4 /dev/sda
sudo iwconfig wlan0 power on
Other bat.time life increases are possible by disabling compiz. Here is a part of my xorg.conf:

Section "Files"
        ModulePath   "/usr/lib/xorg/modules"
        ModulePath   "/usr/lib/fglrx"       
        ModulePath   "/usr/lib/xorg/modules/extensions"
EndSection                                             

Section "Module"
        Load  "extmod"
        Load  "dbe"   
        Load  "record"
        Load  "dri"   
        Load  "dri2"  
        Load  "glx"   
        Load  "GL"    
        Load  "vbetool"
        Load  "freetype"
EndSection              

Section "ServerFlags"
        Option      "AIGLX" "off"
        Option      "DontZap" "on"
        Option      "Xinerama" "off"
#       Option      "AIGLX" "on"    
EndSection 

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver "fglrx"                     
        Option "AllowGLXWithComposite" "true"
        Option "backingstore" "on"           
        Option "XAANoOffscreenPixmaps" "true"
        Option "AddARGBVisuals" "True"       
        Option "AddARGBGLXVisuals" "True"    
        Option "MonitorLayout" "LCD,CRT"     
        Option "MergedFB" "True"             
        Option "OverlayOnCRTC2" "true"       
        Option "CRT2Position" "RightOf"      
        Option "DesktopSetup" "horizontal"   
#       Option      "UseInternalAGPGART" "no"
        Option "VideoOverlay" "on"           
        Option "OpenGLOverlay" "off"         
        Option "Monitor-LCD" "0-LCD"         
        BusID  "PCI:1:0:0"                   
EndSection    
Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "Disable"
        Option      "RENDER" "Enable"
        Option      "DAMAGE" "Enable"
        Option      "XVideo" "Enable"
EndSection


Hope this is usefull for somebody.

Best,
Felix

---

### Post by eScenCe on 2010-01-25
> **miegiel said:**
> Yes :twisted: I decided to turn off the HD4330 in my wallet and buy the 3810T. I haven't played wow on this laptop, but I have played [freeciv]("http://packages.ubuntu.com/karmic/freeciv-client-gtk") (doesn't really count I guess). Honestly, I never missed not having the HD4330.

Oh, and my battery times are crap. The battery got decalibrated and I can't get it to recalibrate. I get about 4 hours on _my workload_, it used to be something between 5 and 6 hours.



There's a 4810TG thread if you can't find it in this thread, you might need a certain BIOS.

Acually I'm quite unsure about what you wanted to tell me?
Is  there a way to deactivate it through BIOS or not?
The search via the board don't reply anthing, else I wouldn't asked.
And browsing over 120 pages isn't that ... well , you know? :)

Any ideas how to?

---

### Post by miegiel on 2010-01-25
> **eScenCe said:**
> Acually I'm quite unsure about what you wanted to tell me?
Is  there a way to deactivate it through BIOS or not?
The search via the board don't reply anthing, else I wouldn't asked.
And browsing over 120 pages isn't that ... well , you know? :)

Any ideas how to?

This is the [thread and post]("http://ubuntuforums.org/showthread.php?p=7807723&highlight=discrete#post7807723") I meant. *"Discrete"* is an ambiguous term for *"use ATI graphics only"*. I always forget if it's ATI or Intel only :roll:

What I wanted to say was; "You only really need to be able to turn it off, even if it's a hassle to go through the BIOS, only in rare circumstances the 4330 will give you a advantage in graphics performance". I remember reading somewhere it's possible to only use the intel graphics on the *x*810TG, but I can't remember where. :| It's posible that you can only switch to "intel only" in certain BIOSes (I think I read that somewhere, not 100% sure).

Finally: [When I took my 3810T apart]("http://ubuntuforums.org/showthread.php?p=7979000#post7979000"), I found a empty card slot under the keyboard (2nd image, top right corner). Who knows? That might be where the 4330 resides in the 3810TG. If it does removing the card might be an option. :twisted:

---

### Post by eScenCe on 2010-01-25
> **miegiel said:**
> This is the [thread and post]("http://ubuntuforums.org/showthread.php?p=7807723&highlight=discrete#post7807723") I meant. *"Discrete"* is an ambiguous term for *"use ATI graphics only"*. I always forget if it's ATI or Intel only :roll:


What I wanted to say was ... brb ... I'll finish the post in a few min ...

Yeah, but I want to disable the 4330 ; not using it all time :)

---

### Post by pimseb on 2010-01-26
I'm testing my Acer aspire timeline 3810tzg.
The battery life in ubuntu is really bad :(
Here are my consumption results :

WINDOWS 7 - screen brightness lowest for all tests - battery saving mode.
Intel videocard - wifi OFF - idle ==> 5 - 5,5 W
Intel videocard - wifi ON - idle ==> 5,5 - 6 W
Intel videocard - wifi ON - youtube watching ==> 10 - 14 W
ATI videocard - wifi OFF - idle ==> 6,5 - 7,5 W
ATI videocard - wifi ON - idle ==> 7,5 - 9 W
ATI videocard - wifi ON - youtube watching ==> 12 - 14 W

UBUNTU - screen brightness at lowest for all tests 
(don't know how to switch from Intel to ATI)
Wifi OFF -  laptop mode enabled - powertop enabled (all power saving options set) ==> 17 W is the lowest I can get

So ... you see. Battery in windows will last 2 times more than in Ubuntu. I'm afraid ... How can we fix that ?

---

### Post by riskable on 2010-01-27
I got my 3810T-8737 a few days ago and I love it!  The default battery life with Ubuntu is great but I knew it could be better.  I've managed to get my laptop down to 7.0-7.3W at idle.  Here's how I did it:

(execute this as root or via sudo)
```
#!/bin/bash
# Author: Riskable
#
# Description: Enables every power saving feature I know of
#

# Enable Intel HD Audio power saving
echo 10 > /sys/module/snd_hda_intel/parameters/power_save
echo Y > /sys/module/snd_hda_intel/parameters/power_save_controller
echo 1 > /dev/dsp # Gotta make a sound to turn it on

# Enable various kernel power saving features
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs

# Enable SATA power management
for i in /sys/class/scsi_host/*; do echo "min_power" > $i/link_power_management_policy; cat $i/link_power_management_policy; done

# Enable Wifi power management
/sbin/iwconfig wlan0 power on

# Enable the most aggressive hard drive power savings
hdparm -B 1 -S 12 /dev/sda # Note: May not work on the Acer Timeline's hard drive
```

I also added "usbcore.autosuspend=1" to the GRUB_CMDLINE_LINUX_DEFAULT variable in /etc/default/grub (run 'update-grub' after making that change).  I don't think that particular setting makes much of a difference.

Here's why I think we can't get power usage below 7W in Ubuntu:  ACPI fan control.  The fan is ALWAYS ON with this laptop--for some reason the BIOS doesn't turn it off on its own (ever).  I suspect this problem won't be fixed until Acer releases a BIOS update that fixes whatever the problem is.

As for getting power usage below 6W, I'm not sure what else can be done.  I suspect that Acer did something with its Windows drivers to get it down that low.  They need to be more transparent about this so Linux hackers can get these features working as well.

---

### Post by eScenCe on 2010-01-28
Still I didn't got any feedback of disabling the HD4330 and using onboard ONLY.
Isn't there any way to do this?

---

### Post by acermobile on 2010-01-28
Powertop tells me around 8,0 W in absolute power saving mode (Wifi/Bluetooth off; all the tweaks from above) with ATI enabled!

With Wifi and low screen brightness ca. 9 W.

Disabeling the ATI card:
- Turn graphics to switchable in BIOS
- Compile lenovo_acpi module (google!)
- add to /etc/modules
- reboot

I am still not 100% sure, that it is disabled though...

---

### Post by miegiel on 2010-01-28
> **acermobile said:**
> ...

I am still not 100% sure, that it is disabled though...

If it's not listed with
```
lspci
```
the card is off.

---

### Post by karak_1984 on 2010-01-28
Is the first time I write anything in a forum, i buy a Acer TimeLine 3810T and I investigated. It's very important for install Ubuntu and Windows 7 (Sorry Linux person for intruducing this in this forum but it is true) update the bios of this computer. because if you dont do this you can't install Ubuntu and Windows 7 apearlish v a blue screen. When I buy this computer have the BIOS version 1.04, you can't update first to 1.20 (the last version), you have to update to 1.10,1.15.1.17 and finally 1.20. When you do this you can install Ubuntu and Windows 7 without problem. 
I hope help all with this comentary.

Sorry for my english mistakes but I am from Spain and i dont speak and write English very well. 

Good Luck.

---

### Post by tomfool on 2010-01-29
Hi to everyone!
Well i tried the script wrote by Riskable and it works (thank Riskable),i have the same results,only one question,maybe two:
1)Does your hd completely stop?Mine doesn't.
2)I can't get under 7.3w even if i switch-off wi-fi,is it normal?
I think that we should use ram in a better way,using it like a hd,so we could reduce hd-access.

---

### Post by eScenCe on 2010-01-29
> **acermobile said:**
> Powertop tells me around 8,0 W in absolute power saving mode (Wifi/Bluetooth off; all the tweaks from above) with ATI enabled!

With Wifi and low screen brightness ca. 9 W.

Disabeling the ATI card:
- Turn graphics to switchable in BIOS
- Compile lenovo_acpi module (google!)
- add to /etc/modules
- reboot

I am still not 100% sure, that it is disabled though...

Some fantastic news. I'll definitly give this a try.
Oh, another thing comes to mind.
Does Ubuntu support passiv cooling? The 3810 is quite noisy if active cooling is switched on. (Yeah  ; Sorry ; I'm such a noob -_-)

---

### Post by pimseb on 2010-01-30
> **riskable said:**
> I got my 3810T-8737 a few days ago and I love it!  The default battery life with Ubuntu is great but I knew it could be better.  I've managed to get my laptop down to 7.0-7.3W at idle.  Here's how I did it:

(execute this as root or via sudo)
```
#!/bin/bash
# Author: Riskable
#
# Description: Enables every power saving feature I know of
#

# Enable Intel HD Audio power saving
echo 10 > /sys/module/snd_hda_intel/parameters/power_save
echo Y > /sys/module/snd_hda_intel/parameters/power_save_controller
echo 1 > /dev/dsp # Gotta make a sound to turn it on

# Enable various kernel power saving features
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs

# Enable SATA power management
for i in /sys/class/scsi_host/*; do echo "min_power" > $i/link_power_management_policy; cat $i/link_power_management_policy; done

# Enable Wifi power management
/sbin/iwconfig wlan0 power on

# Enable the most aggressive hard drive power savings
hdparm -B 1 -S 12 /dev/sda # Note: May not work on the Acer Timeline's hard drive
```I also added "usbcore.autosuspend=1" to the GRUB_CMDLINE_LINUX_DEFAULT variable in /etc/default/grub (run 'update-grub' after making that change).  I don't think that particular setting makes much of a difference.

Here's why I think we can't get power usage below 7W in Ubuntu:  ACPI fan control.  The fan is ALWAYS ON with this laptop--for some reason the BIOS doesn't turn it off on its own (ever).  I suspect this problem won't be fixed until Acer releases a BIOS update that fixes whatever the problem is.

As for getting power usage below 6W, I'm not sure what else can be done.  I suspect that Acer did something with its Windows drivers to get it down that low.  They need to be more transparent about this so Linux hackers can get these features working as well.

WOW !! Thank you. I had 20W before (see my post #642) and now I have 9W when surfing! It's like windows now :)
Just one thing, I see this error : Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
How can I fix it ?
thanks

---

### Post by PatrickVogeli on 2010-01-30
install linux-backports-modules-wireless-karmic-generic, reboot and try again

---

### Post by pimseb on 2010-01-30
I've installed this packet now.
The script above works good with kernel 2.6.31.14. But the wireless power saving doesn't, I still see "SET failed on device wlan0" even with linux-backports-modules-wireless-karmic-generic installed. When screen brightness is at its lowest and wifi off, I see 8 W in powertop.

With kernel 2.6.31.17, is seems that the script does nothing at all. I see 20W in powertop (with or without the script). However in this kernel I don't see the error "SET failed on device wlan0". Strange ... ?!

Another question : all these results are with "switchable graphics = discrete" in BIOS.
If I change to "switchable" I can't boot to ubuntu at all. The screen is blinking and I can't log into X. Any idea ?

---

### Post by acermobile on 2010-01-30
Getting below 7 W is only possible, with the Speedstepping is properly supported - which is apparently not the case!

E.g., on the SU4100 (2x1300 Mhz), the only frequencies available are 1300 and 1200 Mhz. I have also pointed this out in an earlier post but still nobody seems to have found a solution to the problem :-(

Any suggestions are welcome. I have also a response from ACER GERMANY.

Here is the original text:
> 
vielen Dank für Ihre Kontaktaufnahme mit ACER.

Wichtig wäre hier zu wissen, auf welche Version Ihre Aussage sich stützt.
Verhält es sich auch mit dem BIOS 1.20 immer noch so ?

Wir werden keine Tests mit Linux machen. Sobald uns die genaueren angaben
aber bereit stehen, können wir gern dieses weitergeben. Da es sich um ein
nicht supportetes Betriebssystem handelt, geben wir keine 100%
Funktionsgarantien.


I will fill out their online web form and see what will happen...

---

### Post by loll31 on 2010-02-01
> **acermobile said:**
> Getting below 7 W is only possible, with the Speedstepping is properly supported - which is apparently not the case!

E.g., on the SU4100 (2x1300 Mhz), the only frequencies available are 1300 and 1200 Mhz. I have also pointed this out in an earlier post but still nobody seems to have found a solution to the problem :-(


Hum can not get less than 9w with 4810TZG (wifi on, all the rest is off and opmimized, ati card off).

So the 14" seems to eat 2w against 13.3" screen ?! should be another think, no ?
Any other 4810TZG users to comfirme this ?

PS: under Seven 64 bits, system uses 7w in the same condition....

---

### Post by acermobile on 2010-02-02
Has anyone tried processor throttling (0 % for one cpu?!?)? Also, why is it not possible to disable one core?

BTW: Any news on the suspend issue?!?

---

### Post by PatrickVogeli on 2010-02-02
> **acermobile said:**
> E.g., on the SU4100 (2x1300 Mhz), the only frequencies available are 1300 and 1200 Mhz. I have also pointed this out in an earlier post but still nobody seems to have found a solution to the problem :-(

That's the processor's design. In windows, it also won't go below  1200MHz.. cause the processor can't. Actually, the differences between the SU4100 and the SU7300 are 1MB cache, VT extensions and the ability to clock down to 800MHz (and 0,8750V. SU4100: 0,9250V).

I doesn't support Dynamic Front Side Bus, I believe it was called.

---

### Post by robert.jarzmik on 2010-02-03
As for the 3810T with a SU9400, with Wifi Off, Bluetooth Off, HDA sound in powersave, SATA in powersave, HDD spined down, camera in powersave (USB suspended), and screen in powersave (ie you don't use your laptop), I get 6W of power drain.

In the same configuration but with screen on (in X + Emacs) and writing text, I get 8W.

If I add wifi, I climb to 9W, and surfing with firefox makes me go even higher towards 10W.


Only my 2 pens for power usage reports.

---

### Post by riskable on 2010-02-04
> **tomfool said:**
> Hi to everyone!
Well i tried the script wrote by Riskable and it works (thank Riskable),i have the same results,only one question,maybe two:
1)Does your hd completely stop?Mine doesn't.
2)I can't get under 7.3w even if i switch-off wi-fi,is it normal?
I think that we should use ram in a better way,using it like a hd,so we could reduce hd-access.

What I failed to mention in my post is that I've also enabled some other power-saving features.  Some of which take care of the issues you're referring to:

1) Enable Laptop Mode (set ENABLE_LAPTOP_MODE=true in /etc/default/acpi).  This should get your hard drive spinning down.
2) "sudo apt-get install preload".  This keeps frequently-accessed data (e.g. shared libraries) in memory so your hard drive doesn't have to spin up as much.  The more memory you have in your laptop the better it will work (I have 4GB but even with 1GB it can save a lot of spinning).  It also has the benefit of seriously improving your system's all-around performance!
3) Use tmpfs (RAM disk) for /tmp (it saves a few more hard drive spinups):  'echo "tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0" >> /etc/fstab'.  This can also improve performance somewhat.

...and here's some general all-around power saving tips:

A) Use Konqueror (with Flash plugin disabled) if you really need to save battery while surfing the web.  It causes considerably less wakeups (see powertop) than Firefox, Chrome, and Opera (in order of most-to-least wakeups).
B) If using Firefox or Chrome, install Flashblock and restart your browser after you're done using Flash on a page.  Flash has a tendancy to eat up 100% CPU even after you've navigated away from a page (64-bit is the worst!).
C) "killall gpg-agent ssh-agent".  These two cause a few wakeups here and there (all the time) and they're just convenience features.  You may not have them running on your system.
D) Disable any constantly-updating desktop widgets such as clocks, CPU/Memory meters, temperature monitors, etc.

Also, contrary to what some people believe, most of the daemons running in the background on a typical Ubuntu system don't cause enough wakeups to have any noticeable impact on battery life.  For example, stopping cupsd and sshd aren't going to buy you any battery time.

If you must have your desktop widgets I've found that if I set the update interval to 5 seconds or greater it reduces their impact on wakeups by many orders of magnitude without negating their usefulness.  My only experience with this has been with CPU/RAM/Network monitors in KDE (native Plasma widgets).

---

### Post by riskable on 2010-02-04
> **PatrickVogeli said:**
> That's the processor's design. In windows, it also won't go below  1200MHz.. cause the processor can't. Actually, the differences between the SU4100 and the SU7300 are 1MB cache, VT extensions and the ability to clock down to 800MHz (and 0,8750V. SU4100: 0,9250V).

I doesn't support Dynamic Front Side Bus, I believe it was called.

This is true (the SU4100 doesn't go down to 800MHz) but I just wanted to mention something regarding the SU7300:  When I first received my 3810T with an SU7300 it could only go down to 1200MHz.  It wasn't until I updated the BIOS that it started supporting 800MHz.

---

### Post by riskable on 2010-02-04
I just discovered something interesting:  Compositing only adds 0.1W to power consumption.  I haven't tested it with Compiz but in KDE that's all it adds.  So you might as well keep those desktop effects on!

Note:  My laptop has only the Intel 4500MHD graphics.  With discreet graphics (ATI) it might be different.

---

### Post by tomfool on 2010-02-04
Thanks Riskable!I'll try every tomorrow morning!Will see...;)

---

### Post by riskable on 2010-02-04
Doh!  I forgot to add one of the most important battery savers:  Set vm.swappiness to 10...

```
sudo sysctl -w vm.swappiness=10
```

...and make the change permanent:

```
sudo echo "vm.swappiness=10" >> /etc/sysctl.conf
```

That will reduce the frequency of hard drive spinups considerably by telling the Linux kernel to keep less-frequently-accessed bits in memory instead of swapping them out to disk (as long as possible).  BONUS:  It also improves system performance quite a bit!

---

### Post by Gvorcek48 on 2010-02-06
Just bought 3810TZ one and expecting same problems, seem to be typical for this device.

Wi-fi disconnects and internal mic fixed by installing backport modules, suspend still not working. Subscribing to this thread.

---

### Post by fictivetoast on 2010-02-06
Heya folks - I haven't been keeping up with this thread for a few months, and was hoping that a suspend/resume fix *had finally been found by now*....


The wiki [claims success is possible with a specific 64 bit kernel]("https://help.ubuntu.com/community/AspireTimeline/Fixes")
but someone on launchpad says this is [an isolated success case]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405120").

So, can anyone fill me in?  I've got a 3010t with the su9400 (and haven't bothered updated my bios)... has **any** progress been made since November?

---

### Post by miegiel on 2010-02-06
> **fictivetoast said:**
> Heya folks - I haven't been keeping up with this thread for a few months, and was hoping that a suspend/resume fix *had finally been found by now*....


The wiki [claims success is possible with a specific 64 bit kernel]("https://help.ubuntu.com/community/AspireTimeline/Fixes")
but someone on launchpad says this is [an isolated success case]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405120").

So, can anyone fill me in?  I've got a 3010t with the su9400 (and haven't bothered updated my bios)... has **any** progress been made since November?

My intuition says that "success" was a successful suspend but not a successful wakeup. ;)

Lucid might bring some relief. I'm going to give the alpha a shot when I get my camera (with the SD card) back from my sister (this bum doesn't feel like wasting CDs). But my hopes for a "out of the box" functioning internal mic are higher than my hopes for a functioning suspend/resume.

---

### Post by caelestis2 on 2010-02-08
> **fictivetoast said:**
> Heya folks - I haven't been keeping up with this thread for a few months, and was hoping that a suspend/resume fix *had finally been found by now*....


The wiki [claims success is possible with a specific 64 bit kernel]("https://help.ubuntu.com/community/AspireTimeline/Fixes")
but someone on launchpad says this is [an isolated success case]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405120").

So, can anyone fill me in?  I've got a 3010t with the su9400 (and haven't bothered updated my bios)... has **any** progress been made since November?

The battery life and suspend issues (also the HD playback isnt good in linux) make using linux for me infeasible. :( Who knows how long I will be using windows, but everyone is hoping a solution will come.

---

### Post by Sashin on 2010-02-08
Anyone know how to get brightness working on karmic with the new bios?
It freezes when I try.

---

### Post by tomfool on 2010-02-08
> **caelestis2 said:**
> The battery life and suspend issues (also the HD playback isnt good in linux) make using linux for me infeasible. :( Who knows how long I will be using windows, but everyone is hoping a solution will come.

Well,i can get 8 hrs on battery,and play full-hd in right way,for the suspend it doesn't work yeat.3810t (intel video-card)

---

### Post by fictivetoast on 2010-02-08
> **tomfool said:**
> Well,i can get 8 hrs on battery,and play full-hd in right way,for the suspend it doesn't work yeat.3810t (intel video-card)

+1

I've never had HD playback problems (su9400 dualcore), and even with wireless, a handful of firefox tabs, and banshee all running I get 10,4 watts and 6h40min power estimates - jumps closer to 8 without wireless...

Not being able to suspend is hugely annoying, but thankfully booting is lightning fast for me on koala so it isn't too terrible of a problem.

---

### Post by miegiel on 2010-02-08
> **fictivetoast said:**
> +1

I've never had HD playback problems (su9400 dualcore), and even with wireless, a handful of firefox tabs, and banshee all running I get 10,4 watts and 6h40min power estimates - jumps closer to 8 without wireless...

Not being able to suspend is hugely annoying, but thankfully booting is lightning fast for me on koala so it isn't too terrible of a problem.

HD playback depends highly on the movie. 720p plays without a hitch for me (su9400 with intel graphics), but for 1080p I boot windows and play them in [XBMC]("http://en.wikipedia.org/wiki/XBMC"). Not really surprising since the flow of bits of a 1080p movie is about double that of a 720p movie. The only 720p movies I have trouble with are [AVCHD]("http://en.wikipedia.org/wiki/AVCHD") coded movies from my camera (.MTS files), but I recode those into a more sane format for editing anyway.

VLC and most other players in windows give me the same playback performance as VLC in (x)ubuntu. So there's no real difference between linux and windows for me apart from being able to run the resource friendly XBMC. I love VLC but it is a bit of a resource hog.

---

### Post by Gvorcek48 on 2010-02-08
> **miegiel said:**
> HD playback depends highly on the movie.

Have you tried to use mplayer with VDPAU video output? Works for me.

---

### Post by riskable on 2010-02-08
> **tomfool said:**
> Well,i can get 8 hrs on battery,and play full-hd in right way,for the suspend it doesn't work yeat.3810t (intel video-card)

One of the first tests I performed on the laptop was a full-screen 1080p test.  Every video I threw at it played flawlessly--even when output to an external display.  I'm curious:  What sort of 1080p video you had trouble with?  I've tested h264/AVC (not sure what the bitrate was) and WMV videos up to 8000kbps.  The WMV video ate up about 60+% of one CPU core but it still played without any framerate issues (in SMPlayer which is a front-end for mplayer).

I'm running an SU7300 CPU.  For h264/AVC/MPEG, these videos should be accelerated by the Intel 4500MHD chip and the CPU shouldn't matter.  For WMV and other codecs (e.g. Theora) it must rely on the CPU...  So if you have a slower chip that could explain your issues.

If you're using Flash, well, full-screen 1080p videos only play properly in Flash in Windows.  They don't seem to play well on Macs or Linux no matter how fast the system is.  I've thrown a quad-core at Flash in Linux and it still skips frames.  Point being, Flash sucks.  Download the video in some other format and get over it.

The sooner the web gets rid of Flash for playing video the better off we'll all be.

---

### Post by miegiel on 2010-02-08
> **Gvorcek48 said:**
> Have you tried to use mplayer with VDPAU video output? Works for me.

No, at least I don't think so. I tried mplayer and a bunch of other players, which did perform a bit better than VLC but still not good enough. I'll give VDPAU a shot. Thanks for the tip.

---

### Post by avilella on 2010-02-10
Hi Gvorcek48,

Can I ask you for more details on mplayer with VDPAU? Which version of the packages are you using? Where did you get them from?

I'll write a blog post about it so other people know you made it work,

Cheers,

Albert.

> **Gvorcek48 said:**
> Have you tried to use mplayer with VDPAU video output? Works for me.

---

### Post by Gvorcek48 on 2010-02-10
> **avilella said:**
> 
Can I ask you for more details on mplayer with VDPAU? Which version of the packages are you using? Where did you get them from?


As i've understand from [Wikipedia]("http://en.wikipedia.org/wiki/VDPAU#NVIDIA_VDPAU_Feature_Sets"), vdpau implements hardware video decoding features. 

I'm not sure if it really works in mplayer, but i can watch 1080p videos with my **MPlayer SVN-r29237-4.4.1** without any problems and framedrops. You can try it by playing your video with "mplayer -vo vdpau <filename>" and gathering information from **top** shell command.

---

### Post by jimmy the saint on 2010-02-14
Just discovered something by accident and thought I'd share.

When installing Ubuntu REMOVE ALL HARDWARE possible.  I did a fresh installation because I redid the partitions and it was just easier than preserving a rarely used installation.  I had a wireless usb mouse attached during the installation.  That issue with the touchpad going bonkers was there in the new installation, whereas it had never been there in the old.

I read somewhere about someone fixing the bonkers mousepad by changing the order that the input devices were recognized, as it only happened when he booted with USB mouse attached.  I decided to run the experiment. It worked.

If your touchpad is hypersensitive and goes insane if two fingers are in the same zipcode, attempt a reinstallation with no other mouse device attached.  It should solf the issue once and for all.  The sympotms are that your mouse jumps around continuously for as long as your fingers are near, clicking on everything and wreaking havoc.  It is not the single jump we all experience when removing a finger. Imagine that 1000/sec continuously.

---

### Post by tedrampart on 2010-02-16
I have an 1810T, and the only issue I have is the jumping mouse problem.  However, I never had anything other than the SD card I was installing from plugged in.  I tried adding an xorg.conf file will minspeed and jumpycursorthreshold, as well as installing gsynaptics..

now I'm playing with fdi file that someone posted about earlier, and we'll see how that works.

it seems like the touchpad settings are reverted when suspend/resume.. but then it also seems like it goes crazy when the system heats up (I notice it mostly after watching a couple eps of top gear on megavideo the last couple days).  

I'm unsure how removing the backup partition would create this problem, especially if people are swapping out the hdd for an ssd.  

I'll try to post back about this later after I've tested the fdi hack a bit more.  Does anyone else have any other ideas on what to try if it doesn't work?

---

### Post by caelestis2 on 2010-02-16
> **jimmy the saint said:**
> Just discovered something by accident and thought I'd share.

When installing Ubuntu REMOVE ALL HARDWARE possible.  I did a fresh installation because I redid the partitions and it was just easier than preserving a rarely used installation.  I had a wireless usb mouse attached during the installation.  That issue with the touchpad going bonkers was there in the new installation, whereas it had never been there in the old.

I read somewhere about someone fixing the bonkers mousepad by changing the order that the input devices were recognized, as it only happened when he booted with USB mouse attached.  I decided to run the experiment. It worked.

If your touchpad is hypersensitive and goes insane if two fingers are in the same zipcode, attempt a reinstallation with no other mouse device attached.  It should solf the issue once and for all.  The sympotms are that your mouse jumps around continuously for as long as your fingers are near, clicking on everything and wreaking havoc.  It is not the single jump we all experience when removing a finger. Imagine that 1000/sec continuously.


Finally I someone addresses the problem that's been driving me insane! I'm curious though, I use KDE and arch linux now, how would I change the input device order? The touchpad works every once in a blue moon, but when I restart, it goes crazy.

---

### Post by tedrampart on 2010-02-17
> **caelestis2 said:**
> Finally I someone addresses the problem that's been driving me insane! I'm curious though, I use KDE and arch linux now, how would I change the input device order? The touchpad works every once in a blue moon, but when I restart, it goes crazy.

yes this is an interesting suggestion.  I'd like to know more about this too.. the fdi file I tried worked a bit, until the device heats up, then it goes bonkers.  so maybe changing order of devices would help me too.

---

### Post by miegiel on 2010-02-17
> **avilella said:**
> Hi Gvorcek48,

Can I ask you for more details on mplayer with VDPAU? Which version of the packages are you using? Where did you get them from?

I'll write a blog post about it so other people know you made it work,

Cheers,

Albert.

```
user@machine:~$ **mplayer [COLOR="Blue"]-vo vdpau[/COLOR] Videos/MIR20091027_350kb.mp4** 
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Videos/MIR20091027_350kb.mp4.
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [avc1]  400x300  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 name: Exclusive Interview with Hamas Leader Khaled Meshal
[vdpau] Could not open dynamic library libvdpau.so.1
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
[pulse] working around probably broken pause functionality,
        see http://www.pulseaudio.org/ticket/440
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   4.3 (04.2) of 1468.8 (24:28.7)  0.6% 
Exiting... (Quit)
```
(*Videos/MIR20091027_350kb.mp4* was just je 1st video file I stumbled upon in the *Videos* dir to use as an exalmple)

But as you can read, I got audio but no video output (I do get video if I omit the *-vo vdpau* switch). From what I've read *vdpau* is nvidia's technology to accelerate video playback in the graphics chip, though they did open the technology for other graphics chip manufactures. When digging into the matter, I also found that lucid (ubuntu 10.4) will come with more *vpdau* support than karmic. But I still didn't get around to giving lucid's alpha a test run.

Regarding the **touchpad issue on the 1810T**; You'd expect a heat issue to be a hardware issue and that it would bug windows users too. Maybe you can find something on a hardware geek forum like [[H]ard|Forum]("http://www.hardforum.com/index.php"). (Just my 2ct, I've got the 3810T.)

---

### Post by tedrampart on 2010-02-23
seems it wasnn't the heat that was causing the wonky mouse.. it was actually from installing gsynaptics.  None of the settings were honoured in the program and perhaps it conflicted with something.  Regardless, I removed gsynaptics, and went back to the regular mouse settings, and boingo boingo, its working great consistantly.

---

### Post by within on 2010-02-23
Hi there,

I follow this topic for a long time now, and I want to thank the contributors.

About the Skype and PulseAudio issue (mic sound), here is maybe some fix and steps to follow to make it work. I haven't found the time yet to do this, but I will:

[PulseAudio: unleash Skype at last?]("http://pulseaudio.org/wiki/PerfectSetup#Skype")

Finally, I did start a Blog to present my Acer TimeLine laptop and Ubuntu with it. It is just a start, but I plan to add to more to bring some interesting info about what I did and how it works:

[http://thierrite.blogspot.com/]("http://thierrite.blogspot.com/")

Don't hesitate to offer some comments.

Cheers

---

### Post by Gvorcek48 on 2010-02-24
> **within said:**
> Hi there,
About the Skype and PulseAudio issue (mic sound), here is maybe some fix and steps to follow to make it work. I haven't found the time yet to do this, but I will:

I've installed backport kernel modules:

linux-backports-modules-alsa-2.6.31-19-generic

and after that in alsa-mixer i've adjusted capture level of left (by pressing Z) to zero and increased right to maximum by pressing E. That was helpfull.

---

### Post by within on 2010-02-25
Thanks Gvorcek48 for this tip, happy it was helpfull for you.

I did find a way of using ALSA in skype and it works great. I gathered some information, and here there are:

1st, I did follow the steps given by **Notselfcreated** here:
[http://ubuntuforums.org/showpost.php?p=8289899&postcount=9](http://ubuntuforums.org/showpost.php?p=8289899&postcount=9)

# Installed padevchooser 
```
apt-get install padevchooser
``` it did install few other things
# Unchecked all "Mute" options and checked "Record" in the mixer settings and sound settings.
# Tested with default "Sound Recorder" (it works fine there).
# Installed linux-backports-modules-alsa-karmic-generic
# Set all volume options to max.
# Unchecked "Allow Skype to control... etc. etc." in the Skype options.

2nd, I did launch skype in using ALSA (in fact, it fails launching PulseAudio, so t swich to Alsa insted) as **blackest_knight** said:
[http://ubuntuforums.org/showpost.php?p=8483092&postcount=15](http://ubuntuforums.org/showpost.php?p=8483092&postcount=15)

In System --> Preferences --> Main Menu

edit the properties of skype and replace in Command **skype** by **/bin/sh -c "PULSE_SERVER=127.0.0.1 skype"**


When launching skype, you can make a test call and you will see you can finally record your own voice and can call people!!!!!!!!!

---

### Post by Sashin on 2010-02-26
anyone know how to get two finger scrolling on lucid (it no longer has hal).

Also brightness still doesn't work on the 4810T.

---

### Post by within on 2010-02-26
Since I've booted my laptop and logged in, my fan is running all the time. Even if the sound is not high, I am afraid after some months of usage it will get worse. 
This also reflects some supposed issue with proper power control (I use 99% of the time AC power, not battery).
I've read **riskable** posts and plan to modify things to get lower power usage, but I am not sure it will completely solve this. Indeed, it seems no one here speaks about what I call a 'fan issue'...

*Question:* What to do to make the laptop more silent and keeping it cold?

Right now, I have with **sensors** command:
```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +26.8°C  (crit = +127.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +43.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +42.0°C  (high = +100.0°C, crit = +100.0°C)  

```

and with **acpi -ac** command I get:
```
Adapter 0: on-line
Cooling 0: LCD 3 of 9
Cooling 1: Processor 0 of 10
Cooling 2: Processor 0 of 10

```
By the way, I run Ubuntu 9.10 32-bit Karmic Koala on a Acer TimeLine AS3810TZG-413G32n model, with ATI card with PowerPlay feature on, set as 'maximum battery'.

---

### Post by miegiel on 2010-02-26
> **Sashin said:**
> anyone know how to get two finger scrolling on lucid (it no longer has hal).

Also brightness still doesn't work on the 4810T.

Make a .fdi file.

[Here's a post]("http://ubuntuforums.org/showthread.php?p=7978911#post7978911") on my 1st fdi adventure. There's also info at [Ubuntu Documentation > Ubuntu on the Acer Timeline laptops]("https://help.ubuntu.com/community/AspireTimeline")

My cuernt .fdi file :
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
<!-- external mouse
  <device>
     <match key="info.capabilities" contains="input.mouse">
        <merge key="input.x11_driver" type="string">mouse</merge>
        <match key="/org/freedesktop/Hal/devices/computer:system.kernel.name" string="Linux">
           <merge key="input.x11_driver" type="string">evdev</merge>
           <merge key="input.x11_options.Emulate3Buttons" type="string">false</merge>
           <merge key="input.x11_options.ButtonMapping" type="string">2 1 3</merge>
        </match>
     </match>
  </device>
-->
  <device>
     <match key="info.capabilities" contains="input.touchpad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
<!-- 
           DON'T USE SHMConfig (unless you must, for example to run 'synclient -m 10'),
           obsolete (in karmic and later at least) and a security risk.
        <merge key="input.x11_options.SHMConfig" type="string">On</merge> -->
<!-- 
           The following is an example of swapping buttons on the Synaptics
           TouchPadthat DOESN'T WORK anymore. See the end of 'man synaptics'
        <merge key="input.x11_options.Buttons" type="string">3</merge>
        <merge key="input.x11_options.ButtonMapping" type="string">2 1 3</merge>

           NOTES :
        <merge key="input.x11_options.RTCornerButton" type="string">0</merge>          disable tap-right-top-corner button
        <merge key="input.x11_options.LTCornerButton" type="string">0</merge>          disable tap-left-top-corner button
        <merge key="input.x11_options.LBCornerButton" type="string">0</merge>          disable tap-left-bottom-corner button
        <merge key="input.x11_options.ClickFinger1" type="string">1</merge>            For pads that support true multitouch
        <merge key="input.x11_options.ClickFinger2" type="string">3</merge>            For pads that support true multitouch
        <merge key="input.x11_options.ClickFinger3" type="string">2</merge>            For pads that support true multitouch
-->
[COLOR="Red"]        <merge key="input.x11_options.TapButton1" type="string">2</merge>              <!-- set tap-click to middle mouse button, run 'xinput set-button-map "SynPS/2 Synaptics TouchPad" 2 1 3' to swap buttons 1 and 2. This gives you middle click on the left button and left click on tap. -->[/COLOR]
        <merge key="input.x11_options.TapButton2" type="string">0</merge>              <!-- disable 2 finger tap-click, 2 finger tap-click to menu = 3 -->
        <merge key="input.x11_options.TapButton3" type="string">0</merge>              <!-- disable 3 finger tap-click -->
        <merge key="input.x11_options.RBCornerButton" type="string">0</merge>          <!-- disable tap-right-bottom-corner button (is on by default on my machine) -->
        <merge key="input.x11_options.VertEdgeScroll" type="string">0</merge>          <!-- disable edge scrolling -->
        <merge key="input.x11_options.EmulateMidButtonTime" type="string">0</merge>    <!-- effectivelly disable middle button emmulation -->
        <merge key="input.x11_options.EmulateTwoFingerMinZ" type="string">4</merge>    <!-- set 2 finger emulation presure -->
        <merge key="input.x11_options.EmulateTwoFingerMinW" type="string">7</merge>    <!-- set 2 finger emulation pinch width -->
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>     <!-- enable 2 finger scrolling -->
        <merge key="input.x11_options.JumpyCursorThreshold" type="string">150</merge>  <!-- stabilize 2 finger tapping and 2 finger scrolling -->
        <merge key="input.x11_options.MaxDoubleTapTime" type="string">50</merge>
     </match>
  </device>
</deviceinfo>
```
[COLOR="Red"]Beware[/COLOR] of the left button a middle mouse botton swap !!!

ps. Stuff between *<!--* and *-->* are notes.

Hmm wait, **lucid** (must read better ](*,)). This doesn't work in lucid anymore !?

---

### Post by Sashin on 2010-02-26
It doesn't seem to, I've tried. Hal seems to be 100% gone.

---

### Post by miegiel on 2010-02-26
> **Sashin said:**
> It doesn't seem to, I've tried. Hal seems to be 100% gone.

That's bad news (for me anyway).

Maybe you can find info or help in the [Lucid Lynx Testing and Discussion]("http://ubuntuforums.org/forumdisplay.php?f=377") sub-forum.

---

### Post by acermobile on 2010-03-01
Hey everyone.

Bad news: The backlit of my laptop ceased on Friday. I will send the notebook for a (hopefully quickly done) repair - they announced it to take 5-7 days... Since the laptop has been (carefully) used for just about 3 month I am greatly disappointed. My previous MSI book had the same failerure after almost 4 years and abusive use (thousands of lid open/close-procedures). Cross your fingers...

---

### Post by miegiel on 2010-03-01
> **acermobile said:**
> Hey everyone.

Bad news: The backlit of my laptop ceased on Friday. I will send the notebook for a (hopefully quickly done) repair - they announced it to take 5-7 days... Since the laptop has been (carefully) used for just about 3 month I am greatly disappointed. My previous MSI book had the same failerure after almost 4 years and abusive use (thousands of lid open/close-procedures). Cross your fingers...

Does it look like this (see attachment)? That's the botom edge of my screen, a bit left of center (3810T). I made my desktop white, you can't see it that well when it's black.

In the past month or 2 it sometimes would go off if I carried the laptop holding it at the battery, but it would always come on again. But now it's been off for about a week. I think it's a loose contact. It's not annoying me that much anymore. But that might be because I went to the dentist last week. There are always worse things that can happen.

Anyway, I think I've said it before in this thread, I'm never ever ever buying an acer again.

---

### Post by acermobile on 2010-03-01
My entire screen is carbon black.If there is enough diffuse light, then the reflections suffice to view parts of the screen (need good eyes though). I had exactly the same on my previous notebook in which a cable running through the hinges broke. I "repaired" the old notebook and kept on using it for another 8 months or though (currently writing on it actually), but it was time for a new one after more than 4 years...

Now it appears that 3 month can also eliminate the backlight (has to be a loose contact or something, but i tried everything possible without having to open the device - nothing helped).

Has anyone else had product failure on this notebook? I am also keen to see the response time - package sent this morning...

---

### Post by jpgv on 2010-03-01
Yes, this happened to me a couple weeks ago:

> **acermobile said:**
> My entire screen is carbon black.If there is enough diffuse light, then the reflections suffice to view parts of the screen (need good eyes though). I had exactly the same on my previous notebook in which a cable running through the hinges broke. I "repaired" the old notebook and kept on using it for another 8 months or though (currently writing on it actually), but it was time for a new one after more than 4 years...

Now it appears that 3 month can also eliminate the backlight (has to be a loose contact or something, but i tried everything possible without having to open the device - nothing helped).

Has anyone else had product failure on this notebook? I am also keen to see the response time - package sent this morning...

I fact, it began as a flicker when I held the laptop in a certain way, but the backlit eventually died.  I just sent it in and they replaced the whole screen.  The response time must vary in different countries.  In Colombia, it took three days to 'diagnose' and one day to replace the screen.

---

### Post by acermobile on 2010-03-02
Now I am scared. If there are already two of these failures observed by visitors of this thread, then what happens next? Will we have to send in the computer every once in a while till the warranty time runs out and then trash the thing (I do not need an ultralight notebook with ca. 7 h battery life when I am obliged to use an external display...)? Never ever am I going to buy an ACER product again...

The 5 days are promising though.

---

### Post by miegiel on 2010-03-02
> **Sashin said:**
> anyone know how to get two finger scrolling on lucid (it no longer has hal).

I started [a thread on this in the Lucid subforum]("http://ubuntuforums.org/showthread.php?t=1419833").

---

### Post by almozavr on 2010-03-03
Hi.

I wonder if someone tried 2.6.33 kernel on Acer 3810t? Did it solve the suspend problem or it still remains? Tnx

---

### Post by miegiel on 2010-03-05
Two finger, twofinger, 2finger scrolling script for ubuntu lucid 10.04 :D

As > **Sashin said:**
> anyone know how to get two finger scrolling on lucid ... already discovered. You can't use the *.fdi* file in */etc/hal/fdi/policy/* to simulate two finger scrolling in lucid anymore.

No worries, in lucid you only need to run a script and make the script auto run in *Settings >> Sessions and Startup* so that it runs when X starts. Enjoy!

**touchpad.sh**
```
#!/bin/bash
#
# list of synaptics device properties http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html#sect4
# list  current synaptics device properties: xinput list-props '"SynPS/2 Synaptics TouchPad"'
#
xinput --set-prop --type=int --format=32 '"SynPS/2 Synaptics TouchPad"' "Synaptics Two-Finger Pressure" 4
xinput --set-prop --type=int --format=32 '"SynPS/2 Synaptics TouchPad"' "Synaptics Two-Finger Width" 7         # Below width 1 finger touch, above width simulate 2 finger touch. - value=pad-pixels
xinput --set-prop --type=int --format=8  '"SynPS/2 Synaptics TouchPad"' "Synaptics Two-Finger Scrolling" 1 1   # vertical scrolling, horizontal scrolling - values: 0=disable 1=enable
xinput --set-prop --type=int --format=8  '"SynPS/2 Synaptics TouchPad"' "Synaptics Edge Scrolling" 0 0 0       # vertical, horizontal, corner - values: 0=disable  1=enable
xinput --set-prop --type=int --format=32 '"SynPS/2 Synaptics TouchPad"' "Synaptics Jumpy Cursor Threshold" 250 # stabilize 2 finger actions - value=pad-pixels
xinput --set-prop --type=int --format=8  '"SynPS/2 Synaptics TouchPad"' "Synaptics Tap Action" 0 0 0 0 1 2 0   # pad corners rt rb lt lb tap fingers 1 2 3 (can't simulate more then 2 tap fingers AFAIK) - values: 0=disable 1=left 2=middle 3=right etc. (in FF 8=back 9=forward)
exit
```

**run as:**
```
sh touchpad.sh
```
Who knows, it might even work in karmic. :-k

---

### Post by miegiel on 2010-03-05
> **almozavr said:**
> Hi.

I wonder if someone tried 2.6.33 kernel on Acer 3810t? Did it solve the suspend problem or it still remains? Tnx

In [https://launchpad.net/~acertimeline](https://launchpad.net/~acertimeline) some people are kind of putting a bounty together. Do you know anyone who understands this [DSDT stuff]("http://ubuntuforums.org/showthread.php?t=1036051"), it's a bit beyond me. :|

---

### Post by jimmy the saint on 2010-03-05
> **miegiel said:**
> In [https://launchpad.net/~acertimeline](https://launchpad.net/~acertimeline) some people are kind of putting a bounty together. Do you know anyone who understands this [DSDT stuff]("http://ubuntuforums.org/showthread.php?t=1036051"), it's a bit beyond me. :|

I wrote the email about putting a bounty together.  The response was pretty promising.  I have absolutely no idea how to start a bounty.  I have been looking at some freelance programming sites but most of them seem to require that you "hire" a programmer.  I was thinking more of a "hey everyone, whoever brings us the solution first gets this cash bounty" model.  If anyone knows anything about software bounties I would sure appreciate the input/help.  

Currently I am thinking about creating a small site with a paypal link or some kind of escrow service.  It would be nice if the money could be paid in and held for a year or so then returned to the person who donated it if the problem is never solved.  Anyway, if you have a thought, go ahead and send me a PM.

JTS

---

### Post by Sashin on 2010-03-05
so no one knows how to fix the brightness problem on 4810t without sacrificing kernel mode setting?

---

### Post by Arlanthir on 2010-03-06
> **Sashin said:**
> so no one knows how to fix the brightness problem on 4810t without sacrificing kernel mode setting?

There's a script that needs sudo and changes the maximum value of brightness, effectively changing the current value.
It works with KMS, I think, if you don't mind assigning it to a different shortcut and providing your password every time you want to change the brightness.

```

#!/bin/bash

function getAddr {
        ADDR=`lspci | grep VGA | cut -d' ' -f1`
}

function getBL {
        CURR=`sudo setpci -s $ADDR F4.B`
}

function setBL {
        sudo setpci -s $ADDR F4.B=$1
}

function toDec {
        DEC=`printf "%d" 0x${1}`
}

function toHex {
        HEX=`printf "%02x\n" ${1}`
}

function inc {
        NEWVAL=`expr $1 + 10`
        if [ $NEWVAL -gt 255 ]
        then
                NEWVAL=255
        fi
}

function dec {
        NEWVAL=`expr $1 - 10`
        if [ $NEWVAL -lt 0 ]
        then
                NEWVAL=0
        fi
}

getAddr
getBL
toDec $CURR
case $1 in
        up)
                inc $DEC
                ;;
        down)
                dec $DEC
                ;;
        *)
                echo "Usage: backlightControl.sh (up|down)"
                exit -1
                ;;
esac
toHex $NEWVAL
setBL $HEX 

exit 0
```

If you're assigning it to shortcuts, remember to write:
```
gksu /home/USER/backlight.sh up
gksu /home/USER/backlight.sh down
```

I tried this and it worked :)
I set it to Super (windows key) + Left/Right, so it's right next to Fn anyway.

---

### Post by within on 2010-03-07
Hi,

I was looking for some information about the HD installed in my laptop model:

It is a Western Digital Model WDC WD3200BEVT-22ZCT0; among the specifications, I can read it has NCQ (Native Command Queuing) capability.

Thus, if you use IDE or even AHCI but in setting "libata.force=noncq", performances will be drastically reduced.

Anyone knows how to be sure NCQ is not disabled?

Since Kernel 2.6.18, NCQ is natively supported, as I could read from wikipedia: 
> For NCQ to be enabled, it must be supported and enabled in the SATA host bus adapter and in the hard drive itself. The appropriate driver must be loaded into the operating system to enable NCQ on the host bus adapter. Many newer chipsets support the Advanced Host Controller Interface (AHCI), which should allow a generic driver supplied by the operating system to control them and enable NCQ. In fact, newer mainstream Linux kernels support AHCI natively

Then, the good question is: Does the SATA chipset on this laptop supports NCQ?

---

### Post by Sashin on 2010-03-07
> **Arlanthir said:**
> There's a script that needs sudo and changes the maximum value of brightness, effectively changing the current value.
It works with KMS, I think, if you don't mind assigning it to a different shortcut and providing your password every time you want to change the brightness.

```

#!/bin/bash

function getAddr {
        ADDR=`lspci | grep VGA | cut -d' ' -f1`
}

function getBL {
        CURR=`sudo setpci -s $ADDR F4.B`
}

function setBL {
        sudo setpci -s $ADDR F4.B=$1
}

function toDec {
        DEC=`printf "%d" 0x${1}`
}

function toHex {
        HEX=`printf "%02x\n" ${1}`
}

function inc {
        NEWVAL=`expr $1 + 10`
        if [ $NEWVAL -gt 255 ]
        then
                NEWVAL=255
        fi
}

function dec {
        NEWVAL=`expr $1 - 10`
        if [ $NEWVAL -lt 0 ]
        then
                NEWVAL=0
        fi
}

getAddr
getBL
toDec $CURR
case $1 in
        up)
                inc $DEC
                ;;
        down)
                dec $DEC
                ;;
        *)
                echo "Usage: backlightControl.sh (up|down)"
                exit -1
                ;;
esac
toHex $NEWVAL
setBL $HEX 

exit 0
```

If you're assigning it to shortcuts, remember to write:
```
gksu /home/USER/backlight.sh up
gksu /home/USER/backlight.sh down
```

I tried this and it worked :)
I set it to Super (windows key) + Left/Right, so it's right next to Fn anyway.

This script doesn't seem to work for me, but I'm using lucid.

---

### Post by Arlanthir on 2010-03-07
> **Sashin said:**
> This script doesn't seem to work for me, but I'm using lucid.

I'll try it on a daily live iso ;)

---

### Post by miegiel on 2010-03-07
> **within said:**
> ...

Then, the good question is: Does the SATA chipset on this laptop supports NCQ?

Yes, as long as you don't disable it in the BIOS.

---

### Post by Arlanthir on 2010-03-07
> **Sashin said:**
> This script doesn't seem to work for me, but I'm using lucid.

Tried it on a daily iso and it worked just fine, I'm afraid.
Do you get any error messages? You have to repeat the command (eg. ./backlight.sh down) some times to notice a difference.

---

### Post by chrisjsmith on 2010-03-07
New 3810TZ user here trying 9.10 32-bit.  I will post back later with problems/solutions if I have anything useful to add.

---

### Post by chrisjsmith on 2010-03-07
> **chrisjsmith said:**
> New 3810TZ user here trying 9.10 32-bit.  I will post back later with problems/solutions if I have anything useful to add.

Ok status update:

**WORKS:**

Video.  Sound.  Flash (smoothly).  All USB ports.  All perfectly.

**Doesn't work:**

Wireless.  It sucks.  If I could get a connection, it wasn't stable and managed to top out at ~ 1Mbit.

Fan.  Constantly stuck on.  I've never heard the fan before until I booted Ubuntu live.

**Untested:**

Touch pad on/off.  WLAN on/off.  Flash reader.

Bored with it already.  Decided to carry on using Ubuntu server inside VMware on Windows 7 for now rather than hosting my dev environment on Ubuntu Desktop.

---

### Post by within on 2010-03-07
> **miegiel said:**
> Yes, as long as you don't disable it in the BIOS.

good, but why my system response is soooooooooooo low?

1st, booting time takes ages (my HD is dedictaed to Linux, no more windows), about 58 seconds to get to the login window, then almost 15 seconds to reach the desktop.

2nd, installed system should be optimized as I followed some advices for it:
    * /             10240 MB (10 GB)
    * /boot          1024 MB (1 GB)
    * /swap         2048 MB (2 GB)*
    * /usr         20480 MB (20 GB)
    * /var         10240 MB (10 GB)
    * /tmp           5120 MB (5 GB)
    * /usr/local    5120 MB (5 GB)
    * /home        available left space

3rd, Nautilus or Firefox for examples take also ages to show up... (at least 2 seconds for Nautilus, and 8~9 seconds for Firefox)

why the OS is not responsive as it should be? I really thought it could be related to the HD, as everything else damn fast compared to my 2 other laptops with Ubuntu, but this one is much slower than others...

If anyone has an idea...

---

### Post by miegiel on 2010-03-07
> **within said:**
> good, but why my system response is soooooooooooo low?

1st, booting time takes ages (my HD is dedictaed to Linux, no more windows)

2nd, installed system should be optimized as I followed some advices for it:
    * /             10240 MB (10 GB)
    * /boot          1024 MB (1 GB)
    * /swap         2048 MB (2 GB)*
    * /usr         20480 MB (20 GB)
    * /var         10240 MB (10 GB)
    * /tmp           5120 MB (5 GB)
    * /usr/local    5120 MB (5 GB)
    * /home        available left space

3rd, Nautilus or Firefox for examples take also ages to show up... (at east 1 second for Nautilus, and 3~4 seconds for Firefox)

why the OS is not responsive as it should be? I really thought it could be related to the HD, as everything else damn fast compared to my 2 other laptops with Ubuntu, but this one is much slower than others...

If anyone has an idea...

Using IDE mode shouldn't make your laptop slow either, AHCI with NCQ just make it a bit faster. Try this to check your disk speed :
```
user@machine:~$ sudo hdparm -t /dev/sda

/dev/sda:
 Timing buffered disk reads:  212 MB in  3.02 seconds =  70.20 MB/sec
user@machine:~$ sudo hdparm -T /dev/sda

/dev/sda:
 Timing cached reads:   2374 MB in  2.00 seconds = 1188.25 MB/sec
```

*3810T with 320GB WDC WD3200BJKT-0*

---

### Post by within on 2010-03-08
Thanks **miegiel**,

here is what I get for my Western Digital Model WDC WD3200BEVT-22ZCT0:

```
thierrite@thierrite-laptop:~$ sudo hdparm -t /dev/sda

/dev/sda:
 Timing buffered disk reads:  178 MB in  3.02 seconds =  58.84 MB/sec
thierrite@thierrite-laptop:~$ sudo hdparm -T /dev/sda

/dev/sda:
 Timing cached reads:   2082 MB in  2.00 seconds = 1042.28 MB/sec

```

According to what you say, I don't think now the slow response speed is related to the HD... but what else?

---

### Post by acermobile on 2010-03-10
I received my Timeline back yesterday after 8 days from shipping. The LCD Screen has been replaced and the laptop is back to work. The actual repair was already finished Friday morning (according to the web tracking). However, the box did not get back to me until Tuesday via UPS.

In addition, the e-mail from acer stating that the box is on its way said something about a UPS tracking number - which was not present at all?!?!?

After having heard quite a lot of bad things about the customer service I can say that the repair went very smooth and with small administrative hassle.

Wonder when it will break, again...

---

### Post by executorvs on 2010-03-11
I'm trying to draw more attention to the brightness bug on launchpad as it also affects most timeline models and I suspect a few of the other Aspire series as well.

there is a bug report at [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/446717](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/446717)

I have marked as duplicates all of the bugs related to the changes in how the brightness keys have failed over time that I am aware of.

if anyone with either a 3810(TZ/TG) or 4810(TZ/TG) or 5810TG could post exact details of how this bug affects there computer under lucid it would be appreciated.

---

### Post by miegiel on 2010-03-11
```
https://bugs.launchpad.net/ubuntu/+s...el/+bug/446717
```
is not the whole url

here it is ;)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/446717](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/446717)

---

### Post by executorvs on 2010-03-11
oops.

---

### Post by chucktastic on 2010-03-18
I did search a bit but can not find any mention of the problem I am having.  

I have a Acer Timeline 3810TZ

I just switched from Win7 to ubuntu and all went well except for the intermittent wifi issues.  

On reboot it will work fine, find my router, connect and allow for firefox to work just fine.  If I just surf the webs for a little while its fine, but after a while it will drop the connection followed by not seeing the wireless card any longer.  

It drops even faster if say I run the update manager it wont even get though half the download process.  

Wireless router is located in same room that I am trying to get on line.  When a hardline is run to the computer it work perfectly with no problems.

Really don't want to go back to Win7, but will have to if I cant figure out why the wifi is flaky.  

Oh yea, on reboot it works fine, if I put it to sleep and wake it up....it works just fine again.

Thanks for any tips, tricks or ideas to fix this problem.

---

### Post by jimmy the saint on 2010-03-18
My personal experience has been that disabling N connections at the router level solved my connectivity issues.  G connections work great in my experience.  I am not sure if there is a better driver in the backports repo, but for internet connections, G speeds are fine and disabling N is far easier (in my opinion) than messing around with finding better drivers.

> **chucktastic said:**
> I did search a bit but can not find any mention of the problem I am having.  

I have a Acer Timeline 3810TZ

I just switched from Win7 to ubuntu and all went well except for the intermittent wifi issues.  

On reboot it will work fine, find my router, connect and allow for firefox to work just fine.  If I just surf the webs for a little while its fine, but after a while it will drop the connection followed by not seeing the wireless card any longer.  

It drops even faster if say I run the update manager it wont even get though half the download process.  

Wireless router is located in same room that I am trying to get on line.  When a hardline is run to the computer it work perfectly with no problems.

Really don't want to go back to Win7, but will have to if I cant figure out why the wifi is flaky.  

Oh yea, on reboot it works fine, if I put it to sleep and wake it up....it works just fine again.

Thanks for any tips, tricks or ideas to fix this problem.

---

### Post by executorvs on 2010-03-18
I had a similar problem in 9.10, especially with WDS networks on campus. This problem is not an issue for me in lucid. I would say you should see if the beta live disc runs on your computer without too much issue and if things go well upgrade now.

---

### Post by megaexception on 2010-03-19
please, can someone confirm that internal mic on 3810T is working after alsa update (1.0.21a or backports-modules-alsa)?

on older alsa, i was able to get external mic working without any efforts.
but after alsa update i cannot unmute mic or choose internal/external mic, because there is no such control in alsa mixer or any other mixer i've tried.

---

### Post by megaexception on 2010-03-20
just updated bios to 1.20. on first look, nothing has changed.

but, when i modprobe kvm and kvm_intel, and launch kvm - everything is working and i do not receive any complains about VT support:


```

# cat /proc/cpuinfo | grep -o vmx
vmx
# modprobe kvm kvm_intel
<nothing here>
# dmesg | grep kvm
<nothing here>
# kvm -monitor stdio                                                                                                                                            QEMU 0.12.50 monitor - type 'help' for more information
(qemu) info kvm
kvm support: enabled
(qemu) 




```


it's look like in bios 1.20, acer silently enabled virtualization :)

---

### Post by megaexception on 2010-03-20
just updated bios to 1.20. on first look, nothing has changed.

but, when i modprobe kvm and kvm_intel, and launch kvm - everything is working and i do not receive any complains about VT support:


```

# cat /proc/cpuinfo | grep -o vmx
vmx
# modprobe kvm kvm_intel
<nothing here>
# dmesg | grep kvm
<nothing here>
# kvm -monitor stdio                                                                                                                                            QEMU 0.12.50 monitor - type 'help' for more information
(qemu) info kvm
**kvm support: enabled**
(qemu) 




```


it's look like in bios 1.20, acer silently enabled virtualization :)

---

### Post by jacktow on 2010-03-23
See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405120/comments/94]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405120/comments/94") for possible fix for suspend issue.

---

### Post by miegiel on 2010-03-23
> **jacktow said:**
> See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405120/comments/94]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405120/comments/94") for possible fix for suspend issue.

Works here \\:D/


```
gksudo gedit /etc/default/grub
```
edit the line :
```
GRUB_CMDLINE_LINUX="[COLOR="Blue"]i8042.reset=1[/COLOR]"
```
You can also edit the *GRUB_CMDLINE_LINUX_DEFAULT="[COLOR="Blue"]i8042.reset=1[/COLOR]  quiet splash"* line, but it will only change the default boot option and not the recovery and old kernel options in the grub menu.
```
sudo update-grub
```
And reboot

---

### Post by mr bob on 2010-03-23
OH MY GOD!!!!! YES! YES! YES! YES! YES! YES!!!

:popcorn: :KS :KS :KS

**Suspend works!** We'll be dancing on the streets of Linux-Acer 3810t tonight.

I'm using Mint with 2.6.31-20 and BIOS 1.17 but it sounds like it is a fix for all of us.

Thank you.

---

### Post by federa on 2010-03-23
seems no progress are be done since the bios 1.00..
i'm running lucid 64-bit, kernel 2.6.32-16-generic and bios 1.00 on acer timeline 3810t core2duo su9400: everything work correctly (brightness, wifi, special keys, sounds), of course there's the exception of suspend/resume (but this is a kind of sorcery :)) and the fans are little bit noisy (but nothing incredible..sometimes they spin up and sometimes down...kind of normal I suppose).
two questions: 
1. is it so important to upgrade the bios?? 
2. is flashing the bios safe?? 
i'm so afraid about flashing it... :)

thanks!

---

### Post by federa on 2010-03-23
> **mr bob said:**
> OH MY GOD!!!!! YES! YES! YES! YES! YES! YES!!!

:popcorn: :KS :KS :KS

**Suspend works!** We'll be dancing on the streets of Linux-Acer 3810t tonight.

I'm using Mint with 2.6.31-20 and BIOS 1.17 but it sounds like it is a fix for all of us.

Thank you.

jeez..!!! let's go get party together because it's work also on mine acer!!!!!! wow!!
thanks to the saint who fixed this problem!!!

---

### Post by iceman on 2010-03-23
Can't believe solution was so easy... a string in cmdline, passed to kernel...
We waited an year for this solution!! Damn you Acer!!
Now my 3810 suspend right!
Amazing... now it's really perfect this machine!

---

### Post by federa on 2010-03-24
basically in my 3810T still there some problems with the suspend stuff..but probably is because i'm using lucid and a lots of PPA..
anyway, when i close the lid the system seems to start the suspend but it doesn't..so i have to use the "disconnect" menu (i'm using also the gnome shell) to suspend.
yesterday the resuming after suspend was successfully but the desktop was blocked: i was able to move the mouse but not to click on anything...
mysterious of the faith probably.. :D

---

### Post by bruderjakob on 2010-03-25
> **federa said:**
> basically in my 3810T still there some problems with the suspend stuff..but probably is because i'm using lucid and a lots of PPA..
anyway, when i close the lid the system seems to start the suspend but it doesn't..so i have to use the "disconnect" menu (i'm using also the gnome shell) to suspend.
yesterday the resuming after suspend was successfully but the desktop was blocked: i was able to move the mouse but not to click on anything...
mysterious of the faith probably.. :D

seems not to be related to lucid (because here it works for me, also some PPAs including xorg edgers), but i've also some issues with "display detection" sometimes it seems that it recognizes a second screen, when i make an screenshot i can see an expanded area on the left which isn't visible normally (sorry, it's hard to describe in english for me), also i can move the mouse cursor in this invisible "nirvana" ;) that's bad because i have some compiz features on the edges normally and the edge is somewhere down left where i can't visibly move the cursor on.
i've caught some strange output in /var/log/messages, something about TV and NTSC :-s

PS:
> **federa said:**
> jeez..!!! let's go get party together because it's  work also on mine acer!!!!!! wow!!
thanks to the saint who fixed this problem!!!

no problem, please send me a message if you plan to spend me some money :D

---

### Post by fictivetoast on 2010-03-25
:D INCREDIBLE!!!  Works here on my 3810t (su9400) running Lucid.  Joy! :D

---

### Post by Romus on 2010-03-26
Hi all. I have acer 3810t with debian testing on it. Suspend wokrs, but just one time. :( Second time i see just black screen :( I installed debian back yesterday, because lucid have too many bugs yet. I had the same problem on lucid too. Somebody had the same problem? 
P.S. Sorry for my English, I'm from Russia.

---

### Post by acermobile on 2010-03-26
Finally!!! Let's start to party :popcorn:
Concerning the "suspend works, but only once"-issue: The machine I am currently writing from has been suspended and successfully resumed four times now without any reboot in the meantime. Additionally, resume is very fast (sub-second regime) and works like I charm with the discrete graphics (intel not tested).

---

### Post by mr bob on 2010-03-26
So I am now curious to know about how the suspend problem was finally fixed, like an ending of Scooby Doo, I would like a little explanation.

I see that the i8042 chip is the keyboard controller. 

Thanks Bruderjakob for fixing this, it really makes this laptop a joy to use now.

---

### Post by acermobile on 2010-03-26
I have found out another strange behaviour:

- Suspend the computer
- Touch the keyboard (press any key) OR touch the (very) sensitive wireless 'button'

As a results, the machine will power up without further warning (and resume properly). This behaviour appears to be deactivated when the lid is closed. Maybe this is a hint to the 8042 chip problem?!

---

### Post by within on 2010-03-26
Thanks very much, it also works great here with my Timeline 3810TZG!

---

### Post by miegiel on 2010-03-26
> **mr bob said:**
> So I am now curious to know about how the suspend problem was finally fixed, like an ending of Scooby Doo, I would like a little explanation.

I see that the i8042 chip is the keyboard controller. 

Thanks Bruderjakob for fixing this, it really makes this laptop a joy to use now.

Sorry, don't know how the fix works. I only did a quick google on *"i8042.reset=1"* to make sure it wasn't something dangerous.

---

### Post by mr bob on 2010-03-27
That is OK Miegiel, I really appreciate that you posted the instructions needed to add to grub, so we didn't have to trawl through the bug report.

---

### Post by jimmy the saint on 2010-03-29
Hey guys.  Just curious.  I am still running the origional BIOS and have not really seen the need to upgrade until the suspend problem was fixed.  Well it wasn't a bios issue after all.

I am considering updating to 1.20.  Are there any reasons to update?  Were any issues fixed that I am not considering?  Should I do it?  I am on 1.10 now.

Thanks

---

### Post by miegiel on 2010-03-29
> **jimmy the saint said:**
> Hey guys.  Just curious.  I am still running the origional BIOS and have not really seen the need to upgrade until the suspend problem was fixed.  Well it wasn't a bios issue after all.

I am considering updating to 1.20.  Are there any reasons to update?  Were any issues fixed that I am not considering?  Should I do it?  I am on 1.10 now.

Thanks

1 reason not to flash too 1.20: You can't boot from a SD card in 1.20, it won't show up in the F12 BIOS boot devices menu. Booting from a SD card with a external USB SD card reader does work though.

1 reason to flash too 1.20: Supports (hardware accelerated?) virtualization according to a post a bit back in this thread.

[s]I was on 1.10 too. I'm not sure if I regret it or not[/s] :D

---

### Post by xir_ on 2010-04-01
> **jimmy the saint said:**
> Hey guys.  Just curious.  I am still running the origional BIOS and have not really seen the need to upgrade until the suspend problem was fixed.  Well it wasn't a bios issue after all.

I am considering updating to 1.20.  Are there any reasons to update?  Were any issues fixed that I am not considering?  Should I do it?  I am on 1.10 now.

Thanks

i just went from 1.10 to 1.24 and i saw a drop of 12 watts to around 9 watts power consumption. This has taken my battery life from 4.5 hours to nearly 7 hours. 

I think that this is due to the presence of lower frequency states (as there is now a 800 mhz state). I'm very glad i updated.

---

### Post by miegiel on 2010-04-01
> **xir_ said:**
> i just went from 1.10 to 1.24 and i saw a drop of 12 watts to around 9 watts power consumption. This has taken my battery life from 4.5 hours to nearly 7 hours. 

I think that this is due to the presence of lower frequency states (as there is now a 800 mhz state). I'm very glad i updated.

:lolflag: Never noticed the 800MHz, the 1.20 BIOS does that too.

---

### Post by jimmy the saint on 2010-04-01
I'm convinced!

---

### Post by mr bob on 2010-04-02
I have a 3410 so I don't know if there is any difference to the 3810 but when I flashed 1.24, there was no saving in power and the fan was spinning permanently on battery.

I reverted to 1.17 and the laptop is nice and quiet again.

BTW, if people would like to know how to flash an older version, there is a DOS flashit option /mc, which ignores version checking.

```
flashit JM3100FR.117 /mc
```

It looks like the little script accepts one option, so this may work too:

```
f.bat /mc
```

---

### Post by muadnu on 2010-04-02
I just installed Lucid and I just can't get Skype to work. Anyone has had any luck?

---

### Post by miegiel on 2010-04-02
> **muadnu said:**
> I just installed Lucid and I just can't get Skype to work. Anyone has had any luck?

Yes, but as with karmic after installing the alsa backport stuff, I need to press my lips against the internal microphone and shout really loud. :twisted: External mic works fine though.

There is 1 thing to be aware of though, you need to select the right input. The default input was my sound output being captured, I only noticed when I was listening to the news while getting my skype to work. 1st you need to start *PulseAudio volume control* (*pavucontrol* in a terminal) and go to the recording tab. It will say "No application is currently recording audio". Next you start a test call in skype and you'll see it listed, ***internal analog stereo*** is my mic and ***monitor of internal analog stereo*** is the capture of my soundcard's output.

---

### Post by mustang7071 on 2010-04-02
Successful "Suspend" to RAM at last!! :popcorn:

Thank you all for the i8042.reset=1 fix.  

Acer Timeline 3810T, BIOS 1.20, Lucid Beta 2.6.32-19-generic.

---

### Post by miegiel on 2010-04-03
New power record =D> (for me anyway).

0.567mA*11.975mV=**6.789825W** to bad it's not 6.789876W :lolflag:

Wifi on, while surfing with chromium (ok, I was reading and not loading any pages) and some stuff running in the background (conky, skype, deluge). To be fair the amps go up and down between 600mA and 800mA, 666mA now :twisted: oh 742mA. Well, you get the idea. Still, I'm really happy with my new depth record.

---

### Post by fmarcia on 2010-04-03
> **miegiel said:**
> New power record =D> (for me anyway).

0.567mA*11.975mV=**6.789825W** to bad it's not 6.789876W :lolflag:

Wifi on, while surfing with chromium (ok, I was reading and not loading any pages) and some stuff running in the background (conky, skype, deluge). To be fair the amps go up and down between 600mA and 800mA, 666mA now :twisted: oh 742mA. Well, you get the idea. Still, I'm really happy with my new depth record.

Could you share your parameters, Miegiel?

I struggled with laptop-mode and parameters from Riskable and [there]("http://www.thinkwiki.org/wiki/How_to_reduce_power_consumption") but could not get my laptop under 8-9W (powertop measurement)!

And everytime I reboot, almost everything is gone :(

Thanks.

---

### Post by acermobile on 2010-04-03
Concerning the microphone issues with skype, try the follwing:

1.) KMIx->Mixer->Configure Channels
2.) Add the Capture channel
3.) MArk the checkbox next to "Capture" and mute the LEFT Channel and pull the amplitude of the right channel up.
4.) Once skype is started you may have to reconfigure the colume (appears to be subject to abrupt changes). Readjust the volume of the right hand channel! It is a bit of a hassle...

BTW sound problems occur from time to time. Goto system settings->multimedia and if asked to remove the devices say yes, they are automatically added.

---

### Post by acermobile on 2010-04-03
Kernel issue for suspend:

I have no time for (multiple) re-compilation of the kernel and I will be unavailable for quite a while. Can anyone try out the following:

- Change i8042.c and recompile kernel (see below). Restart WITHOUT the suspend fix.
Try which one works/does not work.

Changes - Version A:
static int i8042_pm_reset(struct device *dev)
{
        unsigned char param[128]; // CHANGE
        i8042_controller_reset();
        i8042_command(param, I8042_CMD_CTL_TEST); // CHANGE

Changes - Version B:
static int i8042_pm_restore(struct device *dev)
{
        int error;
        unsigned char param[128]; // CHANGE

        error = i8042_controller_check();
        if (error)
                return error;

        error = i8042_controller_selftest();
        if (error)
                return error;

        i8042_command(param, I8042_CMD_CTL_TEST); // CHANGE




Many thanks in advance.

---

### Post by acermobile on 2010-04-03
BTW: The previous tests are needed to (maybe) induce changes in some of the future kernel versions (currently in contact with the developers).

---

### Post by miegiel on 2010-04-03
> **fmarcia said:**
> Could you share your parameters, Miegiel?

I struggled with laptop-mode and parameters from Riskable and [there]("http://www.thinkwiki.org/wiki/How_to_reduce_power_consumption") but could not get my laptop under 8-9W (powertop measurement)!

And everytime I reboot, almost everything is gone :(

Thanks.

Hmmm, it's messy, but when I go off the power grid I run 2 scripts I found somewhere in the forums. I really need figure out what they exactly do to put them in 1 script. 

**edit :**
I should add that I use [conky]("http://ubuntuforums.org/showthread.php?p=8487787#post8487787") to ```
cat /proc/acpi/battery/BAT0/state | grep rate: | awk '{print $3}'
``` the mA drawn from my battery onto my desktop. But that's only when running on the battery, plugged in it displays the battery charging rate. I'm not sure how *powertop* ant *cat*ing */proc/acpi/battery/BAT0/state* compare. :)

Oh, and I have the 3810T with the SU9400 core duo without the ATI graphics.

Anyway, here they are :
```
#!/bin/sh

sudo su -c "echo 5 > /proc/sys/vm/laptop_mode"
sudo su -c "echo min_power > /sys/class/scsi_host/host0/link_power_management_policy"
sudo su -c "echo min_power > /sys/class/scsi_host/host1/link_power_management_policy"
sudo su -c "echo min_power > /sys/class/scsi_host/host2/link_power_management_policy"
sudo su -c "echo min_power > /sys/class/scsi_host/host3/link_power_management_policy"
sudo su -c "echo min_power > /sys/class/scsi_host/host4/link_power_management_policy"
sudo su -c "echo min_power > /sys/class/scsi_host/host5/link_power_management_policy"
sudo su -c "echo 500 > /proc/sys/vm/dirty_writeback_centisecs"
sudo laptop_mode start
# sudo hdparm -S 4 /dev/sda
sudo iwconfig wlan0 power on
```
[COLOR="Red"]run with sudo[/COLOR]
```
#!/bin/bash
# Author: Riskable
# http://ubuntuforums.org/showthread.php?p=8736103#post8736103
#
# Description: Enables every power saving feature I know of
#

# Enable Intel HD Audio power saving
echo 10 > /sys/module/snd_hda_intel/parameters/power_save
echo Y > /sys/module/snd_hda_intel/parameters/power_save_controller
echo 1 > /dev/dsp # Gotta make a sound to turn it on

# Enable various kernel power saving features
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs

# Enable SATA power management
for i in /sys/class/scsi_host/*; do echo "min_power" > $i/link_power_management_policy; cat $i/link_power_management_policy; done

# Enable Wifi power management
/sbin/iwconfig wlan0 power on

# Enable the most aggressive hard drive power savings
hdparm -B 1 -S 12 /dev/sda # Note: May not work on the Acer Timeline's hard drive

# Use tmpfs (RAM disk) for /tmp
echo "tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0" >> /etc/fstab
```
And  yeah, need to run them again after a reboot.

---

### Post by miegiel on 2010-04-03
> **acermobile said:**
> Kernel issue for suspend:

I have no time for (multiple) re-compilation of the kernel and I will be unavailable for quite a while. Can anyone try out the following:

- Change i8042.c and recompile kernel (see below). Restart WITHOUT the suspend fix.
Try which one works/does not work.

Changes - Version A:
static int i8042_pm_reset(struct device *dev)
{
        unsigned char param[128]; // CHANGE
        i8042_controller_reset();
        i8042_command(param, I8042_CMD_CTL_TEST); // CHANGE

Changes - Version B:
static int i8042_pm_restore(struct device *dev)
{
        int error;
        unsigned char param[128]; // CHANGE

        error = i8042_controller_check();
        if (error)
                return error;

        error = i8042_controller_selftest();
        if (error)
                return error;

        i8042_command(param, I8042_CMD_CTL_TEST); // CHANGE




Many thanks in advance.

Ok, I'll go read a bit about this stuff and see how hard it is. To be honest, that code above barely makes sens to me. For example I wouldn't be able to spot a typo.

No promises ;)

---

### Post by muadnu on 2010-04-03
> **miegiel said:**
> Yes, but as with karmic after installing the alsa backport stuff, I need to press my lips against the internal microphone and shout really loud. :twisted: External mic works fine though.

There is 1 thing to be aware of though, you need to select the right input. The default input was my sound output being captured, I only noticed when I was listening to the news while getting my skype to work. 1st you need to start *PulseAudio volume control* (*pavucontrol* in a terminal) and go to the recording tab. It will say "No application is currently recording audio". Next you start a test call in skype and you'll see it listed, ***internal analog stereo*** is my mic and ***monitor of internal analog stereo*** is the capture of my soundcard's output.
I'm not sure what you mean by the last part of your post. Anyway, I see skype listed but can't get any audio unless I hit the microphone or shout loud. I'm really just sick of going over and over again, I just don't get why every other piece of software works fine but not skype. I wish there was an alternative to skype, but at least I am not aware of any (Ekiga works ok, but I won't get the rest of the people I talk to to use it, specially when it's not even available for Windows now).

---

### Post by within on 2010-04-03
> **miegiel said:**
> Yes, but as with karmic after installing the alsa backport stuff, I need to press my lips against the internal microphone and shout really loud. :twisted: External mic works fine though.

There is 1 thing to be aware of though, you need to select the right input. The default input was my sound output being captured, I only noticed when I was listening to the news while getting my skype to work. 1st you need to start *PulseAudio volume control* (*pavucontrol* in a terminal) and go to the recording tab. It will say "No application is currently recording audio". Next you start a test call in skype and you'll see it listed, ***internal analog stereo*** is my mic and ***monitor of internal analog stereo*** is the capture of my soundcard's output.

miegiel, 
have a look at my post in this thread. I did fix completely the skype issues in "forcing" ALSA to be used instead of pulse. I can call without any troubles now in skype.

[http://ubuntuforums.org/showthread.php?p=8881992#post8881992](http://ubuntuforums.org/showthread.php?p=8881992#post8881992)

---

### Post by qnano on 2010-04-03
would anyone know whether it is safe to downgrade to a previous BIOS version, and if yes what would be the simplet go to go about it, either through Windows or Ubuntu? Are all previous BIOS versions compatible?

thanks

---

### Post by miegiel on 2010-04-03
> **qnano said:**
> would anyone know whether it is safe to downgrade to a previous BIOS version, and if yes what would be the simplet go to go about it, either through Windows or Ubuntu? Are all previous BIOS versions compatible?

thanks
previous page :twisted:
> **mr bob said:**
> I have a 3410 so I don't know if there is any difference to the 3810 but when I flashed 1.24, there was no saving in power and the fan was spinning permanently on battery.

I reverted to 1.17 and the laptop is nice and quiet again.

BTW, if people would like to know how to flash an older version, there is a DOS flashit option /mc, which ignores version checking.

```
flashit JM3100FR.117 /mc
```

It looks like the little script accepts one option, so this may work too:

```
f.bat /mc
```

---

### Post by fmarcia on 2010-04-03
> **miegiel said:**
> Hmmm, it's messy, but when I go off the power grid I run 2 scripts I found somewhere in the forums. I really need figure out what they exactly do to put them in 1 script. 

**edit :**
I should add that I use [conky]("http://ubuntuforums.org/showthread.php?p=8487787#post8487787") to ```
cat /proc/acpi/battery/BAT0/state | grep rate: | awk '{print $3}'
``` the mA drawn from my battery onto my desktop. But that's only when running on the battery, plugged in it displays the battery charging rate. I'm not sure how *powertop* ant *cat*ing */proc/acpi/battery/BAT0/state* compare. :)

Oh, and I have the 3810T with the SU9400 core duo without the ATI graphics.

Anyway, here they are :
```
#!/bin/sh

sudo su -c "echo 5 > /proc/sys/vm/laptop_mode"
sudo su -c "echo min_power > /sys/class/scsi_host/host0/link_power_management_policy"
sudo su -c "echo min_power > /sys/class/scsi_host/host1/link_power_management_policy"
sudo su -c "echo min_power > /sys/class/scsi_host/host2/link_power_management_policy"
sudo su -c "echo min_power > /sys/class/scsi_host/host3/link_power_management_policy"
sudo su -c "echo min_power > /sys/class/scsi_host/host4/link_power_management_policy"
sudo su -c "echo min_power > /sys/class/scsi_host/host5/link_power_management_policy"
sudo su -c "echo 500 > /proc/sys/vm/dirty_writeback_centisecs"
sudo laptop_mode start
# sudo hdparm -S 4 /dev/sda
sudo iwconfig wlan0 power on
```
[COLOR="Red"]run with sudo[/COLOR]
```
#!/bin/bash
# Author: Riskable
# http://ubuntuforums.org/showthread.php?p=8736103#post8736103
#
# Description: Enables every power saving feature I know of
#

# Enable Intel HD Audio power saving
echo 10 > /sys/module/snd_hda_intel/parameters/power_save
echo Y > /sys/module/snd_hda_intel/parameters/power_save_controller
echo 1 > /dev/dsp # Gotta make a sound to turn it on

# Enable various kernel power saving features
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs

# Enable SATA power management
for i in /sys/class/scsi_host/*; do echo "min_power" > $i/link_power_management_policy; cat $i/link_power_management_policy; done

# Enable Wifi power management
/sbin/iwconfig wlan0 power on

# Enable the most aggressive hard drive power savings
hdparm -B 1 -S 12 /dev/sda # Note: May not work on the Acer Timeline's hard drive

# Use tmpfs (RAM disk) for /tmp
echo "tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0" >> /etc/fstab
```
And  yeah, need to run them again after a reboot.

I added these lines:
sudo su -c "for i in /sys/bus/usb/devices/*; do echo 1 > \$i/power/autosuspend; done"
sudo su -c "for i in /sys/bus/usb/devices/*; do echo auto > \$i/power/level; done"
sudo su -c "/etc/init.d/bluetooth stop"

And I'm now at 7.6W at best (with a 3810T-SU7400 too)

Thank you.

---

### Post by miegiel on 2010-04-04
> **within said:**
> miegiel, 
have a look at my post in this thread. I did fix completely the skype issues in "forcing" ALSA to be used instead of pulse. I can call without any troubles now in skype.

[http://ubuntuforums.org/showthread.php?p=8881992#post8881992](http://ubuntuforums.org/showthread.php?p=8881992#post8881992)

*mutters* It was the good old "unbalance the input" trick again. Should have tried that 1st. :oops:

Run alsamixer >> press F4 >> move to CAPTURE >> raise the right channel to the max and mute the left channel to the .... uh ... min.

It wouldn't suprise me if that's the only thing I nedded to do in lucid to make the internal microphone work for skype.

---

### Post by qnano on 2010-04-04
> **miegiel said:**
> previous page :twisted:

I 've seen that already, but this "flashit" command does not work in DOS under my computer. I don't know if it is a native Windows command or an additional programme that needs to be downloaded. 

I even googled it buy I could not find any sites mentioning this command other than in this forum.

---

### Post by miegiel on 2010-04-04
> **qnano said:**
> I 've seen that already, but this "flashit" command does not work in DOS under my computer. I don't know if it is a native Windows command or an additional programme that needs to be downloaded. 

I even googled it buy I could not find any sites mentioning this command other than in this forum.

It's an executable in the *DOS* directory in the zip file, you need to be in the (extracted) directory to run it.

---

### Post by muadnu on 2010-04-05
A tangential question: has anyone been able to install Debian on a 
Timeline 3810T? I want to give it Debian testing a try, but I can't figure out how to install it from a USB stick. I've tried Unetbootin but it doesn't boot, and all other methods I've found to do that end up in some sort of kernel panic. I'm not sure if the issue is the hardware or my not being able to set it up from a USB stick...

---

### Post by miegiel on 2010-04-05
> **muadnu said:**
> A tangential question: has anyone been able to install Debian on a 
Timeline 3810T? I want to give it Debian testing a try, but I can't figure out how to install it from a USB stick. I've tried Unetbootin but it doesn't boot, and all other methods I've found to do that end up in some sort of kernel panic. I'm not sure if the issue is the hardware or my not being able to set it up from a USB stick...

Try using the *(USB) Startup Disk Creator* with the debian iso.

---

### Post by muadnu on 2010-04-06
> **miegiel said:**
> Try using the *(USB) Startup Disk Creator* with the debian iso.
Tried it, but still the same (actually, it threw me to the boot prompt and I couldn't do anything from there).

---

### Post by muadnu on 2010-04-06
> **miegiel said:**
> *mutters* It was the good old "unbalance the input" trick again. Should have tried that 1st. :oops:

Run alsamixer >> press F4 >> move to CAPTURE >> raise the right channel to the max and mute the left channel to the .... uh ... min.

It wouldn't suprise me if that's the only thing I nedded to do in lucid to make the internal microphone work for skype.

Yes, I just tried it in lucid and it works great. Thanks!

---

### Post by Romus on 2010-04-06
muadnu, if you want to install debian testing, you need to download debian netinstall but with 2.6.32 kernel, then you need to download  boot.img.gz from debian site. In terminal: zcat boot.img.gz > /dev/sdX (your USB). If it interesting to i can give a link where you can download debian netinstall with 2.6.32 kernel.
P.S. Please, sorry for my english

---

### Post by muadnu on 2010-04-06
> **Romus said:**
> muadnu, if you want to install debian testing, you need to download debian netinstall but with 2.6.32 kernel, then you need to download  boot.img.gz from debian site. In terminal: zcat boot.img.gz > /dev/sdX (your USB). If it interesting to i can give a link where you can download debian netinstall with 2.6.32 kernel.
P.S. Please, sorry for my english

Thanks. If you can give me the link I'd appreciate it!

---

### Post by Romus on 2010-04-06
To install debian on acer 3810t you have to do:
1. Download from [http://kmuto.jp/debian/d-i/](http://kmuto.jp/debian/d-i/)
netinstall(2.6.32 kernel) and boot.img.gz

2. Format you USB stick in FAT32:
insert your USB stick and umount it, then
in terminal:
root # fdisk -l    (to find you USB stick)
root # mkfs.vfat -F 32 -n anyname /dev/sdX

3. root # zcat boot.img.gz > /dev/sdX

4. pull out your USB stick(it's not mount) and insert it back and mount.

5. copy netinst.iso to your USB stick.

6. umount it and boot from it :)

---

### Post by Romus on 2010-04-06
It is possible not to format. To make all from the second item

---

### Post by idreamer on 2010-04-10
sorry... i'm lost! 
i'm install ubuntu 9.10
ok for all.
ok for resume.
but for microphone? how i can use it on ubuntu & skype? [78page is too for read all]
(on archlinux, my previus distro, all ok)

bye and thanks.

---

### Post by miegiel on 2010-04-10
> **idreamer said:**
> sorry... i'm lost! 
i'm install ubuntu 9.10
ok for all.
ok for resume.
but for microphone? how i can use it on ubuntu & skype? [78page is too for read all]
(on archlinux, my previus distro, all ok)

bye and thanks.

In a terminal do :
```
alsamixer
```
press F4 and set the sliders like this (left channel softer than the right):
```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.0.22 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                      F1:  Help               &#9474;
&#9474; Chip: Intel G45 DEVCTG                               F2:  System information &#9474;
&#9474; View: F3: Playback  F4:[Capture] F5: All             F6:  Select sound card  &#9474;
&#9474; Item: Front Mic Boost                                Esc: Exit               &#9474;
&#9474;                                                                              &#9474;
&#9474;                    &#9484;&#9472;&#9472;&#9488;             &#9484;&#9472;&#9472;&#9488;             &#9484;&#9472;&#9472;&#9488;                    &#9474;
&#9474;                    &#9474;  &#9474;             &#9474; [COLOR="Red"]&#9618;[/COLOR]&#9474;             &#9474;  &#9474;                    &#9474;
&#9474;                    &#9474;  &#9474;             &#9474; [COLOR="red"]&#9618;[/COLOR]&#9474;             &#9474;  &#9474;                    &#9474;
&#9474;                    &#9474;  &#9474;             &#9474;&#9618;&#9618;&#9474;             &#9474;  &#9474;                    &#9474;
&#9474;                    &#9474;  &#9474;             &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                    &#9474;
&#9474;                    &#9474;  &#9474;             &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                    &#9474;
&#9474;                    &#9474;  &#9474;             &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                    &#9474;
&#9474;                    &#9474;  &#9474;             &#9474;[COLOR="lime"]&#9618;&#9618;[/COLOR]&#9474;             &#9474;[COLOR="lime"]&#9618;&#9618;[/COLOR]&#9474;                    &#9474;
&#9474;                    &#9474;  &#9474;             &#9474;[COLOR="lime"]&#9618;&#9618;[/COLOR]&#9474;             &#9474;[COLOR="lime"]&#9618;&#9618;[/COLOR]&#9474;                    &#9474;
&#9474;                    &#9474;  &#9474;             &#9474;[COLOR="lime"]&#9618;&#9618;[/COLOR]&#9474;             &#9474;[COLOR="lime"]&#9618;&#9618;[/COLOR]&#9474;                    &#9474;
&#9474;                    &#9474;  &#9474;             &#9474;[COLOR="lime"]&#9618;&#9618;[/COLOR]&#9474;             &#9474;[COLOR="lime"]&#9618;&#9618;[/COLOR]&#9474;                    &#9474;
&#9474;                    &#9474;  &#9474;             &#9474;[COLOR="Lime"]&#9618;&#9618;[/COLOR]&#9474;             &#9474;[COLOR="lime"]&#9618;&#9618;[/COLOR]&#9474;                    &#9474;
&#9474;                    &#9492;&#9472;&#9472;&#9496;            L&#9492;&#9472;&#9472;&#9496;R            &#9492;&#9472;&#9472;&#9496;                    &#9474;
&#9474;                                   CAPTURE                                    &#9474;
&#9474;                    0<>0            80<>100          72<>72                   &#9474;
&#9474;             <Front Mic Boost >    Capture          Digital                   &#9474;
&#9474;                                                                              &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
```
Use the arrow keys to move the sliders up and down and move to the next slider. Use Q Z E and C to move only the right or left channel slider up or down.

---

### Post by idreamer on 2010-04-10
> **miegiel said:**
> In a terminal do :
```
alsamixer
```press F4 and set the sliders like this (left channel softer than the right):
```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.0.22 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                      F1:  Help               &#9474;
&#9474; Chip: Intel G45 DEVCTG                               F2:  System information &#9474;
&#9474; View: F3: Playback  F4:[Capture] F5: All             F6:  Select sound card  &#9474;
&#9474; Item: Front Mic Boost                                Esc: Exit               &#9474;
&#9474;                                                                              &#9474;
&#9474;                    &#9484;&#9472;&#9472;&#9488;             &#9484;&#9472;&#9472;&#9488;             &#9484;&#9472;&#9472;&#9488;                    &#9474;
&#9474;                    &#9474;  &#9474;             &#9474; [COLOR=Red]&#9618;[/COLOR]&#9474;             &#9474;  &#9474;                    &#9474;
&#9474;                    &#9474;  &#9474;             &#9474; [COLOR=red]&#9618;[/COLOR]&#9474;             &#9474;  &#9474;                    &#9474;
&#9474;                    &#9474;  &#9474;             &#9474;&#9618;&#9618;&#9474;             &#9474;  &#9474;                    &#9474;
&#9474;                    &#9474;  &#9474;             &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                    &#9474;
&#9474;                    &#9474;  &#9474;             &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                    &#9474;
&#9474;                    &#9474;  &#9474;             &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                    &#9474;
&#9474;                    &#9474;  &#9474;             &#9474;[COLOR=lime]&#9618;&#9618;[/COLOR]&#9474;             &#9474;[COLOR=lime]&#9618;&#9618;[/COLOR]&#9474;                    &#9474;
&#9474;                    &#9474;  &#9474;             &#9474;[COLOR=lime]&#9618;&#9618;[/COLOR]&#9474;             &#9474;[COLOR=lime]&#9618;&#9618;[/COLOR]&#9474;                    &#9474;
&#9474;                    &#9474;  &#9474;             &#9474;[COLOR=lime]&#9618;&#9618;[/COLOR]&#9474;             &#9474;[COLOR=lime]&#9618;&#9618;[/COLOR]&#9474;                    &#9474;
&#9474;                    &#9474;  &#9474;             &#9474;[COLOR=lime]&#9618;&#9618;[/COLOR]&#9474;             &#9474;[COLOR=lime]&#9618;&#9618;[/COLOR]&#9474;                    &#9474;
&#9474;                    &#9474;  &#9474;             &#9474;[COLOR=Lime]&#9618;&#9618;[/COLOR]&#9474;             &#9474;[COLOR=lime]&#9618;&#9618;[/COLOR]&#9474;                    &#9474;
&#9474;                    &#9492;&#9472;&#9472;&#9496;            L&#9492;&#9472;&#9472;&#9496;R            &#9492;&#9472;&#9472;&#9496;                    &#9474;
&#9474;                                   CAPTURE                                    &#9474;
&#9474;                    0<>0            80<>100          72<>72                   &#9474;
&#9474;             <Front Mic Boost >    Capture          Digital                   &#9474;
&#9474;                                                                              &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
```Use the arrow keys to move the sliders up and down and move to the next slider. Use Q Z E and C to move only the right or left channel slider up or down.

Hi thanks for reply. I have a differerent screen maybe i have a 1.0.20 version of alsa and isn't present "digital" channel. 
but i can record audio with record program now. thanks.
now how i can use microphone in skype? it found pulse server but when i try test i'm mute.

what i can do?

p.s. sorry for my english

---

### Post by miegiel on 2010-04-10
> **idreamer said:**
> Hi thanks for reply. I have a differerent screen maybe i have a 1.0.20 version of alsa and isn't present "digital" channel. 
but i can record audio with record program now. thanks.
now how i can use microphone in skype? it found pulse server but when i try test i'm mute.

what i can do?

p.s. sorry for my english

Sorry forgot to say: In ubuntu karmic (9.10) you might need to install the 'linux-backports-modules-alsa-karmic-generic' package first.

```
sudo apt-get install linux-backports-modules-alsa-karmic-generic
```

Besides that, increase the difference between the left and right channel of you microphone input till you can hear yourself in the "skype test call".

I'm pretty much convinced the whole internal microphone problem is caused by the left channel of the microphone being used to cancel out noises being transmitted through the chassis of the laptop. For example: disk and fan vibrations and typing or tapping noises. When the left and right microphone input are balanced not only undesirable noises get canceled out but your voice gets canceled out too.

---

### Post by idreamer on 2010-04-10
> **miegiel said:**
> Sorry forgot to say: In ubuntu karmic (9.10) you might need to install the 'linux-backports-modules-alsa-karmic-generic' package first.

```
sudo apt-get install linux-backports-modules-alsa-karmic-generic
```Besides that, increase the difference between the left and right channel of you microphone input till you can hear yourself in the "skype test call".

I'm pretty much convinced the whole internal microphone problem is caused by the left channel of the microphone being used to cancel out noises being transmitted through the chassis of the laptop. For example: disk and fan vibrations and typing or tapping noises. When the left and right microphone input are balanced not only undesirable noises get canceled out but your voice gets canceled out too.
i'm shock!!! it's realy how you say..... wow! now all is ok.

other problem/curiosity: my acpi temp is stoped on 27°. anybody have resolve it?

---

### Post by miegiel on 2010-04-10
> **idreamer said:**
> i'm shock!!! it's realy how you say..... wow! now all is ok.

other problem/curiosity: my acpi temp is stoped on 27°. anybody have resolve it?

ACPI temps are not reliable (not on my 3810T anyway). Search the forum, [ubuntu documentation]("https://help.ubuntu.com/community") or google for *lm-sensors*. After instalation and cofiguration use the *coretemp* sensor readout instead.

---

### Post by jimmy the saint on 2010-04-11
Anyone have any advice on how to get the projector screen mode switching button working?

Just picked up a 22 inch monitor to use with my 3810t.  It detects the monitor and there have been no issues, but I am tired of having to open the gui every time to set the monitors up. Does anyone have any idea how I would go about starting to get the FN keys set up right?

Thanks

---

### Post by jimmy the saint on 2010-04-11
FYI, if anyone uses a Samsung monitor/Television with the 3810t, you must rename the HDMI input to PC.  

Still need help with the display switching function keys.

---

### Post by riskable on 2010-04-16
> **miegiel said:**
> 
[COLOR="Red"]run with sudo[/COLOR]
```
# Use tmpfs (RAM disk) for /tmp
echo "tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0" >> /etc/fstab
```
And  yeah, need to run them again after a reboot.

[COLOR="Red"]Only run this command ONCE.[/COLOR]  Also, if you've run it more than once make sure to edit /etc/fstab to get rid of all the extra "tmpfs /tmp..." entries  (you only need it listed once).

Also, you can make these scripts run whenever you're on battery power if you add them to /etc/laptop-mode/batt-start.  For example:

```
root@portarisk:/etc/laptop-mode/batt-start # ls -l
total 4
-rwxr-xr-x 1 root root 805 2010-02-16 17:09 3810t_power_save.sh
root@portarisk:/etc/laptop-mode/batt-start # cat 3810t_power_save.sh 
#!/bin/bash
# Author: Riskable
# http://ubuntuforums.org/showthread.php?p=8736103#post8736103
#
# Description: Enables every power saving feature I know of
#

# Enable Intel HD Audio power saving
echo 10 > /sys/module/snd_hda_intel/parameters/power_save
echo Y > /sys/module/snd_hda_intel/parameters/power_save_controller
echo 1 > /dev/dsp # Gotta make a sound to turn it on

# Enable various kernel power saving features
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs

# Enable SATA power management
for i in /sys/class/scsi_host/*; do echo "min_power" > $i/link_power_management_policy; cat $i/link_power_management_policy; done

# Enable Wifi power management
/sbin/iwconfig wlan0 power on

# Enable the most aggressive hard drive power savings
hdparm -B 1 -S 12 /dev/sda # Note: '-B 1' does work on the 3810T hard drive but doesn't save you much

# Enable USB autosuspend for all USB devices
for i in /sys/bus/usb/devices/*; do echo 1 > \$i/power/autosuspend; done
for i in /sys/bus/usb/devices/*; do echo auto > \$i/power/level; done
```

You can also add a "turn power saving features off" script to batt-stop to speed things back up again on AC power.  Example:

```
root@portarisk:/etc/laptop-mode/batt-stop # ls -l
total 4
-rwxr-xr-x 1 root root 325 2010-02-16 17:10 3810t_power_save_off.sh
root@portarisk:/etc/laptop-mode/batt-stop # cat 3810t_power_save_off.sh 
#!/bin/bash
# Author: Riskable
# http://ubuntuforums.org/showthread.php?p=8736103#post8736103
#
# Description: Disables some power saving features to speed things up when on AC power.
#

# Disable Wifi power management
/sbin/iwconfig wlan0 power off

# Tone down hard drive power savings to speed things up
hdparm -B 254 -S 255 /dev/sda # Note: May not work on the Acer Timeline's hard drive
```

---

### Post by idreamer on 2010-04-16
Hi, new problem :-D
Now my battery don't charge up 88,8% even if I leave it charge 20 hours!
i only put the last firmware of bios and install ubuntu 9.10 (previus i'm use archlinux with gnome)

ideas?
thanks


p.s. i'm control the Statistics of my battery (4day ago my battery go to 100% in the Statistics)

---

### Post by almozavr on 2010-04-16
> **idreamer said:**
> Hi, new problem :-D
Now my battery don't charge up 88,8% even if I leave it charge 20 hours!
i only put the last firmware of bios and install ubuntu 9.10 (previus i'm use archlinux with gnome)

ideas?
thanks


p.s. i'm control the Statistics of my battery (4day ago my battery go to 100% in the Statistics)

I had this problem. For me it means problem with hardware what solves by battery replacement (had no problems with my guarantee, just must wait about 2 weeks in Ukraine)

---

### Post by riskable on 2010-04-17
I'm glad I came back to revisit this thread checking for updates on the suspend problem!  That 'GRUB_CMDLINE_LINUX="i8042.reset=1"' did the trick.  For those who haven't applied this fix yet here's a little command line to take care of everything:

```
sudo sed -i.orig -e 's/GRUB_CMDLINE_LINUX=\"/GRUB_CMDLINE_LINUX=\"i8042.reset=1 /g' /etc/default/grub && sudo update-grub
```

Run that and reboot!  Suspend will now work.

---

### Post by idreamer on 2010-04-18
> **almozavr said:**
> I had this problem. For me it means problem with hardware what solves by battery replacement (had no problems with my guarantee, just must wait about 2 weeks in Ukraine)
same same problem? and now all ok?

---

### Post by fmarcia on 2010-04-22
I struggle with an annoying bug: if the screen turns off automatically after an amount of time defined in battery settings, when I turn it on again, the whole interface becomes sluggish.

The culprit seems to be compiz. As a workaround, I kill it and restart it or logout then login again.

Did somebody experience the same behaviour? Any solution (or trail)?

I'm using Lucid, all packages up to date, and my model is a 3810T-SU9400 with an Intel graphic card.

---

### Post by miegiel on 2010-04-23
> **fmarcia said:**
> I struggle with an annoying bug: if the screen turns off automatically after an amount of time defined in battery settings, when I turn it on again, the whole interface becomes sluggish.

The culprit seems to be compiz. As a workaround, I kill it and restart it or logout then login again.

Did somebody experience the same behaviour? Any solution (or trail)?

I'm using Lucid, all packages up to date, and my model is a 3810T-SU9400 with an Intel graphic card.

I have the same model and never had that happen, did you try running *top* (in a terminal) or the system monitor to see if there are any processes hogging the CPU?

On a side note, for people new to linux it's advised not to run lucid yet. For example, about 2 weeks back there was an error in the kernel's ACPI code and a lot of machines wouldn't boot anymore. You need to know how to deal with situations with the pre-release versions of ubuntu that you won't have to in the released  versions.

---

### Post by miegiel on 2010-04-23
> **riskable said:**
> [COLOR="Red"]Only run this command ONCE.[/COLOR]  Also, if you've run it more than once make sure to edit /etc/fstab to get rid of all the extra "tmpfs /tmp..." entries  (you only need it listed once).

...

Yeah :lolflag: I discovered that already. Good thing I discovered it the next day, else I probably wouldn't have realized where all those *"tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0"* lines  in my */etc/fstab* came from. I had close to 10 already!

> **idreamer said:**
> Hi, new problem :-D
Now my battery don't charge up 88,8% even if I leave it charge 20 hours!
i only put the last firmware of bios and install ubuntu 9.10 (previus i'm use archlinux with gnome)

ideas?
thanks


p.s. i'm control the Statistics of my battery (4day ago my battery go to 100% in the Statistics)
My battery does the same thing. But it's my own fault really. I drained the battery to the point that my laptop crashed due to lack of juice (not the regular "no juice" auto shutdown) twice without fully recharging it in between. This messed up the battery calibration and none of the recalibrate trick I found on the web seem to work. Since it's really my own fault I didn't claim guaranty though. ](*,)

Just a warning to all of you. If you completely drain your battery, the next time you charge it, charge it till it's 100% "blue light on" full.

---

### Post by muadnu on 2010-04-23
> **fmarcia said:**
> I struggle with an annoying bug: if the screen turns off automatically after an amount of time defined in battery settings, when I turn it on again, the whole interface becomes sluggish.

The culprit seems to be compiz. As a workaround, I kill it and restart it or logout then login again.

Did somebody experience the same behaviour? Any solution (or trail)?

I'm using Lucid, all packages up to date, and my model is a 3810T-SU9400 with an Intel graphic card.

Same issue here. And it also happened to me running Fedora 13 Beta...

---

### Post by fmarcia on 2010-04-23
> **miegiel said:**
> Just a warning to all of you. If you completely drain your battery, the next time you charge it, charge it till it's 100% "blue light on" full.

Thanks for the tip!

---

### Post by fmarcia on 2010-04-23
> **fmarcia said:**
> I struggle with an annoying bug: if the screen turns off automatically after an amount of time defined in battery settings, when I turn it on again, the whole interface becomes sluggish.

The culprit seems to be compiz. As a workaround, I kill it and restart it or logout then login again.

Did somebody experience the same behaviour? Any solution (or trail)?

I'm using Lucid, all packages up to date, and my model is a 3810T-SU9400 with an Intel graphic card.

I finally got it: I activated 'Sync to VBlank' in Compiz conf (general/display) sometimes ago which reduced dramatically the amount of wake up in powertop for i915 interrupt but this behaviour was a side effect!

---

### Post by fmarcia on 2010-04-23
> **miegiel said:**
> Two finger, twofinger, 2finger scrolling script for ubuntu lucid 10.04 :D

As  already discovered. You can't use the *.fdi* file in */etc/hal/fdi/policy/* to simulate two finger scrolling in lucid anymore.

No worries, in lucid you only need to run a script and make the script auto run in *Settings >> Sessions and Startup* so that it runs when X starts. Enjoy!

**touchpad.sh**
```
#!/bin/bash
#
# list of synaptics device properties http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html#sect4
# list  current synaptics device properties: xinput list-props '"SynPS/2 Synaptics TouchPad"'
#
xinput --set-prop --type=int --format=32 '"SynPS/2 Synaptics TouchPad"' "Synaptics Two-Finger Pressure" 4
xinput --set-prop --type=int --format=32 '"SynPS/2 Synaptics TouchPad"' "Synaptics Two-Finger Width" 7         # Below width 1 finger touch, above width simulate 2 finger touch. - value=pad-pixels
xinput --set-prop --type=int --format=8  '"SynPS/2 Synaptics TouchPad"' "Synaptics Two-Finger Scrolling" 1 1   # vertical scrolling, horizontal scrolling - values: 0=disable 1=enable
xinput --set-prop --type=int --format=8  '"SynPS/2 Synaptics TouchPad"' "Synaptics Edge Scrolling" 0 0 0       # vertical, horizontal, corner - values: 0=disable  1=enable
xinput --set-prop --type=int --format=32 '"SynPS/2 Synaptics TouchPad"' "Synaptics Jumpy Cursor Threshold" 250 # stabilize 2 finger actions - value=pad-pixels
xinput --set-prop --type=int --format=8  '"SynPS/2 Synaptics TouchPad"' "Synaptics Tap Action" 0 0 0 0 1 2 0   # pad corners rt rb lt lb tap fingers 1 2 3 (can't simulate more then 2 tap fingers AFAIK) - values: 0=disable 1=left 2=middle 3=right etc. (in FF 8=back 9=forward)
exit
```

**run as:**
```
sh touchpad.sh
```
Who knows, it might even work in karmic. :-k

I couldn't make it work fine (not active after a reboot, only after a logout/login cycle) until I added "sleep 3" at the beginning of the script.

Thanks for this gem, miegiel!

---

### Post by miegiel on 2010-04-23
> **fmarcia said:**
> I couldn't make it work fine (not active after a reboot, only after a logout/login cycle) until I added "sleep 3" at the beginning of the script.

Thanks for this gem, miegiel!

You're welcome :mrgreen: Note that at some point the notation for devices changed from **[COLOR="red"]'"[/COLOR]**SynPS/2 Synaptics TouchPad**[COLOR="red"]"'[/COLOR]** to **[COLOR="red"]"[/COLOR]**SynPS/2 Synaptics TouchPad**[COLOR="Red"]"[/COLOR]**.

---

### Post by idreamer on 2010-04-24
> **miegiel said:**
> Yeah :lolflag: I discovered that already. Good thing I discovered it the next day, else I probably wouldn't have realized where all those *"tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0"* lines  in my */etc/fstab* came from. I had close to 10 already!


My battery does the same thing. But it's my own fault really. I drained the battery to the point that my laptop crashed due to lack of juice (not the regular "no juice" auto shutdown) twice without fully recharging it in between. This messed up the battery calibration and none of the recalibrate trick I found on the web seem to work. Since it's really my own fault I didn't claim guaranty though. ](*,)

Just a warning to all of you. If you completely drain your battery, the next time you charge it, charge it till it's 100% "blue light on" full.

trick? can you say me someone?  what do you do this comand:
cat /proc/acpi/battery/BAT0/info 

i have:
```

present:                 yes
design capacity:         5600 mAh <------------normal
last full capacity:      5082 mAh <-------------- my problem
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 0 mAh
design capacity low:     0 mAh
capacity granularity 1:  100 mAh
capacity granularity 2:  0 mAh
model number:            AS09D70
serial number:           2101
battery type:            LION

```

---

### Post by miegiel on 2010-04-24
> **idreamer said:**
> trick? can you say me someone?  what do you do this comand:
cat /proc/acpi/battery/BAT0/info 

i have:
```

present:                 yes
design capacity:         5600 mAh <------------normal
last full capacity:      5082 mAh <-------------- my problem
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 0 mAh
design capacity low:     0 mAh
capacity granularity 1:  100 mAh
capacity granularity 2:  0 mAh
model number:            AS09D70
serial number:           2101
battery type:            LION

```

Correct me if I'm wrong, but I think you're misinterpreting the info ;)

```
user@machine:~$ [COLOR="blue"]cat /proc/acpi/battery/BAT0/info[/COLOR]
present:                 yes
design capacity:         5600 mAh [COLOR="blue"]<<< max capacity when the battery is brand new[/COLOR]
last full capacity:      [COLOR="red"]4989 mAh[/COLOR] [COLOR="blue"]<<< real last full capacity, decreases as the battery ages[/COLOR]
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 0 mAh
design capacity low:     0 mAh
capacity granularity 1:  100 mAh
capacity granularity 2:  0 mAh
model number:            AS09D70
serial number:           5F07
battery type:            LION
OEM info:                SMP-SDI28
user@machine:~$ [COLOR="Blue"]cat /proc/acpi/battery/BAT0/state[/COLOR]
present:                 yes
capacity state:          ok
charging state:          [COLOR="red"]charged[/COLOR]
present rate:            0 mA
remaining capacity:      [COLOR="red"]4350 mAh[/COLOR]  [COLOR="blue"]<<< false full capacity, due to faulty callibration[/COLOR]
present voltage:         12347 mV
```
Note that my battery is fully charged and the *remaining capacity* should be approximately the same as the *last full capacity*. The faulty calibration leads the battery to think it's more empty than it really is. At least that's what I believe.

---

### Post by idreamer on 2010-04-24
> **miegiel said:**
> Correct me if I'm wrong, but I think you're misinterpreting the info ;)

```
user@machine:~$ [COLOR=blue]cat /proc/acpi/battery/BAT0/info[/COLOR]
present:                 yes
design capacity:         5600 mAh [COLOR=blue]<<< max capacity when the battery is brand new[/COLOR]
last full capacity:      [COLOR=red]4989 mAh[/COLOR] [COLOR=blue]<<< real last full capacity, decreases as the battery ages[/COLOR]
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 0 mAh
design capacity low:     0 mAh
capacity granularity 1:  100 mAh
capacity granularity 2:  0 mAh
model number:            AS09D70
serial number:           5F07
battery type:            LION
OEM info:                SMP-SDI28
user@machine:~$ [COLOR=Blue]cat /proc/acpi/battery/BAT0/state[/COLOR]
present:                 yes
capacity state:          ok
charging state:          [COLOR=red]charged[/COLOR]
present rate:            0 mA
remaining capacity:      [COLOR=red]4350 mAh[/COLOR]  [COLOR=blue]<<< false full capacity, due to faulty callibration[/COLOR]
present voltage:         12347 mV
```Note that my battery is fully charged and the *remaining capacity* should be approximately the same as the *last full capacity*. The faulty calibration leads the battery to think it's more empty than it really is. At least that's what I believe.

I don't know much about this calibration problem. But i thinks is possible how you say. In fact last the normal (about 4h) my battery is charge how previus this problem and hardware led is close. 
But this reply get me a doubt: [http://ubuntuforums.org/showpost.php?p=9132459&postcount=788](http://ubuntuforums.org/showpost.php?p=9132459&postcount=788)

few question:
1)When the computer say you have 0% of charge is true o no? 
2)can you explain me same truck even if fail with you?
3)what you think about other user reply?

so always sorry for bad english
ale

---

### Post by idreamer on 2010-04-24
> **idreamer said:**
> I don't know much about this calibration problem. But i thinks is possible how you say. In fact last the normal (about 4h) my battery is charge how previus this problem and hardware led is close. 
But this reply get me a doubt: [http://ubuntuforums.org/showpost.php?p=9132459&postcount=788](http://ubuntuforums.org/showpost.php?p=9132459&postcount=788)

few question:
1)When the computer say you have 0% of charge is true o no? 
2)can you explain me same truck even if fail with you?
3)what you think about other user reply?

so always sorry for bad english
ale

and this: [http://forum.notebookreview.com/showthread.php?p=6143788](http://forum.notebookreview.com/showthread.php?p=6143788)

---

### Post by miegiel on 2010-04-25
ubuntu forums



> **idreamer said:**
> I don't know much about this calibration problem. But i thinks is possible how you say. In fact last the normal (about 4h) my battery is charge how previus this problem and hardware led is close. 
But this reply get me a doubt: [http://ubuntuforums.org/showpost.php?p=9132459&postcount=788](http://ubuntuforums.org/showpost.php?p=9132459&postcount=788)

few question:
1)When the computer say you have 0% of charge is true o no? 
2)can you explain me same truck even if fail with you?
3)what you think about other user reply?

so always sorry for bad english
ale

Don't worry about your english, I misinterpret people who write perfect english all the time. :lolflag:

Regarding your questions:
[LIST=1]
[*]Short answer: No. Long answer: Lithium ion (or lithium whatever) batteries get damaged when they fully discharge. To prevent damage battery manufacturers calibrate the electronics in the battery to always reserve a charge of about 10%. So if the battery meter shows 0%, there's still 10% left. But it's 10% you can't use anyway, if you would, the battery would damage and loose a big chunk of it's capacity. This also relates to the problem with the battery. What I think is going on is that, due to the decalibration, about 20% of the capacity is being reserved. So instead of showing 0% when there is 10% capacity left to prevent damage, now the battery's electronics say it's at 0% while there is still 20% left. And when the battery is fully charged (99%) the battery says it's only at 89%.
[*]The trick is to cause the battery to recalibrate itself. As I posted this happened to my battery when I discharged it to 0% twice in a row and only charged it half in between. This is also what you do to force the battery to recalibrate. First fully charge the battery. This can take a long time and the blue light won't go on, but *cat /proc/acpi/battery/BAT0/state* will tell you when it's charged and how slow it's charging (in mA, time predictions are unreliable because they assume you're charging to 100% instead of 89%). Then discharge the battery as far as you can, don't let the laptop shutdown automatically, keep it running till the battery stops providing power and the laptop crashes.  But only do this once, don't turn the laptop on again to see if you can squeeze a few more drops out of the battery. Next put the laptop away, leave it off for a a couple of hours. What I read in different places on the web was 2 to 4 hours, but I just timed it to be empty round about bed time and left it off till the next morning. Now the battery should be uncalibrated again. The next step is to fully recharge it in one go. The battery's electronics use this charge cycle to calibrate the battery again. I've read suggestions to leave the power connected for a couple of hours again after the battery is charged. But to be honest this step doesn't make much sense to me, though it won't hurt.
[*]> **almozavr said:**
> I had this problem. For me it means problem with hardware what solves by battery replacement (had no problems with my guarantee, just must wait about 2 weeks in Ukraine) Yeah, fixing the problem by replacing it by a calibrated battery will do the trick too :D In the [http://forum.notebookreview.com/showthread.php?p=6143788](http://forum.notebookreview.com/showthread.php?p=6143788) thread people are confusing 2 things: 1) decreasing battery capacity as it ages, 2) a battery with a messed up calibration. This post from that thread seems to contradict everything I said in point 1 and 2 :-k > Same thing here, I bought a 3810t for my friend and after 8 months it will not charge over 88% I thought it was the battery but then when i but the same battery on my wife's 4810tz it charges to a full 100% !!
I also used another power adapter and still the 3810t would not charge to over 88%
[/LIST]

Now, though I get the theory behind the recalibration trick, it **[COLOR="Red"]didn't work for me[/COLOR]** and **almozavr**'s method does seem to work. I might see if I can get a new battery from acer. Still, it's kind of my own fault that the calibration got messed up. And I don't really mis the 10% I've lost. I need a 4 hour charge and deliberately got a laptop that does a lot more then 4h. So that I'd have plenty of reserve capacity, as the battery looses capacity as it ages.

Finaly, HP's [Calibrate the notebook PC battery]("http://h20239.www2.hp.com/techcenter/battery/Battery_max.htm") (at the end of the page).

---

### Post by fmarcia on 2010-04-27
> **miegiel said:**
> You're welcome :mrgreen: Note that at some point the notation for devices changed from **[COLOR="red"]'"[/COLOR]**SynPS/2 Synaptics TouchPad**[COLOR="red"]"'[/COLOR]** to **[COLOR="red"]"[/COLOR]**SynPS/2 Synaptics TouchPad**[COLOR="Red"]"[/COLOR]**.

Grrr... since a few hours (last update?), the mouse went crazy when I use two fingers! Did somebody notice that?

---

### Post by megaexception on 2010-04-27
> **fmarcia said:**
> Grrr... since a few hours (last update?), the mouse went crazy when I use two fingers! Did somebody notice that?

yep.
some time ago, something got changed, and touchpad tapping doesn't work now.


old fix with "xinput --set-prop --type=int 13 'Synaptics Two-Finger Pressure' 80" doesn't help :(

---

### Post by fmarcia on 2010-04-27
> **megaexception said:**
> yep.
some time ago, something got changed, and touchpad tapping doesn't work now.


old fix with "xinput --set-prop --type=int 13 'Synaptics Two-Finger Pressure' 80" doesn't help :(

It's crazy: it's working again (even after a reboot). Things I did in between:
- tweak my vpn conf (gui only)
- have a look at the last gnome-shell release (with "gnome-shell --replace")
- surf the web (with ff)

I love miegiel again :-p

By the way, did you read this: [Synaptics for Linux]("http://bit.ly/dgZ795")

---

### Post by federa on 2010-04-29
i've red about the synaptics stuff some days ago..but, what is it really?? i mean..on the site there's a lots of info about how does it works, what it's gonna do ecc ecc...but..is it downloadable/installable/"scriptable" or what?? anyone knows??

the fan issues is solved just by flashing the bios?

---

### Post by muadnu on 2010-05-01
I'm running lucid now and I still have the issue of the wireless connection suddenly getting disabled. I got a bit lost in the thread and I'm not sure if there's anything I can try to solve this...

---

### Post by within on 2010-05-02
> **muadnu said:**
> I'm running lucid now and I still have the issue of the wireless connection suddenly getting disabled. I got a bit lost in the thread and I'm not sure if there's anything I can try to solve this...

I don't use wireless, so I am not sure if my answer will be "enough", but I know this issue has been discussed and solved.
First of all, I did to get my wireless device info (I have a 3810TZG Timeline model):
```
lspci
```
to find it is:
```
02:00.0 Network controller: Intel Corporation WiFi Link 100 Series

```

Then, you should follow this, posted on the dedicated help page for Timeline, last fix:
[HTML]https://help.ubuntu.com/community/AspireTimeline/Fixes[/HTML]
> Wireless network

Affected model 1810tz with wificard identified as Intel Corporation WiFi Link 100 Series (lspci). Killswitch always off for wireless in 9.04 and 9.10 alpha6. Follow instructions to fix issue.

9.10

   1. Download new microcode from [http://www.intellinuxwireless.org/](http://www.intellinuxwireless.org/) put in /lib/firmware
   2. Download latest compat-wireless (2009-09-30 worked) from [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download), follow instructions (install, unload).
   3. sudo modprobe iwlagn or restart 

Hope it helps :)

---

### Post by shirinasal on 2010-05-04
Just click on the speaker icon then select Sound preferences then find Sound theme tab and select Ubuntu
(I faced this problem before)

---

### Post by muadnu on 2010-05-04
> **within said:**
> I don't use wireless, so I am not sure if my answer will be "enough", but I know this issue has been discussed and solved.
First of all, I did to get my wireless device info (I have a 3810TZG Timeline model):
```
lspci
```
to find it is:
```
02:00.0 Network controller: Intel Corporation WiFi Link 100 Series

```

Then, you should follow this, posted on the dedicated help page for Timeline, last fix:
[HTML]https://help.ubuntu.com/community/AspireTimeline/Fixes[/HTML]


Hope it helps :)

Thanks! It seems to be working, I've been using a wireless connection for several hours now with no problems (which had never happened before). I'll post back if I get disconnected in any case.

---

### Post by splater on 2010-05-06
Hi every one.

I just installed the ubuntu 10.4 on my 3810TZ and everything was ok but I installed the ATI driver proposed and since ... black screen .... If I switch off the computer I can see the logout screen ... 

¿any idea how to solve this ? even if I had to come back with no open source driver ... I can't have acces to CTRL+F1 ...

Thanks

---

### Post by miegiel on 2010-05-06
> **splater said:**
> Hi every one.

I just installed the ubuntu 10.4 on my 3810TZ and everything was ok but I installed the ATI driver proposed and since ... black screen .... If I switch off the computer I can see the logout screen ... 

¿any idea how to solve this ? even if I had to come back with no open source driver ... I can't have acces to CTRL+F1 ...

Thanks

Did you try *Ctrl+Alt+F1*? The GUI starts pretty soon with lucid. Sorry, I can't really help with the driver issue, my timeline has no ati and I haven't had bootup-graphics-driver-issues on one of my machines for ages and don't know where to start solving that anymore. (Well yeah, I know where I'd have to start and it starts with a G)

---

### Post by acermobile on 2010-05-06
Hi.

I have Lucid working with ATI graphics - no probs.
You should install the driver via jockey-kde. Did you switch to "discrete" in the BIOS? This completely disables the onboard graphics. A good way for getting back to X without the proprietary driver is the removal of /etc/X11/xorg.conf

Then (after installation of the driver) you might want to try the following XORG.CONF which is working perfectly for me (backup old config!):

Section "ServerLayout"
        Identifier     "amdcccle Layout"
        Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
        Load  "glx"
EndSection

Section "Monitor"
        Identifier   "0-LVDS"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
        Option      "PreferredMode" "1366x768"
        Option      "TargetRefresh" "60"
        Option      "Position" "0 0"
        Option      "Rotate" "normal"
        Option      "Disable" "false"
EndSection

Section "Monitor"
        Identifier   "0-CRT1"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
        Option      "PreferredMode" "1366x768"
        Option      "TargetRefresh" "60"
        Option      "Position" "0 0"
        Option      "Rotate" "normal"
        Option      "Disable" "false"
EndSection

Section "Device"
        Identifier  "Default Device"
        Driver      "fglrx"
EndSection

Section "Device"
        Identifier  "amdcccle-Device[1]-0"
        Driver      "fglrx"
        Option      "Monitor-LVDS" "0-LVDS"
        Option      "Monitor-CRT1" "0-CRT1"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        DefaultDepth     24
EndSection

Section "Screen"
        Identifier "amdcccle-Screen[1]-0"
        Device     "amdcccle-Device[1]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

and install catalyst (sudo apt-get install fglrx-amdcccle). Further I suggest something like "sudo ln -s /usr/lib/fglrx/bin/amdcccle /usr/local/bin/catalyst" such that catalyst is in your path. Then you are fine to configure the card to your needs.

I just checked my power consumption and achieved the ultimate minimum of 6,7 W with wireless enabled and discrete graphics. So more than 8 h bat. life at office use is feasible (use the various powersaving scripts published earlier in this thread).

BTW: I would not try using Xinerama - it may work, but it may also cause some trouble.

Hope this resolved some of your problems!

---

### Post by splater on 2010-05-06
thanks with the discret I was able to make it working again. Tonigh I will try your config you are talking about !!

Thanks

---

### Post by E@zyVG on 2010-05-06
> **riskable said:**
> [COLOR="Red"]Only run this command ONCE.[/COLOR]  Also, if you've run it more than once make sure to edit /etc/fstab to get rid of all the extra "tmpfs /tmp..." entries  (you only need it listed once).

Also, you can make these scripts run whenever you're on battery power if you add them to /etc/laptop-mode/batt-start.  For example:

```
root@portarisk:/etc/laptop-mode/batt-start # ls -l
total 4
-rwxr-xr-x 1 root root 805 2010-02-16 17:09 3810t_power_save.sh
root@portarisk:/etc/laptop-mode/batt-start # cat 3810t_power_save.sh 
#!/bin/bash
# Author: Riskable
# http://ubuntuforums.org/showthread.php?p=8736103#post8736103
#
# Description: Enables every power saving feature I know of
#

# Enable Intel HD Audio power saving
echo 10 > /sys/module/snd_hda_intel/parameters/power_save
echo Y > /sys/module/snd_hda_intel/parameters/power_save_controller
echo 1 > /dev/dsp # Gotta make a sound to turn it on

# Enable various kernel power saving features
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs

# Enable SATA power management
for i in /sys/class/scsi_host/*; do echo "min_power" > $i/link_power_management_policy; cat $i/link_power_management_policy; done

# Enable Wifi power management
/sbin/iwconfig wlan0 power on

# Enable the most aggressive hard drive power savings
hdparm -B 1 -S 12 /dev/sda # Note: '-B 1' does work on the 3810T hard drive but doesn't save you much

# Enable USB autosuspend for all USB devices
for i in /sys/bus/usb/devices/*; do echo 1 > \$i/power/autosuspend; done
for i in /sys/bus/usb/devices/*; do echo auto > \$i/power/level; done
```

You can also add a "turn power saving features off" script to batt-stop to speed things back up again on AC power.  Example:

```
root@portarisk:/etc/laptop-mode/batt-stop # ls -l
total 4
-rwxr-xr-x 1 root root 325 2010-02-16 17:10 3810t_power_save_off.sh
root@portarisk:/etc/laptop-mode/batt-stop # cat 3810t_power_save_off.sh 
#!/bin/bash
# Author: Riskable
# http://ubuntuforums.org/showthread.php?p=8736103#post8736103
#
# Description: Disables some power saving features to speed things up when on AC power.
#

# Disable Wifi power management
/sbin/iwconfig wlan0 power off

# Tone down hard drive power savings to speed things up
hdparm -B 254 -S 255 /dev/sda # Note: May not work on the Acer Timeline's hard drive
```

1. Will those scripts in start and stop folders run automatically, as I do not see any instruction where it mentions to laptop_mode to launch the 3810t_power_save.sh in corresponding modes!

2. Is the "laptop_mode start" always running, or it has to be launched by including the command in "/etc/init.d/boot.local"? Also it be good to point that laptop_mode is not installed by default, and needs to be installed, hence the question.

I read that them scripts can be as well added to "/etc/init.d/boot.local", and not the /etc/laptop-mode/..." folders.

As per sound problem, I didn't install anything extra, just launched "alsamixer" > F4 > and maxed the rigth channel (0 for left channel) in Capture, and Input Source set to Mic. This way Skype works perfect.

For ATI, select discrete in BIOS, as there is no switching support for now, and install the driver from System>Admin>Hardware Drivers.
[B]
Riskable/Admin >>[/B] It be really handy to have all the instructions, step-by-step posted on first post and pinned, and to include other tweaks as well, related to 3810T/TG models.

Thanks.

---

### Post by within on 2010-05-07
> **E@zyVG said:**
> 
[B]
Riskable/Admin >>[/B] It be really handy to have all the instructions, step-by-step posted on first post and pinned, and to include other tweaks as well, related to 3810T/TG models.

Thanks.

This is the aim idea of my blog... unfortunately, I am quite busy with work lately, and more important, my blog is a google one (blogspot), which is blocked in China, where I work almost 50% of the time in a year.

I know it' a bit off topic, but... if anyone could forward to a blog which is fine, simple, nice AND that works in China... it could be helpful.

---

### Post by miegiel on 2010-05-07
> **within said:**
> This is the aim idea of my blog... unfortunately, I am quite busy with work lately, and more important, my blog is a google one (blogspot), which is blocked in China, where I work almost 50% of the time in a year.

I know it' a bit off topic, but... if anyone could forward to a blog which is fine, simple, nice AND that works in China... it could be helpful.

You should be able to get at your blog via a [VPN]("http://en.wikipedia.org/wiki/Vpn") located somewhere else in the world. Or you could add the stuff to the [Ubuntu Documentation > Community Documentation > AspireTimeline]("https://help.ubuntu.com/community/AspireTimeline") pages. But that's a wiki, so others can edit/expand on it too.

---

### Post by within on 2010-05-07
@ miegiel:

you're right about VPN. I have to find one.
About th official page, I don't believe my contribution will really add benefits to it. I plan to gather the information I used (most of them from there, but also from here) as well as my own comments about the softwares I use, and the way I prepared my laptop to use Ubuntu. It's a bit "too personal" for a contribution to an official page...

---

### Post by almozavr on 2010-05-07
I'm afraid but Ubuntu Linux kills my battery and this is fact :( 0,5 mW capacity reducing each time I use all battery till automatic shutdown. Crap!

I have 10.04 with 2.6.32 kernel. The same problem appeared with 9.10

---

### Post by miegiel on 2010-05-07
> **almozavr said:**
> I'm afraid but Ubuntu Linux kills my battery and this is fact :( 0,5 mW capacity reducing each time I use all battery till automatic shutdown. Crap!

I have 10.04 with 2.6.32 kernel. The same problem appeared with 9.10

You can't blame that on linux. ;) It's normal for lithium batteries to loose capacity over time. They even loose capacity while lying on the shelf. They loose capacity faster when they're completely full or completely empty, at 40-50% they loose the least capacity over time. On the up side they don't age faster when you use them a lot. And they don't have a "memory", so you don't need to fully discharge and fully charge the battery to prevent capacity loss.

That's why I bought a laptop with a 6-8h battery life while I only really need 4h. After about 2 years the battery's capacity will be almost useless, though with a energy efficient laptop you might still get 1h of battery life.

---

### Post by almozavr on 2010-05-07
> **miegiel said:**
> You can't blame that on linux. ;) It's normal for lithium batteries to loose capacity over time. They even loose capacity while lying on the shelf. They loose capacity faster when they're completely full or completely empty, at 40-50% they loose the least capacity over time. On the up side they don't age faster when you use them a lot. And they don't have a "memory", so you don't need to fully discharge and fully charge the battery to prevent capacity loss.

That's why I bought a laptop with a 6-8h battery life while I only really need 4h. After about 2 years the battery's capacity will be almost useless, though with a energy efficient laptop you might still get 1h of battery life.

Yeap, it's understood. BUT!

Battery capacity decreasing started right after using Ubuntu. It APPEARED 3 times in a row when I worked on Ubuntu (during 2 days I had 3 discharging/charging cycles). Till that moment I used Win 7 and had no surges with battery capacity. Now I've got -0.5 mW every time I use my full battery capacity. :(

---

### Post by miegiel on 2010-05-07
> **almozavr said:**
> Yeap, it's understood. BUT!

Battery capacity decreasing started right after using Ubuntu. It APPEARED 3 times in a row when I worked on Ubuntu (during 2 days I had 3 discharging/charging cycles). Till that moment I used Win 7 and had no surges with battery capacity. Now I've got -0.5 mW every time I use my full battery capacity. :(

Just to be sure I'm not misunderstanding you. Do you mean *"-0.5 mW**[COLOR="Red"]h[/COLOR]**"*?

W is a unit for power and batteries capacities are measured in units of energy like Wh (mWh, kWh), or Ah (mAh, kAh :twisted:) at a more or less constant voltage. After all, energy is power over time.

---

### Post by almozavr on 2010-05-07
> **miegiel said:**
> Just to be sure I'm not misunderstanding you. Do you mean *"-0.5 mW**[COLOR=Red]h[/COLOR]**"*?

W is a unit for power and batteries capacities are measured in units of energy like Wh (mWh, kWh), or Ah (mAh, kAh :twisted:) at a more or less constant voltage. After all, energy is power over time.

Certainly, I'm sorry!

My battery lost 500 mWh or 0.5 Wh after last discharging cycle on Ubuntu :( Also I have a problem with charging now: can't reach "Fully charged capacity" and my indicator is yellow all the time. It ges't quickly to 99% during charging then... stucks here for a long time and nothing happens :( I'll see what happens next. But I had such a problem with 9.10 earlier half a year before - all came to battery changing after only 5 monthes of work... But Win 7 works fine with battery. That's offensively :(

---

### Post by miegiel on 2010-05-07
> **almozavr said:**
> Certainly, I'm sorry!

My battery lost 500 mWh or 0.5 Wh after last discharging cycle on Ubuntu :( Also I have a problem with charging now: can't reach "Fully charged capacity" and my indicator is yellow all the time. It ges't quickly to 99% during charging then... stucks here for a long time and nothing happens :( I'll see what happens next. But I had such a problem with 9.10 earlier half a year before - all came to battery changing after only 5 monthes of work... But Win 7 works fine with battery. That's offensively :(

Ok, that's a significant amount. 5600mAh * 12V = 67.2Wh so 0.5 mWh would have been almost nothing.

---

### Post by almozavr on 2010-05-08
> **miegiel said:**
> Ok, that's a significant amount. 5600mAh * 12V = 67.2Wh so 0.5 mWh would have been almost nothing.

No, it's wrong. I wrote
> My battery lost 500 mWh or **0.5 Wh** after last discharging cycle on Ubuntu

It means I have 57 Wh istead of 58,5 Wh after 3 full discharging/charging cycles...

---

### Post by within on 2010-05-08
> **miegiel said:**
> You can't blame that on linux. ;) It's normal for lithium batteries to loose capacity over time. They even loose capacity while lying on the shelf. They loose capacity faster when they're completely full or completely empty, at 40-50% they loose the least capacity over time. On the up side they don't age faster when you use them a lot. And they don't have a "memory", so you don't need to fully discharge and fully charge the battery to prevent capacity loss.

That's why I bought a laptop with a 6-8h battery life while I only really need 4h. After about 2 years the battery's capacity will be almost useless, though with a energy efficient laptop you might still get 1h of battery life.

that's weird... I've always been told charging and discharging battery should always be done from 0 to 100% to have longer battery life and better battery usage.
Of course, charing and discharging should affect the battery capacity amount...
for example, in my case, after 1 complete discharge and recharge of battery (yesterday) I have now:
```
within@within-laptop:~$ cat /proc/acpi/battery/BAT0/info
present:                 yes
design capacity:         5600 mAh
last full capacity:      [COLOR="Red"]5562[/COLOR] mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 0 mAh
design capacity low:     0 mAh
capacity granularity 1:  100 mAh
capacity granularity 2:  0 mAh
model number:            AS09D36
serial number:           3E30
battery type:            LION
OEM info:                SSANY

```

It thus means after only 1 full cycle (discharge/charge), 38 mAh were lost.

Nevertheless, it is a fact that Ubuntu is not perfect for managing power and battery usage; this french article compares on 2 laptops the power consumption with win 7 and Ubuntu 10.04, the differences are sometimes huge:
[HTML]http://www.presence-pc.com/actualite/Windows-Ubuntu-consommation-39263/#xtor=RSS-11[/HTML]

---

### Post by salsa2010 on 2010-05-10
I'm new here! hello everyone! I just bought a 3810T Core2Solo  without ATI and installed Xubuntu 10.04. My BIOS is 1.20. I am quite disappointed about the noise of the fan (after 2 minutes, it runs continuously, which is very annoying). I've read many posts about this topic, but couldn't find a definitive solution.

Could anyone who solved this issue describe the solution ? Which BIOS version is the best regarding this issue (8 versions are available on ACER's site! from 1.04 up to 1.27), which additional software should be used, which system modification can help ? Thank you very much

- salsa

---

### Post by mr bob on 2010-05-10
> **mr bob said:**
> I have a 3410 so I don't know if there is any difference to the 3810 but when I flashed 1.24, there was no saving in power and the fan was spinning permanently on battery.

I reverted to 1.17 and the laptop is nice and quiet again.

BTW, if people would like to know how to flash an older version, there is a DOS flashit option /mc, which ignores version checking.

```
flashit JM3100FR.117 /mc
```

It looks like the little script accepts one option, so this may work too:

```
f.bat /mc
```


Here is my original post, it worked for me. I think the fan permanently spins from 1.20 onwards so 1.17 seems to be the best.

I think the only extra thing you get with 1.24 is hardware accelerated virtualization.

---

### Post by salsa2010 on 2010-05-11
> **mr bob said:**
> Here is my original post, it worked for me. I think the fan permanently spins from 1.20 onwards so 1.17 seems to be the best.

I think the only extra thing you get with 1.24 is hardware accelerated virtualization.

Unfortunately, this didn't work for me ](*,) I downgraded my BIOS from 1.20 to 1.17, but still, the fan is blowing all the time. It blows even more when I switch AC on... I'll try with an older BIOS version, let's see.

Is there anyone who managed to stop the fan blowing all the time on a 3810t + (x)ubuntu ? or is this just normal behaviour ? in this case I'll regret my purchase...:frown:

---

### Post by salsa2010 on 2010-05-11
> **salsa2010 said:**
> Unfortunately, this didn't work for me ](*,) I downgraded my BIOS from 1.20 to 1.17, but still, the fan is blowing all the time. It blows even more when I switch AC on... I'll try with an older BIOS version, let's see.

Is there anyone who managed to stop the fan blowing all the time on a 3810t + (x)ubuntu ? or is this just normal behaviour ? in this case I'll regret my purchase...:frown:

BIOS 1.10 does not solve the problem too ](*,)  help!

---

### Post by miegiel on 2010-05-11
> **salsa2010 said:**
> BIOS 1.10 does not solve the problem too ](*,)  help!

I'm using BIOS 1.24 on my 3810T and have no fan problems at all. It speeds up at about 44°C and speeds up even more at 55°C or so. And has done so with all the BIOSes I've used, the original 1.00 (I assume) 1.04 (I think, hey it was a year ago), 1.08, 1.10, 1.20 and now 1.24.

If the problem is related to the BIOS, it might be that you didn't use the proper update procedure. **Before and after updating the BIOS  you should always enter the BIOS and load the "BIOS defaults".** This prevents changes you made to your BIOS configuration from messing up stuff in the new BIOS.

Else I think there's something wrong with your ubuntu installation.

---

### Post by salsa2010 on 2010-05-11
> **miegiel said:**
> I'm using BIOS 1.24 on my 3810T and have no fan problems at all. It speeds up at about 44°C and speeds up even more at 55°C or so. And has done so with all the BIOSes I've used, the original 1.00 (I assume) 1.04 (I think, hey it was a year ago), 1.08, 1.10, 1.20 and now 1.24.

If the problem is related to the BIOS, it might be that you didn't use the proper update procedure. **Before and after updating the BIOS  you should always enter the BIOS and load the "BIOS defaults".** This prevents changes you made to your BIOS configuration from messing up stuff in the new BIOS.

Else I think there's something wrong with your ubuntu installation.

Thank you for your answer. I tried to load the BIOS default on my current BIOS (1.10), no change.

Which tool are you using to check at which temperatures the fan starts ?

Can you please describe what happens with your fan when you switch the power supply on and off ? on my system, as soon as I switch on power supply, the fan speed increases and gets louder (too much for me...). When I return on battery mode, the fan speed immediately reduces. So the fan speed is not controlled by the temperatures in this case.

---

### Post by miegiel on 2010-05-11
> **salsa2010 said:**
> Thank you for your answer. I tried to load the BIOS default on my current BIOS (1.10), no change.

Which tool are you using to check at which temperatures the fan starts ?

[lm-sensors]("https://help.ubuntu.com/community/SensorInstallHowto") (coretemp sensor) and [conky]("http://ubuntuforums.org/showthread.php?t=281865") to display the sensor readout on my desktop.

> Can you please describe what happens with your fan when you switch the power supply on and off ? on my system, as soon as I switch on power supply, the fan speed increases and gets louder (too much for me...). When I return on battery mode, the fan speed immediately reduces. So the fan speed is not controlled by the temperatures in this case.

I just tried that. To my surprise the fan runs at the same speed. I'd swear I heard it slowdown after unplugging AC on other occasions.

---

### Post by salsa2010 on 2010-05-12
> **miegiel said:**
> 
Else I think there's something wrong with your ubuntu installation.

Does (X)Ubuntu play a role in the regulation of the fan ?
If yes, how ?

---

### Post by splater on 2010-05-13
Hi every one,

I have a 
3810TZ with U4100 2 cores Intel with ATI 4300   bios: 1.20
Ubuntu 10.4
and my problem are:

-fan always on and air is hot
-battery last no more 2 hours .... :(

I install powertop and it says: 18.9W ... What can I do. It seems that Throttling is always on T0 100% (¿is that normal?)

To add more data: lspci with grep vga
```

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
01:00.0 VGA compatible controller: ATI Technologies Inc M92 LP [Mobility Radeon HD 4300 Series]

```
Throttling:
```
state count:             8
active state:            T0
state available: T0 to T7
states:
   *T0:                  100%
    T1:                  88%
    T2:                  75%
    T3:                  63%
    T4:                  50%
    T5:                  38%
    T6:                  25%
    T7:                  13%

```

diretory /proc/acpi/fan/ is empty normal?

powertop output
```

   *T0:                  100%Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 4.6%)         1300 Mhz     0.0%
polling           0.0ms ( 0.0%)         1200 Mhz   100.0%
C1 mwait          0.4ms ( 0.4%)
C4 mwait          1.7ms (95.0%)


Wakeups-from-idle per second : 584.5    interval: 3.0s
Power usage (ACPI estimate): 18.8W (0.8 hours)

Top causes for wakeups:
  55.1% (372.3)   PS/2 keyboard/mouse/touchpad interrupt
  11.6% ( 78.3)   [extra timer interrupt]
  11.3% ( 76.3)   [i915] <interrupt>
   9.0% ( 61.0)   [kernel scheduler] Load balancing tick
   2.5% ( 17.0)   Xorg
   2.2% ( 14.7)   firefox-bin

```


Thanks for your help!!!
Regards

---

### Post by acermobile on 2010-05-13
Have you modified the bios-settings to make sure only the discrete (ATI) graphics card is being used? Otherwise both cards will run simultaneously... Therefore switch graphics to "discrete". Then install the ati proprietary driver using jockey-kde and, further, the amd catalyst control center (see one of my previous posts). You shall be able to achieve less than 10 W without any further tuning (which can be found in this thread).

Good luck.

I have the same configuration and can barely ever hear the fan blowing!

PS: Deinstall all the openjdk stuff and install the sun java instead. This solved some issues concerning java and high cpu load.

---

### Post by splater on 2010-05-14
thanks it works, I have less than 10W. I am pretty sure I can lower this value with some stuff I read in the forum.

Problem is that with discret under Win7 it's a total mess !!! Lot's of device are not working well (device manager says that) and max screen resoltion is not good ...

There is no trick to have bios in switchable and disable it from ubuntu ?

Regards

---

### Post by acermobile on 2010-05-14
Short answer: As far as I know you cannot use switchable in linux with the ati card.

Longer answer: There is a patch available that disables the ati and makes you linux box use the intel card instead. I cannot tell you about power consumption etc. since I need the ati card anyway and barely ever boot up windows. Try this link:
[http://ubuntuforums.org/showpost.php?p=7933876&postcount=11](http://ubuntuforums.org/showpost.php?p=7933876&postcount=11)

---

### Post by within on 2010-05-17
Very good news: the new Linux Kernel v2.6.34 brings many features and corrections, but the very most important thing to my eyes is: if you have 2 GPU (such as in some Timeline model), you will be able with this Kernel to switch from one to another!

[HTML]http://kernelnewbies.org/Linux_2_6_34#head-d5dbe5b78c37bdb03e18b07556b06c1167dc3bb9[/HTML]

> Some laptops have two GPUs, a low-power and inefficient GPU and a high-power and powerful GPU. Users should be able to switch to one or another at runtime. In this version, Linux adds support for this feature. You need to restart X, though. 

:popcorn:

---

### Post by Tocharius on 2010-05-19
Hi there!

I have a problem dual booting Win7 and Ubuntu 10.04 on my 3810T.

The usual procedure is installing Windows, installing Ubuntu by resizing the partition, and Grub works without any problem.

This doesn't work on the 3810T.

When I try the same thing on my Eee PC 1000H, it works flawlessly.

And the really strange thing: When I install Win7 and Ubuntu 9.10, dual boot also works.

So the problem only occurs on the 3810T, and only with 10.04.

Even installing JUST 10.04 without dual booting doesn't result in a proper bootloader.

When just 10.04, or both Win7 and 10.04 are installed, and I tell my notebook to boot from a USB drive containing 10.04, it starts the GRUB on the hard disk. So the USB drive works like a kickstarter for the GRUB installed on the HDD.

So, when I say boot USB with dual boot, it shows me the GRUB menu, and when I do the same thing with only 10.04 installed, it boots the Ubuntu on the HDD.

Anyone else having this problem?

At the moment, I'm running Win7 and 9.10, and everything just works.

My guess: An AHCI/IDE problem?

---

### Post by tomfool on 2010-05-19
Hi!
The problem i guess is that you installed GRUB on usb,that's why it just starts with usb on!
I made the same mistake....re-install 10.04 and at the last page of installation go to advace options and select sdb.

---

### Post by Tocharius on 2010-05-19
> **tomfool said:**
> Hi!
The problem i guess is that you installed GRUB on usb,that's why it just starts with usb on!
I made the same mistake....re-install 10.04 and at the last page of installation go to advace options and select sdb.

That sounds incredibly logical. I will try that. It will take some time though, because at the moment I need that machine for productivity, but I'm optimistic.

Any idea why it just works on the Eee PC? Is the USB drive mounted differently?

---

### Post by tomfool on 2010-05-20
Yep!Depend on the BIOS!In fact with the old one (1.17) i did not have this problem while with the new one i have....!
Try it and let me know if it works!

---

### Post by splater on 2010-05-20
> **tomfool said:**
> Yep!Depend on the BIOS!In fact with the old one (1.17) i did not have this problem while with the new one i have....!
Try it and let me know if it works!

Correct: I have the bios 1.20 and I had to click on advanced to install grub where it should be.
Worked ok for me !

---

### Post by Tocharius on 2010-05-20
Thanks for the help, it works when I use the advanced button to change the boot loader target.

I'm going to flash back to BIOS 1.17 soon. Annoying fan is annoying...

---

### Post by within on 2010-05-24
Hi there,

for some of those who has SSD in their TimeLine (bought like this or replaced the conventional HD), I've found a very interested link about some improvements made for Linux.

Here is the link:
[A Tweaker’s Guide to Solid State Drives (SSDs) and Linux]("http://www.zdnet.com/blog/perlow/geek-sheet-a-tweakers-guide-to-solid-state-drives-ssds-and-linux/9190")

some complementary links:
[http://blog.lawrenceso.ca/2008/10/ssd-optimization-on-ubuntu.html]("http://blog.lawrenceso.ca/2008/10/ssd-optimization-on-ubuntu.html")
[http://www.mydellmini.com/forum/dell-mini-9-hardware-upgrades/6741-tips-tweaking-solid-state-drive-performance-linux.html]("http://www.mydellmini.com/forum/dell-mini-9-hardware-upgrades/6741-tips-tweaking-solid-state-drive-performance-linux.html")
[http://opentechnow.blogspot.com/2010/02/linux-ssd-optimization-guide.html]("http://opentechnow.blogspot.com/2010/02/linux-ssd-optimization-guide.html")

Since I discovered these few minutes ago, I haven't tried these settings, but I will soon.
If any of you have some comments, remarks, warnings or complementary information, everything is welcome to be shared here :)

within

---

### Post by pinotje on 2010-05-24
I'm also owner of the sexy slim Acer 3810T...

Which BIOS version will solve the fan continuously spinning problem?
It's quite annoying to hear that spinning sound whole day :(

I have at this moment the newest BIOS version, 1.27....

---

### Post by splater on 2010-05-25
> **pinotje said:**
> I'm also owner of the sexy slim Acer 3810T...

Which BIOS version will solve the fan continuously spinning problem?
It's quite annoying to hear that spinning sound whole day :(

I have at this moment the newest BIOS version, 1.27....

Be sure you have selected in your bios the discret mode because if not you are perhaps working with both graphic card and it's normal fan is spinning high ... I have the 1.20 bios and since I have put in in discret mode I have no fan problem. 
Hope this helps

---

### Post by pinotje on 2010-05-25
> **splater said:**
> Be sure you have selected in your bios the discret mode because if not you are perhaps working with both graphic card and it's normal fan is spinning high ... I have the 1.20 bios and since I have put in in discret mode I have no fan problem. 
Hope this helps

How to select discret mode in BIOS?

because I don't see the discret settings in BIOS...

---

### Post by mr bob on 2010-05-25
> **megaexception said:**
> just updated bios to 1.20. on first look, nothing has changed.

but, when i modprobe kvm and kvm_intel, and launch kvm - everything is working and i do not receive any complains about VT support:


```

# cat /proc/cpuinfo | grep -o vmx
vmx
# modprobe kvm kvm_intel
<nothing here>
# dmesg | grep kvm
<nothing here>
# kvm -monitor stdio                                                                                                                                            QEMU 0.12.50 monitor - type 'help' for more information
(qemu) info kvm
kvm support: enabled
(qemu) 




```


it's look like in bios 1.20, acer silently enabled virtualization :)

Can anyone confirm that the official Acer BIOS from 1.20 onwards enable hardware virtualization?

I have tried BIOS 1.20 and 1.24 and don't seem to be getting hardware virtualization at all.

---

### Post by mr bob on 2010-05-26
OK, I am definitely running BIOS 1.24.

I have just run a little piece of code from here:

[http://www.linux-kvm.org/page/Enable_VT-X_on_Mac_Pro_%28Early_2008%29]("http://www.linux-kvm.org/page/Enable_VT-X_on_Mac_Pro_%28Early_2008%29")

and it is telling me that VT-X is disabled and locked in the BIOS.

Does anybody know why I am getting a different result from other people, who claim to have virtualization set in the BIOS from 1.20 onwards?

---

### Post by gotham48 on 2010-05-26
Has anyone here got Sleep combination working? I mean Fn+F2? Is there any manual about configuring such hotkeys?

---

### Post by within on 2010-05-26
> **gotham48 said:**
> Has anyone here got Sleep combination working? I mean Fn+F2? Is there any manual about configuring such hotkeys?

I believe it is related to the mapped keyboard you chose.
Here, I use everyday the fn+F4 to suspend my laptop and it works perfectly.

Have a look in System --> Preferences --> Keyboard for further keyboard details.

---

### Post by netimen on 2010-05-28
Suspend doesn't work on my 4810TG when I close the lid. The screen goes black, but the led-lights still work, and the notebook consumes much power and is very warm.

I have checked all the settings in Power Management are OK.

---

### Post by within on 2010-05-28
> **netimen said:**
> Suspend doesn't work on my 4810TG when I close the lid. The screen goes black, but the led-lights still work, and the notebook consumes much power and is very warm.

I have checked all the settings in Power Management are OK.

does suspend mode work if you use fn+F4 keys?

Here, in Power Management Preferences, I set "Suspend" action when closing lid, on both AC & Battery power tabs.
I guess you followed the advice to activate suspend mode right?

> sudo gedit /etc/default/grub

edit the line as follows:
GRUB_CMDLINE_LINUX="i8042.reset=1"

REM: You can also edit the GRUB_CMDLINE_LINUX_DEFAULT="i8042.reset=1 quiet splash" line, but it will only change the default boot option and not the recovery and old kernel options in the grub menu.

Do either one of these 2, not both together.

save edited file, and then:

sudo update-grub

And reboot

---

### Post by netimen on 2010-05-28
Thank you for the answer. Yeah when I pressed Fn+F4 suspend worked OK. The problem is that it does work when I close the lid sometimes too, but most of times doesn't

---

### Post by within on 2010-05-29
seems weird... I believe it might be related to a process you sometimes run, sometimes don't, and can affect the suspend...

have you tried this:
close the lid, the suspend does not work (screen goes black, but the led-lights still work), then press fn+F4? in this case, suspend does work or not?

In my case, I use 99% of the time the fn+F4 keys combination to suspend my laptop, but when I try in closing the lid, until now, it works too.

I'm not really helpful here, but I hope some other people will see your message and bring you complementary answers, maybe with a solution :)

---

### Post by netimen on 2010-05-30
Thank you, I'll try pressing Fn+F4

---

### Post by muadnu on 2010-06-03
I want to try arch in this laptop but I haven't been able to install it. I tried using unetbootin to put the arch installer in a usb drive, but after doing it I can't boot (it says something like "cannot find linux image"). I had tried this before with the same result... Has anyone been able to install arch? Any suggestions?

---

### Post by within on 2010-06-03
> **muadnu said:**
> I want to try arch in this laptop but I haven't been able to install it. I tried using unetbootin to put the arch installer in a usb drive, but after doing it I can't boot (it says something like "cannot find linux image"). I had tried this before with the same result... Has anyone been able to install arch? Any suggestions?

Not sure it is related to Arch... I had the same problem when trying to make an bootable USB with FreeDOS to be able to upgrade the BIOS. I was never able to have a working and bootable USB. I follows a HOW-TO made with unetbootin running under Windows and if I try the Linux version, it does not work for me.
My only explanation is the Linux version has an issue with some Linux ISOs when creating the bootable image...

---

### Post by muadnu on 2010-06-03
> **within said:**
> Not sure it is related to Arch... I had the same problem when trying to make an bootable USB with FreeDOS to be able to upgrade the BIOS. I was never able to have a working and bootable USB. I follows a HOW-TO made with unetbootin running under Windows and if I try the Linux version, it does not work for me.
My only explanation is the Linux version has an issue with some Linux ISOs when creating the bootable image...

You are right, it is not only related to Arch, I've had the same issue with other distros. Another weird thing: with the last Arch version one can simply byte-copy the iso to the usb drive and it is supposed to work; I did it and I can boot using qemu but if I boot the laptop with the usb drive plugged in I can't get past the initial screen that says Acer (I can't even get to the bios), while the usb drive's light flashes continuously. I read somewhere that it may be related with the fact that after byte-copying the drive is not formatted as vfat (indeed it is not, it ends up being udf) but I'm not sure this is the reason...

---

### Post by elrasho on 2010-06-03
Hello all,

I am planning on getting an Acer 4810TZG (model  LX.PK502.003), I assume Unbuntu will run fine with no hicups?

I will be using the laptop for browsing the web, some web design using HTML, CSS, PHP, ASP.net, Dreamweaver CS4 and Photoshop CS4. Will these Adobe products run ok?

Any advice would be greatly appreciated

Thanks

---

### Post by within on 2010-06-04
> **elrasho said:**
> Hello all,

I am planning on getting an Acer 4810TZG (model  LX.PK502.003), I assume Unbuntu will run fine with no hicups?

I will be using the laptop for browsing the web, some web design using HTML, CSS, PHP, ASP.net, Dreamweaver CS4 and Photoshop CS4. Will these Adobe products run ok?

Any advice would be greatly appreciated

Thanks

Hi there,

TZG model means you will have ATI GPU. I have 3810TZG and I am really a happy camper :)

For web design, you will find many useful dev tools in official Ubuntu packages. 
About Photoshop and Dreamweaver, you need to have either a virtual machine or Wine to be able to run it. I really can't say if these versions work OK or not, but I know with old Photoshop 7 it's flawless.
If you plan using Wine, also add wine-doors, it brings few things and also if I remember well some information about Adobe CS stuff. Of course, The Gimp is also a terrific program for image manipulation.

if you search for some information, here are some saying wine + Photoshop CS4 work together fine:
[Photoshop CS4 and Wine]("http://ubuntuforums.org/showthread.php?p=9104270")

a detailed way of installing CS4 with Wine under Jaunty is here:
[Installing Adobe CS4 in Wine]("http://www.sucka.net/2009/08/installing-adobe-cs4-in-wine/")

Cheers,
within

---

### Post by elrasho on 2010-06-04
Thanks for the info within :)

Whats your 3810TZG like running Ubuntu? Does it run flawlessly or is there some lag? Also what kind of battery life are you getting out of it? Does Ubuntu have some power saving settings?

Im totally new to Ubuntu hence the primitive questions lol

---

### Post by within on 2010-06-04
> **elrasho said:**
> Thanks for the info within :)
My pleasure to participate to the Ubuntu Community :) 

> **elrasho said:**
> Whats your 3810TZG like running Ubuntu? Does it run flawlessly or is there some lag? Also what kind of battery life are you getting out of it? Does Ubuntu have some power saving settings?
It runs Ubuntu 10.04 and it's really fast booting, smooth in every aspect, no lag (I have set the Visual Effects to "extra") and no crash. I just had a little issue recently with fglrx that interfered with -radeon Driver, and I did follow this this page ([fglrx fix for radeon]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver")) to fix it (2nd choice was good choice for me).
About the battery, I can't say, my laptop is on my desk, plugged 99% of the time. I beliebe it's good battery life, even if it seems to be less compared to 7 according what has been said on this subject here. There are some power savings tweaks, posted in this topic, so better for you to take some time to read the post and you will find many useful information among the 87 pages up to now.

> **elrasho said:**
> Im totally new to Ubuntu hence the primitive questions lol
There is always a start for everyone. Good you are open minded and chose Ubuntu, it's really a  nice distro, with a great community.

---

### Post by fabase on 2010-06-09
Hi everybody, I have just bought an AS3810T-944G32n, updated BIOS to v. 1.27 and installed Ubuntu 10.4 64bit. Everything works fine except suspend, microphone and (the big problem) the fan, which is always off: when a task requires 100% CPU for some minutes, the notebook shuts down instantaneously (no shut down procedure, it goes off - I think CPU thermal protection, as under the keyboard it is VERY hot). Also fixing CPU freq. to 800 MHz, the cpu reaches rapidly 65°-68°, and no fan is active (no sound and no hot air from the cooling grates).
I tried using sensors and pwmconfig, but no PWM device can be found. I also tried acerhdf ([http://piie.net/?section=acerhdf](http://piie.net/?section=acerhdf)), but unsuccessfully.
Is anyone experienced with the same problem? Maybe I could solve it with a previous BIOS version....?

---

### Post by within on 2010-06-09
Hi fabase,

for the suspend mode:
```
sudo gedit /etc/default/grub

edit the line as follows:
GRUB_CMDLINE_LINUX="i8042.reset=1"

REM: You can also edit the GRUB_CMDLINE_LINUX_DEFAULT="i8042.reset=1 quiet splash" line, but it will only change the default boot option and not the recovery and old kernel options in the grub menu.

Do either one of these 2, not both together.

save edited file, and then:

sudo update-grub

And reboot
```

For microphone, there few tricks around that all works (some say you have to change the balance, but I can't remember the steps well); nevertheless, I remember I did install the ALSA backoprts:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
reboot
```
and for skype, I changed my start command line:
```
In System --> Preferences --> Main Menu

edit the properties of skype and replace in Command skype by /bin/sh -c "PULSE_SERVER=127.0.0.1 skype"
```

About the fan, it seems you are the very first one to mention this issue. I know on the contrary many people complain about the fan working all the time, and thus makes the laptop not quiet. Your problem is far worse, but it can really affect the hardware.

You chose to install the 64bit version. Not sure this is related, but i find I prefer the 32bit, it's less hassles with some packages or settings.

About the BIOS, since I upgraded to 1.20 I haven't changed it, thus I have no experience on higher versions, sorry.

I hope someone will bring you some more help. Don't hesitate to  look for in the whole forum about non working fan, this kind of issue could have happened to other laptops and maybe some fixes are already discussed.

Good luck,
within

---

### Post by fabase on 2010-06-10
Hi within, thanks for your quick reply!
Yesterday I tried to downgrade BIOS to v.1.20 with USB key and FreeDOS procedure, but BIOS downgrade is not permitted by the flash utility.
I'm now planning to install 32 bit version, as you suggested.
I'll also try microphone and suspend fix.
I hope it will work.....
 
thanks
fabase
 
EDIT: I have just tried also the 10.4 32 bit version - no change, fan is always off!

---

### Post by dmgenp on 2010-06-12
Hi there!

Just bought an 3810TZ-272G25i laptop.
Plan to install ubuntu 10.04.

A few questions:
- it came with bios version 1.04. Is there any reason to upgrade it ? I see some people in this thread are even downgrading the bios to fix the issues.
- Plan to install ubuntu right over the windows partition, and leave only the recovery partition intact. Don't plan to use windows at all - should be OK, right ? Or is there some issues what will strictly requre a windows system to fix ?
- Is there any difference in running 32bit or 64bit ubuntu on this laptop ? I'm running a 64 bit version on my other laptop (a larger one), didn't have any real issues for a long time.
- How you guys do a middle-button mouse clicks with touchpad ? The buttons below a touchpad can't be pressed with one finger simultaneously (like i'm doing on my other laptop).

---

### Post by executorvs on 2010-06-12
for the 5810TZ I've found the latest bios update 1.35 is less buggy all around than the previos 6 or so bios versions I've tried. if dumping windows first make your restore discs for use in addition to the recovery partition. there have been some issues with things like brightness keys not working when using compiz and the cdrom eject button not working. the workaround for the cdrom is simply to type "eject cdrom" in terminal or to make a shortcut which runs the command. I'm planning on trying kernel 2.6.35.1 on my timeline later today and will let you know how it works.

---

### Post by dmgenp on 2010-06-13
> **executorvs said:**
> for the 5810TZ I've found the latest bios update 1.35 is less buggy all around than the previos 6 or so bios versions I've tried. if dumping windows first make your restore discs for use in addition to the recovery partition.

The latest bios version I can see on the acer website for 3810TZ is 1.27     2010/04/26
Is there some other means to get more recent versions, or 1.35 is just for 5810, and not for 3810 ?

My laptop don't have dvd drive at all, so to make the restore discs I will have to buy an external one...

---

### Post by executorvs on 2010-06-13
you could also backup to an SDcard and 1.35 on the 5810 was released 4/22

---

### Post by acermobile on 2010-06-14
I just received my 3810TZG back from the second repair within 7 months. The display cable had a defect contact which lead to display corruptions. The first defect was a broken display backlight.

Service was very smooth, send in on Monday, got back the next monday. However, I am getting rid of such lousy quality. Let's see how it turns out during the four months abroad that I am heading for on saturday...

---

### Post by sotomajor on 2010-06-15
> **acermobile said:**
> I just received my 3810TZG back from the second repair within 7 months. The display cable had a defect contact which lead to display corruptions. The first defect was a broken display backlight.

Service was very smooth, send in on Monday, got back the next monday. However, I am getting rid of such lousy quality. Let's see how it turns out during the four months abroad that I am heading for on saturday...

Yesterday I brought my 3810T to service as well. And it's 3rd problem within 1 year. Before it was broken charger and battery problem which could not reach 100% of charge. This time matrix backlight does not work.

I'm really thinking about buying another laptop, but actually I very like this one and don't see decent competitors for same price.

---

### Post by Fizx on 2010-06-15
> **jimmy the saint said:**
> Just discovered something by accident and thought I'd share.

I read somewhere about someone fixing the bonkers mousepad by changing the order that the input devices were recognized, as it only happened when he booted with USB mouse attached.  I decided to run the experiment. It worked.


How do you change input devices? I freshly installed fedora and the touchpad still goes bonkers and the only thing I had attatched was the flash drive. If I boot up without any mouse attatched it still goes bonkers. It's making me go bonkers. Can anyone tell me how to fix this?

P.S. I use fedora because ubuntu has a crazy style going on and fedora is always more lightweight.

---

### Post by Fizx on 2010-06-17
> **miegiel said:**
> 
Oh, and my battery times are crap. The battery got decalibrated and I can't get it to recalibrate. I get about 4 hours on _my workload_, it used to be something between 5 and 6 hours.


You ever figure out how to recalibrate it? I left my laptop in the car for too long and I'm afraid the battery is not optimal.

---

### Post by Fizx on 2010-06-17
Can anyone recommend a good BIOS version to use? I'm on 1.17 right now and have a SU4100 processor. The fan is always spinning on AC, but on battery it reduces rpm.

---

### Post by Fizx on 2010-06-17
I'm going to post this guide on how to configure Fedora 13 so I don't forget, and maybe it will be helpful:


[LIST=1]
[*]Install Fedora through [https://fedorahosted.org/liveusb-creator/](https://fedorahosted.org/liveusb-creator/)
[*]Enable rpmfusion for yum: [http://rpmfusion.org/Configuration](http://rpmfusion.org/Configuration)
[*]```
yum update
```
[*]```
yum install gconf-editor
``` This is needed so we can disable gnome's touchpad settings. It will interfere with ours.
[*]Go to *System Tools > Configuration Editor > Apps > gnome_settings_daemon > plugins > mouse* and uncheck active.
[*]Now to enable multitouch scrolling and tap-click you need to modify xorg. Hal settings are deprecated. We first need a xorg.conf ```
yum install system-config-display
``` ```
system-config-display
```.
[*]There will now be a xorg.conf in /etc/X11/. Edit it and append this: ```
Section "InputClass"
    Identifier "tap-by-default"
    MatchIsTouchpad "on"
    Driver "synaptics"
    Option "SHMConfig" "1"
    Option "TapButton1" "1"
    Option "EmulateTwoFingerMinZ" "50"
    Option "EmulateTwoFingerMinW" "6"
    Option "VertTwoFingerScroll" "1"
    Option "HorizTwoFingerScroll" "1"
    Option "VertEdgeScroll" "0"
EndSection
```
[*]To get suspend working, edit /boot/grub/grub.conf and add ```
i8042.reset=1
``` to the end of the kernel line.
[*]Run these once to turn on wireless and hard disk power saving features: ```
echo "/sbin/iwconfig wlan0 power on" >> /etc/rc.local
echo "vm.swappiness=10" >> /etc/sysctl.conf
echo "tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0" >> /etc/fstab
```
[*][Install laptop-mode-tools]("http://samwel.tk/laptop_mode/packages/fedora")
[*]To enable laptop_mode you must run this command: ```
sudo touch /var/run/laptop-mode-tools/enabled
```
[*]To enable power saving features when unplugged from adapter, add this to a file in /etc/laptop-mode/batt-start/
```
#!/bin/bash
# Author: Riskable
# http://ubuntuforums.org/showthread.php?p=8736103#post8736103
#
# Description: Enables every power saving feature I know of
#

# Enable Intel HD Audio power saving
echo 10 > /sys/module/snd_hda_intel/parameters/power_save
echo Y > /sys/module/snd_hda_intel/parameters/power_save_controller
echo 1 > /dev/dsp # Gotta make a sound to turn it on

# Enable various kernel power saving features
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs

# Enable SATA power management
for i in /sys/class/scsi_host/*; do echo "min_power" > $i/link_power_management_policy; cat $i/link_power_management_policy; done

# Enable Wifi power management
/sbin/iwconfig wlan0 power on

# Enable the most aggressive hard drive power savings
hdparm -B 1 -S 12 /dev/sda # Note: '-B 1' does work on the 3810T hard drive but doesn't save you much

``` Credit goes to riskable
[*]Make that file executable by running ```
chmod +x filename
```
[/LIST]
That's all I can think of right now.

---

### Post by stillnotcool on 2010-06-17
Thanks to everyone for such a great thread.  The resources here are invaluable.  Recently I've been eyeing an Acer Timeline (AS3810T-6376) with SU9400 processor.  Of course, I'm only interested in using Ubuntu 10.04 on this computer, but I'm not necessarily interested in doing much post-install tweaking.

I'm fairly literate technologically, but I'm having trouble wading through the more technical areas of this thread.  Could someone please summarize for me the status of Ubuntu 10.04 on this model of the Acer Timeline?  If I were to install Ubuntu 10.04 on it, would I need to do much post-install tweaking?  Are all components recognized out of the box?

Thanks in advance for helping a new Ubuntu user.

---

### Post by Fizx on 2010-06-17
No, you won't have to configure much. Most everything works out of the box like the webcam, sd card reader, wireless, ethernet, etc. What doesn't work out of the box is the internal microphone, suspend, multitouch on touchpad, and it has less battery life in ubuntu than windows (for me it was 5 hrs vs 8 hrs but I got it to 7 hrs vs 8 hrs).

Internal mic is easily fixable ([https://help.ubuntu.com/community/AspireTimeline/Fixes](https://help.ubuntu.com/community/AspireTimeline/Fixes)) and if you need more battery life, yes you will have to tweak a little, but not more than say 30 minutes worth. Suspend can be fixed in a minute. If you have problems just post here and we can help, or you can read back through thread.

---

### Post by stillnotcool on 2010-06-18
Thanks, Fizx, for your reply.

> **Fizx said:**
> No, you won't have to configure much. Most everything works out of the box like the webcam, sd card reader, wireless, ethernet, etc. What doesn't work out of the box is the internal microphone, suspend, multitouch on touchpad, and it has less battery life in ubuntu than windows (for me it was 5 hrs vs 8 hrs but I got it to 7 hrs vs 8 hrs).

I'm glad to hear this.  The internal mic, multitouch, and decreased battery life aren't dealbreakers for me, but the suspend issue might be.  That's a feature I use every day.

> Internal mic is easily fixable ([https://help.ubuntu.com/community/AspireTimeline/Fixes](https://help.ubuntu.com/community/AspireTimeline/Fixes)) and if you need more battery life, yes you will have to tweak a little, but not more than say 30 minutes worth. Suspend can be fixed in a minute. If you have problems just post here and we can help, or you can read back through thread.

This link is immensely helpful; however, it seems that it's only been update sporadically since the release of Lucid.  Thanks for bringing me up to speed.  I've never fiddled with GRUB, but I'd consider doing so if it means restoring suspend to my Timeline.

---

### Post by Fizx on 2010-06-18
Here's a command by riskable on pg 79 to fix suspend. Just copy and paste into terminal:

```
sudo sed -i.orig -e 's/GRUB_CMDLINE_LINUX=\"/GRUB_CMDLINE_LINUX=\"i8042.reset=1 /g' /etc/default/grub && sudo update-grub
```

---

### Post by majsan on 2010-06-21
Hello,

I recently installed Ubuntu 10.4 on my Acer 3810gz. I installed the 64-bit version using a USB-drive. Ubuntu Live worked just fine and there was no problems during installation. I used the whole hard drive (no need for Windows I thought). Now when I start the computer the Acer-splash screens shows, but then Ubuntu does not start. Instead there is just a black screen with a underscore blinking on it. When I press ctrl-alt-del the computer restarts with the same effects as before.

I tried some different settings in the BIOS-menu, for example using IDE instead of AHCI as SATA Mode. I also tried disabling D2D Recovery since I though that this was on a partition I have now deleted?

I'm confused, I have installed Ubuntu many times before and this is the first time it has happened. Have anyone else had a problem like this or does anybody have an idea how to solve it?

Edit: I have the newest BIOS, just got the computer back from service for fixing the broken screen and they updated it.

---

### Post by Fizx on 2010-06-21
Maybe you installed grub on the usb drive instead of the hard drive. Boot while ur usb is attatched or install again and follow steps more closely. You paid for windows might as well have make back up discs.

---

### Post by majsan on 2010-06-21
Thanks a lot for the help, but I figured out what was wrong. It was a really dumb thing, but I must have been really tired and accidentally followed instructions for installing Ubuntu onto a USB-drive. No wonder something went wrong.

---

### Post by frsk on 2010-06-25
Hi.

I've just installed Ubuntu 10.4 on Acer Aspire 3810T.

Whenever the mouse hovers over a dropdown box or in a window with horizontal scrollbars, the touchpad scrolls to the right. This also prevents me from using the computer as "normal", as the scrolling seemingly is active all the time. I.e. alt+tab doesn't work, as it continuously tries to scroll at the same time.

I've been looking through this thread as well as Googled quite a bit, without any useful help.

In Windows Vista, there's no similar problem, so I'm pretty sure it is not an hardware problem.

Anyone with a similar experience?

---

### Post by within on 2010-07-06
hi frsk,

when you report problems about some of your mouse gestures and alt+tab, is your Ubuntu installation (from CD) just "fresh", out-of-the-box? or after some updates and/or some tweaks/tunings/settings?

Ive read once someone reported a similar problem with alt+tab after changing some settings within compiz.

---

### Post by reddino on 2010-07-09
I read and read posts, but I'm still missing something. Does someone really knows why on some systems frequency scaling include 800 MHz and on some other (like in mine) cpu frequency scaling stops at 1200 MHz?

I'm running 3810TZ with bios 1.24 and ubuntu 10.04 with original kernel 2.6.32 (system upgraded to today).

=============

I JUST READ THAT MY CPU SU4100 DOES NOT SUPPORT SCALING ... AND ALSO IN WINDOWS IT SEEMS RUNNING AT 1200.
NEVER MIND, I'D LIKED IF THE CPU COULD RUN MORE COOL (AND FAN NOT RUNNING AT ALL) BUT THIS IS NOT THE CASE.

---

### Post by acermobile on 2010-07-26
> **reddino said:**
> 
I JUST READ THAT MY CPU SU4100 DOES NOT SUPPORT SCALING ... AND ALSO IN WINDOWS IT SEEMS RUNNING AT 1200.
NEVER MIND, I'D LIKED IF THE CPU COULD RUN MORE COOL (AND FAN NOT RUNNING AT ALL) BUT THIS IS NOT THE CASE.

I have just installed the 2.6.34 kernel and while I am not 100% sure about the following results, I am still optimistic about these points:
- less fan activity (NOTE: I do not see much fan acitivity with 2.6.32-22 and others, too)
- installing FGLRX is a bit messy, but works (ubuntu x-swat ppa, follow this link: [http://www.arausch.de/blog/11/Ubuntu-10-4-lucid-und-2-6-34-Kernel-sowie-ATI-fglrx](http://www.arausch.de/blog/11/Ubuntu-10-4-lucid-und-2-6-34-Kernel-sowie-ATI-fglrx) )
- I had swap issues when resuming from suspend from time to time. This has not occured since I upgraded to 2.6.34, although I have not resumed very often since the upgrade.
- the minimum power consumption on battery with wireless enabled and the established power tweaks should be around 6.6-7 W in idle mode with brightness to the lowest etc. This is at most as much as with 2.6.32, if not less

If you own an ATI graphics card, try using the discrete graphics only,  not the intel one. I remember having both running and the power  consumption and fan noise where much more pronounced.

---

### Post by acermobile on 2010-07-26
Just a side note for people suffering from "Network management disabled" problems:

sudo vim /var/lib/NetworkManager/NetworkManager.state
Check that you have  "NetworkingEnabled=true". If not so, then change to "true" and (if needed) restart network-manager.

This error can occur if resuming a suspended session fails (e.g., if the swapping problem hits you and you decide to reboot instead of waiting 5 minutes). Unfortunately googling for the tweak is a bit tricky if you have no network support, so it is wise to store the trick in a small textfile. If worked for me a couple of times and changed my mood from desperate to relaxed (note that if networkmanagement is disabled, it will stay so even after numerous reboots etc.!)

---

### Post by reddino on 2010-08-03
> **acermobile said:**
> I have just installed the 2.6.34 kernel and while I am not 100% sure about the following results, I am still optimistic about these points:
- less fan activity (NOTE: I do not see much fan acitivity with 2.6.32-22 and others, too)


Fan activity depends most on bios version: with 1.24 on battery it was always spinning at low speed whilst with 1.17 it start and stops. On AC power it's always ON.

---

### Post by almozavr on 2010-08-03
The new kernel 2.6.35 was released with many improvements for Intel chipset :) Who wants to be a tester? Look here:
[http://www.ubuntugeek.com/kernel-2-6-35-officially-available-for-ubuntu-10-04.html](http://www.ubuntugeek.com/kernel-2-6-35-officially-available-for-ubuntu-10-04.html)

---

### Post by haywire.dk on 2010-08-09
I just found another 1.2W of power saving trick in my 3810T, bringing my minimum power usage down from 7.0W to 5.8W.

Powertop used to show the Intel graphics chip as generating 60 interrupts/second:
         51,3% ( 60,0)   [i915@pci:0000:00:02.0] <interrupt>
But if I do a Suspend-to-RAM (Fn-F4) and wake it up again the 60Hz interrupt from i915 disappears and my power usage drops 1.2 Watts.

Now, the odd thing is that if I start a new instance of Powertop the 60Hz i915 interrupts returns and power usage goes up by 1.2W again. It seems that Powertop is probing the hardware and triggering the i915 60Hz interrupt.
The i915 interrupts is described on Powertop's homepage [http://www.lesswatts.org/projects/powertop/known.php#intelgfx]("http://http://www.lesswatts.org/projects/powertop/known.php#intelgfx") but the documented fix (setting "NoDRI" in xorg.conf) doesn't seem to do anything.

My 3810T is configured as follows:
Ubuntu 10.04 with kernel 2.6.32-24 and backports for wireless and alsa.
Compiz configured to minimum bells and whistles.
Core2 Solo CPU U3500@1.40GHz; Harddisk replaced with Intel SSD.
Fan disabled by disconnecting it from the motherboard.  (I'm running a temperature monitor that will hibernate the laptop if it reaches 75°C).

---

### Post by redsk on 2010-08-11
Hi people,

I've bought this notebook in october 2010. I had to send it to support because the monitor died after two months. Now I've another problem: every now and then the sata hard disk connector doesn't work well and I loose the disk. I suspect that this is a mechanical problem related to the connector, in fact if I open the disk bay, uninstall the disk and reinstall it, the disk starts working again. Sometimes just some gentle hits to the disk bay solve the situation. 

Does someone have the same problem?

It would be a hell to send my laptop to tech support because I've just moved to Spain and I've bought it in Italy and because I've just begun a new job and I really need it everyday now... :(

Niki

PS: sorry for the OT but I really don't know where to ask for such an advice.

---

### Post by JaimeJB on 2010-08-22
Hi,
I commented here one year ago. In this time I had to repair it twice for various motives related with hardware fabric problems...

Right now I am trying to do this with no success:
[http://superuser.com/questions/178375/full-ubuntu-install-on-usb](http://superuser.com/questions/178375/full-ubuntu-install-on-usb)

Has anyone here managed to do a full Ubuntu Install on the USB? 
Don't you get boot problems? 
Could please explain me the steps followed and the Acer specs you have?

Thanks a lot.

---

### Post by almozavr on 2010-08-22
> **JaimeJB said:**
> Hi,
I commented here one year ago. In this time I had to repair it twice for various motives related with hardware fabric problems...

Right now I am trying to do this with no success:
[http://superuser.com/questions/178375/full-ubuntu-install-on-usb](http://superuser.com/questions/178375/full-ubuntu-install-on-usb)

Has anyone here managed to do a full Ubuntu Install on the USB? 
Don't you get boot problems? 
Could please explain me the steps followed and the Acer specs you have?

Thanks a lot.

You should use compatible with BIOS usb flash drive. For example, I didn't succeeded with Kingston 8 GB Datatraveller II but had no problems with Transcend 2 GB. Good luck ;)

---

### Post by JaimeJB on 2010-08-22
> **almozavr said:**
> You should use compatible with BIOS usb flash drive. For example, I didn't succeeded with Kingston 8 GB Datatraveller II but had no problems with Transcend 2 GB. Good luck ;)

Hi, 
could you please elaborate a bit more? Like, which process did u follow, which BIOS do u have (I have 1.10), etc.

The USBs I am using are Verbatim, I can create live USBs but booting from BIOS does not seem to fully work. (as explained here [http://superuser.com/questions/178375/full-ubuntu-install-on-usb](http://superuser.com/questions/178375/full-ubuntu-install-on-usb))

Thanks for replying.

---

### Post by almozavr on 2010-08-22
> **JaimeJB said:**
> Hi, 
could you please elaborate a bit more? Like, which process did u follow, which BIOS do u have (I have 1.10), etc.

The USBs I am using are Verbatim, I can create live USBs but booting from BIOS does not seem to fully work. (as explained here [http://superuser.com/questions/178375/full-ubuntu-install-on-usb](http://superuser.com/questions/178375/full-ubuntu-install-on-usb))

Thanks for replying.

I have BIOS v. 1.27. The steps I followed are ordinary ones. Simple install and nothing else. I think U should try install it to another usb flash drive. I had no problems with transcend 4GB

---

### Post by JaimeJB on 2010-08-23
> **almozavr said:**
> I have BIOS v. 1.27. The steps I followed are ordinary ones. Simple install and nothing else. I think U should try install it to another usb flash drive. I had no problems with transcend 4GB

Hi, could you confirm you have an Acer 3810T as well? I cannot find BIOS v 1.27 for it, where did you downloaded it? 
Also, are you using IDE mode or AHCI mode? It may have something to do with it. 
I will try to install it to another USB, but I don't see how that can be the problem.

---

### Post by JaimeJB on 2010-08-23
> **JaimeJB said:**
> Hi, could you confirm you have an Acer 3810T as well? I cannot find BIOS v 1.27 for it, where did you downloaded it? 
Also, are you using IDE mode or AHCI mode? It may have something to do with it. 
I will try to install it to another USB, but I don't see how that can be the problem.

Problem solved. The Verbatim USBs are OK. The problem was that the USB didn't connect properly. My mistake :)

---

### Post by dbingham on 2010-08-24
I'm experiencing a Black screen of death problem with my Timeline 3810T.  I've found instructions that suggest  a BIOS update could at least temporarily fix the problem.  However, I have to flash the BIOS from a flash drive.  Anyone have directions for flashing the BIOS from a flash drive when I cannot see anything on the display?

---

### Post by dbingham on 2010-08-25
Never mind, have now flashed the bios to the latest version.  Didn't help the dead monitor.  I think its just the backlight that's gone out.  Anyone happen to know of a way to revive the backlight with out replacing the whole screen?

---

### Post by almozavr on 2010-08-31
> **dbingham said:**
> Never mind, have now flashed the bios to the latest version.  Didn't help the dead monitor.  I think its just the backlight that's gone out.  Anyone happen to know of a way to revive the backlight with out replacing the whole screen?

I had the same problem. Resolved in service center by screen replacing.

---

### Post by wesselvanpersie on 2010-09-01
I'm planning to install Ubuntu on my 3810T single core.

I'm a little worried about all the possible problems that might occur.
Can I check if all the hardware works fine without removing the pre-installed windows?
If it all works fine I like to run windows, deny the EULA, and make a photo with my camera of the "denied" screen, so I can get a windows refund.

Should I go for ubuntu x64, x32, or netbook edition?

Notebook specifications:
Display: 13.3" WXGA LED, resolutie 1366x768
Processor: Mobile Intel ULV Core 2 Solo SU3500 Single-Core (1.40GHz)
Bussnelheid: 800MHz * L2 Cache: 3MB * Chipset: Intel GS45
Geheugen: 4GB (2x2GB) DDR3 SODIMM (Max. 8GB)
Videokaart: Intel GMA 4500MHD
Harddisk: 320GB SATA
LAN: 100Mbit
WLAN: 802.11 b/g/n
Bluetooth
VGA-out, Microfoon-in
3x USB2.0
1x HDMI
5-in-1 Cardreader
1.0 Megapixel webcam
6-Cells batterij
Microsoft Windows 7 Home Premium 64-bit
Size: 322x228x23.4-28.9mm
Weight: 1.60kg

---

### Post by yuki86 on 2010-09-02
[COLOR="red"]GREAT NEWS!
FAN PROBLEM SOLVED![/COLOR]

I have 3810t (without ati) running kubuntu 10.04 (same like ubuntu, except Gnome)
I have downgraded [COLOR="Red"]BIOS [/COLOR]via windows installer to its first[COLOR="red"] version 1.04[/COLOR] - now I can barely hear the fan when of A/C :)))

I would be glad if someone other can confirm that too..
Cheers

edit: it stars turning faster time to time just for several secs.. but still worth it

---

### Post by dollzii on 2010-09-06
Anybody ever encountered the "black screen of death" with the 3810T? I have a problem with the backlight on my screen and the only explanation is this so-called "Black screen of death".

So, does anybody know of any fixes or do I have to buy a new monitor?

---

### Post by idreamer on 2010-09-07
> **dollzii said:**
> Anybody ever encountered the "black screen of death" with the 3810T? I have a problem with the backlight on my screen and the only explanation is this so-called "Black screen of death".

So, does anybody know of any fixes or do I have to buy a new monitor?
if you have garantee send it to acer and say that you have this problem and problem with stop charge battery at 89% and acer in one week send back you laptop with new screen and you battery!

---

### Post by dollzii on 2010-09-08
Thanks for reply.

---

### Post by seabra on 2010-09-09
Good morning my dear fellow users of the acer timeline 3810T!):P

A year ago i bought this computer and to my susprise the vt-x flag was disabled.#-o
Using the EFI trick i was able to enable it but i was forced to keep the BIOS version 1.08 
Now for several reasons I would like to update to the latest version but the vt-x is a must for me.
Does anyone know if vt-x is still disabled in the latest version?
Does anyone know if i update the vt-x flag will be disabled or since I enabled it it will remain enabled after the update?

If anyone has the latest version with vt-x patch could he/she make it available to me? ;)

Kind Regards,
 Seabra

---

### Post by anywhere88 on 2010-09-11
> **yuki86 said:**
> [COLOR="red"]GREAT NEWS!
FAN PROBLEM SOLVED![/COLOR]

I have 3810t (without ati) running kubuntu 10.04 (same like ubuntu, except Gnome)
I have downgraded [COLOR="Red"]BIOS [/COLOR]via windows installer to its first[COLOR="red"] version 1.04[/COLOR] - now I can barely hear the fan when of A/C :)))

I would be glad if someone other can confirm that too..
Cheers

edit: it stars turning faster time to time just for several secs.. but still worth it

It sounds strange to me, i've that bios version and my fan never turns on at all (at startup i get 40°C while in windows it's about 27), are you sure it is not always off? Which previous bios did you have?
Is there anyone who can say if there is there is any way to fix all fan problems (both always on and off)?

---

### Post by yuki86 on 2010-09-12
Hi I have bought 3810t in june 2009, there had to be 1.04 bios. Time to time the fan starts in both win/linux. Then my laptop had to be repaired and they upgraded the bios .. fan was always on .. week ago I have upgraded to newest version .. fan always on .. 

i downgraded..
with 1.04 (first version) I only can hear the harddrive spinning..(win/linux)
when playing youtube, video, fan go on..

when charging in is always on..

..but it seems strange to me that your fan is always off, why they put a fan there when it could be always off?

---

### Post by anywhere88 on 2010-09-12
> **yuki86 said:**
> Hi I have bought 3810t in june 2009, there had to be 1.04 bios. Time to time the fan starts in both win/linux. Then my laptop had to be repaired and they upgraded the bios .. fan was always on .. week ago I have upgraded to newest version .. fan always on .. 

i downgraded..
with 1.04 (first version) I only can hear the harddrive spinning..(win/linux)
when playing youtube, video, fan go on..

when charging in is always on..

..but it seems strange to me that your fan is always off, why they put a fan there when it could be always off?

Sorry...my bad, my current bios is 1.14, the assistance service upgraded it some time ago when i sent this laptop to them to fix several problems. To tell the truth i didn't try on battery mode, but while charging the fan is off for sure, i've seen others have this problem (even if the main one is the opposite, the always-spinning-fan).
Unfortunately there's no changelog about bios versions... do you think it is safe to go back to the first bios? I would not install something with several bugs...

---

### Post by seabra on 2010-09-16
So to answer about the vt-x flag question:

After upgrading to the latest bios version the vt-x flag remained active.

There seems to be a new bios version (1.28 )  with the so much needed improved battery charging performance.

Regards,

Seabra

---

### Post by crsde on 2010-09-24
Hi!

I have T3810TG, Bios v.1.28

I added "i8042.reset=1" parameter, suspend still does'nt work good.
Notebook correctly wakes up from suspend only one time. Second time, i a black screen appears :(

---

### Post by acermobile on 2010-09-25
Here are some Kubuntu Maverick Meerkat 10.10 Beta impressions:
1.) Suspend still requires aboves fix
2.) Everything else works out of the box :)
3.) Audio is cumbersome. PulseAudio will only let you control the Master Volume. However, headphones and internal speaker are no longer seperately available (tried configurations)
WORKAROUND: use alsamixer to manually mute internal speakers (pain in the butt...)
4.) Very fast boot up time
5.) Significant improvement over previous releases in terms of the overall integration of the Desktop Environment.
6.) I cannot find a performance decay.
7.) After software source update the proprietary ATI driver could easily be installed using jockey and worked immediately after a reboot.

Hope this is of help for some of you that are eagerly waiting for the release on Oct 10th...

ADDED:
Some additional information:
- Flash Player installation: Download the 64bit flash player from adobe.com and copy the libflash...so to /usr/lib64/mozilla/plugins. Restart Firefox and enjoy.
- Sun Java Runtime Environment: follow the descriptions on [http://www.liberiangeek.net/2010/09/install-sun-java-runtime-environment-jre-ubuntu-10-10-maverick-meerkat/](http://www.liberiangeek.net/2010/09/install-sun-java-runtime-environment-jre-ubuntu-10-10-maverick-meerkat/)
- Many of the multimedia libraries/codecs now install during the main installation (user is prompted for it) -> much improved user friendlyness
- Proxy configuration not working perfectly (sometimes it works, sometimes it does not; Firefox can however find the settings; Rekonq seems to be most sensitive to it)
- NetworkManager Applet has great look and feel; will have to find out, whether it works smooth in the future (so far it does)

---

### Post by acermobile on 2010-09-27
More on Maverick usage:
a.) RealPlayer on 64bit systems:
Install using dpkg --force-all -i RealPlayer11GOLD.deb
b.) Audio Controls:
Install pavucontrol. Run pavucontrol to control the stream that is being used bei KMIX (or stick with alsamixer if you don't bother the console...)
c.) Eats some CPU time (I don't know where and why! I have been using KDE 4.5 before)

I am thus waiting for some updates to come along, but it works (no major crashes so far)

---

### Post by megaexception on 2010-10-11
upgraded to 10.10. as already mentioned, everything is rather fine.
only inconvenience i've found is pulse/kmix:
* only master channel
* logarithmic scale (at low volume levels, vol. up/down keys change volume to much)

also, since 2.6.34 vgaswitcheroo is in kernel!
it means i maverick we can change vga cards without need to reboot and changing bios settings.

i've written small script:

> 
#!/bin/bash

MAGICFILE="/sys/kernel/debug/vgaswitcheroo/switch"

case $1 in
        intel|integrated)
                echo -n DIGD > ${MAGICFILE}
                ;;
        ati|radeon|discreete)
                echo -n DDIS > ${MAGICFILE}
                ;;
        off)
                echo -n OFF > ${MAGICFILE}
                ;;
        *)
                cat ${MAGICFILE}
                ;;
esac


it can switch vga card back and forth, and it mostly works (i haven't tested much, but i've managed to switch to ati, and even hardware accelerated video decoding is working!)

single problem - you must stop/start X manually (or add /etc/init.d/?dm stop/start to script actions).

---

### Post by ohadbasan on 2010-10-12
am I the only one with this pc who has problems with cpufreq under mavrick64?

sudo cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq

it doesn't drop below 1.4ghz

---

### Post by megaexception on 2010-10-12
> **ohadbasan said:**
> am I the only one with this pc who has problems with cpufreq under mavrick64?

sudo cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq

it doesn't drop below 1.4ghz


i think yes. on my 3810tg i see 800MHz (on battery):

> 
# cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq
800000


---

### Post by Waklevören on 2010-10-12
*nothing to see here*

---

### Post by Waklevören on 2010-10-13
Nevermind my previous post. 

I tried adding i8042.reset=1 to Grub to enable suspend on the 3810T. However, the only result I get is that no form of suspend/hibernate is available. The only alternatives I get in Power Management is "blank screen" and "shutdown". I've checked, doublechecked, used scripts to add it the right way etc etc. No change. 

Using Maverick 64-bit.

---

### Post by megaexception on 2010-10-15
yesterday i've updated system (maverick current).

results:
1) suspend/hibernate now DOESN'T WORK.
switches to console for 5 secs, then back.
i see following in dmesg:

> Oct 15 08:18:07 t00l kernel: [  300.874641] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
Oct 15 08:18:09 t00l kernel: [  303.091517] PM: Syncing filesystems ... done.
Oct 15 08:18:29 t00l kernel: [  303.150447] Freezing user space processes ...
Oct 15 08:18:30 t00l kernel: [  323.170135] modprobe      D ffff88013b7910f8     0   482      1 0x00800004
Oct 15 08:18:30 t00l kernel: [  323.170145]  ffff880123315d48 0000000000000086 ffff880121fed000 0000000000015980
Oct 15 08:18:30 t00l kernel: [  323.170154]  ffff880123315fd8 0000000000015980 ffff880123315fd8 ffff8801232cadc0
Oct 15 08:18:30 t00l kernel: [  323.170163]  0000000000015980 0000000000015980 ffff880123315fd8 0000000000015980
Oct 15 08:18:30 t00l kernel: [  323.170171] Call Trace:
Oct 15 08:18:30 t00l kernel: [  323.170182]  [<ffffffff81587dd7>] __mutex_lock_slowpath+0xf7/0x180
Oct 15 08:18:30 t00l kernel: [  323.170190]  [<ffffffff81388026>] ? really_probe+0xb6/0x190
Oct 15 08:18:30 t00l kernel: [  323.170212]  [<ffffffff81388170>] ? __driver_attach+0x0/0xa0
Oct 15 08:18:30 t00l kernel: [  323.170218]  [<ffffffff81587cbb>] mutex_lock+0x2b/0x50
Oct 15 08:18:30 t00l kernel: [  323.170225]  [<ffffffff813881c9>] __driver_attach+0x59/0xa0
Oct 15 08:18:30 t00l kernel: [  323.170232]  [<ffffffff81388170>] ? __driver_attach+0x0/0xa0
Oct 15 08:18:30 t00l kernel: [  323.170238]  [<ffffffff81387418>] bus_for_each_dev+0x68/0x90
Oct 15 08:18:30 t00l kernel: [  323.170246]  [<ffffffff81387e4e>] driver_attach+0x1e/0x20
Oct 15 08:18:30 t00l kernel: [  323.170251]  [<ffffffff8138770e>] bus_add_driver+0xde/0x280
Oct 15 08:18:30 t00l kernel: [  323.170260]  [<ffffffff81388550>] driver_register+0x80/0x150
Oct 15 08:18:30 t00l kernel: [  323.170268]  [<ffffffff8158d176>] ? notifier_call_chain+0x56/0x80
Oct 15 08:18:30 t00l kernel: [  323.170278]  [<ffffffff812d8506>] __pci_register_driver+0x56/0xd0
Oct 15 08:18:30 t00l kernel: [  323.170286]  [<ffffffff81084f05>] ? __blocking_notifier_call_chain+0x65/0x80
Oct 15 08:18:30 t00l kernel: [  323.170299]  [<ffffffffa007b000>] ? alsa_card_azx_init+0x0/0x20 [snd_hda_intel]
Oct 15 08:18:30 t00l kernel: [  323.170310]  [<ffffffffa007b01e>] alsa_card_azx_init+0x1e/0x20 [snd_hda_intel]
Oct 15 08:18:30 t00l kernel: [  323.170318]  [<ffffffff8100204c>] do_one_initcall+0x3c/0x1a0
Oct 15 08:18:30 t00l kernel: [  323.170327]  [<ffffffff8109bc6b>] sys_init_module+0xbb/0x200
Oct 15 08:18:30 t00l kernel: [  323.170335]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b
Oct 15 08:18:30 t00l kernel: [  323.170399]
Oct 15 08:18:30 t00l kernel: [  323.170402] Restarting tasks ... done.
Oct 15 08:18:30 t00l kernel: [  323.193412] video LNXVIDEO:00: Restoring backlight state
Oct 15 08:18:30 t00l kernel: [  323.193831] video LNXVIDEO:01: Restoring backlight state
Oct 15 08:18:30 t00l kernel: [  323.260123] Skipping EDID probe due to cached edid
Oct 15 08:18:32 t00l kernel: [  325.440415] lenovo_acpi: disabled the discrete graphics card
Oct 15 08:18:32 t00l kernel: [  325.453821] atl1c 0000:03:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
Oct 15 08:18:33 t00l kernel: [  326.810058] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,user_xattr,commit=600


2) fn-keys now DOESN'T work!
most keys (fn-F2, FN-F3, etc) now are doing same function: making my system hang. even sysrq keys do not work.

3) few times system got hang without any user intervention.
i've leaved notebook powered on for few hours, and when i've returned it was deadly hang

i've only one question. why? why every new ubuntu brings only bugs, problems, and only cosmetic changes (i hate this 'new' 'features')?

UPDATE: my problems were caused by conflict between "radeon" and "lenovo_acpi" kernel modules, which caused to hang modprobe process, which caused to not load/unload some modules when they were needed.
adding "radeon" to modprobe.d/blacklist.conf helped.

---

### Post by chrisjsmith on 2010-10-23
If anyone is interested, I'm selling my 3810TZ.  I'm based on London, UK.

I can pre-install Ubuntu if anyone wants me to.  10.04 works perfectly on mine.  Will do the inevitable powertop run on it and I get about 6-7 hours battery life.

Details including contact details here:

[http://www.gumtree.com/london/38/67334338.html](http://www.gumtree.com/london/38/67334338.html)

---

### Post by jmtritch on 2010-10-24
This is a post in response to the black screen of death that some users are experiencing in their acer 3810XX laptops.  I also had this problem, but have fixed it without having to send the laptop in for a screen replacement.

In my laptop, part of the screen would go dark if I pressed on the lower right side of the laptop.  I removed the screen following these insructions:

[http://www.insidemylaptop.com/replace-broken-screen-acer-aspire-3810t-laptop/](http://www.insidemylaptop.com/replace-broken-screen-acer-aspire-3810t-laptop/)

When I looked at the section where I could press I found a belt that connects the screen circuit board to the screen.  It's orangish-brown and color and is bent at a 90 degree angle when it goes from the circuit board to the screen.  It's about 8 mm wide and was the source of my black screen of death.

If I pressed on the belt where it was bent, then the screen would go dark.  As a solution, I placed a bit of cotton from a Q-tip between the kink.  The cotton is non-conducting (so you won't fry your circuit board) and it takes pressure off the kink to allow the electric signals to easily travel from the circuit board to the screen.

Since inserting the cotton my screen is black-screen free and works like a charm, even when I press on the back of the screen.  Sending in your laptop to acer for a full screen replacement might be a better option, but I live in Africa, so sending it it isn't really an option.

---

### Post by jmtritch on 2010-10-24
> **dbingham said:**
> I'm experiencing a Black screen of death problem with my Timeline 3810T.  I've found instructions that suggest  a BIOS update could at least temporarily fix the problem.  However, I have to flash the BIOS from a flash drive.  Anyone have directions for flashing the BIOS from a flash drive when I cannot see anything on the display?

This is a post in response to the black screen of death that some users are experiencing in their acer 3810XX laptops. I also had this problem, but have fixed it without having to send the laptop in for a screen replacement.

In my laptop, part of the screen would go dark if I pressed on the lower right side of the laptop. I removed the screen following these insructions:

[http://www.insidemylaptop.com/replac...-3810t-laptop/](http://www.insidemylaptop.com/replac...-3810t-laptop/)

When I looked at the section where I could press I found a belt that connects the screen circuit board to the screen. It's orangish-brown and color and is bent at a 90 degree angle when it goes from the circuit board to the screen. It's about 8 mm wide and was the source of my black screen of death.

If I pressed on the belt where it was bent, then the screen would go dark. As a solution, I placed a bit of cotton from a Q-tip between the kink. The cotton is non-conducting (so you won't fry your circuit board) and it takes pressure off the kink to allow the electric signals to easily travel from the circuit board to the screen.

Since inserting the cotton my screen is black-screen free and works like a charm, even when I press on the back of the screen. Sending in your laptop to acer for a full screen replacement might be a better option, but I live in Africa, so sending it it isn't really an option.  I hope this helps you.

---

### Post by miegiel on 2010-10-24
> **jmtritch said:**
> This is a post in response to the black screen of death that some users are experiencing in their acer 3810XX laptops. I also had this problem, but have fixed it without having to send the laptop in for a screen replacement.

In my laptop, part of the screen would go dark if I pressed on the lower right side of the laptop. I removed the screen following these insructions:

[http://www.insidemylaptop.com/replac...-3810t-laptop/](http://www.insidemylaptop.com/replac...-3810t-laptop/)

When I looked at the section where I could press I found a belt that connects the screen circuit board to the screen. It's orangish-brown and color and is bent at a 90 degree angle when it goes from the circuit board to the screen. It's about 8 mm wide and was the source of my black screen of death.

If I pressed on the belt where it was bent, then the screen would go dark. As a solution, I placed a bit of cotton from a Q-tip between the kink. The cotton is non-conducting (so you won't fry your circuit board) and it takes pressure off the kink to allow the electric signals to easily travel from the circuit board to the screen.

Since inserting the cotton my screen is black-screen free and works like a charm, even when I press on the back of the screen. Sending in your laptop to acer for a full screen replacement might be a better option, but I live in Africa, so sending it it isn't really an option.  I hope this helps you.

Well, that was fun. I managed to fry the LCD inverter (the electronics sticking out at the bottom of the LCD) in the process. It turns out to be not that smart to dis/connect the LCD while the laptop is on :twisted: Regardless, I couldn't get the leds to stay on anyway. They'd blink on and off, that was all. But you're right, it is that connection strip. The strip on my screen wasn't folded at the right place (between the 2 indents at the side, see pics below). I think the strip broke because of pressure on the lid (stuff in my bag pushing against it). It might not have happened if it was folded at the right place.

A tip for those of you who are going to try to remove the screen. Start by pulling the top hooking your nails under the frame from the top side pushing the plastic frame around the screen downward. Then loosen the sides hooking your nails on the outside and pulling outwards. Next loosen the frame where it wraps around the lid hinges. You don't need to be afraid to use to much force, the clips here are reasonably strong. Finally you need to loosen the bottom part of the frame pushing it to the center of the screen. These clips break easily (I broke a few not knowing in which direction to loosen the bottom part). Best is to almost close the lid and loosen the bottom frame carefully from the backside.

As 2/3rds of the leds of my screen didn't work, I was already considering a replacement for this cheap piece of plastic junk. Now I need to decide if it will be an [ASUS Eee PC T101MT]("http://www.asus.com/product.aspx?P_ID=xK9O0XZhFswxrTrn") or a [Neo FreeRunner]("http://wiki.openmoko.org/wiki/Neo_FreeRunner"). Ordering a new screen will cost about e250.- but my 3810T doesn't deserve that much affection. It's going to be nailed to the wall as my new eco-server (8-12W isn't bad for a server) and isn't allowed to play outside the house for the rest of it's life.

Needless to say. Acer? Never again! [-X

---

### Post by endofwed on 2010-10-25
Many thanks to jmtritch and miegiel!

I've had this problem once before and was able to send it in for a warranty repair. Now I'm experiencing the same problem but the warranty has expired. I'm a poor college student and was desperately looking for a inexpensive DIY fix but almost gave up hope when I couldn't find anything until I saw your post!

Do you know if I could purchase that 8mm cable from acer? I've tried ebay but no luck. I think I might have have permanent destroyed or bent it since when I had this problem the first time around, I would still be able to get the back light to go on if I pressed or released some pressure on the lower right hand screen. Now, It doesn't work anymore and I hear a clicking sound coming from that area where the cord is.

Thank you!

[IMG]http://farm2.static.flickr.com/1345/5113722649_136656a09f_z.jpg[/IMG]

---

### Post by miegiel on 2010-10-25
> **endofwed said:**
> ... snip ...

Do you know if I could purchase that 8mm cable from acer? I've tried ebay but no luck. I think I might have have permanent destroyed or bent it since when I had this problem the first time around, I would still be able to get the back light to go on if I pressed or released some pressure on the lower right hand screen. Now, It doesn't work anymore and I hear a clicking sound coming from that area where the cord is.

Thank you!

The answer is: "No"

The ribbon cable runs into the LCD panel. I opened the LCD panel , no harm done since I fried it already. :twisted: Don't do this if you want to keep using the LCD panel, even if you have a [cleanroom]("http://en.wikipedia.org/wiki/Cleanroom"). I just did it to take a look inside, to see where the ribbon goes. There's a double layered foil (silver on the outside, black on the inside) around the panel's edge to prevent backlight bleeding. You need super powers to remove the foil without stretching or breaking it and putting it back properly.

The ribbon runs into the LCD panel's corner and along the bottom edge of the panel. The LED's are soldered onto the ribbon (see pic below). Yeah, the LCD is totally wrecked now.
:lolflag:

As for DIY fixes. 1st I'd suggest you to put a thin piece of cardboard, or a piece of paper folded 2 or 3 times into the fold of the ribbon (see the 1st pic in my previous post). For those who don't have dead LEDs yet it could prevent the failure and it might help when the LEDs start to fail. If that doesn't help the only fix I can think of (besides getting a new panel) is to cut the ribbon and reconnect the 2 parts by soldering them together again using thin (but not to thin) wires. When you do this you should reroute the ribbon to the empty space below the panel, else the panel might get damaged from pressure to the lid. Make a photo or a sketch, so you know how the copper lanes are connected before you cut the ribbon.

Good luck.

---

### Post by dsz on 2010-11-14
hi everyone

does anybody know how to enable HARDWARE ACCELERATED H264 video PLAYBACK in lucid or maverick?
I have intel GMA 4500MHD in my acer 3810T laptop.

vainfo command shows only mpeg2 profiles...
:confused:

thank you!
dsz

---

### Post by qnano on 2010-11-24
> **anywhere88 said:**
> It sounds strange to me, i've that bios version and my fan never turns on at all (at startup i get 40°C while in windows it's about 27), are you sure it is not always off? Which previous bios did you have?
Is there anyone who can say if there is there is any way to fix all fan problems (both always on and off)?

Other people have also mentioned that the fan problem can be fixed by downgrading the BIOS to earlier versions. I think I'm gonna give it a go. Do I need to downgrade stepwise from BIOS version 1.28, or can I go to 1.04 for instance directly? Thanks.

---

### Post by miegiel on 2010-11-24
> **qnano said:**
> Other people have also mentioned that the fan problem can be fixed by downgrading the BIOS to earlier versions. I think I'm gonna give it a go. Do I need to downgrade stepwise from BIOS version 1.28, or can I go to 1.04 for instance directly? Thanks.

If you changed any settings in the BIOS you should load the defaults in the BIOS before you flash. If you do, you're probably safe. Also remove any BIOS passwords if you set any.

I haven't read about anyone bricking their laptop by a bad flash, but there's always a risk. When BIOSes are tested (AFAIK) they only test if BIOSes can be upgraded to the new BIOS and not the other way around.

---

### Post by Arlanthir on 2010-11-25
> **miegiel said:**
> If you changed any settings in the BIOS you should load the defaults in the BIOS before you flash. If you do, you're probably safe. Also remove any BIOS passwords if you set any.

I haven't read about anyone bricking their laptop by a bad flash, but there's always a risk. When BIOSes are tested (AFAIK) they only test if BIOSes can be upgraded to the new BIOS and not the other way around.

Careful, I have bricked a 4810T that way.
I've seen recommendations to flash it from a DOS live cd instead of Windows, they say it's safer. 

Bottomline is, at least when I needed it, there was no BIOS recovery method. I had to turn in my device to warranty (they just traded it for a new one because it was the second day).

---

### Post by Tamrac on 2010-12-17
Hello group. I've just installed Ubuntu 10.10 on my 3810T the other day... I've got a few minor issues.

I can't get the SD car reader to work. Inserting an SD card does nothing. 

And how do I monitor for power consumption?

Thanks in advance guys.

---

### Post by miegiel on 2010-12-18
> **Tamrac said:**
> Hello group. I've just installed Ubuntu 10.10 on my 3810T the other day... I've got a few minor issues.

I can't get the SD car reader to work. Inserting an SD card does nothing. 

And how do I monitor for power consumption?

Thanks in advance guys.

Did you try mounting it manually? Maybe the card is just not being automatically detected.

---

### Post by Tamrac on 2010-12-18
> **miegiel said:**
> Did you try mounting it manually? Maybe the card is just not being automatically detected.

Thanks for the reply. Yes, but still no go... :( Any way to make Ubuntu re-detect the sd-card reader?

---

### Post by dollzii on 2010-12-20
Hey guys!
Just got my 3810t back from acer norway, they fixed the so-called Black screen of death for me. When I try booting into ubuntu I get the error:

```
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /dev on /root/dev failed: No such file or directory

Target filesystem doesn't have /sbin/init
```

I've read that I need to boot into a live USB and run fsck but I can't get my system to boot my USB stick. I remember that I had some problems getting the USB to boot when I first installed Ubuntu but I found a workaraound, and now I can't remember what it was. I remember that I changed some sys file in my Vista partition (?) 

My question is, can anybody help me with the booting issue or is there a way to fix this from the command prompt that comes up after the error message? 

Thanks a bunch for any reply!

---

### Post by theasprint on 2010-12-20
Hi, 

I have a 3810T as well, not TG, not 4810.

And I installed Ubuntu 10.04 as its sole OS.

And everything seems fine.

---

### Post by Tamrac on 2010-12-21
> **theasprint said:**
> Hi, 

I have a 3810T as well, not TG, not 4810.

And I installed Ubuntu 10.04 as its sole OS.

And everything seems fine.

Have you tested the SD-card reader? That's the only hardware on the unit that does not work for me on Ubuntu 10.10

---

### Post by Tamrac on 2010-12-22
> **Tamrac said:**
> Have you tested the SD-card reader? That's the only hardware on the unit that does not work for me on Ubuntu 10.10

Ignore this one.... Already fixed the problem. =)

---

### Post by jimmy the saint on 2011-01-06
3810T and fresh maverick install.

The two finger scrolling option is greyed out, so I can't even enable it, much less activate the fix.

Any ideas?

---

### Post by miegiel on 2011-01-06
> **jimmy the saint said:**
> 3810T and fresh maverick install.

The two finger scrolling option is greyed out, so I can't even enable it, much less activate the fix.

Any ideas?

[https://help.ubuntu.com/community/AspireTimeline/Fixes](https://help.ubuntu.com/community/AspireTimeline/Fixes)
scroll down to "Touchpad Multitouch"
scroll on to "10.04"

Works on maveric too.

---

### Post by almozavr on 2011-01-07
> **jimmy the saint said:**
> 3810T and fresh maverick install.

The two finger scrolling option is greyed out, so I can't even enable it, much less activate the fix.

Any ideas?

You can use my script ;)
It enables 2 finger scrolling, 2 finger tap, smooth movements, etc.

---

### Post by TompsonX on 2011-01-07
Hi,

Just wanted to share info about modded bios v1.28 for acer 3810. Unlocked additional options in BIOS setup, added intel only (or integrated) graphics option and modified fan table. Look here for more info:
[http://forum.notebookreview.com/acer/391646-acer-aspire-timeline-owners-lounge-202.html#post6953880](http://forum.notebookreview.com/acer/391646-acer-aspire-timeline-owners-lounge-202.html#post6953880)

---

### Post by jimmy the saint on 2011-01-08
> **miegiel said:**
> [https://help.ubuntu.com/community/AspireTimeline/Fixes](https://help.ubuntu.com/community/AspireTimeline/Fixes)
scroll down to "Touchpad Multitouch"
scroll on to "10.04"

Works on maveric too.

I have that set up.  If memory serves, this fixed the erratic mouse movement when two finger scrolling was activated.  I don't even have the option to activate it because it is greyed out.

---

### Post by miegiel on 2011-01-09
> **jimmy the saint said:**
> I have that set up.  If memory serves, this fixed the erratic mouse movement when two finger scrolling was activated.  I don't even have the option to activate it because it is greyed out.

It  does more than that. The line :
```
xinput set-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 1 1
```
enables vertical and horizontal 2 finger scrolling (change 1's to 0's to disable).

In xubuntu in the graphical mouse configuration tool doesn't have a two finger scrolling option. But what I remember from the last time I ran ubuntu, setting two finger scrolling with *xinput* doesn't have an effect on the option being greyed out. It just enables two finger scrolling.

---

### Post by v6o on 2011-01-11
Hi all,

after trying to update from 10.4 to 10.10 (both 64bit) my Timeline 4810 freezes when booting. I cannot even access a shell via Ctrl+Alt+F1.
So I tried the [SIZE=1]fix "[/SIZE][SIZE=1]Alternative fix for 10.10[/SIZE][SIZE=1]"[/SIZE] after booting with a LiveCD, but the issue persists.

Any suggestions? Where/how to apply the fix?

Cheers 
v6o

---

### Post by jimmy the saint on 2011-01-13
alright. Now I'm getting really frustrated.  It turns out the scripts are fine if I run the manually, but not at startup.

---

### Post by miegiel on 2011-01-13
> **jimmy the saint said:**
> alright. Now I'm getting really frustrated.  It turns out the scripts are fine if I run the manually, but not at startup.

How do you run it at startup? With startup scripts (how + post script) or did you edit/create a *.conf* file in */usr/share/X11/xorg.conf.d* (post that *.conf* file)?

---

### Post by HandleWithCare on 2011-01-18
Whenever I do an update that requires a restart. It will startup with a black screen. I use the laptop (4810TG) in descrete graphics mode with the proprietary ati driver (10.11).
When this happen I have to remove /etc/X11/xorg.conf, reboot. Then it will startup, but it uses twice the amount of power and no 2/3d acceleration. Then I have to completely reinstal the atidriver, reboot and then all goes well again. This shouldn't be al that difficult. Does anyone else have this problem and if so, have you found a fix?

---

### Post by Tamrac on 2011-02-16
Ubuntu 10.10 seems to not last as long as my Win7 install.... shorter battery life. I'm curious as to others with 3810T out there on how long the battery lasts with your Ubuntu 10.10 install.

---

### Post by japglish on 2011-02-23
Not sure if anybody is still using this forum but if they have and are looking for a couple of fixes to Maverick - these fixes work for both the Timeline 3810t and Timeline 4810t for me but no guarantee they will work for you.

1) **Brightness** - edit grub line GRUB_CMDLINE_LINUX="" as follows

```
sudo gedit /etc/default/grub
```

edit grub line GRUB_CMDLINE_LINUX="" so that it reads GRUB_CMDLINE_LINUX="acpi_osi=Linux" and update grub

```
sudo update-grub
```

reboot and brightness keys should work properly.

2) **Internal Microphone** (took nearly two years to find this fix) - edit alsa-base.conf

```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

and make sure that you have the following lines at the bottom of the file:

```
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto
```

reboot and that should be the end of that. Model=auto is important for this fix. Skype also works with internal mic with this fix.

Hope this helps.

---

### Post by miegiel on 2011-02-23
> **japglish said:**
> ...

```
[COLOR="Red"]**gk**[/COLOR]sudo gedit /etc/default/grub
```

...

```
[COLOR="Red"]**gk**[/COLOR]sudo gedit /etc/modprobe.d/alsa-base.conf
```

...

One small point: When you want to *sudo* graphical apps, you should always use *gksudo*.

Though with *gedit* it's usually not a problem, you risk breaking a graphical program's configuration if you don't.

---

### Post by acermobile on 2011-03-01
The display on my 3810TGZ is about to die for the third time within 18 months. I am not very confident on the warranty to still apply :-( So hopefully it will last another few weeks. This time the backlight is dying (in parts). Currently, about 30% of the bottom illumination is dead.

My final conclusion is: no more Acer ever ever ever!!!

This is really the most discouraging device I have ever had and has severly pushed me towards buying either something like Lenovo (rock-solid) or one of the recent tablets...

Has anyone had similar experience with the device?

---

### Post by miegiel on 2011-03-01
> **acermobile said:**
> The display on my 3810TGZ is about to die for the third time within 18 months. I am not very confident on the warranty to still apply :-( So hopefully it will last another few weeks. This time the backlight is dying (in parts). Currently, about 30% of the bottom illumination is dead.

My final conclusion is: no more Acer ever ever ever!!!

This is really the most discouraging device I have ever had and has severly pushed me towards buying either something like Lenovo (rock-solid) or one of the recent tablets...

Has anyone had similar experience with the device?

No, I replaced my 3810T with a [ASUS Eee PC T101MT]("http://www.asus.com/product.aspx?P_ID=xK9O0XZhFswxrTrn") netbook-tablet 4 months ago. Not as powerful, but the battery last almost as long, it's 20% lighter, louder speakers and no design flaws I've discovered or read about yet. It even fits in my camera bag. :D Since I wanted a tablet (the classical type with a keyboard) for years, it's obvious that I I'm really happy with it. Though after "that Acer" I would probably be really happy with almost every laptop.

*ps:* If I wouldn't have bought this netbook I would have probably gone for the, 3 times as expensive, 12" thinkpad tablet of Lenovo.

---

### Post by acermobile on 2011-03-02
Interesting. What about the multi-touch (or touch) in Linux? Is it working? If so, what else is working out-of-the-box with ubuntu (or kubuntu)?

---

### Post by miegiel on 2011-03-02
> **acermobile said:**
> Interesting. What about the multi-touch (or touch) in Linux? Is it working? If so, what else is working out-of-the-box with ubuntu (or kubuntu)?

Yes, though not out of the box yet (assuming you mean the touchscreen). But I'm hopeful about natty. It's a bit like with the acer timeline. In the beginning, when the hardware is just released, support is spartan. But after a year, most or all of the essential parts work out of the box.

However this is all a bit off topic for the acer timeline thread. Here are 2 links to feed your curiosity:
[LIST]
[*]Ubuntu on Eee PC T101MT [thread]("http://ubuntuforums.org/showthread.php?t=1468376")
[*]Eee PC T101MT [Community Documentation]("https://help.ubuntu.com/community/T101MT")
[/LIST]
And I'm sure there are similar threads on other convertible tablets.

---

### Post by leonko on 2011-03-06
Hello, I have a problem with booting Usb 11.04 from flash.

I have notebook Acer 3810t with Windows. I burn iso on flash with usb-creator. All copied ok
When I boot from my flash-drive I see only with syslinux info line  and this is all. No flash or hdd activity.
Please help me

---

### Post by miegiel on 2011-03-06
> **leonko said:**
> Hello, I have a problem with booting Usb 11.04 from flash.

I have notebook Acer 3810t with Windows. I burn iso on flash with usb-creator. All copied ok
When I boot from my flash-drive I see only with syslinux info line  and this is all. No flash or hdd activity.
Please help me

I never had any problems booting from USB on the 3810T. Are you sure it's not a natty problem/bug? If so, you should seek help in [the natty sub forum]("http://ubuntuforums.org/forumdisplay.php?f=394").

Ubuntu 11.04 is still in development and still has bugs. If you want to try ubuntu you're recommended to try 10.10 or another stable version. With development versions you run the risk everything works fine today and everything (software not hardware) is broken tomorrow.

---

### Post by leonko on 2011-03-06
> **miegiel said:**
> I never had any problems booting from USB on the 3810T. Are you sure it's not a natty problem/bug? If so, you should seek help in [the natty sub forum]("http://ubuntuforums.org/forumdisplay.php?f=394").

Ubuntu 11.04 is still in development and still has bugs. If you want to try ubuntu you're recommended to try 10.10 or another stable version. With development versions you run the risk everything works fine today and everything (software not hardware) is broken tomorrow.
Yes, it's bug with creater. I write iso with LinuxLive usb creater and all be ok (on ati card)
Thank you. I try 11.04 to watch energe changes from 10.10..

---

### Post by dollzii on 2011-03-11
Hey!

Any of you with the acer 3810t ever set the resolution to over the standard 1366x768?

If any has done this successfully would you mind posting how you did it. I've been trying to change it with xrandr but it just gives me all these error messages. Maybe someone could post their 10-monitors.conf ?

Thanks in advance..

---

### Post by miegiel on 2011-03-11
> **dollzii said:**
> Hey!

Any of you with the acer 3810t ever set the resolution to over the standard 1366x768?

If any has done this successfully would you mind posting how you did it. I've been trying to change it with xrandr but it just gives me all these error messages. Maybe someone could post their 10-monitors.conf ?

Thanks in advance..

Try
```
xrandr --output LVDS1 --scale 1.5x1.5
```

```
xrandr --output LVDS1 --scale 1.0x1.0
```
will set it back to normal

---

### Post by dollzii on 2011-03-11
Thank you very much. That helped, been searching a long time for a solution to this :-)

---

### Post by malebron on 2011-05-12
> **acermobile said:**
> The display on my 3810TGZ is about to die for the third time within 18 months. I am not very confident on the warranty to still apply :-( So hopefully it will last another few weeks. This time the backlight is dying (in parts). Currently, about 30% of the bottom illumination is dead.

My final conclusion is: no more Acer ever ever ever!!!

This is really the most discouraging device I have ever had and has severly pushed me towards buying either something like Lenovo (rock-solid) or one of the recent tablets...

Has anyone had similar experience with the device?

Yup, my backlight died also - but being a fearless DIY-er I took mine apart and fixed it!

It  turns out that the 3810t has a design problem with a mylar ribbon cable  that connects the display panel to the circuit board attached  to its bottom edge. The ribbon is folded to make a 90 degree turn -  right behind the lower right corner of the screen. This fold sits  between the top lid and the back of the panel. Repeated pressure on the  lid (eg if you carry it around) flexes the fold in the ribbon until it  splits across. There are six wires, so the failure can be partial before  it dies completely.

The cable is attached to the panel and leads to a simple connector on the electronics board.

Fearless fix:

This  is a very easy machine to take apart - you can find instructions on the  web, as I did. If you can't do that - and aren't game for some very  fine soldering work - don't attempt!

After you remove the bezel, take out the display panel and locate the broken ribbon cable.

Cut  out out the split/bent area and use an abrasive to expose the copper  tracks in both sides. Solder a short (2") length of regular ribbon cable  (I used a piece cut from an old IDE cable, six wires wide) to re-connect  the two parts. The regular cable is much more resilient. Mine has  lasted several months so far with no problems.

Yes, it requires  quite a tricky bit of soldering - the wires are VERY small and close  together - but is cheap and if you do it right it's fixed for good.

(If you screw up a new panel is <$100)

---

### Post by muadnu on 2011-07-21
I keep having trouble with the wireless in my Acer Timeline 3810T. I'm running Ubuntu 11.04. I thought by now everything should be working OOB, but my wireless adapter keeps getting randomly disabled every once in a while and I can only reboot to get it back.

I tried installing the latest drivers as instructed in ```
https://help.ubuntu.com/community/AspireTimeline/Fixes
```but I still have the same problem. Is anyone else suffering from this? Maybe I missed something?

---

### Post by ohadbasan on 2011-07-29
> **muadnu said:**
> I keep having trouble with the wireless in my Acer Timeline 3810T. I'm running Ubuntu 11.04. I thought by now everything should be working OOB, but my wireless adapter keeps getting randomly disabled every once in a while and I can only reboot to get it back.

I tried installing the latest drivers as instructed in ```
https://help.ubuntu.com/community/AspireTimeline/Fixes
```but I still have the same problem. Is anyone else suffering from this? Maybe I missed something?

Hey dude.
You are not missing anything.
I experience the exact same problem on ubuntu 11.04 and on my arch linux system which is running 2.6.39
It appears that the problem is only when ur computer is connected to a WIRELESS N network. you can either disable you N support on ur router or disable it through your modprobe configuration file. I have no solution for this issue. I think we need to open a bug. I didn't found something similar.

---

### Post by muadnu on 2011-07-29
Thanks for the answer. Yes, maybe we need to open a bug, but the problem is that this seems to have nothing to do with Ubuntu, and probably neither with the kernel, but instead with the Intel driver.

By the way, I don't think it only happens with wireless N networks, it happens for me at home where I'm definitely not using an N network.

---

### Post by ohadbasan on 2011-07-30
> **muadnu said:**
> Thanks for the answer. Yes, maybe we need to open a bug, but the problem is that this seems to have nothing to do with Ubuntu, and probably neither with the kernel, but instead with the Intel driver.

By the way, I don't think it only happens with wireless N networks, it happens for me at home where I'm definitely not using an N network.

plz post ur dmesg.
maybe we are experiencing different issues.
the issue that i am experiencing is 100% related to the wireless-n thingy. I saw many reports on it all over the web. I'm pretty sure that in case it's a drive bug - it should be opened in the kernel's bugzilla or something. the driver is integrated in the kernel.

---

### Post by littlebigman on 2011-08-01
Hello

(I don't know how to search this very long thread for a possible answer to my problem)

I successfuly installed Ubuntu 11.04 through the NetInstall option on an [Aspire 3810T]("http://www.pcworld.com/product/61705/acer_timeline_3810t.html?p=specs") laptop.

Using the default option, the laptop boots OK, I can ssh to it OK, but the screen on the host just displays a blinking cursor. I assume the stock Ubuntu doesn't have the right display driver:

```

root@ubuntu:~# lshw -short
H/W path               Device     Class       Description
=========================================================
/0/100/2                          display     Mobile 4 Series Chipset Integrated Graphics Controller

```

Has someone seen this, and knows what to do?

Thank you.

---

### Post by muadnu on 2011-08-02
> **ohadbasan said:**
> plz post ur dmesg.
maybe we are experiencing different issues.
the issue that i am experiencing is 100% related to the wireless-n thingy. I saw many reports on it all over the web. I'm pretty sure that in case it's a drive bug - it should be opened in the kernel's bugzilla or something. the driver is integrated in the kernel.

So I guess non-N networks work ok for you. Did you do anything after installing, like updating the wireless driver or recompiling, or did it work OOB?

---

### Post by Fallingwater on 2011-09-16
I realize this is the Ubuntu forum, but I can't find the equivalent thread for Debian, so...
I'm running Debian Squeeze on a 3810T, and having a problem: the wifi touch-button disables the wifi as it should, but doesn't enable it again. I can touch it all day and the light stays off. Only solution seems to be a full reboot, which is seven shades of annoying. Is there a fix?

---

### Post by almozavr on 2011-09-16
You could restart your wireless driver instead of rebooting. Something like
*$ sudo modprobe wl*
but I'm not sure. 

The same problem was with my old dell laptop... It seems to be not solved yet but bug is known.

---

### Post by Fallingwater on 2011-09-16
Says "FATAL: Module wl not found"...

Then I pressed the button and it turned on. I WTFed, turned it off and back on, and it worked.
Rebooted, and now doesn't work again.

*breaks down in tears*

---

### Post by almozavr on 2011-09-16
I don't which module is installed on Acer 3810t laptop, but you could also try something like:
[I]modprobe -r iwlagn
modprobe -r iwlcore
modprobe iwlcore
modprobe iwlagn
[/I]

run 'em all in exact sequence ;)

---

### Post by Fallingwater on 2011-09-16
It's iwlagn. Modprobing it returns no error but doesn't bring the wifi back.
However, opening Wicd and scanning available networks does. Thinking about it, it was what I did before when it turned back on. Once I do it once, it's then possible to use the wifi button as intended.

Weird, but I guess it's a workable workaround.

---

### Post by littlebigman on 2011-09-18
Hello,

This thread is now close to 100 pages long, and unless I missed it, there's no way to search within a thread, so I'll have to add a new post.

Ubuntu 11.04 installs OK on my 3810T with BIOS 1.28, but I get a blank screen so can only interact with it from a remote host with SSH.

I assume even 11.04 doesn't have the right video driver for the 3810T ("Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)").

Does someone know how to solve this issue?

Thank you.

---

### Post by Tombuntu81 on 2012-04-25
Hello 

I'm completely new to Ubuntu and am trying to get it on to my Acer 3810T. I have the Ubuntu 11.10 64-bit loaded to my usb stick (using pendrive [http://goo.gl/dI2O5](http://goo.gl/dI2O5)). After the bios splash screen the acer hangs on boot with the message:

SYSLINUX 4.06 EDD 4.06-pre1 Copyright (C) 1994-2011 H. Peter Anvin et al

notes:
The usb boots absolutely fine on my dell Studio laptop
I have flashed the bios to the latest version (1.28 ) 
I have tried switching the SATA mode from AHCI to IDE mode, but see no change.

am out of ideas so any help would be fantastic
Tom

---

### Post by TREESofRIGHTEOUSNESS on 2012-04-25
Did you read the original post, and do what it indicated?  You might spend sometime searching through the 90something pages of this thread....  or hopefully bumping this thread will get someone who knows to answer you

---

### Post by Tombuntu81 on 2012-04-25
Hi

sorry for the slow reply, hadn't realised I was not subscribed to the thread. 

I've only been able to glance through a few pages so far and discussion seems mainly on more detailed issues. I'll spend more time reading through thoroughly now.

thanks for your response
Tom

---

### Post by Tombuntu81 on 2012-04-26
> **TREESofRIGHTEOUSNESS said:**
> Did you read the original post, and do what it indicated?  You might spend sometime searching through the 90something pages of this thread....  or hopefully bumping this thread will get someone who knows to answer you

Hi I've had a read through the forum.. not finding much. would anyone mind confirming if they were able to boot from a usb stick on the Acer 3810tz? Mine just hangs.. I can't what setting might be adjusted as the bios has only limited variables.

Many thanks 
Tom

---

### Post by miegiel on 2012-04-27
> **Tombuntu81 said:**
> Hi I've had a read through the forum.. not finding much. would anyone mind confirming if they were able to boot from a usb stick on the Acer 3810tz? Mine just hangs.. I can't what setting might be adjusted as the bios has only limited variables.

Many thanks 
Tom

When I need to boot from a USB stick (on different types of machines), I often find the USB sticks listed together with the hard drives in the boot options section BIOS.

---

### Post by Tombuntu81 on 2012-04-28
> **miegiel said:**
> When I need to boot from a USB stick (on different types of machines), I often find the USB sticks listed together with the hard drives in the boot options section BIOS.

thanks Miegiel. But have you you managed to do so on an acer 3810tz? I've done the same, it's definitely set to boot first from the USB.. and clearly the USB is detected but for some reason the system then crashes (it doesn't on my other laptop, a dell).

---

### Post by TREESofRIGHTEOUSNESS on 2012-04-28
Are you running the latest version of Ubuntu (12.04)?  I had a similar problem on an older Compaq Presario where I had to do acpi=off for all versions after 10.04.  I would suggest downloading a 10.04 image and see if it works.  If that image works it might mean something has changed and you are seeing a bug.  If it still doesn't work.... well.... we can keep bumping this thread until someone else can help

---

### Post by Tombuntu81 on 2012-04-28
> **TREESofRIGHTEOUSNESS said:**
> Are you running the latest version of Ubuntu (12.04)?  I had a similar problem on an older Compaq Presario where I had to do acpi=off for all versions after 10.04.  I would suggest downloading a 10.04 image and see if it works.  If that image works it might mean something has changed and you are seeing a bug.  If it still doesn't work.... well.... we can keep bumping this thread until someone else can help

so far I've tried 11.10, 12.04, and also Slitaz 3.0 stable ([http://www.slitaz.org/en/get/]("http://www.slitaz.org/en/get/")). Each of these produced an identical result - i.e. the boot haning on the Linux copyright line.

I'm downloading 10.4 right now though - will see how we go. thanks very much
Tom

---

### Post by Tombuntu81 on 2012-04-28
> **TREESofRIGHTEOUSNESS said:**
> Are you running the latest version of Ubuntu (12.04)?  I had a similar problem on an older Compaq Presario where I had to do acpi=off for all versions after 10.04.  I would suggest downloading a 10.04 image and see if it works.  If that image works it might mean something has changed and you are seeing a bug.  If it still doesn't work.... well.... we can keep bumping this thread until someone else can help

Ah, success! Actually, I had three USB sticks keys handy. The first produced the result I mentioned, the second wouldnt format at all, and the third worked. So I guess corruption on the USB was probably  the error. However, i'd not have tried this without attempting a install of 10.4, so you helped me resolve this. thanks! 

Tom

---

### Post by TREESofRIGHTEOUSNESS on 2012-04-29
> **Tombuntu81 said:**
> Ah, success! Actually, I had three USB sticks keys handy. The first produced the result I mentioned, the second wouldnt format at all, and the third worked. So I guess corruption on the USB was probably  the error. However, i'd not have tried this without attempting a install of 10.4, so you helped me resolve this. thanks! 

Tom
Oh good.  I have found that sometimes just pushing someone to try stuff helps.  Glad you figured it out!!

---

### Post by Tombuntu81 on 2012-04-29
Yeah! And now on to the next series of hurdles (installing openelec dual boot)..

---

### Post by TREESofRIGHTEOUSNESS on 2012-05-01
> **Tombuntu81 said:**
> Yeah! And now on to the next series of hurdles (installing openelec dual boot)..

You can just install XMBC in Ubuntu.  It is in the software center

---

### Post by Tombuntu81 on 2012-05-01
yes I realise, thanks, but openelec looks ideal as the system can boot into it directly..

---

### Post by TREESofRIGHTEOUSNESS on 2012-05-02
cool... here are some other options if you are interested

Ubuntu XMBC distro
[http://wiki.xbmc.org/?title=XBMCbuntu](http://wiki.xbmc.org/?title=XBMCbuntu)

(add a lightdm "session")
[http://forum.xbmc.org/showthread.php?tid=116726](http://forum.xbmc.org/showthread.php?tid=116726)

Hope all goes well

---

### Post by Tombuntu81 on 2012-05-04
> **TREESofRIGHTEOUSNESS said:**
> cool... here are some other options if you are interested

Ubuntu XMBC distro
[http://wiki.xbmc.org/?title=XBMCbuntu](http://wiki.xbmc.org/?title=XBMCbuntu)

(add a lightdm "session")
[http://forum.xbmc.org/showthread.php?tid=116726](http://forum.xbmc.org/showthread.php?tid=116726)

Hope all goes well

great. yeah some nice ideas.. I've seen a vid of the light show.. v flash, although , I presume really only useful for action movies..

Think I'm looking at setting myself up with Ubuntu on USB stick, seems the simplest.
thanks a lot

---

