---
title: "HOWTO: Get proper video resolution with trident video card and Ubuntu 8.04"
date: 2008-04-23
forum: Hardware
---

### Post by ilovelinux33467 on 2008-04-23
This guide assumes that you are doing a fresh install of ubuntu 8.04 and you get a wrong resolution with a trident video card.

These are the steps I did:

1. Boot up the ubuntu live cd. I selected "Try Ubuntu without any change to your computer".

2. Once it has booted up open up a terminal and enter "sudo displayconfig-gtk" (without the speech marks)

3. A window should pop up. Select Graphics Card from top. Click the button where it says 'Driver'. A window will pop up. Select the button where it says 'Choose Driver by model'

4. On the list box on the left select 'Other' then on the right list box select 'VESA (generic driver)' or something to do with 'VESA'

5. Click ok or apply to all the dialog boxes. Log out and Ubuntu will automatically log back on in 10 seconds. Once it has logged back in. go back into terminal and enter "sudo displayconfig-gtk" (without the speech marks).

6. Click on the button where it says 'Model' and a dialog box will pop up. Select 'Generic' on the left list box and 'LCD Panel ' & what ever your laptop's native resolution is. Click ok on that box. Then click ok on the other box. Log out again and wait 10 seconds.

7. Click the icon on the desktop called 'Install' and install Ubuntu on your computer with whatever settings you want. Once Ubuntu is installed then reboot.

8. Log on with your user account that you created during the install. Open up terminal and enter "sudo displayconfig-gtk" (without the speech marks). The terminal will ask for a password. Just put in the PASSWORD that you normally log on with your username with.

9. A dialog box will pop up. Select Graphics Card from top. Click the button where it says 'Driver'. A window will pop up. Select the button where it says 'Choose Driver by model'

10. Select 'trident' on the left list box. On the right list box select what type of trident card you have (In my case I had a CyberBlade)

11. Click OK. Then Click ok on the other dialog box. Then restart the computer. When you log back in you will have the right resolution with your laptop. Enjoy :)


I hope you can understand this guide. I typed what I remembered at the back of my head. Sorry for the Spelling Mistakes and Grammar (hey i'm only 14 years old). I take no responsibility if it stuffs up your computer somehow (but it won't)


Feel free to post whether it worked or not ;)

---

### Post by bradshawd on 2008-04-27
Thanks for this.  Seems to have sorted the issue on the laptop alone. :-)

Unfortunately bieng a 40 something novice to Linux and especially ubuntu (First install).. I am struggling to make a second screen work whilst plugged into docker..  laptop screen down. therefore want secondary monitor to be master...

Looks og at login screen i.e. correct resolution but as soon as I log in auto adjusts back to 800 x 600 leaving a large black border around the edge.

Any assistance would be appreciated

Many Thanks in advance

Derek

P.S do not worry about age or typing skills..  You obviously know more than me and that's what counts.

---

### Post by bradshawd on 2008-04-27
Update

Managed to solve it By disconnecting secondry monitor and updating as above all the relevent configs.  And then restarted each config indivudually so that ubunto could work out what was happening..  

Think I was running before I could walk..  Did the same with some "Redmond" OS as well.

Derek.

---

### Post by aquammles22f on 2008-05-01
This is to confirm that 

sudo displayconfig-gtk

solved my problem on Dynabook T3 410PME resolution problem. The ubuntu menu wouldn't let me choose above 800x600 but playing with above command led me to choose proper 1024x768. Behavior is stalbe after reboot. The hardware is trident CyberBlade XP Ai1.

Thanks,
aquammles22f

---

### Post by heri on 2008-05-06
Hello,

I tried this guide on Hardy live CD and confirm that it works great on my old laptop Toshiba Tecra 8200  :)

My temporary workaround before I found this guide: 
copied the /etc/X11/xorg.conf file from Ubuntu 7.10 (which works fine) to Hardy.

Thanks a lot.

---

### Post by whatsthatmean on 2008-05-10
Duuuude!
Thanks so much for posting. I've been trying to figure this out for weeks. Almost gave up after the 3rd reinstall of Xubu. I changed the last step to a better selection for my lap, dell lcd - but your solution was the easiest and the only one I found that worked. I dont care if you are only 14 - BRILLIANT!!!!!!!!!!!!

---

### Post by some1l8 on 2008-05-25
after following the setting, my 8200 stopped booting up before the user/password window, any idea to change solution back?

---

### Post by bradshawd on 2008-05-25
> **some1l8 said:**
> after following the setting, my 8200 stopped booting up before the user/password window, any idea to change solution back?

Utilise the re-detect option on the Grub Menu..   Usually option 2

Derek

---

### Post by Gestalt_splash on 2008-05-26
Many thanks for the timely and useful information. I have just installed Ubuntu 8.04 and found the resolution suboptimal. It was impossible to change the resolution from 800x600 to 1024x768. By using the command "sudo displayconfig-gtk", I managed to get the best resolution for my laptop, a Toshiba Portege 4010 connected to a Philips LCD monitor. 

To my chagrin, I could not get this solution from Ubuntu Linux Toolbox 1000+ commands. May I ask ilovelinux33467 how this solution was obtained? What may be the best reference book besides the forum?

---

### Post by sdavmor on 2008-05-30
Well done young man!  I put 8.04 on my old Satellite Pro laptop this morning and had "midget screen" syndrome on the Cyberblade display.  But you solved it, and it worked like a charm for me too.  It would have been nice if this display configurator were already on the menu.  Anyway, well done and thank you very much for the tip.

:guitar: SDM (Systems Theory)
[http://systemstheory.net](http://systemstheory.net)

---

### Post by theophiles on 2008-05-31
The way that this turned my screen into a digital Jackson Pollock painting after following the first instruction, I can now see that this is something to try with a live CD rather than a hard drive and later, when I have time. Even still, it is a promising place to begin.

If anyone would like to save me the trouble, however, and figure out the precise choices to make using xubuntu and a Toshiba satellite 4080XCDT, I would be very happy.

---

### Post by roger_1960 on 2008-06-04
Great post.  The method worked with Xubuntu Hardy on a Toshiba S1800 514 laptop with Cyberblade graphics AFTER installing from the alternate CD.  (You have to use your sudo password at each login of course) Iwould note that while installing the laptop fan didn't run properly and I had to take the top off, use bellows etc to get it to the end of the install without crashing due to high temp.  Seems OK once rebooted after install.........:)

---

### Post by Gremlin001 on 2008-06-12
You have got to be one of the brightest 14 year olds around.  Thank you for this post.  As an absolute newbie to linux I have searched and tried many different suggestions but none worked.  This one worked on my Toshiba Satellite 1800 HV9:PIII with the Trident CyberALADDIN-T graphics controller.

=D> \\:D/

---

### Post by thewogg on 2008-07-01
This worked really well.  Nice Job!

I used a little variation to get my install working on my Tecra 8200.

I had already installed ubuntu and wanted to change my settings without re-installing. I used the live-cd method described to set up the xorg.conf file, popped in my usb drive, copied of the /etc/x11/xorg.conf file, rebooted into my ubuntu, hard drive installation, copied the xorg.conf file from my usb drive to /etc/X11 on my hard drive, logged out, logged in, click System, Preference, Screen Resolution, choose 1024x768, apply.

Looking at the new /etc/X11/xorg.conf file showed me that even with this working config the next time I restarted X it would be back at 800x600.

So I edited the file manually and fixed the seettings to display at 1024x768.

Here's my xorg.conf for those that just want a working config for a Tecra 8200 at 1024x768:

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"Trident CyberBlade (generic)"
	Busid		"PCI:1:0:0"
	Driver		"trident"
	Screen	0
	Vendorname	"Trident"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"Trident CyberBlade (generic)"
	Busid		"PCI:1:0:0"
	Driver		"trident"
	Screen	1
	Vendorname	"Trident"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

---

### Post by iClouseau88 on 2008-07-13
Hello ilovelinux33467,

Thank you so much.  Your method works but I had to modify it a bit.  Here's why.

1.  My rig is Toshiba Satellite Pro 4600 with dual-boot Win XP-Hardy.  I updated to kernel 2.6.24-19 but this gave me a 800x600 resolution, i.e. a large black border around the screen (Bug # 185440 regarding xserver-xorg).  Also found that displayconfig-gtk is NOT installed and graphic card for Trident Cyberblade driver is missing.

2. I re-installed displayconfig-gtk.

3. Because the Hardy  Live CD doesn't boot, I skipped Step #1 and Step #7.  In Step#6, I also hit the Resolution button and selected 1024X768.  Other than these, I followed your method and it works!  Now everything is back to normal as far as display goes.

Thank you kindly.

---

### Post by ramengirl on 2008-07-15
Thanks so for much for the tutorial. I've never been able to get Hardy to work right with my video resolution till now.

I have an old HP Pavilion N5470 laptop with a Trident Cyberblade videocard. I didn't use the live cd install, I installed using the alternate cd. I just followed the directions skipping Step 1 and Step 7 as I could not use the live cd. I logged in and started with Step 2. You will have to log out every time after you make a change to the video settings using sudo displayconfig-gtk in the terminal. Also, I had to go into System->Screen Resolution to change the screen resolution to 1024 X 768 after Step 11.

---

### Post by BLTicklemonster on 2008-07-18
Worked for me on a new install without the live cd.

Thanks a gazillion!!!

---

### Post by theNymph on 2008-08-06
My video card is Trident CyberAlladin, and I'm running Xubuntu.

Unfortunately, ilovelinux33467's method didn't work for me. By the time I finished step 4, and I've logged out, I had a black screen with nothing on it. 

However, I did manage to get it working by simply pasting thewogg's xorg.conf (starting from the part after the input devices) into my xorg.conf

I was just trying this out for fun and expected to see some dramatic error messages. But, amazingly, it worked. I can now set my resolution to 1024x768, whereas previously I could only set it to 800x600.

---

### Post by jc349817 on 2008-08-06
Thanks ilovelinux33467!  Works perfectly on a Toshiba 1805-S207 with Trident Cyberblade XP Ai1. \\:D/

---

### Post by hwel2 on 2008-08-07
Thanks to ilovelinux as well, but I too had to use theNymph's strategy of cutting and pasting thewogg's xorg.conf file.  The reason was that whenever I would manipulate the Display settings - Generic -> LCD Display 1024x765 - I would be left with an unusable interface displaying what looked like five or six improperly overlaced visions of the desktop.  That could very well be what theophile meant as a digital Jackson Pollock painting.  Nevertheless, again, all these efforts are much appreciated.

---

### Post by want2bdifferent on 2008-08-19
thankyou thankyou thankyou

I didn't even need to do the last couple of steps but it is working on my toshiba satellite pro 4600, and i couldnt be happier now using ubuntu

thanks again.

---

### Post by revdrwebb on 2008-08-21
Perfect!  Worked like a charm!  Thanks!

---

### Post by K7AAY on 2008-08-22
Thank you!

---

### Post by loewenkind2 on 2008-08-27
Your fine HOWTO perfectly solved my probs with a CyberBlade on my old Toshiba Satellite Pro 6000....:)

Many thanks from Germany for this great help!

loewenkind2

---

### Post by umann on 2008-09-06
:popcorn:I am always amaze about the community around Lunix and how resources  we all have together. Humanity still have a chance.....
Anyway thank you for that post i have been working on that for a week now i edited my xorg.conf file in multiple ways and always the same resolutions were available. I have to say i skipped the whole thing and went directly with the "sudo displayconfig-gtk"and it worked right away (after reboot). No live CD or reinstall.

Thank you that's made my day:guitar:

I have a Toshiba A20 Trident Cyberblade.

---

### Post by jhorner on 2008-09-09
Looking for any assistance on figuring out which Video Card is in my Toshiba Terca 8200.  Toshiba's specs state that the card is a Trident XP card, that's all it said.  Tried calling their support and they could only give me that much info.  So if anyone would know how to obtain this information or has an educated guess, it would be greatly appreciated.  

I loaded Edubuntu on the laptop and was going to find a school to give it to (better than throwing it out) but the resolution is 640x480 and there is a 3+ inch black bar all the way around the screen.  I hope to fix this so I can make it usable...

---

### Post by mpitch on 2008-09-19
Thanks a lot. I am a new user to linux and was after searching quite a bit had almost given up on finding a solution to this resolution problem. AFter installing ubuntu 8.04 on my My laptop I was getting a 800x600 resolution screen instead of the native 1024x768. 

I have a Toshiba A25 S3072 laptop (I beleive it is similar to S307 which has a 2.8 GHz processor but mine has 3.06 Ghz) and has a Trident Cyberblade XP2 graphics processor according to the manual.

I had tried a variety of solutions in vain. Finally I found this blog and the solution provided by    thewogg    worked out. I just copied the xorg.conf file given by thewogg (just the section below the input device section into my xorg.conf file) and it worked just like thenymph mentioned. JUST PERFECT 

Thank you to both ilovelinux33467 for putting the first detailed post on this issue which has helped so many and brought so many comments and alternative solutions and to thewogg for posting the alternative solution for people like me and to thenymph for pointing out that this works.

Thank you to all the others here who are taking the time out to help each other by sharing their knowledge. Linux is a great community.

---

### Post by CohoMike on 2008-09-19
Thanks!  This did the trick on my Toshiba Portege 4005.

---

### Post by Tatty42 on 2008-10-06
[FONT="Trebuchet MS"][SIZE="2"]Weeks of searching for the answer to this problem and you provide a solution that takes 15 mins (and worked from an already installed Xubuntu)! Kudos and thanks to you! :KS[/SIZE][/FONT]

---

### Post by Faust942 on 2008-10-08
> **iClouseau88 said:**
> Hello ilovelinux33467,

Thank you so much.  Your method works but I had to modify it a bit.  Here's why.

1.  My rig is Toshiba Satellite Pro 4600 with dual-boot Win XP-Hardy.  I updated to kernel 2.6.24-19 but this gave me a 800x600 resolution, i.e. a large black border around the screen (Bug # 185440 regarding xserver-xorg).  Also found that displayconfig-gtk is NOT installed and graphic card for Trident Cyberblade driver is missing.

2. I re-installed displayconfig-gtk.

3. Because the Hardy  Live CD doesn't boot, I skipped Step #1 and Step #7.  In Step#6, I also hit the Resolution button and selected 1024X768.  Other than these, I followed your method and it works!  Now everything is back to normal as far as display goes.

Thank you kindly.

Do you have any problems with battery life? I have a Toshiba Satellite Pro 4600 too.

Anyway, followed the instructions and now I have 1028x768. You rock:guitar:, kid!

---

### Post by haroman on 2008-10-13
Hello

It's my first time using linux. I just installed Xubuntu (intrepid)in my laptop and i got that black border in my screen. I have a Trident Ciberblade.

I tried the displayconfig-gtk, but i got "unknoun command"

I also tried "apt-get install displayconfig-gtk" but says its not available. 

Does "intrepid" require a different solution? 



thanks

---

### Post by NoSmokingBandit on 2008-10-16
I followed the guide and everything seems to be working fine but the screen is shifted right a few px. There are a few blank pixels on the left of the screen and my mouse can go past teh edge of the screen on the right a little. Is there a way to get this all centered in?

---

### Post by sdavmor on 2008-11-03
> **haroman said:**
> Hello

It's my first time using linux. I just installed Xubuntu (intrepid)in my laptop and i got that black border in my screen. I have a Trident Ciberblade.

I tried the displayconfig-gtk, but i got "unknoun command"

I also tried "apt-get install displayconfig-gtk" but says its not available. 

Does "intrepid" require a different solution?
thanks 

There's no "Screens & Graphics" tool (displayconfig-gtk) in the Intrepid 8.10 release, regardless of which Ubuntu flavour you are using.  It has been shelved because it's supposed to be no longer needed.  :mad:

What might work, that I haven't tried yet (on my Toshiba Satellite Pro 4600, Cyberblade XP card), is to enable Intrepid backports and get the Hardy version of displayconfig-gtk.  I'll give it a whirl and see if that provides a workaround.  Either way I'll post back here.

:guitar: SDM (Systems Theory internet music project)
[http://systemstheory.net](http://systemstheory.net)

---

### Post by sdavmor on 2008-11-03
Following up.  I enabled Intrepid backports from Hardy.  That didn't solve the problem.  I was still not able to find the Hardy "Screens & Graphics" program. However some poking around in /etc/X11/xorg.conf on other machines gave me enough clues as to want I needed to do.

After verifying that my video was indeed the Trident Cyberblade XP, I saved the existing xorg.conf (which had section holders in it but nothing else).  I then replaced its contents with the following:

Section "Device"
Identifier "Trident Microsystems CyberBlade XP"
Driver "trident"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-51
VertRefresh 43-60
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor	"Generic Monitor"
Device "Trident Microsystems CyberBlade XP"
SubSection "Display"
Depth 8
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 32
Modes "1024x768"
EndSubSection
EndSection

It took me a while to get to that.  I actually had more stuff in there but things kept blowing up on boot.  So it was a case of less-is-more, removing settings that caused video to crash on boot (it dropped me into the log) to arrive at just enough in xorg.conf to access all the screen and provide for various bit depths.  You may not even need the 8 & 16 bit sub sections under "Screen". 

If you find that your screen comes up in 1024x768 at the login prompt, but drops back into 800x600 after you login, you should go into System-->Preferences-->Screen Resolution and select 1024x768 which should now appear in your menu.  Don't be alarmed if that happens the first time you boot up after getting it set correctly.

I hope that gets you sorted.  I spent about 6 hours total on this, which is about 5 1/2 hours too much IMO.  Now I know exactly want to do when "Jaunty" comes along if the same problem occurs! ;)
 
:guitar: SDM (Systems Theory internet music project)
[http://systemstheory.net](http://systemstheory.net)

---

### Post by iClouseau88 on 2008-11-04
Hi sdavmor,

I edited my /etc/X11/xorg.conf file to show exactly the same as yours, saved it then rebooted.  After logging in, the screen shows error with parsing the config file.  Since I chose not to let the system run in default (low-resolution) mode, I picked reconfiguring the card(?) (or graphics?).  Now I have an empty screen!

Several days ago I did post a question on bugs.launchpad.net but did not get very far.

:-{

---

### Post by sdavmor on 2008-11-04
> **iClouseau88 said:**
> Hi sdavmor,

I edited my /etc/X11/xorg.conf file to show exactly the same as yours, saved it then rebooted.  After logging in, the screen shows error with parsing the config file.  Since I chose not to let the system run in default (low-resolution) mode, I picked reconfiguring the card(?) (or graphics?).  Now I have an empty screen!

Several days ago I did post a question on bugs.launchpad.net but did not get very far.

:-{

What kernel are you running?  And are you running Ubuntu, Kubuntu or Xubuntu Intrepid 8.10?

I upgraded my Toshiba Satellite Pro 4600 to the current production CD of Intrepid Ubuntu by doing a fresh install this morning, after doing an online upgrade over the weekend.  I had two problems after the upgrade: (1) I couldn't access network-manager and (2) my screen was stuck at 800x600 resolution.  The clean install somehow fixed the network-manager issue but I was left with a totally empty xorg.conf file.  Or rather it wasn't totally empty.  It just had nothing in it relevant to my Trident Cyberblade card.

So I'm wondering if you  (a) have exactly the same model of Cyberblade, and (b) are you running the exact same kernel (2.6.27-7), and (c) which flavour of the o/s you're running. Push comes to shove I can email you my /etc/X11/xorg.conf and you can overlay yours with it and see what happens.

:guitar: SDM (Systems Theory internet music project)
[http://systemstheory.net](http://systemstheory.net)

---

### Post by iClouseau88 on 2008-11-04
Hello sdavmor,

Thanks for your reply.  My Toshiba Satellite Pro 4600 is a dual boot XP Pro-Ubuntu laptop with Trident Microsystems Cyberblade XP video card.  Not sure which version.  I upgraded from Ubuntu hardy 8.04.1 to Intrepid release candidate.  Now I am using kernel 2.6.27-7.(15?).

Last might after posting the previous thread I turned off the machine and booted back into 2.6.27-7, accepting the default low resolution mode.  It appears that the new xserver-xorg engine ignores the "xserver-xorg-video-trident" driver that is already in the machine.  At this point I am wondering what to do next.

1) reinstall Intrepid on a clean slate?
2) reinstall Hardy the same way?
3) editing xorg.conf file as you suggested.  After I am done with this by saving the (new) file, should I do a "sudo dpkg-reconfigure -phigh xserver-xorg"?  I am not sure I understand the message in the xorg.conf file.

Regards,

---

### Post by iClouseau88 on 2008-11-04
Anyone?

---

### Post by sdavmor on 2008-11-06
> **iClouseau88 said:**
> Hello sdavmor,

Thanks for your reply.  My Toshiba Satellite Pro 4600 is a dual boot XP Pro-Ubuntu laptop with Trident Microsystems Cyberblade XP video card.  Not sure which version.  I upgraded from Ubuntu hardy 8.04.1 to Intrepid release candidate.  Now I am using kernel 2.6.27-7.(15?).

Last might after posting the previous thread I turned off the machine and booted back into 2.6.27-7, accepting the default low resolution mode.  It appears that the new xserver-xorg engine ignores the "xserver-xorg-video-trident" driver that is already in the machine.  At this point I am wondering what to do next.

1) reinstall Intrepid on a clean slate?
2) reinstall Hardy the same way?
3) editing xorg.conf file as you suggested.  After I am done with this by saving the (new) file, should I do a "sudo dpkg-reconfigure -phigh xserver-xorg"?  I am not sure I understand the message in the xorg.conf file.

Regards,

My apologies.  I wasn't online with my laptop so the code wasn't cut and pasted.  I have corrected it above to exactly what is working in my laptop.  The "Monitor" section was wrong.  It should have read:

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-51
VertRefresh 43-60
EndSection

So, don't do 1 2 or 3 of your suggestions (yet).  You can now cut and paste the entire code into xorg.conf and give it a try on your current Intrepid install.  Let me know how it works out.

:guitar: SDM (Systems Theory internet music project)
[http://systemstheory.net](http://systemstheory.net)

---

### Post by iClouseau88 on 2008-11-06
Hello sdavmor,

Good to hear from you again!

I did type in the xorg.conf exactly as you wrote in your post #34, but when I turn on the machine to load Ubuntu, I got the error messsage about parsing error in the config file.  I don't know how to make Intrepid recognize the ati and trident video drivers that are in the laptop since my first Ubuntu - 6.06!

I am almost resigned to giving up on Ubuntu!  Haven't got around to wiping out the Linux partition to re-install Hardy.  I am also tempted to install OpenSUSE or Fedora.

---

### Post by mindviper on 2008-11-07
Hi. I just installed Ubuntu 8.10 so I have been using Linux for at least 7 hours. 
I have Toshiba Tecra 8200 laptop. I copypasted TheWogg's xorg.conf post to my empty xorg.conf after 2 hours of figuring out what sudo means.
After that I rebooted and the machine started asking me weird questions about some sort of reconfiguring. I clicked some buttons and rebooted again. Then I went to check what's up with the xorg.conf and there was some backupfile of it made ("failsafe") + the one I edited but it was changed into some sort of empty template of what it should be (lots of words like "default").
I also still have just 800x600 reso.
So is that TheWogg fix still supposed to be working for Ubuntu v8.10 or is it just for 8.04?

---

### Post by sdavmor on 2008-11-08
> **iClouseau88 said:**
> Hello sdavmor,

Good to hear from you again!

I did type in the xorg.conf exactly as you wrote in your post #34, but when I turn on the machine to load Ubuntu, I got the error messsage about parsing error in the config file.  I don't know how to make Intrepid recognize the ati and trident video drivers that are in the laptop since my first Ubuntu - 6.06!

I am almost resigned to giving up on Ubuntu!  Haven't got around to wiping out the Linux partition to re-install Hardy.  I am also tempted to install OpenSUSE or Fedora.

If you're continuing to get a parsing error then something isn't in there right.  Did you replace the "Monitor" section with what I last posted?  Look closely at it.  Maybe you can post your xorg.conf here and I can take a look at it?

:guitar: SDM (Systems Theory internet music project)
[http://systemstheory.net](http://systemstheory.net)

---

### Post by sdavmor on 2008-11-08
> **mindviper said:**
> Hi. I just installed Ubuntu 8.10 so I have been using Linux for at least 7 hours. 
I have Toshiba Tecra 8200 laptop. I copypasted TheWogg's xorg.conf post to my empty xorg.conf after 2 hours of figuring out what sudo means.
After that I rebooted and the machine started asking me weird questions about some sort of reconfiguring. I clicked some buttons and rebooted again. Then I went to check what's up with the xorg.conf and there was some backupfile of it made ("failsafe") + the one I edited but it was changed into some sort of empty template of what it should be (lots of words like "default").
I also still have just 800x600 reso.
So is that TheWogg fix still supposed to be working for Ubuntu v8.10 or is it just for 8.04?

I don't know.  I started with more instructions in my xorg.conf and had to delete things to get it working on 8.10.  If your Tecra has a Cyberblade video start by using the xorg.conf I provided above. (I have a Satellite Pro 4600 but it's probably the same thing as a Tecra from a video standpoint).  It should be all you need to get 1024x768 video resolution using the full screen on 8.10.  All the other code is really just fluff.  Try it and see.

:guitar: SDM (Systems Theory internet music project)
[http://systemstheory.net](http://systemstheory.net)

---

### Post by retrospective on 2008-11-08
I have a Toshiba Satellite A20 Series System Unit laptop computer Model PSA20C
Video adapter=Trident Cyber Aladdin

Ubuntu is ALWAYS running in low graphics mode :(

My xorg file

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

I tried the xorg settings sdavmor wrote but it didn't work so I had to set it back to default or use the low graphics mode :( Any clues?

---

### Post by retrospective on 2008-11-08
Solved!

> Section "Monitor"
	Identifier	"Configured Monitor"
      Option      "DPMS"  "true"
      HorizSync    30.0-60.0
      VertRefresh  50.0-70.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
      DefaultDepth      24
      SubSection "Display"
                  Depth         24
                  Modes         "1024x768" "800x600"
      EndSubSection
      
EndSection

---

### Post by iClouseau88 on 2008-11-08
Hello sdavmor,

Thanks for not giving up on me.  Further to my last post, I went to the Debian User forum and based on what I saw there made some changes to my xorg.conf file.  Basically adding device driver info and modeline's preferred resolution of 1024x768.  When I restarted the laptop into Ubuntu Intrepid, I no longer see parsing error message (some progress!) but I still get the 800x600 resolution.  Here's my latest xorg.conf file:


Section "Device"
	Identifier	"Trident Microsystems CyberBladeXP"
	Driver		"trident"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
  Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync
Option	"PreferredMode" "1024x768_60.00"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Generic Monitor"
	Device		"Trident Microsystems CyberBladeXP"
   SubSection "Display"
      Depth   24
      Modes   "1024x768_60.00"
   EndSubSection 
EndSection

Could you have a look at it and let me know what you think?

Thanks a lot for your help.

---

### Post by sdavmor on 2008-11-08
> **iClouseau88 said:**
> Hello sdavmor,

Thanks for not giving up on me.  Further to my last post, I went to the Debian User forum and based on what I saw there made some changes to my xorg.conf file.  Basically adding device driver info and modeline's preferred resolution of 1024x768.  When I restarted the laptop into Ubuntu Intrepid, I no longer see parsing error message (some progress!) but I still get the 800x600 resolution.  Here's my latest xorg.conf file:


Section "Device"
	Identifier	"Trident Microsystems CyberBladeXP"
	Driver		"trident"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
  Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync
Option	"PreferredMode" "1024x768_60.00"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Generic Monitor"
	Device		"Trident Microsystems CyberBladeXP"
   SubSection "Display"
      Depth   24
      Modes   "1024x768_60.00"
   EndSubSection 
EndSection

Could you have a look at it and let me know what you think?

Thanks a lot for your help.

Try changing your "Monitor" section to this. You can comment out what you have.

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-51
VertRefresh 43-60
EndSection

Or alternatively put these two lines in before your "Modeline" entry (which should be unnecessary IMO for the Cyberblade XP video device).

HorizSync 28-51
VertRefresh 43-60

I'm off for a couple of hours.  I'll check back in a bit.

:guitar: SDM (Systems Theory internet music project)
[http://systemstheory.net](http://systemstheory.net)

---

### Post by iClouseau88 on 2008-11-09
Good news, sdavmor!

Following your suggestions, I was able to get my 1024x768 resolution back!     Perhaps what worked, including your tip, were the facts that:

1) Trident driver is included in Section "Device";

2) HorizSync 28-51 was added to Section "Monitor".  Note that in some older xorg.conf file I used "28-31" so "31" could have been a mistake;

3) VertRefresh 43-60 was added as well;

4) I used gtf command to generate the "Modeline" entry;

5) DefaultDepth24 was added just above "SubSection "Display"" of Section "Screen"

Here's my currently up-to-date xorg.conf file:

Section "Device"
	Identifier	"Trident Microsystems CyberBladeXP"
	Driver		"trident"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync 28-51
	VertRefresh 43-60
  Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync
Option	"PreferredMode" "1024x768_60.00"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Generic Monitor"
	Device		"Trident Microsystems CyberBladeXP"
	DefaultDepth 24
   SubSection "Display"
      Depth   24
      Modes   "1024x768_60.00" "800x600"
   EndSubSection 
EndSection

Now, how do I back up this xorg.conf file so that X doesn't get messed up the next time Ubuntu release a newer distribution and a new kernel? Secondly, where is the button to mark this thread as "SOLVED"?

Thanks a lot for your help.  You have restored my faith in Ubuntu Intrepid and Ubuntu Forums users.  It's been tough for the last 2 weeks that I had to endure a smaller (i.e. 800x600) screen. 

Cheers!

---

### Post by hjt61 on 2008-11-15
Hey guys,

thanks a lot to all of you sharing your experience... After fighting half a day to get my resolution right.

I just used the same version of xorg.conf as posted by iClouseau88 in post #48, and this works like a charme.

Configuration:
Toshiba Tecra M1
Ubuntu 8.10 Desktop

/Hermann

---

### Post by antoniuk on 2008-11-26
thank you so much! I have a Tecra M1 that would not stretch to the full screen and that xorg.conf worked perfect!

---

### Post by Roll_Tide on 2008-12-01
**sdavmor** & **iClouseau88** - A huge THANKYOU to you guys!!

After having spent the vast majority of my weekend trying to get a version of linux to function on my HP laptop (with the Trident CyberBlade XP video)(*Tried Ubuntu, Kubuntu, Fedora and finally Xubuntu*) I used the exact code in post 48 and it works flawlessly!!

Thanks again!!
:KS:KS:KS:KS:KS:KS:KS:KS

---

### Post by thewogg on 2008-12-04
Had not checked in in quite a while.

I'm using Intrepid (8.10) on my Toshiba Tecra 8200. I used the upgrade utility to get there so my 8.04 configuration was updated automagically.

Here is my working xorg.conf file:

______________________________________________


# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
root@vorador:/etc/X11# cat xorg.conf
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizEdgeScroll" "0"
EndSection

Section "Device"
Identifier "Configured Video Device"
Boardname "Trident CyberBlade (generic)"
Busid "PCI:1:0:0"
Driver "trident"
Screen 0
Vendorname "Trident"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
Vendorname "Generic LCD Display"
Modelname "LCD Panel 1024x768"
Horizsync 31.5-48.0
Vertrefresh 56.0 - 65.0
modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
Gamma 1.0
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
Defaultdepth 24
SubSection "Display"
Depth 24
Virtual 1024 768
Modes "1024x768@60"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
screen 0 "Default Screen" 0 0
Inputdevice "Synaptics Touchpad"
EndSection
Section "Module"
Load "glx"
Load "GLcore"
Load "v4l"
EndSection
Section "device" #
Identifier "device1"
Boardname "Trident CyberBlade (generic)"
Busid "PCI:1:0:0"
Driver "trident"
Screen 1
Vendorname "Trident"
EndSection
Section "screen" #
Identifier "screen1"
Device "device1"
Defaultdepth 24
Monitor "monitor1"
EndSection
Section "monitor" #
Identifier "monitor1"
Gamma 1.0
EndSection
Section "ServerFlags"
EndSection

---

### Post by RichT70 on 2008-12-15
I have tried both 8.04 and 8.10 on my Toshiba Tecra 8200 with Trident/Cyberblade XP - and have the same limited problem - my ubuntu is only using 40-60% at the centre of the LCD panel...

I get 800x600 to start with but only accupying 40% of the screen at the centre of the LCD panel. By changing xcorg.conf as suggested below, I can get 1024x768 in both 8.04 and 8.10versions  - but that only takes up 60% at centre of the LCD panel, with a think black border around the rest... 

Any ideas ??? - do I need an even large resolution, a BIOS upgrade (if so where could I find it given the age of the laptop) - or is there something I am missing with the xorg.conf from this post...


Code:

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"    "/dev/psaux"
    Option        "Protocol"    "auto-dev"
    Option        "HorizEdgeScroll"    "0"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Boardname    "Trident CyberBlade (generic)"
    Busid        "PCI:1:0:0"
    Driver        "trident"
    Screen    0
    Vendorname    "Trident"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    Vendorname    "Generic LCD Display"
    Modelname    "LCD Panel 1024x768"
    Horizsync    31.5-48.0
    Vertrefresh    56.0 - 65.0
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
    Gamma    1.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Virtual    1024    768
        Modes        "1024x768@60"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
  screen 0 "Default Screen" 0 0
    Inputdevice    "Synaptics Touchpad"
EndSection
Section "Module"
    Load        "glx"
    Load        "GLcore"
    Load        "v4l"
EndSection
Section "device" # 
    Identifier    "device1"
    Boardname    "Trident CyberBlade (generic)"
    Busid        "PCI:1:0:0"
    Driver        "trident"
    Screen    1
    Vendorname    "Trident"
EndSection
Section "screen" # 
    Identifier    "screen1"
    Device        "device1"
    Defaultdepth    24
    Monitor        "monitor1"
EndSection
Section "monitor" # 
    Identifier    "monitor1"
    Gamma    1.0
EndSection
Section "ServerFlags"
EndSection

---

### Post by coyotearms on 2008-12-28
This is my first posting after reading this entire thread and going with iClouseau's suggestion, post 48, for my Toshiba Satellite Pro 4600 with the Trident Cyberblade XP.  It worked for me too, thanks for all the hard work!  In my case the /etc/X11/xorg.conf file that was generated after a fresh install of Ubuntu 8.10 (Intrepid) only consisted of some comment lines followed by Device, Monitor and Screen sections, all appearing to be very simple dumbed-down defaults.  I simply cut/pasted iClouseau's version of those sections BEFORE the original ones (man xorg.conf clearly states that the first occurrences are used if multiple ocxurrences exist).  On rebooting, the screen came up as 800x600 covering only a part of the screen (the original problem), but under System -> Preferences -> Screen Resolution, a new choice appeared, 1024 x 768!  With that choice the screen filled to all edges.

Because I am new to Linux, I thought I would also indicate exactly how I changed the xorg.conf file to save other novices some of the efforts I had to endure.  After booting up with my USB stick in a USB port that showed up on the desktop as LEXAR MEDIA:
cp /etc/X11/xorg.conf <space> /media/"LEXAR MEDIA"/xorg.conf
where <space> means the space key to clarify source and destination of the copy command.
Then double clicked on the LEXAR MEDIA icon, right clicked the copied file to edit it with Text Editor, cut/pasted the magic code into it and closed it.  Then
sudo  cp  /media/"LEXAR MEDIA"/xorg.conf <space> /etc/X11/xorg.conf
The sudo command allows the user to get permission to do the copy into the special /etc/X11 directory. Done.

---

### Post by pnguine on 2009-01-18
What I want to know is how the heck did you figure that out?
I can just imagine the primers your parents gave you when you were learning to read. Instead of "See Spot run." it would be "See Linux run." "See the command line. The command line is your friend. It will do anything you ask it too."

Anyway thanks Kiwi :)

---

### Post by fn_tool on 2009-01-28
When you turn 18 or 21 or whatever your legal drinking age is, I'll buy you a beer!

I used diplayconfig-gtk to set up a Toshiba Portege R100, it took 3 times of switching a setting, & logging back in, but I was able to get the screen's native 1024x768 without a problem.

I already had ubuntu installed, I just went to Terminal & sudo'd it.  I followed your steps about selecting a monitor type, then video type & on the last change I was able to set the LCD from 800x600.  Each time I changed only one setting & re-started - I bet that's the "take away" hint here.

Perfect.  Another "old" piece of hardware gets a new life.

---

### Post by Scootrider on 2009-04-24
> **retrospective said:**
> Section "Monitor"
	Identifier	"Configured Monitor"
      Option      "DPMS"  "true"
      HorizSync    30.0-60.0
      VertRefresh  50.0-70.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
      DefaultDepth      24
      SubSection "Display"
                  Depth         24
                  Modes         "1024x768" "800x600"
      EndSubSection
      
EndSection 			 		


Thanks a lot retrospective.

After a clean install, this solution worked for me on a Toshiba Satellite A20-S103, CyberALADDIN-P4, using Ubuntu 9.04.

I would like to thank you to all of other members who help those that are just starting to understand this great piece of software.

---

### Post by jeremypei on 2009-04-27
I am a freshman, my old notebook is thinkpad r30, i installded the ubuntu 9.04, 
i had tried to solve this problem for three days,   
at last   i copied yours xorg.conf ,then the problem was solved.
Thank you very much.
 
 
> **thewogg said:**
> This worked really well. Nice Job!
 
I used a little variation to get my install working on my Tecra 8200.
 
I had already installed ubuntu and wanted to change my settings without re-installing. I used the live-cd method described to set up the xorg.conf file, popped in my usb drive, copied of the /etc/x11/xorg.conf file, rebooted into my ubuntu, hard drive installation, copied the xorg.conf file from my usb drive to /etc/X11 on my hard drive, logged out, logged in, click System, Preference, Screen Resolution, choose 1024x768, apply.
 
Looking at the new /etc/X11/xorg.conf file showed me that even with this working config the next time I restarted X it would be back at 800x600.
 
So I edited the file manually and fixed the seettings to display at 1024x768.
 
Here's my xorg.conf for those that just want a working config for a Tecra 8200 at 1024x768:
 
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg
 
Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection
 
Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection
 
Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"    "/dev/psaux"
    Option        "Protocol"    "auto-dev"
    Option        "HorizEdgeScroll"    "0"
EndSection
 
Section "Device"
    Identifier    "Configured Video Device"
    Boardname    "Trident CyberBlade (generic)"
    Busid        "PCI:1:0:0"
    Driver        "trident"
    Screen    0
    Vendorname    "Trident"
EndSection
 
Section "Monitor"
    Identifier    "Configured Monitor"
    Vendorname    "Generic LCD Display"
    Modelname    "LCD Panel 1024x768"
    Horizsync    31.5-48.0
    Vertrefresh    56.0 - 65.0
modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
    Gamma    1.0
EndSection
 
Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Virtual    1024    768
        Modes        "1024x768@60"
    EndSubSection
EndSection
 
Section "ServerLayout"
    Identifier    "Default Layout"
screen 0 "Default Screen" 0 0
    Inputdevice    "Synaptics Touchpad"
EndSection
Section "Module"
    Load        "glx"
    Load        "GLcore"
    Load        "v4l"
EndSection
Section "device" # 
    Identifier    "device1"
    Boardname    "Trident CyberBlade (generic)"
    Busid        "PCI:1:0:0"
    Driver        "trident"
    Screen    1
    Vendorname    "Trident"
EndSection
Section "screen" # 
    Identifier    "screen1"
    Device        "device1"
    Defaultdepth    24
    Monitor        "monitor1"
EndSection
Section "monitor" # 
    Identifier    "monitor1"
    Gamma    1.0
EndSection
Section "ServerFlags"
EndSection

---

### Post by roki on 2009-08-22
This thread gave new life to old Compaq Armada 110 that was going to be recycled.

Thank you!

PS. It was a way easier to configurate than any of your ways, but the most valuable thing was to find out that 8.04 is last version that can work.

---

### Post by Jackie999 on 2009-09-23
This thread has saved me again! I'm always messing with old laptops and keep ending up with 1" black borders and wrong resolution. Now that the displayconfig.gtk  doesn't work I had to make the changes, per this thread, replacing my device, monitor and screen sections with the above Trident (generic) sections, in my xorg.conf to get full screen back in this old Compaq Presario 1200 (12XL504)
Thanks!!

---

### Post by kimharding on 2009-10-30
Anyone know if this solution will work with Ubuntu 9.10 Karmic Koala? I have just tried the Live CD and can't get resolution above 800 x 600. I just want to be sure before I try and upgrade from 9.04 Jaunty Jackalope, I had hoped this problem would reappear...

---

### Post by haroman on 2009-10-31
I also installed today the xubuntu 9.10 and got the same problem.

Tried to edit xorg with mousepad, gedit and nano and got a blank file. 

Any sugestion?



I have an Acer travelmate 212txv with trident cyberblade A1

---

### Post by sdavmor on 2009-11-01
> **haroman said:**
> I also installed today the xubuntu 9.10 and got the same problem.

Tried to edit xorg with mousepad, gedit and nano and got a blank file. 

Any sugestion?

I have an Acer travelmate 212txv with trident cyberblade A1

Yes, it will be empty. Copy & Paste in this code.  Log out.  Log back in. Go into "System","Display". Select 1024 resolution. Apply it. Have fun.

Section "Device"
Identifier "Trident Microsystems CyberBlade XP"
Driver "trident"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
Option "DPMS" "true"
HorizSync 30.0-60.0
VertRefresh 50.0-70.0
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1024x768" "800x600"
EndSubSection

EndSection

Cheers,
SDM (Systems Theory)
[http://systemstheory.net](http://systemstheory.net)

---

### Post by haroman on 2009-11-01
It worked!!!! THAAAAAANKS!!!



My girlfriend was going to kill me for messing with her laptop.


Thanks again

---

### Post by FredBarns on 2009-11-01
I apologize if this is not the right place for this question.  I just updated to 9.10 today.  No problem of my old Dell laptop, but my Dell Inspirion 530 (which came with Ubuntu, no less) had a big problem.  Specifically, everything looks fine until the login screen, and then I get garbage.  The GUI does not function.  However, I can login and everything sounds like it is working. Thus, besides video, it think the upgrade was a success. 

I gather that this must have to do with the video drivers.  I have worked through similar problems by reading and manipulating configuration files and such, but here I am stymied.

I can't see anything useful on the screen.  I can't even get to the terminal.  If I could see something, I could try to reinstall drivers or edit files as needs  be, but I can't even get to the starting gate.  Is there a "safe mode" type of thing for Unbuntu?  Is there another solution other that just reinstalling Jaunty? In any event it looks like Karmic just just breaks my machine.

Thanks a lot,

Fred.

---

### Post by andrewbmartin on 2009-11-04
Just a note to advise this worked on a Toshiba Satellite 1400 on Ubuntu 9.10 Karmic.

Section "Device"
Identifier "Trident Microsystems CyberBlade XP"
Driver "trident"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
Option "DPMS" "true"
HorizSync 30.0-60.0
VertRefresh 50.0-70.0
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1024x768" "800x600"
EndSubSection

EndSection


Thanks for the good work !

---

### Post by atvasco on 2009-11-05
Thanks, Sdavmor, used the cut and paste specified in reply 63 and it worked a dream!

My laptop is a Toshiba Tecra M1 with Trident Cyber XP4.

I am running Ububntu 9.10

Before I tried it I looked in the /etc/X11 directory and there was NO xorg.conf file present so I created a blank one, pasted in the code, saved, logged out then in again and set up the display resolution...

MAGIC... thanks a bunch

---

### Post by sid1202 on 2009-11-11
Hi,

I'm running 9.04 and bad resolution on my pavilion n3478. It has a trident cyberblade i7. the command suggested "sudo xconfig-gtk" fails with command not wound. I've seen many xconf.xorg suggetions but non for the i7. Also, to midify the xconf.xorg, should I logon as root ?

Please help,
Sidney

---

### Post by wilsonmorgado on 2009-11-23
I install Ubuntu 9.10, but i can't see anything in screen!

any suggestion? I have a PORTEGE R100 WITH TRIDEN video card



[IMG]http://i45.tinypic.com/dontvt.jpg[/IMG]

---

### Post by tpl on 2009-12-04
Worked for me too   !!!!    Ubuntu 9.10 on an ancient Toshiba Satellite 1800 ( 2002) vintage.
I generated an Xorg.conf from post #63   and put it etc/x11 and Lo and Behold... full screen.


Now to get the wireless card working.....

---

### Post by huwjenjinn on 2009-12-13
I'm a complete beginner here but thought I'd just say thanks for getting my Toshiba Satellite 4100 XCDT working. I modified andrewbmartin's post for the Tosh. 1400 entry above to the following (again all in Ubuntu 9.10 - the Karmic Koala - released in October 2009.)

/etc/X11/xorg.conf

[FONT=Courier New]Section "Device"
        BusID       "PCI:0:4:0"
        Identifier "Trident Microsystems CyberBlade XP"
        Driver "trident"
EndSection

Section "Monitor"
        Identifier "Configured Monitor"
        Option "DPMS" "true"
        HorizSync 30.0-60.0
        VertRefresh 50.0-70.0
EndSection

Section "Screen"
        Identifier "Default Screen"
        Monitor "Configured Monitor"
        Device "Configured Video Device"
        DefaultDepth 16
        SubSection "Display"
                Depth 16
                Modes "1024x768" "800x600"
        EndSubSection
EndSection

[/FONT]

---

### Post by nuttymango on 2009-12-27
> **roki said:**
> This thread gave new life to old Compaq Armada 110 ....

... the most valuable thing was to find out that 8.04 is last version that can work.

Would you mind posting your xorg.conf file? I've done battle with an Armada 110 (varying Linux distributions) for a long time and usually get it working after lots of "sudo vi /etc/X11/xorg.conf" trial and error.

I'd like a really definitive xorg.conf for the Trident CyberBlade i1 in this ten year old laptop.

I think I'm on Mint 5 Elyssa right now.

---

### Post by roki on 2010-01-31
> **nuttymango said:**
> Would you mind posting your xorg.conf file? I've done battle with an Armada 110 (varying Linux distributions) for a long time and usually get it working after lots of "sudo vi /etc/X11/xorg.conf" trial and error.

I'd like a really definitive xorg.conf for the Trident CyberBlade i1 in this ten year old laptop.

I'm sorry but I don't have that Compaq anymore and I didn't save any files after the new owner decided to take it with Windows.

If I remember correctly, all I had to do was to make it use trident driver and correct VertRefresh and HorizSync values for LCD.

---

### Post by sid1202 on 2010-01-31
> **nuttymango said:**
> Would you mind posting your xorg.conf file? I've done battle with an Armada 110 (varying Linux distributions) for a long time and usually get it working after lots of "sudo vi /etc/X11/xorg.conf" trial and error.

I'd like a really definitive xorg.conf for the Trident CyberBlade i1 in this ten year old laptop.

I think I'm on Mint 5 Elyssa right now.

Have you tride the one posted by _huwjenjinn_?(post #**[[B]71**]("http://ubuntuforums.org/showpost.php?p=8493614&postcount=71")[/B]) It worked for me. It's simple yet effective.

Sid

---

### Post by MonsterTrimble on 2010-03-18
Has anyone found that Lucid causes issues? I had it working with 9.10 then I reformatted to upgrade to Lucid and if I try to change the Xorg.conf file it says I have no screens. Deleting Xorg.conf returns me to the original 800x600.

I haven't looked at the /var/log/Xorg.0.log yet but I will when I get home tonite and post it here.

---

### Post by wilsonmorgado on 2010-03-18
> **MonsterTrimble said:**
> Has anyone found that Lucid causes issues? I had it working with 9.10 then I reformatted to upgrade to Lucid and if I try to change the Xorg.conf file it says I have no screens. Deleting Xorg.conf returns me to the original 800x600.

I haven't looked at the /var/log/Xorg.0.log yet but I will when I get home tonite and post it here.

If you install **Ubuntu 6.10 **you get a** correct resolution** and Fn Keys orking ...


My X.org confg file:
[http://ubuntu.wilson.com.pt/2010/03/x11-config-file-portege-r100.html](http://ubuntu.wilson.com.pt/2010/03/x11-config-file-portege-r100.html)


Ctrl + F1
sudo service gdm stop
sudo Xorg -configure
sudo mv ~/xorg.conf.new /etc/X11/xorg.conf
sudo service gdm start
Ctrl + F7

sudo gedit /etc/X11/xorg.conf

> Section "Device"
BusID "PCI:1:0:
Identifier "Trident Microsystems CyberBlade XP"
Driver "trident"
EndSection
Section "Monitor"
Identifier "Configured Monitor"
Option "DPMS" "true"
HorizSync 30.0-60.0
VertRefresh 50.0-70.0
EndSection
Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 16
SubSection "Display"
Depth 16
Modes "1024x768" "800x600"
EndSubSection
EndSection

---

### Post by MonsterTrimble on 2010-03-19
What I ended up doing is two fold:

1) First, following a suggestion on another thread, I took my copy of Ubuntu 6.06 and booted up the Live CD. Once up (and having the correct resolution off the hop), I navigated to the Xorg.conf file, copied it to my USB, then rebooted into my Lubuntu Lucid setup and installed the Xorg.conf. I wish i could say all was roses, but no it wasn't. The screen still wouldn't jump up to the correct 1024x768 but at least I could still read it. 

2) I decided to again reformat my hard drive and stick to Lubuntu Karmic. Once that was done I manually mounted the USB, copied over the Xorg.conf and restarted. Success! Worked like a charm.

After this ordeal I *REALLY* get the Debian philosophy. I think it'll be May or June before I upgrade to Lucid just to avoid the LTS rush and let everyone bug test & fix. One thing I also found interesting is that my 6.06 disc found a completely different card then I found everyone else using on here, so use the Live CD and try it out. It may just fix the headaches.

---

### Post by nunomcsoares on 2010-04-19
Hello

I'm beginner in ubuntu, my trident are now working in correct resolution, but i can't use the S-Video Out, how can do that ? thanks in advance for the help !

---

### Post by boy_cad on 2010-04-25
Yes, it does seem that Lucid has these same problems, again.

I'm all new to Linux.  Ive haven't used a console since DOS in grade 5.  My apologies in advance if I'm missing something simple.  

I'm installing Lucid Lynx on a **Thinkpad R30** (circa 2001), and, as previously discussed, resolution tops out at 800x600.  It should be 1024x768.  Currently, we are working in Ubuntu Live, if that matters. 

Getting the proper screen resolution out of an old **Trident Cyberblade Aladdin i1** seems very difficult.  Also, searching for solutions is fun, but the solutions seem to keep changing.  There must be 20 posts about this problem in the Ubuntu forums.  For example, this one, which directs us to the xorg.conf file:

[http://www.uluga.ubuntuforums.org/showthread.php?t=1329192&highlight=trident](http://www.uluga.ubuntuforums.org/showthread.php?t=1329192&highlight=trident) 

It seems to have worked for them, on Ubuntu 9.10.  But, I understand that the xorg.conf file is no longer the correct package to work with for this sort of problem.  Is that true?

I have the xorg.conf (/etc/x11) file open in gedit now.  It is blank.  erm ... should I, y'know, generate one, or something like that?

Can anyone tell us how to get the oldTrident video cards working efficiently with the new,** Lucid Lynx 10.04 LTS Ubuntu**, please?  

It would also be nice to know that the driver for this card is reasonably good.  In some of the old posts, people are commenting that the generic Trident driver is, well, less than stellar.  Is that true?  Can we ask for a new one? 

Thank you for your time, everybody.  Congratulations on a great product from an even greater process.

---

### Post by boy_cad on 2010-04-25
FYI, here is a discussion with the manufacturer (well, Lenovo).  There is no solution here.  Come to think of it, shouldn't a new Linux driver be coming form these people?

[http://forums.lenovo.com/t5/Linux-Discussion/R30-Xbuntu-Linux-install-only-yields-800x600-screen/m-p/40243](http://forums.lenovo.com/t5/Linux-Discussion/R30-Xbuntu-Linux-install-only-yields-800x600-screen/m-p/40243)

---

### Post by roki on 2010-04-26
> **boy_cad said:**
> Can anyone tell us how to get the oldTrident video cards working efficiently with the new,** Lucid Lynx 10.04 LTS Ubuntu**, please?

Not yet. But before 7th of May I will tell you how it has to be done.

I just got that Armada 110 that I told you about earlier back, installed more memory, and it will run 10.04 smoothly when I give it to my daughter as a birthday present on date mentioned above.

- Roki

PS. I'll have only 3 days to do that since I'm on a work trip until tuesday morning. We'll see if 15 years experience in X tweaking helps at all. =)

---

### Post by boy_cad on 2010-04-26
Yeah! Right On!

I put Ye Old XP on the R30 yesterday, and yes, as expected, it moves like a slug with hemorrhoids.  But it is all there (including special-function keys).  Something with a little more -wowzie- would sure be nice.

I also found something.  With the new system on, I went in to Lenovo to update the drivers manually: [http://www-307.ibm.com/pc/support/site.wss/MIGR-40213.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-40213.html)

... and there is a fair amount here relating to the Trident Cyberblade Aladdin. 

It looks like Lenovo Japan has been over this driver section, and it seemed to work much better than the last time I built the machine back in 2007 or so. I know this stuff is proprietary, but Lenovo seems to have gotten in to the video problem a fair ways:

1.  The manual video driver update is absolutely necessary to run the computer.  Without it, even simply moving the mouse across a blank desktop is stuttery.

2.  The video driver improves the situation.  Then, all of the sudden, we get a whole bunch of Taiwanese options in the 'Display-Monitor-Advanced' context menu.

lenovo video driver: 
[http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-40378](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-40378) 

3. But we are not done yet! There are 'additional files' to apply.  Yes, that **Intel Chipset Utility **at the bottom of the page is an additional tweak _especially for the Video Driver_.

here is the 'Supplemental Files' link:
[http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-40378](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-40378)

My point is that Roki or any prospective coders might want to take a look at the readme from the above link.   


So, maybe some of that would be helpful.  Maybe we could just ask Lenovo (nicely) if we could use their drivers, and, y'know, Ubuntu-ize them.  It looks like the solution is not-so-simple. Or maybe its not so bad.  

Conclusion: Fare thee well, COders!  I hope you can get around to it, Roki.  Any solutions will be greatly appreciated, and I'll be looking for them posted here.
                                                            [URL="javascript: leoHighlightsIFrameClose();"]                    
       [/URL]

---

### Post by desQEDo on 2010-05-04
If you're in a hurry and can't wait until May 7 try this old thread. It may help for time being...:o
[http://ubuntuforums.org/showthread.php?t=533793](http://ubuntuforums.org/showthread.php?t=533793)
I have an R100 upgraded to Lucid Netbook Edition proper resolution only switching to the console and back with    	 	 	 	ctrl-alt F1, ctrl-alt F7. I haven't tried any other changes yet.

---

### Post by roki on 2010-05-06
> **desQEDo said:**
> If you're in a hurry and can't wait until May 7 try this old thread. It may help for time being...:o
[http://ubuntuforums.org/showthread.php?t=533793](http://ubuntuforums.org/showthread.php?t=533793)

I saw nothing useful in that thread.

And about Armada 110... You have to enter boot parameter "xforcevesa". X won't run without it. I have the installer running right now, and I guess that I will have xorg.conf in few hours.

- Roki

---

### Post by roki on 2010-05-06
You have to enter boot parameter "xforcevesa" when booting from installation disc. X won't run without it.

X will start after installation, but config is not optimal. (Running in VESA mode.)

Don't use "Xorg -configure"! It will kill your X. (I tried it, so you don't have to.)

After some research I found values that fit my laptop's display, and here we go:
```
# xorg.conf for Compaq Armada 110 by Roki 201005061520

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
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
	Load  "dbe"
	Load  "record"
	Load  "glx"
	Load  "dri"
	Load  "dri2"
	Load  "extmod"
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
	VertRefresh  56-61
	HorizSync    31.5-49
EndSection

Section "Device"
	Identifier  "Card0"
	Driver      "trident"
	VendorName  "Trident Microsystems"
	BoardName   "CyberBlade i1"
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
```
Most important part is to find correct VertRefresh and HorizSync values.

This works for my Compaq Armada 110 and I give no guarantee that it will work in any other macine.

BTW I'm not any kind of coder. Just been using/tweaking X for 15 years.

Next I have to check if 10.04 works with Huawei E220 3G-modem.

---

### Post by localzuk on 2010-05-08
I can confirm that that xorg.conf file works perfectly with the Toshiba Satellite S1400-103. Saved me much fiddling :)

---

### Post by boy_cad on 2010-06-09
Thank you, roki.  Yeah!  Three Cheers!

But, can we have some basic, beginner level instructions on how to apply this fix to a new  installation, please?  

For example, "xforcevesa" : where would we enter this parameter in the installation process. Also, what you have given us is a text file, right?  erm ... should I print it out and make the changes manually?  ooorr ... install direct from disc - cut an paste using the new system?  hmmm.

Its probably the best solution out there, but have just gotten back to this and haven't actually tried to make it work.  I know, I know - put in the disk and give it a try.  Still, it would be nice to have some instructions before going ahead.  It doesn't look too easy.

A few points to clarify: This isn't actually a new driver, is it?  Its more of a work-around, perhaps?  Also, will this x-org.conf work with the Netbook edition?

Like I said, I'll be putting it on to a circa 2001 Thinkpad R30.  I'll do some research and give it a try, but I'm pretty new to this.  Write back if I can get it to work.

---

### Post by roki on 2010-06-23
> **boy_cad said:**
> But, can we have some basic, beginner level instructions on how to apply this fix to a new  installation, please?

Internet is full of beginner level instructions. I can't provide them with my bad English language and point of view a way beyond beginner level.

> **boy_cad said:**
> A few points to clarify: This isn't actually a new driver, is it?  Its more of a work-around, perhaps?  Also, will this x-org.conf work with the Netbook edition?

The driver is one of the oldest in Xorg, I guess. This is just a work-around when auto-probe doesn't work. It should work with Netbook edition if you have package "xserver-xorg-video-trident" installed.

---

### Post by boy_cad on 2010-06-23
Thanks again.  I still haven't tried it, but it doesn't actually look tooo beginner.  "Some Research Required" (...o look my bean just changed color!)

---

### Post by badbob100 on 2010-09-06
Does this still work for 10.04?

---

### Post by boy_cad on 2010-09-10
All the recent posts should refer to the 10.04 release.  Still looking for that research time.  But first ... prep the R30 impregnation ;)

---

### Post by herrdeh on 2011-01-06
Hello everybody,

as this seems to be the ultimate thread on trident video chips, here is my issue:

I could make my girl's Toshiba Satellite 1800-750 work, with /etc/X11/xorg.conf as attached I get a 1024 x 768 screen.

But: I dont have hardware accelaration - switching windows takes several seconds sometimes, and movies (e.g. DVDs) are as slow as one picture every several seconds.

I did some research and found that hardware accereration is not active:

[LIST]
[*]installed mesa-utils
[*]glxinfo said (besides several other things) "OpenGL renderer string: Software Rasterizer"
[/LIST]
As far as I can see in the Xorg.0.log, the trident driver is loaded. I experimeted with several variations in the /etc/sorg.conf, but didnt come to a clou.

If anybody had a good idea, I (and my girl) were very happy.

Thanks a lot and greetings, herrdeh

PS.: Files attached, all are text files, extensions dont matter.

---

### Post by dreaminhere on 2011-01-09
I have much the same problem as Herrdeh with getting a picture every several seconds when I try to play SuperTuxKart.  Highly annoying :) I have a Toshiba Satalite A25-S07 and have tried various config files on the internet with no avail.

---

### Post by herrdeh on 2011-01-21
I filed a bug report here:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-driver-trident/+bug/706004]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-driver-trident/+bug/706004")

Maybe some folks would like to vote for the issue.

Yours, Wolf

---

### Post by roki on 2011-02-02
> **herrdeh said:**
> I filed a bug report here:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-driver-trident/+bug/706004]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-driver-trident/+bug/706004")

Maybe some folks would like to vote for the issue.

Yours, Wolf

IMHO it is not a bug that these old trident chips just are not fast enough for gaming and movies.

- Roki

---

### Post by herrdeh on 2011-02-03
@ Roki

I'm quite sure that on my machine the system doesnt use hardware acceleration at all:

glxinfo said (besides several other things) "OpenGL renderer string: Software Rasterizer"

So if we'd find a way to make use of the hardware accererator of the old trident chip, graphics output would be much faster anyways. Some folks reported having played DVDs on that machines way back with Ubuntu 6 or so- and wintendo actually can do as well.

---

### Post by krustybaguette on 2011-02-15
> **ilovelinux33467 said:**
> This guide assumes that you are doing a fresh install of ubuntu 8.04 and you get a wrong resolution with a trident video card.

These are the steps I did:

1. Boot up the ubuntu live cd. I selected "Try Ubuntu without any change to your computer".

2. Once it has booted up open up a terminal and enter "sudo displayconfig-gtk" (without the speech marks)Feel free to post whether it worked or not ;)

I am trying to get 9.10 (Karmic) up and running and having the Trident Video issue. The command listed in #2. results in "Command not found" both after using terminal in installed version and after rebooting with Live CD. I've also found no trace of an xorg.conf file in /etc or /etc/X11

I found what purports to be a driver for my Trident card. It's a 2.4 MB file named "XF86_SVGA" but can't figure out what to do with it. I tried to copy it to /etc/X11 but "paste" did not appear so I assume I'm not allowed to alter that folder.

Perhaps I should download and try the older version of Ubuntu anyway as I'm probably a little underpowered with this PIII 497 Mhz Toshiba Portege 7140CT and 320 mb RAM.

---

### Post by krustybaguette on 2011-02-15
[QUOTE=sdavmor;8218273]Yes, it will be empty. Copy & Paste in this code.  Log out.  Log back in. Go into "System","Display". Select 1024 resolution. Apply it. Have fun.


snipped code, but this looks like what I'm looking for. My Toshiba Portege 7140CT has Trident Cyber Blade e4-128 controller chip. I've been searching for drivers, how to install, etc. when it appears that all I have to do is create an "xorg.conf" file and put it in the right place!!!:p;):D

Many thanks.

---

### Post by roki on 2011-02-26
> **herrdeh said:**
> @ Roki

I'm quite sure that on my machine the system doesnt use hardware acceleration at all:

glxinfo said (besides several other things) "OpenGL renderer string: Software Rasterizer"

So if we'd find a way to make use of the hardware accererator of the old trident chip, graphics output would be much faster anyways. Some folks reported having played DVDs on that machines way back with Ubuntu 6 or so- and wintendo actually can do as well.
AFAIK there is no hardware acceleration for 3D in these trident chips, so OpenGL will stay in software rasterizer and gaming is impossible. For DVDs and other video stuff you should find another output method than OpenGL. I don't know which one is the best.

---

