---
title: "sony VGN-FW200 Series"
date: 2008-11-28
forum: Hardware
---

### Post by drews_blunted on 2008-11-28
Hello, i just bought a sony vaio labtop and i am trying to install ubuntu onto the computer. When i start the ubuntu install as the loading screen goes and finishes i am left with a weird white screen with odd blackish colors on the screen. It doesnt alow me to see anything or install ubuntu. Does anyone know why this is happening. I do belive that ubuntu should be able to install on this machine! any help would be great!

---

### Post by blls on 2008-11-30
same problem here... I'm new to Ubuntu, but have experience with Suse. Sony vaio FW270

---

### Post by ronmillsap on 2008-11-30
Make that three... FW270
I tried 32 bit and 64 bit, no difference.
Tried live CD, tried install, no difference.

---

### Post by NotoriousMOK on 2008-12-01
Sony Vaio VGN-NS135E

I was able to complete the installation using the alternate CD, but am still working on video issues.


good luck

---

### Post by drews_blunted on 2008-12-01
I have been able to install ubuntu using the Alternative Cd as well. I tryed the normal cd is safe mode but i couldn't get pass the partitioning stage. I am still having a problem getting the white screen to go away.
I tryed to edit the xorg.conf file but when i opened it in nano there was nothing in the file? Not sure if i either had a bad install or if the file is blank for some other reason. hope someone else will come up with a good fix if i cant figure it out.

Also i found this link witch may help fix some other of our problems with ubuntu and this labtop!
[http://vaioubuntu.wordpress.com/](http://vaioubuntu.wordpress.com/)

---

### Post by drews_blunted on 2008-12-01
WOW i found a quick fix to get past the white screen of death!

First i logged into ubuntu once i got to the white screen i typed Ctrl alt f1 to switch to a diffrent console then i loged in. 

And typed: sudo dpkg-reconfigure xserver-xorg

Just went with the regular options.

Once my xorg.conf file was created i edited it with nano
"sudo nano /etc/X11/xorg.conf"

Then i added the line

	Driver	"vesa"

under the section "device" part of the xorg.conf file.

I saved the file by typeing ctrl x to exit and it asked me to save i typed Y for yes. Then i switched to the xorg console "ctrl atl f7" and typed ctrl alt backspace to restart the xserver and WHALLAH! i had a working Xserver. 

Hopefully this will fix some of your problems. 

I just got this labtop at bestbuy on black friday, i have a feeling theres a bunch of us out there who wanted to put ubuntu on it!

Now all i need to do is figure out if i can get a better video driver than vesa to get full performance outta the onboard video!

Thanks!:popcorn:

---

### Post by ronmillsap on 2008-12-01
Thanks Drews,
I'm on my way out to work so I can't do this till tonight.  I'll go nuts all day thinking about it. I HAVE to have my Ubuntu. I too bought a FW270 at Best Buy when my HP died on Friday.
I hope it works !
Thanks again

---

### Post by drews_blunted on 2008-12-01
Ok, so after i got my vesa setup i went ahead and found this generic xorg file somewhere on the forums for a similar sony labtop and i tryed it and i was alowed to get a higer resolution. Only 1024 x 800 but thats better than 800x600. I have a feeling there is not suitable video drivers for this graphics ard right now for ubuntu. For now this is my best workaround untill myself or someone else figure out how to get the onboard video to work with the intel drivers. Hope this helps someone else out!


> ### X.org configuration file


## Server settings
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Touchpad" "AlwaysCore"
	InputDevice    "USBMouse" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection


## Font settings
Section "Files"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection


## Module settings
Section "Module"
	Load  "xtrap"
	Load  "glx"
	Load  "dbe"
	Load  "extmod"
	Load  "dri"
    Load  "vbe"
EndSection


## Input devices
# Keyboard
Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
    Option      "Name" "Sony Vaio Keys"
    Option      "CoreKeyboard"
EndSection

# Trackpad mouse
Section "InputDevice"
	Identifier  "Touchpad"
	Driver      "synaptics"
    Option      "SendCoreEvents" "true"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
    Option      "HorizSrollDelta" "0"
    Option      "SHMConfig" "true"
EndSection

# USB mouse
Section "InputDevice"
	Identifier  "USBMouse"
	Driver      "mouse"
    Option      "CorePointer"
    Option      "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection


## Monitor settings
# Built-in LCD display
Section "Monitor"
	Identifier  "LVDS"
	VendorName  "Sony"
	ModelName   "Vaio SR X-black LED"
   	Option      "DPMS"
	Modeline    "1280x800_76.00"  108.77  1280 1360 1496 1712  800 801 804 836  -HSync +Vsync
	HorizSync   62-63
	VertRefresh 76-77
    Option      "Monitor-LVDS" "LVDS monitor"
EndSection

# VGA output
Section "Monitor"
	Identifier  "VGA"
	VendorName  "VGA"
	ModelName   "VGA-output"
    Option      "Monitor-VGA" "VGA monitor"
EndSection


## Graphics card driver
Section "Device"
	Identifier  "Card0"
    Driver      "vesa"
    #Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "Cantiga Integrated Graphics Controller (Q45)"
    Option      "MonitorLayout" "LVDS"
	BusID       "PCI:0:2:0"
EndSection


## Display settings
Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "LVDS"
    DefaultDepth 24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


---

### Post by ronmillsap on 2008-12-02
Drews,
Thanks for continuing to post here.  Your first solution worked like a charm. I didn't complete the install thinking that I would try to find a more sutible driver. Now, you've once again found the solution and once again, I'll have to try it when I get home from work. 
I for one really appreciate your posts.
Thanks again

---

### Post by drews_blunted on 2008-12-02
Well so far everything work hardware wise on my FW270 even the webcam/wireless works perfectly! Im still working around with the video. So far all i have been able to get is better resolution. But im hoping to see if i can either get the right intel drivers to work (may not be released yet for ubuntu) or trying to find if i can get vesa to run at a higer resolution. Iall post back with any results if i can fix the problem.

---

### Post by drews_blunted on 2008-12-03
So after another night of research i have discovered that alot of other labtops have been having this problem. Dell labtops with ubuntu pre-installed were white screening as well and they had similar hardware to our sony FW series labtops. The Problem is a bug in the intel drivers. It seems the real problem is with our LCD displays not working correctly with the intel drivers. I belive it said AUD lcd displays were causing issues. I do not personaly know much about what display our sony labtops are using but i wouldn´t be suprised if it was the same lcd. Atleast one person said they had the lcd monitor changed and it worked, but im thinking I don´t know how the hell to do that, so its out of the question. I belive our best bet is to use the vesa drivers with restricted resolution. I am working on trying to get the vesa to display at higher resolutions, but so far 1024 x 800 is the best i have been able to get. 

Problems with Dell Labtops with similar setup:
[http://ubuntuforums.org/showthread.php?t=892146&highlight=intel+video+drivers&page=11](http://ubuntuforums.org/showthread.php?t=892146&highlight=intel+video+drivers&page=11)

Reported Bug:
[https://bugs.launchpad.net/ubuntu/+bug/297245](https://bugs.launchpad.net/ubuntu/+bug/297245)

So i guess if we check the link above in the coming months we can see if the bug has been fixed! Longest wait i could see is till jaunty jackalope comes out, by then we should have issues like this cleaned up.

---

### Post by ronmillsap on 2008-12-04
Thanks for the info Drews.  I wouldn't have a problem replacing my lcd if I had more info.  I was able to get 1024x768 going and that will get me functional but I'd like to take full advantage of the display capabilities in Ubuntu and dump Vista.  I'll keep watching and waiting.

---

### Post by ronmillsap on 2008-12-04
Just finished reading the Dell issue and they referenced the AUO made lcd but it was a 15.4 and the Sony FW270 is a 16.4 so I'm thinking it's the driver and not the LCD.  I'll keep my fingers crossed on this one.

---

### Post by drews_blunted on 2008-12-05
We could test if it is the screen by using another monitor pluged into the vga out port to see if the screen works with intel drivers. The reason i think it may be the screen is because if the intel drivers were broke they wouldnt even load the x server, so possibly our lcd monitors are distorting the video and giving us the white screen of death. iall look into it some more. Hopefully some forum elders will know how to fix this problem!

---

### Post by drews_blunted on 2008-12-09
[http://www.linux-gamers.net/modules/news/article.php?storyid=2502](http://www.linux-gamers.net/modules/news/article.php?storyid=2502)

This link says intel released new drivers. Does anyone know if this fixed the problems?

---

### Post by igknighted on 2008-12-09
Hey guys... there is a home-brew patch you can use to make the intel drivers work.  See these two bug reports for the fix and compile the driver yourself and your display will work perfectly.

Ubuntu bug report: [https://bugs.launchpad.net/xorg-server/+bug/268615](https://bugs.launchpad.net/xorg-server/+bug/268615)

Xorg (upstream) bug report: [https://bugs.freedesktop.org/show_bug.cgi?id=17292](https://bugs.freedesktop.org/show_bug.cgi?id=17292)

---

### Post by drews_blunted on 2008-12-10
HORRAY! Its Fixed!

Thank you so much all who helped!

All you need to do is download this file below, remove your existing intel xserver drivers and install the provided .deb files included in the below .tar.gz file.

[http://launchpadlibrarian.net/19868825/intel%20driver%20fix.tar.gz](http://launchpadlibrarian.net/19868825/intel%20driver%20fix.tar.gz)

Make sure to change your drivers from ¨vesa¨ to ¨intel¨ in your xorg.conf file. Once done restart and everything should work! If you were using my custom xorg.conf file for vesa that i posted earlyer do this:
sudo dpkg-reconfigure --phigh xserver-xorg 

This will fix your xorg and everything should auto detect and you will have optimized settings!

3d / high resolution will work for you now!

:popcorn:

---

### Post by ronmillsap on 2008-12-10
Drews,
Please pardon my ignorance but when you say "remove" could you specify "what from where"?
Also, when you say "install" do you just mean copy to a specific location or do you mean to execute a specifi command?
Lastly, when I unpack the tar, should it be to a specific place?
Sorry about all the questions but I still struggle with linux technical stuff.

---

### Post by Crimble on 2008-12-10
Can you all tell me what the path to the Intel drivers that I need to replace are located in Ubuntu 8.10. 

Thank you guys SO much for ALL of your hard work!:guitar:

---

### Post by Crimble on 2008-12-10
So for us novices... (is this correct?)

STEP 1.
Open up a terminal window and type:
sudo dpkg-reconfigure xserver-xorg
(Answer Yes to ALL questions)

STEP 2.
In that same terminal window, now type:
sudo nano /etc/X11/xorg.conf

"Make sure to change your drivers from ¨vesa¨ to ¨intel¨ in your xorg.conf file."
 
---this is what is a lil confusing...
So, the terminal window changes from a notepad looking screen to a unix looking screen that I can edit, so I go to the area that says "DRIVERS" and change the word "vesa" to "intel", I than press the Ctrl button ALONG with x (Ctrl+x) to exit and save my changes, I think.


STEP 3.
Download this file below:
[http://launchpadlibrarian.net/198688...r%20fix.tar.gz](http://launchpadlibrarian.net/198688...r%20fix.tar.gz)

remove your existing intel xserver drivers
*THIS IS WHAT I GET STUCK ON, WHERE DO THEY LIVE?*

install (DO THIS MEAN REPLACE?) the provided .deb files included in the file you just downloaded.

Than, reboot or the equivalent in Ubuntu.

Please Help. I need Compiz back and if I could walk around with Ubuntu on my VAIO I could tell all of my MAC friends to go scratch AND I REALLY WANT TO DO THAT! :p

---

### Post by Crimble on 2008-12-10
...or is their a command line to type into Terminal that will do all of this automatically, instead of using a mouse and GUI?

---

### Post by ronmillsap on 2008-12-10
Whoa !
I got it !  Thanks Drews !
I am SOOOO very impressed with Ubuntu on this display.

As for you Crimble.
Unpack the tar.gz file and in the folder named "Intel" you will find 3 package installer files that all end in ".deb"
Double click on them and then click the "install package" or "re-install package" button on the right near the top.
Once you've installed all three, close those windows, and open a terminal window.
Type "sudo nano /etc/X11/xorg.conf" and once the editor opens, change any line that reads Driver  "vesa" to Driver  "intel"
Save the file.
Then read Drews earlier post and if you need to, in a terminal window type "sudo dpkg-reconfigure --p high xserver-xorg"
When that ends, close out all the windows and restart your computer.
You should then be working fine.

Once again, THANK YOU DREWS !

---

### Post by drews_blunted on 2008-12-10
yup ronmillsap helped clarify it for those new to ubuntu. But dont thank me. Lets all thank whoever it was that finaly patched the bug with the intel drivers! This is one reason i just LOVE linux. You have a problem and instead of waiting forever to deal with tech support and sending your computer back to the manufacture, etc etc.. We can simply fix the problem with the code recompile it and everyone enjoys having a working computer!

I now have all the hardware working PERFECTLY on my brand new sony fw-270 labtop! 

Thanks linux users!!

---

### Post by Crimble on 2008-12-10
WHOOOOOOOOOOOOOOOOOOOOOO HOOOOOOOOOOOOOOOOOOOOOOOOOOOO!
I'm so happy! :guitar:

Ok, next walk through...

Under the names of each poster is something that says "Thanked x Times in x Posts" 

How do I thank you all for the help and raise that number :KS

I Love being part of the Ubuntu movement. Its just the thing the computing world needs. A collection of people dedicated towards the expansion and evolution of an idea that is truly revolutionary in its approach and intension. 
As a computer user I'll run anything you put in front of me, but I find it difficult to embrace the MAC world because of the limits of having 1 company making all of the decisions about the direction of MY computing needs. 
Microsoft is not worth any more of my typing...

---

### Post by Crimble on 2008-12-11
~

---

### Post by Crimble on 2008-12-11
Fixed it.

---

### Post by JunCTionS on 2008-12-12
Oh great!,
I want!
I have the exact same model. But I'm using kubuntu of 64bits, so these drivers are compiled for the i386 architecture (at least two of them, and another one is in the repositories).
Where can I find the 64 bit version compiled (basically tell me where you found this link to see if they did that too).
I tried compiling it but it gave me this error when running ./configure:
> No package 'xorg-server' found
No package 'fontsproto' found
apparently I'll have to install Xorg 7 to get over this... but I'm not sure.
So the pre-compiled drivers are the best option.

---

### Post by JunCTionS on 2008-12-12
Correction: I didn't have to install Xorg7, it comes with Intrepid
I had to have several developer packages related to the xorg to compile (as should be expected).
I compiled and did a make install, but it doesn't seem to work. (I tried just about everything, uninstalling and reinstalling it after removing the packages on the package manager, but nada... it doesn't seem to be even installing the same thing)

How do you make the deb packages when compiling?

---

### Post by smoosh on 2008-12-12
I love whoever figured this out.  LOVE.

---

### Post by JunCTionS on 2008-12-12
If I'm not mistaken, the one that "figured" this out might be mentioned in the README of that file:
> The X.Org version of this driver is maintained by Intel Corporation.
<http://www.intellinuxgraphics.org>
It's great to see that some of our hardware manufacturers make an effort for linux :).
Although I'm still looking for the 64-bit drivers or to learn how to compile them. Help! I've got a very impatient tech-support"costumer" (my girlfriend :P) waiting to get her new computer fixed so she can keep working in her thesis.

---

### Post by JunCTionS on 2008-12-12
sorry. re-post.
for some reason it got posted twice.

---

### Post by smoosh on 2008-12-12
Hmmm, it works fine for a little bit actually, and then the graphics go crazy and scramble themselves all over the screen.  Anyone else have this issue?  I'm having a heat issue (the fan don't come on ever.), too, so it might be the video chip getting hot.

---

### Post by JunCTionS on 2008-12-12
Done!
[daniel in launchpad]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/268615") was nice enough to compile them.
Here they are (the 64-bit version of the drivers): [http://launchpadlibrarian.net/20392873/fixed%2064%20bit%20driver.tar.gz]("http://launchpadlibrarian.net/20392873/fixed%2064%20bit%20driver.tar.gz")
Just install the three files in there (they replace the old intel ones so no need to uninstall them) and then change "vesa" for "intel" and then restart the X Server (Close and save anything important then press "Alt+Ctrl+Backspace" which will also log you out or reboot).

smoosh: I have no such problem here. it might be the fan or it might be that your computer is from a slightly different series than these posts.

---

### Post by Misz on 2008-12-18
With much help from this thread, I was able to get the install & the higher resolutions working with the 8.10 install CD on my Sony VAIO VGN-FW235J.  MUCH thanks to =D> drews_blunted, ronmillsap & Crimble =D> for their research, persistence & detailed explanations which helped a newer Linux user (Ubuntu for about a year now) like me get it working! 

Thanks everyone! \\:D/

---

### Post by ronmillsap on 2008-12-20
Ahhhhhhh
A fellow Michigander huh?

---

### Post by Misz on 2008-12-22
Yes sir.  Better to be inside trying to get Ubuntu working on my new "Black Friday" laptop than outside in the freezing cold & wind! 8-)

---

### Post by blls on 2009-01-20
Hi community!

I got my vaio laptop using the intel 4500mHD graphics chip working using the fix. However, I updated xserver with the auto-update and now it's broken again. 

I have tried to reinstall the patch (3 files), but it ends in dependency errors. I have tried "sudo dpkg reconfigure --p high xserver-xorg" but the command will not reconfigure due to a conflict with the current settings.

Can anyone help me reconfigure/repatch, or roll-back the update?

Thanks in advance

---

