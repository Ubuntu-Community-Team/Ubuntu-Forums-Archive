---
title: "Compaq Laptop"
date: 2006-08-31
forum: Hardware &amp; Laptops
---

### Post by gniss on 2006-08-31
I have a brand new Compaq v6030us laptop, basic specs are AMD Turion 64 X2 Mobile Technology TL-50 Processor, 1GB RAM, 80GB Hard Drive, 15.4-inch WXGA TFT Display, 8X DVD+/-RW Drive.

I have tried both the PC (Intel x86) desktop and the 64-bit PC (AMD64) desktop versions. Both fail during the boot (e.g. hangup), at different prompts but most common being after it displays 'Starting Enterprise Volume Manager'.

Any suggestions please? I have installed Ubuntu on a couple of other machines successfully and would like to get it going on this laptop as well.

---

### Post by Ziox on 2006-08-31
> **gniss said:**
> I have a brand new Compaq v6030us laptop, basic specs are AMD Turion 64 X2 Mobile Technology TL-50 Processor, 1GB RAM, 80GB Hard Drive, 15.4-inch WXGA TFT Display, 8X DVD+/-RW Drive.

I have tried both the PC (Intel x86) desktop and the 64-bit PC (AMD64) desktop versions. Both fail during the boot (e.g. hangup), at different prompts but most common being after it displays 'Starting Enterprise Volume Manager'.

Any suggestions please? I have installed Ubuntu on a couple of other machines successfully and would like to get it going on this laptop as well.

I would suggest that you use the alternative CD to install Ubuntu, liveCDs aren't the best or the most powerful...

---

### Post by cee-jay on 2006-08-31
I was wondering if you mean that you are using the respective Live CDs and *those* aren't booting -or- they boot and you install and then the newly-installed OS on your hard disk won't boot?

---

### Post by reedatschool on 2006-09-01
Hey I just bought a new Presario V3000 which is VERY similar to your new laptop in specs.  I posted a thread about what I got to work which was basically everything.  I used the alternate install cd for Dapper 6.06.1 for the install and everything worked fine in the end.  I see no reason you can't turn this laptop into a kickass  Ubuntu machine

---

### Post by skeezicks on 2006-09-05
I have the exact same laptop was you. It's a great laptop. Anyway to boot up to the install screen you have to press F8 and type in acpi=off. Then the livecd will boot successfully. 
  
  Just to save you further headaches and searching. Here's my experience so far installing ubuntu 6.06.1 LTS amd64 onto the laptop:
 1)Nvidia linux drivers do not currently support the Geforce Go 6150 card so no compiz or xgl. You have to use the 'nv' driver in xorg.conf so you can get a 1280x800 res. The next driver release 9xxx series will support the 6150.

2) Wireless will work but not out of the box. I've heard that some people have had success throuhg the ndiswrapper method. I haven't tried it yet.

3) LAN card works fine out of the box.

4) No acpi support yet. So no battery feedback and efficiency not all there yet.

5) Sound does not work. It's a conexant modem audio sound card. I tried and tried to get this to work and crashed both winxp 64 and ubuntu numerous times with wrong drivers. I gave up and bought a turtle beach usb audio card ("audioadvantage micro") for $30 which runs perfectly in both ubuntu and winxp 64 without having to install any drivers.

6) Volume control buttons work out of the box in gnome.

Just one last thing. I bought this laptop from compusa. When I purchased it they had some rebates but not all. I found this one while looking at the compaq website. 

[http://h30014.www3.hp.com/offers/us/pdf_printable_coupon/1333_compaq-notebook_smartstart_mir30.pdf#search=%220023810.pdf%22](http://h30014.www3.hp.com/offers/us/pdf_printable_coupon/1333_compaq-notebook_smartstart_mir30.pdf#search=%220023810.pdf%22)

I hope this post has been able to help you.

Justin

---

### Post by reedatschool on 2006-09-05
"1)Nvidia linux drivers do not currently support the Geforce Go 6150 card so no compiz or xgl. You have to use the 'nv' driver in xorg.conf so you can get a 1280x800 res. The next driver release 9xxx series will support the 6150."

Thats a bummer, the 32 bit version of Dapper works great with the 6150.  Actually, when I come to think of it when I did the 64-bit install the nvidia acceleration did work.  Are you sure you installed nvidia-glx?  This is what I did

sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-glx-config enable

and everything worked fine, try it and tell me if it works.


"2) Wireless will work but not out of the box. I've heard that some people have had success throuhg the ndiswrapper method. I haven't tried it yet."

Wireless works fine with Ndiswrapper.  Grab the drivers from your Windows partition to get the 64 bit version of the broadcom drivers (Message me if you can't find them and I'll send them to you)

"4) No acpi support yet. So no battery feedback and efficiency not all there yet." 

That is lame, battery indicator and ACPI support seem to work fine with my V3018CL Presario.  Maybe it will work in Edgy?


Reed Harding

---

### Post by skeezicks on 2006-09-05
Hey thanks for the reply reed. I'll let you know if the nvidia and broadcom drivers work. I hope they do. Thanks again.

---

### Post by AlReece45 on 2006-09-12
I didn't try setting up the wireless card yet, but I can't seem to get the proper driver working. With the "nv" driver it won't go above 640x480 and with the "nvidia" driver (from the steps above)... well I can almost see a logo.

---

### Post by skeezicks on 2006-09-13
You have to use the nv driver. And then run this command and reconfigure your settings.

sudo dpkg-reconfigure xserver-xorg

Let me know if you have any troubles.

---

### Post by AlReece45 on 2006-09-13
Thanks for the information, it took a little while to select the correct settings, but eventually I got it working :)

Hopefully the rest of the stuff will be working soon so I can stop using windows so much.

---

### Post by dracule on 2006-09-13
when i try to install it on that exact laptop, it wont partition the hdd, and i have tried a different partitioner too.

---

### Post by AlReece45 on 2006-09-13
If you're trying to resize the NTFS partition, I had a similar problem. Go back to Windows XP, goto Start > Run, and enter "chkdsk /F" and then restart the computer twice. Afterwords try the installation. 

I took me a few days to find out about this. If you don't want to just try it and see if its the problem, use the linux shell to try use use ntfsresize. That program told me the problem, if only Ubuntu had.

---

### Post by AlReece45 on 2006-09-13
With the WLAN driver, you used the 64-bit version with ndiswrapper? Whenever I install the driver it installs the 32-bit version of the driver. When I force it to use the 64-bit one, it tells me that its an invalid driver.

But that's not my problem with wireless; neither driver enables the  WLAN card for me. I was using instruction on [The Wiki]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") and the futhest I've gotten to 2.4.2.3 but I can't get it to see the card. Did any of you have similar problems?

---

### Post by skeezicks on 2006-09-13
I haven't had any luck installing the wireless drivers. I've gotten to the point where ndiswrapper will tell me "driver loaded and hardware present" but it seemed like nothing else was happening. So... I dunno. 

Do any of you guys have the laptop battery monitor woirking? It's bugging me that I have to guess when my battery is going to die.

---

### Post by skeezicks on 2006-09-13
@dracule

try using gparted. It worked for me. Here is the link to the livecd.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by AlReece45 on 2006-09-13
My battery died after that last post :D 

Unfortunately the acpi=off option makes it so you can't see your battery, but removing that option makes it so we can't start Ubuntu... just can't win.

And about the formating, every GUI partion manager I tried when trying to install Ubuntu failed unable to resize a NTFS partition. After 3 days I found out that there was one error on the NTFS partition that needed to be fixed before any of them would resize the drive. After running chkdsk any tool I used to resize the NTFS partition worked perfectly :) (Yes, I did waste a CD-R burning GParted only to get the same error)

I was reading a newer Linux kernel might support the wireless card natively, has anyone tried Edgy yet with more luck? If not I might want to try it.

---

### Post by dracule on 2006-09-20
I think it is because I have 3 partitions already made (2 for hp backup restore thing). and linux requires 2 more to be made but it only supports 4.

I really dont want to delete the recovery partition because it might void the warrenty or something.

---

### Post by AlReece45 on 2006-09-21
I used a HP utility to delete the partion, didn't get any messages about voiding warranty. Either way you can burn recovery disks or order them from HP and the only thing I need from them is the drivers.

Also today, I just finished trying a Knoppix Live DVD I burned a while ago. It was only the 32-bit version but some things I really noted were the following that started up without acpi=off, the option was there, but it didn't need this option. This results in a battery meter :). I also noticed that sound works.

Of course, the graphics driver didn't work correctly, it used the vesa one, so it didn't give me wide screen support, maybe there's an option i'm missing for this. Wireless didn't work, but I couldn't find anything about ndiswrapper, but no wireless cards were found.

It might only be the kernel 2.6.17 on the DVD, but more stuff worked in the Knoppix DVD than Ubuntu.

Edit: One other major thing I noticed: I another post i posted this problem about how my mouse and other stuff stopped working after a random amount of time. Well, mouse worked, stuff didn't stop working. So that's a step closer to linux for me.

---

### Post by AlReece45 on 2006-09-24
Well, here I am, again posting some more of what I've done to try and get this working. Just moments ago, I finished reinstalling Ubuntu Dapper Drake and then Upgrading it to Edgy Edge. I've been trying to get this to work for a while now.

Well, I booted up into Edgy Edge (unfortunately acpi=off still seems to be required to boot). The first thing I noticed was in the upper right hand corner (notification area) the sound is no longer just muted like it was in Dapper, its available to use and is adjustable using the controls on the laptop, but even though the sound control and stuff was nice, it would be even nicer if the sound worked. I did the updates on Edgy, about five, and went in to update the display configuration (i didn't reconfigure it when i reinstalled dapper). The only major difference there was that "dpkg-reconfigure xserver-xorg" recognized the widescreen monitor automatically.

The next thing I went in to test was my problem with just about any USB mouse. Put simply, that isn't fixed yet. After the USB mouse stopped working, the ethernet soon followed. Before restarting though, I decided to look around a bit. Well, to my suprise, I found something we want under networking: Wireless Connection. Unfortunately, even though Edgy detects it, I havn't been able it to connect to any wireless networks yet.

As I am talking, I am working on fixing the USB mouse problems and trying to get the beta nvidia drivers installed. Again, any help would be appreciated.

(also, for more info on the usb mouse problem google IRQ INTR_SF lossage)

---

### Post by AlReece45 on 2006-09-24
I'm not sure if anyone else with this laptop noticed, but I just noticed the BIOS update on the HP/Compaq support website. I'm still playing with it, but sound works more now. Its choppy, but I hear it. Though after the kernel update from below it stopped.

Well, I didn't think it did it before, but I just restarted after updating the kernel again (I reinstalled again just b/c I like to see how things are affected, and exactly what does what) It passed the "Loading Hardware Drivers" step without the acpi=off, though it did stop after "Configuring network interfaces" now, but it continues with acpi=off enabled. Before it wouldn't get past "Loading Hardware Drivers" with acpi enabled.

---

### Post by lurker68 on 2006-09-24
I am having problems with the little mouse pad on the laptop.  It always clicks and drags no matter how I move the mouse.  It is very frustrating.  My mouse pad works fine in Windows. Any ideas on how to get it to not do this?

---

### Post by AlReece45 on 2006-09-25
Uh, there's mouse settings under System > Preferences, try making the sensitivity on there less, and also make sure you have the latest BIOS update.

---

### Post by RD1945 on 2006-09-28
Works fine here (even audio works) except the NVIDIA drivers.
No ndiswrapper needed, no USB mouse errors.
I'm currently running Edgy Eft Knot-3 on a Compaq Presario V6066EA.;)

---

### Post by AlReece45 on 2006-09-28
Uh, ndiswrapper isn't needed as much with edgy, but this is a Dapper topic :( You're laptop is also a little different, we have 6030US, so going by numbers yours is newer? and i think I said a BIOS update fixed mouse problems.

Anyways, the problem I'm having with wireless that appears to be that it is "DISABLED" even though my switch is enabled... don't know how to fix this, maybe there is an update available that I havn't seen yet since I installed (especially since I have to manually connect it to get to the internet)

I'm about to try another BIOS Update that was released on the compaq website v18, the one I posted 4 days ago that I saw was v17, but somehow this v18 was released 8 days ago and has the exact same fixes... hmm...

I'll let you know if BIOS update helps, hopefully it'll get sound working :)

---

### Post by elizleisndahizle on 2006-09-29
I have the HP Pavilion DV9000z with a turion x2 TL-60 and a geforce 7600 go.  Sound, battery, acpi, and the thing that controls what your processor speed is don't work, but I believe that they all did in Sabayon Linux not sure about sound but I am absolutely certain about everything else.  It was the 64 bit version of it.  The volume buttons didn't work though, which the volume buttons and my remote buttons work in here.  When I booted up into the live cd my res was 1680x1050 so that works fine.  Sound obviously works in linux because HP QuickPlay is linux based.  Just a thought.

---

### Post by WhiskeyTangoFoxtrot on 2006-09-29
well heres my install on my Presario V3010US with Ubuntu 6.06

sound works perfectly.
installed nvidia drivers from the synaptic package mannager - have proper 3d acceleration
installed the latest bios update and that seems to have fixed the problem with the touchpad.
cannot get wireless with ndiswrapper. it says the drivers i got from window are installed and the hardware is present but running a iwconfig shows none of the network adapters have wireless ](*,) . can anyone direct me to the proper proceedures to get wireless up and running here please ?

thanks

---

### Post by bigfatgeek on 2006-09-30
I have a Presario V2000 AMD64 Turion, 14 inch WXGA Screen, DVDburner, etc... 
I used the live cd to install and it all works great right off the bat except wireless, which I've yet to dig in to.

---

### Post by AlReece45 on 2006-09-30
Uh, update for all those who havn't seen [guyesinho's post in another thread]("http://ubuntuforums.org/showpost.php?p=1560444&postcount=11") his recommendation was to use noapic instead of acpi=off and that gets more stuff working such as battery indicator, processer speed changing (forgot official term), and most importantly of this list, sound. Please post if it works or doesn't work. (don't forget to erase the acpi=off when you booting if your not reinstalling)

---

### Post by AlReece45 on 2006-09-30
About Wireless help, uhm [this post]("http://ubuntuforums.org/showthread.php?t=201902") might help. Also sorry if my post yesterday was harsh at all, wasn't a good day. Since we're adding more laptops to this thread, it might be a good idea to show lshw output or something similar so we can't compare hardware. I'm going to try ndiswrapper again later today... or tonight.

---

### Post by boz on 2006-09-30
I have a Compaq zv6000 and I cannot get my broadcom 4311 to work with ndiswrapper.  I followed the broadcom howto verbatim.  So I then purchased a linksys usb wireless adapter and now that isn't working.  :evil: However, when I looked at the hardware manager I noticed that Dapper recognizes my usb as 1.1, not 2.0.  Is anyone else having this problem?  I think 1.1 is probably too slow for this device, but I expect that Ubuntu should at least recognize it.  It's a WUSB54GC so the driver should be in Dapper's database.  If anyone has any ideas, please let me know.  Thank you.

---

### Post by AlReece45 on 2006-10-02
I can't seem to find statistics for a Compaq zv6000... maybe its a HP Pavilion zv6000?

Anyways, I can't seem to get the 4311 Wireless card working either. I've tried ndiswrapper, self compiled many times, then I decided to try the bcm43xx module, after extracting firmware from wl_apsta.o it appeared to start working, the wireless LCD even changed from orange to blue (which means its on). It also got an IP address from the router via DHCP, but after that... nothing. It just acts like there's no network connection there. So close yet so far...

BTW, anyone had any success installing the beta nvidia drivers?

---

### Post by boz on 2006-10-02
Actually, it's a Compaq v6000z.  Sorry about the misprint.  I've tried ndiswrapper, but to no avail.  I've also tried the nVidia beta drivers, but I get a blank screen after bootup.  I could type my login information and hear the Ubuntu login theme music.  :rolleyes: I've heard that nVidia is coming out with a new update sometime in the near future, so there's hope yet.

---

### Post by AlReece45 on 2006-10-02
Okay :) Uh, I don't know why but my wireless just started working today :D only thing is even though its a G network and card, it connects using wireless B and its actually connection speed with the network is about 150kbps (thats bits) which is about 13KBps... consider my internet is at least 1-1.6 Mbps I think I would like at least match that, other than the internet seeming drastically slow it appears to work with the bcm43xx linux module.

---

### Post by jfmpreach on 2006-10-03
To get Broadcom 4318 working on a Compaq V2321US or V2000 follow the following: [http://ubuntuforums.org/showpost.php?p=1171008&postcount=67](http://ubuntuforums.org/showpost.php?p=1171008&postcount=67).

I've installed several times always works.:) :)

---

### Post by AlReece45 on 2006-10-05
Good news for people with this laptop: Wireless works with full capabilities with ndiswrapper, i'm not sure if it'll work in dapper, but I don't see any reason why it wouldn't. I'm also not sure whether it would work with the packaged version, but the version I used was 1.23. I'm going to give the exact commands I used, but they might vary.

1: Install ndiswrapper (I used 1.23, older/newer versions might work too, 1.25 wouldn't work for me... the program wouldn't run at all).

2: Ensure the bcm43xx module is disabled and offline.

Add "bcm43xx" to /etc/modprobe.d/blacklist to prevent it from loading automatically. Use the following code to stop it without restarting

```

sudo modprobe -r bcm43xx

```

3: Get the windows driver, one way to get the driver is to download the exe from hp website, run it so it'll extract drivers to a folder on your computer, you do not need to run anything afterwards. The drivers will be in something like C:\SWSetup. Post in thread if you can't get them.

4: Install the driver, it seems this is where most of us get. From the folder where you have the driver located (preferable on the linux partition, not the windows one)

```
ndiswrapper -i bcmwl5.inf
```

now this command

```
ndiswrapper -l
```

should show

```
Installed drivers:
bcmwl5          driver installed
```



5: You've gotten that far, now what? Associate the driver with the hardware.

5.1: Run the following command:

```
lspci | grep Broadcom
```

You should get something like:

```
03:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)
```

The important part here is the first 7 characters. In my case its  "03:00.0". Now use this in the next step where it says <id1>

5.2: Run the following command:

```
lspci -n | grep <id1>
```

It should output something like:

```
03:00.0 0280: 14e4:4311 (rev 01)
```

Now the important part is the xxxx:yyyy. In my case its 14e4:4311, its probably the same for users of my laptop. Use this value for <id2> below.

5.3: The part I didn't seem to see at all in tutorials: 

```
sudo ndiswrapper -d <id2> bcmwl5
```

now this command

```
ndiswrapper -l
```

should show

```
Installed drivers:
bcmwl5          driver installed, hardware present
```

6: Have it reload module and have it auto-loaded:

```

sudo ndiswrapper -m
sudo ndiswrapper -da
sudo ndiswrapper -di
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper

```

Now you should see the card correctly and follow the steps in other tutorials. I had to restart the computer to get it working correctly, though you might not need to. Enjoy and please let me know if it does/doesn't work.

---

### Post by RD1945 on 2006-10-06
> **AlReece45 said:**
> Uh, ndiswrapper isn't needed as much with edgy, but this is a Dapper topic :( You're laptop is also a little different, we have 6030US, so going by numbers yours is newer? and i think I said a BIOS update fixed mouse problems.

Anyways, the problem I'm having with wireless that appears to be that it is "DISABLED" even though my switch is enabled... don't know how to fix this, maybe there is an update available that I havn't seen yet since I installed (especially since I have to manually connect it to get to the internet)

I'm about to try another BIOS Update that was released on the compaq website v18, the one I posted 4 days ago that I saw was v17, but somehow this v18 was released 8 days ago and has the exact same fixes... hmm...

I'll let you know if BIOS update helps, hopefully it'll get sound working :)

Yes, mine is newer. But I thought it had almost the same hardware. By the way, have you tried installing the acerhk driver for your wireless card to become active??
I'm trying to get NVIDIA driver working (beta 9x.xx series). No luck so far.

---

### Post by AlReece45 on 2006-10-06
No problem, just wasn't in a good mood that day. Read above for my wireless solution, and for that post the bcm43xx firmware wasn't installed. Finally, It took a while, but I do have the nvidia driver beta, there's [a guide for it on dapper]("http://ubuntuforums.org/showthread.php?t=271704"), that's the one I used and it worked. Good Luck, and if it doesn't load, tell me the most important error in the log, I might be able to help.

---

### Post by juhizz on 2006-10-19
> **AlReece45 said:**
> Uh, update for all those who havn't seen [guyesinho's post in another thread]("http://ubuntuforums.org/showpost.php?p=1560444&postcount=11") his recommendation was to use noapic instead of acpi=off and that gets more stuff working such as battery indicator, processer speed changing (forgot official term), and most importantly of this list, sound. Please post if it works or doesn't work. (don't forget to erase the acpi=off when you booting if your not reinstalling)

What if I installed edgy with *acpi=off* (sound doesn´t work) Do I have to reinstall it with using *noapic*? Or can I just put it somewhere while I'm booting?:-k

How do I erase *acpi=off* on booting?

---

### Post by AlReece45 on 2006-10-19
```
sudo gedit /boot/grub/menu.lst
```

Best method is probably to replace every instance of apci=off to noapic and then save it. That will update the entries in the boot menu and will have it automatically added when updates update the file.

---

### Post by juhizz on 2006-10-23
> Best method is probably to replace every instance of apci=off to noapic and then save it. That will update the entries in the boot menu and will have it automatically added when updates update the file.

That worked, the sound is working, but my headphone jack doesn't. Has anyone resolved this problem ?? (the laptop speakers aren´t the best ones to listen music)

I still have to wait the nvidia beta driver to come a normal driver to ubuntu. I couldn't install the beta driver. Is anyone having this same problem with this laptop **Compaq presario v6000 (AMD turionx2, nvidia Geforce go 6150)**??:confused:

---

### Post by jmullagh on 2006-10-23
> **AlReece45 said:**
> If you're trying to resize the NTFS partition, I had a similar problem. Go back to Windows XP, goto Start > Run, and enter "chkdsk /F" and then restart the computer twice. Afterwords try the installation. 
 
I took me a few days to find out about this. If you don't want to just try it and see if its the problem, use the linux shell to try use use ntfsresize. That program told me the problem, if only Ubuntu had.
 
 
Thank you! This did it for me. My V3000T is running beautiful and... the Intel(R) PRO/Wireless 3945ABG Network Connection card worked right out of the box. I only had to set up the security. EXCELLENT...    :KS

---

### Post by AlReece45 on 2006-10-23
> **juhizz said:**
> That worked, the sound is working, but my headphone jack doesn't. Has anyone resolved this problem ?? (the laptop speakers aren´t the best ones to listen music)

I was just asking about this in the irc channels the other day. I think one of them told me it was fixed in the latest alsa, which isn't included in the current linux kernel, nor the one included in edgy. I'm going to try compiling the kernel again with new alsa drivers and see if that works. I've tried three times with one method, and I'm going to try again with another.

> I still have to wait the nvidia beta driver to come a normal driver to ubuntu. I couldn't install the beta driver. Is anyone having this same problem with this laptop **Compaq presario v6000 (AMD turionx2, nvidia Geforce go 6150)**??:confused:

Well, first off, when installing beta driver, try finding 9626 instead of 9625. Its newer, but still doesn't fix much if anything. 

I used [this guide ]("http://ubuntuforums.org/showthread.php?t=263851")to install the nvidia drivers.

---

### Post by juhizz on 2006-10-24
> **AlReece45 said:**
>  

I used [this guide ]("http://ubuntuforums.org/showthread.php?t=263851")to install the nvidia drivers.

Maybe I'm asking something stupid, but what is *beryl*?:-k

---

### Post by AlReece45 on 2006-10-24
Its a window manager like compiz, but You don't have to install beryl with that guide, just use Step 2 (the repository didn't work for me with AMD64 version of ubuntu)

---

### Post by AlReece45 on 2006-10-30
Well, I got the headphones and built-in microphone working and microphone port working. I compiled in alsa, I ended up using the most recommended way because it took quite a bit of searching to find a solution. So you might be able to compile alsa 1.0.13 in another method (perhaps directly with the kernel)

First downloaded and installed the 2.6.18.1 kernel using [this guide]("http://ubuntuforums.org/showthread.php?t=217657") (currently has 2.6.18, but works with 2.6.18.1 (replace the numbers))

After booting to the new kernel, I needed to reinstall the nvidia beta drivers and ndiswrapper (from source so wireless works). Then I downloaded the  alsa-driver-1.0.13, alsa-lib-1.0.13, and alsa-utils-1.0.13 to /usr/src

Next I installed the alsa-lib-1.0.13 (simple install)

```
cd /usr/src
sudo tar -xjvf alsa-lib-1.0.13.tar.bz2
cd alsa-lib-1.0.13
sudo ./configure
sudo make
sudo make install
```

The part which seemed to fix the problem I got from the alsa mailing list. (unfortunately no one answered him, I didn't have an answer for him either)

Add the following /etc/modprobe.d/options

```
options snd-hda-intel model=z71v position_fix=1 disable_msi=1
```

Then I installed the driver and utils in one go

```
cd /usr/src

sudo tar -xjvf alsa-driver-1.0.13.tar.bz2 > /dev/null
sudo tar -xjvf alsa-utils-1.0.13.tar.bz2 > /dev/null

cd alsa-driver-1.0.13

echo Configuring Driver
./configure  --with-kernel=/usr/src/linux-2.6.18.1 --with-cards=hda-intel  --with-oss=yes > /dev/null
sudo make
sudo make install

cd ../alsa-utils-1.0.13
sudo ./configure
sudo make
sudo make install 


```

Running the following extracts, configures, and installs.

Then I ran alsaconf, selected the first option, when it finished loading I ran ./snddevices from the alsa-driver-1.0.13 directory. Finally I ran speaker-test, this started a speaker test, and it alsa prompted the volume control to show its new options. The volume needed to be raised to hear the volume test, but now everything seems to be working, headphone, mic, mic port, speakers.

---

### Post by martinquested on 2006-11-12
That solution looks interesting.

Can you explain why it's necessary to compile a new kernel and not just do the alsa part described above?

The how-to which you link to makes recompiling look like an operation fraught with difficulties and risks - I've got my system (largely) up and running now so I'd rather not risk messing it up and having to reinstall...


Well, I tried it without a kernel reinstall, and (after remembering to kill all sound apps, including the KMix volume control), I managed to get it working... sort of.  The problem is, it has made the headphone channel the "master sound channel", which is the one the keyboard volume and mute buttons access.  Even if I go into KMix (having restarted it) and reconfigure the master sound channel to be the speaker, or the PCM, the keyboard mute button still mutes the headphones, not the newly specified master sound channel.

Additionally, I note that the laptop speakers do not cut out when headphones are inserted (although this may be linked to the above issue).

Is this correct functionality?  Anyone any ideas how to tweak this?



The tips for the ndiswrapper and the video card worked great for me by the way.  I'm getting an ideal picture with "nv" driver and the monitor "Compaq 1720 Flat Panel Monitor" (widescreen setting).

---

### Post by LukeyMI on 2006-11-12
> **martinquested said:**
> The tips for the ndiswrapper and the video card worked great for me by the way.  I'm getting an ideal picture with "nv" driver and the monitor "Compaq 1720 Flat Panel Monitor" (widescreen setting).

The latest release of the Nvidia driver works for the v6030 now.

What I am using in xorg.conf:

```

Section "Device"
	Identifier	"nvidia"
	Driver		"nvidia"
	BusID		"PCI:0:5:0"
        Option		"NoLogo"	"true"
	Option "ExactModeTimingsDVI" "TRUE" 
	Option "ModeValidation" "DFP-0: NoEdidDFPMaxSizeCheck, NoVesaModes"
EndSection

```

Found those last two options in point 7 of the problems section on this wiki page:

[https://help.ubuntu.com/community/Latest_Nvidia_Dapper?highlight=%28nvidia%29](https://help.ubuntu.com/community/Latest_Nvidia_Dapper?highlight=%28nvidia%29)


For resolution in xorg.conf:

```

Section "Screen"
	Identifier	"Default Screen"
	Device		"nvidia"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

For refresh rate:

```

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-67
        VertRefresh     30-60
EndSection

```

I'm not sure if those are the correct refresh rates for the display. I'm using some auto detected values there...

I'm now using the latest Nvidia driver that was released a few days ago without any problems using the method 2 installation on that wiki page.

Wireless works great when removing the ndiswrapper packages and compiling ndiswrapper manually. I haven't tried the headphones though...don't have a set of headphones for the laptop to try. :\

---

### Post by AlReece45 on 2006-11-19
> **martinquested said:**
> That solution looks interesting.

Can you explain why it's necessary to compile a new kernel and not just do the alsa part described above?

The how-to which you link to makes recompiling look like an operation fraught with difficulties and risks - I've got my system (largely) up and running now so I'd rather not risk messing it up and having to reinstall...


Well, I tried it without a kernel reinstall, and (after remembering to kill all sound apps, including the KMix volume control), I managed to get it working... sort of.  The problem is, it has made the headphone channel the "master sound channel", which is the one the keyboard volume and mute buttons access.  Even if I go into KMix (having restarted it) and reconfigure the master sound channel to be the speaker, or the PCM, the keyboard mute button still mutes the headphones, not the newly specified master sound channel.

Additionally, I note that the laptop speakers do not cut out when headphones are inserted (although this may be linked to the above issue).

Is this correct functionality?  Anyone any ideas how to tweak this?



The tips for the ndiswrapper and the video card worked great for me by the way.  I'm getting an ideal picture with "nv" driver and the monitor "Compaq 1720 Flat Panel Monitor" (widescreen setting).

I thought that alsa was compiled into the kernel ubuntu included.  Using the one in the kernel and compiling according to many guides "will not work."

and Yes, that functionality is correct, it gets annoying, but its better than it not working at all:)

---

### Post by martinquested on 2006-12-15
Hello again everyone.

So yesterday I think a few packages updated as recommended by the Adept update tool.  And now I don't have a working sound card any more.

I re-ran alsa-conf and snd-devices and both worked fine without complaint.  But speaker-test then reports the following:

```
speaker-test 1.0.13

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2143:(snd_pcm_open_noupdate) Unknown PCM default
Playback open error: -19,No such device

```

And kmix, realplayer and anything else I try tell me they can't find/initialise/use a sound card.

Anyone any ideas what's happened and how to fix it?

---

### Post by martinquested on 2006-12-17
For my happy ending, see [http://ubuntuforums.org/showpost.php?p=1897576&postcount=28](http://ubuntuforums.org/showpost.php?p=1897576&postcount=28)

---

### Post by Levitation on 2007-03-09
When attempting to load Live CD (5.10):
Tried "acpi=off"....what happened was that I got to a screen that reported graphic problems and would I like to try to diagnose.
Then it stopped loading...

Any ideas? I have tried "noapic" and/or "nolapic" (did I need to add "=off" for those?

I just got a Compaq 6210us/AMD Turion64/Vista Home Premium (I know...don't ask)

Anyone have any luck with the Live CD? I am fairly noobie so the Alternate CD is beyond me. I should be getting 6.06 soon (32-bit and 64-bit) as well as Kubuntu 6.06. Will those make any difference? Would 6.10 be any better?

Merci, Todah Rabah, Spacibah, Gracias, Shukran and Thanks.

---

### Post by martinquested on 2007-03-10
Yours isn't exactly the same model as mine, but it's close.  I would definitely go for 6.06 at least.  No idea about 6.10.

You will also likely find you can get more things running and more compatibility if you use the 32-bit version rather than the 64-bit version, even though you have a 64-bit CPU.  That was my experience 4 months ago, anyway.

---

### Post by martinquested on 2007-06-13
Hey folks,

has anyone else here (with a Compaq V6030US) upgraded to Feisty and found that their sound card cannot be recognised for love nor money?  I've tried reinstalling all the versions of ALSA I can think of, recompiling the kernel, adding bits onto the end of alsa-base... in short, all the things suggested on various forums, and still modprobe complains that the module has an unknown symbol or parameter, KMix says there is no sound card present...

What can I do???

---

