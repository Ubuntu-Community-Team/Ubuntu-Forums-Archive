---
title: "Tethering iPhone to USB Bluetooth dongle"
date: 2020-12-03
forum: Hardware
---

### Post by mark bower on 2020-12-03
Ubuntu 20.04, iPhone SE 2020, Sabrent BlueTooth (BT) dongle.

I am trying to make a functional connection between my iPhone and BlueTooth (BT) dongle in order to download photos from the iPhone to the PC.  Following standard setup, both the Bluetooth Manager GUI and my iPhone show pairing successful - this includes matching a 6 digit code and accepting the code as seen via the BT Manager and the iPhone.  The BT icon on the system tray shows the BT icon with a lock symbol, and the BT Manager GUI has both a key and the trusted symbol affixed to the iPhone device likeness.  Yet, I do not achieve a functional connection.

Following are some command line diagnostics.  Of particular note is results from lsusb and idevicepair which do not return positive results.

lsusb sees the dongle, but not the iPhone
sudo rfkill list shows -
	hci0:  Bluetooth
	Soft blocked:  no
	Hard blocked:  no

hcitool dev sees MAC addresses of iPhone and BT dongle

hcitool scan returned nothing

idevicepair pair shows:
	"No device found, is it plugged in?"

hciconfig -a shows (abbreviated)

	BD Address: 00:1A:7D:DA:71:13  (Sabrent MAC addr)
	UP RUNNING PSCAN ISCAN 
	Link policy: RSWITCH HOLD SNIFF PARK 
	Link mode: SLAVE ACCEPT 
	Name: 'mark'
	Service Classes: Rendering, Capturing, Object Transfer
	Device Class: Computer, Desktop workstation
	Manufacturer: Cambridge Silicon Radio (10)
	
ifconfig -a  returned 3 different ethernet MACs

I tried to pair a Sony noise cancelling headset and encountered similar results as above.  I also tried a different BT dongle, and again, similar results:  appearance of pairing, but seemingly not really paired.

Since the GUI configuration gives the appearance of complete pairing, but isn't, I would like to assume there is some last tweak that could make the process complete.  Help please.

---

### Post by mark bower on 2020-12-05
Bump - for help

---

### Post by mark bower on 2020-12-10
Bump #2 - for help

---

### Post by mark bower on 2020-12-18
Bump #3 - for help

---

### Post by CelticWarrior on 2020-12-19
Comments and a question:

Tethering usually refers to sharing internet connection, not access to and transfer from storage.
I don't know exactly what happened with the Bluetooth headset but I imagine it paired correctly which doesn't mean the system automatically changes to that audio output (and Ubuntu may need additional software to support HFP).

The question comes regarding the iPhone: Doesn't it strictly requires iTunes for what you're trying to do? Last time I checked it did.

---

### Post by yancek on 2020-12-19
The simplest way I've found to download to/from an iphone is to use the vlc for mobile app on the iphone.  Do an online search on using it by searching  "using vlc for mobile on iphone ubuntu".  That should give you a number of sites explaining its use.  You can then use your browser with the ip address of the iphone to copy to/from the iphone.

When I plug my iphone into a usb port on the computer and click on iphone in the left panel of the Desktop, it opens shotwell which shows the DCIM directory wth the photos on the iphone.  On Ubuntu 20.04, this only works if I first open 'iphone' in Shotwell, then close it and open it again.  Not sure what that's about.

I expect your problem is related to the method you are using with the dongle and bluetooth.  I don't use bluetooth so can't help, good luck.

---

### Post by mark bower on 2020-12-28
@ yancek
I will try the VLC approach.  I find it a bit perplexing that there is not an abundance of iPhone/Ubuntu users who choose to download data wirelessly.  I assumed someone would nail the process.  I have downloaded with a wired connection, and I do it all the time with my camera.  Just believe it would be convenient to avoid the plug-in requirement.

@CelticWarrior
Thank you.  I looked up the definition of tethering and indeed it involves the internet.  I believe I was mis-told by my iPhone service provider (in fact, Consumer Cellular) was no help with my attempt to BT pair.

---

### Post by yancek on 2020-12-29
An iphone will be another device on your network if it is not physically attached to the computer.  Ubuntu documentation at the link below suggests using SSH although the documentation doesn't seem complete.

[https://help.ubuntu.com/community/Iphone%20connecting%20wireless](https://help.ubuntu.com/community/Iphone%20connecting%20wireless)

You can apparently also use VNC or Samba.  Never tried either myself.  A good part of the problem is the extremely proprietary nature of all Apple software which makes it extremely difficult for Linux developers to create software to work with Apple products.  Additionally, the percentage of iphone users is much lower than android so there really isn't much incentive.

[https://www.idc.com/promo/smartphone-market-share/os](https://www.idc.com/promo/smartphone-market-share/os)

---

### Post by mark bower on 2020-12-30
o.k., thanks for additional info.  i will try and get to "VLC approach" this eve or tomorrow.  I can say that I have transferred photos from iPhone to my PC via emailing, not a major effort, but Earthlink has a 20MB limit such that iPhone videos are too large to process(maybe even a 10sec burst may be too many MB).  I should state that that is the main driver for me:  not individual photos but video clip transfer to PC, while avoiding the cloud stuff.

---

### Post by yancek on 2020-12-31
The most common and simplest way to do this is with the cable with the usb you get with the iphone.   When I do this on Ubuntu, I see 2 icons in the left panel, one an icon of the phone and the 2nd an icon of a camera.  Clicking the camera icon opens the iphone to the pictures showing the DCIM directory.  If you open the file manager (nautilus) to the directory to which you wish to copy (/home/user/Pictures for example), you should be able to drag and drop the picture from your iphone to the Pictures directory.  Also, right clicking an image in the DCIM directory or sub-directory and selecting copy, you should be able to then paste the file there.

If you select the camera icon in the left panel on your Desktop, a window opens showing the DCIM folder and in the upper right of this window, you can click on Shotwell, you need to click the File tab in the upper left and select the option Import from folder which will then open a new window which shows the folders in your /home/user directory.  Click on the iphone icon in the left panel of shotwell and you will see the DCIM folder containing photos/videos. Double-click on DCIM and you should see any sub-directories with your photos/videos. Click OK in the upper right and a new window will give you an Import to library message with options to Copy Photos or Import in place. If you click Copy Photos, a message in the left panel will show importing and the files will be imported to a sub-directory under /home/user/Pictures. When it finishes, you should see a message photos successfully imported.  This imports all images in the specific folder.  I don't see any way to select individual or several image files.


The Import in Place option is explained at the link below.  The option you want is to Copy Photos.

[https://askubuntu.com/questions/152993/shotwell-does-not-copy-but-imports-files-without-copying](https://askubuntu.com/questions/152993/shotwell-does-not-copy-but-imports-files-without-copying)

---

### Post by mark bower on 2020-12-31
yes, i have transferred iPhone to PC via cable via your method 1.  no problem there.  i rate myself as being obstinate - just wanted to do it wirelessly.  i appreciate all your detail and i now realize that i never mentioned being successful with the cable method - my apologies as i should have include that in my 1st post.

but, your help is not for naught.  its caused me to jump out of my stubbornness and into more practical thinking - i am going to use the cable method as the method of choice for the immediate future.  however, i will copy your VLS instructions and given a little more time, see if i can get it to work.  and yes, i may even pursue bluetooth again in the far future.

thanks again
mark

---

### Post by yancek on 2021-01-01
If you install the VLC for mobile app on your iphone, make certain that it is open on the iphone before you try to access it from your computer.  When you open VLC on the iphone, there will be several icons.  One is network so tap that.  There will be an option Sharing via Wifi so select that.  Just below Sharing via WiFi you will see the IP address of the iphone which is what you need to enter in the address box on your computer browser, something like:  192.168.0.34.  You don't need the http part and it doesn't work if it shows https.

Hopefully you will have better luck than I did as this failed on Ubuntu 20.04 for me.  When I try to drag and drop from the iphone to the file manager on Ubuntu, I get a pop up saying Drag and drop is not supported  An invalid drag type was used and it fails. When I drag and drop from the computer to the iphone, the image file name shows in VLC with -100% showing after the file name which would indicate it was copied but it is not, isn't see in Photos on the iphone.  I get the same result on clicking the + in the upper right window of VLC and navigating to a folder with images and opening/copying it. Also on Ubuntu, if I right click an image on the iphone under the Download Files box, it does not give an option to Copy so cannot Copy/Paste to nautilus on the computer.  I can right click an image in nautilus and select Copy but there is no option to paste in VLC. I also have Slackware Linux installed on this computer and the methods of drag and drop to and from the iphone as well as copy/paste to and from work without problems so I'm not sure what the problem is . 

Good luck with it, especially the bluetooth method.

---

