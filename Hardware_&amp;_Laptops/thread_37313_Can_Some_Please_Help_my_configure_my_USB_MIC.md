---
title: "Can Some Please Help my configure my USB MIC"
date: 2005-05-26
forum: Hardware &amp; Laptops
---

### Post by dragonopolis on 2005-05-26
I use my computer as my main source of communication in my home.  I have VOIP service and no conventional phone. 
 
  My mic input jack to my sound card broke, so I bought a USB logitech mic (AK5370).  I plugged the device, booted into Linux, and recognized it immediately.  I went to use it, but didn't work.  I checked to see if it was muted but it wasn't.  I need someone to help me solve my USB mic issues so that I can go back to using Ubuntu as my desktop.  Meantime, I reloaded XP on my computer to test if it was my device.  I am happy to report that it is working flawlessly

I went back into Ubuntu to check the mixer to see if there was any conflicts.  I did notice that the input was set as my sound card (ALC650 realtek).  I figured I change the input to my USB mic and my problems would be solved. It actually made it worst.  I tried recording my voice but that didn't work.  So I decide to go back to the mixer to see what was up and I noticed I had lost sound.  

So I checked the mixer and discovered that when I had changed my input to my usb mic, the mixer had also changed my output to the same device.  I tried changing my output back to my soundcard, but in doing so, the mixer changed the input back to my sound card.  I am sure that Linux allows multiple sound devices but I obviously don't no how to configure it in Linux or in Gnome.

I really need some help to tackle this issue --  I had to switch back to XP -- but I really want to use Ubuntu.

 :|

---

### Post by socrates32 on 2005-11-24
Have you found a solution for this? I've been facing the same problem with the same device (Logitech USB mic). I was hoping that Breezy would fix it, but no luck. I'm certain that it's a rather minor configuration issue, but I can't figure out where to go from here.

---

### Post by anil_robo on 2005-12-04
I have a Logitech QUickcam webcam which also has a microphone in it. It's a USB device with both video and audio input capabilities. I tried hard to make the webcam work, but have not been successful so far, because I don't know how to compile the drivers, and there is not enough information available on the web how to compile the drivers.

I can't record sound through the USB webcam.

If someone finds some info, please post it here as a reply. THanks!

---

### Post by pieterk on 2005-12-13
On the site of OpenWengo I read that the Quickcam should work "out of the box" in Breezy. I didn't with me. But encouraged by this I pulled my Quickcam out of my usb-hub en connected it direct into the computer-case itself. And EUREKA!

Hope it helps.

Pieter

---

### Post by pieterk on 2005-12-13
I would like to add this:
I installed "camora". It doesn't get a link in the user-menu so you have to call it from a terminal and/or create a link yourself.

This program showes your webcam in a nice way!

Also I installed "usbview". From the output of this program I learned that the built-in mic of the Quickcam _is_ recognized!

I will try to ask on the Dutch Ubuntu forum about this. If I hear anything I'll keep you posted. 

Pieter.

---

### Post by anil_robo on 2005-12-14
Thank you Pieter for considering our problem. The webcam is recognized by Ubuntu, but it locked up when I tried to initiate viewing it by camorama etc. I read a tutorial by Arnieboy in these forums - he says I had to recompile the kernel. That's what I did and now I'm able to view the webcam properly. However, I have not tested it yet with gnome-meeting because I don't have any friend who uses Linux/gnome meeting.

Video has started working, but the USB mike in the camera still doesn't work! I've tried with several settings etc. but it never worked - except for one second during a skype session with my friend! God knows why! There's clearly an inadequacy of sound recording help in the forums, but apparently few people are concerned about it.

---

### Post by anil_robo on 2005-12-17
Good news!
 I have successfully recorded sound in Ubuntu few times just half an hour back! Read my post [here]("http://www.ubuntuforums.org/showthread.php?t=102377#6")

---

### Post by pieterk on 2005-12-27
Perhaps even better news! I installed the 2nd flight of "Dapper". Skype again does not work with the mike. BUT its French equivalent Openwengo does so excellent.
In Wengo dial 333 and wait until the french voice stops its speedy story. Then you can hear your own sounds echo. At least I can.

Hope this is a good omen!

Happy endings Pieter

---

