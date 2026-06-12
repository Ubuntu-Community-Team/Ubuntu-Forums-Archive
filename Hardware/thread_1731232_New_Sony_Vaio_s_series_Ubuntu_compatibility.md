---
title: "New Sony Vaio s series Ubuntu compatibility"
date: 2011-04-16
forum: Hardware
---

### Post by drum19258 on 2011-04-16
I am currently in the market for a new laptop and I would like to continue to dual boot Windows and Ubuntu. The new Sony Vaio s series is what I plan to get ([http://www.sonystyle.com/webapp/wcs/stores/servlet/CategoryDisplay?catalogId=10551&storeId=10151&langId=-1&categoryId=8198552921644768015]("http://www.sonystyle.com/webapp/wcs/stores/servlet/CategoryDisplay?catalogId=10551&storeId=10151&langId=-1&categoryId=8198552921644768015")). I've been reading that people have had problems with Ubuntu on Vaio machines, thoughts?

---

### Post by Paddy Landau on 2011-04-17
It's hard to know whether to get a machine when it's not Ubuntu-certified.

Here is what I suggest.

[LIST=1]
[*]Make a Live CD on a USB stick. Use System > Administration > Startup Disk Creator. Use a USB stick with at least 2Gb, preferably more, and reserve 1Gb or more "Stored in reserved extra space". By the way, I'd suggest you use the 64-bit version, but that is your choice.
[*]Boot from the Live CD, and install any programs you need in order to check the machine, for example Cheese (to test the webcam), Skype, and whatever. You might want to include non-free-extras.
[*]Now go to the shop and take your USB with you. Ask the salesperson permission to boot the machine with your USB (let him know that you will not change anything on the hard drive) so that you can check whether it's Ubuntu-compatible. Play around and check that Ubuntu recognises the wireless, can use the screen at full resolution, etc.
[/LIST]

I've done just that when helping someone look for an Ubuntu-compatible computer. The salesperson was like, "Wow, Linux looks really nice!"

---

### Post by drum19258 on 2011-04-17
That's a really good idea, but the stores near me do not carry this computer (you have to order it and pick it up).

---

### Post by wep940 on 2011-04-17
I would get detailed specs - cpu, their motherboard type, video processor, wireless adapter, audio processor, etc., then do a net search on the model and the specific piece of hardware - as an example  ubuntu 10.10 vaio (your model here) video.  You can also replace ubuntu in the search string with the word linux and see the problems from others in other versions of linux.  Do similar searches on this forum.  If you find reference to a problem, post back here and we can see if there is a work around.  The whole idea is to identify what might be problem areas and their solutions prior to installing ubuntu so that you don't run into problems you are not prepared for.  I'm no expert, but there are plenty of people here to help you!

---

### Post by drum19258 on 2011-04-17
> **wep940 said:**
> I would get detailed specs - cpu, their motherboard type, video processor, wireless adapter, audio processor, etc., then do a net search on the model and the specific piece of hardware - as an example  ubuntu 10.10 vaio (your model here) video.  You can also replace ubuntu in the search string with the word linux and see the problems from others in other versions of linux.
I tried searching for the model but I didn't find anything useful as far as I can see (the computer came out last month, maybe that's why). 

One potential problem I did see was the video. The computer has a switch that toggles the graphics between speed and stamina, with the stamina being integrated graphics (Intel® HM65 Express Chipset) and the speed being the AMD Radeon™ HD 6630M GPU (512MB VRAM) with Intel® Graphics Media Accelerator HD. Is this technology supported in any way by Ubuntu?

---

### Post by wep940 on 2011-04-17
I wish I could tell you an answer, but I don't know anything about that kind of video switching.  I also don't know if those adapters are supported well in ubuntu or not.  I'm hoping someone with more knowledge than me (that's not hard!) will be able to help you further.
 
Good luck!!

---

### Post by binoy4linux on 2011-04-17
I don't know if this helps any, I'm reading this while at work but, I have 2 Sony Vaio's and Ubuntu works well on them both with version 10.10.  Both dual boot with Win7 Home Premium.  I put Ubuntu 10.10 on a USB Stick first and ran from the stick before trying complete install.  My Vaio's are 1 and 2 years old and not the "S" Series, I guess, since the "S" Series is new.  I don't see where you can go wrong if you do the USB Stick first to see if all will work.

---

### Post by K_45 on 2011-04-17
Don't buy anything with switchable graphics. I have a Z series and it doesn't work. Only the Nvidia chip works and if I changed to Intel X would have a heart attack. I'd get a basic laptop built to order or choose one with an older AMD CPU and GPU (before Fusion).

---

### Post by drum19258 on 2011-04-18
> **K_45 said:**
> Don't buy anything with switchable graphics. I have a Z series and it doesn't work. Only the Nvidia chip works and if I changed to Intel X would have a heart attack. I'd get a basic laptop built to order or choose one with an older AMD CPU and GPU (before Fusion).

What if I just leave it in stamina mode (integrated Intel graphics) and don't switch it to the AMD Radeon? I don't really play games so I wouldn't need it anyway. Also, maybe there's better support for these Intel chips in Ubuntu 11.04? Just a thought.

---

### Post by K_45 on 2011-04-18
> **drum19258 said:**
> What if I just leave it in stamina mode (integrated Intel graphics) and don't switch it to the AMD Radeon? I don't really play games so I wouldn't need it anyway. Also, maybe there's better support for these Intel chips in Ubuntu 11.04? Just a thought.

 That should work. Just don't flip the switch by accident.

---

### Post by koenigjm on 2011-04-21
I just got my new S series yesterday and below are some initial hurdles using 11.04 Beta 2:

Graphics:  The radeon driver present in the 2.6.38-8 did not work with the Radeon HD 6470M. Initially installing the X driver via Restricted Drivers resulted in Unity not working, however, after removing the X driver, and a few reboots, I was met with a black screen post-grub (backlight turned off).  

A kernel dump ending in RIP: evergreen_cp_start radeon led me to blacklisting the radeon kernel module.  I then switched into "stamina mode" and am confined to using the intel adapter for now.  11.04 is much quicker without the broken module, and the black screen issue has yet to return. 

Touchpad: Works, however edge scrolling nor two-finger scrolling are working. X11 sees it as an AlpsPS/2 mouse in /var/log/Xorg.0.log.  No work around yet, but I suspect it is treating the touchpad as a generic two button mouse.  

Touchpad issues seem related to the following bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565543](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565543)


Sound:  Playback is working through the built-in speakers, but the internal microphone does not.

Sleep/Hibernate:  Works after blacklisting radeon kernel driver.

More to come as I continue to experiment....

---

### Post by drum19258 on 2011-04-21
Thanks for the insight koenigjm.

With the Intel graphics is the resolution at least decent? The results you got worry me about this laptop...

---

### Post by K_45 on 2011-04-21
If you want a laptop for Linux buy a basic single GPU model that is nothing fancy, otherwise you are paying for features that you will never use.

---

### Post by Paulster on 2011-04-21
I don't know about compatibility on VAIO's, but I recently ordered a VAIO F. When it arrived I was disappointed in a few things. When I sent it back they required me to talk to tech support and verify my problem with the machine before they OK'ed the RMA (Return Merchandise Authorization). They did take it back and even e-mailed me a prepaid shipping label for FedEx. Try, try, try to find someone with an S who will let you Live Boot (as suggested above) before you order, though.  I think I have seen VAIO S for sale at Office Max.  Don't know if you have those where you are.

I wanted a dual booter, as well. So I made a System Image disc-set on DVD's to save Win7 Pro. Then I pulled out the 320GB, 5400rpm drive and popped in my own 750GB, 7200rpm drive ($109 on Amazon.com, thank you! $200 on SonyStyle.com). Installed Karmic Koala ubuntu 9.10 first, leaving a little more than 320GB for Win7.  I read that a System Image backup has to go back onto a hard-drive at least as big as it came from.  I was concerned that Win7 was going to be a master-boot hog and take over what versions of Windows it would allow me to boot! I did find, however, that Win7 was gracious enough to let me boot whatever I wished and I could reboot freely between Win7 and Ubuntu.  YAY!!!  

Something just wasn't right about the video.  I didn't troubleshoot for long, because my main problem was the exterior of the machine.  SonyStyle.com's sales-chat agents all told me the exterior was a durable magnesium alloy finish.  But when I got it, The VAIO F exterior was PLASTIC! After playing with it a little, I called back and got the ball rolling to return it.  I wish I had played with it more, but I wanted my money back as soon as possible so I can order a real metal notebook, Dell XPS 15.  The VAIO looked very cool, though!  Maybe that was magnesium-alloy-colored-paint on plastic. ;)

One other thing:  The electronic invoice for the VAIO said the 4GB of memory was 1333MHz.  But the memory that came with this VAIO F had a sticker on it which ended in "1060 00". The sticker on the two memory modules of the 8GB Corsair kit I ordered to replace that 4GB ended in "1333 C9" ($89 on Amazon.com . $200 on SonyStyle.com . Have I established a pattern here? )  I can't help but wonder if this Sony actually came to me with 1060MHz memory installed instead of the 1333MHz listed on the invoice. Hmm.... I don't know!

Bottom line:  You may have to order an S to find out if it will run Ubuntu.  Regardless of what computer you get, verify that you got the processor and memory you actually ordered and set it up for dual booting before the return period is up (14 or 30 days, I think).

( Attached:  The memory modules which came with the VAIO F )

---

### Post by K_45 on 2011-04-22
^^^  PC3-10600 is equal to 1333MHz . . .

---

### Post by koenigjm on 2011-04-22
> **drum19258 said:**
> Thanks for the insight koenigjm.

With the Intel graphics is the resolution at least decent? The results you got worry me about this laptop...

Resolution is max for the model I have 1366 x 768.  I haven't noticed any graphics issues with the intel adapter whatsoever.  Also, after blacklisting radeon kernel driver standby is working!

I agree that buying hybrid graphics cards is currently an issue for linux users, however, I didn't buy the new S series for graphics performance.  Sandy bridge i7 and battery life were the selling points for me.  So far I am happy with my purchase, despite a few pending hardware issues (trackpad and radeon).

---

### Post by drum19258 on 2011-04-22
> **koenigjm said:**
> Resolution is max for the model I have 1366 x 768.  I haven't noticed any graphics issues with the intel adapter whatsoever.  Also, after blacklisting radeon kernel driver standby is working!

I agree that buying hybrid graphics cards is currently an issue for linux users, however, I didn't buy the new S series for graphics performance.  Sandy bridge i7 and battery life were the selling points for me.  So far I am happy with my purchase, despite a few pending hardware issues (trackpad and radeon).

That sounds great. I'll take your word on the graphics, they were my biggest concern. Could you let me know if anything notable happens? I'm looking to buy soon. Thanks.

---

### Post by beew on 2011-04-22
> **drum19258 said:**
> What if I just leave it in stamina mode (integrated Intel graphics) and don't switch it to the AMD Radeon? I don't really play games so I wouldn't need it anyway. Also, maybe there's better support for these Intel chips in Ubuntu 11.04? Just a thought.

Then why not just buy a laptop with an intel card? It would be cheaper.

---

### Post by drum19258 on 2011-04-22
> **beew said:**
> Then why not just buy a laptop with an intel card? It would be cheaper.

I need the graphics for a few Windows applications, even though I primarily use linux.

---

### Post by koenigjm on 2011-04-23
> **drum19258 said:**
> That sounds great. I'll take your word on the graphics, they were my biggest concern. Could you let me know if anything notable happens? I'm looking to buy soon. Thanks.

I will be sure to post here if anything new arises.

---

### Post by amaj1407 on 2011-04-26
hey koenigjm, I am looking for a new laptop and this laptop catch my eyes and from your posts in this topic it seems the problem are :
1- ATI card does not work
2- TouchPad has some issues and I don't care about that because I use an external mouse. So, not an issue for me.

What about headphone jack does the sound work via it, and is there a mic jack or just a combined one.

Also what about HD and FHD video playback, and does the HDMI port work with intel card?

How many hours this laptop can last?

Final question: Can you enable intel virtualization extensions from bios or not?

Is there any issues you noticed later, other than what you already mentioned?

I know I asked too much questions but I have been searching for a laptop for 2 weeks and I could not find some thing that suits me the most with less linux issues.My choice was the Macbook Pro but I like this more since it's lighter.

For the ATI problem, this link [http://www.phoronix.com/scan.php?page=news_item&px=OTI3MQ](http://www.phoronix.com/scan.php?page=news_item&px=OTI3MQ), has a great news witch states hybrid graphics with ati cards will be supported with catalyst 11.4 but do you think it will work with this laptop.

Thank you.

---

### Post by koenigjm on 2011-04-26
> hey koenigjm, I am looking for a new laptop and this laptop catch my eyes and from your posts in this topic it seems the problem are :
1- ATI card does not work
2- TouchPad has some issues and I don't care about that because I use an external mouse. So, not an issue for me.

You got it.  The important thing to remember is the blacklist the radeon kernel module immediately after install.  Add "blacklist radeon" (without quotes) to the end of /etc/modprobe.d/blacklist.conf.

I used recovery mode from the grub menu to do this. 

> What about headphone jack does the sound work via it, and is there a mic jack or just a combined one.

Yes, sound does work from the headphone jack.  In fact I am using it right now.   When the headphones are present the internal speakers turn off as expected.

There is no separate microphone jack unfortunately.  It worked out alright for me as I use one of those portable headphones from logitech that include a USB connector.  I use that for skype currently.  

As a side note the built-in webcam works well out of the box. 

> Also what about HD and FHD video playback, and does the HDMI port work with intel card? 

I haven't tried the HDMI yet, I can confirm that the VGA cable works however.  I will try the HDMI port tonight and get back to you.  

> How many hours this laptop can last?

I purchased the optional slate battery for the model.  In the battery indicator it shows both batteries, and I am currently seeing around 6 hours steady work with both fully charged. 

Both batteries seem to have similar capacities according to linux, so I am guessing without a slate you would see around 3 hours of life under an average load.  

> Final question: Can you enable intel virtualization extensions from bios or not?

Yes.  

> Is there any issues you noticed later, other than what you already mentioned?

There are a few minor knits: 

1) Unity (do we call it gnome these days?) will restart.  This is very infrequent and I have only noticed it twice today after updating to the latest packages.  I haven't seen anything in the logs that make me suspect a hardware issue, so I have chalked this up to running beta 11.04 for now.  Something I will be keeping an eye on. 

2) The fans run at low speed when the machine is cool and idle.  This isn't such a bad thing as they aren't the loudest fans I have experienced, but something that may bother some.  Also, in typical Vaio fashion, these fans can get very loud under heavy load.  

3) Occasionally the battery indicator will vanish (usually when switching from battery to wall or visa versa).

---

### Post by amaj1407 on 2011-04-27
Thank you for getting back with the answers and I am sorry if I am being heavy on you but an important question I forgot to ask, does hibernate and specially sleep work will and does closing the lid sleep the macnhine?

Again thank you and execuse my asking.

---

### Post by koenigjm on 2011-04-27
> Also what about HD and FHD video playback, and does the HDMI port work with intel card? 

The HDMI port does in fact work.  I verified this last night by using my television as an extra monitor.  There were some artifacts on the laptop screen immediately after the external was enabled, but as soon as the screen refreshed everything was as expected.  

> Thank you for getting back with the answers and I am sorry if I am being heavy on you but an important question I forgot to ask, does hibernate and specially sleep work will and does closing the lid sleep the macnhine?

Not a problem, glad to help others make informed decisions.  

Sleep and hibernate do work, but only after blacklisting the radeon kernel module. I do not use hibernate regularly, but I frequently put the machine to sleep by closing the lid.   So far wakeup has been very consistent, with only a few instances where the OS totally froze shortly after wakeup.

---

### Post by koenigjm on 2011-04-27
Sure, install Ubuntu into a virtual machine within Windows:

> [http://www.virtualbox.org/](http://www.virtualbox.org/)

Or, your other option is to install 11.04 using Wubi.  I have heard rumors that Wubi has some issues in the alpha version of 11.04..so do some research before trying this option.

---

### Post by Frogs Hair on 2011-04-27
I have noticed some users have problems with the Sony Vaio not only on this forum but  on Windows forums as well.
 
Just be sure to that you are satisfied with customer support for this computer . I read that it is only 6 months While some other brands offer a year.

---

### Post by lemuelinchrist on 2011-04-27
i just got touchpad verticall scrolling to work on my Vaio S series.

I followed the instructions here:
[http://ubuntuforums.org/showthread.php?t=1472195]("http://ubuntuforums.org/showthread.php?t=1472195")

it's basically just running these two lines in terminal:

```
sudo rmmod psmouse
sudo modprobe psmouse proto=imps
```

"if proto=imps doesnt work, try proto=exps

try the touchpad again for scrolling..

if it works, u need to make it permanent."

```

sudo nano /etc/modprobe.d/options
```
enter these lines in the nano editor
```
options psmouse proto=imps
```

---

### Post by koenigjm on 2011-04-27
Well look at that.  proto=exps did the trick for me.

This is a nice workaround until the actual trackpad can be supported. I would rather have edge scrolling than no scrolling. :)

---

### Post by flyver on 2011-04-27
I have [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/702344") problem with my Vaio computer. But mine is 3 years old though.

---

### Post by dash10 on 2011-04-28
I have a VAIO VPCEA and it works perfectly, all hardware was good to go right after install.

I should add I bought it recently, in January of this year.

---

### Post by lemuelinchrist on 2011-05-01
I bring another good news to my Ubuntu Vaio S series friends.

I finally found a solution on GETTING THE INTERNAL MIC TO WORK in Ubuntu 11.04, after hours of rummaging through the internet

It turned out that our problem was due to an ALSA bug. It's now patched up and the fix has already been committed upstream, but you'll have to wait for the update to come if you want the bug to be fixed.

If you cant wait anymore, here are the steps to do it:

oh... and please do this at your own risk. your system might break so dont blame me if it does.

Lastly, I'm writing down the steps that worked for me on my notebook. I'm pretty sure there's an easier way to do this (one that doesn't need patching) that I don't know yet. So if you do know, please share it with us.

1. download the patch here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/752792/+attachment/1992949/+files/0001-ALSA-HDA-Fix-single-internal-mic-on-ALC275-Sony-Vaio.patch]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/752792/+attachment/1992949/+files/0001-ALSA-HDA-Fix-single-internal-mic-on-ALC275-Sony-Vaio.patch")

2. download [AlsaUpgrade-1.0.24-2.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=182961&d=1297117212")
   
3. copy both files to /opt

4. cd /opt
5. sudo tar xzvf AlsaUpgrade-1.0.24-2.tar.gz
6. sudo chmod +x AlsaUpgrade-1.0.24-2.sh
7. sudo ./AlsaUpgrade-1.0.24-2.sh -d
8. sudo patch /opt/Alsa-1.0.24/alsa-driver-1.0.24/sound/pci/hda/patch_realtek.c < 0001-ALSA-HDA-Fix-single-internal-mic-on-ALC275-Sony-Vaio.patch
9. sudo ./AlsaUpgrade-1.0.24-2.sh -c
10. sudo ./AlsaUpgrade-1.0.24-2.sh -i

11. reboot your system and test your mic


EDIT:
Here are the sites I read to come up with this fix:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/752792](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/752792)
[http://ubuntuforums.org/showthread.php?t=1719770&page=2](http://ubuntuforums.org/showthread.php?t=1719770&page=2)
[http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

---

### Post by shenten on 2011-05-08
Hi, it seems you made some progress to make you Vaio S working with ubuntu, maybe you could give me some help on my issue :)
I have the VPCSB.

I've installed ubuntu 11.04 and I can't seem to have my card be detected by the drivers. I tried the proprietary drivers from jockey, and the ones from ATI directly (.run script). Everytime I end up having aticonfig telling me I have unsupported hardware, which is kinda strange.
Keep in mind I have an hybrid graphics setup (dual card setup: ATI and Intel) You can switch between them using a stamina/speed button, I'm on the speed state (which means using the ati card).

```
root@shenten-Vaio:~# sudo aticonfig --initial
aticonfig: No supported adapters detected
root@shenten-Vaio:~# 
```

If I check for the kernel detection although , I get the following:
```
root@shenten-Vaio:~# lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: ATI Technologies Inc NI Whistler [AMD Radeon HD 6600M Series]
```

I checked for the switch:
```
root@shenten-Vaio:~# sudo grep -i switcheroo /boot/config-2.6.*
CONFIG_VGA_SWITCHEROO=y
root@shenten-Vaio:~# 
```

but when I want to see the current state, it doesn't work:
```
root@shenten-Vaio:~# sudo cat /sys/kernel/debug/vgaswitcheroo/switch
cat: /sys/kernel/debug/vgaswitcheroo/switch: No such file or directory
```

I tried loading the module, but no success:
```
root@shenten-Vaio:/sys/kernel/debug# sudo modprobe vgaswitcheroo
FATAL: Module vgaswitcheroo not found.
root@shenten-Vaio:/sys/kernel/debug# sudo modprobe vga_switcheroo
FATAL: Module vga_switcheroo not found.
root@shenten-Vaio:/sys/kernel/debug# 
```

I use x64 version, don't know It changes anything

Does someone have a clue what I could do next ? :) If I can't make it work with the ATI, how can I use the intel card ? simply black listing the radeon module will work ? how about the x server then ? 

Thanks for any help :)

---

### Post by koenigjm on 2011-05-08
I do not know much about vgaswitcheroo, so I cannot speak to its functionality. I have heard that support of hybrid AMD cards was promised in AMD's software stack as of 11.3.   
 
Having the same model Vaio as you, I did try to install the latest 11.4 ATI driver. It seemed to work for me (I had the .run generate natty deb packages), however the performance in Unity was pretty rough around the edges (read: choppy).  Installing the restricted driver from the standard repos has yet to work.   

For now, I have simply blacklisted the radeon module and left the switch in Stamina mode. I didn't have to do anything beyond what I just mentioned, simply restart the machine and Unity should come up all ready to go.  In a few months I may check back on the state of AMD driver and try again.

---

### Post by thelibran on 2011-05-08
I got an SB and changed my hdd to 120gb intel 510 ssd. I dont feel like installing ubuntu on to it eating up memory and was wondering if i can install and run it from a memory stick since i wont be using that memory stick slot. Any idea if SB can boot into ubuntu from the memory stick?? I got 11.04 on a live usb and it boots in but i hate the unity feel. so gonna fall back to 10.04 like i had before on my ASUS ROG. 

my major worry is not to have my MBR affected by grub. can i keep grub on my memory stick? I am worried of installing it out and see if it works coz of the pain of reinstalling windows if something goes wrong. i dont hv a second windows or linux machine arnd and everything i got arnd me is a mac. can anyone cared to do such an experiment?

curious to know.


thanks

---

### Post by shenten on 2011-05-08
> **koenigjm said:**
> I do not know much about vgaswitcheroo, so I cannot speak to its functionality. I have heard that support of hybrid AMD cards was promised in AMD's software stack as of 11.3.   
 
Having the same model Vaio as you, I did try to install the latest 11.4 ATI driver. It seemed to work for me (I had the .run generate natty deb packages), however the performance in Unity was pretty rough around the edges (read: choppy).  Installing the restricted driver from the standard repos has yet to work.   

For now, I have simply blacklisted the radeon module and left the switch in Stamina mode. I didn't have to do anything beyond what I just mentioned, simply restart the machine and Unity should come up all ready to go.  In a few months I may check back on the state of AMD driver and try again.

I tried installing by generating the package but I had a crash of the installer. Strange. I'll try to black list the radeon for now and see later. Thanks for the input.

---

### Post by olsman037 on 2011-05-09
Yes you can boot on the usb stick... You can use a persistent mode and remove the ubiquity software from the key in order to boot faster.

---

### Post by garbelini on 2011-05-18
@koenigjm Thanks for all the input.

How does your xorg.conf look? Mine has a record number of devices and monitors for some reason.

External monitor works very poorly and Unity doesn't load since no 3D is available. Also the Stamina/Speed switch doesn't seem to have any effect. I blacklisted the radeon driver like you mentioned.

Here is my crazy xorg.conf after running:

```
Xorg -configure
```

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	Screen      2  "Screen2" RightOf "Screen1"
	Screen      3  "Screen3" RightOf "Screen2"
	Screen      4  "Screen4" RightOf "Screen3"
	Screen      5  "Screen5" RightOf "Screen4"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dri2"
	Load  "FGL.renamed.libglx"
	Load  "extmod"
	Load  "dri"
	Load  "glx"
	Load  "record"
	Load  "dbe"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor2"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor3"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor4"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor5"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "DefaultRefresh"     	# [<bool>]
        #Option     "ModeSetClearScreen" 	# [<bool>]
	Identifier  "Card0"
	Driver      "vesa"
	BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "DefaultRefresh"     	# [<bool>]
        #Option     "ModeSetClearScreen" 	# [<bool>]
	Identifier  "Card1"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "AccelMethod"        	# [<str>]
        #Option     "DRI"                	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "VideoKey"           	# <i>
        #Option     "FallbackDebug"      	# [<bool>]
        #Option     "Tiling"             	# [<bool>]
        #Option     "Shadow"             	# [<bool>]
        #Option     "SwapbuffersWait"    	# [<bool>]
        #Option     "XvMC"               	# [<bool>]
        #Option     "XvPreferOverlay"    	# [<bool>]
        #Option     "DebugFlushBatches"  	# [<bool>]
        #Option     "DebugFlushCaches"   	# [<bool>]
        #Option     "DebugWait"          	# [<bool>]
        #Option     "HotPlug"            	# [<bool>]
        #Option     "RelaxedFencing"     	# [<bool>]
	Identifier  "Card2"
	Driver      "intel"
	BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "Dac8Bit"            	# [<bool>]
        #Option     "BusType"            	# [<str>]
        #Option     "CPPIOMode"          	# [<bool>]
        #Option     "CPusecTimeout"      	# <i>
        #Option     "AGPMode"            	# <i>
        #Option     "AGPFastWrite"       	# [<bool>]
        #Option     "AGPSize"            	# <i>
        #Option     "GARTSize"           	# <i>
        #Option     "RingSize"           	# <i>
        #Option     "BufferSize"         	# <i>
        #Option     "EnableDepthMoves"   	# [<bool>]
        #Option     "EnablePageFlip"     	# [<bool>]
        #Option     "NoBackBuffer"       	# [<bool>]
        #Option     "DMAForXv"           	# [<bool>]
        #Option     "FBTexPercent"       	# <i>
        #Option     "DepthBits"          	# <i>
        #Option     "PCIAPERSize"        	# <i>
        #Option     "AccelDFS"           	# [<bool>]
        #Option     "IgnoreEDID"         	# [<bool>]
        #Option     "CustomEDID"         	# [<str>]
        #Option     "DisplayPriority"    	# [<str>]
        #Option     "PanelSize"          	# [<str>]
        #Option     "ForceMinDotClock"   	# <freq>
        #Option     "ColorTiling"        	# [<bool>]
        #Option     "VideoKey"           	# <i>
        #Option     "RageTheatreCrystal" 	# <i>
        #Option     "RageTheatreTunerPort" 	# <i>
        #Option     "RageTheatreCompositePort" 	# <i>
        #Option     "RageTheatreSVideoPort" 	# <i>
        #Option     "TunerType"          	# <i>
        #Option     "RageTheatreMicrocPath" 	# <str>
        #Option     "RageTheatreMicrocType" 	# <str>
        #Option     "ScalerWidth"        	# <i>
        #Option     "RenderAccel"        	# [<bool>]
        #Option     "SubPixelOrder"      	# [<str>]
        #Option     "ClockGating"        	# [<bool>]
        #Option     "VGAAccess"          	# [<bool>]
        #Option     "ReverseDDC"         	# [<bool>]
        #Option     "LVDSProbePLL"       	# [<bool>]
        #Option     "AccelMethod"        	# <str>
        #Option     "DRI"                	# [<bool>]
        #Option     "ConnectorTable"     	# <str>
        #Option     "DefaultConnectorTable" 	# [<bool>]
        #Option     "DefaultTMDSPLL"     	# [<bool>]
        #Option     "TVDACLoadDetect"    	# [<bool>]
        #Option     "ForceTVOut"         	# [<bool>]
        #Option     "TVStandard"         	# <str>
        #Option     "IgnoreLidStatus"    	# [<bool>]
        #Option     "DefaultTVDACAdj"    	# [<bool>]
        #Option     "Int10"              	# [<bool>]
        #Option     "EXAVSync"           	# [<bool>]
        #Option     "ATOMTVOut"          	# [<bool>]
        #Option     "R4xxATOM"           	# [<bool>]
        #Option     "ForceLowPowerMode"  	# [<bool>]
        #Option     "DynamicPM"          	# [<bool>]
        #Option     "NewPLL"             	# [<bool>]
        #Option     "ZaphodHeads"        	# <str>
	Identifier  "Card3"
	Driver      "radeon"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "Rotate"             	# <str>
        #Option     "fbdev"              	# <str>
        #Option     "debug"              	# [<bool>]
	Identifier  "Card4"
	Driver      "fbdev"
	BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "Rotate"             	# <str>
        #Option     "fbdev"              	# <str>
        #Option     "debug"              	# [<bool>]
	Identifier  "Card5"
	Driver      "fbdev"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen2"
	Device     "Card2"
	Monitor    "Monitor2"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen3"
	Device     "Card3"
	Monitor    "Monitor3"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen4"
	Device     "Card4"
	Monitor    "Monitor4"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen5"
	Device     "Card5"
	Monitor    "Monitor5"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

### Post by ikkari on 2011-05-22
I just got VAIO VPCSB11FX and installed Ubuntu 11.04 and I believe  have  severe issues regarding processor temperature and power consumption the  fan is spinning all the time and heat coming from the heat sink is  immense when running almost nothing (even killed gdm), the battery dies  in just 2h. I didn't have these issues on windows the processor is much cooler and battery last 6h+. I was just  wondering if anybody have observed similar behavior and if there is some  solution to that.

---

### Post by garbelini on 2011-05-22
Got a VPCSB1V9E/B running Natty.

The new 2.6.39 kernel makes things better for me.

Things that work now that didn't work with the 2.6.38 kernel.

- Unity Dash typing was veeery slow and now it works like expected
- Suspend is working out of the box
- No more black screen failed boots (this was intermittent)
- Not completely sure but I think the heating/fan issue is better as well

Video card support still sucks though. No ATI at all not even with the latest driver downloaded from ATI ([http://goo.gl/jvWs4](http://goo.gl/jvWs4))

With the Intel video the story is the same. Works ok on the default screen but no luck with external monitors.

```
sudo add-apt-repository ppa:kernel-ppa/ppa 
sudo apt-get update
sudo apt-get install linux-headers-2.6.39-0 linux-headers-2.6.39-0-generic linux-image-2.6.39-0-generic --fix-missing 
```

---

### Post by Romanovzky on 2011-05-24
So... we will have to keep up with stamina boot with radeon module blocked for a while.

I can live with that. Also, I run gnome classic and hence I don't trouble myself with Unity and its lack of finesse or performance.

I hope we get reasonable support and performance for 11.10...

---

### Post by carocco on 2011-05-27
Hi!

In order to improve the battery performance and the Unity dash typing I've experienced this solution:

1) I've blacklisted the radeon module
2) after the log in, I execute the command

```
sudo echo OFF > /sys/debug/kernel/debug/vgaswitcheroo/switch
```

Battery duration: up to 4,5 hours
Unity Dash typing: faster than before.

---

### Post by carocco on 2011-05-28
Ops....

my mistake: the radeon modulee isn't blacklisted!!!

---

### Post by ikkari on 2011-05-28
[carocco]("http://ubuntuforums.org/member.php?u=1293594"), are you using the latest 2.6.39 kernel ?

---

### Post by koenigjm on 2011-05-28
I am currently running the latest 39 kernel from ppa.  I have re-enabled the radeon module and followed carocco's instructions.  I will report back if I notice any difference.

---

### Post by carocco on 2011-05-30
@ikkari No, I'm using the 2.6.38-8.

Someone has configured the third button emulation for the touchpad? Why there isn't by default? It's annoying!!

---

### Post by carocco on 2011-05-31
Good morning!

I've done some experiment in Windows 7 with the graphic cards.
If I disable the Intel one in the Control Panel, after rebooting I get an error about missing Ati driver, even if the driver are installed.

So, I've downloaded the 3DMark Vantage and I ran a benchmark: I get the same results reported on notebookcheck.it with both cards activated.

My opinion is that the ATI card is used only for processing and not for displaying.
I think that the ATI GPU processes data and pass the results to the Intel that provides to display them.

It's my conclusion correct?

---

### Post by unixlike on 2011-06-02
Hi,
I am a new owner of this notebook and I would install ubuntu in my nb.
I read in some forums that the temperature rises so much with ubuntu.
Have you solved this problem? Is this problem also in lts version?

Thanks.

---

### Post by ikkari on 2011-06-03
@unixlike

I haven't found a solution for the heating problem. You can try the  proposed above solutions ans see if it works for you. My guess is that  this is firmware/motherboard related issue because of the custom Sony  hardware. I did make a clean install of Windows 7 and without the  thousand Sony drivers it behaved pretty much the same way it is doing on  Ubuntu(a lot of heat and short battery life). I hope a solution is  found and will keep looking.

---

### Post by nicgom on 2011-06-03
Hi, i got the vaio VPC SB1V9E/B a couple of weeks ago, been trying to install ubuntu on it, now i´m having two problems, tryed first installing 11.04, it more or less worked fine, just the  fan is n all the  time, which is something i don´t like, and also the touchpad doesn´t work, mobile broadband worked fine in lice sesion, i just didn´t install because of the touchpad not working properly, it does recognice movement, but not acuratedly, is as it were wet or my fingers covered with cream, it just doesnt work, i googled a bit and didnt find any solution, so i tried 10.10 and the touchpad works, i installed it, but somehow i cannot connect to my mobile internet, im with vodafone germany, bought the laptop with a 2 year mobile internet offer wich works great with win 7, but i´m used to work with ubuntu and would like to be able to do so with this device, that is why i also need the touchpad working, im always on the move, dont want to have to carry any usb mouse wth it.

so please if anybody nows what i could do, just let me know.
thanks

---

### Post by swish123 on 2011-06-05
Can anyone help me figure out how to blacklist the radeon module?

I opened up terminal and issued "**sudo etc/modprobe.d/blacklist**"

Then I typed "**blacklist radeon**" and saved.

After a restart I still see ATI radeon when I do lspci.

What do I do?

Thanks

---

### Post by carocco on 2011-06-06
> **swish123 said:**
> Can anyone help me figure out how to blacklist the radeon module?

I opened up terminal and issued "**sudo etc/modprobe.d/blacklist**"

Then I typed "**blacklist radeon**" and saved.

After a restart I still see ATI radeon when I do lspci.

What do I do?

Thanks


Hi swish!
Blacklisting modules does not hide/delete the lspci entry for the hardware.
If you blacklist the radeon module, you can check with the command

```
lsmod|grep radeon
```

However, I'm quite sure that the file to edit is **/etc/modprobe.d/blacklist.conf **

---

### Post by Romanovzky on 2011-06-06
Seeing the radeon doesn't mean the module was loaded. What matters is the radeon module not to load. I don't remember the command to see the modules that are running but you can use it to check the module is not running. The lspci command only lists the devices plugged in a pci interface, it is a good sign you still see the radeon it means it didn't disappear :P

---

### Post by oldcity11 on 2011-06-06
Did not read entire thread. Suggestion to do a USB thumb drive to check the machine you intend to buy is correct.
I have an older Vaio that I wanted the driver for the wireless card and Sony support would not provide the driver and advised to the effect they did not support linux on their machines.

---

### Post by koenigjm on 2011-06-13
> Hi, i got the vaio VPC SB1V9E/B a couple of weeks ago, been trying to install ubuntu on it, now i´m having two problems, tryed first installing 11.04, it more or less worked fine, just the fan is n all the time, which is something i don´t like, and also the touchpad doesn´t work, mobile broadband worked fine in lice sesion, i just didn´t install because of the touchpad not working properly, it does recognice movement, but not acuratedly, is as it were wet or my fingers covered with cream, it just doesnt work, i googled a bit and didnt find any solution, so i tried 10.10 and the touchpad works, i installed it, but somehow i cannot connect to my mobile internet, im with vodafone germany, bought the laptop with a 2 year mobile internet offer wich works great with win 7, but i´m used to work with ubuntu and would like to be able to do so with this device, that is why i also need the touchpad working, im always on the move, dont want to have to carry any usb mouse wth it.

so please if anybody nows what i could do, just let me know.
thanks

nicgom, I had the same touchpad issues when I first installed.  Somewhere between software updates the trackpad starts tracking motion as expected.

Keep in mind though it will act like generic two button mouse.  Read this thread for tips on getting the side-scrolling to work.

---

### Post by carocco on 2011-06-16
Good morning!
Has anyone tried the new ATI Catalyst drivers with the 6470M?

---

### Post by CLTPilot on 2011-06-16
It figures they'd come out with a new driver 1 day after I gave up and uninstalled Ubuntu 11.04 due to numerous video issues.  Back to Win7 for now, also very curious how these new drivers do with the VAIO S series running the 6470M.  I could never get the 11.5 driver to install properly, maybe 11.6 works.

Cltpilot

---

### Post by carocco on 2011-06-16
> **CLTPilot said:**
> It figures they'd come out with a new driver 1 day after I gave up and uninstalled Ubuntu 11.04 due to numerous video issues.  Back to Win7 for now, also very curious how these new drivers do with the VAIO S series running the 6470M.  I could never get the 11.5 driver to install properly, maybe 11.6 works.

Cltpilot

Tonight I'll get it a try (I'm in Italy). Then, I'll tell you if it works!

---

### Post by carocco on 2011-06-16
It doesn't work :(

---

### Post by koenigjm on 2011-06-17
A few more tips (which come with some downsides) on decreasing temperature, increasing battery life, and better Unity experience:

1) Follow carocco's post on using vgaswitcheroo (until we get some AMD drivers that work).  Before you are able to "echo OFF" to vgaswitcheroo/swtich the radeon kernel module will have to be enabled.  For ease of use, you can make a bash script which performs this echo for you (as root) at startup.  This will save you from having to do it manually everytime you boot your system.

2) Upgrade to the latest kernel using the kernel ppa ([https://launchpad.net/~kernel-ppa/+archive/ppa](https://launchpad.net/~kernel-ppa/+archive/ppa)).  Plenty of general sandybridge updates happening, and I feel its best to keep up with the latest while this hardware is still receiving a fair amount of developer attention.  

3) Add the xorg-edgers ppa ([http://www.ubuntuupdates.org/ppas/87](http://www.ubuntuupdates.org/ppas/87)).  There have been significant updates for sandybridge graphics recently, ones which probably won't find their way into the mainline repos until 11.10.  I haven't experienced any system instability using this ppa, and overall my Unity experience is very smooth now.

THE DOWNSIDE:  The loading of the radeon kernel module still fails terribly from time to time (same evergreen_start issue).  This results in one in a handful of boots ending at a black screen, with no other recourse but to restart the system.  This issue seems to occur less frequently with the xorg-edgers PPA.  Of course, using PPAs always means one needs to be extra careful with upgrading Ubuntu distros.  

THE UPSIDE: Overall system temperature is down 10 degrees Celsius during normal usage (~43 C down from ~54 C), and battery life has noticeably improved.  I have also experienced less random Unity restarts, over the past week, with these changes in place.

---

### Post by carocco on 2011-06-17
In order to avoid boots ending at a black screen, I use this method:

1) The radeon kernel module is blacklisted in /etc/modprobe.d/blacklist.conf
2) After login, I execute a simple script with only two instrucions
```
#!/bin/bash
modprobe radeon
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

```I've created a launcher on desktop that runs the script with gksu.

In this way, the boot never fails and the ati card can be switched off.

---

### Post by koenigjm on 2011-06-17
That is a clever way to get around the black screen issue..though I am guessing the modprobe radeon still fails periodically on your setup.  :)

---

### Post by carocco on 2011-06-17
so far, it never happened. It seems to work quite well...You have just to wait a few seconds before running the script!

---

### Post by Go7enKs on 2011-06-17
I just got a new Sony Vaio VPCSB and I'm wondering if it'w worth installing Ubuntu. I love Ubuntu and I grew used to have it (been a Ubuntu user for 3+ years) but I'm concerned about two things:
1) Does the battery lose a lot of performace using Ubuntu?
2) Can you get to make the mic work?

Thanks!

---

### Post by koenigjm on 2011-06-18
> **Go7enKs said:**
> I just got a new Sony Vaio VPCSB and I'm wondering if it'w worth installing Ubuntu. I love Ubuntu and I grew used to have it (been a Ubuntu user for 3+ years) but I'm concerned about two things:
1) Does the battery lose a lot of performace using Ubuntu?
2) Can you get to make the  mic work?
Thanks!

Go7enKs, I really cant make a comparison on Windows as I the only thing I did when I got my VAIO was create backup discs then clobber the Windows install.  However, I can say that despite the issues presented in this thread I have had a pretty good overall Ubuntu experience.

Make sure you read through this thread!  I believe there was a fix for the microphone a few pages back and of course tips/fixes on how others have increased battery performance.

---

### Post by Go7enKs on 2011-06-19
> **koenigjm said:**
> Go7enKs, I really cant make a comparison on Windows as I the only thing I did when I got my VAIO was create backup discs then clobber the Windows install.  However, I can say that despite the issues presented in this thread I have had a pretty good overall Ubuntu experience.

Make sure you read through this thread!  I believe there was a fix for the microphone a few pages back and of course tips/fixes on how others have increased battery performance.
So you've had Ubuntu on this laptop for a while...how long does your battery last on average? I'm really undecided on switching because I need a decent battery life (although I also bought the secondary battery to be safe) and I can't afford having Ubuntu if I lose a lot of battery life. I hate Windows though...

---

### Post by koenigjm on 2011-06-20
With vgaswitcheroo fix, latest kernel, and latest drivers, I am seeing around 6 hours under steady usage (coding, compiling, email, IM, etc).  This is with the additional battery.

This is just my gut estimation.  I usually only drain the battery down on days I forget to plugin the laptop at my desk. :)

---

### Post by carocco on 2011-06-20
> **koenigjm said:**
> With vgaswitcheroo fix, latest kernel, and latest drivers, I am seeing around 6 hours under steady usage (coding, compiling, email, IM, etc).  This is with the additional battery.

This is just my gut estimation.  I usually only drain the battery down on days I forget to plugin the laptop at my desk. :)

Have you installed new vga driver? Which videocard have you??

---

### Post by koenigjm on 2011-06-20
Carocco, I am not using the AMD drivers at all, just the latest intel drivers from the xorg edgers ppa.

---

### Post by Go7enKs on 2011-06-20
I've installed it and followed your instructions but when I unplug the charger and check the estimate battery left it just says 2.30 or 2.40 tops (when battery is at 100%). 

Carocco, do you get 4 hours with brightness 100%?

---

### Post by Romanovzky on 2011-06-21
> **koenigjm said:**
> With vgaswitcheroo fix, latest kernel, and latest drivers, I am seeing around 6 hours under steady usage (coding, compiling, email, IM, etc).  This is with the additional battery.

This is just my gut estimation.  I usually only drain the battery down on days I forget to plugin the laptop at my desk. :)

When you say latest kernel do you mean the new 3.x? Do you have a ppa for a newer kernel then the one offered by canonical in the default reps?

---

### Post by Go7enKs on 2011-06-21
> **lemuelinchrist said:**
> I bring another good news to my Ubuntu Vaio S series friends.

I finally found a solution on GETTING THE INTERNAL MIC TO WORK in Ubuntu 11.04, after hours of rummaging through the internet

It turned out that our problem was due to an ALSA bug. It's now patched up and the fix has already been committed upstream, but you'll have to wait for the update to come if you want the bug to be fixed.

If you cant wait anymore, here are the steps to do it:

oh... and please do this at your own risk. your system might break so dont blame me if it does.

Lastly, I'm writing down the steps that worked for me on my notebook. I'm pretty sure there's an easier way to do this (one that doesn't need patching) that I don't know yet. So if you do know, please share it with us.

1. download the patch here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/752792/+attachment/1992949/+files/0001-ALSA-HDA-Fix-single-internal-mic-on-ALC275-Sony-Vaio.patch]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/752792/+attachment/1992949/+files/0001-ALSA-HDA-Fix-single-internal-mic-on-ALC275-Sony-Vaio.patch")

2. download [AlsaUpgrade-1.0.24-2.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=182961&d=1297117212")
   
3. copy both files to /opt

4. cd /opt
5. sudo tar xzvf AlsaUpgrade-1.0.24-2.tar.gz
6. sudo chmod +x AlsaUpgrade-1.0.24-2.sh
7. sudo ./AlsaUpgrade-1.0.24-2.sh -d
8. sudo patch /opt/Alsa-1.0.24/alsa-driver-1.0.24/sound/pci/hda/patch_realtek.c < 0001-ALSA-HDA-Fix-single-internal-mic-on-ALC275-Sony-Vaio.patch
9. sudo ./AlsaUpgrade-1.0.24-2.sh -c
10. sudo ./AlsaUpgrade-1.0.24-2.sh -i

11. reboot your system and test your mic


EDIT:
Here are the sites I read to come up with this fix:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/752792](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/752792)
[http://ubuntuforums.org/showthread.php?t=1719770&page=2](http://ubuntuforums.org/showthread.php?t=1719770&page=2)
[http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)
Is there a simpler way to do that? I got stuck at point 8. I pasted the command you wrote and got this: "bash: 0001-ALSA-HDA-Fix-single-internal-mic-on-ALC275-Sony-Vaio.patch: No such file or directory"

What did I do wrong?

EDIT: I got past point 8. But still got stuck at point 9. " alsa-driver-1.0.24 make failed".

How can I fix it?

---

### Post by carocco on 2011-06-21
Go7enKs,
I've solved the microphone issue with a single line command...but I don't remeber which one because I haven't the nb with me now.

Tonight I can write the solution.

P.S. What's happened with Skype? You're disappeared!

---

### Post by carocco on 2011-06-21
I've found it in my mailbox:

```

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)

```

---

### Post by Go7enKs on 2011-06-21
Thanks, somehow it already works. I should've tested it before posting. Thanks anyway

---

### Post by koenigjm on 2011-06-21
> **Romanovzky said:**
> When you say latest kernel do you mean the new 3.x? Do you have a ppa for a newer kernel then the one offered by canonical in the default reps?

I added the kernel ppa ([https://launchpad.net/~kernel-ppa/+archive/ppa](https://launchpad.net/~kernel-ppa/+archive/ppa)) and I am using kernel 2.6.39.

---

### Post by Go7enKs on 2011-06-21
> 
Originally Posted by lemuelinchrist  
I bring another good news to my Ubuntu Vaio S series friends.

I finally found a solution on GETTING THE INTERNAL MIC TO WORK in Ubuntu 11.04, after hours of rummaging through the internet

It turned out that our problem was due to an ALSA bug. It's now patched up and the fix has already been committed upstream, but you'll have to wait for the update to come if you want the bug to be fixed.

If you cant wait anymore, here are the steps to do it:

oh... and please do this at your own risk. your system might break so dont blame me if it does.

Lastly, I'm writing down the steps that worked for me on my notebook. I'm pretty sure there's an easier way to do this (one that doesn't need patching) that I don't know yet. So if you do know, please share it with us.

1. download the patch here: [https://bugs.launchpad.net/ubuntu/+s...ony-Vaio.patch](https://bugs.launchpad.net/ubuntu/+s...ony-Vaio.patch)

2. download AlsaUpgrade-1.0.24-2.tar.gz

3. copy both files to /opt

4. cd /opt
5. sudo tar xzvf AlsaUpgrade-1.0.24-2.tar.gz
6. sudo chmod +x AlsaUpgrade-1.0.24-2.sh
7. sudo ./AlsaUpgrade-1.0.24-2.sh -d
8. sudo patch /opt/Alsa-1.0.24/alsa-driver-1.0.24/sound/pci/hda/patch_realtek.c < 0001-ALSA-HDA-Fix-single-internal-mic-on-ALC275-Sony-Vaio.patch
9. sudo ./AlsaUpgrade-1.0.24-2.sh -c
10. sudo ./AlsaUpgrade-1.0.24-2.sh -i

11. reboot your system and test your mic


EDIT:
Here are the sites I read to come up with this fix:
[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/752792](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/752792)
[http://ubuntuforums.org/showthread.php?t=1719770&page=2](http://ubuntuforums.org/showthread.php?t=1719770&page=2)
[http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)
Guys sorry to bother you again. My sound suddenly doesn't work. I assume it's because of something I did trying to get the mic to work. As I said earlier I got stuck at point 8. What do I need to undo to get my sound back?

Thanks

---

### Post by Richo on 2011-06-22
I'm looking at buying a new Viao S series (1600x900 res). I didn't see in mentioned in the thread so I assume that the WiFi works fine?

Cheers,

Richo

---

### Post by Go7enKs on 2011-06-22
Anybody can help me with the sound issue?

---

### Post by carocco on 2011-06-23
Good morning,
I've written to the AMD technical support asking for the graphics driver for the HD 6470M.

Bad news:

> The drivers from AMD are not compatible for switchable graphics laptops in any operating system, including Linux.
 If Sony has no drivers there are none.
 In order to update this service request, please respond, leaving the service request reference intact.
 Best regards,


So?

---

### Post by Romanovzky on 2011-06-23
Well I guess that means bad news for us :\

Is there any client support contact for linux users in sony? We could all drop some kind of request or complaint with these technical issues.

I also have one more issue, I know the touchpad is not working properly but what really annoys me is that it won't disable itself when I'm typing. Right now I'm writing down my masters thesis and it kind of sucks...

---

### Post by clemmy on 2011-06-23
> **Romanovzky said:**
> I also have one more issue, I know the touchpad is not working properly **but what really annoys me is that it won't disable itself when I'm typing.** Right now I'm writing down my masters thesis and it kind of sucks...
I remember that I've seen a script that disables any kind of mouse while typing with the keyboard. It was successfully used to disable a crappy touchpad. Unfortunately I did not bookmarked that page.. but it should be somewere in this forum I think.

I'm sorry I cannot help you more that this.. just wanted you to know that THERE IS a working solution. "Just" need to find it

---

### Post by 23dornot23d on 2011-06-23
This is old but it should work ..... [I][LINK]("http://embraceubuntu.com/2006/03/24/disable-synaptics-touchpad/")


if not .... have a look at some other search results ...... [LINK]("http://www.google.com/search?client=ubuntu&channel=fs&q=disable+touchpad+xorg.conf&ie=utf-8&oe=utf-8")
[/I]

---

### Post by clemmy on 2011-06-23
> **clemmy said:**
> I remember that I've seen a script that disables any kind of mouse while typing with the keyboard. It was successfully used to disable a crappy touchpad. Unfortunately I did not bookmarked that page.. but it should be somewere in this forum I think.

I'm sorry I cannot help you more that this.. just wanted you to know that THERE IS a working solution. "Just" need to find it
Maybe I found something..
[here ]("http://ubuntuforums.org/showpost.php?p=10869949&postcount=8")is a script working for regular touchpads and [here ]("http://ubuntuforums.org/showpost.php?p=10877992&postcount=14")a comment from another user who modified the original script and got it to work with a crappy touchpad that is recognised as a regular ps/2 mouse..

hope it helps

---

### Post by Pierre Zabell on 2011-07-09
I have the new sony vaio sb, and i figured out how to make everything work, from better performance from the CPU, to getting the integrated 3G modem working.
 
I also have turned down the Radeon 6470M graphic card like everyone else.
 
Isen't there really no way to et it working? AMD releases new drivers all the time, but none of them have compatibility with the discrete card.....
 
It might be, as i also read, that AMD have nothing to do with the drivers for this computer, that sony needs to have a driver for this specific setup?
 
Hope there will be a solution in the future, maybe inform of a open source driver. I would like to see more activity on this subject, if anyone have the same computer, and have questions about Ubuntu 11.04, i might have some answers.
 
Thanks.

---

### Post by unixlike on 2011-07-09
Hi,
how can I do to configure my 3g modem?
It is not recognized by default.

---

### Post by carocco on 2011-07-09
> **Pierre Zabell said:**
> I have the new sony vaio sb, and i figured out how to make everything work, from better performance from the CPU, to getting the integrated 3G modem working.
 
I also have turned down the Radeon 6470M graphic card like everyone else.
 
Isen't there really no way to et it working? AMD releases new drivers all the time, but none of them have compatibility with the discrete card.....
 
It might be, as i also read, that AMD have nothing to do with the drivers for this computer, that sony needs to have a driver for this specific setup?
 
Hope there will be a solution in the future, maybe inform of a open source driver. I would like to see more activity on this subject, if anyone have the same computer, and have questions about Ubuntu 11.04, i might have some answers.
 
Thanks.


Hi Pierre! You're right...AMD has nothing to do with the drivers...but I've read this bug report on launchpad

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/727620/+index?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/727620/+index?comments=all)

It seems they are near to find a kind of solution for this issue! I've not tried the various bisects..I'll wait for the final solution!

---

### Post by coldman239 on 2011-07-11
Hi guys!

I need serious help here! I bought a Sony Vaio S series model VPC-SA2C a week ago. I wanted a dual boot between Ubuntu and Windows 7. All the hardware works fine in WIndows 7, however in Ubuntu( version 10.04) the wireless card is not recognized and  I don't know what else can I do? Any tip/ help? Have somebody had the same problem???

---

### Post by Pierre Zabell on 2011-07-12
> **unixlike said:**
> Hi,
how can I do to configure my 3g modem?
It is not recognized by default.

Hello unixlike,

I found you a very easy step by step guide, you can follow to setup your 3G modem.

[http://westhoffswelt.de/blog/0045_howto_setup_sony_vaio_x_wwan_gobi_2000_under_ubuntu_linux.html](http://westhoffswelt.de/blog/0045_howto_setup_sony_vaio_x_wwan_gobi_2000_under_ubuntu_linux.html)

Try it, and if it fails come back to me, and i'll see if i can help.

(The guide is for Qualcomm 2000 modem, as found in my Sony Vaio SB)

And yea, i'm also looking forward to a solution carocco, i really look forward to see my hardware fully functioning!

---

### Post by Romanovzky on 2011-07-24
Hi people,

I've installed the 3.0 (rc7) kernel from here

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc7-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc7-oneiric/)

You just have to download and install the debs by the following order


linux-headers
linux-headers-generic
linux-image


And reboot. The mic works out of the box as so does the touchpad (as in it is recognized a normal touchpad with all its functionality).

*Edit:* Strange enough the touchpad is not recognized (doesn't show in the mouse configuration tool) but it responds nicely to side scrolling and tap to click. Also it doesn't show in "xinput list", any idea?

---

### Post by garbelini on 2011-07-24
I decided to try out Oneiric Alpha2 and as it turns out it runs better than Natty at the moment for me.

Many missing UI features but at least I can always boot up, which was always an intermittent problem under Natty. And the external display plugs in and out just fine.

Fglrx is still broken and I was not able to turn off the AMD graphics card so the battery life is still less than 2h.

Please bear in mind that Oneiric is all kinds of still-not-ready as in many options not available and broken features. Since I can now boot up, I'll stick to it.

PS1.: My machine is a Sony Vaio VPCSB

PS2.: I'm kinda of addicted to updates and can't resist running the update-manager several times a day.

---

### Post by Romanovzky on 2011-07-24
If fglrx is broken and you didn't turn off amd what is your settings? Did you installed amd drivers from their site? Can you use the stamina-speed switch without problems?

---

### Post by garbelini on 2011-07-24
> **Romanovzky said:**
> If fglrx is broken and you didn't turn off amd what is your settings? Did you installed amd drivers from their site? Can you use the stamina-speed switch without problems?

Last time I tried to install the AMD driver from their site it didn't work.

I'm using the Intel card with the default driver, no changes at all. The Stamina/Speed switch does nothing.

I believe the AMD card is on but doing nothing in the background except for sucking the juice out of my battery when I'm unplugged.

---

### Post by Romanovzky on 2011-07-24
I think the switch enables and disables the access to the amd card. But in 11.04 my ubuntu won't boot in speed mode (I had to block the module and boot in stamina), that's why I asked you because from what you said it seems that it works better in 11.10.

---

### Post by garbelini on 2011-07-24
> **Romanovzky said:**
> I think the switch enables and disables the access to the amd card. But in 11.04 my ubuntu won't boot in speed mode (I had to block the module and boot in stamina), that's why I asked you because from what you said it seems that it works better in 11.10.

Just tried to switch to Speed and boot and it worked!

I'll try to install the AMD driver again once the final 11.10 is out. At this point I can only dream we will ever get this dual display thing working properly one day.

---

### Post by Romanovzky on 2011-07-24
It will. But for now I think the working switch is really good news.

I hope we see some development in the amd driver installation issue and in power regression. But both are highly related to kernel issues and features so we must wait patiently.

---

### Post by clemmy on 2011-07-25
Hi poeple,

I wanted to share my experience because I have a better situation that what I read in some of the previous comments.

Also here the stamina/speed switch does nothing, but:
* I **always** boot successfully
* I can **power off** the amd graphics card via vgaswitcheroo
* Mic works
* I have more than 4 hours of battery juice when browsing and doing some text editing
* External monitor connected to the vga port works perfectly. I can control it via the control center and also via the dedicated button on the keyboard (Fn + F7)


I have a VPCSB with i5-2410M and AMD Radeon HD 6470M
I run natty with 2.6.39-3-generic kernel

---

### Post by Pierre Zabell on 2011-07-25
> **garbelini said:**
> Just tried to switch to Speed and boot and it worked!

I'll try to install the AMD driver again once the final 11.10 is out. At this point I can only dream we will ever get this dual display thing working properly one day.

The AMD discrete graphic card works in 11.10? From what i understand the Stamina/Speed switch is based on software from Sony not a actual hardware switch?

Please go in more details, i'm very interested!

---

### Post by garbelini on 2011-07-25
Cool! After your message I went to try again vgaswitcheroo and it works now! The Radeon is off.

All I did was the echo OFF > switch part from here:
[http://www.33dots.com/index.php/linux/hybrid-graphics-in-sony-vaio-and-fedora.html](http://www.33dots.com/index.php/linux/hybrid-graphics-in-sony-vaio-and-fedora.html)

From the text it looks like the AMD driver install removes vgaswitcheroo for some reason. That's where I was having problems.

> **clemmy said:**
> Hi poeple,

I wanted to share my experience because I have a better situation that what I read in some of the previous comments.

Also here the stamina/speed switch does nothing, but:
* I **always** boot successfully
* I can **power off** the amd graphics card via vgaswitcheroo
* Mic works
* I have more than 4 hours of battery juice when browsing and doing some text editing
* External monitor connected to the vga port works perfectly. I can control it via the control center and also via the dedicated button on the keyboard (Fn + F7)


I have a VPCSB with i5-2410M and AMD Radeon HD 6470M
I run natty with 2.6.39-3-generic kernel

---

### Post by garbelini on 2011-07-25
Sorry if I was not clear:

The AMD card never worked for me on 11.10 nor on 11.04.

Regarding the Stamina/Speed switch it's just guess work for me. No idea how it works. What I can tell is that in my case linux is ignoring it completely and it never had any effect on my system whatsoever.

> **Pierre Zabell said:**
> The AMD discrete graphic card works in 11.10? From what i understand the Stamina/Speed switch is based on software from Sony not a actual hardware switch?

Please go in more details, i'm very interested!

---

### Post by lvanderree on 2011-07-28
Thanks for all the info guys!

I bought myself a Vaio SA and got everything up and  running within no-time thanks to you.

I installed natty (not using USB-3 port, since then it couldn't found the drive while booting)

upgraded all packages, added the 2 PPA's for:
 * linux-kernel (3.0.0-5-generic)
 * xorg

I followed the instruction from our fedora friend: [www.33dots.com/index.php/linux/hybrid-graphics-in-sony-vaio-and-fedora.html](www.33dots.com/index.php/linux/hybrid-graphics-in-sony-vaio-and-fedora.html) to disable the radeon as good as possible.

and changed my mouse with the 
  options psmouse proto=imps
which gives me edge scrolling and a better responding mouse than in Windows (no two finger unfortunately) 

and I am now pretty happy with the result. I didn't bought this laptop for the radeon anyway, and everything else seems to work! Including audio, headphone (alsamixer let you enable both speakers and headphone at the same time), wireless, bluetooth, keyboard backlight, and all other keyboard function-keys.

So things that can be improved are:
- two finger scrolling (does not work in windows either)
- keeping the radeon completely disabled (also after resuming hybernate/standby)
- more energy saving, although I don't know yet how long it will currently hold (I guess 8hours with the battery sheet, not 15 though)

But that is about it!

---

### Post by lvanderree on 2011-08-02
I can recommend taking a look at [http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/) where they are working on disabling the radeon. And I can say they do so very successfully, with also the radeon module blacklisted/disabled!

I am currently running Mint, with kernel 2.6.38 (-10)

Here are the results of 
```

grep rate /proc/acpi/battery/BAT1/state

```

after booting my battery is used:
21035 mW

after disabling the radeon with the acpi call:
9694 mW

after resuming from standby:
19307 mW

after again disabling the radeon with the acpi call:
10949 mW


So you see the enormous difference after siabling the radeon!
You also see it being back enabled after resuming standby,
but I can again disable it, in contradiction to switcheroo, which also requires the radeon module!

Looks very nice to me!

---

### Post by lvanderree on 2011-08-03
I did some more research and wrote some small scripts to automatically disable the radeon after booting and resuming from standby/hibernation.

As mentioned in the previous post, I blacklisted the radeon module and have compiled the acpi_call module from [http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/) 

To automatically deactivate the radeon card, I have done the following:

**install the acpi_call module**
```

sudo cp acpi_call.ko /lib/modules/`uname -r`/kernel/
sudo depmod

```

To test if the module will work correctly, call
```

sudo modprobe acpi_call

```
Which should give no errors

if it works, add acpi_call to /etc/modules
```

sudo gedit /etc/modules

```
I've added a line after lp

**create a script to perform the acpi call**
```

sudo gedit /usr/local/bin/radeon_off_sony_sa.sh

```

And add the following 
```

#!/bin/sh

echo "\_SB.PCI0.PEG0.PEGP._OFF" > /proc/acpi/call
```

Then make it executable and test if it works:
```

chmod 755 /usr/local/bin/radeon_off_sony_sa.sh

/usr/local/bin/radeon_off_sony_sa.sh
cat /proc/acpi/call

```
The cat should return:
0x0


**automatically run the script during booting**
Once the script is working, this is easy. Add the script to /etc/rc.local before exit 0

```

sudo gedit /etc/rc.local

```

and add (before the exit line):
```

/usr/local/bin/radeon_off_sony_sa.sh

```


**automatically re-deactivate the radeon after standby/hibernation**
```

sudo gedit /etc/pm/sleep.d/10_disable_radeon

```


and add the following code to it:
```

#!/bin/sh

# Action script ensures that discrete graphics card is disabled after  
# resuming from standby/hybernate
#
#

PATH=/usr/local/bin:/bin

case "${1}" in
        resume|thaw)
                radeon_off_sony_sa.sh
                ;;
esac

```

And that is it! Now the Radeon will be disabled at all time, saving you from some heat, and more important some battery draining!


The only I would like to have improved now is the touchpad. Make it detect my hand palms and enable two finger scrolling.

---

### Post by baaryyy on 2011-08-04
can someone tell me what you would need to do to get this laptop up and running from the start? is the above enough?

---

### Post by lvanderree on 2011-08-04
Download the Ubuntu 11.04 live CD (or Mint, or Fedora, whatever suits you most), 
burn it on CD or create an USB-Disk and 
boot from it (change boot order in your bios)

Tip: Don't put the USB-disk in the blue USB-3 port (for some reason it could not find the usb-disk anymore during booting, but the other ports are fine)

Everything will work out of the box, but the above will optimize your system (disabling the not used/non-functioning Radeon, saving you battery-power and heat).

Also updating to the latest kernel (3.0) is an option, but not required. (At the moment I don't use it, 2.6.38 is running stable)

Also the Radeon-kernel-module can break standby/hibernation, depending on your linux-kernel version. So I advise you to at least blacklist that module.

---

### Post by carocco on 2011-08-08
Does anybody tried the new 11.07 Catalyst? I've read on the italian forum that they support the 6470M card..I can't try them now...

---

### Post by nicgom on 2011-08-21
> **lvanderree said:**
> I did some more research and wrote some small scripts to automatically disable the radeon after booting and resuming from standby/hibernation.

As mentioned in the previous post, I blacklisted the radeon module and have compiled the acpi_call module from [http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/) 

To automatically deactivate the radeon card, I have done the following:

**install the acpi_call module**
```

sudo cp acpi_call.ko /lib/modules/`uname -r`/kernel/
sudo depmod

```

To test if the module will work correctly, call
```

sudo modprobe acpi_call

```
Which should give no errors

if it works, add acpi_call to /etc/modules
```

sudo gedit /etc/modules

```
I've added a line after lp

**create a script to perform the acpi call**
```

sudo gedit /usr/local/bin/radeon_off_sony_sa.sh

```

And add the following 
```

#!/bin/sh

echo "\_SB.PCI0.PEG0.PEGP._OFF" > /proc/acpi/call
```

Then make it executable and test if it works:
```

chmod 755 /usr/local/bin/radeon_off_sony_sa.sh

/usr/local/bin/radeon_off_sony_sa.sh
cat /proc/acpi/call

```
The cat should return:
0x0


**automatically run the script during booting**
Once the script is working, this is easy. Add the script to /etc/rc.local before exit 0

```

sudo gedit /etc/rc.local

```

and add (before the exit line):
```

/usr/local/bin/radeon_off_sony_sa.sh

```


**automatically re-deactivate the radeon after standby/hibernation**
```

sudo gedit /etc/pm/sleep.d/10_disable_radeon

```


and add the following code to it:
```

#!/bin/sh

# Action script ensures that discrete graphics card is disabled after  
# resuming from standby/hybernate
#
#

PATH=/usr/local/bin:/bin

case "${1}" in
        resume|thaw)
                radeon_off_sony_sa.sh
                ;;
esac

```

And that is it! Now the Radeon will be disabled at all time, saving you from some heat, and more important some battery draining!


The only I would like to have improved now is the touchpad. Make it detect my hand palms and enable two finger scrolling.


Hi, thanks for the how to, it works, i get 4:30 mins batery life, and tha laptop doesn't get as hot as before, i also got the mouse working thanks to an earlier comment in this same thread, works even better than in win7, i just would like to have the same gestures as in win7. the other thing that bothers me, is that i have compiz installed but somehow doesn't work at all, why is that, if i understand correctly the intel chip onboard should  be more than capapble of running compiz. does anybody know how to make it work, i don't use the cube, but the wall and some light effects.

by the way, i am running the gnome classic ui in pinguy os mini 11.04 (ubuntu 11.04 based)

---

### Post by lvanderree on 2011-08-30
Maybe it has something to do with pinguy os, or its gnome classic ui setup, since I can use compiz on both Ubuntu 11.04, 11.10 and Mint 11

---

### Post by superthermal on 2011-09-22
hi all! just wondering if there are any updates on how your vaios are working--battery life is still ~3-4hrs? no further hardware compat issues? also, slightly off-topic, but how is the laptop in general? screen vibrant? sturdy? trackpad work well?

thanks!

---

### Post by adm1968 on 2011-09-25
[FONT="Georgia"][SIZE="2"]I have followed your instructions really carefully, no errors
I've seen a very good increase in battery life, but it is impossible to suspend/hibernate
Is something else needed for these?

Cheers![/SIZE][/FONT]

---

### Post by adm1968 on 2011-09-25
> **lvanderree said:**
> Re: New Sony Vaio s series Ubuntu compatibility
I did some more research and wrote some small scripts to automatically disable the radeon after booting and resuming from standby/hibernation.

As mentioned in the previous post, I blacklisted the radeon module and have compiled the acpi_call module from [http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/)

To automatically deactivate the radeon card, I have done the following:

install the acpi_call module
Code:

sudo cp acpi_call.ko /lib/modules/`uname -r`/kernel/
sudo depmod

To test if the module will work correctly, call
Code:

sudo modprobe acpi_call

Which should give no errors

if it works, add acpi_call to /etc/modules
Code:

sudo gedit /etc/modules

I've added a line after lp

create a script to perform the acpi call
Code:

sudo gedit /usr/local/bin/radeon_off_sony_sa.sh

And add the following
Code:

#!/bin/sh

echo "\_SB.PCI0.PEG0.PEGP._OFF" > /proc/acpi/call

Then make it executable and test if it works:
Code:

chmod 755 /usr/local/bin/radeon_off_sony_sa.sh

/usr/local/bin/radeon_off_sony_sa.sh
cat /proc/acpi/call

The cat should return:
0x0


automatically run the script during booting
Once the script is working, this is easy. Add the script to /etc/rc.local before exit 0

Code:

sudo gedit /etc/rc.local

and add (before the exit line):
Code:

/usr/local/bin/radeon_off_sony_sa.sh


automatically re-deactivate the radeon after standby/hibernation
Code:

sudo gedit /etc/pm/sleep.d/10_disable_radeon


and add the following code to it:
Code:

#!/bin/sh

# Action script ensures that discrete graphics card is disabled after  
# resuming from standby/hybernate
#
#

PATH=/usr/local/bin:/bin

case "${1}" in
        resume|thaw)
                radeon_off_sony_sa.sh
                ;;
esac

And that is it! Now the Radeon will be disabled at all time, saving you from some heat, and more important some battery draining!


The only I would like to have improved now is the touchpad. Make it detect my hand palms and enable two finger scrolling.
Last edited by lvanderree; August 4th, 2011 at 10:12 AM.. 

[FONT="Georgia"][SIZE="2"]I have followed your instructions really carefully, no errors
I've seen a very good increase in battery life, but it is impossible to suspend/hibernate
Is something else needed for these?

Cheers![/SIZE][/FONT]

---

### Post by adm1968 on 2011-09-25
> **lvanderree said:**
> I did some more research and wrote some small scripts to automatically disable the radeon after booting and resuming from standby/hibernation.

As mentioned in the previous post, I blacklisted the radeon module and have compiled the acpi_call module from [http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/) 

To automatically deactivate the radeon card, I have done the following:

**install the acpi_call module**
```

sudo cp acpi_call.ko /lib/modules/`uname -r`/kernel/
sudo depmod

```

To test if the module will work correctly, call
```

sudo modprobe acpi_call

```
Which should give no errors

if it works, add acpi_call to /etc/modules
```

sudo gedit /etc/modules

```
I've added a line after lp

**create a script to perform the acpi call**
```

sudo gedit /usr/local/bin/radeon_off_sony_sa.sh

```

And add the following 
```

#!/bin/sh

echo "\_SB.PCI0.PEG0.PEGP._OFF" > /proc/acpi/call
```

Then make it executable and test if it works:
```

chmod 755 /usr/local/bin/radeon_off_sony_sa.sh

/usr/local/bin/radeon_off_sony_sa.sh
cat /proc/acpi/call

```
The cat should return:
0x0


**automatically run the script during booting**
Once the script is working, this is easy. Add the script to /etc/rc.local before exit 0

```

sudo gedit /etc/rc.local

```

and add (before the exit line):
```

/usr/local/bin/radeon_off_sony_sa.sh

```


**automatically re-deactivate the radeon after standby/hibernation**
```

sudo gedit /etc/pm/sleep.d/10_disable_radeon

```


and add the following code to it:
```

#!/bin/sh

# Action script ensures that discrete graphics card is disabled after  
# resuming from standby/hybernate
#
#

PATH=/usr/local/bin:/bin

case "${1}" in
        resume|thaw)
                radeon_off_sony_sa.sh
                ;;
esac

```

And that is it! Now the Radeon will be disabled at all time, saving you from some heat, and more important some battery draining!


The only I would like to have improved now is the touchpad. Make it detect my hand palms and enable two finger scrolling.

[FONT="Georgia"][SIZE="2"]OK, I've just followed your instructions again, this time with Mint 11 (64). 
Before applying your method, the laptop went into suspend/hibernate without a glitch.
After applying it, the laptop will not go into suspend/hibernate.
Any ideas?

Many thanks![/SIZE][/FONT]

---

### Post by Victor101 on 2011-09-25
> **adm1968 said:**
> [FONT="Georgia"][SIZE="2"]I have followed your instructions really carefully, no errors
I've seen a very good increase in battery life, but it is impossible to suspend/hibernate
Is something else needed for these?

Cheers![/SIZE][/FONT]

I don't know what to say. I also followed the instructions really carefully on my Vaio SB and I don't see any change on suspend/hibernate behavior...

---

### Post by lvanderree on 2011-10-03
> **adm1968 said:**
> [FONT="Georgia"][SIZE="2"]OK, I've just followed your instructions again, this time with Mint 11 (64). 
Before applying your method, the laptop went into suspend/hibernate without a glitch.
After applying it, the laptop will not go into suspend/hibernate.
Any ideas?

Many thanks![/SIZE][/FONT]


I am back from vacation, so it took a while before I wrote this reply. Unfortunately I have No idea. 

I am currently running Ubuntu 11.10 alpha/beta/rc and again have no stability problems (after disabling the radeon driver).

However Ubuntu 11.10 seems to be using a lot more energy...

grep rate /proc/acpi/battery/BAT1/state
currently gives me:

present rate:            26292 mW

instead of something arround 10W

---

### Post by clemmy on 2011-10-07
> **lvanderree said:**
> However Ubuntu 11.10 seems to be using a lot more energy...

grep rate /proc/acpi/battery/BAT1/state
currently gives me:

present rate:            26292 mW

instead of something arround 10W

Same power consumption regression on my Vaio. I'm disabling the ATI card via the vgaswitcheroo instead of the acpi_call method, but I'm experiencing the same problem.

I used to see a rate of ~11W with Natty  (readeon OFF, wifi ON, medium screen backlight). Now in the same conditions I have ~ 17W. I hope it will discovered where it come from this regression!

Do you know if this problem is specific of this notebook, of if it is common with other hardware?

---

### Post by Victor101 on 2011-10-10
> **clemmy said:**
> Same power consumption regression on my Vaio. I'm disabling the ATI card via the vgaswitcheroo instead of the acpi_call method, but I'm experiencing the same problem.

I used to see a rate of ~11W with Natty  (readeon OFF, wifi ON, medium screen backlight). Now in the same conditions I have ~ 17W. I hope it will discovered where it come from this regression!

Do you know if this problem is specific of this notebook, of if it is common with other hardware?

I am experiencing the same regression on my Vaio SB...

---

### Post by nicgom on 2011-10-15
hi i just installed 11.10 yesterday and while i could turn off the ati, with the acpi_call method, somehow batery life is now worst, with 11.04 i was getting about 4:40 from 2:00, now im getting 2:40 from 1:40, its not good at all? does anybody here know any fix for it.

thanks in advance.

---

### Post by lvanderree on 2011-10-15
I don't completely understand your counting, but I guess what you try to say is you are out of battery faster...

Please have a look at this thread: [http://ubuntuforums.org/showpost.php?p=11346775&postcount=7](http://ubuntuforums.org/showpost.php?p=11346775&postcount=7)

Adding that to your kernel parameters in grub does the trick! More info can be found in the entire thread.

---

### Post by deaththeorist on 2011-10-16
hey! does this work for the i7 version of vaio s?

you only had to add this one line to experience the power savings? no other settings like the acpi_call and blacklist?

---

### Post by lvanderree on 2011-10-16
Yes this works for the i7 as well,

it improves/enables the power saving capabilities of the intel graphics card on a sandy bridge, as can be read here: [http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1)

So I also still disable the Radeon, by blacklisting it, and turning it off with the acpi_call command.

I also disable my bluetooth by default, since I am not using it always anyway, by adding another line to /etc/rc.local 

```

#disable radeon on startup
/usr/local/bin/radeon_off_sony_sa.sh

#disable bluetooth on startup
rfkill block bluetooth

exit 0


```

You can still enable bluetooth by clicking on the icon in the tray when you need it.

---

### Post by deaththeorist on 2011-10-16
wow cool! thanks for the tip! :)
u using the i7 vaio s too? how much batt life u do get with ur settings? i'm so gonna try this later :):):)

---

### Post by clemmy on 2011-10-16
lvanderree pointed out the most important tweaks, they work great!

Eventually if you want to go further you can also find a script to activate power management for usb and pci devices. [link]("http://ubuntuforums.org/showpost.php?p=11337515&postcount=25")


Have fun!

---

### Post by lvanderree on 2011-10-16
Jep I have an i7 as well (and 7200rpm harddisk).

I also have the additional sleeve battery, but set my batteries to charge only till 80% (with the sony settings-tool on windows), so I don't know how much it is worth telling how long I do with my setup...

Yesterday I was working with these settings, and I could work again for something like 7 hours, with wifi on and screen 80% bright, system temperature between 40 and 45degrees Celcius. I was working on a Django project and had my IDE (PyCharm) and Chromium open all of the time. 

When you charge your batteries fully till 100% you of course should get even more out of it, but I guess Linux can be optimized even further. I sometimes see my webcam, fingerprint reader and audiodevice popup in powertop, demanding energy while not even being in use...

---

### Post by lvanderree on 2011-10-16
> **clemmy said:**
> 

Eventually if you want to go further you can also find a script to activate power management for usb and pci devices. [link]("http://ubuntuforums.org/showpost.php?p=11337515&postcount=25")


Thanks clemmy, I will definately try these out as well when I have some more time to spare.

Regards
Leon ;-)

---

### Post by deaththeorist on 2011-10-16
> **lvanderree said:**
> Jep I have an i7 as well (and 7200rpm harddisk).

I also have the additional sleeve battery, but set my batteries to charge only till 80% (with the sony settings-tool on windows), so I don't know how much it is worth telling how long I do with my setup...

Yesterday I was working with these settings, and I could work again for something like 7 hours, with wifi on and screen 80% bright, system temperature between 40 and 45degrees Celcius. I was working on a Django project and had my IDE (PyCharm) and Chromium open all of the time. 

When you charge your batteries fully till 100% you of course should get even more out of it, but I guess Linux can be optimized even further. I sometimes see my webcam, fingerprint reader and audiodevice popup in powertop, demanding energy while not even being in use...
same setup and settings as u but no additional sheet battery... hmm..... with windows its 7 hours on the most powersaving settings.... i saw somewhere that some people got their ubuntu laptops to run longer than on win7.... guess vaio s still cant hit that standard eh?
would u guys say that using lxde with ubuntu would help? like have unity/kde when i'm plugged in and use lxde or xfce when i'm out? would this make sense?

---

### Post by deaththeorist on 2011-10-16
btw, i've noticed that if i charge my laptop while in ubuntu, ubuntu will ignore the 80% max setting in windows and charge to 100...however, if i plug in my laptop while in win7, charge to 80%, then restart into ubuntu, ubuntu will jus use ac power. is there anyway to set the 80% limit in ubuntu?

---

### Post by clemmy on 2011-10-17
Just found a solution to enable advanced features of the touchpad! :)

Just go [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625/comments/492") and install the package psmouse-alps-dkms, reboot and enjoy. (Remove and psmouse proto=imps option that you may have added in /etc/modprobe.d/ to enable side-scrolling before, it's not needed anymore) 

I'm experimenting two-finger scrolling and circular scrolling, they both work very good. 

Also the two-finger tapping to emulate right click is working, but it's a little more tricky, I get it only sometimes.. I think it requires to be very precise..

Three-finger tapping to emulate 3rd button click should also work, but so far I've not been able to trigger it. (Don't know if it's still buggy, or if I'm not enough precise..)

---

### Post by deaththeorist on 2011-10-17
> **clemmy said:**
> Just found a solution to enable advanced features of the touchpad! :)

Just go [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625/comments/492") and install the package psmouse-alps-dkms, reboot and enjoy. (Remove and psmouse proto=imps option that you may have added in /etc/modprobe.d/ to enable side-scrolling before, it's not needed anymore) 

I'm experimenting two-finger scrolling and circular scrolling, they both work very good. 

Also the two-finger tapping to emulate right click is working, but it's a little more tricky, I get it only sometimes.. I think it requires to be very precise..

Three-finger tapping to emulate 3rd button click should also work, but so far I've not been able to trigger it. (Don't know if it's still buggy, or if I'm not enough precise..)

i love u 2 LOL! making ubuntu on vaio much more usable

---

### Post by lvanderree on 2011-10-18
> **clemmy said:**
> Just found a solution to enable advanced features of the touchpad! :)


Great! It's not perfect yet, but it is a good start! Nice to see some progress on this area as well!


@deaththeorist The charging till 80% works every time for me. I have set it up once in Windows, and now always boot to Ubuntu. I don't turn my computer off that much though, always putting it into standby... But I have rebooted it and occasionally turn it off and it keeps charging till 80%

---

### Post by clemmy on 2011-10-18
> **lvanderree said:**
> @deaththeorist The charging till 80% works every time for me. I have set it up once in Windows, and now always boot to Ubuntu. I don't turn my computer off that much though, always putting it into standby... But I have rebooted it and occasionally turn it off and it keeps charging till 80%
How can you check, in ubuntu, if it's carged completely or just till 80%? (How can you check if the setting from Windows have been preserved?)

---

### Post by lvanderree on 2011-10-18
> **clemmy said:**
> How can you check, in ubuntu, if it's carged completely or just till 80%? (How can you check if the setting from Windows have been preserved?)

Simple, the charging simply stops at 80%. So when you click on the battery in the notification area you see one (or two) battery(s) which are charged till 80% .

I was surprised that these settings, which I configured in Windows with the Vaio tool apparently are stored in the battery(s), or other hardware, the first time I noticed Ubuntu stopped charging when it was at 80%.

---

### Post by clemmy on 2011-10-18
> **lvanderree said:**
> Great! It's not perfect yet, but it is a good start! Nice to see some progress on this area as well!
Yes, not perfect yet.. but I was able to improve a lot it's "feeling" playing with synclient settings.

I put them in a .sh script, made that file executable, and I automatically launch it on login via Startup Applications dialog. This is what I put in the script:
```
#!/bin/bash

device="AlpsPS/2 ALPS DualPoint TouchPad"

# Finger pressure
xinput set-prop "$device" "Synaptics Finger" 10 12 255

# Circular scrolling
xinput set-prop "$device" "Synaptics Circular Scrolling" 1
xinput set-prop "$device" "Synaptics Circular Scrolling Trigger" 1
xinput set-prop "$device" "Synaptics Circular Scrolling Distance" 0.1

# Dragging
xinput set-prop "$device" "Synaptics Locked Drags" 1
xinput set-prop "$device" "Synaptics Locked Drags Timeout" 1000


# Speed
xinput set-prop "$device" "Synaptics Move Speed" 0.5 2.0 0.07 40.0


# Tapping
xinput set-prop "$device" "Synaptics Tap Move" 200
xinput set-prop "$device" "Synaptics Tap FastTap" 1

# Emulate middle-button when tapping with two fingers
xinput set-prop "$device" "Synaptics Tap Action" 2 3 0 0 1 2 3

exit 0


```
Now it's much better , but tap-and-drag is not as good as old driver yet. Sometimes I want to tap-and-drag the touchpad just records a simple tap followed by a normal movement of the mouse.. :(

---

### Post by clemmy on 2011-10-18
> **lvanderree said:**
> Simple, the charging simply stops at 80%. So when you click on the battery in the notification area you see one (or two) battery(s) which are charged till 80% .
LOL, great! :D

---

### Post by deaththeorist on 2011-10-19
hmm.... i've discovered where my 80%/100% problem is.... 
if i boot into ubuntu and charge my battery when its below 80%... it will charge to 80% and stop.... then if i unplug and plug it in again.... it will charge to 100%....
if i now boot into windows.... the vaio center program will say hey! ur batt is over 80%....we will not use the external power supply until it hits 80%.... 


one more thing.... sometimes when i boot into ubuntu.... it gets stuck at a black screen with my mouse cursor in the middle.... some times there is the lightdm screen....but the mouse cursor is stuck in the middle and the typing cursor is stuck and not blinking.... no response from pressing any key combination.... then i have to hold down power button... and jus attempt to boot a few more times without changing settings and its all good... (i found that if i mess around with the settings... removing i915... adding nomodeset.... and combinations of them.... it always gets stuck... however if i boot with the same settings... it boots right within 3 tries most of the time...)
i've only added i915.i915_enable_rc6=1 into my kernel settings thing....what am i doing wrong? is there something else i need to add?

---

### Post by clemmy on 2011-10-19
> **deaththeorist said:**
> one more thing.... sometimes when i boot into ubuntu.... it gets stuck at a black screen with my mouse cursor in the middle.... some times there is the lightdm screen....but the mouse cursor is stuck in the middle and the typing cursor is stuck and not blinking.... no response from pressing any key combination.... then i have to hold down power button... and jus attempt to boot a few more times without changing settings and its all good... (i found that if i mess around with the settings... removing i915... adding nomodeset.... and combinations of them.... it always gets stuck... however if i boot with the same settings... it boots right within 3 tries most of the time...)
i've only added i915.i915_enable_rc6=1 into my kernel settings thing....what am i doing wrong? is there something else i need to add?
I've never experienced such problems, nor in natty neither in oneiric.  Anyway, if I recall correctly, some users having such problems solved them by blacklisting the radeon module.

The downside of this is that you cannot power off your ati video card via the already installed vgaswticheroo, but you have to install acpi_call

---

### Post by deaththeorist on 2011-10-19
hmm... but i did blacklist radeon and use acpi...

---

### Post by lvanderree on 2011-10-19
> **deaththeorist said:**
> hmm... but i did blacklist radeon and use acpi...

I don't experience any of your problems.

I of course have also disabled radeon and use acpi_call, but it is running very stable on 3.0.12

I also don't have any problems regarding the charging, it charges till 80% and then it stops. I haven't tried to disconnect and reconnect the charger when it is at 80%, but I do sometimes unplug when it is standby to find myself using another powersocket in my house...

---

### Post by deaththeorist on 2011-10-19
hmm..... i wonder whats wrong with my laptop :(... do you guys tink a fresh install would help? but i jus installed it......

---

### Post by deaththeorist on 2011-10-23
hey, do you guys set your vaio switch to stamina or speed? i find that if i set it to speed, i never get the booting problems i mentioned earlier

---

### Post by lvanderree on 2011-10-23
> **deaththeorist said:**
> hey, do you guys set your vaio switch to stamina or speed? i find that if i set it to speed, i never get the booting problems i mentioned earlier

Hmm never thought of this, but I always have it set to Stamina. 
I haven't got a clue on why it is running unstable for you and how to fix this. What is the output of sensors for you?

For me it currently is around 50degrees. Maybe it gets to hot?

---

### Post by deaththeorist on 2011-10-23
yea it runs around 50 degrees too...but when i on it it should be room temperature...or even lower?

---

### Post by opodaniel on 2011-10-26
> **clemmy said:**
> Yes, not perfect yet.. but I was able to improve a lot it's "feeling" playing with synclient settings.

I put them in a .sh script, made that file executable, and I automatically launch it on login via Startup Applications dialog. This is what I put in the script:
```
#!/bin/bash

device="AlpsPS/2 ALPS DualPoint TouchPad"

# Finger pressure
xinput set-prop "$device" "Synaptics Finger" 10 12 255

# Circular scrolling
xinput set-prop "$device" "Synaptics Circular Scrolling" 1
xinput set-prop "$device" "Synaptics Circular Scrolling Trigger" 1
xinput set-prop "$device" "Synaptics Circular Scrolling Distance" 0.1

# Dragging
xinput set-prop "$device" "Synaptics Locked Drags" 1
xinput set-prop "$device" "Synaptics Locked Drags Timeout" 1000


# Speed
xinput set-prop "$device" "Synaptics Move Speed" 0.5 2.0 0.07 40.0


# Tapping
xinput set-prop "$device" "Synaptics Tap Move" 200
xinput set-prop "$device" "Synaptics Tap FastTap" 1

# Emulate middle-button when tapping with two fingers
xinput set-prop "$device" "Synaptics Tap Action" 2 3 0 0 1 2 3

exit 0


```
Now it's much better , but tap-and-drag is not as good as old driver yet. Sometimes I want to tap-and-drag the touchpad just records a simple tap followed by a normal movement of the mouse.. :(
This is not working for me, got this errors :
> property Synaptics Finger doesn't exist, you need to specify its type and format
property Synaptics Circular Scrolling doesn't exist, you need to specify its type and format
property Synaptics Circular Scrolling Trigger doesn't exist, you need to specify its type and format
property Synaptics Circular Scrolling Distance doesn't exist, you need to specify its type and format
property Synaptics Locked Drags doesn't exist, you need to specify its type and format
property Synaptics Locked Drags Timeout doesn't exist, you need to specify its type and format
property Synaptics Move Speed doesn't exist, you need to specify its type and format
property Synaptics Tap Move doesn't exist, you need to specify its type and format
property Synaptics Tap FastTap doesn't exist, you need to specify its type and format
property Synaptics Tap Action doesn't exist, you need to specify its type and format

Anyway, if someone need to disable the touchpad ( that can be really anoying while typing), there is a script here : [http://ubuntuforums.org/showthread.php?t=1675603](http://ubuntuforums.org/showthread.php?t=1675603)
> **$xinput --list**
&#9121; Virtual core pointer id=2 [master pointer (3)]
&#9116; &#8627; Virtual core XTEST pointer id=4 [slave pointer (2)]
&#9116; &#8627; Logitech USB Optical Mouse id=11 [slave pointer (2)]
&#9116; &#8627; _PS/2 Mouse id=14_ [slave pointer (2)]
&#9116; &#8627; _AlpsPS/2 ALPS GlidePoint_ id=13 [slave pointer (2)]
&#9123; Virtual core keyboard id=3 [master keyboard (2)]
&#8627; Virtual core XTEST keyboard id=5 [slave keyboard (3)]
&#8627; Video Bus id=6 [slave keyboard (3)]
&#8627; Sony Vaio Keys id=7 [slave keyboard (3)]
&#8627; Video Bus id=8 [slave keyboard (3)]
&#8627; Power Button id=9 [slave keyboard (3)]
&#8627; USB2.0 Camera id=10 [slave keyboard (3)]
&#8627; AT Translated Set 2 keyboard id=12 [slave keyboard (3)]

then make the following script **$vim ~/touch.sh**
> # toggle synaptic touchpad on/off
SYNSTATE=$(xinput list-props "_PS/2 Mouse_" | grep Enabled | grep -Eo '.$')
if [ $SYNSTATE = 0 ]; then xinput set-int-prop "_PS/2 Mouse_" "Device Enabled" 8 1
else xinput set-int-prop "_PS/2 Mouse_" "Device Enabled" 8 0; fi

The best practice is to make a key-combination to call the script which will enable/disable the touchpad.

---

### Post by opodaniel on 2011-10-26
> **clemmy said:**
> lvanderree pointed out the most important tweaks, they work great!

Eventually if you want to go further you can also find a script to activate power management for usb and pci devices. [link]("http://ubuntuforums.org/showpost.php?p=11337515&postcount=25")


Have fun!

disable the USB when not on power ac  is bad idea because it disable also the touchpad . The moment you disconnect the power supply you cannot use the mouse too. I have commented that portion of the script. I also modified the CPU option on power supply mode from performance to ondemand since it fits beautifully my needs and keep my laptop cooler.

---

### Post by deaththeorist on 2011-10-26
did u check out post #126 on this thread? you need to do that before all the xinput things.
and nope disabling usb power when unplug has no problems for me.. apparently the power comes back on when you need it

btw, i noticed you are using 32-bit ubuntu... why 32?

the rest are you guys using 32 too? i'm using 64... would that be the problem? :'( i still cant figure out

---

### Post by Victor101 on 2011-10-27
64-bit Ubuntu is not your problem, I'm actually using it on my vaio SB and all the tricks worked fine on it.

---

### Post by deaththeorist on 2011-10-27
the tricks work splendid!:) but ubuntu itself does not:(

---

### Post by tobik on 2011-10-30
Hi, I'm thinking of buying this laptop. I went through the thread but there are three things I'd like to make more specific.

(1) How long can the laptop go with only _one_ battery? Let say doing some basic work with a powersaving profile and lowered brightness?

(2) Does the Intel card support hw accelerated desktop? Like Unity/Kwin/Compiz? With some decent performance?

(3) These laptops are supposed to have keyboard backlight which is automatically adjusted by a light sensor. Does it work?

---

### Post by lvanderree on 2011-10-30
> **tobik said:**
> Hi, I'm thinking of buying this laptop. I went through the thread but there are three things I'd like to make more specific.

(1) How long can the laptop go with only _one_ battery? Let say doing some basic work with a powersaving profile and lowered brightness?


It depends on the amount of tricks you apply, because currently out of the box the energy consumption is definitely not optimal yet.

In Windows I guess you can get around 6-7 hours.
On Ubuntu probably around 4-5hours, but I didn't apply all tricks yet.

I notice that after resuming from standby the consumption is also higher than after a fresh reboot.

> **tobik said:**
> 
(2) Does the Intel card support hw accelerated desktop? Like Unity/Kwin/Compiz? With some decent performance?



The Intel card is not bad, it can handle all compiz actions by hardware acceleration perfectly.

> **tobik said:**
> 

(3) These laptops are supposed to have keyboard backlight which is automatically adjusted by a light sensor. Does it work?

Yep it works perfectly. In Windows you can enable and disable the backlight, but in Ubuntu the sensors works and the keyboard is light when it gets dark, and the backlight stops when you are not using the keyboard for a while.

---

### Post by tobik on 2011-10-30
> **lvanderree said:**
> It depends on the amount of tricks you apply, because currently out of the box the energy consumption is definitely not optimal yet.

In Windows I guess you can get around 6-7 hours.
On Ubuntu probably around 4-5hours, but I didn't apply all tricks yet.


4-5 hours is really not bad. Few people in this thread mention 6-7 hours but with the extra battery which means only about 3 hrs with the built-in one and that's not much considering that with Windows you can get up to 6-7 hrs... I know that power management in Linux isn't perfect so if you're right I'd be really happy :)

And thanks for the other answers too.

---

### Post by clemmy on 2011-11-02
Reagarding the script that I posted some time ago, to enable powersaving fetures when on AC mode, I've found a bug: I was not able to use the sdcard reader when on battery! It's solved in the new version I'm posting now.

Regarding the inability to use usb mouse mentioned by opodaniel, I don't have such a problem. But this new version should solve it anyway for those who have it.

I've also included the reduction of display backlight, since the new gnome3 does not do this automatically. (If you don't like it, just remove the line)

New version:
```
#!/bin/sh

# Shell script to reduce energy consumption when running battery. Place
# it in /etc/pm/power.d/ and give execution rights.

# This is a modified version of an original script of by Skumpic,
# available here: http://blog.liberailvoip.it/2010/04/27/
# ubuntu-lucid-lynx-acer-aspire-one-impostazioni-ottimizzate-
# autonomia-prestazioni/




# Disable Wake On Lan
ethtool -s eth0 wol d


if on_ac_power; then

# Start AC powered settings --------------------------------------------#

 
# Disable laptop mode
echo 0 > /proc/sys/vm/laptop_mode
 
# Set SATA channel: max performance
for foo in /sys/class/scsi_host/host*/link_power_management_policy;
do echo max_performance > $foo;
done
 
# Set Max Power for wifi interface
# change value according to your hardware!
iwconfig wlan0 txpower 14    
 
# Disable wifi power saving
iwconfig wlan0 power off
 
# CPU Governor: Performance
for foo in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor;
do echo performance > $foo;
done 

# Disabile USB autosuspend
for foo in /sys/bus/usb/devices/*/power/control;
do echo on > $foo;
done

# Disable PCI autosuspend
for foo in /sys/bus/pci/devices/*/power/control;
do echo on > $foo;
done
 
# Disabile audio_card power saving
echo 0 > /sys/module/snd_hda_intel/parameters/power_save_controller
echo 0 > /sys/module/snd_hda_intel/parameters/power_save

# Set maximum display backlight
echo 15 > /sys/class/backlight/acpi_video0/brightness
 
# End AC powered settings ----------------------------------------------#





else






# Start battery powered settings ---------------------------------------#
 
# Enable Laptop-Mode disk writing
echo 5 > /proc/sys/vm/laptop_mode
 
# Set SATA channel to power saving
for foo in /sys/class/scsi_host/host*/link_power_management_policy;
do echo min_power > $foo;
done
 
# Activate wifi power saving
iwconfig wlan0 power timeout 500ms
 
# Reduce wifi txpower
iwconfig wlan0 txpower 5
 
# Select Ondemand CPU Governor
for foo in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor;
do echo ondemand > $foo;
done
 
# Activate USB autosuspend
echo auto > /sys/bus/usb/devices/1-1.1/power/control # Fingerprint sensor
echo auto > /sys/bus/usb/devices/1-1.3/power/control # Webcam

# Activate PCI autosuspend
for foo in /sys/bus/pci/devices/*/power/control;
do echo auto > $foo;
done
 
# Activate audio card power saving
# (sounds shorter than 5 seconds will not be played)
echo 5 > /sys/module/snd_hda_intel/parameters/power_save
echo 1 > /sys/module/snd_hda_intel/parameters/power_save_controller

# Set medium display backlight
echo 5 > /sys/class/backlight/acpi_video0/brightness
 
 
# End battery powered settings -----------------------------------------#




 
fi
```

---

### Post by clemmy on 2011-11-02
> **tobik said:**
> Hi, I'm thinking of buying this laptop. I went through the thread but there are three things I'd like to make more specific.

(1) How long can the laptop go with only _one_ battery? Let say doing some basic work with a powersaving profile and lowered brightness?

(2) Does the Intel card support hw accelerated desktop? Like Unity/Kwin/Compiz? With some decent performance?

(3) These laptops are supposed to have keyboard backlight which is automatically adjusted by a light sensor. Does it work?
I confirm what already written:
1) 4-5 hours.
2) Yes, perfectly.
3) Yes. As far as I'm concerned there it's not possible to control it (eg: modify the ambient light level at which keyboard backlight is activated, nor disable it completely) but it works perfectly

---

### Post by clemmy on 2011-11-02
> **opodaniel said:**
> This is not working for me, got this errors :

According to your xinput --list our touchpad are reported to be different, mine is  AlpsPS/2 ALPS **DualPoint** TouchPad, while yours is AlpsPS/2 ALPS **GlidePoint**.

Maybe we have different hardware? Or maybe you are not using the modified version of the psmouse module form [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625/comments/492")?

If you go into System Settings -> Mouse, do you see the touchpad tab? Or you see just the mouse tab?

---

### Post by hartillo on 2011-11-08
Hello,
I have received my new laptop vaio s serie. I have used your messages to
improve the use of Ubuntu, I have blacklist the radeon, improve the touchpad.
 Thank you all :D.
But I can not add the kernel option 
i915.i915_enable_rc6=1
When I add this option in the /etc/default/grub
after reboot the system gives a black screen. I have to boot in secure mode to delete the option.
The answer to
grep rate /proc/acpi/battery/BAT1/state
is
present rate:            37 mW
I think it may be better.
Any help, please :confused:

---

### Post by swaprava on 2011-11-10
> **lvanderree said:**
> I did some more research and wrote some small scripts to automatically disable the radeon after booting and resuming from standby/hibernation.

As mentioned in the previous post, I blacklisted the radeon module and have compiled the acpi_call module from [http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/) 

To automatically deactivate the radeon card, I have done the following:

**install the acpi_call module**
```

sudo cp acpi_call.ko /lib/modules/`uname -r`/kernel/
sudo depmod

```To test if the module will work correctly, call
```

sudo modprobe acpi_call

```Which should give no errors

if it works, add acpi_call to /etc/modules
```

sudo gedit /etc/modules

```I've added a line after lp

**create a script to perform the acpi call**
```

sudo gedit /usr/local/bin/radeon_off_sony_sa.sh

```And add the following 
```

#!/bin/sh

echo "\_SB.PCI0.PEG0.PEGP._OFF" > /proc/acpi/call
```Then make it executable and test if it works:
```

chmod 755 /usr/local/bin/radeon_off_sony_sa.sh

/usr/local/bin/radeon_off_sony_sa.sh
cat /proc/acpi/call

```The cat should return:
0x0


**automatically run the script during booting**
Once the script is working, this is easy. Add the script to /etc/rc.local before exit 0

```

sudo gedit /etc/rc.local

```and add (before the exit line):
```

/usr/local/bin/radeon_off_sony_sa.sh

```
**automatically re-deactivate the radeon after standby/hibernation**
```

sudo gedit /etc/pm/sleep.d/10_disable_radeon

```
and add the following code to it:
```

#!/bin/sh

# Action script ensures that discrete graphics card is disabled after  
# resuming from standby/hybernate
#
#

PATH=/usr/local/bin:/bin

case "${1}" in
        resume|thaw)
                radeon_off_sony_sa.sh
                ;;
esac

```And that is it! Now the Radeon will be disabled at all time, saving you from some heat, and more important some battery draining!


The only I would like to have improved now is the touchpad. Make it detect my hand palms and enable two finger scrolling.

the following part of the code requires sudo privilege:

 ```

chmod 755 /usr/local/bin/radeon_off_sony_sa.sh

/usr/local/bin/radeon_off_sony_sa.sh
cat /proc/acpi/call

```

Since while running the script, it bumped an error:
```
/usr/local/bin/radeon_off_sony_sa.sh: 3: cannot create /proc/acpi/call: Permission denied
```

I'm not sure putting these lines in the rc.local will execute at all, or does rc.local is automatically run as root?

---

### Post by clemmy on 2011-11-10
> **swaprava said:**
> [...] or does rc.local is automatically run as root?
rc.local automatically run as root, so no need to 'sudo' there. ;)

---

### Post by Aksoy on 2011-11-10
Hey everyone. I've just bought a VPCSB and I've fixed almost all issues from this thread. But the video performance is not good at all. Compiz is incredibly smooth but the video is choppy. And if I fix the choppiness (not 100% but ok), there is another problem where the video doesn't play smoothly. This is really bothering me. I was wondering if anyone has solved this issue. Thanks in advance.

---

### Post by lvanderree on 2011-11-11
> **Aksoy said:**
> Compiz is incredibly smooth but the video is choppy.

Do you maybe have installed Jupiter and set its Performance mode to power saving? When you set it to on-demand (high performance) you will probably see it will be all smooth again...

---

### Post by Aksoy on 2011-11-11
Nope. That wasn't it. I hadn't installed the xorg from the repository before. After adding the repo and updating the system, things got better. Even though the video playback is satisfying enough, it is not as smooth as it's supposed to be. I believe the smoothness gets better after following the instructions from [this]("http://ubuntuforums.org/showpost.php?p=11401854&postcount=13") thread. I was just wondering if anyone had been able to improve the video playback smoothness by making any changes in the Compiz Config Settings Manager or anywhere else for that matter. Any help would be appreciated.

---

### Post by vincenzoml on 2011-11-15
So concluding, it seems to me that all the problems of the Vaio S series can be solved except that one has to use stamina. 

Three more questions after reading the *whole* thread :) 

1) Do videos play smoothly? Especially full-screen hd flash movies, e.g. megavideo or youtube with HD? 

2) Did any of you try bumblebee (the forked version)? Does it work well?

3) Is it a good linux machine? Would you advice it to other linux users?

Thanks a lot; I'll probably place an order by tomorrow!

---

### Post by lvanderree on 2011-11-18
> **vincenzoml said:**
> So concluding, it seems to me that all the problems of the Vaio S series can be solved except that one has to use stamina. 

Three more questions after reading the *whole* thread :) 

1) Do videos play smoothly? Especially full-screen hd flash movies, e.g. megavideo or youtube with HD? 



jep, no problems there.


> **vincenzoml said:**
> 
2) Did any of you try bumblebee (the forked version)? Does it work well?



I didn't know about bumblebee, but from what I have found it is:

1. for Nvidia cards (the sony has an Radeon)
2. is forked to another transformer-name
3. It uses the acpi_call script we already described in this thread

So in short, no, haven't checked it, don't know if it does work, but you don't need it.

> **vincenzoml said:**
> 

3) Is it a good linux machine? Would you advice it to other linux users?

Thanks a lot; I'll probably place an order by tomorrow!

I don't think it is the best linux machine, although all is looking pretty well:

- The touchpad driver could be better (although in Windows it wasn't that good either). Luckily they are working on it!
- The powerconsumption still feels a little too high. However this might be an Ubuntu issue, instead of a Vaio-Linux issue...


Currently I am (again) running Mint. This time however version 12RC (Lisa) which suits me really well.


My power consumption currently is around 
12W !

or 
```

grep rate /proc/acpi/battery/BAT1/state
present rate:            12183 mW

```

---

### Post by lvanderree on 2011-11-18
> **hartillo said:**
> Hello,
I have received my new laptop vaio s serie. I have used your messages to
improve the use of Ubuntu, I have blacklist the radeon, improve the touchpad.
 Thank you all :D.
But I can not add the kernel option 
i915.i915_enable_rc6=1
When I add this option in the /etc/default/grub
after reboot the system gives a black screen. I have to boot in secure mode to delete the option.


strange it is working for me, I have got:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=\"force\" i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1"

```
in  /etc/default/grub

(don't forget to run sudo update-grub afterwards)

> **hartillo said:**
> 

The answer to
grep rate /proc/acpi/battery/BAT1/state
is
present rate:            37 mW
I think it may be better.
Any help, please :confused:


Your rate is nearly 0! This probably means you are asking how much power your battery provides, while you got your power-adapter connected, and the battery is completely charged ;)

try calling it again a couple of times, after you disconnected your powercable (and wait for some seconds)

---

### Post by hartillo on 2011-11-21
> **lvanderree said:**
> strange it is working for me, I have got:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=\"force\" i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1"

```in  /etc/default/grub

(don't forget to run sudo update-grub afterwards)




Your rate is nearly 0! This probably means you are asking how much power your battery provides, while you got your power-adapter connected, and the battery is completely charged ;)

try calling it again a couple of times, after you disconnected your powercable (and wait for some seconds)

Thank you for the answer :D, I have changed the /etc/default/grub and I restart without problem but now the fan is always running, and 
grep rate /proc/acpi/battery/BAT1/state
returns (without the power adapter :
present rate:            26911 mW
It may have be any relation with new kernel?

---

### Post by lvanderree on 2011-11-21
I could really recommend Linux Mint, instead of Ubuntu.

It uses much less power, while applying the same tricks and more importantly: the power remains low, even after resuming from standby (something I couldn't fix in Ubuntu).

So give Mint it a try, Ubuntu unfortunately failed this time.

---

### Post by unixlike on 2011-11-24
Hi,
how fan and temperature are working with mint?
Are you using mint 11 or mint with debian?

---

### Post by lvanderree on 2011-11-24
```
leon@VPCSA2C5E ~ $ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +52.0°C  (crit = +97.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +53.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +53.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +52.0°C  (high = +86.0°C, crit = +100.0°C)
```

I don't hear the fan...

while working:
 - external-monitor
 - external wireless mouse
 - many (15+) chrome tabs open, 
 - thunderbird
 - netbeans
 - spotify

Is that a good indication ;-)

---

### Post by unixlike on 2011-11-24
Ok, now I will download it.
Which of these? Linux Mint 11 Katya or Linux Mint Debian?

Can you post the main steps you have done to configure all the necessary? (When you have time)

Thank you so much!

---

### Post by lvanderree on 2011-11-24
Ah sorry, forgot to mention.

I run Mint 12(RC) 64bit.
[http://blog.linuxmint.com/?p=1858](http://blog.linuxmint.com/?p=1858)

after starting the live cd (from USB) I first run an update (sudo apt-get update/dist-upgrade) then start the installer.

After that I simply install acpi-call, the intel-settings in grub, Jupiter and the touchpad driver. All as described in this thread.

---

### Post by unixlike on 2011-11-24
fantastic :) it's based on oneric but as you say works better!
I am downloading the iso, I will install and I will inform you!

thanks

---

### Post by unixlike on 2011-11-25
> **lvanderree said:**
> Ah sorry, forgot to mention.

I run Mint 12(RC) 64bit.
[http://blog.linuxmint.com/?p=1858](http://blog.linuxmint.com/?p=1858)

after starting the live cd (from USB) I first run an update (sudo apt-get update/dist-upgrade) then start the installer.

After that I simply install acpi-call, the intel-settings in grub, Jupiter and the touchpad driver. All as described in this thread.

Is this guide correct for installing acpi-call? [http://hybrid-graphics-linux.tuxfamily.org/index.php?title=Acpi_call](http://hybrid-graphics-linux.tuxfamily.org/index.php?title=Acpi_call)

Can you post me your intel-settings in grub?

What of these Jupiter version you are using? [http://sourceforge.net/projects/jupiter/files/](http://sourceforge.net/projects/jupiter/files/)

Thank you so much!

---

### Post by Aksoy on 2011-11-26
> **lvanderree said:**
> 

After that I simply install acpi-call, the intel-settings in grub, Jupiter and the touchpad driver. All as described in this thread.

Actually I would like to know what you mean by the intel-settings. I've done all the other things you've mentioned with the help of this thread. But I don't recall anything about the intel-settings. Can you explain and if you have the time post what to do in order to perform those settings. And in the below, there are all the configurations that I've performed after installing Ubuntu 11.10. I will try them again with Mint. Can you tell me what is missing or what is redundant. Thanks.

----------------------------------------------------------
sudo nano /etc/modprobe.d/blacklist.conf

add the following at the end of the file

	blacklist radeon
-------------
sudo nano /etc/modprobe.d/options

add the following to the file

	options psmouse proto=imps
-------------
sudo nano /etc/modprobe.d/i915.conf

add the following to the file

	options i915 i915_enable_rc6=1
-------------
sudo apt-get install git
git clone [https://github.com/mkottman/acpi_call.git](https://github.com/mkottman/acpi_call.git)
cd acpi_call
make
sudo insmod acpi_call.ko
lspci -vnnn | grep VGA
sudo chmod +x test_off.sh
./test_off.sh
sudo cp acpi_call.ko /lib/modules/`uname -r`/kernel/
sudo depmod
sudo modprobe acpi_call
-------------
sudo nano /etc/modules

add the following after 'lp'

	acpi_call
-------------
sudo nano /usr/local/bin/radeon_off_sony_sa.sh

add the following to the file

	#!/bin/sh

	echo "\_SB.PCI0.PEG0.PEGP._OFF" > /proc/acpi/call
-------------
sudo chmod +x /usr/local/bin/radeon_off_sony_sa.sh
sudo /usr/local/bin/radeon_off_sony_sa.sh
sudo cat /proc/acpi/call
-------------
sudo nano /etc/rc.local

add the following before 'exit 0'

	/usr/local/bin/radeon_off_sony_sa.sh
	rfkill block bluetooth
-------------
sudo nano /etc/pm/sleep.d/10_disable_radeon

add the following to the file

	#!/bin/sh

	# Action script ensures that discrete graphics card is disabled after  
	# resuming from standby/hybernate
	#
	#

	PATH=/usr/local/bin:/bin

	case "${1}" in
	        resume|thaw)
	                radeon_off_sony_sa.sh
	                ;;
	esac
------------------
sudo chmod +x /etc/pm/sleep.d/10_disable_radeon
------------------
sudo nano /etc/pm/power.d/wireless

add the following to the file

	#!/bin/sh
	/sbin/iwconfig wlan0 power off
------------------
sudo chmod +x /etc/pm/power.d/wireless
----------------------------------------------------------

---

### Post by swish123 on 2011-11-26
Hi guys.

After following all the instructions on this thread, I have managed to disable the Radeon card at all times.

But when I need to, I want to be able to turn on the graphics card.

To turn it on, I tried opening terminal and typed:

```

sudo modprobe -r acpi_call

```

I didn't notice any difference.

How do I check to see if that actually turned on the card?

Thanks

---

### Post by Zweifrosch on 2012-01-01
Hi,
is there maybe a How-To or something where everything is written together?
Scrolling through the Board is a bit confusing :/

Thx in advance!

---

### Post by dmoos on 2012-01-08
Hi everybody,
im also a total newbie to linux and cannot get it running properly on my vaio (fan, battery). I tried everything from this thread with ubuntu but now I am more confused than before and would like to give it another try with mint. I would really appreciate it if one from the pros would post a up-to-date summary of all the steps so necessary so far.

thx a lot

---

### Post by mörgæs on 2012-01-08
Moved to Hardware and Laptops.

---

### Post by schaze on 2012-01-17
Hi all,

many thanks for all the great tips and know-how in this thread - it really helped me improve my just newly bought georgeus vaio se 15 laptop.

I found have one more thing which seems to make my fan run lesser/slower (at least that is what I tell myself).
I added

```
acpi_osi=Linux
```to my grub commandline arguments. You can find an explanation about the parameter here: [http://askubuntu.com/questions/28848/what-does-the-kernel-boot-parameter-set-acpi-osi-linux-do](http://askubuntu.com/questions/28848/what-does-the-kernel-boot-parameter-set-acpi-osi-linux-do)[URL="http://askubuntu.com/questions/28848/what-does-the-kernel-boot-parameter-set-acpi-osi-linux-do"]
[/URL] 
[B]
In addition I also have a [/B]**problem where I will need your help**. It seems that I cannot use the newer 3.0.0.14 or .15  kernel since with those my Laptop hangs about 1-2 minutes on boot at the /script/init-bottom step. So far I have no idea where this comes from. Do any of you experience similar issues?
I also had problems with the latest unity patches from the oeneiric-proposed repository - alt-tab killed untiy everytime. In both cases I downgraded the according packages again.

Any ideas or thoughts?

thanks a lot for your help,
schaze

---

### Post by opodaniel on 2012-01-20
Very strange, I added all this commands in /etc/rc.local
> /usr/local/bin/radeon_off_sony_sa.sh
/# Disable discrete graphics at startup
chown -R $USER:$USER /sys/kernel/debug
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
echo '_SB.PCI0.PEG0.PEGP._OFF' > /proc/acpi/call
but when I log in ( Xubuntu  XFCE Session) the temperature of the CPU reach 70C. Then I login terminal and execute the same commands and the cpu temp goes down to 52C.  Why those commands are not executed while loaded in rc.local?

If anyone have all the workaround's organized, can he/she make a post or a blog post with this and put a link here?
Also why some take the acpi_call approach and others the vgaswitcheroo approach?

Linux kernel 3.3 is said to fix the power-regression problem : [http://ubuntuforums.org/showthread.php?p=11620746](http://ubuntuforums.org/showthread.php?p=11620746)

---

### Post by mjoshawa on 2012-01-28
I'm trying to install acpi_call on a new Mint KDE 12 install and am having some trouble.  I've used the following commands and get the error shown below.  
```
sudo apt-get install git
# type password

git clone http://github.com/mkottman/acpi_call.git
cd acpi_call
make
```After attempting make I get this message:
```
make -C /lib/modules/3.0.0-15-generic/build M=/home/josh/acpi_call modules
make: *** /lib/modules/3.0.0-15-generic/build: No such file or directory.  Stop.
make: *** [default] Error 2

```I tried just making the directory myself, but then I get this:
```
make -C /lib/modules/3.0.0-15-generic/build M=/home/josh/acpi_call modules
make[1]: Entering directory `/lib/modules/3.0.0-15-generic/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/3.0.0-15-generic/build'
make: *** [default] Error 2

```I'm not sure what this means or how to fix it.  Any help would be really great.
Thank you,
Josh

---

### Post by lvanderree on 2012-01-30
Have you installed your linux-headers?

sudo apt-get install linux-headers-generic

---

### Post by Aksoy on 2012-01-31
Hey guys. 

I've almost solved all the issues thanks to this form but there is only one more problem left which is kinda driving me crazy. Sometimes parts of the screen goes black (link for the screenshot is below). I switch to another window, then it goes away. But when I come back to the window that I had this problem with, it comes back again. When I close that window some other parts of the screen goes black. I don't really know what is wrong but if anyone else had come across with this problem and found a solution, please let me know.

Thanks.

Screenshot
[http://imageshack.us/photo/my-images/708/scrx.png/](http://imageshack.us/photo/my-images/708/scrx.png/)

---

### Post by mjoshawa on 2012-02-03
Thank you for the help.  Acpi_call and the scripts you created (Thank you very much) now seem to be working well.  With the brightness all the way down power management is reporting about 2 1/2 to 3 hours of life with one battery at 80% charge. (Mint 12 KDE)

I don't know if this question belongs here or not, but I'll give it a try:  My school's wireless network is unsecured, but requires a log in within the web browser.  I've registered my MAC address (from Windows) so that I no longer have to log in.  For some reason in Linux I can connect to the network, but am unable to connect to any websites.  Any advise?

Thank you again for the help,
Josh

---

### Post by primetomas on 2012-02-11
Thanks to the posts in this forum I decided to buy a new Vaio SE15 (VPCSE1V9E).

I installed Ubuntu 12.04 Alpha2 without problems, and followed the forum posts to lower power consumption to decent levels.

Since it's getting quite spread out, and some people asked about it above, I have distilled all the settings I have made in a blog article.

[Check my summary here.]("http://blog.ejbca.org/2012/02/ubuntu-gnulinux-1204-precise-on-sony.html") (at [http://blog.ejbca.org](http://blog.ejbca.org))

If anyone think I missed something, please let me know. 

Cheers,
Tomas

---

### Post by primetomas on 2012-02-12
After some more experimentation I have updated my findings. there are really only very few things you need to do, at least on Ubuntu 12.04.

Blacklisting the radeon driver does not do anything, so you can skip that.

Vgaswitcheroo is preferred before acpi_call to power of the radeon card. acpi_call causes resume (from suspend) to take a long time, it pauses with black screen for a while, but with vgaswitcheroo it is instant.
Vgaswitcheroo works out of the box with Ubuntu 12.04 so it's trivial to use.

Read my [updated summary of this forum thread]("http://blog.ejbca.org/2012/02/ubuntu-gnulinux-1204-precise-on-sony.html").

Cheers,
Tomas

---

### Post by primetomas on 2012-02-12
I am looking at the ASPM power savings, but they don't seem to work on the Vaio SE (VPCSE1v9E).

I have added pcie_aspm=force to kernel parameters, and the kernel acknowledges this.
"PCIe ASPM is forcibly enabled"

But then it disables it with the message:
"ACPI _OSC control for PCIe not granted, disabling ASPM".

Is this a kernel or a bios issue? Any ideas?

This might be the last powersave item that would bring us closer to windows battery performance?

Cheers,
Tomas

---

### Post by opodaniel on 2012-02-12
On kernel 3.0.0-15 the acpi_osi=Linux option in grub has no effect, the ventilator is quite noisy :(.

---

### Post by plech.d on 2012-02-24
Hi,
one quick question - why exactly do you disable bluetooth at boot?

Thank you.

> **primetomas said:**
> After some more experimentation I have updated my findings. there are really only very few things you need to do, at least on Ubuntu 12.04.

Blacklisting the radeon driver does not do anything, so you can skip that.

Vgaswitcheroo is preferred before acpi_call to power of the radeon card. acpi_call causes resume (from suspend) to take a long time, it pauses with black screen for a while, but with vgaswitcheroo it is instant.
Vgaswitcheroo works out of the box with Ubuntu 12.04 so it's trivial to use.

Read my [updated summary of this forum thread]("http://blog.ejbca.org/2012/02/ubuntu-gnulinux-1204-precise-on-sony.html").

Cheers,
Tomas

---

### Post by primetomas on 2012-02-26
Because it is turned on by ddefault when booting the machine. Since it will drain some power, and I never use bluetooth, I prefer to have it disabled by default.

---

### Post by bvandev on 2012-03-11
For the record, I upgraded by Sony VPCSC to 12.04 this morning and made the changes Primetomas recommended.  (Thanks for the blog post.)  

I had been using the ACPI script to handle power consumption, but figured I'd go with vgaswitcheroo since it was installed by default.  I need to recompile the ACPI script with each new kernel revision.  

With vgaswitcheroo in place, my power consumption sat at about 15.  I disabled it and went back to ACPI.  With that in place my power consumption dropped to about 12.

---

### Post by bvandev on 2012-03-12
Correction:  Further research determined that vga_switcheroo was not activated by default when I updated from 11.10.  Maybe that only happens with a clean install?  I tested by running off a live-cd and vga_switcheroo was indeed active and working.  Power dropped to about 11 when I turned it on.  

So, at some point, I'll do a clean install and move off of acpi.

---

### Post by siersmak on 2012-03-22
Hello,

I'm a little surprised to not see a lot of discussion in this thread about disabling the touchpad while typing.  Maybe I'm the only one having trouble getting this to work?  I'm running Ubuntu 11.10 on a VPC SA and the touchpad is being identified as ImPS/2 Generic Wheel Mouse.  As such, I do not have a Touchpad tab in my Gnome mouse settings, and I believe synclient won't work either although I haven't tried it.  Maybe I'm wrong... I'm currently using xinput to disable the touchpad while a USB mouse is attached, but that's a temporary workaround.

Any ideas?

---

### Post by primetomas on 2012-03-22
No problems at all on my VPC SE using Ubuntu 12.04 beta. Two finger scrolling works great.

---

### Post by Startacus on 2012-03-22
I'm having a hell of a time with my VPCSC. I fought for two days to get Catalyst to work and I finally did. However, I was still having issues with overheating and I reboot my machine and now I can't even boot into Ubuntu. This is incredibly frusturating.

---

### Post by siersmak on 2012-03-22
Primetomas, that's encouraging, I'm glad to hear that.  It's a production machine so I'm not willing to put a beta version on there, but I look forward to April 29th when I can get the final 12.04 release.  

Is the touchpad correctly identified?  I honestly don't even know what kind of touchpad my laptop has since Ubuntu can't recognize it.  You didn't mention disabling while typing, so does that mean you don't have a problem with the touchpad throwing your cursor around the screen when you are typing?

---

### Post by madmack on 2012-03-22
> **siersmak said:**
> Primetomas, that's encouraging, I'm glad to hear that.  It's a production machine so I'm not willing to put a beta version on there, but I look forward to April 29th when I can get the final 12.04 release.  

Is the touchpad correctly identified?  I honestly don't even know what kind of touchpad my laptop has since Ubuntu can't recognize it.  You didn't mention disabling while typing, so does that mean you don't have a problem with the touchpad throwing your cursor around the screen when you are typing?

I use this to disable my touchpad: [http://code.google.com/p/vaio-f11-linux/](http://code.google.com/p/vaio-f11-linux/)

I baked the patch into my kernel and used the little tool called vaio control center to disable the touchpad completely when I want to. It does the job. 

I also have set it to disable the touchpad automatically when I use the keyboard (and re-enable it after 2 sec of idling) but I can't remember what I did exactly to achieve that.

---

### Post by plech.d on 2012-03-28
There is actually no need to upgrade to 12.04, all you need to do is update your kernel on 11.10 to version 3.2. There, the touchpad is correctly recognized, supports all types of scrolling and can be disabled using various widgets.

Has anyone been able to get the fan noise down to at least as little as Windows makes? Ubuntu still makes my fan spin a lot more, even with vgaswitcheroo correctly in place and Jupiter taking care of power managment. I'm using both Windows and Ubuntu in dual boot and the difference is very noticable.

It's actually not the problem that the fan would be spinning without need. It's supposed to be spinning, because the computer is truly heating up. But why is it heating up?

Thanks, D.

---

### Post by siersmak on 2012-03-28
Hi plech.d, 

well, I tried that already.  I compiled kernels 3.2 and 3.3 but still had the same touchpad detection issues.  So I'm guessing upgrading to 12.04 won't help this issue anyway.  I've been testing the scripts at [http://ubuntuforums.org/showpost.php?p=10869949&postcount=8](http://ubuntuforums.org/showpost.php?p=10869949&postcount=8) and have been meeting some success so I'll probably go that route.

siersmak

---

### Post by opodaniel on 2012-03-30
After upgrading to 3.0.0-17 I got wifi problem - no more wifi , does any-one have this problem  or solution to it?

Found a solution to have ATI and Intel Graphic cards:
[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)
```
#aticonfig --pxl 
#PowerXpress: Integrated GPU is active (Power-Saving mode).
```

Baterry is reporting 3.38 hours of autonomy.

---

### Post by binnisb on 2012-04-21
Tanks all for this excelent post!

> **primetomas said:**
> After some more experimentation I have updated my findings. there are really only very few things you need to do, at least on Ubuntu 12.04.


I just installed Kubuntu 12.04 on to my vaio SA and so far I am very happy. The touchpad works well out of the box, and I have applied the fixes fron primetomas blogpost. It works nicely except that the radeon seems to turn it self on again after resuming from sleep and hibernation.

I added this line at the bottom of /etc/modprobe.d/blacklist.confg:

```
blacklist radeon
```

I have added this to grub and updated grub:
```
GRUB_CMDLINE_LINUX_DEFAULT="quite splash i915.i915_enable_fbc=1 i915.i915_enable_rc6=1 pcie_aspm=force"
sudo update-grub
```

I added thi to /etc/rc.local:
```
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```

I skipped the bluetooth since I use that regularely.

I added the file /etc/pm/sleep.d/10_disable_radeon and it contains:
```
#!/bin/sh
# Action script ensures that discrete graphics card is disabled after
# resuming from standby/hibernate
#
#
case "${1}" in
resume|thaw)
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
;;
esac

```
and added the x permition so its like this now:
```
-rwxr-xr-x 1 root root  213 Apr 21 03:30 10_disable_radeon

```

Then I did:
```
sudo apt-get install ethtool
sudo vi /etc/pm/power.d/powersavings
```

And pasted the code from the blogpost and gave it x permition.

And I did:
```
sudo vi /etc/polkit-1/localauthority/50-local.d/com.ubuntu.desktop.pkla

```
And created the file with this.
```

[Re-enable hibernate by default]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes
```

Am I missing something? Why is radeon reactivating on resuming from sleep / hibernation?

The power is around 10W when computer is idle / little load after reboot. It goes to around 18W idle /little load after resuming from sleep.

Like I say, I'm loving KUbuntu on this machine :) so now it's just figuring this sleep problem out.

Thanks in advance.

---

### Post by binnisb on 2012-04-21
> **binnisb said:**
> 
I just installed Kubuntu 12.04 on to my vaio SA and so far I am very happy. The touchpad works well out of the box, and I have applied the fixes fron primetomas blogpost. It works nicely except that the radeon seems to turn it self on again after resuming from sleep and hibernation.


It is always nice when you can answer your own problems :)

The script running when resuming from sleep did not quite work. Reading the Fedora post about the same problem gave me that sometimes the switch file indicates that the radeon is off even if it is running.

The solution is having these two lines in the /etc/pm/sleep.d/10_disable_radeon file:

```
echo ON > /sys/kernel/debug/vgaswitcheroo/switch
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```

Not just the OFF line.

Hope someone benefits from this :)

EDIT: how low do you get the Watts ? And how low do you get the temperature?

I seem to go to 10-12W and temp 51°C idle

---

### Post by rich-brun on 2012-04-24
I've got a VPCSA running 12.04. I installed the Catalysis driver, and this allows me to switch between the Intel and Radeon graphics cards, which is handy in the Radeon runs far too hot (it really cannot be good for the laptop). However I cannot get the Intel HD 3000 to run with 3D hardware acceleration, so I cannot run standand Unity or Darktable.

The Touchpad is seen a PS2 mouse, and therefore I cannot access the options to disable the touchpad whilst typing so I keep clicking whilst typing. I've tried psmouse-alps-dkms without any joy, including [http://ubuntuforums.org/archive/index.php/t-1887683.html]("http://ubuntuforums.org/archive/index.php/t-1887683.html"). This had lead to me nearly posting passwords on the internet! :-p

I've played around with installing new kernels in the hope of solving either of the above issues without any joy (I cannot get lightdm to run with the newer kernels).

Slightly less importantly, the Ethernet port seems to be running at 500Mbps and not the 1000Mbps I was expecting (as tested using iperf and compared with my other gigabit hardware). 

Very frustrating as I very nearly have the perfect Ubuntu laptop.

---

### Post by koenigjm on 2012-04-27
Hey everyone.

In case others run into missing opengl drivers on 12.04 (probably due to trying to install AMD drivers via "Additional Drivers", which currently fails) you can restore the open source intel drivers by follwing the recommended instructions here:

[http://nerdysermons.blogspot.com/2011/11/solve-graphic-driver-errors-unity-3d.html]("http://nerdysermons.blogspot.com/2011/11/solve-graphic-driver-errors-unity-3d.html")

---

### Post by rich-brun on 2012-04-29
If anyone else is trying to get GLX rendering working with the Intel graphics card, there's an excellent guide here...

[http://ubuntuforums.org/showpost.php?p=11819555&postcount=107]("http://ubuntuforums.org/showpost.php?p=11819555&postcount=107")

---

### Post by opodaniel on 2012-04-29
Finally the touchpad can be control from the settings > settings manager> mouse and touchpad. You can disable -it or you can enabled ( disabled by default ) the option to disable touchpad when typing from the Touchpad tab, it finally work out of the box :KS
This is on XFCE4 :D, don't know for others.

---

### Post by Izy on 2012-05-03
Hey did you have some experiences with this Vaio control center under 12.04? I Can run the center but all options are gray and I cant make it work. [http://code.google.com/p/vaio-f11-linux/wiki/VaioControlCenter](http://code.google.com/p/vaio-f11-linux/wiki/VaioControlCenter)

---

### Post by madmack on 2012-05-03
> **Izy said:**
> Hey did you have some experiences with this Vaio control center under 12.04? I Can run the center but all options are gray and I cant make it work. [http://code.google.com/p/vaio-f11-linux/wiki/VaioControlCenter](http://code.google.com/p/vaio-f11-linux/wiki/VaioControlCenter)

you'll need to patch the kernel yourself (or rebuild the modules):

[http://code.google.com/p/vaio-f11-linux/wiki/KernelSupport](http://code.google.com/p/vaio-f11-linux/wiki/KernelSupport)

use the patch from here:

[http://www.absence.it/vaio-acpi/source/patches/](http://www.absence.it/vaio-acpi/source/patches/)

I use this tool to disable the backlights on the keyboard.

---

### Post by IceBlurr on 2012-05-18
Hello,

I am new at installing Linux (only used it on a VM) and I'd like to have a dual boot on my Sony VAIO S.
It has a SSD 128 Go from Sony, so no RAID0 I suppose, and I'd like to put the Ubuntu partition in place of the recovery partition.

Do you have any idea of how i shoud part that partition ? 
Also, where do i put the grub thing ? 

Maybe someone could do a complete tutorial for dual boot? :)
Thank you very much !

---

### Post by mjoshawa on 2012-06-18
I'm in the process of building up a system from a minimal debian/xfce4 install.  The only real problem I have (at the moment) is the touchpad isn't fully recognized.  It's recognized as an Alps touchpad in the mouse settings and two finger scrolling works, but there are no touchpad specific settings available.  For example, tap to click is not enabled and there is no option to enable it.

If anyone has any ideas to fix this or maybe a package I might be missing, I would appreciate the help.

Thank you.

---

### Post by tr3nton on 2012-06-26
Thought i'd come and mention my findings.

I have the vpcsb17gg model, and currently running 12.04

I did the method of switcheroo, by adding the OFF switch in /etc/rc.local.

I didn't blacklist the radeon module, as it seemed to have no effect.

I find after boot, the power hovers around 10-11 watts - which is decent. The annoying thing is after resuming from suspend, the power consumption seems to go back up to 15-20 watts. Not really sure why this is? looking at the switcheroo switch file, the discrete graphics is still being reported as Off.

I tried using the startup script as described here, instead of rc.local, but it didnt seem to work for me after a few attempts, so i got over that idea. [https://help.ubuntu.com/community/HybridGraphics#Script_for_use_during_bootup](https://help.ubuntu.com/community/HybridGraphics#Script_for_use_during_bootup)

I may test a couple more things:

* Power saving script - Post 149
* Disable bluetooth
* Try using the acpi method instead of switcheroo

---

### Post by tr3nton on 2012-06-26
Thought i'd report by experience re: battery.

I am currently using the switcheroo method to disable the discrete gpu, by adding the off switch into /etc/rc.local. I didnt bother blacklisting, as it didnt seem to have any effect

On a fresh boot, power hovers around 10-11 Watts. However, after resuming from a suspend, it goes back up to 15-20 Watts. Not sure why this is, as the discrete gpu is still reported as Off when inspecting the switch file.

I test test the startup script described here, [https://help.ubuntu.com/community/HybridGraphics#Script_for_use_during_bootup](https://help.ubuntu.com/community/HybridGraphics#Script_for_use_during_bootup) , but the discrete gpu was still on, so i gave up on that after trying a few different things, and just stuck with rc.local.

I may need to test a few more suggestions to see if there is any change:

* Power saving script - Post 149... *Done. No real change*
* Disable bluetooth - Post 119 (I doubt this would have much effect, but I really don't use bluetooth, so might as well)
* Using the acpi method - Post 109
* Review summary by primetomas - Post 181

---

### Post by lvanderree on 2012-06-27
At the moment switcheroo is het best solution.

The solution is to enable the radeon again before going to standby, and then resume again, when awakening from standby. If you don't enable the radeon before going to standby, resuming will introduce a 5-10s hang. If you don't enable & re-disable the radeon, it will report to be off, but will consume power.


See: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/859171](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/859171) 
and: [http://pastie.org/4080789](http://pastie.org/4080789)

---

### Post by tr3nton on 2012-06-27
> **lvanderree said:**
> At the moment switcheroo is het best solution.

The solution is to enable the radeon again before going to standby, and then resume again, when awakening from standby. If you don't enable the radeon before going to standby, resuming will introduce a 5-10s hang. If you don't enable & re-disable the radeon, it will report to be off, but will consume power.


See: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/859171](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/859171) 
and: [http://pastie.org/4080789](http://pastie.org/4080789)

Awesome! Let's see how that goes!

---

### Post by jdc on 2012-07-03
Does anyone know how the new 2012 Sony S 15 compares to the 2011 model when it comes to installing Ubuntu?  Are there any success stories?  I'm quite experienced with linux installs, but don't want to attempt something that's impossible...

---

### Post by jdc on 2012-07-04
I should mention that the new Viao S 15 has (optional) NVidia discrete graphics instead of the ATI graphics.  If I configure it with only the integrated Intel graphics, that should avoid many of the problems in this thread.  But would I be missing out on future support for graphics switching?

More importantly, I'd like to see at least one success story before I try it.

---

### Post by chone on 2012-07-09
> **jdc said:**
> Does anyone know how the new 2012 Sony S 15 compares to the 2011 model when it comes to installing Ubuntu?  Are there any success stories?  I'm quite experienced with linux installs, but don't want to attempt something that's impossible...
I am also curious about this; I'm getting a 2012 Sony S 13 Premium in the mail any day now (it shipped yesterday). I will install some form of Linux on it (maybe Debian...not sure yet) and let you guys know what happens. Either way, I can try installing Ubuntu for fun, since this is an Ubuntu forum, and I have a predisposition for y'all.

I have a feeling I'll be able to get it to work, and am going to try the real, hybrid graphics stuff that people have been posting about elsewhere on these forums. I've also heard about problems with the BIOS and getting it to actually boot outside the Windows partition. I will report on all of this. Gimme a few days to get my computer and find time to install it, though.

---

### Post by Paddie on 2012-07-26
> **chone said:**
> I am also curious about this; I'm getting a 2012 Sony S 13 Premium in the mail any day now (it shipped yesterday). I will install some form of Linux on it (maybe Debian...not sure yet) and let you guys know what happens. Either way, I can try installing Ubuntu for fun, since this is an Ubuntu forum, and I have a predisposition for y'all.

I have a feeling I'll be able to get it to work, and am going to try the real, hybrid graphics stuff that people have been posting about elsewhere on these forums. I've also heard about problems with the BIOS and getting it to actually boot outside the Windows partition. I will report on all of this. Gimme a few days to get my computer and find time to install it, though.

Hi,

have you tried to install Ubuntu (or an other Distri) on the Sony Vaio?

I´m in to order a Sony Vaio 13" with i5 an big Batterie in the next Days. I don´t need the Nvidia Card, so if i can use it with the intel all the time I´m fine (Batterielife is more important than Graphics-Power ;-).

If you could write some short Impressions..It would be very cool ;-)

---

### Post by Olodin on 2012-08-06
> **lvanderree said:**
> At the moment switcheroo is het best solution.

The solution is to enable the radeon again before going to standby, and  then resume again, when awakening from standby. If you don't enable the  radeon before going to standby, resuming will introduce a 5-10s hang. If  you don't enable & re-disable the radeon, it will report to be off,  but will consume power.


See: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/859171](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/859171) 
and: [http://pastie.org/4080789](http://pastie.org/4080789)

Worked well here! Saves a lot of power after resuming from standby.

And thx to all infos in this thread I managed to get my new VPC-SA3C5 up and running with Linux Mint 13 in no time!

Especially the summary in [http://blog.ejbca.org/2012/02/ubuntu-gnulinux-1204-precise-on-sony.html](http://blog.ejbca.org/2012/02/ubuntu-gnulinux-1204-precise-on-sony.html) was very helpful!

---

### Post by hteamspy on 2012-08-16
I follow that thread since the beginning as I'm the owner of a Sony VPCSB 13 with the dual video card. 

But I received today the new Sony SV15, I5 with Intel HD only. I can say that this machine is a pleasure to use, even more than the previous 13" version.

Just swapped the old disk, removed the quick boot thing, and all worked properly.

The only thing that I'll have to get used to is the touchpad, it's very sensitive.

I hope it'll help people asking about the experience.

---

### Post by mimozus on 2012-08-17
I booted 12.04 from usb thumb drive, on a display model S at Frys.  Worked great, with default intel graphics.  Of course, I don't know how well, or if, bumblebee would drive optimus nVidia.

For the most part, I prefer Sony VAIO laptops for Ubuntu, since I have had very few problems running Ubuntu on them.

Good luck.

---

### Post by shawn3 on 2012-08-19
I just grabbed a new 13.3 i5 sony s vaio with Intel HD 4000 only graphics from [here]("http://www.newegg.com/Product/Product.aspx?Item=N82E16834127673").

I installed 12.04 64 bit on it. For me, everything works well except power usage (as already mentioned on this forum) and the touchpad. I haven't tried any of the power tricks mentioned yet, because I have been preoccupied with trying to fix up the touch pad.

I touchpad "works" (with 2 finger scrolling and such), but it is physically so large that the right half of it basically becomes a palm rest for my right hand. This means that when I type, my palm is detected as 2 fingers trying to scroll and all kinds of crazy things happen. By the way, I should mention that on Windows 7 the touchpad works great -- it never jumps around from palm touches and responds immediately to finger touches even right after typing. I would love to get a little closer to that in Ubuntu.

Hopefully, this post will serve as both a document of my issue and a list of potential solutions for other folks.

The first obvious solution is the "disable the touchpad when typing" idea that is referenced all over the net. Basically, you can run something like ```
syndaemon -i 2.0 -d -t -K -R
``` which deactives the mouse when typing -- it sort-of works for me. However, I guess I tend to pause a lot as I type, so the mouse becomes reactivated often unless I set the deactivation period to a long value. But, that becomes problematic when you actually want to switch from typing to mousing. Unfortunately, not a great solution for me.

Another solution is to grab one of those touchpad/mouse system tray apps that let you enable and disable the touchpad with a shortcut key. That is a tough sell for me -- I toggle back and forth between the two operational modes for that to be a good solution.

The next solution is to enable palm detection in the synaptics xinput driver. You can do that in several ways, but to just try it out on the command line, you can enable it with ```
synclient PalmDetection=1
```. Then, you can configure the minimum palm pressure with ```
synclient PalmMinZ=10
``` where 10 is the pressure, and configure the minimum palm width with ```
synclient PalmMinWidth=5
``` where 5 is the width. You can check your handy-work with ```
synclient -l
```.

I tried the palm detection, but it had no effect. So, on a hunch, I grabbed the source for the synaptics xinput driver (i.e., the xserver-xorg-input-synaptics_1.6.2 package) and modified the palm detection code a bit. It appears that the "fingerWidth" value coming into the driver is always 0, so the palm detection (which utilizes width and pressure to detect palms) has no hope of working; unless my finger and palm pressure are fairly distinct (which was not really workable solution for me either).

My current workaround is disabling the right half of my touch pad which is not very satisfying.

So, two lines of questions.

One, does anyone know of an easy fix for this? Config tweaking, driver swap out, kernel recompile, etc?

Two, if I have to dig deeper still, can anyone give me a heads up on where I should be looking. I'm guessing that the kernel module (psmouse) is a good place to start a bisection, but I don't know how that talks to the synaptics xinput driver (and don't really want to have to learn either). Any thoughts on where to start or good docs online is always appreciated. Does the hardware even support "fingerWidth" or is Windows doing something extra smart?


Thanks.

---

### Post by Romanovzky on 2012-10-19
has anyone tried out 12.10? Any luck?

---

### Post by schaze on 2012-10-19
> **Romanovzky said:**
> has anyone tried out 12.10? Any luck?

Tried it yesterday (upgrade), but the system does not boot with the new 3.5 Kernel for me.
I am glad I kept the old Kernels so it at lest boots up with this one...

---

### Post by kubaz93 on 2012-10-19
> **Romanovzky said:**
> has anyone tried out 12.10? Any luck?

Upgrade destroyed my GPU configuration and now I'm trying all tutorials about this, but unsuccessfully I still haven't 3d support for now.

---

### Post by na01 on 2012-10-21
I've updated right now and I'm experiencing problems with power saving.
With the 12.04 the idle power consumption was around 8-10w,
now is almost always over 20W.


it seems a problem related with the cpu governor. Independently on the governor, with no load the frequencies are around 2ghz (2.4ghz is the maximum freq. with no turbo boost). On ubuntu 12.04 they the freq was 800mhz...

---

### Post by na01 on 2012-10-21
I've found the "problem".
while powertop is running the cpu raises its frequencies with apparently no reason, but the values in /sys with powertop off are reasonably near 8-10w.

I've lost the /proc/acpi/battery file, I don't know if it is due to the new kernel.
now the laptop (sa3) runs as with the 12.04 :)

---

### Post by lvanderree on 2012-10-22
I haven't got any problems either after upgrading.

I am however already curious about the next Ubuntu (13.04), which is said to get improved mobile support, like better battery life.

---

### Post by twidxuga on 2012-10-24
Finally got the (alps) touchpad of my VPCSA to be recognized and double finger scrolling working!

I essentially followed the instructions from [here]("http://nwoki.wordpress.com/2012/10/02/multitouch-fix-for-alps-touchpad/") that were meant for a dell Vostro.

Still afterwards I found that the touchpad, although correctly detected, was too "stiff" and required too much pressure, so I modified the alps.c to make it more sensitive. The resulting alps.c can be found [here]("http://pastebin.com/download.php?i=ZJg0tku1"). 

It is still not 100% perfect, for example there is no pinch to zoom, but double finger scrolling is good to have and can be configured to work decently with Kubuntu's touchpad configuration  (and I am guessing the same will be the case with whatever touchpad configuration utility exists in Ubuntu).

Got so much out of this thread that I was compelled to contribute, Thank you all.

---

### Post by twidxuga on 2012-10-24
By the way, if you need/want to revert the procedure in my previous post, run (as root):

```
dkms remove psmouse/alps-dst-0.4 --all
rmmod psmouse && modprobe psmouse
```

---

### Post by lvanderree on 2012-10-24
Thanks, 

I already had multitouch, but not always very smooth.

I tried this, and building it was pretty easy, and it seems to work fine. I am currently however using my external mouse, so won't be testing it very much know.

---

### Post by primetomas on 2012-11-30
I am on a SandyBridge VAIO SE15 and mostly after good CPU performance and good battery life and found this combination to be a win.    

I updated my notes at [http://blog.ejbca.org/2012/02/ubuntu-gnulinux-1204-precise-on-sony.html](http://blog.ejbca.org/2012/02/ubuntu-gnulinux-1204-precise-on-sony.html).    

Summary: 

[LIST]
[*]Ubuntu 12.10
[*]Use hacked BIOS with advanced menus. This enables me to permanently disable the Radeon in BIOS. Otherwise it will be re-activated after suspend/resume so power consumption will be high after resume. Much better than vgaswitcheroo or acpi_call :-)
[*]Use a powersavings script, originally from somewhere here. Perhaps does not save much power(?) but makes it a bit nicer plugging/deplugging power.
[*]Use Kernel 3.7 from Ubuntu Mainline. This have some new power saving improvement.  This turns out to be a win for me. I can get 4+ hours from the battery, also over suspend/resume cycles.
[/LIST]

Referenses: 

[LIST]
[*]Hacked BIOS with advanced menu: [http://forum.notebookreview.com/sony/641671-sony-vaio-sa-sb-sc-se-advanced-menu-bios-hack.html](http://forum.notebookreview.com/sony/641671-sony-vaio-sa-sb-sc-se-advanced-menu-bios-hack.html)
[*] Ubuntu kernel mainline: [https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
[/LIST]

---

### Post by lvanderree on 2012-12-03
Thanks!

I wasn't aware of any hacked BIOS-es but I like! this saves me the trouble of disabling the Radeon everytime I change my system, since I never intend to use it anyway!

which kernel did you install? I've chosen to install the rc7-raring variant, which seems to work OK, but I guess I have to do a clean install of Ubuntu to get better battery lifetime.

When I boot I often get messages about errors it want to report, and my power usage (with chrome runnning) seems to be around 25W (although maybe this can also be reduced by removing Flash-player...)

---

### Post by primetomas on 2012-12-04
I did not reinstall my system. My vaio has gone through 12.04beta->12.04->12.10->12.10 with rc7-raring kernel.

I also get messages about errors to report. Power usage for me with nothing running is <10w, with thunderbird, firefox, eclipse, terminal it idles <12w.

I don't use flash, finally flash is on it's way out of this world.

---

### Post by shiv1499 on 2013-02-19
> **wep940 said:**
> I would get detailed specs - cpu, their motherboard type, video processor, wireless adapter, audio processor, etc., then do a net search on the model and the specific piece of hardware - as an example  ubuntu 10.10 vaio (your model here) video.  You can also replace ubuntu in the search string with the word linux and see the problems from others in other versions of linux.  Do similar searches on this forum.  If you find reference to a problem, post back here and we can see if there is a work around.  The whole idea is to identify what might be problem areas and their solutions prior to installing ubuntu so that you don't run into problems you are not prepared for.  I'm no expert, but there are plenty of people here to help you!

Hi,
 
I bought a sony vaio s series and currently using ubuntu on it. There is no problem for the drivers. The only problem I faced was with NVIDIA Graphic card which when installed does not give me the required resolution. The one installed by default is onboard intel 4000 HD which is quite enough for the display. For games I use windows.
Other drivers like wifi , sound , bluetooth, ambient sensor etc all work fine. Installing LTS version is recommended.

---

### Post by harlequin_ on 2013-03-23
Hi, I recently bought a Vaio S15 (i7, 12 gb ram, GPU and an ATA disk). Solving the dual-boot was a pain in the ass, as the working methods that are recommended for other vendors did not work at all. After getting frustrated for a few nights I finally managed to do it. In case you cannot solve your problem with boot-repair, you might find the below websites useful. Please carefully read all of them and ask questions about things you do not understand before you take any action, otherwise you might end up with 7-8 complete system restores. Also, DO NOT FORGET to make the recovery media disk using Windows 8 as soon as you open the computer for the first time. That will relax you about the possibility that you will screw up the recovery partiton (outside Win 8) and will make it less likely for you to make mistakes. The websites I found useful for dual boot:

[http://www.linuxrelease.com/2012/07/sony-vaio-with-insyde-h2o-efi-bios.html](http://www.linuxrelease.com/2012/07/sony-vaio-with-insyde-h2o-efi-bios.html)
[http://askubuntu.com/questions/91437/uefi-hardware-and-dual-booting-with-windows/130984#130984](http://askubuntu.com/questions/91437/uefi-hardware-and-dual-booting-with-windows/130984#130984)
  [http://www.hackourlife.com/sony-vaio-with-insyde-h2o-efi-bios-ubuntu-12-04-dual-boot/](http://www.hackourlife.com/sony-vaio-with-insyde-h2o-efi-bios-ubuntu-12-04-dual-boot/)
[http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file](http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file)

After I managed to dual boot, the only problem I had after I booting Ubuntu was with the switchable graphics mods and therefore with NVIDIA graphics card. After driver installation I had no desktop and Unity. I launched a terminal and purged/removed the NVIDIA packages I installed and rebooted, and all worked fine. As noted by the previous user, for now the integrated card seems quite enough, so I am not planning to mess with installing the dedicated card until a steady and easy solution, or a step-by-step guide is available. Other than this, all I can say is that she is a powerful, light and beautiful beast in both Win 8 and Ubuntu 12.10.

---

### Post by jaumegp on 2013-04-07
Hi,

I'm thinking of buying a Vaio S series 13 (SVS13) laptop:
[http://store.sony.com/c/SB-Series-Notebooks/en/c/S_SB_SERIES_PAGE](http://store.sony.com/c/SB-Series-Notebooks/en/c/S_SB_SERIES_PAGE)

I will chose the Nvidia GPU + HD4000 with a 1600x900 display as I want to try some Steam games :P

Has anyone tried this one with Ubuntu? Any issue with battery, hibernate..?

Thanks!

---

### Post by harlequin_ on 2013-04-09
Hi,

I can't get my NVIDIA® GeForce® GT 640M LE (hybrid graphics) working on Ubuntu 12.10. I tried many things all of which ended up with a desktop with either no panels/unity or low resolution.
I would really appreciate if someone (with preferably a Sony Vaio S13/15) who could get their Nvidia card running on Ubuntu 12.10 explain step-by-step how they managed.

Many thanks in advance.

---

### Post by MZaza on 2013-04-28
> **harlequin_ said:**
> Hi,

I can't get my NVIDIA® GeForce® GT 640M LE (hybrid graphics) working on Ubuntu 12.10. I tried many things all of which ended up with a desktop with either no panels/unity or low resolution.
I would really appreciate if someone (with preferably a Sony Vaio S13/15) who could get their Nvidia card running on Ubuntu 12.10 explain step-by-step how they managed.

Many thanks in advance.

I have Sony Vaio SVS13125CAW with nVidia Geforce and Bumblebee worked for me, what's nice about it is that  you can choose which application to run using the dedicated card and that saves you battery.
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by harlequin_ on 2013-05-03
Hi, 

Thanks a lot for your reply. Knowing that there is a solution, although suboptimal, is nice. But I actually was looking for another type of a solution  such that when I open my computer, the selected video card, without installing new software or typing in additional commands, would kick in properly. Is this not possible at all, for instance using a specific kernel version or Nvidia drivers?

---

### Post by bopsis on 2013-07-06
Hi,

my story just for info.
I got a new Sony Vaio SVS15112C5E (Windows 8 pre-installed) and wanted to have a dual boot with Ubuntu. After a couple of hours of messing up, made a backup of hard drive, formated it and installed fresh Windows 7 (legacy mode). So far Windows 7 does not recognize anything :) No WiFi, Graphic etc. drivers. As I almost do not use Windows, will try to solve this later. 
Now tried to install Ubuntu 13.04. Somehow didn´t worked from Live USB (hanged on copyrigt or so message and blinking coursor), so burned a DVD and worked fine. After installation almost everything (Nvidia I switched off in Bios) works right from the box except I guess the: WebCam, multitouch.
Does anyone knows how to get the WebCam working?
Plus I would like to minimize the power consumption - tried to install battery applet:

sudo add-apt-repository ppa:iaz/battery-status && sudo apt-get updatesudo apt-get install battery-statusBut it doesn´t works: ´*failed to fetch*..´ etc. Does anyone knows: a) if it´s a good idea to install this; b) if yes, what could be the problem.
Thanks!

---

### Post by hermantili on 2013-07-09
> **MZaza said:**
> I have Sony Vaio SVS13125CAW with nVidia Geforce and Bumblebee worked for me, what's nice about it is that  you can choose which application to run using the dedicated card and that saves you battery.
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

I have an SVS151290x with NVIDIA 640M LE. I tried Bumblebee but I can never get the driver to recognize the card! 

Running 'nvidia-detector' simply returns 'none'. 

Did you have any such problems?

---

### Post by bopsis on 2013-08-05
Hi,

I´m trying to switch off keyboard backlight, but it doesn´t works ([FONT=Ubuntu Mono, Ubuntu Beta Mono A, Consolas, Bitstream Vera Sans Mono, Courier New, Courier, monospace]tried suggestions from here [/FONT][http://askubuntu.com/questions/276983/cant-disable-control-keyboard-backlight-on-sony-vaio-vpcf236fm](http://askubuntu.com/questions/276983/cant-disable-control-keyboard-backlight-on-sony-vaio-vpcf236fm)). Has anyone ideas?
I´m using TLP power saver, maybe it somehow conlicts with it (for example also the display backlight is allways bright after restart despite the fact that I always turn it to zero).
Thanks!

---

### Post by opodaniel-x on 2013-09-14
Found a nice program to keep the cpu cooler (nothing new btw). 
> apt-get install cpufrequtils
This will help set governors and cpuf frequence. I keep my cpu's under 1.6GHz. Just set in /etc/rc.local :
> cpufreq-set -u 1.6GHz   
I see this freq is ok for watching moovies and surfing the net while keeping the ventilator quiet.  
BR

---

### Post by AussieGuy on 2013-09-17
Does anyone know if the [SVP11216CGB]("http://www.sony.com.au/product/svp11216cg") (Vaio Pro 11) model is linux-compatible?  It certainly looks like a nice machine, and 128GB would probably be enough for me, as I don't have movies or games.  And I'd remove Windows completely, as I have no use for it.  

Thanks!

---

