---
title: "Dell XPS m1330"
date: 2007-09-16
forum: Hardware &amp; Laptops
---

### Post by Johnson on 2007-09-16
Do anyone have any experience with Dell XPS m1330 with Ubuntu 7.04? :(

---

### Post by alaind on 2007-09-16
I just tried without success, I tried to follow the instruction on the french ubuntu forums

[http://doc.ubuntu-fr.org/dell_xps_m1330](http://doc.ubuntu-fr.org/dell_xps_m1330)

but even with those instruction which mention the fact to install in safe graphic mode, because the the right nvidia driver are not in the distro, it fails, It go a bit furhter but xwindows fails to lauch, then the sequence gets stuck in starting "local scripts" or something like that.

---

### Post by xturmn8r on 2007-09-21
I upgraded to the m1330 from an m1210, and I used the old hard drive from the 1210, because I didn't want to migrate all my data. I was dual booting, Ubuntu worked great, except for the speakers, but including the nvidia driver / everything else (I didn't get the finger scanner). Vista, however was not so amused. So, I wiped the hard drive. Now I can only get vista to work well. I hope for gutsy to solve my linux woes.  

Incidentally, the Live CD boots, you just have to do the break=top option (f6 on the live CD), and safe graphics mode install. After you install, do the sudo commands prescribed there. It should then boot, but it breaks easily. I have experienced this multiple times on bleeding edge hardware though, ever since my geforce fx 5600 that broke the nvidia driver.

---

### Post by crisby on 2007-09-22
1.) UBUNTU AND VISTA ON m1330

Gutsy works like a charm!

I installed tribe 5. You just have to use the "alternate" CD. If you want to use a dual boot system, to keep vista and media direct working, it's a little bit tricky:

You need the alternate cd and the "normal" live cd.

install windows vista an media direct.
install ubuntu with alternate cd
IMPORTANT: grub has to be installed to /dev/sda{yourBootPartition} NOT to MBR!!!
After Installation boot with a live CD
execute:
  dd if=/dev/sda{where you installed grub} of={whereever you want to have the file}/linux.bin bs=512 count=1

copy the linux.bin to an usb stick.

reboot. your m1330 should boot automatically vista.
copy the linux.bin to c:\

open the commandline:
bcdedit /create /d &#8220;whatever text you like e.g. ubuntu&#8221; /application BOOTSECTOR

then you get a  looooong GUID

bcdedit /set {GUID} device boot
bcdedit /set {GUID} PATH \boot.bin
bcdedit /displayorder {GUID} /addfirst
bcdedit /timeout 5

The timeout can be set easily in the system properties/advanced/system variables (or something like this). There you can also check/choose which OS shall boot by default.

There are some graphical tools for bcdedit as well, but I did not find a very good one yet.

If everything worked well, you should be able to use media direct, vista and ubuntu.
After reboot you see the windows bootloader at first. If you choose Ubuntu, grub bootmanager is shown and you can boot ubuntu.


I did not try to boot vista or media direct via grub boot manager yet, because I was afraid to frag my installation. If anybody is brave enough, please tell me if it works too.

2) UBUNTU AND NVIDIA
I did not get my NVIDIA card working with the "normal" installation. I had to use the prorietary driver from nvidia.com (You should keep that file, because actually I have to install it everytime a kernelupdate took place.)
- Switch to command line Strg+Alt+F1
- sudo killall gdm Xorg
- execute you nvidia driver: ./NVIDIA...blabla... (eventually you have to use a chown a+x NVIDIA...blabla... first)
- let the installation change your xorg.conf
- After reboot you should see the NVIDIA logo. If so, everything is fine.
  IF NOT... then you have the same problem I had, that the nvidia module is not started
  switch to console,
  then open the /etc/rc.local (/etc/modules didn't work for me) by executing
  sudo nano /etc/rc.local
  add these two lines before the "exit" line:

  modprobe -r nvidia  #maybe you do not need this one... I do.
  modprobe -i nvidia

If there are still any problem, just tell me and I will try to help.

Greetings crisby

---

### Post by Celestial Teapot on 2007-09-22
I'm glad to see Gutsy works on my M1330. :-D
My only concern is the constant whoosh from the fan. It makes my laptop sound like a vacuum cleaner. Is there perhaps an easy way to exert some control over the fan's activity? :-({|=

---

### Post by crisby on 2007-09-24
I did not find any yet, so please let me know if you find something.

Meanwhile powernowd works for me. The m1330 is still not half as quite as my old Samsung X10, but I can live with it. 

After I watched powertop, I would like to find something to throttle down my nvidia card. I guess it produces most of the heat.

Did someone find a program to use the fingerprintreader? Thinkfinger works for the login, but I am still searching for something which works for web-logins as well (like the windows program).

---

### Post by crisby on 2007-10-02
Sry for doubleposting, but I found something for the fingerprint reader:

[http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader]("http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader")

It's still not as good as the windows version, but in the end it works pretty well.

---

### Post by atlas95 on 2007-10-02
Hello, I have do a howto for install gusty on m1330

[http://leblogdatlas.com/wordpress/index.php/2007/10/02/installation-tweaking-dell-xps-1330-avec-ubuntu-gusty/](http://leblogdatlas.com/wordpress/index.php/2007/10/02/installation-tweaking-dell-xps-1330-avec-ubuntu-gusty/)

in english : [http://translate.google.com/translate?u=http%3A%2F%2Fleblogdatlas.com%2Fwordpress%2Findex.php%2F2007%2F10%2F02%2Finstallation-tweaking-dell-xps-1330-avec-ubuntu-gusty%2F&langpair=fr%7Cen&hl=fr&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools](http://translate.google.com/translate?u=http%3A%2F%2Fleblogdatlas.com%2Fwordpress%2Findex.php%2F2007%2F10%2F02%2Finstallation-tweaking-dell-xps-1330-avec-ubuntu-gusty%2F&langpair=fr%7Cen&hl=fr&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools)

I hope this can help you !

;)

---

### Post by vagrahb on 2007-10-08
Media direct works for me after installing grub on the mbr.

---

### Post by crisby on 2007-10-10
Really?! Windows Vista, Ubunutu + Media Direct?
My partition crashed when I pressed the media direct button the first time after installing
grub to the mbr.

---

### Post by b0ng0 on 2007-10-10
Can anyone confirm that Ubuntu works on the XPS M1330? I am thinking of buying one but will be doubtful if Ubuntu does not work at all on it (I don't mind so much about small features though).

---

### Post by jespdj on 2007-10-10
Yes, it works on the M1330. Even the webcam works.
See: [http://ubuntuforums.org/showthread.php?t=568733](http://ubuntuforums.org/showthread.php?t=568733)

---

### Post by FrankVdb on 2007-12-10
If you choose the standard M1330 with the integrated Intel graphics accelerator, forget it. 

If you buy an M1330, get the higher-end version with at least the GeForce 8 series graphics card. 

I bought the 2,2 Gh dual-core configuration with the GeForce card and Gutsy installed without any problem, although I haven't tried the webcam and the mike yet, for which problems have been reported. 

For the rest, this is a powerful system. I'm even running XP in VirtualBox without noticeable lag!

---

### Post by crisby on 2007-12-10
I can confirm that.
The webcam works fine too. (Skype, Ekiga) Only the integrated mic is not working for me (even with the patch you can find). I hope this will be fixed with the next kernel-update. External mic works perfectly so it's not a problem to me.

---

### Post by jnnnnn on 2008-05-04
To get the internal microphone working:

Double click the volume icon at the top right

Edit->Preferences (if your title bar says HDA Intel: Alsa Mixer, otherwise change it using File->Change Device)

Select the Capture, Digital, and Digital Input Source boxes (the others can be left as they are)

Close the dialog

On the Recording tab, set Capture to maximum, Digital to half-maximum (otherwise I find there is a lot of white noise from the microphone).  Also ensure nothing is muted (no red X symbols on the buttons at the bottom of the sliders).

On the Options tab, set Digital Input Source to Digital Mic 1.

That should be everything; close the Volume Control window and test your mic with Applications->Sound and Video->Sound Recorder (record something and play it back).

---

### Post by jbor7755 on 2008-05-04
I just got mine last week.  I've now got Vista, Ubuntu and Media Direct Working as normal.  I followed the instructions on this page:

[http://www.daryl.mu/2008/03/05/howto-triple-boot-dell-xps-m1330-with-vistaubuntu-and-media-direct/](http://www.daryl.mu/2008/03/05/howto-triple-boot-dell-xps-m1330-with-vistaubuntu-and-media-direct/)

The MD button works fine and grub doesn't have to go anywhere.  You just need to do a clean instal of MD + Vista. You have to first boot with the MD disc which creates a partition for your Vista (you can chose how big it should be) and a small fat16 one for utilities or some such (which i know nothing about). Everything else is made an extended partition in which MD takes up about 2GB.  The remainder of this extended partition can be used however you like.

I had plenty of room to play with so I made Vista rather small (about twice the expected initial installation volume) and then, once it was installed along with Drivers and the MD and I was happy this was working, I popped in the Ubuntu live disc, hit install and then when it came to partitioning I manually allocated the remainder of the extended partition to a big /home partition, root (/), swap and a 10GB fat32 partition for windows data (the MD partition MUST be left where it is at the end of the table).  Everything else was pretty much default and worked flawlessly.  I didn't move grub anywhere.  The MD button boots into MD as expected, and the power button boots to grub where i can choose my operating system. MAD!!!

My scheme will probably change again at some point (when I get jack of MD).  At that time I'll probably wipe the hard drive again and just install Vista and Ubuntu and set the MD button to boot grub and the power button to boot Vista. Some details on this page:

[http://forum.notebookreview.com/showthread.php?t=182495](http://forum.notebookreview.com/showthread.php?t=182495)

Although the details are more sketchy and the process sounds a lot more involved. This one needs a re write as a proper how-to.

---

