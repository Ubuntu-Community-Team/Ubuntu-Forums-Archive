---
title: "Sony Vaio TT and Ubuntu"
date: 2009-03-31
forum: Hardware
---

### Post by ilcontegis on 2009-03-31
Hi everyone,
I do this post to know how many others own a TT series vaio and how is it working with ubuntu.
Here the specs of my tt50b:

- Intel® Core&#8482; 2 Duo Processor SU9300 1.20 GHz Speed
800MHz Front side bus
L2Cache 3MB
- 3gb ram  PC3-6400
- hard disk 160GB 5400rpm SATA
- Screen 11.1" 1366 x 768 
- Multimedia card reader One Memory Stick PRO&#8482; (Standard/Duo) media slot with MagicGate® functionality One ExpressCard® /34 slot One Secure Digital (SD&#8482; memory card) media slot 
- Sound system Intel® High Definition Audio 
- Graphic chipset Mobile Intel® GS45 Express Chipset (Mobile Intel® Graphics Media Accelerator 4500MHD with Intel® Clear Video Technology Total Available Graphics Memory: 790MB (max.))
- Intel® WiFi Link 5100AGN (802.11a/b/g/n) 

```

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
0b:04.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
0b:04.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
0b:04.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
0b:04.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)

```

**What does it work out of the box (Karmic 9.10 64bit):**

- cpu and scaling                              **OK**
- ram 3gb seen                                 **OK**
- wifi and ethernet                            **OK**
- blue-tooth                                   **OK**
- touchpad                                     **OK**
- Webcam                                       **OK**
- On board Speakers                            **OK**
- Screen and external screen (VGA out)         **OK**
- HDMI out                                     [COLOR="Red"]Needs verification[/COLOR]
- dvd reader/ burner                           **OK**
- Intel graphic chipset                        **OK**
- All front buttons                            **OK**  
- Usb 2.0                                      **OK**
- SD card reader                               **OK** Seems to be working
- All FN combinations                          **OK**   

**What still is not working out of the box (Karmic 9.10 64bit):**
- Internal microphone (no way to make it work properly)
- 1seg tv (japanese model)
- finger sensor


**[SIZE="6"][COLOR="Green"]Deprecated - Look further only for Jaunty 9.04[/COLOR][/SIZE]**

**What does it work out of the box (Jaunty 9.04 64bit):**

- cpu and scaling                              **OK**
- ram 3gb seen                                 **OK**
- wifi and ethernet                            **OK**
- blue-tooth                                   **OK**
- touchpad                                     **OK**
- Webcam                                       **OK**
- On board Speakers                            **OK**
- Screen and external screen (VGA out)         **OK**
(Resolution for the external screen manually changed in the xorg)
- HDMI out                                     [COLOR="Red"]Needs verification[/COLOR]
- dvd reader/ burner                           **OK**
- Intel graphic chipset                        **OK**
- +,- and mute volume front buttons            **OK**  
- Usb 2.0                                      **OK**
- SD card reader                               **OK** Seems to be working

[B]What is not working out of the box:
[/B]
- Microphone (no way to make it work properly)
- 1seg tv (japanese model)
- finger sensor
- Fn + (x) combinations
- S1 and eject buttons on the front of the laptop
- Headphone jack output, it works but the pc speakers don't become mute (it's useless like this to put headphones)

If somebody succeeded to make something else work please write here, in this way we can make a small guide.
See ya.

**[SIZE="6"][COLOR="Red"]Problems Solved[/COLOR][/SIZE]**

**- How to make work the CD button Eject and the FN combinations** (Thanks to leibnitz27 and elboeufx for the help)

**With the new kernel 2.6.30 the FN combinations and the eject button will work out of the box**

If you don't want to install the new kernel follow the guide below

This operation is to repeat for each new kernel. For this guide replace the 2.6.28.12-generic with the kernel YOU are using.
1. Download sony-laptop.ko from here [http://www.benf.org/files/sony-laptop.ko](http://www.benf.org/files/sony-laptop.ko)
2. Make a backup of the sony-laptop.ko
```
sudo cp  /lib64/modules/2.6.28-12-generic/kernel/drivers/misc/sony-laptop.ko /lib64/modules/2.6.28-12-generic/kernel/drivers/misc/sony-laptop.ko.bk 
```
I have a 64 bit edition so if you have still a 32 bit you will not have lib64 but var/lib/....the rest is the same
_If you do not find sony-laptop.ko search it:_
2a) Go to "Places" on the top menu bar.
2b) Click on "Search for Files."
2c) In the "Look in Folder" drop-down menu, hit "File System"
2d) Type "Sony" into "Name Contains," and hit enter.
2e) You will get a huge list of everything in the computer that pertains to Sony. Scroll down the list until you find a file called "sony-laptop.ko." Right beside the name you will see the "Folder" in which this is located (in my case it was /lib/modules/2.6.28-11-generic/kernel/drivers/misc
3. remove the module with
```
sudo rmmod sony_laptop
```
4. overwrite the new file over the old one (in my case was on my Desktop)
```
sudo mv /home/teo/Scrivania/sony-laptop.ko /lib64/modules/2.6.28-12-generic/kernel/drivers/misc/ 
```
5. ```
sudo modprobe -v sony-laptop
```
6. Press Eject button 
(On my pc it did not work!)

**- How to make work the headphone jack exit** (Thanks to rick1500 for the help)

1. Give
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```
and add this at the end of the file
```
options snd_hda_intel model=6stack-dig
```
2. Reboot the pc
3. Open alsamixer, select the "HDA Intel (Alsa mixer)" device.
4. Click the "Preferences" button to add the "Surround" and "Front" controls.
5. Use "Surround" to control the headphones and "Front" to control the laptop speakers independently.
(On my pc it did work!)

---

### Post by ilcontegis on 2009-04-15
nobody has a vaio tt? i'm the only one in the whole ubuntu community??

---

### Post by geekygirl on 2009-04-15
lol no I have a Vaio TT as well - a VGN-TT15GN, 1.2GHz, 120G HDD and I upped it to 4G DDR3.

How did you go when you updated Jaunty? Last night I had to remove Compiz and Compiz-Core just to get it past the GDM screen (although this appears to be an Intel bug) and then I enabled UXA and was able to reinstall compiz...a lot of mucking around - this is the post here: [http://ubuntuforums.org/showpost.php?p=7069702&postcount=81]("http://ubuntuforums.org/showpost.php?p=7069702&postcount=81")

So far I am considering returning back to Intrepid and trying the Emperor Linux kernel as I am finding Jaunty a bit too 'beta' on my TT right now, although I am waiting out the 9 days before judging to much.

I am keen to investigate the Emperor Linux kernel more though as they claim on their site to have fully functioning Vaio TT notebooks for sale running Ubuntu with their own custom kernel - which means it is possible to get all the Fn keys, fingerprint sensor and buttons (especially eject - I miss my eject button on the front!!) working...either that or they spend time mapping out each key after the install...

You can download the kernel and give it a go - might be worth looking at?

[http://www.emperorlinux.com/]("http://www.emperorlinux.com/")

Otherwise I am like you - finding it extremely hard to get much info about running any *nix flavour on the TT - then again its only a new notebook, and a highly specialised one at that (read: expensive)

lol

---

### Post by flipper20009 on 2009-04-15
Hi, I have a TT as well, just installed 9.04 - I have exactly the same issues as you but I have the added issue of the 3G card not working. I have a VGN TT11WN. I must admit that 9.04 seems to be running very well apart from the few things that arent working. 

I have globe trotter (Options) emailing me a driver that they have in beta to try. once I have this I will test and post a link here for you all. 

I have seen a feed today at work that gives the FN functionality back as well but I cant remember where I have seen this so may need to wait till I get back to work to find that but will leave a post once i have tested them.

---

### Post by ilcontegis on 2009-04-15
I am not alone :D...
Thank you for the reply.

@Geekygirl
I upgraded to the 9.04 since the alpha 6 no 1 problem since then (except the things that were not working before as well)
Before to upgrade, I always:
1. put vesa driver
2. remove the 3rd part repositories
3. run autoclean and autoremove

Interesting this thing of the kernel. When I have time I will try it if I am able to :P

I really need that the mic is working and that when I put the headphone jack the sound does not come anymore from the speakers.

edit: mmmm I don't know this company. Do you think we can trust them to install this kernel? I am a bit worried to damage the pc. If they did some change to the kernel we should be able to know what they did. or not?

edit2: could you test the hdmi exit and the cards slots? are they working? I do not have the chance to use them so if you could tell me I would be able to update the first page info. THX

---

### Post by leibnitz27 on 2009-04-16
Also have a TT I'm looking to stick Ubuntu on, but need working 3g, so be very interested in how much luck you have, Flipper.

Did any of you get any success with the LDR? (light sensor)  - I hated this at first, but it's actually quite handy for saving battery life.  

Mine's a TT11WN by the way.   

Cheers!

---

### Post by geekygirl on 2009-04-16
Ok, my model did not come with HDMI so I cannot test that, but I did try the SD Card slot on my Vanilla (but updated daily - just nothing else added) Jaunty install.

SD Card - Not Working

Sony MS Slot - unable to test as I don't own a Sony MS.

Fn F5 and F6 (brightness) not working but the software works - probably a case of key mapping perhaps?


I am also having that issue with the system only reading 2.9G of memory, despite there being 4G shown in the BIOS and the memory modules all passed Memtest x86. I am running a 32 bit version but I would have thought I could see about 3.5G - same as a 32bit Vista install does.....(and we cannot remap memory in the H20 bios..grrrrrr....)

---

### Post by ilcontegis on 2009-04-16
thanks for your help I updated the first page.
Tomorrow I will try that strange kernel, let's see if it works ;D

---

### Post by geekygirl on 2009-04-17
I am reinstalling Intrepid right now (using my Vostro for this hehe) and going to give it a go. I have also been doing some reading on key mapping and kernel cusomisation.....must..not..let it beat...me...lol

(I can code in C++ but the kernel stuff is a *little* bit different!)

---

### Post by ilcontegis on 2009-04-17
> **geekygirl said:**
> I am reinstalling Intrepid right now (using my Vostro for this hehe) and going to give it a go. I have also been doing some reading on key mapping and kernel cusomisation.....must..not..let it beat...me...lol

(I can code in C++ but the kernel stuff is a *little* bit different!)
why intrepid? jaunty is really stable from a while....;)

---

### Post by geekygirl on 2009-04-18
Because the 'empkernel' was written for Hardy/Intrepid not Jaunty?

They are using 2.6.27 currently. 

Jaunty might be stable but I can wait a few days for the full release before I use it in a production environment. I prefer tried and tested over stable beta's and RC's when it comes to using my laptop for work and coding Uni assignments at the moment! (ie no time to play with the OS, I need to just be able to use my laptop)

(Basically when I had the issue with xorg.conf and compiz I knew then Jaunty was not for me personally right now if it still breaks on updating!! lol)

---

### Post by ilcontegis on 2009-04-19
> **geekygirl said:**
> Because the 'empkernel' was written for Hardy/Intrepid not Jaunty?


I see.. :D 
Could you try this kernel? Me I am a bit busy now.. How was it?

---

### Post by AlanR8 on 2009-04-19
To get the sound working, mic and headphones, try this. It works on my VGN-FZ21S under Jaunty and Intrepid.

> sudo kate /etc/modprobe.d/alsa-base 

Add this to the bottom

options snd-hda-intel model=vaio

Then

sudo apt-get install linux-backports-modules-$(uname -r)

Note I use Kubuntu so *sudo kate* will have to be replaced by whatever text editor you use.

---

### Post by leibnitz27 on 2009-04-19
FWIW - 

Haven't got around to shrinking my vista partition yet, but I thought I'd try live Jaunty - and my SD cards work just fine.

(mounted as : )
/dev/mmcblk0p1 on /media/disk type vfat 

Rgds,

Lee

---

### Post by ilcontegis on 2009-04-19
> **AlanR8 said:**
> To get the sound working, mic and headphones, try this. It works on my VGN-FZ21S under Jaunty and Intrepid.



Note I use Kubuntu so *sudo kate* will have to be replaced by whatever text editor you use.

my alsabase is empty is it normal? the sound works perfectly, just the jack and the mic does not work.

---

### Post by AlanR8 on 2009-04-19
> my alsabase is empty is it normal? the sound works perfectly, just the jack and the mic does not work

Exactly the same symtoms as mine. Try my suggestion it should sort it for you

---

### Post by ilcontegis on 2009-04-21
> **AlanR8 said:**
> Exactly the same symtoms as mine. Try my suggestion it should sort it for you
Unfortunately it does not work. :( probably we have different sound card,i have the alc889 not yet supported by alsa (on the doc I found it reaches until the 888)

p.s. I tryed to install the emperorkernel but is only available for 32bit -.- does someone with 32bit version of Ubuntu tried it?

---

### Post by geekygirl on 2009-04-26
Ok I was busy for a few days last week so was unable to test the empkernel for a while but I have just finished with it and, well, nothing works that didnt already work under Jaunty, and Emperor Linux must have more config files than just the kernel (with its fancy boot splash screen!) to get the buttons and Fn keys working. Still no eject, no S1 key, no brightness Fn keys either.

Have a few more tricks up my sleeve to experment with, with regards to Fn keys - will let you know how it goes.

The most WORRYING thing with the empkernel? WHY oh why did one core on my CPU run flat out at 100% at all times?!!!, and the fan was on max until I installed the CPU Freq applet and set the scaling manually - thats a major regression right there! (Actually this was what did it for me - and I am definately not sending my laptop away to the US to have them install their 'custom' packages - would have consdiered paying for software downloads though - if they really do work as claimed)

Personally I would not recommend this kernel for the Vaio TT thats your main machine. But if you want to experiment you should be fine.

I ran it on Ubuntu Intrepid Ibex 32bit, had to stuff around with grub as it installs itself under grub in some bizarre fashion and you need to manually edit your grub menu.lst to get it to boot otherwise you get error 22 or error 15 in grub.

Shame, it showed promise - but failed to deliver in my case!

---

### Post by gcvisel on 2009-04-26
> **ilcontegis said:**
> 

[B]What is not working:
[/B]
- Microphone (no way to make it work properly)
- 1seg tv (japanese model)
- finger sensor
- Fn + (x) combinations
- S1 and eject buttons on the front of the laptop
- Headphone jack output, it works but the pc speakers don't become mute (it's useless like this to put headphones)
- card reader  (Sd and sony pro are not working thx to geekygirl who tested it)

If somebody succeeded to make something else work please write here, in this way we can make a small guide.
See ya.

Try typing ALSAMIXER in a terminal and tab to the inputs section.  Check that your mike is turned up there.

---

### Post by ilcontegis on 2009-04-26
> **gcvisel said:**
> Try typing ALSAMIXER in a terminal and tab to the inputs section.  Check that your mike is turned up there.

Thank you man, but this is the first thing I tried to do. Is not working.:(

---

### Post by leibnitz27 on 2009-04-28
Using 9.04 - I've got the CD eject working, by patching the sony-laptop kernel module as mentioned here:

[http://www.pharscape.org/forum/index.php?topic=696.0](http://www.pharscape.org/forum/index.php?topic=696.0)
(patch here - [http://ta.iki.fi/ubuntu/](http://ta.iki.fi/ubuntu/) )

[as per my earlier post, my SD card reader worked out of the box with 9.04.]

There's some info on the globetrotter in that thread too, but I've run out of time for tonight! :)

Lee

edit:  In case you feel brave and can't be bothered to compile your own:
[http://www.benf.org/files/sony-laptop.ko](http://www.benf.org/files/sony-laptop.ko)
(don't trust random binaries of the internet, etc etc etc ;) )

---

### Post by geekygirl on 2009-04-28
Ah excellent! Awesome find there :P

---

### Post by geekygirl on 2009-04-29
ok I am going into noob mode now...

Ca you please explain how you did it? (ie where and how to install)I would be most appreciative, as would others who might be scratching their heads right now lol

---

### Post by leibnitz27 on 2009-04-29
If you want to go from the binary I've posted above to test

* backup /var/lib/modules/2.6.28-11-generic/kernel/drivers/misc/sony-laptop.ko
* rmmod sony_laptop
* copy new one over the above file
* modprobe -v sony_laptop

... press eject! :)

If you want to compile it up yourself, you need the kernel tools and source (I'm definitely assuming jaunty release here ;)

sudo apt-get install fakeroot build-essential makedumpfile
sudo apt-get build-dep linux
sudo apt-get install linux-source-2.6.28

untar the source (from /usr/src), patch the sony_laptop.c, and the sonypi.h files (man patch, if you've not used it before)

build as per the instrunctions on the link above, bob's your uncle!  (and yay to the patch author, which wasn't me).

---

### Post by geekygirl on 2009-04-29
Thank you so much for this! (and props to the person who created the kernel patch in the first place :) )

Did you notice the eject key works, but so do the Fn keys?

Awesome!

(I am a kernel noob btw, hardly ever added things to them before, so thanks for showing the way ;) )

---

### Post by ilcontegis on 2009-04-29
Thank you very much, I update the main page now.

I really hope that someone succeed to make the mic and headphone work. This is the most important problem to me now. :)

---

### Post by geekygirl on 2009-04-29
I am also writing this up on my blog (don't look now as there isnt anything there anymore lol) so that if people search Google they can see more about using Ubuntu/Linux with the TT as I found it hard to find information.

With full credit and links back here :)

---

### Post by ilcontegis on 2009-05-08
It went out alsa 1.0.20 but nothing changed....same problems :(

---

### Post by stratusgr on 2009-05-14
I have a tt21wn vaio.I try to use the patch but when i try to use make -C .... i get several errors and the procedure stops.Also i try to use the sony-laptop.ko but no luck with the fn keys and eject button.Any idea to fix the problem;

---

### Post by elboeufx on 2009-05-16
Hi Everyone--

I'm new to Ubuntu, so, as usual, I'm asking questions that are probably ludicrous. Nonetheless, as someone who doesn't really do code very well, I'm hoping someone can help me in a step-by-step way. 

I'm a Mac refugee (love the OS, hate the hardware . . .) and recently bought at Sony Vaio TT-180c, thinking I'd put Ubuntu on it and live happy.

For the most part I'm happy, but I'm having trouble installing the sony_vgn_tt11_ubuntu9.04_2.6.28-11.patch.

I tried to do it using a few elementary command lines given by a friend.

Here's what I tried:

I tried: root@TamasComputer:~# apt-get install  sony_vgn_tt11_ubuntu9.04_2.6.28-11.patch 

But I got the following response from Terminal: 

Reading package lists... Done 
Building dependency tree       Reading state information... Done 
E: Couldn't find package sony_vgn_tt11_ubuntu9.04_2.6.28-11.patch 

Then I tried: wget  [http://ta.iki.fi/ubuntu/\sony_vgn_tt11_ubuntu9.04_2.6.28-11.patch]("http://ta.iki.fi/ubuntu/%5Csony_vgn_tt11_ubuntu9.04_2.6.28-11.patch") 

And I got the following from Terminal: 

--2009-05-14 10:44:22--   [http://ta.iki.fi/ubuntu/sony_vgn_tt11_ubuntu9.04_2.6.28-11.patch](http://ta.iki.fi/ubuntu/sony_vgn_tt11_ubuntu9.04_2.6.28-11.patch) 
Resolving ta.iki.fi... 217.30.184.182 
Connecting to ta.iki.fi|217.30.184.182|:80... connected. 
HTTP request sent, awaiting response... 200 OK 
Length: 23016 (22K) [text/x-diff] 
Saving to: `sony_vgn_tt11_ubuntu9.04_2.6.28-11.patch' 

100%[=====================================>] 23,016      52.8K/s   in  0.4s     
2009-05-14 10:44:23 (52.8 KB/s) -  `sony_vgn_tt11_ubuntu9.04_2.6.28-11.patch' saved [23016/23016] 

So then I tried: root@TamasComputer:~# apt-get install  sony_vgn_tt11_ubuntu9.04_2.6.28-11.patch 

But I got the following from Terminal again: 

Reading package lists... Done 
Building dependency tree       Reading state information... Done 
E: Couldn't find package sony_vgn_tt11_ubuntu9.04_2.6.28-11.patch 

So, I think the package was downloaded the second time, but then the  computer wouldn't install it. Is there something I'm doing wrong? Should  I be typing a different command line? 

I was told to try Adept, but whenever I open it, regardless of whether I'm in root via Terminal, it tells me I don't have the privileges to change anything. I've looked around at various ways and means of installing patches, but, frankly, I'm confused, since the examples frequently are for different software, and I have a hard time differentiating between essential code and the examples.

Any help would be greatly appreciated.

Thanks,
Elboeufx

---

### Post by rick1500 on 2009-05-17
> **ilcontegis said:**
> Thank you very much, I update the main page now.

I really hope that someone succeed to make the mic and headphone work. This is the most important problem to me now. :)

I'm able to use the headphones with the laptop speakers muted on my Vaio TT in Ubuntu 9.04 by doing the following:

[LIST]
[*]add "options snd_hda_intel model=6stack-dig" to /etc/modprobe.d/alsa-base.conf
[*]reboot.
[*]open alsamixer, select the "HDA Intel (Alsa mixer)" device.
[*]click the "Preferences" button to add the "Surround" and "Front" controls.
[*]use "Surround" to control the headphones and "Front" to control the laptop speakers independently.
[/LIST]
 It's not as nice as having the laptop speakers automatically mute when headphones are plugged in, but at least you can listen to headphones without disturbing others.  I just have "Front" muted since I usually use headphones or external speakers exclusively.

I have not tried the mic, but maybe these additional sliders will help with that too.

There is obviously a bug that needs to be filed in launchpad about these sliders being mislabeled and the additional option needing to be added to alsa-base.conf manually.

---

### Post by ilcontegis on 2009-05-18
@ elboeufx

I tried to explain better in the first page what is to do.
Hence to me is not working

---

### Post by ilcontegis on 2009-05-19
Thank you rick1500 I added your explanation on the first page.
:popcorn:

---

### Post by elboeufx on 2009-05-20
Dear ilcontegis,

Thanks for your help. Much appreciated. However, it still doesn't seem to work for me.

First, I downloaded the sony-laptop.ko to my desktop, as per your instructions.

But when I go into terminal and enter: sudo cp /var/lib/modules/2.6.28-12-generic/kernel/drivers/misc/sony-laptop.ko /var/lib/modules/2.6.28-12-generic/kernel/drivers/misc/sony-laptop.ko.bk

Terminal gives me the following:cp: cannot stat `/var/lib/modules/2.6.28-12-generic/kernel/drivers/misc/sony-laptop.ko': No such file or directory

I'm using 9.04, if that's any help.  I'm sure I'm just entering something wrong in the command line. 

Thanks,
Elboeufx

---

### Post by ilcontegis on 2009-05-20
you need to go to see where is located the sony-laptop.ko inside the system. try to search it, and from the properties you will be able to see the path.
Probably as I have a 64 bit edition I have another path.
Be careful that you will have a sony-laptop.ko file for each kernel you have. Be sure to change the one of the kernel you are using.

I followed this guide myself but it did not work so I don't know so much more how to help you. Maybe someone else succeeded. But you know, we have another button to open the cd player, so to me is not so important.

---

### Post by elboeufx on 2009-05-21
Dear ilcontegis--

Thanks again for continuing to help me.

First off, I'm not so concerned about the eject button, since as you say there is another button that opens the drawer anyhow. Yes, it would be nice to have, but it's not my main reason for wanting to have the Sony patch. There are a number of outstanding issues that need to be resolved on my TT, and I want to get the patch in to see if it makes a difference. My FN keys don't work; my power management is wonky, where it will automatically suspend if the power chord is in, but not if it's out; my webcam doesn't seem to work; there's the identified problem with the speakers (which I need the patch installed to fix). There are a few other things as well. I'd like to get the patch in and working, see whether it fixes anything, and then move on from there.

I am using kernel 2.6.28-11-generic. The OS (9.04) is installed on an external hard drive that my laptop boots from. This wsa done by a friend in order to preserve Vista (and my Sony support) if all else fails, but sadly this friend is too busy to help me further and has encouraged me to use the forums. I don't think he realizes how useless I am when it comes to code, or this system. As a Mac user I've been accustomed and addicted to certain ease of access: all the programs are in one place, a file called applications, and when you want to connect a file type with one of them you just go "open with" and a nice neat list pops up etc. (I still can't find Adobe Acrobat Reader 9, no matter how many times I run "search for files" and open every single folder looking for the right purple diamond, in order to link it with .pdf files in Thunderbird, but that's another issue . . .)

When I go into File System /var/lib/ there is no folder entitled "modules" hence the inability of terminal to locate the file you are talking about in the command line, which is why terminal always tells me, "cannot stat" when I try and enter your code. Essentially, there is no Sony module of any kind, or any kind of Sony patch, installed on my computer apart from the two files on my desktop: 1) sony_vgn_tt11_ubuntu9.04_2.6.28-11.patch; and 2) sony-laptop.ko. Neither of them, as far as I can tell, are doing anything other than sitting there, inert. When I double click the first I get a window with a bunch of code in it, and when I double click the second I get "sony.laptop.ko" cannot be opened. 

I know my problem must be utterly elementary, perhaps even painfully so, perhaps to the point of barring me from the basics necessary for being part of the Ubuntu community. How do I get these patches, either of them, into my system? Obviously, opening terminal and following the instructions you kindly left doesn't work because there just is no "module" of any kind, including Sony, in my OS.

I have been tempted to just give up, and go back to Vista, but I feel as if I'm so close to having a laptop running on Ubuntu that I want to pursue it to the point of absolute failure. Besides, Vista is just so bad that my heart sinks every time I have to use it.

Anyhow, one last post here. If anyone at all can help me, walk me through this thing, I'd really appreciate it. And maybe there are some other Ubuntu dunces out there who might profit from this as well.

In any case, I want to thank you, ilcontegis, for the help you've offered so far. Sorry I'm such a poor disciple.

Best,
Elboeufx

---

### Post by ilcontegis on 2009-05-21
Don't worry :)...we are all a big family here, so no problem.

it is impossible that you don't have the file. Did you make a research? You must find it. My webcam is working perfectly, but maybe in your model you have another type? are you sure your friend installed correctly ubuntu? you should have the sony-laptop file.

I have another solution for you. If you wish is possible to download the latest kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") the .30 is still in rc6 but you can try it. 
The .30 kernel will implement all the fix for our vaio tt. So by installing that kernel by theory you should have the fn buttons working and the eject button as well. I am not sure about the camera, as I don't know which model you have.

If you wish to put the latest kernel:
1. the pc can have problem after. In this case from the grub select the previous kernel.
2. some software might not work anymore. 
3. if you do it I do not assume the responsability in case of problem. Personally I did it, but I had some problems with some software, so I prefere to wait the karmic koale this october.

What you have to do to install
[From here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc6/") you will download the 2.6.30 rc6 kernel (i suggest you to check sometimes the kernel index on this website to see when the .30 stable go out and install it).
You need to download and install 4 file as far as i undestood:
linux-headers-2.6.30-020630rc6-generic_2.6.30-020630rc6_amd64.deb [COLOR="Red"]if you have a 64bit[/COLOR] 	
linux-headers-2.6.30-020630rc6-generic_2.6.30-020630rc6_i386.deb [COLOR="Red"]if you have a 32 bit[/COLOR]	
linux-headers-2.6.30-020630rc6_2.6.30-020630rc6_all.deb [COLOR="Red"]in both cases[/COLOR]
linux-image-2.6.30-020630rc6-generic_2.6.30-020630rc6_amd64.deb	[COLOR="Red"]if you have a 64bit[/COLOR] 
linux-image-2.6.30-020630rc6-generic_2.6.30-020630rc6_i386.deb	[COLOR="Red"]if you have a 32 bit[/COLOR]
linux-source-2.6.30_2.6.30-020630rc6_all.deb [COLOR="Red"]in both cases[/COLOR]

I hope this can help you. remember that if you have a problem with this kernel you can always use the grub to make the pc start with a previous kernel and then by using synaptic uninstall the latest kernel.
**Be careful**

See ya,
Teo

---

### Post by geekygirl on 2009-05-26
Just a quick question: has anyone tried 2.6.30 RC6 with any other Ubuntu derivatives?

I am asking because after installing xubuntu-desktop and removing ubuntu-desktop (and all its packages ;) ) I had a few issues with my Fn keys no longer working (scratching my head a bit - maybe I just fat fingered it somewhere though lol)

So now I am running the minimal installer as I like lean and mean (do not want Crunchbang though as its based on 8.10 still) and am curious if I used that with the minimal install would it save a bit of extra effort in patching the older kernel or will there be other things that I will need to look out for?

(no I have not updated my blog yet to feature all this good TT info :( )

---

### Post by elboeufx on 2009-05-26
Hi Everyone--

Okay. Thanks for all the information, especially to ilcontegis.

I have managed to get my FN keys and eject button working. It was, as I suspected, a deceptively simple task.

So, I offer this to everyone who's in my shoes: totally inexperienced with Ubuntu.

Basically, what ilcontegis has done in the first post on this thread is what needs to be done, though there are a few preliminaries.

I'm running Ubuntu 9.04 32 bit (Kernel 2.6.28-11-generic) on a TT-180c, which, I understand, is the Canadian variant of the ultraportable.

This is what I did:

1) Go to "Places" on the top menu bar.
2) Click on "Search for Files."
3) In the "Look in Folder" drop-down menu, hit "File System"
4) Type "Sony" into "Name Contains," and hit enter.
5) You will get a huge list of everything in the computer that pertains to Sony. Scroll down the list until you find a file called "sony-laptop.ko." Right beside the name you will see the "Folder" in which this is located (in my case it was /lib/modules/2.6.28-11-generic/kernel/drivers/misc
6) Essentially, this is the line you will type in (using terminal) following ilcontegis's instructions: "sudo cp" and then the name of your folder. The rest you just do as ilcontegis said, and it works!

It's beautiful! Thanks a million. (And thanks to the friend who sorted this out for me.)

Now if anyone can tell me how to get full power out of my wireless card (runs at 30% on Ubuntu and 100% on Vista from the same location); and why for some reason the computer won't automatically suspend (even though it's set up to do so in Power Manager), I'd be much obliged . . .

I've got to say I'm very glad to be using Ubuntu, and happily free of my crappy Apple hardware. No more visits to the Mac service centre!

Cheers,
Elboeufx

---

### Post by geekygirl on 2009-05-28
Hmm tried the kernel patch - gets the Fn keys running under Xubuntu - no eject key (it was working under Ubuntu though :( ) or any other keys for that matter - at least with Ubuntu the volume and mute keys are working, not so for Xubuntu - something is a miss here!

Just tried the RC6 kernel with Xubuntu, Fn keys work but none of the front keys are still.

Seems I will be resintalling Ubuntu, perhaps install pure XFCE over the top of it, minimal install yielded the same results with regards to hardware and Fn keys....maybe there is something missing in XFCE/Xubuntu libs-wise or otherwise that is also required to get these buttons to work 	](*,)

---

### Post by elboeufx on 2009-05-28
Hi Everyone Again--

Now that I've got the FN keys and eject button working, I'm onto the next stage . . . getting my wireless signal going at full strength. It works at 100% on Vista from my office, but bounces between 30 and 40% from the same location on Ubuntu. It makes up- and downloading a painful process.

I've looked up some information on the forums. A lot of people say to go with ndiswrapper, though there are some conflicting claims here. Another source said to download and install WLan Driver Broadcom 802.11g 3.100.46.0.zip.

From my "Device Manager" I've managed to get the following info. on my "Network Controller," which I assume is my wireless card: Wireless WiFi Link 5100, Intel Corporation, PCI. Everything underneath this has a question mark sitting in a purple box next to it.

Any help particular to the TT would be much appreciated.

Cheers,
Elboeufx

---

### Post by ilcontegis on 2009-05-28
> **geekygirl said:**
> Hmm tried the kernel patch - gets the Fn keys running under Xubuntu - no eject key (it was working under Ubuntu though :( ) or any other keys for that matter - at least with Ubuntu the volume and mute keys are working, not so for Xubuntu - something is a miss here!

Just tried the RC6 kernel with Xubuntu, Fn keys work but none of the front keys are still.

Seems I will be resintalling Ubuntu, perhaps install pure XFCE over the top of it, minimal install yielded the same results with regards to hardware and Fn keys....maybe there is something missing in XFCE/Xubuntu libs-wise or otherwise that is also required to get these buttons to work 	](*,)

Do not use xubuntu, is really crap. If you wish to use xfce put ubuntu minimal and then install xfce. I do not understand the meaning of xubuntu...is NOT light, is for 80% GNOME, is useless. 
Much bettere ubuntu minimal + xfce or if you wish a very ligh OS put ubuntu minimal + LXDE.

@ elboeufx

I am sorry man, in this case I have no clue of what is your problem. Moreover it seems you are the only one with a vaio tt having this problem.
Are you sure you did not mess up something?

---

### Post by elboeufx on 2009-05-29
Hi ilcontegis--

I don't know whether I screwed up. Is there any way to troubleshoot? I have never really played around with the wireless; I just noticed it didn't really have the connection for quick down- and uploading. I know there are other people out there who have this problem with Sonys, but not necessarily the TT. Does anyone else know anything?

My final major issue is power management. For some reason, when the TT is plugged in it will automatically suspend. When it's not plugged in it won't; the screen goes dark but the green light stays on. And I have adjusted this numerous times in the Power Manager Applet (even tried the KDE version, but KDE stuff runs wonky on my computer), but it just doesn't want to put the computer to sleep automatically when it's running on battery. I can do it manually by hitting the power button or closing the lid, but that's a pain, since my work frequently calls me away from my computer. In addition to this, when the computer is asleep and I start it up again, it makes this awful sound, kind of like sand pouring through into a metal duct. I suspect it's a software issue because it works fine in Vista. For some reason my hardware manager doesn't really know what kind of battery it is, only saying "Sony" when I click on the purple square with the question mark in it. If anyone has had this experience, or knows how to fix it, along with the above, that would be great.

Otherwise, the computer is mainly usable now, so I might just have to put up with this stuff, though the weak wireless is truly irritating.

Thanks,
Elboeufx

---

### Post by geekygirl on 2009-05-29
> **ilcontegis said:**
> Do not use xubuntu, is really crap. If you wish to use xfce put ubuntu minimal and then install xfce. I do not understand the meaning of xubuntu...is NOT light, is for 80% GNOME, is useless. 
Much bettere ubuntu minimal + xfce or if you wish a very ligh OS put ubuntu minimal + LXDE.

Probably should have specified that I did the minimal install and installed the XFCE dekstop - my bad ;)

The minimal install is just that, minimal - it doesn't get a lot of what you obviously need in order to get the TT running good under Ubuntu and my limited knowledge as to what would actually be required to be installed from a minimal install is going to require some good googling :) (Wont be able to get stuck into that as the next study period at Uni starts on Monday and I just need a working machine now :( )

Thanks for the efforts ilcontegis you have put in some effort to which the rest of the Ubuntu/TT owners are truly grateful!

---

### Post by ilcontegis on 2009-05-30
> **elboeufx said:**
> Hi ilcontegis--

I don't know whether I screwed up. Is there any way to troubleshoot? I have never really played around with the wireless; I just noticed it didn't really have the connection for quick down- and uploading. I know there are other people out there who have this problem with Sonys, but not necessarily the TT. Does anyone else know anything?

My final major issue is power management. For some reason, when the TT is plugged in it will automatically suspend. When it's not plugged in it won't; the screen goes dark but the green light stays on. And I have adjusted this numerous times in the Power Manager Applet (even tried the KDE version, but KDE stuff runs wonky on my computer), but it just doesn't want to put the computer to sleep automatically when it's running on battery. I can do it manually by hitting the power button or closing the lid, but that's a pain, since my work frequently calls me away from my computer. In addition to this, when the computer is asleep and I start it up again, it makes this awful sound, kind of like sand pouring through into a metal duct. I suspect it's a software issue because it works fine in Vista. For some reason my hardware manager doesn't really know what kind of battery it is, only saying "Sony" when I click on the purple square with the question mark in it. If anyone has had this experience, or knows how to fix it, along with the above, that would be great.

Otherwise, the computer is mainly usable now, so I might just have to put up with this stuff, though the weak wireless is truly irritating.

Thanks,
Elboeufx

Did you try to run a live cd? do you have the same problems?

---

### Post by ilcontegis on 2009-05-30
> **geekygirl said:**
> Probably should have specified that I did the minimal install and installed the XFCE dekstop - my bad ;)

The minimal install is just that, minimal - it doesn't get a lot of what you obviously need in order to get the TT running good under Ubuntu and my limited knowledge as to what would actually be required to be installed from a minimal install is going to require some good googling :) (Wont be able to get stuck into that as the next study period at Uni starts on Monday and I just need a working machine now :( )

Thanks for the efforts ilcontegis you have put in some effort to which the rest of the Ubuntu/TT owners are truly grateful!

I did not do anything :) but thanks, I just want that our vaio tt works perfectly with ubuntu as soon as possible.

You did install minimal + xfce! :) sorry I should think about that..
I completely agree with you, with the minimal you will not install too many packages that are necessary to have your tt working properly. If you have a lot of free time, maybe you will be able to fix it.
Otherwise I try to give you 2 possible solutions:
1. Install ubuntu full, and then put xfce (is not at all the same thing but....)
2. Install Ubuntu. Personally I now have Jaunty 64bit and is running smoothly without any problems.

I am waiting now the kernel .30 stable hoping that some problems will be solved....

---

### Post by cyrus_SR on 2009-06-03
So what about Memory Stick Ricoh R5C592? Is it work?

---

### Post by elboeufx on 2009-06-03
ilcontegis,

Forgive my ignorance, but what is a live CD?

elboeufx

---

### Post by cyrus_SR on 2009-06-03
> **elboeufx said:**
> ilcontegis,

Forgive my ignorance, but what is a live CD?

elboeufx

[http://en.wikipedia.org/wiki/Live_CD](http://en.wikipedia.org/wiki/Live_CD)

You can download iso file from official site (K\Ed\X)Ubuntu. Burn it to clear CD and start your system from this CD. Make in BIOS boot from CD-ROM. Then insert this CD and reboot your computer.

---

### Post by ilcontegis on 2009-06-10
It went out the new kernel 2.6.30.
It's working perfectly! FN combinations and eject button will now work!

---

### Post by geekygirl on 2009-06-11
The microphone is working.
 
I have been using Skype with both webcam and microphone with no issues on my TT now.
 
I am using a headset though (in case that makes a difference) and I just set the sound to Capture: HDA Intel - ALC889 Analog (Pulse Audio Mixer) and it works perfectly.
 
I also used the sound fix to use the headphones as well.
 
:D

---

### Post by ilcontegis on 2009-06-12
> **geekygirl said:**
> The microphone is working.
 
I have been using Skype with both webcam and microphone with no issues on my TT now.
 
I am using a headset though (in case that makes a difference) and I just set the sound to Capture: HDA Intel - ALC889 Analog (Pulse Audio Mixer) and it works perfectly.
 
I also used the sound fix to use the headphones as well.
 
:D

I cannot make it work,
Would you mind to explain a bit more in detail?
Where you set HDA Intel?
Did you try with the integrated mic?
THX

---

### Post by geekygirl on 2009-06-12
> **ilcontegis said:**
> I cannot make it work,
Would you mind to explain a bit more in detail?
Where you set HDA Intel?
Did you try with the integrated mic?
THX

No have not tried the integrated mic, as I said, using a headset plugged in and it works fine.

All I did was open Volume Control, change the Device in the drop down at the top to Capture: HDA Intel - ALC899 Analog (Pulse Audio) and I was able to test this worked using the voice recorder under Sound & Video, voila - I can talk on Skype.

As I only use an external mic and headset I can only say that the mic jack works with an external mic as I have had no need to test the internal mic :(

---

### Post by geekygirl on 2009-06-14
Now I know a couple of you said the SD card reader is working but on my TT it is not :(

I cannot say with all honesty if it was working after the initial install, but (as I have now got a very full SD card to empty from my camera!!) when I tried using it this evening I get a bit of a flicker of activity on the HDD (as if it is thinking about something) and nothing..

I have tried a couple of brands of SD card (Verbatim, Sandisk, ADATA) in case it was just a card issue to no avail...

Is anyone else experiencing this as it seems to be a bit of an issue across the board with Jaunty and SD card readers :(

---

### Post by elboeufx on 2009-06-19
> **ilcontegis said:**
> It went out the new kernel 2.6.30.
It's working perfectly! FN combinations and eject button will now work!

Hi,

Can someone give me a quick tutorial on how to install this new Kernel? Normally I used the "update manager" through "System." The new kernel isn't there. But I'm sure I could do it through terminal . . .

Thanks,
Elboeufx

---

### Post by ilcontegis on 2009-06-19
> **elboeufx said:**
> Hi,

Can someone give me a quick tutorial on how to install this new Kernel? Normally I used the "update manager" through "System." The new kernel isn't there. But I'm sure I could do it through terminal . . .

Thanks,
Elboeufx

Again?
I already explained everything step by step..
> **ilcontegis said:**
> 

If you wish is possible to download the latest kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") the .30 is still in rc6 but you can try it. 
The .30 kernel will implement all the fix for our vaio tt. So by installing that kernel by theory you should have the fn buttons working and the eject button as well. I am not sure about the camera, as I don't know which model you have.

If you wish to put the latest kernel:
1. the pc can have problem after. In this case from the grub select the previous kernel.
2. some software might not work anymore. 
3. if you do it I do not assume the responsability in case of problem. Personally I did it, but I had some problems with some software, so I prefere to wait the karmic koale this october.

What you have to do to install
[From here]("http://kernel.ubuntu.com/~kernel-ppa/mainline") you will download the 2.6.30 rc6 kernel (i suggest you to check sometimes the kernel index on this website to see when the .30 stable go out and install it).
You need to download and install 4 file as far as i undestood:
linux-headers-2.6.30-020630rc6-generic_2.6.30-020630rc6_amd64.deb [COLOR="Red"]if you have a 64bit[/COLOR] 	
linux-headers-2.6.30-020630rc6-generic_2.6.30-020630rc6_i386.deb [COLOR="Red"]if you have a 32 bit[/COLOR]	
linux-headers-2.6.30-020630rc6_2.6.30-020630rc6_all.deb [COLOR="Red"]in both cases[/COLOR]
linux-image-2.6.30-020630rc6-generic_2.6.30-020630rc6_amd64.deb	[COLOR="Red"]if you have a 64bit[/COLOR] 
linux-image-2.6.30-020630rc6-generic_2.6.30-020630rc6_i386.deb	[COLOR="Red"]if you have a 32 bit[/COLOR]
linux-source-2.6.30_2.6.30-020630rc6_all.deb [COLOR="Red"]in both cases[/COLOR]

I hope this can help you. remember that if you have a problem with this kernel you can always use the grub to make the pc start with a previous kernel and then by using synaptic uninstall the latest kernel.
**Be careful**

See ya,
Teo

Just in this case instead of the 2.6.30 rc6 you will take the latest.
What is not clear?

---

### Post by elboeufx on 2009-06-21
Teo--

Thanks. I didn't see this the first time. This is the thread I follow, and I only saw your two-line message saying you'd installed it and it worked. So, I download the right one, and then go into terminal and type "sudo apt-get install <<filename>>? Anyhow, I might just wait with this until it's made official. I have enough lingering bugs anyhow.

I tried Live CD and it didn't fix my power management issue. I also tried fixing it with conf. eidtor, changing the values around there, but it still won't suspend on battery, only on AC power. Right now I'm running off an external hard-drive; I'm going to try installing to hard-drive to double boot next week. We'll see if that fixes it. Don't know why the double boot, since I never use Vista anymore anyhow, but I guess it's better to be safe.

Maybe then I'll try the new kernel. From what I gather you can also get it by going alt+f2, and then typing update-manager -c -d.

Thanks,
Elboeufx

---

### Post by ilcontegis on 2009-06-21
Ok, so the dual boot is a good choice, but are you sure you really need windows? Me too at the beginning I putted the dual boot, but then I noticed that it was worthless. I much prefer to use Ubuntu and install XP under virtualbox (it works perfectly). Expecially when I use 2 screen I can have ubuntu on one screen and windows emulated on the other one.
Maybe virtualbox can be a solution for you as well.

Concerning the installation.
I suggest you to do like this. (I actually did in the same way and I did not have any problem)
0. Decide if you want 32 or 64 bit (I use 64bit and no problem)
1. Decide if you want dual boot or use virtualbox
2. Make 3 partition for ubuntu: one for the OS in ext4 (/), one for your home in ext3 just to be sure (/home) and one for the swap (less than 1gb)
3. Install and reboot
4. Download the latest version of the kernel (actually you will need only three .deb file):
- first is the linux-headers.............**all**.deb
- then the linux-headers.........**generic**..........deb
- finally the linux-**image**..........................deb
5. Install this 3 files **in this order** by simple double clicking on them. (check before if you have a 32 or 64 bit)
6. reboot
7. Now you can add what you need repository extra, programs, etc.

I hope this helps
For whatever problem just ask
See ya
Teo

---

### Post by elboeufx on 2009-06-22
Teo--

Thanks a ton. I will try this. I need to think about how badly I need Windows. I didn't know about virtual box, so I will check it out now, and see if it will answer my needs. If it does, then most probably I won't bother with the dual boot, because I really hate windows. I'll let you know how all this works out . . .

Cheers,
Tamas

---

### Post by ilcontegis on 2009-06-22
It's my pleasure.
I forgot to tell you one important thing: very soon it will come out virtualbox 3 (now is in beta) with the 3d support.
They say that we should be able to finally play games with virtualbox.
Another important thing, if you want to use virtualbox take the last version from the website, DO NOT use the ose (open source edition) because it has a lot of limitations.
you can add the repo from here by following the steps:
[http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

If you wish to try here you have the BETA version of virtualbox 3
[http://download.virtualbox.org/virtualbox/3.0.0_BETA1/]("http://download.virtualbox.org/virtualbox/3.0.0_BETA1/")

Hope this helps,
Teo

---

### Post by akbardotinfo on 2009-06-23
Thanks in million! :)
all work, fn, brightness,sound controller,eject key! SUPER!
just suggestion, maybe using `uname -r` would be much easy for newbie user to get to their current kernel location :)

```
sudo cp  /lib64/modules/`uname -r`/kernel/drivers/misc/sony-laptop.ko /lib64/modules/`uname -r`/kernel/drivers/misc/sony-laptop.ko.bk
```

```
sudo mv /home/teo/Scrivania/sony-laptop.ko /lib64/modules/`uname -r`/kernel/drivers/misc/
```

Thank you!!

---

### Post by elboeufx on 2009-06-29
Hi Teo and Gang,

Well, the new kernel works like a hot damn! I've got it all done, everything loaded right onto the hard drive, and I'm perfectly happy except for one thing (below).

I decided not to go double boot, on Teo's advice. So far, it's the right move.

Just one problem. Maybe someone can help me. I downloaded a bunch of codecs and whatnot to run video from [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) and now I do not have the "surround" function in my HDA Alsa Sound Mixer. This means I can't use my headphones. I go into "preferences" to enable it, but it's not included as one of the things that can be enabled. It's not listed at all!

Here's what I get when I open alsabase.conf:

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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2

As you can see, there's a bunch of overrides here, "loaded above," probably as a result of the codecs and plug-ins and whatever that I downloaded. Surround was certainly there as an option before I did this! So, now, the question is: How do I get it back? I really need the headphone jack to work.

The new kernel was a clean instal by the way. And the mixer was fine before I got the necessary codecs.

Thanks,
Tamas

---

### Post by elboeufx on 2009-06-30
Hi Everyone--

So nobody knows how to get my "Surround" back in Alsa? I've looked through the forums, but no help. I tried deleting the /var/lib/alsa/asound.state and restarting, but it didn't change anything. Is there another strategy for getting the headphones to work?

Another problem has emerged in the meantime: My computer won't inhibit suspend function when the computer is in the middle of doing something like listening to music, or undertaking a massive print job. Does anyone have any experience here?

Much appreciated . . .

Thanks,
Tamas

---

### Post by ilcontegis on 2009-07-07
Hi man,
did you follow the first page how to?
**- How to make work the headphone jack exit** (Thanks to rick1500 for the help)

1. Give
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```
and add this at the end of the file
```
options snd_hda_intel model=6stack-dig
```
2. Reboot the pc
3. Open alsamixer, select the "HDA Intel (Alsa mixer)" device.
4. Click the "Preferences" button to add the "Surround" and "Front" controls.
5. Use "Surround" to control the headphones and "Front" to control the laptop speakers independently.
(On my pc it did work!)
This must work.
Which codec did you install? maybe you installed something wrong....
if you need codecs for ubuntu just give
```
sudo apt-get install ubuntu-restricted-extras
```
you will have all the codecs you need.

The problem of suspend I do not have any ideas, sorry. However it often happens that the suspend function does not work on newer laptops.

Hope this helps.
Teo

---

### Post by elboeufx on 2009-07-07
Hi Teo--

Yeah, I went through that. The problem is that "surround" is not one of the options I can add to my Alsa Mixer. So when I add the line the Also mixer always pops up with an error because "surround" is simply not there. My suspicion is that I have a bad version of the Alsa mixer, but I don't know how to uninstall and reinstall it. Lot's of work.

I've solved the suspend issue, at last. Some programs come with a function that suspends automatic sleep (such as the music player); other wise, if I'm doing some big print run, I just use the "Power Manager Inhibit Applet," which seems to do the trick.

I will try your advice on the restricted codecs, but I do believe I've already done that. It's just really a question of trying to figure out why "surround" isn't one of the options listed in "Volume Control Preferences" in Alsa. Looking at the forums, some other people have problems with this too.

If you have any other ideas, I'd appreciate it. Otherwise, I'll try and muddle through . . .

Thanks,
Tamas

---

### Post by elboeufx on 2009-07-07
Hi Teo (Again),

I decided to try the headphone jack fix one more time, and for some reason this time it worked. I swear last time, I added the line to the .conf file, but ended up getting an error message from Alsa when I rebooted. This time, however, I rebooted no problem, and now the "surround" option was present! So I've got it all set up. Thanks for bearing with me. Your patience is appreciated.

I have found, too, that having Ubuntu installed on my TT's native hard-drive has cleared up the issue with the wireless (which now functions at full power) and also with the power management. It was wonky while running on an external hard-drive, but is now sorted out.

I also did not go double-boot, on your advice. Vista is completely gone from my computer. I don't miss it at all.

Now if someone could just tell me how to play Civilization IV on this computer I think that all my needs would be met . . .

Thanks,
Tamas

---

### Post by elboeufx on 2009-07-09
Hi Again,

Sigh. Just when it seemed everything was working. Has anyone had the experience that suddenly the eject button and the mute button no longer work? Everything else does, all the FN keys, but for some reason these two have stopped . . . I'm wondering, even with the new kernel (2.6.30-020630-generic) is there any way to reload the information for the various keys? For a while there they were working intermittently, then not at all . . .

Thanks,
Tamas

---

### Post by ilcontegis on 2009-07-10
> **elboeufx said:**
> Hi Again,

Sigh. Just when it seemed everything was working. Has anyone had the experience that suddenly the eject button and the mute button no longer work? Everything else does, all the FN keys, but for some reason these two have stopped . . . I'm wondering, even with the new kernel (2.6.30-020630-generic) is there any way to reload the information for the various keys? For a while there they were working intermittently, then not at all . . .

Thanks,
Tamas

Hi,
I have no clue at all why 2 buttons only are not working. 
It's really very very strange.......

Concerning Civ IV, as for all games you can always have a look on the winehq websites.
For instance here you have all the versions of Civ IV, just pick up the one you have and follow the instructions if needed:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2514]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=2514") 

See ya

---

### Post by elboeufx on 2009-07-10
Teo--

Thanks anyhow. It's very frustrating. It was all working so beautifully until about four or five days ago when the buttons went. They are still intermittent. Sometimes they work on every click, and then I have to hit them twenty or thirty times to get them to work, if they work at all. Eject works more often than S1 which works more often than mute. FN buttons all work still. 

I thought it might be a hardware issue, so I went into System>Preferences>keyboard shortcuts, and assigned different functions to the Eject, S1, and Mute buttons, in this case raising and lowering the volume, and they worked each time, so clearly the computer detects those buttons, but not in the case of the eject, S1, and mute functions. It's almost as if the whole thing has become corrupted somehow.

The same thing happened when I was using 2.6.28. I followed your system for getting the buttons to work, and they did, but then, after a while, and one too many "updates" via the update manager, they stopped working again. Has anyone else had this experience? Then I installed 2.6.30, and they were working just fine, and now, some three weeks later, the same problem (though in the former they didn't work at all, and now they work intermittently).

Should I try wiping the hard-drive again and doing a clean install? That seems like an incredible amount of work . . . seeing as how I just did that with the new kernel. Is ther any way to try and reinstall this module?

Yeesh.

Maybe I'll just wait for October . . .

Thanks,
Tamas

---

### Post by ilcontegis on 2009-07-11
you can try to reinstall if you wish.
If you divide the / and the /home when you reinstall you almost do not have to do anything as all the configurations are stored in the /home.

---

### Post by elboeufx on 2009-07-12
Thanks, Teo. I might try a reinstall, but I feel as if I've already spent far too much time getting this system to work, and having to go through it all again is just too much . . . The sad thing is it was fine, everything worked, and then boom out of nowhere these two keys stop. I went back to my external disk version, and the mute worked fine, so it's clearly a software issue. I would reinstall, but then what do I do: live in fear that each time my update manager tells me to install something I have to worry that it will kill something on my system? I think at this point I'll probably just live with it until October when the new version comes out. If that doesn't work, Windows 7 will be out by then, which I'm hearing good things about, and in a year Google will release their OS, which might be even better. In the meantime if anyone experiences this problem and has a fix, let me know . . .

Thanks,
Tamas

---

### Post by ilcontegis on 2009-07-13
you are quite unlucky..
but don't give up, maybe try once more.
I am not sure that with the new version of ubuntu something will change, you already have the kernel .30 that will be in ubuntu 9.10.
If really you keep having the same problems, you might think to change to something else.
Don't give up ;)
Teo

---

### Post by elboeufx on 2009-07-13
Teo--

Okay. I'll give it a shot. Maybe I'll post a message first to the Ubuntu community in general to see if there's any help for this problem. I don't mind doing the work once or twice, but three times is just too much.

Cheers,
Tamas

---

### Post by ilcontegis on 2009-07-14
> **elboeufx said:**
> Teo--

Okay. I'll give it a shot. Maybe I'll post a message first to the Ubuntu community in general to see if there's any help for this problem. I don't mind doing the work once or twice, but three times is just too much.

Cheers,
Tamas
Tamas, I understand very well.
Unfortunately sometimes these things happen. I hope you can solve your problem quickly ;)

All best 
Teo

---

### Post by elboeufx on 2009-07-14
Hi Teo--

Okay. I spent half the day yesterday fixing things. I went back to my old version of Ubuntu on my external disk to play around a bit, and then I went and reinstalled 9.04 on my computer. I decided to stick with kernel 2.6.28-13 instead of the new kernel, because it seems easier to fix if there's a problem, using your recommendations at the start of this thread. It took a long time, but the system is up and running fine again. So, for now, one last kick at this can, we'll see how it goes from here.

One note you may consider adding to your fix at the start of the thread. When I upgraded my external drive from kernel 2.6.28-11 to 2.6.28-13 the eject button and FN buttons stopped working again, but this was easily fixed by going back and simply reinstalling the sony-laptop,ko as per your instructions. It only takes a few minutes, not too onerous. But some newbies like myself might not realize this, and think that the system is broken again. So simply posting a note that says kernel upgrades, even minor ones, may require you to go through this process again would be useful, I think. At least until 2.6.30, where it's supposed to be fixed for you, though I think it's still buggy if you ask me.

Thanks for all your support! It keeps me using Ubuntu, which I do like very much, when it's working properly . . .

Best,
Tamas

---

### Post by ilcontegis on 2009-08-02
Installed the kernel 2.6.30.4.
No problems found, everything works perfectly...

---

### Post by leibnitz27 on 2009-08-07
(just come back to this after a few months distracted by a butterfly ;) )

Seen a few messages saying everything works, but not heard much about the 3G support - is this working for people?

I'm in the UK and have vodafone - vanilla 9.04 has built in configuration for this, so easy to set up, but when I attempt to connect, I get the following crash of NetworkManager in /var/log/messages ....

Anyone else been through this, before I start digging?  Or did it work for you?

Cheers,

Lee.



msg dump:


Aug  7 07:34:43 pinky kernel: [  283.028624] usb 1-3: USB disconnect, address 5
Aug  7 07:34:48 pinky kernel: [  287.836638] usb 1-3: new high speed USB device using ehci_hcd and address 6
Aug  7 07:34:48 pinky kernel: [  287.979954] usb 1-3: configuration #1 chosen from 1 choice
Aug  7 07:34:48 pinky kernel: [  288.068330] hso0: Disabled Privacy Extensions
Aug  7 07:35:08 pinky kernel: [  308.580799] usb 1-3: USB disconnect, address 6
Aug  7 07:35:08 pinky kernel: [  308.586409] *pde = 00000000 
Aug  7 07:35:08 pinky kernel: [  308.586433] Dumping ftrace buffer:
Aug  7 07:35:08 pinky kernel: [  308.586440]    (ftrace buffer empty)
Aug  7 07:35:08 pinky kernel: [  308.586443] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat i915 drm binfmt_misc ppdev bridge stp bnep hso input_polldev lp parport snd_hda_intel snd_pcm_oss arc4 snd_mixer_oss ecb snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi iwlagn snd_seq_midi_event iwlcore snd_seq snd_timer snd_seq_device joydev led_class mmc_block mac80211 snd uvcvideo pcmcia video sdhci_pci soundcore compat_ioctl32 intel_agp tpm_infineon tpm sdhci snd_page_alloc cfg80211 pcspkr psmouse serio_raw yenta_socket rsrc_nonstatic pcmcia_core iTCO_wdt iTCO_vendor_support videodev v4l1_compat btusb output agpgart tpm_bios sony_laptop ohci1394 ieee1394 e1000e fbcon tileblit font bitblit softcursor
Aug  7 07:35:08 pinky kernel: [  308.586571] 
Aug  7 07:35:08 pinky kernel: [  308.586578] Pid: 2863, comm: NetworkManager Not tainted (2.6.28-11-generic #42-Ubuntu) VGN-TT11WN_B
Aug  7 07:35:08 pinky kernel: [  308.586584] EIP: 0060:[<c0501a13>] EFLAGS: 00010206 CPU: 0
Aug  7 07:35:08 pinky kernel: [  308.586590] EIP is at mutex_unlock+0x3/0x10
Aug  7 07:35:08 pinky kernel: [  308.586595] EAX: 0000003c EBX: f5dac300 ECX: f5e7d060 EDX: 00000001
Aug  7 07:35:08 pinky kernel: [  308.586600] ESI: 00000001 EDI: 00000000 EBP: f5ffbe7c ESP: f5ffbe7c
Aug  7 07:35:08 pinky kernel: [  308.586606]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
Aug  7 07:35:08 pinky kernel: [  308.586621]  f5ffbe98 f81d9083 00000000 c062ac8f f4627000 f4627000 f5c9dba0 f5ffbf40
Aug  7 07:35:08 pinky kernel: [  308.586877] ---[ end trace 3a527f4aa6bd177a ]---
Aug  7 07:35:13 pinky kernel: [  313.348133] usb 1-3: new high speed USB device using ehci_hcd and address 7
Aug  7 07:35:13 pinky kernel: [  313.491491] usb 1-3: configuration #1 chosen from 1 choice
Aug  7 07:35:13 pinky kernel: [  313.605227] hso0: Disabled Privacy Extensions

---

### Post by quini on 2009-08-09
Hi!

This is my 1st message here; I've purchased a TT11LN/M (spanish version), and it has a built-in 3G modem.

I've remove Vista, installed XP (15G) & Karmic alpha 3 64 bits.  I'm using the 2.6.31-rc5 from [ppa]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc5/"), and Symio as a provider.

@leibnitz27

> **leibnitz27 said:**
> Seen a few messages saying everything works, but not heard much about the 3G support - is this working for people?

My experiences with 3G are that it works like a charm, using Network Manager; it simply appears as an option, together with wired and wireless networks, and config couldn't be as simple.

**But**...

-if I turn wireless off using the hardware button, then on again, I never get the 3G option available again
-some boots seem not to initialize the hardware correctly, as I'm not always shown the 3G option

When any of those behaviours occur, I've never managed to get it working using:
```
echo 1 > /sys/devices/platform/sony-laptop/wwanpower
```

Neither echoing 0, then 1...

Regards from Ibiza  :popcorn:

Edit: corrected wrong address to ppa kernel

---

### Post by ilcontegis on 2009-08-10
Sorry leibnitz27, I do not have the 3g on my tt (japanese version) so I cannot try it.

I do have a 1-seg tv but I cannot make it work

---

### Post by ilcontegis on 2009-08-10
Hello quini.
As you are using already the KK 9.10...
How is it working? Is it stable? And how is the new kernel .31?
I was thinking to put the KK but usually I wait until the alpha 5 or the beta to use it in my everyday pc.

let me know when you can.
See ya.

---

### Post by quini on 2009-08-11
Hi!

It's... an "alpha".  You can find several bugs, but it mostly works.

For instance, gdmsetup doesn't even open, and the lcd power isn't reduced nor turned off by the gnome-power-manager when on battery...

I don't recommend it to anyone who doesn't mind finding and solving problems...

Ah, thanks for opening this forum; I'll post the behaviour with my TT in a short while  ;)

---

### Post by ilcontegis on 2009-08-11
> **quini said:**
> Hi!

It's... an "alpha".  You can find several bugs, but it mostly works.

For instance, gdmsetup doesn't even open, and the lcd power isn't reduced nor turned off by the gnome-power-manager when on battery...

I don't recommend it to anyone who doesn't mind finding and solving problems...

Ah, thanks for opening this forum; I'll post the behaviour with my TT in a short while  ;)

It is a pleasure!
I think there should be this kind of post for each laptop in this way we can help each others to solve our specific problems, and at the same time we can make a mini guide to help others!

I'm waiting your comments on the KK alpha 3 ;)

See ya

---

### Post by quini on 2009-08-12
Hi again!

I've spent some time making some tests on my TT11LN.  As I mentioned in an older post, I'm using Karmic 64 bits (actually alpha 3), and the tests were run:

a) using the *karmic* kernel image linux-image-2.6.31-5-generic version 2.6.31-5.24
b) using the kernel image 2.6.31-rc5 from [kernel-ppa]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc5/")

Results are the same with both kernels as of Karmic beta 1 (updated).


I always used cold boot, never booted to windows, and run the test on battery, unplugged from AC.  An USB mouse was pluged in, and, if supported, the screen was set to maximum bright minus minus 5 (maximum bright, then pressed 5 times Fn+F5).


**Tests run:**
[LIST=1]
[*]**Is 3G available** in Network Manager?  If so, what does "cat /sys/devices/platform/sony-laptop/wwanpower" show?
Yes, 3G is available through NM and working fine (tested with the spanish Simyo provider).
Note 1: wwanpower contained the expected "1" (on) on the Karmic kernel, but "0" when using the ppa kernel; **see test 7**
Note 2: do you use to work without the battery inserted (as I do when at home)?  **See notes at the end of the post!**

[*]**Do Fn + F5 / F6 work** (lcd brightness)?
Yes, out of the box as of Karmic beta 1 (updated)

[*]Do **volume buttons** & mute work?
Yes, out of the box

[*]Does the **CD eject button** work?
Yes, out of the box

[*]Does the **S1 button** give a code (I've used "xbindkeys -k")?
Yes; the output is "m:0x0 + c:156  XF86Launch1"

[*]Does "sudo -s 'echo 0 > /sys/devices/platform/sony-laptop/bluetoothpower'" **power the BT device off**?  If so, how much -approximately- is the power savings (mW/h after 3 minutes)?
Yes, it seems to power the BT off, as the battery drain is lowered in approximately 800mW/h after 3 minutes; also, it appears as unavailable in gnome-bluetooth

[*]May I use "sudo -s 'echo X > /sys/devices/platform/sony-laptop/wwanpower'" to **power the Wwan ON or OFF** (where X= 0 or 1)?
**No**.  It accepts echoing 0 or 1 to that pseudo-file, but I've always been able to establish a working connection with my provider, despite wwanpower showed 0 or 1.  *Edit 18/8/09*: **[Filed as bug 414833 at launchpad.net]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/414833")**

[*]May I control the **CD reader power** through "/sys/devices/platform/sony-laptop/cdpower" (I could on my -died- Vaio TZ)?
**No**.  In my -dead- Vaio TZ I could turn power off echoing 0 onto that pseudo-file, but it doesn't even exist in the TT.  This also **has to be filed as a bug**

[*]May I set the **wifi** card (Intel 5100) to use the **power management** features to save battery?
**No**.  Running "iwconfig wlan0 power on" answers "operation not supported".  Also, "cat /sys/bus/pci/drivers/iwlagn/0000:02:00.0/power_level" always shows 0, despite it accepts echoing values from 1 to 5... **this also should be solved**, as it drains a lot of battery

[*]Does the **SD card reader** work?
**No**, and it shows nothing in dmesg.  What driver is it supposed to use?  I remember I've been able to use it sometimes, but I'll have to check in what conditions...
*Edit 18/8/09*: it sometimes work fine, but after eject it doesn't work any more.  Dmesg shows errors related to the "sdhci" module, and removing sdhci_pci & sdhci, and modprobing them does not solve the problem.

[*]Does it **suspend to RAM** fine?
Yes

[*]Does the **webcam** work (tested with "cheese")?
It works with the ppa kernel.
*Edit 18/8/09*: it now works fine with Karmic kernel 2.6.31-6 (rc6 based).

[*]Does the **"Wireless ON/OFF" button** work?  If so, does wifi, bluetooth & wwan work after switching it back to ON?
Yes
[/LIST]


**Notes**
[LIST=1]
[*]Have you got a HSUPA (3/3.5G) modem integrated in your Vaio TT?  I've *never* managed to get the 3G modem recognized when booting without having the battery inserted; it doesn't even appear when running *lsusb* (it's called *Bus 001 Device 004: ID 0af0:7601 Option*).
*Edit 18/8/09*: I noticed **it didn't work in windows either**, so I asked Sony, and they just answered "La bateria tiene que estar puesta" (the battery has to be on)...
[/LIST]


That's all for now; you're invited to contrast your experience with mine, so we can file the necessary bugs to get everything working.  One bug we could use as a basis to file our is [this one]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/364678").


Thanks for your time!  Regards  ;)

---

### Post by leibnitz27 on 2009-08-15
re the 3g modem... (on my TT11WN/B, UK)

Bizarrely, I've had a lot more problems than everyone else here.... (probably cos I'm doing something daft ;) ).... 

However, I've finally noticed that if I use wvdial, and I force it to use ttyHS8, instead of ttyHS2, which is what NetworkManager wants to use, it works!! (woo!)

Anyone know how to override NetworkManager's device decision?  I've been googling for ages.....

Cheers,

Lee.

---

### Post by quini on 2009-08-15
Hi,

No, I have no idea on how to override Network Manager's decision to choose ttyHS2; you're advised to post a new thread for this, as I understand it's not TT (only) related.

By the way, could you tell me if the 3G modem gets recognized when booting without the battery on the laptop, and what version of ubuntu and kernel are you using?  :confused:

TIA  ;)

---

### Post by quini on 2009-08-17
> **quini said:**
> May I use "sudo -s 'echo X > /sys/devices/platform/sony-laptop/wwanpower'" to power the Wwan ON or OFF (where X= 0 or 1)?
**No**.  It accepts echoing 0 or 1 to that pseudo-file, but I've always been able to establish a working connection with my provider, despite wwanpower showed 0 or 1.  This is something that **has to be filed as a bug**

Hi!  **I already filed the bug**; who should subscribe to it?

a) if you have the internal 3G modem, &
b) it gets recognized (you may use it through Network Manager or wvdial), &
c) your battery live is low, 3 to 4 hours

If we can turn it off, the laptop battery should last 5 to 6 hours; now I get about 4 hours.

Bug link: [Cannot turn on/off 3G modem in Vaio TT]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/414833")

Regards  ;)

PD please make me know if your mileage differs from mine!

---

### Post by ilcontegis on 2009-08-17
quini how you get so long life battery?
My tt50b has only 3 hours and 20 min...........Did you buy a bigger battery?

---

### Post by quini on 2009-08-18
Hi!

Let's see how to improve battery life:

**1) is laptop-mode working?**
```
quini@quinitt:~$ cat /etc/default/acpi-support | grep LAPTOP
ENABLE_LAPTOP_MODE=true
quini@quinitt:~$ cat /etc/laptop-mode/laptop-mode.conf | grep ON_BATTERY
ENABLE_LAPTOP_MODE_ON_BATTERY=1
```

**2) is laptop-mode "optimized"?**
      -HD readahead:
```
quini@quinitt:~$ cat /etc/laptop-mode/laptop-mode.conf | grep CONTROL_READAHEAD
CONTROL_READAHEAD=1
```
      -Use of "relatime" option when mounting partitions:
```
quini@quinitt:~$ cat /etc/laptop-mode/laptop-mode.conf | grep RELATIME
USE_RELATIME=1
```
      -Set the HD to spin down when idle (I've set it to 60"):
```
quini@quinitt:~$ cat /etc/laptop-mode/laptop-mode.conf | grep IDLE_TIMEOUT
CONTROL_HD_IDLE_TIMEOUT=1
LM_AC_HD_IDLE_TIMEOUT_SECONDS=7200
LM_BATT_HD_IDLE_TIMEOUT_SECONDS=60
NOLM_HD_IDLE_TIMEOUT_SECONDS=7200
```
      -We'll let laptop-mode control the HD power management; default is 1, but I use to use 128... YMMV:
```
quini@quinitt:~$ cat /etc/laptop-mode/laptop-mode.conf | grep HD_POWERMGMT
CONTROL_HD_POWERMGMT=1
BATT_HD_POWERMGMT=128
LM_AC_HD_POWERMGMT=254
NOLM_AC_HD_POWERMGMT=254
```
      -Let's activate AC97 power savings (sound card):
```
quini@quinitt:~$ cat /etc/laptop-mode/conf.d/ac97-powersave.conf | grep AC97_POWER=
CONTROL_AC97_POWER=1
```
      -Let's stop BT when on battery:
```
quini@quinitt:~$ cat /etc/laptop-mode/conf.d/bluetooth.conf | grep BLUETOOTH
CONTROL_BLUETOOTH=1
BATT_ENABLE_BLUETOOTH=0
AC_ENABLE_BLUETOOTH=1
BLUETOOTH_INTERFACES="hci0"
```
      -We can set the CPU policy here; for instance, we can use "conservative" instead of "ondemand", or limit the maximum CPU speed when on battery setting the "governor" to "powersave":
```
quini@quinitt:~$ cat /etc/laptop-mode/conf.d/cpufreq.conf | grep BATT_CPU
BATT_CPU_MAXFREQ=fastest
BATT_CPU_MINFREQ=slowest
BATT_CPU_GOVERNOR=conservative
...
```
      -Ethernet powersaving options:
```
quini@quinitt:~$ cat /etc/laptop-mode/conf.d/ethernet.conf | grep ETHERNET
CONTROL_ETHERNET=1
BATT_THROTTLE_ETHERNET=1
LM_AC_THROTTLE_ETHERNET=1
NOLM_AC_THROTTLE_ETHERNET=0
ETHERNET_DEVICES="eth0"
```
      -Disable polling of CD drive when on battery:
```
quini@quinitt:~$ cat /etc/laptop-mode/conf.d/hal-polling.conf | grep HAL_POLLING
CONTROL_HAL_POLLING=1
BATT_DISABLE_HAL_POLLING=1
AC_DISABLE_HAL_POLLING=0
HAL_POLLING_DEVICES="/dev/scd?"
```
      -Set the powersaving options of HDA audio codec on:
```
quini@quinitt:~$ cat /etc/laptop-mode/conf.d/intel-hda-powersave.conf | grep HDA_POWER=
CONTROL_INTEL_HDA_POWER=1
```
      -We'll set the Intel Sata power management settings on:
```
quini@quinitt:~$ cat /etc/laptop-mode/conf.d/intel-sata-powermgmt.conf | grep SATA_POWER
CONTROL_INTEL_SATA_POWER=1
```
      -Let's set Linux Scheduler to save power on multi-core processors:
```
quini@quinitt:~$ cat /etc/laptop-mode/conf.d/sched-mc-power-savings.conf | grep MC_POWER_SAVINGS
CONTROL_SCHED_MC_POWER_SAVINGS=1
```
      -We can set the autosuspend feature of USB devices on (it doesn't work fine for me):
```
quini@quinitt:~$ cat /etc/laptop-mode/conf.d/usb-autosuspend.conf | grep USB_AUTOSUSPEND
CONTROL_USB_AUTOSUSPEND=1
```
      -We can stop video output ports:
```
quini@quinitt:~$ cat /etc/laptop-mode/conf.d/video-out.conf | grep VIDEO_OUTPUTS
CONTROL_VIDEO_OUTPUTS=1
BATT_DISABLE_VIDEO_OUTPUTS="TMDS VGA"
LM_AC_DISABLE_VIDEO_OUTPUTS="TMDS VGA"
NOLM_AC_DISABLE_VIDEO_OUTPUTS=""
```
      -Let's enable wifi power management savings, as it drains a lot of power from the battery (note: it doesn't work as of 18/8/09 on the Karmic kernel):
```
quini@quinitt:~$ cat /etc/laptop-mode/conf.d/wireless-iwl-power.conf | grep IWL_POWER
CONTROL_IWL_POWER=1
```


**3) Screen brightness should be set as low as it's still fine to work with**; this can be done through gnome's system -> preferences -> power control, manually, or through laptop-mode.


**4) turn off all devices you're not going to use**: wifi, bluetooth and/or 3G when not used (note that switching 3G off is not working, and there's a [bug filed]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/414833")).



You can control how battery is being drained through the following command:
```
watch -n 2 cat /proc/acpi/battery/BAT0/state
```

Battery info is shown at /proc/acpi/battery/BAT0/info:
```
cat /proc/acpi/battery/BAT0/info
```

Also, **remember to reload laptop-mode after making any change to its configuration files**, as otherwise it won't take effect until next boot:
```
sudo /etc/init.d/laptop-mode reload
```


Hope the above helps  ;)

---

### Post by ilcontegis on 2009-08-18
most of this things are already done, but still I can only have 3.2 hours....
at the moment is ok like this, I hope with 9.10 there will be other improvements in this sense.
Thank you very much for you kind help. I will try to add the suggestions you posted and see if I can reach a higher durability.

Thankyou!
:popcorn:

---

### Post by quini on 2009-08-20
Hi!

I've been working on battery for 1h 22' today:

*Laptop set-up*:
[LIST]
[*]The screen has been always on; I've been using the internet about 50', and organizing photos in F-Spot about 30'
[*]I was running Karmic alpha 4, kernel 2.6.30.5 from [kernel-ppa]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.5/")
[*]the screen is using gnome's default settings (about 1/2 power)
[*]wifi was on (with power management on)
[*]bluetooth was off on both the gnome applet and /sys/devices/platform/sony-laptop/bluetoothpower
[*]/sys/devices/platform/sony-laptop/wwanpower was set to 0 (although I know it -still- does nothing)
[*]laptop-mode was on (with the settings shown in my previous post, except for cpu, that was set always to 800mhz)[/LIST]

*Results*:
[LIST]
[*]11:45h, battery 100%
[*]13:07h, 72,2% battery **=> 100% = 4h 55'**
[LIST]
[*]The battery applet says it could last 3h 45', and if we use real life data, it could last about 3h 33', so it's accurate (+/- 6%)
[*]It means the medium battery drain is 12.100mW/h (out of a standard BPS14/B 5.400mAh battery); use 'watch -n 2 cat /proc/acpi/battery/BAT0/state' to watch it.  /proc/acpi/battery/BAT0/info shows 59.500mW as the battery capacity.
[/LIST]
[/LIST]

I don't know why your battery is lasting only 3h 20', but... are you doing something that's using a lot of cpu?  What does 'cat /proc/acpi/battery/BAT0/state' show?

Regards  ;)

Note: I still had this battery life with my -died- Vaio TZ, and it was supposed to last near 6 hours; my TT11LN/B is supposed to last 8h (480')!!  And it's far from that (I've never used windows to compare...)

---

### Post by ilcontegis on 2009-08-20
It gives this.
Even if I'am only surfing the battery will not go over 3h20min.
I will just wait the KK alpha 5 that usually is already stable and I will put that one and see if there will be some improvement.

Thank you

```
teo@teo:/$ cat /proc/acpi/battery/BAT0/state
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            0 mW
remaining capacity:      59500 mWh
present voltage:         12311 mV

```

---

### Post by ilcontegis on 2009-09-09
We have new alsa driver 1.0.21 to download a try from the alsa website. 
I installed them, but still the mic doesn't want to start to work, crap....
Did somebody, maybe more expert than me succeeded?
See ya.

---

### Post by dymaxion on 2009-09-09
[http://bugzilla.kernel.org/show_bug.cgi?id=12816](http://bugzilla.kernel.org/show_bug.cgi?id=12816)

Since upgrading to kernel 2.6.30 on Fedora 11, my laptop brightness has stopped working.  Was perfectly fine on 2.6.29
I think whatever the guys did on this thread might be related?

Have any of you Ubuntu users found the same problem with kernel 2.6.30 ?

gnome-applet-brightness shows permanent [red] disabled icon

---

### Post by ilcontegis on 2009-09-09
> **dymaxion said:**
> [http://bugzilla.kernel.org/show_bug.cgi?id=12816](http://bugzilla.kernel.org/show_bug.cgi?id=12816)

Since upgrading to kernel 2.6.30 on Fedora 11, my laptop brightness has stopped working.  Was perfectly fine on 2.6.29
I think whatever the guys did on this thread might be related?

Have any of you Ubuntu users found the same problem with kernel 2.6.30 ?

gnome-applet-brightness shows permanent [red] disabled icon

I have the 2.6.30 from the official ubuntu kernel page, and everything is working fine....maybe try to put the 2.6.31...it is very strange..

---

### Post by quini on 2009-09-12
> **ilcontegis said:**
> We have new alsa driver 1.0.21 to download a try from the alsa website. 
I installed them, but still the mic doesn't want to start to work, crap....
Did somebody, maybe more expert than me succeeded?
See ya.

I haven't tryed that alsa driver, and with Karmic (alpha 5) the laptop's speakers don't yet become mute when you plug the headphones in, but you can find an option to switch between "Analog output" and "Analog headphones" in the sound properties panel.

Note that I added "model=6stack-dig" in /etc/modprobe.d/alsa-base.conf as shown in your 1st post in this thread.

Regards  ;)

---

### Post by quini on 2009-09-12
> **dymaxion said:**
> [http://bugzilla.kernel.org/show_bug.cgi?id=12816](http://bugzilla.kernel.org/show_bug.cgi?id=12816)

Since upgrading to kernel 2.6.30 on Fedora 11, my laptop brightness has stopped working.  Was perfectly fine on 2.6.29
I think whatever the guys did on this thread might be related?

Have any of you Ubuntu users found the same problem with kernel 2.6.30 ?

gnome-applet-brightness shows permanent [red] disabled icon

Hi!

There seems to be a regression here; I'm using Ubuntu Karmic (now in alpha 5), and kernel 2.6.30.5 from [kernel-ppa]("http://kernel.ubuntu.com/~kernel-ppa/mainline/").  Brightness works fine with this kernel.

But it does not with the following kernels:
-Ubuntu Karmic 2.6.31-5 to 10, based on 2.6.31-rc5 to 2.6.31 final.

I've filed [bug 414810]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/414810") at launchpad.net.

---

### Post by ilcontegis on 2009-09-14
> **quini said:**
> I haven't tryed that alsa driver, and with Karmic (alpha 5) the laptop's speakers don't yet become mute when you plug the headphones in, but you can find an option to switch between "Analog output" and "Analog headphones" in the sound properties panel.

Note that I added "model=6stack-dig" in /etc/modprobe.d/alsa-base.conf as shown in your 1st post in this thread.

Regards  ;)
This problem is solved, the one that is still there is the internel mic problem, is really annoying one.....I'd like to find a solution but unfortunately I cannot solve..

---

### Post by quini on 2009-09-26
Hi,

The **headphones** are **working** fine **out of the box with Karmic** (alpha 6)...  the laptop's speakers become mute automatically now, without need of adding anything to /etc/modprobe.d/alsa-base.conf

Shame the internel mic still doesn't work...

Regards,

---

### Post by Kenai119 on 2009-09-29
First, sorry but my english. I'm spanish and I don't speak it very well. I have a Vaio TT and I did the alsamixer solution to resolve the headphone jack problem. The headphone jack sounds now but...the volume is too low with the Surround level on top. Anybody ocurred this?? What I did it wrong??

---

### Post by ilcontegis on 2009-09-29
> **Kenai119 said:**
> First, sorry but my english. I'm spanish and I don't speak it very well. I have a Vaio TT and I did the alsamixer solution to resolve the headphone jack problem. The headphone jack sounds now but...the volume is too low with the Surround level on top. Anybody ocurred this?? What I did it wrong??

did you put up the PCM ? maybe is too low. Never had this problem.
From the volume tab -- go to preferences and from there you can add other options to the mixer. maybe one of them is too low. try.

Tomorrow will go out the ubuntu 9.10 beta version, if you want you can try with that one. almost everything work out of the box now!
Only the mic still not working.

See ya

---

### Post by quini on 2009-10-02
Hi!

Brightness is now working out of the box in Karmic beta 1.  I've also updated [post #83]("http://ubuntuforums.org/showthread.php?p=7775745#post7775745").

Regards  :popcorn:

---

### Post by ilcontegis on 2009-10-04
> **quini said:**
> Hi!

Brightness is now working out of the box in Karmic beta 1.  I've also updated [post #83]("http://ubuntuforums.org/showthread.php?p=7775745#post7775745").

Regards  :popcorn:

I installed the KK 9.10 beta. fantastic.....only the mic is left!
I updated the first post!

---

### Post by xaviwan on 2009-10-06
Hi,
I've installed ubuntu 9.04 (with compiz fusion) on my new Vaio TT 11m/n and I've problems with the v-synch when I watch a video. Any idea??

Thanks!!

---

### Post by quini on 2009-10-06
Hi!  I don't have any problem watching videos with Karmic beta 1 & compiz enabled.

You're advised to upgrade to karmic, as soon as it becomes stable -about 3 weeks-.

Hope that helps  ;)

---

### Post by xaviwan on 2009-10-06
> **quini said:**
> Hi!  I don't have any problem watching videos with Karmic beta 1 & compiz enabled.

You're advised to upgrade to karmic, as soon as it becomes stable -about 3 weeks-.

Hope that helps  ;)

Thanks! I've upgraded to Karmic beta 1 and now all works great with videos and compiz. Also the eject button at last works fine.

---

### Post by ilcontegis on 2009-10-06
yep, with karmic there is only the internal mic that does not work. 
everything else is perfect!
:popcorn:

---

### Post by ilcontegis on 2009-10-22
hey guys is your 3d card working properly?
I wanted to play to savage 2 but I do not see the 3d models inside the game (i even don't see the menu).
Any suggestions?

---

### Post by quini on 2009-10-23
Hi!

Same behaviour here, no suggestions!

I get the following output when run from a console:

```
quini@quinitt:~/tmp/Savage2$ ./savage2.bin 
warning: The VAD has been replaced by a hack pending a complete rewrite
Mesa 7.6 implementation error: Unsupported opcode 8 (BGNLOOP) in vertex shader
Please report at bugzilla.freedesktop.org
Mesa 7.6 implementation error: Unsupported opcode 11 (BRK) in vertex shader
Please report at bugzilla.freedesktop.org
Mesa 7.6 implementation error: Unsupported opcode 27 (ENDLOOP) in vertex shader
Please report at bugzilla.freedesktop.org
Mesa 7.6 implementation error: Unsupported opcode 8 (BGNLOOP) in vertex shader
Please report at bugzilla.freedesktop.org
Mesa 7.6 implementation error: Unsupported opcode 11 (BRK) in vertex shader
Please report at bugzilla.freedesktop.org
Mesa 7.6 implementation error: Unsupported opcode 27 (ENDLOOP) in vertex shader
Please report at bugzilla.freedesktop.org
Mesa 7.6 implementation error: Unsupported opcode 8 (BGNLOOP) in vertex shader
Please report at bugzilla.freedesktop.org
Mesa 7.6 implementation error: Unsupported opcode 11 (BRK) in vertex shader
Please report at bugzilla.freedesktop.org
Mesa 7.6 implementation error: Unsupported opcode 27 (ENDLOOP) in vertex shader
Please report at bugzilla.freedesktop.org
Mesa 7.6 implementation error: Unsupported opcode 8 (BGNLOOP) in vertex shader
Please report at bugzilla.freedesktop.org
Mesa 7.6 implementation error: Unsupported opcode 11 (BRK) in vertex shader
Please report at bugzilla.freedesktop.org
Mesa 7.6 implementation error: Unsupported opcode 27 (ENDLOOP) in vertex shader
Please report at bugzilla.freedesktop.org
Mesa 7.6 implementation error: Unsupported opcode 8 (BGNLOOP) in vertex shader
Please report at bugzilla.freedesktop.org
Mesa 7.6 implementation error: Unsupported opcode 11 (BRK) in vertex shader
Please report at bugzilla.freedesktop.org
Mesa 7.6 implementation error: Unsupported opcode 27 (ENDLOOP) in vertex shader
Please report at bugzilla.freedesktop.org
```

I haven't found anything in google... have you tryed googling with better luck than me?

---

### Post by ilcontegis on 2009-10-25
[here]("http://forums.savage2.com/showthread.php?t=18339") it seems that is a problem of our crap video card.

they say to try to put away the shader effect...the problem is that I cannot see the menu so I do not know where to click.....

we might have to wait until intel will make a proper linux driver....

---

### Post by ilcontegis on 2009-11-01
my 3d seems not to work properly with any game...are you guys having the same issue?

---

### Post by quini on 2009-11-01
Hi!

I'm running a recently installed Karmic; my experiences with 3D are:

-compiz works fine,
-glxgears shows 2.1XX fps,
-glest game seems to work fine,
-tremulous game seems to work fine,
-warsow game seems to work fine,
-sauerbraten game doesn't work fine for me (the textures are not shown fine, it's not playable).

What games are not working fine for you?  8-?

Also, "it works fine" means it works, but our video card hasn't got a lot of power, you know  ;)

---

### Post by mu22le on 2009-11-01
hi, I am considering buying a TT and I have a question. Does the
synaptic touchpad have multifinger capabilities?
could someone try running
synclient -m500
and touching the pad with 1, 2 or 3 fingers and see if the column f
(number of fingers change)?
Hope you can help me,

Emme

---

### Post by quini on 2009-11-02
Hi!  It seems it hasn't got multifinger capabilities:

```
quini@quinitt:~$ synclient -m500
    time     x    y   z f  w  l r u d m     multi  gl gm gr gdx gdy
   0.000   226  524   0 0  0  0 0 0 0 0  00000000   0  0  0   0   0
   1.501   528  303   0 0  0  0 0 0 0 0  00000000   0  0  0   0   0
   2.001   600  305  67 1  0  0 0 0 0 0  00000000   0  0  0   0   0
   2.501   603  307   0 0  0  0 0 0 0 0  00000000   0  0  0   0   0
   5.002   467  253  65 1  0  0 0 0 0 0  00000000   0  0  0   0   0
   5.503   466  263  61 1  0  0 0 0 0 0  00000000   0  0  0   0   0
   6.003   395  279  70 1  0  0 0 0 0 0  00000000   0  0  0   0   0
   6.503   380  252  61 1  0  0 0 0 0 0  00000000   0  0  0   0   0
   7.003   378  270   0 0  0  0 0 0 0 0  00000000   0  0  0   0   0
   7.503   705  286   0 0  0  0 0 0 0 0  00000000   0  0  0   0   0
   9.004   728  354   0 0  0  0 0 0 0 0  00000000   0  0  0   0   0
   9.504   810  197  64 1  0  0 0 0 0 0  00000000   0  0  0   0   0
  10.004   818  383   0 0  0  0 0 0 0 0  00000000   0  0  0   0   0
  10.504   241  349  61 1  0  0 0 0 0 0  00000000   0  0  0   0   0
  11.005   315  330  40 1  0  0 0 0 0 0  00000000   0  0  0   0   0
  11.505   827  294  95 1  0  0 0 0 0 0  00000000   0  0  0   0   0
  12.005   803  285  78 1  0  0 0 0 0 0  00000000   0  0  0   0   0
  12.505   730  215  64 1  0  0 0 0 0 0  00000000   0  0  0   0   0
  13.005   251  374   0 0  0  0 0 0 0 0  00000000   0  0  0   0   0
  13.506   133  252  79 1  0  0 0 0 0 0  00000000   0  0  0   0   0

```

I was using 1 to 3 fingers simultaneously, so I'm afraid it's not multitouch capable...

---

### Post by ilcontegis on 2009-11-07
> **quini said:**
> Hi!

I'm running a recently installed Karmic; my experiences with 3D are:

-compiz works fine,
-glxgears shows 2.1XX fps,
-glest game seems to work fine,
-tremulous game seems to work fine,
-warsow game seems to work fine,
-sauerbraten game doesn't work fine for me (the textures are not shown fine, it's not playable).

What games are not working fine for you?  8-?

Also, "it works fine" means it works, but our video card hasn't got a lot of power, you know  ;)

compiz is fine for me as well. I tried glest and it works.
What does not work properly is:
astromenace (working with 9.04)
nexuiz
savage 2

---

### Post by quini on 2009-11-08
Hi!

**Nexuiz is almost playable** here  :popcorn:

... but I've had to change some defaults:

[LIST=1]
[*]Video[LIST=1]
[*]Resolution: 1024x768
[*]Color depth: 16
[*]Vertex buffer: Off
[/LIST]
[*]Effects[LIST=1]
[*]Quality preset: Low
[/LIST]
[/LIST]


**Astromenace doesn't work here** either; I've soft linked all 64 bit libraries to /usr/lib/, and it seems to start, but ends with black screen (I've switched to the text console to hard kill it).

And **Savage2 doesn't** seem to be a Ubuntu problem, but an Intel one.  It seems that Intel cards are not supported:
[http://www.savage2.com/en/specs_pop.html]("http://www.savage2.com/en/specs_pop.html")
[http://tiyukquellmalz.org/blogs/blog5.php/2009/02/20/a-practical-report-on-untainted-linux-ga]("http://tiyukquellmalz.org/blogs/blog5.php/2009/02/20/a-practical-report-on-untainted-linux-ga")

---

### Post by ilcontegis on 2009-11-08
> **quini said:**
> Hi!

**Nexuiz is almost playable** here  :popcorn:

... but I've had to change some defaults:

[LIST=1]
[*]Video[LIST=1]
[*]Resolution: 1024x768
[*]Color depth: 16
[*]Vertex buffer: Off
[/LIST]
[*]Effects[LIST=1]
[*]Quality preset: Low
[/LIST]
[/LIST]


**Astromenace doesn't work here** either; I've soft linked all 64 bit libraries to /usr/lib/, and it seems to start, but ends with black screen (I've switched to the text console to hard kill it).

And **Savage2 doesn't** seem to be a Ubuntu problem, but an Intel one.  It seems that Intel cards are not supported:
[http://www.savage2.com/en/specs_pop.html]("http://www.savage2.com/en/specs_pop.html")
[http://tiyukquellmalz.org/blogs/blog5.php/2009/02/20/a-practical-report-on-untainted-linux-ga]("http://tiyukquellmalz.org/blogs/blog5.php/2009/02/20/a-practical-report-on-untainted-linux-ga")

Thanks,
I will try to find a less exigent ftp :)
pity for astromenace....and savage.

---

### Post by ilcontegis on 2009-12-08
Some updates here:

- Installed latest kernel .32. The boot is faster and the intel video card works better
- Istalled from ppa the latest intel video card drivers (from the bleeding edge repo), they works really well! I can play Heroes of Newerth without any problems.
- I compiled by hand the latest alsa drivers .21 all ok, except the integrated mic as usual!

Stay tuned :)

---

### Post by ilcontegis on 2010-01-11
Update:

- I found a nice ppa with latest kernel (from lucid) and good updated intel drivers!
[https://launchpad.net/~guido-iodice/+archive/best-intel]("https://launchpad.net/~guido-iodice/+archive/best-intel")
Use it if you wish!
Each new kernel must be installed manually

- I compiled the new version of alsa .22, but still no changes with the internal mic!

See ya

---

### Post by ilcontegis on 2010-01-21
update

new kernel available from the repo
[https://launchpad.net/~guido-iodice/+archive/best-intel]("https://launchpad.net/~guido-iodice/+archive/best-intel")
2.6.32-11

---

### Post by quini on 2010-01-22
@ilcontegis:  are you using those debs?  If so, I assume they're working fine, aren't they?

Tnx  ;)

---

### Post by ilcontegis on 2010-01-24
> **quini said:**
> @ilcontegis:  are you using those debs?  If so, I assume they're working fine, aren't they?

Tnx  ;)

Yes of course I am using them. I would not write here without testing before.
I have no problems, everything works fine for me.
Just be careful as usual.

---

### Post by ilcontegis on 2010-03-11
update

new kernel available from the repo
[https://launchpad.net/~guido-iodice/+archive/best-intel](https://launchpad.net/~guido-iodice/+archive/best-intel)
2.6.32-16 (taken directly from lucid 10.04)

- boot is faster
- battery keeps longer

---

### Post by ilcontegis on 2010-03-24
I didn't like the choices for the ubuntu 10.4
I didn't like what Mark said
I don't like how ubuntu is becoming
I passed to debian testing
Here some final considerations before leaving the forum for a while:

The Vaio TT works much better with debian:
- boot is faster
- much more updated than ubuntu
- around 80mb of ram less used 
- the video card is finally working perfectly with all games
- the internal mic is still not working

All bests to all people following this post.
Regards.
Teo

---

### Post by leandromartinez98 on 2010-05-09
Hello all,

I've reported a but on the internal microphone problem a while
ago, but there was no progress so far. You can mark yourselves
as been affected by the bug and maybe provide more information:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/454789](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/454789)

---

### Post by ilcontegis on 2010-05-11
Hi Leandro,
I suggest you to buy an external microphone like we all did. The integrated mic wont work. I personally gave up. :(

---

### Post by jav09 on 2010-05-22
I just posted a patch at [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/454789](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/454789) that enables the internal mic (at least in my TT). It's for kernel 2.6.34, but it should be pretty easy to port to other versions.

---

### Post by ilcontegis on 2010-05-25
> **jav09 said:**
> I just posted a patch at [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/454789](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/454789) that enables the internal mic (at least in my TT). It's for kernel 2.6.34, but it should be pretty easy to port to other versions.

Interesting.
This means that with .34 the mic on the vaio tt should start to work? Or anyway we need to patch?
Can you make a small guide how to patch? thanks

---

### Post by jav09 on 2010-05-25
> **ilcontegis said:**
> Interesting.
This means that with .34 the mic on the vaio tt should start to work? Or anyway we need to patch?
Can you make a small guide how to patch? thanks
No, the mic doesn't work in .34, you need to apply the patch I uploaded to Launchpad ( [http://launchpadlibrarian.net/48940908/vaiott.diff](http://launchpadlibrarian.net/48940908/vaiott.diff) ). This is a simple patch to apply to file sound/pci/hda/patch_realtek.c in kernel sources.

I did a quick review of other kernel releases (such as .32) and looks like it could apply also quite cleanly to those, but I haven't tried it.

It doesn't requiere full kernel recompilation. Just the snd-hda... modules should be fine.

---

### Post by ilcontegis on 2010-05-25
Jav09 thanks for your message.
I did see your patch, my problem is that I have no clue how to apply the patch, if you could write down the steps you did it would be greatly appreciated.

Is this the command to apply a patch? i'm not sure....
```

cd /sound/pci/hda/
patch -p1 < vaiott.diff
```

---

### Post by ilcontegis on 2010-10-06
Hey guys,
some news for the mic?
Still not working here......

---

### Post by konoko on 2010-11-15
It is working for me without any problems on Slackware 13.1.  I have kernel 2.6.37-rc1.   I patched the kernel with the above mentioned patch. I did not even try it without patch. Skype and Ekiga are working great.   I put the following in /etc/modprobe.d/alsa.conf. "options snd_hda_intel model=sony-vaio-tt".  

Headphones are also workingt without any problems by using these options and the speakers are off when I plug in headphones.   All other hardware is also working. I will test fingerprint reader and HDMI this week.

---

### Post by ilcontegis on 2010-11-15
> **konoko said:**
> It is working for me without any problems on Slackware 13.1.  I have kernel 2.6.37-rc1.   I patched the kernel with the above mentioned patch. I did not even try it without patch. Skype and Ekiga are working great.   I put the following in /etc/modprobe.d/alsa.conf. "options snd_hda_intel model=sony-vaio-tt".  

Headphones are also workingt without any problems by using these options and the speakers are off when I plug in headphones.   All other hardware is also working. I will test fingerprint reader and HDMI this week.

Could you please write a small guide about how to apply the patch?
Thanks

---

### Post by konoko on 2010-11-16
```
1. cd /usr/src/linux/sound/pci/hda
(go to the folder with the drivers)

2. wget -c http://launchpadlibrarian.net/48940908/vaiott.diff
(download patch from the above mentioned link)

3. patch -p0 --dry-run <vaiott.diff
(test patch with "--dry-run")

4. patch -p0 <vaiott.diff
(apply patch)
```now you have to recompile kernel modules. standard command to run is:
```
cd /usr/src/linux
make modules modules_install
```and reboot your machine.

I do not know whether debian/ubuntu has something special to rebuild kernel modules but I think that this should work anywhere.

You should probably read this Ubuntu howto and google little bit about compiling kernel on Debian/Ubuntu if you have never upgraded kernel manually:
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by konoko on 2010-11-16
I just checked the howto from above ([https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)) and it should contain everything you need to download, patch (instructions in my last post), recompile and install new kernel on Ubuntu.


I saw some people are writing that their battery last max 4-5h. My 14 months (87% of original capacity) old battery lasts on Slackware 13.1 around 6 hours (brightness on 40-50%, surfing over wireless connection with Firefox, programming on the shell...).

3G connection needs a lot of power (there is no some good powersaving mode) but >= 4 hours are still there. 

I will try to undervolt CPU today and test battery again during the next few days.

---

### Post by ilcontegis on 2010-11-17
@konoko

Thank you for your kindness

I actually have a problem to patch as I don't have the "linux" folder but only "linux-headers-2.6.35-23" and "linux-headers-2.6.35-23-generic"

I installed all this as written in the guide
```
sudo apt-get install fakeroot build-essential crash kexec-tools makedumpfile kernel-wedge
sudo apt-get build-dep linux
sudo apt-get install git-core libncurses5 libncurses5-dev libelf-dev asciidoc binutils-dev
```
I get this error
```
teo@teo-vaio:/usr/src/linux-headers-2.6.35-23/sound/pci/hda$ patch -p0 --dry-run <vaiott.diff
patching file patch_realtek.c
Hunk #1 FAILED at 6937.
Hunk #2 FAILED at 8830.
Hunk #3 FAILED at 10141.
3 out of 3 hunks FAILED -- saving rejects to file patch_realtek.c.rej

```

---

### Post by konoko on 2010-11-17
I also forgot to tell you to run all commands with "sudo" like this:
```
sudo patch -p0 --dry-run <vaiott.diff
```/usr/src/linux is just symbolic link to your current kernel source. I do know whether ubuntu needs it but it does not hurt to make it if it is missing:
```
sudo ln -s /usr/src/linux-headers-2.6.35-23 /usr/src/linux
```
I have no idea why do you get patch errors. Maybe Ubuntu has some custom things but I am just guessing. You have kerne 2.6.35.x and you could get official kernel source from kernel.org (2.6.35.8 > [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.35.8.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.35.8.tar.bz2)) and compare patch_realtek.c from there with your existing patch_realtek.c. You will maybe know more after that. Or as a last solution you could just replace your patch_realtek.c with the official one.

---

### Post by ilcontegis on 2010-11-19
The file patch_realtek.c was not present in my pc!
I copied from the kernel source you gave me and I pasted it in the folder /usr/src/linux/sound/pci/hda
I could patch, but after I get an error when I try to recompile, it says I don't have any config files......
It doesn't work, I give up....I just don't get why they don't simply implement this patch in the kernel?

---

### Post by konoko on 2010-11-19
well, you are obviously missing kernel source and the folder kernel-headers is really containing only kernel-headers without full source.  did you do the following from  [https://help.ubuntu.com/community/Kernel/Compile#B%29%20Download%20the%20source%20archive](https://help.ubuntu.com/community/Kernel/Compile#B%29%20Download%20the%20source%20archive) and get the kernel source  ```
sudo apt-get build-dep --no-install-recommends linux-image-$(uname -r) apt-get source linux-image-$(uname -r)
```  > I just don't get why they don't simply implement this patch in the kernel?  because this patch is maybe destroying something else. and probably nobody sent it kernel developers.

---

### Post by ilcontegis on 2010-11-19
Yes I followed that guide and I installed everything, unfortunately it gives this error.

---

### Post by konoko on 2010-11-19
I think you are still missing kernel source or you are looking in a wrong folder.  You should maybe under generel help ([http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)) ask people how to install the kernel source package.  you could also try this to get kernel source: ```
sudo apt-get install linux-source
```

---

### Post by ilcontegis on 2010-11-21
> **konoko said:**
> I think you are still missing kernel source or you are looking in a wrong folder.  You should maybe under generel help ([http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)) ask people how to install the kernel source package.  you could also try this to get kernel source: ```
sudo apt-get install linux-source
```

Now 2 out of 3 give error.....I'll try to post somewhere else to give this problem higher visibility. Thank you
```
teo@teo-vaio:/usr/src/linux/sound/pci/hda$ sudo patch -p0 --dry-run <vaiott.diffpatching file patch_realtek.c
Hunk #1 succeeded at 7087 (offset 150 lines).
Hunk #2 FAILED at 8862.
Hunk #3 FAILED at 10173.
2 out of 3 hunks FAILED -- saving rejects to file patch_realtek.c.rej

```

---

### Post by konoko on 2010-11-22
attach you patch_realtek.c here or paste it on pastebin.com and I will try to addapt the patch for your.

---

### Post by ilcontegis on 2010-11-22
> **konoko said:**
> attach you patch_realtek.c here or paste it on pastebin.com and I will try to addapt the patch for your.

[http://pastebin.com/kRqwS848]("http://pastebin.com/kRqwS848")

thank you

---

### Post by konoko on 2010-11-22
your patch_realtek.c is already patched. open the vaiott.diff and you patch_realtek.c in gedit and try to find some parts of patch in patch_realtek.c and you will see that this file is patched.

fyi if you want to check that file is already patched:
in line 7058 in patch_realtek.c begins this first part,
in line 8969 beginn 2nd part,
in line 10287 begins 3rd part of this patch.


your mic should be working if you are running on that kernel and you probably did not activate it.

do you have ```
options snd_hda_intel model=sony-vaio-tt
``` in any file in /etc/modprobe.d/??

if not you should make a new file with above line, save it as whatever you want (i.e. alsa.conf) and reboot.



when you run "alsamixer" on the command line you should see 6 different "settings": Master, Headphone, Front, Mic, Mic Boost and S/PDIF.

unmute "Mic" with key "m", make it louder, make Master and Front loud and test it with "gnome-sound-recorder".

---

### Post by ilcontegis on 2010-11-22
> **konoko said:**
> your patch_realtek.c is already patched. open the vaiott.diff and you patch_realtek.c in gedit and try to find some parts of patch in patch_realtek.c and you will see that this file is patched.

fyi if you want to check that file is already patched:
in line 7058 in patch_realtek.c begins this first part,
in line 8969 beginn 2nd part,
in line 10287 begins 3rd part of this patch.


your mic should be working if you are running on that kernel and you probably did not activate it.

do you have ```
options snd_hda_intel model=sony-vaio-tt
``` in any file in /etc/modprobe.d/??

if not you should make a new file with above line, save it as whatever you want (i.e. alsa.conf) and reboot.



when you run "alsamixer" on the command line you should see 6 different "settings": Master, Headphone, Front, Mic, Mic Boost and S/PDIF.

unmute "Mic" with key "m", make it louder, make Master and Front loud and test it with "gnome-sound-recorder".

Doesn't work unfortunately.
I added the line in alsa-base.conf 
No sign of life in the mic :(

---

### Post by konoko on 2010-11-23
I don't have any more ideas. Sorry mate.

---

### Post by ilcontegis on 2010-11-23
> **konoko said:**
> I don't have any more ideas. Sorry mate.

No prob, thank you anyway :)

---

### Post by Mausoleum on 2010-12-26
Has the patch been submitted to kernel upstream?  It would be nice if this started working out of the box in the future...

---

### Post by ilcontegis on 2010-12-27
> **Mausoleum said:**
> Has the patch been submitted to kernel upstream?  It would be nice if this started working out of the box in the future...
No idea, how do you do that?

---

### Post by konoko on 2011-01-17
Does your wireless adapter work with "N" wireless standard?  I am not able to connect to my N router. B/G is working.

---

### Post by ilcontegis on 2011-02-20
> **konoko said:**
> Does your wireless adapter work with "N" wireless standard?  I am not able to connect to my N router. B/G is working.

How can I check that? :)

---

